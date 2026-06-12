---
title: "A very Controversial Suggestion!"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by degarb on 2011-02-20
I just was reading Comodo time machine is not compatible with linux.  Something about fighting over mbr.  I wonder if this is true for acronis and other rollback products.

But.... I bet.... If Ubuntu had a tool to snapshot Windows, and restore the snapshots, it would: A. **** a lot of linux user off for even considering such a thought  B. Earn a heck of a lot of converts over from windows.  Since, this very tool would secure their windows machines.

Yes, there is Vbox.  But I found a year ago, many aps didn't work in it.  And, I still don't have powerful enough machines to do both OS's at same time.

---

### Post by grahammechanical on 2011-02-20
What would bother me is Windows users expecting a Ubuntu forum to fix their Windows problems. Some forum members use Windows and can offer suggestions. That is fine as far as it goes. I have no problem with someone seeking help and asking for it on a forum that is welcoming and helpful to anyone. Such as this forum.

I have noticed that there are some out there who install Ubuntu and then blame it and criticize it when the problem is due to their ignorance of what the hardware can do and not do, and their ignorance of the machine's user guide and the Ubuntu help documentation. They seem to expect instant support as if they had paid for the OS and as if we were paid to give the support.

Regards.

---

### Post by wilee-nilee on 2011-02-20
There are numerous tools that can image the windows, gparted, dd, clonzilla just to name a few, not snap shots, but even better.

Personally I started with open source and have a couple of win licences, they were cheap, and it is helpful to be familiar with Linux and MS for helping.

---

### Post by degarb on 2011-02-21
> **grahammechanical said:**
> What would bother me is Windows users expecting a Ubuntu forum to fix their Windows problems. Some forum members use Windows and can offer suggestions. That is fine as far as it goes. I have no problem with someone seeking help and asking for it on a forum that is welcoming and helpful to anyone. Such as this forum.

I would expect a special forum just to any obvious "imaging" program.

> **grahammechanical said:**
> 
I have noticed that there are some out there who install Ubuntu and then blame it and criticize it when the problem is due to their ignorance of what the hardware can do and not do, and their ignorance of the machine's user guide and the Ubuntu help documentation. They seem to expect instant support as if they had paid for the OS and as if we were paid to give the support.

Regards.

This point is off topic.  Except, yes you would have a rash of newbies, since you would be converting new masses over to the OS.  Especially, as something they thought to be a backup tool for windows, becomes a viable alternative.  And that, my friend is where your gui's design and intelligence is truly tested.  


----These windows people are accustomed to expect things to work, without hours of tweaking, and within certain established design standards. They are looking to use the machine to save them time, not cost them time.  I believe, even the novice computer user, can sense lazy, unfinished, and even bloated programming, without rational reasoning. (Support is the number one cost of a commercial sw companies. So, they put effort to minimize this cost with the 'picture worth a thousand words' approach.)  And so, as Linux has progressed in this area, so has the user base.  



-------------------------
I will look into clonezilla and gparted imaging.  (I have yet to move main desktop to Ubuntu, other than the backup OS: I got one machine poised with XP vbox guest, I need to crack a few issues like, how to upgrade the OS without loosing installed programs, testing all compatibility.}

---

### Post by HermanAB on 2011-02-21
Howdy,

