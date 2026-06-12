---
title: "any disadvantages to using alternate iso?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-01
Using the desktop ubuntu iso is giving me problems.

are there any disadvantages to using the alternate ubuntu iso?

---

### Post by iponeverything on 2010-05-01
The only difference is the nifty gui for the install, the end result will be the same.

---

### Post by llamabr on 2010-05-01
You're likely to have similar problems.  But sure, give it a try.

Or, tell us the problems, and we can start that way.

---

### Post by arpanaut on 2010-05-01
```
are there any disadvantages to using the alternate ubuntu iso?
```

Yeah ... You gotta pay attention more, it won't hand hold so much.

When you accept changes to your system be sure what you are being offered is what you want to do!

You won't get the **[COLOR="Red"]You Be Sure, Fool?[/COLOR]** dialog so much.  LOL!

Remember that you can always back yourself out of a your selection of options, before you accept the offered changes.

Quite honestly, it is my preferred installation system.  I have more control, just takes some getting used to  re:navigating etc.

---

### Post by cariboo on 2010-05-01
Actually, there are more advantages to using the alternate installer, you can setup LVM and full disk encryption, where the Live CD has no LVM options, and only allows you to setup encryption on your home directory. The Live CD has problems detecting drives in a SATA only systems unless you have an ide hard drive installed, If your video card/monitor aren't detected properly, the alternate iso will allow you to install the system, and allow you to set up graphics after the first reboot.

---

### Post by iponeverything on 2010-05-01
> **llamabr said:**
> You're likely to have similar problems.  But sure, give it a try.

Or, tell us the problems, and we can start that way.

It's not uncommon for install not to work the desktop disk but work with the alternate disk.

---

### Post by aysiu on 2010-05-01
The Alternate CD takes longer to install.

---

### Post by hanzj on 2010-05-01
It does? I would think that the Alternate CD takes shorter to install.

---

### Post by aysiu on 2010-05-01
> **hanzj said:**
> It does? I would think that the Alternate CD takes shorter to install.
It does. The Desktop CD "installs" Ubuntu by pretty much copying over the live session (and then downloading and configuring some language packs). The Alternate CD installs Ubuntu from scratch by unpacking and then installing each individual package.

---

### Post by Paqman on 2010-05-01
> **aysiu said:**
> It does. The Desktop CD "installs" Ubuntu by pretty much copying over the live session (and then downloading and configuring some language packs). The Alternate CD installs Ubuntu from scratch by unpacking and then installing each individual package.

You learn a new thing every day. Cheers Aysiu!

---

### Post by zeekoman on 2010-05-01
I use the Alternate CD to install text-only Ubuntu, which is useful if you want to build up from just Ubuntu.

---

### Post by jvc26 on 2010-05-01
> **aysiu said:**
> It does. The Desktop CD "installs" Ubuntu by pretty much copying over the live session (and then downloading and configuring some language packs). The Alternate CD installs Ubuntu from scratch by unpacking and then installing each individual package.

Wow, didn't know that - and there was me continually using the Alternate as I thought it was faster!

Doesn't it work out about the same since the Desktop CD has to do that loading of the live session at the start which is a similar amount of work?

J

---

### Post by Morbius1 on 2010-05-01
A while back the LiveCD did not allow you to install grub in any other place but the MBR. Is that still true or have I been using the alternate CD for no reason the last few installs.

---

### Post by NightwishFan on 2010-05-01
You can use 'Expert Mode' to custom tailor your install. This includes enable root account and etc.

---

### Post by aysiu on 2010-05-01
> **Morbius1 said:**
> A while back the LiveCD did not allow you to install grub in any other place but the MBR. Is that still true or have I been using the alternate CD for no reason the last few installs. You can install other than the MBR. At the last screen click the **Advanced** button to specify where to install Grub.

> **jvc26 said:**
> Wow, didn't know that - and there was me continually using the Alternate as I thought it was faster!

Doesn't it work out about the same since the Desktop CD has to do that loading of the live session at the start which is a similar amount of work?

J No, it doesn't work out the same at all. It takes considerably more time to load up, unpack, and then install each individual package. Loading up the live session takes one minute. In fact, the Desktop CD gives you the option to go directly to installing without loading the full live session first (it loads up a kind of minimalist live session that has only the installer application running).

---

