---
title: "Ubuntu USB problems"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by jordanC on 2011-01-27
Ive recently installed ubuntu desktop edition onto my laptop and wanted to give the netbook edition a go. Ive got the netbook edition on my USB and ive prioritised the USB as the top start up option in the BIOS, the only problem is, my system starts up Ubuntu desktop as normal evrytime i reboot, any ideas?

---

### Post by Foxheadz on 2011-01-27
If you have a laptop why would you want to use the netbook remix? Also you sure you downloaded the Netbook edition from [this]("http://www.ubuntu.com/netbook/get-ubuntu/download") site?

---

### Post by jordanC on 2011-01-27
Not getting on with ubuntu right now, wanted to see if the netbook was any easier. And yes thats the site i got the download from.
I have a feeling i need to make my usb a bootable deivice but i have no idea how to do so

---

### Post by Foxheadz on 2011-01-27
Well if your making it with something like unetbootin or startup disk creator it should do it automatically

---

### Post by ghostborg on 2011-01-27
I would say that for some reason the usb stick is not bootable.
That's what I would look into first. Try it on another machine.

---

### Post by andymorton on 2011-01-27
You can install the netbook GUI from the synaptic package manager. I think the package is called 'ubuntu-netbook'

andy

---

### Post by Gremlinzzz on 2011-01-27
I was having trouble with usb boot!
what the problem solver for me was i had to change usb mass storage emulation from auto to all fix disc.== in the bios
also had a problem with some distro but hitting tab and typing live then hit enter did the trick.

---

### Post by C.S.Cameron on 2011-01-27
Did you install using Ubuntu's Startup Disk Creator?
Since you are already running Ubuntu, this is the easiest.

Sometimes you can press F10, F12 or Esc, etc, at boot and it will give you a list of available devices to boot.

---

### Post by quadproc on 2011-01-27
> **C.S.Cameron said:**
> 
Sometimes you can press F10, F12 or Esc, etc, at boot and it will give you a list of available devices to boot.
Good suggestion.  Every BIOS seems to use a different way to select the boot device; if you don't have the key information then you can try the most likely keys which are DEL, F2, F8, F10, F12, and possibly F4 or F6.  This has to be keyed in at the right time, usually just after the startup/POST screen.  Once recognized by the BIOS, the selection will show on the screen.  You can then select it by using the arrow keys and ENTER.

quadproc

---

