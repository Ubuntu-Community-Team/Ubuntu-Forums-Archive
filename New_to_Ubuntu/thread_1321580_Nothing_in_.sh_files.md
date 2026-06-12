---
title: "Nothing in .sh files"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Athenite on 2009-11-10
I'm relatively new to Ubuntu, I only have a little experience from the past few months. I recently installed VirtualBox to run Windows 7 from. I ran into the problem that my USB ports didn't seem to work, so I went back to my motto 'Just google it!'. So I found a tutorial

[http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/](http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/)

Old tutorial, I know, but it's still somewhat relevant. Now here comes my problem: I open the .sh file and there's nothing there! It's frustrating, as I'm so close to the solution yet so far away.

When I open the .sh file there is absolutely nothing. This has happened frequently before, and I have googled for solutions to no avail. Please help

---

### Post by Cuddles McKitten on 2009-11-10
I'm not entirely sure by what you mean by nothing's in the file.  Are they empty from the start (don't exist) or are you editing them and they aren't getting changed?


If the files in your /etc/init.d directory don't exist, that means you don't have that package installed and should look for it on synaptic.
If you're editing them and it's not saving the changes, are you editing the files as root?  Stuff in the /etc directory can't be saved by your non-superuser.

---

### Post by Athenite on 2009-11-10
I open them fine, but then there's nothing in them. They're completely blank. No writing, no nothing. They must exist since I can open them, or am I being stupid?

---

### Post by Rayve on 2009-11-10
Can you please post what you are entering?  Oftentimes if you just mistype a file name, you're creating a blank file instead of opening the one you intend.

---

### Post by Cuddles McKitten on 2009-11-10
> **Athenite said:**
> I open them fine, but then there's nothing in them. They're completely blank. No writing, no nothing. They must exist since I can open them, or am I being stupid?

Linux doesn't ask you if you want to create a file when you open an empty one.  You probably just need to install those packages.  The one your link provides: **mountdevsubfs doesn't seem to be in synaptic though.****[SIZE=1][/SIZE]**

---

### Post by Athenite on 2009-11-10
root@anja-laptop:~# sudo gedit /etc/init.d/mountdevsubfs.sh

---

### Post by Athenite on 2009-11-10
I'm confused. If it's not in synpatic, does that mean the tutorial is too outdated?

---

### Post by Rayve on 2009-11-10
It's possible that the package is no longer in the repositories.  Maybe something here will help?

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Note at the top where it says USB support is only available for the non-free version.

Google also suggested this one, not sure about the source though (I'd try the ubuntu one above, first, and as always, research a command someone tells you to do if you aren't sure what it means):

[http://linuxmini.blogspot.com/2007/10/virtualbox-usb-setting-on-ubuntu-and.html](http://linuxmini.blogspot.com/2007/10/virtualbox-usb-setting-on-ubuntu-and.html)

Good luck!

---

### Post by kio_http on 2009-11-10
If it doesn't work. Just open terminal and type

sh /path/to/file/file.sh

---

