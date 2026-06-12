---
title: "networking a share"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by ttallos on 2008-02-22
I want to use ubuntu as a file server for a small company I want to set it up for them I need to have 10-20 machines all having access to a share. Will the desktop version work ok?

---

### Post by dca on 2008-02-22
As long as you install the 'samba' package from the repos it should be fine.  However, most of the servers I set up are primarily headless so when using the install media for the server edition during the course of installation it even asks you what the server will be used for 'ssh', 'sendmail', 'apache', 'samba', etc which I found nice.  Whatever you put a check in it will install the nec packages and unlock the nec ports.  Once installation complete and you reboot your server for the first time at the CLI you can always do:
 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
 
The first two lines install any missed updates, the third is what installs the actual GNOME environment and libraries...

---

### Post by ttallos on 2008-02-22
Yes I installed and configured samba.... thanks for the quick reply by the way. I set it up and have learned how to make it work for many years now. I just never had it on a medium sized network.

---

### Post by ttallos on 2008-02-22
I just noticed what you said about loading from the server disk and then after a few things loading the desktop. I never thought of that! I always just loaded the text installer method. Thanks for the extra info there. Does it matter that I loaded the desktop version?

---

### Post by notwen on 2008-02-22
Desktop version will work fine w/ Samba. =]  Some people prefer to run as few services(ie, no gui, etc desktop services) as possible when serving files to a large network ov er using a standard desktop install(gui included).

---

### Post by ttallos on 2008-02-22
Thanks you guys are great!

---

