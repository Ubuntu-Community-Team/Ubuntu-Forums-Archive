---
title: "Need wifi help with NetworkManager"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by psyoptic on 2009-01-26
Whenever I boot into my Ubuntu partition, I keep getting a prompt asking to enter a keyring password in order to connect to my wireless network. I tried following the instructions on this site ([http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)) to automatically unlock the pam keyring connect to the network but gedit won't allow me to save my changes to /etc/pam.d/gdm

The other thing I noticed is that it can sometimes take a while (5-7) to connect to my wifi network on Ubuntu, while I'm able to connect to it always starts instantly on my Windows XP partition. I'm also asked to type in my wifi security key several times over. Is this common and is there any way to speed it up so that it connects a lot faster? It will connect pretty fast some of the time but there are a lot of times where it takes so long. 

Any help on these issues would be greatly appreciated!

---

### Post by LostMagix on 2009-01-26
You made sure your running gedit as a sudo super-user right

---

### Post by psyoptic on 2009-01-26
> **LostMagix said:**
> You made sure your running gedit as a sudo super-user right

I don't think so (didn't type sudo apt anywhere). Can you show me how to?

---

### Post by Crafty Kisses on 2009-01-26
Try to run the following:
```
sudo /etc/pam.d/gdm
```
Then see if you can make changes to the file.

---

### Post by skern03 on 2009-01-26
> **psyoptic said:**
> Whenever I boot into my Ubuntu partition, I keep getting a prompt asking to enter a keyring password in order to connect to my wireless network. I tried following the instructions on this site ([http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)) to automatically unlock the pam keyring connect to the network but gedit won't allow me to save my changes to /etc/pam.d/gdm

The other thing I noticed is that it can sometimes take a while (5-7) to connect to my wifi network on Ubuntu, while I'm able to connect to it always starts instantly on my Windows XP partition. I'm also asked to type in my wifi security key several times over. Is this common and is there any way to speed it up so that it connects a lot faster? It will connect pretty fast some of the time but there are a lot of times where it takes so long. 

Any help on these issues would be greatly appreciated!

What sort of security are you using on your wireless router, and what router? I'm not experiencing any of those issues.

I'm using a Linksys WRT54G. I set wireless mode to Mixed, Security mode to WPA Personal, WPA Algorithm to TKIP.

What version of Ubuntu are you using? I've had virtually no difficulty with wireless since 7.x. You shouldn't have to edit the config keyring file manually. Try accessing it from the Network Manager (System, Preferences, Network Manager). In U8.10, there's a tab for Wireless, and you can edit your wireless set up there. From your description, it sounds like there's some sort of mismatch between your wireless router and your wireless net config on your PC. Make sure your settings on the router and on the PC match, i.e., if you set the router to WPA Personal, then set the Wireless config on the PC the same.

If the above suggestion doesn't fix it, then open a terminal (Applications, Accessories, Terminal), and enter the following line:
```
sudo lshw -c network

```
Then copy and paste the output into a reply.

I apologize if you already know this stuff - it's hard to tell how much people know, and better to give explicit instructions rather than make people ask and wait. JMHO...:)

---

### Post by abyssius on 2009-01-26
> **skern03 said:**
> What sort of security are you using on your wireless router, and what router? I'm not experiencing any of those issues.

I'm using a Linksys WRT54G. I set wireless mode to Mixed, Security mode to WPA Personal, WPA Algorithm to TKIP.

What version of Ubuntu are you using? I've had virtually no difficulty with wireless since 7.x. You shouldn't have to edit the config keyring file manually. Try accessing it from the Network Manager (System, Preferences, Network Manager). In U8.10, there's a tab for Wireless, and you can edit your wireless set up there. From your description, it sounds like there's some sort of mismatch between your wireless router and your wireless net config on your PC. Make sure your settings on the router and on the PC match, i.e., if you set the router to WPA Personal, then set the Wireless config on the PC the same.

If the above suggestion doesn't fix it, then open a terminal (Applications, Accessories, Terminal), and enter the following line:
```
sudo lshw -c network

```
Then copy and paste the output into a reply.

I apologize if you already know this stuff - it's hard to tell how much people know, and better to give explicit instructions rather than make people ask and wait. JMHO...:)

You may want to capitalize the -c part like this ...

```
sudo lshw -C network
```

---

### Post by skern03 on 2009-01-26
> **abyssius said:**
> You may want to capitalize the -c part...

Love your byline - *Axis Bold as Love* is literally within arm's reach as I type!!!

Anyway, like you, I've always seen it with a capital "C", but if you run *lshw --help*, you get the following output (this is just the pertinent part):
```
options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'

```

So unless I'm misreading this, upper and lower case makes no difference and using lower case "c" seems to work just fine!

---

### Post by psyoptic on 2009-01-27
> **Codename said:**
> Try to run the following:
```
sudo /etc/pam.d/gdm
```
Then see if you can make changes to the file.

