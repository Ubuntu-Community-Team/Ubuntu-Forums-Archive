---
title: "Netwok card compatibility"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Yankeefan984 on 2010-01-19
So I decided to try ubuntu after my pc got anvirus.  Everything went great during the instalation, however, I cannot connect to the Internet.  I have a USB zonet zew2546.  Does anyone have any advice on how to fix this problem?

(I known that on the internet someone's going to ask a stupid question so I'll answer it now, I used an iPod to get on.)

---

### Post by Yankeefan984 on 2010-01-19
Can someone please answer this?

---

### Post by papuccino1 on 2010-01-19
Please give us some facts, first:

> 
1. What version of Ubuntu are you using?
2. What motherboard do you have?
3. Give us the exact make/model of your wireless card/adapter.


---

### Post by Yankeefan984 on 2010-01-19
> **papuccino1 said:**
> Please give us some facts, first:

I am using version 9.10
I am using the motherboard that came on my computer (it is a Dell precision 670)
as previously stated, the adapter is a zew2546 made by zonet

---

### Post by achase79 on 2010-01-19
type "lsusb" in terminal while the wifi adapter is installed and paste results here

---

### Post by Cabs21 on 2010-01-19
Did you try hard wiring to the internet thru a LAN cable and updating your Wireless drivers in the Hardware Drivers menu?  9 times out of 10 that is why you cant get a wireless card to work on ubuntu.  Soon as you do this and reboot it should work.  You need to be connected to the internet somehow (LAN) and you need to pick the correct drivers.

---

### Post by achase79 on 2010-01-19
you may use ndiswrapper and the winxp driver to get this to work it uses the Realtek RTL8191SU chipset

---

### Post by achase79 on 2010-01-19
this may also work:

You need to download and install the native Linux Realtek 8192Se driver from the following location


[http://www.mediafire.com/?zxgmyniz2hd](http://www.mediafire.com/?zxgmyniz2hd)


These drivers work with Jaunty's 2.6.28 kernels


Youl'll need to compile the drivers, so make sure you do:

sudo apt-get install build-essential

This will ensure you have the right tools installed for compilation.

---

### Post by cebesius on 2010-02-03
This post removed due to wrong information.

---

### Post by Joe Awsome on 2010-02-12
thanks achase79 for the advise, it recognized my wireless network but when using wifi radar on xubuntu it just keeps searching gor an IP adress forever. Any sugestions?;)

---

### Post by MooPi on 2010-02-12
When all else fails I can say with certainty that this adapter works. [http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022)

---

### Post by Joe Awsome on 2010-02-13
sorry buddy, I'm using an n-network, thats why I got the Zonet one. But your help is appreciated ;). BTW, I'm running Xubuntu 9.10 on an old compaq deskpro EX (pentium 3 at 700megahertz, 371mb ram, and a 10gig hdd). I used the terminal code mentioned b4 after I downloaded and extracted the driver. Now how to install the blasted driver? BTW, I can detect wireless networks with it, but as mentioned b4, it seaches for the IP adress infinitely

---

### Post by Joe Awsome on 2010-02-18
I have gotten ndiswrapper to us my usb stick, but i can't connect to my network because it doesn't like passwords, any ideas? And for those of u who care, i upgraded a little bit, got a used mobo/cpu and ram for free, now running pentium 3 at 933Mhz, 512mb of ram and ubuntu now recognizes my sound card at boot!

---

### Post by achase79 on 2010-02-18
try the different code types (passcode, password, hex, etc.)

---

### Post by coolbrook on 2010-03-11
How did this work out, Joe?

---

### Post by coolbrook on 2010-03-16
```
net8192su : driver installed
	device (0BDA:8172) present (alternate driver: r8192s_usb)
```

I've got the **ZEW2546** working (albeit with a 802.11g router.)

I'm using ndiswrapper and the [net8192su.inf](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) driver from Realtek.

I go into WICD's preferences and it works with the 'dhclient' option and 'wext' instead of 'ndiswrapper' in the pull down menu.

---

### Post by Joe Awsome on 2010-03-26
I was able to get ndiswraper to work with it using the xp driver, but I still have the password bug, I'm using a 10 digit hexcode (64bit) on my new linksys router (G+ mimo). Would using the native linux driver fix that bug? (BTW I upgraded once more, someone at my school threw out an hp d530(full size) computer with a 2.8Ghz pentium 4 in it, put in my hdd, disk driver and a 1/2gig ddr ram and it fired right up. I know have usb 2.0 ports for this thing!!)
I'm going to do a fresh install on my new (to me) 160gig ide hdd with lubuntu beta. It has the network manager aplet on it, (I think thats the buggy program) and was planing to install wicd on it to see if that worked. Any ideas?

---

