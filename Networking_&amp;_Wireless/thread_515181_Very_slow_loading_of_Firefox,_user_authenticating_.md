---
title: "Very slow loading of Firefox, user authenticating via NIS and home dir mounted on NFS"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by danielfarley on 2007-08-01
Very slow loading of Firefox, for  user authenticating via NIS and home dir mounted on NFS.

Server is a Fedora 4 box, and just looking at upgrading the clients to Ubuntu 7.04

Any idea's as to what could be causing this to happen??

Daniel

---

### Post by danielfarley on 2007-08-01
Just tryed installing galeon as well same isuew with it.. this is quite randem.. open office and the games load ok.. its like it is "just web browers"

Daniel

---

### Post by tvreeland on 2007-08-07
Not sure if I'm having the same problem so I wanted to check before starting a new thread...

I work at a school trying to get rid of Win2k & XP machines and use Ubuntu workstations.  Our servers are all running BSD.  After jumping through a few hoops today, I got a Feisty workstation to authenticate through NIS and mount NFS as /home.

The problem is that now my Firefox won't open at all!  It appears to be loading on the App Panel at the bottom of the screen, but then just disappears appx 30 sec later.

If I log in using the one local account that I created at install (I moved ~ out of /home so it isn't overwritten by NFS) everything works fine.  Firefox comes right up and zips along the web.

My first thoughts were that there was trouble creating the necessary files in ~/.mozilla.  However, it appears that all the correct files exist there.  I also started looking through the file all.js to see if anything there struck me as an option.

It seems that all read/write access to the mounted /home directories is horribly slow!  OpenOffice files also seem to take a long time to open and close.  Not sure if this is related or not.

Anyone have any success with this or even an idea to try?

Thanks!

---

### Post by tvreeland on 2007-08-07
Again, I'm not sure if the 'slow loading' you're talking about is the same as my failure to load but ...

I did a bit of research at the Firefox site, still focusing on the ~/.mozilla directory.  Playing around at home on my Ubuntu box that's just on a home network I changed the ownership of my ~/.mozilla directory to root:root.  The result is the _same exact_ symptoms that I get on the networked machines at work...that makes me think that there are some files or directories inside ~/.mozilla that have the wrong owner.  The actually .mozilla directory had the correct owner but I didn't look inside.

I'll check in on that at work and come back here to post my findings.

---

### Post by danielfarley on 2007-08-08
For me, it does load in the end and all works fine once loaded, i have removed the .mozilla dir incase there was anything in there that was stuffing it up (as firefox recreates all the info need in that dir on startup if its not there).  And that changed nothing.


Daniel

---

### Post by tvreeland on 2007-08-10
The permissions all seemed to check out fine for me :(

I wonder if it has to do with slow file access over the network share?  Perhaps your delay is due to that and my inability to get into Firefox at all is due to a time-out?   ::grumble::

---

### Post by danielfarley on 2007-08-12
Other stuff reqireing IO over the network seems fine. here ](*,)](*,)

---

### Post by morrislaw on 2007-08-14
Dear all,

I am new to Ubuntu.  The same thing happens to NIS users in our PC running Fedora 7 and Firefox 2.0.0.5.  I think that the kernel is rather the same.  Hope to solve the problem quickly.  It appears that Firefox, OpenOffice suffered the same problem with NIS users in Ubuntu and Fedora 7.

Best Regards,

Morris Law

---

### Post by Jaguar0616 on 2007-08-19
I have exactly the same problem: On a nis/nfs client/server network running Feisty clients and Fedora Core 4 servers, there are long delays using firefox, abiword, and openoffice. Using strace, you can find the problem is with system calls like:

**fcntl64(6, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}**

Where the programs are pausing for exactly 30 seconds on each call to fcntl64.


First I tried updating the servers to Feisty, thus running the same software everywhere and the same behavior persisted..

Then I switched a client over to Fedora 7 and, with the Fedora client/Feisty server setup, the problem went away.

Seeing as:
1) A smoothly running nis/nfs network is non-negotiable for me
2) I don't know enough about the fnctl64 call to go any further
and
3) I don't have time to research it :confused:
4) on Fedora this Just Works

It seems my fix is going back to Fedora.

