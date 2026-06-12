---
title: "Problems with Dual Boot windows xp ati drivers"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by drewski24 on 2011-04-14
So i wanted to give ubuntu a try so i borrowed a friends live cd, version 9.10. using gparted i shrunk my windows xp partition and installed 9.10. Then once it was installed I upgraded to version 10.4. 

After the entire installation was complete i rebooted my computer and low and behold I have a problems. Some how my ati graphics drivers had been uninstalled, and it was not operational in windows xp. I went and downloaded and reinstalled the correct drivers for my card, ATI Mobility RADEON HD 3650. Then I restarted my computer and low and behold none of the drivers are installed. 

I really don't want to uninstall ubuntu, but i need a working graphics cad when i boot up in windows. 

If anyone could help me fix this issue it would be greatly appreciated.

---

### Post by coffeecat on 2011-04-14
Installing Ubuntu on another partition would not affect a Windows video driver, so uninstalling it (yes, I know you don't want to) wouldn't help.

This sounds like a Windows issue that has cropped up coincidentally with your installing Ubuntu. The fact that you have tried to re-install the driver and it is still not there is very strange, and does point to a Windows problem. I'd suggest looking for a registry corruption, or have you tried going back to an earlier restore point? Also, do a comprehensive malware scan.

---

### Post by drewski24 on 2011-04-14
Ya i don't know what is going on. I tried what you said, and once I got the graphics drivers were installed i did a couple of tests. First I just booted into windows xp a couple of times to if the drivers would not get un-installed, and this showed that when just booting into windows, the drivers were not deleted. 

However i ran into problems in my next test. I then with the graphics drivers working booted into Ubuntu 10.4 and everything worked fine. However when i went and booted back into windows the graphics drivers were gone again. 

This is really puzzling me and I'm beginning to wonder if something is going on during the Ubuntu boot up that disables or deletes the graphics drivers.

---

### Post by coffeecat on 2011-04-15
OK, I follow you. When you say the graphics drivers were deleted, do you mean that you were not getting the correct resolution from the graphics card when booting into Windows? That is not necessarily the same as the driver being deleted. Ubuntu would not selectively delete files from another partition, especially if it hasn't been mounted, nor can it affect registry settings.

What might be going on here is that hardware can be left in an inconsistent state when rebooting from one operating system to another. This is sometimes seen with wireless cards not working on a reboot and can happen going from Windows > Linux as well as Linux > Windows.

Try this. Boot into Windows and ensure that the graphics are working correctly. Now reboot into Ubuntu. Now go back to Windows but do not do a warm reboot. Shut down and wait a few moments. No do a cold boot into Windows. What happens?

---

### Post by mastablasta on 2011-04-15
also in additona to what was said above how did you install Ubuntu? via Wubi?
 
and when you upgraded from 9.10 to 10.04 did you first remove linux ATI drivers for 9.10 and then upgrade and then install new drivers?

---

### Post by Mark Phelps on 2011-04-15
Remember seeing some similar threads in the past, but in those situations, the folks had PCs that had both onboard video (usually Intel) and an add-on ATI card.  The problem was that they were unable to disable the onboard video -- and while that was not a problem in Windows, it was a problem in Ubuntu.  They would install the ATI drivers, reboot into Windows (OK), come back into Ubuntu -- and the ATI drivers were gone.

We were unable to solve their problem because they were unable to disable the onboard video.

---

### Post by drewski24 on 2011-04-15
@coffee cat

 I tried the method you described and got the following results. 

When i did the cold boot into windows, I got a pop up message from ATI that said no graphics driers were installed for this device, and to install the proper drivers. the graphics drivers were not active at that time. however when i went to reinstall the drivers, all the files were still there because i was asked if i wanted to overwrite the previous installation. 

So i think something is going on when I boot into windows where the correct drivers are not being run and or recognized. 

@ mark phelps

I have a lenovo t500 which came with the ATI Mobility RADEON HD 3650 graphics card. I do not know how to check if I have on board video for this machine. 



Overall I don't think this is a game breaker, but it is quite inconvenient, and can't be good for the machine.

---

### Post by drewski24 on 2011-04-15
@masta blaster 

I first defragged my c drive in windows xp. 

then I used gparted on the 9.10 live CD to shrink my windows partition. 

Then I installed Ubuntu 9.10 from the live CD. 

Once that was complete i right away updated the to 10.4 

Then when I booted back into windows to see if it was still working properly this issue cropped up. 


I never actively installed or removed any drivers during the Ubuntu install process.

---

### Post by Raiyan on 2011-04-15
Can you try installing a new version of Ubuntu. I am going to recommend you remove the version of Ubuntu that you currently have and get Ubuntu 10.10.

---

### Post by drewski24 on 2011-04-16
I uninstalled 10.4 and installed 10.10 and I'm still having the same problem.

---

### Post by drewski24 on 2011-04-19
OK interesting development. I had the drivers installed and working properly in windows, rebooted into Ubuntu 10.10 and my laptop, and my battery ran out while using my computer. when i rebooted into windows the drivers were still there. this is really starting to puzzle me.

---

