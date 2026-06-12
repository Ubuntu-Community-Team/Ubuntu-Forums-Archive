---
title: "Wiping out Samba ENTIRELY"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by xtemplarx on 2007-10-23
I had tons of problems with my (primary desktop) Feisty machine's folder sharing via SMB.  I tried everything I could get my hands on to get samba to play nice and share a "public" folder (i.e., no login required by the windows users) from my Feisty box.  Nothing worked.  If it worked at ALL, the user would still have to log in as my user account (only one set up for it... i could have set up other users for this but still, defeats the purpose).  I had pretty much given up.

I upgraded the machine recently to Gutsy and am still working out the kinks but for the most part everything is great and I can't complain.  However, I still have my smb share problem.

I got excited, though, because a small server box I set up with a CLEAN install of gutsy was able to share its public folder right out of the box and it works JUST like I would expect it to, not asking anyone for logins and such.  I was thrilled.  :D  SO, I grabbed the /etc/samba folder from that machine and popped it onto my main desktop machine to replace what was there.  Still no dice (and yes I adjusted the paths to match that machine).  Any time someone tries to connect to my machine, they get the "folder contents could not be displayed" error just trying to get the listing of shares available on the machine.  

THUS... I want to wipe out ALL of my folder sharing bits and pieces on this box since obviously somethin's awry!  If the one machine's doing great, this one should be too.  I'm obviously missing something.  Is there another config file or such other than the smb.conf file that I need to be worried with?

Thanks ahead of time and feel free to ask any questions - I'll do my best to answer them.

---

