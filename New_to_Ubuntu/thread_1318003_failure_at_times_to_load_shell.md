---
title: "failure at times to load shell"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by captain granite on 2009-11-07
Hello Ubuntu users,
                               I have been running Ubuntu 6.4 with little problems, I have now updated to 6.10, lovely system but I have problems at boot, Its haphazard to say the least, unable to load shell is a message I get and your CPU has changed change settings in bios.
It displays a date Wed 1st January 2003 which it reverts back to. On the occasional successful boot the time on the screen is 2003 but it corrects when the internet kicks in to the present correct time and date.
Is this a bug or as a person suggested could it be the little motherboard battery going dead and not remembering the bios detail and re setting every time.

I am a relative Linux beginner who thinks the system is amazing.

                        Captain G

---

### Post by jrothwell97 on 2009-11-07
Please clarify: are you using Ubuntu 6.10 or 9.10?

---

### Post by jasonab on 2009-11-07
Your computer has a little battery in called a CMOS battery (usually the CR2032). The function of the battery is to power the nonvolatile Bios memory and in doing so keep your cmos settings in the event of a power failure. After a few years the battery goes flat and each time you power off your computer it will loose the CMOS settings and disconnedt the power. When the computer boots up the bios reads the cmos settings for instructions. if there are no settings it uses the default BIOS settings. One of these settings is the time. So your computer has lost the settings and is using the default time from the bios, that is 1 January 2003 for your BIOS.

Your OS (ubuntu) will attempt to synchronize it's time with a time server some where on the internet using network time protocol. If it can successfully contact a NTP server it updates the time on your computer based on the time zone you specified when you installed the OS.

What you need to do is replace the CMOS battery. The last time I bought one it cost me about US$1. The process is very simple. Just remove the side panel of your pc, look for a round silver thing and read the information off of it and take it to any pc store or sometimes you'll be able to get it at a watch maker store. Ussually the the battery is a CR-2032.

[How to replace a CMOS battery]("http://www.smartcomputing.com/editorial/article.asp?article=articles/2004/w1510/32w10/32w10.asp")

To get the shell working again, once you've replaced the battery you'll need to set all the settings in the BIOS again. Consult your motherboard manual if you still have it.

---

### Post by captain granite on 2009-11-07
Jasonab
              You were absolutely spot on with your diagnosis, it looks like problem solved, I robbed a spare machine I have under the bench and just for the hell of it tested the old battery, 00000volts  Thanks
                               Captain G :D

Solved, thanks very much

---

