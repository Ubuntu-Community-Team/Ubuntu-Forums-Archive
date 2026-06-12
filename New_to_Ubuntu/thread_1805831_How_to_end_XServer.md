---
title: "How to end XServer"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by GeneralShep on 2011-07-16
Please help! I need to install my driver!

---

### Post by _0R10N on 2011-07-16
You should execute

```
sudo stop gdm
```

from tty different than tty7

Regards!

---

### Post by nzjethro on 2011-07-16
To change tty, press Ctrl + Alt + F1, or any other F-button up to F6. These are your terminal ttys, while ttys 7 and above are graphical ttys.

---

### Post by ajgreeny on 2011-07-16
> **_0R10N said:**
> You should execute

```
sudo stop gdm
```from tty different than tty7

Regards!
I think it should be ```
sudo service gdm stop
```but if your way works, my apologies.

---

### Post by GeneralShep on 2011-07-16
Can you telll me EVERYTHING to press cause when I type it in the terminal nothing happens. When ever I press CTRL+ALT+F2 the screen goes black. I try to type but nothing even comes up.

---

### Post by ajgreeny on 2011-07-16
Ctrl+Alt+F1 to get to tty1 comand line interface.

gdm or whatever display manager you use will still be running, so use command ```
sudo service gdm stop
```

---

### Post by GeneralShep on 2011-07-16
Okay, but when I type after I press that CTRL + ALT + F1 It dosnt type Nothing happens other than a cursor blinks. Is this how it is suppose to look?

---

### Post by ajgreeny on 2011-07-17
Ctrl+Alt+F1 should get you to a command line interface showing possibly a few lines of text, but with a final two lines in the format:-
```
Ubuntu 10.04.2 LTS <hostname> tty1
<hostname> login:
```that is, in order
1.  Your distro and version number
2.  The hostname of your computer which you chose at install
3.  the tty number (F1 will give you tty1, F2 gives you tty2 etc etc)
4.  hostname again (on second line) with login prompt.

If you don't see something like that there is something wrong with your setup, I think.  If you do see that on screen, just type in your username, hit enter, type in your password, which will not show on screen in any way; nada, nothing; and hit enter again.  You will now be logged in to the command line, and able to install your graphic driver

---

### Post by 2901119 on 2011-07-19
Im having this exact issue in 11.04. I have considerable linux experience. I'm trying to install the proprietary graphics driver that I downloaded from its respective website.    #### things I've tried ####   ```
update-rc.d -f gdm remove  pkill X  CTRL+ALT+BACK /etc/init.d/gdm sudo service gdm stop kill gdm 
```  /* all of the above resulted in a unresponsive frozen black screen */   I also tried using a virtual terminal to install the graphics driver with the same result as the other forum member.  Completely black screen with no prompt, then when I try to go back to tty 7 the display is all fudged(likely related to the refresh rate and lack of drivers)   So I have two questions...    1.) What is the correct way to setup a tty login or even just kill gdm on 11.04 natty?    2.) Can you even use virtual terminals on natty?

---

