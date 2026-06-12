---
title: "Cant see my bios at startup"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by pierreyy on 2011-07-23
I went into my bios and changed a setting that speeds up the boot process(from the hard disk settings), now i cant see my bios when i boot up and i have no clue how to get it back... any suggestions.


 i have a toshiba a665

---

### Post by amjjawad on 2011-07-23
> **pierreyy said:**
> I went into my bios and changed a setting that speeds up the boot process(from the hard disk settings), now i cant see my bios when i boot up and i have no clue how to get it back... any suggestions.


 i have a toshiba a665

Hello and Welcome :)

The SAME Key that you pressed when you first entered BIOS, press that key again. Keep pressing once you turn your machine ON.

Please, make sure to change the start-up delay to 5 seconds at least. 5 sec delay won't kill anyone ;)

Each machine has different BIOS than the other and different Keys that you need to press to enter BIOS.

Maybe it's "Del" or "F2" or "F10".

Good luck!

---

### Post by pierreyy on 2011-07-23
> **amjjawad said:**
> Hello and Welcome :)

The SAME Key that you pressed when you first entered BIOS, press that key again. Keep pressing once you turn your machine ON.

Please, make sure to change the start-up delay to 5 seconds at least. 5 sec delay won't kill anyone ;)

Each machine has different BIOS than the other and different Keys that you need to press to enter BIOS.

Maybe it's "Del" or "F2" or "F10".

Good luck!

thank you... i already tried that and still nothing it automatically goes to the menu where i select which os (dual boot)

---

### Post by amjjawad on 2011-07-23
> **pierreyy said:**
> thank you... i already tried that and still nothing it automatically goes to the menu where i select which os (dual boot)

Have you tried them all? are you sure?
Have you tried "Esc"?
You need to keep pressing once you turn your machine one. Continuous pressing.

---

### Post by Frogs Hair on 2011-07-23
Check your manual if you still have it . The key used to enter the bios can be different depending on the mother board . The bios screen being skipped is what is supposed to happen when the option to speed up boot is used.

---

### Post by pierreyy on 2011-07-23
ill keep pressing i promise:P but it was the f12 button that got me in the bios in the first place... ill press other ones...and ill stop being greedy too:P thanks again guys

---

### Post by amjjawad on 2011-07-23
> **pierreyy said:**
> ill keep pressing i promise:P but it was the f12 button that got me in the bios in the first place... ill press other ones...and ill stop being greedy too:P thanks again guys

You welcome :)
Please let's know what will happen with you!

Good luck ;)

---

### Post by bkratz on 2011-07-23
> **pierreyy said:**
> ill keep pressing i promise:P but it was the f12 button that got me in the bios in the first place... ill press other ones...and ill stop being greedy too:P thanks again guys



Found an online manual for your device page 7-4 says the following"


To change the boot drive, follow the steps below.
1. Hold down F12 and boot the computer. when the TOSHIBA Leading
Innovation >>> screen appears, release the F12 key.
2. Use the up and down cursor keys to select the boot device you want
and press ENTER.  "

it also speaks of the mode you tried

"
Boot Speed
This option allows you to select system boot-up speed.
Fast Reduces system boot-up time. System can boot
    only from the built-in HDD and only internal LCD
   and keyboard are supported during the boot
  process.
Normal System boots up at normal speed (Default).
"

The manual is at

