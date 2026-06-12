---
title: "I know this is ubuntu forum but could use some help"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Captainklt on 2011-01-31
I have an windows ops sp1 pro with windows 2000 older computer and it crashed again.  I would rather throw linux on there but i need windows for my printer and all typing programs.  So it won't even let me turn it on just get into boot but i need a boot cd so if anyone has an idea where to download and burn on to this nice runing ubuntu so i can fix the windows on the other it would be greatly appreciated thank you

---

### Post by 12apennachi on 2011-01-31
So let me get this straight. You have xp on your computer with no Ubuntu partition and the xp partition crashed and will not boot so you need a livecd of ubuntu to fix it without access to the computer. Is this all correct?

I meant windows 2000.

---

### Post by Matt__ on 2011-01-31
what exactly is wrong with the pc? (apart from win2000 :P ) 

What specifically requires windows for the printer/typing programs?

you could try this tool [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by bigsmitty64 on 2011-01-31
[http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso)

---

### Post by elliotn on 2011-01-31
What he mean is he want a windows cd to fix his win2000, just search google for it.

Most of the printers works out of the box in linux and Oo.org and other programs are good office programs

---

### Post by Mark Phelps on 2011-02-01
> **Captainklt said:**
> ...so i can fix the windows on the other it would be greatly appreciated thank you

In general, you can't "fix" MS Windows from Ubuntu.

You can do some limited things like replace the MBR, and you can run ntfsfix to repair really trivial NTFS errors, but Ubuntu is not a repair facility for MS Windows.

If you want to mess around with repairing your MS Windows install, Google for Hiren's Boot CD.  It contains LOTS of MS Windows utilities that can be used to repair various things.

---

### Post by Captainklt on 2011-03-16
I need a Boot Cd Along with instructions for solving my black screen death.  Computer turns on and goes black.  any help would be appreciated thanks

---

### Post by wojox on 2011-03-16
> **Captainklt said:**
> I need a Boot Cd Along with instructions for solving my black screen death.  Computer turns on and goes black.  any help would be appreciated thanks

Try this, I find it works well [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en")

---

### Post by lkraemer on 2011-03-16
I just sent you a PM.  I need an Email Address.

It is very possible that your Monitor died or your Graphics card
died. Use some Logical Troubleshooting!

1. If your Video Card is a PCI Card, Power OFF the Computer,
Unplug from the MAINS, and then Carefully Remove and Reseat your
PCI Video Card. Then try one Monitor again.
2. Take the monitor and plug it into the MAINS. (120 VAC)
(Do not connect the Video Cable!)
3. Turn on the Monitor while you watch the Display area & LED.
4. Check to see if the Power LED is "ON". It should be "Green"
during the Initialize Phase, then turn "Yellow" if the Video
isn't present. (Colors may be different on yours, or yours
may work slightly different!)
5. If the Power LED is NEVER "ON" then you have a Power Supply Problem.
Could be AC (Input) or DC (Output) Problem........or Fuse......
6. If the display Quickly Blinks, and displays an error message then it
is likely to be functional. (You won't be able to access the Menu!)
7. Connect the Video to a Good Functional Computer with a known Good
Video Card, and see if you can get to the MENU of the Monitor, if
available. (I prefer to use an old DOS computer for this initial
test, as just TEXT will be displayed initially.)
8. If you know 100% that the DOS text should be displayed, (Typing
"DIR A:" makes the Floppy active), Shine a Bright Light on the Display
and see if you can see some Faint Text. If the Text is present,
then your Backlighting is defective on your Monitor. (Assuming it's
not a CRT type.) Repair the Backlight, as needed. Probably/maybe
some bad caps in the circuits. If you are not Technical Savy, get
someone who is, to assist.......You'll save money/equipment.....
9. Unplug the Video Cable, then Plug it in again, watching the Display
closely. See any changes, Video blinks, Power LED Change?
If not, try a different Monitor, as it may actually be defective.

Ref:
[http://www.edaboard.com/forum.php](http://www.edaboard.com/forum.php)


[http://www.badcaps.net/](http://www.badcaps.net/)
[http://www.badcaps.net/forum/forumdisplay.php?f=30](http://www.badcaps.net/forum/forumdisplay.php?f=30)
[http://www.badcaps.net/forum/showthread.php?t=7130](http://www.badcaps.net/forum/showthread.php?t=7130)
[http://www.badcaps.net/forum/showthread.php?t=7077](http://www.badcaps.net/forum/showthread.php?t=7077)
[http://www.badcaps.net/forum/showthread.php?t=7155](http://www.badcaps.net/forum/showthread.php?t=7155)

That should get you some good information.

Keep in mind, you can tear up more in a few minutes, than a trained
technician is willing to fix......AT YOUR COST!


Also, Since you're running Win2000 it's likely that you won't be
able to run a LiveCD of Ubuntu.  Try Puppy Linux instead.
It should work fine.

lk

---

### Post by grahammechanical on 2011-03-16
You say you see a black screen. Do you see the motherboard flash screen? It should show a message like esc to enter BIOS and tab to see POST messages. If you see these things then you know that the monitor is working. If you press tab and see the Power On System Test messages you might get some information as to why the operating system is not loading. Do you get any error messages?

Switch the monitor on but do not switch on the computer. You might see a message saying no signal or the colour of the screen may change. This would show if the monitor is working.

Your graphic card could be faulty. Do you see or hear hard disc drive activity? Or does the machine stop? 

Regards.

---

### Post by no2498 on 2011-03-17
i have a dell computer and a memory card went bad and only give me a black screen

---

### Post by Captainklt on 2011-05-02
Hello I didn't really try anything on it yet.  I believe it is an OPS either crash or even a virus that re routed some drivers.  Well I fixed it like two years ago from reading an blog about blue screen death or Black screen death.  The computer turns on and the monitor comes on.  The computer led flashing like its loading and then the monitor says Windows loading like it is going to go to the Xp Background but doesn't.  It just goes black and doesn't do anything.  The screen before the black abis lets me go into F1 Options like starting Normal, or Safe Mode, etc. I fixed this same thing earlier by finding an boot cd and then typing some stuff like system root and or other stuff.  But i don't remember what i did and where the cd went? I have alot of Music on the computer that i would like to get off before i switch it to an linux version.  Others recommended puppy version.  My computer is an Windows 2000 xp sp1 Ops Pro I believe let me know with any help.  And please respond like i am computer illiterate thanks for all who reply my address if needed is [email]agentorangetoy@yahoo.com[/email]

---

