---
title: "Question About Terminal Login Prompt"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-11-06
While I was having a problem (since solved) with Firefox loading pages even though I definitely was connected to the internet, I 'forced' the computer to offer the choice of the repair mode (I've done this before with other versions of Ubuntu).

When it is finished repairing whatever needs to be repair and I select the option to log in normally, it presents me with a black screen (with lots of writing) and, at the bottom, asks me to login.

I login, then enter my password, and then it shows the Terminal command
< username:~$ >

I do not know what to enter here; can someone tell me please? Also please tell me the command to get out of the Terminal (normally I just shut it down with the cursor).

Thanks for any help.

---

### Post by SunnyRabbiera on 2009-11-06
Yipes, you didnt remove any packages right?
As for shutdown in the terminal, the command is sudo reboot

---

### Post by JugglinPhil on 2009-11-06
You can start your X-server (your graphical interface) using the command 'startx'.

---

### Post by lhb1142 on 2009-11-06
Thanks to both of you. Those commands are just what I needed. ):P

---

### Post by corncob on 2009-11-06
> **JugglinPhil said:**
> You can start your X-server (your graphical interface) using the command 'startx'.

"startx was the first command I learned in Linux but it never worked for me.  Is this a program or script that needs to be installed?

---

### Post by corncob on 2009-11-06
> **lhb1142 said:**
> 

I login, then enter my password, and then it shows the Terminal command
< username:~$ >

I do not know what to enter here; can someone tell me please? Also please tell me the command to get out of the Terminal (normally I just shut it down with the cursor).

Thanks for any help.

I played with this a little bit since my last post a couple minutes ago and [ctrl][alt][F7] worked (did what startx was supposed to do).

---

### Post by JugglinPhil on 2009-11-06
> **corncob said:**
> I played with this a little bit since my last post a couple minutes ago and [ctrl][alt][F7] worked (did what startx was supposed to do).
Yes [ctrl]+[alt]+[1-7] changes the terminal you are on at the moment, whereas terminal 7 is the graphical one. This means your X server was already running, you were only on a different terminal, thus it didn't let you run X again.

---

### Post by JugglinPhil on 2009-11-06
> **lhb1142 said:**
> Thanks to both of you. Those commands are just what I needed. ):P
Glad to help. :)

---

