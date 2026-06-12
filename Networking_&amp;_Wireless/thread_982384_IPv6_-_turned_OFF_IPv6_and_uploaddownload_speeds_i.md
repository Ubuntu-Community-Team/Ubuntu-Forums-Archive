---
title: "IPv6 - turned OFF IPv6 and upload/download speeds increased 4x"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by bmullan on 2008-11-14
I have been puzzled after installing Ubuntu 8.10 in that my wireless
speeds were so SLOW... 

Wireless router is: Linksys wrt160n

Wireless PCI card is: Linksys 

I tried the built-in BCM driver
I tried the windows bcmwl5 driver

nothing made a difference.   I know that my Time Warner Roadrunner downlink is approx 10Mbps and 512kbps uplink.

So... I turned OFF IPv6 on Ubuntu 8.10 using the commands per help system instructions:

**3.3.6.&#8195;IPv6 Not Supported**

[B][INDENT]1. IPv6 is supported by default in Ubuntu and can sometimes cause   problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.[/INDENT][/B]

My uplink and downlink speeds both increased 300-400% !!  Not sure if its a bug with IPv6 implementation or just the conversion btwn IPv6 and IPv4 but the difference was immediate and made world of difference.

From:   

[B][INDENT]1.5Mbps down and 190kbps up
[/INDENT][/B]
To:

**[INDENT]5.8Mbps down and 495kbps up[/INDENT]**

---

### Post by buccaneere on 2008-11-14
Interesting.

Is there a way to test current speed, and speed after the mod?

And if it doesn't help for whatever reason, what is the reversal script?

Thanks!

---

### Post by bmullan on 2008-11-15
to reverse it.. just edit the same file and put the original entry back in.

if you edit it the first time... just comment the original line out with the "#" symbol.

---

### Post by hoopystrag42 on 2008-11-26
Thanks it definitely help me out (probably about a 4-fold increase in download)

---

