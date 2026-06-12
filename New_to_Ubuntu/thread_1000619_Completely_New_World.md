---
title: "Completely New World"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Yukazi on 2008-12-03
[FONT="Tahoma"][SIZE="2"]I have been a member of the Windows community for quite some time now (10 of my 20 years on this earth) and I finally decided to make the switch over to Linux.

After some searching I came across Ubuntu and decided I would go for it. I installed a dual-boot for Windows XP and Xubuntu 8.10 to be sure I could get everything working before jumping in headfirst.

After the install I realized that the majority of what I would need required an internet connection for Synaptic but my wireless was not working. I looked around and found I needed ndiswrapper but I could never get it to work right. I've come across other programs that, despite following the instructions provided, would not configure properly and thus couldn't be installed.

I have a feeling that I may just be missing some commands but it may just be user error. As I've said, I am completely new to Linux so I could just be messing something up along the way. I've used the command (I forget the exact name, but it is supposed to list your wireless card as well as your USB hubs, etc) to see what is going on but my Wireless card isn't mentioned.

Right now I am on the Windows side to post this and to see if I can find any information about getting the internet to work on the Linux side.

HP Pavillion zd7000
Broadcom 802.11b/g WLAN (Broadcom BCM94306MPSG)

Any help would be greatly appreciated even if just a guess.[/SIZE][/FONT]

---

### Post by SunnyRabbiera on 2008-12-03
I suggest using this to pick up Ndiswrapper and its dependencies and perhaps you can burn them to a CD:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Tip: search for packages for your version of Ubuntu, there are pulldown menus that are easy enough to understand.
I also suggest downloading and installing ndisgtk

---

### Post by mapes12 on 2008-12-03
I have a Thinkpad T23 with a Linksys wifi device which needed a windoze driver via ndiswrapper to work. I got it to work (eventually) but the connection became slower and slower. So, I decided to get myself a linux supported PCMCIA adapter instead. It cost me £10 for the new card but it works out of the box and I haven't looked back since. I got the Comtrend RT2500 from this site: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by hyper_ch on 2008-12-03
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Michael.Godawski on 2008-12-03
The easiest way to check your network status in Linux is to use the terminal:

```
iwconfig
ifconfig
sudo iwlist scan
lspci
sudo lshw -C network
```

Run these commands and post the result here. Might be some trouble if you do not have any internet connection on the Xubuntu machine.

I also recommend to buy another wlan card. In the past I had a broadcom card too. But they are no joy with linux. To save you many hours of work buy yourself a fully compatible wlan card.

Also have a look at these how-tos:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

---

