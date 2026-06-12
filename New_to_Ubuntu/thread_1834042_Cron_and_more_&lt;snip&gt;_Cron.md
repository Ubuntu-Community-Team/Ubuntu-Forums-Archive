---
title: "Cron and more &lt;snip&gt; Cron"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-08-26
OK, I give up. I have tried this every way I know how.

The basic file is kill_image

#!/bin/sh
#This is a script which will a) detlete all incidences of image*.* from the webcam file
# and will then start guvcview and get it to take a single photo.
# I will then use cron to run this scrip every hour.

PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


rm /home/pj-weather/Pictures/Webcam/image*

#sleep 10

guvcview -i /home/pj-weather/Pictures/Webcam/image.jpg -m 2 -c 30 --exit_on_close

mv /home/pj-weather/Pictures/Webcam/image* /home/pj-weather/Pictures/Webcam/image-1.jpg



exit 0

I chmod +x and Chmod 777 this script. I placed it in cron.hourly in the expectation that it would run. It never did I can get it to run with run-parts --verbose etc.

So, I thought, OK, I will run if from crontab if cron.hourly does not work...so here is the crontab...and yes there is a new line at the end...

0 1 * * * /etc/cron.hourly/kill_image

That does not work either!

This is all running on my weather machine which is on 10.04.

Cron.hourly is working as I tested it our with a basic echo file.

---

### Post by anewguy on 2011-08-27
Before I reply, please, no *&%^()) or any other implications in titles or text on the forum.

What happens if you manually run the script?  Does it require sudo to work manually?

---

### Post by dunbrokin on 2011-08-27
> **anewguy said:**
> Before I reply, please, no *&%^()) or any other implications in titles or text on the forum.

What happens if you manually run the script?  Does it require sudo to work manually?

Apologies for the frustration....sudo not required to run manually.

---

### Post by anewguy on 2011-08-27
Ok, so we know the script runs under your logon.  Now we need to determine if it is started by cron but ends up with some error so it doesn't appear to run.  I would add an echo with a redirect at the start, and after each significant part of the script.  Say perhaps you decide you want to put the output of the echoes in a file like test.txt in your home folder:

the first echo would be something like:

echo ** at beginning  ** > /home/"your user id here"/test.txt  notice only 1 redirect symbol (">") - this basically starts the file over as new.

for each subsequent echo:

echo ** at xxxx  ** >> /home/"your user id here"/test/txt notice the 2 redirect symbols (">>") which causes an append to the file


now, after cron has supposedly run the script, check for the file in your home folder and see what its' contents are.

This can help us determine 2 things:  whether or not the script even starts via cron and whether or not there is some sort of error if the script does start from cron.

I'm not very familiar with the cron stages right now - it seems like things are slightly different then they were in Unix 20 years ago!  I can research cron if needed when that time comes.  Right now it would be good just to see if it starts and whether or not it completes with no errors.

---

### Post by lisati on 2011-08-27
Thread title edited.

Friendly reminder from the [code of conduct]("http://ubuntuforums.org/index.php?page=policy"):

> Profanity: We have users of all age groups and of all tolerance levels where profanity is concerned. A language filter is in place to catch most major forms of profanity that may accidentally be used. Do not attempt to circumvent the language filter by using variations or slight misspellings of profanities.

---

### Post by anewguy on 2011-08-27
I'm not any form fo shell expert, but I did notice somethings you may want to consider:

Even though you know your app so supposedly everything would always exist, some checking and then error handling might be appropriate.  As an example, say something and the directory you try to remove things from is gone - the remove would fail.  There is no check first to see if anything exists, and no check for an error code afterwards.  Something this simple can cause your script to error out if I'm remember the basics correctly. 

Just some ideas while waiting for the results from my previous suggestions.

Dave ;)

---

### Post by dunbrokin on 2011-08-27
> **lisati said:**
> Thread title edited.

Friendly reminder from the [code of conduct]("http://ubuntuforums.org/index.php?page=policy"):

mea culpa

---

### Post by dunbrokin on 2011-08-27
> **anewguy said:**
> I'm not any form fo shell expert, but I did notice somethings you may want to consider:

