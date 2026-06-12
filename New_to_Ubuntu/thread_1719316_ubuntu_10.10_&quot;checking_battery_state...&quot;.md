---
title: "ubuntu 10.10 &quot;checking battery state...&quot; hang"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by averyisle on 2011-04-01
I have searched the forums only to find this problem dating back a few years with no workable solutions for me.  I recently updated from 9.10 -> 10.04 ->10.10 and everything was working great except the splash screen at start up was really ugly and low resolution.  I followed all of the steps in [How to Fix the Big and Ugly Plymouth Logo in Ubuntu 10.04]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") and when I rebooted, my start up is hanging at *Checking battery state...

I've run:

sudo apt-get update
sudo apt-get install gdm
reboot

now it hangs at *Checking battery state... [ OK ]

I am really at a loss of what to do! Is there something that I need to reinstall? I'm not using any 3rd party video drivers.  It is a 1008HA Eee PC.

---

### Post by averyisle on 2011-04-01
.

---

### Post by averyisle on 2011-04-01
i ran:

sudo do-release-upgrade -d

then reran

sudo apt-get install gdm

now it clears start up but takes longer than usual the resolution is bad and the keyboard and mouse don't work. hah. does this mean that i need to totally reformat?

man i guess this is what happens at the junction of impatience and noobery...

---

### Post by averyisle on 2011-04-01
an external usb mouse works

when i go to monitors it doesn't give me any other options for resolution than 800x600 (native is 1024x768.) and it lists Monitor: Unknown in red.  Detect monitors does nothing.

Update manager says "not all updates can be installed.  run a partial upgrade to install as many updates as possible.  This can be caused by: a previous upgrade which didn't complete, problems with some of the installed software, unofficial software packages not provided by Ubuntu, normal changes of a pre-release version of Ubuntu"

other programs seem to open and run okay though everything is groggy and slow to respond.

when searching for additional drivers it says 'no proprietary drivers are in use on this system'

---

