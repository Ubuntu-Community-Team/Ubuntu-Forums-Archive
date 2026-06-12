---
title: "weird pppoeconf problem..no worky after restart..."
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by floyd27 on 2005-10-18
hey..
I set up my adsl with pppoeconf 
and everything goes fine.. However after arestart I need to go through it all again..everytime..
i think it may be related to "sudo su"
I used this in 5.04 to set a su password but now it just gives me root access..no setting of a password, just straight to root..
When i set up pppoe with this it only lasts for the session?

any one know about this problem?

---

### Post by adwait on 2005-10-18
When you restar try running
```
sudo pon dsl-provider
```

---

### Post by floyd27 on 2005-10-18
That may be a temp solution but i dont want to have to do that at all.
In 5.04 it did it automatically..

---

### Post by adwait on 2005-10-18
If that is working, you probably haven't selected start connection at startup in pppoeconf. Try  running it again. If that doesnt work, put that in a file, make it exectuable using
```
chmod +x <filename>
```
Copy it to the /etc/init.d/ directory. The run rcconf
```
sudo rcconf
```
Check the box against the filename of the file you created usinmg the spacebar and ok it.
This will run all the commands in your file run at each start up.

---

### Post by mips on 2005-10-19
Why dont you let your ADSL router habdle the PPPoE stuff and just set your PC up for DHCP, much less hassle.

---

### Post by floyd27 on 2005-10-19
Got it wokring ..
Thanx for the help guys..

---

### Post by raywang on 2005-11-20
I encountered the same weird problem.  My solution is:

1. Edit the file /etc/network/interfaces (Don't forget to backup it), delete the lines automatically added by pppoeconf (you may identify them by the comments made by pppoeconf)

2. Re-run the `sudo pppoeconf' command

Hope it helps.

---

### Post by riokerr on 2005-11-26
Hi guys, 

I'm having a similar problem with my computer... It refuses to start DSL automatically after a reboot even in pppoeconf I told it too...  I installed a batch file in /etc/init.d/ that is supposed to automatically bring up my DSL connection and it only works sometimes after a reboot... 


I deleted my entry in /etc/network/interfaces and that fails to help my problem either... does anyone have any suggestions?  This is a fresh install of breezy on a pentium 4 and this is my major complaint.  I have to manually type pon dsl-provider everytime and sometimes that doesn't even work...

I even found my nameservers were different from what they were and changed them and that worked once... This is very annoying and frustrating... trying to hook this computer so it can be used by less novice users... :(   If anyone has any more suggestions I'd be very happy.  Thank you :)

---

### Post by floyd27 on 2005-11-26
Do you have dual lan?
I do and the problem i had was i was choosong the second lan..I switched to the first one and it worked fine.. You have to do this in the install though..

---

### Post by riokerr on 2005-11-27
OK, yes I do have a dual lan setup I originally used my builtin etherexpress pro 100 as the NIC for my dsl and eth1 (a Linksys) for the internal network.  On my most recent install I switched it using my 2nd lan as dsl connection and 1st as internal network... Then I  had even worse luck...  Is there any logical reason to why it doesn't start automatically???  on my next install I'll try it on the 1st lan device but I've done it several times before w/out any success...

John

---

### Post by floyd27 on 2005-11-28
Well I did a re-install and choose my main lan port.. Both of mine are built in but the second is different i guess.
All i know is when i switched to the main one (in the install config) everything was good..
Hope you get it working.
im sure there is a way to switch without having to re-install but im not the one to ask..

---

