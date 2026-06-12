---
title: "Ubuntu install problem"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by bguy on 2009-05-26
Hi all,
I have a video card that doesn't seem to be compatible with ubuntu.  Whenever i try to enable the 180 nvidia driver from within ubuntu it craps out on the reboot and in order to run ubuntu again I have to reinstall the whole os.  When i reboot after enabling the driver i get forwarded to the command line i believe.  It says something about login I think. My graphics card is a quadra nvs 440 that is capable of supporting 4 monitors but i currently only have it set up to use 1.  Could any one lend a hand with this?  
THanks,
B

---

### Post by Didius Falco on 2009-05-26
> **bguy said:**
> Hi all,
I have a video card that doesn't seem to be compatible with ubuntu.  Whenever i try to enable the 180 nvidia driver from within ubuntu it craps out on the reboot and in order to run ubuntu again I have to reinstall the whole os.  When i reboot after enabling the driver i get forwarded to the command line i believe.  It says something about login I think. My graphics card is a quadra nvs 440 that is capable of supporting 4 monitors but i currently only have it set up to use 1.  Could any one lend a hand with this?  
THanks,
B

Hi,

I'm not very well versed in nVidia cards in Ubuntu, but I do know that there is an utility called **nvidia-settings** that should be installed and run to set up your card and display. I'm unsure if it is installed along with the driver, but you can check for it in **Applications/Administration/Synaptic Package Manager **by searching for it.

Have you done that?

Also, when you get the black screen and log in prompt, that's a way to recover your system without having to reinstall from scratch. 

I'd recommend installing and running **nvidia-settings** before you reboot.

Some searching in the forums should turn up more info on the subject from people that are actually using it. It'd also help if you told us what version of Ubuntu you are using.

I hope this helps...

Regards,

Didius

---

