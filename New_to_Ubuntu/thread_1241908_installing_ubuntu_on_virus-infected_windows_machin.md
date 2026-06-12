---
title: "installing ubuntu on virus-infected windows machine"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by leyo on 2009-08-16
Hi,

I stupidly managed to acquire the rather virulent rootkit.pakes.m trojan on my laptop which is running Windows XP. AFter faffing around trying to get rid of it and failing, the machine is now only managing to boot up in safe mode. Since I've been toying with the idea of switching to linux for a while, I thought this might be the moment.

Is there any way I should modify the ubuntu installation process to take into account the fact that windows xp is currently failing to boot properly (it gets stuck loading the desktop)? Will that cause problems for the ubuntu installation?

Any advice appreciated.

Thanks!

Leyo

---

### Post by oldos2er on 2009-08-16
Do you want to keep your Windows partition(s), or not?

---

### Post by mcduck on 2009-08-16
> **leyo said:**
> Hi,

I stupidly managed to acquire the rather virulent rootkit.pakes.m trojan on my laptop which is running Windows XP. AFter faffing around trying to get rid of it and failing, the machine is now only managing to boot up in safe mode. Since I've been toying with the idea of switching to linux for a while, I thought this might be the moment.

Is there any way I should modify the ubuntu installation process to take into account the fact that windows xp is currently failing to boot properly (it gets stuck loading the desktop)? Will that cause problems for the ubuntu installation?

Any advice appreciated.

Thanks!

Leyo

If you are not intending to keep the Windows, then no. Just boot from the Ubuntu CD and let Ubuntu's installer use the whole drive.

If you want to copy your files from the Windows to some USB stick or something you can do that from the Ubuntu CD before you start the installer.

(and even if you plan on setting up dualboot there's no problem. Ubuntu simply couldn't care less if the Windows works or not. :D)

---

### Post by roger_1960 on 2009-08-16
Hi

If you are happy to reformat you hard drive as part of the installation, it should not cause a problem.  You would need to use the "use entire disk "  (or similar - cant recall the exact phrase) option when the installation gets to partitioning.  Do back up anything you need before doing the installation. (If you can)

---

### Post by bumanie on 2009-08-16
You should be able to dual boot as long as there is no virus/trojan affecting the MBR of the windows hard drive. You could try a virus with clamav off the live ubuntu cd and see if that clears the infection. I have had the experience of clam finding viruses/trojans that other anti-virus programs missed. f-prot is good too [This may]("http://njlinux.blogspot.com/2008/01/virus-scan-windows-using-linux-live-cd.html") help.

---

### Post by LewRockwell on 2009-08-16
> **leyo said:**
> I stupidly managed to acquire the rather virulent rootkit.pakes.m trojan on my laptop which is running Windows XP. AFter faffing around trying to get rid of it and failing, the machine is now only managing to boot up in safe mode. 

Any advice appreciated.

Thanks!

Leyo

you haven't got anything to lose at this point...download, md5sum, slow-burn, and boot this rescue disk up and see if it cures your nasties

[http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html](http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html)

.

---

### Post by LewRockwell on 2009-08-16
I also wanted to clarify that I recommend keeping the appropriate sized primary partition available for Windows(this is most easily accomplished where the Windows partition most often is found...at the beginning of the hard drive)

The reasoning for this is simple. If you decide you need windows for some reason...or you decide to sell your equipment to someone else...having Windows still on the machine(and keep it up to date) makes it more valuable to the average guy/gal on the street

but hey...it's your money

.

---

### Post by Paqman on 2009-08-16
> **oldos2er said:**
> Do you want to keep your Windows partition(s), or not?

Due to the rootkit, i'd strongly advise against trying to repair and keep the Windows install. Once a system has been rootkitted it should be nuked and reinstalled from scratch.

---

### Post by LewRockwell on 2009-08-16
> **Paqman said:**
> Due to the rootkit, i'd strongly advise against trying to repair and keep the Windows install. Once a system has been rootkitted it should be nuked and reinstalled from scratch.

I thought about that also...

I figured there might be a chance that the OP isn't really infected with what they think they have(maybe not a rootkit)

and...

Either way they will benefit from learning a little bit more about their equipment, operating systems, and killing nasties

Overall I do agree about doing a Secure Erase via a utility disk like Parted Magic and then after you know the disk is completely clean...partitioning and installing fresh operating systems

