---
title: "Linux Sports Ticker"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-09-26
I'm looking for a simple linux sports ticker with the following sports:

Cricket
Football (Soccer)
Formula 1

Basically I just want it to display current (preferably live) scores somewhere on my desktop. It can be an app, widget, or even a conky add-on. I have been unable to find anything.

Please help!

---

### Post by Marflus on 2009-09-26
You could use an RSS feed. There are loads of RSS feeds that display latest sports scores etc, and there are plenty of ways to display RSS on your desktop. Screenlets, conky scripts, I'm sure you can find loads.

That's how I'd do it.

---

### Post by abhiroopb on 2009-09-26
> **Marflus said:**
> You could use an RSS feed. There are loads of RSS feeds that display latest sports scores etc, and there are plenty of ways to display RSS on your desktop. Screenlets, conky scripts, I'm sure you can find loads.

That's how I'd do it.

Could you suggest any feeds please?

I have looked at a few feeds and none of them was really satisfactory...The problems I noticed were:

1. Feeds aren't really "live" they are dependent on how often they are updated from the source, and in some cases it hasn't been very effective.

2. The RSS feed format isn't really a "neat" way of displaying score updates..for example:

```

5" Liverpool 1 v 1 Hull
7" Man U 0 v 0 Man City
13" Liverpool 2 v 1 Hull

```

Basically, when there are many simultaneous matches going on it gets REALLY messy.

3. Feeds (generally speaking) aren't always customisable so I may have to put up with watching a number of games I don't particularly care about.

Anyway, if there is an RSS feed that solves the three problems above then I wouldn't mind using it, but so far I haven't found one that is suitable.

Thanks!

---

### Post by howefield on 2009-09-26
What about the score centre from sky sports ?


