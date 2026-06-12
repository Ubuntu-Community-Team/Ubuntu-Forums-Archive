---
title: "System failure after boot from cd"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Rhenson68 on 2010-12-24
I have a 64 bit winows 7 machine and I thought I would play with ubuntu over the holidays.

I created a 64 bit 10.10 cd and booted to it hoping to demo the desktop system.  IIt failed saying a bad bios was found and stopped at a boot: prompt.  This is my first attempt to use unix, so I removed the cd and restarted.  My system wont boot.  I tried to restore windows and my c drive appears to have nothing on it.  I fear my attempt to demo unix has destroyed my windows system...any ideas on how to re over?

---

### Post by nothingspecial on 2010-12-24
Hi, do not panic,

Try removing the cd and setting your bios back to boot from the hard disk.

---

### Post by amjjawad on 2010-12-24
> **nothingspecial said:**
> hi, do not panic,

try removing the cd and setting your bios back to boot from the hard disk.

+1

---

### Post by Rhenson68 on 2010-12-24
I wish I had read more first instead of jumping right in.

Linux assumes you know exactly what you`re doing..laughs of pain

Changed bios to boot from hd and am being told that windows failed to start and that I need to repair the computer

I boot to the windows cd and try to repair - it fails and notes that no os is found

---

### Post by karthick87 on 2010-12-24
Boot from a live cd and post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags.

---

### Post by Rhenson68 on 2010-12-24
If only I had a computer to create the cd on :D. I am typing this on my iPad...

I will see if a family member can help me create one this evening...this really has messed up the holidays!

---

### Post by amjjawad on 2010-12-24
> **Rhenson68 said:**
> If only I had a computer to create the cd on :D. I am typing this on my iPad...

I will see if a family member can help me create one this evening...this really has messed up the holidays!

Are you sure that there's no other HDD or USB in your system?

If you ran the LiveCD ONLY WITHOUT Installation then NO WAY it will damage your system.

---

### Post by Rhenson68 on 2010-12-24
That's what I keep telling my wife...there is no way this can happen!

I do have other HDs in the computer.  I am going to shut down and disconnect everything but the primary.

When trying to boot to the unix cd initially it noted a bad bios - could this have caused it to format my c drive?

---

### Post by msandoy on 2010-12-24
A live cd would never format your drive without you first choosing it, and confirming it at least twice. To me it sounds like a coincidence, of your testing with the live cd, and a file corruption in windows. There also might be a bug in your BIOS. You should try updating it, and see if it fixes your problem.

You can also try booting from the live cd, but in the startup menu, after choosing language, press F6, and choose "no acpi". It might help you to boot.

---

### Post by amjjawad on 2010-12-24
> **Rhenson68 said:**
> That's what I keep telling my wife...there is no way this can happen!

I do have other HDs in the computer.  I am going to shut down and disconnect everything but the primary.

Very good idea. That's what I'm trying to say. There must be something wrong and to be sure, it's better to disconnect the other devices.

> 
When trying to boot to the unix cd initially it noted a bad bios - could this have caused it to format my c drive?
NO WAY!

---

### Post by Rhenson68 on 2010-12-24
After disconnecting everything but my PrimaryHD I see my windows installation on the new D drive and the c drive is now a system drive. It is as if the drive has been repartioned.

---

### Post by amjjawad on 2010-12-24
> **Rhenson68 said:**
> After disconnecting everything but my PrimaryHD I see my windows installation on the new D drive and the c drive is now a system drive. It is as if the drive has been repartioned.

Can you post a screenshot for Disk Device Manager?
Let's see the HDD and its partitions.

---

### Post by msandoy on 2010-12-24
The system partition you describe, is the windows restore partition. It should not show up in windows at all.

---

### Post by Rhenson68 on 2010-12-24
If I get back up or have to install again - I would like to say thanks to you guys for the help you are giving!

---

### Post by amjjawad on 2010-12-24
> **Rhenson68 said:**
> If I get back up or have to install again - I would like to say thanks to you guys for the help you are giving!

Too early for thanks now :D
Let's get your problem fixed and we'll be glad if you'll do that ;)

---

### Post by Rhenson68 on 2010-12-24
I am booted up from the windows cd to try the repair process after booting to the HD and being told that I had to repair

I run the repair process, the search for windows installations finds a problem with the bootmgr and finds the recovery on the d drive

I click repair and restarted and get a window saying "failed to save startup options."

I click ok

It notes no os to select - i click next to get to the command prompt

If I go to a command prompt i see c has a temp dir with .txt files named boot failure and bcd info
The d drive looks like what my c drive used to look like

---

### Post by Rhenson68 on 2010-12-24
I am scared to try to change the partitions from the command prompt to get the c drive to include my d rive detail...but I think that is what I may need to do...do you agree?

---

### Post by msandoy on 2010-12-24
It seems like you will have to do a reinstall. 
Do you have a windows installation DVD, or just a restore cd? 
If you have the windows installation DVD, you can, as a last option, remove the rescue partition, making your D-drive into C-drive, and then windows should be able to find itself again.

---

### Post by msandoy on 2010-12-24
If I understand you correctly, you are able to boot into a commandline, Check if you have a program called fdisk.
Try entering FDISK /MBR
If you have the program installed, it should try to restore your original bootrecord.

---

### Post by nothingspecial on 2010-12-24
> **Rhenson68 said:**
> 

Linux assumes you know exactly what you`re doing..laughs of pain



