---
title: "Can't Activate Nvidia Driver"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by scythe01 on 2009-04-26
There are two options in the Hardware Drivers, 
*NVIDIA accelerated graphics driver (version 180) [recommended] and 
*NVIDIA accelerated graphics driver (version 173)
both doesn't activate. when I click the activate button, a window will appear saying "Downloading and installing driver" but it will not progress and will remain at 0% then there will be an error window

---

### Post by schou on 2009-04-26
Hi there,
I think it points to a dead link and somehow fails to time out..
Go directly to Nvidia's page instead and download a Linux driver: 
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
Remember to shut down X before installing the driver.

Kind regards,
Jakob

---

### Post by iKevin on 2009-04-26
> **scythe01 said:**
> There are two options in the Hardware Drivers, 
*NVIDIA accelerated graphics driver (version 180) [recommended] and 
*NVIDIA accelerated graphics driver (version 173)
both doesn't activate. when I click the activate button, a window will appear saying "Downloading and installing driver" but it will not progress and will remain at 0% then there will be an error window

Hi There

I just went through this and it took a very long time for the download to start.  I thought something was wrong but it eventually went through.  I am guessing the server is very busy.  I would just try again leter.

---

### Post by Sidewinder1 on 2009-04-26
ikevin is probably correct. Since Jaunty came out a few days ago, I have noticed a considerable slow-down in the transfer rates when downloading updates. The servers are obviously very busy. I know it doesn't help but just try to be patient or as suggested above by schou, go directly to NVIDIA's site. Being somewhat a noob myself, I would probably wait a little for the servers to clear; as the install would probably be easier and less prone to me 'screwin'' something up. :-)
Side

---

### Post by scythe01 on 2009-04-26
> **schou said:**
> Hi there,
I think it points to a dead link and somehow fails to time out..
Go directly to Nvidia's page instead and download a Linux driver: 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Remember to shut down X before installing the driver.

Kind regards,
Jakob

I already downloaded the driver from nvidia. It is a .run file.
How can I install it?
And what is X and how to shut it down?

Sorry, just a noob:(

---

### Post by 4Orbs on 2009-04-26
The same thing happened when I tried to activate the driver. No activity from the progress bar, then Jockey crashed error, then the progress bar disappeared. But I noticed my cpu light still flashing like something was happening. So I just left the Hardware Drivers Mgr open. After several minutes of waiting, I rebooted. The new driver had been installed correctly and all was good. Obviously the bad progress bar and Jockey crash didn't stop the driver installation.

---

### Post by BeBoBli on 2009-04-26
I had this problem as well... there really should be some feedback on the GUI that the download failed due to high bandwidth traffic.

---

### Post by ikisham on 2009-04-26
Scythe01, it's much useful to have in the panel the applets that show CPU activity, RAM (for someone that has few RAM), network activity etc. As 4Orbs said, it helps us if other things fail.
I'm not using ubuntu right now and have not used Jaunty, but usually all that must be done is right-click the panel and ask to add panel items, there you'll find the system monitor applet, if I remember well.

---

### Post by schou on 2009-04-26
> **scythe01 said:**
> Sorry, just a noob:(
Nothing wrong with that :-)
If you are uncomfortable with the manual installation process then maybe you should just try again and be patient - as iKevin did.

If this fails, you could try the manual approach.
There exist a ton of guides for this, e.g. [http://ubuntuguide.org/wiki/Ubuntu:Jaunty#NVidia_Driver]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#NVidia_Driver")

Kind regards,
Jakob

---

### Post by expatCM on 2009-04-26
I experienced exactly the same thing.

Solved it by getting out of bed early and installing the driver then.  It worked without issue but I did not see any suggestion that it was working until the process was completed.

---

### Post by ombzzz on 2009-04-26
Same problem here.

I tried to activate the 173 nvidia driver and had the following problemas:

i) message box says "downloading" but no progress activity 

ii) then "Jockey" crashes and driver is still not activated.

Update:

I tried again and now the driver seems activated. Will reboot the PC and see if it is true.

---

### Post by philinux on 2009-04-26
If anyone manually installs then following a kernel update the driver will have to be manually installed again unlike via synaptic.

To install the 180 driver open synaptic then search nvidia. Mark the 
nvidia-glx-180 for installation.

---

### Post by Vunutus on 2009-04-26
Download the driver from NVIDIA's site and install it directly. I never get the drivers to work unless I do a manual install.

To install the driver, you need to follow these steps:

Switch to a non-graphical terminal by pressing "Ctrl+Alt+F3". You should be at a text login screen. Either log in as root (easier) or as your regular user. If you run as your regular user you'll need to prepend "sudo" to these commands.

-Type "/ect/init.d/gdm stop"
-Use "cd" to change to the directory where you downloaded the driver. For example, if it's on your desktop then "cd /home/youruser/Desktop"
-Type "sh NVIDIA_driver_name_here"
-Follow the instructions it presents, I'm pretty sure all the default options will work correctly. It will probably say it can't find kernel interfaces and such and ask to build its own, accept.
-When it finishes you should probably just restart, but if you want to bring your system up without restarting you can probably type "/etc/init.d/gdm start" then hit "Ctrl+Alt+F7".

---

### Post by scythe01 on 2009-04-26
> **Vunutus said:**
> Download the driver from NVIDIA's site and install it directly. I never get the drivers to work unless I do a manual install.

To install the driver, you need to follow these steps:

Switch to a non-graphical terminal by pressing "Ctrl+Alt+F3". You should be at a text login screen. Either log in as root (easier) or as your regular user. If you run as your regular user you'll need to prepend "sudo" to these commands.

-Type "/ect/init.d/gdm stop"
-Use "cd" to change to the directory where you downloaded the driver. For example, if it's on your desktop then "cd /home/youruser/Desktop"
-Type "sh NVIDIA_driver_name_here"
-Follow the instructions it presents, I'm pretty sure all the default options will work correctly. It will probably say it can't find kernel interfaces and such and ask to build its own, accept.
-When it finishes you should probably just restart, but if you want to bring your system up without restarting you can probably type "/etc/init.d/gdm start" then hit "Ctrl+Alt+F7".

I did those and it seems my video card is working now but the display of my screen is still not as good as when I'm still using windows. And it is being detected as a CRT although it is a LCD monitor

---

### Post by JGSD on 2009-04-27
I tried activating the nvidia 180 driver, but the progress bar was stuck on 0% for ages, and I pressed cancel. It wouldn't cancel, so I just rebooted.

Then I tried again. The progress bar was still stick on 0% for ages, so I just left it. After a while, I got an error about Jockey crashing, and the progress bar was gone. I rebooted after this, but the driver was still not installed.

For the 3rd time, I tried to activate the nvidia 180 driver. I left it to itself and it seemed as though it was going to be stuck on 0% forever again. Then, all of a sudden, a dialog box came up saying that I had to restart to use the driver.

I did... and now it's working! I'm getting 2560x1600 on my 30" monitor, and all of the funky desktop effects are working :) :) :)

I can't really say what I did to get it working, though. It's just a matter of persistence, I guess!

---

