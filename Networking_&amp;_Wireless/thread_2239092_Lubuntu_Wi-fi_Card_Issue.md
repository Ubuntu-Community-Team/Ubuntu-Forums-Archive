---
title: "Lubuntu Wi-fi Card Issue"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by Zer0_Day on 2014-08-11
Hi, I have a Gateway ML3109 laptop that I have installed Lubuntu 14.04.1 LTS on. (Dual booting Windows Vista Home Basic SP2 64bit, in which the Wi-Fi card works fine.) I am new to Linux. For the life of me I can't seem to get the Wi-Fi card working. I have tried all of the Ubuntu Wireless troubleshooting tips. I have created another [thread]("http://askubuntu.com/questions/500380/lubuntu-14-04-drivers-issue") on AskUbuntu, but I'm not getting any good answers, and do not have enough rep for a bounty. The card I am trying to use is a Realtek RTL8185L. Lubuntu has assigned the RTL8180 driver to it. The card is not hardware or software blocked. The driver module seems to be loaded correctly and the card is recognized and not marked as disabled. Yet, the network-manager still can't find any networks and says "disconnected". If I cannot find a way to get the internal card working, I have a Netgear N600 WNDA3100v2 USB adapter that I could try. 

Thanks,

-Zer0

---

### Post by Hadaka on 2014-08-12
Hi, see if this helps.
[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by Zer0_Day on 2014-08-12
Hi, I've actually already tried this. It just creates a second network manager applet in the panel. It looks identical to the other one, and also shows "Wifi-Networks, disconnected." <----- This text is grayed out, (unable to click). 

By the way, when I installed Lubuntu, I used the alternate installer and had to use the option "acpi=off". (This is really a completely separate [issue]("http://askubuntu.com/questions/509578/gateway-ml3109-only-boots-with-acpi-off") that I am trying to solve. It is preventing my laptop from shutting down.) Could this be causing the problem? 

I ran the [wireless script ]("http://dl.dropboxusercontent.com/u/57264241/wireless_script")posted [here]("http://ubuntuforums.org/showthread.php?t=370108"). In **-Device:wlan0** the state is marked as "disconnected". In **iwlist scan**, wlan0 yields "No scan results". In **iwconfig**, Power Management is marked as "off".

---

### Post by Zer0_Day on 2014-08-13
I have good news and bad news. I gave up on the Realtek card and its unknown problems. I decided to try the Netgear Adapter. I have made substantial progress by using [this]("http://ubuntuforums.org/showthread.php?t=1383708") thread. (Except I changed one step. Instead of using Wine to get the Windows XP driver, I downloaded a VM from [here]("https://www.modern.ie/en-us/virtualization-tools#downloads") and installed the software from the cd. I used VirtualBox and had to insert the adapter during the install, and use Guest Additions and Shared Folders to get the files out.) 

I have now run into the problem described in [this]("http://ubuntuforums.org/showthread.php?t=1885380") thread. When I try and connect to my network (hidden), I get a popup requiring me to authenticate the wireless password. It is already autofilled, but I tried re-typing it in anyway. After I click connect, it just continues to pop up. I have tried restarting my router and ignoring IPV6 settings. Any ideas?

---

### Post by weatherman2 on 2014-08-13
Let me toss out another idea: replace your internal wireless card with one that is automatically supported in Lubuntu.

Go on YouTube and search for your laptop model number and "replace wireless card" - so search for "Gateway ML3109 replace wireless card."  It may be ridiculously easy to do. I have replaced numerous wireless cards in laptops.

I think that's an older laptop, so you may not be able to get an 802.11n wireless card - maybe limited to 802.11g (not sure, don't know of any 802.11n cards that would fit the older size, could be though).  An Intel 2200bg or 2915abg card (wider than the newer wireless cards) will probably work.  Maybe $5 USD on eBay. You would be limited to 802.11g speeds but that is fine for most internet browsing, slower mostly in the case of transferring files on a local network.  You don't have to get a "Gateway" card - but don't get an IBM/Lenovo/HP version of the card.

---

### Post by Zer0_Day on 2014-08-13
I have considered this before, and was about to purchase a new card online, until I found my Netgear adapter. Seeing as I have almost gotten the Netgear Adapter working, I will purchase a new card as a last resort if I fail to get the Netgear working. 

I see [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI") that there is a fix for the Realtek Linux driver that Will Daniels created, it was discussed [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285") and [here]("http://ubuntuforums.org/showthread.php?t=210958&page=5&p=4743700#post4743700"). The [link]("http://www.willdaniels.co.uk/index.php/blog/tech-stuff") seems to be dead, does anyone know if the fix is still available or working? I know that it was a while back that this fix was released, and it's for a ancient version of Ubuntu, but I still want to try, as it's the only thing suggested in the hardware support.

---

### Post by kurt18947 on 2014-08-14
> **Zer0_Day said:**
> issue[/URL] that I am trying to solve. It is preventing my laptop from shutting down.) Could this be causing the problem? 
........................................


I don't have any thoughts about your wifi problem but did have a similar problem with shutting down.  My Thinkpad would not shut down, it would act like it was going into suspend but would then resume.  I had to unplug the AC adapter and remove the battery to get it to power down. There's an intermittent bug that causes this.  What worked for me was to enable 'wake on LAN' in BIOS.  That Netgear adapter has a reputation for being ........ challenging .......... to get working in Ubuntu.  I hope you're able to work it out.

---

### Post by Zer0_Day on 2014-08-14
Thanks for the suggestion. Sadly, I do not have a WOL option in my BIOS. I only have a LAN Boot option. I also checked for a BIOS update on Gateway's site, but didn't find any. 

You're right, I have the problem child of USB adapters, but the adapter isn't actually the issue at this point. It is operating normally, it finds networks and it's status light is working. I have actually ran into this [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/912702"). Going to try the fix and see how it goes.

---

