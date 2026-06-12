---
title: "installation help"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by NachosTacos on 2010-01-13
hey guys, i kinda ran into this huge problem. i was running ubuntu for a while and when it came time to update to jaunty, i messed up the install and havent been able to get it right since.

so my neighbor found an old windows xp install disk and agve it to me, but it didnt have the pass, so now i wanna just get my linux back, but i cant get away from the windows install screen, since i never entered the correct pass. what should i do? i already have a copy of ubuntu 9.10 ready to go, but it wont start up when i restart my computer

any help would be appreciated

---

### Post by mbzn on 2010-01-13
Looks like your computer is booting from the hard drive, just change your first boot device to cd-rom in the bios and all should be fine.

---

### Post by NachosTacos on 2010-01-13
thanx, but i hate to be a pain... this is what i did. (keep in mind, im not the brightest crayon...) when i started my pc, and got to the boot menu, i changed the order, so the cd-rom was the first one, then i turned off the boot for the harddrive cause after i changed the order, it will was booting from the HD. so once i disabled it, and restarted my pc, it took me to a blk screen that said "media test failure" and "exiting PXE ROM" and it keeps repeating itself

i have a feeling im not doing something right. if ud like, i have yahoo messenger (s/n - aiichef) to speed things up

---

### Post by mbzn on 2010-01-13
I prefer to keep things on the forums so it could be helpful to others in future. This seems to be some problem with your bios settings. Please tell me what bios and motherboard you have.

---

### Post by NachosTacos on 2010-01-13
im not even sure what my bio is... and my motherboard? i guess what ur asking for is what kind of computer i have... its an HP pavillion zd7140us. and i honestly cant tell u the rest. i havent really messed with this thing since early last year. i kno its a pentium 4 processor

---

### Post by mbzn on 2010-01-13
Sometimes on notebooks you have an option to boot from other devices by pressing a certain key at startup.

---

### Post by NachosTacos on 2010-01-13
yea, it says press esc to change boot order, f10 to boot from setup and f12 to boot from LAN

---

### Post by dzon65 on 2010-01-13
Ok.So you were able to set the boot order to start from cd? Have you saved those settings? If so,you might wanna (if this is an old pc with a floppy ) try smart boot manager. Is there a possibility to boot from usb? If everything fails,you probably will have to upgrade your bios.But since you can't get into windows that would be a bit difficult.
Could you post the model?
Just read it,pentium 4?Then there's no flopy of course.Try saving the boot settings first.

---

### Post by NachosTacos on 2010-01-13
> **dzon65 said:**
> Ok.So you were able to set the boot order to start from cd? Have you saved those settings? If so,you might wanna (if this is an old pc with a floppy ) try smart boot manager. Is there a possibility to boot from usb? If everything fails,you probably will have to upgrade your bios.But since you can't get into windows that would be a bit difficult.
Could you post the model?

well i changed the order and when i restarted to boot from the disk, it never did... it just started up and took me to a blk screen and said that "the media failed" & "exiting PXE ROM"

i do believe this laptop is from 2004 and does not contain a floppy drive. i have an HP zd7140us, and it has a pentium 4

---

### Post by dzon65 on 2010-01-13
There should be a menu in bios where you 1)set to boot from cd 2) save those settings .Many pc's tend to keep there default settings.If you did that,and it still won't boot you will probably have to upgrade it from their site. Can you boot from usb ?

---

### Post by NachosTacos on 2010-01-13
sorry if im making this harder than it seems... but ill tell u everything, ok? lol

i turn on my pc, i hit ESC to change the boot order. once i hit that, a screen pops up with a list of 4 booting options (1. floppy diskette drive 2. atapi cd rom drive 3. hard drive 4. network adaptor and a 5th choice of going to the boot settings) i choose to go to the boot settings to change the order

now when i go to change the order (1. cd-rom drive 2. floppy 3. hd 4. network adap) i also disable the harddrive boot. then i save and restart, it takes me to that blk screen. that keeps repeating itself.

