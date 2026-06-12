---
title: "Install on a Computer with no current OS"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by Double Ott on 2011-07-16
Hey, I want to switch to Ubuntu from windows, but I messed up my first install after already deleting Windows.  What is the best way to install now?  Could someone give me a link, or lay it out in step by step?  
Thank you - 
Double Ott

---

### Post by TheMatej on 2011-07-16
jus go on [www.ubuntu.com](www.ubuntu.com), download latest iso image, burn it on CD, reboot ur computer, and follow the instructions :) gl

---

### Post by Elfy on 2011-07-16
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[Make sure the downloaded iso file is good before you start.]("https://help.ubuntu.com/community/HowToMD5SUM") [Hashes can be found here]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by XubuRoxMySox on 2011-07-16
The above on a borrowed computer, of course. And burning it to a CD isn't just a matter of putting data on a disk. The downloaded installation file is an image, and it must be burnt on the CD *as an _image_*, not as "data." And I don't mean image as in a picture, painting, or photograph, lol. Most CD burning programs recognize it and include the option to burn the file as an image.

Once that is done, go to you blank computer and put the new Ubuntu CD in the CD-ROM drive and close it up.

Now "reboot" the computer and watch for the Setup screen - the one that ordinarily appears only for a few seconds when the computer is first powered up. Somewhere on the screen there will be a *"press F5 to enter Setup"* or something to that effect. Hit that key rapidly a few times before that screen disappears, and you'll be taken to a menu that includes "Boot Options" or "Boot order" or something close to that.

Select "Boot from CD-ROM," and close the Settings. The computer will now boot into Ubuntu, and you're running Ubuntu Linux from the CD! No changes are being made to your computer, you're just browsing Ubuntu, taking it for a test drive, kicking the tires. While you're doing that make sure your internet connection is working (if it works on the CD, it'll most likely work - and work better - installed to the hard drive). Make sure it recognizes your printer, sound card, all that stuff.

If you're satisfied that Ubuntu is cool and works on your hardware, then just click the "Install" icon, answer a few questions on the form, and let 'er rip.

Ubuntu's installation is usually effortless after that!

Enjoy,
Robin

---

### Post by Double Ott on 2011-07-16
I'm installing on a netbook, which doesn't have a CD drive, so I've been trying to use an external CD drive.  On the BIOS boot menu, CD ROM isn't an option.  Any tips?

---

### Post by amjjawad on 2011-07-16
> **Double Ott said:**
> I'm installing on a netbook, which doesn't have a CD drive, so I've been trying to use an external CD drive.  On the BIOS boot menu, CD ROM isn't an option.  Any tips?

Does your machine boot from USB?

---

### Post by wolfen69 on 2011-07-16
> **Double Ott said:**
> I'm installing on a netbook, which doesn't have a CD drive, so I've been trying to use an external CD drive.  On the BIOS boot menu, CD ROM isn't an option.  Any tips?

Then something is wrong with your computer. All modern computers have the ability to boot from cd. What key are you pressing for the boot menu? Also, sometimes switching usb ports can help.

It also matters which usb plug (from the external drive) you are plugging in. The one with 2 wires coming off it is the one you want.

---

### Post by amjjawad on 2011-07-16
> **wolfen69 said:**
> Then something is wrong with your computer. All modern computers have the ability to boot from cd. 

OP has Notebook. Notebooks have NO Internal CD/DVD Drive.

---

### Post by Megaptera on 2011-07-16
Repeated #8 at the same moment - so deleted.

---

### Post by Double Ott on 2011-07-16
I'm pressing F2, which is the start-up key.  What do you mean the Plug with 2 wires coming off it?

---

### Post by Double Ott on 2011-07-16
How can I tell?

---

### Post by amjjawad on 2011-07-16
> **Double Ott said:**
> How can I tell?

First of all, you need to create a LiveUSB. Go to [www.ubuntu.com](www.ubuntu.com) then go to Get Ubuntu. There's HOWTO create a Live USB.

After that, Plug your LiveUSB, restart your machine and Login to BIOS. There must be an option in your Boot Devices where it mentions USB HDD or something like that.
If yes, set that to be the first boot device, save and reboot.

---

### Post by wolfen69 on 2011-07-16
> **amjjawad said:**
> OP has Notebook. Notebooks have NO Internal CD/DVD Drive.

I realize that. I was talking about booting from an EXTERNAL DRIVE. Also, I think you meant netbook, not notebook. Notebooks have cd drives. ;)

---

### Post by amjjawad on 2011-07-16
> **wolfen69 said:**
> I realize that. I was talking about booting from an EXTERNAL DRIVE. Also, I think you meant netbook, not notebook. Notebooks have cd drives. ;)

The one with 10 inch screen has no CD/DVD Drive :)

---

### Post by wolfen69 on 2011-07-16
> **amjjawad said:**
> The one with 10 inch screen has no CD/DVD Drive :)

Then it's classified as a netbook, not notebook or laptop. Anyway, the OP has an external cd drive that should work just fine.

---

### Post by amjjawad on 2011-07-16
If the OP has an External CD/DVD Drive, then there is an option to boot from that drive and it's either USB Something or "External" word is mentioned clearly.

---

### Post by wolfen69 on 2011-07-16
> **amjjawad said:**
> If the OP has an External CD/DVD Drive,

If you had read the OP's second post properly, we could have avoided the last few posts. I was trying to help him get his [SIZE="4"]EXTERNAL DRIVE[/SIZE] going. OK?

---

### Post by amjjawad on 2011-07-16
> **wolfen69 said:**
> If you had read the OP's second post properly, we could have avoided the last few posts. I was trying to help him get his [SIZE=4]EXTERNAL DRIVE[/SIZE] going. OK?

:)

---

### Post by XubuRoxMySox on 2011-07-16
LOL, okay... same directions, though. Only instead of burning the iso image to a CD, put it on a USB drive, and tell Setup to boot from the USB drive. Then proceed as described earlier as if the USB was a LiveCD.

Enjoy!

-Robin

---

