---
title: "I installed Ubuntu and now my Computer won't turn on!  (It's okay now)"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by trulan on 2009-06-07
While I am not new to computers, I am an absolute beginner in all things Linux.  I installed Ubuntu Studio 9.04 three days ago.  I have had quite the adventure, and thought some of you might enjoy reading about it.

I had a spare 100gb hard drive, so I put Ubuntu on that and left my Windows XP drive untouched.  Other than messing up on the software packages I wanted to install (I hit enter when I should have hit the spacebar - grrr...) the installation was easy and painless.

My screen was flickering and the resolution was horrible, but I had Ubuntu up and running!!  Sound worked out of the box, and getting on the internet again took me less than five minutes.  The screen resolution and flickering was another story though.  I have since learned that most of the advice on this topic is a bit out of date and does not quite apply to Ubuntu 9.04.  More on that later.

Let's just say that I succeeded in editing xorg.conf just enough to hose my graphics support.  Not exactly what a beginner wants to do.

I booted into Windows to scour the forums for a solution.  Got some ideas, booted back into Ubuntu to try them.  Nothing worked, but I did accidentally discover that I could hit the up arrow and cycle back through the commands I had entered, even those done before my last reboot when I had messed everything up in the first place.  I found an earlier command that looked good and ran it.  Then, unsure how to just restart from the command prompt, I turned my computer off.

That was the last thing it did.

No amount of button pressing, holding, cord pulling, computer disassembling, cable re-setting, had any affect at all.  My computer was dead.  The only response I could get at all was a flashing green light on the back of my power supply, accompanied by a light ticking sound.

I did happen to have a borrowed laptop on hand, and was on the interet once again, looking for clues and maybe a ray of hope, a way to undo the massive destruction I had caused.  Googling the phrase 'computer won't turn on flashing green light' turned up some very interesting and helpful results.  It seems that HP (which is what my PC is) has a bad habit of under-sizing their power supplies, and mine had chosen this very inopportune moment to give up the ghost.

Fast-forward two days.  I now have a new power supply in my computer.  I have just finished hooking up all the cables, and plugging it into the power strip.  I flipped the switch on the back of the new power supply (the old one just had the little green light), and to my dismay, nothing happened.  My computer was still dead, and no amount of plugging and unplugging had any affect.

Then I remembered the little button on the front. :oops:

I was happily surprised to learn that not only did my PC power up, but also, that last command I had run had successfully re-enabled graphics support!

I was also happy to find that what my screen needed was not to have xorg painstakingly manually edited, or even to find and run some magic command line.  All I had to do was enable the NVidia (that's my graphics chip) drivers in System/Administration/Hardware Drivers.

Soooo, now maybe I am ready to tackle my next project - firewire audio support.  That's actually what I was after when I installed Ubuntu studio - a way to defeat whatever was putting the pops and clicks in my recordings done through Windows.  But that's another subject for another day.  Hope you enjoyed my story!

---

### Post by switch10 on 2009-06-07
Hey trulan.  Welcome to Ubuntu Studio!  It's pretty cool huh?  I myself have been recording with Cubase on Windows for many years.  I just switched to Ardour, and it is great!  It works way better than Cubase in my opinion, and it was a lot easier to configure as well.  I was getting xrun's at first because I am running Compiz-Fusion, but I setup a seperate user account for recording and now it works flawlessly.  

Have fun man.  See you around.

Dave

p.s. check out RoseGarden if you have a midi keyboard controller.  its rad.

---

### Post by LewRockwell on 2009-06-07
[http://www.newegg.com/Product/Product.aspx?Item=N82E16899705003](http://www.newegg.com/Product/Product.aspx?Item=N82E16899705003)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

"must have" items for the home technician...

---

