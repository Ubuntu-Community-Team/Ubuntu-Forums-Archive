---
title: "Sylvania Meso with Ubuntu won't recharge battery from a.c."
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Bob Barrett on 2009-10-15
Hi,  I've got a Sylvania Meso with Ubuntu Netbook Remix.  Worked fine until the battry stopped recharging when the a.c. was connected.  Nothing wrong with the cord.  A brief message came up while it was booting that said it couldn't find the battery or ac connection or something.  There is only 3 minutes of battery time left, and I'm afraid to boot it up until I know what to do.

I can't find a tech support for this product.  The local Best Buy told me they'd charge $129. to look at it.  

Can anyone help?

Thanks, Bob

---

### Post by LowSky on 2009-10-16
Will it run without the battery plugged in?

if no something is wrong with the PC... most likely something internal.

---

### Post by Bob Barrett on 2009-10-16
Hi, LowSky,  Yes, it will run with out the ac.  The problem seems to be that the ac doesn't charge the battery.  I think it's a software problem.  Do you think that reinstalling the operating system would help?  Do you know how to do that?  Thanks for your help.
Best, Bob

---

### Post by LowSky on 2009-10-16
It isn't a OS issue. The OS just reports battery time. So it either a bad power line or bad battery.

Try a Live CD or Live USB of Ubuntu if you like but it will most likely confirm what I'm telling you.

---

### Post by starcannon on 2009-10-16
Some things too try:

[LIST=1]
[*]Leave it plugged in and turned off, every netbook and laptop I've dealt with are happy to recharge while turned off, if your's isn't then continue on reading anyway.
[*]Take the battery out, with the battery out, and the power adapter unplugged from the machine, press the power button a few times, then wait for about 45seconds. Now plug it all back in and see how it behaves.
[*]Enter Bios Setup as soon as the computer boots, I believe the key to rattle as soon as you turn it on is F2, at least it is on this Everex Cloudbook, and I believe it is a twin to the Sylvania Meso. Go to the last tab of the Bios Setup screens, and choose "Load Setup Defaults" or the equivalent. Press F10 and agree to save and quit. Now see how the system behaves.
[/LIST]
Other than digging around and finding out how to fry cmos that's about all I can think of at the moment, and definitely where I'd start if one of my netbooks started misbehaving in the same manner as yours.

GL

P.S. I agree that it is highly unlikely to be the OS, this is either as mentioned a bad cable, power supply, or possibly a corrupt cmos(which is why I gave the instructions I gave). I hope its just a corrupt cmos setting and that one of the methods I listed will fix you. Otherwise get a tester on the power supply.

---

### Post by Bob Barrett on 2009-10-16
Hi, again, LowSky,

Thanks for your speedy response.  My problem is that there is only 3 minutes of battery time left, and I'm afraid to boot it up because that takes a couple of minutes.  
I'm boggled.
Best, Bob

---

### Post by Bob Barrett on 2009-10-16
Thanks, Starcannon,  I'll try that and get right back on to let you know (hopefully) that it worked.
Best, Bob

---

### Post by lavinog on 2009-10-16
> **Bob Barrett said:**
> Hi, again, LowSky,

Thanks for your speedy response.  My problem is that there is only 3 minutes of battery time left, and I'm afraid to boot it up because that takes a couple of minutes.  
I'm boggled.
Best, Bob

He was asking to take the battery out, then see if it will turn on.

---

### Post by Bob Barrett on 2009-10-16
Yes, it will work if I take the battery out, put it back in, then turn it on.  The battery is very low.

do you mean that I should try to take the battery out, plug it in, then try to boot it up with the battery out?

---

### Post by starcannon on 2009-10-16
> **lavinog said:**
> He was asking to take the battery out, then see if it will turn on.
+1 

I know some laptops do not allow this, but I know my Everex Cloudbook does, just checked too make sure. I'm not sure if the Meso is the twin to the Cloudbook, the [Sylvania g]("http://www.digitalgadgets.com/products.php?p=g") is though.

GL

---

### Post by Bob Barrett on 2009-10-16
Now I can't find a Bios Setup!  I'm really a Mac person, and I love this linux, but I do feel like a kindergardener here.  Thanks for the continued help, everyone.

