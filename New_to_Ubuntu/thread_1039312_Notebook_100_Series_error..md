---
title: "Notebook 100 Series error."
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Karenmrees on 2009-01-14
Just purchasd a Toshiba Notebook NB100-110 and connected it to my broadband via the wireless connection. Which was pretty simple.   I was told several updates were essential which I downloaded.  Now im unable to find the wireless connection option and can only either select wired connection or point to  point! Obviously an upgrade has cancelled out the wifi option. Any ideas as to how I can rectify?

---

### Post by thewrinklyninja on 2009-02-05
drop into the terminal and try :

sudo depmod -a

then reboot

---

### Post by Tuliku on 2009-03-01
A lot of people including myself experienced problems with the wired network connection after upgrading to the 2.6.27-11.

Currently i am using again 2.6.27-9 cause there everything still works.

---

### Post by Karenmrees on 2009-03-08
Tried this but it didnt work any other suggestions?

---

### Post by Karenmrees on 2009-03-08
no sure how rollback from 2.6.27-11.

---

### Post by Tuliku on 2009-03-09
Tell me first some more info about your system. 
You run 8.10 on a the toshiba nb100 ? 
Or 8.04 UNR ? 
And the only thing is Ubuntu or do you have some dual boot ?
What exactly do you get when you start our laptop, does it start up ubuntu directly, or you you first get the grub menu with a 10 second pause ?

---

### Post by Karenmrees on 2009-03-09
Oh god wish id stuck to windows! Well im running 8.04 when it starts up it goes directly to ubuntu. The only way to solve the problem is to  reload original settings but dont really want to have to do that again!  Really greatful for any help.

---

### Post by Tuliku on 2009-03-11
When your laptop starts up, there is a moment when it says "starting up grub, press esc to enter" or something like that. Press Esc and then choose the 3rd line which should be "2.6.27-09" or "2.6.27-07", and press enter. Then you start up the previous kernel.
When it works, let me know, and we can then set it up permanently so you dont have to press esc everytime you boot..

Good luck

---

