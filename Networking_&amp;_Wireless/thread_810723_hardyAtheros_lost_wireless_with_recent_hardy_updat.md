---
title: "hardy/Atheros lost wireless with recent hardy updates"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by clockworkmcd on 2008-05-28
hey, anybody have this issue? I was running hardy, had my wireless running great, had some updates last night and when i rebooted the wireless was gone. do i just need to set it up again? or is there something else i'm not aware of?

{update}

It appears that the current update resets the wireless stuff. so all i did was do what i did in the first place to get my wireless working. Here's the steps i did (again) to get it working.

-plug your machine into a wired connection

- go to system/administration/hardware drivers, and disable by un-ticking the box for atheros hardware access layer (hal)

-reboot your box

-when ubuntu comes back up open the terminal by going to applications/accessories/terminal

-in the terminal type the following:

mkdir madwifi
cd madwifi
wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
sudo apt-get install build-essential

-enter your password when it asks for it and then answer yes to the prompt

-then in the terminal type the following:

tar xfz madwifi-ng-42756-ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
sudo make install
sudo modprobe ath_pci

-at this point if you are using a wired network, unplug your network cable

-in the terminal enter:

sudo reboot

-after you log back into ubuntu, left click on the network icon in the top right corner of the screen and you should see your wireless network listed.

-left click on your wireless ssid and you should see the icon connecting and then you'll see wireless signal bars. at this point you should be connected to your wireless network.

-(this is for an open network not suing wep or wpa)

-go to system/administration/hardware drivers and enable by re-ticking the box for the atheros hardware access layer (hal)

-if you wait a second after you close that box you should get a 'system restart required' popup

-click the blue recycle button in the top right corner, or if after a minute you don't get it, manually select restart.

you should now be online. these are the step that i followed for an acer aspire 5315-2153 notebook with hardy.

---

### Post by shaggy1054 on 2008-05-28
I had the same issue - I was using the madwifi drivers (.9.4) before, and after updating the kernel, my performance and connectivity went to ****. I've started rebooting in an earlier kernel version (.16, as opposed to .18) - that seems to fix all of my problems. A more lasting solution (figuring out why the kernel change killed the wireless) has not yet been forthcoming, although I have seen numerous people having wireless problems after the latest update.

Edit: If you don't know, to do this, press a button at the very beginning of bootup, when you see a countdown. After you do this, you should be able to select an earlier kernel. Don't use the recovery version.

---

### Post by Bartender on 2008-05-28
Had the exact same experience
[http://forum.notebookreview.com/showthread.php?p=3409908#post3409908](http://forum.notebookreview.com/showthread.php?p=3409908#post3409908)

Got the Atheros card in my Dad's HP/Compaq working after several attempts to install the madwifi drivers.  Whoohoo!  The first thing the HP did was update the kernel.  Wireless quit.  D'oh!  I moved the Atheros over to my Acer Centrino laptop, gave my Dad my 4965 card, followed the rules in the above link, and it's working again.  My Acer already had the kernel update.  

I plan to buy a replacement 4965 card soon, so will probably just pull the Atheros and forget this problem ever plagued me.

---

### Post by ElEdTech on 2008-05-28
I had the same issue with my Acer Aspire 5570z running the Atheros 5007 wireless card. After I updated the kernal the wifi did not work. 

What I did to fix mine was uninstall the Madwifi patch and reinstall using the newly updated tarball. 

I used the version 3366 from this forum posting...

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)


Here is the madwifi link..

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

Before I was using the r2756 tarball which was broken by the update. Last night I refollowed the steps from this website...

