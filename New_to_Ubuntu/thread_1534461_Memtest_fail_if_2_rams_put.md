---
title: "Memtest fail if 2 rams put"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Kangarooo on 2010-07-19
Ive tested memtest for 512mb sdram in slots 1 and 2
failed
tested each seperatly in slot 1 went to 100% pass for both
tested in slot 1 and 3 both toghether failed.
why?
is it possible to lock bad sectors?
how can i scroll up and down in memtest? (SP)scroll_lock (CR)scroll_unlock to see other failing adreses?
in slot 1 and 3 doing test first i see is:
00000faff30
00000faf148
00000fb1248
00000fbc7c8
00000fd32b0
00000fd9df0
...
should i write more info like witch MB and good and bad and Err-Bits and count?

---

### Post by mcduck on 2010-07-19
Since both RAM modules pass the test when inserted in slot 1, the modules aren't broken. Instead one (or two) of your motherboard's RAM slots is faulty.

First check your motherboards manual to see which slots should be used when using two RAM modules, it might well be that two modules only work in slots 1 and 2, for example. If they should work with the combinations you already tried, then both RAM slots are probably broken.

Anyway, there's no easy fix for broken memory slots on the motherboard, trying to repair it would most likely cost more than buying a new one..

---

### Post by LowSky on 2010-07-19
Its sounds likes you have a bad motherborard.
Second thought:
Motherboards have capacities on how much RAM they can use. Since you mention SDRAM, I figure the system is kinda old, say 8+ years. It may not be able to use more than 512MB of RAM at a time.

---

### Post by pricetech on 2010-07-19
Could be compatibility between sticks also.  Are they identical ??

---

### Post by egalvan on 2010-07-19
> **Kangarooo said:**
> 

tested each seperatly in slot 1 went to 100% pass for both

tested in slot 1 and 2   failed
tested in slot 1 and 3   failed




now you should complete the test and try

TEST SINGLE
test each stick in all three slots SEPARATELY

TEST PAIRS
slot 2 and 3  TOGETHER

also, just to eliminate possible bad combos,,,
try each pair both as AB, and then BA


> is it possible to lock bad sectors?


back when RAM was far more costly than now, there existed a set of tools to locate and lock-out bad RAM locations.

It still exists, but is not much used these days of cheap RAM.

---

### Post by lkraemer on 2010-07-19
Look for the manufacture of the Motherboard and the Model number.
Download the manual.  It should have a chart specifying the exact
placement of the memory cards and how much it will accept.

Then test your memory.  If the cards aren't exactly the same
specifications, or if they are different manufactures you might
try to locate two that are identical.

lk

---

### Post by sandyd on 2010-07-19
Ive had this problem for some time as well. After yanking out, and sticking the RAM back in a gazilllion times, it mysteriously worked....

---

### Post by pricetech on 2010-07-20
Another thought; check the specs on the mobo for RAM speed supported.  I learned this one by experience with some Dell boxen that would work most of the time with a less than optimum speed RAM, but occasionally throw a memory error because of the slower speed.

---

### Post by Kangarooo on 2010-07-25
I made bios update. (after tryng grub ubuntu bios update thread didnt help did it on cd doing the same but only in windows couse also info in that thread a little old)
btw my bios after flashing i thought is dead but i found i need to clean DMOS either by changing jumper J1 for 3 sec or removing battery.

Testing BAD 512mb ram
so now im again testing and now.. actually it looks like one ram is bad.. but both are identicall and bought them together to make this old pc faster..
But when i posted this both rams one by one tested worked. now 1 is working and 1 is failing..
Screenshots of that one ram witch fails
screenshots from slot 1-3 and repeating 1 and 2 slot.

[[img]http://www.zimagez.com/avatar/2010-07-25-165614.jpg[/img]](http://www.zimagez.com/zimage/2010-07-25-165614.php)[[img]http://www.zimagez.com/avatar/2010-07-25-171700.jpg[/img]](http://www.zimagez.com/zimage/2010-07-25-171700.php)[[img]http://www.zimagez.com/avatar/2010-07-25-172812.jpg[/img]](http://www.zimagez.com/zimage/2010-07-25-172812.php)[[img]http://www.zimagez.com/avatar/2010-07-25-182436.jpg[/img]](http://www.zimagez.com/zimage/2010-07-25-182436.php)[[img]http://www.zimagez.com/avatar/2010-07-25-183947.jpg[/img]](http://www.zimagez.com/zimage/2010-07-25-183947.php)

Update1:
Now with cloth i cleaned a bit ram metal pieces and now failing is only in 2 places.. in slot 2. before (see screenshots) the same fails in all slots.
[[img]http://en.zimagez.com/avatar/2010-07-25-203056.jpg[/img]](http://en.zimagez.com/zimage/2010-07-25-203056.php)

Update2:
Cleaned again and put in slot 3 and no failing.. That means i can also clean ram and it will work..?

Update3:
Since in Update 2 i got no errors im tryng both 512mb rams but now got a lot almoust 1/2 million errors [[img]http://en.zimagez.com/avatar/2010-07-25-231203.jpg[/img]](http://en.zimagez.com/zimage/2010-07-25-231203.php)
but then in slot3 only 2 bad places in bad 512 ram[[img]http://en.zimagez.com/avatar/2010-07-26-011207.jpg[/img]](http://en.zimagez.com/zimage/2010-07-26-011207.php) as previously was only 2 errors in slot2

---

### Post by Kangarooo on 2010-07-29
Whats been tested (sdrams)
2 old 128mb rams
1st: passes in slot 1 and 2
2nd: passes in slot 1 (insteresting that in slot 2 only 2 errors. als oas for 2nd 512mb in slot 2) and slot3 85 errors (none other showed so much errors)

512mb rams:
1st: passes all 3 slots
2nd: in slot 1 errors allway in slot 2 2erros or passes sometimes and slot 3 passes sometimes doesnt with 5-7erros

so i leaved 1 128mb it in slot 1 and put passed 512 mb in slot 2 and the run the test and test failes
then put other 128mb in slot 1 and leaved 512mb in slot 2 and also test failes

putting 2nd 128mb in slot1 and 1st 128mb in slot 2 fails

putting 1st 128mb in slot1 and 1st 512mb in slot 2 fails
putting 1st 128mb in slot1 and 1st 512mb in slot 3 fails
putting 1st 128mb in slot2 and 1st 512mb in slot 3 ... coming later

putting 2nd 128mb in slot 1 and 1st 512mb in slot 2
putting 2nd 128mb in slot 1 and 1st 512mb in slot 2


BTW all erors only in test5

---

### Post by Paqman on 2010-07-29
> **carlee said:**
> Ive had this problem for some time as well. After yanking out, and sticking the RAM back in a gazilllion times, it mysteriously worked....

You probably polished up a slightly corroded pin.

---