### Post by jordanC on 2011-01-28
Ok so im still stuck on how to get it to boot from USB despite you guys helping. Ive got a windows 7 installation disk and thought i would go back to using that, but im just getting a black screen with a flashing line in the top left and if i leave it it just starts up Ubuntu!
Ive looked in the BIOS and theres no CD/DVD option that i can move to top priority out of the list of bootable devices. USB is there but i still cant get it to work :(

---

### Post by quadproc on 2011-01-28
> **jordanC said:**
> Ok so im still stuck on how to get it to boot from USB despite you guys helping. Ive got a windows 7 installation disk and thought i would go back to using that, but im just getting a black screen with a flashing line in the top left and if i leave it it just starts up Ubuntu!

I think that we will need some more information to be able to really help so here are a few questions:

What make and model of computer?
Which BIOS (including its version number)?
How big is the disk?
Which version(s) of Ubuntu are you using?

I have a theory which we can explore if you like.  The theory is that you are booting from the USB stick.  I say this because the startup behavior that you describe (after the BOIS finishes there is a blinking cursor in the corner of the screen, then the system asks for login) is normal behavior for a system which has only one operating system and that system is Ubuntu.

I am assuming that your Ubuntu version is relatively recent, say within the last 1.5 years or so.  If this is not true then what I am writing will not work so please ignore it.  If it is true then your system should be using grub-pc (also known as grub 2).  Grub-pc will look at your keyboard to see if the SHIFT key is pressed during the time between the BIOS finishing and the beginning of loading Linux.  If the SHIFT key is depressed then grub will present a menu showing the available choices instead of just silently taking you to a login.  So, try booting and hold down SHIFT at the right time and report what happens.

Another way to tell what operating system(s) are on your hardware is to look in the grub configuration file.  This is normally located in the directory /boot/grub/grub.cfg.  Start up your favorite editor and open that file.  Look for lines which start with the word menuentry.  See how many of these you have, and which operating system each is associated with.  These are the possible choices that you can boot.

If you see only one operating system version then it is highly likely that you are running from the USB stick.  If you see more than one then I suspect that you have some kind of damage to the software and that will require investigation and repair.

Please let us know what you find, and good luck!

quadproc

---

### Post by jordanC on 2011-01-28
my laptop is a sony vaio VGN-N38Z and im currently running ubuntu desktop edition. I held down shift and it went to a smiilar screen but this time saying " GRUB loading" then nothing happend and it ran ubuntu desktop as usual

---

### Post by quadproc on 2011-01-28
> **jordanC said:**
> I held down shift and it went to a smiilar screen but this time saying " GRUB loading" then nothing happend and it ran ubuntu desktop as usual
This is not good - it means that something is broken in the installation on the USB stick.  When you just get the loading message from grub then that means that grub cannot find anything to do for some reason.

Perhaps the boot flag is not set, and your computer's BIOS requires that flag?  You can check the flag by running gparted on the USB stick; select the stick using the little window in the upper right of gparted's display.  Then look at the main part of the window and you will see a column at the right which shows what flags are set.  You should have a boot flag; if not then you can set it with gparted by highlighting the partition of interest, clicking on the Partition selection, and selecting Manage Flags.

quadproc

---

### Post by ellgor on 2011-01-29
Hi,

A suggestion, when I installed puppy-linux to a USB and because it had a bootloader on it the bios didn't recognise it as a USB device, instead it was read as a hdd, much later I found it listed with the hdd's with the usual boot options.

Regards, Ellgor.

---

### Post by viditgoyal3009 on 2011-01-29
Hi,

Just a personal advice, do not install ubuntu-netbook. It is ANNOYINGLY SLOW. I have a core i7 processor, 4gb RAM, and ATI Radeon 5650 graphic card with 1 gb dedicated memory and still it was lagging on this machine...

---

### Post by jordanC on 2011-01-29
Ha okay thanks, any idea how to boot windows 7 from a disk with these problems? same thing happens with the usb.

---

### Post by viditgoyal3009 on 2011-01-30
same problems occured with me when i tried to install ubuntu with a usb on my machine. i would recommend buy a blank dvd, burn ubuntu on it with windows 7 since it comes with a pre installed program to burn iso file.. then boot from the dvd. Everything should work fine from then.

---

### Post by jordanC on 2011-01-30
Thanks but ive got windows 7 burned onto a disk, yet it still get stuck on a screen with a flashing blip, then just starts up ubuntu again.

---

### Post by quadproc on 2011-01-30
> **jordanC said:**
> Thanks but ive got windows 7 burned onto a disk, yet it still get stuck on a screen with a flashing blip, then just starts up ubuntu again.
If I am reading this correctly then you have a bootable CDROM with Windows 7 on it and when you place this disk in your system and boot the system, then you get Ubuntu?

Assuming that the above is correct, it sounds your BIOS is not paying attention to the CDROM.  I would try interrupting the BIOS during startup by pressing whichever key is needed to allow you to select the boot device, and then moving the cursor to the CDROM line and typing ENTER.  That should start up the CDROM and should boot from it.

If you can't get the system to boot from the CDROM then I would suspect a damaged BIOS.

quadproc

---

### Post by jordanC on 2011-01-31
Okay thanks, would you have any idea which key i need to press to interupt BIOS? my laptop is a sony vaio VGN-N38Z, also if i have a damaged BIOS does this mean im going to have to shell out money to get it repaired? cheers for your help mate

---

### Post by quadproc on 2011-01-31
> **jordanC said:**
> Okay thanks, would you have any idea which key i need to press to interupt BIOS? my laptop is a sony vaio VGN-N38Z,
I do not know which key that particular computer uses to interrupt the BIOS during its startup but the most popular keys that I have seen are ESC, F2, F10, F12, and F8.   If none of them are it then you might try the other even numbered function keys.
>  also if i have a damaged BIOS does this mean im going to have to shell out money to get it repaired? cheers for your help mateVery possibly.  A BIOS normally is stored in EEPROM and perhaps some of it is in ROM; the ROM portion would not be changeable but the EEPROM portion is.  There are programs which will rewrite your EEPROM (frequently known as "flashing" the BIOS), usually for the purpose of installing updates to the BIOS.  Generally, the manufacturers only furnish these programs to run under some version of Microsoft Windows.

If your BIOS is damaged then I can only think of two probable causes: either the EEPROM is bad, or something happened to reprogram at least a little bit of the BIOS.  The latter is quite unlikely but it is conceivable.

quadproc

---

### Post by jordanC on 2011-01-31
> **quadproc said:**
> I do not know which key that particular computer uses to interrupt the BIOS during its startup but the most popular keys that I have seen are ESC, F2, F10, F12, and F8.   If none of them are it then you might try the other even numbered function keys.
Very possibly.  A BIOS normally is stored in EEPROM and perhaps some of it is in ROM; the ROM portion would not be changeable but the EEPROM portion is.  There are programs which will rewrite your EEPROM (frequently known as "flashing" the BIOS), usually for the purpose of installing updates to the BIOS.  Generally, the manufacturers only furnish these programs to run under some version of Microsoft Windows.

If your BIOS is damaged then I can only think of two probable causes: either the EEPROM is bad, or something happened to reprogram at least a little bit of the BIOS.  The latter is quite unlikely but it is conceivable.

quadproc

So if im running ubuntu then i wont be able to repair my BIOS? Great this makes me love Ubuntu even more!

---

### Post by quadproc on 2011-02-01
> **jordanC said:**
> So if im running ubuntu then i wont be able to repair my BIOS? Great this makes me love Ubuntu even more!
I do not know what policies your RIOS provider may offer.  It is possible that they may have something that you could use.  You would probably need to contact the BIOS provider.  If they do not support Ubuntu then you could suggest to them that they should.  The issue here is not Ubuntu, it is the BIOS provider's policies.

Making changes to a BIOS is tricky because you need to keep the system running while you change the code that is being run in the BIOS.  This requires considerable care in the design of the BIOS and the motherboard hardware.  Generally, such things are best left to people who thoroughly understand the hardware and software so there are not a lot of them around.

quadproc

---

