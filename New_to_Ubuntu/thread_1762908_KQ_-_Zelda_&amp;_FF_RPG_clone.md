---
title: "KQ - Zelda &amp; FF RPG clone"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by cabbrick1243 on 2011-05-19
EDIT: I found it and posted it below. THIS IS NOT FOR KING'S QUEST
This is for a package named KQ of which was a Zelda and Final Fantasy clone that was available until 8.10

I played KQ several years ago, and I am disappointed that it is no longer in the repo's for 11.04.
It installed fine with .deb files I pulled from 10.04, so I am curios as to why it is no longer there?
Has lack of interest in the game caused it not to be moved forward?
Are there problems with it that I am unaware of?
Would someone be so kind as to add it back or to instruct me as to how I might?

---

### Post by wildmanne39 on 2011-05-19
> **cabbrick1243 said:**
> I played KQ several years ago, and I am disappointed that it is no longer in the repo's for 11.04.
It installed fine with .deb files I pulled from 10.04, so I am curios as to why it is no longer there?
Has lack of interest in the game caused it not to be moved forward?
Are there problems with it that I am unaware of?
Would someone be so kind as to add it back or to instruct me as to how I might?
If it has been around a long time it was probably just not that much interest in it anymore, you know the young people play a whole different type of games these days.

---

### Post by cabbrick1243 on 2011-05-19
> **wildmanne39 said:**
> If it has been around a long time it was probably just not that much interest in it anymore, you know the young people play a whole different type of games these days.

I understand..
I'm young, however, and enjoyed playing this on my bro's box several years ago.
He never was very good with linux though.
It reminds me of The Legend of Zelda: A Link to the Past on the SNES.
Thanks.

---

### Post by wlraider70 on 2011-05-19
WAIT...I can haz kings quest?

Where can I find it?

---

### Post by Gremlinzzz on 2011-05-19
You can find the games here free
[http://www.agdinteractive.com/](http://www.agdinteractive.com/)
they work using wine or windows
i see they have some new ones since the last time i played
[http://www.agdinteractive.com/games/games.html](http://www.agdinteractive.com/games/games.html)

---

### Post by cabbrick1243 on 2011-05-19
> **wlraider70 said:**
> WAIT...I can haz kings quest?

Where can I find it?

Here you go:
[https://launchpad.net/ubuntu/intrepid/+package/kq](https://launchpad.net/ubuntu/intrepid/+package/kq)
[https://launchpad.net/ubuntu/intrepid/+package/kq-data](https://launchpad.net/ubuntu/intrepid/+package/kq-data)

Downloads the .deb files of both under "Published Versions" for your system type.
I installed kq-data first, then the other and it seems to be working fine.
My bro is playing it at the moment. He says its running good.

---

### Post by cabbrick1243 on 2011-05-19
I now realize from Google that there are several games called King's Quest.
This is about a game that was labeled KQ on older versions of Ubuntu.
It is similar to The Legend of Zelda: A Link to the Past in graphics and gameplay.

---

### Post by Kim Kibum on 2011-08-09
Ok, first of all, i am a real newbie in all the Ubuntu stuff. 

And i want to install (and play) Kq (old zelda rpg fan). But....how do i do that..?

---

### Post by cabbrick1243 on 2011-08-09
> **Kim Kibum said:**
> Ok, first of all, i am a real newbie in all the Ubuntu stuff. 

And i want to install (and play) Kq (old zelda rpg fan). But....how do i do that..?
If you have 32 bit Ubuntu download these:
[1 kq-data]("http://launchpadlibrarian.net/15563001/kq-data_0.99.cvs20070319-1.1_all.deb")
[2 kq]("http://launchpadlibrarian.net/15563002/kq_0.99.cvs20070319-1.1_i386.deb")
If you have 64 bit Ubuntu download these:
[1 kq-data]("http://launchpadlibrarian.net/15563001/kq-data_0.99.cvs20070319-1.1_all.deb")
[2 kq]("http://launchpadlibrarian.net/15565619/kq_0.99.cvs20070319-1.1_amd64.deb")
Other processor types [kq-data]("https://launchpad.net/ubuntu/intrepid/+package/kq-data") and [kq]("https://launchpad.net/ubuntu/intrepid/+package/kq").

After that double click on the downloaded .deb that begins with kq-data to install it first. The software center should load and offer to install. Install it and give it your password. Once finished install the other .deb that begins with kq.
You should be able to find it by searching for KQ in Unity or under Games in GNOME.

Run it and it should be good to go. The default controls are a bit odd so do look at the config in the main game menu. I think there is a glitch in the menu while playing... Don't expect anything in the game to be fixed unless you do it yourself because the development on this game is pretty much dead.

---

### Post by SoFl W on 2011-08-09
When they bring back Leisure Suit Larry let me know.

---

### Post by cabbrick1243 on 2011-08-09
> **SoFl W said:**
> When they bring back Leisure Suit Larry let me know.

I'm not familiar with that game. If you're referring to a game that was once in Ubuntu I can try and find it.

---

### Post by SoFl W on 2011-08-09
No.   King's Quest just reminded me of old DOS games from about 20 years ago.  Leisure Suit Larry was an adventure game set in modern times with an adult theme.  The author of King's Quest also designed LSL.

I thought some more "old timers" would comment.

---

### Post by cabbrick1243 on 2011-08-09
> **SoFl W said:**
> No.   King's Quest just reminded me of old DOS games from about 20 years ago.  Leisure Suit Larry was an adventure game set in modern times with an adult theme.  The author of King's Quest also designed LSL.

I thought some more "old timers" would comment.

Oh ok. I do believe that there was one made in 2009 called "Leisure Suit Larry: Box Office Bust"

---

### Post by dawynn on 2011-11-14
Sorry for joining the party so late.  Yes, I've looked at this game briefly, and even tried to push for it.  Notice that I got it added again to Lucid, but it disappeared again after that. 

Worth noting that the latest version in both the Debian repositories (including Sid) and the Ubuntu repositories is the 2007-03-19 build.  The latest on the main site (See the download link at [http://kqlives.sourceforge.net/](http://kqlives.sourceforge.net/)) is 2009-12-14.  Not sure how much development actually happened in the nearly 3 years in-between.  I have not been able to find pre-built packages for the latest version.

Edit: I stand corrected!

Bug #325263 (started by me) caused another maintainer to build new packages some time ago.  See [https://launchpad.net/~cepeda/+archive/ppa](https://launchpad.net/~cepeda/+archive/ppa).  (According to the bug, these *may* have been the packages loaded to Lucid.  But why wouldn't they change the name to reflect the newer CVS build?)

---

