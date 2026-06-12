---
title: "Nvidia card problems Maverick"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by beew on 2010-10-16
I would like to know how to install the Nvidia-96 driver in  Maverick. I have upgraded an old computer from Lucid to Maverick and the Nvidia driver has gone. I logged into the terminal instead of the desktop as a result (even though the nouveau drivers were installed). With the help of someone on this forum I was able to boot back into the desktop by removing /etc/X11/xorg.conf

Now I am back to ugly graphics and I need to reinstall the Nvidia driver. In Lucid it is just firing up "Hardware Drivers" and it will handle it automatically. Problem is in Maverick "Additional Drivers" doesn't even detect the card. I installed the nvidia-96 package via Synaptic (it is the one Lucid used before the upgrade) and rebooted but there was no effect. I ran "sudo nvidia-xconf" and then rebooted and I landed in the terminal again so once again had to remove xorg.conf to boot back into the Desktop.

 I have been going around in circle. I would appreciate any help.

P.S. I tried with another computer with a newer Nvidia card and "Additional Drivers" picked up the card and installed the package nvidia-current But on reboot the splash screen disappeared and it gave an error message about plymouth and momentarily showed the terminal before booting into the Desktop. Once I got to the Desktop it worked flawlessly. But I cannot get back the splash screen even after removing the Nvidia driver (I actually have Maverick installed in an external hard drive,--it is a different installation from the one above,  so I have to remove the Nvidia driver before I exit so I can use the installation on other computers)

So apart from the first question about nvidia-96, there are also some less severe problems with newer nvidia cards. None of these happen in Lucid and it seems like a very bad regression.

---

### Post by azurehi on 2010-10-16
> **beew said:**
> I would like to know how to install the Nvidia-96 driver in  Maverick. I have upgraded an old computer from Lucid to Maverick and the Nvidia driver has gone. I logged into the terminal instead of the desktop as a result (even though the nouveau drivers were installed). With the help of someone on this forum I was able to boot back into the desktop by removing /etc/X11/xorg.conf

Now I am back to ugly graphics and I need to reinstall the Nvidia driver. In Lucid it is just firing up "Hardware Drivers" and it will handle it automatically. Problem is in Maverick "Additional Drivers" doesn't even detect the card. I installed the nvidia-96 package via Synaptic (it is the one Lucid used before the upgrade) and rebooted but there was no effect. I ran "sudo nvidia-xconf" and then rebooted and I landed in the terminal again so once again had to remove xorg.conf to boot back into the Desktop.

 I have been going around in circle. I would appreciate any help.




P.S. I tried with another computer with a newer Nvidia card and "Additional Drivers" picked up the card and installed the package nvidia-current But on reboot the splash screen disappeared and it gave an error message about plymouth and momentarily showed the terminal before booting into the Desktop. Once I got to the Desktop it worked flawlessly. But I cannot get back the splash screen even after removing the Nvidia driver (I actually have Maverick installed in an external hard drive,--it is a different installation from the one above,  so I have to remove the Nvidia driver before I exit so I can use the installation on other computers)

So apart from the first question about nvidia-96, there are also some less severe problems with newer nvidia cards. None of these happen in Lucid and it seems like a very bad regression.

I had the same Nvidia 96 problem with Maverick.  I ended up installing it using the alternate install iso.  Once installed I had no mouse cursor.  I updated, rebooted...no mouse cursor.  I then went to Synaptic, found Nvidia 96, installed it and rebooted.  I Then had a cursor but the flicker was intolerable.  I believe I looked then looked under system > Administration > Nvidia X server and found that I could choose from several resolutions (1024x768) but the refresh rate was zero and could not be changed.  Most disappointing!  

I went back to 10.04 and got Nvidia 96 driver to work, as above, and have stayed with it.  Prior to returning to 10.04 after 10.10 troubles, I was using PCLinuxOS 2010.07 Gnome with Excellent results - until an upgrad last week would not let me get to desktop.

Ubuntu used to be my first choice but after 9.04 I have had increasing difficulties because of my video card, which I guess Is old.

---

### Post by cariboo on 2010-10-16
I don't think the Nvidia 96 drivers have been upgraded to work with Xorg 1.9 yet, so your only choice is to use the nouveau drivers, you can get 3D by installing libgl1-mesa-dri-experimental, it is in the repositories.

---

### Post by beew on 2010-10-16
> **cariboo907 said:**
> I don't think the Nvidia 96 drivers have been upgraded to work with Xorg 1.9 yet, so your only choice is to use the nouveau drivers, you can get 3D by installing libgl1-mesa-dri-experimental, it is in the repositories.


I removed the Nvidia packages (nvidia-96, nvidia settings, nvidia-96 modalities) from Synaptic and installed libgl1-mesa-dri-experimental. The left screenshot shows what the desktop looked like after reboot.

This is clearly unacceptable so I reinstalled the Nvidia packages from Synaptic and the second screen shot shpws what the appearance of my desktop after reboot. This is much better than the first one but I can't enable any 3D effect. To do so would require running "Sudo nvidia-xconfig" and on restart that will reboot into the terminal.

How do I get out of this impass without reinstalling Lucid?

