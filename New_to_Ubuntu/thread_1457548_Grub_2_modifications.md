---
title: "Grub 2 modifications"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by GMHilltop on 2010-04-18
Does anyone know how to "hide" a partition using Grub 2?

[http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList)

shows that 'hide' has now been replaced - Now a part of parttool

What is parttool???

I can't find anything on it.

I have 2 windows installations, and 1 Ubuntu.  When I am booted into one of the windows installations, I don't want it to be able to SEE the partition the other windows partition is on, and vice versa.

Does anyone know how to do this with Grub 2????

Thanks

---

### Post by oldfred on 2010-04-18
Parttool is a command line tool for edit partition flags maybe other things.

If you go into gparted and right click on the partition you can manage flags. Hidden is one of the flags but I have no idea what it does.

---

### Post by drs305 on 2010-04-18
I have not used parttool in Grub2, but here is a quote from a BURG [bug report]("https://bugs.launchpad.net/burg/+bug/517194"). The user seems to be familiar with parttool and Grub2:
> 
I have a triple boot system set up (Ubuntu, Windows 7, Windows XP). When I boot into one of the windows-es, I have to hide the other's partition from it (for compatibility and security reasons). In grub2 I use the following commands:
parttool (hd0,3) hidden+
parttool (hd0,4) hidden-


I would test them for you but don't currently have access to my dual-boot laptop.

---

### Post by GMHilltop on 2010-04-18
Thank you, Thank you!

That did the trick.

For those who learn by seeing like I do, here is what I entered into my 40_custom file that is located in the /etc/grub.d/ directory:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Windows OS to Grub 2 Menu"
cat << EOF
menuentry "Mom & Dads" {
insmod chain
insmod ntfs
parttool (hd0,1) hidden-
parttool (hd0,2) hidden+
parttool (hd0,5) hidden-
set root= (hd0,1)
search --no-floppy --fs-uuid --set 9A7A430F7A42E819
chainloader +1
}

menuentry "Kids Operating System" {
insmod chain
insmod ntfs
parttool (hd0,2) hidden-
parttool (hd0,1) hidden+
parttool (hd0,5) hidden+
set root= (hd0,2)
search --no-floppy --fs-uuid --set 9A18464D18462919
chainloader +1
}

menuentry "Ubuntu" {
parttool (hd0,2) hidden-
parttool (hd0,1) hidden-
parttool (hd0,5) hidden-
parttool (hd0,6) hidden-
recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a1e8016-a158-4e98-ae38-6da0fd528d9a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9a1e8016-a158-4e98-ae38-6da0fd528d9a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}

menuentry "Memory Test - Memtest86+" {
linux16    /boot/memtest86+.bin
}
EOF

FYI partition number 5 (hd0,5) is a partition that we have our stuff on, that I don't want the kids to be messing around with, so I have hidden it.  Partition 6 (hd0,6) is theirs to save stuff on.

I am still going to reorder stuff, but I needed to make it work first.

In case anyone was wondering how I came up with the entry for the Ubuntu partition, I just opened the grub.cfg file and copied what was already written there and entered it into the 40_custom file . . . what can I say - it works, though some of it I don't understand. . . . I just wanted to be able to name it a little cleaner for the menu.

Hope this helps others too.

---

### Post by drs305 on 2010-04-18
Thanks for sharing your solution.  :guitar:

Explaining how and why you made it the way you did is very helpful, and using the 40_custom file makes it a simple way to get it into the Grub2 menu.

When I find time I will try to incorporate your findings into the Grub2 Title Tweaks (with attribution of course). It's not really a *title* tweak but it's something that many users will find helpful.

Edit: Done.
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

---

### Post by oldfred on 2010-04-19
I do not think you want or need these lines in your 40_custom:

echo "Adding Windows OS to Grub 2 Menu"
cat << EOF

I think they came from one original post or web site where the user was adding the lines to the file from a terminal.

---

