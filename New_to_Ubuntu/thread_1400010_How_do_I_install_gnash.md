---
title: "How do I install gnash?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Caramin on 2010-02-06
Dear friends!  Since 2 hours I am Ubuntu user. It's amazing! Can anybody tell me how I can install gnash? On the hompage there is something about cvs which I never heard of...  I dont have the slightest idea what file I have to use from downloaded Version 0.8.5. Probably there is no .exe like in windows  THX  edit: I would like to watch youtube etc..

---

### Post by mikewhatever on 2010-02-06
Applications->Software Center, search for gnash, click install. You almost never have to download executables manually form websites in Ubuntu.

---

### Post by tom.swartz07 on 2010-02-06
> **Caramin said:**
> Dear friends!  Since 2 hours I am Ubuntu user. It's amazing! Can anybody tell me how I can install gnash? On the hompage there is something about cvs which I never heard of...  I dont have the slightest idea what file I have to use from downloaded Version 0.8.5. Probably there is no .exe like in windows  THX  edit: I would like to watch youtube etc..

If youre looking to watch youtube, I would suggest that you just use Flash. In the software center, add Ubuntu-restricted extras and flashplugin-installer.

---

### Post by 311005901 on 2010-02-06
Hi Caramin! Welcome to the Ubuntu community!

Gnash, in my opinion, sucks. ](*,) Don't even bother trying to work with it. It's not up to par with the regular Flash plugin.

First, I need to know if your computer has a 32 bit processor or a 64 bit processor.
Do you know?
If you don't, open up Applications>Accessories>Terminal and type in
```
uname -m
```

Then, post back with what you've got. :)

---

### Post by lovinglinux on 2010-02-06
+1 for Adobe plugin.

See Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If you are using 64bit, then follow [this](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1).

---

### Post by Caramin on 2010-02-06
thank you a all lot!!! with you help i will learn quickly- i thought gnash wuold be fine cause it is open - flash isn't.   @3300.. uh ..5109 (sorry, if i post your name correctly i will have to go back and type all this again )  :the info i get is from terminal i686.

---

### Post by lovinglinux on 2010-02-06
> **Caramin said:**
> thank you a all lot!!! with you help i will learn quickly- i thought gnash wuold be fine cause it is open - flash isn't.   @3300.. uh ..5109 (sorry, if i post your name correctly i will have to go back and type all this again )  :the info i get is from terminal i686.

So it's 32bit. Follow my tutorial and you will be fine.

Gnash is open source, but unfortunately, not quite there yet.

---

### Post by Caramin on 2010-02-06
ok! thx! i will do so :)

---

### Post by 311005901 on 2010-02-06
Yay! :D
I'm glad you fixed your problem!

Could you please mark the thread as 'SOLVED' under the "Thread Options" link? This really helps out the forums staff. 
:popcorn:

---

### Post by Caramin on 2010-02-06
sorry to bother again. i pasted the code. unfortunately i get info that the adobe packet couldn't be found. (I just had to paste the 4 or 5 lines, right?)

---

### Post by lovinglinux on 2010-02-06
> **Caramin said:**
> sorry to bother again. i pasted the code. unfortunately i get info that the adobe packet couldn't be found. (I just had to paste the 4 or 5 lines, right?)

No problem. I just put all those lines to make sure, because some people install multiple versions at the same time.

Run each line, one by one to make sure. It will complain about some stuff not being installed and at the end will install flashplugin-nonfree.

---

### Post by Caramin on 2010-02-06
That didnt work, I am afraid. Could the problem be that my main language is german? Or should I restart the computer (still on the first time?)

---

### Post by lovinglinux on 2010-02-06
> **Caramin said:**
> That didnt work, I am afraid. Could the problem be that my main language is german? Or should I restart the computer (still on the first time?)

What didn't work? Did it installed flashplugin-nonfree or gave an error?

You don't need to restart the machine, that's a Windows thing, but you need to restart Firefox, so it can detect the plugin.

What version of Ubuntu are you using?

---

### Post by Caramin on 2010-02-06
I get the message that flashplugin-nonfree could not be found (in the terminal) the version is 9.10  Karmic Koala.

---

### Post by lovinglinux on 2010-02-06
> **Caramin said:**
> I get the message that flashplugin-nonfree could not be found (in the terminal) the version is 9.10  Karmic Koala.

The package flashplugin-nonfree is a dummy, but it should be there. Anyway, try this:

```
sudo apt-get install flashplugin-installer
```

---

### Post by Caramin on 2010-02-06
That is the reply I get:  Paketlisten werden gelesen... Fertig Abhängigkeitsbaum wird aufgebaut        Lese Status-Informationen ein... Fertig E: Konnte Paket flashplugin-installer nicht finden  I try to translate it :)  packetlist are beeing read...done dependencetree is beeing build reading status-information on... done E: couldn´t find flash (..)inst. packet

---

### Post by Caramin on 2010-02-06
is there any basic updating necessary - installed it from dvd (ubuntu)

---

### Post by lovinglinux on 2010-02-06
> **Caramin said:**
> That is the reply I get:  Paketlisten werden gelesen... Fertig Abhängigkeitsbaum wird aufgebaut        Lese Status-Informationen ein... Fertig E: Konnte Paket flashplugin-installer nicht finden  I try to translate it :)  packetlist are beeing read...done dependencetree is beeing build reading status-information on... done E: couldn´t find flash (..)inst. packet


Open "System >> Administration >> Sofware Sources" and enable the multiverse repository, click Close, then Reload, then try to install flashplugin-nonfree or flashplugin-installer.

---

### Post by Caramin on 2010-02-06
IT WORKED HUUUUUUUUURRRRRAAYYYYYYYYY!!!!!!   Thank you soo much! If I could ever help you to misunderstand a computer let me know... That was really nice from you! My first Ubuntu-day seems to be just fine!! The last thing I have to find is marking this thread solved.  Thanks again!!!!!!!!

---

### Post by lovinglinux on 2010-02-06
> **Caramin said:**
> IT WORKED HUUUUUUUUURRRRRAAYYYYYYYYY!!!!!!   Thank you soo much! If I could ever help you to misunderstand a computer let me know... That was really nice from you! My first Ubuntu-day seems to be just fine!! The last thing I have to find is marking this thread solved.  Thanks again!!!!!!!!

You are welcome. I should have figured out the problem earlier, but enabling the multiverse and other repositories is one the first things I do when I install a new Ubuntu version, so I never had this problem. I guess I should add a note to my tutorial.

BTW, welcome to the community. You are gonna love it.

---

### Post by Caramin on 2010-02-06
I think I do so even after some hours- I am still surprised. If one was an absolute beginner (with computers) at all this system should for her/him be much easier than windows or mac.  Thanks again!

---

