---
title: "Uninstallation help"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by monpolo on 2009-03-02
Alright, I started with a laptop with Vista and installed Ubuntu 8.10 onto my external hard drive. However I didn't plan too far ahead and I didn't take into account that my external requires a power cord and is therefore inconvenient to carry around. Whenever I don't have my external plugged in I get grub error 21 on booting up.

So, I installed Intrepid Ibex on my thumb drive and can successfully boot into it... Now I would like to uninstall Ubuntu from my external and use it for purely media storage. 

Can anyone give me instructions on how to remove linux from my external and is there any way I can guarantee any drivers or programs I install to my thumb drive linux will be saved on my computer's internal hard drive so I don't have to drag around my external? 

P.S. I am keeping Vista for games and Visual Studio which is obviously installed on my internal.

Sorry if this isn't a very clear format for my question, any tips for future posts would be appreciated.

---

### Post by halitech on 2009-03-02
you can restore the windows boot loader by using the windows install cd or you can use supergrub to repair the bootloader. 

not sure what you mean by this:
> Can anyone give me instructions on how to remove linux from my external and is there any way I can guarantee any drivers or programs I install to my thumb drive linux will be saved on my computer's internal hard drive so I don't have to drag around my external?

---

### Post by mkvnmtr on 2009-03-02
You really don't uninstall. With a tool like gparted you reformat the drive. You can get gparted in the repositories. When you download it youfind it under partition editor. If you dont wish to donload it to your Ubuntu system it is on the ubuntu live disk. Boot from the disk look for partition editor and with your external you should be able to repartition.

---