Ah well, in 6 months with Ubunutu I've gotten the most definite impression their goal is to become the Windows of Linux, i.e. owning the desktop everywhere but not necessarily being a great server OS.

---

### Post by tvreeland on 2007-08-19
I've come to believe, based on other things I've read, that this is a problem with the kernel and/or modules specifically compiled for Ubuntu 7.04.  Seems 6.x versions didn't have this problem...so...perhaps somebody with the understanding and skill can figure out where the problem is and fix it.  I'm too new to all this to have any real shot at troubleshooting it!

---

### Post by danielfarley on 2007-08-22
This may help i am yet to try.


[http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/109811/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dfcntl64%2Bnis%2Bnfs%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3Dt4h%26sa%3DG](http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/109811/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dfcntl64%2Bnis%2Bnfs%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3Dt4h%26sa%3DG)

Daniel

---

### Post by tvreeland on 2007-08-22
:(   I got so frustrated with this, due to the fact that our school opens in a couple of days, that I decided to try using PC-BSD instead.  This was because all our servers are BSD machines and I thought it should go off better.  I just removed Ubuntu off my test machine today!! :(

Perhaps I'll go back and try it all again with this command added to /etc/fstab and see if it works.  I'd be interested in hearing about your success with it as well!

---

### Post by danielfarley on 2007-08-22
Fixed the problem by using this in the fstab for the nfs mount

server:/home       /home   nfs      nolock 0 0

I couldn't used: 

server name: /serverdir /mountpoint NFS rw, rsize=8192, wsize=8192, nolock 0 0 

didn't seem to like multipull options with the (,) separating it ??  

But the problems solved now :)

Hope this helps you guys as well.

Daniel

---

### Post by moonpup on 2007-08-22
try removing the spaces between the options on the nfs mount. i know when using automounter and nfs mounts, that having spaces between the mount options will give errors or undesired results.

server name: /serverdir /mountpoint NFS rw,rsize=8192,wsize=8192,nolock 0 0

---

### Post by tvreeland on 2007-08-22
Wow!  Excellent!  Now I guess I HAVE to go back and install Feisty...  I can't believe you found that!  In German, no less!  Well done.

---

### Post by gate on 2007-08-29
I had the same problem, but my solution was significantly easier. 
   turned out that not all nfs packages are installed by default as they seem to have been with 6.10.
   apt-get install nfs-common
or
   apt-get install nfs-client

  Fixed it for me.

  I was running a large domain of 7,04 PCs connecting to Debian Etch NFS/LDAP servers, symtoms were extreemly slow load times for most applications, especially FireFox and Open Office.

---

### Post by tvreeland on 2007-08-29
Aye. I had seen that posted elsewhere.  However, it didn't work for me.

I guess trying to install the additional packages is a first step and if that doesn't work, adding the nolock option to fstab is the second option.

---

### Post by larocha on 2007-10-19
I have this problem too.

I've tried to solve it, changing ethernet cables, upgrading and downgrading kernel packages, switching from NFS to Samba, swtching from NFS-user-space to NFS-kernel-space. Nothing worked.

My next try will be to use another ethernet card.

Has anybody found a solution or circunvent to this bug?

Perhaps Upgrade/Downgrade/Remove/Install any package?


Thanks a lot in advance.

---

### Post by tvreeland on 2007-10-19
Adding the NOLOCK option to the /etc/fstab file mount options did the trick for me (and I believe for several other people).  Are you saying these last few post's tricks didn't help fix the problem?

---

### Post by larocha on 2007-10-19
Yes, I've used the nolock option since the very begining.

I've also tried using samba but it failed too.

I suspect the ethernet card module in kernel is failing with medium/heavy transfers, so I will try a PCI ethernet card. (Mine is embedded in motherboard)

Kernel 2.6.20 works better for me than 2.6.22, but not completly fine.

FYI:
I'm using gutsy in the client and feisty in the server.

I do some other tests and post my results.

Thank your for any advice you can give me.

---

### Post by larocha on 2007-10-21
I've found a solution to the problem, -not the better solution, but it works for me-.

I've changed the kernel to Debian Etch linux-kernel-2.6-18.

Now everything works fine: firefox, amarok, mplayer...

:)

---

