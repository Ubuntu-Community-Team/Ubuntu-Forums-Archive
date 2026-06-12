---
title: "Cloning folders between XP and UIbuntu"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by gv29847 on 2009-01-19
I want to run a single program either on an XP machine or a Ubuntu one. In either case the objective is to force a (windows) folder on the Ubuntu machine to be the same as a folder on the XP machine by over the network by changing only what is necessary.

Currently my Ubuntu machine can see and read from the XP machines folders OK, but the XP machines can see the Ubuntu machine but cannot see any folders on the Ubuntu. I have an app (FolderClone) that would push from XP to Ubuntu, if it could see the Ubuntu folder. I don't have anything on Ubuntu that will pull from XP. Rsync was suggested but I read this needs to be at both ends and that seems troublesome at the XP end.

Any suggestions?

---

### Post by compiledkernel on 2009-01-19
Samba is probably not configured correctly, or windows file sharing isnt configured correctly on the Windows side. Or both. 

I would also make sure the accounts your using to access exist on both side, both on the Linux Side as well as the Windows side. 

For going from Ubuntu to XP -- [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Read here for further information as well -- [https://help.ubuntu.com/8.04/serverguide/C/windows-networking-introduction.html](https://help.ubuntu.com/8.04/serverguide/C/windows-networking-introduction.html)

---

### Post by emarkd on 2009-01-19
rsync doesn't have to be at both ends.  it can operate as a stand-alone client on the ubuntu box with no problems.  it's faster and more efficient with a rsync daemon running on the server side, but it'll work fine without it.

how are you mounting the ubuntu folder in xp?  samba?  if so, i've been having issues wiith samba lately as well and found that browsing to the share using the network placed widget in xp doesn't work well, but entering the ip of the ubuntu box in the address bar of windows explorer works fine.  enter it like: \\192.168.1.1.  of course, this assumes that the ip of the ubuntu box won't change on your network.

---

### Post by gv29847 on 2009-01-19
Replying to both the last two -

Windows side is fine - I have been running fine with the ubuntu machine running on XP, and I can see the windows side from the ubuntu machine and from other XP's on the network.

I had not installed samba (or done anything else system wise). I found instructions for this, but when I try to open a terminal window it just comes up as an empty white rectangle. Running other stuff - calculator, disc usage, firefox .. the windows come up fine.

Good to here about rsync runnable on linux only!

I tried entering the ip as suggested and it correctly pulls up the ubuntu machine, but does not show anything at a lower level except 'printers and faxes' which is what i get under 'MS windows network'>'workgroup' anyway.

Looks like I have to fix the terminal problem and then run samba (and smbfs?) - correct?

Peter

---

### Post by Kellemora on 2009-01-19
Hi GV

If I'm reading your question correctly, it SOUNDS like you are trying to make single user documents MULTI-USER and that will lead to major problems no matter how you do it.

One can SHARE a single user document, make changes to it, then save those changes.  BUT if you have two folks opening the same document, making changes, then saving it back again, the one who made the last write is who's document will be available, all changes made by the first person to save that document will be lost.

In order for more than one person to access a document and make changes where all changes are updated requires Multi-User software for those documents, which virtually runs those documents as live!
My accounting program works that way!
I can be looking at a clients folder, perhaps making a change myself, while one of the front office is adding an order or accounts receivable recording a payment.  I see that happening right in front of my eyes while I have that clients folder or document open.

At one time I had a multi-user document editing program and it worked basically the same way.  Every keystroke is saved as it is being made, so one user is not overwriting what another user is doing.

Now, all of our documents are single user and simple!

TTUL
Gary

---

### Post by gv29847 on 2009-01-19
Sorry - I obviously did not explain very well. This is nothing to do with multiple users - though I agree with Kellemora's comments in that area. 

No this is much simpler - its just trying to push from an XP machine over the network into a Ubuntu machine used only for keeping backup data, or to pull it from XP into Ubuntu.

Peter

---

### Post by Kellemora on 2009-01-20
Hi gv

Then your home free actually.

I don't have a File Server, but I have a Data File Server!

At first I formatted it in EXT3 for the speed and simplicity, since the Hard Drive of the Data File Server was connected to an Ubuntu Machine, Windows had no problems reading the files from it.

Ubuntu has tons of cool features not found in the Doze!

I was having a tad of a problem (my fault) with rsync, which I finally straightened out.  But more as a safety measure than anything else, I MIRROR my EXT3 files to an NTFS Drive, so in an emergency, I could just plug the ntfs drive into a Doze machine and have all the files available.

So in a nutshell, I have two EXT3 drives, one is a Mirror, and a third drive formatted in NTFS that mirrors the mirror.  The third HD is connected to a Doze machine off-site (out of this building and in another building)  I run a hardwired LAN!
Really serious data is stored further off-site, like 530 miles away, hi hi........

Even with all these precautions and redundancy, we still lost a whopping pile of data, mostly client images (not replaceable) when a glitch in a Doze program called Retrospect messed up royally.  Instead of saving the actual files as it should, ALL of the data was saved as LINKS back to the original drive.  So when it when kablooy and we plopped the mirror in, all there was was Links, but they didn't look like links when we checked them while the system was up and running.  So we didn't catch it.
Needless to say, the mirror of the mirror was just the links copied over to it.  So ever since that very costly event, after we run a new mirror and script, we physically PULL the HD and mount it on another independent machine to make sure what supposed to be there really is.  It cost us roughly 2 years of profits to pay for that tragic loss!  Included were some of our own family photo's as well that were not replaceable.

So I can't stress checking those backups and/or mirrors!

TTUL
Gary

---

### Post by Meph1st0 on 2009-01-20
Have you considered using SyncToy?  It's a windows app made by microsoft that has worked very well for me.  It'll synchronize across windows and linux shares.

You just gotta be sure you can write to the ubuntu shared directory from the windows xp machine.  If you can configure samba for you to do that then you're golden.

---

### Post by gv29847 on 2009-01-20
I already have an XP side app I am happy with (folderclone) My problem is getting to the point where I "can write to the ubuntu shared directory from the windows xp machine. If you can configure samba for you to do that .. " I can't do this. I have installed samba and smbfs, but the samba documentation just leads me into a maze. I hate to say it but its 3 clicks in XP to make a folder visible to the network - is it really so much more difficult in ubuntu? Anyway any help on how to get there appretiated.

---

### Post by Kellemora on 2009-01-21
Hi GV

First, remove smbfs it BLOCKS shares from being visible!

You can prove this to yourself by installing smbtree on your ubuntu machine.

Check your shares, then install smbfs and you'll find a few disappear from the listing, uninstall smbfs and they reappear again.

I have 2 XP machines and 6 ubuntu machines on the same workgroup.
They all read and write to each other with no problem at all.

And now that I'm running a central Ubuntu Data File Server things are even much simpler than when I had certain data stored on each separate machine.

How I was set up in the distant past was each computer had two internal hard drives of identical size the primary was mirrored to the secondary and an external HD that mirrored the mirror and was physically carried off-site each evening and mirrored to the offsite drive, which was like 8 miles away.

After moving operations south, I set up a little differently at first.  I used smaller hard drives for the System Files, and the larger hard drives for the Data Files, but maintained only certain file types on certain machines.  The Data Files were mirrored to an external HD 4 times a day, and once in the evening the external mirrors were mirrored to an off-site location through the LAN, 200 feet in a different building.
From that building the big mirror of all the drives were mirrored to our office back home 530 miles away.

The problem with this system, especially after switching to Ubuntu, was Nautilus would mess up all the time, until the recent fix.  So each person had to enter IP numbers by hand, and access whichever machines they needed their data from.  Sometimes this could be time consuming when Nautilus was in a bad mood for a day or two.

The change to Ubuntu did however increase our production levels considerably.  My next logical step was to build a file server, even played around with Edubuntu a little to learn how they work.  But for our operations a file server was definitely not the way to go.  A Cluster would be more appropos, hi hi.......
But making all the Data Files centrally located was what we really needed.  So I took one of our computers and loaded it down with 4 500 gig hard drives.  One for each primary division.  But then later synced them all together so you really don't know which drive you are accessing from, you just point to a single folder and everything is there under it.

As I said earlier, at first I had set this up as ALL EXT3, including the mirrors.  But then while redoing some things, I decided to keep the WORKING Data File Server as EXT3, but made the external mirrors NTFS so they could be portable to XP machines if needed.  Our off-site machines are DOZE machines, so if this place burns down, I'm not out of business!

I personally have never liked the way ntfs works, but it appears to work differently using the ntfs programs in Ubuntu than it does using the DOZE.  So all seems to be going great!

The ONLY things I have (that I know of) besides Samba running are smbclient and smbtree, ntfs programs of course and NFS is turned on as well, on this machine anyhow.  I don't think it is on the others though.
Permissions are set to Read Write for all GROUP users and each person with a log in is in the smbusers file.
The ONLY changes to smb.conf are the addition of our workgroup name, the rest is stock from the package as installed.  Except at the bottom it has the File-Server Folder data.

ALL of the problems we encountered were directly related to a bug in Nautilus that was there for over 2 years.  The most recent upgrade to Nautilus apparently fixed that problem.

On an interesting note:  I use Rsync to mirror the File-Servers drives to the external ntfs mirrors.  But I use the off-site's backup program to DRAW the mirror to it's mirror.

I started doing it this way because for almost 3 months I had a problem with Permissions changing when I PUT a file onto another computer, but permissions would remain intact if I FETCHED a file.  So we made it a practice to only FETCH files, leave them on the computers and let the File-Server Fetch them back again.
I hate to say, I don't remember what was done to fix this problem.  I myself didn't do it, I had an IT guy who works on UNIX come over and he locked permissions in somehow.  Told me what he did, simple, but over my head at the time.  I think he simply did a CHOWN -R group:group or something from Terminal to the entire File-Server which took hours to run.  But it worked perfectly every since!  I should study up on this, just in case!

In any case, that's why my complaints have dwindled down to nothing!  Everything is working like a swiss watch under Ubuntu! Knock on simulated wood grain, hi hi............

If it were not for LINUX REQUIRING a DOZE machine to function, we wouldn't have ANY DOZE machines here at all anymore!  90% of our work is done on Ubuntu, faster, easier and with less problems than we ever did on the DOZE!

So just hang in there and you'll get your machines humming like a Swiss watch also!

TTUL
Gary

---