Even though you know your app so supposedly everything would always exist, some checking and then error handling might be appropriate.  As an example, say something and the directory you try to remove things from is gone - the remove would fail.  There is no check first to see if anything exists, and no check for an error code afterwards.  Something this simple can cause your script to error out if I'm remember the basics correctly. 

Just some ideas while waiting for the results from my previous suggestions.

Dave ;)

Thanks, I wondered about that myself....but at this was supposed to be a "quick and dirty" script, (and as I am no expert in scripting) I decided to go the lazy route. I hear what you say, but I don't think that is the problem.

I have found a way around the problem for now....but, as you have had the decency to try and answer my question, it is only fair that I follow your instructions as it may help somebody else in the future....so, let me go and dig the original script out of the trash and set up as you suggested....back in a while.

---

### Post by dunbrokin on 2011-08-27
run-parts --verbose /etc/cron.hourly

Running the above command allows you to test cron.hourly scripts.

The script I ran was as follows:

#!/bin/sh
#This is a script which will a) detlete all incidences of image*.* from the webcam file
# and will then start guvcview and get it to take a single photo.
# I will then use cron to run this scrip every hour.

PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

echo first line > /home/pj-weather/Desktop/kill_image.txt

rm /home/pj-weather/Pictures/Webcam/image*

echo second line > /home/pj-weather/Desktop/kill_image.txt
#sleep 10

guvcview -i /home/pj-weather/Pictures/Webcam/image.jpg -m 2 -c 30 --exit_on_close

echo third line > /home/pj-weather/Desktop/kill_image.txt

mv /home/pj-weather/Pictures/Webcam/image* /home/pj-weather/Pictures/Webcam/image-1.jpg

echo fourth line > /home/pj-weather/Desktop/kill_image.txt


exit 0


and here is the content of the txt file

fourth line

Now, that was not so clever of me as each line probably overwrote the next....but at least it was executed.

Now, we will see what cron.hourly brings....watch this space :)

---

### Post by dunbrokin on 2011-08-27
OK, we got the exact same result in the txt file...and the image*.jpg file was deleted....the only difference was that the guvcview command was not executed.....so, therein the problem lies!

---

### Post by gmargo on 2011-08-27
> **dunbrokin said:**
> the only difference was that the guvcview command was not executed

Of course **guvcview** was executed.  You didn't see anything because **cron** runs a cron script in a santized environment, and does not supply a **$DISPLAY** environment variable, so **guvcview** doesn't know where to go.  And it probably printed an error message to that effect.

Check /var/log/syslog.  If you see cron throwing output away because there is no MTA installed, then install an MTA (Message Transfer Agent, aka Mail server.)  Then you'll get any script output and errors via email.

---

### Post by dunbrokin on 2011-08-27
As far as I can tell, this was the syslog output at the time the last cron was run


Aug 27 23:17:01 pj-weather-laptop CRON[19333]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 23:17:01 pj-weather-laptop postfix/pickup[17722]: 854E91F8D: uid=0 from=<root>
Aug 27 23:17:01 pj-weather-laptop postfix/cleanup[19344]: 854E91F8D: message-id=<20110827111701.854E91F8D@pj-weather-laptop>
Aug 27 23:17:01 pj-weather-laptop postfix/qmgr[11236]: 854E91F8D: from=<root@pj-weather-laptop>, size=874, nrcpt=1 (queue active)
Aug 27 23:17:01 pj-weather-laptop postfix/local[19346]: 854E91F8D: to=<root@pj-weather-laptop>, orig_to=<root>, relay=local, delay=0.48, delays=0.41/0.02/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Aug 27 23:17:01 pj-weather-laptop postfix/qmgr[11236]: 854E91F8D: removed
Aug 27 23:55:27 pj-weather-laptop crontab[20170]: (pj-weather) LIST (pj-weather)
Aug 27 23:56:02 pj-weather-laptop crontab[20184]: (pj-weather) DELETE (pj-weather)

---

### Post by gmargo on 2011-08-27
> 
  ... postfix/local[19346]: ...  to=<root@pj-weather-laptop>, orig_to=<root>, relay ... status=sent (delivered  to mailbox)
That looks good - it was delivered to your root mail account.  This would be **/var/mail/root** by default.  Of course you need to be root or use sudo to read that mailbox.  But it will give you the info that **guvcview** printed, if any.

You could set up the /etc/aliases file to forward root mail to your own userid.

---