[http://www.skysports.com/score_centre/](http://www.skysports.com/score_centre/)

---

### Post by abhiroopb on 2009-09-26
Its a good website, but its just as useful as going to BBC sports. The feeds provided by Sky are "news feeds" and not really live updates. I mean I'd have to keep the browser open. I usually quite enjoy the BBC Live texts of various matches and events, but I was looking for something that would simply update the scores and would reside on my desktop (i.e. without a browser having to be opened).

---

### Post by upengan78 on 2009-09-28
How about this,

[http://sandeep.co.in/2008/11/01/get-the-cricket-score-on-linux-command-line-or-conky/](http://sandeep.co.in/2008/11/01/get-the-cricket-score-on-linux-command-line-or-conky/)

Although I haven't used it, it should work.

What I am using is below,

In conky.conf I have,
> ${execi 300 /etc/conky/conkyrss}

in conkyrss I have,
> 
#RSS Setup
URI=http://static.cricinfo.com/rss/livescores.xml
LINES=6 #Number of headlines

#Environment Setup
EXEC="/usr/bin/curl -s" #Path to curl

#Work Start
$EXEC $URI | grep title |\
sed -e :a -e 's/<[^>]*>//g;/</N' |\
sed -e 's/[ \t]*//' |\
sed -e 's/\(.*\)/ \1/' |\
sed -e 's/\.//' |\
sed -e 's/\"//' |\
sed -e 's/\"//' |\
head -n $(($LINES + 2)) |\
tail -n $(($LINES))

---

### Post by abhiroopb on 2009-09-28
Thanks for pointing out that post REALLY useful. I did not use you're script as it didn't work for me :(

---

### Post by upengan78 on 2009-09-28
> **abhiroopb said:**
> Thanks for pointing out that post REALLY useful. I did not use you're script as it didn't work for me :(

Glad the post worked for you, and I understand my script isn't helpful actually, I am now using the python script itself. Unfortunately it is pouring down at Jo'burg...

---

### Post by abhiroopb on 2009-09-28
It works really great now. I was wondering if it would be possible to get a script showing current football scores for (live) matches in the EPL.

---

### Post by abhiroopb on 2009-09-28
I know. I woke up in Singapore at about 12 midnight to start watching and just as I turned it on the game was stopped :(! Incidentally, I'm Indian so I don't think I'll be able to sleep tonight anyway.

---

### Post by abhiroopb on 2009-09-29
Would someone be kind enough to help write one for football scores, specifically in the English Premier League.

---

### Post by pkjm17 on 2009-11-02
I'm interested in a script for the EPL too in Conky. Also, does anyone have Audacious music player in their Conky file? Mine stopped working once I upgrated to 9.10. Anyone know the script?

---

### Post by sachin6870 on 2009-12-01
I have written gnome applet for cricket.  Please give try and let me know how it goes. It is written in python.
 [http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)



Thanks,

-- Sachin

---

### Post by sachin6870 on 2009-12-01
Screen shot:

[IMG]http://cricscoreapplet.sourceforge.net/cricscore.jpg[/IMG]

I am planning to enhance this applet to show wicket, score changes alert by using libnotify module.
 Also I am planning to have one applet for football score also.

Interested developers can join me. 

Thanks,

-- Sachin
[http://www.sachystechnoworld.co.cc/](http://www.sachystechnoworld.co.cc/)

---

### Post by abhiroopb on 2009-12-01
> **sachin6870 said:**
> I have written gnome applet for cricket.  Please give try and let me know how it goes. It is written in python.
 [http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)


Great applet and thanks for the hard work. Unfortunately, my panel is already full and I don't think I'd be able to fit this in (as it seems to take up quite a bit of space). Nevertheless I will be following the project eagerly.

---

### Post by sachin6870 on 2009-12-01
you can run this in separate window also,

sachin@sachin-laptop:~$ cricketscore.py run-in-window

cheers,

Thanks,

-- Sachin.

---

### Post by abhiroopb on 2009-12-01
Thanks will definitely try that. A libnotify updater is quite useful.

---

### Post by upengan78 on 2009-12-01
> **sachin6870 said:**
> I have written gnome applet for cricket.  Please give try and let me know how it goes. It is written in python.
 [http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)



Thanks,

-- Sachin

Thanks It's working. Will it also show score if there's more than 1 match ?

---

### Post by sachin6870 on 2009-12-02
No, currently it uses source data from 
[http://livechat.rediff.com/sports/score/score.txt](http://livechat.rediff.com/sports/score/score.txt)
which  is limited current popular match in India.

I am planning to extend it by using some other source like cricinfo or cricbuzz feed.

Thanks,

-- Sachin

---

### Post by upengan78 on 2009-12-02
> **sachin6870 said:**
> No, currently it uses source data from 
[http://livechat.rediff.com/sports/score/score.txt](http://livechat.rediff.com/sports/score/score.txt)
which  is limited current popular match in India.

I am planning to extend it by using some other source like cricinfo or cricbuzz feed.

Thanks,

-- Sachin

If you get that working, it will be 'cool':p 

Good luck!

---

### Post by sachin6870 on 2009-12-03
Hi All,
Released 1.0-alpha version of cricscore applet
 New features
  1) Match selection preference if there are multiple matches in progress.
  2) wicket, four, sixes update through libnotify module.

Download link and screenshots @ [http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)

Enjoy...

---

### Post by upengan78 on 2009-12-03
> **sachin6870 said:**
> Hi All,
Released 1.0-alpha version of cricscore applet
 New features
  1) Match selection preference if there are multiple matches in progress.
  2) wicket, four, sixes update through libnotify module.

Download link and screenshots @ [http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)

Enjoy...


Fun :)

Sorry but I am not using ubuntu right now. I am on gentoo and your first version = 0.9 worked on gentoo but this isn't working for me.

> cricketscore.py              
Traceback (most recent call last):
  File "/usr/local/bin/cricketscore.py", line 14, in <module>
    import pynotify
ImportError: No module named pynotify
Any idea?

emerged dev-python/notify-python , it was missing from my system,, now the error does not come up. 

I can't seem to see this applet in panel though :(


**It is working as intended. Many thanks for such a nice applet. Good luck for more such applets** ;)

---

### Post by Jorgo on 2009-12-03
Great applet!  I've been looking for something like this.  Just what I needed!

---

### Post by abhiroopb on 2009-12-03
Can you make the applet smaller so that it is just an icon or something. I love the libnotify update but I really don't want it taking up the entire applet and I don't want to open a separate window. Ideally I would like it to sit in my notification bar (i.e. next to pidgin, skype, etc.)

---

### Post by sachin6870 on 2009-12-04
Glad you liked it...

^above: Please use [Tracker]("http://sourceforge.net/tracker/?atid=1229722&group_id=290695&func=browse") to add feature request. I dont see it much needed feature. 

Cheers.

Thanks,
Sachin
[My Blog]("http://www.sachystechnoworld.co.cc/")

---

### Post by Jorgo on 2010-02-12
The cricscore applet doesn't seem to list one-day matches.  I'm trying to use it for the Australia vs West Indies game that is on at the moment but it doesn't come up in the list.

It worked great for the test matches!

---

### Post by EssexEagle on 2010-02-12
Is there any way of getting the cricscore applet to run in KDE?

---

### Post by sachin6870 on 2010-02-12
> **Jorgo said:**
> The cricscore applet doesn't seem to list one-day matches.  I'm trying to use it for the Australia vs West Indies game that is on at the moment but it doesn't come up in the list.

It worked great for the test matches!

score feed provider has changed base url to "http://synd.cricbuzz.com/splsng/scores-multi.xml"

Update /usr/local/bin/cricscore_prefs.py (Line No. 35)
from
     MAIN_URL = "http://synd.cricbuzz.com/splsng/"
to 
     MAIN_URL = "http://synd.cricbuzz.com/splsng/scores-multi.xml"

---

### Post by sachin6870 on 2010-02-12
> **EssexEagle said:**
> Is there any way of getting the cricscore applet to run in KDE?
no, it does not work with KDE yet.

---

### Post by Jorgo on 2010-02-22
> **sachin6870 said:**
> score feed provider has changed base url to "http://synd.cricbuzz.com/splsng/scores-multi.xml"

Update /usr/local/bin/cricscore_prefs.py (Line No. 35)
from
     MAIN_URL = "http://synd.cricbuzz.com/splsng/"
to 
     MAIN_URL = "http://synd.cricbuzz.com/splsng/scores-multi.xml"

That's done the trick.  Thanks.

---

### Post by sachin6870 on 2010-03-09
> **Jorgo said:**
> That's done the trick.  Thanks.

Released 1.1.0.3 verison with above fix

    * Corrected score feed URL
    * Corrected timeout to seconds

[http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)

---

### Post by Jorgo on 2010-12-16
I'm trying to get the scores for the Australia vs England game (3rd Ashes test) but the applet keeps saying "Match not yet started".  The game appears in the drop-down list.  It worked fine for the two previous tests.  Any ideas?

---

### Post by sachin6870 on 2010-12-19
Cricket score rss feed url was changed and updated url and fixed and released 1.1.0.4, download it from [here. ]("https://sourceforge.net/projects/cricscoreapplet/")

---

### Post by Jorgo on 2010-12-19
Thanks!

---

### Post by anlag on 2011-10-07
So has there been any progress on a good application or whatever method to get convenient and customizable live notifications of football games? I've looked around but I'm still struggling to be honest. There are websites but they're kinda nasty to use in comparison to what a neat app would be.

---

