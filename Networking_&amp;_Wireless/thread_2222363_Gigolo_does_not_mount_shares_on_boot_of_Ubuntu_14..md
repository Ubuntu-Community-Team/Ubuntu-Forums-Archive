---
title: "Gigolo does not mount shares on boot of Ubuntu 14.04"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by paul1945 on 2014-05-06
I presume this is a problem that arises from my lack of knowledge.
I start Gigolo in startup as "gigolo -a"
Gigolo starts fine and in the background but does not mount the shares.
When I either bring Gigolo up manually or in startup as just "gigolo"
it mounts the shares no problems.
I was able to automate this in Ubuntu 13.10 without problems,
but cannot figure out here what is going awry.
Any help would be appreciated.
Thanks, Paul.

---

### Post by johnnyis on 2014-05-10
Not sure if this will help. I just upgraded to 14.04 and had to do a bit of fiddling to get gigolo back to working as normal.
I have always had Gigolo set as a startup program, using the built-in "Startup Applications" program, I added it with name Gigolo, command /usr/bin/gigolo
This starts it just fine on each startup. 
I didn't have to make any changed to settings within Gigolo to get it working in 14.04, it continued to start and connect to shares same as always for me, however, I have shortcuts in my filesystem set to each of my shares, and these were broken in 14.04.
The reason for this was that where previously gigolo was mounting the shares in /run/user/"username"/gvfs/smb-share.... they are now mounted in /run/user/"usernumber"/gvfs/  so, for example my previous path was /run/user/johnny/gvfs/ it is now /run/user/1000/gvfs so I had to create new symbolic links to each share in order to access them within my "Home" directories.

---

### Post by paul1945 on 2014-05-10
> **johnnyis said:**
> I just upgraded to 14.04 and had to do a bit of fiddling to get gigolo back to working as normal.
I have shortcuts in my filesystem set to each of my shares, and these were broken in 14.04.
The reason for this was that where previously gigolo was mounting the shares in /run/user/"username"/gvfs/smb-share.... they are now mounted in /run/user/"usernumber"/gvfs/  so, for example my previous path was /run/user/johnny/gvfs/ it is now /run/user/1000/gvfs so I had to create new symbolic links to each share in order to access them within my "Home" directories.
This is exactly what I found.
In my case the network directory for Ubuntu 13.10 was in /home/paul/.gvfs/ 
In Ubuntu 14.04 the .gvfs directory appears in the same place as before, but it is protected and cannot be entered into and when I tried changing this, it seemed to break things.
So as a beginner I am a bit nervous to play around with this as I do not have the know-how as to how to fix a bad stuffup.
I guess ideally the /home/paul/.gvfs/ directory should represent a symbolic link to /run/user/1000/gvfs/ so that other programs including Gnome Commander will be able to access the network again; but as I said I need the method to get rid of this protected directory and confirmation from someone with a bit more knowledge than myself that this will not break anything.
Thanks, Paul.

---

### Post by paul1945 on 2014-05-16
It appears that with my other modification of the smb.conf Gigolo works OK now.

---

