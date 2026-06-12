---
title: "Sony Ericsson MD300 usb modem HSPDA not supported?"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by mosm on 2008-07-09
Dears,


I tried install the MD300 modem during all last week and nothing.

I used udev rules (normally is mounted with usb_storage):

ACTION=="add", BUS=="usb", ATTRS{product}=="Sony Ericsson MD300" , GROUP="marcelo", MODE="0660" , SYMLINK+="sony" , RUN:="/sbin/modprobe usbserial vendor=0×0fce  product=0xd0cf"


Its create a /dev/sony and run the usbserial module.

But in the gnome-ppp with all settings..DONT WORKING!!!

anybody help me? :confused:

---

### Post by mosm on 2008-07-10
No help? ](*,)

---

### Post by Sealbhach on 2008-07-10
Make the Gnome-PPP dock in the notification area. Then look at the connection log - it might give you some clues.

Also, if you haven't already, try ticking "Ingnore Terminal Strings" (stupid mode).



.

---

### Post by mosm on 2008-07-10
nothing!!


Other idea?


:(

---

### Post by Sealbhach on 2008-07-10
What does the connection log say?

It might be simply a problems with DNS servers.

Don't give up - getting Ubuntu to find the modem is the hardest part.


.

---

### Post by hardskinone on 2008-07-13
Hi, 
 I have an MD300. How exactly add these information to udev?

Thanks

> **mosm said:**
> 
ACTION=="add", BUS=="usb", ATTRS{product}=="Sony Ericsson MD300" , GROUP="marcelo", MODE="0660" , SYMLINK+="sony" , RUN:="/sbin/modprobe usbserial vendor=0×0fce  product=0xd0cf"


---

### Post by mosm on 2008-07-14
Simple:

Create the file 10-wireles.rules in the /etc/udev/rules/

After:

/etc/init.d/udev restart


But not work for me!!!

remember: In the GROUP="marcelo" change for your nickname in your system. ex: 

ACTION=="add", BUS=="usb", ATTRS{product}=="Sony Ericsson MD300" , GROUP="hardskinone", MODE="0660" , SYMLINK+="sony" , RUN:="/sbin/modprobe usbserial vendor=0×0fce product=0xd0cf"



Please!!! The Question of 1 milion dollar is:

Modem MD300 work in the GNU/Linux ?? :guitar:

---

### Post by mosm on 2008-07-14
> **Sealbhach said:**
> What does the connection log say?

It might be simply a problems with DNS servers.

Don't give up - getting Ubuntu to find the modem is the hardest part.


.

It isnt problem with DNS, remember.... NOT CONNECT!!

The Symbolic device isnt setting for the modem md300

I will post my log event!!

---

### Post by hardskinone on 2008-07-14
Thanks for the reply. Now udev creates /dev/sony but looks like to be a simple symlink to /dev/sdb1 and seems gnome-ppp doesn't like to talk to an USB stick...

I will investigate this device in next days...

---

### Post by mosm on 2008-07-17
any news ??

MD300 still not work in GNU/LINUX?

](*,)

---

### Post by hardskinone on 2008-07-24
mosm,
I used your udev rule. It looks like to create a mere link /dev/sony to /dev/sdb1

I think it never gonna work in this way. The kernel have to recognize the usb key as a modem (a character device, I suppose). This simple do not happen.

As a side note the key does not works even with Xandros installed on EEE900.

If I take the sub-human who created this usb modem... :twisted:

---

### Post by hardskinone on 2008-07-25
After some nights fighting with udev, wdial.conf and usbserial I surrender. I just change the md300 with an "old" huawei e169 and it's work quite flawless (just search for it in the forum).

---

### Post by pretto on 2008-09-19
solved here: [http://laudecioliveira.org/blog/?p=70](http://laudecioliveira.org/blog/?p=70) (pt_BR)

---

### Post by danielcaraj on 2009-01-17
Sony Ericsson does not support GNU/Linux:(

---

### Post by barkik on 2009-03-22
I tried this driver [http://www.niclabs.cl/entel/MD300/UbuntuDebian%3DENG.html]("http://www.niclabs.cl/entel/MD300/UbuntuDebian%3DENG.html"), and it works after installing gnome-ppp.
If there is some trouble try to find out how to run pppd for a non-root user.

---

### Post by ipmaks on 2009-03-26
Hi! 

I have an idea. May be it is connected with switched off radio-transmitter on the MD300 modem.

Try to switch it on from the windows utility for everytime or find additional AT commnad to switch on from Linux.

---

### Post by fmercerat on 2009-07-01
The AT command is AT+CFUN=5 for HDMSA 4 for EDGE and 1 for automatic

---

