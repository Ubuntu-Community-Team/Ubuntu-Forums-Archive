---
title: "safe shutdown ?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-03
suppose my laptop hangs up,
is there a safe way to power off than the off button on the lappy ?

---

### Post by robert shearer on 2011-04-03
Yes !.
[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

After reading the link note that sometimes the whole rseiub series has to be run twice to allow time for file system synching and try to allow a second or more between each key combo, the more locked-up the system is the more important it is to go slow.

Note that the rseiub  series will reboot.
If you just want to shutdown then use rseiuo where the o stands for off.

---

### Post by neil_1 on 2011-04-03
whats a  SysReq key ?

---

### Post by ajgreeny on 2011-04-03
> **neil_1 said:**
> whats a  SysReq key ?
Print Screen.

---

### Post by Sidewinder1 on 2011-04-03
SysRq is exactly the same key as "Print Screen".
HTH,
Side

P.S. I believe that it's REISUB although is may not make a difference

---

### Post by neil_1 on 2011-04-03
my print screen is fn+prtsc
so i have to hold down alt+fn+prtsc+r (eisub) ..?

---

### Post by Sidewinder1 on 2011-04-03
This has worked (fortunately I haven't needed to use it more than 3 times since 2007) for me: While holding down the Alt and shift (the letters need to be upper case) and print screen keys, then type in R wait 2 -3 seconds then type E wait 2-3 seconds I wait 2-3 secs S wait U wait B  Note that it's BUSIER in reverse. Hope that it works for you as it has for me.
Side

P.S. Yes, I know, that combination is a little rough on the fingers...

P.P.S. The Caps Lock may work in lieu of holding the shift key but I have never tried it.

---

### Post by ajgreeny on 2011-04-03
I am not sure that it needs to be REISUB in upper case;  I am pretty sure when I used it I did everything in lower case and it still worked.

The biggest problem I have found is that everything freezes, including the keyboard, making this an impossible option!

---

### Post by Sidewinder1 on 2011-04-03
Maybe that's the difference with using lower case instead of upper case, which has always worked fine for me with no freezing. No disrespect intended...

Side

---

### Post by Dutch70 on 2011-04-03
I have used it many, many times and I've never used upper case. 

I have discovered that with some keyboards, you have to release the alt+sysrq keys before releasing the "b". 
 
Also, changing the last letter "b" to an "O", as in (r-e-i-s-u-o) will shut down the computer, instead of rebooting it.

---

### Post by Rex Bouwense on 2011-04-03
If you can get to a terminal, I believe that you can force a shut down by typing halt or if you want to reboot by typing reboot.  I think you can get to the terminal by using Ctrl, Alt and F1 or F2.

---

### Post by Paqman on 2011-04-03
> **Rex Bouwense said:**
> If you can get to a terminal, I believe that you can force a shut down by typing halt or if you want to reboot by typing reboot.  I think you can get to the terminal by using Ctrl, Alt and F1 or F2.

Yep, Ctrl-Alt-F1 and:
```
sudo shutdown -P now
```
To shutdown, and:
```
sudo reboot
```
...to reboot.

---

### Post by Dutch70 on 2011-04-03
> **Rex Bouwense said:**
> If you can get to a terminal, I believe that you can force a shut down by typing halt or if you want to reboot by typing reboot.  I think you can get to the terminal by using Ctrl, Alt and F1 or F2.

(Cntl+Alt+F1) takes you to a tty. To get to a terminal it's (Cntl+Alt+T) and then, "sudo reboot"

---

### Post by robert shearer on 2011-04-04
> **neil_1 said:**
> whats a  SysReq key ?

Well, if you read the link then it says....
> What the heck is a SysReq key? Look for it on your PrtSc or Print Screen key. 

rseiub or reisub both work, the former is preferred.

No it does not need to be upper case.

This sequence works even when the lock-up is such that the keyboard cannot be used to reach a terminal as the  'r' puts the keyboard in raw mode.

Read the link and the replies. It starts from 2006 and almost all questions pertaining to this have been covered there.

---

### Post by neil_1 on 2011-04-05
*bump*
umm when vlc had crashed in full screen mode , i couldnt use rseiub :(
had to forcefully shutdown , anyway around that ? like an end process as windows has it ?

---

### Post by Dutch70 on 2011-04-05
> **neil_1 said:**
> *bump*
umm when vlc had crashed in full screen mode , i couldnt use rseiub :(
had to forcefully shutdown , anyway around that ? like an end process as windows has it ? 

Have you ever used it successfully? Are you sure you're using it correctly, cause that's just about as good as it gets AFAIK. It's always worked for me. As I said, with some keyboards, you have to release the alt+sysrq keys before releasing the "B". You may also have to do it twice.

---

### Post by neil_1 on 2011-04-06
> **Dutch70 said:**
> Have you ever used it successfully? Are you sure you're using it correctly, cause that's just about as good as it gets AFAIK. It's always worked for me. As I said, with some keyboards, you have to release the alt+sysrq keys before releasing the "B". You may also have to do it twice.
ive used rseiub before and it worked , but when vlc crashed in full screen mode , it didnt :(

---

### Post by Kixtosh on 2011-04-06
Well, I don't know if this will work in your particular case, but for my laptops, I always:

1) Go to the System menu in the top panel and choose Preferences,
2) From the drop down list, choose Power Management,
3) From there choose the General tab,
4) Adjust "When the power button is pressed" to "Shutdown".

Usually, if I get in trouble, even if everything seems frozen, it means that just pressing the power button for a second or so shuts everything down, since no dialogue screen is supposed to pop up (asking if I want to shut down, reboot, suspend ...). I don't remember the last time it has failed to rescue me. It's also handy for shutting down quickly during normal usage, since that one press of the button does everything, without asking for confirmation, by mouse click or keyboard. 

Obviously this seems gentler than holding the power button down for five seconds, which forces shutdown just about as surely as pulling the power cord and battery would do.

---

