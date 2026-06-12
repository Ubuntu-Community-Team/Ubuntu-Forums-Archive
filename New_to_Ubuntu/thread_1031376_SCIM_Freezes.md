---
title: "SCIM Freezes"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by azathrael on 2009-01-05
I posted this in the general help thread and I've had no response from anyone for the past THREE WEEKS.  I'm tired of waiting so I'm going to post in this section of the forums to see if I'll have any better luck.

I was trying to activate my laptop's built-in mic when all of a sudden, for a reason I can't even begin to guess, the process SCIM-launcher or SCIM-bridge starts eating up my CPU and crashes any program that utilizes SCIM (ie. Firefox, Open Office, Tomboy Notes, etc).

I had to uninstall SCIM and I am now operating Ubuntu with no other language input methods.  I use Korean and Japanese on a regular basis and I have urgent need for both languages.

Complete removal and reinstallation of SCIM has not solved the problem.

Anyone know what's wrong with my SCIM?

My computer specs:

Toshiba Satellite X205-SLi5
Intel Core2Duo T8300
Nvidia SLi GeForce 8600M GT
2x160GB HDD

Any help would be appreciated.

---

### Post by azathrael on 2009-01-08
Bump

---

### Post by azathrael on 2009-01-08
To people who might have the same problem as me, this is for your reference:

What I did was first uninstall everything. Restart.

Then go to Places -> Home Folder (Your username) -> ctrl + H (Shows hidden files) -> Look for foreign language folders such as .anthy or .pinyin or whatever, delete those folders.  Look for .xinput.d and delete all files in that folder.

Reinstall everything and restart.

Something must have been messed up in one of those folders because this fixed all problems.

GG me.

---

