---
title: "Adding &quot;reserve=&quot; to grub2"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Blojic on 2011-06-21
I've just installed Natty over a fresh install of Lucid to try it out.

I have a weird and wonderful laptop with a bios bug to do with hardware memory addressing and so need to add "reserve=0xffb00000,0x100000" as a boot parameter, see this link:
[http://www.fitzenreiter.de/averatec/index-e.htm]("http://www.fitzenreiter.de/averatec/index-e.htm")

The author gives instructions on how and where to put these things into menu.lst, but with grub2 things are different (and I'm a bit thick!)

Could anyone please point me in the right direction as to where to put them with grub2 so that my kernels and future updates will pick this parameter up?

I have no sound with Natty either and don't know where to start looking, but I'll post that in a different thread...

Thanks,

---

### Post by samigina on 2011-06-21
This will create a custom entry for your grub.

**sudo gedit /etc/grub.d/40_custom**

This file should looks like:

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

Add your new custom entry to the file, this is a example of a grub2 menu entry:

> menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f1139728-31c0-4033-b3af-78eaa5694eef
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f1139728-31c0-4033-b3af-78eaa5694eef ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}

The final file should look like:
> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f1139728-31c0-4033-b3af-78eaa5694eef
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f1139728-31c0-4033-b3af-78eaa5694eef ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}

Then do a **sudo update-grub2**

I guess your "reserve" must be in the line with "quiet" and "splash".

You can copy your default entries from /boot/grub/grub.cfg paste it in 40_custom, edit the entrie with the new parameter and update the grub.

Let me know if it works.

---

### Post by Blojic on 2011-06-21
Thanks for the response - unfortunately no, no luck. My file looked like this: -

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f1139728-31c0-4033-b3af-78eaa5694eef
linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f1139728-31c0-4033-b3af-78eaa5694eef reserve=0xffb00000,0x100000 ro quiet splash vt.handoff=7
initrd	/boot/initrd.img-2.6.38-8-generic
}
```

but the system still hangs before the grub screen.

Any other ideas? Your help is appreciated.

Thanks,

---

### Post by drs305 on 2011-06-21
> **Blojic said:**
> Thanks for the response - unfortunately no, no luck.

but the system still hangs before the grub screen.

Any other ideas? Your help is appreciated.

Thanks,

Where you placed your entry is the correct location for adding kernel pararmeters [(http://www.kernel.org/doc/Documentation/kernel-parameters.txt)]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"). I checked the available kernel options and the one you added is available and appears to be in the correct format (I can't vouch for the actual numbers).

However, you state the system still hangs *before* the Grub screen. You may have other problems, since the kernel options are passed to the kernel *after* Grub starts to transfer control. If you aren't getting to the Grub menu then adding the kernel option isn't going to solve that part of the problem.

Are you sure you aren't getting the Grub menu before the problem starts? You can try holding down the SHIFT key to ensure you get the Grub menu in case you just aren't seeing the menu and it is progressing beyond that point during the boot before the problem presents itself.

Added:
You posted the contents of your custom menu. Did you check the contents of /boot/grub/grub.cfg to make sure the contents were added to the actual controlling file? (running 'sudo update-grub' and making sure the /etc/grub.d/40_custom file is executable if it isn't incorporated)

---

### Post by Blojic on 2011-06-21
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187671]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187671")

Show the problem with my particular laptop

Have a look at comment #64

> In case anyone is wondering, with GRUB2 (karmic) default kernel boot parameters go in /etc/default/grub, specifically in 'GRUB_CMDLINE_LINUX_DEFAULT'. Editing this file should be followed by a 'sudo update-grub'.

My /etc/default/grub looks like this...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Does this sound right to anyone? If so, could you point me towards the right syntax (ie, where wound "Reserve=" go in relation to ""quiet splash"")

(Sorry, but it's all gobbledygook to me!)

Thanks,

---

### Post by drs305 on 2011-06-21
If you don't want a custom menu, you would open /etc/default/grub and add any kernel options to the end of the line (inside the quotes). Save the file, then update grub.
```

gksu gedit /etc/default/grub
```

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reserve=0xffb00000,0x100000"

---

### Post by Blojic on 2011-06-21
> Added:
You posted the contents of your custom menu. Did you check the contents of /boot/grub/grub.cfg to make sure the contents were added to the actual controlling file? (running 'sudo update-grub' and making sure the /etc/grub.d/40_custom file is executable if it isn't incorporated)

Sorry, only just read that/...

/boot/grub/grub.cfg - No, "reserve=..." wasn't added

```
ls -l  /etc/grub.d/40_custom
-rwxr-xr-x 1 root root 681 2011-06-21 14:41 /etc/grub.d/40_custom

```

Any ideas?

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reserve=0xffb00000,0x100000"

will work for me for now - it'll save my <Esc> key falling off at boot.

Twould be nice to get it sorted though.

Once again, thank you for your time (and patience!)

---

### Post by drs305 on 2011-06-21
> **Blojic said:**
> 
will work for me for now - it'll save my <Esc> key falling off at boot.


You'll have to try it and see. If the problem occurs before Grub it won't help; afterward it might.

By adding the lines to /etc/default/grub it may have corrected any of the following issues:
[LIST]
[*]Grub/you weren't selecting the 40_custom menu at boot. The kernel option will now be in all the automatically-generated menu items in your default installation.
[*]If for some reason the 40_custom entry wasn't incorporated into the Grub menu.
[*]There was a mistake in the /etc/grub.d/40_custom menu which prevented it from booting
[/LIST]

---

### Post by Blojic on 2011-06-22
Solved - I must've been doing something wrong yesterday.
I edited 40_custom & /etc/default/grub as previous on fresh installs of 11.04 & 10.04 and both boot fine (even after kernel updates on both).

Thank you very much, gentlemen.

---

