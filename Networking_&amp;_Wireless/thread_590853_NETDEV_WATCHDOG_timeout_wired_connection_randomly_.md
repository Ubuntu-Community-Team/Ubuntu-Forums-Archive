---
title: "NETDEV WATCHDOG timeout: wired connection randomly breaking"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by Mr. Tos on 2007-10-25
My Ubuntu 7.10 randomly loses its network connection, without any contingency on what I do. Sometimes it takes only 30s after booting, sometimes it works fine for up to an hour. When it happens, only a reboot restores connection (so logging out, eth0 down / up, /etc/init.d/network restart doesn't work).

When it happens, I can't even ping my router anymore (only 127.0.0.1 and my own IP) and the system log spams "NETDEV WATCHDOG: eth0: transmit times out". No other errors. I don't have any network problem under windows, and this one appeared upon a reinstall of ubuntu. So it's not simply a network, cable or router malfunction.

Comparing things like ifconfig, netstat, arp, ethtool, the only difference I can see before and after the disconnect is in the arp output, where the entry becomes "('incomplete)". Manually setting it through "arp -s IP MAC" restores the entry (with an 'M' added in the flag masks though) but not the connection.



What is happening here? Is some driver or program putting my network card into an infinite loop (assuming the watchdog timer is that of my network card)? What other diagnostics should I run?

---

### Post by Mr. Tos on 2007-10-26
Hmm after some searching and excluding other possibilities, I think this is a kernel bug that was fixed in .23. 

From release notes:
>  Change INT0 trigger mode from edge-sense mode to level-sense mode,
    in order to fix the following timeout error:
      'NETDEV WATCHDOG: eth0: transmit timed out'.

It seems to be an interrupt error indeed ("Tx timed out, lost interrupt?"), but there aren't any conflicts, or errors related to APIC. The interrupts look perfectly fine. So this kernel fix is my last hope :/

Compiling kernel, will post whether that solved it...

---

### Post by Mr. Tos on 2007-10-27
using the .23 kernel seems to have fixed it, no disconnects so far :)

---

### Post by rbrisbourne on 2007-10-28
Just found a similar problem on upgrade (Edgy was fine).  Googling "netdev watchdog" got thousands of hits going back several years.

The following in /var/log/messages may or may not throw some light- it seems to come up at about the time eth0 disappears.

Oct 28 21:42:50 Dennis kernel: [ 2935.205610] Call Trace:
Oct 28 21:42:50 Dennis kernel: [ 2935.205612]  <IRQ>  [__report_bad_irq+30/128] __report_bad_irq+0x1e/0x80
Oct 28 21:42:50 Dennis kernel: [ 2935.205638]  [note_interrupt+643/704] note_interrupt+0x283/0x2c0
Oct 28 21:42:50 Dennis kernel: [ 2935.205645]  [handle_fasteoi_irq+221/272] handle_fasteoi_irq+0xdd/0x110
Oct 28 21:42:50 Dennis kernel: [ 2935.205651]  [do_IRQ+123/256] do_IRQ+0x7b/0x100
Oct 28 21:42:50 Dennis kernel: [ 2935.205654]  [default_idle+0/64] default_idle+0x0/0x40
Oct 28 21:42:50 Dennis kernel: [ 2935.205658]  [ret_from_intr+0/10] ret_from_intr+0x0/0xa
Oct 28 21:42:50 Dennis kernel: [ 2935.205660]  <EOI>  [unix_poll+0/176] unix_poll+0x0/0xb0
Oct 28 21:42:50 Dennis kernel: [ 2935.205670]  [default_idle+41/64] default_idle+0x29/0x40
Oct 28 21:42:50 Dennis kernel: [ 2935.205674]  [cpu_idle+112/192] cpu_idle+0x70/0xc0
Oct 28 21:42:50 Dennis kernel: [ 2935.205679]  [start_kernel+645/784] start_kernel+0x285/0x310
Oct 28 21:42:50 Dennis kernel: [ 2935.205685]  [x86_64_start_kernel+286/352] _sinittext+0x11e/0x160
Oct 28 21:42:50 Dennis kernel: [ 2935.205689]

---

