---
title: "[SOLVED] wireless/wired networking problem"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by loso on 2008-01-13
I recently bought a wireless router (linksys WRT54G), and I'm trying to set up a a wired/wireless home network, but I'm having problems.  Everything worked fine before when I was using a wired switch for all the computers, but not any more.  My set-up is as follows:

#1: computer (Ubuntu 7.10) wired to the router
#2: computer (ubuntu 7.10) wirelessly accessing router
#3: computer (Win XP) wirelessly accessing router
I'm using WPA encryption on the router, and aside from that the router's settings are all "as is" from the factory. 

at the moment, all 3 can access the internet, but the home network is all messed up.  #1 (the wired computer) can see all the computers on the network.  #2 and #3 can see each other, but not #1.  Does anyone know how I can get #2 and #3 to see #1?

---

### Post by amo-ej1 on 2008-01-14
How do you define 'see'. Have you tried to ping in all directions ?

---

### Post by Hightide on 2008-01-14
can you give more information on your setup? are you using usb/cards what type?

i dont know if this will help
[http://ubuntuforums.org/showthread.php?t=87991](http://ubuntuforums.org/showthread.php?t=87991)

:)

---

### Post by loso on 2008-01-14
#2 and #3 are both dell inspiron laptops, so they both have broadcom wifi cards built-in.  I have no idea how to ping in all directions.

I was reading in the router documentation that if your devices are in ad-hoc mode, they can't communicate with wired devices.  I think this might be my problem, but I don't know how to switch from ad-hoc to infrastructure :(

---

### Post by loso on 2008-01-14
By 'see', I mean that #1 can access and change all the shared folders on #2 and #3 from the file browser.
#2 and #3 can do this to each other, but not to #1.

---

### Post by loso on 2008-01-14
my smb.conf file on #1 was missing the line that gives it a netbios name
netbios name = xxx

Thanks to everyone that tried to help, you're part of what makes ubuntu great :)

---