[http://ubuntufor5570z.blogspot.com/2008/04/update-new-wireless-instructions.html](http://ubuntufor5570z.blogspot.com/2008/04/update-new-wireless-instructions.html)

And my wireless started working... the problem was my suspend and hibernate still did not work and when ever I went to hibernate or suspend I had a full black screen with lots of text.

Then today in the forums I read somewhere that the updated r3366 Madwifi for Atheros patch fixed the hibernate and suspend problem.

So after uninstalling the old Atheros patch, I downloaded the new snapshot, used archive manager to pull it out, used the make and make install commands, did the sudo modprobe ath_pci command, and then added ath_hal and ath_pci to /etc/modules 

Now my wifi is back running (just as it was with the 2756 tarball snapshot from Madwifi) AND my computer hibernates and suspends now!

I would list out all of the commands but I am VERY new to Linux and would feel horrible if someone followed my exact order and messed up their computer. 

All of the information I found was from within different posts in the Networking and Wireless forum...

---

### Post by Bartender on 2008-05-28
"I would list out all of the commands but I am VERY new to Linux and would feel horrible if someone followed my exact order and messed up their computer." 

Well, you're doing better than me.  I still haven't sat down and figured out how to make install etc.  Couldn't have done what I did without step-by-step commands posted.  Afraid I'll break something!

---

### Post by clockworkmcd on 2008-05-28
my network card is built in so no switching it to another computer. i'm also running the wubi version of ubuntu so it's nice because i can just back up the virtual disk and mess around all i want :P so if i mess something up i just restore the virtual disk.

i suppose i'll try what i did before and see if it works. if it does i'll post my findings here. maybe the update just reset the wireless stuff.

---

### Post by clockworkmcd on 2008-05-28
ok i did what i did before and it worked, it appears that it just reset the wireless stuff. i'll update the first post with the steps i followed in case anybody else has this problem.

---

### Post by williamson389 on 2008-05-28
-clockworkmcd
i was very happy that there was another way for this, as i have been trying the walkthrough from nicedude in this thread [http://ubuntuforums.org/showthread.php?p=5058802#post5058802](http://ubuntuforums.org/showthread.php?p=5058802#post5058802)  unfortunately i just tried the steps at post 1 and received 404 page not found error when typing in wget.......
anyone else have this problem or just me?

---

### Post by ElEdTech on 2008-05-28
> **Bartender said:**
> "I would list out all of the commands but I am VERY new to Linux and would feel horrible if someone followed my exact order and messed up their computer." 

Well, you're doing better than me.  I still haven't sat down and figured out how to make install etc.  Couldn't have done what I did without step-by-step commands posted.  Afraid I'll break something!

Basically I used similar commands as listed in this thread. I previously had already done the sudo apt-get install make and build-essential so those we installed already. The only thing different that I did was use a different madwifi link. I think the link I used, as mentioned in my post earlier, is newer. After trying it along with the commands above (replacing the different madwifi tar) my wireless began working again along with sleep and hibernate.

The 2756 driver broke hibernate and suspend on my comp. The 3366 driver makes it work now.

---

### Post by williamson389 on 2008-05-29
when running the command wget [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)  the terminal shows 
connecting to snapshots.madwifi.org|217.24.1.134...connected.
http request sent, awiting response........404 not found
17:14:35 error 404 not found.

anyone know what to do to fix that?

---

### Post by kevdog on 2008-05-29
Just an FYI --

madwifi is a kernel module --> its compiled for a specific kernel version and inserted into the kernel.

When you upgrade kernels, you have then multiple different kernel available or contained on your hard drive, although you only boot using one of them.

When you upgrade kernels, the madwifi driver that was contained in the last kernel, is not contained in the new kernel.  The kernel module must either by installed (through synaptic, apt-get, aptitude), or manually compiled and manually inserted into the new kernel (modprobe).  

That is what your solution is giving you.  You are manually recompiling and reinserting the kernel module into the new kernel.  Booting into the old kernel works, because the kernel module (or simply a file) is contained within the directory structure of the old kernel.

---

### Post by daRealScanMan on 2008-05-29
> **williamson389 said:**
> when running the command wget [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)  the terminal shows 
connecting to snapshots.madwifi.org|217.24.1.134...connected.
http request sent, awiting response........404 not found
17:14:35 error 404 not found.

anyone know what to do to fix that?It's a bad link.  Try this one:  ```
http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
```

---

### Post by williamson389 on 2008-06-03
does anyone know if installing the updates from the update manager will mess with the wireless?
updates include:linux generic, linux restricted modules(which i remember removing)

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by williamson389 on 2008-06-15
^that guy has posted in almost every thread i have read.  i dolved my problem finally.  i used nicedudes walkthrough.  it didnt work for mee before so i ddnt bother trying it until now.  heres the link:  [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

i have a feeling it worked this time because i unistall all of linux-restricted-modules in synaptic

Good Luck

---

### Post by sargirio on 2008-06-22
I have the same problem with my atheros. After the latest update difficulty connected with my network. If I have not wire connection with the net but only wifi how i can install theese drivers??? 

Thanks a lot for your help.

---

### Post by Midwest-Linux on 2008-06-22
I had the same problem and solved it and posted it here on this forum yesterday.


[http://ubuntuforums.org/showthread.php?t=836177](http://ubuntuforums.org/showthread.php?t=836177)

---

### Post by enigmageek on 2008-11-13
Hello all. I have a Toshiba A205 S5843 laptop with AR5007EG chipset. Using the original instructions with the newest ath_hal my wireless works perfectly. I recently built the latest 2.6.27 kernel from kernel.org in Hardy cuz I don't want to give up my KDE 3.5.10 yet. To avert the need to manually recompile the drivers I installed DKMS which recompiles drivers upon kernel updates,madwifi, virtualbox, etc., automatically. I have the dkms.conf file for madwifi_hal and it works great. Just a thought. If anyone wants, I can post the dkms conf and commands to add, build, etc. Also I use scripts to reset networking, set link speed, etc. after resume from suspend.
Regards,
Ray
Ubuntu Hardy 8.0.4.1- 2.6.27.5
Windows Vista and XP via VirtualBox :)

---

### Post by dantakeoff on 2008-11-20
when my wireless disappeared after updating, i just installed ndiswrapper and the relevent xp driver, hey presto...no more running the madwifi patch.:)

---

