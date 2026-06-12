---
title: "boot problem"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by jtclicker on 2009-04-10
Just tried to boot into ubuntu for the first time today and had a boot problem. I have 3 ubuntu kernels to choose from
8.04 kernel 2.6.24-17/16/14
The first two of these give a 'file not found press any key to continue' error and I can only boot into ubuntu using kernel 2.6.24-14 from October (I think).
Is this a grub error or something else? How would I go about problem solving this?

---

### Post by Tralce on 2009-04-10
Try running, from a terminal:
```
sudo update-grub
```

---

### Post by jtclicker on 2009-04-10
OK I get this

 ```
A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified.                       
What would you like to do about menu.lst?                            
                                                                      
      install the package maintainer's version                  
      keep the local version currently installed                     
         show the differences between the versions                      
          show a side-by-side difference between the versions           
         show a 3-way difference between available versions          
        do a 3-way merge between available versions (experimental)      
   start a new shell to examine the situation   
```

as I haven't a clue what I'm doing with this, what would you recomend?

---

### Post by drs305 on 2009-04-10
I can't remember if the script makes a backup so I usually copy the existing menu.lst then accept the new one (install the package maintainer's version). To make a copy of the current menu.lst, open another terminal window and:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

After updating, if you have any specialized listings at the bottom of the menu you can copy them to the new menu.lst. You can open both copies with:
```

gksudo gedit /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

---

### Post by Kevbert on 2009-04-10
Boot up the -14 kernel. It suggests that your updates/upgrades to the newer kernels may have been corrupted in some way. First try installing the package maintainer's grub and see what happens. If you still get the problem go back to the -14 kernel and try the following commands in terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```
Please post back any problems.

---

### Post by jtclicker on 2009-04-10
Thanks guys.
First I tried the codes from drs305 and this had the effect of deleting the -16 and -17 kernels from the grub menu and leaving me with -14 as the latest kernel going back to -10.

Then I tried the commands from kevbert but had 0 packages upgraded and rebooting didn't show me anything newer than -14

---

### Post by ranch hand on 2009-04-10
Have you looked in synaptic to see what is available there?

In the bottom left corner of the synaptic page click on Status.  Then at the top of that collumn click on Uninstalled.  Scroll down to linux on the list and see what you have there.

There could be a problem with your update manager.  Synaptic should have this stuff in it.  I find that it is a useful tool to find what you have installed and so forth.

I usually update using the update managers list but updating using the terminal as I like the added info that I get there along with reccomended and suggested packages.

---

### Post by Kevbert on 2009-04-10
Missed a line...the latest kernel for 8.04 is 2.6.24-23-generic. You want to do a 
```
sudo apt-get dist-upgrade
```
**BUT** before you accept the newer kernel make sure it's 2.6.24-23 (it will show the packages to be upgraded and give you the option to do this or not. If the kernel is anything else you want to go into System-Admin-Software Sources and select the Updates Tab and check that under Release Upgrade it shows Long Term Support Releases only (otherwise you'll update to 8.10).

---

### Post by jtclicker on 2009-04-10
> **Kevbert said:**
> Missed a line...the latest kernel for 8.04 is 2.6.24-23-generic. You want to do a 
```
sudo apt-get dist-upgrade
```
**BUT** before you accept the newer kernel make sure it's 2.6.24-23 (it will show the packages to be upgraded and give you the option to do this or not. If the kernel is anything else you want to go into System-Admin-Software Sources and select the Updates Tab and check that under Release Upgrade it shows Long Term Support Releases only (otherwise you'll update to 8.10).

Thanks I've just done that and I'm still not getting anything to upgrade. All my software sources seem to be ok

---

### Post by jtclicker on 2009-04-10
just to confirm, having done everything suggested I'm now running 8.10 with the 2.6.27-14 generic kernel.
I've looked in synaptic and the update manager seems to be installed. Looks like somehow I bumped up to 8.10 in all the problem solving, although terminal was always showing 0 installed!

---

