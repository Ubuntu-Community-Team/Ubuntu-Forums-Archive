---
title: "? Virtual Box vs Wine interaction w/Ubuntu?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Kellemora on 2009-02-05
Hi Gang

I keep hearing about this Virtual Box, looked into it, but couldn't find the answer to my only real question about it.

Here is an example:  I use Eudora e-mail in WINE, often I get attachments I need to view or documents I need to open or links to visit.
Using Wine this is no problem because it uses the Ubuntu programs to handle these tasks.  Adobe will open to read a pdf, open office will open to read a document or spreadsheet, Firefox will open for a link and gimp will open for a photo.

In other words, WINE interacts with Ubuntu and uses the Ubuntu programs.

Can Virtual Box do the same thing, or is it more like Dual Boot without the time taken up for dual booting?????

FWIW:  Although I have dual and triple boot machines, I use a KVM when I need the DOZE or other Ubuntu machines for something.  But they are not interactive, except for file sharing with the data file server.  But I do use WINE primarily for my desired e-mail program.

Thanks

TTUL
Gary

---

### Post by Cypher on 2009-02-05
If you were to run XP within VirtualBox, it's entirely contained within that virtual machine. XP has no clue that it's running on a virutal machie and not a real X86 machine. That being the case, if you were to open your various attachments, like the real XP, local apps will be launched to deal with them.

If you've got your application running in Wine and using the native Ubuntu applications for everything, you're going to be better off sticking to that than switching to VirtualBox.

---

### Post by binbash on 2009-02-05
It will be opened at windows inside virtual machine.They are 2 different machines

---

### Post by Kellemora on 2009-02-05
Thanks Cypher and BinBash!

That's what I thought!
I would have to load all the Windows programs, plus the Windows OS in order to use it.

I'm trying to get AWAY from the Doze!
And since WINE works for basically the only Doze program I still use, I'll stick with WINE for that............

This new computer I'm building was intended for Ubuntu ONLY, but I quickly found that in order to load the Bios data from the CD, it had to be run from the Doze....  Once loaded though I could eliminate the Doze, but I couldn't get Bios updates.
It's an Asus MOBO!  So I decided to go ahead and put the Doze on and give it little space, but more than it needs.  Space is not an issue, but I doubt I will ever have to boot into it.

By that same logic, I see no reason why I would ever need Virtual Box either!  WINE truly is amazing in how it interacts with Ubuntu when necessary!

TTUL
Gary

---

### Post by Cypher on 2009-02-05
Newer Mobo's are getting smarter in how you update the BIOS. My Mobo allows me to put the BIOS binary on a USB flash stick, and then bootup I hit a key sequence to get into the BIOS updater built right in. It detects the USB flash drive and allows me to save the current BIOS to the drive while upgrade to the newest BIOS also located on the flash drive.

Pretty nifty, also the Mobo has dual BIOS' so I don't have to worry about bricking my Mobo..

I've got XP installed in VirtualBox JUST in case I need it. I've been perfectly fine using Ubuntu for everything for a long time now..:)

---

### Post by Kellemora on 2009-02-05
Hi Cypher

Mine might do the same thing, I'm just NOT UP on all these newfangled computin' contraptions they have out today!

It's an ASUS M2N68-AM MOBO and being NEW I'm even afraid to try to plug my multi-card reader into it, due to all the warnings in the booklet.  I did buy a Sata HD 3g with it, since I need the only IDE to run the CD/DVD reader, have no idea if it has ATA at all.
But since I use a server for my data files, most of that extra stuff is just candy anyhow!

I plan on getting the same board and going with a quad core Phenom after I get this one up and running correctly.
My not so old puters here are dying slow deaths.  The oldest ones were running just fine, just dumped them to make room for newer is all.  Then don'cha know, add a new one and the ones I was relying on decided to begin to die on me.
The transition from multiple hard drives on different machines to a central data file server must have scared them to death, hi hi.......  Or overworked them moving all that data around!

Thanks for your tips and pointers!

TTUL
Gary

---

