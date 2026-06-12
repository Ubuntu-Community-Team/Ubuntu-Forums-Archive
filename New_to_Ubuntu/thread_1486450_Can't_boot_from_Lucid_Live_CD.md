---
title: "Can't boot from Lucid Live CD"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Tholley on 2010-05-17
I was planning on upgrading to 10.04 from 9.04, and was under the impression it was best to do a fresh install instead of upgrade since it is a LTS. I have 3 computers running Ubuntu, 2 old ones and this semi recent HP Pavilion Media Center. The old ones I can boot from the 10.04 live cd with no problem, this HP I try to boot, get the 2 little icons at the bottom of the screen (a black screen, not the purple haze), then the curser blicks a few times at the top left, then nothing. My moniter goes to sleep like it is not receiving any input, and even my keyboard lights go off. I can see the cd light blinking on the box for a few minutes, but nothing happens.  I have to do a hard shut down. 

I have downloaded 3 different times, from main site and torrent, burnt on 3 different cds, 2 different brands, and even to usb, all the exact same thing.

I saw a bug report on a similar problem, but the screenshot he provided at least showed a partial Lucid screen, and wasn't sure how or if I should add to the report.

The video card in this HP is NVIDIA GeForce 6150 LE
Not sure what else could be a factor.

Thanks!

---

### Post by -humanaut- on 2010-05-17
I have the same video card but I was able to boot into the LiveCD/(USB) without any problems have you tried using the Alternate text-based C.D.?

---

### Post by Tholley on 2010-05-17
> **-humanaut- said:**
> I have the same video card but I was able to boot into the LiveCD/(USB) without any problems have you tried using the Alternate text-based C.D.?

No... I have a copy, but it is only for "upgrading" without a Internet connection.

I can upgrade by using update manager, but wanted to do a fresh install since it is a LTS.

And now, funny thing, I took a closer look at update manager and it only shows upgrade to 9.10 (I have 9.04 on this machine). Even after clicking "check" about 5 times and it telling me my system is up to date, it still only shows 9.10, not 10.04 available for upgrade.

Hmmm... I'll worry about more tomorrow, got an early morning ahead.

If anybody has some good suggestions, I'd appreciate it, and I'll check back in the morning.

Thanks again!

---

### Post by Tholley on 2010-05-18
BTW... this computer in question dual boots w/XP.
 
It has been working great with Jaunty and Grub1, so now I'm not even sure I want to switch to Lucid. :-k
 
The older computer with Karmic and XP on it, does ok too, even tho I had allot of issues at the beginning, (couldn't upgrade, had to do a clean install, and still had issues that took allot of work to get thru) and I don't like grub2 as compared to the versatility of grub1.
 
So if I can't even boot into the Live CD without issues, makes me think any kind of upgrade or install is going to be havoc. :confused:
 
Any good news or suggestions out there? If it turns out to be simple, then I would still like to try, since I hate being outdated, even if outdated sometimes works better.

---

### Post by garvinrick4 on 2010-05-18
If you are running 9.04 you have to go thru 9.10 to get to 10.04 in update manager or command line. That is why update manager is not showing Lucid. Can USB boot in that machine? Worth a try who knows. Does not take to long at all to make a USB drive with 10.04 on it. Look in BIOS and see if you can set USB before HDD leave CD before HDD.
If does not work nice to have Live USB around are quicker than Live CD. Have a nice day.

---

### Post by Tholley on 2010-05-18
>  
Can USB boot in that machine?

 
Tried that already (mentioned it in first post) exact same thing as any of the cds.

---

### Post by fooman on 2010-05-18
when the cd boots up,  press esc, then choose language.

at the next screen,  press f6 for more boot options....choose "nomodeset" from the list,  press enter and see if it boots up.

hope that helps.

---

### Post by John F on 2010-05-18
I had the same problem with my Dell 12" netbook.

I booted, hit Esc as the "Dell" logo came on, then (quickly) F12.
The menu gave me a choice of booting from the CD-ROM and installation started.

John F

---

### Post by Tholley on 2010-05-18
I'll give that a try. 
 
Thanks! :)

---

### Post by -humanaut- on 2010-05-18
> **fooman said:**
> when the cd boots up,  press esc, then choose language.

at the next screen,  press f6 for more boot options....choose "nomodeset" from the list,  press enter and see if it boots up.

hope that helps.


+1 Nomodeset should atleast allow you to boot the LiveCD

---

### Post by Tholley on 2010-05-19
ok... I did all that, checked nomodeset, and was able to access the LiveCD.
 
It just makes me think now, if i had to go to that much trouble just to get into the Live CD, then how much trouble will the install be? [-o<
 
And is it correct that with Lucid/Grub2 that you can have only 2 operating systems?

---

### Post by fooman on 2010-05-19
> **Tholley said:**
> 
And is it correct that with Lucid/Grub2 that you can have only 2 operating systems?

not true.

i fresh installed 10.04 when it was released.... it correctly picked up my suse and vista hard drives and added them to the grub menu.

---

### Post by Catharsis on 2010-05-19
> **Tholley said:**
> It just makes me think now, if i had to go to that much trouble just to get into the Live CD, then how much trouble will the install be? [-o<

You'll most likely just have to add "nomodeset" through grub during your first boot. At the grub menu, highlight your Lucid kernel and hit 'e'. Then type "nomodeset" after "quiet splash". Ctrl+x to boot.

Then make sure your nVidia drivers get installed through System->Administration->Hardware Drivers.

---

### Post by Tholley on 2010-05-20
> **fooman said:**
> not true.
 
i fresh installed 10.04 when it was released.... it correctly picked up my suse and vista hard drives and added them to the grub menu.
 
Thanks for that info... but I could have sworn I readin the release notes or somewhere, like a warning saying something like "if you are running more than 2 operating systems, do not install Lucid..." maybe I was dreaming it, cause I sure can't find the notes now. :)
 
>  
You'll most likely just have to add "nomodeset" through grub during your first boot. At the grub menu, highlight your Lucid kernel and hit 'e'. Then type "nomodeset" after "quiet splash". Ctrl+x to boot.


 
Thanks for that info too... :P

---

