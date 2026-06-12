---
title: "No network interface"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by SWoodhall on 2007-01-13
I've been using Kubuntu for some time on my laptop and am a recent convert from XP, so quite new to Linux.

Basically I have an old Dell PE600SC which I wanted to install Ubuntu server on. After the install though my network card is not detected (an Intel PRO/1000). As a newbie to linux I am a bit stuck as to what to do to resolve this. I checked /etc/network/interfaces and it just shows the loopback.

Any gurus out there who could advise how I can do this? I guess I need to install a driver, but I'm not sure how to do this, particularly without X (can't quite shake the Windoze habit, but would like to!)

Thanks very much

---

### Post by SWoodhall on 2007-01-15
OK, I've moved this on a bit since the original post. I have found the drivers source from Intel (although it's for an earlier kernel version so not sure if this will work?)

The drivers had a guide on how to install them, but I can't do a make install. It says make: command not found. I guess I need to install a package to provide the tools to do this. Bearing in mind this machine has no net connectivity yet, I will need to download whatever package I need and stick it on CD.

Can anyone assist with telling me what packages I need?

---

### Post by Unknowndeepness on 2007-01-15
```
sudo apt-get install build-essential
```

will probably work. (:

---

### Post by SWoodhall on 2007-01-16
Thanks a lot, that worked. Unfortunately still cannot get the NIC to work

I added a Intel PRO/100 pci card to the system as that is a very standard card, then ran through the install again. During the install it correctly recognises both cards, but fails to get DHCP. After the install it then just fails to see either card.

So I thought, ok lets try Debian (as my limited understanding of this is that Ubuntu is a variation on Debian). Installed that (very similar installer), same network card detection screen, except that the cards work fine with Debian. Now obviously I could just leave it at that, but I would be interested to find out why Ubuntu server wasn't detecting them, as I would like to learn more about Ubuntu, if anyone has an idea?

Thanks

---

### Post by Unknowndeepness on 2007-01-16
I'm quite interested in that myself, since i'm having similar problem, i know you can check in /var/modules after your network card, then use modprobe to load it, then it should work.
But why it doesnt do that by it self, i have no idea.

I'm fairly new to linux, so dont hate me if i'm all out of track. (:

---

### Post by SWoodhall on 2007-01-16
Thanks I'll give that a try. 

I'm a complete beginner myself. All this stuff just kind of worked when I used the Kubuntu install CD on my laptop. I'm determined to learn to completely configure my box with commands only. Once I get a net connection life becomes a lot easier :)

---

### Post by Unknowndeepness on 2007-01-16
Mabie a bit offtopic, but "the journey on learning commandline-linux" really teaches you one thing and another. Not just in linux, very much in general computing too, and that's really fun. (:

Besides, who doesnt think a fully-customized TTY-terminal is cool? :D

Anyway, good luck. ;)

---

