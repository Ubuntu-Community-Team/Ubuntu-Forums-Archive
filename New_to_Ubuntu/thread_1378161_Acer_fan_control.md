---
title: "Acer fan control"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by kermit2435 on 2010-01-11
Does anyone have an idiots guide to controlling the fan on an Acer Aspire One, I am a newbie to this linux lark so need a Janet and John guide i.e open a terminal and type "bla bla".  I am currently running version 9.10, the previous version 9.04 had the facility for me to open a terminal and type the following "sudo /usr/local/bin/acerfand" this would switch the fan off until the CPU got hot.
I am not familiar with installing packages so really need the Janet and John approach.
Thanks Kev:D

---

### Post by wojox on 2010-01-11
With A110 and UNR v9.10, (late 2009 release), the only thing needed to be changed form the vanilla install is to edit /etc/modprobe.d/acerhdf.conf and add the line: options acerhdf kernelmode=1 then reboot. This controls the fan and is worth swapping to ubuntu just for this, the netbook is then silent apart from the sound made by using the keyboard..

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

---

### Post by shuttleworthwannabe on 2010-01-11
> **wojox said:**
> With A110 and UNR v9.10, (late 2009 release), the only thing needed to be changed form the vanilla install is to edit /etc/modprobe.d/acerhdf.conf and add the line: options acerhdf kernelmode=1 then reboot. This controls the fan and is worth swapping to ubuntu just for this, the netbook is then silent apart from the sound made by using the keyboard..

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

Any such luck for my lenovo ThinkPad x200--the fan is just unbearable?

---

### Post by kermit2435 on 2010-01-11
> **wojox said:**
> With A110 and UNR v9.10, (late 2009 release), the only thing needed to be changed form the vanilla install is to edit /etc/modprobe.d/acerhdf.conf and add the line: options acerhdf kernelmode=1 then reboot. This controls the fan and is worth swapping to ubuntu just for this, the netbook is then silent apart from the sound made by using the keyboard..

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

Thanx, but how do I get to the line to edit ?:popcorn:

---

### Post by shuttleworthwannabe on 2010-01-11
> **kermit2435 said:**
> Thanx, but how do I get to the line to edit ?:popcorn:

Run this is terminal
```
sudo gedit /etc/modprobe.d/acerhdf.conf
```

---

### Post by kermit2435 on 2010-01-11
> **wojox said:**
> With A110 and UNR v9.10, (late 2009 release), the only thing needed to be changed form the vanilla install is to edit /etc/modprobe.d/acerhdf.conf and add the line: options acerhdf kernelmode=1 then reboot. This controls the fan and is worth swapping to ubuntu just for this, the netbook is then silent apart from the sound made by using the keyboard..

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

I keep getting permission denied, how do I switch this bloody thing off, it's driving me mad Gibber Gibber:(

---

### Post by kermit2435 on 2010-01-11
> **shuttleworthwannabe said:**
> Run this is terminal
```
sudo gedit /etc/modprobe.d/acerhdf.conf
```


Thank you -Silence is Golden!:P

---

### Post by shuttleworthwannabe on 2010-01-11
you are most welcome! 

now can you help me with my Thinkpad X200--the noise is driving me nuts---I feel like I lunatic with all the fan-noise buzzing in my head.

---

### Post by kermit2435 on 2010-01-11
> **shuttleworthwannabe said:**
> you are most welcome! 

now can you help me with my Thinkpad X200--the noise is driving me nuts---I feel like I lunatic with all the fan-noise buzzing in my head.

If it's running windows I highly recommend the free program - aa1 fan control, if your running Ubuntu I'm a newbie with capital N, I did a general search on fan control and there were lots of posts, but most were over my head?

---

### Post by wojox on 2010-01-12
> **shuttleworthwannabe said:**
> you are most welcome! 

now can you help me with my Thinkpad X200--the noise is driving me nuts---I feel like I lunatic with all the fan-noise buzzing in my head.

Could try this:

[http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)

---

### Post by shuttleworthwannabe on 2010-01-12
@kermit: that is for acer only. I have a Lenovo Thnkpad.
@wojox: Thanks, is cpu scaling not a feature now with the new kernels; I checked it out and CPU freq scaling is already working fine.

---

### Post by 3ar1 on 2010-05-31
Does this still apply to Ubuntu 10.04?
There's no /etc/modprobe.d/acerhdf.conf on my system. How would I install acerhdf? I searched the Ubuntu Software Center without any luck.

---

### Post by alchemistkevin on 2010-06-02
> **3ar1 said:**
> Does this still apply to Ubuntu 10.04?
There's no /etc/modprobe.d/acerhdf.conf on my system. How would I install acerhdf? I searched the Ubuntu Software Center without any luck.
did you try to edit /etc/modprobe.d/acerhdf.conf and add the line: options acerhdf kernelmode=1 and reboot?

I'm having the same problem on Acer AOA150/acerhdf 0.5.20/BIOS 0.3310

---

### Post by monograph on 2010-11-14
I seem to have the opposite problem with my ACER 5720Z Dual Core Intel. When I  installed Ubuntu 10.10 it turned off my fan altogether. So now when i boot up it lasts about 10 mins and then turns off dead. No shutdown just off. I have gone through lots of forums so far about APCI controls and added code to the kernal etc. But I am a linux - newbie and also i cant my system on for long enough to start doing much at all.

In saying this, one time I booted up and the fan ran for the duration of that session. Only did that once and never has done again. Why?

---

