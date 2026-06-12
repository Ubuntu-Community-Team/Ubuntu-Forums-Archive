---
title: "Persistent Network Shares in 8.04"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by tlg on 2008-05-13
I have network storage set up using a Linksys NSLU2 running Unslung firmware. It has two discs attached which are shared on the network using samba. The unit also runs ssh.

I want the discs to be available on Ubuntu PCs under the Places menu and on the File/Save menu in applications. 

To mount the shares in Ubuntu 7.04 I go to Places/Network and browse the Windows network to find the NSLU2 device and open to see the shares. 
Then right click on the required share and select Mount Volume from the menu.

I then get a dialog box which allows me to rename the share if required. 
After this the share is added to the Places list and an icon appears on the Desktop.

Alternatively I can select Places/Connect to Server and select Windows Share or SSH and specify the IP address of the NSLU2 and create a share in a similar way.

So far so good.

However, having upgraded to 8.04 I have noticed a couple of differences.

First there is no dialog to allow renaming the share.

Second, and most critical, the share is not persistent ie it disappears after a restart or logout, both from the Desktop and the Places list.

I understand that significant changes have been made to the way this stuff is implemented in 8.04, but are these changes in the UI made for some good reason, or are they just a inadvertent side effect?

Am I missing something basic here or is there some way to set this up in the same way as works in 7.04?

Thanks in advance for help on this.

---

### Post by TonyS on 2008-05-13
Second the problem, and its not a small issue, especially in a business environment! The PC on my office desk is currently useless due to this.

Be aware that the various documentation floating around about editing FSTAB to mount shares persistently appears to be of no use either... mounting instructions referring to smbfs don't work, as smbfs has been replaced by cifs. And cifs doesn't seem to work properly with Samba shares, creating wierd permissions problems or making drives appear empty.

There appear to be known issues here, relating to the updated file system architecture in Hardy.

There is one putative fix posted if you're brave... see here:-

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

... at the bottom of teh comments is a download for a i386 binary, which simplifies things greatly. I can't personally vouch yet that it works.

This is EXACTLY the kind of bug that will alienate CIOs from Ubuntu... I'm sad to see it has happened in an LTS release, its very bad for the reputation of Ubuntu. I hope we can get it sorted URGENTLY!

Cheers,

Tony

---

### Post by tlg on 2008-05-14
Hi Tony
Glad to see your comments - it's not just me after all!!
Paranoid - moi??
To date I have been running a successful campaign to switch my users to Ubuntu - this sort of glitch is a real pain.

OK I have made some progress.
The answer for me was to create a Bookmark in Nautilus.

The process is simple - just mount the required share to get a Nautilus file browser window open showing the contents of the share.

From the top menu select Bookmark/Add Bookmark.
This will create an entry in the Places menu for the share.

You can right click on the item in the Places menu and rename it.

Thenceforth it will appear in the Places and File/Save-Open menus of applications, and is persistent across sessions for that user.

Each user has to create the Bookmark for their login.

The only small issue remaining is that when the share is accessed, an icon for the share appears on the desktop, and stays there for the rest of the session. Hopefully this will get sorted out in a future update.

Now to get commercial DVDs to play and I can upgrade my fleet to 8.04 which is overall an excellent product (glitches above notwithstanding) - my compliments and eternal thanks to the developers at Canonical and elsewhere.

---

### Post by TonyS on 2008-05-21
I found the solution!

[http://ubuntuforums.org/showthread.php?t=800313](http://ubuntuforums.org/showthread.php?t=800313)

I like linux again.....

T.

---

### Post by TonyS on 2008-05-21
Hiya TLG,

About the DVD issue... I happen to make DVDs professionally, so its a big thing for me.

I tried for ages working through dozens of how-tos without success... then, predictably, found the winner right here in the forums:-

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Worked great for me. Five minutes to complete multimedia happiness.

Tony

---

### Post by tlg on 2008-05-21
Hi Tony
Many thanks on both the network shares and the DVD setup link. 
Like you, I had found the Multimedia How to - a mine of information!!
All is working well on 8.04 now.
Currently working through the fleet here upgrading to Hardy. Going well although I did get caught with the broken plparser10 package in the repository bug which fouled up a couple of network upgrades, but sorted out now.
regards
tlg

---

