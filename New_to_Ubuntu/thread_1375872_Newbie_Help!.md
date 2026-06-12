---
title: "Newbie Help!"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by isonr51 on 2010-01-08
Hello folks.  I am _brand new_ to Ubuntu (or any type of Linux platform) after a lifetime of Windows use and am excited about the conversion but I need your help badly. :(

The problem I am having is that, after installing Ubuntu 9.10, and re-booting from the hard drive, I am getting boot failure.  I have a brand new hard drive installed and am letting Ubuntu use the entire disc.  The installation process seems to go just fine but when I remove the installation CD and re-boot I get the following error message:

[COLOR=Red][B]error:  no such device:  a6055979f-d106-4518-8b15-714d6a66962c
failed to boot default entries.[/B][/COLOR]

[COLOR=Red]**press any key to continue....**[/COLOR]

Pressing any key repeats the same message over and over.  If I press ESC I get a menu screen reading "**[COLOR=Blue]GNU GRUB  version 1.97~beta4[/COLOR]**" at the top with the option to start "**[COLOR=Blue]Ubuntu, Linux 2.6.31-14-generic[/COLOR]**", "**[COLOR=Blue]Ubuntu, Linux 2.6.31-14-generic (recovery mode)[/COLOR]**", or a couple of options to run a memory test.

I just can not seem to get past this.

If I then boot from the installation CD and select "Run Ubuntu without making any changes to your computer" (or something like that) I get the normal GUI.  If I select the "Places" menu, the hard drive shows up as "158 GB Filesystem".  If I select that option a windows comes up that has "[COLOR=Red]**a6055979f-d106-4518-8b15-714d6a66962c - File Browser**[COLOR=Black]"[/COLOR] [COLOR=Black]at the top and all of the folders on the HDD show up.

What do I need to do to get my computer to boot from the HDD?

Thanks much!
[/COLOR][/COLOR]

---

### Post by juancarlospaco on 2010-01-08
edit the grub from the grub itself (press e) 
and change "a6055979f-d106-4518-8b15-714d6a66962c" for "/dev/sda"
where sda is your /

---

### Post by presence1960 on 2010-01-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nothingspecial on 2010-01-08
The first thing to try is booting into recovery mode and typing ```
update-grub
```

If that doesn`t work I`m afraid this is going to get a bit complicated, especially for a new user.

---

### Post by presence1960 on 2010-01-08
> **nothingspecial said:**
> The first thing to try is booting into recovery mode and typing ```
update-grub
```

If that doesn`t work I`m afraid this is going to get a bit complicated, especially for a new user.

in recovery mode choose netroot then run that command.

---

### Post by isonr51 on 2010-01-11
Thanks!  This worked!  Now, if I can just get it to recognize my old wireless NIC.

---

