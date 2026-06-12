---
title: "How to disable wifi (so light turns off) on startup on eeepc 701"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by ultragamer2 on 2014-06-27
I have an old eeepc 701 which I want to use for a movie player and I don't need wireless or any other networking and I want to turn wireless off so the light does not come on and it does not use power.

This is what I have tried so far

1. Turning it off in the bios - *works until lubuntu starts then the light comes back on*
2. Blacklisting it in /etc/modprobe.d/blacklist.conf where I wrote "blacklist ath5k - [I]This doesn't have any effect, it still turns on at startup
[/I]
The only thing that works is typing the command "sudo rfkill block wifi" into the terminal but as soon as you reboot lubuntu the wifi is back on again. So I tried putting this in /etc/rc.local both with any without the sudo - [I]doesn't work

[/I]I am a Ubuntu newbie certainly when it comes to any soft of coding or commands but I have read about 10 threads and done what it suggested and nothing works. So I thought of starting my own thread.

I just want to permanently disable wifi so the blue light doesn't come on.

So in short I can disable it in the bios but every time lubuntu starts it turns it back on. So how can I tell Lubuntu not to turn on the wireless adapter?

Any help would be appreciated.

---

### Post by chili555 on 2014-06-27
While the light is on, let's have a look at:```
lsmod | grep ath
cat /etc/rc.local
rfkill list all
lspci -nn | grep 0280
```Thanks.

---

### Post by kalehrl on 2014-06-27
Just right click the network icon in the bottom right corner and untick wireless networking.
It will be remembered after reboot.

---

### Post by ultragamer2 on 2014-06-27
Hello,

Thanks for the replies.

It's not a huge deal about this but it seems like a good time to start learning to do something atleast in lubuntu. :)


By pasting all the lines at once I got this.

ubuntupc@ubuntupc-701:~$ lsmod | grep ath
ubuntupc@ubuntupc-701:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


sudo rfkill block wifi




exit 0
ubuntupc@ubuntupc-701:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no



--------------------------------------


About the networking icon, there is no networking icon at the bottom of the screen (it's lubuntu).
The only icons are speaker, language, keyboard, battery, time and power.

---

### Post by kalehrl on 2014-06-27
Do this to get the icon:
[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by ultragamer2 on 2014-06-27
Thanks, I now have the icon but when I click on it it only shows wired connection 1 so I can't choose any setting for wireless because it's not there, but the wireless light is still on.

Also I removed the non functioning code in blacklist.conf and rc.local and it doesn't make any difference either.

Also I turned enable networking off but the wireless light is still on.

:(

The only thing that turns off the light is [COLOR=#000000]sudo rfkill block wifi but I have to type is in every time manually.

Is there some way I can uninstall the wireless drivers since I don't need wifi?
Then I could turn it off in the bios and lubuntu wouldn't turn it on again.[/COLOR]

---

### Post by chili555 on 2014-06-27
ath5k is not your wireless driver, so blacklisting it is ineffective, it seems. 

How about this one?```
lspci -nn | grep 0280
```

---

### Post by ultragamer2 on 2014-06-27
Thanks, I pasted it into terminal but it doesn't seem to do anything.

On the bottom of the eeepc it says wireless module Atheros AR5BXB63, not sure if that is any help.

I can try another linux distro as long as it runs vlc and fits on the 4gb internal ssd.

---

### Post by chili555 on 2014-06-27
> **ultragamer2 said:**
> Thanks, I pasted it into terminal but it doesn't seem to do anything.

On the bottom of the eeepc it says wireless module Atheros AR5BXB63, not sure if that is any help.Please try:```
lspci -nn
lsusb
```Pick out your wireless device from all the listings and post it here.

---

### Post by ultragamer2 on 2014-06-27
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L2 Fast Ethernet [1969:2048] (rev a0)



ubuntupc@ubuntupc-701:~$ lsusb
Bus 001 Device 004: ID eb1a:2761 eMPIA Technology, Inc. EeePC 701 integrated Webcam
Bus 001 Device 003: ID 0951:1606 Kingston Technology Eee PC 701 SD Card Reader [ENE UB6225]
Bus 001 Device 002: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2014-06-27
> [[COLOR="#FF0000"]0200[/COLOR]]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)Interesting! Usually wireless is listed as 0280 and ethernet as 0200. I don't believe I've ever yet encountered a wireless as 0200. I learn each and every day!

Please amend your /etc/rc.local as follows:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rfkill block 0

exit 0
```That is a zero, not a capital O. After proofreading carefully, save and close your text editor, reboot and give us your report.

For the benefit of all, sudo is not needed in rc.local. I suspect the system doesn't understand the command and bails out rather than trying to parse a malformed request.

---

### Post by ultragamer2 on 2014-06-27
Thanks, I added the line but the blue light still comes on.

:(

It was like this when I read all the other threads about disabling wifi, none of them worked with my eeepc.

---

### Post by chili555 on 2014-06-27
So was the line effective at all?```
rfkill list all
```

---

### Post by ultragamer2 on 2014-06-27
ubuntupc@ubuntupc-701:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2014-06-27
No, it is not yet effective. Please change:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rfkill block all

exit 0
```Reboot and report, please.

---

### Post by ultragamer2 on 2014-06-27
Didn't seem to make any difference.

---

### Post by chili555 on 2014-06-27
Sorry, I'm out of ideas.

---

### Post by ultragamer2 on 2014-06-27
Ok thanks, that's the same idea I got from reading other threads.

I will try running the eeepc 1.7 operating system instead.

---

### Post by kalehrl on 2014-06-27
Try pressing Fn + F2 keys and then check if right clicking gives you an option to enable/disable Wi-Fi.
I've just fired up my eee pc and it disabling Wi-Fi works just fine the way I described it.

---

### Post by ultragamer2 on 2014-06-27
Ok thanks. So it seems that it works.

I actually just spent a while installing Tiny Core Linux and once I installed vlc, nautilus and alsa sound drivers it works great!

It had an option not to install the wifi drivers during installation so now since it is switched off in the bios there are no drivers to turn it back on so the light stays off (and I assume the power consumption).

So I guess I won't be able to test this new method but thanks anyway, hopefully it will be of use to someone else, or I'll try it in the future.

---

### Post by amoun on 2014-11-22
Hi kalehrl

That's fine. I have 14.04 running on an EEEPC 900

1. Wifi on at boot
2. Using Ethernet
3. Right click on networking icon
4. Enable and then Disable wifi
5. Reboot :: No Wifi Light on :-)

Thanks

---

