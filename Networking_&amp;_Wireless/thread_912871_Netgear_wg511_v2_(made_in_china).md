---
title: "Netgear wg511 v2 (made in china)"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Menno van Holsteijn on 2008-09-07
Hello everyone,

I've installed xubuntu on a old laptop with a wireless card from netgear. This card doesn't seem to be working so i've got no connection to the internet. how can i get this to work? I already checked a lot of forums but all the solutions i found required a internet connection on the laptop. I do have a connection on my other pc.

---

### Post by mcld on 2008-09-07
Hi - you'll need to use one of those solutions which "require an internet connection", but you have to do a bit of copying from one PC to another.

For example, if you find a solution which tells you to install a piece of software (let's call it "superthing") using synaptic, then the normal way to install "superthing" is for synaptic to download it. But instead, if you search the web (using your other computer) you should be able to find a trustworthy source where you can download the package file which will be called something like "superthing.deb". Make sure you download a file that is intended for ubuntu. 

Then copy the file onto a USB stick or a CD, and transfer it to your xubuntu box. You can then install the package using a command similar to

  sudo dpkg -i superthing.deb

If you manage to get your wireless working, please post a message here to tell us how you did it! I'm having a very similar problem to you, on a laptop with a Netgear WG511U card.

---

### Post by Menno van Holsteijn on 2008-09-07
I did get the card to be regognized by the computer using another forum. Using ndiswrapper I was able too install the correct driver. 

open a terminal in the folder where the drivers are located

log in as root

ndiswrapper -i wg511v2.inf
ndiswrapper -i wg511v2.sys

after that I did the following:

ndiswrapper -l

I got the following response:

Installed drivers:
wg511v2           driver installed, hardware present
wg511v2.sys       invalid driver!

Then:

modprobe ndiswrapper

Then:

dmesg

This was the response

.....
.....
ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
usbcore: registered new interface driver ndiswrapper
.....
.....

Still no green light on the device itself.

Please help me further with this

kind regards menno

---

### Post by djfhryg on 2010-05-30
I think Netgear wg511 v2 ([made in china]("http://www.madeinchinab2b.com/")) is not work.

---

