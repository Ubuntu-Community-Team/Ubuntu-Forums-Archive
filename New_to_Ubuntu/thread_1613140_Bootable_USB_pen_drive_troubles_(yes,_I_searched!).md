---
title: "Bootable USB pen drive troubles (yes, I searched!)"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by RogerStenning on 2010-11-04
Morning all, first post here, so be gentle ;)

I'm looking to migrate from WinXPsp3 to a Linux distro; i've done a little homework obviously (why I'm here, lol),  and decided to see what all the hype was about; I therefore downloaded both the *ubuntu-10.10-desktop-i386.iso* distribution, along with the Universal USB installer, so as to burn the distributions to a bootable CD.

Well, no joy there, the drive didn't see the disk I made as bootable, so, given that the drive's four years old, figured, "ho hum, obviously on the way out", and tried a bootable USB pen drive instead. No joy. I got an error message, instead:

> No DEFAULT or UI configuration directive found
Boot:So, I guessed that it was a problem with the most recent distribution, went back and downloaded *ubuntu-10.04.1-desktop-i386.iso*, and repeated the pen Drive process. Same result, and the very same error message.

By now, this was, as you might imagine for a neophyte 46 year old non-technical twit, beginning to grate, so I had a look on here, found that there were problems with the Universal USB installer on recent distributions, and went for the alternative that was suggested, *unabootin*, to create the bootable USB pen drive...

Yep, you can see where this is going, can't you?

I got the self same error message. Confused and frustrated? You bet I am.

I can only assume that something's gone a tad, shall we say, fubar, in creating the bootable bits.

Question is, how the heck can this be fixed?

Thanks in advance for any and all assistance in this hair-thinning exercise ;-)

---

### Post by Temposs on 2010-11-04
Hello!

You should take a look at this page for making a bootable Ubuntu USB drive: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Scroll down to the "From Windows" section if you are using Windows. Try following those instructions. Follow the instructions in the "Booting the Computer from USB" section after that and let me know how it goes.

I think once you do this you will have a great experience with Ubuntu.

---

### Post by arochester on 2010-11-04
1)When making a disk you need to "burn an iso". That is a **special** operation which will fully create a Linux bootable disk. If you are "making the disk bootable" you are doing something wrong. Have a look at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

2) When you run the disk you need to change the BIOS/Boot Order so that the computer will boot from the disk before the Hard Drive. Similarly when you run the USB stick you need to change the BIOS/Boot Order so that the computer will boot from USB before the Hard Drive.

---

### Post by RogerStenning on 2010-11-04
> **Temposs said:**
> Hello!

You should take a look at this page for making a bootable Ubuntu USB drive: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Scroll down to the "From Windows" section if you are using Windows. Try following those instructions. Follow the instructions in the "Booting the Computer from USB" section after that and let me know how it goes.

I think once you do this you will have a great experience with Ubuntu.

OK, thanks - I'll have a look and give it a try :)

> **arochester said:**
> 1)When making a disk you need to "burn an iso". That is a **special**  operation which will fully create a Linux bootable disk. If you are  "making the disk bootable" you are doing something wrong. Have a look at  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

2) When you run the disk you need to change the BIOS/Boot Order so that  the computer will boot from the disk before the Hard Drive. Similarly  when you run the USB stick you need to change the BIOS/Boot Order so  that the computer will boot from USB before the Hard Drive.

Sorry, poor choice of words in my first post. I did indeed burn the ISO, but for some reason or other, the machine here failed to recognise it as a bootable CD. Hence the USB route.

Regarding booting sequences, the KT4 Ultra motherboard I've got in my machine (which built from the ground up by a friend a few years back, not shop-bought) has a BIOS feature that allows temporary suspension of the normal boot order (F11 on start-up/reboot), allowing you to select a one-off boot order. Despite this, it's failing to recognise the CD ROM that was burnt from the ISO as a boot disk, and proceeds to boot under windoze :(

The problem is now that the USB pen Drive is not running correctly; I believe that there's a problem with the bootability (for want of a better phrase) of the drive in the write process under both the *Universal USB installer* and [I]unabootin.

[/I]I'll have a look and try the first suggestion above from Temposs, and get back to you all*.*

Thanks for the replies :)

