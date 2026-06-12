---
title: "Using Ubuntu-10.10(maverick) showing error while using .sh scripts"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by baba786 on 2010-10-27
Hello every one I just installed Ubuntu-10.10 now I am trying to install Codeblocks... and Openframeworks ... but its showing error when I am compiling it from terminal...


sudhanshu@sudhanshu-M61PME-S2P:/media/84AADE63AADE50F2/openframeworks-openFrameworks-454e0e1/scripts/linux/ubuntu$ sudo ./install_codeblocks.sh
sudo: ./install_codeblocks.sh: command not found


Please Help me out from this

---

### Post by terdon on 2010-10-27
Hi, sounds like the script you are trying to run is not in the current directory. Are you sure it is there?

---

### Post by baba786 on 2010-10-27
yeah its there even I installed it when I was running it on Ubuntu-10.04 but now its not working

---

### Post by Terl on 2010-10-27
is it executable?  Do a ls -l in the directory and see if it is marked as such.

if not then do a chmod +x your_script and it should work

---

### Post by baba786 on 2010-10-28
I performed this method ... but its still showing same error..


sudhanshu@sudhanshu-M61PME-S2P:/media/84AADE63AADE50F2/openframeworks-openFrameworks-454e0e1/scripts/linux/ubuntu$ ls -l install_codeblocks.sh
-rw------- 1 sudhanshu sudhanshu 1647 2010-10-25 09:33 install_codeblocks.sh
sudhanshu@sudhanshu-M61PME-S2P:/media/84AADE63AADE50F2/openframeworks-openFrameworks-454e0e1/scripts/linux/ubuntu$ chmod +x install_codeblocks.sh
sudhanshu@sudhanshu-M61PME-S2P:/media/84AADE63AADE50F2/openframeworks-openFrameworks-454e0e1/scripts/linux/ubuntu$ sudo ./install_codeblocks.sh
[sudo] password for sudhanshu: 
sudo: ./install_codeblocks.sh: command not found

---

