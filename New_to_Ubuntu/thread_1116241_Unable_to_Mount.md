---
title: "Unable to Mount"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by SebastianMcK on 2009-04-04
Hi all,

Ive recently encrypted my windows partition with Truecrypt and i stuffed up some system files and wanted to replace them using ubuntu so i installed Truecrypt on ubuntu live cd and selected the encrypted one, entered in my password and selected Pre-Boot Authentication AKA System Encrypted clicked ok and:

-------------------------------------------------------

[B]$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/mapper/truecrypt5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/mapper/truecrypt5 /media/truecrypt5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/mapper/truecrypt5 /media/truecrypt5 ntfs-3g force 0 0[/B]

----------------------------------------------------------------

So i entered: 

---------------------------------------------------------------

**mount -t ntfs-3g /dev/mapper/truecrypt5 /media/truecrypt5 -o force**

----------------------------------------------------------------

and it said that only the root user could do that so i then found that you have to put sudo in the front

----------------------------------------------------------------
[B]
sudo mount -t ntfs-3g /dev/mapper/truecrypt5 /media/truecrypt5 -o force[/B]

---------------------------------------------------------------

and i got: 

----------------------------------------------------------------

[B]ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/mapper/truecrypt5 /media/truecrypt5 -o force
ntfs-3g: Failed to access volume '/dev/mapper/truecrypt5': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.[/B]

-------------------------------------------------------

Please HELP!!! I tried the ubuntu irc but there way to busy and i guess no one in there could help me.

Im a total Newb at Ubuntu PLEASE HELP!!!

I really need this windows installation fixed as its my school laptop and i need all my work.

---

### Post by ibuclaw on 2009-04-04
Force mounting an uncleanly shutdown Windows Partition is **potentially dangerous** and could lead to loss of data.

Try booting back into Windows, and ensuring that you shutdown properly, then try mounting the partition again from Ubuntu.

Regards
Iain

---

### Post by SebastianMcK on 2009-04-04
> **tinivole said:**
> Force mounting an uncleanly shutdown Windows Partition is **potentially dangerous** and could lead to loss of data.

Try booting back into Windows, and ensuring that you shutdown properly, then try mounting the partition again from Ubuntu.

Regards
Iain

The thing is i cant, because i cant even get to the logon screen without it saying: Missing DLL.

---

### Post by sir_cheats_a_lot on 2009-04-04
did you try getting into safe mode?  reboot and just hit F8  after the post screen dissappears...maybe even just before it.  don't even need to log in, just get to the login screen and reboot again.

---

### Post by SebastianMcK on 2009-04-04
> **sir_cheats_a_lot said:**
> did you try getting into safe mode?  reboot and just hit F8  after the post screen dissappears...maybe even just before it.  don't even need to log in, just get to the login screen and reboot again.

Ill try that, so ill be back.

EDIT: No still the DLL missing and when i click ok its just a blank screen with my cursour.

---

### Post by SebastianMcK on 2009-04-04
Not sure if this is allowed double posting i tried booting into safe mode same thing.

---

### Post by sir_cheats_a_lot on 2009-04-04
does it mention what DLL file is missing?  might be able to find away to grab and replace it from a windows CD.  I'm pretty sure you could find a way to do this by spending time at google.  not sure how to do that myself as I've never had to.

---

### Post by SebastianMcK on 2009-04-04
> **sir_cheats_a_lot said:**
> does it mention what DLL file is missing?  might be able to find away to grab and replace it from a windows CD.  I'm pretty sure you could find a way to do this by spending time at google.  not sure how to do that myself as I've never had to.

authui.dll the main problem is my system is encrypted.

---

### Post by sir_cheats_a_lot on 2009-04-04
anyway you can get to the command prompt at least?  here's something else i didn't think to ask.. which version of windows are you running? xp or vista?  if i you can some how get to the command prompt, you might be able to replace it still.  you likely will need a floppy drive for this though.  no idea if you'll have access to a usb drive or not from the MSDOS prompt(haven't had to use it in years). if all else fails burn it to cd. the process invovles copying the file to the system32 folder and running "regsvr32 authui.dll"
 the windows recovery console on the windows CD should get you in too.

---

### Post by SebastianMcK on 2009-04-04
> **sir_cheats_a_lot said:**
> anyway you can get to the command prompt at least?  here's something else i didn't think to ask.. which version of windows are you running? xp or vista?  if i you can some how get to the command prompt, you might be able to replace it still.  you likely will need a floppy drive for this though.  no idea if you'll have access to a usb drive or not from the MSDOS prompt(haven't had to use it in years). if all else fails burn it to cd. the process invovles copying the file to the system32 folder and running "regsvr32 authui.dll"
 the windows recovery console on the windows CD should get you in too.

Im running Windows Vista Basic and i would have no idea how to boot into the command prompt i know what it is and i use it on a regular basis but i wouldnt know how to get into the command prompt booting up. Selecing Safe mode with Command Prompt just does the same thing.

But my system is encrypted thats the ONLY problem I have. The CDs boot before the password authentication so it just recongises the drive as corrupted. Any encryption program can mount it.

---

### Post by sir_cheats_a_lot on 2009-04-04
should be an option in the boot menu when you go to boot to safe mode.. i think its Ctrl+shift+F5 i forget.
or
perhaps you should really be considering decrypting via the rescue disk, so you can repair it.
see the following:
[http://www.truecrypt.org/docs/rescue-disk](http://www.truecrypt.org/docs/rescue-disk)

---

### Post by SebastianMcK on 2009-04-04
> **sir_cheats_a_lot said:**
> should be an option in the boot menu when you go to boot to safe mode.. i think its Ctrl+shift+F5 i forget.
or
perhaps you should really be considering decrypting via the rescue disk, so you can repair it.
see the following:
[http://www.truecrypt.org/docs/rescue-disk](http://www.truecrypt.org/docs/rescue-disk)

Oh sweet awesome thanks, ill ry that.

---

### Post by SebastianMcK on 2009-04-05
I decrypted my system and every boot manager i go into it cant mount it, it reconsiges my drive in windows just i dont know how to mount it. It wont even open.

---

