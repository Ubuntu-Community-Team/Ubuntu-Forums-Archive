---
title: "Ubuntu 20.04.1 LTS, network disconnects every so often? Fix?"
date: 2021-01-18
forum: Networking &amp; Wireless
---

### Post by geekgeek4 on 2021-01-18
Hello everyone, 

I'm new to Linux and so I'm not completely sure what information I can provide to best debug this issue. Please let me know and I can provide whatever logs etc. needed. 

It appears that after a recent update, my network sometimes disconnects for about 2 minutes, and can happen twice every hour or so. It just disconnects and automatically reconnects. I notice because my zoom meetings drop. I am using Wifi, and before, I never experienced this issue and have been therefore running Ubuntu 20.04 for the past 10 months without any issues of any kind. It seems like this issue surfaced after an update about 1-2 weeks ago. 

I verified that it is not my wifi/network. While my computer is disconnected from the internet (note that the Wifi in the top right corner still shows as connected), I tried connecting using my phone and wifi, and verified that my phone was able to communicate using my Home Network's IP address to the internet while my computer was disconnected. This was to make sure it wasn't piggy backing on LTE Data. 

For this reason, I am certain it is simply the operating system. 

I'm not sure how to tackle this issue. I tried forgetting my Wifi network and then reconnecting. This did not resolve the issue. 

I've also assigned a static IP Address to my system in the Router. It has been this way for several months. 

Overall, nothing has really changed, other then the SW update.

---

### Post by chili555 on 2021-01-18
Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```
Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```
Proofread carefully, save and close the text editor.    

Is there any improvement?

---

### Post by geekgeek4 on 2021-01-18
Thank you very much. 

I removed the power management as you recommended. I also set my country code. 

To answer your question, the security tab says WPA & WPA2 Personal. On the details tab, it says it is using WPA2. The only non-mixed option I see under Security is WPA3, but that does not work with my router. 

I do only have one AP. As you mentioned, it does have 2.4 Ghz and 5 Ghz, and does band steer to always use 5G when possible. For now, I was hoping to keep it one name, but if the changes made so far do not do anything, I will certainly follow your advice. 

With that being said, my wifi configuration and overall my entire system did not change in any way. The only thing that changed is the update. I wonder if Ubuntu will release a patch of some kind. I do recognize that there are steps that I could take to address the problem, but it appears to me it is purely Ubuntu. 

Thank you again. I will report back if I keep on seeing the issue.

---

### Post by geekgeek4 on 2021-01-18
I also noticed that I had some unknown, surrounding networks saved. I don't know the password to these, but these networks had the gear icon next to them and had the option to forget the network. Of course, with no password, the connection would never be established with my neightbor's networks. However, I'm wondering if there were moments where it would try to connect to those. Perhaps, I accidentally clicked on the network but did not enter the password, and it stayed as a remembered network. In any event, I have forgotten these networks just in case they are the culprit.

---

### Post by chili555 on 2021-01-18
> To answer your question, the security tab says WPA & WPA2 Personal. On the details tab, it says it is using WPA2. I'm sorry if I wasn't clear. I am refering to settings in your router. Please check in the adminitration pages for your router; something like this:

[IMG]https://i.postimg.cc/zvHxM7NV/Screenshot-from-2021-01-18-17-09-06.png[/IMG]

---

### Post by geekgeek4 on 2021-01-18
Thank you. 

My router is WPA only. I don't have the option to set it to anything else. I have the Ubiquiti Unifi AC Lite.

---

### Post by geekgeek4 on 2021-01-18
Issue is still happening. 

Is there a way to submit feedback to Ubuntu? They should simply fix the update or revert it.

---

