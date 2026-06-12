---
title: "How to set up Netzero in Ubuntu"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by zieglerj on 2008-08-01
I'm working on setting up Ubuntu for a friend who uses Netzero dial-up. I've got the modem configured and can access his netzero act. through wvdial but they wont let him access anything else online without using the Netzero software to connect. I've tried downloading their Linspire software but it seems to be hopelessly incompatible with Ubuntu. (Linspire, Ha! Linux for sale :P)
Does anyone out there know of a way to get around the using Netzero's software issue? Or even a way to install the Linspire software.

---

### Post by ecuajosh on 2008-12-06
i have installed this software on ubuntu 8.10
just  double click on the file and drag the file netzero.dev in the window, out to the desktop.
go to a terminal make sure you are in the same path,otherwise type:
"cd Desktop"(don't ignore the capital letters)
then
"sudo dpkg -i netzero.deb"
this should have installed al of the file in your system but if im not wrong it isntalled a file on the folder on root
so you need to browse to root\Desktop\
and you will see a netzero file and you need to drag it to your desktop.
now i make it run. (i just don't get the software to find my modem). 
i hope you have luck.

---

### Post by daqron on 2010-12-09
**Good:** Yes, you can get the free version of netzero to work on Ubuntu.
**Bad:** It requires Netzero's Java runtime, it's not command-line friendly, and it requires root privs.

I didn't really need netzero but I thought it would be cool to have a failsafe in case the zombies attack and the power goes out. As I'm spending my final few hours huddled in the corner with my laptop and a dial-up connection, waiting for my brains to be eaten, I will look back fondly on these times of configuring netzero on Ubuntu.

Thanks to [this post]("http://www.linuxquestions.org/questions/slackware-14/netzero-628659/") it's pretty easy. Allow me to summarize the steps for Ubuntu users (my netzero adventure was on xubuntu 10.10 but I suspect it's probably about the same all around):

[SIZE="2"]**Install & Setup**[/SIZE][LIST]
[*]Setup your modem; make sure /dev/modem is linked to it in rc.local
[*]Install Java Runtime Environment from Ubuntu Software Center.
[*]Get netzero.deb [from here]("http://dl.netzero.net/pub/netzero/linux/lindows/netzero.deb") and install it like so:
```
sudo dpkg -i netzero.deb
```
[*]sudo /etc/resolv.conf and add these lines:
```
nameserver 64.136.52.73
nameserver 64.136.44.73
```
[*]Change permissions on /etc/resolv.conf:
```
sudo chmod 644 /etc/resolv.conf
```
[/LIST]

[SIZE="2"]**Run the NetZero dialer**[/SIZE]
```
sudo /opt/nzclient/runclient.sh
```

Or if you want to dispense with the sudo, add something like this to [/etc/sudoers]("http://ubuntuforums.org/showthread.php?t=1132821"):
```
yourusername localhost = /opt/nzclient/runclient.sh
```

---

### Post by notiones on 2011-04-27
Thanks. It worked perfectly and is still relevant.

---

