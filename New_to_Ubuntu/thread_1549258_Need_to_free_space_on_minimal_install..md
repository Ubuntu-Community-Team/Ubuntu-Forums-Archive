---
title: "Need to free space on minimal install."
date: 2010-08-09
forum: New to Ubuntu
---

### Post by frostypepper on 2010-08-09
I have made a minimal install of 9.10 on a tiny 2Tb sata flash disk-on-module. I would like to strip out all the unnecessary items out of the OS to make as much room as possible.

Any ideas what I can ditch to give me some elbow room?

I have tried to uninstall openoffice to no avail. It keeps telling me I dont have a libboost1.38-doc needed but wont install it. How lovely, a apt-get install libboost1.38 does nothing for me.

I simply want to strip this thing down to bare bolts, its ultimately going to be running xbmc (which is actually already on it). I dont need anything else related to a desktop, email, office, etc.

I will graciously accept any assistance.

---

### Post by Bachstelze on 2010-08-09
> **frostypepper said:**
> I have made a minimal install of 9.10 on a tiny 2Tb sata flash disk-on-module.

2 GB, surely. ;) If you have openoffice installed, your installation is nt minimal. Try this: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Type 'cli' at the prompt, you will get a real minimal system.

---

### Post by snowpine on 2010-08-09
+1, OpenOffice indicates it is not a "minimal install."

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

2gb is going to be a tight squeeze no matter how you slice it. Have you tried Puppy (~100mb), SliTaz (~30mb), or TinyCore (~10mb)?

---

### Post by frostypepper on 2010-08-09
I was fairly certain it was a minimal install. Downloaded a minimal Cd and everything.

I started digging around the / dir via 'sudo du -ks * |sort -rn |head' to find the largest thing on the drive. I eventually ended up in a openoffice folder under /usr that was taking up much of my space.

What perhaps is this folder for?

Snowpine, thanks for the suggestions; I will most definitely look into those distros.

---

### Post by linux18 on 2010-08-09
openoffice is for writing documents that microsft will understand (thats why its so bloated)

it can be uninstalled through synaptic, also try this script ```
 #!/bin/bash

####----------------------------------------------------------
####----Functions---------------------------------------------

aa (){
  echo
  echo
  echo
}

####----------------------------------------------------------
####----Intro-------------------------------------------------

echo "Seth's Ubuntu Cleaner"
echo "version 0.01.1    revision 3"

####----------------------------------------------------------
####----Package Cleanup--------------------------------------- 

aa
read -p "remove braile display and screen magnifier (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove gnome-orca brltty brltty-x11 gnome-accessibility-themes gnome-mag libgnome-mag2
fi

aa  
read -p "remove speech synthesizer (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove espeak espeak-data libespeak1 libgnome-speech7
fi

aa
read "remove Bluetooth support (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove bluez-audio bluez-cups bluez-gnome bluez-utils
fi

aa
read "remove evolution mail and Ekiga voip (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove evolution-common evolution-data-server evolution-exchange evolution-plugins evolution-webcal
fi

aa
read "remove various Asian/Arabic fonts (y/n)?" y
if [ $x = "y" ]; then
 sudo apt-get remove ttf-arabeyes ttf-arphic-uming ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-thai-tlwg ttf-unfonts-core
fi

aa
read "remove F-spot, Tomboy, Banshee(y/n)?" y
if [ $b = "y" ]; then 
 sudo apt-get remove mono-common
fi

aa
read "remove openoffice (y/n)?" y
if [ $b = "y" ]; then 
 sudo apt-get remove openoffice*
fi

aa
read "remove printing support (y/n)?" y
if [ $b = "y" ]; then 
 sudo apt-get remove cups* hplip*
fi

aa
read "remove help documentation (y/n)?" y
if [ $b = "y" ]; then 
 sudo apt-get remove ubuntu-docs
fi

####----------------------------------------------------------
####----Cache Cleaner-----------------------------------------

aa
read -p "clean .deb caches (y/n)?" x
if [ $x = "y" ]; then
  sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove 
  sudo rm /var/cache/apt/*.bin 
fi

####----------------------------------------------------------
####----Log File Utility--------------------------------------

aa
print -p "Summarize log file size (any)?" a
sudo du -hs /var/log/
print -p "empty logs (y/n)?" x
if [ $x = "y" ]; then
 cp /dev/null /var/log/*.log
 cp /dev/null /var/log/*/*.log
fi

####----------------------------------------------------------
####----Diagnostics-------------------------------------------

aa
read -p "find rogue files larger than 1GB (y/n)?" x
if [ $x = "y" ]; then 
 sudo find / -name '*' -size +1G
fi 

aa
read -p "find rogue files larger than 500MB (y/n)?" x
if [ $x = "y" ]; then 
 sudo find / -name '*' -size +500M
fi

aa
read -p "print total disk usage on all partitions (y/n)?" x
if [ $x = "y" ]; then
 df -Th | grep -v "fs" | sort
fi

####----------------------------------------------------------
####----Outro-------------------------------------------------

aa
echo "DONE"

####----------------------------------------------------------
####----------------------------------------------------------
 
```

---

### Post by frostypepper on 2010-08-10
Linux18 thats great, thanks so much. That script got me pointed in the right direction I think.

I ended up eventually doing a 'sudo apt-get autoremove openoffice*' which cleared out close to 400 mb. I am certainly hoping that it didnt clear out more than needed, but I used clonezilla beforehand to make a image backup just in case. Gotta have a backup for experimentation right?

I cleared out some .deb cache files for a few more Mb, I went from a 97% full disk to having over 40% free. That is not insignificant by anymeans. I will post back if problems occur in case any new linux users  such as myself try to search and reference this post.

---

### Post by linux18 on 2010-08-10
Your welcome, that script is over a year old, but it still gets the job done. I would like to know how well it went or if any data was lost, as I've never used my script on a drive so full. If everything works, then a few tweaks will probably make it a very effective script.

---

### Post by frostypepper on 2010-08-10
I have ended up rebooting the computer a half a dozen times and it seems rock solid.

The script looks great, but most of the things listed were not installed, but it sure helped me get pointed in a right direction.

I left in "remove openoffice", "clean .deb caches"; and the utility and diagnostic sections.

Since Openoffice isnt actually "installed" the apt-get remove doesnt seem to work. I changed it to 'sudo apt-get autoremove openoffice*' and it cleared what I hope to be a ton of office related things out.

It stripped a minimal install from 1.6 Gb to close to 1.1 Gb. Awesome, I had plenty of room to put libboost and x11-dev and scons on to compile my xboxdrv!

---

### Post by linux18 on 2010-08-10
> **frostypepper said:**
> I have ended up rebooting the computer a half a dozen times and it seems rock solid.

The script looks great, but most of the things listed were not installed, but it sure helped me get pointed in a right direction.

I left in "remove openoffice", "clean .deb caches"; and the utility and diagnostic sections.

Since Openoffice isnt actually "installed" the apt-get remove doesnt seem to work. I changed it to 'sudo apt-get autoremove openoffice*' and it cleared what I hope to be a ton of office related things out.

It stripped a minimal install from 1.6 Gb to close to 1.1 Gb. Awesome, I had plenty of room to put libboost and x11-dev and scons on to compile my xboxdrv!
looks like I should continue working on the script, I have a few more things I could include to improve it and I do have time tomorrow if I'm not working on my own distro. I'll post back if I find a way to further reduce space, but 1.1 GB sounds pretty cllose to the limit of 1034MB

---

