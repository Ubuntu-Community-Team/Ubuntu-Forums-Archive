---
title: "Editing GRUB 2"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by gredawarha on 2009-11-01
Hello all

Apologies if this has been asked and answered but I could not find.

just installed 9.10, have followed the ubuntu wiki and edited my GRUB timeout to 1 second but when booting I still get a ten second time out.  Really confused?

Any ideas?

---

### Post by wilee-nilee on 2009-11-01
Sounds like your dual booting if the 10 second thang is happening, if this is the case install startup manager in synaptic and it will allow you to rearrange the OS that grub defaults to as well as the wait time. If you are dual booting that sort of information is really important, you can't really post to much information the more you do will get you help quicker generally. :)

---

### Post by philinux on 2009-11-01
After changing the grub scripts you have to use

```
sudo update-grub
```

To regenerate grub.cfg, otherwise your changes will not take effect.

At the moment startupmanager seems a bit hit and miss.

---

### Post by gredawarha on 2009-11-01
Yes, dual booting, going to try your suggestions now

---

### Post by wilee-nilee on 2009-11-01
> **gredawarha said:**
> Yes, dual booting, going to try your suggestions now

 It may be as easy as the above sudo update-grub but startup manager can make life a little easier.

---

### Post by gredawarha on 2009-11-01
Seems to be all okay now, thanks!!!!

---

### Post by wilee-nilee on 2009-11-01
> **philinux said:**
> After changing the grub scripts you have to use

```
sudo update-grub
```To regenerate grub.cfg, otherwise your changes will not take effect.

At the moment startupmanager seems a bit hit and miss.

 There was a short period when startup manager was removing grub-pc but this has been resolved. But if a person has a geeked set-up I could see a problem occurring although I have no clue as to what it could be.

---

### Post by autocrosser on 2009-11-01
SUM (Startup Manager) is being rewritten by its developer to "really" work with Grub2--It is generally advised to look at the Tutorial in Tutorials & Tips about working with Grub2.

---

### Post by ranch hand on 2009-11-01
> **autocrosser said:**
> sum (startup manager) is being rewritten by its developer to "really" work with grub2--it is generally advised to look at the tutorial in tutorials & tips about working with grub2.
+1,357

---

### Post by autocrosser on 2009-11-01
Thank you my friend--& still waiting to get Lucid "off the ground"--I've got 2 partitions ready--nuked my old Jaunty install & have this Karmic that is converted & ready to GO!!!

---

### Post by philinux on 2009-11-01
> **autocrosser said:**
> Thank you my friend--& still waiting to get Lucid "off the ground"--I've got 2 partitions ready--nuked my old Jaunty install & have this Karmic that is converted & ready to GO!!!

I'll be there too! ;)

---

### Post by crjackson on 2009-11-01
> **autocrosser said:**
> SUM (Startup Manager) is being rewritten by its developer to "really" work with Grub2--It is generally advised to look at the Tutorial in Tutorials & Tips about working with Grub2.

Woot!  Woot!  :p

---

### Post by autocrosser on 2009-11-01
My My--are we all over the forums or what--you would think the lab rats are loose :KS:p

Carry on my friends & help as many as possible until Lucid opens!!!!  BRING ON THE BREAKAGE!!!!!!!

---

### Post by philinux on 2009-11-01
> **autocrosser said:**
> My My--are we all over the forums or what--you would think the lab rats are loose :KS:p

Carry on my friends & help as many as possible until Lucid opens!!!!  BRING ON THE BREAKAGE!!!!!!!

I think we got bored since they closed the testing forum. :p

---

### Post by crjackson on 2009-11-01
> **autocrosser said:**
> My My--are we all over the forums or what--you would think the lab rats are loose :KS:p

Carry on my friends & help as many as possible until Lucid opens!!!!  BRING ON THE BREAKAGE!!!!!!!

They are, I'm trying to catch one right now...

---

### Post by autocrosser on 2009-11-01
1000+  Lucid is rather dull right now--so helping people thru the learning curve is the way to go....

---

### Post by ranch hand on 2009-11-01
Yup, I have a drive almost ready to go and am excited.
EDIT
We do seem to be insidious.

---

### Post by autocrosser on 2009-11-01
Fingers itch from lack of updates to play with--it is a condition known as geek-itus--lack of shiny toys to play with & not enough updates to sate the brain......:p:p

Hey--CR  how are you doing--PM me.....

Sorry to the OP--we hijacked your thread......

---

