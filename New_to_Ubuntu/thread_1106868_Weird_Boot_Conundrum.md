---
title: "Weird Boot Conundrum"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by mksugg on 2009-03-26
[-o<[http://ubuntuforums.org/images/smilies/eusa_pray.gif](http://ubuntuforums.org/images/smilies/eusa_pray.gif)
Here's a head scratcher.
When I installed Ubuntu on my Dell for the first time three weeks ago and booted up everything seemed to be going smoothly with startup until I realized the screen had gone black and everything seemed to come to a halt. After a lot of trial and error I was able to get the system to boot successfully by changing the BIOS. Since then the only way I can get the system up and running is by going in each time and changing the boot sequence. Here is the sequence.

Diskette Drive
Internal HDD
USB Storage Device
CD/DVD/CD-RW Drive
   CARDBUS NIC
   ONBOARD NIC

By flipping the first place between Diskette Drive and Internal HDD I'm able to boot up without a hitch every time. Then yesterday it hit me!

When I try to start up without changing the BIOS, as I said, the screen does not light up. But I do here the little drum riff that I have come to associate with the user sign-in page. What if the only problem is the screen is not lighting up? So I typed in my user name, hit enter and then typed in my password and...Voila!...the hard drive kicked in again and in a moment I heard the Ubuntu theme music indicating I was at the GNOME desktop, but the screen was still black. Maybe I just need to hit the right key to get the screen to light up, but no, I've tried pretty much everything I can think of and nothing works.

Any bright ideas why the screen stays black and why alternating the BIOS solves the problem?

Kent****

---

### Post by mksugg on 2009-03-26
Hello. Is anybody out there?

---

### Post by decoherence on 2009-03-26
> **mksugg said:**
> 
Any bright ideas why the screen stays black and why alternating the BIOS solves the problem?


That is a head scratcher. Is there a BIOS update available?

---

### Post by mksugg on 2009-03-26
Sorry, don't know what a BIOS update is.

---

### Post by Coreigh on 2009-03-26
I don't think this is really a BIOS issue. My guess is that it is a xorg issue. The Xwindows settings or configuration is wrong somehow. When does the screen go black? You can see it at BIOS time, do you see any of the initial Linux boot text or the Ubuntu loading logo? Does the computer work normally with the LiveCD?

---

### Post by decoherence on 2009-03-26
The behavior you describe sounds like it might be a bug in the BIOS. Hopefully Dell has released an update that fixes it.

Go to Dell's web page, go to the support section for your particular model... they should have a 'downloads' section there... see if there's a newer version of the BIOS you can download (your current version is displayed right when you boot up, generally just under teh Dell logo)

How you install the BIOS will depend, and there may be several options available. If you still have Windows on there, you can likely get an installer program that will run from there. If you don't have Windows, hopefully they offer a disc image that you can burn to CD and boot from.

If you don't have any luck getting/installing the BIOS update, let us know the specific model of Dell and we might be able to help further.

---

### Post by mksugg on 2009-03-26
I see initial boot text, but I don't think I've ever see a boot logo. I think it goes dark right before the ubuntu drum riff.

---

### Post by mksugg on 2009-03-26
Oh and yes the computer does work normally with the live CD.

---

### Post by decoherence on 2009-03-26
If it is an xorg error, you should be able to get GRUB to boot in to Recovery Mode (you might have to hit Escape when prompted. It will be early on in the boot process so watch for it) then run the "Fix X" program (or whatever it's called) from the menu that comes up.

---

### Post by mksugg on 2009-03-26
> **decoherence said:**
> The behavior you describe sounds like it might be a bug in the BIOS. Hopefully Dell has released an update that fixes it.

Go to Dell's web page, go to the support section for your particular model... they should have a 'downloads' section there... see if there's a newer version of the BIOS you can download (your current version is displayed right when you boot up, generally just under teh Dell logo)

How you install the BIOS will depend, and there may be several options available. If you still have Windows on there, you can likely get an installer program that will run from there. If you don't have Windows, hopefully they offer a disc image that you can burn to CD and boot from.

If you don't have any luck getting/installing the BIOS update, let us know the specific model of Dell and we might be able to help further.
thanks, I'll give it a try.

---

### Post by mksugg on 2009-03-26
> **decoherence said:**
> If it is an xorg error, you should be able to get GRUB to boot in to Recovery Mode (you might have to hit Escape when prompted. It will be early on in the boot process so watch for it) then run the "Fix X" program (or whatever it's called) from the menu that comes up.

OK, I'll give that a try. Thanks.

---

### Post by mksugg on 2009-03-26
> **decoherence said:**
> If it is an xorg error, you should be able to get GRUB to boot in to Recovery Mode (you might have to hit Escape when prompted. It will be early on in the boot process so watch for it) then run the "Fix X" program (or whatever it's called) from the menu that comes up.

Well, I tried this, but no go. Thanks for the suggestion.

---

### Post by mksugg on 2009-03-26
> **decoherence said:**
> The behavior you describe sounds like it might be a bug in the BIOS. Hopefully Dell has released an update that fixes it.

Go to Dell's web page, go to the support section for your particular model... they should have a 'downloads' section there... see if there's a newer version of the BIOS you can download (your current version is displayed right when you boot up, generally just under teh Dell logo)

How you install the BIOS will depend, and there may be several options available. If you still have Windows on there, you can likely get an installer program that will run from there. If you don't have Windows, hopefully they offer a disc image that you can burn to CD and boot from.

If you don't have any luck getting/installing the BIOS update, let us know the specific model of Dell and we might be able to help further.

So far no luck. I am not running windows on this computer and they don't appear to have a disc image that I can burn. I'm using a Dell Inspiron 1100. Thanks again for the help.

---

### Post by mksugg on 2009-03-26
Here is another element that I think points to it not being a BIOS problem. When I try to switch users or log out a user the screen also goes black. In this instance I suspect that everything is fine in the background...the screen is just not lit.

---

### Post by decoherence on 2009-03-27
> **mksugg said:**
> Here is another element that I think points to it not being a BIOS problem. When I try to switch users or log out a user the screen also goes black. In this instance I suspect that everything is fine in the background...the screen is just not lit.

But you only get a graphical boot when you mess with the BIOS, right?

If xorg was broken, it probably wouldn't work some of the time and not others. It's this "consistently inconsistent" behaviour that makes me suspect the BIOS.

For instance, if your screen changes resolution when you log out or switch users, that could be triggering the bug and maybe making the backlight turn off or something. Hey, here's an idea... boot it up so you DON'T have video... then take a flashlight and shine it on the screen at an angle. Look really close and see if video IS in fact working and your backlight is just turned off.

That'd almost definitely be BIOS, or a failing power inverter but in my experience, when those things die, they don't come back.

Now, the question is how do you apply that update? Dell has a bit of info here

[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

Scroll down to the "BIOSdisk" section. I also found this

[http://bootdisk.com/](http://bootdisk.com/)

But I can't vouch for it. In either case, the basic method is to make a FreeDOS boot disk, copy the BIOS update on there and boot from that.

Good luck! Hopefully somebody has an easier solution to suggest.

---

