---
title: "Lubuntu, no wifi showing up"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by alex236 on 2014-08-13
When I use the nm-applet, I don't see ANY wifi networks. If I were to look in Windows XP, I would see many and would easily be able to connect. On my new Lubuntu desktop, I can't seem to do so? How do I connect to my WiFi network? A screenshot is below.

([http://oi60.tinypic.com/2qlfrqc.jpg](http://oi60.tinypic.com/2qlfrqc.jpg))

---

### Post by Rex Bouwense on 2014-08-13
Have you enabled Wireless and networking?  Right click the nm-applet.

---

### Post by alex236 on 2014-08-14
How do I enable it?

---

### Post by mörgæs on 2014-08-14
I have moved your post to Networking. Please read the sticky notes.

---

### Post by alex236 on 2014-08-16
> **mörgæs said:**
> I have moved your post to Networking. Please read the sticky notes.

Please watch the video below. I made it and it fully explains my problem. There are 3 links below. All of them are the same video, but, some may not play depending on your browser.

1) [http://tinypic.com/r/34h9iq1/8](http://tinypic.com/r/34h9iq1/8)

2) [http://www.filesnack.com/files/cdzps176](http://www.filesnack.com/files/cdzps176)

3) [https://vid.me/oky](https://vid.me/oky)

Thanks so much! You have no idea how much this means to me!! ;)

---

### Post by mörgæs on 2014-08-16
No, the video shows that there is some problem, not the reason for it. 
Again, please read the sticky notes and post the output as directed.

---

### Post by varunendra on 2014-08-17
Being on a limited connection plan and limited time, I wouldn't bother with a video (which probably won't tell us much anyway). I'm sure I'm not alone in having this kind of tendency towards videos (everyone's time is limited, even if the connection plan/speed is not).

Reading the sticky, and posting technical details (if required) as suggested in it, are the best way to seek help.

---

### Post by alex236 on 2014-08-26
Sorry for being rude....

I sincerly apologize. Thank YOU for taking your time to help me. I will try to fix this problem. Have a great day!

---

### Post by christopher9 on 2014-08-26
Did you run the Software Updater after installation?

---

### Post by varunendra on 2014-08-26
> **alex236 said:**
> I read the ones that showed up but they didn't relate to this at all.
One of the _only two_ stickies of this section tells you how to provide relevant info to get help.

> **alex236 said:**
> Where can I find live support to answers on SIMPLY HOW TO CONNECT TO WIFI?!?
[https://webchat.freenode.net/?channels=ubuntu](https://webchat.freenode.net/?channels=ubuntu)

By the way, typing in all caps is considered shouting, and saying "I'm about to leave.." is something nobody cares about - so one is rude the other useless. Support quality here is amazing here if you ask politely, and follow the instructions patiently. Without showing these two qualities, I doubt even paid support can help you.

> **alex236 said:**
> also, how do you enter a command like this?
The same sticky thread also tells that -
> copying and pasting the command below in the terminal (**ctrl+alt+t** opens the **terminal**)...

---

### Post by abraham9 on 2014-09-13
1 Connect your laptop to the internet with the ethernet cable.
2 Open the terminal [COLOR=#000000]* *[/COLOR][B](ctrl+alt+t)
[/B]3 Write this in the terminal:
> [COLOR=#4B4B4B][FONT=Monaco]sudo apt-get update[/FONT][/COLOR]
> [COLOR=#4B4B4B][FONT=Monaco]sudo apt-get --reinstall install bcmwl-kernel-source[/FONT][/COLOR]
Then unplug the cable.

---

### Post by alex236 on 2014-09-22
> **varunendra said:**
> One of the _only two_ stickies of this section tells you how to provide relevant info to get help.


[https://webchat.freenode.net/?channels=ubuntu](https://webchat.freenode.net/?channels=ubuntu)

By the way, typing in all caps is considered shouting, and saying "I'm about to leave.." is something nobody cares about - so one is rude the other useless. Support quality here is amazing here if you ask politely, and follow the instructions patiently. Without showing these two qualities, I doubt even paid support can help you.


The same sticky thread also tells that -

I apologize for being rude and impatient. I really wanted to get this to work. So far it has not. I meant to ask how to enter commands that are multiple lines long. I will read the sticky and try to run the software update as suggested by another user above. Thank you for taking your time to respond and help me despite my rudeness. Have a great day and continue to be amazing!

---

### Post by alex236 on 2014-09-22
> **abraham9 said:**
> 1 Connect your laptop to the internet with the ethernet cable.
2 Open the terminal [B](ctrl+alt+t)
[/B]3 Write this in the terminal:


Then unplug the cable.

I'm not sure if I have access to one of those. I will find out and try it. I am not very familiar with those type of things.

---

### Post by varunendra on 2014-09-23
Alex,
It is always good to work with those who are ready to improvise. :)

Regarding this -
> **alex236 said:**
> I meant to ask how to enter commands that are multiple lines long.
..if you are still having problem, I think it would help to post the part(s) of the commands that you are having problem with.

---

