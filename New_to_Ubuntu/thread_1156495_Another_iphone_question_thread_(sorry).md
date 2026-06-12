---
title: "Another iphone question thread (sorry)"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by model citizen on 2009-05-11
Hi,

I've recently upgraded to an iphone 3g 16gb (O2 - UK) and I've been trying for about 3 weeks to get it working in ubuntu 9.04 Jaunty with no success. I know about pwn player but if at all possible I would like to use the actual ipods built in music player. 

I've read all the guides and haven't managed to make anything work. I've jailbroken it on the latest firmware - 2.2.1 and can mount the filesystem on the ubuntu desktop - transferring files to and from the ipod is no problem. 

I've got amarok2 gtkpod and rhythmbox all downloaded, none of them worked. I've used rhythmbox before on my old ipod and liked it but I'd be glad to use anything with it. 

I havent got a powerful computer and no xp disc so virtual box or dual boot is a no-go. 

I activated and sync'd the iphone on a friends XP desktop that I can use but I dont want to keep hassling her. 

Any help would be really appreciated!

---

### Post by Dynaflow on 2009-05-12
Here you go:  [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

In particular, this section will be of interest: [https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

Have fun, and after you've got everything working, be sure to send Apple feedback on how much fun you had.

---

### Post by Garrovick on 2009-05-12
iPod and iPhones are iTunes only.  XP or OSX are the only choices.

---

### Post by Dynaflow on 2009-05-12
> **Garrovick said:**
> iPod and iPhones are iTunes only.  XP or OSX are the only choices.

Oh ye of little faith.

---

### Post by Garrovick on 2009-05-12
> **Dynaflow said:**
> Oh ye of little faith.

"Faith" is lost after almost 3 months of trying making my Apple stuff work as it was designed to work. Not as it "can, sort of work" with Linux.

My XP netbook solution worked the best, in that I regained "faith"

But then at least Ubuntu can play all DVDs, surf and e-mail. All by it's self.

Ubuntu is a fine alternate OS, but we don't need to make stuff up about stuff Ubuntu can not do.

---

### Post by Dynaflow on 2009-05-12
Believe me, I share your angst: [http://ubuntuforums.org/showthread.php?t=1150268](http://ubuntuforums.org/showthread.php?t=1150268).  In general, I consider Apple hardware to be a gigantic pain in the rear.

However, interesting things can be done with jailbroken iPods and iPhones, such as being made to play nice with Linux.  Have you tried the instructions linked above?

---

### Post by Garrovick on 2009-05-12
> **Dynaflow said:**
> Believe me, I share your angst: [http://ubuntuforums.org/showthread.php?t=1150268](http://ubuntuforums.org/showthread.php?t=1150268).  In general, I consider Apple hardware to be a gigantic pain in the rear.

However, interesting things can be done with jailbroken iPods and iPhones, such as being made to play nice with Linux.  Have you tried the instructions linked above?

No, but dozens of other "Attempts" not only here, and across the web. My Apples and my Ubuntu have officially divorced.

On the other hand, maybe some one good with Linux can "jail break" us an iTunes version to work with Linux.  Like in "iTunes Linux"?

---

### Post by model citizen on 2009-05-12
> **Dynaflow said:**
> Here you go:  [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

In particular, this section will be of interest: [https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

Have fun, and after you've got everything working, be sure to send Apple feedback on how much fun you had.

Thanks a LOT - I'm going to follow the guide now.

---

### Post by model citizen on 2009-05-13
It worked! Thanks again, it's great to have everything working in ubuntu instead of being reliant on XP.

---

### Post by Zane Chua on 2009-05-13
I dont want to create a new thread so can i put my question here? Thanks to DynaFlow above for the link but thats what i have tried. I can mount and unmount my phone properly. i have done everything properly. Amarok can show all my media files but the iPod app in my phone cant. BUT apparently the iPod app in my phone shows a song, One song actually. Thats a purchased song from itunes. I have no idea how to remove it and i think that is causing the problem. Anyone? I am using Amarok 1.4 and my iPhone is running on FW 2.2.1

EDIT :After finding the bloody song in /var/mobile/Media/Purchases. I deleted the whole directory of Purchases and as a result the song in the iPod app was gone BUT i still am unable to get the iPod app to read the songs.

---

### Post by Dynaflow on 2009-05-13
Are you using a third-party music player on the iPod itself, like PwnPlayer, or are you using the infernal machine's own, general-issue music player?

---

### Post by Zane Chua on 2009-05-13
I am currently using the default iPod app. No third party players like PwnPlayer and I still am not sure why it won't show up. I have done the firewire Guid like 3 times both before and after I deleted the purchases folder but the songs still aren't showing up.

---

### Post by Dynaflow on 2009-05-14
I think you may need to use a third-party app.

Another resource: [http://marcansoft.com/blog/2009/01/using-amarok-and-other-itunesdb-compatible-software-with-the-iphone-2x/](http://marcansoft.com/blog/2009/01/using-amarok-and-other-itunesdb-compatible-software-with-the-iphone-2x/)

---

### Post by Zane Chua on 2009-05-14
I see. I shall try something i have been thinking for these 2 days and i;ll update you if it works.

---

### Post by model citizen on 2009-05-15
Update: 

My iphone now isn't recognised on my friends XP with itunes - it just says it needs restoring. I don't care about this, I'd much rather it work on my ubuntu than her XP (and it could just be something I did?) but thought I'd mention it.

---

### Post by timcredible on 2009-05-15
> **Garrovick said:**
> iPod and iPhones are iTunes only.  XP or OSX are the only choices.

wrong!  all ipods are compatible with linux apps.  iphones are too if you jailbreak it.

---

### Post by Zane Chua on 2009-05-15
Just tried restoring the phone with iTunes and its perfectly clean now. But now ubuntu gives me

zane@Kyrtales:~$ iphone-mount
root@192.168.1.100's password: 
root@192.168.1.100's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
zane@Kyrtales:~$ iphone-umount
fusermount: entry for /media/ipod not found in /etc/mtab
root@192.168.1.100's password: 
zane@Kyrtales:~$

---

