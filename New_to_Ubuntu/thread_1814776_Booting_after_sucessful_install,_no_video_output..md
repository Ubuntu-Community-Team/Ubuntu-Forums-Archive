---
title: "Booting after sucessful install, no video output."
date: 2011-07-30
forum: New to Ubuntu
---

### Post by clubagreenie on 2011-07-30
Hi all,

I've just sucessfully installed 11.04 on a 2nd hand dell inspiron 530. Running from onboard video card at the moment. Created a install CD and sucessfully installed but had to force boot from CD then, just after a line or two appears very quickly hit F6 as advised in another posting I found and this brings up a screen titled UBUNTU with various options, Try, Install, Check for Defects etc. Arrow down to install then F6 again and edit the following;

GRUB_CMDLINE_LINUX_DEFAULT=quiet splash

to

GRUB_CMDLINE_LINUX_DEFAULT=nomodeset

Then enter will run the CD and it will sucessfully run the install and then after completion will want to reboot after removal of CD. When rebooting it starts up but there's no video out to monitor.

I can get it to boot into O/S from the hartd drive *if* I run as above and when the first install screen appears quit out of the installation process. I tried editing the

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; in /etc/default/grub and running update grub but it won't boot with video output. 

One thing I do notice is when it's sucessful in loading through to the install screen there is a list of what it's doing and the only line that comes up as a fail is the following and coincidently it's video related;

[COLOR="Red"]starting load failbacks graphics devices = fail[/COLOR]

I have a ASUS EAH 4650 ATIRaedon video card to install when the rest is sucessful, it won't boot from it either but I can't get as far as I have with the on board either.

Any suggestions greatly appreciated as running a partial install just to boot is getting boring.

Thanks in Advance.

J

---

### Post by Noncon on 2011-07-30
When you lose video, pressing CTRL-ALT Num Pad + or - should get your video back. 

When you get to the desktop; System|Preferences|Monitor, then set resolution and save it and you shouldn't lose video again on bootup. 

KJ

---

### Post by clubagreenie on 2011-08-01
CTRL-ALT gets some action if still in boot from CD mode, get auto adjust message on screen. But doesn't have any action after video loss on reboot. 

Tried going into system after quitting install and then setting res but no matter what res setting ends up the same.

---

### Post by Noncon on 2011-08-01
Probably one of the many anomalies of 11.04, save yourself some headaches and install 10.04 or 10.10.

KJ

---

### Post by oldfred on 2011-08-01
If you only have Ubuntu then you do not get the grub menu.

Hold shift key down from BIOS boot until menu appears. On linux line you can edit quiet splash and change to nomodeset or other parameters.
Once you find the set of parameters that work then you can permanently add them to /etc/default/grub. Usually if you need nomodeset on the CD you need it to boot first time. Does it offer to install proprietary drivers.

# nvidia.txt
Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by clubagreenie on 2011-08-03
So thanks for all the help so far.

Have it booting all the way via the on board video using the hold shift method and then editing the etc/default/grub file and saving/updating.

[This]("https://help.ubuntu.com/community/RadeonDriver") & [this]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti")  page shows my card should be supported by open source & "fglrx" proprietary drivers but they seem to rely on being able to see output from it from the proprietary driver and then deleting that & changing to the open driver.

Issue I have is I still can't boot from ATI card and see output though system does acknowledge there is another video card there as I have the option in the bios screen of shutting down and switching the cable to the other outlet.

From what I've read there should be built in support for the card but from the [raedon driver]("https://help.ubuntu.com/community/RadeonDriver") page instructions it says to check the card type with 
lspci -nn | grep VGA
and check if it's in the supported list. 

There's [another page]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") detailing fglrx interfering with ATI/Raedon drivers but following that there doesn't seem to be any remnants of it left but I'm wondering if I need to find a clean install of the open source drivers.

---

