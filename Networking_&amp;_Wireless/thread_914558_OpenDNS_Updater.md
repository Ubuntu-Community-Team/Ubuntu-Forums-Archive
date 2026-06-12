---
title: "OpenDNS Updater"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by john8791 on 2008-09-08
Bluej744 made an excellent script to automatically update your dynamic IP with OpenDNS in this post from earlier this year:
[http://ubuntuforums.org/showthread.php?t=693788](http://ubuntuforums.org/showthread.php?t=693788)

I just wanted to post an update to this.  I had to change the URL to updates.opendns.com rather than updates.dnsomatic.com.  Attached is the file with changes made.  Just replace username and password with your info.  Copy to /etc/cron.daily to update every day.

---

### Post by wmgcf on 2008-09-26
nothing like an older post to help you out.

opendns has such an amazingly great service for families. I have seen others ridicule family net monitoring on forums - I wonder if they have children, too? No doubt my kids will be exposed to slime and sleaze in their life, but anything I can do to help keep my home and their minds clean is worth it. Hopefully they will always remember their home as clean and nice.

- I configured my stock verizon router to use their DNS. Our windows and linux PCs are now configured to update our router IP address to opendns for the filtering.

I am a newbie, but based on what i gleaned from many places on these forums:

1. I created a very limited user specifically for this script.
2. In the home folder of this user I created a folder called bin
3. I placed the script in this folder
4. Then I entered the following line onto my /etr/rc.d

sudo -u NAMESCRIPTUSER bash /home/NAMESCRIPTUSER/bin/opendns.sh

this means that root will run the script as the special purpose user on startup.

So, when I restart, I can go to /var/log/messages and see the message "OPEN DNS UPDATED SUCCESSFULLY"

Now, here is where I could use community help. I would like tips or links to:
[LIST]
[*]test for network connection inside the script
[*]how to use cron to run at intervals of x (time)
[*]how to rerun script on a key network connection event - would IP assign be the best one? net activation? ???
[*]how to make my SCRIPTUSER boot only to bash - no graphical apps
[*]what else should I know about this subject?
[/LIST]

---

### Post by darco on 2008-09-27
When I first read this thread I said, "huh, my router already does that. Why do I need this script?"
I then realized that my linksys router runs a 3rd party fw (tomato) that incorporates a script that does this exactly...(plus the link is very old)



tomato firmware.....dont leave home w/o it...
[http://www.linksysinfo.org/forums/forumdisplay.php?f=160](http://www.linksysinfo.org/forums/forumdisplay.php?f=160)

darco

---

