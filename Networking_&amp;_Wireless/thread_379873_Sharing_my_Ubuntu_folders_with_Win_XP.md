---
title: "Sharing my Ubuntu folders with Win XP"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by Sturm on 2007-03-08
Okay; finally got Ubuntu Edgy Eft up and running on an older system (P4 2.8GHz).  I have it, along with two other WinXP machines on a lan through my wireless router.

I'd like the Ubuntu system to be a file server, of sorts, so that the other computers can access its files.  I've been hearing that I need to use SMB (Samba) to do this, but I've only ever seen references to accessing Windows shared folders from with Ubuntu, not the other way 'round.  In fact, I don't seem to have any trouble getting my Ubuntu system to see my Windows systems and their HDDs.

I already have all the files I need on an IDE hard drive (hda1) in that Ubuntu system, on an NTFS partition.  I can see and access this partition from within Ubuntu, but I cannot share it on the network (I get an "access denied" error message).  No big deal, I can just copy everything from that NTFS partition to an ext3 partition and share it.  Once done, however, I have no idea how my WinXP machines on the network can see these shared folders.  Any pointers to some newbie guides or anything?  Thanks!

---
Sturm

---

### Post by Mr. C. on 2007-03-09
I can see my Ubuntu shares just fine from my Windows XP system.  It works both ways.  Search for my recent post regarding SMB shares (it was within the last hour).

Permission denied is probably an indication that ... you guessed it.. the permission are incorrect.

Be sure that the files and directory(ies) you are sharing allow that user to read, and examine, and write if that's what you want.
MrC

---

### Post by Sturm on 2007-03-09
Please be patient with me.  I am almost a complete newbie when it comes to linux.  I am, however, fairly well-versed in Windows networking.  Enough to get me by on my home network and at work, at least.

So, I have been banging my head against the Samba and SWAT wall today.  And boy, is it a solid wall!  Five hours later of browsing various sites, Googling, reading SMB-HOWTOs, SWAT-HOWTOs, editing smb.conf, etc., and I still am no closer to getting it to work.

My Edgy installation is almost out-of-the-box, if that helps any.  I can also post my current smb.conf file if that will help.

I simply cannot "see" any shared folders from my Windows XP boxes under "My Network Places", so I can only assume that Samba isn't work.  This assumption could be wrong, of course, as there may be other ways to access the shared folders from Windows other than through "My Network Places"; I just don't know about them.

As I stated, I have tried for hours to find a simple, step-by-step, layman's terms guide to getting SMB working in Ubuntu and tested, but cannot find one.  Maybe when this is all said and done and *working,* I'll write my own and credit everyone who helped me.  Until then, please help.  Thank you.

---

### Post by Mr. C. on 2007-03-10
No problem - I'll be as patient as you need.

Did you find my recent post helping the other user configure Samba for guest users?  That user posted a smb.conf file, and I gave some corrections and explanations.  It works - I tested it before I posted.

Please look for that post, move your smb.conf file aside, and replace it with the one posted, and include my recommended adjustments.

MrC

---

### Post by Gerard Barberi on 2007-03-10
Try reading here, maybe this will help
[http://samba.netfirms.com/sambconf.htm](http://samba.netfirms.com/sambconf.htm)

---

### Post by Sturm on 2007-03-10
I shall give those a try in a moment...  First of all, I noticed something odd this morning.  While browsing around through the file system, I came across another smb.conf file!  So it seems I have *at least* two, now:  One in /etc/samba and the other in /usr/share/samba.  How can I tell which one is being used by Samba?

---

### Post by Mr. C. on 2007-03-10
/etc/samba/smb.conf.

---

### Post by lenwood on 2007-03-10
There are two tools which may help, Webmin and SWAT.

Webmin is a browser based collection of tools that allow you to administer your system.
[www.Webmin.com](www.Webmin.com)

SWAT is a browser based control for Samba.
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html)

HTH,
Len

---

### Post by Sturm on 2007-03-10
Mr. C, thank you for referring me to your other post.  I was able to use its information to create a new smb.conf file which allows me to finally see the computer from the Windows systems.

Now I just am curious to know, is it normal for a folder to be shared twice?  I have one test folder share, but on the Windows machines, it appears twice under My Network Places.  I can send a screenshot and/or my smb.conf, if this is not normal.

---

### Post by Mr. C. on 2007-03-10
The Network Places icons are like bookmarks.  When something changes in the names of the share, you may have multiple copies.  Simply toss them in the trash, and explore via Workgroup Computers.  They will also expire eventually.