[http://partedmagic.com/](http://partedmagic.com/)

.

---

### Post by Old_Grey_Wolf on 2009-08-16
> **LewRockwell said:**
> you haven't got anything to lose at this point...download, md5sum, slow-burn, and boot this rescue disk up and see if it cures your nasties

[http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html](http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html)

.

I would give that rescue disk a try as well. Pakes.M is something like 3 years old. Most anti-virus software should deal with it nicely. Also, the rescue disk is a Linux OS that the rootkit can't hide from.

---

### Post by Paddy Landau on 2009-08-16
One thing that hasn't been mentioned is that if you intend to install [Wubi]("http://wubi-installer.org/"), then it'll be a no-go.

But if you do a standard install from a Live CD, then the previous comments are fine.

---

### Post by leyo on 2009-08-17
Wow, thanks very much for all your responses, it's really helpful.

Originally I was thinking of just wiping windows because I'd run out of ideas for how to get rid of the rootkit - I ran a bunch of programs like malwarebytes' antimalware, spybot search and destroy, AVG which detected/identified the rootkit as soon as it got into the system. I used HijackThis and ran the log through ComputerHope. After all that I thought I might have cleared it so I tried rebooting, but obviously not!

I still have the XP reinstallation CD which came with the laptop so I could just put that back on, but I'm a bit fed up with Windows and I'd like to try Ubuntu. I also get the impression reinstalling XP might be a hassle -- having to DL all the security fixes and service packs etc for hours.

I think I'll give that rescue disk a shot and see what happens. If it fixes it I could make a new partition to put Ubuntu on alongside XP, if it doesn't then I can just wipe the lot and start again. Luckily I've got all my data backed up on an external drive.

I have one other question -- my dad said one time he wiped win98 off an old laptop one time and he lost all the laptop-specific software and was unable to replace it, stuff to do with the touchpad and sleep mode. Is that likely to be a problem? My laptop is a Dell Inspiron 1300 if that helps.

Thanks again for all the help!

---

### Post by mcduck on 2009-08-17
> **leyo said:**
> 
I have one other question -- my dad said one time he wiped win98 off an old laptop one time and he lost all the laptop-specific software and was unable to replace it, stuff to do with the touchpad and sleep mode. Is that likely to be a problem? My laptop is a Dell Inspiron 1300 if that helps.

Thanks again for all the help!

That pretty much depends on what kind of CD's you got with your laptop. Usually all the default drivers and applications are included either on the vendor-specific restoration CD or on a separate disk(s). Recently some laptop manufacturers have instead started just putting all this stuff on a hidden partition in the laptop's hard drive, requiring you to create the restoration disk yourself. (all the *good* ones still provide CD's..)

Anyway, even if you don't have such disks available you will most likely be able to download all the drivers and other included applications from the laptop manufacturer's web site.

(of course with Ubuntu you won't need such things.. ;))

---

### Post by Crunchy the Headcrab on 2009-08-17
> **mcduck said:**
> 
(of course with Ubuntu you won't need such things.. ;))
I was going to say that.  The only problem with my laptop with Linux is that I made the mistake of buying an Asus (good brand btw) but it's loaded with leds and stuff.  I can't turn them off so now they just run all the time :guitar: 
Everything else more or less works out of the box.

---

### Post by leyo on 2009-08-17
Aha, there is a hidden special DellUtility partition. Though from googling it sounds like it's just got diagnostic stuff on it. CDs which came with it were just XP reinstallation disc, and a couple of CDs with trial versions of applications on them (like PaintshopPro). Which I'm not bothered about. Really I just want to make sure all my hardware will work ok. Sounds like it should be fine.

---

### Post by mcduck on 2009-08-17
> **Crunchy the Headcrab said:**
> I was going to say that.  The only problem with my laptop with Linux is that I made the mistake of buying an Asus (good brand btw) but it's loaded with leds and stuff.  I can't turn them off so now they just run all the time :guitar: 
Everything else more or less works out of the box.

Can't say much about those LEDs, I'm very happy owner of Asus laptop as well, but I went for a more business-like model without any decorations..

I the decoration LEDs don't have any hardware switch, or if there's no option in BIOS to turn them off, you might be doomed to live with the Christmas lighting on.. ;)

By the way, I can turn the only extra led I have, the mail led, on & off by running "sudo echo 1 > /sys/class/leds/asus\:\:mail/brightness". (echo 0 to tuen the light off). You could check if there's anything related to your extra LEDs in the /sys/class/leds-directory..)

---

### Post by Paddy Landau on 2009-08-17
> **leyo said:**
> I still have the XP reinstallation CD which came with the laptop...As it came with the laptop, that will be intended to fully restore the computer to its factory-default status. Of course, you will lose all data that's already on the hard drive, but you already knew that.

If you want to dual-boot Windows and Ubuntu, then make your life easier and get your Windows working first. The Windows factory installation disks usually wipe the entire drive when they install.

To make it even easier, if the installation disk gives you the option, install Windows on only half the drive and leave the other half unused. You can use that half for Ubuntu.

---

### Post by mcduck on 2009-08-17
> **leyo said:**
> Aha, there is a hidden special DellUtility partition. Though from googling it sounds like it's just got diagnostic stuff on it. CDs which came with it were just XP reinstallation disc, and a couple of CDs with trial versions of applications on them (like PaintshopPro). Which I'm not bothered about. Really I just want to make sure all my hardware will work ok. Sounds like it should be fine.

If the restoration disk is marked with the manufacturer's brand (instead of being a normal Windows install disk) and is named as "restoration CD" or anything similar it will contain all the required drivers.

---

### Post by leyo on 2009-08-17
> **mcduck said:**
> If the restoration disk is marked with the manufacturer's brand (instead of being a normal Windows install disk) and is named as "restoration CD" or anything similar it will contain all the required drivers.

Great! That's exactly what I have.

Thanks everybody for the advice to try the Avira rescue CD but I couldn't get it to work due to a bug of some kind, and nor did a BitDefender rescue CD -- gave me a very strange set of error messages including "kernel panic"! (I am not tech savvy enough to have any idea what that means)

I think I have to go for the complete format and reinstallation.

---

### Post by egalvan on 2009-08-17
first, Dell still shows the downloads for this lappie...

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=pub&catid=&impid=&os=WW1&osl=en&SystemID=INSPIRON1300/B130](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=pub&catid=&impid=&os=WW1&osl=en&SystemID=INSPIRON1300/B130)


Second, the original install CD that Dell sent  you may NOT have  all the extra drivers you need...
you may need the Drivers CD that many Dell systems receive.

In any case, download all the appropriate stuff from Dell, and burn your own driver cd...
it's what I do for all my computers.

You can install Windows-XP, and leave it alone...
you don't HAVE to update it, if you will not be using it... :)

My IBM ThinkPad T40 is set up this way...
Ubuntu and Puppy for the *nix stuff, 
and an un-used XP that is updated about once a month...

---

### Post by Old_Grey_Wolf on 2009-08-17
> **leyo said:**
> Thanks everybody for the advice to try the Avira rescue CD but I couldn't get it to work due to a bug of some kind, and nor did a BitDefender rescue CD -- gave me a very strange set of error messages including "kernel panic"! (I am not tech savvy enough to have any idea what that means)

I think I have to go for the complete format and reinstallation.

A complete format and reinstall may actually be the best solution. I looked up my own post on another forum from when I discovered a new variant of Pakes. The thread is [here]("http://www.dslreports.com/forum/remark,19884237?hilite=oldgraywolf"). It wasn't detected by the anti-virus vendors yet.

Pakes is a downloader. It is used to download other malware. So, you may have other nasties on your machine. In my case; because of the firewall, it wasn't able to download any malware. It was Pakes' attempt to access the Internet that alerted me to its presence.

---

### Post by leyo on 2009-08-18
Thanks old_gray_wolf and egalvan, I went for the complete wipe and XP reinstall, v. successful! Though I struggled to get all the drivers off the Dell website, they have some special downloader program which is really crap. Anyway I guess now I have them I can burn them onto a CD in case of doing this again.

I'm going to try installing Ubuntu now, wish me luck. :)

I'm slightly confused about what's going to happen with drivers and things, though from what I understand with Ubuntu it's not necessary to go hunting for drivers in the same way as with XP. See what happens, there's nothing to lose I think.

---

### Post by Schendje on 2009-08-18
> **leyo said:**
> I'm slightly confused about what's going to happen with drivers and things, though from what I understand with Ubuntu it's not necessary to go hunting for drivers in the same way as with XP. See what happens, there's nothing to lose I think.

You understand correctly. ;)

---

### Post by leyo on 2009-08-18
> **Schendje said:**
> You understand correctly. ;)

