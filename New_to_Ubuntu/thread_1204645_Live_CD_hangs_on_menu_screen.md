---
title: "Live CD hangs on menu screen"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Cringer on 2009-07-05
Hello all, first let me say this is a great board. I have been using Ubuntu 9.04 for most of two months now, through a Wubi install. I just now registered today though because every time I have had a question or problem, searching here or all over the internet has given me the answers. Until now of course. As I said, I have 9.04 installed through Wubi. I have decided to do a full install because 30 GB through Wubi won't cut it, plus I want to couple little bonuses of doing a full install. I may or may not try to migrate my Wubi install, but that has actually been forgotten about now and doesn't matter to me because of my problem.

I downloaded the .iso, burned it to CD and then tried to boot. It starts to boot, I get to the menu, and then when I pick an option it hangs sitting on that menu screen doing nothing, not letting me do anything. I have tried the CD check option and the run from Live CD option, same result for both. I have done the searches, most of today in fact spent on this. The answers I have found have not worked;

F6 and delete quite splash
replace quiet splash with noapic nolapic
replace with acpi=off
replace with irqpoll 
replace with lapic pci=routeirq
and checking the other options when you hit F6.

Nothing has helped. Some have had slightly different reactions, like the sound of my cd/dvd drive reading more then on another option. Still, it will fade off and just hang. I have checked my CD, the .iso seems to have burned fine, files and folders are there. Here are my specs;

HP Pavilion dv2000 laptop
AMD Turion 64 x2
nVidia graphics - GeForce7150m / nForce630m 512mb - integrated of course
2 GB ram
240 GB HD with 80 GB free still

If anyone has any ideas, or suggestions I would appreciate it. I have searched numerous threads here, googled it, read the stickied newb threads and have found a couple things similar, but no answers that solved my situation. One specific question, what kind of time frame should I expect when selecting the option to run from LiveCD? I wonder if I have perhaps done it right but my impatience killed it and I didn't know. I have given it up to 10 minutes on a couple, but usually kill it after 30-60 seconds.

Thanks guys.

---

### Post by diablo75 on 2009-07-05
Well, as a backup plan, you might check into using a USB flash drive for installing instead of a CD.  There is a utility in Ubuntu that you can use to create such a disc, in the System menu.  Though if your laptop doesn't support USB booting, this won't help you.

The other suggestion is to use an Alternate CD instead of the Live CD.  It's a low-end text-based installer.

[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

Lastly, burn install CD's at a low speed (like 4x or less) and if possible, use the burning software to confirm the integrity of the burn after it's finished (some include this feature, others don't).

---

### Post by Cringer on 2009-07-05
I think I will try to boot from USB just to try it, then try the alternate. Am I correct in assuming you can use the alternate boot from USB as well?

---

### Post by Cringer on 2009-07-05
Wow, didn't think the USB boot would make any kind of difference but it did. Ubuntu booted right up from it. I wonder what was wrong with my CD? I see a couple scratched, perhaps that was it? I followed the slow burn instructions and everything else. Oh well, I am good for now it seems. Thanks, and sorry for starting a semi-useless thread like the newb I am.

---

### Post by LewRockwell on 2009-07-05
> **Cringer said:**
> Wow, didn't think the USB boot would make any kind of difference but it did. Ubuntu booted right up from it. I wonder what was wrong with my CD? I see a couple scratched, perhaps that was it? I followed the slow burn instructions and everything else. Oh well, I am good for now it seems. Thanks, and sorry for starting a semi-useless thread like the newb I am.

perhaps you might explain what you did and how you did it?

or post the links you used(if any)

also, edit the title in your first post to include "[SOLVED]" at the beginning

thanks

.

---

### Post by CaseSensative on 2009-07-05
Did you check for Flaws on the CD?

---

### Post by Cringer on 2009-07-05
> **LewRockwell said:**
> perhaps you might explain what you did and how you did it?

or post the links you used(if any)

also, edit the title in your first post to include "[SOLVED]" at the beginning

thanks

.

As far as the CD goes, I followed the links below...

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

wanted to try the Cd Integrity Check, but that got the same result as trying to boot from the CD. When it comes to the F6 key and changing the boot string, I tried a ton of different ideas, found both here and on other sites. To be honest I wrote a lot of them out by hand and didn't bother saving or remembering specific locations.

When I moved onto the USB memory stick I used the exact same .iso file I used for the CD above, I used these instructions;

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I used UNETbootin to do the work for me. Rebooted, hit F9 to select boot device, selected USB, a fairly short time later I was in Ubuntu. 

Then I closed it out and came back into Vista to start clearing things out and cleaning up before I try to partition the HD.

---

