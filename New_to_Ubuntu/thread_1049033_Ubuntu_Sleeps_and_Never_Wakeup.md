---
title: "Ubuntu Sleeps and Never Wakeup"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by NeoIndigo on 2009-01-24
Hi, 

I am having a problem whenever the OS goes to sleep, I can't run any programs. I cannot wake up. I have to restart my computer in order to run a program. 

I check the task manager, all of the program are sleeping. 

Can you please let me know how to solve this issue ? 

Thanks,

---

### Post by adobrakic on 2009-01-24
have you tried putting your cpu in the shower and turned really cold water on?
usually wakes me up

---

### Post by NeoIndigo on 2009-01-24
hey, 

Can anybody give me a help with this problem ?  

Thanks,

---

### Post by Cosimix on 2009-01-24
Hi there.
Programs in "Sleeping" status is ok, just means idle.
What do you mean for "goes to sleep", Suspend or Hibernate?? 
Do you have mouse/keyboard control?
*"I check the task manager, all of the program are sleeping." *How can you launch the gnome-system-monitor if your pc is not resuming[I]?
[/I]
The following are the most common problems and work around, if you explain in detail and step-by-step what happens and what the symptoms are, I might be able to give you a specific solution for you problem:

Simply try :
Ctrl+Alt+F1 wait for 3 secs Ctrl+Alt+F7 if nothing  Ctrl+Alt+F8 if nothing Ctrl+Alt+F7 again

Make sure you are running the latest kernel, I had this problem in the past with older kernels, so lets check your version:
**uname -r**                <<it should be 2.6.27-11
If not run this command...
**sudo apt-get update && sudo apt-get dist-upgrade**

One of the million of nice things in linux is that you seldom really need to restart the PC. Most of the times this should give you control back (**Note** _close your open files before proceeding_):
**sudo /etc/init.d/dbus restart**
...still hung? restart X by pressing **Ctrl+Alt+Backspace**

...if you can't open a terminal in X then do this instead:
Ctrl+Alt+F1 and login
**sudo /etc/init.d/gdm restart**
then Ctrl+Alt+F7 and login again in the graphic environment

---

### Post by NeoIndigo on 2009-01-24
Hi, 

Sorry If my explanation is not clear. 

Actually, the computer neither goes hibernate nor suspend. 

After inactive for a while, all of a sudden, I cannot run a firefox. Whenever I tried to run it, It's simply put into 'sleeping' status. (However, the screen is not turned to black as the usual screen when a computer goes to sleep)

I even cannot shut down the computer by clicking the shutting down icon on the top right of the desktop. If I click it, the computer then hang.

However, i can go to System>>Administration>>System Monitor to see the status of the programs. All of them are sleeping except the system monitor. (Is that a common case ?)

I checked my kernel version, it is 2.6.24-23-generic. I run your command "sudo apt-get update && sudo apt-get dist-upgrade". And it still gives me the same kernel version. 

Please let me know if you still need more explanation. I really appreciate your help. 

Thanks,

---

### Post by Cosimix on 2009-01-25
Hi Neo,
got it now! 

1. Try to open a terminal and run **sudo /etc/init.d/dbus restart**
2. Retry firefox launching it from the command line this time with the command **firefox-3.0 google.com** 
3. Observe the debugging info on the CLI

If you don't succeed and cannot launch applications in your Desktop Manager (GDM) you have to close your applications docs, pics, all your open files then restart GDM and Xserver, the problem may be with either one.


To restart X server use **Ctrl-Alt-Backspace** keystroke 

To restart GDM only: 

[B]Ctrl-Alt-F1 keystroke
[/B]login with your account
**sudo /etc/init.d/gdm restart**


**[COLOR=Red]YOU ARE DONE[/COLOR]**

It would be nice however to know which Ubuntu you are using. I am using Intrepid-8.10 and never had any problem at all (I am an heavy user of Ubuntu Server-8.04 Desktop-8.10).

If you want to upgrade your Desktop version to Intrepid do the following:

[B]sudo cat /etc/update-manager/release-upgrades
[/B]
add this line:[B]
Prompt=normal

sudo apt-get update && sudo apt-get dist-upgrade
[/B]

Cheers

---

### Post by NeoIndigo on 2009-01-26
Hi Cosimix, 

Thanks a lot for your information. Now, I have some work arounds to do if the problem comes up !! 

Thanks !! 

Bytheway, I have the same version as yours. I am not sure how to check my desktop version though. 

Thanks.

---

### Post by Cosimix on 2009-01-29
To be honest, I dont know how to do it from the CLI, but you can find it out in the  System Tab of your Gnome System Monitor

Cheers m8

---

