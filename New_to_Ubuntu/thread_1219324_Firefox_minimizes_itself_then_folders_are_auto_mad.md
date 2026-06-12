---
title: "Firefox minimizes itself then folders are auto made on desktop"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by frimilden on 2009-07-21
So Since the last set of updates a few days ago I am having a very weird issue. I will be browsing the net with firefox then all of the sudden firefox will minimize itself and folders then start to create themselves "untitled folder'. Sometimes only 1 folder other times 10+ Them sometimes instead of folders creating themselves, the trash will open up and en masse like 50+times. Or if I have y second HDD mounted that will open like 10+ times really quick. This is driving me nuts, someone please help

This has been ongoing and will happen at a minimum of 3 times in any 8 hour period sometimes much more. 

I am using Ubuntu 9.04

---

### Post by LewRockwell on 2009-07-21
sounds like someone else is accessing your equipment

you don't give any information about where this is happening?

office, home, coffeeshop?

and your equipment including modems, routers, switches, etc

.

---

### Post by frimilden on 2009-07-21
This is at home. I am behind a router hardwired not wireless (Belkin wiresless G) and have GUFW running. Only thing I have allowed in and out in Gufw is my router addy and it's subs. IE, 192.168.2.1-192.168.2.25. I know this could not be someone I live with as they know nothing of PC's all they know is how to connect to the wireless and use stumbleupon.
I have pretty good router security. I filter by Mac addy, use password and WPA2

This  is random and can happen at anytime. It could be in the next 5 minutes or in the next 3 hours. Could be 8 AM or 8 Pm, etc... there is no rhyme or reason to the crash/problem. But it does happen anytime I am on and regularly. Also the quickess with which the folders are created or the trash/Mounted HDD folders are created or opened is beyond any human possibility of doing it. I mean it will create 25+ folders in a split second. Or open the trash 40 times in less than 1 second, then all I will see is the folders appear like mad one after the other and very, very quickly.

---

### Post by frimilden on 2009-07-22
Bump

No one can help with this one? :confused::(

I would hate to have to do a clean install and loose over 250 gigs of HD movies and so on and so forth.

---

### Post by Durden on 2009-07-22
Install the Xmarks extension so you can upload your bookmarks/passwords/history etc to their servers as a backup and then sync them back when you've done what I'm about to suggest.

Then once you backed them up, type "mv .mozilla .mozilla.backup" in a terminal while in your home directory.

This will force Firefox to create a new directory and thus set you back to the defaults. Install Xmarks again if need be and restore your settings from the server.

If this solves the problem then you can "rm -rf .mozilla.backup" and be happy. If not let us know here and we'll see what we can do.

Additionally, the Xmarks setting is optional. If you don't care about history/passwords/bookmarks etc then don't bother with it. You can just export your bookmarks and import them back without the xmarks stuff. I just like Xmarks because I sync between 5 different computers.

---

