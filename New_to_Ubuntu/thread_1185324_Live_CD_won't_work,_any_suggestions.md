---
title: "Live CD won't work, any suggestions?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by IcedEarth UK on 2009-06-12
First time user here, so bare with me :(
 
I downloaded Ubuntu 9.04 Desktop from the Ubuntu website, and I then downloaded the MD5 summer to verify the download. The codes matched exactly according to the Ubuntu hashes, so I know the downloaded ISO was 100% intact. 
 
I then did a bit of reading and found 3 ways in which I could run Ubuntu:
 
Virtual Machine
Dual Boot
Wubi
 
I chose Wubi, due to the fact that I thought it would be great to get to know Linux before I go through the pain of reinstalling Windows to create a partition. 
 
Anyways, moving swiftly on :D
 
I created a Ubuntu CD using InfraRecorder. I tried booting the 'Live' CD in Windows using autorun and I get a 'Drive Not Ready' error. 
 
I thought it may have been a dodgy disc, so instead I created a bootable USB drive, but I get the exact same error. 
 
By this time I was getting confused, and so I manually downloaded Wubi and tried running that. I get the exact same error!
 
Does anyone know how I can get my Ubuntu Live CD to work? I know the ISO is intact, I just don't know what I'm doing wrong from that point on :(
 
Sorry to be a pain, I know you must have discussed this plenty of times on the forums already. But I seem to have done most of the research and still haven't found a solution.

---

### Post by Mornedhel on 2009-06-12
You missed one of the ways you can run Ubuntu. Running as a LiveCD is by far the most common way of testing Ubuntu as well as hardware compatibility issues.

Just insert your CD, reboot, make sure you are booting from the CD (change the boot order in the BIOS for instance), and select "Run without installing" (not the exact wording).

---

### Post by s.fox on 2009-06-12
> **IcedEarth UK said:**
> 
 
I created a Ubuntu CD using InfraRecorder. I tried booting the 'Live' CD in Windows using autorun and I get a 'Drive Not Ready' error.

Hi and welcome to the forums :) ,

Do you mean you tried to run the LiveCD from within windows?    If you are then you will need to alter your boot order to make it have cd drives as #1.  [Here]("http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm") is a guide on how to do so.

-Ash R

---

### Post by Michael.Godawski on 2009-06-12
hi, 

that's true. Just boot with the Ubuntu CD and start the live session. 

Just a hint for the future: we have a great community based documentation which answers a lot of common questions

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

I don't want to shoo you away, but it is good to have more than one place to search for anwers. ;)

---

### Post by IcedEarth UK on 2009-06-12
No probs, I've been using several sites to gather my information. Including:

[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

This has been a great site for advice, I shall also check the community section in future. Thanks mate.

I tried booting from the CD, and it worked. It came to a screen were I had the option to check the integrity of the disc. 2 errors were found :(

Anyhoo, I decided to try and load it up anyway. I chose the 'Try Ubuntu without affecting your computer' option and it started loading, then came to a command line! I have no idea what to do with a command line, I thought it would take me a desktop environment. 

Is this normal, if so were do I go from here. If not, is it possibly from the two errors?

I will do some digging around and see if I can find any answers, I'm also going to try and boot from the USB drive that I prepared.

Thanks so far, I appreciate the advice. 

Iced

---

### Post by Mornedhel on 2009-06-12
> **IcedEarth UK said:**
> I tried booting from the CD, and it worked. It came to a screen were I had the option to check the integrity of the disc. 2 errors were found :(

Anyhoo, I decided to try and load it up anyway. I chose the 'Try Ubuntu without affecting your computer' option and it started loading, then came to a command line! I have no idea what to do with a command line, I thought it would take me a desktop environment. 

Is this normal, if so were do I go from here. If not, is it possibly from the two errors?

If it's the Live CD you're using, then it should indeed take you to a desktop environment, assuming you have no hardware issues. I'd try and download the ISO again, then burn it not too fast, and then boot it again. If it passes the integrity check and still drops you on a command line, it's probably a hardware compatibility issue. Could you post what kind of computer you have, including details ?

Just in case, you can also order an Ubuntu CD from here : [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

It's completely free, but it does take a few weeks before the CD ships. On the other hand, it's guaranteed errors-free.

---

### Post by IcedEarth UK on 2009-06-12
PC Stats would be a good place to start I suppose :)

C2D E6700 
DFI P35 DK
4GB G Skill PC8000
Gcube 3870x2
Corsair 520W HX
IDE DVD Drive
320GB Seagate Barracuda 7200.10
Audigy 4 Sound Card

I put all settings at stock, I didn't want my overclocks causing me any issues. 

The ISO seems to be 100% but I will download it again anyways. 

I did originally burn it at 8x due to a guide that I read, but I will try it at 4x this time. 

If that still doesn't work I may have to try grabbing one of those Cd's from ubuntu, thanks for the link. Much appreciated.

---

### Post by tea for one on 2009-06-12
If you are having difficulty with burning your CD and I assume from your forum name that you live in the UK, I suggest that you pay a visit to a high street newsgaent and purchase a copy of the current edition of Linux Format.

It has a Live DVD containing Ubuntu (9.04)including Kubuntu applications.

---

### Post by IcedEarth UK on 2009-06-13
I took your advice, tea. The magazine cost me £6.50 but if it came with an error free CD then it would be well worth the purchase. 

Well, I put it in, boot up and click the 'Try Linux without changing anything on your computer' 

It sent me to the exact same command line as the other two CD's i created myself :( See picture below:

[IMG]http://i149.photobucket.com/albums/s55/IcedEarth_2007/1244892696826.jpg?t=1244901789[/IMG]

Apologies for the quality, it was taken with my G1. 

I'm totally lost now, I have no idea what I could do to resolve the issue.

---

### Post by Therion on 2009-06-13
> **IcedEarth UK said:**
> I'm totally lost now, I have no idea what I could do to resolve the issue.
This is a long-shot, but what the heck... Boot to the CD and when you come to the *ubuntu@ubuntu:~$* prompt type in:  **startx** and press enter.

If it works you'll soon be looking at the Ubuntu desktop.  

If it doesn't there should at least be some error messages that might help troubleshoot the issue.

---

### Post by rogueleader12345 on 2009-06-13
Same thing with your USB drive. I boot Ubuntu off of my flash drive. You don't even really have to reorder your boot menu. With mine I hit F10 and select my flash drive. It's a one time thing. That way next time I start the computer up it boots off of the hard drive. But I don't know if your BIOS supports that.

---

### Post by IcedEarth UK on 2009-06-13
Same thing with my USB drive also, yea :(

I tried what you stated Therion, and this was the result, again I apologise for the picture quality:

[IMG]http://i149.photobucket.com/albums/s55/IcedEarth_2007/2009-06-13152204.jpg?t=1244903223[/IMG]

Three things I noticed were:

No Screens Found
No such file or directory, unable to connect to x server
No such process. Server error. 

I don't think this is important, but what the hell. I've currently got my PC hooked up to my 32" HDTV, I'm not sure whether this would cause any issues, but I thought I would bring it up due to the 'No Screens Found' error.

---

### Post by tea for one on 2009-06-13
When you boot the live CD/DVD, there is an option F4 for safe graphic mode. It might be worth a shot, probably with the PC using its correct monitor rather than a TV at the moment.

---

### Post by IcedEarth UK on 2009-06-13
> **tea for one said:**
> When you boot the live CD/DVD, there is an option F4 for safe graphic mode. It might be worth a shot, probably with the PC using its correct monitor rather than a TV at the moment.

I decided to make another bootable USB, and this time round it booted no problem :)

Seems like it was an issue with my optical drive all along, which means I now need to replace it lol

Thanks for the help anyways :) Much appreciated. It's a shame there isn't a 'rep+' feature for this forum.

---

### Post by tea for one on 2009-06-13
Excellent, I'm pleased that you have arrived at a workable desktop.

If you created a "persistent" storage area on your USB device, you will be able to save extra applications, data, settings, wallpapers etc.

Try and play a CD with your optical drive while in Ubuntu, it may still have some life left in it.

---

### Post by IcedEarth UK on 2009-06-13
May do:D

I must admit, it is the only thing in my PC that I have never upgraded. Just never seen the point up until now!

I don't need to save any extra applications at the moment. I just wanted to verify that Linux would work on my PC prior to actually installing :) I will be creating a partition on my Vista install tomorrow using Gparted and hopefully Linux should be on my system by tomorrow afternoon and I can start my learning curve :)

---

### Post by Old_Grey_Wolf on 2009-06-13
DO NOT change the partition size of Vista using Gparted. Use the Vista resize capability from within Vista. Vista does not behave well if you use Gparted to resize the partition.

In Vista Help and Support search for "shrink volume".

---

