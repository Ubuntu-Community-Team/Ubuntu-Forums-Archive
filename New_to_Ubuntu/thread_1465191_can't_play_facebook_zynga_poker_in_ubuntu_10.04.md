---
title: "can't play facebook zynga poker in ubuntu 10.04"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by tanvir_tamim on 2010-04-29
Hi,
   i am using ubuntu 10.04 now and i have installed adobe flash plugnis. but stil i cant play facebook zynga poker . it loads the page but not the full poker interface. after connecting to the poker,i cant see any table list and online poker buddy . i am a poker freak,so please help me with this.

---

### Post by Jon Monreal on 2010-04-29
Are you using Firefox?

Perhaps you could try [Chrome]("http://www.google.com/chrome") and see if that works any better for you.

---

### Post by Calash on 2010-04-29
Can you type the following into your address bar

```

about:plugins

```

You should find a section title "Shockwave Flash"
Past the area right below the title that tells you the file and version in your reply here.

---

### Post by tanvir_tamim on 2010-04-29
i used chromioum ,opera as well as firefox,,but still the same problem. let me put a screenshot. this will help u to understand my problem.  [ATTACH]154705[/ATTACH]

---

### Post by Calash on 2010-04-29
That may be a Facebook issue.  It has been running painfully slow for me today.


Can you get me your flash version as posted earlier?  That way we can be sure the advice is relevent to your setup.


Thanks

---

### Post by DrMelon on 2010-04-29
It's because Ubuntu has an awesome "Anti-crappy-game" filter.

On a serious note, maybe Flash is struggling? Do you have the latest version of flash?

---

### Post by tanvir_tamim on 2010-04-29
ya, i have all updated flash player . adobe flash plugin 10, and later i hav installed swfdec flash player too. i have tried that in diffrent browsers like firefox,chromioum,chrome,opera,and seamonly nevigator,,but never worked for me . feeling helpless ryt now coz i m a poker freak.

---

### Post by tanvir_tamim on 2010-04-29
> **Calash said:**
> That may be a Facebook issue.  It has been running painfully slow for me today.


Can you get me your flash version as posted earlier?  That way we can be sure the advice is relevent to your setup.


Thanks



see this [ATTACH]154717[/ATTACH]

---

### Post by QIII on 2010-04-29
swfdec conflicts with Flash.

Try removing it and see if your situation improves.

---

### Post by Calash on 2010-04-30
As noted above you should get rid of swfdec and gnash (if you have it).  

Two other suggestions you could try if the above does not work.


1 - Try installing swiftfox and see if it performs better.
[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

2 - There is a beta version of the newest Adobe that I have had much success with.  I only reccomend this as a last option as you will be installing something directly.  Being that it has no repo there will be no updates automatically and you would have to update it yourself.

(I suggest this because my wife had issue with Bejeweled on Facebook.  This version of Flash cleared it up for her)

I have only tested these instructions in Firefox/Swiftfox.  I do not know if they work outside of that.


Instructions
- Remove all flash plugins via your preferred package manager
- Close Firefox/Swiftfox
- Open a terminal and type the following

```

sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 

```

This removes the file for the flash plugin incase the uninstall does not do it.

- Download the following
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz)

This is the 10.1rc2 release

- Extract the libflashplayer.so to your home folder
- type the following in the terminal

```

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

```

Restart you favorite "fox" type browser and type about:plugins to see if everything worked.

Please note that if you decide to do this, then go back to the repositories you should hand delete the file using the rm line before starting.

Use at your own risk...yadda yadda :)

---

### Post by TheConsaw on 2010-04-30
this works for me 10.04

[http://ubuntuforums.org/showpost.php?p=8676654&postcount=13](http://ubuntuforums.org/showpost.php?p=8676654&postcount=13)

---

### Post by StuartIanNaylor on 2010-05-01
Get exactly the same fault. Zynga poker loads but you cant get a table list or see the online players (buddies).

Is your a new install of 10.04 LTS as mine is. Same in firefox and chrome everything seems to me loaded. Go to laptop with Karmic with the same and it works.

? Dunno the answer been trying Flash, Java to no avail.

---

### Post by rjaguar3 on 2010-05-01
The solution got the game running; however, after playing a few hands, I cannot use the type-in raise box nor the raise slider, obviously making strategic gameplay impossible.  Has anyone been able to fix this?

---

### Post by refr80 on 2010-05-03
Hi:
I downloaded a lot of different things(from this thread and other places) but nothing worked.  Then I thought: "what if I download shockwave from Synaptic?"  It kinda work.  So far I can play Farmtown, haven't been so lucky with Cafeworld.
Just go to System > Administration > Synaptic Package Manager.  Start writing shockwave and check to download and install this two packages:
    swfmill
    libimage-size-perl

If someone else has an idea to fix this completely, please help.
RE.

---

### Post by todorasa on 2010-05-28
thanks [Calash]("http://ubuntuforums.org/member.php?u=244658")..
now i can play zynga poker.. :)

---

### Post by urban191 on 2010-06-07
Well , after searching the web for a long time I found a _**WORKING SOLUTION** _for this problem !
thought I should share it with you guys so here it is : 

[http://www.icemanblogger.com/2010/05/enabling-zynga-poker-table-list-and.html](http://www.icemanblogger.com/2010/05/enabling-zynga-poker-table-list-and.html)

I'm using ubuntu 10.04 (Lynx)
I took the concept of his tutorial and changed it to my system .
First , I had Firefox & Chrome installed already via the Software Center .
Then just copied the file he listed there and boom Zynga Poker is working !!

Sorry for my bad English and I hope it will work for all of you :)

---

