---
title: "Server with a desktop GUI"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by tamays on 2007-08-06
Could somebody please direct me to documentation that would instruct me as to how I can install Ubuntu Server 7.04 with a GUI Desktop in a step by step manner?

---

### Post by Nythain on 2007-08-06
its easy... install server... then make sure you enable all the repos in /etc/apt/sources.list... then sudo aptitude install <gui package of preference, eg ubuntu-desktop (or whatever the base gnome package is) kubuntu-desktop (or kde-base or whatever its called)>

basically its that easy

---

### Post by kerry_s on 2007-08-06
just grab the server iso> [http://mirrors.cs.wmich.edu/ubuntu-releases/feisty/ubuntu-7.04-server-i386.iso](http://mirrors.cs.wmich.edu/ubuntu-releases/feisty/ubuntu-7.04-server-i386.iso)

then burn it as a image at 4x
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

once you have it installed, you just apt-get what you need, server's are not really suppose to have a gui, so i suggest you just get something light and fast.

sudo apt-get install xorg gdm synaptic jwm menu mc
reboot(ctrl+alt+delete)
select jwm in the session menu and log in

this will give you a super light gui install, you can use synaptic to install/remove stuff graphically, mc is a file manager, editor, all around fantastic tool that can be used with or without the gui.

---

### Post by petit.padavoine on 2007-08-06
Install the Ubuntu server edition.

Then install the xubuntu-desktop package. It's lightweight, so it won't hog to much of your server's resources, but you'll get all the functionality of a standard desktop computer.

---

