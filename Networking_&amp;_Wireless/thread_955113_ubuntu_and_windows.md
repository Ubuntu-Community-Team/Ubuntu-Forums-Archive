---
title: "ubuntu and windows"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by rusty_jones on 2008-10-21
I have 2 pc's one windows and one Ubuntu 8.04 just installed.  I am a newbie to linux, about two weeks. I have a wired network and am trying to setup Ubuntu to be able to see the windows network. 

I have a windows network icon on my Ubuntu pc but can't see my windows pc.I also can't see Ubuntu on my windows pc. 

Due to my inexperience in linux can anyone point me in the right direction or program that will help me with this?

Rusty

---

### Post by pytheas22 on 2008-10-21
You need to install samba, which allows you to communicate using the Windows file-sharing protocol.  There are instructions [here]("http://www.jonathanmoeller.com/screed/?p=181") that should work, or just google 'ubuntu samba' and you'll find dozens of other tutorials.

Also, as the first comment to that blog post that I linked to says, you actually don't have to do any manual configuration to get samba working on Ubuntu 8.04.  You can simply right-click on a folder that you want to share on the network, click "Sharing Options" and go from there--it should automatically prompt you to install samba if it's not already there, and do all the other configuration for you.

If you want to set up samba with a password, however, I think you need to edit some configuration files by hand, as that blog explains.

---

