---
title: "Ubuntu 8.10:How to I enable Nvidia 180 Driver option in Hardware Drivers?"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-03-12
I have the nividia 180 driver files (The 3 proprietry .deb files) installed but when I go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS to select NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 180, but I only have the option of enabling versions 173 or 177. 

How do I get the 180 Driver option to appear on the HARDWARE DRIVERS Section? Can anybody help me on this one?

**PS:** Thanks to Paqman's advice I realised I was running before I could crawl and went back to 8.10, your right mate best to wait for Ubuntu 9.04 to be released instead for running alpha's. Ta ;)

---

### Post by Nightstrike2009 on 2009-03-12
Bump! Can anyone help this is driving me nuts?

---

### Post by crjackson on 2009-03-12
Try this:

"To see nvidia 180 driver in hardware drivers, install nvidia-180-modaliases.

To do this you can type in terminal sudo apt-get install nvidia-180-modaliases . Or you can use synaptic."

---

### Post by Nightstrike2009 on 2009-03-12
Thanks crjackson,

I am using a windows connected internet PC, though the Linux one (Mine) doesn't have the internet so I cant use linux to download packages. I maybe able to find a website with the file on it (with the Windows one & copy it via USB drive to mine), like this one: [http://packages.ubuntu.com/intrepid-updates/nvidia-180-modaliases]("http://packages.ubuntu.com/intrepid-updates/nvidia-180-modaliases") 

I take it [COLOR="SeaGreen"]nvidia-180-modaliases[/COLOR] is the file iam missing though? I'll try this is soon as possible, hope this works for me, if it does then thanks crjackson. In fact thanks for the advice anyhow, cheers mate. ;)

---

### Post by Nightstrike2009 on 2009-03-13
Thanks Crjackson this does indeed work now the option has been added to hardware drivers (after restarting ubuntu 8.10) and my 3D driver & desktop effects are working now. Cheers mate ;)

---

### Post by Nightstrike2009 on 2009-03-13
For the other newbies out there these files are required for nvidia 180 driver in ubuntu 8.10:

[COLOR="Green"]dkms_2.0.20.4-0ubuntu2_all
nvidia-180-kernel-source_180.11-0ubuntu1~intrepid1_i386
nvidia-glx-180_180.11-0ubuntu1~intrepid1_i386
nvidia-settings_177.78-0ubuntu2.1_i386[/COLOR]

The one below is the modaliases one; 
[COLOR="Green"]nvidia-180-modaliases_180.11-0ubuntu1~intrepid1_i386.deb[/COLOR]

And these for compizconfig:

[COLOR="Green"]compizconfig-settings-manager_0.7.8-0ubuntu3_all
python-compizconfig_0.7.8-0ubuntu1_i386[/COLOR]

Hope this helps ;)

---

### Post by philinux on 2009-03-13
Interestingly, installing 180 and it's modalias removes the 177 driver.

I've rebooted and now under nvidia settings it correctly show the 180 driver in use but in jockey, hardware drivers, it still shows the 173 and 177 driver with non in use. Bug I think maybe.

---

### Post by Nightstrike2009 on 2009-03-13
Thanks for info Phillinux thats weird as we are both from Lancashire, UK, must be a few Northern Linux users out there after all. LOL 

I was testing Jaunty (32bit) and it seems quite stable, the bluetooth applet in the jaunty test versions seems better and easier to use in Jaunty than Intrepid. Is there any way to update intrepid with this, think its bluetooth is 4.32 or something like that?

UPDATE: Well done Phillinux on the post below thats one less thing to bother us in the final release, hopefully :)

---

### Post by philinux on 2009-03-13
> **Nightstrike2009 said:**
> Thanks for info Phillinux thats weird as we are both from Lancashire, UK, must be a few Northern Linux users out there after all. LOL

Quite a lot of UK users :P.

Off to launchpad with a bug report.

---

### Post by crjackson on 2009-03-13
> **Nightstrike2009 said:**
> Thanks Crjackson this does indeed work now the option has been added to hardware drivers (after restarting ubuntu 8.10) and my 3D driver & desktop effects are working now. Cheers mate ;)

You're welcome. Glad it worked for you. I see Phil has found a bug to report...

---

### Post by Ian Clark on 2009-04-19
> **philinux said:**
> Interestingly, installing 180 and it's modalias removes the 177 driver.

I've rebooted and now under nvidia settings it correctly show the 180 driver in use but in jockey, hardware drivers, it still shows the 173 and 177 driver with non in use. Bug I think maybe.

Please please confirm [this]("https://bugs.launchpad.net/ubuntu/+bug/358470") bug.  Ubuntu devs need to know about it!  All my sound is borked and I don't know how to undo the damage from the 180 modaliases upgrade.  Thanks!

---

