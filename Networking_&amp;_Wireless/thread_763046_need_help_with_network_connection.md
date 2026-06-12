---
title: "need help with network connection"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by Seadevil on 2008-04-22
Help!  I am trying to get online and hooked up to my lan, and
I can't get ubuntu 7.10 to connect to my router. Following some
instructions, i got to this line:  "Check for a connection to the router
   1.  Open a Terminal (Applications ? Accessories ? Terminal) and type the command: iwconfig.
   2.  If there is an entry that says ESSID="" then see Setting Up WPA (the section called “Configuring WPA support.”
   3. If the ESSID for our router is shown there may be a problem with ACPI support. Boot the kernel with the pci=noacpi option"

my question is this:  How do i do line #3 ?? how do i boot the kernel ??  what kernel?  do i do this in the terminal?

thanks

---

### Post by Iowan on 2008-04-23
Do some more searching for details (mine are incomplete...sorry), but you will need to edit a file (from a terminal): ```
 sudo nano /boot/grub/menu.lst
``` modify the line that begins **kernel** Unfortunately, I don't remember exactly where to put the **pci=noacpi** option.  Afterward, issue **update-grub**.

---

