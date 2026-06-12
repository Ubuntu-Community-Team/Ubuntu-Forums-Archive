---
title: "Updated kills windows dual boot."
date: 2010-06-03
forum: New to Ubuntu
---

### Post by kiev749 on 2010-06-03
I recently updated to lucid and now when i restart my Dell e1705 and run grub to dual boot, it gives me the option to return to windows(Windows Xp Media Center Edition) but it will not allow it to run properly as i get a Gen Error when selected. When selected again it says "No Bootable Devices" what do i need to do?

---

### Post by echo.whoami on 2010-06-03
Take a look here 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

It says how to reinstall grub and update it. I hope that this helps

---

### Post by wilee-nilee on 2010-06-03
> **kiev749 said:**
> I recently updated to lucid and now when i restart my Dell e1705 and run grub to dual boot, it gives me the option to return to windows(Windows Xp Media Center Edition) but it will not allow it to run properly as i get a Gen Error when selected. When selected again it says "No Bootable Devices" what do i need to do?

it is not a good idea to try fixes without more information and help from somebody who knows the answers. 
To quickly see your set up posting this boot script is the best start, post it in code tags so it is easier to read.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kiev749 on 2010-06-04
i went and did what you said and this is what i got when i ran terminal:

kevin@kevin-laptop:~$  sudo bash [path/to/the/download_folder]/boot_info_script*.sh

bash: [path/to/the/download_folder]/boot_info_script*.sh: No such file or directory

Should point out that i not a very heavy linux user... just looking to see what other OS are out there.

---

### Post by wilee-nilee on 2010-06-04
> **kiev749 said:**
> i went and did what you said and this is what i got when i ran terminal:

kevin@kevin-laptop:~$  sudo bash [path/to/the/download_folder]/boot_info_script*.sh

bash: [path/to/the/download_folder]/boot_info_script*.sh: No such file or directory

Should point out that i not a very heavy linux user... just looking to see what other OS are out there.

I had a few problems when I first tried running the script.;)
So down load the script with the live cd put it on the desktop by dragging it from where it shows up then run
```
sudo bash ~/Desktop/boot_info_script*.sh 
```
this sholud drop the readout to the desktop which you open copy and paste into the reply window with the code tags. You can also highlight the text in the reply and click on the # in the reply panel and this will put it in code tags.

If you look The code to use in the terminal just been changed from, [path/to/the/download_folder] to Desktop.

---

