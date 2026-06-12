---
title: "Broadcomm 4318: Some gotcha's you can avoid"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by bilange on 2006-11-26
This post is a semi howto, semi "info gathering" from the community, and semi help request. Honestly I find this setup quite special to make it work. Hey, but at least it works ;)! So i'm spreading the word.[INDENT][COLOR=Navy]**Note:** this is probably Acer-related only, but it may work on other laptop brands, too. It "could" work on brands where you need a special program to make your "wireless button" work. Your miles WILL vary, I didn't test with anything else but my laptop.

** Note 2:** By "network interface" and *iface*, I am referring to eth0, wlan0, and anything similar.

** Note 3:** I always assume that you're using sudo for all the commands I wrote. You better use "sudo -i" to have a "fully-superuser" command line. Please don't forget to exit once you're done.[/COLOR]  [/INDENT]This post is specially dedicated to people who gets "**ADDRCONF(NETDEV_UP): eth1: link is not ready**" error message, for those who seem to get the driver fully installed by any means (ndiswrapper, the bcm43xx original driver or the firmware "patch") but doesnt get any input from the wireless card, espacially on Acer laptops where you "need" to have a special program loaded (at least when using it in Windows) to make the wireless card working.

Ive struggled for three days now to get my wireless card working, and Ive figured out that Windows seem to leave my card in a non-working state when I go back to Linux. 

First, the facts: 

My laptop is an Acer 5044 ("5040 series"), with a Broadcom 4318, listed by lspci as "*06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)*". Rest of the specs are: AMD Turion64 1.8GHz, 1Gb of RAM, Ubuntu Edgy (x86)/Windows XP MCE in dual boot.

Ive probably read every wireless/bcm4318 howto and troubleshooting pages twice, and after messing around, trying to patch/workaround/you name it, it finally "decided" to work. To be sure, I tried to trim down my configuration and reboot, everything worked fine... as long as I didnt boot into Windows again. 

Then I proceeded to booting into Windows to setup my wifi connection here, and then came back into Ubuntu, to see at my surprise that the wireless connection doesnt work anymore ("*link is not ready*" error). 

Long story short, Ive figured out that Windows does mess up with the wireless controller in a strange way so it becomes unusable, unless you unload any wireless-related kernel modules, bring down wireless interfaces, and reload them again.

To make things worse, on my laptop there is an external button which, in Windows, enables the wireless device (or allow the device to actually transmit signals, I dont know for sure). It's more or less like an on/off switch, in addition/complement to the Networking configuration in Windows XP. While troubleshooting on Ubuntu i have messed around with acer_acpi and acerhk kernel modules for awhile (as it was recommended for my Acer laptop by another Ubuntuforums member). When my wifi card finally worked for the first time, those acer modules were actually NOT loaded. So I first thought that those modules were useless, since I was able to use my wifi card with only ndiswrapper and no special program/kernel modules for my laptop. In reality, I was able to use my wifi connection, with only ndiswrapper, as long as I just booted into Linux and NOT Windows. 

At any time when going back into Ubuntu after a Windows session, dmesg/syslog says that "*link is not ready*" and doenst tell much more. To get around this, you need to do this steps: 

(You need to make sure your wireless kernel module is loaded and that the card is well detected, though. This isnt the goal of my post.)[LIST=1]
[*] Bring down the network interface linked to your wireless card, if it's not already done, by doing *"ifconfig iface down*". If it's already done or you don't see any wireless interfaces, let's assume it's already done or your card isn't quite detected/set up automatically for networking, so just goto #2.
[*] Unload ndiswrapper / bcm43xx, or whatever the way you're trying to make your wireless card work with, using rmmod.
[*]Also unload any laptop-specific modules where the module tries to (or mess around) the "wireless button" or LED. [COLOR=Silver](If you don't have (or find) such buttons, LED's, and/or kernel modules for it, chances are that this thread wont help much. The goal of this tread if to make a bcm4318 card on certain tricky setups with a button/led interfering with the usual Wifi card behavior. Since the bcm4318 seems to be a popular troubleshooting subject (as in, lots of people asks for help),  I assume this will be useful for laptops other than Acer, but I may be wrong. Either way, someone has to publish the howto, right? ;))[/COLOR]
[*] Load your laptop-specific modules for your button/LED **BEFORE** loading ndiswrapper or bcm43xx.

