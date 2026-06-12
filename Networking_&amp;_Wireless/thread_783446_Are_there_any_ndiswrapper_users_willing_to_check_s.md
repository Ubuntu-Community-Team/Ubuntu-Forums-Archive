---
title: "Are there any ndiswrapper users willing to check something for me?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by caljohnsmith on 2008-05-05
I'm trying to figure out whether changing the MTU (maximum transmission unit for a tcp packet) is even supported with ndiswrapper. I can't seem to change it for my wireless card, a TEW-423PI, but I don't know if it's a limitation of my card/driver combo or whether ndiswrapper is the culprit; I haven't been able to find anything in the ndiswrapper documentation about MTU limitations, but maybe I missed it.

If there is someone willing to check their card, in case you aren't familiar, just do a "ifconfig" to find what your MTU is first (for most people using a DSL type connection it will be 1500). Then try changing it with "sudo ifconfig wlan0 mtu 1400" (where wlan0 is your wireless interface, might also be eth1 or something like that depending on your setup). Then do ifconfig again and see if the change stuck.

Anybody have any success doing this? Thanks for any help! :)

P.S. For anyone who might be reluctant to try changing their MTU, note the above command does not permanently change your MTU; it will be back to the same as it was before on reboot unless you modify your /etc/network/interfaces file to change the MTU permanently. And if you are successful changing your MTU with the command, you can always change it back with the same command to avoid rebooting. :)

---

### Post by Ayuthia on 2008-05-05
I tried it out and it seemed to work fine for me.  I did a few things online and it stayed at 1400.

---

### Post by caljohnsmith on 2008-05-09
> **Ayuthia said:**
> I tried it out and it seemed to work fine for me.  I did a few things online and it stayed at 1400.
Thanks, Ayuthia, for taking the time to check. If it works for your card, then my problem must be with my card/driver and not ndiswrapper. I appreciate the help. :)

---