I glad things are working for you now.
MrC

---

### Post by Sturm on 2007-03-11
Yep, that seemed to do it!  Thank you very much, Mr. C!  You've helped me considerably!  If I can ever do anything for you, just let me know!

---

### Post by Mr. C. on 2007-03-11
You're welcome.  Glad to hear everything is working out.

MrC

---

### Post by Sturm on 2007-03-18
Lost it.

I'm afraid I've lost the ability to connect to my Ubuntu shared folders all of a sudden from my Windows systems, but I cannot figure out what I have done wrong recently to cause this.  Shall I post my smb.conf file?

---

### Post by Sturm on 2007-03-19
Now this is odd...  I booted up another Windows XP system that I hadn't run in a while.  When I brought up Windows Explorer and clicked on My Network Places, it saw all of my shared folders on Ubuntu!!  So, I guess there's nothing wrong with my Samba after all.  But here's where things get interesting.

Just as a quick test, I right-clicked on one of the shared folders from within My Network Places and chose "Delete."  I figured this would just delete it from that list, but would be re-detected after refreshing the list.  Not so.

I tried refreshing several times--even rebooting both computers (Windows XP box and Ubuntu box).  That shared folder that I deleted will *not* reappear on the list, even though it *does* still exist on the Ubuntu box and is still listed as being shared.  Why is this happening, and how can I get Windows XP to re-detect this shared folder?  Thanks.

---

### Post by Mr. C. on 2007-03-19
I'll be frank.  Windows File and Print networking stinks.  It is unpredictable, difficult to manage, and frustrates users to no end.  It was not designed for rapid convergence, and user's cannot determine why something is failing.  We all hate that loud THUNK everytime some network share is no longer accessible.

I won't even begin to try to fully describe what is going on and why, as I would end up repeating what's been written over and over (i'm not saying you haven't look or read, just saying it is far too difficult a subject to address properly in a forum response).

But in brief, windows machines try to become the master browser of the network.  Whether they succeed or not depends on other windows machines on the network.  Essentially, they haggle to become king of the domain or workgroup.  When the king dissappears, others have to take over.  But this process can take upwards of 45 minutes!  Its simply poor design.  If you are doing a lot of rebooting, reconfiguring, restarting Samba, you can expect these troubles.

Make the machine that is the most stable, always up, become the master browser.  This will reduce the troubles.

MrC

---

### Post by Sturm on 2007-03-20
Thanks, Mr. C....

I tried your plan of waiting 45 minutes...  Heck, even overnight...  With no success...  Then I discovered the next day that it happens with all Windows machines, as you described, and their shared folders.  Once you delete it off that "My Network Places" list, it's gone for good!   Unless...

I discovered this by just messing around on the Windows machine, once I realized it was not a Linux issue.  Right-click on the "My Network Places" icon (which can be found in Windows Explorer's tree list right under "My Documents" and "My Computer") and choose "Search for Computers..."  This little tip could actually even be handy for other networking problems, apart from Linux altogether.

Anyway, in the Search Results dialog that appears, you can just leave the search input box blank and hit the Search button, which will display all the computers it can detect on the network, including itself.  This allowed me to see the Ubuntu system and all of its shared folders, thankfully.  Once I double-clicked on one of the shared folders in that dialog, it appeared in the "My Network Places" list finally.  I went ahead, though, and right-clicked on each of those shared folders, choosing "Map Network Drive..." to map each of them to a drive letter on that Windows Machine.

So there you have it.  I found the way to "force" Windows to re-detect networked computers and shared folders/files.

---

### Post by Mr. C. on 2007-03-20
Yeah, you basically have it down.

The 45 minutes is a time for shares to be *available*, and this is in more complex environments.  For Network Places, those are semi-permanent.

Network Neighborhood / My Network Places should be thought of as really just a set of "shortcuts", created during auto-discovery or after manual visits.  I never use them.  The are often outdated and useless.  When I travel, I'll have network short cuts from my relative's network still on the system, and they'll stay there sometimes for days, or until I delete them.

You can always access your correctly setup shares via View Workgroup Computers which is below Microsoft Windows Network (shows all groups/domains), or directly via network path.

Just type in \\computername\sharename in any IE's or any Folder's Address bar to get where you're going.

If you want more reliable shares in Network Places, you need to have the most stable system on the net be the Master Browser.  You can configure any system to win the election.

MrC

---

