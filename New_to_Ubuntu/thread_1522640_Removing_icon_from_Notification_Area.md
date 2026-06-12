---
title: "Removing icon from Notification Area"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-07-02
Whenever I run TweetDeck, the notification area at the top of the screen 'helpfully' adds a TweetDeck icon with an annoying white background to tell me that the program is running.

As I've set TweetDeck to begin at startup this icon is totally irrelevant, and just bugs me because of the white border on an otherwise black toolbar.

There's nothing in TweetDeck's settings that lets me adjust this, but is there some console command or other method I can use to stop this icon from appearing in the notification area?  It doesn't display icons for every running program, so surely this must be possible.  If it's not possible to remove it, I would like to at least replace the white-bordered icon with the regular launcher icon (seen on the right-hand side of my screenshot).

(Note: TweetDeck is an Adobe AIR application. This may have something to do with it.)

---

### Post by weezalxc on 2010-07-02
I have the same issue, and I can't find any solutions as well.  I've tried to google for solutions, but it seems like no one is working on this issue since the notification system is going away in the next release.  I have also attached a screenshot as well.

---

### Post by danielgrosvenor on 2010-07-02
They're losing the notification area in the next release?  To be honest, I only keep it because it seems tied to the WiFi icon for some stupid reason (and devs reading this: please make all those battery/volume/WiFi/email icons *separate* in next release).

Will wait for the next release in that case.  Look forward to seeing what changes have been made. :)

---

### Post by myusuf3 on 2010-07-28
this is so annoying. I was reading somewhere else this guy managed to get rid of it on accident, and he is complaining LOL. :o

---

### Post by aeiah on 2010-07-28
i dont know about getting rid of it, but it should be pretty straight forward to replace the icon. have you done a filesystem search?

it might be in /usr/share/pixmaps


although ive got a notification area on my laptop, i cant stand it on my desktop. serves no purpose at all and i always get rid of it straight away. but then i dont like having the power button or me bar either

---

### Post by mcduck on 2010-07-28
There's no other way to remove a program's icon from the notification area than through that program's settings. The program that creates an icon there is the one that's responsible of the icon. 

You could probably hide it by changing the icon image to transparent one, but that might leave a gap between notification icons depending on which order they get loaded, as the icon would still be there, only invisible.

Apart from that, you'll just have to ask for the program's developer(s) to make the icon optional. Although they probably should just remove it if it's not actually notifying you from anything or even providing any  useful functionality. The notification area isn't supposed to be used to show what programs are running...

---

### Post by nickolasemp on 2010-08-26
I have Google Desktop and I don't want to show the whole world that it is on and anybody can search with a few buttons my desktop computer... :-x](*,)

---

### Post by isakk on 2010-09-25
I can help with removing the TweetDeck notification icon

$: sudo mv /opt/TweetDeck/share/icons/TweetDeck_128.png /opt/TweetDeck/share/icons/TweetDeck_128_bak.png 

This does the trick, but might break something that I'm not aware of.

---

