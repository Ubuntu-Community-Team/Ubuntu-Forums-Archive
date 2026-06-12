---
title: "Live CD won't boot"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by carusoswi on 2009-09-27
So, I've burned three of them, one using gnomebaker, one from brasero, one from k3b.  None will boot.

I remember from the past I used to set a switch in the burner program to make the cd bootable.  Can't find such a setting in any of the three above burner aps.

What am I doing wrong?  I don't remember this being so tough.

Thanks for any help.

Caruso

---

### Post by Ratscallion on 2009-09-27
Check your BIOS, sometimes, you need to go into the settings and tell it which device to boot first. In many BIOSes, it's often boot the Hard Drive first, you want it to boot CD. Feel free to ask how to do this if you're unsure :).

---

### Post by carusoswi on 2009-09-27
> **Ratscallion said:**
> Check your BIOS, sometimes, you need to go into the settings and tell it which device to boot first. In many BIOSes, it's often boot the Hard Drive first, you want it to boot CD. Feel free to ask how to do this if you're unsure :).

Checked that.  It is set correctly.  I have an 8.10 disc that I made way back when.  It boots ok, so the problem is somehow related to how I'm burning the discs.  I do remember having to tell the burner that I wanted the disc to be bootable.

Certain of it.

Is not that an option in one of the three burner aps that I'm using?

Thanks.

Caruso

---

### Post by Ratscallion on 2009-09-27
What version are you trying to boot now? it maybe related to that... Try 8.10 (seeing as you know that works) in one of the methods you're using now. If that works, try ordering a disc, if you're willing to wait, if that doesn't work, then it obviously is the version.

---

### Post by carusoswi on 2009-09-27
> **Ratscallion said:**
> What version are you trying to boot now? it maybe related to that... Try 8.10 (seeing as you know that works) in one of the methods you're using now. If that works, try ordering a disc, if you're willing to wait, if that doesn't work, then it obviously is the version.

The laptop has 9.04 on it.  I wanted to boot using a Live CD to see if I can just copy the files over to some other drive, then, reinstall 9.04.

If I boot using the 8.10 Live CD, I can see his drive, his Home directory, but, clicking on it brings up a blank, probably because I don't have read/write permission.  Can't change the permissions from where I am on the live CD because I am not the owner.

I rebooted in recovery mode, dropped to the root prompt, and I can browse into his home/desktop/Documents, and see the files I want to save.  Don't know how to manually copy them from there to some other drive.  We have an external hooked up, and, if I can figure it out, perhaps I can copy to his windows partition.

If you or anyone can offer suggestions, I'd be most appreciative.  He leaves tomorrow morning, and I want to try to straighten out this mess I made, if possible.

Caruso:popcorn:

---

### Post by s.fox on 2009-09-27
Hello,

I would try checking the iso file.  Have you done a MD5 check sum on it?  [Here]("https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file") is some useful information on 9.04 MD5 check sum

-Silver Fox

---

### Post by Ratscallion on 2009-09-27
Use the terminal command ```
cp
``` to copy it

for example ```
cp folder1 folder2
cp text.txt folder2
```

that is, I do think, the correct syntax for the command. Do, however, correct me if I'm wrong.

---

### Post by tuxxy on 2009-09-27
Heres a guide to burning the ISO maybe this can help

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by NinjaNumberNine on 2009-09-27
If you had windows I would have suggested using wubi to "help me boot from disc" :)
Sorry! :wink:

---

### Post by Blackice115 on 2009-09-27
Not sure if you have already figured this out, or if this will work at all. But I was having the same problem for a while and I figured out that I was just burning the cd too quickly. I tried re-burning it at 4x and then it worked great. Hope this helps!

---

### Post by NinjaNumberNine on 2009-09-27
Do you know of a Windows burner that will burn 4x? Nero won't.

---

### Post by Blackice115 on 2009-09-27
Seriously, I'm not at all sure what the deal with this is, I tried three different burning programs on my laptop(running vista) and I couldn't get any of them to burn at less than 10x. My girlfriend has an old computer with XP on it, I had to use that to get my liveCD to run.

---

### Post by carusoswi on 2009-09-28
> **Blackice115 said:**
> Seriously, I'm not at all sure what the deal with this is, I tried three different burning programs on my laptop(running vista) and I couldn't get any of them to burn at less than 10x. My girlfriend has an old computer with XP on it, I had to use that to get my liveCD to run.

Exactly what I ended doing.  I booted into XP where I have a free, old burner (CDXPBurnerPro3).  That finally gave me a disc that would boot.

It's usually so long for me between having to use Live CD's, that I start doubting myself when things do not go as expected.

There wasn't anything wrong with the file(s) that I downloaded, but something was up with the burning of them to disc using the Linux side burners.

CDXPBurnerPro3 does have a switch that can be set to make the CD bootable, also.  That is, I guess, where I picked up that bit of confusing info.  Setting the switch was not necessary, however.

Thanks for all the suggestions.

Caruso

---

