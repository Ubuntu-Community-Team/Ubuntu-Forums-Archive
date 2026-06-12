---
title: "thinkpad W500 ethernet"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by Bashar &quot; on 2008-10-18
Hello,
i have installed 8.10 and it detected almost everything but my ethernet card does not work

as as per the vendor its:
Intel 82567LM Gigabit Network Connection (Boazman), PHY, PCIe x

any advise how to get it working ?

Thank you

---

### Post by Bashar &quot; on 2008-11-02
it works now with the new release fix

for those who might search

---

### Post by inf32n0 on 2008-11-02
Hey Bashar,
I have been trying to install ubuntu 8.10 for two days now on my thinkpad W500 but i cant get the graphical interface to work!

So, I installed 8.04 and it worked, but with only ethernet working not wireless. After i installed the updates, my ethernet stopped working, so now i have no internet lol.

8.10 is supposedly supposed to work "out of the box" for both ethernet and wireless.

Did you have any problems installing 8.10? i tried both the desktop and alternate iso's for 8.10.

I searched all over the net and these forums trying ALOT of solutions to getting the graphical interface to work but no luck. so now i am stuck with 8.04 without internet:mad:

Can you please provide me with exactly how you installed 8.10 and if you had the same graphical interface problem, can you let me know how you fixed it?

Help will be MUCH appreciated

Thanks in advance

---

### Post by inf32n0 on 2008-11-03
Ok i figured it out.

I was having the same problems with my system.

-> the problem is, since the new thinkpads have switchable graphics, ubuntu is confused with which graphics card to use and appearently can't locate the appropriate one.

after reading the message carefully it says that no PCI Express display found or something like that, don't remember the message exactly

to solve this problem:

SOLUTION: Go into BIOS and change your display settings to:

Default Primary Video Device = PCI Express
Boot Display Device = ThinPad LCD
Graphics Device = Discrete Graphics
OS Detection for Switchable Graphics = Disabled

This worked for me

I didnt try different combinations of these setting. I might try them and post the results when i have time.

---

### Post by klausner on 2008-11-04
> **Bashar " said:**
> it works now with the new release fix

for those who might search

Explain. What new release? You said you were already running 8.10.

I have a Sony Vaio Z-Series with 8.10, and the 82567LM Gigabit Ethernet controller, and I cant get the system to use configure Ethernet. 
> sudo lshw -C network returns:>  *-network UNCLAIMED
       [INDENT]description: Ethernet controller
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03[/INDENT]

Editing /etc/network/interfaces doesn't help.

How did you get yours to work?

---

### Post by Bashar &quot; on 2008-12-09
i meant i was running 8.10 beta and when release came out it worked well

---

