---
title: "Problems Burning a CD"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Julian Sidewind on 2009-11-05
Hey guys, 

I recently downloaded Kubuntu both 32 and 64 bit, and when i try to burn one, it says it burns all sectors, but when it verifies, it says the cd is smaller than the iso file and i realize there are 2 bad sectors on the cd.

I know it isn't a problem with my burner because i just burned a copy of windows 7 professional 64 bit and installed it and it worked, so now i want to add a partition with Kubuntu, and i can't get a working cd.

Thanks

---

### Post by uberg on 2009-11-05
What are you using to burn the CD?

---

### Post by Julian Sidewind on 2009-11-05
ImgBurn... used this for the dvd that worked too.  Maybe i should mention im burning it on a regular cd instead of a dvd though that shouldnt matter

---

### Post by uberg on 2009-11-05
Try using KD3 or another burner.  I had this problem before (in an older version of Ubuntu; can't recall which) and the solution at the time was to use another burner.  KD3 is what I ended up using.

---

### Post by Julian Sidewind on 2009-11-05
Well im running windows so i dont think i can run that :P
But ill try another one

---

### Post by uberg on 2009-11-05
Ahhh, gotcha!  Can't help you there but good luck in your journey.  If you have a usb keychain you can create a liveUSB device.  I think that unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) has a binary for Windows and will then let you put the image on the USB device.

---

### Post by Julian Sidewind on 2009-11-05
Thanks, im currently trying the windows disc image burner
if that doesnt work ill definitely try to make a usb bootable

thanks a lot

---

### Post by alien8predator on 2009-11-05
> **Julian Sidewind said:**
> Thanks, im currently trying the windows disc image burner
if that doesnt work ill definitely try to make a usb bootable

thanks a lot

try this:

[http://cdburnerxp.se/](http://cdburnerxp.se/)

---

### Post by coldReactive on 2009-11-05
Infra Recorder if anything else fails on windows.

---

### Post by uberg on 2009-11-05
I have generally found that the installation is a lot quicker from a USB device than a CD too.  Good luck!

---

### Post by alien8predator on 2009-11-05
> **uberg said:**
> I have generally found that the installation is a lot quicker from a USB device than a CD too.  Good luck!

I agree :)

---

### Post by Julian Sidewind on 2009-11-05
Ok good news and bad news

Good news - installed Kubuntu via USB, worked great

Bad news - i accidentally deleted the part of the task bar that shows what windows are open...anyone know how i can get it back?

---

### Post by Julian Sidewind on 2009-11-05
Ok i installed kubuntu with the usb and i have another problem...i acidentaly deleted the part of the task bar that hows you what windows you have open, if anybody knows how to bring that back. Thanks

---

### Post by uberg on 2009-11-05
Oh Crap.  Didn't think you could delete that.  And I just tried to prove it too.  Hee Hee.

So far if you right click the other task bar and hit new panel.  This should just go to the bottom but if it doesn't right click it and adjust this through the properties menu.

Then right click and add hit Work Place switcher.

As soon as i figure out how to add the open applications i'll let you know.

---

### Post by uberg on 2009-11-05
You also readd "Trash" this way but I can't figure out how to get the windows open list working again.

---

### Post by Julian Sidewind on 2009-11-05
lol i hope you figure it out soon, didnt mean to make you delete it too :P

---

### Post by uberg on 2009-11-05
That is all part of the fun Julian.  Did you try what I suggested so far?

---

### Post by Julian Sidewind on 2009-11-05
I actually forgot about it until i realized i could use the usb boot disk you said i could make created and i used that to see what that widget was called that i deleted, turns out its the task manager widget, so i just added it and moved it back to where it was with panel settings and bang, back to normal.

Team effort!

---

### Post by rbee on 2009-11-05
try using burncdcc--never had problems burning iso with it

---

### Post by uberg on 2009-11-05
I can't find that widget.

---

### Post by Julian Sidewind on 2009-11-06
its called task manager, you just right click on the bar and go add widget, it should be there.  I;m using 9.10 if that makes a difference

---

### Post by uberg on 2009-11-06
I right click on the bar and hit "Add to Panel" but there is no entry for "Task Manager".  There is no mention of widget either although i know that is what these are.  I am using 9.10 too, so that shouldn't make a difference.  I don't know what I am not doing here.  Yikes! lol

---

### Post by Julian Sidewind on 2009-11-07
Ok see snapshot 1 for what i see when i right click in an arbitrary part on the task bar, and the highlighted entry is what you should click on, snapshot 2 is the window where i selected task manager.

If this doesn't work i really don't know what to do...maybe show what you see?

---

### Post by uberg on 2009-11-07
Hey Julian, thanks for posting those.  I figured out where you and I were having a communications problem.  You are using KDE, right?  I am using Gnome.  Slightly different nomenclature.  I did figure out what I needed though.  When I right click on it doesn't have the widget option just "Add to panel".  And the item I was looking for is "Window List"  I think when I was attempting to add it before it was adding it in an area where it couldn't expand like it usually does.  But I have it now.

Julian, I want to wish you luck in your Linux adventures.  It can be frustrating as hell sometimes but once you get into it you will never want to go back to the other OS.  

Take care Brother and I will see you around the forums.

---

### Post by Julian Sidewind on 2009-11-07
Thanks a lot uberg, you too.

---

### Post by PhattyPhorumer on 2009-11-10
> **alien8predator said:**
> try this:

[http://cdburnerxp.se/](http://cdburnerxp.se/)
I used this and i'm having the same problem as the OP. CDburnerXP won't burn it it either.

---

### Post by Julian Sidewind on 2009-11-10
Use a USB drive like suggested earlier.  That's what ended up working for me.

---

### Post by PhattyPhorumer on 2009-11-10
ok will do

---

### Post by PhattyPhorumer on 2009-11-10
Sooo... How do u run it from a USB? I put the files on the stick.

---

### Post by MelDJ on 2009-11-10
> **uberg said:**
> I right click on the bar and hit "Add to Panel" but there is no entry for "Task Manager".  There is no mention of widget either although i know that is what these are.  I am using 9.10 too, so that shouldn't make a difference.  I don't know what I am not doing here.  Yikes! lol

it should be system monitor.

to PhattyPhorumer
change your BIOS to boot from USB

---

### Post by PhattyPhorumer on 2009-11-10
Yeh but I accessed a ubuntu site that told me i had to do all this **** before it would be bootable.

---

### Post by MelDJ on 2009-11-10
could you show me the site?

---

