---
title: "Wipe HDD on Wrong Password?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by nakama85 on 2010-01-04
I was wondering if there was something on out there that would automatically wipe either the whole HDD or specific areas if a wrong password was entered a designated number of times.

Thanks.

Note** I already have the computers in questions set up with truecrypt Hidden OS using the cascade algorithm.

---

### Post by chewearn on 2010-01-05
Found via Google:
[http://code.google.com/p/beerbottle/](http://code.google.com/p/beerbottle/)

---

### Post by spiderbatdad on 2010-01-05
without much thought it seems like it would fairly easy to work in some kind 'else dd if=/dev/zero of=/dev/sda' into gdm/PreSession/default or the like. But this is like swatting a fly with a sledgehammer...it's great in the movies. Not very practical in the real world.
It takes a fair amount of time to overwrite all the data on a hdd. No forensics effort would be stopped by a silly measure like this...maybe a dumb thief who sits in front of a disappearing login screen for half an hour.

---

### Post by iponeverything on 2010-01-05
It sounds like it would be a fairly trivial "feature" to add something like the dd on set number of failures. 

Something that might be an effective solution would be buy a drive that has password option implemented in hardware, and on certain number of failed logins, have very long sequence of pseudo random characters automatically set for the hard-drive password. This would effectively brick the drive.

As insurance against a toddler banging on your keyboard and bricking your drive, you can keep a copy of the "pseudo random characters" that would be used to lock the drive somewhere safe.

[http://www.laptoptips.ca/security/hard-disk-password/](http://www.laptoptips.ca/security/hard-disk-password/)

---

### Post by nakama85 on 2010-01-05
Thanks everyone. I understand the practicality issue however it would be nice to have it delete only a specified non-os file.

---

### Post by warfacegod on 2010-01-05
A much more effective measure would be to have the drive explode not delete or overwrite itself. Theoretically any file can be recovered, just ask your local C.I.A. agent.

---

### Post by Grenage on 2010-01-05
Or make some gunpowder, mix it with thermite and mould it into the corner of the drive, out of the way of the platters.  However, any forensics team would disconnect and mount the drive in their lab.

---

### Post by Paqman on 2010-01-05
Of course, doing this would allow someone to destroy what is clearly sensitive data without gaining any kind of privileges on your system.

---

### Post by pricetech on 2010-01-05
I like the exploding hard drive option myself.

---

### Post by adam814 on 2010-01-05
If you have anything that sensitive you might want to look into this:

[http://www.truecrypt.org]("http://www.truecrypt.org/")

You might be interested in the hidden volume feature.  Basically you set up two passwords for the encrypted file/partition/disk/whatever.  One is for the outer volume (things you're not as concerned about, but you hide for plausible deniability).  The other is for an "invisible" inner volume for really sensitive stuff.  Short of guessing the password I don't think there's any way of proving the existence of the inner volume.  I've even heard of making completely hidden operating systems this way.

And it probably won't get you on "that list" for googling thermite recipes per the exploding drive option:-P

---

### Post by Grenage on 2010-01-05
The problem with deleting data is that it's very easy to recover unless you then cover it with random data (or many passes when *zeroing* the drive).  Randomising takes a lot of time, but if it's just one file then I guess scripted use of the 'secure-delete' tools would do the job both quickly and securely.

I did work on a project to blow up the drive at the flick of the switch; thankfully common sense intervened before it was finished.  Thermite is nasty, and and it would be useless unless I was present.  For any tangible amount of data, encryption alone should be enough.

---

### Post by warfacegod on 2010-01-05
You could hire a mob guy named Vinny to show up and smash it with a hammer. Hell, he could smash the guy in the head too. That's perfect, not only does he not get your sensitive data but he gets a plate in his skull for his trouble.

---

### Post by Grenage on 2010-01-05
Ubuntu Forums: Advocating amateur explosives and crude assassins. ;)

---

### Post by doas777 on 2010-01-05
> **spiderbatdad said:**
> 
It takes a fair amount of time to overwrite all the data on a hdd. No forensics effort would be stopped by a silly measure like this...maybe a dumb thief who sits in front of a disappearing login screen for half an hour.

yeah, this is the killer. 
what you really need is some ultra-high power electromagnets, and a rube goldberg machine to use them. 

lol rube goldberg. made one for 7th grade physics many many years ago. loved them ever since. [http://mousetrapcontraptions.com/cool-machines-3.html](http://mousetrapcontraptions.com/cool-machines-3.html)

---

### Post by doas777 on 2010-01-05
> **Grenage said:**
> Ubuntu Forums: Advocating amateur explosives and crude assassins. ;)

darn tootin'!

---

### Post by Cheesemill on 2010-01-05
If you use full disk encryption then there is no need to set up a method of deleting files, if you use a strong enough password then no-one can get to the data.

---

### Post by Cheesemill on 2010-01-05
> **warfacegod said:**
> Theoretically any file can be recovered, just ask your local C.I.A. agent.

This just isn't true.
[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

### Post by doas777 on 2010-01-05
> **Cheesemill said:**
> If you use full disk encryption then there is no need to set up a method of deleting files, if you use a strong enough password then no-one can get to the data.

the problem is that I have never found an enterprise worthy full disk ency system that wasn't easily cut through. There are several easy attacks against safeboot, for instance. for the law enforcement, all they have to do is call mcaffee to get todays unlock code.

---

### Post by Cheesemill on 2010-01-05
> **doas777 said:**
> the problem is that I have never found an enterprise worthy full disk ency system that wasn't easily cut through. There are several easy attacks against safeboot, for instance. for the law enforcement, all they have to do is call mcaffee to get todays unlock code.
How about using the alternate install CD to set up LUKS/dm-crypt full disk encryption.
As they are open source you can be sure that there are no back doors.

---

### Post by doas777 on 2010-01-05
> **Cheesemill said:**
> How about using the alternate install CD to set up LUKS full disk encryption.
As LUKS is open source you can be sure that there are no back doors.

the problem with that approach, is what do you do, while the investigator is powering up your box? they ask for the password (because the system is asking them for it on boot automatically), and then you have 2 choices: give your password, or go to jail.
most recommend using a folder based ency system and burying your archive in weird parts of your filesystem.

---

### Post by J V on 2010-01-05
> **warfacegod said:**
> A much more effective measure would be to have the drive explode not delete or overwrite itself. Theoretically any file can be recovered, just ask your local C.I.A. agent.Fragments of an exploded harddrive can be recovered, and though the chances of data being recovered are slim parts of files can be...

The quickest effective measure would be to remove the key for the encryption of the /home drive...

This way the key you were asked to remember would unlock it but your password woulden't, anyone who tried to brute force your system woulden't have access to your data...

---

### Post by pgp_protector on 2010-01-05
Thermite for the win 
[img]http://www.pgp-protector.com/images/ThermiteHD.jpg[/img]

Though I guess even better would be Thermite on a SSD, I doubt even the Black Ops could recover that then.

---

### Post by pgp_protector on 2010-01-05
Yea that just might work :D

Get a SSD for your data you want to be able to destroy.
Build a case for it including a few LARGE Caps (inside the case)
Tamper Switches
Software Trigger
Lots of wiring.
Dump the caps voltage into a photoflash coil to generate a nice High Voltage charge that you've wired to go into each memory chip of your SSD frying it.
Then set off your thermite.

---

### Post by chewearn on 2010-01-05
...

---

### Post by adam814 on 2010-01-05
> **doas777 said:**
> the problem with that approach, is what do you do, while the investigator is powering up your box? they ask for the password (because the system is asking them for it on boot automatically), and then you have 2 choices: give your password, or go to jail.
most recommend using a folder based ency system and burying your archive in weird parts of your filesystem.

That's probably the one thing TrueCrypt has over LUKS/dm-crypt right now.  With a hidden volume you can give a password that "works" and unlocks your encrypted volume.  They can't *prove* you also have a hidden volume inside it, but you've complied and given your password in a situation where you can't withold it.

---

### Post by warfacegod on 2010-01-05
> Ubuntu Forums: Advocating amateur explosives and crude assassins.

Not crude assassins, crude hitmen.

Actually shouldn't that be crude explosives and amateur assassins (hitmen!)?

Never mind, either way would be accurate.

---

### Post by warfacegod on 2010-01-05
In all seriousness, I've run across threads like this before. I always end up thinking: "What's this guy got that's so sensitive? Kiddy pics? Nuclear secrets? Making sure his wife doesn't find his "little black book"?

It's always in the back of my mind: "Am I aiding and abetting someone in some incredibly illegal and/or heinous crime?"

---

### Post by Grenage on 2010-01-05
I doubt most people here really have anything to hide, at most they might have some shady torrents (who am I kidding; a lot of shady torrents).  It's _fun_ to at come up with ways to secure computers!

---

### Post by doas777 on 2010-01-05
> **Grenage said:**
> I doubt most people here really have anything to hide, at most they might have some shady torrents (who am I kidding; a lot of shady torrents).  It's _fun_ to at come up with ways to secure computers!

agreed. many of us have a secret buried desire to be as good as the famed 1337 hax0rs.

---

### Post by doas777 on 2010-01-05
> **warfacegod said:**
> In all seriousness, I've run across threads like this before. I always end up thinking: "What's this guy got that's so sensitive? Kiddy pics? Nuclear secrets? Making sure his wife doesn't find his "little black book"?

It's always in the back of my mind: "Am I aiding and abetting someone in some incredibly illegal and/or heinous crime?"

please don't assume that everyone who is interested in protecting their privacy "has somthing to hide". it's really insulting to the people that do care. If I lost my privacy, the world would not be a safer place, but it seems like the politicians, cops, and security products vendors like to believe that it will.

---

### Post by pgp_protector on 2010-01-05
> **doas777 said:**
> please don't assume that everyone who is interested in protecting their privacy "has somthing to hide". it's really insulting to the people that do care. **If I lost my privacy, the world would not be a safer place, but it seems like the politicians, cops, and security products vendors like to believe that it will.**

Where is the Rep Button :KS

---

### Post by Paqman on 2010-01-05
> **Cheesemill said:**
> This just isn't true.
[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

Even Gutmann himself said that a couple of passes with random data would scupper any hope of recovery. Yet all the secure delete tools default to a ridiculous 34 passes, making them slow as hell. On the very rare occasions that I use one I wind it right down to a couple of passes.

There's a lot of nonsense talked about data recovery. Nobody is going to put your drive in an electron microscope, even if you blew up a bus load of nuns.

---

### Post by warfacegod on 2010-01-05
> 
please don't assume that everyone who is interested in protecting their privacy "has somthing to hide". it's really insulting to the people that do care. If I lost my privacy, the world would not be a safer place, but it seems like the politicians, cops, and security products vendors like to believe that it will.

I'm not assuming anything. If I were, I would think "This guy's doing evil stuff" not "Am I aiding...". I care very much about privacy, yours, mine, everyone's and have no wish to insult. Offending is a different matter. Offending often leads to thinking, if for only a second. Read my quote, for instance. It's superficially offensive but if just person thinks about it, *whatever* they think about it, then I've helped someone become a little bit more free. Those politicians, cops, and other such folk believe no such thing, but they would have _***us***_ believe it.

---

### Post by nakama85 on 2010-01-07
ok everyone. I have had a lot of laughs at the responses and some to actually consider.

I did not think for a minute that people would start questioning my intent but for those of you who are wondering there is simply nothing that sensitive. Although I can see how that thought process would form. 

I am one of those people who wants to know how to do it for 2 different reasons.

1. Just to say that I can and going the knowledge to do so
2. It's is yet something else to put on a resume. 

Sure I have private stuff but it is nothing truecrypt  can't handle. I was just wondering if it was possible.

Wow, I never thought I would have to defend myself in the forums. I do honestly get a laugh out of it.

---

### Post by nakama85 on 2010-01-07
> **warfacegod said:**
> I'm not assuming anything. If I were, I would think "This guy's doing evil stuff" not "Am I aiding...". I care very much about privacy, yours, mine, everyone's and have no wish to insult. Offending is a different matter. Offending often leads to thinking, if for only a second. Read my quote, for instance. It's superficially offensive but if just person thinks about it, *whatever* they think about it, then I've helped someone become a little bit more free. Those politicians, cops, and other such folk believe no such thing, but they would have _***us***_ believe it.

Thanks, I as well care about privacy. As far as my mind goes, **the question I am asking is not any different than asking how to shred paper.**

I do trust things such as encryptions to a certain extent but the way I figure it is that if someone came up with the encryption method then someone can also break it.

---

### Post by warfacegod on 2010-01-07
I agree. Besides, shredding paper isn't as much fun as smashing a hard drive with a hammer.

---

### Post by niteshifter on 2010-01-07
> **warfacegod said:**
> I agree. Besides, shredding paper isn't as much fun as smashing a hard drive with a hammer.

Even more fun: Have at one with an oxy-acetylene torch. Pretty colors when the metals burn :) 

Should anyone actually want to try this: A well ventilated area and standing upwind of it are must-do - "welder's flu" is a miserable experience.

nakama85, the most important thing to learn about data security is this:

There is no magic bullet, no one thing that fixes all technique. Effective security is a system of components, not a single item.

Case in point: Full disk encryption has been mentioned. Further, choosing a strong password will keep anyone out.

Not true. Give me that machine for a few minutes ... and you'll tell me the password. How? I'll boot the machine from CD or USB, modify the (not encrypted) resident boot loader with a simple keylogger code insertion. When I next access the machine, I have your password.

This is known as the Evil Maid attack. 

The solution here is to:

A) Keep the machine (or HD) physically secured (locked in a safe, for example) when you are not using it or have it in sight. Most folks find this impractical ;) 

B) Backstop the FDE with hashes of the boot loader programs made when the machine is known to be clean and compared to hashes computed after unlock. A mis-match of hashes signals that the machine is compromised.

---

### Post by warfacegod on 2010-01-07
How about a bangstick or a bag of angry rats? Ooh! I know, plasma cutter!

I think the hydrogen bomb would qualify as a "magic bullet". A bit messy though.

Dropping to shell in recovery allows you to change passwords as well.

---

### Post by Microft24 on 2010-03-31
> **adam814 said:**
> That's probably the one thing TrueCrypt has over LUKS/dm-crypt right now.  With a hidden volume you can give a password that "works" and unlocks your encrypted volume.  They can't *prove* you also have a hidden volume inside it, but you've complied and given your password in a situation where you can't withold it.

For the record, this quarter's 2600 magazine has a detailed description of an easy way to beat Truecrypt, PGP, or any other hole disk encryption. The test was done on a linux system, although that doesnt matter in terms of hole disk encryption. 
Hidden volumes may be more difficult but not impossible by any means. 


The University of California at San Diego hosts the Center for Magnetic Recording Research. 
CMRR tested the effectiveness of a set of commands that are built into every HDD built since 2001, but are mysteriously locked to the consumer. They found that the HDDErase commands actually erase all data on the drives, including bad sectors which 99.9% of zero wipe utilities cant touch. It writes over every partition, HPA (Host Protected Area) and DCO (Device Config Overlay). These sections of the drive are not even visible to the OS, but the HDD will erase them anyway with the software built in. Seagate, Maxtor, WD, Hitachi, Fujitsu... etc they all have this built in if it was made after 2001 and is bigger than 15GB. CMRR proved through extensive testing (funded by the NSA) to prove that this is an acceptable method for data destruction up to the top secret level, in accordance with the NIST 800-88 guidelines. 

Now everyone knows, no matter what command you use, overwriting a hdd takes time. In most cases a lot of time. But there is a way to safely destroy your data in under a minute. If your drive is encrypted, using the Enhanced Wipe option will immediately over write the entire sector that the key is written to with random data. If your encryption is good (at least AES1024 with a 256bit key if the NSA is raiding your house) you should be covered, According to CMRR, NSA & DoD lab testing. If you really want to sleep well at night, perform a second wipe after the enhanced, to over write the encrypted data as well. According to their lab tests (including disassembly) there was virtually no magnetic signature left at all. 

Complies with All of the following:

Sarbanes-Oxley, the Health Information Portability and 
Accountability Act (HIPAA), the Personal Information Protection and Electronic Documents Act (PIPEDA), the Gramm-Leach-Bliley Act (GLBA), and California Senate 
Bill 1386 

Dr. Gordon Hughes of CMRR helped develop the Secure Erase standard and this tool to unlock its use in your hdd. 

So after this terribly long post, here is the link:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)  


