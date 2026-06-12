---
title: "Newbie Ubuntu 20.04 missing wired connections in settings"
date: 2021-06-28
forum: Networking &amp; Wireless
---

### Post by Ianvolin on 2021-06-28
I am burned out

---

### Post by TheFu on 2021-06-28
Desktop or Server?
What hardware?
Which drivers?
What settings?
The big questions are DHCP or static IP?

For answers, you'll want to look up commands.  A few to gather data:

[SIZE=3]What hardware?[/SIZE]
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
inxi -Nxz
sudo lshw -C network
```
Those commands should capture the what drivers too.  No drivers = no ethernet. Fix that first.  BTW, never confuse wired ethernet and wifi. They are extremely different and completely different commands are needed.

For network settings, let's start by doing some ping tests to determine what is and isn't working. Often, a DNS problem seems like a network problem, when it isn't.
* ping the router by IP address
* ping well-know internet IP addresses 1.1.1.1
Do those work or not? 
* ping google.com
Does that work or not?

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) explains why.
Be certain that you look up each command before running it and understand each option. You'll want to learn a little more each day.  I've been learning linux since 1993. Still learning.

I've assumed that the network wasn't working. If it does work, they perhaps the setup was configured for system-level control, not end-user control?  If the end user doesn't control the network, like we'd desire in a multi-user setup or on any server, then there's little reason to show an icon to end users. They wouldn't be allowed to change anything.

---

### Post by dddman on 2021-06-28
???
[ATTACH=CONFIG]288743[/ATTACH]

---

### Post by Ianvolin on 2021-06-28
My hardware: B470 motherboard, Ryzen 7 2700 CPU, 16x2 32 gigs DDR4 at 3000 speed RAM. GTX 750 (old) video card. 1TB SSD

---

### Post by Ianvolin on 2021-06-28
Sorry all for being a pest/pain. I forgot to say, it is a desktop I made a few years ago. I  made a new desktop, but kept my 2080 video card and placed the GTX 750 in my  (Hopefully  Ethernet running soon) Linux PC.  Thank you again for any help that can be passed down.

---

### Post by TheFu on 2021-06-28
If you don't answer the questions asked, we cannot help. Sorry.
[LIST=1]
[*]Run the commands.  
[*]Post the results, wrapping in "code tags", so the output is readable to us.  Code-tag How to:  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
[*] No images for terminal commands. Just text.  Copy/paste ... or select/paste into these forums, if using X/Windows.
[/LIST]

Please.

---

### Post by Ianvolin on 2021-06-28
Forgive me, I don't mean to be ignorant. I shall do my best to run the commands as requested. I am honestly grateful for the time and help. PTSD is not fun. I shall post them once I figure this out. Thank you again, to everyone. :)

---

### Post by Ianvolin on 2021-06-28
Okay, I am far too green for this. I am finding it rather hard to understand this, and (no violin) the flashbacks/PTSD health is kicking me. I am sorry I wasted everyone's time. Thank you all the same.

---

