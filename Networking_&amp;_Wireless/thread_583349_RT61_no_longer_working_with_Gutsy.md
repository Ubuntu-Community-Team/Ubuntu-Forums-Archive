---
title: "RT61 no longer working with Gutsy"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Alamar on 2007-10-20
This is in part an information post for others searching who may have this problem...

My Ralink RT61 based wireless card no longer works in Gutsy, after working fine (including WPA) in Feisty.  Why?  Because the RT61 module has once again been replaced by the flaky RT61pci module in the kernel!  This happened the other way round Edgy->Feisty and lead to much rejoicing at no longer having to use ndiswrapper.

Since I'm not keen on recompiling my wireless drivers on every new kernel update, back to Feisty I go.  I hold out slim hope that the RT61pci module can now be made to work (at all), but when the output of "iwpriv wlan0" shows no mention of all the settings previously required (AuthType, EncrypType, CountryRegion, etc.) I'm not optimistic.

A working /etc/network/interfaces file for RT61 with WPA in *Feisty* can be found [here](http://ubuntuforums.org/showpost.php?p=2825485&postcount=54).

Here's hoping the RT61 module gets put back into Hardy...

---

### Post by Jadd on 2007-10-20
So that's the problem. I was wondering why I couldn't get my rt61 to work on Gutsy. You seem to know what you're talking about, could you post a bug report on [launchpad.net](http://www.launchpad.net) for us please? Thanks.

---

### Post by Pete051 on 2007-10-20
I have had the same experience luckily I upgraded so the 2.6.20 kernel was still available I could set up the rt61 in there with no problem

---

### Post by Alamar on 2007-10-20
I've added a comment to an existing [Launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/28464) that will hopefully get looked at.  Whilst I may be able to diagnose the source of the problem, deciphering Launchpad to find the correct bug report is more difficult!

---

### Post by Jadd on 2007-10-20
After fiddling with the instructions for rt61 at wiki.ubuntu.com,  I tried these instructions, and now wifi with WPA2 works!
[http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help/](http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help/)

---

### Post by bmpv666 on 2007-10-22
i have the same problem with Gutsy and the RT61 pci card...
i tried those instructions @lokergnome, and i did manage to get my wireless working with WEP. but after a while working, the connection would drop completely! only restarting the network would make it work again for a while more...
well like the author of this thread, i went back to Feisty, where it works flawlessly out of the box..i'll wait for Hardy Heron to give it another shot at.

---

### Post by balak on 2007-10-23
I should admit that my Ralink wireless card (rt61) is working just fine in gutsy.

I had major issues with feisty - had to uninstall networkmanager, compile my own driver from rt2x00 project (I used the legacy rt61 driver), add 'rutilt' utility to connect, compile my own version of wpa_supplicant to get support for ralink. Finally I got it to work both with WEP and WPA2 (Enterprise).

In gutsy, WEP now works with networkmanager. Initially it looked like networkmanager was acting up again. So I installed Wicd (which removed networkmanager). But that didn't help. So I  reinstalled networkmanager and networkmanager-gnome and everything is good now. I am able to connect to the WEP network at home.

However, I haven't tried the WPA2 connection at work - will do it today.

I am not sure how much my experience will help you - but you can try the above.

From the forums, it looks like a 'rt61' itself has two sets of cards. For some people, feisty worked beautifully and gutsy got broken while for the some its the other way around. Hope ubuntu can fix for both these varieties in hardy.

---

### Post by undertakingyou on 2007-10-25
balak, that is weird that you are having the complete opposite problem that I am seeing everyone else have.  I am in the majority here.  Feisty it worked well, edgy and dapper it worked for me also.  Now I can get nothing.  Strange side note:  Before the rt61 interface was named ra0.  Now, I have wlan0 and wmaster0.  I hope that this driver can get unborked soon.

---

### Post by balak on 2007-10-25
Ok, it looks like WPA2 is not working. I am trying to debug that now.  

Yes, the interface has changed to wlan0. Apparently gutsy ships with the 'new' rt2x00 drivers. [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=26946#26946](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=26946#26946)

If you are interested (and have the time and enegy), check out the rt2x00 forums - they may be able to help you fix the driver.

---

### Post by frojnd on 2007-10-25
Hello guys. I've been using rt61 for 3 weeks and everything worked just fine untill now. Computer freezes every 30min. I'm on feisty. Here is the las /var/log/syslog output

[http://paste.ubuntu-nl.org/42124/](http://paste.ubuntu-nl.org/42124/)


Oh another thing. When I check if rt61 is loaded with lsmod | grep rt61 it's there. I also have rt61pci under blacklist. 

If someone can help? I'm desperate.

Here is my wireless card:

```
02:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Linksys WMP54G ver 4.1
        Flags: bus master, slow devsel, latency 32, IRQ 21
        Memory at fb000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
```


I've blacklisted rt61pci cause it was said so to install this card here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

Do I have to update my modul? or install drivers? Cause now I only have rt61 loaded. Oh and I don't know how to load this module automatically.

THANX IN ADVANCE

---

### Post by bgc on 2007-10-25
Hi, I have a Belkin PCMCIA F5D7010 g wireless card. I managed to get it working under Feisty (with WPA) following 

[http://ubuntuforums.org/showthread.php?t=419709](http://ubuntuforums.org/showthread.php?t=419709) 

However, I upgraded to Gutsy, and everything stopped working. I attempted the same steps, and tried following other suggestions (including downloading drivers from serialmonkey, using wicd, etc.) with no success. 

I subsequently decided to do a fresh install of Gutsy. Network manager now sees my network, and occasionally even connects to it, but disconnects immediately. I again tried the same workarounds, including wicd, and again no success. 

More worryingly, I attempted to connect without WPA, and still nothing. And the final drop is that I do not seem to manage to connect through ethernet either! 

I would appreciate any help, as this is driving me nuts!! If there is any further info I can provide you with, I would be happy to do so... Thanks in advance!!!

---

### Post by neu_ser on 2007-10-28
I have my rt61 card working with WPA in Gutsy,

I had to blacklist the current rt61pci then compile and install the latest rt61 driver from serialmonkey.
The readme file which comes with the driver is actually pretty good, even a noob like myself could follow it,
You just need to download the driver from a working connection and know how to un-tar it 'tar -zxvf *tar.gz' and you should be on your way.

I can get the connection via shell commands but can not get it working automatically with /etc/network/interfaces or network-manager. Infact network manager seems worthless, even now whilst connected it reports 'no active device'.

I'm currently trying to install Rutilt but it's complaining about something or other.

---

