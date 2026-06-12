---
title: "crontab not working...."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by davidstri on 2009-04-15
I have a script that looks like this, and it's name is anki: 
#!/bin/sh
export DISPLAY=:0
anki
and I'm trying to direct crontab to it with this at 12:42 pm: 
42 12 * * * $HOME/anki
But it isn't working.
This is what the permissions for the anki file and the .Xauthority file look like. Anki file: "-rwxr-xr-x 1 david david 33 2009-04-15 12:22 anki"
.Xauthority: "-rwxr-xr-x 1 david david 124 2009-04-09 13:52 /home/david/.Xauthority" (without quotes). I do not know why it not working. It worked before. Please help. Any help would be much obliged.

---

### Post by jbrown96 on 2009-04-15
I'm pretty sure that bash scripts have to end in .sh

---

### Post by llamabr on 2009-04-15
> **jbrown96 said:**
> I'm pretty sure that bash scripts have to end in .sh

Nope.  That's just a convention.

This script runs in a loop, since it calls itself.  was that your intention?  it also never ends -- it should have the exit command at the end.

What are you doing to edit your cron file.

---

### Post by Nepherte on 2009-04-15
Use the full path to the scipt instead of $HOME and make sure the script is executable. Cron doesn't know that variable.

---

### Post by davidstri on 2009-04-15
This is what I'm doing to my crontab, "15 13 * * * $HOME/anki". That should have started the anki script that was in my home folder at 1:15 p.m, but it didn't... I don't see anything wrong with either of my files... Also, I remember when the script was working, the bottom of the script had "exec" before the word anki. I tried adding "exec" to the script, but it did nothing. It still did not work.
Again, here is what the script to start the gui program, anki, looks like:

#!/bin/sh
export DISPLAY=:0
anki

When I click it, it works, so I do not know what the problem could be.

---

### Post by davidstri on 2009-04-15
Changing $HOME/anki to /home/david/anki or home/david/anki or /david/anki ect. did not work.

---

### Post by klein de usa on 2009-04-15
hi 
i'm having problems to, with a bash script and cron.
cron rund the script but it doesn't start the file.

#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
echo "helo corntabtrans $(hostname)" >> /home/klein/Desktop/tyler
export DISPLAY=:0.0
/usr/bin/transmission
exit 0

 echo "helo corntabtrans $(hostname)" >> /home/klein/Desktop/tyler  opends a file on my desk top and prints the output of  echo "helo corntabtrans $(hostname)" i know the script is running just isn't starting transmission


i also have found that echo 'date' does not print the date any more i thought it worked a while back

---

### Post by bodhi.zazen on 2009-04-15
cron uses a very minimal shell.

You have to use the full path to applications.

---

### Post by davidstri on 2009-04-15
Sorry klein de usa, but I don't know anything about cron or sripts, and, to tell the truth, I don't think cron works that well, or maybe I'm not adding the full path to the script. Can someone please give me an example of a full path to a script. Or just an example of a script and crontab that work. It would be a great help to all of us using cron, thanks.

---

### Post by klein de usa on 2009-04-15
hi davidstri

i have one that works that is why i'm so confused. below is what my root cron looks like:

#m= minute(s)
#h= hour(s)
#dom= day(s)_of_month
#mon= month(s)
#dow= day(s)_of_week
# m h  dom mon dow   command
30 3 * * * /home/klein/scrip/aupdate
46 15 * * * /home/klein/scrip/crontabtrans

and this is my bash script that works:

#!/bin/bash
# This script will autoupdate ubuntu 8.04.01 and creat a file on my desktop 
# as to what it did i can deleat the file if it is ok or leave it and the 
# next update will just add to the bottom of the file 
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
echo "helo $(hostname)" >> /home/klein/Desktop/tyler
date >> /home/klein/Desktop/tyler
echo 'data'>> /home/klein/Desktop/tyler
echo "subject: Aptitude cron $(date)" >> /home/klein/Desktop/tyler
echo "aptitude update" >> /home/klein/Desktop/tyler
aptitude update >> /home/klein/Desktop/tyler 2>&1
echo "" >> /home/klein/Desktop/tyler
echo "aptitude dist-upgrade" >> /home/klein/Desktop/tyler
aptitude -y dist-upgrade >> /home/klein/Desktop/tyler 2>&1
echo "" >> /home/klein/Desktop/tyler
echo "aptitude clean" >> /home/klein/Desktop/tyler
aptitude clean >> /home/klein/Desktop/tyler 2>&1
echo "done updateing and installing" >> /home/klein/Desktop/tyler 


