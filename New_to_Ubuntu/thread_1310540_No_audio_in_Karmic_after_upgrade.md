---
title: "No audio in Karmic after upgrade"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Greanbeens on 2009-11-01
Hi,

I just upgraded to Karmic from Jaunty using the update manager. Everything is fine except i am getting no sound at all.

In sound preferences under the "hardware" tab, nothing is there. 

I am sorry but i don't know what information about my computer set up would be helpful, or even really how to get it, i'll give you what i know, though. 

I am on a laptop, Toshiba Satellite A100. The sound isn't muted in any programs or in the settings. Sorry about the lack of info, this is posted in "Absolute Beginner" for a reason... :-/

I have tried playing saved movie files, using youtube and doing the system sounds test, nothing works. 

I tried the System Testing program in System>Admin, which wanted me to lodge a bug report. A few other people had sound problems, but i don't know if it's the exact same problem because i have no idea what sort of audio hardware i have. So rather than mess things up over there i figured i'd post here first. 

Once again, sorry for the lack of info, if anyone has any tips or a solution that would be awesome. Your patience with the noob is appreciated.

---

### Post by Greanbeens on 2009-11-02
Re-reading my post i realise i'm not giving anyone much to go on, i'm just really not sure what information is needed. Any help at all is appreciated.

---

### Post by gillza on 2009-11-02
Yup. Same here. Have ASUS P5K-V motherboard with onboard Realtek ALC883 audio. Disappeared after the update into thin air...

Here is what I have found:

[http://ubuntuforums.org/showthread.php?t=1289480](http://ubuntuforums.org/showthread.php?t=1289480)

There are a couple of suggestions on how to fix the problem, which I will try as soon as I am home.

@Greanbeens could you read through it and see if anything suggested works for you?

---

### Post by feb3 on 2009-11-02
Huge numbers having same problem so you might want to search for replies on the matter - there are many.
I too had this problem and all I can say is that having searched for a solution it was quicker to do a fresh install and the sound was then OK. 
Have gone back to Jaunty though - not happy with KK at the mo.

---

### Post by Nausser on 2009-11-02
No sound here either. No sound devices show up in the sound prefs. Acer laptop running Ubuntu since Hardy without sound issues. Standard intel onboard.

---

### Post by Greanbeens on 2009-11-02
Thank you guys! I will check out that thread now and see if anything helps. I will post back here soon with any results!

---

### Post by Don1500 on 2009-11-02
I used this how to, even though it says it's for 9.04 IT WORKS!

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

Do what it says and you will have sound.

---

### Post by -=hazard=- on 2009-11-02
I had the same problem after update, and much more problems and definitely I did a fresh install and it's much more better now. Works everything perfectly. I suggest making a fresh install.

---

### Post by Greanbeens on 2009-11-02
Good news, using the code:

sudo alsa force-reload

Fixed the problem for me. I found out that my hardware is: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Thank you to everyone who replied with a tip :)

---

### Post by Greanbeens on 2009-11-03
Just discovered that when i restart my computer, the sound issue comes back. Just thought i'd mention that in case someone else with the same problem reads this thread.

Edit: The same solution works.

Edit: But now youtube and other embedded streaming players are without sound. Music files played from hard drive work fine though. I'm thinking this might be a flash error. In update manager there is a flash update that i cannot mark for download?

---

### Post by Triryche420 on 2009-11-04
I had the same issue... after checking volume control under hardware profile it was set to analog.. changed it to digital and had volume.. hope this helps

---

### Post by Greanbeens on 2009-11-04
> **Triryche420 said:**
> I had the same issue... after checking volume control under hardware profile it was set to analog.. changed it to digital and had volume.. hope this helps

I just checked that and i don't seem to have an option for digital. 

Youtube vids etc are working now, they just started to on their own, how weird! 

Thanks for your help.

---

### Post by gillza on 2009-11-04
I was trying to fix my issue yesterday by removing the ~./pulse folder and restarting the process - did not work.

Found some advices here: 
[http://ubuntuforums.org/showthread.php?t=1308034](http://ubuntuforums.org/showthread.php?t=1308034)

will try it today

---

### Post by gillza on 2009-11-06
Ok... So after trying everything I could think of and tracing the bug to the incorrectly updated Grub (there is a bug launchapad entry out there that traces audio problems to the wrong kernel being loaded by Karmic) and trying to update the menu.lst and other things (which resulted in the system just flickering insanely) I just reinstalled Karmic from the scratch. Everything works now... 
Never had such problems before, a little disappointing now (in myself for not being able to solve it)

---

