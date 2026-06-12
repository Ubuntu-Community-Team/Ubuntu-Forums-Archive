---
title: "Wine - Running EXE File"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by chome4 on 2010-11-30
I've got a folder containing an executable file. I've set it up in Wine under Applications but cannot see the chosen .exe file. How can I run an exe without having to start VirtualBox?

The .exe file lives in a folder in the 'p' directory.

---

### Post by rizman on 2010-11-30
I'm very new to Ubuntu and Wine so this might not be what you're looking for but I can start an exe (namely WoW.exe) by either opening a terminal and doing
```
wine /media/Data/Games/WoW/Wow.exe
```
or browsing to the exe using the 'Windows Explorer' like thingie (Nautilus they call it I think?), right-clicking the exe and selecting 'Run using Wine' (or something similar. I'm at work right now so I'm not sure what they call it.

---

### Post by chome4 on 2010-11-30
Neither worked, I'm afraid.

---

### Post by c00lwaterz on 2010-11-30
it's really hard to work with wine in my "personal experience". I try steam and counter strike source. the only thing work is steam lols. counter strike source don;t load. I also try some other games and exe but did not work. maybe it is case to case basis. better find linux native application or games. as for me, I play in linux when it is native linux. I play other games in windows if it is not native in linux. but most and many other stuff such as web surf, email chat, and etc.., i do it in ubuntu. I like ubuntu. that;s all hehe

---

### Post by Thras0 on 2010-11-30
wine has an online database with supported applications --> [http://appdb.winehq.org/]("http://appdb.winehq.org/"). 

you may wanna check that out before wasting time with some application that might not even work.

personally i had allot of problems running win games on linux, but then again i don't play that much and didn't invest allot of time in searching a solution (gaming its not a must for me). but if you do manage to get them working then thats a plus IMO.

---

### Post by ronnielsen1 on 2010-11-30
What program (& version number) are you trying to run? That always helps

---

### Post by ronnielsen1 on 2010-11-30
> How can I run an exe without having to start VirtualBox?

You do realize that Virtualbox and wine are 2 entirely different animals. Virtualbox will actually run a windows (or other) OS while wine can run certain windows programs

> you may wanna check that out before wasting time with some application that might not even work.

Just because the program is not in winehq database does not mean it won't work.

---

### Post by Goldfissh on 2010-11-30
> **c00lwaterz said:**
> it's really hard to work with wine in my "personal experience". I try steam and counter strike source. the only thing work is steam lols. counter strike source don;t load. I also try some other games and exe but did not work. maybe it is case to case basis. better find linux native application or games. as for me, I play in linux when it is native linux. I play other games in windows if it is not native in linux. but most and many other stuff such as web surf, email chat, and etc.., i do it in ubuntu. I like ubuntu. that;s all hehe

You can't run a lot of games using Wine as they all use DirectX to run - something which can't be used on Linux (to my knowledge).

---

### Post by mikechant on 2010-11-30
When you run it from the terminal as per post #2 above, you say it doesn't work, but do you get any error messages?

---

