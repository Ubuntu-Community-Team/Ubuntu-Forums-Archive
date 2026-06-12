---
title: "How do you enable wireless networking?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by ranch hand on 2010-02-03
Running searchs on this I can find plenty of answers to questions for problems that come up after enabling, but nothing on how in flinder ation you do this in the first place.

I have always been on dial up until March of 2009.  Moved to where DSL is available.

Bought this laptop for my wife.  Got it 2days ago.  Works great on the wire.  This town of 500 does not have wireless around.  We have no wireless router.  A local bar has wireless.

They give you a number to plug in to where ever it goes.  I have no idea what this number is for or where it goes.

I do know that I do not have the option of enabling a wireless connection in network manager.  I need to edit an "account".

This Sys76 Pang7 has an Intel Corporation Wireless WiFi Link 5100. 

I have no idea where to go from here.  Can anyone give the clueless a clue?

---

### Post by mikewhatever on 2010-02-03
I'd assume that a System76 product should work out of the box with Ubuntu. At least the laptops with Intel wifi I've seen had wireless available without any tweaking. Perhaps there is a button to turn it on, fn something or the other.
Generally speaking, once wireless is enabled, you should just click on the network manager icon, wireless networks are displayed, you pick one, and the network manager asks for a password.
Post the output of the following to see what's going on:

sudo lshw -C network

---

### Post by Sealbhach on 2010-02-03
Have you checked that you have enabled the hardware drivers, if you need to do that?

.

---

### Post by nhasian on 2010-02-04
> **ranch hand said:**
> I do know that I do not have the option of enabling a wireless connection in network manager.  I need to edit an "account"

thats the key right there.  If your wireless network card is enabled and functioning properly you should see any wifi access points just by left clicking on the wifi icon on the top taskbar next to the sound icon.  my HP laptop has a hardware switch on the front of it.  if i bump it sometimes i turn it off by mistake and i have to switch it back on.  Other laptops may have a software switch where you have to press the Fn button in combination with one of the Fkeys to enable/disable wifi adaptor.

Also i've seen some computer Bios have options for On/Off/Auto or something like that.  if thats the case, you should force it ON and save the bios settings.

---

### Post by ranch hand on 2010-02-04
> **mikewhatever said:**
> I'd assume that a System76 product should work out of the box with Ubuntu. At least the laptops with Intel wifi I've seen had wireless available without any tweaking. Perhaps there is a button to turn it on, fn something or the other.
Generally speaking, once wireless is enabled, you should just click on the network manager icon, wireless networks are displayed, you pick one, and the network manager asks for a password.
Post the output of the following to see what's going on:

sudo lshw -C network
I will send that later.  Not on that machine as wife is home and this is to be a surprise.

I will also look for a button, never crossed my mind to look.  Laptops are also brand new in my universe.

---

### Post by ranch hand on 2010-02-04
> **Sealbhach said:**
> Have you checked that you have enabled the hardware drivers, if you need to do that?

.
I did do that and there was nothing listed.

---

### Post by ranch hand on 2010-02-04
> **nhasian said:**
> thats the key right there.  If your wireless network card is enabled and functioning properly you should see any wifi access points just by left clicking on the wifi icon on the top taskbar next to the sound icon.  my HP laptop has a hardware switch on the front of it.  if i bump it sometimes i turn it off by mistake and i have to switch it back on.  Other laptops may have a software switch where you have to press the Fn button in combination with one of the Fkeys to enable/disable wifi adaptor.

Also i've seen some computer Bios have options for On/Off/Auto or something like that.  if thats the case, you should force it ON and save the bios settings.
I feel kind of silly that I didn't think about a switch/button.  Never fooled with a laptop before.

I will also check the bios.  I was in there but only to change the boot order so that I can boot from an external drive.  I want the boot menu to need a password and while you can do that it is easy to screw so I want to be able to get in and fix it easily.

---

### Post by ranch hand on 2010-02-05
Got the bugger going.  In this case it is fn+f11 to enable wireless.

Then calling the nice folks at System 76 I was told what I was to look for in the network applet.  Went to where there is a wireless connection and sure enough it works real slick.  Slightly harder than the DSL connection in that you do have to pick a connection (hard in this case - only one).

It really is kind of cool.

Thanks for the hints and suggestions.

I'll mark it solved.

---