Enter Bios Setup as soon as the computer boots, I believe the key to rattle as soon as you turn it on is F2, at least it is on this Everex Cloudbook, and I believe it is a twin to the Sylvania Meso. Go to the last tab of the Bios Setup screens, and choose "Load Setup Defaults" or the equivalent. Press F10 and agree to save and quit. Now see how the system behaves.

---

### Post by lavinog on 2009-10-16
> **Bob Barrett said:**
> 
do you mean that I should try to take the battery out, plug it in, then try to boot it up with the battery out?

Yes.
The purpose is to check that the ac power is sufficient to run the laptop.

There are faults that can occur where the ac adapter voltage seems fine until a load is attached.

---

### Post by lavinog on 2009-10-16
> **Bob Barrett said:**
> Now I can't find a Bios Setup!  I'm really a Mac person, and I love this linux, but I do feel like a kindergardener here.  Thanks for the continued help, everyone.


bios is not specific to linux...do macs not have a bios? (I never had a mac)

---

### Post by Bob Barrett on 2009-10-16
> **lavinog said:**
> Yes.
The purpose is to check that the ac power is sufficient to run the laptop.

There are faults that can occur where the ac adapter voltage seems fine until a load is attached.

You are so kind to be helping me.  Nothing happened when I tried to boot it up with the ac power connected and the battery out.

I then disconnected the ac power and hit the power button a few times, waited, then reinstalled the battery, turned on the ac, and tried to boot it up.  It did boot up, and the battery says it is half charged (when I turned it off last, the battery icon was almost empty.  So that's a good sign.  It is now turned off with the ac connected, and hopefully it is charging.

However:  when it booted up, a very brief message popped up in what looked like DOS, that said something about the battery module - not connected or not detected?  

Should I just let it sit for a couple of hours plugged in and see if when it boots up it has a full battery?  And see if that message pops up?

Also, I couldn't find the Bios setup.  F2 didn't work.

Thanks for your helpfulness,
Best, Bob

---

### Post by lavinog on 2009-10-16
> **Bob Barrett said:**
> You are so kind to be helping me.  Nothing happened when I tried to boot it up with the ac power connected and the battery out.


It sounds like a bad charger then.  Do you have access to another charger?  Is there a store that has one on display that they might let you test with your laptop?

Carefully inspect the charger cable for any cuts.  Try another wall outlet.
Is there an indicator light on the charger to show that it has power?
Does the plug spark when you plug it into the wall outlet?
How do you store your charger? Do you wrap the cables tightly? You want to be careful that you do not bend the cable too tight.

You might want to call the tech support for that manufacturer...many companies will send you a new charger if it is in the warranty period.

---

### Post by starcannon on 2009-10-16
> **lavinog said:**
> bios is not specific to linux...do macs not have a bios? (I never had a mac)
Mac's do not have a bios like we using PC's think of it; they have EFI, which is actually nicer, I wish the PC world would switch to something like it.
[http://guides.macrumors.com/EFI](http://guides.macrumors.com/EFI)

---

### Post by lavinog on 2009-10-16
I searched sylvania's website for information about the bios...there is a bios update for suspend issues, but there doesn't seem to be any way to access the bios...weird design.

Their website doesn't offer much in documentation.  One reason why I prefer HPs and Dell...They have documentation for everything.

---

### Post by starcannon on 2009-10-16
If the boot splash screen does not list an F-key or some other hotkey for accessing setup, then you can try rattling the Esc(ape) key, this will bring up a boot menu on most computers, sometimes a menu option for "setup" is in there. Another option is to try all the F-keys, requires lots of Ctrl+Alt+Del till you find the right one, but I have successfully found Bios Setup access keys using that method, I have also been known to just run my fingers back and forth across the F-key row during boot, the down side to this method is your never really sure which F-key got you in lol.

GL

P.S. 
F2, F10, and F12 are the three most common F-keys for accessing Bios.

---

### Post by lavinog on 2009-10-16
I found a review that said that there was no way to access the bios setup.

---

### Post by starcannon on 2009-10-16
Ouch, no way to access?
I'd call Sylvania Support and see if there is a secret squirrel handshake:
**888-571-0866**


That's the number from their website:
[http://www.digitalgadgets.com/gmesonotebook.php](http://www.digitalgadgets.com/gmesonotebook.php)

---

