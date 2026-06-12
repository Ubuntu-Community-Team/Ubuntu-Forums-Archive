---
title: "Netgear WG111 USB 802.11g Device Install"
date: 2005-08-05
forum: Networking &amp; Wireless
---

### Post by blakeyrat on 2005-08-05
So I've found the following instructions that I think I need to use:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

I've managed to get the ndiswrapper installed from the CD.

I've managed to copy the Windows driver from the CD to my Ubuntu home directory.

And I've typed in the command in the how to:

ndiswrapper -i ~/windows_drivers/netwg111.inf

The message I get back is:

cp: cannot stat `root/windows_drivers/netwg111.inf': No such file or directory

What does that mean?  Does that mean the install worked, or that it failed?  (The how to doesn't cover errors.)  I'm completely confused, and any help would be appreciated.

---

### Post by kgreiner on 2005-08-05
no it is basically stating that it can not find the *.inf file it the path it is looking for. Figure out where it may have been placed and then change the path to it correct location.

---

### Post by blakeyrat on 2005-08-05
No what?  No it didn't work?  How do I find the path?  I followed the example in the link as close as I could.

---

### Post by dsmudger on 2005-08-06
Have you tried typing the full path to the .inf file? 

You say you copied it to your home directory, but it looks like since you're running as root, it's now looking in root's home folder, instead of yours (since you used ~/ which means 'home folder for the *current* user').

I'm new to Ubuntu, but I imagine it will be something like /home/yourusername/ in place of ~/


(can't confirm the default home path - reading on Windows ATM, since I only just installed - now copying wifi HOWTOs off the wiki/forums via USB stick - ran into this post on the way - hope this helps!)

---

