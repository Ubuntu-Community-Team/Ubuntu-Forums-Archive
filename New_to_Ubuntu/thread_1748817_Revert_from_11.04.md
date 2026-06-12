---
title: "Revert from 11.04 ?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Winterdream on 2011-05-04
I upgraded my Ubuntu laptop from 10.10 to 11.04 and now it won't even start unless I take out the battery and then replace it.  How can I revert to 10.10 without losing everything?  I got a look at 11.04 and it's not something that I want to use anyway.

---

### Post by ubudog on 2011-05-04
Sorry, but this is all I could find.  A bit complicated...

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

---

### Post by ubudog on 2011-05-04
If you really need to, you could backup your stuff onto an external HD, then get a 10.10 disk and reinstall.  (though I suggest 10.04 if you're gonna stick with it for a while)

---

### Post by Winterdream on 2011-05-04
> **ubudog said:**
> If you really need to, you could backup your stuff onto an external HD, then get a 10.10 disk and reinstall.  (though I suggest 10.04 if you're gonna stick with it for a while)

Thanks, ubudog.  The first suggestion looked way too complicated for me so I'm downloading 10.04 now.  After I posted last night I got it to tell me that there was some hardware that was incompatible with "Unity" (?) but I could run in the classic mode.  I could only get it to boot by starting in a previous version - and that brought me to a command-line, so I could start with startx.  And then I could only shut it off with "sudo shutdown -h now"!  (Or by taking out the battery)

I bought it with Ubuntu installed and it's still under warranty so I sent the company an email and will see what they say about it.

---

### Post by ubudog on 2011-05-04
10.04 should work fine for you.  It is probably the most stable release of Ubuntu yet.  Just make sure to back your stuff up.

---

### Post by matthewbpt on 2011-05-04
I don't see how having to replace to take out the battery and replace it could possibly be caused by 11.04 ... That sounds like a hardware problem to me ...

---

### Post by ubudog on 2011-05-04
> **matthewbpt said:**
> I don't see how having to replace to take out the battery and replace it could possibly be caused by 11.04 ... That sounds like a hardware problem to me ...

Yes, it does sound more like a hardware problem... does this happen if you take out the battery and run it on AC only?

---

### Post by fabricator4 on 2011-05-04
> **Winterdream said:**
> And then I could only shut it off with "sudo shutdown -h now"!  (Or by taking out the battery)


Definitely do not power off by removing the battery. It's a good way of damaging the file system and losing all of your data.  Also, you can normally power off the machine by pressing and holding the power button but you don't want to do this normally either - it's only for if the machine is completely locked up and won't respond to other means.

Damaging the file system can make it harder to recover your data.

Chris.

---

### Post by searchfgold6789 on 2011-05-04
Have you tried adding "acpi=force" to your boot options in GRUB before booting?
Also, there may be some power options in your BIOS you can fiddle with to make it work better.

---

### Post by Winterdream on 2011-05-04
Thank you all !

I didn't know that holding the power button down would shut it off, thank you for that information, fabricator4.

It is a hardware problem; something in my laptop is not compatible with 11.4.  I went through the upgrade and it just hung up when it tried to restart, didn't get to the login screen. I couldn't find anyway to shut it off so I finally figured I'd just unplug it and take out the battery.  It made sense to me. Several attempts to start it never got further than a blank screen.

I got all my files and configurations onto a USB drive and I am now installing 10.4.

Then I just have to install and configure the LAMP and reinstall my files and I hope it'll be almost as nice as it was when I bought it!

The company I bought it from did offer to re-install 10.10 for me, but of course I would have to send it to them and I need it back ASAP.

I just got it in November, I didn't imagine there could be a hardware incompatibility with the upgrade!  Wrong again!

---

### Post by ubudog on 2011-05-05
Let us know how it goes, and good luck.  

Also, a small question... did you use Update Manager to upgrade?

---

### Post by matthewbpt on 2011-05-05
If it doesn't work on 11.04 you should file a bug in [Launchpadt]("http://www.launchpad.net") so it can get fixed in this or a later release. Also if your system completely crashes first thing you should try is the [Magic SysRq Combo]("http://en.wikipedia.org/wiki/Magic_sysrq"), which can help prevent filesystem damage and possible data loss, before trying any forcing such as taking out the battery or keeping the power button pressed. It can be a bit cuumbersome at first, what you do is press Ctrl + Alt + SysRq and keep them pressed while pressing R,E,I,S,U,B one after the other, waiting a second or two between each. The link will give you a full explanation of what each of those things are doing.

---

### Post by Winterdream on 2011-05-06
> **ubudog said:**
> Let us know how it goes, and good luck.  

Also, a small question... did you use Update Manager to upgrade?

Yes, I used Update Manager to upgrade.

I tried to install 10.4 and I was able to install the LAMP and get it configured and got my web application working.  But I had so many other problems, it was terrible.  So I packed it up and it's on it's way back to Linucity.  They're going to reinstall 10.10 for me.

---

### Post by Winterdream on 2011-05-06
> **matthewbpt said:**
> If it doesn't work on 11.04 you should file a bug in [Launchpadt]("http://www.launchpad.net") so it can get fixed in this or a later release. Also if your system completely crashes first thing you should try is the [Magic SysRq Combo]("http://en.wikipedia.org/wiki/Magic_sysrq"), which can help prevent filesystem damage and possible data loss, before trying any forcing such as taking out the battery or keeping the power button pressed. It can be a bit cuumbersome at first, what you do is press Ctrl + Alt + SysRq and keep them pressed while pressing R,E,I,S,U,B one after the other, waiting a second or two between each. The link will give you a full explanation of what each of those things are doing.

I don't know what the bug is.  I only know that it failed miserably and I don't think that reporting a bug "didn't work" is very helpful, is it?

Thank you for the information, I have saved it.

Hopefully I haven't done any real damage to it and Linucity will be able to reinstall 10.10.  I was really happy with it before all this happened; I even had it printing to a printer connected to a Windows PC.  Life was good for awhile!

---