### Post by dunbrokin on 2011-08-27
Yes, it did run as you said....but I am not sure why it would give the option list as the error message when it ran OK in run-parts.

From root@pj-weather-laptop  Sat Aug 27 22:17:02 2011
Return-Path: <root@pj-weather-laptop>
X-Original-To: root
Delivered-To: root@pj-weather-laptop
Received: by pj-weather-laptop (Postfix, from userid 0)
	id 20A9C3BEF; Sat, 27 Aug 2011 22:17:01 +1200 (NZST)
From: root@pj-weather-laptop (Cron Daemon)
To: root@pj-weather-laptop
Subject: Cron <root@pj-weather-laptop>    cd / && run-parts --report /etc/cron.hourly
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>
Message-Id: <20110827101702.20A9C3BEF@pj-weather-laptop>
Date: Sat, 27 Aug 2011 22:17:01 +1200 (NZST)

/etc/cron.hourly/kill_image:
option parsing failed: Cannot open display: 
guvcview 1.4.3
Usage:
  guvcview [OPTION...] - local options

Help Options:
  -?, --help                       Show help options
  --help-all                       Show all help options
  --help-gtk                       Show GTK+ Options

GTK+ Options
  --class=CLASS                    Program class as used by the window manager
  --name=NAME                      Program name as used by the window manager
  --screen=SCREEN                  X screen to use
  --sync                           Make X calls synchronous
  --gtk-module=MODULES             Load additional GTK+ modules
  --g-fatal-warnings               Make all warnings fatal

Application Options:
  --version                        Prints version
  -v, --verbose                    Displays debug information
  -d, --device=VIDEO_DEVICE        Video Device to use [default: /dev/video0]
  -a, --add_ctrls                  Exit after adding UVC extension controls (needs root/sudo)
  -o, --control_only               Don't stream video (image controls only)
  -r, --capture_method=[1 | 2]     Capture method (1-mmap (default)  2-read)
  -g, --config=FILENAME            Configuration file
  -w, --hwd_acel=[1 | 0]           Hardware accelaration (enable(1) | disable(0))
  -f, --format=FORMAT              Pixel format(mjpg|jpeg|yuyv|yvyu|uyvy|yyuv|yu12|yv12|nv12|nv21|nv16|nv61|y41p|grey|y16 |s501|s505|s508|gbrg|grbg|ba81|rggb|bgr3|rgb3)
  -s, --size=WIDTHxHEIGHT          Frame size, default: 640x480
  -i, --image=FILENAME             Image File name
  -c, --cap_time=TIME              Image capture interval in seconds
  -m, --npics=NUMPIC               Number of Pictures to capture
  -n, --video=FILENAME             Video File name (capture from start)
  -t, --vid_time=TIME              Video capture time (in seconds)
  --exit_on_close                  Exits guvcview after closing video
  -j, --skip=N_FRAMES              Number of inital frames to skip
  -p, --show_fps=[1 | 0]           Show FPS value (enable(1) | disable (0))
  -l, --profile=FILENAME           Load Profile at start
  --display=DISPLAY                X display to use

mv: cannot stat `/home/pj-weather/Pictures/Webcam/image*': No such file or directory

---

### Post by anewguy on 2011-08-27
I'm not sure of the syntax, but since it actually didn't run the guvcview and instead gave you the options and the error message about the display,  maybe you should try adding this option:

-d, --device=VIDEO_DEVICE Video Device to use [default: /dev/video0]

specifically, I wonder if it lets you say --device=NULL or some such thing to just dump the display output to nowhere.  I don't know if it will take that assignment or not, but it is quite evidently looking for an assigned video device and can't find one.  Maybe the directing to null will get around that.

Let us know.....

Dave ;)

---

### Post by gmargo on 2011-08-27
> **dunbrokin said:**
> 
option parsing failed: Cannot open display: 
...
  --display=DISPLAY                X display to use


You have not supplied either a --display argument or it's default, a **$DISPLAY** environment variable.

One way to make this work is to add a **$DISPLAY** variable (indicating the default display) to your script (before guvcview is run):
```

export DISPLAY=:0

