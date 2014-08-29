---
title: Using pip instead of git submodules for python packages
layout: post
---

## Git submodules are a pain

Git submodules are a pain in the ass because of the strange and
counterintuitive aspects of the workflow -- e.g. they don't clone
automatically with the archive, and require multiple commands to clone
after the initial clone of the archive. Also, whenever you want to
update what submodule commit your outer repository points to, you
add the directory ``as a file,'' which is a strange syntactic 
construct imho. 

## Use pip instead when including a python package

In case your desired submodule happens to be a python package, you're
in luck because there's a more user-friendly way. Just include the
commit id in your `requirements.txt` as show below, and running
`pip install -r requirements.txt` will clone and install the package.
The clone will be found in the `src/<module_name>` directory. 
There you can edit the code, and it will be loaded by python when
you modify it. As soon as you want to lock in a new commit of the
submodule in your outer project, just modify the `requirements.txt`
file accordingly. 

Example: Include this line in `requirements.txt`.

    -e git+https://github.com/scottgwald/wearscript-python.git@5984a00bddbbbfa7c8b62a9b70571632d0a48e41#egg=wearscript

scottgwald
2014.08.29
