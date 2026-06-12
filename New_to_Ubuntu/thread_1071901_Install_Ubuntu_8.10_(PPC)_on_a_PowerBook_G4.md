---
title: "Install Ubuntu 8.10 (PPC) on a PowerBook G4"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Ledsled7 on 2009-02-16
Greetings, all.

For anyone finding it difficult to install Ubuntu on a PPC machine because of scattered resources and plain inability to speak Linux -- I've written a one page How-To guide.

[INDENT]Guide:   *Link removed -- see post directly below.*[/INDENT]

Perhaps if enough newbies find it helpful, it could become a sticky.  If not, let it become the target of the odd monthly search.

Thanks to everyone who helped, whether they knew it or not.

LedSled7

---

### Post by Ledsled7 on 2009-03-14
You'll no longer be redirected to download a PDF document, it's all here now.
- - - - - -
[LIST=1]
[*]**GET UBUNTU**:  Download the most recent version of an “Alternate Install CD” from here: [INDENT][http://cdimage.ubuntu.com/ports/releases/]("http://cdimage.ubuntu.com/ports/releases/")[/INDENT]


[*]Burn the new ISO disk image to CD using Disk Utility.app.  **Do not mount and burn in the Finder.*
 

[*]**PREPARE THE HDD**:  Use Disk Utility.app to decrease the size of your existing Mac OS X partition(s) until there are at least 10 GB free on the hard drive.  **Do not create a partition in this empty space as the Ubuntu installer will create the necessary partitions there.*


[*]If you surf wirelessly, connect your PowerBook to the web via ethernet now. 


[*]**REBOOT & INSTALL**:  With the Ubuntu Install CD in the drive, press ALT while rebooting to select the CD-ROM, as holding “C” during reboot may not work.  *You may need to enter an admin password.*


[*]If your Mac fails to boot from the install disc, reboot the Mac while pressing COMMAND-OPTION-O-F to boot to the Open Firmware prompt.
**Make sure the following path matches that of yaboot on the install disc.*  At the prompt, enter:
[INDENT][FONT="Courier New"][SIZE="3"]boot cd:,\install\yaboot[/SIZE][/FONT][/INDENT]


[*]After the reboot, type [FONT="Courier New"][SIZE="3"]install[/SIZE][/FONT] at the prompt.  Follow onscreen instructions.  Enter information as required.


[*]**CD-ROM FIX**:  When the installer attempts to MOUNT & DETECT CD-ROM, your CD-ROM may not be detected.
Press ALT+F2 to open another shell, and at the prompt type:
[INDENT][FONT="Courier New"][SIZE="3"]modprobe ide-scsi[/SIZE][/FONT][/INDENT]


[*]Switch back to the installation shell and choose to MOUNT & DETECT CD-ROM again, and the CD-ROM drive will spin-up.  Carry on.


[*]Follow further onscreen instructions.  Enter further information as required.


[*]**AIRPORT WIRELESS**:  When the installer attempts to CONFIGURE DHCP, it will not recognize an Airport Wireless con&#64257;guration.  After you boot into Ubuntu, you can download the Broadcom driver to enable Airport WiFi.


[*]Follow instructions.  Enter information.  Go brew a tea, smoke a cigarette, or pet the dog for bit while the OS is being installed.


[*]When the installation is complete, the CD will eject, and you will be prompted to reboot.


[*]After rebooting, to boot into Linux at the "Stage 1" prompt type (lower case "L"):
[INDENT][FONT="Courier New"][SIZE="3"]l[/SIZE][/FONT][/INDENT]
To boot into Mac OS X, you type ‘x’… but &#64257;nish the next few steps before you do anything else.


[*]**VIDEO FIX**:  To avoid booting into darkness, at the boot prompt type:
[INDENT][FONT="Courier New"][SIZE="3"]Linux video=ofonly nosplash[/SIZE][/FONT][/INDENT]
Enter your username and password at the login panel when it appears.


[*]As soon as the OS loads, open the Terminal application from the Ubuntu Menu.  You will edit the bootloader (yaboot.conf) &#64257;le so that you won’t have to perform the VIDEO FIX step every time you boot Ubuntu.

Backup yaboot.conf before you edit it.  At the terminal prompt, type:
[INDENT][FONT="Courier New"][SIZE="3"]sudo cp /etc/yaboot.conf/etc/yaboot.conf.bak[/SIZE][/FONT][/INDENT]

**This puts a copy of it in the same directory.  The &#64257;le can now be safely edited.*


[*]To open yaboot.conf in the editor, type:
[INDENT][FONT="Courier New"][SIZE="3"]sudo nano /etc/yaboot/conf[/SIZE][/FONT][/INDENT]

[*]Find the &#64257;rst occurrence of the string:
[INDENT][FONT="Courier New"][SIZE="3"]append=”quiet splash”[/SIZE][/FONT][/INDENT]
...and replace with this:
[INDENT][FONT="Courier New"][SIZE="3"]append=”video=ofonly nosplash”[/SIZE][/FONT][/INDENT]
If you don’t &#64257;nd it within in the &#64257;rst block of text, insert it after the string:
[INDENT][FONT="Courier New"][SIZE="3"]defaultos=[/SIZE][/FONT][/INDENT]
or
[INDENT][FONT="Courier New"][SIZE="3"]initr=[/SIZE][/FONT][/INDENT]


[*]**SUCCESS**: Save the &#64257;le. Exit the terminal.  Enjoy Ubuntu.
[/LIST]
- - - - - -

---

### Post by kiddoc on 2009-03-29
Will this method also allow me to dual boot on my PowerBook?  I'd like to keep OS X as well as Ubuntu on my laptop. Overall, this is exactly what I've been looking for.

Thanks

---

### Post by Ledsled7 on 2009-03-29
kiddoc, the procedure will allow you to dual boot OS X and Linux.

In Step 3, you're only decreasing the size of the OS X partition to make free space for a Linux partition -- *not* erasing the disk and re-partitioning.

Cheers.

---

### Post by red_hawk on 2009-03-31
Does this only work with the alternate install cd?

---

### Post by kiddoc on 2009-04-03
> **Ledsled7 said:**
> kiddoc, the procedure will allow you to dual boot OS X and Linux.

In Step 3, you're only decreasing the size of the OS X partition to make free space for a Linux partition -- *not* erasing the disk and re-partitioning.

Cheers.

So, I can type lower case L at the prompt and get into Ubuntu just fine but if I type lower case X at the prompt it just hangs there.  PowerBook G4 1Mhz

Why can't I get back into OS X?

---

### Post by inieves on 2009-04-30
Has anyone had issues with the screen flickering?  After booting into the graphical mode, with the desktop, etc... occasionally the screen shows horizontal lines that appear to be moving up and down... flicker..

---

### Post by brett987 on 2009-09-04
Hi,

After a day and half later of suffering, this newbie simply had to go back into terminal and enter:
sudo ybin -v

Then Sucess!

Thank you, if not for this post I would not have made it!
-Brett



[*]**SUCCESS**: Save the &#64257;le. Exit the terminal.  Enjoy Ubuntu.
[/LIST]
- - - - - -[/QUOTE]

---

### Post by odd42 on 2009-10-15
[COLOR=Black][SIZE=2]Ledsled7, brett987, others -- thanks a ton for the instructions and hints.  Saved me a lot of time, I registered just to say so!

One thing to add: the Ubuntu installation through me for a loop by not putting me in the sudoers group.  But [this post]("http://ubuntuforums.org/showpost.php?p=935062&postcount=10") helped me out, after I booted off the CD to get into rescue mode.[/SIZE] 
[/COLOR]

---

