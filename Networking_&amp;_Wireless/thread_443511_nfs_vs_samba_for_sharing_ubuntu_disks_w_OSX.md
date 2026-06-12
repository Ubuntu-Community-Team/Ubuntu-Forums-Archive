---
title: "nfs vs samba for sharing ubuntu disks w/ OSX"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by sgg on 2007-05-14
I have here 6 OSX boxes that need rw access to external drives
connected to an ubuntu 6.06 server.

I'm in the process of trying to get nfs working for this purpose.
However I'm wondering if samba would be faster or more convenient.
Anyone have experience with this type of setup?

Also, I'm having trouble connecting to the server from the OSX stations.
I use "connect to server" under the "go" menue, 
I type the address "nfs://xxx.xxx.xxx.xxx/media/apollo1"

and I get 'Could not connect to server, because the name or password is not correct."

In my exports, I have specified an ip range as follows:

/media/apollo1 192.168.1.1/24(rw, async)


thanks

---

### Post by kidders on 2007-05-15
Hi there,

My instinct would be to say that Samba would be slower and *less* convenient. When you think about it, you would be opting for a filesharing protocol native to neither platform, when you have one alternative native to both (ie NFS) and another native to one of them (ie AFP).

For me, the most irritating side-effects of using Samba with Linux & OSX would be:[LIST]
[*]Having to contend with crappy permissions mappings to and from a third party schema, even though both the OSs are completely intercompatible.
[*]Putting up with pointless Microsoft limitations, such as file naming restrictions that would cause filenames that are perfectly legal on both OSs to appear garbled.[/LIST]That's just _my_ personal opinion, however ... I'm the sort of person that cringes when I see my father emailing himself something (via London, Washington & back again), when the computer he wants to copy his files to is at the other side of the room!

The issue you will encounter when using things like NFS and AFP is that, since you'd be working with protocols that were actually designed for the systems you'd be using them on, you'd have to follow the rules. For instance, file ownership over NFS works identically to the way local filesystems handle it (ie using UIDs and GIDs). Consequently, you would need to enforce at least partial consistency between the two platforms for file sharing to work effectively. (This may be what's causing your access difficulties.)

Briefly, a file on a MacOS box owned by user 501 will appear on a Linux box to be owned by user 501, just as if you had taken the hard disk out of the MacOS box and plugged it into the Linux one. The "correct" way of enforcing user & group ID consistency across multiple systems is by centralising your user database (eg with LDAP, which OSX has very neat support for). While centralised authentication has major advantages, whether doing something like that is worthwhile would be up to you. In the short term, I would suggest doing something like this, just to make certain I'm diagnosing your problem correctly...[LIST=1]
[*]Create a temporary user account on a Mac box, being careful to manually specify a UID of, say, 1099. Be sure to set a password, etc. (so the account is actually usable).
[*]Create an identical account on a Linux box. Since (as per usual with Linux & OSX) the UIDs are the important thing, both usernames *can* be different ... but that would just be confusing, imo.
[*]Share something safe (like /Users or /home), and see if your test accounts can log into each others' NFS shares & poke around.[/LIST]If all goes to plan, you should see both accounts (which, in practice, would belong to the same person) interacting seamlessly with one another, without any intermediate mapping.

I hope that helps a little. Sorry for rambling!

**Edit:** I forgot to mention something important. NFS & Samba aren't strictly comparable, in that Samba replicates an entire suite of protocols, designed to handle naming, service discovery, and a host of other things, as well as file sharing. NFS, on the other hand, is basically just a file sharing protocol. Calling it glorified FTP would be a bit cruel, but it's closer to the truth than saying it's like Samba.

Anyhow, the point is that you may prefer to opt for AFP, over either of the other two options. The biggest gain would be mDNS (Bonjour) integration, so that service discovery would be nice and neat ... although there would be other (probably less significant) advantages too. You would (obviously) be giving up Linux -> Linux nativeness though.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by sgg on 2007-05-16
Thanks for this info.

I now have the linux shares mounted on the osx boxes. NFS Manager on osx came in quite handy for that.

The latest issue I'm facing is with the file permissions.  I have a room full of osx boxes each
with a different username and password. From your post, I gather that i can use LDAP to manage this.
Any info on setting this up for this up would be helpful at this stage.

Thx

---

### Post by kidders on 2007-05-16
Exactly where to start depends on whether you want a Linux box or a MacOS box to be the LDAP server. They should both be perfectly intercompatible, so it's a question of personal preference, really. I would suggest reading up on OpenLDAP ... in my experience, LDAP server configuration can be a bit finicky. Once you get it right, it's useful for all sorts of things though. :-)

Two quick notes:[LIST]
[*]LDAP isn't the *only* option ... it just happens to be one I'm familiar with. You might like to take a look around for other possibilities.
[*]Don't forget that usernames are only half the story ... UIDs & GIDs also need attention, so you don't wind up with a situation where files owned by sgg on one PC get mapped to kidders on another one.[/LIST]Ideally, what you'd finish up with is a scenario where individual users use the same username & password to log into any computer (or NFS share) set up to authenticate against LDAP (or whatever you pick), and have consistent file ownership across the entire network.

---

### Post by sgg on 2007-05-16
I have a JBOD attached to an ubuntu 6.06 server and 6 osx clients.
The drives on the jbod ext3. I wish to avoid using openldap if possible.

Is there an option for mounting or exporting these disks which
will universally open the disk's permissions allowing osx users
to access the disks without having to alter any permission settings
on the client? I think that I'm looking for something similar
to the umask=002 option I would use under ntfs disks.

thx

---

### Post by sgg on 2007-05-18
FIXED

The answer is as follows:

I set my share folder and it's parent folder to the desired owner and group.

Realizing that NFS wants UID and GID numbers, I went to each osx station,
Using utilities > netinfomanager, I changed each machines main user's
GID to match the group number from my linux group.
Reboot.

---

### Post by kidders on 2007-05-18
Sorry it's taken me so long to reply!

Without centralised authentication, that's what you end up having to do alright. Depending on how many computers you have, the manual approach may work out easier than setting it all up. :-)

---

