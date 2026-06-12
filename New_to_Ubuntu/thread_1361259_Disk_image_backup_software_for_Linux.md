---
title: "Disk image backup software for Linux?"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by MyR on 2009-12-21
Is there anything like Acronis True Image available for Linux?

Software that quickly makes an image of the entire hard disk, as small as feasible, without rebooting, and can easily and quickly be restored.

Or are image backups really just a waste of time?

P.S. I know Acronis does in fact sell what I'm looking for, but it's over $850 USD.

---

### Post by juancarlospaco on 2009-12-21
Clonezilla LiveCD based on Ubuntu at SourceForge...

---

### Post by MyR on 2009-12-21
Thanks for your reply

I am hoping to not have to boot live media. Am I all out of options then?

---

### Post by juancarlospaco on 2009-12-21
Why not...?

Its the *"Best Practice"*, 
on other legacy systems there are other ways, 
but here we promote the correct and better way to do it.
:)

---

### Post by MyR on 2009-12-21
Because it's more work ;]

---

### Post by juancarlospaco on 2009-12-21
If you are looking for less-effort solution, i recommend to use [Back In Time]("apt:/backintime-gnome"),
is just like Time Machine from the Mac, install, configure, forget.
*(it not create image files, but backup anyways)*

---

### Post by Bigadada_saba on 2009-12-21
> **MyR said:**
> Is there anything like Acronis True Image available for Linux?

Software that quickly makes an image of the entire hard disk, as small as feasible, without rebooting, and can easily and quickly be restored.

Or are image backups really just a waste of time?

P.S. I know Acronis does in fact sell what I'm looking for, but it's over $850 USD.

 Try remastersys backup

---

### Post by sgosnell on 2009-12-21
+1  Remastersys works.

---

### Post by delysid on 2010-02-01
> **sgosnell said:**
> +1  Remastersys works.

I just tried to create a backup using Remastersys,
But was given an error saying the file size was too large for the ISO specification.  

Anyone know a way around this?

I'd love to be able to just pop in a cd after a format
and completely install everything (packages/settings etc) I need in one go.

Thanks in advance :D

---

### Post by garvinrick4 on 2010-02-01
> **delysid said:**
> I just tried to create a backup using Remastersys,
But was given an error saying the file size was too large for the ISO specification.  

Anyone know a way around this?

I'd love to be able to just pop in a cd after a format
and completely install everything (packages/settings etc) I need in one go.

Thanks in advance :D
A CD is only 700 meg. A dvd about 4 gig. What is the size of drive or partition you want
to image? These mediums do not have persistence (hold changes to system)
Make a LIVE CD of what ever program you are going to use. Back-up to an external drive.
Use the Live CD to make the image or restore the image. Using live CD nothing is mounted
while making image or restoring. 

I would just make a USB start-up disk with 4 gig USB stick, your settings will be saved up to 4 gig. It will be a LIVE CD and an install disk in one. Keep your /home on different backup.
That is if you want a carry around convenient way to manage this.
In Ubuntu use code:  sudo apt-get install usb-creator-gtk

---

### Post by gabreal2k on 2010-02-04
I too am interseted in this. I have a 10gb root partition. 

If I made a startup disk (thumbdrive) of my root partition could I "reimage" that partition, 

and have all my settings and updated packages "restored" or no?

---

### Post by warfacegod on 2010-02-04
Aside from some modifications, this is what I do:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by gabreal2k on 2010-02-07
Thanks, I did what you do and it'll work splendid for my purposes.

---

### Post by warfacegod on 2010-02-07
Great. Just remember, if you can, always test a backup.

---

### Post by gabreal2k on 2010-02-07
I usually try to test all my backups. Hey you dont happen to know how to span my /home partition over 2 hard drives do ya? I think im gonna have to use LVM but not sure.

---

### Post by warfacegod on 2010-02-07
> **gabreal2k said:**
> I usually try to test all my backups. Hey you dont happen to know how to span my /home partition over 2 hard drives do ya? I think im gonna have to use LVM but not sure.

I'm not entirely sure what you're looking to do or why but, at a guess, I'd say look into rsync.

---

### Post by tecknomage on 2012-11-26
Found [**Image for Linux**]("http://www.terabyteunlimited.com/image-for-linux.htm") full function image backup utility with GUI :)

You 'make' a boot CD (*for license version*), then enter your license, and make the boot CD.


[COLOR=Red]Make sure you read the README.TXT[/COLOR]

Just used the trial version and it worked as advertized.

One caution, if you backup to a USB Stick like I do, have it plugged in BEFORE boot so **Image for Linux** will see it.

---

### Post by howefield on 2012-11-26
Old thread back to sleep.

---