this script updates my computer every night i leave it on and creates a txt file on my desktop telling me what it did, also if there are any errors 


i have done this before that is why i can't figure out why i can start transmission with a script ?  confused lol 

#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
echo "helo corntabtrans $(hostname)" >> /home/klein/Desktop/tyler
date >> /home/klein/Desktop/tyler
export DISPLAY=:0.0 
echo "display" >> /home/klein/Desktop/tyler
/usr/bin/transmission %F
echo "transmission" >> /home/klein/Desktop/tyler 
exit 0


here is the out put of my text file after the script has run:

helo corntabtrans klein-aopen
Wed Apr 15 15:46:01 EDT 2009
display
transmission


so to me it looks like it is running just not starting the program transmission?

---

### Post by kerry_s on 2009-04-15
> below is what my root cron looks like:

it's a user program it shouldn't be in root any thing, just>
crontab -e <no sudo!


> Can someone please give me an example of a full path to a script. Or just an example of a script and crontab that work. It would be a great help to all of us using cron, thanks.

i only have a poor mans alarm clock in mine.

---

### Post by davidstri on 2009-04-16
kerry_s: Sorry, it's taken a while to get back. I outputted crontab's error into a file using cheesehead's tip and this is what it says, 
"Invalid MIT-MAGIC-COOKIE-1 keyanki: cannot connect to X server :0"

---

### Post by davidstri on 2009-04-16
Oops, I meant unutbu's tip, sorry, again.

---

### Post by klein de usa on 2009-04-16
hi davidstri
 
not sure if this will help and i haven't tried it my self yet but reading [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto") has a couple of tips.

look under tips on this web page and it is the third example down:
00 06 * * * env DISPLAY=:0 gui_appname

for you it might be :
00 06 * * * env DISPLAY=:0 gui_anki

---

### Post by davidstri on 2009-04-17
Sorry klein de use, it didn't work. Nothing seems to be working with cron. Maybe I'll just do a clean re-install of ubuntu onto my hard-disk and see if it works, because I really want this crontab to work.

---

### Post by davidstri on 2009-04-18
I fixed it! And the solution was so easy! lol. I narrowed the problem down to the .Xauthority file...or at least one of those hidden system files in my home folder. I did not actually fix the .Xauthority file, but I found a permanent workaround: delete all the hidden system files in your home directory(take extreme caution, I really had no idea what I was deleting so make a backup before deleting all your sysytem files) and replace them( not the backups) with all the hidden files from a new account. You can make the new account with ```
sudo adduser username
```. Then go into the new account and copy all the hidden system files onto a disc or external hdd. Go back to your account(the one with the problems) and paste all the hidden system files from the hdd.(the files in the hdd are hidden so you have to hit Control+h to reveal them.) Wala! Everything's back to normal. Oh, and if you want you can delete the new account you made through System> Administration> Users and Groups.

---

### Post by davidstri on 2009-04-18
btw. Do NOT delete all the files in your filesystem directory. Delete the ones in your account directory, e.g home/david(your home account directory).

---

### Post by llamabr on 2009-04-18
Deleting your user and adding it back fixed your crontab problem?

---

### Post by davidstri on 2009-04-18
No, I didn't have to delete my user(david). I deleted all the hidden files,the files that begin with a dot, in my user home directory(I'll call it david). To get to your user home directory, go to Places> Home. Then I made a new user, I'll call it david2. After I made the new user(david2), I took all the hidden system(?) files from it's (david2's) home directory and copied them to my original user's (david's) home directory. 
Hope this helps if you're having the same problem. And yes, it did solve my crontab problem, if there was a problem with crontab wich I'm pretty sure there wasn't. I am almost 100 percent sure the problem was with the .Xauthority file in my home directory.

---

### Post by davidstri on 2009-04-18
Maybe you just have to replace the .Xauthority file, but I replaced all the hidden files in my home just to be sure.

---

