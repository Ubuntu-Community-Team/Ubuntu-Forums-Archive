---
title: "Grub2 Boot Resolution Problem"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by doninsa on 2011-02-13
Runing Lucid Lynx with Grub2 boot loader.  I used Startup Manager to set boot menu resolution from 800X600 to 1600X1200 now the system doesn't recognize my monitor and I can't get the boot menu to come up.  

I can get to the recovery console and I've tried everything there but nothing works except going to the command prompt.  From the command prompt I can login but can't run gedit or terminal. I need some way to reset the boot resolution to 800x600.

I understand that update-grub needs to be run after any changes and I suspect the setting that needs to be changed is in 00_header.  

Any help would be appreciated.

Don

---

### Post by JRV on 2011-02-13
Open a terminal, run the command:

    sudo gedit /etc/default/grub

change the line that says: 

  #GRUB_GFXMODE=640x480

to:

  GRUB_GFXMODE=800x600

then:

  sudo update-grub

---

### Post by doninsa on 2011-02-13
I can't get terminal to run.

---

### Post by JRV on 2011-02-13
At the command prompt type:

  sudo nano /etc/default/grub

Make the edit mentioned above, then update-grub.


Nano is the text based editor.

---

### Post by Hippytaff on 2011-02-13
or CTRL+ALT+F1 if the above suggestion doesn't work. though instead of```
gksudo gedit /etc/default/grub
``` you will need to use ```
sudo nano /etc/default/grub
```failing that you can edit boot into rescue/recovery mode and do it that way

---

### Post by rburkartjo on 2011-02-13
don you should be able to access the terminal by using ctrl+alt+t

---

### Post by doninsa on 2011-02-13
> **rburkartjo said:**
> don you should be able to access the terminal by using ctrl+alt+t

I was able to get terminal up and running by using my old Unbuntu 8.10 CD.  My drive won't read my Ubuntu 10.4 CD.  I was then able to get Terminal running and edit grub.cfg but that didn't help. Not sure where to go from here.  Nothing will run when I boot from the hard drive. Ctrl-Alt F1 doesn't work and neither does holding the shift key down during startup. Tried Ctrl-Alt T from the command prompt and that didn't work either. Dang!      

From recovery console here is what I'm getting when I try to run in low graphics mode.  
"Ubunu is running in low-graphics mode
   Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.
   - Run Ubuntu in low-graphics mode for just one session
   - Reconfigure graphics
   - Troubleshoot the error
   - Restart X "
None of the above choices work.

---

### Post by Quackers on 2011-02-13
Why did you choose 1600x1200 resolution? Is that resolution supported by your monitor? The best resolution to choose is the native resolution of the monitor.
I would imagine (though am not 100% sure) that the Grub Customizer will have made a change to your /etc/grub/default file - probably by adding the line
```
GRUB_GFXPAYLOAD_LINUX=1600x1200
```
That line needs to be changed to the native resolution of your monitor - I would say.
You will need to boot the live cd and select "try ubuntu" then chroot into your actual installation, then edit that line in the above file, then save the file, quit the file and then run sudo update-grub.

ps How did you install 10-04 if the cd doesn't work?

---

### Post by doninsa on 2011-02-13
> **Quackers said:**
> Why did you choose 1600x1200 resolution? Is that resolution supported by your monitor? The best resolution to choose is the native resolution of the monitor.
I would imagine (though am not 100% sure) that the Grub Customizer will have made a change to your /etc/grub/default file - probably by adding the line
```
GRUB_GFXPAYLOAD_LINUX=1600x1200
```
That line needs to be changed to the native resolution of your monitor - I would say.
You will need to boot the live cd and select "try ubuntu" then chroot into your actual installation, then edit that line in the above file, then save the file, quit the file and then run sudo update-grub.

ps How did you install 10-04 if the cd doesn't work?

I installed 8.10 then upgraded to 10.04. 

The symptoms have changed some since the onset of this problem.  The Grub boot menu now comes up but no matter what "kernel?" I select it always fails, leaving me back at the Recovery Console. I can start Windows XP but not Ubuntu.

I missed the question about why I selected 1600x1200 resolution.  In Startup Manager it was one of the choices offered, At the time I didn't think much about it.

---

### Post by Quackers on 2011-02-13
oops wrong forum - please ignore.

---

### Post by Quackers on 2011-02-13
I'm not sure you will be able to chroot into your existing system from a 8.10 live cd. You may need a more modern live cd/usb. Maybe somebody else could confirm or deny that?

---

### Post by doninsa on 2011-02-13
> **JRV said:**
> At the command prompt type:

  sudo nano /etc/default/grub

Make the edit mentioned above, then update-grub.


Nano is the text based editor.

Hey this worked!  Nano started right up and I was able to edit grub.  But, the resolution was already set to 640x480.  I changed it to 800x600 just to see if I could and after runing update-grub I tried to boot into Ubuntu.  Sorry to say it failed and I'm again left at the Recovery Console.  I changed it back to 640x480 and ran update-grub again. Any suggestions on where to look now?  I'm pretty much out of ideas.

---

### Post by doninsa on 2011-02-13
> **doninsa said:**
> Hey this worked!  Nano started right up and I was able to edit grub.  But, the resolution was already set to 640x480.  I changed it to 800x600 just to see if I could and after runing update-grub I tried to boot into Ubuntu.  Sorry to say it failed and I'm again left at the Recovery Console.  I changed it back to 640x480 and ran update-grub again. Any suggestions on where to look now?  I'm pretty much out of ideas.

Well, I decided that the fastest way to recovery was a complete reinstall.  The reinstall is in progress as I type this email.  I hate to lose all the work and time spent setting up the Ubuntu 10.04 but that's the way it goes.  Thanks to all those that tried to help.  This forum is one of the things that keeps me coming back to Ubuntu.

Regards,
Don

---

