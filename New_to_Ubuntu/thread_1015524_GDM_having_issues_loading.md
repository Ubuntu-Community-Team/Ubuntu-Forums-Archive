---
title: "GDM having issues loading?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2008-12-18
My boot up is really quick until it gets to the part where GDM is supposed to appear, then it sits there and loads with the little "clock" for up to two minutes before GDM appears.

The cursor flashes in the entry-box, but I cannot type anything, nor move my mouse.

Any idea what is hanging GDM? Trying to get my parents to use Ubuntu on this stupid Vista laptop and could really use your help!!

---

### Post by kostkon on 2008-12-18
> **pHreaksYcle said:**
> My boot up is really quick until it gets to the part where GDM is supposed to appear, then it sits there and loads with the little "clock" for up to two minutes before GDM appears.

The cursor flashes in the entry-box, but I cannot type anything, nor move my mouse.

Any idea what is hanging GDM? Trying to get my parents to use Ubuntu on this stupid Vista laptop and could really use your help!!
You can check your logs for any error messages, for example. You can easily access them in *System &#8594; Administration &#8594; System Log*.

You can add more logs by selecting *File &#8594; Open...*  They exist in the */var/log* folder.

If you find something suspicious, you could paste it here and we may be able to help you with that.

---

### Post by pHreaksYcle on 2008-12-18
Development: It actually lets me log in now. 

But it still takes two minutes to appear. 

I have everything set up perfectly, would like to present this to my parents, but when my dad sees it taking two minutes to boot, he won't like it :P

I looked in all the tabs of system logs, nothing suspicious, or even about GDM.

---

### Post by VastOne on 2008-12-19
> **pHreaksYcle said:**
> Development: It actually lets me log in now. 

But it still takes two minutes to appear. 

I have everything set up perfectly, would like to present this to my parents, but when my dad sees it taking two minutes to boot, he won't like it :P

I looked in all the tabs of system logs, nothing suspicious, or even about GDM.

What is your setup regarding a single disk or multiple? How did you install as far as partitions setup on this disk?  How much swap space is allocated? How old is the drive and how much has it been used?  I am getting at a defrag question or two but need some prelim answers first...

Do you know of anything else that may be loading as you start up, printer, wifi connection, usb disk...etc etc?

VastOne

---

### Post by howlingmadhowie on 2008-12-19
does anyone know if gdm waits for an internet connection for some reason?

---

### Post by pHreaksYcle on 2008-12-19
It is a whole-drive ubuntu install, single disk, laptop. Installed via alternate install disk, guided, full drive, hopefully that gave me swap.

I don't think the drive is bad (just installed an OS on it), but could always be a possibility.

I thought you didn't need to defrag linux as it never fragments itself anyway.

Anyway, literally just installed this copy of ubuntu last night, so clutter is NOT an issue just yet.

Thanks for your responses.

---

### Post by VastOne on 2008-12-19
> **pHreaksYcle said:**
> It is a whole-drive ubuntu install, single disk, laptop. Installed via alternate install disk, guided, full drive, hopefully that gave me swap.

I don't think the drive is bad (just installed an OS on it), but could always be a possibility.

I thought you didn't need to defrag linux as it never fragments itself anyway.

Anyway, literally just installed this copy of ubuntu last night, so clutter is NOT an issue just yet.

Thanks for your responses.


Read this thread and see if it helps....

I found this by searching the forums with the parameters of slow + boot + process

[http://ubuntuforums.org/showthread.php?t=992133&highlight=slow+boot](http://ubuntuforums.org/showthread.php?t=992133&highlight=slow+boot)

---

### Post by VastOne on 2008-12-19
> **howlingmadhowie said:**
> does anyone know if gdm waits for an internet connection for some reason?

I have seen some threads discussing DHCP issues and stalled logins due to not finding a DHCP server, especially with a WIFI setup.  If you are wireless, I would try to connect with a hard line and see if the delay is the same...

---

