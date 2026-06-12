---
title: "Help with live disk boot-up"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Javelin Dan on 2010-12-29
I'm currently running Xubuntu 9.1 (Karmic) on a Compaq Pressario laptop. I want to boot-up a live install disk of Puppy Linux just to familiarize myself with it for future use of rescuing a couple of old legacy computers. I can't get it to boot. Upon power-up, I hit the esc. key and it does stop at the boot menu, but I only have options to boot my current version of Xubuntu and several rescue versions - there is no choice to scroll to for booting from the disk. Would booting from a USB drive bypass this problem? If so, please explain the process. The install disk (for Puppy) is one I ordered online from OSDisk.com as I wasn't confident enough to try to create one on my own. I don't know for sure if it's OK, but when inserted into an old Dell Impressario laptop that I have, it does automatically stop at the boot menu and give me a choice to boot either the Windows XP or the Puppy (shown as Xubuntu on the boot menu). However, Windows is denying me acces as a type of hal.dll file is said to be missing, and I don't have the original Windows install disk to correct that either. Can anybody help with either or both of these problems? I've never used the command line so be gentle with me. Thanks.

---

### Post by QLee on 2010-12-29
[QUOTE=Javelin Dan]I'm currently running Xubuntu 9.1 (Karmic) on a Compaq Pressario laptop. I want to boot-up a live install disk of Puppy Linux just to familiarize myself with it for future use of rescuing a couple of old legacy computers. I can't get it to boot. Upon power-up, I hit the esc. key and it does stop at the boot menu, but I only have options to boot my current version of Xubuntu and several rescue versions - there is no choice to scroll to for booting from the disk....[/QUOTE]

From your description of symptoms it seems your Pressario is set in the BIOS to boot first from the  internal hard drive. That's why you only can boot to the GRUB menu. You'll need to enter the BIOS setup to change your computer to boot from the CD first. Usually the key to do that is shown on the screen at boot time. Maybe Del or F2, those are common ones but you could check the Pressario's documentation to find out. In addition there is often a key which can be pushed to get a boot screen to select which to boot from CD or harddrive, it might be F8 or something else which might show or be in the documentation.

---

### Post by mikewhatever on 2010-12-29
Are you sure you are booting from the cd at all? Double check that the boot order in the bios is correct. Also, as far as I know, you don't need to press Esc or any other key.

The "hal.dll is missing" is a grub error. See if any of the causes apply to you.
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)

---

### Post by Javelin Dan on 2010-12-29
I'm not sure if I'm confussing you - I apologise if I am. The Compaq is a new (1-year old) computer; the Dell is ancient. The Compaq is the one loaded with Xubuntu. That's where I can't get an option to boot the CD. The only words I see on start-up (lots of words flashing pretty fast) concerning boot is "press esc.". That stops the boot-up of Xubuntu, but I only have choices to select The current version or several rescue versions.
 
The Dell has Windows XP loaded which is useless on this old machine because it runs so slow. It was my plan to load Puppy on this, but because of the missing file, I can't. There is nothing on this compter I wish to save - is there a way to wipe the hard drive and do a clean install of Puppy on this? Sorry for the confusion.

---

### Post by Bucky Ball on 2010-12-29
Try looking in the manual for the button you press at boot to get into the BIOS ...

Delete, f1, f2, f12 ... could be any of them or something else. Look on very *first* screen.

---

### Post by QLee on 2010-12-29
[QUOTE=Javelin Dan]I'm not sure if I'm confussing you - I apologise if I am. The Compaq is a new (1-year old) computer; the Dell is ancient. The Compaq is the one loaded with Xubuntu. That's where I can't get an option to boot the CD. The only words I see on start-up (lots of words flashing pretty fast) concerning boot is "press esc.". That stops the boot-up of Xubuntu, but I only have choices to select The current version or several rescue versions.[/QUOTE]

