---
title: "Keyboard not working while in GRUB"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by Davidthewin on 2011-03-18
Not sure if this is the best place for the question, seeing as it is likely to be a hardware fault, but I am near enough as new as can be to Linux, so I may very well need step by step instructions.

In short, my keyboard does not work until Ubuntu has booted, I found the error when I couldn't change option to boot from my Windows partition. I have tried both PS2 and USB keyboards and my case speaker, which usually beeps once just after being powered up did nothing, which is why I suspect it is a hardware fault.

I left my computer off this morning, after getting onto Windows fine and no one has had the opportunity to use my computer since I last did this morning. I have seen a thread in which someone fixed the problem by changing the keyboard setting from OS to BIOS, but I am not sure where or how they did this.

Does anyone have any ideas? (Just a reminder that I'm near enough completely new to Linux and the most I know about it is a few sudo codes using sudo)

(I am using Ubuntu 10.04 LTS (I think it's the Lucid Lynx version, it's the only one I've seen around))

EDIT: I managed to load Windows by changing the highlighted OS on the GRUB interface but the keyboard wasn't working on Windows either. I read somewhere that in BIOS the keyboard control can be  changed from BIOS to OS, could this  be the problem in this case? And if  so, how would I go about fixing it  seeing as I can't use a keyboard  until this point?

---

### Post by rupak447 on 2011-03-18
> **Davidthewin said:**
> Not sure if this is the best place for the question, seeing as it is likely to be a hardware fault, but I am near enough as new as can be to Linux, so I may very well need step by step instructions.

In short, my keyboard does not work until Ubuntu has booted, I found the error when I couldn't change option to boot from my Windows partition. I have tried both PS2 and USB keyboards and my case speaker, which usually beeps once just after being powered up did nothing, which is why I suspect it is a hardware fault.

I left my computer off this morning, after getting onto Windows fine and no one has had the opportunity to use my computer since I last did this morning. I have seen a thread in which someone fixed the problem by changing the keyboard setting from OS to BIOS, but I am not sure where or how they did this.

Does anyone have any ideas? (Just a reminder that I'm near enough completely new to Linux and the most I know about it is a few sudo codes using sudo)

(I am using Ubuntu 10.04 LTS (I think it's the Lucid Lynx version, it's the only one I've seen around))

It seems like ma problem. I generally reboot my system so that keyboard works well while  in GRUB and after some time it is hanged.

---

### Post by Davidthewin on 2011-03-18
I have seen some threads with a similar problem that recommended that  the original poster restore his GRUB, would that work here?

Rupak, I don't think its hanging, and it just doesn't work at all while in GRUB

---

### Post by Davidthewin on 2011-03-18
OK so I changed the GRUB settings to load Windows first automatically  and it turns out that the keyboard doesn't work when loading Windows  either. I read somewhere that in BIOS the keyboard control can be  changed from BIOS to OS, could this be the problem in this case? And if  so, how would I go about fixing it seeing as I can't use a keyboard  until this point?

---

### Post by Davidthewin on 2011-03-18
Am I allowed to bump due to inactivity? If not, I would just like to ask whether anyone knows a good introductory guide to Ubuntu, reasonably comprehensive, such as keyboard shortcuts, some theory behind how it runs and specifically some information on terminal (there are several fragments I've seen, but nothing as comprehensive as I'd like)

---

### Post by matt_symes on 2011-03-18
Hi

What computer do you have and what is the make of your BIOS ?

Kind regards

---

### Post by Davidthewin on 2011-03-18
It is an Advent CPD1301 (It isn't stock so the model name isn't as important)

Motherboard is Foxconn A7VMX-S (not sure on the revision)

BIOS is American Megatrends INC Version 080014 Revision 8.14, it says "8042 Keyboard services are supported (int 14h0 and USB legacy is supported (used sudo dmidecode -t bios to find this)

---

### Post by matt_symes on 2011-03-18
Hi

Is there an option to disable/enable legacy keyboard/mouse/input support in the BIOS ?

If there is change that option.

Kind regards

---

### Post by Davidthewin on 2011-03-18
I can't get into the BIOS as the keyboard does not work unless a version of Ubuntu is booted

---

### Post by matt_symes on 2011-03-18
Hi

Hmmm. Yes could be a hardware fault. Could you get into the BIOS before installing Ubuntu ?

Kind regards

---

### Post by Davidthewin on 2011-03-18
Yes, and I could even after installing Ubuntu, today it just spontaneously stopped allowing me to use my keyboard before Ubuntu had booted

---

### Post by matt_symes on 2011-03-18
Hi

> **Davidthewin said:**
> Yes, and I could even after installing Ubuntu, today it just spontaneously stopped allowing me to use my keyboard before Ubuntu had booted

I'm not sure what to make of that.

There are a couple of things you could try to eliminate things. 

You could install windows MBR and see if that fixes it (unlightly i think).

You could try flashing your BIOS and see if that fixes it (maybe but always dangerous).

I would suggest it's hardware but as the keyboard works when you boot into Ubuntu i am not convinced. 

See what others suggest as well.

Kind regards

---

### Post by Davidthewin on 2011-03-18
I've been told the best option would be to reset my BIOS to the original settings, but I've no idea how I'd go about this, or whether or not it would work.

Thanks for the help :)

---

### Post by matt_symes on 2011-03-18
Hi

That is generally done using jumpers on your motherboard or you could take the CMOS battery out. It's certainly worth a try. 

Try to download your motherboard manual. In there it should give the recommended way to reset.

Take care not to brick you motherboard.

Kind regards

---

### Post by matt_symes on 2011-03-18
Hi

Here you go (i think this is the page)

[http://www.foxconnsupport.com/download.aspx?models=en-us0000346&category=C000000001&series=en-us0000008&keywords=&sort=Motherboard%20Manual](http://www.foxconnsupport.com/download.aspx?models=en-us0000346&category=C000000001&series=en-us0000008&keywords=&sort=Motherboard%20Manual)

Select your motherboard and download the manual

```
sudo lshw
```

will tell you what you need to know about your motherboard.

Please post back how you get on.

Kind regards

---

### Post by Davidthewin on 2011-03-18
Which would be the best to install from that list, the bottom one?

---

### Post by Davidthewin on 2011-03-18
I removed and replaced the CMOS battery and everything is working fine now! Exactly as it was yesterday, thanks to everyone who helped :)

---

### Post by sebarau on 2013-04-22
hi hello.. my grub also have this problem, i already tried reseated the CMOS battery but USB keyboard still not working. The keyboard work in BIOS, die in GRUB and alive again when booting windows. I try to boot ubuntu live cd but keyboard also not working just when straight to black screen. Sorry I already google to find solution. I will try the ps2 keyboard after i find it.

---

### Post by oldos2er on 2013-04-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

