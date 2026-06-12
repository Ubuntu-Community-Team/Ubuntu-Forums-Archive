---
title: "Exporting Evolution 2.28.3 Calendar to Gmail?"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by blueghoti on 2011-05-25
Hi all - 

After reading through similar articles, I'm still struggling with exporting my Evolution calendar and hoping you can help.

I can't locate an Export option in Evolution, nor can I find the source file on my file system on the assumption I can just import that into Gmail.

Any suggestions for something quick and painless?

Chris

---

### Post by jtarin on 2011-05-25
How are you connecting....IMAP or POP?
Are you synched with online calender?

---

### Post by jtarin on 2011-05-25
[Maybe some help here.]("https://help.ubuntu.com/community/GoogleCalendarWithEvolution")

[Or this....I might try myself.]("http://lifehacker.com/software/google-calendar/geek-to-live--sync-google-calendar-and-gmail-contacts-to-your-desktop-251279.php") :)

---

### Post by jtarin on 2011-05-25
Calendar path:
Quit Evolution. Go to 'user home/.evolution/calendar/local' folder by the Evolution. The calendar file's path would look like the following:

/home/yourname/.evolution/calendar/local/7831150487.204.15@PC/calendar.ics

---

### Post by blueghoti on 2011-05-26
> **jtarin said:**
> How are you connecting....IMAP or POP?
Are you synched with online calender?

Hi!  Thanks...

Hmm - not sure if this helps...

My calendar is local - no connection at all and my email is with a different provider (IMAP connection).  I want to move my services fully to Google and am tacking Calendar and Contacts at this point.

So for the sake of calendar, I'm not synched / connected at all to Google.

Chris

---

### Post by blueghoti on 2011-05-26
> **jtarin said:**
> [Maybe some help here.]("https://help.ubuntu.com/community/GoogleCalendarWithEvolution")

[Or this....I might try myself.]("http://lifehacker.com/software/google-calendar/geek-to-live--sync-google-calendar-and-gmail-contacts-to-your-desktop-251279.php") :)

Thanks!

Both of these solutions seemed to focus on bringing my Google calendar to my desktop - or did I misunderstand?

I want to export my Evolution calendar exclusively to Google and stop using Evolution.


Chris

---

### Post by blueghoti on 2011-05-26
> **jtarin said:**
> Calendar path:
Quit Evolution. Go to 'user home/.evolution/calendar/local' folder by the Evolution. The calendar file's path would look like the following:

/home/yourname/.evolution/calendar/local/7831150487.204.15@PC/calendar.ics


Thanks!  I think I am doing something incorrectly, as I can't find a .evolution directory at all, and I couldn't locate calendar.ics in search.

Do I have a view turned off perhaps, or am I just being really dim?

Chris

---

### Post by jtarin on 2011-05-26
I'm not on my Ubuntu computer but open Nautilus in your /user/home directory (default view) in the Menu....View>Show Hidden Files and Folders. This will make all files and folders prefaced with a dot..as in ".evolution", a hidden file, show.
If you have a Google account already you should be able to set up an IMAP account with evolution and then synch your calender. I haven't done it, but I did have my Gmail calender in evolution at one time and use to update it on my website from in evolution.

---

### Post by blueghoti on 2011-05-31
Thanks guys - I was successful and your help is much appreciated!

---

### Post by jtarin on 2011-05-31
Can you explain how you did it and help others? Please mark this thread as solved.

---

### Post by blueghoti on 2011-05-31
> **jtarin said:**
> Can you explain how you did it and help others? Please mark this thread as solved.

Actually it was through your help :-)

The things that I was missing in particular (which you kindly explained...) were: 

* how to see all my hidden files, thus exposing the correct path for .evolution
* and just simply to upload the .ics file through the Google interface

Mind you, I didn't have any complex formatting or other tags - so for me this worked perfectly.

Thanks again!

Chris

---

### Post by jtarin on 2011-05-31
Thanks and mark as solved please, to help others.

---

