---
title: "Need help with wireless internet-Ubuntu 10.04"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Tyler Kessler on 2010-08-30
I have a Toshiba Satellite A505-S6035 and recently installed Ubuntu 10.04.  I'm running a dual-OS with Windows 7. After some work, I have everything except my wireless internet working. I tried using ndiswrapper for the driver, which says it is correctly installed, but where I can check my connections, I don't even have the option for a wireless network. :confused:

Also, I am extremely new to Ubuntu (my first experience with it was three days ago), so please be as descriptive as possible.

Thank you in advance for your help.

---

### Post by sgosnell on 2010-08-30
Ndiswrapper is unnecessary, the standard network manager works.  I don't know what you've done to change things, so it's difficult to know where to start.  You normally access the network manager through the icon in the top panel, or from System/Preferences/Network Connections.

---

### Post by andrewthomas on 2010-08-30
Check out this post for **Realtek RTL8191SE**

[http://ubuntuforums.org/showpost.php?p=8524632&postcount=7](http://ubuntuforums.org/showpost.php?p=8524632&postcount=7)

---

### Post by NUboon2Age on 2010-08-30
i found that installing ndiswrapper with ndisgtk (available via synaptic from repositories and shows up on menu as "Windows wireless drivers" was the least painful and most effective way to correctly install it in my newbieness.  For some reason reinstalling modemmanager jiggled something that needed jiggling and got the whole thing working.  See my signature for the all gui way to do wireless -- maybe something there will help.

---

### Post by sgosnell on 2010-08-30
On my wife's Satellite, wireless just worked after the install.  I didn't do any tweaking, wiggling, jiggling, or anything else, it just worked.

---

### Post by gabriel8a2002 on 2010-08-31
Have you tried going to hardware drivers in System-->Administration-->Hardware drivers and tried installing the drivers through there?  Im sure that realtek cards you need proprietary software in ubuntu.  I may be wrong, but it should come out there, even video cards hardware acceleration need installation through there.  Might want to take a look at that  :KS

---

### Post by Tyler Kessler on 2010-08-31
Unfortunately, I tried all of your suggestions before posting. Just in case I had messed up, I tried them again to no avail.

---

