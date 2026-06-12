---
title: "Wirelss network problem. Netgear WG511."
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by CapitanYochua on 2007-11-13
I am trying to get the WG511 wireless PC card working in Xubuntu (Gutsy). I am not even able to identify which WG511 is mine.  But my lspci...
```

02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78) 
        Subsystem: Dell Unknown device 00f3 
        Flags: bus master, medium devsel, latency 80, IRQ 10 
        I/O ports at 3000 [size=128] 
        Memory at e8000000 (32-bit, non-prefetchable) [size=128] 
        [virtual] Expansion ROM at 24000000 [disabled] [size=128K] 
        Capabilities: <access denied> 

02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller 
        Subsystem: Dell Unknown device 00f3 
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10 
        Memory at e8001000 (32-bit, non-prefetchable) [size=4K] 
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176 
        Memory window 0: 20000000-23fff000 (prefetchable) 
        Memory window 1: 28000000-2bfff000 
        I/O window 0: 00003400-000034ff 
        I/O window 1: 00003800-000038ff 
        16-bit legacy interface ports at 0001 

```
I obviously have no internet on that computer. So what should I do to get my wireless working? Anything with ndiswrapper? Help please.

---

### Post by CapitanYochua on 2007-11-13
bump

---

### Post by hounjac on 2007-11-13
Hello;

Maybe you can help me,
I am working with a standalone Ubuntu Linux System
I have Comcast Internet connection with a linksys access point
I have a Netgear WG311 wireless adapter card I need to know how
to install the drivers for the wireless adapter card. Can you
tell me how this is done!
Thank you hope you can help!!!
hounjac

---

### Post by CapitanYochua on 2007-11-13
There is a sticky thread that has a list of compatible cards. Look for yours and it should have a link to the driver you need to download and install with ndiswrapper. I still need help on my issue because I am not even sure which of the WG511 is mine.

---

### Post by CapitanYochua on 2007-11-14
I have internet on the liveCD, but when I install and boot off hard drive my internet doesn't work due to WG522 I suppose. Any help?

---

### Post by CapitanYochua on 2007-11-14
bump.

---

### Post by jacksonz123z on 2007-11-16
I have a wg511v2 and it works fine with ndiswrapper under xubuntu Gutsy .  This card comes with two different chipsets, a Marvel and a Prism.  The Prism should just work.  The Marvel needs ndiswrapper.  I had to add "ndiswrapper" to /etc/modules otherwise the standard procedure works.

---

### Post by crispinb on 2007-11-16
> **jacksonz123z said:**
> I have a wg511v2 and it works fine with ndiswrapper under xubuntu Gutsy .  This card comes with two different chipsets, a Marvel and a Prism.  The Prism should just work.  The Marvel needs ndiswrapper.  I had to add "ndiswrapper" to /etc/modules otherwise the standard procedure works.

When you say the 'standard procedure', do you mean using system->prefs->network to configure the card after the windows driver is installed and ndiswrapper module loaded?

I also have the wg511v2 (with Marvell chipset), and the ndiswrapper part goes OK, the light comes on. iwconfig recognises the card, and iwlist finds my access point. But I haven't been able to get the card to have an IP yet, either static or dhcp. And this is with temporarily setting my AP to open; it's hard to imagine getting things working with WPA.

Is there a doc somewhere highlighting the standard procedure you've used? Cheers.

---

### Post by dodgingspam on 2007-11-17
I just installed Ubuntu Gutsy. It's a Compaq laptop and uses Netgear WG511 v2. Works fine under windows XP but I am yet to figure out how to connect under Ubuntu. As soo as I'm able to I'll wipe out XP and will never look back.

I keep reading about some ndiswrapper and everyone sounds like a pro on this board. How do I go about getting things going?  Is there a step-by-step procedure somwhere? I can't even figure out still how to load Gutsy on system boot before XP kicks in...

---

### Post by jacksonz123z on 2007-11-17
To get the card going I did the following:

Install ndiswrapper from synaptic and copy the Win drivers from the card's installation  CD.
Firstly, you need to place the WG511v2.INF _**and**_ WG511v2.sys  files together in a folder.  From memory I think I have been using Win2000 drivers.  Next open a terminal and
```
sudo ndiswrapper -i <path to the .inf file>
```.

Now check and see if you have been successful at loading the driver:
```
ndiswrapper -l
```

