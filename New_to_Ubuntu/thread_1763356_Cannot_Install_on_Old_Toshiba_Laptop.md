---
title: "Cannot Install on Old Toshiba Laptop"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Coachdbeard on 2011-05-20
I have inherited from a great friend a Toshiba Satellite 1505-s102 (I think, working off memory here).  It has a Celeron 1ghz, 20 GB HD, and 384 MB RAM (I think, again) and was running Win XP fine.  The problem is I hate XP and wanted a 'buntu distro on there.  Lu seemed like a good fit, but I can't get it installed.  The laptop overheats to a shutdown point (which seems common for this age Toshi) before 11.04 install is complete.  Made some progress with Xu 11.04 alternate install (I had on hand) but ran into some kind of error in the install.  Tried Lu 11.04 mini install, but wouldn't boot up when finished.  Burned a Lu 10.10 alternate (finally found) last night, but it was already running hot from trying Lu 11.04 again and failing, then getting Puppy 5 going and exploring it. and I was tired so I went to bed.  I like what I see in Puppy, but I'd rather have something I'm more familiar with (I have used Ubuntu, Xubuntu, and Lubuntu and worked out numerous problems with them and my old hardware).
 
Anyway, I think I'm just missing something small.  Any suggestions?  Am I using the right distro?  Should I just run with Puppy and not worry about Lu?  Any success stories with this laptop?  Any input would be appreciated.

---

### Post by dniMretsaM on 2011-05-20
Lubuntu should work. If it over heating, find a way to cool it off. Maybe a fan blowing on it or stick it in the fridge. OK, maybe not the fridge, but I'm sure their is a way to keep it cool enough to complete the install.

---

### Post by HermanAB on 2011-05-20
Howdy,

Toshiba and Sony laptops are best avoided with Linux.  You should put WinXP back on, sell it on Ebay and buy another laptop.  Pretty much anything else will be better.

The cooling fan is a killer problem on a Toshiba.  If you don't fix it you can burn out the central processor or the video processor.  Either one will mean that the machine can be thrown away.  I have one lying in my junk box...

However, if you really want to persevere, then you need to get a 3 inch cooling fan and stick it below the air intake, or you need to open the laptop and rewire the fan so that it always runs - which is the best solution.  Disassembling a Toshiba is very risky - it is easy to break the flex connectors and if that happens, you can throw the machine away, since there is no easy way to fix it.  The best solution is to cut a large square of plastic around the fan open with a Dremel, fix it and then glue the plastic back in again, without opening the case.

Apart from the cooling fan issue, the laptop doesn't have enough RAM.  You need to add more if you want it to be able to run regular Ubuntu.

---

### Post by fabricator4 on 2011-05-20
I also think you are on the right track with Lubuntu.  One thing that may speed up the installation is if you make the partitions before you start, and in particular the swap partition of at least 500 MB.  Do this with Gparted. The Gparted LiveCD is a quick download of about 125MB and it boots quickly too. An interesting distribution in its own right.  If you can't download this then use Gparted off one of the LiveCD's.

The Lubuntu installer will use the swap partition you made as extra RAM, and given the small amount of RAM in the machine it may make a big difference to the intall.

Another thing you should investigate is the ventillation on the machine.  If it's an older well used machine then the fans and heatsinks could just be blocked up with dust and fluff.  This might be restricting the airflow enough to cause you major problems.

Chris

---

### Post by Hralgmir on 2011-05-20
I'm running Ubuntu 10.10 on a Dell Latitude CPx H500GT,PIII 500MHz, 30GB HDD and 512MB RAM right now. I had Lubuntu 10.10 on it for a bit too. The lack of system tools and limited Lubuntu specific help online made it difficult to use as a Linux newcomer though, hence the change. Runs fine, but try loading the OS without an internet connection, then shutting down to cool off for a few hours. Then load the important updates over the internet using update manager,  allow to cool off, then load the recommended updates. That's what I did anyway, loading from a CD. Also check the POST setting in the BIOS is on thorough not minimal, if you have this option. Ubuntu would probably work on your setup, although a bit more RAM would give you more headroom. Lubuntu 10.10 jammed with me during the restart after loading, pressing CTRL ALT F1, F2, F3, etc got it going somewhere down the line of F numbers:D. Also check your RAM in the BIOS after installing from the CD, as I had to remove the HDD, remove a RAM chip, boot to BIOS setup, shutdown, replace the chip, BIOS, shutdown, replace HDD and boot up to get the full 512MB after CD installation, with both Ubuntu and Lubuntu. It 'lost' some RAM at the restart, and this caused it to be recognised again. May just be my particular system of course.

