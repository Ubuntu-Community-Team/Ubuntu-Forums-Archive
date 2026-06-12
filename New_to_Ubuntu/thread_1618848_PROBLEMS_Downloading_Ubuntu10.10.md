---
title: "PROBLEMS Downloading Ubuntu10.10"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by ian19jam on 2010-11-11
I have downloaded the new Ubuntu 10.10 onto a USB stick, when I plug this into the computer all the files come up but no indication of how to install? Can anyone please help? I am not very computer orientated.  Thanks

---

### Post by Goldfissh on 2010-11-11
When you say "all the files come up", do you mean that it boots the desktop?

---

### Post by ian19jam on 2010-11-11
No When I open the USB key a box appears with all the files to do with Ubuntu one is boot one sis in stall. I clicked onto some of these and they would not open.

---

### Post by P4man on 2010-11-11
You have to reboot and boot from the stick. That may require pressing a function key in the bios to bring up the bios boot menu (so it doesnt boot from the harddisk in to windows), most bioses will write that at the bottom of the screen for a few seconds (something like PRESS F9 FOR BOOT MENU) or changing the boot order in the bios.

iF you dont get it figured out, post what PC or laptop you have.

---

### Post by mastablasta on 2010-11-11
> **ian19jam said:**
> I have downloaded the new Ubuntu 10.10 onto a USB stick, when I plug this into the computer all the files come up but no indication of how to install? Can anyone please help? I am not very computer orientated. Thanks
 
you can't just download it to USB, you will need to make USB bootable. first you owuld download iso to your hard disk and then create a bootable USB drive. to make it easy...
 
...use unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
or maybe better linuxliveusb creator: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) 
 
anyway once that is done you need to either change boot order in BIOS as it was suggested so that USB is first in line for boot. this can be also done temporary in new BIOS systems (as it was already mentioned).
 
Once you boot you will be able to select to try the system (this is called "Live session"). this won't make any changes to your computer. also once you are done all settings will be lost. but with USB it is possibel to make persistant live system that will save the settings.
 
another option to try the system will be to plug in the USB and in windows you iwll be ablet to install Ubuntu on your computer via Wubi. Wubi basically creates a large file inside windows and might not run as fast as the real system. but it is good enough to try it out.

---

### Post by P4man on 2010-11-11
Actually, in this case I might agree to try first with wubi. That way you can install ubuntu from within windows just like you install a windows program. See here:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

Try it out. If you like ubuntu and want to keep it, then do all of the above to make a bootable stick, boot from it and make a proper install. Wubi is great to install easily for a test, but its not a good idea to keep using it.

---

### Post by ian19jam on 2010-11-11
Thanks for all the advice but I am somewhat confused. When I had downloaded the Ubuntu 10.10 file I received a file on the desk top ending in iso. I then went to System and Administration and into Start up disk creator and followed the procedure for a USB stick, which has produced all these Ubuntu files. There is no instruction as to how to download this onto my computer. At the moment I am using 10.4 Ubuntu version and I want to upgrade to 10.10. So I cannot use the advice given with downloading from a windows version as I am not on Windows.

I looked at the UNetbootin site but I find it is rather confusing and no idea what to do? Sorry I am not very knowledgeable with Computer jargon etc.

I tried to press a function key in the bios to bring up the bios boot menu, but could not see any key to do this and it was very quick. Not sure what to do next. Please can you kindly advise in simple terms. Thanks

---

### Post by P4man on 2010-11-11
ok, that clears up a lot.
you can do two things; either you upgrade ubuntu from 10.04 to 10.10, but that doesnt require a usb stick or downloading the ISO. you can do that with update manager. Go to system > administrion > update manager. Click "settings" > updates > show new releases at the bottom set it to "normal releases". Its probably set to LTS releases only (and ubuntu 10.10 is not an LTS release).

Then rerun update manager and you will have to option to upgrade.

Now before doing this, I would recommend you try to boot the USB stick anyhow, especially since you already made it. That way you can test 10.10. If it works okay, go ahead and do the upgrade as described above (dont install it from the usb stick, as it will wipe everything or create a double install). If it doesnt work for whatever reason, think twice because you can not downgrade.

To help you boot the USB stick, can you tell us what computer you have exactly?

---

### Post by ian19jam on 2010-11-11
Many Thanks for your advice and will give it a try. Apologies for late reply but been out. My computer was hand built in2007 powered by ISUS with a Motherboard Integrated Graphics and a Memory Corsaire. That is all I have as detail on it. Obviously at the moment using Linux Ubuntu 10.4 at the moment.Thanks

---

