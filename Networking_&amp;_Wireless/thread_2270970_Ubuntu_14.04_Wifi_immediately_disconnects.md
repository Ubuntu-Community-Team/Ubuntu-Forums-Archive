---
title: "Ubuntu 14.04 Wifi immediately disconnects"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by The_ERBA on 2015-03-26
Hi (this is my first thread so i could make a mistake here)
I've installed Ubuntu 14.04 to my pc (dual-boot) but it does not connect to wi fi.
when i try to connect it says connecting then it wont connect.
Please help me!
(64 bit Dell Inspiron N5110 [15R])
edit : i am on windows now.
(sorry for my bad english i am from turkey)

---

### Post by kc1di on 2015-03-26
Hello The_ERBA and welcome to Ubuntu, 

I believe the you wireless card may be a broadcom and you'll need to install the proper drivers for it. 
can you connect to a ethernet cable temporarily?

if you can go to software center select edit and then software sources, then select additional driver tab.  it will take a few minutes to scan you hardware , then should offer to let you install the correct driver for you wireless card.  install the recommended driver. then reboot , see if you wireless card will work then. 
good luck :)

---

### Post by The_ERBA on 2015-03-27
i connected my ethernet cable now and its searching.
i wish it works. Thank you for your support.

---

### Post by The_ERBA on 2015-03-27
no way, it just found the nvidia driver

[IMG]http://i.imgur.com/yY4rJTu.png[/IMG]

and this is the photo of wi fi hardware
sudo lshw -C network

and let me see you what happens when it connects

[img]http://i.imgur.com/3PfWNoA.jpg[/img]

---

### Post by kc1di on 2015-03-28
[Here's ]("http://zeroset.mnim.org/2014/04/22/unstable-wifi-connection-on-ubuntu-14-04-trusty-tahr-ctrl-event-disconnected-reason4-locally_generated1/")another page that may offer an answer.  Unfortunately I do not have that card here available to test. 

Also try running this script in a terminal and posting the output file here.
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

The command will download a script and create a file named (wireless-info.txt or wireless-info.txt.tar.gz) depending on the size of the file. It will be placed in your home folder.  it will give us detailed information about your wireless connection and may be of help in helping you.

you may also find[ this thread ]("http://ubuntuforums.org/showthread.php?t=2220377")of help.

---

### Post by goofprog on 2016-03-09
A lot of people back in the hay day loved to do static IPs.  Maybe try to make your router reserve your DHCP address to a static one.  Why?  It may help, it may not.  When a person cannot get free wireless they may just want to wedge into it.  This is just from paranoia of years of computing but it is fact.  It may just be the signal strength and it waxes and wanes because it is not reliable.

---