Here's what I have to do for my Acer laptop:

```
/sbin/modprobe acerhk autowlan=1 poll=0 force_series=5020 verbose=3 usedritek=1
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1" > /proc/acpi/acer/wireless
```
[*] Load your wifi module, either ndiswrapper bcm43xx, whatever.
[*] Bring your network interface back up (using ifup iface), cross your finger and toes and [...], and PRAY!!!!
[*]At this point, your wireless LED (if you have one) should be blinking a bit. If nothing happens, check for any pointers in dmesg or /var/log/kern.log.
[*]Now you can try to scan for networks with wifi-radar, or just configure your wireless setup using your preferred application/tool/commandline utility.
[*] ???
[*] Profit! ;)[/LIST]This made the trick on my Acer 5040. 

At the time of this writing, I just figured out the "problem" and I didnt optimize the solution yet!

The problem though, is that you need to do it manually (unless someone else figure out how to make it work?)... So far, any attempt to make this steps automated into the boot sequence will make the wifi card go back into its "link not ready" state. Thats whats going on in my machine, at least. Your miles may vary.

An ideal setup would be to leave your wireless network interface (wlan0, eth1, whatever) to manual (aka: not starting automatically) until it hits your wifi initialization script. To do this: in */etc/network/interfaces*, comment out the "*auto iface*" line, so the Ubuntu networking script (which is ran at startup using */etc/init.d/networking*) doesn't try to start it up before you "reset" your wifi card correctly in your script. Also, you would make sure that bcm43xx and ndiswrapper doesn't get loaded automatically by adding them to the */etc/modprobe.d/blacklist* file, and removing them from /etc/modules.

As far as I know/tried, the wifi initialization script would be put into /etc/rc.local (unless there are better ways to put commands at startup? i'm not quite sure), where you'd basically do the same steps as mentionned higher. Unfortunatley, this didnt do the trick on my laptop, I have to start it manually for some strange reason.

Additional infos:

If you have an Acer 5040 with a bcm4318, heres some drivers that worked.[LIST]
[*][The official, Acer 5040's specific driver]("ftp://ftp.support.acer-euro.com/notebook/aspire_3040_5040/driver/broadcom_80211bg.zip")
[*][wl_apsta.o]("http://drinus.net/airport/wl_apsta.o") from the [bcm43xx Wiki article (for Edgy)]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy")[/LIST]I used both of them with [bcm43xx-fwcutter]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy#head-d2623559f21cb2d6373aaa3a17dece9d8f2abb50") mostly, ndiswrapper never really worked beyond the module installation point (the network interface doesnt come up, the wireless LED just blinks once and never goes back on.)

That's it to make it work. Now it seems that I have a very limited wireless range, and I'm not sure where to look at. I assume, if I refer to [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices), that my card isnt fully supported and that I should wait to get the full range, and there's nothing else we can do about it. Am I wrong?

Anyway. I hope this semi-howto will help anyone setup his wireless. To be honest, I never knew it would be SO hard (as in: lots of work) to make it work... but thats probably just me?

I'd like to hear about the reduced wireless range, though... im not quite sure. Actually I also have like 33% of packetloss, and my wireless router is just next to me! Thats insane, isnt it? :-k

Thanks for reading! :-D

[COLOR=Gray] Mods: feel free to move this tread around. I thought it was best to post it in the Networking/wireless rather than in the Howto section because most users requesting help (and who was going to create a new thread about his networking problems anyway) will go see in the Networking section first (and not often in the Howto section). Furthermore, this isnt a complete solution and it has flaws - probably due to the drivers itself. Since it it's not 100% reliable I thought it would fit more into the Networking section again. Apologies if I broke a rule somewhere![/COLOR]

---

