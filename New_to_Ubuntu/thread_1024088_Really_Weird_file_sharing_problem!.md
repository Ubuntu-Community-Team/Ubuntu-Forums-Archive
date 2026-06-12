---
title: "Really Weird file sharing problem!"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-28
Hi Gang

Hit a very weird snag here!

Got the new File Server up and running over the weekend and all is GREAT, Except........

We used an Ubuntu machine to copy all the files from each of the working computers (2 were Doze machines) to the new Ubuntu File Server.  Then ran a Mirror of the Ubuntu File Server to an off-site XP-Pro external drive.

We can read ALL the files from both the new Ubuntu File Server and from the XP-Pro mirror, from any machine, without a single problem.

Now here is the Really Weird part!
From the Windows XP-PRO MIRROR machine, which can read every single file no problem, I cannot COPY (mirror) the Ubuntu File Server to the External hard drive on it.  I get the error "Cannot Copy File:  Cannot Read From Source File or Disk."

I cannot PUT the files from the Ubuntu File Server ONTO the Mirror because it will change all the permissions!  That's been an ongoing problem here for many months now!  So we normally only FETCH files.

However, as I said, we can Fetch a File, Edit it, Save it back to the Ubuntu File Server and Permissions no longer get messed up.  So that's a major milestone.

NOW - Using an Ubuntu Machine that is NOT the File Server, I CAN with great ease, COPY the entire file FROM the Ubuntu File Server to the Off-Site XP-Pro's external Hard Drive and the file permissions stay intact.

If ALL computers can READ and SAVE to the File Server, no problem.  INCLUDING the off-site XP-Pro Machine that holds the external mirror drive.  WHY does it give the error when I try to COPY the files from the File Server to the external HD mirror?

It does not appear to be a Permissions Problem!
Since I can Open, Edit and Save a File to either the File Server or the External Mirror and it works just fine.
I just can't COPY even a small folder from the Server to the Mirror.

Is there something I'm missing here??????
File Server is EXT3 and Mirror is NTFS!
But that doesn't seem to affect using or saving files, or moving them around using an Ubuntu machine to do it.

If I'm not making sense here I'll be glad to clarify even more!

TTUL
Gary

---

### Post by bodhi.zazen on 2008-12-28
It is difficult to tell from your post.

First, when you say "file server" what server ? Are you using FTP or Samba ?

Second, NTFS does not support Linux permissions, so that may be part of the problem.

Third, I can not tell from your post if the problem is on the Windows or Ubuntu machine.

Last, It may also have to do with samba or ftp users / group permissions or mapping users. Again, hard to know from your post.

---

### Post by Kellemora on 2008-12-28
Hi BZ

Thanks for taking a look for me!

First I'll start by saying it's NOT a Server in the sense of the machine being configured as a Server.  Although that is ALL this machine is used for now!

The Local Machine was originally a Compaq5420.  I virtually stripped it down to bare bones so I had plenty of air flow for the hard drives.  It has a 160 gig IDE named Business, a 120 gig IDE named Family, and two 80 gig IDE drives named Property & Reference.  All of these are formatted EXT3, running Ubuntu Hardy 8.04 LTS, using Samba.  This machine also has a 500 gig External formatted as EXT3 that I have made into the Main File Server for all the rest of the machines that access the files.
I used Rsync to copy the files from the internal drives to the new external drive.  That went perfectly.  The name of the External Drive is File Server and the root directory tree contains only Business, Family, Property & Reference, with tons of subdirectories within those 4 Broad Classifications.

The Remote Machine is an DellOptiPlex GX270 running XP-PRO with a 500 gig External USB hard drive.  Primarily used for Cash Accounting and Front Office.  I have a stand alone machine just for Major Accounting purposes.

The Primary Computer I use almost all day and night is an HP Pavilion 753n running Ubuntu Hardy 8.04 LTS.
Plus I have like 5 other active computers we use.

My INTENT is to have ALL FILES on the 500 gig External EXT3 Drive for Daily Use.  Then Mirror this Drive to the Off-site 500 gig NTFS Drive, through a LAN of course as a backup system.

Without making this sound too confusing, the 4 separate internal HD's that used to previously serve everyone, will NOW be used as redundant manual backups.

So in a nutshell, here is what's going on!
From ANY computer, I can access the 500 gig File Server Hard Drive, open a file, edit it, and write it back to the File Server Hard Drive.  From those same computers I can access the Remote 500 gig backup hard drive (mirrored not using backup programs, meaning it's a direct copy of the File Server Drive).
In other words, from any computer I can read, write, create folders and put documents into them.

So see, so far everything is going along just as expected!  It's basically working perfectly, just as I wanted.
EXCEPT when it comes to copying the Local 500 gig File Server drive to the Remote 500 gig Mirror.

If I go down to the house to the XP-Pro machine with the external 500 gig NTFS drive, go into Network Neighborhood, access the 500 gig EXT3 drive up here.  I can open any file or folder I want to, no problem.  BUT if I highlight a folder and select copy, then go to the 500 gig external connected to that machine and hit Paste.  I get the error "Cannot Copy File:  Cannot Read from Source File or Disk."

This makes NO SENSE as I can Open, Edit and Write back any file to the File Server, or I can write it to the Mirror with no errors.  I can Create a Folder from that machine ON the File Server up in the office.  Select that new folder and Copy it to the Mirror connected to that machine.  But I can't COPY the primary file folder that's named FileServer and contains everything on that drive.

BUT, now DIG THIS!
I can go up to my office to my HP Pavilion 753n machine, running Ubuntu (of course!)  I can go to Places/Network/Compaq5420/500gigExternal and highlight FileServer and hit COPY.
Then I can move down the list to Places/Network/EMachine/500gigExternal and hit PASTE and it will copy the File Server Hard Drive to the Mirror Hard Drive on the XP-Pro machine, without a hitch and without any permissions getting altered.

Naturally it takes longer doing it this way, because the file has to be read from the Compaq machine, Pass through the HP machine, and then go to the DellOptiPlex off-site.

It just seems mighty ODD to me that the machine I WANT to Copy the files to, cannot read from the Source to Copy, but it CAN if I want to Edit a File or move a single small folder.

But going through a THIRD MACHINE and it all works OK.........

See why I'm STUMPED?????

Thanks

TTUL
Gary

---

