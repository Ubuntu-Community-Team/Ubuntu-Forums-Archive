---
title: "Can't resolve squat with ethernet under 7.10"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by jhmiller42 on 2008-04-27
I've installed 7.10 on my Averatec 3225HS laptop, intending to upgrade to 8.04. (Can't install 8.04 directly because of another glitch entirely -- don't ask.) But now I can't upgrade because I can't resolve anything using the wired connection to my Buffalo WHR-54G-HP.

I mean nothing. Nada. It's not a DNS problem; I can't even resolve the router itself using its IP.

And it's doubly frustrating because I know it works. During the 7.10 (alternate) install half an hour ago, DHCP configuration went off without a hitch, the time-synch worked as far as I could tell, and when I boot into Ubuntu it tells me exactly how many updates are available...but can't download them.

I'm such a noob that I don't even know where to begin. Pointers?

---

### Post by jhmiller42 on 2008-04-28
Here's my ifconfig. Excuse the pic -- I'm working with a broken wrist, can't type too quickly.

[IMG]http://img87.imageshack.us/img87/7236/dscf2646lp4.jpg[/IMG]

---

### Post by Monicker on 2008-04-28
That 169.254.x.x address means no dhcp address was received from the router.  Right now your machine is not on the local network.

I would start with checking physical connectivity.  Verify the network cable is plugged in snugly.

---

### Post by jhmiller42 on 2008-04-28
Works fine when I boot into XP, so there's a connection. I thought I knew enough about networking to get by, but this has me utterly stumped.

---

### Post by Monicker on 2008-04-28
> **jhmiller42 said:**
> Works fine when I boot into XP, so there's a connection. I thought I knew enough about networking to get by, but this has me utterly stumped.

Are you using XP as a dual boot form the same laptop on which Ubuntu is installed?

If this is a wireless connection, please show the output of the following commands:

```
sudo lspci -v
sudo iwconfig
sudo ifconfig -a
```

---

### Post by jhmiller42 on 2008-04-28
Nope, it's the wired connection. The wireless is a whole 'nother story -- I've got the Broadcom curse. But I can't tackle that problem until I handle this one.

[edit] Yes, same laptop. So the identical physical setup works fine under XP.[/edit]

---

### Post by joes_meat on 2008-04-28
Sounds like the same problem I'm having.

I wouldn't try to fix the wireless before fixing this networking problem.

I've tried with two different NIC's with exactly the same results - so it's a networking problem, not a card problem. I suspect you'll have the same issues with the wireless card too, regardless of drivers.

---

### Post by jhmiller42 on 2008-04-28
Well, let me know if you find anything! I've no idea what to do about utter DHCP failure....

---

### Post by Monicker on 2008-04-28
> **jhmiller42 said:**
> Well, let me know if you find anything! I've no idea what to do about utter DHCP failure....

What is shown if you manually try to initiate a dhcp request from the terminal?


```
sudo ifconfig eth1 down
sudo dhclient eth1
```

---

### Post by joes_meat on 2008-04-28
This might not be much help, but my ethernet is back up!

I don't know which of the things I did helped, but networking is fully functional now.

Via Rhine is eth0
Intel pro 100 is eth1

- I installed a second ethernet card (eth1). That card had the exact same problem. I decided it was not a card or diver problem. It was a system networking problem.
- I blacklisted ipv6
- I removed all entry of eth0 in /etc/network/interfaces. It now looks like:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet ipv4ll
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

### NO MENTION OF ETH0

Then in network settings I enabled roaming on eth0 and bam! Fully working ethernet. I restarted a few times to make sure it wasn't a fluke and it's fine. Maybe someone with a bit more knowledge can figure out which of the things I've done fixed the problem.

It could be:
- Blacklisting ipv6
- Removing entry in /etc/networking/interfaces
- Installation of a second NIC - possibly changing IRQ resources/conflicts?

I hope this helps.

---

### Post by jhmiller42 on 2008-04-28
Weirder and weirder. It hardlocks, with the capslock and i/o lights blinking endlessly. No cursor movement. It's totally frozen.

[edit] Yep, confirmed. Running dhclient freezes her up.[/edit]

---

### Post by Monicker on 2008-04-28
> **jhmiller42 said:**
> Weirder and weirder. It hardlocks, with the capslock and i/o lights blinking endlessly. No cursor movement. It's totally frozen.

[edit] Yep, confirmed. Running dhclient freezes her up.[/edit]

Very strange.  I've never seen a machine freeze up while trying to run dhclient before.  Perhaps someone else here has run into this particular issue.

---

### Post by jhmiller42 on 2008-04-28
> **Monicker said:**
> Very strange.

Maybe it's the off-brand notebook, but a lot of responses to my Linux questions begin that way....

---

### Post by jhmiller42 on 2008-04-28
Not to spam, but I just had an idea. How integrated is the networking stack? Specifically, is there any reason to think my nonfunctional *wireless* NIC -- which isn't what I'm trying to get working here -- could be contributing to the problem?

The firmware and drivers for the wireless chip, a Broadcom 4306, are completely borked, and prevented me from running the 7.10 liveCD or any form of the 8.04 installation. The latter hangs on an infinite loop as per [this thread]("http://ubuntuforums.org/showthread.php?t=765616").

---

### Post by jhmiller42 on 2008-04-29
Anybody? Any ideas why dhclient would freeze a system? Or why DHCP would (apparently) work flawlessly during the alternate install but not after?

---

### Post by jhmiller42 on 2008-04-29
OK, problem solved, apparently. For the unlucky few with this issue:

It's an IRQ conflict, a [known issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48263") with certain revisions of the VIA Rhine-II NIC and the Linux kernel. The solution is to add the modifier 'acpi=noirq' to the kernel line in GRUB's menu file, located at '/boot/grub/menu.lst'.

If, like me, you're a complete rookie, it may also help to know that you'll have to edit said file by running 'gksudo gedit /boot/grub/menu.lst' in a terminal; otherwise you won't have permission to modify the file.

---

