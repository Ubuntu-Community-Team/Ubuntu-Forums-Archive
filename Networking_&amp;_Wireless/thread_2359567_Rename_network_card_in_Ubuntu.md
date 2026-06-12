---
title: "Rename network card in Ubuntu"
date: 2017-04-25
forum: Networking &amp; Wireless
---

### Post by Gascogne on 2017-04-25
Have installed Ubuntu 16.04 LTS and have 3 different network cards install which I would like to rename.

Running the command ifconfig -a they show up with the following names:

enp3s0
enx6c198fb17147
enx6c198fb15a57

Want to rename them to eth0, eth1 and eth2 but have not been able to find a solution that works.

---

### Post by TheFu on 2017-04-25
There are multiple ways to do this, but it would be better to learn to use the newer naming convention, if possible.  It isn't going anywhere. [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) explains. If the issue is with commercial software, contact the vendor and see what they recommend.

Ok - so after that careful consideration, you still want to change the name, then near the bottom of that link are 3 methods which work. I'm using the grub method. ;)

---

### Post by Gascogne on 2017-04-26
> **TheFu said:**
> 3 methods which work. I'm using the grub method.

The link did explain some things but I am not familiar with the grub method?

---

### Post by sisco311 on 2017-04-26
I guess, by the grub method, TheFu refers to the 3rd method in the " I don't like this, how do I disable this? " section of the link. 


You have to pass the "net.ifnames=0" boot parameter to the kernel. If you are using GRUB2, then you can follow this instructions:  [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)


I'm still curious why do you want to do this and I'm also curious why TheFu does this. :)

---

### Post by TheFu on 2017-04-26
> **sisco311 said:**
> I'm still curious why do you want to do this and I'm also curious why TheFu does this. :)

Some scripts *expect* certain device names and I'm lazy.  Typing 4 characters versus 6 characters (3{tab}1{tab}1{tab}) just sucks. On my only 16.04 machine, I change networks all the time and need to change routes, IPs, bridges, etc ALL-THE-TIME on networks that I've never been on before. It gets tiresome.  I have 20+ yrs of knowing which network eth0, eth1, eth2, eth3, wlan0 are on. 

On systems that don't move, I wouldn't touch it.

There are lots of network complexities like this for me. I purge network manager, since it always gets in the way.  I'm usually on at least 2 networks, sometimes 3 with my presentation netbook.  Non-trivial networking.  

I switched from MS-Office when they introduced the ribbon too.  Similar issue.  I never saw any reason to change.
If I could, I'd purge the resolvconf crap too. Just gets in the way for me.

More and more, I find the core distros forcing solutions onto everyone to problems that 99% of the world doesn't have.  However, I was an early adopter of UUIDs/Labels for drive mounting. ;)  I HAD that issue.  

I'd love it if they fixed SPICE and made it work easily over a secured network.

</rant>

---

