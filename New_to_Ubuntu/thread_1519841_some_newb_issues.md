---
title: "some newb issues"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by sinnedam on 2010-06-28
Hey guys, I would appreciate any insight you might could offer on the following things. 

1. WINE. I have it installed, but im not sure how to use it. I thought it was pretty much like a virtual machine..but it doesn't look like thats the case. Can someone give me an example of how to install a windows software using WINE?

2. My wireless still seems flaky..browsing websites is slower than it is on a comparable Windows laptop on the same wireless connection. and see problem 3..

3. How do you access a network share in Ubuntu? I tried to just go to places/network. It had the other computer listed as a network place. I clicked, then authenticated, and it showed me the actual shares on that computer, but when i tried to browse them, i authenticated again, but this time it hangs for a second then i get a dialog box telling me to wait for the process to complete...it goes away and nothing happens...i click on it again i repeat the same process with no results..is this tied to my wireless problem?

thanks for the help guys.

---

### Post by nhasian on 2010-06-28
well #1 is easy enough to answer.  to install windows software, right click on the setup.exe or installation file and say open with wine.  then it will be installed under applications-> wine-> programs.  it is not a virtual machine.  if you want to run windows in a virtual machine you can install virtualbox or kvm.

are you trying to access a windows share?  you may need to adjust the share settings from the windows computer.

---

### Post by sinnedam on 2010-06-28
> **nhasian said:**
> well #1 is easy enough to answer.  to install windows software, right click on the setup.exe or installation file and say open with wine.  then it will be installed under applications-> wine-> programs.  it is not a virtual machine.  if you want to run windows in a virtual machine you can install virtualbox or kvm.

are you trying to access a windows share?  you may need to adjust the share settings from the windows computer.

Thanks for the insight..also, yes its a Windows share, and i can access it from a Windows machine using the same credentials so i know its nothing on the share side. I think it may be this wireless..is there any way to look at the wireless nic settings? or maybe look for a driver update?

---

