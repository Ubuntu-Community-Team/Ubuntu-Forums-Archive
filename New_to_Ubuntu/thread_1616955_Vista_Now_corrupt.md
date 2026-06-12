---
title: "Vista Now corrupt"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by wedoo2 on 2010-11-08
Last week I installed Ubuntu 10.10 along side my Vista operating system on my notebook.  No problems and since I have previously had the operating system I had no real problem other than it automatically finding my wireless network.  I had not yet started to work on that.

Yesterday I had the notebook unplugged and the battery got low and the computer turned off.  I was unable to boot back into Windows.  I have tried system restore and it seems I have errors on the hard drive.  I looked through some forum info and found some mention of hibernation and corrupting windows files.

I thought about uninstalling Ubuntu, but that seems to be difficult and involves partition manipulation and possibly done through windows, and I am unable to boot up to it anyway.

Is this a known problem and can it be fixed?

---

### Post by JustinR on 2010-11-08
Were you in Ubuntu or Windows when this happened?

---

### Post by wedoo2 on 2010-11-08
I was in Windows checking my fantasy football team

---

### Post by JustinR on 2010-11-08
Can you still boot into Ubuntu?

---

### Post by wedoo2 on 2010-11-08
I was able to boot up Ubuntu with the disk in.  I guess with the install I did I need the disk in all of the time???

---

### Post by JustinR on 2010-11-08
> **wedoo2 said:**
> I was able to boot up Ubuntu with the disk in.  I guess with the install I did I need the disk in all of the time???

But can you boot without the CD in?

---

### Post by wilee-nilee on 2010-11-08
Boot vista hit the f8 key=safe mode go to the command terminal and run chkdsk /r it will not do it but ask for one on restart. Let it run the chkdsk. Removing Linux I doubt will do anything but if you need to we can.

You can also do this with a vista recovery disc, from the repair command line.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You can also reload the bootlaoder to just boot straight to vista; from the repair command line.
[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)
I think you only need the command to load the mbr
```
bootrec.exe /fixmbr
```

If you do this and need Ubuntu back as the booting OS then reload the mbr using this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If nothing works; post the bootscipt in my signature in code tags as described in the signature. You can wrap the text in code tags by highlighting the text then clicking on the # in the reply panel.

---

### Post by wedoo2 on 2010-11-08
No, but it would not boot into Ubuntu without the disk in before my problem.  I might mention that I was able to get into my BIOS and run the diagnostics on the hard drive and memory.  I feel like the HDD is okay, just the Vista operating system is a problem.

---

