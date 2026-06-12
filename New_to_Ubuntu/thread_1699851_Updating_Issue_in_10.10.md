---
title: "Updating Issue in 10.10"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by pseudosmart on 2011-03-04
[SIZE=2]I had a problem with the display on my sony vaio laptop after installing 10.04, and after much digging I learned how to disable the nouveau driver and install the proprietary driver for my card (a GeForce 330M) as well as the application nvidia-settings to control the screen resolution. And everything worked great for a few weeks, until I installed the updates recommended by the Update Manager. Then everything was broken again, and I gave up and went back to Windows for a few months. [/SIZE]
   
  [SIZE=2]So now I’m trying again with 10.10, and of course it’s great, I love it. And it was much easier to fix the display issue for my graphics card as I learned how to do it last time. But this time when I installed the updates, the GUI wouldn’t even launch, and I didn’t know how to get it back from the command line. I tried sudo /etc/init.d/gdm start, but that didn’t work. So, I finally reinstalled 10.10, fixed the display issue, and then just uninstalled the Update Manager, and figured I would use the system without updating.[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2][FONT=&quot]I really love using Ubuntu, but I am very frustrated that simply updating my system seems to wreck everything. My questions are, just how bad is it to use Ubuntu without updating it? Does anyone know why this might be happening, or has anyone run into this issue before and know how to fix it? Any suggestions anyone can offer are greatly appreciated. (And please keep in mind that I’m completely new at using Linux). Thanks in advance for your help.[/FONT][/SIZE]

---

### Post by mikewhatever on 2011-03-04
Can you provide some details on how you 'fixed the display issue'.
Installing Nvidia drivers has been point and click in Ubuntu, which also takes care of the nouveau, and also installs nvidia-settings. However, do it manually, and you'll be required to reinstall the driver after every kernel update. I suspect that's what happens in your case.

---

### Post by pseudosmart on 2011-03-04
Thanks for the response. I tried using the point and click method to install the proprietary drivers at first, but it didn't work. So I installed nvidia-settings with 'sudo apt-get install nvidia-settings'. Then I downloaded the Nvidia Linux driver for my graphics card (GeForce 330M). But every time I tried to install it in the command line, it said that the nouveau driver was currently running and needed to be disabled. So the instructions I found online said to disable nouveau with [FONT=monospace]'[/FONT]sudo apt-get --purge remove xserver-xorg-video-nouveau'. Then I was able to install the Nvidia driver with no problem. Again, I'm very new at this, but could it be that the updates that are installing are looking for that nouveau driver? And if so, is there a way to install the updates without them trying to use the nouveau driver again? Thanks again for your help, I really appreciate it.

---

### Post by mikewhatever on 2011-03-04
No, I don't think the updates are looking for nouveau. Here's how it works: when you installed the downloaded proprietary driver manually, a kernel module was built, and now, that the kernel got updated, it needs another module. That simply means that you have to install reinstall the downloaded nvidia driver.
I am not quite sure why the point and click way didn't work. ... what exactly didn't?

---

### Post by pseudosmart on 2011-03-11
> **mikewhatever said:**
> No, I don't think the updates are looking for nouveau. Here's how it works: when you installed the downloaded proprietary driver manually, a kernel module was built, and now, that the kernel got updated, it needs another module. That simply means that you have to install reinstall the downloaded nvidia driver.
I am not quite sure why the point and click way didn't work. ... what exactly didn't?

Sorry for the delay in getting back to you. When I originally tried using the point and click method via Jockey, to Enable the nvidia 3-D Accelerated graphics, my screen got huge and there were several error messages. I'm not sure if my card just wasn't supported, or if I did something wrong. But long story short, I learned from another discussion thread that removing nouveau altogether probably wasn't the best way to go, but that blacklisting it was easier and made more sense I guess. And I had made some mistakes in fooling around with my user permissions, so I backed up my files and reinstalled and followed the instructions to create a text file called 'disable-nouveau.conf', which is simply:

blacklist nouveau
options nouveau modeset=0

And then used 'chown' to make root the user. Then I moved it to '/etc/modprobe.d/'. After I did that, I went to the command line with <ctrl-alt-F1> and stopped the xserver with 'sudo /etc/init.d/gdm stop', and installed the nvidia driver. Then I started the xserver back up with 'sudo /etc/init.d/gdm start', and my display was perfect.

And you were right about having to reinstall the nvidia driver after I updated. When I installed the updates and rebooted, the boot screen would hang and the GNOME desktop wouldn't load. But I had access to my command line again. So I just installed the nvidia driver again from the command line, and rebooted, and everything worked fine again, and the updates were successfully installed.

I apologize for taking so long to post a response, but thanks again for your help.

---