---

### Post by RogerStenning on 2010-11-04
Temposs -

OK, I think I know why the CD-ROM didn't work. It's unreadable. That's probably down to my somewhat rubbish CD/RW drive. No real surprises there, it's been giving me grief for a while. ho hum.

So, I extracted *usb-creator.exe* from the USB pen drive, which is, at least, readable, if not bootable, lol

I tried the process you suggested I follow, but it fell at the first hurdle, in that *usb-creator.exe* is not allowing either ISO selection I downloaded. It's recognising the pen drive, but not the ISOs.

Any ideas would be welcome, cause I'm totally stymied now :(

PS - the alternative package that's suggested in the article, *Unetbootin*, was one of the previous ports of call for creating the bootable USB drive, and that failed too :(

---

### Post by mastablasta on 2010-11-04
> **RogerStenning said:**
>  
I tried the process you suggested I follow, but it fell at the first hurdle, in that *usb-creator.exe* is not allowing either ISO selection I downloaded. It's recognising the pen drive, but not the ISOs.
 

 
what do you mean it's not recognising the ISO. you got the programme here: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
You told it which ISO to you (gave it a path to that ISO file) and it's not recognising it?
 
also did you check the md5sum on iso if the ISO downloaded correctly?

---

### Post by RogerStenning on 2010-11-04
> **mastablasta said:**
> what do you mean it's not recognising the ISO. you got the programme here: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
I got *usb-creator.exe* from the pen drive copy, the CD that was burnt being completely unreadable. The article ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)) suggested either reading that from the CD, or extracting it from the ISO using yet another package. It seemed easier - and faster - to extract it from the pen drive instead. I'll try the link you suggest instead, though frankly at this point, I don't hold out much hope of a successful resolution.

> You told it which ISO to you (gave it a path to that ISO file) and it's not recognising it?Yes, that's it exactly. It's not recognising the path to the ISO, which I find astounding, given that it's on the [IMG]http://www.practicalairsoft.co.uk/forums/censored.gif[/IMG] desktop. It's seeing the USB pen Drive, though. Fat lot of good that is, of course, since it's not seeing the [IMG]http://www.practicalairsoft.co.uk/forums/censored.gif[/IMG] ISOs (either of them) ](*,)

> also did you check the md5sum on iso if the ISO downloaded correctly?I wouldn't know an MD5 from a hole in the ground, mate. I'm a bus driver, not a techie :) The ISOs were both downloaded from the download page on the Ubuntu website at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) if that helps at all.

I'll report back shortly, after I've tried again.

Roger

---

### Post by RogerStenning on 2010-11-04
Right, partial success. LiveLinux is now on the stick, and while it failed to boot (the same error occurred, as expected), at least it'll run under windoze, although it's HORRIBLY slow like this. Took TEN MINUTES to load and run up.

Can't say as I've very impressed, thus far.

Thanks for the help, anyhow, folks. It's appreciated.

...A few minutes later...

Right, update time. Having wandered around the livelinux screen for a few minutes, the interface, once loaded, was fast enough; firefox loaded in seconds, which was agreeably nice, and while it hasn't got flash installed in it (which probably explains the swift loading!), it does at least give me an idea of what it's capable of to a very limited degree. The acid test will be to get the thing booted into Linux from the get go, and see what happens...

Ideas on the above would be most welcome, by the way. Frankly, that's got me totally stumped. From what I can see, there's no reason whatsoever that it should fail to boot from the USB drive, yet there we are, stuffed beyond reason in that department.

Anyhow, partial success, for which many thanks all :)

---