---

### Post by jerrrys on 2011-05-20
some older PC's will not play nice with 'acpi' and you may want to turn it off at the beginning of the live install (i think its f6).  this should make your fan run all the time, but will cause your battery to drain at a high rate.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+off+acpi&as_qdr=all&sa=Google+Search&lang=en#881](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+off+acpi&as_qdr=all&sa=Google+Search&lang=en#881)

---

### Post by markyork on 2011-05-20
> **dniMretsaM said:**
> or stick it in the fridge.

Cool idea, man!:lolflag:

---

### Post by dniMretsaM on 2011-05-20
> **markyork said:**
> Cool idea, man!:lolflag:
Nice pun! But seriously, that could possibly work if you kept it at the least amount of cool. I wouldn't recommend it though unless you're desperate. Another weird thing is that putting a failed HD in the freezer for 12 hours makes it work again for a few minutes. Go figure.

---

### Post by markyork on 2011-05-20
That may be so, but when you take the drive out of the fridge/freezer you'll quite possibly get condensation on it that can definitely - and very permanently - destroy your drive!

An extreme solution with extreme consequences!

---

### Post by Coachdbeard on 2011-05-20
Thanks for all the assistance!  I'll give some of these suggestions a go this evening and I'll let you know how it goes.
 
I do know that I don't want to give up and I'm pretty locked on to Lubuntu (I like Xubuntu better, but as I understand Lu is "lighter" and that could help).  Any more thoughts?

---

### Post by josephmills on 2011-05-20
you could always take it apart and clean the crap out of it I have had almost the sme issue what I did was open the laptop up. Then cleaned it then mad sure that the fan was not being blocked by anything dust hair ect and cleaned with an old toothbrush then gave my room mate the tooth brush to clean his teeth just kindding about the roomate stuff:) next after you clean the whole thing out I would say to get some new heat grease take off the heat sink for the cpu then get all of the old heat grease off of it then use a TINY bit of rubbing alcohol to get the fingerprints off of the top of the cpu (the part that touches the heat sink) then apply the new heat grease then put it all back together and there you go no more over heating I would also look into getting more clean air into the fan if there is anything that is blocking your fan then it is going to overheat, remeber that heat is a computer worst nightmare. Hope that this helps and hey might be FUN :popcorn:

---

### Post by Coachdbeard on 2011-05-23
Thanks, All!  Lubuntu 10.10 is up and running with all updates in and everything working fine.....almost.  I ended up leaving the panel off between the keyboard and monitor which exposed part of the cpu fan allowing a lot more air in (after everything was clean).  I also placed an ice pack under the computer in the cpu vacinity and balanced another on top where the fan would draw cool air.  I used the Lubuntu 10.10 alternate install and kept fresh ice packs on it and watched the condensation level closely.  Got it all loaded, got wireless card set up, got updates done.  I may have the guts to try the upgrade to 11.04........eventually.:P
 
The only issue I'm having now is that the monitor is not detected correctly....I think.  The desktop doesn't spread across the whole screen.  There is about a 1" to 1.5" margin of black screen all the way around.  Not ideal, but totally usable.  I'll post this issue as a new thread and see what happens and I'll mark this thread as solved if I can figure out how.
 
Again, thanks for the help!

---

### Post by Coachdbeard on 2011-06-06
Since marking the thread solved, I have cleaned the old grease off and put new on.  That seemed to totally solve the overheating issue.

Thanks again!

---

