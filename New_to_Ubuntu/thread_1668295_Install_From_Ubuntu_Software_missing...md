---
title: "Install From Ubuntu Software missing..?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-01-16
Good morning, all! 
I've been trying to check out VegaStrike since I ran across some screenshots of it and was excited that it was available from Ubuntu Software center. The problem is that the game isn't in my games list and I cannot find where the data was saved to try to play it. Any ideas are greatly appreciated!! 
 
-Nick

---

### Post by diablo75 on 2011-01-16
On occasion, I'll catch Ubuntu forget to enable the shortcut for software I've just installed.  You might check your System>Preferences>Main Menu settings to see if there is a shortcut for your game there, just unchecked and thus hidden.  Adding a checkmark will bring it back.

If that's not the case you may have to create your own.

---

### Post by amsterdamharu on 2011-01-16
Could you press alt + F2 type vegastrike and press run.

If that didn't work then try to press alt + F2 then copy and paste the following:[FONT=monospace]
[/FONT]```
gedit /usr/share/games/vegastrike/README

```
Click run and read.

I don't have the package at the moment so not sure what is the executable to start the game.

---

### Post by Nickjpost on 2011-01-16
Thanks for the replies, but neither worked. The README file in gedit just gives system requirements and there was no option when I went to System>Preferences>Main Menu. the executable should be "./vegastrike" but that didn't work either. When I tried to run from alt+F2, a screen flashed for a moment, then stopped. I tried to see what happened in the terminal, but it flashed by too fast. I think that there is some compiling to do, which I tried before from [http://vegastrike.sourceforge.net/wiki/HowTo:Checkout_SVN_(Ubuntu-Linux](http://vegastrike.sourceforge.net/wiki/HowTo:Checkout_SVN_(Ubuntu-Linux)) but the method there didn't work either. I've concluded that it is my processor since it didn't meet the requirements anyways. I'll try again when I can afford a better laptop (I have a Toshiba Satelite L25-S1217 Celeron processor, 1G RAM....ancient, I know....try to stiffle your laughing ;^] )

---

