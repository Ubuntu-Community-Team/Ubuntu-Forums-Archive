---
title: "No ethernet connection at all"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Jamax_us on 2007-02-22
I am 2 hours into Linux and have installed Ubuntu 6.10. When looking at
System>Administration>Networking I see a wired connection with a DHCP address enabled (shown by check mark and also by propertied enable this ....

I can't get anywhere, I have opened a terminal window and run ping -c 5 [www.gentoo.org](www.gentoo.org) and get unknown host. I have also tried ping -c 5 192.168.50.7 (another machine on the local network) and get Network is unreachable.

can someone please point me in the right direction. I am reaching out here so that I can reach out!

---

### Post by Jamax_us on 2007-02-22
I should add that the cable is plugged in and the light is green!

Looking in the device manager I see SMC2-1211TX and it appears to have all sorts of values I don't understand, but they are there!

I have searched and see lots of things for routers and also Firefox, but this problem appears to be before that.

---

### Post by Jamax_us on 2007-02-22
OK, if ran lshw and it shows the Ethernet interface as DISABLED, however, as above the network settings shows it as enabled.

I ran sudo ifconfig eth0 up and was told device or resource busy
running ifconfig eth0 down then up again did nothing.

---

### Post by Jamax_us on 2007-02-22
Searching the forums I found ifdown eth0 && ifup eth0 this gives
failed to open temproary statefile /var/run/network/.ifstate.tmp: Permission denied. I ran the above command as sudo.

This is a clean install on an old machine, no dual boot no other system.

---

### Post by chili555 on 2007-02-22
Please try sudo modprobe 8139too followed by sudo ifup eth0. If that works, you can add 8139too to the file /etc/modules.

---

### Post by Jamax_us on 2007-02-22
Thanks for responding! I tried your suggestion. on the ifup
SIOCSIFFLAGS: Device or resource busy,

Then on DHCPDISCOVER send_packet: Network is down

---

### Post by chili555 on 2007-02-22
Please let me see the full output of sudo ifconfig -a.

We'll get it!

---

### Post by Jamax_us on 2007-02-22
Man, that's a lot of typing, let me get it for you.

---

### Post by chili555 on 2007-02-22
Before you type, check this out: [http://www.linuxforums.org/forum/linux-newbie/33681-linux-internet-networking.html](http://www.linuxforums.org/forum/linux-newbie/33681-linux-internet-networking.html)

---

### Post by Jamax_us on 2007-02-22
sudo ifconfig -a returns

eth0
[INDENT]Link encap:Ethernet HWaddr 00:10:B5:65:09:9A
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0,0 b)
Base address: 0x4000[/INDENT]

lo
[INDENT]Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:60 errors:0 dropped:0 overruns:0 frame:0
TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4492 (4.3 KiB) TX bytes:4492 (4.3 KiB)[/INDENT]

sit0
[INDENT]Link encap:IPv6-in-IPv4
NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0,0 b)
Base address: 0x4000[/INDENT]

---

### Post by Jamax_us on 2007-02-22
OK so that thread recommends 
[B]In the bios in the boot section there lies a setting called Plug & Play O/S: Yes/No
Set this to NO[/B]

can you please give some instructions how to do this?

---

### Post by Jamax_us on 2007-02-22
OK, my brain was stuck in linux, I looked in the bios and don't have any PnP settings. I do have an os setting and it was set for windows xp/2000. I changed it to other and it seemed to affect the display of ubuntu. I allowed me to login but then the screen when "wacky".

I turned the bios setting back to windows.

Since I have just started I think I will try changing the setting back to other and reinstalling. Before I do, any other ideas?

---

### Post by chili555 on 2007-02-22
Boot again under "operating system: other" and when it's all fully booted, see if the system will try to fix your display. As Radar used to say, "Wait for it."

If it just stays wacky, press Ctrl-Alt-F1 and you'll get a login prompt. Just for grins, do ping -c3 [www.google.com](www.google.com). If you get any message at all record it and let me know the shorthand version. Then we can try to fix the display.

---

### Post by Jamax_us on 2007-02-22
So I don't qualify by age but - impetuous youth! I changed the bios settings and went for the reinstall. When the os booted off the cd I was able to get to the internet so there is somethign there.

I am now installing to a clean drive. I will let you know one way or the other.

That Radar, he was something wasn't he.

---

### Post by Jamax_us on 2007-02-22
Hey Chili555 thank you for your guidance and help.

The bios change and reinstall was the business, now I am in business. Installed Samba and accessed my windows share.

All is well with the world! This Ubuntu is very nice indeed.

Again, thank you

---

### Post by chili555 on 2007-02-22
Thanks for your kind comments! Welcome to the party!

---

