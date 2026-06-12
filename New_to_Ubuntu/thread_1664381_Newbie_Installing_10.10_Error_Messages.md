---
title: "Newbie Installing 10.10 Error Messages"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Scorpius1Man on 2011-01-10
I am a Newbie to Linux and Ubuntu 10.10 who is installing after changing  my motherboard on PC and not having my boot discs be allowed to load  because my new board does not carry Compaq's digital tattoo in the BIOS.  A friend supplied me with a copy of XP to attempt a reload and it gave  me error after error while loading drivers etc and I just got sick of  it. Then I read in another forum that I did have an option in that of  UBUNTU, so here I am. Here is where the problem begins.

**PROBLEM**:  I burned a copy of Ubuntu 10.10 and attempted to open WUBI from D:\  while the PC is logged in XP, and it would not open it stating:
"D:\wubi.exe is not a valid win32 application"

What am I doing wrong and where do I go from here?

I  have tried to run the CD from the boot menu, and it goes to Windows to  run from there. New and frustrated. PLZ help. I know once I get past  initial setup things will come together but for now plz help

---

### Post by Eternal_Light on 2011-01-11
Well my guess is you downloaded the Ubuntu x64 edition while your WinXP is a 32bit edition. Try downloading the 32bit version of ubuntu and it might just work :)

---

### Post by cogier on 2011-01-11
To get the CD to boot you need to change the boot order. See the Ubuntu help file here [https://help.ubuntu.com/community/BootFromCD]("https://help.ubuntu.com/community/BootFromCD")

---

### Post by Hippytaff on 2011-01-11
If you want a Wubi install it's probably easier to download Wubi.exe from windows if you can. Be aware that when you do updates with a Wubi install there can be issues, so avoid any updates with grub in the title.
 
Otherwise it might be better to dual boot which you can do from the live cd. Plenty of documentation for that, but if you need help post back.

---

### Post by Scorpius1Man on 2011-01-12
I burned the CD again at a slower speed and now the computer recognizes the disc, however, I am confronted with new issues.Now when I get to the first screen to select a language and I elect to install UBUNTU it starts to install and the screen goes blank. The computer is still on, the dvd drive is still revolving, but nothing on the screen. 

What am I doing wrong?
'

---

### Post by dFlyer on 2011-01-12
From what I get from your first post, you are having trouble with xp and want to run ubuntu? If that is the case why are use installing wubi.exe. Would it be better to use the live cd and wipe out xp completely? Before doing this I would try to run the live CD to make sure everything does work with your computer.

---

### Post by Scorpius1Man on 2011-01-13
> **dFlyer said:**
> From what I get from your first post, you are having trouble with xp and want to run ubuntu? If that is the case why are use installing wubi.exe. Would it be better to use the live cd and wipe out xp completely? Before doing this I would try to run the live CD to make sure everything does work with your computer.



That sounds cool. Can you shed more light on how to do this? Where can I get a "live cd"? Is it available for download. I sit different from 10.10 that I downloaded? I am trying to get on this ASAP as I have been without my PC now for 3 weeks.

---

### Post by Quackers on 2011-01-13
What graphics card is your pc using?

---

### Post by Scorpius1Man on 2011-01-13
Nvidia

---

### Post by Eternal_Light on 2011-01-14
From what I gathered you are trying to run an 64bit version of ubuntu on a 32bit enabled system. _I don't mean a slower burning speed but a different version of ubuntu to download_. If you go to Ubuntu's homepage you will see that you have the option to select if you want 32bit or 64bit. You should download the 32bit and try again the installation steps you tried the first time. If all is done correctly WUBI will be recognized and launched normally by your xp.

---

