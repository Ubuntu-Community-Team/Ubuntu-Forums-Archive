---
title: "Manually Saving Settings for Live CD"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Hishighness on 2009-06-22
Hey everyone, firstly I'd just like to mention I did try to search for this answer but came up empty, I found posts about persistence but that isn't what I'm looking for. I know some people get mad if you ask the same question over and over again but I couldn't find the answer anywhere, so please don't hurt me. :D

That being said, here's my situation. I'm running Ubuntu 9.04 off a live CD and I can't seem to get persistence to work, I dunno if it's just not reading my USB drive or I'm doing something wrong (which wouldn't be unusual since I've used Linux for a grand total of about a week) or what. So now I'm wondering if there is a way for me to manually save my settings so that when I restart I can just type in some command to the terminal or run some program or something and everything will be restored. I have a USB drive to store anything I need on. I remember there was an option when I used Knoppix to set up a space on a hard drive or USB for this purpose.

Thanks for your time,
Hishighness

---

### Post by sideffects on 2009-06-22
So, you're booting Ubuntu from a Live CD and using that as your OS?

---

### Post by Hishighness on 2009-06-22
Yup, that's right. What I'd like is for it not to reset back to the drawing board every time I restart.

---

### Post by sideffects on 2009-06-22
Well, I think the Live CD is designed for testing purposes, so it will not save any settings. It has no place to save them. I mean, it can't save your settings to the CD. So, you will need to install Ubuntu in order to get it to do what you want. Does that make sense?

---

### Post by izizzle on 2009-06-22
Or you could install it onto a USB stick and use it as a [Persistent LiveUSB]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").

---

### Post by Andy06 on 2009-06-22
Live USB is the best method. The casper file it creates can actually be copied over and used with any stock Live USB to have the same settings restored.

If you are experienced, check out what puppy linux does. It creates some settings file that is readable by the Live CD. Does exactly what you want. Perhaps you can figure out how to do that for ubuntu.

---

