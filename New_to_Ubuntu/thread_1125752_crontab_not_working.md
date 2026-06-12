---
title: "crontab not working"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by davidstri on 2009-04-14
I opened crontab with crontab -e, and then added the following line to make the program run at 6:45 pm: 45 18 * * * /usr/bin/anki
but it won't open anki even though I can see that anki is in /usr/bin. How can I make it open this program?

---

### Post by kerry_s on 2009-04-14
is that a gui program?
if it is you need to export the display.
example:
export DISPLAY=:0

here's my alarm script as a example:
in crontab i have:
00 7 * * * $HOME/Scripts/alarmclock

alarmclock is:
#!/bin/sh
export DISPLAY=:0
amixer set Master 100% unmute
alsaplayer -S ~/Scripts/alarm.wav
amixer set Master 50%

---

### Post by davidstri on 2009-04-14
Wow, that looks complicated. Isn't there a program that just simply runs a command in a terminal at a specified time? I thought that was what cron did, but I guess not. I typed anki, a gui program, in terminal and it opened it correctly. I wonder why cron isn't working. :confused:

---

### Post by glennric on 2009-04-14
cron does run a program in a terminal at a specified time.  The thing is that a GUI program like anki is not run in a terminal.  cron does not have the environment variables set that your user has set.  That is why you have to have a script to set the environment variables for the program run via cron.

---

### Post by davidstri on 2009-04-14
I added this line to crontab: 44 19 * * * export DISPLAY=:0 && /usr/bin/anki
 and it still didn't open the program. Is there anything else I can try?

---

### Post by unutbu on 2009-04-14
Run this command to see if /usr/bin/anki is getting run by cron:
```
grep anki /var/log/syslog
```

You should see something like

```
Apr 14 18:58:01 host /USR/SBIN/CRON[10948]: (davidstri) CMD (/usr/bin/anki)
```

Run the following command to check that you (rather than root) own .Xauthority. 
```

ls -l ~/.Xauthority
```

(If you do not own ~/.Xauthority, cron loses the ability to display graphical apps.)

Finally, if neither of the above uncover any problems, change your crontab to 
```

44 19 * * * export DISPLAY=:0 && /usr/bin/anki > ~/anki.out 2>&1

```
This will pipe any output from stdout or stderr into ~/anki.out.
After the cron job is run, take a look at anki.out for any error messages.

---

### Post by Cheesehead on 2009-04-14
Try:
45 18 * * * DISPLAY=:0.0 /usr/bin/anki 2>&1

You shouldn't need to export the DISPLAY
Don't use a && after the DISPLAY

---

### Post by davidstri on 2009-04-14
I changed ownership of .Xauthority so that it now looks like this, -rwxr-xr-x 1 david root, then I tried running it again, still didn't work, so I looked at the anki.out file and this is what it says, 
"No protocol specified
anki: cannot connect to X server :0" 
What does that mean?

---

### Post by kerry_s on 2009-04-14
> **davidstri said:**
> Wow, that looks complicated. Isn't there a program that just simply runs a command in a terminal at a specified time? I thought that was what cron did, but I guess not. I typed anki, a gui program, in terminal and it opened it correctly. I wonder why cron isn't working. :confused:

sorry, i confused you mine is only a example of what mine looks like.

for yours it's very simple.
first create a file(right click> new file), in it put:

```
#!/bin/sh
export DISPLAY=:0
anki
```

right click it> properties> check the box to allow it to run. click on it to check if it works.

now just point cron to that: **$HOME/your-file**

very simple.

---

### Post by davidstri on 2009-04-14
kerry_s: It didn't work. I made the file in my Desktop directory and named it anki. Since, for some reason, I can't make scripts executable by clicking them, I wasn't sure if it worked or not. I then added this to my crontab, "33 20 * * * export DISPLAY=:0 && $HOME/Desktop/anki" but it didn't work. I also tried 33 20 * * * $HOME/Desktop/anki which also didn't work, heh.

