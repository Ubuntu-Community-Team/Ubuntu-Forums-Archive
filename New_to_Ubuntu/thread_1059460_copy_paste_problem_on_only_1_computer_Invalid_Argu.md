---
title: "copy paste problem on only 1 computer? Invalid Argument!"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Kellemora on 2009-02-03
Hi Gang

Last month I built a new Data File Server, it works great, no problems.

This week I have been building up a new computer and placing files onto it to bring it into service.

Hit a weird snag I've never hit before.

I've got about 120 documents that I can copy and paste to any shared folder in any of six computers and into the Data File Server, no problems with permissions or anything.
HOWEVER, I cannot paste these same 120 documents into ANY shared folder on my new computer.  And I cannot find anything different.  Even tried recreating the folder, which many of you know requires logging off and back on again to share the folder due to a bug in Ubuntu that is still unresolved.

I should clarify, it's ONLY 120 out of like 1000 documents, NOT ALL THE DOCUMENTS.  All the rest work OK, also with no permission problems.

I'm getting the ERROR "Invalid Argument" when I try to paste ANY of these particular 120 documents into the folders on ONE computer only, the new one, which figures.

And here I thought I was done for this evening and could go home!
Looks like another all-nighter in the office!  AGAIN!

Any Ideas Gang?

---

### Post by handydan918 on 2009-02-03
Not so much a fix-it idea as an eliminate possibilities idea.
How are you trying to copy? I assume this is over a LAN...have you tried any command line apps?? (Like scp?)

---

### Post by Kellemora on 2009-02-03
HI Handy Dan

This is Getting WEIRDER Now!!!!!

I made a folder on the Data File Server and copied ALL of the 120 files that are giving me problems into the new folder.
My thought was, copy them there, then from the new computer, simply fetch those files from the file server!

ARE YOU READY FOR THIS???????

I have a total of 8 computers here!  The new one is replacing one that is dying a quick death.  So I'll still have just 8 computers.
In any case, I can go to ANY computer, except the new one, open the folder in the Data File Server and see the 120 files I placed there!  Open them, edit them, and write them back.

BUT, they DO NOT APPEAR AS BEING ON THE FILE SERVER when looking at it from the NEW COMPUTER!!!!  YES I hit RELOAD to make sure I was not seeing the old cache!

Even rebooted the new computer!  Cannot see these 120 files, but I can see all the rest of the files I place in the File Server!

They are SMALL simple one and two page Open Office Writer.odt text files, nothing crazy like an 8 gig image!  And a couple of msWord.doc files.........

Since I CAN open them on OTHER Ubuntu computers, just not this one, I'm thinking it might be because it's a MORE POWERFUL 64 bit Distro of Ubuntu Hardy.......?????
More Power, less user friendly, eh!

If you have any ideas, I'm all ears!

TTUL
Gary

---

### Post by handydan918 on 2009-02-03
How are you trying to copy? I assume this is over a LAN...have you tried any command line apps?? (Like scp?)

---

### Post by Kellemora on 2009-02-03
OK, lets get even more weird!

I just checked the file count of the new folder as well as worked with yet another new folder I just created.

I placed 16 .odt files that I know are OK and 6 of the 120 that don't show up.

I went around to the 6 Ubuntu machines and opened the folder.
All of the files are showing except on the new computer, same problem. 

BUT DIG THIS NEW MYSTERY!

There are 22 Documents in the Folder.
Backing up to the folder and checking properties SHOWS 23 items.  The folder counts as 1 item is why it shows 23!
I go to the computer that is NOT showing the 6 documents and do the same thing, it shows 23 items in the folder, but displays only 16 of them..........

Can this get any weirder?????

Probably, the night is still young!

TTUL
Gary

---

### Post by cariboo on 2009-02-03
On your server, type at the prompt:

```
testparm
```

to see if there are any errors in your /etc/samba/smb.conf file.

On your new computer open a Applications-->Accessories-->Terminal and type:

```
smbclient -L <servername> -U%
```

You should get an output that looks something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	stuff           Disk      misc stuff
	images          Disk      iso images
	updates         Disk      Project Dakota
	data            Disk      Data directory
	music           Disk      Music library
	movies          Disk      TV Shows and Movies
	print$          Disk      Printer Drivers
	HP_LaserJet_5P_LPT_parport0_HPLIP Printer   HP LaserJet 5P
	HP_LaserJet_5P_LPT_1 Printer   HP LaserJet 5P
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

Make sure all the shares on the server show up.

One other thing to check, is the ownership and permissions of the file that won't copy.

Jim

---

### Post by Kellemora on 2009-02-03
Hi Jim

I tried a few more experiments and finally located the problem!

I used rsync to copy several test files and a few of the files that were giving me problems.
rsync was clearer about what the problem was!
File Name Not Valid, Illegal Characters in File Name!

NOTE: rsync DID NOT give this error when copying the files from an Ubuntu 32 bit machine to an Ubuntu 32 bit machine holding the Data File Server files.

It ONLY gives an error when I try to copy to any shared folder on a 64 bit Ubuntu machine!

I also recreated how the invalid file name happened in the first place.  This part is an Open Office FEATURE that I LOVE!
But apparently Ubuntu 64 bit is not up to par with the 32 bit Distro.......

I will fill out a bug report on the problem over at launchpad and DELETE the 64 bit Ubuntu and return to 32 bit on my new Dual Core machine.  That's the simplest and cheapest fix I can think of.

I would have to develop a new file naming system for my company and change close to 150,000 filenames, by hand, one at a time, in order to be able to use the 64 bit version of Ubuntu, that cannot recognize filenames used by the Doze and by 32 bit Ubuntu!
That was one of the very first things I checked before converting my office over to Ubuntu too!

I'm going home and going to bed!

TTUL
Gary

---

