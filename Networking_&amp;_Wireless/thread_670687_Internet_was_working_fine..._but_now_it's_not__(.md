---
title: "Internet was working fine... but now it's not : ("
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Darkest Wolf on 2008-01-17
Exclamation  Internet was working fine... but now it's not : (
Ok, Heres the situation

I'm a new user to Xubuntu 7.10

I installed it yesterday, and I was able to get on to my wireless Internet connection with no problems. Halfway through today, while I was online it just disconnected. When I go to connect the option to use a wireless networks isn't there.

Previously I just clicked on the network symbol, and chose my network, but no it's not there, nor are any other wireless networks. When I click on manual, the wireless profile isn't there, just wired and Dial up.

I know it's not the router or network, because I can still access them on another (Windows) laptop. And I don't think it's a driver issue because they were working fine yesterday.

I put the live CD back in, to see if it would work there (Because it used to) and I have the same problem. I don't know what to do.

I know it's probably something really simple, but I'm new to Xubuntu and don't know what to do about it, I've looked online, but can't find much.

So, any help?

ps
I know that this is a Ubuntu forum, but from what I understand Xubuntu is incredibly similar, and any help you can offer should still work.. right?

---

### Post by Elmer Fudd on 2008-01-18
Same thing happend to me. Everyting was working great since 7.10 came out. Right after I tried to load KD4 and the new NVIDIA drivers, my wirerless and audio adapters stoped working. They show "UNCLAIMED" by a driver. I have been unsuccessful in getting them restarted-even after unloading KDE4 and the new NVidia modules.  Had you just done any kind of an upgrage prior to your failure?
If I boot from a new kubuntu live CD, everything works, so I know it is not a hardware problem.

HP dv9000t, Intel 3945 wireless. Kernel 2.6.22-14-386

---

### Post by pytheas22 on 2008-01-18
Could you both please post the output of:

```
iwconfig
```

and

```
lspci
```

And if you already know, what kind of wireless cards do you have (manufacturer and chipset if you know)?

As for this:
> 
I put the live CD back in, to see if it would work there (Because it used to) and I have the same problem. I don't know what to do.

it sounds like maybe there is a physical or a BIOS switch on your computer to turn your wireless card on or off.  Did you change that setting?

---

