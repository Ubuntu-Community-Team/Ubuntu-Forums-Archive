---
title: "ndis drivers and hardware present, but no wlan0?"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2005-07-27
I installed ndiswrapper the same way I did on my old laptop, where it worked, and everything looks great.
ndiswrapper -l produces:
Installed ndis drivers:
bcmwl5  driver present, hardware present

ifconfig returns:
eth0  {bunch of stuff}
lo {bunch of stuff}

but *no* wlan0!

am I doing something wrong?

System>administration>networking does not show my wireless device either.

It just seems odd because it feels like everything is working fine, minus the fact that I cannot find/access wlan0

(and yes, I have wireless-tools installed and have rebooted a few times after adding ndiswrapper to /etc/modules

---

### Post by mad_scientist03 on 2005-07-27
Try doing a 'lspci'. Does it find your wireless card? Post the output if you're not sure.

---

### Post by OneSeventeen on 2005-07-27
[quote=lspci]
0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)
[/quote]

[quote=iwconfig]
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[/quote]

[quote=ndiswrapper-l]
Installed ndis drivers:
bcmwl5  driver present, hardware present
[/quote]

Any ideas?

---

### Post by mad_scientist03 on 2005-07-27
What's the laptop model? Do you have ACPI enabled?

---

### Post by OneSeventeen on 2005-07-27
It is an HP zv6000 with an AMD Athlon 64, but I'm running the 32 bit version of Hoary.

This is a replacement laptop, and my old one (same model, different cpu) ran the 64 bit version of Hoary, and the 64 bit version of the same driver I'm using now worked perfectly.

I used the same guide to install ndiswraper this time as I did last time.  The only difference is that when I went to the network dialog box wlan0 was there, and during this try it isn't.

---

### Post by JayCnrs on 2005-07-27
Did you try sudo modprobe ndiswrapper, see if there are any errors that show. Then check to see if wlan0 shows in System-->Administration-->Networking. If it shows in here go back to the terminal and type ndiswrapper -m

---

### Post by OneSeventeen on 2005-07-27
```

root@tigershark:/ # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
root@tigershark:/ # modprobe ndiswrapper
root@tigershark:/ # ndiswrapper -m
modprobe config already contains alias directive

root@tigershark:/ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:73:1C:14
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe73:1c14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2675789 (2.5 MiB)  TX bytes:1033406 (1009.1 KiB)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5123186 (4.8 MiB)  TX bytes:5123186 (4.8 MiB)

```

still no wlan0

---

### Post by mad_scientist03 on 2005-07-28
Do you know if ACPI is enabled on your laptop? If ACPI is disabled, it will definitely affect your ability to use your wireless card.

---

### Post by OneSeventeen on 2005-07-28
It shouldn't be disabled, but what I do know is I'm a goof and don't know how to read log files.

Apparently the problem was "driver couldn't intialize device".

A quick [www.google.com/linux](www.google.com/linux) brought me to another thread over at linuxquestions, which offers the solution:

[solution](http://www.linuxquestions.org/questions/showthread.php?postid=1756590#post1756590)

Apparently all you need to do is download the **entire** driver package and unpack **all** of the files, not just the .inf and .sys files.  After doing that, removing the old drivers from ndiswrapper, installing the new, modprobing, and **rebooting**, it works perfect!!!

(go to that thread for more details, and for a link to a *very* functional copy of the drivers!)

---