### Post by mastablasta on 2010-11-04
> **RogerStenning said:**
>  
Yes, that's it exactly. It's not recognising the path to the ISO, which I find astounding, given that it's on the [IMG]http://www.practicalairsoft.co.uk/forums/censored.gif[/IMG] desktop. It's seeing the USB pen Drive, though. Fat lot of good that is, of course, since it's not seeing the [IMG]http://www.practicalairsoft.co.uk/forums/censored.gif[/IMG] ISOs (either of them) ](*,)
 
 
strange. but maybe yoou have some antivirus preventing it to work porpperly or somehting.
 
i used Unetbootin. i downloaded the iso via torrent (as it is less likely to be corrupted on download. i downloaded it to my download folder (not desktop) and i also put unetbooting in the same folder. it found the iso file automaticly i believe.
 
it should be quite easy and all these USB boot creators are quite good and should work with no issues. i do think you must have done something wrong or have a strange/security setting on your computer. but, sorry i can't pinpoint exactly what is wrong to help you.
 
>  
 
I wouldn't know an MD5 from a hole in the ground, mate. I'm a bus driver, not a techie :) The ISOs were both downloaded from the download page on the Ubuntu website at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) if that helps at all.
 
 
 
More on md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
During download there could be small errors that occur withouth us noticing it. usually some movie or something will work fine but for OS they can be fatal. now all ISO files on server have a certain "code" and you can find the numbers and letters of that code on ubuntu site. 
 
after you download the iso and check this md5sum the numbers and letters that you get have to be exactly (!) the same. otherwise there was an error in download. you can i think also check your bootable USB like that to see if everything was put on it. 
 
 
if you are still having problem and you are not in a hurry you can always order a FREE CD from Ubuntu. yes, it's totally free. only it will take some time for them to ship it to you (5-7 weeks i believe).
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
 
you are going after desktop version ofcourse.

---

### Post by mastablasta on 2010-11-04
> **RogerStenning said:**
>  
Right, update time. Having wandered around the livelinux screen for a few minutes, the interface, once loaded, was fast enough; firefox loaded in seconds, which was agreeably nice, and while it hasn't got flash installed in it (which probably explains the swift loading!),  

 
nope firefox is indeed much faster in linux then windows and even with flash available it will pop up in almost no time.
 
for even faster access you could later install chromium.

---

### Post by RogerStenning on 2010-11-04
heh. Your post and my update above were posted at the same time, by the look of it, lol!

Anyhow...

Re antivirus stuff. Yeah, that was my thought at first, but I cannot find any settings that would affect the BIOS or its ability to boot (or in this case, fail to boot) off the USB slots. Bleeping odd, that :confused: For what it's worth, I';ve got AVG, SB S&D, Ad-Aware, and ZoneAlarm Free, running under Windoze; Ad-Aware and S&D are as and when required to scan for certain things that I've been hit with before over the years (another reason to get away from Windoze), although the S&T "Tea Timer" is always running to protect the machine.

Come to think of it, I've had massive problems getting windoze disks to be bootable, so there may be more to it that merely AV/FW settings. probably needs some ca$h thrown at an engineer to fix it, and frankly, I can't be asked. I'll haul out the drives and wipe them with magnets than spend any more money under windoze :twisted:

Re MD5 stuff. I'll have a look in the next week on that - no time today, unfortunately.

Heh. Close to two months for a CD from the folks at Ubuntu, eh? Well, it's a thought :) Nice that it's free, mind :mrgreen:

Anyhow, many thanks for the help, have a great balance to your week :)

Aha - just spotted your second reply :)

I'm in two minds about Chrome; I seem to recall comments about it not being too secure (privacy issues) from a while back. Dunno if that was solid or not, but it stuck in my head. At least with FF I can run NoScript, Leechblock, and Betterprivacy add-ons, to improve security here (as the advert says, "Every little helps"! ;))

Anyhow, many thanks again, and have a great week ):P

Roger

---

### Post by mastablasta on 2010-11-04
well i mean that some of your antivirus may have scnanned the iso and is now blocking access to the ISO file. just a guess. AVG is also known for it's false positives, though they might have got better lately.
 