```

---

### Post by dunbrokin on 2011-08-27
Nope, that did not work either....see below for the command in the script and the root mail folder output.

There is an option for --no_display in guvcview...but that is in version 1.5 and I only have only been able to download version 1.4.3 from the repositories.

From kill_image script

#!/bin/sh
#This is a script which will a) detlete all incidences of image*.* from the webcam file
# and will then start guvcview and get it to take a single photo.
# I will then use cron to run this scrip every hour.

PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

export DIPLAY=:0



rm /home/pj-weather/Pictures/Webcam/image-1.jpg


guvcview -i /home/pj-weather/Pictures/Webcam/image.jpg -m 1 -c 20 --exit_on_close


From /var/mail/root

/etc/cron.hourly/kill_image:
option parsing failed: Cannot open display: 
guvcview 1.4.3
Usage:
  guvcview [OPTION...] - local options

AAARRRGGGHHH!...it is a spelling mistake....my bad....I only saw this after I had posted....back to the drawing board.

---

### Post by anewguy on 2011-08-27
Try DI_S_PLAY, not DIPLAY.  Did you try adding the --device=NULL on the guvcview statement itself?

Dave;)

---

### Post by dunbrokin on 2011-08-28
OK, thanks all...that worked....much obliged to you all for  your help.

---

### Post by dunbrokin on 2011-08-28
> **anewguy said:**
> Try DI_S_PLAY, not DIPLAY.  Did you try adding the --device=NULL on the guvcview statement itself?

Dave;)

No, I did not try that...I did try --no_display....but that option only exists on 1.5 apparently.

---

### Post by dunbrokin on 2011-08-28
Hmmmm! the images produced now are locked with only root privilege....should I chmod 777 the newly created image within the script?

---

### Post by anewguy on 2011-08-28
If you don't care that anyone and any process can get access to the image(s), then sure.

If, however, the file(s) or the folder that contains them is not something you want everyone to have access to, perhaps you change ownership and access.  I guess it's up to you.  I'm curious if you'll be able to do so - I assume if it's running out of cron it's running with su rights, but if not I don't know if it will have the permissions to be able to change the rights.

At least you have gotten this far - if I've helped in anyway that's fine too - I'm just glad it's at least running now.

Best of luck!
Dave;)

---

### Post by dunbrokin on 2011-08-28
> **anewguy said:**
> I

At least you have gotten this far - if I've helped in anyway that's fine too - I'm just glad it's at least running now.

Best of luck!
Dave;)

Thank you so much....your help has been much appreciated...

---

### Post by Cheesehead on 2011-08-28
Now that you have the script working nicely with cron, you can fix the permissions issue by one of the following:
1) Go back to a user-based crontab
2) Put your user name in the cron.hourly crontab
3) Have the script chown and chmod to the desired username and permissions.

The third option is a hack. Either of the first two are preferable.

---

### Post by dunbrokin on 2011-08-28
No 2, seems to me the intuitively "best" way....can you give me some more details, please, as to how I might do this?

---

### Post by anewguy on 2011-08-28
I'm not sure, so I thought I would put this here so if nothing else perhaps Cheesehead can explain some of this to both of us ;)

I know you can run something like crontab -e and it will create things for crontab where you can specify the time increment it should run in.

Maybe this is what you already did - I'm not familiar with any of that.

Dave ;)

---

### Post by dunbrokin on 2011-08-28
Hi Dave,

I did both, I put the script in cron.hourly and set up a crontab when the cron.hourly did not work.....of course, and we now know why, the crontab did not work also....setting up the crontab was the easy bit crontab -e. In disgust, I deleted my crontab file...and have been working with the cron.hourly ever since.

Later..Ah!, I am guessing that by adding my name to the permissions for the cron.hourly I will have gained local control......neat!

---

### Post by anewguy on 2011-08-28
Cool!  I'm learning more every time I'm on the forum - now I know about the crontab users thing!

Thanks!

Dave ;)

---

### Post by dunbrokin on 2011-08-28
The gratitude is all mine, if it were not for you replying and getting me off my butt, I would not have solved the problem so elegantly.

---

### Post by ebecheto on 2013-04-04
For me the following execution works without X forwarding (when I disable X in putty). And so it works too with cron.

guvcview --display=:0 -i pic.jpg -m 1 -c 2 --exit_on_close --no_display &>/dev/null

version : guvcview 1.5.3

---

### Post by coffeecat on 2013-04-04
Old thread closed.

---