Great! That sounds ... amazing. It was definitely a bit of a hassle trying to get the Dell website to cough up all the necessary drivers (what a crap website for such a big manufacturer).

---

### Post by Schendje on 2009-08-18
As far as I know, all manufacturer driver websites are like that. Just want a driver? First, input your location, language, gender and BMI, so we can help you better. :lolflag:

Good luck!

---

### Post by leyo on 2009-08-18
Thanks again for all the help everybody, I managed to install Ubuntu alongside XP and so far everything's just peachy!

Only difficulty was getting the wireless to work, as I tried in vain to use ndiswrapper to install the driver, but the script located here:

[http://ubuntuforums.org/showthread.php?t=1203415](http://ubuntuforums.org/showthread.php?t=1203415)

worked like a dream.

---

### Post by egalvan on 2009-08-21
> **leyo said:**
> Though I struggled to get all the drivers off the Dell website, **they have some special downloader program which is really crap. **

I've been using FireFox for over two years, before that used IE...

I NEVER had to use "some special downloader program"...

Nor have I given any information....

just clicked on "download now" and down it came...

the url i gave in my prev post is a direct link to the drivers you were looking for.


(yeah, an older post, but I wanted to show folks that Dell does not require anything special...
neither have HP or IBM, for that matter.)

---

