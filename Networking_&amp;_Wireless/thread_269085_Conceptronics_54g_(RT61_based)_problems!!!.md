---
title: "Conceptronics 54g (RT61 based) problems!!!"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by bennez on 2006-10-01
Hi, I hope you can help me!!!

I've just installed ubuntu and everything seemed ok, but the wireless card didn't work.](*,) 
I tried to config from administration/networking (maybe I have to use iwconfig with root account??), the card seems to be ok, it find the wireless network, but it doensn't connect........in addiction, when I choose my card from the list, it takes almost 60s of freezing (or thinking)....I think that it's not right...


Today the miracle: it works (I don't know why....)!!! 
So I download the updates and reboot.........

....and now ubuntu crash!!! 
During the boot (I tried with both kernels, old and new one), when it show the message "networking interface", it crash........i tried to skip it with ctrl-c but it still doesn't works.
The only way to use my ubuntu is to pull off my card, but it doens't solve the problem......

I find some RT61 threads here, but it speaks about installation and some hard-to-use procedures, I am an new users!!!

So, anyone could help me??? ](*,) ](*,) ](*,) ](*,)

---

### Post by JanAre on 2006-10-01
I hope I can help you, I've just make my own Linksys rt61 based card work (using WEP) :p 

Take a look at this link : [https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?highlight=%28rt61%29]("https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?highlight=%28rt61%29")

It did the work for me.... :cool: 

In addition to this I added my card in /etc/network/interfaces to set up an static IP. And also marked out my eth0 card... (not sure if you have more than the wireless?)

If you only have the wireless card, you have to download manually on another PC and copy/paste to your Linux, instead of this :  *wget [http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)*

Info, my /etc/network/interfaces looks like this:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet static
#address 192.168.1.201
#netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
#gateway 192.168.1.1

# Linksys WMP54G
auto ra0
iface ra0 inet static
address 192.168.1.200
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


And it work auto from boot, I don't have to do anything but sitting back and relax..
Good luck!

---

### Post by JanAre on 2006-10-08
](*,)  Ok, I was a bit optimistic in my last reply... I didn't work.

I therefore continued my search for a solution and found this:

[http://ubuntuforums.org/showthread.php?t=132980]("http://ubuntuforums.org/showthread.php?t=132980")

I "mix" my earlier attempt with this on, deleted all info about ra0 in /etc/network/interfaces and it seems like it is working.  But how about default gateway? I did this : > sudo route add default gw 192.168.1.1 ra0 (the IP-adress may alter for you) and finally added the above line in */etc/init.d/rt61up*

FYI: My WLAN has now been working for several days :KS

---

