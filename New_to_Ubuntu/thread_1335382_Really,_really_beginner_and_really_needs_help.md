---
title: "Really, really beginner and really needs help"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by SamanthaB2895 on 2009-11-23
Hey, I'm new to Ubuntu and I decided a while ago I would like to try it out. So, I burnt the .ISO file into a CD and installed it dual-boot style. 
I went to see how it was but it just came up with "VGA Not Supported" before I even got to any kind of log-in screen. I have a Grundig tv/monitor hybrid 1680'1050 resolution 60Hzs refresh rate. (I'm not that good with computers so I don't really understand most of the hi-tech computer mumbo-jumbo stuff)
I followed [http://ubuntuforums.org/showthread.php?t=1329428](http://ubuntuforums.org/showthread.php?t=1329428) this but when it said "Now find Section "Monitor" and add below lines in bold under identifier:" In the xorg.conf there was no Monitor section, it was just completley blank. Help?

---

### Post by SamanthaB2895 on 2009-11-23
Also, if I completley remove Windows XP from my computer, will it make the problem go away?

---

### Post by scorp123 on 2009-11-23
> **SamanthaB2895 said:**
> Also, if I completley remove Windows XP from my computer, will it make the problem go away? If you use your dad's hunting rifle and shoot yourself in the foot will your mom's headache stop?

Sorry if that sounded mean. I just wanted to stress that one thing here has nothing to do whatsoever with the other thing.

So please don't delete anything yet!

It would be more helpful if you could tell us far more about your PC. What's the make and model? What graphics card does it have? How much memory does it have? How big are the disks? How exactly did you install Linux?

Info like this would be helpful.

EDIT:

**Also important:** [COLOR="Red"]**Please don't follow threads blindly**[/COLOR] if you're not sure that the instructions are really about your problem! You just followed what looks to be a thread about a user with a Nvidia card ... Do you even have a Nvidia card? In any case: [COLOR="Red"]**Know what you do! Or else: ask others!**[/COLOR] But don't copy & paste instructions blindly, OK?

---

### Post by gdonwallace on 2009-11-23
In answer to the first question, we need to know what kind of video card you have in your computer.  (i.e. Intel, Nvidia, etc)

In answer to the second question, no, XP will not effect how Ubuntu resolves your monitor / video.  Think of it as oil and water.  The XP and Ubuntu do not use files or drivers from each other.  So XP cannot be causing the problems that you are having with the video on your computer.

---

### Post by Merovius on 2009-11-23
I would not remove XP just yet. At least you can use it as a backup OS.

I believe in 9.10 there is no xorg.conf by default. You can create one but first you need to know the stats of your monitor. If you search the forums you will probaby find where people are doing just that. Can't tell you off the top of my head.

You could try installing 9.04 and see if that works for you. I run my lcd at the same settings as you do so it should work eventually. Good luck.

---

### Post by SamanthaB2895 on 2009-11-23
Okay. I have a Dell Dimension 5150, I have an ATI Radeon X300 series, 1GB memory. I installed Linux by the CD I burned the .ISO file onto, I just installed it alongside Windows XP

---

### Post by lisati on 2009-11-23
> **SamanthaB2895 said:**
> Also, if I completley remove Windows XP from my computer, will it make the problem go away?

+1 to previous answers: Ubuntu and Windows generally work independently of each other.Each needs to be separately "told" how to use your gear, and, unless you mess something up by being careless, it is extremely unlikely that changing one will affect the other.

---

### Post by SamanthaB2895 on 2009-11-23
I tried 9.04 but I still get VGA not supported

---

### Post by Don1500 on 2009-11-23
Keep going, that's an old video card. You might try 8.04.

How big is your hard drive?

---

### Post by ayenack on 2009-11-23
Are you using a Live CD to install from?

If you are that at least shows you are able to get to the Desktop GUI.

The Live CD is the one that lets you try Ubuntu without installing anything. It runs from the Install CD and takes you to a Desktop GUI where you can surf the web and generally try Ubuntu without actually installing anything.

---

