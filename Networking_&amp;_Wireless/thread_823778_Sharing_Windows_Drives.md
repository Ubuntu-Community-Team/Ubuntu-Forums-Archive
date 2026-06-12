---
title: "Sharing Windows Drives"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by mikeman141 on 2008-06-09
Hey all,

I've looked around via google and search here, but haven't seen this problem and was looking for some help.  

I am trying to share a drive on my Vista machine over the wireless network.  I have followed several different instruction sets I've found, and nothing has worked.  I've tried to access the shared drive on other windows machines on the network, and I've been able to access them no problem.

I'm rubbing Hardy Heron, when I go to Places > Network > Windows Network > Workgroup > MikeDell the file browser is empty.  If I do that on a PC, I can access the C drive as expected.

Any ideas on what could be wrong?  I've installed samba and smbfs  .

---

### Post by Mgiacchetti on 2008-06-09
[http://ubuntuforums.org/showthread.php?t=511327](http://ubuntuforums.org/showthread.php?t=511327)

someone with the same issue found a resolution in post #2

---

### Post by ThomThom on 2008-06-17
> **mikeman141 said:**
> Hey all,

I've looked around via google and search here, but haven't seen this problem and was looking for some help.  

I am trying to share a drive on my Vista machine over the wireless network.  I have followed several different instruction sets I've found, and nothing has worked.  I've tried to access the shared drive on other windows machines on the network, and I've been able to access them no problem.

I'm rubbing Hardy Heron, when I go to Places > Network > Windows Network > Workgroup > MikeDell the file browser is empty.  If I do that on a PC, I can access the C drive as expected.

Any ideas on what could be wrong?  I've installed samba and smbfs  .

Did you find a way to make Samba work?
I got the same issue. My Windows machine is listed, but none of the shares appears. However, if I go "System->Connect to Server..." and specify the name of the windows machine and the name of the share it will open the share.

One thing though, when I manually connected it I was asked for username and password where I entered the username and pw of my Windows machine. I was not asked this when trying to access via System->Network.

I've enabled the Guest account on my windows machine.

---