P.S. Do you notice anything strange about the first screenshot apart from the distorted graphic? Yes, "Additional Drivers" told me that the bcmlegacy driver is not installed but I was connnecting to the internet using the bcmlegacy driver! So  I tried to activate it in hardware driver to see what would happen and I got the error message on the screenshot.  I should start a new thread on the broadcom driver. But it appears that the upgrading was not going so well on the propietary drivers. :(

---

### Post by beew on 2010-10-17
There is no /etc/X11/xorg.conf in Maverick and whenever one is created (by Nvidia setting manager or manually) the machine always boots into the terminal and xorg.conf has to be removed into to boot into the desktop.

Any help??

---

### Post by beew on 2010-10-18
bump??

There is a work around here which  is similar to cariboo907's idea but in more detail, but it doesn't work for me because I don't have an xorg.conf file and attempting to create one always sends me to the terminal on reboot and I could only get back to the desktop by removing the xorg.conf file I had created.

[http://ubuntuforums.org/showthread.php?t=1590367&page=2](http://ubuntuforums.org/showthread.php?t=1590367&page=2)

---

### Post by beew on 2010-10-21
Hahahahaha!!!! After some trial and error and two fresh installations I  have finally done it. I now have 3d and Compiz in my Maverick box with a  Nvidia-96 driver.

The idea is basically that if  I can't wait for them to upgrade the Nvidia driver, I may try downgrading Xorg.

Here is the procedure.

1. Remove all Nvidia related items using Synaptic

2. Remove xserver-xorg (and all the dependencies)

3. Remove gtk-jockey, jockey common and fglrx-modalities (more on this later)

4. make a back up copy of the sources list and then replace all  occurrence of "maverick" with "lucid" and save it as the new sources  list. Then refresh the repositories (either reloading Synaptic or "sudo  apt-get update)

5. Reinstall xserver-xorg (and all the dependencies which are removed in  step 2), reinstall gtk-jockey, jockey common and fglrx-modalities. So  these are all from Lucid. In particular step 3 and 5 downgrade  "Additional Drivers" to Lucid's "Hardware Drivers".

6. Replace the sources list by the old one that has been saved, thus reverting back to Maverick. Refresh the repository.

7. Lock the version for all the xserver-xorg packages and the jockey  packages that Synaptic suggests upgrading so they won't get upgraded.

8. Make sure that Nouveau drivers are installed because we need to reboot and you don't want to get stuck in the terminal.

9. Reboot.

10. Activate "Hardware drivers" and let it detect and install the nvidia driver  like in Lucid (Maverick's "Additional driver" does not detect the  nvidia-96 driver) Then restart and done!


At first I tried to install the nvidia driver from Synaptic after  downgrading xserver-xorg and reinstating the Maverick repo and  reconfigure xorg and the nvidia driver following this link but it didn't work
[URL="http://ubuntuforums.org/showpost.php?p=9874780&postcount=12"]
http://ubuntuforums.org/showpost.php?p=9874780&postcount=12[/URL]

Somehow I had to reproduce the condition in Lucid and let Hardware Drivers do the detection and installation.

Now I can start working on the wifi problem.
[URL="http://ubuntuforums.org/showpost.php?p=9874780&postcount=12"]
[/URL]

---

### Post by Tosho on 2011-03-19
> **beew said:**
> 
4. make a back up copy of the sources list and then replace all  occurrence of "maverick" with "lucid" and save it as the new sources  list. Then refresh the repositories (either reloading Synaptic or "sudo  apt-get update)

6. Replace the sources list by the old one that has been saved, thus reverting back to Maverick. Refresh the repository.

[URL="http://ubuntuforums.org/showpost.php?p=9874780&postcount=12"]
[/URL]

Can you explain how to accomplish steps 4. and 6., pretty Please? :)

---

### Post by beew on 2011-03-19
> **Tosho said:**
> Can you explain how to accomplish steps 4. and 6., pretty Please? :)

Hi, I think the nvidia-96 driver now works in Maverick. I created this thread before Nvidia updated the driver.

Anyway here is how to do 4) 

In the terminal type

```
gksudo gedit /etc/apt/sources.list
```The sources list will open in the text editor. Then save it under another name, say sources.list_old

Now do a find and replace, change all occurrences of Maverick to Lucid (check whether it is a capital M or not, I don't remember. If you have "mavarick" then change it to "lucid")
After that save it under the name "sources.list". At this point you have replaced Maverick's sources list with Lucid's.


For 6) you basically want to change sources.list_old back to sources.list (now you have two files, sources.list is actually for Lucid whereas sources.list_old is the Maverick one)

In the terminal type
```
cd /etc/apt

sudo mv sources.list_old sources.list
sudo rm sources.list_old


```The second line overwrites the content of sources.list with that of sources.list_old (i.e changing all the "lucid" occurrences back to "maverick". At this point you have two files and they have identical content. The third line removes the duplicate that you no longer need.

P.S.

 The package libgl1-mesa-dri-experimental suggested in cariboo907's post apparently doesn't work with such an old card. I have recently tried it on a machine with a newer Nvidia card and it works. This package  is to be used with the open sourced nouveau driver. The nouveau driver gives you only basic 3d acceleration functions (enough for compiz)but it doesn't support other advanced features for the graphic card like vdpau and quality of video playback is not great.

---

### Post by Mr.Dee on 2011-03-20
Reading this thread would have saved me a fresh install... arg... I should get my vid card working now.

---

### Post by Tosho on 2011-03-26
thanks :) but I did fresh install of lucid anyway it's a good tip!

---

