---
title: "Just downloaded wine need help"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by dan9686 on 2010-11-18
I'm new to Linux. I just downloaded WINE and am curious if there are any instructions for activating it or if it will run on its own.

---

### Post by Hippytaff on 2010-11-18
> **dan9686 said:**
> I'm new to Linux. I just downloaded WINE and am curious if there are any instructions for activating it or if it will run on its own.

Once it's installed go to Applications -> Wine

Take it from there :-)

if it's not in the applications menu its not installed :-)

---

### Post by eriktheblu on 2010-11-18
You'll want to run the configuration program first (applications>>wine, or winecfg in the terminal).

Ubuntu may not automatically associate Windows executables (.exe) with Wine, so you might want to associate them at some point.

Look at the Wine AppDB for the programs you want to run to see if there are any tricks to make them run better.

---

### Post by Hippytaff on 2010-11-18
> **eriktheblu said:**
> You'll want to run the configuration program first (applications>>wine, or winecfg in the terminal).

Ubuntu may not automatically associate Windows executables (.exe) with Wine, so you might want to associate them at some point.

Look at the Wine AppDB for the programs you want to run to see if there are any tricks to make them run better.

Really? it worked for me without any configuration :-s so maybe I should butt out :-)

---

### Post by WeAreLinux on 2010-11-18
I would also suggest to read the precautions about Wine in the Security Sticky: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by realzippy on 2010-11-18
...rightclick a windows .exe file,select "Open with",choose "wine",mark "remember".

If you are looking for windows games in wine,have a look at [playonlinux]("http://www.playonlinux.com/en/"),which often provides the correct -and sometimes special- wine setup for each game .

---

### Post by Hippytaff on 2010-11-18
basically
>  [COLOR=darkred][B]DO NOT RUN WINE AS ROOT

[/B][/COLOR]if you are running wine as a user, a Windows virus will be confined to your home directory.
and you'll be fine :-)

---

