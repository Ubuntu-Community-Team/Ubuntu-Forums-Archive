---
title: "Issue with NETGEAR WNA3100 and WNDA3100V2 wireless network adapters"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by Triston_Marbut on 2016-03-03
Hello, I have been watching around on the forums about Netgears histroy with Linux systems and it seems it doesn't end up well. 
I am seeking assistance for these 2 wifi adapters on which i despertly need to work, I cannot go back to Windows 8 becasue I dont have a USB big enough or a DVD disk.
I read some of the other forms about this issue and i did what they had done such as $sudo\desktop\bcmnxx64.inf and what not and that works but my problem is unique , after is hit $ sudo modprobe ndiswrapper both of the adapters work and I go to load 3\4 sites, they load up but after some time  poof it doesn't have internet anymore  , still registering connected but not receiving data at all. 

I am litterly  3 days new to Ubuntu and I have tried 7 other Linux OS's and they all do the same.
I do not have Ethernet either,  I only managed to get this far thanks to my Iphones  hotspot via USB ... Of course I have used 4\21 GB of data trying to get the dammn thing to work .. 

No luck^^  please help!!

---

### Post by chili555 on 2016-03-03
Both of these devices use the twitchy and tricky ndiswrapper which is a method to (barely) use Windows XP inf and sys files. It is, in my opinion, not well supported and a crutch. Whenever possible, I suggest any number of well-supported native devices be used instead. I bought a USB wireless device that works out of the box for US $10.

I do understand, however, that sometimes time, budget and other factors force us to use what we have for now.

There are a few things you might try to give your device the best chance at success. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Finally, I suggest you check here: [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)> I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.

---

### Post by Triston_Marbut on 2016-03-03
Thank you for your help. Budget is not a problem I'm just lazy . also if it helps, the internet goes out after 6 or so MB is downloaded I can get about 20 sites loaded .

---

### Post by Triston_Marbut on 2016-03-03
Is this like a TX power issue of something? It was resgesterimg at 40 for a bit during sudo modprobe ndiswrapper

---

### Post by Triston_Marbut on 2016-03-03
It's a problem that's internal.. But there driver seems to work on 32 bit driver a lot longer than the 64 bit

---

### Post by Triston_Marbut on 2016-03-03
Also, do you know how to reinstall windows ?? I downloaded the 8 ISO from Microsoft I own a product key, but after I boot into the 3 option I get an error saying a usb\cd\ DVD driver is missing . is my disk Ubuntu screwed up? I made 2 partions in gparted ISO, one 32 one nfst and it still didn't recognize it .

---

### Post by Triston_Marbut on 2016-03-03
Lastly , would openSUSE work with my adapters ?? I know it says windows drivers compatable which means the latest driver from NETGEAR .

---

### Post by Triston_Marbut on 2016-03-03
I need a solution to this problem I hate alot of work I need to do and I can't do anything on this bricked operating system which doesn't even support a driver that's as old as Linux is practically . I litterly am stuck.

---

### Post by chili555 on 2016-03-03
Linux supports a great many drivers perfectly well. Broadcom drivers and, particularly their firmware, is proprietary. If Broadcom doesn't release drivers and firmware for the WNA series, there is really nothing, aside from ndiswrapper, that we can try.

If you can load a few pages, I suggest you start here: [http://www.amazon.com/gp/product/B002SZEOLG?keywords=722n&qid=1457020432&ref_=sr_1_1&s=electronics&sr=1-1](http://www.amazon.com/gp/product/B002SZEOLG?keywords=722n&qid=1457020432&ref_=sr_1_1&s=electronics&sr=1-1)

I know nothing about Windows or its installation.

---

### Post by Triston_Marbut on 2016-03-03
Do you know about OpenSUSE? Maybe that is worth trying it does point out it is compatable with all windows drivers

---

### Post by chili555 on 2016-03-03
Sorry, I know even less than nothing about SUSE. I do know that the Linux kernel and ndiswrapper are essentially the same across all Linux distributions. If SUSE have tweaked ndiswrapper in any way, which is possible, I am unaware of it.

---

### Post by Triston_Marbut on 2016-03-03
I'll try openSUSE, you can't say "all windows drivers and media compatable " without that being true haha which is what they said .

---

### Post by chili555 on 2016-03-03
> **Triston_Marbut said:**
> I'll try openSUSE, you can't say "all windows drivers and media compatable " without that being true haha which is what they said .Yes. If it is on the internet, it must be true.

---

### Post by Triston_Marbut on 2016-03-03
Haha true. Also openSUSE was a complete fail , didn't even re ongize my Ethernet adapter which Ubuntu did .. So no iPhone hotspot. 
Your said you don't think NETGEAR wna3100\wnda3100v2 could work on 14.04 and 15.04 what about 12.04 ?? I'm installing as I type this. 
Please do give instruction for 12.04 install attempt .

---

### Post by chili555 on 2016-03-03
The instructions are the same. I explained it here: [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

---

### Post by Triston_Marbut on 2016-03-03
Can you provided the link again for the WNA3100 again? The links I have found don't work.

---

### Post by chili555 on 2016-03-03
> **Triston_Marbut said:**
> Can you provided the link again for the WNA3100 again? The links I have found don't work.The link in my post just above works for me. Click and go.

---

### Post by Triston_Marbut on 2016-03-03
I fixed it!! It still didn't work  the beginning so I unplugged it quickly typed sudo iwconfig wlan0 txpower 15 and  sudo wlan0 power on and it works !! Much much much longer than before , I have got wine downloading at about 1mb per 4 seconds but ATLEAST ITZ CONSTANT  .  it's been running for 3 minutes now

---

### Post by Triston_Marbut on 2016-03-03
And it stopped ....

---

### Post by Triston_Marbut on 2016-03-03
And I just typed power off and it started again... Wtf?

---

### Post by Triston_Marbut on 2016-03-03
Wish it stalls and restarts itself I'm not doing anything

---

