---
title: "Will rt61 card work with 7.04?"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by ubuntukid on 2007-04-12
As far as I'm aware the rt61 driver was included in ubuntu 6.10 but it was broken and required a fair amount of work to get it working properly. Has this been fixed for ubuntu 7.04 so that my card will work without extensive editing of files?

---

### Post by Valstorm2323 on 2007-04-13
Well I hope by god hey have because I'm about to resort to last option.
Take wireless card from comp A and put into comp B. Hoping that the older card would be easily accepted by ubuntu. 

I've done 80% of the work now so it's just a matter of saving settings... aye.

---

### Post by huygens on 2007-04-14
Yes and no :-)
The problem with this ralink chipset is that it is not 100% compatible with NetworkManager (see [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware) about unsupported hardware and the rt2x00).
In Feisty, the rt2x00 is now used for your (and actually mine too) card and this is no more broken as it was in Ubuntu 6.10. However, due to the compatibility issue with Network Manager (NM), you can only connect using NM to unencrypted or WEP wireless network. No WPA or WPA2 is possible without playing with configuration files.

Actually now it is easier as we can follow the guides for Ubuntu 6.10, but the driver is working properly ;-) so it is only the last part, which is configuring the WPA, that should be performed. Also remember to deactivate (uninstall/remove) NM because it will interfere with your configuration.

---

### Post by Valstorm2323 on 2007-04-15
I upgraded to fiesty thanks to my ethernet cable. Took an hour but after updating to Feisty, my wireless actually works NOW!!

---

### Post by freshman on 2007-04-17
Hi,
I have Ralink rt61 wireless card:
```

# lspci
...
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

#ifconfig
...
ra0       Link encap:Ethernet  HWaddr 00:08:A1:AA:05:F8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56644 (55.3 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 

```

Does it mean that WLAN card is fully supported? How I can configure it to my network (WEP)?

Thanks in advance!

---

### Post by huygens on 2007-04-17
If you are using Feisty Fawn, there is not much things you have to do. If you look under Gnome in the upper right part of your screen next to the clock. You will have a small icon for the network. Click with your left mouse button on it, you should see you Wi-Fi network, simply select it. A screen will appear which asks you for your login and password. It should have detected automatically the type of encryption, but give it a look because sometimes it is mistaken.
Note: this is working as simple if you have WEP or unencrypted network. If you have WPA or WPA2, it will not work. You have to follow the tutorials on the forums.

To answer your question about the output of ifconfig. It seems that the driver is correctly installed, but no network connection is established: you do not have an IP address set. Check again this output once you will have follow the above step, just to see the difference. ;-)

---

### Post by huygens on 2007-04-17
for a tutorial (I mention them, but forgot to point to one...), you could use this one: [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

Simply start at step 6, and skip step 7 & 8.
You should also skip the steps regarding "add broken module to blacklist", "add new module to module autostart", "and create an alias", all three are located after the message "Now everything SHOULD work" :-)

:)

---

### Post by whayong on 2007-04-18
Well that sucks, kinda.  I was looking forward to Feisty, but I may end up with Edgy so I don't have to mess around and configure my wireless setting anymore.  

Seriously though, who still uses WEP these days?

---

### Post by jhpope on 2007-04-19
don't have the rt61sta.dat file...what should i do

---

### Post by lukaszJarochowski on 2007-04-22
I have rt61 from ralink working in WPA enabled network, to get it working you should follow this howto:
[http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693")

---

### Post by Ynem on 2007-04-22
system freezes after 6 minutes of surfing with my dwl-g630 (rt61 card)

this is the system log:
Apr 21 12:44:29 LaptopYen2 NetworkManager: <information>^IUpdating allowed wireless network lists.
Apr 21 12:44:29 LaptopYen2 NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

suggestions?

Y

---

### Post by leibowitz on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91192](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91192) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				yep, blacklist the rt61 kernel module, recompile your kernel, or try with a newer version of the module.

---

### Post by Ynem on 2007-04-22
thanks for the advice, but i'm not shure wether your talking about dismantling a nuclear weapon or my wifi card :) I saw the website you were referring to and I'll try to figure it out Ok, it looks less complicated than the  installation in edgy, but I think anyone who uses ubuntu for the first time gives up on it immediatly.

Y

---

### Post by leibowitz on 2007-04-22
Sure. That's why I was happy to found that bug one month before the official release of Ubuntu 7.04. And I hoped it would be fixed for the release, but no one have reacted to the bugreport I did. I even reported a bug in the upstream project bugzilla (rt2x00).

I was very sick of this one week ago, when the release was going to be done with this bug in it.

And I feel as I didn't do the right thing somehow. But can't figure how I should have report this bug, or to who.

---

