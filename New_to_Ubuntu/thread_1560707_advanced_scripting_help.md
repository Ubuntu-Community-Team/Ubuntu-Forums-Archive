---
title: "advanced scripting help"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-08-25
i have all my scripts in /home/ray/.gnome2/nautilus-scripts

when i right click on the desktop and open the scripts folder i get a pop up of all my scripts. if i click on the scripts they will run from the popup menu except for the following two i have to open the script folder (wont run from the popup menu) what do i need to do to modify them here they are

#!/bin/bash
echo xxx | sudo -S rkhunter --check
sleep 5

and

#!/bin/bash
echo xxx | sudo -S chkrootkit 
sleep 5

note the xxx is my password

must be a syntax problem as an example the following script will work from the popup menu and it follows the same syntax as the two above

#!/bin/bash
echo xxx | sudo -S shutdown -r now

tks

---

### Post by jazzerit on 2010-08-25
Use this instead for them:

#!/bin/bash
gksudo -S chkrootkit 
sleep 5


#!/bin/bash
gksudo -S shutdown -r now

this means that when you run it, it will come up with a graphical box to enter your password- the same one as when you start synaptic package manager. Hope this does what you want.

---

### Post by ayenack on 2010-08-25
Could be because they are being run as root.

Edit:- Just read the above post says the same thing and gives a solution.

Edit:- An alternative would be to run the programs as cron jobs.

Have a look here for cron how to.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

It could be something like this.

**sudo crontab -e**

Then add.

[B]# m h  dom mon dow   command

00 13 * * 1 /usr/bin/sudo rkhunter -c -sk[/B]


This would run rkhunter every monday at 13:00 hours.

---

### Post by rburkartjo on 2010-08-25
tks guys but even if i use gksudo get the same result i have to physically open the script folder to run. might try the cron idea. really curious as to why the scripts wont work from the popup window. all the others do i and i am running some of them as root/tks

---

### Post by ayenack on 2010-08-25
hello rburkartjo.

Are you sure the script is not running?

I was puzzled why the scripts would not run so I made the exact same script as your rkhunter one put in /home/ayenack/gnome2/nautilus-scripts and it does run from right click menu but it runs in the background.

You can use top from command line or system monitor to see if it's running.

---

### Post by rburkartjo on 2010-08-26
aye how would i change it not to run in the background and how would i use top??/tks

---

### Post by ayenack on 2010-08-26
To run top open a terminal and type top.

I'm not sure how you'd get it to show up in a terminal.

But I've got a solution for you.

Right click on a panel and select **Add to Panel** then select **Custom Application Launcher** and then **Add** then in the drop down window select **Application in Terminal** call it H
**RKHunter** and use the command **/home/ray/.gnome2/nautilus-scripts** and the name of the script. You can do this with all the scripts.

Then you can run it with a single click. ;-)

---

### Post by rburkartjo on 2010-08-27
aye great idea tks

---

### Post by ayenack on 2010-08-27
No problem.

---

### Post by rburkartjo on 2010-08-27
aye just a note i had to set that launcher to application in terminal to work  verses just application to work. but does the job great

---

### Post by ayenack on 2010-08-27
Yep. That's what I put in the post have a look.

---

