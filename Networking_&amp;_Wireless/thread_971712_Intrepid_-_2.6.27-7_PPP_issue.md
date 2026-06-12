---
title: "Intrepid - 2.6.27-7 PPP issue"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Speedster on 2008-11-05
I'm having a really strange problem with my DSL connection under the 2.6.27-7 kernel installed with Intrepid. Basically the connection establishes fine, and a lot of sites work without problem but there are a large number that don't work, e.g
 - store.apple.com
 - youtube.com
 - MSN messenger
 - [www.anz.com.au](www.anz.com.au)

If I set GRUB to boot 2.6.24-21 (this was upgraded from Hardy) then after a reboot everything works as expected. This is the ONLY change made between connections.

I have tried the following in an attempt to narrow down the issue:
 - reduced MTU from 1492 to 1460 and 1420
 - rebuilt as a clean 32-bit install
 - rebuilt as a clean 64-bit install (not upgraded from Hardy)
 - turned off tcp_timestamps and tcp_sack

None of the above has worked, the ONLY workaround at the moment is to boot 2.6.24-21. To me this indicates a kernel issue but I'm completely stumped as to what it could be. I've attached a couple of PCAP outputs that show what is being sent out the PPP connection.

Any help would be appreciated!

---

### Post by Speedster on 2008-11-08
Bump. Noone?

I'll also add that I tried a simple iptables MASQUERADE rule rather than the complex firewall I have in place now and no go.

I'd rather not file a bug in case it is a simple fix, but considering nobody else can shed any light on this I may have to. :(

---

### Post by Turms on 2008-11-08
you could try also echo 0 > /proc/sys/net/ipv4/tcp_window_scaling (in addition to what you did before, that is setting to 0 both tcp_timestamps and tcp_sack)
if it doesn't work i think you should reopen kernel.org bug 11721 :
[http://bugzilla.kernel.org/show_bug.cgi?id=11721](http://bugzilla.kernel.org/show_bug.cgi?id=11721) .
in order to speed up things i think you should compile first kernel 2.6.26 (from kernel.org [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.tar.bz2)) to see if that problem was already present in that release, i advise you to compile making use of kernel-package and doing make oldconfig just accepting everything it proposes to you, and afterward please follow what i did in comment 42 of the a/m bug report, obviously changing what is different in your set up (my wan eth is eth0, maybe your is different, the kernel releases are obviously different, etc.)

aldo

---

### Post by Speedster on 2008-11-09
2.6.26 source compiled works perfectly.

Attached are the tcpdump outputs for the various scenarios.

---

