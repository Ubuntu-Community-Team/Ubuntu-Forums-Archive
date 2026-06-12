---
title: "Uninstalling lucid lynx and reinstalling studio 10.04"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by johnharris on 2010-05-25
Hi guys,

I'm absolutely new to ubuntu, I installed lucid on my dell xps 1330 with vista as a dual boot a few days ago.  I now realize that I should have installed ubuntu studio 10.04 with the 64 bit architecture.  I found this thread [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) but since it is 4 years old I was wondering if there is a better way to do this i.e. leave a partition for ubuntu studio. 
I am using unetbootin from a flash drive to install, can I simply go back into windows and use unetbootin, choose ubuntu studio 64 bit and click reinstall?  so far everything i've dealt with in ubuntu ends up being far far easier than I would expect.
Thanks.

---

### Post by Ozymandias_117 on 2010-05-25
First question: Did you use Wubi to install it? Or is it a dual boot?

---

### Post by johnharris on 2010-05-25
no wubi, i didn't even know what wubi was till like yesterday. so i know, i know, linux noob.

---

### Post by Ozymandias_117 on 2010-05-25
Then you should be able to boot to the flash drive, and during the installation select manually partition (Something to that effect). All you need to do is tell it to use the current partition 10.04 is on as / and the current swap file as swap then install.

---

### Post by k3lt01 on 2010-05-25
1 point to clarify before we go anywhere 10.04 IS Lucid Lynx.

If you have Ubuntu 10.04 already installed you can install Ubuntu Studio's packages making your current install Ubuntu Studio without having to do anything else like download an iso image and burn it to a disk etc.

So, what I would do if I were you, and this assumes you still have Ubuntu installed, is go System > Administration > Synaptic Package Manager, typ in your password when prompted and that will open Synaptic. Now that Synaptic is open go to the Quick Search function and type in ubuntustudio, or copy and past that as is. It will take you to the Ubuntu Studio packages and you can select the ones you want to install. Now click Apply up the top and follow the instructions from there.

Edit: OR you could just use the command line and paste this command in
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
``` hit enter, follow the prompts and let it install for you.

---

### Post by johnharris on 2010-05-26
The synaptic update worked very well.  Thanks for the quick advice!

---