I think I misinterpreted your original post. You actually tried to restore windows after the live cd boot error.

I still believe what I said was the answer to your original issue after trying to boot the live cd. In that I think our computer was still trying to boot the cd before you tried to repair it. I could be (probably) wrong.

However, I know nothing of windows, so once you have tried to restore it, I`m out..... sorry.

btw the thing about linux knowing exactly what you`re doing is my 'sig' and appears in all my posts. It wasn`t directed at you personally :D 

Sorry if I offended you.

Good luck.

---

### Post by Rhenson68 on 2010-12-24
You are correct, and I understood that it was your signature...just fitting

I will try the fdisk option...

---

### Post by amjjawad on 2010-12-24
I'm a bit lost now.

Can we summarize what's going on?

---

### Post by nothingspecial on 2010-12-24
Tried to boot linux live cd

Didn`t work

Tried to reboot windows whilst bios was still set to boot from cd, didn`t work (this happens in some systems)

Restored windows (from cd I assume)

c partition is empty, everything is on d partition, mbr thinks c should be c but everything is on d

I think

If you see what I mean

Correct me if I`m wrong.

---

### Post by msandoy on 2010-12-24
There is a windows commandline tool called DISKPART, this can be used to change partition drive letters. See the following page, describing the procedure about mid way down. Don't be confused because of the referances to server, it also applies to desktop versions.
[http://technet.microsoft.com/en-us/library/cc757491%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc757491%28WS.10%29.aspx)

---

### Post by amjjawad on 2010-12-24
> **nothingspecial said:**
> Tried to boot linux live cd

Didn`t work

Tried to reboot windows whilst bios was still set to boot from cd, didn`t work (this happens in some systems)

Restored windows (from cd I assume)

c partition is empty, everything is on d partition, mbr thinks c should be c but everything is on d

I think

If you see what I mean

Correct me if I`m wrong.

Thank you!
Waiting for the OP to confirm that.

---

### Post by msandoy on 2010-12-24
From what I understand, the restore partition has become visible after trying to restore system with cd. Windows can't find itself anymore. With the DISKPART tool, he should be able to remove teh driveletter assigned to the rescue partition, and restore letter C to the original partition.

---

### Post by Rhenson68 on 2010-12-24
A brief history

1 I woke up and thought it would be fun to check out this thing called ubuntu
2 reading nothing I created a 64 bit cd from the "get desktop" page on the site
3 I followed the instructions on creating a cd and booted to it
4 the boot did not result in a working demo, but failed.
5 I removed the cd and rebooted and got no message or prompt - just a cursor.  This is probably actually the beginning of my problem.  For some reason I thought the boot order in my bios was fine to have it as cd and then hd...so, I panicked and inserted my windows cd to repair.  I should have changed my bios to hd boot first.  If I understand, this may have worked with no issue, but now I have a system partition on my HD.

I am now going to try and remove the c partition in hopes that my d becomes c and all is well with the world...at which time I will resume my quest to see ubuntu.   If it doesn't I will probably spend the next few days reinstalling everything on my system aver reinstalling windows...

I have most probably brought it on myself, but it all started with a failed livecd boot...I will research that next time around.

Sorry for the confussion, and I really do appreciate the help.

---

### Post by amjjawad on 2010-12-24
> **msandoy said:**
> From what I understand, the restore partition has become visible after trying to restore system with cd. Windows can't find itself anymore. With the DISKPART tool, he should be able to remove teh driveletter assigned to the rescue partition, and restore letter C to the original partition.

Please wait until the OP confirms the steps he did to fix the issue. I'm totally lost and need to understand what happened.

Thank you!

---

### Post by Rhenson68 on 2010-12-24
Nothing special has it right...will post disk part results soon.

---

### Post by nothingspecial on 2010-12-24
> **Rhenson68 said:**
>   For some reason I thought the boot order in my bios was fine to have it as cd and then hd...so, I panicked and inserted my windows cd to repair.  I should have changed my bios to hd boot first.  If I understand, this may have worked with no issue, but now I have a system partition on my HD.



In almost all cases this is absolutely fine, and infact I can`t confirm personally that this is the case with cds. But I have had one system that would refuse to boot (with a similar error) if set to boot from usb drive, with any usb drive plugged in (operating sytem contained, data, whatever).

---

### Post by msandoy on 2010-12-24
> **amjjawad said:**
> Please wait until the OP confirms the steps he did to fix the issue. I'm totally lost and need to understand what happened.

Thank you!

I see your frustration. I tought it was clear that his rescue partition had popped up as drive C. I hope OP tries the tools I mentioned before removing the partition.

---

### Post by amjjawad on 2010-12-24
> **Rhenson68 said:**
> A brief history

1 I woke up and thought it would be fun to check out this thing called ubuntu
2 reading nothing I created a 64 bit cd from the "get desktop" page on the site
3 I followed the instructions on creating a cd and booted to it
4 the boot did not result in a working demo, but failed.
5 I removed the cd and revolted and got no message or prompt - just a cursor.  This is probably actually the beginning of my problem.  For some reason I thought the boot order in my bios was fine to have it as cd and then hd...so, I panicked and inserted my windows cd to repair.  I should have changed my bios to hd boot first.  If I understand, this may have worked with no issue, but now I have a system partition on my HD.

I am now going to try and remove the c partition in hopes that my d becomes c and all is well with the world...at which time I will resume my quest to see ubuntu.   If it doesn't I will probably spend the next few days reinstalling everything on my system aver reinstalling windows...

I have most probably brought it on myself, but it all started with a failed livecd boot...I will research that next time around.

Sorry for the confussion, and I really do appreciate the help.

Okay, fair enough

Now, excuse me if you already have mentioned that before but I'll start from scratch.

Do you have another machine right now? can you create a new LiveCD or LiveUSB? here is how:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Check step2

After that, in my signature, there's a link called Step1. Please read it. You need to look for MD5SUM. Check that before anything else.

If MD5SUM for your downloaded iso is equal to the one in Ubuntu Hashes link then you're good to go.

Insert the LiveCD you have created

Reboot your machine

Set BIOS to boot up from CD

Save and reboot

Once you get the purple screen with that man with opened arm ... press any key, choose your language and then choose: Try Ubuntu without installation.

Once you get the GUI Desktop, please run this:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post back the result and wrap up the text with "CODE" tags.

Waiting for you ;)

