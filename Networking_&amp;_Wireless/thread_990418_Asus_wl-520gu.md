---
title: "Asus wl-520gu"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by tweak on 2008-11-22
Not sure if this is the best section to post the question, so forgive me if I've erred.

---

I have an ASUS WL-520GU which I want to plug into my network to share the existing DSL service with my wireless devices. Currently my network devices are just this workstation (wired) and my ipod touch (wireless). The network structure is:

workstation <==> switch <==> modem

If all goes to plan I'll replace my 8 port switch with the router's internal 4 port switch, making the structure change to

workstation <==> router <==> modem (still wired)
ipod <===========/

As a wireless unit, everything is functional. I'm able to connect and authenticate with the ipod, even reconfigure the router through it's web interface using the ipod without any problems.
The issue occurs when I plug the router into the network. If my workstation is plugged into the network at any point (into the router directly or if they both plug into the existing switch), then the workstation has a kernel panic - the full CAPS and Scroll lock LEDs flashing and everything locked up dealy. The time between the two units present on the network to the kernel panic is less than 2 seconds.

In terms of the workstation's configuration, it's running 8.10 as of last night, however the same issue occured with 8.04 earlier yesterday. I ran a dist-upgrade to 8.10 in the hope it was some kernel bug or other software issue which an upgrade would patch, but no luck.

Basically since I have no real time to investigate the network state before the kernel panic, I'm somewhat at a loss as to how to work out what's going on. Haven't managed to turn anything of use up on google either.

My next thoughts are that the workstation's NIC is faulty or incompatible somehow, but surely any issues there would manifest in a more dramatic way if that were the case?


Can anyone give me some ideas or suggestions as to what or how to investigate next? Or similar past experiences and how you resolved them?

Cheers

---

### Post by tweak on 2008-11-22
Output of uname -a:

Linux flare 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

output of lsmod and lspci -v attached

---

