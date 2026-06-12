---
title: "standard application setting won't stick"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by bennypr0fane on 2011-07-23
Hi,
I installed totem video player and ever since all mp3 are automatically opened by totem. I went into settings > standard applications > multimedia and set Rhythmbox as the default player, but when I open an audio file, it's still totem. How can I fix this?
Thanks Ben

---

### Post by relay_man on 2011-07-23
In 10.04 I believe there is another location where this preference may need to be set.  It is at System > Preferences > Preferred Applications under the Multimedia tab.

---

### Post by bennypr0fane on 2011-07-23
That is the the place where I made the setting, I just translated it to English with different terms since my system is in German.
However this setting is not taking effect!

---

### Post by relay_man on 2011-07-23
O.K.

The next place to look is at the desktop.

Places > Music > Edit > Preferences

Look under the Media tab

I changed my setting from Rhythmbox to Brasero and tested.
When I inserted a CD, a disc copy utility opened instead of Rhythmbox.
It appears that this setting has priority over the setting in Preferred
Applications.

Hope this helps

---

### Post by bennypr0fane on 2011-07-24
This is still not working, I hope I didn't get confused again with the german/english terms for the UI. See attached screenshots of what I did:
1. "Musik - Datei-browser-1"
2. "Einstellungen zur Verwaltung..."

So, these are the settings for what Ubuntu should do when a data storage device ("media") is connected, yes? I set everything audio-related to Rhythmbox, but how does that affect handling of filetypes? In fact, .mp3s are still opened with video player.

Then I tried something else, see these screenshots:

3. "Musik - Datei-browser-2"
4. "Öffnen mit"

I checked the box that says "remember this app for this filetype", but it's still not sticking! Still Videoplayer! :confused:

---

### Post by no2498 on 2011-07-24
in your music folder right click open with what ever program you like

hope this helps

you can also do it in the down load folder open it then right click

---

### Post by bennypr0fane on 2011-07-24
> in your music folder right click open with what ever program you like

I already did what you said, as you can see on the screenshots included in my above post.
I **can** open mp3 files with my preferred program (Rhythmbox) alright, but I want that program to be the **default** application for playing mp3 - this is the part that is not working.

---

### Post by relay_man on 2011-07-30
Hello Benny

Got your PM and that is O.K. , no worries.

Give me some time to look at this more. 

I'll be back as soon as I find something.

Chin up!  :D

---

### Post by relay_man on 2011-07-30
Benny  
 
 I looked through your screen shots and I believe you have set 

correctly the screen at.

Places > Music > Edit > Preferences > Media tab

But I did not see a screen shot for:

System > Preferences > Preferred Applications (under the Multimedia tab)


I've included a screen shot of mine below

---

### Post by bennypr0fane on 2011-08-01
> **relay_man said:**
> Benny  
 
But I did not see a screen shot for:

System > Preferences > Preferred Applications (under the Multimedia tab)

I forgot to make a screenshot of that setting, but it's already in place right there - that's the first thing I tried even before posting here, :(
I guess this is how you're supposed to do it if you want to set the standard application for anything, but I'm guessing it must be a bug, because the system is obviously not doing what I told it to.
The question is, how can I diagnose what's causing the bug and fix it?

---

### Post by CatKiller on 2011-08-01
Right-click on a file & select Properties. Go to the Open With tab. Select Rhythmbox in the list.

---

### Post by bennypr0fane on 2011-08-04
> **CatKiller said:**
> Right-click on a file & select Properties. Go to the Open With tab. Select Rhythmbox in the list.
OMG, That was it! Dude, you made my day! I just love it when things can be fixed :D
Thanks!

---