i kno i prolly lied, but i dont see a floppy drive on my laptop. but it says i do from the boot menu. sorry for any confusion.

---

### Post by clive littlewood on 2010-01-13
Hi

Do not disable the hardrive boot.

Just set the order as stated then SAVE the settings.

When no cd rom is in the drive it will skip to hardrive boot.

Hope that helps

Clive

---

### Post by NachosTacos on 2010-01-13
thanx clive. i re-enabled the hard drive boot, and saved. but it still seems to be booting up from the hard drive, cause i am still being redirected to the windows installation page.

---

### Post by ndefontenay on 2010-01-13
Hi.

you say you got a media failure when booting from the CD.
It could be that your CD is faulty. Burn your linux ISO to a new CD. 

It looks like you're doing everything else just fine.

1) You don't have a CD in and you got the windows password screen
2) you boot to CD and you got media failure.

Seems pretty straight forward to me:
1) your CD is not good
2) Your CD Rom is not working fine

Nico

---

### Post by NachosTacos on 2010-01-13
that makes alot of sense nico!

but i do have the CD in, i boot from the CD and it still takes me to the windows install screen (not the windows password screen)

but i totally get what ur saying... i was thinking of running a test drive with the disk on my desktop, but i wasnt sure if it would be able to support it consdering this desktop is pretty old

---

### Post by dzon65 on 2010-01-13
Yes,you could make a new cd.Make sure you burn it at a low speed (2X for cd is fine).Put the cd in.You could leave the settings as thy are but I'd rather set them to boot from cd first.Scroll  through your bios menu until you see "save settings" (mostly in the first column).Boot.If you still got the same line wrong media or something,them I'm pretty sure it's the bios that can't handle it.I had EXACTLY the same on  an  old pc trying to put minimal ubuntu on it.Although everything in the bios was set as it should be,it simply was a no go.I tried several cd's,all of them failed to boot!Until I found some bios upgrade on compaq's site.Installed the upgrades,inserted the disk and it took off immidiately.

---

### Post by lisati on 2010-01-13
+1 for trying a new CD. Don't forget to use the "Burn as disk image" option.
See [here]("https://help.ubuntu.com/community/BurningIsoHowto") for more info

---

### Post by dzon65 on 2010-01-13
You might wanna go to this site,there's a bios update for your machine.Scroll alittle around there to make sureit's the wright type of HP.[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&product=392741](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&product=392741)

---

### Post by satismo on 2010-01-13
nachos...  pressing F10, is that your BIOS setup utility?  remember, you have to *save* changes to the BIOS before they will take effect.  if a newly burned CD (please, burn the disk "as image" to ensure the disk is an exact copy) still doesn't work, and you've saved the CD drive as the primary boot location in BIOS, the drive may be on the fritz.  one thing you may want to try is booting from a USB disk instead of CD -- if you have access to another computer that works (which i get the impression you do) boot into karmic on there, throw in a thumb drive, run usb-creator-gtk, follow the instructions.   when that's all done, throw your usb disk into the HP, and go back into BIOS -- choose USB as the primary boot.  *save* the changes before you exit.  good luck!

---

### Post by dzon65 on 2010-01-14
> **satismo said:**
> nachos...  pressing F10, is that your BIOS setup utility?  remember, you have to *save* changes to the BIOS before they will take effect.  if a newly burned CD (please, burn the disk "as image" to ensure the disk is an exact copy) still doesn't work, and you've saved the CD drive as the primary boot location in BIOS, the drive may be on the fritz.  one thing you may want to try is booting from a USB disk instead of CD -- if you have access to another computer that works (which i get the impression you do) boot into karmic on there, throw in a thumb drive, run usb-creator-gtk, follow the instructions.   when that's all done, throw your usb disk into the HP, and go back into BIOS -- choose USB as the primary boot.  *save* the changes before you exit.  good luck!

Exactly.And,if everything else fails,ther's only one option left.......swapping hd's.Takes a bit more work on a laptop but it can be done.

---