FOR THE RECORD, THERMITE IS THE ONLY REAL ABSOLUTE WIPE.  ;)
Just dont forget to que the music before you make your Jason Bourne like esacpe into the night, lol.

---

### Post by Jive Turkey on 2010-04-18
Another theoretical mechanism would be a bank of capacitors that could discharge directly onto the platters of the disk, and/or the hands of anyone tampering physically with the hard-disk.  The computer wouldn't even need to be plugged in.  I'm reminded of the Hainan Island incident [http://en.wikipedia.org/wiki/Hainan_Island_incident](http://en.wikipedia.org/wiki/Hainan_Island_incident).  Such technology would have been helpful to the pilots of the spy plane.

Alternately, I don't think it would be too hard to make a daemon that would refer to an encrypted list of files/directories to destroy, and while running in memory, remove most of the evidence of its own existence on the hdd.  It could possibly monitor logfiles for X failed login attempts or something.

---

### Post by chikara99 on 2010-09-23
If you are going to wipe a drive 3 wipes is good enough. I've read somewhere that the government standards are 3 passes of 1s and 0s to deleting data.

Essentially a hard drive is made out of rust that is on top a platers that getting + or - charges to that represent data.

---

### Post by psusi on 2010-09-23
> **Microft24 said:**
> 
CMRR tested the effectiveness of a set of commands that are built into every HDD built since 2001, but are mysteriously locked to the consumer. They found that the HDDErase commands actually erase all data on the drives, including bad sectors which 99.9% of zero wipe utilities cant touch. It writes over every partition, HPA (Host Protected Area) and DCO (Device Config Overlay). These sections of the drive are not even visible to the OS, but the HDD will erase them anyway with the software built in. Seagate, Maxtor, WD, Hitachi, Fujitsu... etc they all have this built in if it was made after 2001 and is bigger than 15GB. CMRR proved through extensive testing (funded by the NSA) to prove that this is an acceptable method for data destruction up to the top secret level, in accordance with the NIST 800-88 guidelines. 

Wow, that's a lot of misinformation.  First, the command is not "locked to the consumer".  If you want to run the SECURE ERASE command you can do so with hdparm.  A bad sector kind of means you CAN'T read or write it, so suggesting that you have a magic incantation that will or will not erase it is absurd on its face.  The host protected area can be detected and accessed by the OS, and in fact, Ubuntu kernels do this by default ( though they shouldn't and this hopefully will be fixed in the future ).  The DCO?  Who cares?  It can't have any information that you care about since it is only accessible to the drive to store its internal configuration.

---

