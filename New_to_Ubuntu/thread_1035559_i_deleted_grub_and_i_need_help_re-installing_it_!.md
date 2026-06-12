---
title: "i deleted grub and i need help re-installing it !"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by smooth3006 on 2009-01-09
i was triple booting vista / 7 beta / xubuntu. i think grub installed to the 7 partition and i accidentally deleted it. now i can't access xubuntu at all because grub is gone. i get an error 22 now when i boot. i was able to re-install 7 and get the vista bootloader back but i think i will have to totally install grub again from scratch. 


can this be done ? or is my install toast now ? what would be the command do do this ? :confused:

---

### Post by taurus on 2009-01-09
Maybe this helps.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Ben Page on 2009-01-09
here is some more info here
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
I had problem dual booting, too, windows is a *******, it sees only Microsoft. Ended up reinstalling Ubuntu, freshly installed GRUB recognizes everything correctly. Install Vista, the 7 and then install Ubuntu last and you'll have a nice multiboot computer. For some reason Winblows doesent like to boot with Linux :o, but Linux dualboots with Windows and any other OS without a problem...

---

### Post by caljohnsmith on 2009-01-09
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://internap.dl.sourceforge.net/sourceforge/bootinfoscript/boot_info_script.sh' && sudo bash boot_info_script.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

