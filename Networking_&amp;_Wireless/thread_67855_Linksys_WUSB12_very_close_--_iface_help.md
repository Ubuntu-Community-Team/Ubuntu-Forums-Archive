---
title: "Linksys WUSB12 very close -- iface help?"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by vicG on 2005-09-21
I'm really close to getting my Linksys WUSB12 to work, I just need a little help -- maybe with configuring an interface?

Anyways, I booted up, and dmesg seems to recognize it's there:

prism2 usb_init: prism2_usb.0  0.2.1-pre25 Loaded
dev_info is: prism2_usb

And lsmod knows it's there (dots just for formatting, not sure how to use this board yet)

prism2_usb..........70532.....0
p80211...............30608.....1 prism2_usb

modprobe knows it's there:

modprobe -l prism*

/lib/modules/2.6.10-5-i386/kernel/drivers/net/wireless/prism54.ko
/lib/modules/2.6.10-5-i386/kernel/drivers/net/wireless/prism2_usb.ko

even lsusb knows it's there:

Bus 006 Device 002: ID 066b:2213 Linksys, Inc WUSB12v1.1 802.11b Adapter

So it seems that the Linksys WUSB12 is recognized out of the box, but Ubuntu didn't do anything about it, and that's where I need help from you experts.

ifconfig just has lo and nothing else, iwconfig says "no wireless extensions" for lo, eth0, and wlan0.

I tried (from a root shell):

 iface wlan0 up 

and got:

Ignoring unknown interface wlan0=wlan0

Which isn't nice.  Why is it unknown, and how can I make it known?

I launched that GUI thing (System -> Administration -> Network, IIRC) and all it shows is lo and eth0, and says they're both not configured.  The tool doesn't seem to have a way to add an interface, which is odd.

So here I am.  I think I need to add an interface, but I'm a noob, so what the heck do I know?  The Ubuntu docs say that if iwconfig returns "no wireless extensions" for everything, then "you have a problem" which, while accurate, isn't going to get my arse online. ;)

I monkeyed a bit with /etc/network/interface (interfaces? -- can't remember the exact name).  The man page is written by experts for experts, so what little I gleaned was to try and add:

auto wlan0
iface wlan0 inet dhcp
wireless-essid my_essid

but that didn't do anything after I rebooted, so I rolled the file back to the original.

Does anyone know the exact dance steps to get me on the net?

Thanks for any help!

---

### Post by vicG on 2005-09-21
*bump*  Anyone?

Also, I just grabbed a wireless G card from my wife's Windows PC, and tried to use ndiwrappers, and I'm getting a really strange result.

I installed ndiswrappers using synaptic and pointing at my install CD.  Worked great.

sudo ndiswrapper -i /path/to/rt2500.inf   -- worked fine
sudo ndiswrapper -d 18:14:0201 rt2500 -- worked fine, got some happy message about driver x pointing to device y
sudo ndiswrapper -m  -- worked fine, got Adding "alias wlan0 ndiswrapper to /etc/modprobe.d/ndiswraper"

And then it all fails.  

sudo modprobe ndiswrapper -- hangs the entire system.  I get:
FATAL:  Error inserting ndiswrapper (/path/to/ndiswraper.ko) Operation not permitted
It then returns me to a prompt, and then, after about one second, the prompt (flashing prompt thing) *disappears* and nothing on my system will work. 

I didn't thing you could hang Linux like that.  Ctl-Alt-<any button on the keyboard> does nothing!

Anyways, at this point, I'll take help on either front -- anyone?

---

### Post by mlomker on 2005-09-22
> 
Ignoring unknown interface wlan0=wlan0


They tend to show up as **eth1** in Ubuntu.  You can change that later in /etc/iftab, but hold off until you get things working.

> 
The Ubuntu docs say that if iwconfig returns "no wireless extensions" for everything, then "you have a problem" which, while accurate, isn't going to get my arse online. ;)


That usually means that the driver isn't loaded.

**dmesg | grep prism** give you anything?

I think that particular card is a modified Prism chipset that'll only work with ndiswrapper.  Do some searches here and on Google for your card and you'll discover what other people are doing.

---

### Post by mlomker on 2005-09-22
> sudo ndiswrapper -d 18:14:0201 rt2500 -- worked fine, got some happy message about 

There's a native driver for that card but it has to be compiled/installed.  Ndiswrapper shouldn't hang your system, though...obviously.

---

### Post by vicG on 2005-09-22
[QUOTE=mlomker]

**dmesg | grep prism** give you anything?
[/QUOTE]

Yes:

prism2 usb_init: prism2_usb.o 0.2.1-pre25 Loaded
dev_info is: prism2_usb

[QUOTE=mlomker]
I think that particular card is a modified Prism chipset that'll only work with ndiswrapper.  Do some searches here and on Google for your card and you'll discover what other people are doing.[/QUOTE]

Yup -- in progress

---

### Post by coccoon55 on 2007-12-06
newbie here working on same issue.  wusb12 card.  got about the same results so far.  Did you ever get it resolved?

---

### Post by coccoon55 on 2007-12-07
I got my wusb12 working.  It linked to the neighbors unsecured linksys router.  I was fighting the network disabled issue for several days.  I really, really wish I knew exactly what I did to get it working.  I don't need the wireless.  Have my own system and connected wired but I loath not knowing how it works/worked.  But at least its working.  I messed with ndiswrapper.  Said it was already loaded.  Did the kwifiManager but that only let me know I was connected and what access is available.  Only thing I've noticed different in all the screens.  In network settings it now indicates the Wireless connection has roaming mode enabled.  Could it have been that simple?

---

