---
title: "[SOLVED] Very weird problem with my internet connection"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by daanbrg on 2008-08-26
Hi everybody,

On my main computer (I'm using right now), I'm running Ubuntu 8.04 for almost 3 months now and I must say that I love it. It's simple, and I already know how the terminal works because I used Ubuntu before...

So, let's get to the point. I have a Sitecom Wireless Range Extender connected to the LAN-port of my computer. Why did I do that: my house runs on a wireless network which shares the internet connection and you can share files over it. One problem: my room is a dead point and thus I don't have any reception of signal when I use one of those 'USB Networking Sticks'. So that's why I bought the Wireless Range Extender and connected it to my computer (that was a year ago, at that point, I didn't had this computer yet and the computer I had in that time was running Windows XP Home Edition). It worked beautifully, and I (I mean this!!) NEVER had ANY problems with it.

After about a half year, that computer didn't worked for me any more, because it only had 64MB of RAM and a Pentium Celeron with the speed of a Pentium 3... so I got this one from eBay. Beautiful computer with pretty nice specifications and a very good graphics card (which is supported beautifully within Ubuntu, it's an NVidia Gforce).

I installed Ubuntu on it (Windows XP didn't run so well), and I connected it to the Wireless Range Extender. It worked, and I had a good internet connection.

But that same day, I would find out that something was wrong with either Ubuntu OR the computer; every time when my internet connection got working hard (like downloading music or watching a video on YouTube), it disconnected. You didn't noticed it at the top of the screen, because the network monitor still just showed the 'connected image' (two black screens, you get my point). So I unplugged the Wireless Range Extender and connected it again. The internet worked again.

And that's actually the story so far, because nothing happened, nothing got solved, and I'm getting a little angry, because sometimes it's really inconvenient and always it's **_*REALLY ANNOYING!!!*_**

So, does anybody knows what I can do about this? If this can be solved, well, that would be great.

Please let me know what I need to do, and I'll get back to you as fast as my hands can write the response ;)

Daan.

PS: My system specifications:

PC Model: Medion Titanium MD 8000
Processor: Intel Pentium 4 running at 2.66 GHz, 533 MHz Front Side Bus 512KB Secondary Level Cache
Motherboard: 3 PCI slots, 1 AGP, 8x slot, 2 DDR RAM slots (max. 2GB)
Memory: Samsung 256 MB DDR 333MHz (in one module)
Video card: nVidia GeForce 4 with 128 MB DDR SDRAM
Hard drive: Seagate Barracuda, with 120 GB hard drive space when empty.
Ultra ATA/100
Running at 7200 RPM
Average seek time: 9.4 ms
Drives:
[LIST]
[*](unknown DVD-RW burner, it's not branded)
[*]Artec/Ultima DHI-G40 (DVD-ROM drive 16x) with firmware 3.10
[/LIST]
Network adapter: SiS 900-Based PCI Fast Ethernet Adapter running at 100Mbps, it's integrated on the motherboard
Connectors:
[LIST]
[*]5x USB 2.0 (3 front, 2 rear)
[*]3x FireWire/IEEE1394 (1 front, 2 rear)
[*]1x S-video IN (front)
[*]1x S-video OUT (rear)
[*]1x Composite IN (front)
[*]1x Composite OUT (rear)
[*]1x Game Port (front)
[*]2x Audio IN (1 front, 1 rear)
[*]2x Microphone (1 front, 1 rear)
[*]1x Digital Audio IN (rear)
[*]1x Digital Audio OUT (rear)
[*]1x Ethernet 100 Mbps (rear)
[*]1x 9 pin Serial Port (rear)
[*]1x Parallel Port (rear)
[*]2x VGA (dual screen mode, so you can do 2 things at once, rear)
[/LIST]

---

### Post by jigsaws on 2008-08-26
Can you ping extender after connection "hangs"?
Try to check it with another computer - you will know if the problem is with your computer.
You can also check it with any "live cd" distribution - you will know if the problem is with your Ubuntu installation.
It can be hardware problem - i.e. with power suply of extender.

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> Can you ping extender after connection "hangs"?


I'll check that, but for that the connection first needs to hang :)

If I connect the UTP cable from the extender to a different computer, the computer can go on the internet and access the network hard drive, so probably it's either Ubuntu or my computer.

I've had this problem with my other (older) computer before, that was running Ubuntu 7.10 and was giving ***excactly*** the same problem. I tried reinstalling - didn't helped out.

The extender is my only option, because I don't have any reception with the standard reception stuff with wireless networking, and I don't want to have cables running all through the house... so, yeah.

Let me know, and I'll let you know when I run in the error and I've pinged the extender.

---

### Post by jigsaws on 2008-08-26
Once more "So I unplugged the Wireless Range Extender and connected it again. The internet worked again."

Did you unplug UTP or power from the extender? It it works ok after unplug UTP and plug it once more?

You can run terminal with ping <Extender IP> and watch your video in the other window. Check if it stops pinging.

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> Once more "So I unplugged the Wireless Range Extender and connected it again. The internet worked again."

Unplugging the power and putting it back in, but replugging the UTP cable also works with me. So probably it's something hardware or software-related on my computer...?

---

### Post by jigsaws on 2008-08-26
Have you any other pci network card? You can install it, configure in Ubuntu and check if it also hangs.

It looks like hardware problem but it can be software.

But first try any othe liveCD distro. Maybe something with older kernel?

One more idea, try this:

echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
(as root - sudo su first, because I'm not sure sudo echo... will works ok with > )

It turns off tcp window scaling - maybe it's problem with large packets.

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> Have you any other pci network card? You can install it, configure in Ubuntu and check if it also hangs.

No, I don't, sorry...

> **jigsaws said:**
> But first try any othe liveCD distro. Maybe something with older kernel?

Ubuntu + older kernel...? And even if so, remember what I said? 'Everytime when I put my connection under pressure like downloading music or something, the connection collapses'. So I can't download a distro :mad:

> **jigsaws said:**
> echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
(as root - sudo su first, because I'm not sure sudo echo... will works ok with > )

It turns off tcp window scaling - maybe it's problem with large packets. 

I'll try that and tell you if it worked. By the way: I have no idea how to log in as root, so I'm first going to try the sudo way, and if that doesn't works, I'll get back to you. I'll get back to you anyway ;)

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> One more idea, try this:

echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
(as root - sudo su first, because I'm not sure sudo echo... will works ok with > )

It turns off tcp window scaling - maybe it's problem with large packets.

Nah, it gives me a 'permission denied':

daan@daan-desktop:~$ sudo echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
bash: /proc/sys/net/ipv4/tcp_window_scaling: Permission denied

So, how do I get in the Root-account :confused::confused::confused:

---

### Post by jigsaws on 2008-08-26
sudo su
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> sudo su
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling

Thanks, I think that he has done it. But now, I'm going to check what happens if I download a big file. This is the output from the terminal:

```
daan@daan-desktop:~$ sudo su
[sudo] password for daan: 
root@daan-desktop:/home/daan# echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
root@daan-desktop:/home/daan# 
```

---

### Post by jigsaws on 2008-08-26
Ok, check if it helps.

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> Ok, check if it helps.

THANK YOU so much! This helped me solve my problem; I've just downloaded 200 MB without any gaps!!

Again: thank you. I'm running in my room like :guitar: haha! ;)

No, just joking about the running. Hey, thanks for solving this and eh... what was the problem?

---

### Post by jigsaws on 2008-08-26
Ok, first if you want it to work after restart you should add one line to /etc/sysctl.conf (I don't remember this file has the same name in Ubuntu, but I think yes):

net.ipv4.tcp_window_scaling = 0

The problem is that your network card or extender don't accept big TCP windows (when there are no problems with transmission your computer make those windows bigger for better performance). But with this parameter kernel knows that should disable windows scaling.

---

### Post by daanbrg on 2008-08-26
> **jigsaws said:**
> Ok, first if you want it to work after restart you should add one line to /etc/sysctl.conf (I don't remember this file has the same name in Ubuntu, but I think yes):

net.ipv4.tcp_window_scaling = 0

The problem is that your network card or extender don't accept big TCP windows (when there are no problems with transmission your computer make those windows bigger for better performance). But with this parameter kernel knows that should disable windows scaling.

It works! Thank you again so much!

---