The tools to make images of hard disks are low level utilities which are available for Windows too, in the form of Cygwin ([http://cygwin.org](http://cygwin.org)).

Ferinstance the Data Definition (dd) or Concatenate (cat) and Zip (gzip) commands:
# cat /dev/sda1 | gzip -9 > /media/disk/windoze.gz

Lots of seemingly complex and expensive Windows programs are one liners in Linux.

Nothing beats a little RTFMing...

---

### Post by degarb on 2011-02-21
> **HermanAB said:**
> Howdy,

The tools to make images of hard disks are low level utilities which are available for Windows too, in the form of Cygwin ([http://cygwin.org](http://cygwin.org)).

Ferinstance the Data Definition (dd) or Concatenate (cat) and Zip (gzip) commands:
# cat /dev/sda1 | gzip -9 > /media/disk/windoze.gz

Lots of seemingly complex and expensive Windows programs are one liners in Linux.

Nothing beats a little RTFMing...

To me, # cat /dev/sda1 | gzip -9 > /media/disk/windoze.gz , is about as memorable as jkekitijpskdjgjglllksdjjj:/sss  While it has more meaning to me, since I have experience with these commands, it is inevitability overlooked as a useful tool for anyone except those of the third order. 

A. You would need a desktop icon leading to a gui.
B.  Doing a second backup, should only do the windows changes, so the each weekly snapshot would only take a few minutes or less.
C. The use, purpose, and learning curve needs to be 5 minutes or less. Immediately at a glance, the purpose should be obvious.  

Else, you got nothing.

(Most people will be doing other things while considering the use of Linux to snapshot secure their windows--entering the Linux world as with a gateway drug.)

---

### Post by degarb on 2011-02-21
Though a good start, would not necessarily need to do progressive images.  That could come later.  Perhaps, a stripped down clonezilla tool, that only snapshots/restores the booting windows partition.  Keep it pretty, and keep it simple.

---

### Post by wep940 on 2011-02-21
Well, I personally believe that anything that is just going to image Windows belongs with Windows.  If, however, you were to say "I want to image my entire disk - dual boot - so I can restore it" that would be another matter.  Incremental imaging for Windows is best left in Windows.  Essentially you are asking to move a Windows function to a different operating system but have it perform the same operations on the same Windows platform.  It's just me, I know, and I'm not a "purest" by any stretch of the imagination (I do cross-platform development), but if you are moving a Windows function like that to a different operating system, why not just convert completely to that operating system so you don't need Windows functions?
 
That 1 line command, by the way, can be put it a script file, and a launcher created on the desktop so all you do is click.

---

### Post by Paqman on 2011-02-21
> **degarb said:**
> 
A. You would need a desktop icon leading to a gui.


Something like Grsync?

> B.  Doing a second backup, should only do the windows changes, so the each weekly snapshot would only take a few minutes or less.

Sounds like Grsync

> 
C. The use, purpose, and learning curve needs to be 5 minutes or less. Immediately at a glance, the purpose should be obvious.  


What about Grsync?

Joking aside, there are tons of excellent backup tools on Linux, both Gui and command-line. Command-line gobbledegook can very easily be turned into a script with a bit of cut and paste, and automating it would then be as simple as dropping it into an anacron folder. Or just tuck it away somewhere and click to run whenever you feel the need.

Seriously, doing backups on Linux is not hard. You've actually got a lot more options than you do on Windows, and many of them require far less tinkering.

You'll probably find as you learn more about Linux that you'll spend far less time fiddling about with it than you did in Windows. A lot of maintenance that you do manually on Windows is either unnecessary or can be easily automated.

---

### Post by walt.smith1960 on 2011-02-21
> **wep940 said:**
> Well, I personally believe that anything that is just going to image Windows belongs with Windows.  If, however, you were to say "I want to image my entire disk - dual boot - so I can restore it" that would be another matter.  Incremental imaging for Windows is best left in Windows.  Essentially you are asking to move a Windows function to a different operating system but have it perform the same operations on the same Windows platform.  It's just me, I know, and I'm not a "purest" by any stretch of the imagination (I do cross-platform development), but if you are moving a Windows function like that to a different operating system, why not just convert completely to that operating system so you don't need Windows functions?
 
That 1 line command, by the way, can be put it a script file, and a launcher created on the desktop so all you do is click.

I'm not a developer or have any expertise but it seems like taking a "picture"(image) of something that's not changing is easier and more accurate than something that is changing. Using Linux to image an inactive windows installation seems reasonable.  I use a shareware Linux backup solution that has been quite reliable.  The vendor also offers DOS & Windows versions of the same application--DOS takes *forever.:)*

---

### Post by degarb on 2011-02-21
> **wep940 said:**
> Well, I personally believe that anything that is just going to image Windows belongs with Windows.  If, however, you were to say "I want to image my entire disk - dual boot - so I can restore it" that would be another matter.  
 
That 1 line command, by the way, can be put it a script file, and a launcher created on the desktop so all you do is click.


I am going off assumption that with "Install programs", donations, and advertisement, there is money to be made in a linux distro.  The more users means more stuff just works for old users; the road becomes less bumpy, and world expands of possibilities.  Users benefit with a unified platform not driven by the urge to force upgrades when not needed.  So, why only advertise your product to your product's user base?

I am talking a tool that first helps secure things, before it obviates those things.  Freezing, backing up, and securing a 'windows installation that works', is a billion dollar industry.

---

### Post by wep940 on 2011-02-21
Yeah, and there are a "zillion" free tools to do it in Windows.  I personally use the free version of Macrium Reflect for my Windows backups.  Again, just my thoughts, but there are tools already to do this in Windows - why bring it Linux to back it up - why not just use native tools.  But that's just me.  Believe me, I'm not arguing with anyone or trying to preach - it's just my thought alone. :)

---

### Post by Trooper_Max on 2011-02-21
I think this idea has some merit... I already backup a lot of my data (Windows or not) on an Ubuntu machine...

> **wep940 said:**
> Yeah, and there are a "zillion" free tools to do it in Windows.  I personally use the free version of Macrium Reflect for my Windows backups.  Again, just my thoughts, but there are tools already to do this in Windows - why bring it Linux to back it up - why not just use native tools.  But that's just me.  Believe me, I'm not arguing with anyone or trying to preach - it's just my thought alone. :)

Macrium Reflect also runs under linux apparently:

> Macrium Reflect FREE Edition - for personal use     

The fastest disk imaging software is now available as a free edition.

Absolutely free! No strings! The only free XP, Vista and Windows 7 compatible disk imaging software **with BartPE and *Linux* based recovery options.** 

At the very least you need an alternate system for restoration purposes (this can be a live cd like I'm guessing is what Macrium Reflect offers or an alternate OS like Ubuntu could be used). Otherwise when your system is hosed you can't recover.

For the more deeply paranoid/security/reliability-minded folks though, a separate system to handle backups would be ideal. In the event that Windows is subverted (even if the fault/error isn't malicious), you may not be able to trust software running within Windows to correctly backup/secure your data. I'm not really that paranoid, but this is along the lines of what I do anyway.

In reality though, I don't think most people are that paranoid and will be perfectly satisfied with Windows-based backup solutions with a restore disk option. Gearing Ubuntu up for Windows disaster recovery may add some benefit, but I don't think it will necessarily do any more to convert the masses.

~Troop

---

### Post by wep940 on 2011-02-21
> **Trooper_Max said:**
> At the very least you need an alternate system for restoration purposes (this can be a live cd like I'm guessing is what Macrium Reflect offers or an alternate OS like Ubuntu could be used). Otherwise when your system is hosed you can't recover.~Troop
 
Yep - like most of those products that prepare for a "disaster", such as losing your hard drive to errors, etc., Macrium Reflect has 2 options for the restore boot - either a specialized Linux CD (they let you build it right out of Macrium reflect) or a Bart PE Windows disk.  For the laptop I sent to my folks, I used Reflect to make an image of their newly created disk onto a USB flash drive, then built the Linux boot disk and sent it all along with the PC.  They're quite elderly so I told them just to store the disk and the flash drive in a safe place.  Well, Dad called saying the wireless mouse I sent with it didn't work.  Turns out he was putting the flash drive in instead of the wireless receiver! ;)
 
> For the more deeply paranoid/security/reliability-minded folks though, a separate system to handle backups would be ideal. In the event that Windows is subverted (even if the fault/error isn't malicious), you may not be able to trust software running within Windows to correctly backup/secure your data. I'm not really that paranoid, but this is along the lines of what I do anyway.
 
I've always wanted to try that just because I'd like to have a dedicated system to try the server version on and try to learn all of that stuff.  However, since I'm poor, another PC is out of the question, and the truth is I need to learn "TONS" of stuff with regular Ubuntu first ;)  I guess like a lot of us, I just keep my backups on a pair of external drives (1 fails, I always have the older [hopefully] ).  
 
 
> In reality though, I don't think most people are that paranoid and will be perfectly satisfied with Windows-based backup solutions with a restore disk option. Gearing Ubuntu up for Windows disaster recovery may add some benefit, but I don't think it will necessarily do any more to convert the masses.
 
That's where my thinking lies, and hence my thoughts - could add some benefit, but won't do anything to convert the masses - they want to know what the OS can do for them, instead of what they can do to help with their Windows install.  Again, just my thoughts!
 
Thanks for letting express my personal feelings on the matter here without being taken the wrong way - I really never mean to argue with someone.  After all, for these types of questions it's really all just personal preference.  ;)

---

### Post by degarb on 2011-02-21
> **wep940 said:**
> Yeah, and there are a "zillion" free tools to do it in Windows.    

Not talking backup.  I haven't found those zillion tools.  Really, not one, maybe 4 fifty dollar ones.  As mentioned, I did find 
ctm which is junk and doesn't understand dual boot.

[http://redobackup.org/](http://redobackup.org/)  linux  and linux [http://www.fogproject.org/?q=screenshots](http://www.fogproject.org/?q=screenshots)

---

### Post by wep940 on 2011-02-21
> **degarb said:**
> Not talking backup. I haven't found those zillion tools. Really, not one, maybe 4 fifty dollar ones. As mentioned, I did find 
ctm which is junk and doesn't understand dual boot.
 
[http://redobackup.org/](http://redobackup.org/) linux and linux [http://www.fogproject.org/?q=screenshots](http://www.fogproject.org/?q=screenshots)
 
 
Well, your initial request and those carried forward are for backup. You want to be able to fully image or do incremental backups - that's what the functionality you've been talking about is called. There are many free backup programs for Windows that do full and incremental backups (I already mentioned Macrium Reflect free version, there are a lot more - try checking downloads.com for a start), just as there are many free ways to back up Ubuntu. I also dual-boot and would love a tool that would copy a partition no mater what it is - hence the ability to restore Windows or Linux from a single backup. However, I don't think we'll see such a product. I definitely don't see a tool being developed to do Windows incremental backups in Linux. Maybe on of the existing commands has a way to that against a NTFS partition, but I've never seen it mentioned. I think you'd truely find more people interested in developing apps strictly for Linux, or cross platform than would be interested in developing such a tool. Again, I could definitely be wrong, and it's just my opinion! 
 
Have a good one! ;)
 
BTW -  Back in the early 1980's we put a co-processor in one of our mainframes in order to run Unix along side and talking with the proprietary OS.  I had already worked with Unix a little in those days, but when a problem came up I called the national technical support center for the hardware/OS vendor.  One of the guys there said he thought Unix (and of course Linux is pseudo Unix) was created by a bunch of guys sitting around late at night in their shorts, tye-died's, and sandles who at 3 a.m. would say "oohhhh, look what I made it do!".  I remember the documentation being divided into 3 or 4 sections.  You could look in the sysadmin guide and find a command, but you could also look in 2 or 3 of the other sections and find it being used for something completely different.  Some of that underlying theme is still there - powerful command line tools, etc..  Linux, and Ubuntu in particular, have made huge jumps from the way things were back when they first came out as well.  I remember Linux command line installation - no GUI, no LiveCD, nothing to guide you but a bunch of documentation that said if you want this, install this from this disk set (you can still see the remnants of the old disk sets if you explore a LiveCD - in Ubuntu's case the /pool/main folder).  The point is things are changing and progressing at a very rapid pace.  Someone may take the time for such tools as wanted in this thread, but I really think they'll be focusing on more advanced main-line things.  Just me, of course!.

---