### Post by CelticWarrior on 2021-01-19
> [COLOR=#000000]My router is WPA only. I don't have the option to set it to anything else. I have the Ubiquiti Unifi AC Lite.[/COLOR]
That model, at least the one they're currently selling, surely supports WPA2. Any router who doesn't is hopelessly obsolete.

---

### Post by geekgeek4 on 2021-01-19
Well, my devices all use WPA2 to connect to it. However, in the settings, it shows WPA and I have no option to select differently. However, it is likely implementing WPA2, since all my devices default to that when connecting.

---

### Post by geekgeek4 on 2021-01-19
This issue is breaking my downloads, prints, Zoom sessions etc. Terrible that this update was pushed. Is there anything else that can be done in Ubuntu? Is there a way to see if the developers are looking into this? Can I submit a complaint somewhere to Ubuntu? If it won't/can't be resolved, I'll have to move to a different OS. That is pretty much the only thing that I can do then.

---

### Post by chili555 on 2021-01-19
> Is there a way to see if the developers are looking into this? Can I submit a complaint somewhere to Ubuntu? I doubt that the developers are looking into it. I doubt that they know what to look at, frankly. 

Is this an issue with the kernel? wpa-supplicant? Network Manager? The vendor supplied driver? The vendor supplied firmware, if any? 

If the driver, which driver?

Is the problem reproduceable? Is everyone who upgraded having the exact same issue? I am certainly not.

> I do only have one AP. As you mentioned, it does have 2.4 Ghz and 5 Ghz, and does band steer to always use 5G when possible. For now, I was hoping to keep it one name, but if the changes made so far do not do anything, I will certainly follow your advice.
Did you make the change?

What do the logs tell us? If we knew your driver and interface, we'd check the log for unusual activity. Please run and post:

```
lshw -C network
```Then let's check the log.

---

### Post by geekgeek4 on 2021-01-19
Thank you. I appreciate your assistance with this, especially since I would like to keep Ubuntu. 

Honestly, I did not make the change yet. But I guess I'll do it, just to rule it out. 

Here is the output: 

----START------

  *-network                 
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 78
       serial: 94:b8:6d:e0:06:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-38-generic firmware=36.77d01142.0 8265-36.ucode ip=192.168.1.248 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:86 memory:fc700000-fc701fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 26
       serial: 24:4b:fe:93:61:38
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-38-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII
       resources: irq:36 ioport:f000(size=256) memory:fc604000-fc604fff memory:fc600000-fc603fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: 52:54:00:cd:f1:8a
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: 52:54:00:cd:f1:8a
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s


----END----

Thank you again.

---

### Post by chili555 on 2021-01-19
> product: Wireless 8265 / 8275
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: [COLOR="#FF0000"]wlp[/COLOR]4s0
version: 78
serial: 94:b8:6d:e0:06:cd
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=[COLOR="#FF0000"]iwlwifi [/COLOR]driverversion=5.8.0-38-generic firmware=36.77d01142.0 8265-36.ucode Let's see what the logs say:

```
dmesg | grep -e wlp -e iwl
```Ideally, taken a few minutes after a drop.

You can save it as a text file to post later with:

```
dmesg | grep -e wlp -e iwl  >  dmesg.txt
```On my machine, which gets rebooted on New Years and July 4th, the file is pretty long. If so, please paste it here and give us the link:  [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by geekgeek4 on 2021-01-19
Thank you. 

I have attached the file, in its current state. This is not after a drop, but while I wait for a drop, I thought I would upload whatever is in there. When I do experience the drop, I will post the updated file. I did have about three drops today. 

I thought I would also mention that my laptop is running the same version of Ubuntu and is experiencing the same issue after the update. Anyways, I'm focusing on the desktop which I use most of the time, but not sure if that would hint at anything. I guess the network is the one shared thing between the two. 

Thanks again.

---

### Post by geekgeek4 on 2021-01-19
This is what I have from the laptop: 

-- Start -- 


  *-network                 
       description: Wireless interface
       product: BCM4350 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:3a:00.0
       logical name: wlp58s0
       version: 08
       serial: 54:8c:a0:a3:f7:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmfmac driverversion=7.35.180.119 firmware=01-e791c176 ip=192.168.1.109 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:137 memory:dc400000-dc407fff memory:dc000000-dc3fffff


-- END -- 


This is all I have from dmesg from the laptop currently. It also experienced the drop at different time from the desktop. I just booted it up, and so I suspect the logs are useless. But here is what I have for dmesg: 

[   11.365018] brcmfmac 0000:3a:00.0 wlp58s0: renamed from wlan0
[   21.825458] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes ready

---

### Post by geekgeek4 on 2021-01-20
I've been running some tasks that I usually run when the disconnection occurs. I also was running this website ([http://startrinity.com/InternetQuality/InternetConnectionMonitor.aspx](http://startrinity.com/InternetQuality/InternetConnectionMonitor.aspx)), which continuously monitors the internet connection. So far so good after 3 hours. Normally, I would expect a drop by now. This program, likely just continuously pings (aka continuous internet traffic). At the same time, my usual usage generally involves continuous traffic as well (downloads, video/audio etc.)

Anyways, I'm not sure if this is significant or not. In terms of continuous vs non-continuous traffic, I imagine that the network card might power off as we discussed earlier. But that should be disabled now. 

Either way, I think those logs I sent should contain the drop. I haven't powered down my desktop today and so the 3 or so drops should be there hopefully. In the meantime, I'll keep waiting for more drops and logs.

---

### Post by chili555 on 2021-01-20
> sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*Did you make this change to both machines?

> device wlp4s0 entered promiscuous modeWhat is this about?

---

### Post by geekgeek4 on 2021-01-21
Yes, I did.

I'm not sure. What does it mean? Do I have a virus? Or could it be my VM?

---

### Post by chili555 on 2021-01-21
> Or could it be my VM?Possibly. Is your VM running when the wireless drops? If you quit the VM, is the wireless steady again?

---

### Post by geekgeek4 on 2021-01-21
Well, I've lately had a pretty decent connection, and my VM hasn't been running. Previously,  I had been running my VM on and off, although I haven't been running it as frequently as before. I cannot specifically recall if I had a VM open at the time the disconnections were occurring, but I believe it is likely.

Since it has been stable without my VM, I will try running my VM and see what happens. However, my laptop did not have a VM running ever. 

I did also install some updates. Wonder if that fixed it.

---

### Post by geekgeek4 on 2021-01-22
So, my Laptop that is running the same OS, did just experience a drop for about 30 seconds. After I was able to reconnect again, I ran the dmesg command. The numbers are slightly different, but overall the output is the same as I what I posted previously about my laptop dmesg output. 

Previously: 

[   11.365018] brcmfmac 0000:3a:00.0 wlp58s0: renamed from wlan0
[   21.825458] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes 

Except for the numbers in the brackets [ ], the current output a few minutes after the drop is the same.

The only application that was running is Zoom. (No VM).

---

### Post by geekgeek4 on 2021-01-22
Another disconnection during Zoom call on laptop. dmesg does not contain much information, same as above. 

Just to clarify, all previous settings have been set and configured on the laptop as well.

---

### Post by geekgeek4 on 2021-01-26
Another disconnection on the desktop about 3 minutes before dmesg output. Zoom was running. 

dmesg output attached.

---

### Post by gde061-www on 2021-01-26
It's funny, this kind of issue started appearing in 16.04.  Apparently still haven't solved it even though the "solution" that is always recommended is to upgrade to current distro version.  My advice to you: when you encounter these network drops, open a terminal and type

```

sudo service network-manager restart

```
You will most likely then be immediately brought back online with your wifi network.
This is what "loyal" ubuntu folks who don't want to open the can of worms that just unleashes many many more headaches have been living with for years.  Do a google search on similar issues and you will see this come up over and over. Not that the troubleshooting above is not valid, but it's not necessarily going to be productive in my experience.

---

### Post by geekgeek4 on 2021-01-26
> **gde061-www said:**
> It's funny, this kind of issue started appearing in 16.04. Apparently still haven't solved it even though the "solution" that is always recommended is to upgrade to current distro version. My advice to you: when you encounter these network drops, open a terminal and type

```

sudo service network-manager restart

```
You will most likely then be immediately brought back online with your wifi network.
This is what "loyal" ubuntu folks who don't want to open the can of worms that just unleashes many many more headaches have been living with for years. Do a google search on similar issues and you will see this come up over and over. Not that the troubleshooting above is not valid, but it's not necessarily going to be productive in my experience.

Thanks for the advice. I'll give the command a try when the drop happens.

What frustrates me is that Ubuntu was working perfectly for me, not a single hitch, up until the update that happened in the beginning of January. I realize that mistakes and errors can happen, but I really hope that they fix it. However, from the sounds of what you are saying, it seems like the issue might be here to stay. That is very disappointing. I can't have downloads breaking and live applications going down e.g. zoom.

I wish they would get it to work. After all, Windows, Android, IOS, smart TV, chromecast, Raspberry Pi are examples of devices I have running and work perfectly fine. Others can make the networking work without a problem and without it periodically disconnecting, so I hope they do something about it to have it work in a stable and consistent fashion

---

### Post by chili555 on 2021-01-26
In my suggestions above, I said:

> Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

What we see in your latest dmesg is:

> associate with 80:2a:a8:48:93:41 

Later:

> associate with 4e:a8:25:28:29:f0

Still later:

> associate with 80:2a:a8:48:93:41 

So your wireless is indeed dropping because it is roaming from among several access points, always looking for a better connection, somewhat like my ex-girlfriend.

Did you try my suggestion?

You might also try binding your wireless to the strongest of the competing access points like this: [https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624](https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624)

---

### Post by gde061-www on 2021-01-26
> **chili555 said:**
> In my suggestions above, I said:


What we see in your latest dmesg is:


Later:


Still later:


So your wireless is indeed dropping because it is roaming from among several access points, always looking for a better connection, somewhat like my ex-girlfriend.

Did you try my suggestion?

You might also try binding your wireless to the strongest of the competing access points like this: [https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624](https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624)

So if he has a "mesh router" system -- those neat looking little router pods that come in packs and look like my great-autie's old ashtrays, you are saying he is SOL because when NM goes to switch from one AP to the other, it craps out?

---

### Post by geekgeek4 on 2021-01-26
Thank you.

I went ahead and assignment 80:2a:a8:48:93:41 to BSSID of my network. Based on what I read, I guess this will bind my network connection to the 5G network. I recall we discussed separating the 2.4 and 5 Ghz networks with separate names. I did not go through with this just because it worked well with my other devices. But I will go ahead and do it. I promise. For now, in the meantime, I'll see if the BSSID option changed anything. As you mentioned, this will make sure it doesn't switch to other antennas/APs.

I do have just one AP, but the 2.4 and 5 Ghz spectrums are put under one name (for now until I change it), with band steering favoring the 5Ghz one. 

Thanks

---

### Post by chili555 on 2021-01-26
> you are saying he is SOL because when NM goes to switch from one AP to the other, it craps out?That's what I suspect, based upon many dozens of similar cases I've responded to over the years. 

He, the OP, is not stuck out of luck, however, because he can rename one and he can also try binding the BSSID as I linked.

No operating system is perfect. I have now and have experience with iOS, Windows 10, ChromeOS and Ubuntu (x3). Each have a flaw or three that are irritating that I wish would be fixed.

---

### Post by gde061-www on 2021-01-26
I was just reading about how the progress is going in terms of brining ubuntu over to IWD.  It was like 3 years ago that it was promised that IWD was going to fix all the wireless idiosyncrasies that make linux a major headache for a significant portion of adopters (it was my opinion that the problems started after 14.04, but I think part of it was that you maybe had to do more youself in the older versions, so if you could figure it out, you were golden, but many people couldn't figure the stuff out.  Anyway, back on this point, in one of the things I read, it said that IWD isn't going to support mesh networks.  Maybe that was old article...  anyway, I hope OP will update if this solved his issue.  I have been doing test configs with 2.4 and 5gHz using very similar, not same, names (to avoid insanity of forgetting which ones I was working on)... and am using same pw for both.  And have diff AP's using same name (actually mesh system I just was trying out).  I have sinking suspicion that they are mapping to same space in the hash table which is blowing up my network.  I would not have thought about that but for what you raise as issue in this thread.

---

