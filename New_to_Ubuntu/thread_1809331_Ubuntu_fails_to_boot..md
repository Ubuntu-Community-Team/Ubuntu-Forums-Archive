---
title: "Ubuntu fails to boot."
date: 2011-07-21
forum: New to Ubuntu
---

### Post by smashn on 2011-07-21
Hi, I've got Ubuntu 10.10 32-bit on my pc along with Windows XP. It's worked charmingly for two months without any problems. But now Ubuntu fails to boot after the Grub screen and all it shows is the following screen (I took a pic). Last time that it booted, it was working real slow and the save as dialog window wasn't showing when I tried saving a pic. So I restarted the system and it doesn't boot now. Also, the timer in the Grub screen is not showing now.

[ATTACH]197986[/ATTACH]

Any help would be greatly appreciated. Thank you :)

---

### Post by _0R10N on 2011-07-21
Did you modify something on the grub's configs? It looks like something related to the modules information required at boot time is missing.

---

### Post by Bucky Ball on 2011-07-21
Boot from a live CD, plug an ethernet cable in so you are online and try this in a terminal (Applications>Accessories>Terminal), one command after the other waiting for each command to do its thing before proceeding to the next:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```From here:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Once installed, run Boot-Repair and choose, 'Install Grub to MBR' option. Reboot.

Hope that helps. ;)

(Before anyone asks, yes, this app is designed to install and run in a LiveCD boot as it is designed for people that can't get to grub.)

---

### Post by smashn on 2011-07-25
I tried this, but it just refuses to install. Sometimes it just says files are missing or else gets stuck. It doesn't even work from the Software Center. Is there any other way? Can I repair Ubuntu; in the process repairing grub?

---

### Post by Seq on 2011-07-25
> **smashn said:**
> Hi, I've got Ubuntu 10.10 32-bit on my pc along with Windows XP. It's worked charmingly for two months without any problems. But now Ubuntu fails to boot after the Grub screen and all it shows is the following screen (I took a pic). Last time that it booted, it was working real slow and the save as dialog window wasn't showing when I tried saving a pic. So I restarted the system and it doesn't boot now. Also, the timer in the Grub screen is not showing now.

[ATTACH]197986[/ATTACH]

Any help would be greatly appreciated. Thank you :)

Hard to tell from just the screenshot, but it looks like grub is working and ran your kernel. The trouble seems to be in the initrd, which is either missing completely or incomplete.

In the grub menu you should be able to select an older kernel. Hopefully it still has an intact initrd. From there you should be able to rebuilt the initrd for the newest kernel. If the grub menu doesn't show up, try pressing a button before it should (I usually press the down arrow) to indicate you want to change from the default selection.

Alternatively, you will need to do it from the Live CD.

---

### Post by smashn on 2011-07-26
> **Seq said:**
> Hard to tell from just the screenshot, but it looks like grub is working and ran your kernel. The trouble seems to be in the initrd, which is either missing completely or incomplete.

In the grub menu you should be able to select an older kernel. Hopefully it still has an intact initrd. From there you should be able to rebuilt the initrd for the newest kernel. If the grub menu doesn't show up, try pressing a button before it should (I usually press the down arrow) to indicate you want to change from the default selection.

Alternatively, you will need to do it from the Live CD.
Guys, I'm a total noob. I don't know what you meant there about rebuilding the kernel. The grub menu displays always but the countdown to default option doesn't show now. I have to manually select which OS to run. 

Please tell me if I can reinstall Ubuntu without losing the folders I had on my desktop?

---

### Post by Peter09 on 2011-07-26
Create a live usb/cd and you can then get to your home directory and copy off all your data.Then re-install - set up your user as normal and copy back your documents etc to your directory.
 
Also - some of the live cds have a recovery mode - might be an option.

---

### Post by smashn on 2011-07-26
> **Peter09 said:**
> Create a live usb/cd and you can then get to your home directory and copy off all your data.Then re-install - set up your user as normal and copy back your documents etc to your directory.
 
Also - some of the live cds have a recovery mode - might be an option.
Okay, I guess I'm going to have to resort to this. Can anyone tell me how I can copy Google chrome preferences including saved passwords and so? I really wish to avoid reinstalling as a lot of the updates to 11.04 had been downloaded and I'd lose that now. Is this the last resort? Any other way to fix Grub?

---

### Post by Peter09 on 2011-07-26
They will normally in hidden directories in your home directory. Copy all of your home directory, then just copy back any hidden directories back afterwards.

---

### Post by smashn on 2011-07-26
> **Peter09 said:**
> They will normally in hidden directories in your home directory. Copy all of your home directory, then just copy back any hidden directories back afterwards.
Do you mean the chrome preferences or the downloaded updates?

---

### Post by Peter09 on 2011-07-26
your preferences etc are held in hidden directories in your home folder.

---

### Post by smashn on 2011-07-26
> **Peter09 said:**
> your preferences etc are held in hidden directories in your home folder.
OK. I'll try reinstalling. I don't mind loosing the downloaded updates. Thanks. :)

---

### Post by smashn on 2011-08-10
Can you guys tell me which is my Home folder where the preferences have been saved?

---

### Post by mikodo on 2011-08-10
If you are in a live usb/cd environment and have your desktop loaded, press alt + Home together and your home will be displayed; or click Places -> Home for it also. Then, press the highlighted arrow pointing up twice; right click on Home; click copy and copy your Home to whatever you plan to save it in.

For a more detailed and advanced way of backing up your stuff, with explanations of where your downloads & other things are saved, see this forum thread:

[http://ubuntuforums.org/showthread.php?t=701386](http://ubuntuforums.org/showthread.php?t=701386)

EDIT: To find the hidden files on you system, when you have clicked the arrow pointing up twice; click View, and in the drop-down list below, click on the button to Show Hidden Files. The link above gives an excellent description of what is in each of the folders for you to follow.

Good Luck!

---

### Post by smashn on 2011-08-10
> **mikodo said:**
> If you are in a live usb/cd environment and have your desktop loaded, press alt + Home together and your home will be displayed; or click Places -> Home for it also. Then, press the highlighted arrow pointing up twice; right click on Home; click copy and copy your Home to whatever you plan to save it in.

For a more detailed and advanced way of backing up your stuff, with explanations of where your downloads & other things are saved, see this forum thread:

[http://ubuntuforums.org/showthread.php?t=701386](http://ubuntuforums.org/showthread.php?t=701386)

Good luck
But i did that and the folders are empty. I don't see any of the files I had saved there when I had been running Linux before Grub screwed up. Or are they all there in hidden files?

---

### Post by Peter09 on 2011-08-10
Cntrl+H should show your hidden files.

---