---

### Post by davidstri on 2009-04-14
I checked the box to make the script executable and now it works when I click it, so at least I've narrowed it down to there being something wrong with something in the crontab.

---

### Post by glennric on 2009-04-14
Type
```
sudo chown david:david ~/.Xauthority
```
to set the user and group to your user "david" and group "david" (assuming that is your users group).
Then try it.

---

### Post by glennric on 2009-04-14
If that doesn't work type
```
/etc/init.d/cron status
```
If it returns " * cron is running" then check for typos in your command line.  If it returns " * cron is not running" then start it with
```
sudo /etc/init.d/cron start
```
Then try the cron line again.

---

### Post by davidstri on 2009-04-14
Thank you all, especially glennric and kenny_s, it worked. It worked when I changed the ownership and then directed crontab to the anki script glennric gave me. Thank you all again.

---

### Post by glennric on 2009-04-14
Just to make sure that the credit goes to the proper place, I think kerry_s gave you the script.

---

### Post by davidstri on 2009-04-14
oh yeah, sorry. kerry_s, my bad, hehe.

---

### Post by Alinn on 2009-06-06
Hi 
crontab doesn't run any comman.even:
```
00 03 * * * /sbin/shutdown -P now
```:-(

---

### Post by davidstri on 2009-06-08
Any command in sbin has to be used with the root crontab. e.g ```
sudo crontab -e
```. Hope this helped.

---

### Post by Alinn on 2009-06-08
> **davidstri said:**
> Any command in sbin has to be used with the root crontab. e.g ```
sudo crontab -e
```. Hope this helped.
Thanks davidstri
but crontab also doesn't run this :
```
gwget 
```or
```
transmission
```and i run this commands (also /sbin/shutdown witout sudo ) in ubuntu 8.10. in 9.04 not work:(

---

### Post by davidstri on 2009-06-09
([COLOR="Red"]Go to page 3 of this thread to see the workaround for this problem.[/COLOR])

Man, I tried using crontab for the first time using Ubuntu 9.04, and it didn't work. I tried doing it a lot of different ways and it still didn't work. I did the exact same thing I did for Ubuntu 8.10. So, I know there's something wrong with crontab.
Sorry, Alinn, I'm stumped. I'm guessing it's a glitch with crontab.
Sorry, hope you have better luck, and if you do, let me know, thanks.

---

### Post by davidstri on 2009-06-10
I found a workaround. If anybody has a better idea I would gladly except it, but for now I just have this workaround.

(First, make a new user and check and see if crontab works with that user, if it does you can do the workaround, but if it doesn't, the workaround probably won't work for you.
You can now either get rid of the new user you just made that works with crontab or use it for the workaround below)

Make a folder called hiddenfolder1 and place all of your hidden text files (text files that begin with a dot) into hiddenfolder1. 
Open up a terminal and type ```
sudo adduser temp
```(or add any other user-name besides temp).
Log into user "temp" and make a folder called hiddenfolder2 and place all of temp's hidden text files into it.
Open up a terminal while still logged into temp and type ```
su yourusername
```
and enter your password.
While in terminal, type, ```
sudo mv hiddenfolder2 /home/yourusername
```
Exit the terminal and log out of temp.
Log into your account and open up a terminal again, and type ```
cd hiddenfolder2
```
Then type ```
sudo chown yourusername:yourusername .*
``` 
take all of the hidden files in hiddenfolder2 and place them in your home folder.
Check and see if crontab works. If it doesn't work, you can delete the hidden folders that you placed there from temp and place all of your original files back into home folder. 
Let me know if any of the above directions were confusing

WARNING: DO THIS AT YOUR OWN RISK, don't say I didn't tell you to put all of the hidden files in your home folder into a different folder instead of deleting them.

This is only a workaround. If you would like to experiment by replacing each hidden file in your home folder with the ones in temp one-by-one until crontab starts working, that would be awesome!

Since I am not a Linux wiz, I could not properly fix this problem, but if there's anyone out there who could, I would be glad to hear from them!

---

### Post by Alinn on 2009-06-10
thanks so much davidstri:p
when i type ```
sudo chown alinn:alinn .*
```output is:
```
chown: cannot access `.gvfs': Permission denied
```:(

---

### Post by davidstri on 2009-06-10
Oh yeah, I forgot there are hidden folders too.
Then make a folder called hiddenfolder3 and move all of your hidden text files into it and then open a terminal and type ```
cd hiddenfolder3
``` and ```
sudo chown alinn:alinn .*
```, then move all of the hidden files in hiddenfolder3 back into your home folder. If crontab still doesn't work, then I guess you'll have to do the entire workaround, hehe, sorry.

---

### Post by Alinn on 2009-06-11
I did all of this steps.but crontaab not work yet :(

---

### Post by davidstri on 2009-06-11
Huh, then, make another user and see if crontab works with that user. 
```
sudo adduser newuser
```
BTW, what does your crontab entry look like and what are you trying to do make it do?

Here, this is what I did.
I put this entry into my sudo(root) crontab:
28 23 * * * /sbin/shutdown -hP now
and it works fine.
I am not sure why my crontab was not working earlier.

Did you maybe replace the hidden files from the new user yourusername with your original user hidden files?

Check if you own .Xauthority with ls -l .Xauthority, if you do, you should be good, but, if you want to try the steps again you can.
I will try to make the steps more clearer.
(I just made the steps more clearer if you want to try the workaround again, and I added something else that might help)

---

### Post by Alinn on 2009-06-11
> **davidstri said:**
> Huh, then, make another user and see if crontab works with that user. 
```
sudo adduser newuser
```BTW, what does your crontab entry look like and what are you trying to do make it do?

Here, this is what I did.
I put this entry into my sudo(root) crontab:
28 23 * * * /sbin/shutdown -hP now
and it works fine.
I am not sure why my crontab was not working earlier.

Did you maybe replace the hidden files from the new user yourusername with your original user hidden files?

Check if you own .Xauthority with ls -l .Xauthority, if you do, you should be good, but, if you want to try the steps again you can.
I will try to make the steps more clearer.
(I just made the steps more clearer if you want to try the workaround again, and I added something else that might help)
Thanks
I test it in temp and newuser but didn't work.output of ls -l .Xauthority:
```
-rw------- 1 alinn alinn 122 2009-06-11 19:54 .Xauthority
```
I tried these:
```
25 21 * * * /usr/bin/firefox
25 21 * * * firefox
25 21 * * * transmission
25 21 * * * gwget
25 21 * * * /usr/bin/gwget

```

---

### Post by davidstri on 2009-06-11
Put this into a file and name it firefox_script, 
#!/bin/sh
export DISPLAY=:0
firefox
, make it executable with sudo chmod +x, double click it, click "run", and if it opens firefox then add this to your crontab, "50 13 * * * /home/alinn/firefox_script" (without quotes)
and tell me what the output of ```
cat .Xauthority
``` is.

---

### Post by Alinn on 2009-06-11
It works:)
output for that command is:
```

 Alinn-Linux0MIT-MAGIC-COOKIE-1a&#65533;&#333;&#65533;&q&#65533;&#65533;x~&#65533;&#65533;localhost.localdomain0MIT-MAGIC-COOKIE-1a&#65533;&#333;&#65533;&q&#65533;&#65533;x~&#65533;&#65533;
```
it is strange!:shock:

---

### Post by davidstri on 2009-06-11
Haha, the same thing happened to me. After moving the files around and changing the permissions a lot, it automatically started working. I couldn't really explain it.
I'm glad yours started working too.
I hope it keeps working,;),  bye.

---

### Post by Alinn on 2009-06-11
For all thing that i want run in crontab i must create a script with:
```
#!/bin/sh
export DISPLAY=:0
my command
```
is it correct?

---