If things look good
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -m
```

I found also that I had to add the word "ndiswrapper" to /etc /modules configuration file to load the module at boot (at least for xubuntu).  Now it should easily be possible to set up networking using the Admin Network tool.  I only use WEP but one day when I feel strong I will have a crack at WPA.

I hope this helps, the card certainly works on my Acer Aspire laptop under Gutsy and most recently Gutsy Xubuntu.

---

### Post by dodgingspam on 2007-11-17
Where do I copy all these files? I open terminal and can create a new folder but where? Or shall I place it in some existing directory? I've downloaded the latest wrapper and have it on my CD. Whe you say get it from synaptic, does it meat it's already there on my HD?

I bit lost.

---

### Post by jacksonz123z on 2007-11-17
From the Netgear install CD that came with the wireless card browse to the Driver/Windows 2000 folder.
Copy the .INF and .sys files to any directory on your laptop.  For example make a folder called Drivers in you home directory and copy  the two files to it.  All you are trying to do is make a path to the driver.

If you have installed ndiswrapper then it will be on your HD, check synaptic to see if it is installed, use "status". ( I assume that you have installed Gutsy and are not running a LiveCD.)

You are set to start.  To load the driver do something like this (based on above example)

```
sudo ndiswrapper -i /home/<your home directory name>/Drivers/WG511v2.INF
```

Now follow the my previous post, code instructions.

---

### Post by crispinb on 2007-11-17
> **jacksonz123z said:**
> T

 I only use WEP but one day when I feel strong I will have a crack at WPA.

I hope this helps, the card certainly works on my Acer Aspire laptop under Gutsy and most recently Gutsy Xubuntu.


Thanks, that all works for me too.

Has anyone else reading this here got WPA working with the WG511? My attempts have failed so far, and I'm doubtful about leaving my wireless AP unsecured.

---

### Post by jacksonz123z on 2007-11-18
You got me thinking.  Ubuntu has come a long way fast.  WPA is really easy now.  Just go to Admin/ Network and check out your Wireless Connection properties.  Click the Pass Word Type box and select WPA personal, enter your shared secret and it works!

Thanks for raising this question.  I am really impressed with Gutsy!

---

### Post by jacksonz123z on 2007-11-18
Well! I posted too soon.  WPA works, but on re-boot to get wireless working I have to re-enter the secret phrase!  I saw a lot of posts on this topic with no apparent solution.  I am going back to WEP, it does work and I have wasted too much time on this Laptop today!

---

### Post by crispinb on 2007-11-18
For some reason, WPA via NetworkManager just won't work for me -- I can still only connect using  WEP. WPA connections hang for a while, with the NetworkManager applet saying "waiting for network key for wireless network xxx".

Unless I can live with WEP, I may have to summon up the courage and abandon NetworkManager and give the older methods a try.

---

### Post by dodgingspam on 2007-11-18
I have installed dniswrapper and the driver for card. I even saw the lights came on the card, however, I did not have time to test drive. Now when I start my laptop the lights on the card are not on. I went to Network Setting and still do not see the Wireless option. I checked thrpough synaptics and ndiswrapper is listed as installen. When I run sudo ndiswrapper -i /home/mydir/drivers/WG511v2.INF it tells me that the driver is already installed...

So how do i get it to kick in when I start the laptop?

---

### Post by crispinb on 2007-11-18
> **dodgingspam said:**
> I have installed dniswrapper and the driver for card. I even saw the lights came on the card, however, I did not have time to test drive. Now when I start my laptop the lights on the card are not on. I went to Network Setting and still do not see the Wireless option. I checked thrpough synaptics and ndiswrapper is listed as installen. When I run sudo ndiswrapper -i /home/mydir/drivers/WG511v2.INF it tells me that the driver is already installed...

So how do i get it to kick in when I start the laptop?

OK what you've got here is the driver installed for ndiswrapper, but ndiswrapper itself is a kernel module, and it's not yet being loaded into the kernel. So:

Add a line just containing the single word **ndiswrapper** to the file /etc/modules (which is just a list of kernel modules to load when booting).

You'll need to do this as root, ie. sudo gedit /etc/modules

---

### Post by dodgingspam on 2007-11-18
Ok, I went through some steps and I think it took care of loading card along with whatever else it needed. I rebooted laptop and the card is blinking. HOWEVER... I was so eager to wipe out my Windows that I totally forgot to check what settings I had there in order to be able to connect. I see my network on the list -- which is good. I remember my passwphrase. I can not remember what I used to have as Password type, and there are several options. I think it was some sort of WEP. I've tried both (hex and ascii) -- no contact.

Connections settings also throw me off. I left configuration on Auto Config (DHCP).
I did not enter anything for IP address, subnet mask and Gateway address.

My stationary PC is connected to the wireless router. How can I check what settings do i need to get my laptop inline?

I'm getting closer -- I can feel it already!

---

### Post by dodgingspam on 2007-11-18
not sure what I did but I'm connected!

---

### Post by jacksonz123z on 2007-11-19
I think WEP is quite OK for home use.  My neighbours can't even start a lawn mower let alone hack my account!  There seems to be a major bug in WPA for Gutsy, I expect it will be fixed in the Heron.
Networkmanager has been causing trouble for years!  I deleted it  and just use the manual config.  I came across WICD in the forum, this appears to work very well.  I will give it a go one day but just waiting for the Heron could be better.

---

### Post by crispinb on 2007-11-20
> **jacksonz123z said:**
> I think WEP is quite OK for home use.  My neighbours can't even start a lawn mower let alone hack my account!  There seems to be a major bug in WPA for Gutsy, I expect it will be fixed in the Heron.
.

I expect you're right. Also, in my case, my wireless AP has such crappy range that someone would have to hide in my garden to hijack it. And if they're willing to go to that amount of trouble, I can spare them a bit of my bandwidth.

---

### Post by John Jason Jordan on 2007-12-22
I finally got my Netgear WG511 v2 with the Marvel chipset working on Gutsy x86_64 using ndiswrapper. Details are here:

[http://ubuntuforums.org/showthread.php?p=3999047#post3999047](http://ubuntuforums.org/showthread.php?p=3999047#post3999047)

---

