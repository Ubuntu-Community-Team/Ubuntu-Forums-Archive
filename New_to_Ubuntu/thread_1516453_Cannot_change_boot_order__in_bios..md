---
title: "Cannot change boot order  in bios."
date: 2010-06-23
forum: New to Ubuntu
---

### Post by RJB10 on 2010-06-23
Hi all! Could i pick your brains please as i have a problem installing ubuntu via cd as on a acer aspire 5720z in the boot options it has :usb cdrom and when i have it as first boot device the pc is ignoring it and loading vista as normal.This is the first time i have come across  this sort of boot order where it has usb fdd,usb hdd and usb cdrom.Any ideas would be appreciated. Cheers all!

---

### Post by jtarin on 2010-06-23
Make sure there isn't an option for internal CD-ROM. Usually it's a separate option for internal and external CD-ROM.
Possibly a key combination at boot like most computers these days will give you a boot device menu....example F11 or F12.Sometimes your bios screen will tell you or your mfg's docs.

---

### Post by tacotime on 2010-06-23
> **RJB10 said:**
> Hi all! Could i pick your brains please as i have a problem installing ubuntu via cd as on a acer aspire 5720z in the boot options it has :usb cdrom and when i have it as first boot device the pc is ignoring it and loading vista as normal.This is the first time i have come across  this sort of boot order where it has usb fdd,usb hdd and usb cdrom.Any ideas would be appreciated. Cheers all!

On some computers you can do a custom boot by pressing like F9, where you can select where you want to boot without editing your BIOS try that.

---

### Post by Ionic-user on 2010-06-23
Hello all,
I'm a complete ubuntu newbie, hoping to evolve painlessly from the Mac world to Open Source. When I got my new little computer (Asrock Ion330HT) I just turned it on, slipped in the LiveCD, and installed directly; everything works perfectly, Lucid Lynx is really great but now I'm wondering whether I should have installed the BIOS programs that came on a CD in the same box as the machine before installing Ubuntu. I think they're just for Windows users but the documentation isn't at all clear about that. I presume that the machine wouldn't work at all if some basic BIOS wasn't already in the firmware but I'd be grateful for any confirmation from knowledgable people. Sorry if this is not the appropriate thread - I'm new here. I did hunt around but maybe my question is too basic!

---

### Post by RJB10 on 2010-06-23
I would`nt worry about that everything is done at the factory, any bios info on a disk will probably be there for flashing (updating) purposes.You should`nt have touch the bios unless in the future you want to update it as in the future your pc as it stands might not be compatible with some future hardwear.

---

### Post by RJB10 on 2010-06-23
> **tacotime said:**
> On some computers you can do a custom boot by pressing like F9, where you can select where you want to boot without editing your BIOS try that.
 I really appreciateed your reply but as far as i can gather f9 just loads setup defaults which does not help also have you ever heard of insydeh20 setup utility? cheers!

---

### Post by john newbuntu on 2010-06-23
Is there an option on the "Boot" tab/menu of your BIOS setup?  If so, do you see "IDE 0" and "IDE 1"?  Try making IDE 1 (if that is your CD-ROM) as your first boot device.  Then pop in the CD-ROM and see if you can boot from it.

Also, in the BIOS "Main" tab/menu, enable the F12 boot.  This will help you hit F12 at startup and choose the boot device.  Otherwise, it would use defaults in the setup to boot.
I based these on what I saw somewhere to the middle of the following doc:
[http://www.scribd.com/doc/25431944/Acer-Aspire-5720-5720G-Service-Guide](http://www.scribd.com/doc/25431944/Acer-Aspire-5720-5720G-Service-Guide)
My apologies if your BIOS screen does not have the same layout.

---

### Post by RJB10 on 2010-06-24
Thanks for your advice john the boot screen is the same as they are both acer aspire models im finding that when i enter the bios it will let me use the left and right arrow keys to change menu options but on each page i car`nt use the up and down arrows to select anything to change such as changing the boot menu from disabled to enabled as i car`nt use the arrow keys to get to it. nightmare! cheers!

---

### Post by SoFl W on 2010-06-24
> **RJB10 said:**
> I really appreciateed your reply but as far as i can gather f9 just loads setup defaults which does not help also have you ever heard of insydeh20 setup utility? cheers!

When it boots look for something that says "for boot menu press...", on Dell's it is F12.
It might be a bad CD.

---

### Post by john newbuntu on 2010-06-24
> **RJB10 said:**
> h as changing the boot menu from disabled to enabled as i car`nt use the arrow keys to get to it.
Hmm surprising! Try if hitting the tab key once helps.  Also try the "enter" key and then the up/down arrows.  If none of these work, hit F1 and see if there are any options.
Hitting "Esc" takes you back to the exit menu.

---

### Post by oldfred on 2010-06-24
F2 should get you into BIOS. Often the setting of device, hd, fd, cd etc is a different place than the setting for which hd to boot.

---

### Post by RJB10 on 2010-06-30
Thanks for everyones input on my issue with this acer aspire but i never got it to boot from the cd and will be giving it back to the owner tonight but ill try keep away in the future from any pc`s with a insydeh20 set up as id been reading of others who had been having issues with it anyway cheers everyone!

---

