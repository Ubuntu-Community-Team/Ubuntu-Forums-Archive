---
title: "Need help with cron scripts"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by dchglat on 2008-12-13
Hi, I've searched the forums but couldn't find anything that would solve my problem.
I want to run a cron script that records streaming audio at a certain time. I followed a guide I found at instructables.com in order to do so. My script runs fine if run in the terminal (/home/gary/scripts/streamrecord), however cron fails to execute it.

this is the script:
#!/bin/sh
NOW=$(date +"%b-%d-%y")
/usr/bin/mplayer "http://207.245.67.204:80/" -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null ;
lame -m s /tmp/mystream.wav -o "/home/gary/Radio/PRH - $NOW.mp3" ;
rm /tmp/mystream.wav ;

After that I added this via the program kcron (this is the entry it added copied from "crontab -l"):
# StreamRecorderSun
0 14 * * 7	/home/gary/scripts/streamrecord

Nothing shows up in my /tmp/ directory when it's supposed to run and I'm unable to figure out why the script fails to be run by cron.

---

### Post by Bachstelze on 2008-12-13
Is the script executable?

```
ls -l /home/gary/scripts/streamrecord
```

Uh, yeah, if you can run it in the terminal, it most likely is. :p

cron usually sends you an email when stuff fails to be run, install exim and mutt:

```
sudo apt-get install exim4 mutt
```

And then you should see a "You have mail." mesage in your terminal when cron try to run the script but fails.

---

### Post by dchglat on 2008-12-13
Well, I erased everything and started from scratch and it works now. I'm not sure why exactly. I used gnome-schedule this time instead, after reading about it in other posts.
"crontab -l" now reads:
20 23 * * * /home/gary/scripts/streamrecord >/dev/null 2>&1 # JOB_ID_1
25 23 * * * /home/gary/scripts/pkill >/dev/null 2>&1 # JOB_ID_2

time is changed to test it. everything works as it should. I did install exim and mutt; sounds like it would be very useful in case of problems. I was unaware of this. thanks.

so my new question is what is ">/dev/null 2>&1" that gnome-schedule added at the end of every command? is that what I was missing iniatially for it to run properly?

---

