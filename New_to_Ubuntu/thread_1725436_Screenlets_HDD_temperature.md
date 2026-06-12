---
title: "Screenlets HDD temperature"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by D4J0K3R on 2011-04-09
Hi,

I've installed the screenlets manager from the UbuntuSoftwareCenter.
I use "meter".
I have 2 problems.
The text is often too long to fit in the square, I know I can remove the text but I was wondering if I could modify the text.
The second thing is, I don't have the option to show my HDDs temperature.
If I type $ sudo hddtemp /dev/sdX in the terminal it will show me the temp, but I would like to have it on my desktop permanently.
Any help would be appreciated.

Thank you!

---

### Post by taseedorf on 2011-04-09
I use gnome sensors.... that can show hdd temp.

Or try out gnome-look.org for better screenlets, etc... you might find something you'll like

As far as the text, everything is written within a config file that is usually fairly easy to edit if you know any programming....sometimes.  If you do, edit the screenlets configuration file if you can find it.... otherwise, I don't use that screenlet program so I have no clue.

---

### Post by D4J0K3R on 2011-04-09
I've tried Gdesklets because it looks better from my opinion, but I can't even start the software!
I've googled the problem & it seems that Gdesklets wants to use python 2.5 & I have 2.6.
I don't understand how to solve the problem, but it seems the problem has been there for a couple of years.
I don't understand how this was never fixed...

Thank you taseedorf!

---

### Post by GrouchyGaijin on 2011-04-09
I use im sensors and have the output piped into conky.

---

### Post by D4J0K3R on 2011-04-09
Wow, Conky seems to be pretty awesome.
I'm a n00b with Linux so I'll have a lot of reading to do.

Thank you GrouchyGaijin!

---

### Post by GrouchyGaijin on 2011-04-10
> **D4J0K3R said:**
> Wow, Conky seems to be pretty awesome.
I'm a n00b with Linux so I'll have a lot of reading to do.

Thank you GrouchyGaijin!

It is pretty cool.  You can get it in the repos.  Get the conky-all version and check the forum for help.  It looks intimidating but it's really not that hard.

---

### Post by D4J0K3R on 2011-04-10
I beg to differ sir.
It's not that easy to understand how it works...
I have intermediate knowledge in HTML & basically no knowledge with the commands of Linux / Ubuntu in the terminal.
Where should I start to understand how to modify the .conkyrc to my liking?
I have an ambitious project for Conky so I would like to understand _everything_.
I've attached an image of what I want to do. (yikes!)
It might not be the final version, it's only a concept.
So where should I begin, because I can't find an easy tutorial.
Most of them starts you with, copy-paste this (yeah well, what all of these things means?).
Basically a Conky for dummies is for me, but I guess I need to learn some language before starting?

Thank you!

---

### Post by GrouchyGaijin on 2011-04-10
> **D4J0K3R said:**
> I beg to differ sir.

I've attached an image of what I want to do. (yikes!)

Basically a Conky for dummies is for me, but I guess I need to learn some language before starting?

Thank you!

First, don't call me sir.  I'm as good as you are.:D


Join this thread: [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+screenshots]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+screenshots")

and check out [The New Conky Pitstop]("http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page")

I don't know any programming languages, but like you have a decent handle on html.  You don't need to with conky.  Check out that thread and website.

If you need help please send me a private message.

OK I just saw the attached image.  This looks like a job for Lua.  Lua does rings nicely.  The guy you want to talk to is mrpeachy.  Send him a message and tell him what you want to do.  He is a true guru (plus a nice guy.)

---

### Post by D4J0K3R on 2011-04-10
Domo arigato gozaimashita!

---

