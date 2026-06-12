---
title: "Can no longer boot from live usb"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by beew on 2011-07-05
Well actually it is a bit more complicated than the title suggests. 

My friend has a hp pavilion dv2 netbook [http://www.handingchao.com/hp-pavilion-dv2-is-available-features-specs-and-price/](http://www.handingchao.com/hp-pavilion-dv2-is-available-features-specs-and-price/)

 I am going to install Ubuntu on. I have tested it for a few weeks and everything worked flawlessly. That was a few weeks ago, since I couldn't get around to install it and teach her how to use it, she took the netbook back and has been using Vista in the mean time.  

Today she came and told me she is having problems again. Basically whenever the netbooks boots up it gives a loud beeping sound (it is not overheat) and the touchpad and keyboard doesn't seem to be working right (when highlights an item in a menu by placing the cursor on the item the highlight would keep shifting up in a wavy fashion, the keyboard doesn't seem responsive at time.

Ran the virus scan, nothing, ran Windows update, nothing changed.  

I then tried to boot into Ubuntu but it wouldn't boot, instead I am stuck in the splash screen (with the Ubuntu logo and the 4 dots) which flickers like crazy.

The live usb has no persistence (so nothing unusual has been installed) and it works on other computers.

Like I said I had ran tests on this for a few weeks and everything worked. 

I think maybe the hardware is damaged, but can't say what it is. Can't be the hard disk as booting from a live usb shouldn't depend on what happens to the internal disk. Maybe the graphic card?

Any idea? Thanks.

---

### Post by androssofer on 2011-07-05
does sound like hardware... perhaps overheating...? is it 1 long beep?

my only suggestion wud be turn it all off, run a vacuum over all the vents, with extra time spent on cpu area... get the dust out.. i used to have an acer that i could only install stuff on when i used air spray on the cpu wen running it... 

past tht its out of my league... might be (dare i say it) new laptop time?

---

### Post by wildmanne39 on 2011-07-05
> **beew said:**
> Well actually it is a bit more complicated than the title suggests. 

My friend has a hp pavilion dv2 netbook [http://www.handingchao.com/hp-pavilion-dv2-is-available-features-specs-and-price/](http://www.handingchao.com/hp-pavilion-dv2-is-available-features-specs-and-price/)

 I am going to install Ubuntu on. I have tested it for a few weeks and everything worked flawlessly. That was a few weeks ago, since I couldn't get around to install it and teach her how to use it, she took the netbook back and has been using Vista in the mean time.  

Today she came and told me she is having problems again. Basically whenever the netbooks boots up it gives a loud beeping sound (it is not overheat) and the touchpad and keyboard doesn't seem to be working right (when highlights an item in a menu by placing the cursor on the item the highlight would keep shifting up in a wavy fashion, the keyboard doesn't seem responsive at time.

Ran the virus scan, nothing, ran Windows update, nothing changed.  

I then tried to boot into Ubuntu but it wouldn't boot, instead I am stuck in the splash screen (with the Ubuntu logo and the 4 dots) which flickers like crazy.

The live usb has no persistence (so nothing unusual has been installed) and it works on other computers.

Like I said I had ran tests on this for a few weeks and everything worked. 

I think maybe the hardware is damaged, but can't say what it is. Can't be the hard disk as booting from a live usb shouldn't depend on what happens to the internal disk. Maybe the graphic card?

Any idea? Thanks.Hi, I worked on a dell 2 weeks ago and on there site they had a listing for the computer that told what each sound meant when it was having an error, hp might have the same thing, anyway since you can not use usbpendrive, I would think it is either the memory or the bios, you might reseat the memory and perhaps see if anything changed in the bios that you can see. Even if the hard drive was not working it would not stop the pendrive from being loaded into ram.

---

### Post by beew on 2011-07-05
Don't think it is overheating because I get the beep sound  even if the netbook has been off  for hours and is cold.

Also ran memory check in BIOS and it said pass.

---

### Post by beew on 2011-07-05
So, any theory?

---

### Post by beew on 2011-07-06
Bump!

---

### Post by wolfgangmcq on 2011-07-06
Does it do it if you hit F12 or F1 or ESC or whatever and get into the BIOS? What about after you leave the BIOS?

---

### Post by beew on 2011-07-06
> **wolfgangmcq said:**
> Does it do it if you hit F12 or F1 or ESC or whatever and get into the BIOS? What about after you leave the BIOS?

I could get into and leave the BIOS with no problem.

---

### Post by smurphy_it on 2011-07-06
As wildmanne39 suggested there are beep codes specific to each BIOS manufacturer.  Go into your BIOS and find out what kind it is.  It would be something like:

Award BIOS
AmiBIOS
etc...

Post the Manufacturer of the BIOS and the BIOS Revision.  Once that information is gathered its pretty trivial to find out the beep codes for that specific BIOS.

---

### Post by wolfgangmcq on 2011-07-06
Does it make the funny beep after you exit the bios, or before?

---

### Post by beew on 2011-07-06
> **wolfgangmcq said:**
> Does it make the funny beep after you exit the bios, or before?

It makes the beep when booting, after exiting the BIOS there is no beep, but restarting it starts beeping again. Another thing is that Vista keeps doing check disk on startup but it says it is fine everytime.

---

### Post by wolfgangmcq on 2011-07-06
Even if it doesn't beep (ie you enter the BIOS), does it still act odd? Also, does Vista have other hardware checks (besides just the HD)? If so, have you run them?

---

### Post by beew on 2011-07-06
> **wolfgangmcq said:**
> Even if it doesn't beep (ie you enter the BIOS), does it still act odd? Also, does Vista have other hardware checks (besides just the HD)? If so, have you run them?

Yeah, it acts very odd, the scrolling and the cursor doesn't seem to be working. Say if you want to highlight an item on a menu by placing the cursor on it and the highlight would just keep moving up (this is in Vista, to be clear)

I have checked memory with the BIOS and it came up clean (it has only hd check and memory check) I don't think it is a hd problem though as it shouldn't affect booting off a Ubuntu live usb.

---

### Post by beew on 2011-07-06
Oh yeah I can stop the beeping by pressing the space bar and after that instead of booting into vista a menu thing show up with options like "starting Windows normally"..

---

### Post by beew on 2011-07-06
I tried booting from another usb (with a full install of Ubuntu) Press spacebar to stop te beeping and the grub menu showed up normally, then a whole screen is overflown with "^CCA" (with square "C") and then it starts showing a whole page of "starting.. stopping .. [OK] ..." it just keep scrolling  nonstop

---

### Post by beew on 2011-07-07
Hello?

---

### Post by cre8ive65 on 2011-07-07
Check the CMOS battery? (the little watch battery in the computer)

---

### Post by createdcreature on 2011-07-07
Try a BIOS upgrade. They will be given out by the manufacturer of your PC on the website. Probably a buggy BIOS.

---

### Post by linuxman94 on 2011-07-07
> **cre8ive65 said:**
> Check the CMOS battery? (the little watch battery in the computer)
The cmos battery only prevents the bios settings from being cleared when the power is disconnected or the battery is dead.  It would not cause the problem the OP is having.

Oh and i completely agree with Robert.  Check for a new bios.

---

### Post by smurphy_it on 2011-07-07
Hmm... Are you using a USB Keyboard or a PS/2 style ?

If it's a ps/2 style, unplug it and verify the PINS are good.  They can cause a faulty connection, which could be causing the temp errors and beeping.

PS.  I'm still waiting on what type of BIOS you have ;-)

---

### Post by beew on 2011-07-07
> **smurphy_it said:**
> Hmm... Are you using a USB Keyboard or a PS/2 style ?

If it's a ps/2 style, unplug it and verify the PINS are good.  They can cause a faulty connection, which could be causing the temp errors and beeping.

PS.  I'm still waiting on what type of BIOS you have ;-)

It just says PhoenixBIOS  (version F.03) in the setup utility. It is not a USB keyboard (so it is a Ps/2?) I don't know how to unplug it to verify the pin.

---

### Post by wolfgangmcq on 2011-07-08
If it's a laptop, the keyboard isn't USB *or* PS/2.

---

### Post by smurphy_it on 2011-07-11
If it's a standard PS/2 keyboard plug, just trace the wire back to the source.  It's a small round plug.  Unplug it, and look inside, see if any of the pins are bent.  If they are, you should be able to fix them with a small screwdriver or flat instrument.  Just bend them back to being vertical again, and plug it back in.  If they are really, really bad.. replace the keyboard.

If it's a laptop, it's neither.

---

### Post by smurphy_it on 2011-07-11
```
It just says PhoenixBIOS (version F.03)
```

Refer to the below webpage, and have a look at the beep codes.  I don't recall seeing an explanation of the beeps in your posts, so this website should help you out.

[http://www.bioscentral.com/beepcodes/phoenixbeep.htm](http://www.bioscentral.com/beepcodes/phoenixbeep.htm)

---

