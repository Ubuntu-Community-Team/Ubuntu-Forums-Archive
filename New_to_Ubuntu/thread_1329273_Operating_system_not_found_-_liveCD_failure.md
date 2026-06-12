---
title: "Operating system not found - liveCD failure"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Metal Giant on 2009-11-17
Hi all,

I wiped an old desktop PC with Darik's Boot and Nuke. It's done a really thorough job, that baby is as clean as a whistle. I now power it on and a few seconds later, she buzzes and declares "Operating System Not Found". That's good, time to install Linux.

So I pop in a liveCD (I've tried Ubuntu, Xubuntu, Kubuntu, Mint, Fedora, and Puppy) and nothing* happens. Straight back to the "Operating System Not Found" screen. I have changed the boot order in the BIOS to look for the CD drive first, so it can't be that.

Interestingly, if I pop in the CD I made with Darik's Boot & Nuke on it, it will read that and is prepared to wipe again, but the LiveCD's (even my old Windows XP CD) won't boot.

What do you reckon I've done? Shall I plant petunias in it or is there any hope?

MG

---

### Post by Jazzy_Jeff on 2009-11-17
If you can't get the live cd to work try downloading the alternate install disk. It is a text based install but easy to install. Here is a link for you [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate).

---

### Post by Metal Giant on 2009-11-17
Thanks Jazzy,

I've just downloaded the alternative text-based version of kubuntu and there's no success. I put the CD in the drive, power up and a few seconds later, "Operating System Not Found", which I shall hereto refer to as OSNF!

I notice now that even my simple Darik's Boot&Nuke CD is not being seen on power-up, with that in the drive it's straight to OSNF (do not pass Go). I reset the settings in my BIOS, checked the CD drive was first to be checked (it is), reboot again with B&N and Kubuntu CD's respectively. Nothing.

Hmmmm?

---

### Post by ST3ALTHPSYCH0 on 2009-11-17
Double check that you have the proper drive channel selected for your primary. I don't know if this is an option in your BIOS, but in mine you set the boot order on one screen, then, on a totally different screen, you tell the mobo which of each type of drive is primary. 
You might also try setting every boot option to CD, or setting all besides the first to None until install is complete (just remember to set it back when the installer reboots!)

---

### Post by nperry on 2009-11-17
If the above seems to not fix the issue, next thing to check is the md5sum to do this;

1. run this command within the dir where the .iso is held. (Change isofile.iso to right name)
> md5sum isofile.iso
2.Output should look like.
> 24ea1163ea6c9f5dae77de8c49ee7c0
3.Compare that against the Hashes table
[Found here]("https://help.ubuntu.com/community/UbuntuHashes")

Thanks,
Neil Perry

---

### Post by Metal Giant on 2009-11-17
Thanks for pitching in and helping me with this.

@ST3ALTHPSYCHO You might have to elaborate what you mean by "proper drive channel selected for your primary", I mean, I've looked at the four IDE "Drives" on the main page of the pheonixBIOS that pops up when I press F12. I've set the first two to [NONE] and the third to [CD-ROM CCD-48X6S-(SM)] with the last just set to [IDE Drive 4:] (although I go in its settings and choose CD-ROM, when I come out it just says that).

The Boot order sequence is set to: 1, CD-ROM Drive 2, +Hard Drive 3, !+Diskette 4, !Legacy LAN Card.

I accept these settings, boot up. Nothing.

@nperry I can't get a cursor to type in any commands. I just get a black screen with the "OSNF" message and any attempt to type on the keyboard just repeats the message. If I understand correctly, the md5sum is to check if the liveCD has burned correctly (is that right?) and I'm 90% sure it has as all the CD's I've burned work in other machines.

MG

---

### Post by QLee on 2009-11-17
Metal Giant,

Most of what you wrote sounds like the system isn't trying to boot from the CD drive.

For a visual indication, when you boot, does the CD drive light hit first and spin up the CD before the HDD light hits and doesn't find an OS?

---

### Post by HarrisonNapper on 2009-11-17
Also, on your installation disk did you burn it with an image burner or did you copy the iso to the cd?

In other words, where did you get the LiveCD and/or how did you create it? Have you tried it on other PCs?

If the cd just contains suchandsuch.iso, it will be skipped during boot.

---

### Post by Metal Giant on 2009-11-17
@QLee I'm certain that the CD Drive is being checked on powerup. It lights up, the disk spins, everything seems normal before I get the OSNF. Plus, the boot order in the BIOS is set to check the CD-ROM first/

@HarrisonNapper Definitely a good CD. I burned the image with an image burner not just copied the .iso. All the CD's I've tested work on other machines, so that's Linux Ubuntu, Kubuntu, Xubuntu, Fedora, Mint, and Windows XP. All disks fail to startUp despite the CD Drive whizzing around first. Then, black screen and "Operating System Not Found".

It's a conundrum isn't it?

---

### Post by Metal Giant on 2009-11-17
I'll also add that even the Darik's Boot & Nuke CD I'd made to wipe the old system clean, that used to work before, now suffers a nil response like the rest. <shrugs>

---

### Post by QLee on 2009-11-17
Well, MG did state that his Windows disk wouldn't boot either, presumably, it is a professionally created disk.

---

### Post by QLee on 2009-11-17
> **Metal Giant said:**
> @QLee I'm certain that the CD Drive is being checked on powerup. It lights up, the disk spins, everything seems normal before I get the OSNF. Plus, the boot order in the BIOS is set to check the CD-ROM first/
...

It's a conundrum isn't it?

At this point, it looks a lot like a hardware problem, were you inside the case at all, are all the connections inside good?

---

### Post by Metal Giant on 2009-11-17
Hang on, I've just taken out the Kubuntu disk to check it on another PC again (it checks fine) I've put it back in the drive again, this time to carefully watch the lights on powerup as QLee suggests. Other than that, I've done nothing different.

I've just powered up again and for no reason whatsoever it seems to be working! I'm in the text-based install mode (I can live with that) but it's reading and trying to install. I mean, how weird is this?

I'll keep you posted as to how the install goes, I'm not confident. I think maybe she's haunted?

---

### Post by QLee on 2009-11-17
[QUOTE=Metal Giant]
I'll keep you posted as to how the install goes, I'm not confident. I think maybe she's haunted?[/QUOTE]

Yeah, haunted, or maybe a flaky laser or dirty lens, you did say it was an old system.

---

### Post by Metal Giant on 2009-11-17
...just while its working in the background partitioning the drive, I'll just say that yes the case was opened, I had been checking all the connections and they all seemed just fine. I'm worried that it is a hardware glitch somewhere. In fact, it probably has to be that? It's a good job it's only a spare machine. I'd just love to know whats making it so temperamental. Haunted theory looks the strongest one so far.

---

### Post by ST3ALTHPSYCH0 on 2009-11-17
I think that your optical drive is working on a "Dear John" letter! From the sounds of things, I'd start looking into a new drive if I were you.

---

### Post by Metal Giant on 2009-11-17
Agreed. In fact, as I remember, the place I picked it up from had it in the corner of a room with a wireless LAN connection. They had an aerial with a heavy magnetic base stuck to the top of the metal case over the CD-Drive. I remarked at the time that that probably wasnt a good idea. I wonder if that's the cause of my woes? But the drive worked before, so I'm clueless.

Anyway, 40% installed, which is a great result so far...

---

### Post by Metal Giant on 2009-11-17
Well, success! It finally decided to behave itself, I'm going to put it down to hardware glitchyness in the CD-ROM. So I guess this thread can be listed as [SOLVED] now?

Thanks you guys, for your assistance and ideas, what a thoroughly good bunch you are!

---