That didn't seem to work. I got sudo: /etc/pam.d/gdm: command not found



> **skern03 said:**
> What sort of security are you using on your wireless router, and what router? I'm not experiencing any of those issues.

I'm using a Linksys WRT54G. I set wireless mode to Mixed, Security mode to WPA Personal, WPA Algorithm to TKIP.

What version of Ubuntu are you using? I've had virtually no difficulty with wireless since 7.x. You shouldn't have to edit the config keyring file manually. Try accessing it from the Network Manager (System, Preferences, Network Manager). In U8.10, there's a tab for Wireless, and you can edit your wireless set up there. From your description, it sounds like there's some sort of mismatch between your wireless router and your wireless net config on your PC. Make sure your settings on the router and on the PC match, i.e., if you set the router to WPA Personal, then set the Wireless config on the PC the same.

If the above suggestion doesn't fix it, then open a terminal (Applications, Accessories, Terminal), and enter the following line:
```
sudo lshw -c network

```
Then copy and paste the output into a reply.

I apologize if you already know this stuff - it's hard to tell how much people know, and better to give explicit instructions rather than make people ask and wait. JMHO...:)

I think I'm using a WRT54G as well. My network adapter is a WMP54G and my wireless encryption is WEP. I'm using Intrepid 8.10 and have tried setting the connection rules manually in the wireless tab of Network Manager. 

Screenshots:
[IMG]http://i44.tinypic.com/i5dxrt.png[/IMG]
[IMG]http://i39.tinypic.com/25ti68m.png[/IMG]
[IMG]http://i43.tinypic.com/6536lx.png[/IMG]


And here are my results from lshw -c network.
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:7d:7d:42:ed
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:e5:27:ac:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.104 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:2f:bb:8f:7f:2f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by psyoptic on 2009-01-27
Bump.

---

### Post by xbalboa on 2009-01-27
NetworkManager booted slowly on my setup (Hardy on a Dell XPS1530 with Vista dual-boot) and was inconsistent. After battling with it for about 6 mos, I switched to wicd and now I connect to the internet immediately on bootup (Vista takes almost 3 minutes!).

---

### Post by skern03 on 2009-01-27
> **psyoptic said:**
> I think I'm using a WRT54G as well. My network adapter is a WMP54G and my wireless encryption is WEP. I'm using Intrepid 8.10 and have tried setting the connection rules manually in the wireless tab of Network Manager. 


Try switching to WPA. I used WEP, and it worked on an ancient laptop running Ubuntu 7.x, but when I purchased a Mac Book for my daughter (college graduation present), it puked. I switched to WPA and have no problems at all. The ancient laptop died, and I now have a Dell 8600, approx 4.5 years old running Ubuntu 8.10, and it connects with no problems.

WEP codes are a pain in the butt, IMHO... And supposedly, it's less secure than WPA Personal.

BTW, you probably know this already, but you can access your router via this URL:
[http://192.168.1.1](http://192.168.1.1)
Sometimes it's 0.1, or 1.0, but usually, it's 1.1.

Linksys will display the Administration panel in your browser, and you can see how wireless is set up, and play around with the settings easily.

Also, sometimes the router goes out to lunch - not often, but the only cure is to turn it off for a full minute, then back on.

---

### Post by psyoptic on 2009-01-27
> **skern03 said:**
> Try switching to WPA. I used WEP, and it worked on an ancient laptop running Ubuntu 7.x, but when I purchased a Mac Book for my daughter (college graduation present), it puked. I switched to WPA and have no problems at all. The ancient laptop died, and I now have a Dell 8600, approx 4.5 years old running Ubuntu 8.10, and it connects with no problems.

WEP codes are a pain in the butt, IMHO... And supposedly, it's less secure than WPA Personal.

BTW, you probably know this already, but you can access your router via this URL:
[http://192.168.1.1](http://192.168.1.1)
Sometimes it's 0.1, or 1.0, but usually, it's 1.1.

Linksys will display the Administration panel in your browser, and you can see how wireless is set up, and play around with the settings easily.

Also, sometimes the router goes out to lunch - not often, but the only cure is to turn it off for a full minute, then back on.

I'm fine with WEP for now, I'll keep that in mind though. I don't want to mess around with the router too much...I'm afraid I'll mess something up and not be able to connect at all :S

The router itself has been fine and I rarely ever dropped a connection when I'm using Windows or Ubuntu. It's just connecting to it initially when starting up on Ubuntu that's a pain.

> **xbalboa said:**
> NetworkManager booted slowly on my setup (Hardy on a Dell XPS1530 with Vista dual-boot) and was inconsistent. After battling with it for about 6 mos, I switched to wicd and now I connect to the internet immediately on bootup (Vista takes almost 3 minutes!).

Thanks for the tip! I'll try that now.

---

### Post by psyoptic on 2009-01-31
Wicd works perfectly! Now I don't have any issues with Ubuntu :D

Thanks for all the help guys. It's support like this that's helped me to stick it out with this great OS.

---

