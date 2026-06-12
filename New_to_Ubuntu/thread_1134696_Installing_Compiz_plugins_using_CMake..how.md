---
title: "Installing Compiz plugins using CMake..how?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by appliedmath on 2009-04-23
Hello,

I have Ubuntu 9.04 and 

I would like to install a Compiz plugin called Grid:

[http://git.compiz.org/compiz/plugins/grid/](http://git.compiz.org/compiz/plugins/grid/)


The Grid plugin used to have makefile so that I can simple "make install", but it changed to CMake stuff.

I installed cmake, and tried to install Grid, but I get the following errors


```

CMake Error at CMakeLists.txt:1 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake



CMake Error at CMakeLists.txt:3 (include):
  include could not find load file:

    CompizPlugin


CMake Error at CMakeLists.txt:5 (compiz_plugin):
  Unknown CMake command "compiz_plugin".


```


I am not familiar with CMake at all.  I could not find a solution to this online.  Please help.

---

### Post by Hospadar on 2009-04-23
Sounds like a missing dependancy issue, for problems like this (I try to build something and get a complaint about a missing file) I like to use apt-file, you can search all packages for a filename, and it will tell you what package(s) have that file.

To use it, from a terminal, ```
sudo apt-get install apt-file
apt-file update
apt-file search <filename>
```
That said, I searched for the files mentioned and didn't come up with anything, so probably it's some third party dependency,  Double check the readme and see if it says anything about dependencies, or maybe even just shoot the developer an email with the error.

---

