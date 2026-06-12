---
title: "can i roll back?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by tednumber8 on 2009-01-04
I have jut did some sort of command and now ubuntu is saying "connected to auto eth0" but it isnt picking up the internet. Oh god what have I done :(

---

### Post by albinootje on 2009-01-04
> **tednumber8 said:**
> I have jut did some sort of command and now ubuntu is saying "connected to auto eth0" but it isnt picking up the internet. Oh god what have I done :(

Did you have internet connection earlier on ?
Is it about wired and/or wifi networking ?

Can you post the output of :
```

lshw -c network
lspci
cat /etc/resolv.conf
route -n
ifconfig -a
dmesg|tail -n30

```

---

### Post by tednumber8 on 2009-01-04
i cant post output because its offline now/1 Im really cracking up that i went and did something ... why so confusing lol

But seriously can I roll back to say 10 hours ago?

---

### Post by tednumber8 on 2009-01-04
Im going to start again. At least it will be a learning curve for me :D

---

### Post by albinootje on 2009-01-04
> **tednumber8 said:**
> Im going to start again. At least it will be a learning curve for me :D

You're gonna reinstall ? Erhmm... Have fun ;-)

Which brand and type computer is it ?
And which Ubuntu release are you installing ?

---

### Post by ans5685 on 2009-01-04
No need to start ALL over :D
Just click on the network applet in the system tray on the top panel and look around the new window that pops up, things are written preety clearly there.

I suppose you have been automatically connected to the internet via DHCP on your eth0 i.e first network card/chip.
Which is not a bad thing if that is what you use :popcorn:

If not then all you need to do is change it to what you use.
No need to fret it is preety much point and click.:P

---

### Post by tednumber8 on 2009-01-04
its not so much point and click when the network configuration (GUI) tool is not installed, and I couldn't get it installed. Anyhow I've favoured a reinstall so I can learn!

---

