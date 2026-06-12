---
title: "problem with iwconfig,then wlan0 and so on..really need your help!!"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by albert1905 on 2016-09-08
hey there im a new user in ubuntu, im asking here only after 3 days of looking for the solution on the web.

_**i tried **_the simple action doing iwconfig
i got:

enp0s3    no wireless extensions.

lo        no wireless extensions

_**so**_ i searched online and found out that i probably have a deeper problem cus i couldnt set up wlan0:

i did:
barak@barak-VirtualBox:~$ ifconfig wlan0 up

i got:
wlan0: ERROR while getting interface flags: No such device

another try:

i did:
barak@barak-VirtualBox:~$ ifconfig wlan0 up

i got:
wlan0: ERROR while getting interface flags: No such device

_**so**_ i searched more and i saw a solution with this command:

barak@barak-VirtualBox:~$ sudo apt-get install linux-firmware-nonfree

and i got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree

i did some more actions i dont wont to make this post to long.

my wifi card is: AC 7260 (intel), i have the latest ubuntu 16.04 i think.
im working with virtual box and my network adapter there is on bridged adapter

i know that i missing alot of details so if someone can also explain me whats im missing thatll bew great!please please please help me work it out.
thx !!!!

---

### Post by jeremy31 on 2016-09-08
Is Ubuntu a guest OS?

---

### Post by albert1905 on 2016-09-08
yes it is, my real os is windows 10

---

### Post by ajgreeny on 2016-09-08
I've not used VBox on a host with wifi so I do not really know how the bridged connection works but I presume it means you need the same wifi driver mod in your VM as you would need in a hard-metal installed OS.
Do you have the wifi drivers in the VM?

---

### Post by albert1905 on 2016-09-08
no i dont have those drivers should i download them?
i cant understand your first question, im on brigded network, i dont know is the default.
and im using wifi not ethernet cable.

edit: ihad a lil prob with the drivers, ihave a hard time to find the specific one, and i saw i need to download firmware, so i downloaded the one the is matching for my wifi card and my kernel, but i couldt paste it to the /lib/firmware.
again i dont really know what im doing so im getting loss pretty quick.

thx for ur help

---

### Post by jeremy31 on 2016-09-08
You will not be able to control the wireless from the guest OS since the wifi is on the PCI bus, if it was a USB wifi chip then you could control it from the Guest OS.  I tried VMWare on a Windows 7 machine with Ubuntu 16.04 as a guest and that is what happened.  If you booted the Ubuntu ISO directly then your PCI wireless would work as Ubuntu has supported most 7260 cards for a couple years.

You should have internet access through the virtual bridged connection that showed up as enp0s3 and you may not see wlan0 in Ubuntu 16.04 because of the new naming scheme

---

### Post by gordintoronto on 2016-09-10
You are working in a virtual machine. It has a virtual *Ethernet* device which you use to access the network. What was the full output from iwconfig?

---

