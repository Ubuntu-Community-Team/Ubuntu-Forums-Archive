---
title: "Ubuntu 8.10 Intrepid Ibex Floppy Drive Problems"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by NHArticleTen on 2009-02-04
Ubuntu 8.10 Intrepid Ibex Floppy Drive Problems

You'll notice after you've installed/upgraded-to the latest release (8.10) that the floppy module isn't loaded by default(wisdom of the ubuntu-gods).

In terminal(Applications>Accessories>Terminal):

sudo gedit /etc/modules (enter)

(you'll be asked for admin/super-user password and then press enter again)

(the editor will start and will open /etc/modules in read AND write)

In the editor you will add "floppy" to /etc/modules (as per instructions on the top of that page) and then save it.

Close the editor application and return to the terminal:

sudo mkdir /media/floppy (enter)

(this makes a directory in /media/ called "floppy")

Again, in terminal:

sudo gedit /etc/fstab (enter)

(you will add the following line to your /etc/fstab and save it)

"/dev/fd0        /media/floppy     auto user,exec,rw,noauto 0 0"

(everything between the quotation marks can be copied and pasted into your /etc/fstab file...I try to duplicate the spacing from the cdrom entry that you'll probably see right above it...depending on your hardware, of course)

After you've edited, saved, and exited the editor and terminals you should reboot your machine and check out your handiwork!

Now you should see the "Floppy Drive" shown/listed in your "Places" area (around where you see your optical drives listed).  You should test the drive with a known good disk(say an old dos/windows/driver diskette or something like that) to see if it is mounted properly and that you can view the contents of the disk.

So now that you've successfully taken care of that...now let's raise your hair on our next adventure.

Put a blank disk into the floppy drive(make sure the disk's write-protect "tab/window" is in the "unlocked/closed/can't-see-through-the-hole" position).

Navigate: System>Preferences>Main_Menu (this is where you select what you want to show up in the "main menus") -then- In this new Main_Menu window, select Applications>Accessories and then check-mark/select the "Floppy Formatter", then you can close it.

Navigate: Applications>Accessories>Floppy_Formatter and see if it actually starts the formatter...or gives you the "permission denied" warning...

If you get the formatter up and running, Great!  If not, let's continue...

Navigate: System>Administration>Users_and_Groups and then you should get a "Users Settings" window.  Here, you will "unlock" this window using the "unlock" button down by the "close" button(enter password to unlock).

Then select "Manage Groups" and a window titled "Group_Settings" will appear.  There you will select "Add_Group" and you will add "floppy" as a new group.

Please make sure to check-mark your username in the "Group_Members" area and then select "OK"(don't change the "group id number).  Close Group_Settings and User Settings and then reboot your machine.

Hope that helps!

---

### Post by Muffinabus on 2009-02-04
Or you can buy a flash drive for $2 (:

---

### Post by bubba_169 on 2009-02-04
I think unless your machines is a decade old with no usb there is no excuse to still be using floppies? With the cost of flash memory at an all time low ... it just makes no sense?

Unless you're wanting to use the floppy drivers to load a floppy so you can back it up to pen drive? Or to make a rescue disk for an older system?

I for one am glad the floppy module has been removed by default as it used to cause problems with the live CD on my dell laptop... like i had to wait an extra 15 minutes during boot for it to realise there was no floppy drive! Good times :D

---

### Post by NHArticleTen on 2009-02-05
> **bubba_169 said:**
> I think unless your machines is a decade old with no usb there is no excuse to still be using floppies? With the cost of flash memory at an all time low ... it just makes no sense?

Ubuntu is for everyone.  Not everyone is done/finished with legacy devices/drivers/media.  Quite the contrary, as the economy suffers and more legacy equipment is gifted/given to others who, in many cases, just want Ubuntu to work with their equipment.

> **bubba_169 said:**
> 
Unless you're wanting to use the floppy drivers to load a floppy so you can back it up to pen drive? Or to make a rescue disk for an older system?

Exactly.  Many people have not yet finished with content on legacy media such as floppies, zip disks, and even the 5.25 diskettes(discovered in grandma's attic).  I know there is a cottage industry centered around rescuing data off of legacy devices, but why should we actively drive people to that expense?  I have a legacy machine running windoze 3.1 specifically dedicated to the task of transfering data from 5.25 media to 3.5 media when necessary(and for the nostalgic value, of course).

> **bubba_169 said:**
> 
I for one am glad the floppy module has been removed by default as it used to cause problems with the live CD on my dell laptop... like i had to wait an extra 15 minutes during boot for it to realise there was no floppy drive! Good times :D

Your reference to Ubuntu taking fifteen minutes of boot time to recognize that your equipment didn't have a legacy drive is strictly a programming/coding issue(and unnecessary, reflecting on the performance of other nix distros).

Obviously the vast majority of users of software/OSes just want them to work, regardless of the age of the hardware.

As always, thank you for relating your specific experiences with those who might well not be experiencing your good fortunes.

---

### Post by kansasnoob on 2009-02-05
I'll have to give that a try.

I used a different method. I did of course install fdutils from Synaptic and then just added "floppy" to /etc/modules so it looked like this:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
floppy

Your way looks more "correct".

---

### Post by kansasnoob on 2009-02-05
Oh, and I first noticed Floppy support was gone in 8.10 when I needed to burn a Super Grub Disk floppy for a much older machine!

---

### Post by germclown on 2009-04-07
Whether floppies are useful or not, this is a very clear, well-written guide. Thanks and kudos.

And floppies *are* useful. I need SATA drivers on disk so I can install XP on a second partition. Since I don't already have it installed and I don't have access to another Windows box, a custom CD is not an option. My install disk doesn't let me check storage cards or USB drives either.

I tend to agree that a leaner default Ubuntu is better. However, non-default but still fairly common needs (like floppies) should be much easier to enable (for "What's a Google?" people, not just terminal jockeys). Maybe even just a "My computer's new and awesome / My computer's so old it's made of wood" option during install that would direct Ubuntu to add or skip (for the time being) legacy support.

---

### Post by NHArticleTen on 2009-05-12
You'll probably notice that Ubuntu 9.04 Jaunty has corrected the prior deficiencies with respect to automatically setting up floppy drive services.

Sadly enough, a few daring souls who checked out Ubuntu during 8.04 and 8.10 were probably turned off enough to abandon their investigation of Linux solely based on the poor OOBE(out of box experience) with respect to floppy media access and usage.

Something that did NOT need to happen!

Anywho...welcome to Jaunty!

---

### Post by Zoowey on 2009-05-12
> **NHArticleTen said:**
> Ubuntu is for everyone.  Not everyone is done/finished with legacy devices/drivers/media.  Quite the contrary, as the economy suffers and more legacy equipment is gifted/given to others who, in many cases, just want Ubuntu to work with their equipment.



Exactly.  Many people have not yet finished with content on legacy media such as floppies, zip disks, and even the 5.25 diskettes(discovered in grandma's attic).  I know there is a cottage industry centered around rescuing data off of legacy devices, but why should we actively drive people to that expense?  I have a legacy machine running windoze 3.1 specifically dedicated to the task of transfering data from 5.25 media to 3.5 media when necessary(and for the nostalgic value, of course).



Your reference to Ubuntu taking fifteen minutes of boot time to recognize that your equipment didn't have a legacy drive is strictly a programming/coding issue(and unnecessary, reflecting on the performance of other nix distros).

Obviously the vast majority of users of software/OSes just want them to work, regardless of the age of the hardware.

As always, thank you for relating your specific experiences with those who might well not be experiencing your good fortunes.

I don't mean to insult anyone do to their economic status but I seriously must say I see no excuse for anybody to not have a decently modern computer. I just went on newegg.com and they got new computers that are only $135. Legacy/old hardware is only holding back operating systems such as Linux/Ubuntu.

---

