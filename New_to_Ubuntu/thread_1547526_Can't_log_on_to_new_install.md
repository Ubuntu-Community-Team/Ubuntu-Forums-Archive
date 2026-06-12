---
title: "Can't log on to new install"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by bill.denbigh on 2010-08-06
I have just spent 2 days using a GSM modem setting up a new Ubuntu 10.04 system and updating all the things that needed doing. 

The first day i come to try to use the system for work, it shows me a graphical box, has bill-dmpss (my name and the computer) and asks for my password. The system has never asked for this before but i enter '123' (not my real password) which is the password i set up and have used many times over the last two days when i was asked to authenticate my updates or loading new programs. The gui goes black, thinks for a while and then makes a bing-bong sound and comes back to the same login screen. 

If i enter any password other than '123' it makes a thud sound and says 'authentication failure' and asks for a new password. This is different to when i enter '123'.

I tried going into the system from the grub menu into recovery mode (the second option down) and it asks me to enter a uid and p/w. I enter 'bill' and '123' and it logs in and gives me a command line prompt. I can use the only unix command i know 'ls' and see my files no problem. I just have no idea what to do after that.

Please help me, i have finally got the ubuntu system i wanted (this is my third try) and now after all the hard work the darn thing won't let me in. I think i am cursed...

Thanks in advance, Bill

---

### Post by ubunterooster on 2010-08-06
Restart the pc, when you come to the grub screen press the Escape key.  select "recovery mode". When you come to the command line type ```
 passwd bill
```follow the prompts to recover password and then type ```
reboot
``` to restart the pc and use the new password

---

### Post by Elmer Fudd on 2010-08-06
From your description, it sounds like you have the right uid/password.

Get back to the command prompt from the recovery mode choice and try:

sudo apt-get check
sudo apt-get update
sudo apt-get upgrade

startx

Let us know what happens

---

### Post by bill.denbigh on 2010-08-06
> **ubunterooster said:**
> Restart the pc, when you come to the grub screen press the Escape key.  select "recovery mode". When you come to the command line type ```
 passwd bill
```follow the prompts to recover password and then type ```
reboot
``` to restart the pc and use the new password

I followed the above instructions and reset the password to '123456789' and then rebooted. I got back to the graphical screen and when i entered the new password, it acted exactly the same as if i entered the '123' password before. Now if i enter '123' i get the 'authentication failure' message.

I can go back and enter the system in recovery mode and it requires the new '123456789' password to enter. Other than that, everything is exactly the same.

---

### Post by bill.denbigh on 2010-08-06
> **Elmer Fudd said:**
> From your description, it sounds like you have the right uid/password.

Get back to the command prompt from the recovery mode choice and try:

sudo apt-get check
sudo apt-get update
sudo apt-get upgrade

startx

Let us know what happens

sudo apt-get check - gives me:
Reading package list... Done
Building dependency tree
Reading state information... Done

sudo apt-get update and sudo apt-get upgrade - fails to connect to any internet site as the only internet connection i have is a GSM modem that connects directly into the system.

startx - runs and gives me an all black screen with a mouse cursor but no ability to do anything

---

### Post by Elmer Fudd on 2010-08-07
> **bill.denbigh said:**
> sudo apt-get check - gives me:
Reading package list... Done
Building dependency tree
Reading state information... Done

sudo apt-get update and sudo apt-get upgrade - fails to connect to any internet site as the only internet connection i have is a GSM modem that connects directly into the system.

startx - runs and gives me an all black screen with a mouse cursor but no ability to do anything

Sorry, I don't understand.
You are appearantly connected to the net to post here.
What exactly is the system message from the "update" command?

---

### Post by bill.denbigh on 2010-08-07
> **Elmer Fudd said:**
> Sorry, I don't understand.
You are appearantly connected to the net to post here.
What exactly is the system message from the "update" command?

To post here I am connecting through an XP machine via a GSM modem that connects to the USB port. This is the only connection i have as i live at the top of a mountain in a remote part of the Philippines. To make this connection from Ubuntu, i have had to install the modeswitch thingy and it only runs after ubuntu is completely booted and working.

I am really at a loss here. I think i will wipe the system and start over. Something has obviously gone bad but i think finding it will take longer than re-installing and updating a fresh system.

---

### Post by cornelis spronk on 2010-08-13
I had the same problem on one of my computers.  I burned a new CD, and installed it, and I had the same problem again.

There is a bug in Lucid that needs to be fixed, and it apparently has not been fixed yet.

I reinstalled 9.04, which for me is the most bug free version at present.

---

### Post by bill.denbigh on 2010-08-15
It was certainly strange but this situation only occurred on one of the three systems i set up and once i reloaded the whole thing, everything has worked wonderfully. I am just writing it off to to a momentary glitch.

---