### Post by GMHilltop on 2010-04-21
I wasn't sure what that part of the code meant so I left it.

I stripped out the:
[INDENT][COLOR=Red]echo "Adding Windows OS to Grub 2 Menu"
cat << EOF[/COLOR]
[/INDENT]from the top
and I got rid of the:
[INDENT][COLOR=Red]EOF[/COLOR]
[/INDENT]at the bottom.  Everything works perfectly.

Just for clarification, the code looks like this:
[INDENT][COLOR=DarkGreen]#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.

menuentry "Mom & Dads" {
insmod chain
insmod ntfs
parttool (hd0,1) hidden-
parttool (hd0,2) hidden+
parttool (hd0,5) hidden-
set root= (hd0,1)
search --no-floppy --fs-uuid --set 9A7A430F7A42E819
chainloader +1
}

menuentry "Kids Operating System" {
insmod chain
insmod ntfs
parttool (hd0,2) hidden-
parttool (hd0,1) hidden+
parttool (hd0,5) hidden+
set root= (hd0,2)
search --no-floppy --fs-uuid --set 9A18464D18462919
chainloader +1
}

menuentry "Ubuntu" {
parttool (hd0,2) hidden-
parttool (hd0,1) hidden-
parttool (hd0,5) hidden-
parttool (hd0,6) hidden-
recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set  9a1e8016-a158-4e98-ae38-6da0fd528d9a
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=9a1e8016-a158-4e98-ae38-6da0fd528d9a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}

menuentry "Memory Test - Memtest86+" {
linux16    /boot/memtest86+.bin
}[/COLOR]    
[/INDENT]Hope that helps someone.
Cheers

---

### Post by drs305 on 2010-04-21
Thanks for posting a successful result.

Just for a bit of clarification, with Grub 2 version 1.98, you can still add a comment in a custom file so you can see it as grub updates. 

The method of doing so has changed now that the initial lines in /etc/grub.d/40_custom file have changed.

To add a comment, you would insert it near the *top* of the default lines, as displayed below:
> 
#!/bin/sh
**[COLOR="DarkRed"]echo "Adding 40_custom." >&2[/COLOR]**
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


When added as above, when update-grub is run, you would see the result in the terminal as the command is executed:
> 
Generating grub.cfg ...
Found background image: bg_earth.png
Adding 40_custom.
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Ubuntu lucid (development branch) (10.04) on /dev/sda2
done


---

### Post by GMHilltop on 2010-04-21
Is there a way to add a comment to the Menu that gets displayed to the users?

For example, could I make the list look like this:

[INDENT][COLOR=DarkGreen]Kids Operating System
Mom and Dads
Ubuntu

<=== The selections Below are for Maintenance Only ===>

Memtest86+[/COLOR]
[/INDENT]
I did that with the old menu.lst but I am not sure how to do it with the new Grub2.

Any thoughts?

---

### Post by drs305 on 2010-04-21
> **GMHilltop said:**
> Is there a way to add a comment to the Menu that gets displayed to the users?
I did that with the old menu.lst but I am not sure how to do it with the new Grub2.

Any thoughts?

You can do it with an almost-blank menuentry. For example:
> 
menuentry "Don't Even THINK About Choosing This Selection" {
insmod ext2
}


In experimenting I found I had to include at least one operation below the menuentry line for it to display.

It's easy to place it where you want in a 40_custom menu. Getting it where you want it to display in one of the other scripts would be a bit more difficult.

---

### Post by GMHilltop on 2010-04-21
I thought I tried that, because that is basically how I got it to work with the menu.lst

Oh well, Thanks drs305

That worked perfectly - not sure what I did wrong last time .... (I think I might have inserted ntfs instead of ext2 - don't know if that was it though)

---

### Post by oldfred on 2010-04-21
I put in spacer also, but one time I set the boot the the wrong number so it was trying to boot my blank line. For some strange reason that did not work well.:)

menuentry " " {
set root= 
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

---

