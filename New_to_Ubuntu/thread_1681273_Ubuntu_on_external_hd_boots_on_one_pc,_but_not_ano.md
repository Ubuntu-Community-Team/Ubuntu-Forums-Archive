---
title: "Ubuntu on external hd: boots on one pc, but not another"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by ClaudeFleming on 2011-02-03
I tried completely reformatting the external hd twice and installing ubuntu on it on my old laptop. It worked fine. I tried booting from this usb drive on my newer toshiba L675D laptop and it wouldn't work. So I did a fresh format and install on my new laptop. Now when I boot from the usb drive, and hold down shift, it says: Grub loading, and a blinking hyphen stays underneath it, blinking incessantly. I have to press the power button to get my computer up and running again. It's version 10.4. I don't know what to do.

Any help would be appreciated, 

Sorry for the whining,

Claude

---

### Post by bhaverkamp on 2011-02-03
Could be you don't have the right drivers installed for the new hardware on the newer computer. Try booting into a live CD on the new computer and then checking to see if you can see the USB HD after that. If you can it is a driver issue with the initrd of your HD.

---

### Post by ClaudeFleming on 2011-02-03
I CAN see my external hd. And what was that last initialism you were talking about? You don't know how much I appreciate your response! Thanks a lot. lol this is nothing like windows.

But what if I've completely wiped out my hard drive and given it all to ubuntu?

---

### Post by bhaverkamp on 2011-02-04
Just reread your original email. Failed to note that you said you had built the USB boot disk on your new computer.

Download the boot info script from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and copy it to a USB thumbdrive.

Boot your new computer with a liveCD and your USB drive plugged in. Make sure to boot from the CD.

After the system is up and running, plug in the thumb drive.

Open a terminal and cd to the thumbdrive directory where you put the script.

Run the script 'sudo ./boot_info_script.sh'. This will save a file to your thumbdrive. Include that file in your next response.

This will give us more info to go on...

---

