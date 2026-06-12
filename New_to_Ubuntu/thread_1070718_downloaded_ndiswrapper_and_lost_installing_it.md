---
title: "downloaded ndiswrapper and lost installing it"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by bigbandwith on 2009-02-15
From what I have read I need to install ndiswrapper to make my linksys wireless adapter work with kubuntu. It is the rt2500 chipset.   I downloaded ndiswrapper 1.54 and it is sitting in a folder in my home/space folder with space being my user name.     In tried intalling from my desktop terminal with the following commands

space@space-desktop:~$ # tar -xzf ndiswrapper-1.54.tar.gz
space@space-desktop:~$  # cd ndiswrapper-1.54
space@space-desktop:~$  # make
space@space-desktop:~$  # make install

Then i try to go to the root with sudo -s

root@space-desktop:~# # tar -xzf ndiswrapper-1.54.tar.gz
root@space-desktop:~#  # cd ndiswrapper-1.54
root@space-desktop:~#  # make
root@space-desktop:~#  # make install

Both sets of commands do nothing

Any help would be appreciated. 
Thanks.

---

### Post by kk0sse54 on 2009-02-15
Check out this link
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by bigbandwith on 2009-02-15
Figured it out by spending some time in:

[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)

Note to all newbies.  Spend some time learning the basis commands in terminal and then spend some time in terminal exploring the system.   This is all starting to make sense now.

:P

---

