---
title: "&quot;Firefox is already running...&quot;"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by JoeYsUn on 2011-06-07
Whenever i open firefox i get that message "firefox is already running......" but then another firefox window opens and i can just use it normally, but that error-message-window always appears in the beginning  and it seems useless...
how can i get rid of it?

---

### Post by hakermania on 2011-06-07
Hello, every time you get this message press Alt+F2, type in
```
killall firefox-bin
```and start firefox again

this will kill the already open firefox process.
If there's no such process (firefox-bin) while you open firefox and you get the message again, then it is probably a firefox bug.


But, for example, do you take this error message if you restart your PC and open firefox (once) ?

---

### Post by unapendeza on 2011-06-07
> **JoeYsUn said:**
> Whenever i open firefox i get that message "firefox is already running......" but then another firefox window opens and i can just use it normally, but that error-message-window always appears in the beginning  and it seems useless...
how can i get rid of it?

Open the terminal (Applications > Accessories > Terminal) and enter
```
killall firefox-bin
```Then restart firefox, if that doesn't work try rebooting.

---

### Post by JohnBoy99 on 2011-06-07
You are probably double-clicking the little icon on the top panel. Just single click it. 

regards,
JB

---

### Post by hakermania on 2011-06-07
> **unapendeza said:**
> Open the terminal (Applications > Accessories > Terminal) and enter
```
killall firefox-bin
```Then restart firefox, if that doesn't work try rebooting.

Hello unapendeza, as terminal use must be avoided if possible for new users, I'd say that Alt+F2 (supported by unity bar as well) is preferable.

---

### Post by jtarin on 2011-06-07
> **hakermania said:**
> Hello unapendeza, as terminal use must be avoided if possible for new users, I'd say that Alt+F2 (supported by unity bar as well) is preferable.
Why should the terminal be avoided? Too traumatic? Lack of typing skills?:P
In fact launch Firefox from the terminal and see if you detect any error messages. This way there is no question of double-click.The command would be ```
firefox
```

---

### Post by unapendeza on 2011-06-07
> **hakermania said:**
> Hello unapendeza, as terminal use must be avoided if possible for new users, I'd say that Alt+F2 (supported by unity bar as well) is preferable.
Why? As a new user I think that other new users should be introduced to the terminal right away, besides it's not a complex command.

---

### Post by hakermania on 2011-06-07
OFFTOPIC: Well i think that completely new users have to get used to the sytem first before going through terminology, im not  the only one with this opinion: [http://ubuntuforums.org/showthread.php?t=1775713](http://ubuntuforums.org/showthread.php?t=1775713) :)

---

### Post by jtarin on 2011-06-07
> **hakermania said:**
> OFFTOPIC: Well i think that completely new users have to get used to the sytem first before going through terminology, im not  the only one with this opinion: [http://ubuntuforums.org/showthread.php?t=1775713](http://ubuntuforums.org/showthread.php?t=1775713) :)This perception is understandable but to overcome the reticence to use the terminal allows you to learn your system faster, in depth and removes you from the Windows mindset of only GUI control. The terminal has its place among all users.

---

### Post by I2k4 on 2011-06-07
The original poster didn't say if he's using FF 4 or FF 3, the earlier FF had a problem with continuing to run processes and I haven't had much (but a little) of the same problem in FF 4.  

As to how to kill processes, the simpler the better.  Many committed Ubuntu users don't realize that the future of operating systems is invisibility (that's why Chrome is hiding Linux under its browser in the "revolutionary" Chrome OS.)  I don't love Google, but I agree that operating systems are inherently boring functional platforms for useful or enjoyable software, and should just bloody work with as little fuss as possible for users who should and will focus on work or fun with the software, not with the OS.

---

### Post by jtarin on 2011-06-07
> **I2k4 said:**
> 
As to how to kill processes, the simpler the better.
People have the same problem no matter the platform.

> **I2k4 said:**
> Many committed Ubuntu users don't realize that the future of operating systems is invisibility (that's why Chrome is hiding Linux under its browser in the "revolutionary" Chrome OS.)No...the commited users of Ubuntu don't have this problem, but you might receive a different reply from commited Linux users.

 > **I2k4 said:**
>  I don't love Google, but I agree that operating systems are inherently boring functional platforms for useful or enjoyable software, and should just bloody work with as little fuss as possible for users who should and will focus on work or fun with the software, not with the OS.
Perfect world.....in which you can pay according to the level of functionality you would prefer..

---

### Post by roadrash on 2013-04-12
After installing Ubuntu I install a app called "Task manager"  (install with software centre)  if you get the firefox already running mesage just run task manger then find firefox in the list of running tasks and right click it and select Kill task.  I think its a problem with unity because it sometimes happens to me usually running firefox for the first time after boot up.

---

### Post by lisati on 2013-04-12
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