my suspicion is based on the fact that i use avira antivirus and first thing it did after i created the USB drive was to have notified me that it blocked access to autorun.inf on the USB because it felt like it's malicious. i told him to ignore it but it happened again another time. the thing is this file was not malicious and is porbably there just to autostart Wubi installer in Windows.
 
then again it could also be some hardware issue but if you USB works ok then i think it would rule it out. 
 
Yes, Chrome reports to Google. But not Chromium (which is Chrome without google stuff).

---

### Post by RogerStenning on 2010-11-04
(This from the train!)

OK, last point first - ah, I didn't know that - thanks :) Chromium will be looked at, then :)

On AV... the curious thing here is that it was the booting sequence that failed, BEFORE windoze started to get loaded by default. Bleeping strange that. Thoughts?

Roger

---

### Post by mastablasta on 2010-11-05
> **RogerStenning said:**
> (On AV... the curious thing here is that it was the booting sequence that failed, BEFORE windoze started to get loaded by default. Bleeping strange that. Thoughts?

 
there is either:
- an error on your boot disk (error or boot disk wasn't created propperly for some reason). as i mentioned before AV could have cause this mess. to check this use the md5sum test.
 
- there could also be a hardware fault on the USB disk

---

### Post by phredbull on 2010-11-05
From what you said in post#8, it sounds like you *are* running a Live Ubuntu session off of the USB stick. Not sure what you meant by "it runs under Windoze"? How can another OS "run under Windoze"? Did you install Ubuntu via Wubi? It does take several minutes, (or longer) to boot the OS from USB. I have CrunchBang on a USB, and it takes about 10 minutes to boot, and when I had Mint Fluxbox on a USB, it took over an hour to boot, though once it was up and running, it *flew*.

I think you're all good. If you like what you see, just click the "Install Ubuntu" icon on the desktop...

---

### Post by migs73 on 2010-11-05
> **phredbull said:**
> From what you said in post#8, it sounds like you *are* running a Live Ubuntu session off of the USB stick. Not sure what you meant by "it runs under Windoze"? How can another OS "run under Windoze"? Did you install Ubuntu via Wubi? It does take several minutes, (or longer) to boot the OS from USB. I have CrunchBang on a USB, and it takes about 10 minutes to boot, and when I had Mint Fluxbox on a USB, it took over an hour to boot, though once it was up and running, it *flew*.

I think you're all good. If you like what you see, just click the "Install Ubuntu" icon on the desktop...

I assumed he meant a WUBI install. 

Roger, do you now get an option on booting to boot into Windows or Ubuntu?

If not, I'm confused? :confused:

---

### Post by phredbull on 2010-11-05
I think he is booted off the live USB. I read this whole thread, and there is no mention of Wubi.

---

### Post by migs73 on 2010-11-05
I thought if you plug in a LiveUSB whilst running Windows, there was an autorun for WUBI which gives the option to 'Install Inside Windows'.

Just assumed that was what had happened.

---

### Post by hsgeek on 2012-11-12
Hello  Folks!

Well, I encountered the same problem with at least two distros (Ubuntu 10.04 & Linux Mint 13). 

Various solutions suggested here or there didn't work (Changing name of syslinux file & like...)

This is what worked for me:

1: when creating USB use command line (gnome-terminal)
2: issue the following:  [COLOR=RoyalBlue]** usb-creator-gtk -n -s -i /home/path to the .iso/xxxxxx.iso**[/COLOR] (read the respective man page for details ;-) )
3: press enter and follow the instructions (usb drive selection, root password & like....)

Yahoo! you are done!

Guys, it worked in my case when all other solutions failed. 
However, let me warn you, this is not bound to work for  latest ubuntu release 12.10.
It spit out "Boot Error" message without any description:(

So give it a try and post back the results!

cheers,


zak

---

### Post by newb85 on 2012-11-12
Er...welcome to the forums, hsgeek.

However, this thread is two years old, and the release the OP was trying to install is now EOL.  I'm sure the OP has moved on.  And a moderator/staff will be along any minute to kill this thread.

Generally, it's best to stick to threads no more than a year old, as they will have more current information.

---

