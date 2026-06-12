---
title: "What constitutes a &quot;flavor&quot; of Ubuntu"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-06
I have installed XUbuntu 9.04 (Jaunty) I immediately had a list of 200 updates to install also.

My question is:  Is there a list of packages that are included in the release?

(When they talk of "maybe Gimp won't be included", or "Pulse Audio is something new in the install", etc. leads me to believe that I CAN look at a list of the applications included.)

I'm specifically thinking of "aplay", when I look it up I am told that it is part of the AlsaMix Package, but I don't find it in the synaptics; and when I enter it into the terminal, it tells me "No such file" or some message like that.

Thank you.

---

### Post by snowpine on 2010-02-06
Hi Chris, 200 updates is normal (9.04 has been out for almost a year) and here is a list of everything that's included in Xubuntu:

[http://packages.ubuntu.com/jaunty/xubuntu-desktop](http://packages.ubuntu.com/jaunty/xubuntu-desktop)

---

### Post by Chris Edgell on 2010-02-06
Thanks, snowpine,

It's a great page for a general overview.

I was hoping for something a little more specific: instead of saying great art program, say GIMP.

If it says sound: say alsa or pulse...see what I mean?

Still it is as I said a good overview and starting point.

Thanks again

---

### Post by Chris Edgell on 2010-02-06
[http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/](http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/)

Then I looked at this author but I'm afraid of this to-do-list because he says take out your list and put in mine.  That doesn't sound good.

I did have a good page at the Ubuntu Documentation but can't seem to get back to it.

---

### Post by snowpine on 2010-02-06
Don't trust random websites for Ubuntu advice. :)

Lots of good documentation in the official wiki: [https://help.ubuntu.com/](https://help.ubuntu.com/)

Don't edit your /etc/apt/sources.list unless you know exactly what you are doing. The default software sources include 10,000+ applications that you can trust.

---

### Post by Chris Edgell on 2010-02-06
Thank you, snowpine...I needed that advice.

Here's another "poser"...Finally I had been able to find again something I had hit upon and lost by a misc. click.

I got back and began getting into it and immediately came upon this...
compare the written word to the reality in these two screenshots: (the first is just to show you the title of the page: Ubuntu Doc.

On the right of screenshot #2 is what it says is new and great...
and the left side of screenshot #2 is how it really looks and IS really new and GREAT!

---

### Post by louieb on 2010-02-06
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) - may be what your looking for.

> take out your list and put in mine.

Looked at his sources.list - nothing suspicious looking - just the standard with medibuntu, wine, virtual box and some  ppa repositories added.  - It is for Ubuntu v9.04.  

I would not use it - don't think the guy has much sense - :D-  the black background makes me think that.

---

### Post by Chris Edgell on 2010-02-06
Still, when I ask about what steps to take after installing a new "Big Package" 9.04

I ask because I had not anticipated this phase.  Fortunately I have a worked throughg Ubuntu 9.04 whereas THIS install is XUbuntu.  I

First I discovered I had no sound, then when I got to a Ubuntu troubleshooting sound the first step was sidetracked by the fact that it said to put aplay into the terminal, and it said, no such file...I began to look for Alsamixer, I started wondering about all that stuff I'd read about PulseAudio,  I wanted to know WHAT is the sound package that COMES in Xubuntu Jaunty 9.04...I still haven't found that out.

---

### Post by durand on 2010-02-06
Type this into the terminal:
```
which pulseaudio
```
This tells you whether or not pulseaudio is installed. If you get a path, then it is. Otherwise, it's a combination of oss and alsa.

aplay is part of alsa-utils. So if you install that, you should get it.

---

### Post by Chris Edgell on 2010-02-07
I have learned a lot about synaptic and the terminal with all these hours of trying to follow instructions.

Now that I've learned what a grave ` is and found out that the troubleshooting page I was using had printed a 1 instead of an "l".    I have gotten far enough to know that I have a sound card in my computer, well, I guess we knew that. whether it's on the motherboard or a standup, removable,and so more easily replaceable thing, I don't know.  Well, of course I keep hoping one little thing and there will be the sound.  If it's just not working, I don't know.  Wouldn't you think it would have been programmed for sound right out of the box, so to speak.  It didn't have Pulse Audio in the version, and neither did it have the XUbuntu restricted extras which would be required for sound...that's true isn't it?  I'm asking you: Someone please answer me this, Did Jaunty XUbuntu come with SOUND or not...did it have to be TURNED ON?   

Well, tomorrow is another day...and a good one, a fun one, each week at church another little two year old wants to dance with me, with us...AND wave a ribbon baton...I just love it and so do they..  We'll be a dance troupe before you know it.  I enjoy children lots more than I enjoy grown-up Christians, so often.  No comment required, it's a rhetorical statement.
.....................................................................
Well, enough about me, what about you?  How do you like my dress?
Bette Midler in "Beaches"


See ya' later.

---

### Post by NCLI on 2010-02-07
Ideally, sound should "just work." How about trying the latest version, 9.10, from a live cd, to see whether your audio troubles have been fixed?

---

