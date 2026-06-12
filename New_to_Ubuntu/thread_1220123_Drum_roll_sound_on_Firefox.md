---
title: "Drum roll sound on Firefox"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-07-22
I updated my Firefox through Ubuntuzilla yesterday to 3.5.1. 

I get the "drum roll" whenever I delete a message on Yahoo mail. Kinda neat but totally unnecessary :D

Is there a fix for this?

---

### Post by oOarthurOo on 2009-07-22
Haha... no solution in mind, but that is funny as heck.

---

### Post by dnguyen1963 on 2009-07-22
> **emeraldgirl08 said:**
> I updated my Firefox through Ubuntuzilla yesterday to 3.5.1. 

I get the "drum roll" whenever I delete a message on Yahoo mail. Kinda neat but totally unnecessary :D

Is there a fix for this?

I had this "drum roll" happened to me once when I logoff a user and switched to a different user, except that this "drum roll" did not stop until I restarted the computer.  This incident never happened again so I did not report it to the forum.:D

---

### Post by l-x-l on 2009-07-22
FF 3.5.1 does the same thing to me too when I get a new IM from different boards I'm registered. It also does it in any site that I go to that has pop-up messages. Kind of cool but get annoying sometimes.

---

### Post by tsuchang on 2009-07-23
Turn down the sound for now until someone more helpful than me gives you a good solution.

---

### Post by brookie on 2009-07-23
did you try System/Preferences/Sound Sounds Tab (intrepid) and try to mess with the alert sounds. 
btw, any difference with ff 3.5 compared to 3.0.12?

---

### Post by oOarthurOo on 2009-07-23
Ok, I'm done laughing I'll try to be more constructive. First, disable your plugins and restart firefox. If it still does the sound then at least we're sure of the source.

Second, type "about:config" into the address bar. Then, just below it in the search box type sound. There is only one thing I can see and it defaults to true. Apparently it should only be enabled if you've enabled accessibility features for the browser, and it supposedly has an adjustable sound. In any event, set it from true to false, restart firefox and see if it is still there.

I'm out of ideas I think, and a small part of me hopes it doesn't work. :popcorn:

---

### Post by emeraldgirl08 on 2009-07-23
> I'm out of ideas I think, and a small part of me hopes it doesn't work.

Lol. 

Unh unh!

I just got back in from work. I'm also in the middle of configuring a Grub boot that consists of three OS' on a SATA and IDE drive. Yeah for a noob that is enough to keep me busy :D

I'll try out these things and get back to you guys! It's late so if I don't post soon I'll do it in the AM.

---

### Post by emeraldgirl08 on 2009-07-23
> **brookie said:**
> did you try System/Preferences/Sound Sounds Tab (intrepid) and try to mess with the alert sounds. 
btw, any difference with ff 3.5 compared to 3.0.12?

I want to say that it seems faster but it could just be b/c my sis isn't downloading another "cotton pickin" show!

:P

No. I really think it is faster and I like the little "+" sign for instant tabs. I'd say give it a little more time and then update. I just did it on a whim. I really wasn't going to but temptation lead me down this road.

It's not that big a deal so if you can hang on until Karmic comes out- cool :)

---

### Post by peakshysteria on 2009-07-23
I have the sound as well. And I agree, there would be nice to have a fix for this.

---

### Post by copperfish on 2009-07-31
After trawling the net it seems that Windows users are having the same issue.  It's a Firefox 3.5 thing.  Almost irritating enough to make me go back to 3.0x.  I'd love a fix for this.

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=tr&forumId=1&comments_parentId=380140](http://support.mozilla.com/tiki-view_forum_thread.php?locale=tr&forumId=1&comments_parentId=380140)

[http://forums.mozillazine.org/viewtopic.php?f=38&t=1327615&start=15](http://forums.mozillazine.org/viewtopic.php?f=38&t=1327615&start=15)

---

### Post by Lupatrian on 2009-09-05
I have the same drumroll issue and it's driving me nuts. I'm using Swiftfox, and every little alert in gMail drumrolls me. My about:cfg sound set to false didn't stop it. At one point, in trying to stop those alert sounds, I deactivated my sound entirely (accidentally). 

As I was writing this, I wondered if we could just move the sound file (that's an Ubuntu sound) out of the folder, so the browser won't find it when it goes looking for it. I tried it; I'm 99% sure it worked (based on my tests). Interestingly, it also stopped some of the accompanying visual alerts - in gmail, anyway.

Keep in mind that this drumroll alert sound is often used for other Ubuntu system stuff, so it won't be there any longer for that. Aaaaand, you have to access root with priviledges, which is not generally recommended. The file is here:
root>user>share>sounds>ubuntu>stereo>dialog-question.wav

And - use this with EXTREME CAUTION (and forget you know how to do it after this!) - you have to open your file system thusly, via Terminal:
Ubuntu: sudo su nautilus
Kubuntu: sudo su dolphin
which will give you the permissions you need to move the file. I just moved mine from the STEREO directory up a level to the UBUNTU directory, so that I can move it back if needed.

---

### Post by Lupatrian on 2009-09-06
Nope. Upon shut down/restart, the drumroll has returned/gmail. Persistent little sucker!

---

### Post by emeraldgirl08 on 2009-09-25
:D

lol. Still no fix eh??? I've been on Suse and M$ on my desktop lappy for awhile now. I have Ubuntu on my traveling lappy and haven't traveled much lately! So now I'm back on for the moment I sure thought it'd be fixed!

Guess Karmic will take care of that. I also had to reinstall my Jaunty. Accidentally killdisking the wrong drive wiped out my partition tables and I had to reinstall both OS' all day yesterday and part of today.

So I'm back in Jaunty and loving it!!!

---

### Post by houdodu on 2009-12-25
this happens for me too. and it scares the **** out of me when my headphones are on and the music has stopped for a bit. "*CAKKADUNK*"

sound effects are off and muted in the sound prefs.

---

