---
title: "Installing Ubuntu"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by corncob on 2009-01-17
Hi Everybody!  I made an Intrepid CD and sent it to my friend so she could install Ubuntu.  This is what she wrote me:
-----------------------------------------------------------------------
Hi,I got back on my computer today,it just started up.I backed up all my files I want to save so now I can format whenever I'm ready.I tried your disc and was unable to use it.It said things like
 
MP.BIOS BUG 8254 Timer not connected to IO-APIC
Kernel Panic not syncing IONAPIC+ timer doesn't work
Boot with APIC debug
Try NOAPIC option
--------------------------------------------------------------------------
Does anybody have any ideas what's going on?  I successfully installed Intrepid in my laptop with that download although I did send her a different copy.  She was having trouble with her computer not starting sometimes -- just sitting there beeping.

---

### Post by abn91c on 2009-01-17
the beeps may be bad hardware, usually bad RAM or a video card.

---

### Post by ugm6hr on 2009-01-17
> **corncob said:**
> She was having trouble with her computer not starting sometimes -- just sitting there beeping.

This sounds like a hardware issue.  Often HD failures can cause this kind of intermittent booting issue, although I'm not sure that would cause problems with a LiveCD.

---

### Post by 2hot6ft2 on 2009-01-17
> **corncob said:**
> 
MP.BIOS BUG 8254 Timer not connected to IO-APIC
Kernel Panic not syncing IONAPIC+ timer doesn't work
[COLOR="Blue"]Boot with APIC debug
Try NOAPIC option[/COLOR]
--------------------------------------------------------------------------
Does anybody have any ideas what's going on?  I successfully installed Intrepid in my laptop with that download although I did send her a different copy.  She was having trouble with her computer not starting sometimes -- just sitting there beeping.
Did you suggest trying the options it mentions trying?

When booting the livecd right after selecting the language hit the F6 key and add
noapic
to the end of the line and hit Enter

---

### Post by ugm6hr on 2009-01-17
Indeed this is a BIOS / kernel issue, it appears:
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

It is worth trying the noapic boot option

---

### Post by corncob on 2009-01-18
Thanks for the input Everybody.  She's a hundred miles away so I can't really see what she's doing.  I too think its a hardware issue because of the intermittent boot failures.  Her last letter included this:
---------------------------------------------------------------------
> Hi,I tried what  2hot6ft2 on the forum said,the noapic boot and just got an MSDOS page of changing numbers.I attached a picture.It said at one point "scsi scan failed" whatever that means.If I decide to try it,I'll download it from the site.Maybe I'll try the Windows 7 too.I have that download on my laptop so will have to get it from there.
------------------------------------------------------------------------
I'll try to upload the picture she sent me.

---

### Post by linux_tech on 2009-01-18
There is a complete list of kernel options here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by redseventyseven on 2009-01-18
I have a couple of questions. Was she having troubles with her computer not starting properly and just beeping *before* she tried Ubuntu? Was her motivation to give Ubuntu a go a result of those problems?

I fear that just throwing new operating systems at the problem is not going to work - it's just polishing a turd. It sounds like the problem is elsewhere.

It would also help if she signed up to these forums so that she can get help directly rather than the via the roundabout method of emailing you - we're a very friendly bunch really...

---