---

### Post by msandoy on 2010-12-24
Very fast moving thread. :-)

---

### Post by amjjawad on 2010-12-24
> **msandoy said:**
> Very fast moving thread. :-)

That's why I feel blind now!

---

### Post by Rhenson68 on 2010-12-24
Okay did the disk part and reassigned d to be c.  The reboot did not work.  I then removed the repair partition - still no luck.

Right now my c drive looks like it should.  I think at this point I may reinstall and hope that it keeps my setup.

I will borrow my sisters laptop tonight at dinner, do the livecd and post back tonight or in the morning.

Unfortunately I have to run - I will say that I am excited about converting still and you have all proven what a great community this is over the windows world.

More results later.

---

### Post by amjjawad on 2010-12-24
I might be sleeping when you'll come back. It's too late here now.
If I won't be online then definitely someone else will help you.

Good luck :)

---

### Post by Rhenson68 on 2010-12-24
Thanks so much!

---

### Post by amjjawad on 2010-12-24
> **Rhenson68 said:**
> Thanks so much!

You most welcome and in case I'll be online and found you online too, I'll jump in ;)

Good luck!

---

### Post by msandoy on 2010-12-24
I'll be eating christmas dinner in an hour or two, but I will check in when I have time again. I hope you can manage to save your system settings and files.

---

### Post by Rhenson68 on 2010-12-26
Just wanted to give a final update.  After spending a couple of days trying to repair my boot manager, i finally gave up and ended up backing up my user directory, formatting the drive and reinstallng my os...thanks again for everyones help!

---

### Post by amjjawad on 2010-12-26
> **Rhenson68 said:**
> Just wanted to give a final update.  After spending a couple of days trying to repair my boot manager, i finally gave up and ended up backing up my user directory, formatting the drive and reinstallng my os...thanks again for everyones help!

I'm really sorry to hear that.
Hope everything will go smoothly for you now.

Let us know if you need any help :)

---

