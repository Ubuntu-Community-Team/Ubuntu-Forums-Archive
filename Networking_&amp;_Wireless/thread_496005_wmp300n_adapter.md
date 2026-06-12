---
title: "wmp300n adapter"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by marjanh on 2007-07-08
Hi,
I just started installing the Ubuntu for the first time and got the problems with the wireless. My card is Linksys wmp300n and got installed the ndiswrapper (the latest). Also installed the driver from the originale install. CD (folder with both sys and inf were created at home).The result is that the hardwere was not recognized at all. What driver should I use for this particular device, if tehre is any. Pls. help! 
Rgds,
Marjan

---

### Post by swarm on 2007-09-14
Same question. Did you ever figure it out?

---

### Post by jtonti1 on 2007-09-17
Check out what A-Dub  said on 2007-08-12:
[https://answers.launchpad.net/ubuntu/+question/3973]("https://answers.launchpad.net/ubuntu/+question/3973")

In summary:

Install ndiswrapper - allows use of Windows drivers
Install ndisgtk - installs drivers from Linksys disk.  You need to browse to /media/cdrom/Drivers to find the .inf file
Make ndiswrapper load at bootup by executing it with -m and also adding it to /etc/modules

This worked for me on Ubuntu  6.10 on an old Dell machine.  Needed to reboot in step 10 to get the hardware recognized.

Good luck!

---

### Post by SwedishHatFaction on 2007-11-19
I have an old Compaq with Gutsy recently installed. The tutorial worked flawlessly and now my wireless internet is up and running. Thanks guys!

---

### Post by tmattoneill on 2008-01-30
Same stories of wo for me.

NDISWRAPPER - CHECK
NDISKGTK - CHECK
DRIVERS LOADED FROM LINKSYS DISK - CHECK

Status reported from ndisgtk is driver loaded, hardware present.

However, when I go to try to configure network there is no wireless network listed. Same deal under the network menu bar icon. No dice.

I'm not sure what the issue is, since the driver seems to be there and it detects the hardware.

PLEASE help me out. I'm really looking forward to using Ubuntu with some decent speed.

M

---

### Post by chatrang on 2008-04-25
I have followed so many different tutorials to get this nic working, but it just won't work.  The card will detect networks, and I am able to put the info in, but after the two green lights come on the system locks up.  I am using the 64 bit version of Ubuntu 8.04 now, but I have not gotten it to work on any version.  It works on Suse 10, but I hate Suse so I really don't want to use that.  Any suggestions?

---

