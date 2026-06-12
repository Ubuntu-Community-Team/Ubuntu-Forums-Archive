---
title: "Newbie to linux, kubuntu update issue"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by slow_90firebird on 2011-04-17
Hi all

Ive always used windows, but even then I was never what you would call a "power user". Few days ago decided to try linux, researched different distros, was a toss up between kubuntu and slack for the KDE, figured kubuntu would be better for me as a total newb.

This is on my main PC, which still has WinXP installed on the primary SATA drive. I installed kubuntu on a smaller primary ext4 partition on my 2nd SATA drive and used GAG bootloader to load NTLDR or GRUB. Had to install with the alternate CD due to my SATA drives not being recognised.

After getting it installed, it took me a few days of really trying alot of different things to get both my monitors working. I ended up having to use the NVIDIA driver (i have dual 7600GT's with SLI bridge) downloaded from the website and installed at the command line. However, there was alot of other work I had to do in the command line just to get the driver to install. I cant remember all I did because I was trying so many commands from different sites and never really understood what they were doing.

Anyhow, now my graphics are displaying properly on both monitors, and twinview works great! Luckily I took and image of the partition, because when I when I tried to let kubuntu install the (242) updates available, it went fine untill i rebooted. It booted straight into the "welcome to ubuntu" command line. No GUI or login screen ever appeared. I tried starting KDM and X (dont know the difference) from the command line with "sudo" and both had different errors.

Any help would be appreciated because I really have taken a liking to kubuntu and would like to start seriously using it, but if I cant ever let it update what is the point?

Thanks!

---

### Post by oldos2er on 2011-04-17
Did you try installing the Nvidia proprietary drivers from the repositories? There's nothing wrong with downloading and installing the drivers from Nvidia's website manually, but everytime there is a kernel update or upgrade you will have to install them again, and I think this is what might have happened to you (rebooting to no GUI). When you use the drivers from the repositories, APT (the package management system) automatically upgrades the kernel for you.

Try booting into recovery mode, root access with networking, and run ```
apt-get update && apt-get install nvidia-current
``` Reboot, and let us know if that worked. If not, posting any error messages you see will help us to help you.

---

### Post by SeijiSensei on 2011-04-17
> **oldos2er said:**
> Try booting into recovery mode, root access with networking, and run ```
apt-get update && apt-get install nvidia-current
``` Reboot, and let us know if that worked. If not, posting any error messages you see will help us to help you.

You might want to run nvidia-xconfig from the terminal before rebooting as well.

---

### Post by slow_90firebird on 2011-04-17
thanks guys. I had no idea how to boot into a command line, never mind with admin privilages. So, I shut off the GUI instead. I ran all of those commands you posted, and then restarted the computer and did the automatic updates.
 
After the updates were done, I still had everything working untill I rebooted again, and then now I am stuck back in the command prompt.
 
 
 
IIRC when I first installed kubuntu, it automatically used its own set of drivers to run my card. The downside to this was it would only recognise my older dell monitor, not my new viewsonic, and would display the same image on both. I didnt have the nvidia configuration utility to set both monitors active. And get twinview working. Also, everything was a little blurry and the eye candy didnt work as smoothly.
 
Looks like I will have to re-ghost that partition again when I get time, cause Im useless with the command line.
 
But I think if this is how its going to be every time a new update comes out, il stick with windows XP. Unless you can recommend a different distro that will support nvidia cards better.
 
Thanks

---

### Post by slow_90firebird on 2011-04-17
i just reghosted the partition with an image I took of the fresh kubuntu install before both monitors worked. Im gonna play with it and see if I can figure any thing out.

---

### Post by oldos2er on 2011-04-17
> **slow_90firebird said:**
> But I think if this is how its going to be every time a new update comes out, il stick with windows XP. Unless you can recommend a different distro that will support nvidia cards better.
Thanks

The proprietary Nvidia Linux drivers are the same no matter the distro. And, like I said, if you install the ones from the repositories upgrades are painless. In Kubuntu, click the Kickoff menu, Applications, System, Additional Drivers.

---

### Post by slow_90firebird on 2011-04-17
> **oldos2er said:**
> The proprietary Nvidia Linux drivers are the same no matter the distro. And, like I said, if you install the ones from the repositories upgrades are painless. In Kubuntu, click the Kickoff menu, Applications, System, Additional Drivers.
 
I just installed the drivers as you described, through the GUI. It wouldnt work though, untill I opened konsole and typed "sudo apt-get update"
 
After that It installed the nvidia driver all automatically.
 
I restarted the computer and was able to configure both monitors perfectly! No command prompt.
 
Then I started the kubuntu auto updates and when they finished i restarted.
 
It showed the blue screen with some dots, then went straight to the command line. No login screen. I can use my same name and password to login to the command line, but that doesent get me far.

---

### Post by mastablasta on 2011-04-18
very odd. Makes me think if you first removed any previously installed drivers and purged them off the system before installing new ones as mentioned.
 
type 
 
startx
 
to start the X windows system (GUI). if it doens't start it should at least give out an error.
 
to restart computer from command line
 
sudo shutdown -r now

---

### Post by slow_90firebird on 2011-04-18
Is there a way I could remove the universal driver that was there, while keeping the new one? I've already ghosted it back to a working state again.

Another thing is that the nvidia configuration couldn't update the xorg so I copied it from the preview and ran sudo Kate to paste and save.

If I just never get the updates how long can I use kubuntu before I see issues?

---

### Post by oldos2er on 2011-04-18
> **slow_90firebird said:**
> Another thing is that the nvidia configuration couldn't update the xorg

It needs to be run as root

**sudo nvidia-xconfig**

---