[http://www.pdfuu.com/toshiba-satellite-a665-manual-users-guide-troubleshooting.html](http://www.pdfuu.com/toshiba-satellite-a665-manual-users-guide-troubleshooting.html)

---

### Post by pierreyy on 2011-07-23
> **bkratz said:**
> Found an online manual for your device page 7-4 says the following"


To change the boot drive, follow the steps below.
1. Hold down F12 and boot the computer. when the TOSHIBA Leading
Innovation >>> screen appears, release the F12 key.
2. Use the up and down cursor keys to select the boot device you want
and press ENTER.  "

it also speaks of the mode you tried

"
Boot Speed
This option allows you to select system boot-up speed.
Fast Reduces system boot-up time. System can boot
    only from the built-in HDD and only internal LCD
   and keyboard are supported during the boot
  process.
Normal System boots up at normal speed (Default).
"

The manual is at




  i can officially say i broke the thing... thanks for ur time and effort guys...im always open for new ideas though...


 the toshiba leading innovation doesnt show anymore... is there a way i can restore the thing to the factory settings...a way that doesn't require me to go into the bios(i doubt it but u know)...

---

### Post by pierreyy on 2011-07-23
im looking around to try to find a way to change the bios settings from the command line... does anyone know a way to do that?

---

### Post by wildmanne39 on 2011-07-23
Hi, you can open it up and reset the cmos that should do it I believe.

---

### Post by pierreyy on 2011-07-24
> **wildmanne39 said:**
> Hi, you can open it up and reset the cmos that should do it I believe.

okay... how do i do that?

---

### Post by amjjawad on 2011-07-24
> **pierreyy said:**
> okay... how do i do that?

Since it's a laptop, you need to understand it won't be that easy. I suggest you refer to your manual.
I think in most cases, you need to remove the battery.

[http://www.google.ae/search?q=how+to+reset+CMOS+in+laptops&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.ae/search?q=how+to+reset+CMOS+in+laptops&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Are you sure BIOS is no longer accessible?

---

### Post by Jacobonbuntu on 2011-07-24
....maybe a stupid question, but are you sure f12 is the bios? I remember I had a laptop once, I could press one of the f- buttons for startup options, and a seperate one for the full bios options...
[B]

edit: the manual sais F2 to enter the bios, not F12!!!
[/B]You should startup and press F2 repeatedly, it has to work[B].
[/B]

---

### Post by westie457 on 2011-07-24
Pressing F12 gives you the options to select the boot device for one session only. Correct. Does it also give an option to 'Enter Setup'? If so that will be your entry point to the bios.

Another way if you still have Windows on your hard drive is run Windows and try to change things in the HW Utility.

Failing that it is going be a job for the screw drivers and a look at the technical manual for your box to attempt to find the CMOS-jumpers and reset them.

This is the best solutions I can come up with. Hope they help.

---

### Post by Jacobonbuntu on 2011-07-24
> **westie457 said:**
> Pressing F12 gives you the options to select the boot device for one session only. Correct. Does it also give an option to 'Enter Setup'? If so that will be your entry point to the bios.

Another way if you still have Windows on your hard drive is run Windows and try to change things in the HW Utility.

Failing that it is going be a job for the screw drivers and a look at the technical manual for your box to attempt to find the CMOS-jumpers and reset them.

This is the best solutions I can come up with. Hope they help.


I thought so. 
Is it possible that pierryy set the bios  to surpass the first stage of grub by choosing the "fast boot option", and resetting it to "normal" will fix that? (I guess you managed to enter the bios once by accident :grin:). As the manual sais F2, it should work anyway I guess. (as I said press it repeatedly on startup f.e. 2x per second).

---

### Post by amjjawad on 2011-07-24
> **Jacobonbuntu said:**
> Is it possible that pierryy set the bios  to surpass the first stage of **grub** by choosing the **"fast boot option"**, and resetting it to "normal" will fix that?

Fast Boot Option has NOTHING to do with GRUB ;)

---

### Post by westie457 on 2011-07-24
Another question for the OP. 

Has the option of using a supervisor password been set?

If so you will need to have a look at this link.

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=246045&#246045](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=246045&#246045)

---

### Post by Jacobonbuntu on 2011-07-24
> **amjjawad said:**
> Fast Boot Option has NOTHING to do with GRUB ;)

....it was just a wild guess, I am not really into theoretical stuff \\:D/but I can imagine it somehow messes up the boot process. The manual of my 1001PX net book tells me to disable fast boot up option if I reinstall (any) system....
Anyway, it might be worth a try before taking more drastical actions.

---

### Post by pierreyy on 2011-07-24
> **westie457 said:**
> Another question for the OP. 

Has the option of using a supervisor password been set?

If so you will need to have a look at this link.

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=246045&#246045;](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=246045&#246045;)

no... the only password i have on my computer is the log in for ubuntu and thats it...

---

### Post by pierreyy on 2011-07-24
> **Jacobonbuntu said:**
> I thought so. 
Is it possible that pierryy set the bios  to surpass the first stage of grub by choosing the "fast boot option", and resetting it to "normal" will fix that? (I guess you managed to enter the bios once by accident :grin:). As the manual sais F2, it should work anyway I guess. (as I said press it repeatedly on startup f.e. 2x per second).

i think ive tried every f-key on the keyboard and before something else goes wrong im gunna stop restarting it 20 times in a row...

---

### Post by pierreyy on 2011-07-24
Guys thank you soo much!! i just got it... i held down the f2 button instead of repeatedly pushing it and it put in the boot menu... i changed the boot speed settings into normal again...and now its good as new... 

 again thank you soo much, i owe you!

(and ill never do that one again:P)

---

### Post by Jacobonbuntu on 2011-07-24
> **pierreyy said:**
> Guys thank you soo much!! i just got it... i held down the f2 button instead of repeatedly pushing it and it put in the boot menu... i changes the boot speed settings into normal again...and now its good as new... 

 again thank you soo much, i owe you!

(and ill never do that one again:P)

I am glad things worked out!! I hope your keyboard is not worn out by now \\:D/(just kidding)
have a good time!,
Jacob

---

### Post by westie457 on 2011-07-24
> **pierreyy said:**
> Guys thank you soo much!! i just got it... i held down the f2 button instead of repeatedly pushing it and it put in the boot menu... i changes the boot speed settings into normal again...and now its good as new... 

 again thank you soo much, i owe you!

(and ill never do that one again:P)

HOORAY You did it!!!!!=D>

Mark as solved please

---

### Post by amjjawad on 2011-07-24
Good Job :)
I knew that you'll manage to do it without resetting CMOS :)

Please, mark this thread as SOLVED ;)


[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

