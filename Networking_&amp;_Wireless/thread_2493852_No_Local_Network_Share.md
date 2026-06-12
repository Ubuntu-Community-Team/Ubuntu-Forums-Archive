---
title: "No Local Network Share"
date: 2023-12-27
forum: Networking &amp; Wireless
---

### Post by jbl85 on 2023-12-27
I am running Ubuntu 22.04.3.  I feel like I have tried everything, including the simple instructions found here:

[https://www.techrepublic.com/article/share-directories-lan-from-ubuntu-desktop-22-04/](https://www.techrepublic.com/article/share-directories-lan-from-ubuntu-desktop-22-04/)

Not sure why this is so difficult, and so I must be missing something pretty simple.  I just want to be able to share folders from my Ubuntu machine so that I can see them on my Windows machines, and visa versa.

Any insight is greatly appreciated.  Thank you.

---

### Post by TheFu on 2023-12-27
Look for instructions that don't use the GUI.  The GUI isn't worked reliably in years. This is because MSFT changed things.
You need to find instructions in these forums from Mobius1 that include setting up Samba, editing the smb.conf and installing  avahi and mdns tools or MS-Windows wont allow browsing to shared storage.  Sometimes browsing doesn't work regardless.  [Https://ubuntuforums.org/showthread.php?t=2477510&p=14106261#post14106261](Https://ubuntuforums.org/showthread.php?t=2477510&p=14106261#post14106261)

If you share storage from MS-Windows, you'll need to look for Linux instructions that modify the fstab file and mount the storage using CIFS.  Again, this is thanks to MSFT changing things so that new subsystems are needed which are created by 3 different project teams, if that makes sense.

Hope that helps you understand why it doesn't "just work".  Hard to get 3 teams from 3 different organizations to work tightly together for a single outcome.  This is why just mounting the storage using a CIFS mount and the fstab file is the easiest answer.  Doing that removes 2 of the teams from any involvement.
[https://help.ubuntu.com/community/MountCifsFstab](https://help.ubuntu.com/community/MountCifsFstab) are the Ubuntu Community instructions.  

Be certain to use authentication file method for security.  Also, vers=3 or vers=3.10 will help security and performance for specific MS-Windows versions.  Win7 uses vers=2.1. I don't know about later versions, sorry.  For MS-Win10+ shares, in the /etc/samba/smb.conf file, ensure the [global] section has this line:
```
client max protocol = SMB3
```
That only helps manual mounts, not through the GUI.

---

### Post by jbl85 on 2023-12-28
> **TheFu said:**
> 
If you share storage from MS-Windows, you'll need to look for Linux instructions that modify the fstab file and mount the storage using CIFS.  Again, this is thanks to MSFT changing things so that new subsystems are needed which are created by 3 different project teams, if that makes sense.

Hope that helps you understand why it doesn't "just work".  Hard to get 3 teams from 3 different organizations to work tightly together for a single outcome.  This is why just mounting the storage using a CIFS mount and the fstab file is the easiest answer.  Doing that removes 2 of the teams from any involvement.
[https://help.ubuntu.com/community/MountCifsFstab](https://help.ubuntu.com/community/MountCifsFstab) are the Ubuntu Community instructions.  


Thanks for your insight, and yes, well said on the dynamics of the software industry.  I'll give this a look, with lowered expectations of course :)

---

### Post by TheFu on 2023-12-28
> **jbl85 said:**
> Thanks for your insight, and yes, well said on the dynamics of the software industry.  I'll give this a look, with lowered expectations of course :)

Well, if you use NFS, which has been stable for 20+ yrs, this goes away.

Alas, NFS on MS-Windows is a pile of crap.  I first was forced into using NFS on MS-Windows around 1995.  NFS on Netware was actually pretty great - not as easy to handle as with Unix, but still great and fast.  Then our netware server kept crashing - learned months later after bringing in Novell engineers for a week why - our admin had self-inflicted the issue (installed a newer libc with the backup software over an older Netware version), but we'd been forced by higher powers to move off borrowed DEC equipment onto WinNT Server stuff.  

The entire campus outside mission critical stuff was forced to move to MS-Windows ... which made little sense as our equipment WAS mission critical with lives and billions of $$$ at risk if it ever failed. Anyway, political leaders many, many, levels above me decided MSFT. At the time, I was a lowly software developer, so it shouldn't have been my decision.  Out of about 2K systems in an air-gapped network, we had the only equipment running any MSFT OS. That bothered everyone in the environment except the 2 people who forced the decision.  We should have switched to Solaris or Solaris x86 if they wanted to reuse the hardware.  We'd been using Solaris x86 in the lab for about a year and found it bug-for-bug to the the same as regular Solaris on UltraSPARC hardware.  Sigh.  Politics shouldn't force technical decisions. It seldom works out. 

I have a few other stories where contracts were signed by Sr VPs playing golf that couldn't possibly be useful or implemented.  Let's just say, before there was any "Azure" - someone signed a contract promising to replace all our existing systems (80% UNIX) with MSFT solutions.  There was a bunch of software and systems that would never, ever, run on MS-Windows and MS-Windows didn't scale sufficiently to run it.  Unfortunately, that SrVP who signed the contract wasn't laughed out of his job, like he should have been.  I had DBs that ran on 64-CPU systems. We had 5 of those computers, just for the DBs.  We had other systems that used 128 CPUs.  I don't think the MSFT sales guy was fired either for promising things they could never deliver either.  Too bad there wasn't a $100M failure clause in the contract to make the point.

For the MS-Windows setups, a manual mapping between MS-Windows user-UUIDs and Unix uid/gid is required.  We had about 6000 users with 1000 coming and going every year. It was a pain to maintain the mapping .... we paid a less technical person to handle that aspect of the setup and every day, he'd go visit the Unix centralized admin team to get a list of the new groups and users added to their network accounts.  Sigh.  Sometimes jobs suck.

BTW, NTFS has a mapping method for keeping users and groups mounted under Linux consistent.  It worked here for about 1 month over 6+ yrs ago. Then it never worked again and I didn't bother looking at it again.  Something like this:
uid:gid:Windows-UUID is the layout, I think:
```
1007:1007:S-1-5-21-3141592653-589793238-462643383-1007 
1008:1008:S-1-5-21-3141592653-589793238-462643383-1008 
1009:1009:S-1-5-21-3141592653-589793238-462643383-1009
```

This mapping is just for NTFS storage mounted under the ntfs-3g driver in Unix/Linux.To my knowledge, it has nothing at all to do with NFS storage mapping. That happens only on MS-Windows.  We used a commercial solution all those years ago. I have no idea how to do it today.  I think NFS is a built-in service under MS-Windows Professional and higher. Just enable it and follow MSFT's instructions on mapping accounts.  Back on Win7, I tried to get it working, but never could.  

Some others in these forums claim they got MSFT NFS clients working and use it.  May look for those people and their posts.

---

### Post by Morbius1 on 2023-12-28
> I am running Ubuntu 22.04.3. I feel like I have tried everything, including the simple instructions found here:

[https://www.techrepublic.com/article...desktop-22-04/](https://www.techrepublic.com/article...desktop-22-04/)
Back when I was young and incredibly good looking I ued to go after authours of bad samba howto's like that but I ended up doing nothing else.

Anyhoo, from the HowTo:
> Right-click the Public folder and select Local Network Share ...If you want other users to be able to create and share files within the directory, click the checkbox associated with that option. 
That will not work. Not in Ubuntu 22.04. Not because of samba but because Ubuntu 22.04 sets permissions on a users home folder that only allows that user access. "Other users" are not you so access will be denied.

You can make it work:

Edit /etc/samba/smb.conf and right under the **workgroup = WORKGROUP** line add this one:
```
force user = morbius
```
*[COLOR="#0000FF"]Change morbius to your Ubuntu login user name.[/COLOR]*

Then restart smbd:
```
sudo service smbd restart
```

THen he has you create a share directly in smb.conf:
> [Public]
path = /home/USER/Public
browsable = yes
writable = yes
read only = no

Where USER is your user name. Save and close the file.
That won't work either. Well ... it will work but only if the samba client user is USER. All other client users will be denied access for the same reason as the share that was created in the file manager.

This works better:
> [Public]
path = /home/morbius/Public
browsable = yes
writable = yes
read only = no
force user = morbius

If you want a guest accessible share:
> [Public]
path = /home/morbius/Public
browsable = yes
writable = yes
read only = no
guest ok = yes
force user = morbius

Then restart smbd:
```
sudo service smbd restart
```

**[COLOR="#B22222"]NOTE[/COLOR]**: Do not - I repeat - do not create a samba share of the same folder using both methods. It will confuse the ... um ... daylights out of samba. Use one method or the other.

**[COLOR="#B22222"]One last note[/COLOR]**: A modern Windows machine ( Win10/11 ) will never be able to discover your Linux Samba server in Explorer because the old method of doing that has been disabled on both sides for security purposes.

To make it possible you need to add a package to Ubuntu that enables the server discovery mechanism that Windows now uses:
```
sudo apt install wsdd
```

---

### Post by SeijiSensei on 2023-12-28
> **Morbius1 said:**
> right under the **workgroup = WORKGROUP** line add this one:
```
force user = morbius
```

Let me explain a bit about the "force user" command.

SMB has permissions structures that are different from those used by Unix. Since the Samba server interoperates with the file system as the root user, it takes work to get Samba set up correctly so that bill's files can only be seen by bill, while nancy's files can be seen by both bill and nancy. The "force user" command avoids this problem.

With "force user" active, the server writes to the filesystem as the designated Unix user, no matter which Samba user is creating the file. That eliminates all sorts of permissions problems in shared-files arrangements. It's also, obviously, less secure.

---

### Post by jbl85 on 2023-12-29
Thank you so much.  As it is, I am such an amateur at Linux, so something as simple as modifying a text file proves impossible.  I can open the file, but Linux will NOT allow me to save it.  Sorry for such an elementary error, but please advise.

---

### Post by jbl85 on 2023-12-29
> **TheFu said:**
> Some others in these forums claim they got MSFT NFS clients working and use it.  May look for those people and their posts.

Thank you.  I am deeper into this than I ever thought possible.  The show goes on.

---

### Post by TheFu on 2023-12-29
> **jbl85 said:**
> Thank you so much.  As it is, I am such an amateur at Linux, so something as simple as modifying a text file proves impossible.  I can open the file, but Linux will NOT allow me to save it.  Sorry for such an elementary error, but please advise.

Unix file permissions need to be learned and understood.  Your Linux system isn't single-user, it is multi-user from the ground up. That is the basis of all Unix security, and you need to learn this.  There are probably 20-50 different user accounts on your system to protect it from being hacked. 

Anyway, system config files need to be edited using **sudoedit** command and can only be edited by the user setup as the **sudo** user.  There are lots of complications possible, but that should be enough to get you started.  By default, sudoedit will use a very simple editor. You can setup any editor you like to be used, but until you figure out how to do that, you shouldn't. Run **sudoedit** from a terminal.

---

### Post by jbl85 on 2023-12-29
> **TheFu said:**
> Unix file permissions need to be learned and understood.  Your Linux system isn't single-user, it is multi-user from the ground up. That is the basis of all Unix security, and you need to learn this.  There are probably 20-50 different user accounts on your system to protect it from being hacked. 

Duly noted, and learning slow but sure.  Got the Ubuntu machine to show up on my Windows file manager, but when I try to sign in, nothing works.  My user name is my first name [space] last name.  Am using the password for that profile AND the su password but I cannot get in.  Here are the changes I made.  My network workgroup is MSHOME btw, surely that is not an issue?

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
   force user = John Smith

[Public]
   path = /home/John Smith/Public
   browsable = yes
   writable = yes
   read only = no
   guest ok = yes
   force user = John Smith

---

### Post by TheFu on 2023-12-29
Unix usernames don't allow spaces.  Period.

Fix that.

---

### Post by Morbius1 on 2023-12-29
Run the following command:
```
id
```

I seriously doubt your user name is John Smith for the reason TheFu mentioned. I'm betting your Linux user name is johnsmith:
> uid=1000(johnsmith).....

> Got the Ubuntu machine to show up on my Windows file manager, but when I try to sign in, nothing works.
You have a guest accessible share. THere is no signing in.

If you want the share to be defined in smb.conf you need to remove the share you created in the file manager. Just go into the file manager and "unshare" your share.

If you don't know what I'm talking about go to /var/lib/samba/usershares and delete the public file you find there.

> My network workgroup is MSHOME btw, surely that is not an issue?
If you are running Win10 /11 your workgoup name is irrelevant.

---

### Post by jbl85 on 2023-12-29
I've executed all steps above, and still nothing.  My username is just jbl as it turns out, but that is not what is on the sign in page, it is my full name with a space.  jbl is what comes up when I run a terminal, so that is my username I assume.  Made necessary changes to the smb.conf file and restarted smb, again, to no avail.  You guys have been very patient and kind, and I don't want to take up anymore of your time.  This may be a deeper issue than this forum deserves.  Thank you very much for your assistance.

---

### Post by TheFu on 2023-12-29
Claiming you've done things is different from proving it. If we believed you, we'd never figure out the root problem, so it is best to prove it.  Please.  Show all your work, just like in 3rd grade math class.

---