You're not confusing me, although there is some confusion evident. It could be from trying to do two things at once, probably better to follow through one thing at a time. Either follow mikewhatever's suggestion and install Puppy on the old computer or try and boot the Puppy CD on the new computer.

On Pressario computer you're seeing the GRUB menu because it is set to boot from the internal hard drive first.

On the computer you will have to change the boot order in the system BIOS in order to boot from the bootable CD. You'll need to figure out what key to push while the system is booting in order to get into the system BIOS. Look in the manuals or post the model number. If you post the model number someone will google for you and advise if you don't want to google for yourself.

---

### Post by mikewhatever on 2010-12-29
> **Javelin Dan said:**
> ...
 
The Dell has Windows XP loaded which is useless on this old machine because it runs so slow. It was my plan to load Puppy on this, but because of the missing file, I can't. There is nothing on this compter I wish to save - is there a way to wipe the hard drive and do a clean install of Puppy on this? Sorry for the confusion.

You should be able to install Puppy regardless of the missing file because Linux doesn't use dll libraries. That error only affects Windows, and yes, you get an option to format the hard drive during the installation.

---

### Post by Javelin Dan on 2010-12-29
Thanks to all for your replies. 
 
To QLee & Bucky Ball: I will definately follow up on your suggestions. I didn't realize that I wasn't in BIOS yet where I would see my options. I'll figure out what key I need to press to get there.
 
To mikewhatever: When I start-up the Dell with the Puppy install disk inserted, it goes immediately to a black screen that gives me 2 choices for boot-up - Windows XP or Xubuntu (which has never been on this computer, so I'm assuming it's the Puppy install - right?). When I select Xubuntu, I get the error message teklling me access is denied due to the missing hal.dll file. I have no other options to click at that point other than to go back and boot up Windows. If I can still install Puppy by another means, How do I do it? I don't mean to be ADD by trying 2 things at once, but the experiment on the Compaq was just a precurser to Perminently installing Puppy on the Dell. Thanks again for your attention and sorry for my ignorance.

---

### Post by QLee on 2010-12-29
[QUOTE=Javelin Dan]...
To mikewhatever: When I start-up the Dell with the Puppy install disk inserted, it goes immediately to a black screen that gives me 2 choices for boot-up - Windows XP or Xubuntu (which has never been on this computer, so I'm assuming it's the Puppy install - right?). When I select Xubuntu, I get the error message teklling me access is denied due to the missing hal.dll file. I have no other options to click at that point other than to go back and boot up Windows. If I can still install Puppy by another means, How do I do it? I don't mean to be ADD by trying 2 things at once, but the experiment on the Compaq was just a precurser to Perminently installing Puppy on the Dell. Thanks again for your attention and sorry for my ignorance.[/QUOTE]

You should wait for a reply from mikewhatever because I haven't used Puppy in a couple of years. However, are you sure the old computer is booting to the CD? I would expect the Puppy CD to call itself Puppy not Xbuntu and to not give you the choice of Windows if it is a live CD. Could you possibly have a wubi style of Xbuntu on the old computer?


[Edit] Could the old Dell be a latitude or inspiron, I don't think I've seen one with the name you gave in your original post?

---

### Post by Javelin Dan on 2010-12-29
QLee: Now that you mention it, it is possible as I do vaguely remember fooling around with trying to download Xubuntu a couple of years ago. Should I use the same proceedure on the Dell - press the appropriate F# key to bring up the BIOS? If so, the fog may be beginning to clear...

---

### Post by Bucky Ball on 2010-12-29
Yes, appropriate f* key to get to the BIOS.

---

### Post by QLee on 2010-12-30
[QUOTE=Javelin Dan]... If so, the fog may be beginning to clear...[/QUOTE]

Good, that fog has not been your friend, and it made it difficult to give you useful help.

You're on the right track now, option your BIOS to boot from the CD drive first in order to use the live CD on either or both computers.

On a sunny day, we all feel better, eh?

---

