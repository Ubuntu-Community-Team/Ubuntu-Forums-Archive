---
title: "Live CD problems"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Roger Browne on 2009-11-03
I have been trying to use the live CDs for Ubuntu and for Kubuntu.  The only programs that seem to work are the web browsers and even they need add-ons that do not install.   I cannot play any of my media files using the programs provided with the OSs

I use dual monitors and only one of them is recognised and I can see no way of fixing this unless I install the full OS to the computer.   Is there anything I can do about this?  or should I just go back to Windows?

The live CDs are supposed to give people a taste of the operating systems and hopefully encourage them to install.   With the experience I have had, not to mention spending many fruitless hours on it, I consider that the live CDs are most likely to drive people away from Linux distros.

Do you have any helpful suggestions?

---

### Post by Locke_99GS on 2009-11-03
You'll want to install *ubuntu-restricted-extras* on the LiveCD to use proprietary media formats.

```
sudo apt-get install ubuntu-restricted-extras
```

You have to make sure that the Multiverse repo is enabled.

These changes won't hold while you're on the LiveCD.

---

### Post by Dark_Stang on 2009-11-03
Ubuntu can't put restricted software (browser plugins, media plugins, restricted video card drivers, etc) on their live CD. So you are pretty limited running it off of the CD. We can only have free and open source software included on the CD. You will need to install to get those things working.

---

### Post by Roger Browne on 2009-11-03
Understood.  I will do an install and see how it goes.   Many thanks.

---

### Post by mivo on 2009-11-03
> **Dark_Stang said:**
> Ubuntu can't put restricted software (browser plugins, media plugins, restricted video card drivers, etc) on their live CD.

They could, they just choose not to. The licenses would allow it. 

Before installing, I would try a Live CD of another distro just to make sure that your hardware is supported before you format your HDD. I think [Mint]("http://www.linuxmint.com/"), which is Ubuntu based (so if it works, Ubuntu will most likely work also), includes codeces, drivers, etc. on their Live CD.

---

### Post by Dark_Stang on 2009-11-03
> **mivo said:**
> They could, they just choose not to. The licenses would allow it. 

Before installing, I would try a Live CD of another distro just to make sure that your hardware is supported before you format your HDD. I think [Mint]("http://www.linuxmint.com/"), which is Ubuntu based (so if it works, Ubuntu will most likely work also), includes codeces, drivers, etc. on their Live CD.
That would break a part of the promise.
> Ubuntu core applications are all free and open source. We want you to use free and open source software, improve it and pass it on.

---

### Post by Roger Browne on 2009-11-03
I installed Ubuntu on the computer.   After fiddling about with it most of the night, and using the Nvidia tool It all works sort of OK now.  The Nvidia tool is very confusing and unclear as to what to do to get the desired effect.

Many thanks to you all.

Now I have to sort out printer problems which look like they may be insurmountable.

---

