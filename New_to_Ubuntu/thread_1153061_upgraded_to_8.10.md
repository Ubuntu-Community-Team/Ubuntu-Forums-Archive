---
title: "upgraded to 8.10"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-08
and aftert I log in I get a blank screen. Can some one help me or direct me to a webpage that explains how to fix this? Thanks

---

### Post by taurus on 2009-05-08
Boot into recovery mode from GRUB menu (if you don't see the menu, then press Esc key to bring it up).  Then, pick the **xfix** option to reset your X server.

---

### Post by shadowlands on 2009-05-08
Can you give me step by step directions for performing this task?  Thanks!!> **taurus said:**
> Boot into recovery mode from GRUB menu (if you don't see the menu, then press Esc key to bring it up).  Then, pick the **xfix** option to reset your X server.

---

### Post by taurus on 2009-05-08
The steps are similar but you would pick the xfix option when you get to the last step to reset your X server.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by shadowlands on 2009-05-08
You are great!! Wonderful!! but it did not work. > **taurus said:**
> The steps are similar but you would pick the xfix option when you get to the last step to reset your X server.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by taurus on 2009-05-08
Did you upgrade your machine from 8.04 to 8.10?  You were not able to use your machine since the upgrade?

---

### Post by shadowlands on 2009-05-08
That is correct. > **taurus said:**
> Did you upgrade your machine from 8.04 to 8.10?  You were not able to use your machine since the upgrade?

---

### Post by bodhi.zazen on 2009-05-08
What videocard do you have ?

Are you using compiz ?

---

### Post by shadowlands on 2009-05-08
Not sure what that is and how do I find out?> **bodhi.zazen said:**
> What videocard do you have ?

Are you using compiz ?

---

### Post by shadowlands on 2009-05-08
I cannot get to anything?  Help please!! > **bodhi.zazen said:**
> What videocard do you have ?

Are you using compiz ?

---

### Post by abn91c on 2009-05-08
if its a blank screen but you can move the mouse around, removing compiz from the command prompt may fix your issue
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by piobair on 2009-05-08
In upgrading to 8.10, KDE 4.4 came with it.
It is horrible. The entire look & feel changed toward the worst of Vista.
What is the best way to step back to 4.3? Using Package Manager I can remove everything that is 4.4.2 and then install (something else). Is this the best way?
Piobair

---

### Post by shadowlands on 2009-05-08
I did  the screen still fades not to black but to a muddy tan color.   I open the  root thing to take the chip set off and no no it still not working > **abn91c said:**
> if its a blank screen but you can move the mouse around, removing compiz from the command prompt may fix your issue
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by abn91c on 2009-05-09
what happens if yor run the **metacity --replace** command

---

