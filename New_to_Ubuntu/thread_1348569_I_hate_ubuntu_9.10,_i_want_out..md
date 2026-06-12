---
title: "I hate ubuntu 9.10, i want out."
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-12-07
I would like to return to 9.04, i like 9.10's features. Runs slick and looks nice. But it is not stable enough, i left windows a year ago for a more stable Operating system and i got that [almost] with 9.04 had a few problems when i was starting but i did like the system. With 9.10 on the other hand i am not impressed. It has broke 3 times on me with the grub. I set it to security only updates and i still get the grub updates and they just ***** up my file system. I have had help from here and nothing seems to fix it. I want to know if i can downgrade to 9.04 from the boot disk for 9.10 which im using to get on here now. I dont think i have any blank disks around so is there an altern way to get this done. its really pissing me off /rage

---

### Post by halitech on 2009-12-07
the only feasible way to "downgrade" is to format and start over again by re-installing. If you have a seperate /home folder then this will be easy. 

Did you upgrade from 9.04 or did you do a fresh install of 9.10?

---

### Post by Merk42 on 2009-12-07
Well we could try and fix those issues, could you link to those threads?
As for downgrading without a CD, the only other way I know of is with a [USB drive](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by snowpine on 2009-12-07
> **Rave Gloves said:**
> I would like to return to 9.04, i like 9.10's features. Runs slick and looks nice. But it is not stable enough, i left windows a year ago for a more stable Operating system and i got that [almost] with 9.04 had a few problems when i was starting but i did like the system. With 9.10 on the other hand i am not impressed. It has broke 3 times on me with the grub. I set it to security only updates and i still get the grub updates and they just ***** up my file system. I have had help from here and nothing seems to fix it. I want to know if i can downgrade to 9.04 from the boot disk for 9.10 which im using to get on here now. I dont think i have any blank disks around so is there an altern way to get this done. its really pissing me off /rage

Hi Rave Gloves, you will need either a blank CD or a USB thumb drive for the 9.04 installer (you can't install 9.04 using the 9.10 installer, I think you already knew that). If you can't afford either, Canonical will send you a CD for free!

Ubuntu 9.10 is by no means a "stable" operating system (it's based on Debian Unstable), especially since they've introduced major new features like Grub 2. Sorry you had to learn that the hard way. I would recommend sticking with the LTS (long term support; currently 8.04) releases if stability is your #1 concern.

I bet, however, that if you are patient and ask the right questions, you'll be able to fix the grub problem and enjoy 9.10. Good luck!

---

### Post by zkriesse on 2009-12-07
Could you possible explain as to what issues you're having? Most likely it's something that could be resolved or at least I would hope that to be the case as Ubuntu 9.10 is very stable now. Please link to any threads you might have unanswered and or need help with as I'd be more than happy to help you with them.

---

### Post by zkriesse on 2009-12-07
> **snowpine said:**
> Hi Rave Gloves, you will need either a blank CD or a USB thumb drive for the 9.04 installer (you can't install 9.04 using the 9.10 installer, I think you already knew that). If you can't afford either, Canonical will send you a CD for free!

Ubuntu 9.10 is by no means a "stable" operating system (it's based on Debian Unstable), especially since they've introduced major new features like Grub 2. Sorry you had to learn that the hard way. I would recommend sticking with the LTS (long term support; currently 8.04) releases if stability is your #1 concern.

I bet, however, that if you are patient and ask the right questions, you'll be able to fix the grub problem and enjoy 9.10. Good luck!

Ah, 9.10 is pretty stable. You're right about the Grub but still...it's stable... :)

---

### Post by Rave Gloves on 2009-12-07
[http://ubuntuforums.org/showthread.php?t=1336769](http://ubuntuforums.org/showthread.php?t=1336769)

this was the tread that was made and i followed it all correctly. 

I think the grub is just a bit, sensitive. and just likes to kill your system ):

---

### Post by zkriesse on 2009-12-07
Do you use xchat? If so please tell me.

---

### Post by Rave Gloves on 2009-12-07
^ Remember im limited to what i can do, im on the "Try ubuntu" on the boot disk.

---

### Post by bodhi.zazen on 2009-12-07
Unfortuinately there is no easy way to downgrade.

Your options are to either fix your problems, or back up your data and re-install.

One suggestion moving forward, use a data partition for, well data, and multiple partitions to multiboot.

---

### Post by Rave Gloves on 2009-12-07
> **bodhi.zazen said:**
> Unfortuinately there is no easy way to downgrade.

Your options are to either fix your problems, or back up your data and re-install.

One suggestion moving forward, use a data partition for, well data, and multiple partitions to multiboot.

I will try to fix them, im getting help as we speak, and about the partition with my home folder, i was told about this on the 2nd break of the grub. I wasnt to sure how to go ahead with it so i just left it thinking my system would be fine for good this time.

---

### Post by Rave Gloves on 2009-12-08
Well, we seem to think the disk i first used had an error and its just been broke since day one beacuse of this. I have a few problems.

The disks still wont burn correctly, i have used a diffrent ISO burner with a 1x speed, a new iso downloaded from ubuntu.com and brand new cd's. Still the disk ether has an error or when i go to check the disk on boot, they screen goes black and thats it. 

Any sugestions this is very annoying, i really dont want to go through more disks.

Edit: tried another disk, gave me an "unable to boot cd" error whenever i tried to load any feature on the live boot screen

---

### Post by Locke_99GS on 2009-12-08
If you can get grub working correctly again, you can lock it to it's current version to prevent any more updates to it. (The same goes for any problematic packages)

---

### Post by Rave Gloves on 2009-12-08
> **Locke_99GS said:**
> If you can get grub working correctly again, you can lock it to it's current version to prevent any more updates to it. (The same goes for any problematic packages)

Yes but my system will still be pretty much broke as the disk seemed to have an error when i first installed, what im trying to do now is burn a working disk to back up my memory from my partion. There seems to be an error on all disks i burn and it wont allow me to get root access to be able to copy the files onto an external HD.

---

### Post by t0p on 2009-12-08
If you've got a good .iso image and you're still burning bad CDs, the issue is with your CD drive.  Have you checked the integrity of your .iso?  If it's good, you'll need to use another computer to burn the CD.

An alternative approach: you can run a live session ("try Ubuntu") from a 9.10 disk, right?  There is an option to put Ubuntu onto a USB stick (I think it's called a "start up" stick or something similar).  If the issue is with your CD drive, maybe transferring the .iso to a USB stick and installing from that will work.

**EDIT:**

> **Rave Gloves said:**
> it wont allow me to get root access to be able to copy the files onto an external HD.

What do you mean, it "won't let you get root access"?  What exactly are you doing to try and get root access?  And what exactly is happening to stop you?

---

### Post by The_Pirate_King on 2009-12-08
> **Merk42 said:**
> Well we could try and fix those issues, could you link to those threads?
As for downgrading without a CD, the only other way I know of is with a [USB drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")
In my personal opinion using a USB drive to install is tricky and not worth it, it's better just to create another live CD, the live CD is a great tool to have as you can boot off it even if you have no HDD [as I am doing now]

---

### Post by Merk42 on 2009-12-08
> **The_Pirate_King said:**
> In my personal opinion using a USB drive to install is tricky and not worth it, it's better just to create another live CD, the live CD is a great tool to have as you can boot off it even if you have no HDD [as I am doing now]
But considering originally the person asked how to do it **without a CD** I suggested USB.

---

### Post by Locke_99GS on 2009-12-08
@The_Pirate_King: Tricky? You use the provided tool, point it to your flash drive and iso, and tell it to go. Done. I do this all the time. Boots far faster than the CD, and you can even have it store data (settings, upgrades, whatever) to the flash drive.

---

### Post by Rave Gloves on 2009-12-08
I will need to find a diffrent laptop then, i dont think i have any black Disks ether, so this may prove a problem. I will go on a look for another laptop. and report back to this thread if it worked. Also Putting it on a usb stick with a disk that has errors would still give me an iso with errors, am i right?

---

### Post by t0p on 2009-12-08
> **Rave Gloves said:**
> I will need to find a diffrent laptop then, i dont think i have any black Disks ether, so this may prove a problem. I will go on a look for another laptop. and report back to this thread if it worked. Also Putting it on a usb stick with a disk that has errors would still give me an iso with errors, am i right?

You said that the *disk* had errors, but that you had downloaded a good .iso.  If you have a good .iso, you can put it on a USB stick and it will be still good.  When you transfer an .iso to a flash stick, it does not involve physical burning.  So a good .iso transferred to a flash stick will be good.

**EDIT:** Check the integrity of the .iso, as explained [here]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by Locke_99GS on 2009-12-08
Once the LiveCD iso is burned (or imaged to a USB drive) you'll be able to test it's integrity from the menu that appears when you boot it.

---

### Post by running_rabbit07 on 2009-12-08
Normally I would recommend using unetbootin, but it doesn't work with grub 2, yet. I recommend getting Jaunty back on there if possible. Karmic still has too many bugs for a production system.

---

### Post by Rave Gloves on 2009-12-08
Integrity of the iso is fine, I think i will indeed get jaunty back. Before i go doing anything. If i live boot with jaunty cd. I will still be able to Access my partion and get my data?

---

### Post by Locke_99GS on 2009-12-08
unetbootin can also download iso's itself. I unsure if you can have it download certain versions of distro's, though.

edit: Rave, yes you can.

---

### Post by running_rabbit07 on 2009-12-08
Yes, you should be able to do that. I would make a /home during the next install. It will make life much easier in the future.

---

### Post by Rave Gloves on 2009-12-08
> **running_rabbit07 said:**
> Yes, you should be able to do that. I would make a /home during the next install. It will make life much easier in the future.

How is it i would go about this?, When the partion screen comes up make one there?

---

### Post by Rave Gloves on 2009-12-08
I cant seem where to download Jaunty, Ubuntu.com only has 9.10 and 8.04.

---

### Post by running_rabbit07 on 2009-12-08
> **Rave Gloves said:**
> How is it i would go about this?, When the partion screen comes up make one there?

Yes. Make one partition of about 8-10 gigs for / and one partition as big as you want for /home, and a 1-2 gig swap partition.

---

### Post by Locke_99GS on 2009-12-08
Jaunty: [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

---

### Post by wojox on 2009-12-08
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by t0p on 2009-12-08
Info [here]("http://www.psychocats.net/ubuntu/installseparatehome") on how to make yourself a separate home directory during installation of Ubuntu.

---

### Post by grief -l on 2009-12-08
> Yes but my system will still be pretty much broke as the disk seemed to have an error when i first installed, what im trying to do now is burn a working disk to back up my memory from my partion. There seems to be an error on all disks i burn and it wont allow me to get root access to be able to copy the files onto an external HD.
 
I burned about a dozen .iso's on CD-RWs and none of them worked. Burned on CD-R and every one of them worked first time.

---

### Post by Sylslay on 2009-12-08
I back to Juanty today , it's faster on my laptop.

[http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso)

here is how install (in windows BTW, but is descripton for linux )
and make boot USB Drive:

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

I think that Kramic is much more improve since realisce but juanty is better in my case.

Had 1200 point in glxgears in Karmic,
Have 1600 point in Juanty now,

but youtube movie are beter whan I play them in Karmic and firefox 3,55, no chooping on full sceen.
Back to Juanty after testing Karmic since alpha6 and waiting for 10.4

8.04 is good for my hardwere,
8.10 coludn.t switch on,
9.04 is good for my hardere
9.10 is just ok,
10.04 will be good?;)

---

### Post by Rave Gloves on 2009-12-09
> **Sylslay said:**
> I back to Juanty today , it's faster on my laptop.

[http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso)

here is how install (in windows BTW, but is descripton for linux )
and make boot USB Drive:

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

I think that Kramic is much more improve since realisce but juanty is better in my case.

Had 1200 point in glxgears in Karmic,
Have 1600 point in Juanty now,

but youtube movie are beter whan I play them in Karmic and firefox 3,55, no chooping on full sceen.
Back to Juanty after testing Karmic since alpha6 and waiting for 10.4

8.04 is good for my hardwere,
8.10 coludn.t switch on,
9.04 is good for my hardere
9.10 is just ok,
10.04 will be good?;)

Thanks for the links, i will check it out when im back from work. And about 10.04 hopefully it will be great, its lts so hopefully it will be good (:

---

### Post by m4tic on 2009-12-09
Is there a way to install the old grub not the new grub

---

### Post by Rave Gloves on 2009-12-09
> **m4tic said:**
> Is there a way to install the old grub not the new grub

I dont think im going to bother, we suspect it was the disk drive in an old laptop i use to burn the disks, it may have had an error on the disk and my system has slowly got worse, im happy with 9.04, i just need to find another laptop to burn the disk OR do it on a USB stick.

---

### Post by Sylslay on 2009-12-09
[http://www.pendrivelinux.com/ubuntu-9-04-flash-drive-install-from-cd/](http://www.pendrivelinux.com/ubuntu-9-04-flash-drive-install-from-cd/) 

or you go to Softwere centre in 9.10 ,  type 'unetbootin', install ubuntu*.iso on usb key,

---

### Post by Rave Gloves on 2009-12-09
For some reason this is taking up more than 2gigs, i found a 2 gig memory stick and when i try to extract onto the memory stick its using it all up ):

---

### Post by Rave Gloves on 2009-12-09
Update, i found how to boot the usb, but when i do it comes up 

"could not find Kernel "linux""

Dose this mean the ISO in the usb isnt right?

---

### Post by nothingspecial on 2009-12-09
As long as you have an iso image of 9.04 I would recommend formatting the usb stick to Fat32 first.

I`ve had problems in the past when trying to do this without doing that in the past.

---

### Post by TheLoneHoot on 2009-12-14
Hope this isn't too OT but...

...I also want to "downgrade" from Karmic back to Jaunty.  I have the actual 9.04 CD from Canonical.  The problem is, I'm such a neophyte that I don't even know how to get it to boot from the CD!  :oops:

I put the CD in and restart the machine, but it boots right to the 9.10 login screen.  Someone told me to either hold down or press F8 (or F10) while restarting to get to a boot menu, but no combinations of key presses worked at all.

Do I have to reformat my HDD to get it to boot from the CD?  I don't mind doing this if necessary as I have backed up my files, etc., and I'm not running any other OS (not a dual boot set up, etc.).

---

### Post by sports fan Matt on 2009-12-14
On my lenovo machine it's F12..Could that be a possibility?

---

### Post by mikewhatever on 2009-12-14
Karmic rules.:twisted::-P There is no escape.

---

### Post by Fidelio on 2009-12-14
> **TheLoneHoot said:**
> Hope this isn't too OT but...

...I also want to "downgrade" from Karmic back to Jaunty.  I have the actual 9.04 CD from Canonical.  The problem is, I'm such a neophyte that I don't even know how to get it to boot from the CD!  :oops:

I put the CD in and restart the machine, but it boots right to the 9.10 login screen.  Someone told me to either hold down or press F8 (or F10) while restarting to get to a boot menu, but no combinations of key presses worked at all.

Do I have to reformat my HDD to get it to boot from the CD?  I don't mind doing this if necessary as I have backed up my files, etc., and I'm not running any other OS (not a dual boot set up, etc.).
You don't need to reformat to boot from the CD. You just need to get into the BIOS to choose the boot options. Sometimes it's F8, sometimes is del sometimes its something else. Depends on your motherboard.

---

### Post by Geoff918 on 2009-12-14
It's usually going to be one of the F-keys or ESC or DEL.

When your system first turns on most BIOS will have something on the screen somewhere that says "Setup Options" or something to that effect. Maybe even Boot Selection. :)

---

### Post by running_rabbit07 on 2009-12-14
My HP laptops are F2. My Dell Desktop is F12. And my Lenovo Desktop is F12.

---

### Post by slimjimmy23 on 2009-12-14
You have to set your BIOS to boot from the CD instead of going straight to the OS, usually to get the BIOS you press F2 or F8 or F12, etc. immediately after turning on the computer.

---

### Post by running_rabbit07 on 2009-12-14
You can ussually just go to the boot menu if you are doing this for a one time thing. If you plan to boot from CD often, then you may want to make the change in bios.

---

### Post by slimjimmy23 on 2009-12-14
> December 5th,2009, Metallica made my ears bleed in Las Vegas!

Thats strange, I saw Kiss live in Houston on the 5th, my ears rang for 2 days :D

---

### Post by User3k on 2009-12-14
I was having a lot of issues with Ubuntu 9.10. I was thinking of just going to 9.04 or just using Suse 11.2 only. But I decided to try one more thing before I gave up. I installed Xubuntu 9.10 and that, so far, is working out great. So I am sticking with that one for now even though my hardware can handle much more.

---

### Post by running_rabbit07 on 2009-12-14
> **slimjimmy23 said:**
> Thats strange, I saw Kiss live in Houston on the 5th, my ears rang for 2 days :D

Mine rang for days also. My left ear actually bled. Next time I am taking a box of ear plugs to sell. There were  people who brought there kids and left early because it was too loud.

---

### Post by slimjimmy23 on 2009-12-14
My ears have only bled once and that was when I was in the same room as my little cousin watching some crap on Disney channel.

---

### Post by cartisdm on 2009-12-14
> **slimjimmy23 said:**
> My ears have only bled once and that was when I was in the same room as my little cousin watching some crap on Disney channel.

Dude, don't hate on the Disney channel, that's where Miley Cyrus got her start!

....wait, you do like Hannah Montana right?

---

### Post by TheLoneHoot on 2009-12-14
Wait, what was this thread about again?  :lol:

Well, I tried all those keys, and ESC seemed to get me into a menu, but it was a menu that only offered various versions of the 9.10 kernel.:confused:

So for whatever reason I don't think mine is going to let me boot from the CD with 9.10 installed (which completely doesn't make any sense, but I don't see any evidence to the contrary either).  So if I just want to remove 9.10 first, what would you recommend that would allow me to do that and still boot 9.04 from the CD (to install 9.04)?

And I know this sounds completely stooopyd, but remember this is "Absolute Beginner Talk" help, so is there a simple (non-malicious) command to reformat the drive or whatever?  Sorry for the Uber-n00ber questions, but I'm not really a computer guy (in fact that's part of why I am trying to stay with Ubuntu - to not have to deal with a lot of breakdowns like Windows - which right now is feeling pretty ironic).

---

### Post by TheLoneHoot on 2009-12-14
Well, no reply may be necessary to my question/situation.  Then again...

...can't tell yet but...

...for now, the problems I was having with 9.10 (video playback in FF 3.5.5) seem to have inexplicably cleared up.  :shock: :shock: :shock:

I didn't make any changes (that I'm aware of) or tweak any settings since the last time I posted or rebooted (okay, rebooting was SEVERAL times), but it seems to be completely fixed.

Weird.  :rolleyes:

Anyway, thanks to everyone trying to help.  I appreciate the true "Ubuntu" spirit when others try to pitch in to help a guy like me.  :D

---

