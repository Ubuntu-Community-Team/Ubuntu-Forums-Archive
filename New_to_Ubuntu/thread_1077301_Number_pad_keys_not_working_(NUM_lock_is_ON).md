---
title: "Number pad keys not working (NUM lock is ON)"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by usererror on 2009-02-22
My Numeric keypad on my keyboard and mouse do not work.  Yet the Num Lock key is illuminated.

I checked the Keyboard preferences but did not find anything obvious.

Thanks!

---

### Post by billgoldberg on 2009-02-22
What kind of keyboard is it (make, PS/2, usb, wireless, ...)?

Did it work fine on Ubuntu at a certain time?

Did the behaviour start after performing an update?

Can you test it on another computer?

We need more info.

---

### Post by usererror on 2009-02-22
> **billgoldberg said:**
> What kind of keyboard is it (make, PS/2, usb, wireless, ...)?

Did it work fine on Ubuntu at a certain time?

Did the behaviour start after performing an update?

Can you test it on another computer?

We need more info.

1) Wireless Keyboard Microsoft Laser 6000 v2.0
2) It works fine in Windows (was dual booting) and with 8.04
3) Started when I formatted my hard drive and reloaded with 8.10 no dual boot
4) Works in Windows

---

### Post by Outdoor83 on 2009-02-22
I can think of two types of "not working":

1) you expect numbers when you hit the numpad, but instead get the other things on the keys (arrows, end, home, pgup, pgdown, ins, del, etc)
2) you hit the keys and nothing happens

Which one do you have?  They can indicate two different problems.

Do you have another keyboard to test with?  If you plug in a different keyboard and still have the problem, it's probably not the keyboard.

---

### Post by usererror on 2009-02-26
> **Outdoor83 said:**
> I can think of two types of "not working":

1) you expect numbers when you hit the numpad, but instead get the other things on the keys (arrows, end, home, pgup, pgdown, ins, del, etc)
2) you hit the keys and nothing happens

Which one do you have?  They can indicate two different problems.

Do you have another keyboard to test with?  If you plug in a different keyboard and still have the problem, it's probably not the keyboard.

This is crazy.  I was getting what you described as both #1 and #2.  I would hit the num pad keys and would expect numbers (since the num lock light is on) but I would get nothing, not even up or down motions.

I just got another keyboard finally and I plugged it in, and then hit num lock, checked the light, it was on, pulled up gedit and **i got numbers!**. I unplugged the test keyboard and made sure numlock was on with the original keyboard and i got numbers again!

so confused.  Will see what happens when I reboot later.

112316456789456489789456456498415615  --> all num pad entries.

---

### Post by usererror on 2009-07-26
i am bringing this back up from the past since it's still not fixed. :(

i put the offending keyboard and mouse all on another PC and the NUM lock pad works as expected with num lock on and off.

in ubuntu it doesn't do anything, with num lock on or off. suggestions? :confused:

---

### Post by usererror on 2009-08-01
OK, now i've tried a completely different keyboard and still same thing Gnome does not see my num lock being turned on.  The keyboard also works on another computer.

this all started after upgrading to 9.04

---

### Post by usererror on 2009-08-01
FOUND SOLUTION!!

[http://ubuntuforums.org/showpost.php?p=4948640&postcount=2](http://ubuntuforums.org/showpost.php?p=4948640&postcount=2)

The option to control the mouse with the number pad got turned on at the upgrade.  GRRRRRRRRRRR.

---

### Post by mr_skater99 on 2009-08-03
I've got a similar problem.

The Numlock is on at boot - LED and working (number when i type).

This continues right up to the gnome login screen (can use the numpad to login).

But once i log in the numlock led goes out - but the numlock is still "on" as in i type on the numpad and get numbers. 

If i then hit numlock, the led comes on - but the numlock is actually - "off".  I tried another USB keyboard and it did the exact same thing.

How has this got out of sync???

---

### Post by oakbox on 2010-04-28
> **usererror said:**
> My Numeric keypad on my keyboard and mouse do not work.  Yet the Num Lock key is illuminated.

I checked the Keyboard preferences but did not find anything obvious.

Thanks!

For me, the '0' key was the only one not working.  The mouse buttons solution was not the problem.  
After every reboot, I have to go into 'System > Preferences > Keyboard > Layout' and change the layout to 'something else'.  As soon as I make a change here, Ubuntu suddenly starts recognizing the Num Lock key and zeros start coming on the screen.

Frustrating!!!!

---

### Post by spier on 2010-09-21
> **usererror said:**
> FOUND SOLUTION!!

[http://ubuntuforums.org/showpost.php?p=4948640&postcount=2](http://ubuntuforums.org/showpost.php?p=4948640&postcount=2)

The option to control the mouse with the number pad got turned on at the upgrade.  GRRRRRRRRRRR.

I've got the very same problem, runing ubuntu 10.04, kernel 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux.

The solution found in the above link (setting Keyboard preferences) corrected it!

Thanks!

---

### Post by twizler on 2010-09-29
THANK YOU it works -- I also had the issue --  thanks to bluefrogs post of the unmark --> system/preferences/keyboard [mouse key tab]
uncheck the box. BACK TO NORMAL!! 


[IMG]http://img96.imageshack.us/img96/509/ubuntunumlock.png[/IMG]

---

### Post by joama on 2010-10-08
> **usererror said:**
> FOUND SOLUTION!!

[http://ubuntuforums.org/showpost.php?p=4948640&postcount=2](http://ubuntuforums.org/showpost.php?p=4948640&postcount=2)

The option to control the mouse with the number pad got turned on at the upgrade.  GRRRRRRRRRRR.

It worked with me too :), I have a msi A6200 laptop and the number pad on the keyboard stopped working although Num lock is on it was driving me crazy thanks :)

---

### Post by meehan80 on 2011-06-07
Had the same problem. My cat changed the setting somehow ???, was pulling my hair out to figure it out. This was the solution for me too. (to deselect the pointer control box under keyboard preferences, mouse tab)

---

