---
title: "Information for drivers for NVIDIA 6600gt from terminal"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-03-07
01:00.0 VGA compatible controller [0300]: nVidia [[COLOR=blue][COLOR=blue ! important][FONT=inherit ! important][COLOR=blue ! important][FONT=inherit ! important]Corporation[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.tomshardware.com/forum/forum2.php?config=tomshardwareus.inc&cat=50&post=237416&page=1&p=1&sondage=0&owntopic=1&trash=0&trash_post=0&print=0&numreponse=0&quote_only=0&new=0&nojs=0#") NV43 [GeForce 6600 GT] [10de:00f1] (rev a2) 
	Kernel driver in use: nouveau 
	Kernel modules: nvidia-96, nouveau, nvidiafb 
  

So it looks like I'm using Nouveau driver but I have three drivers  loaded Nvidia 96, which I believe is the 96.43.19, nouveau (the one I  think it's using) and Is the nvidia fb mean it is a nvidia fbcon and is  that another driver or what? 
The point is I've been trying to test all the nvidia 6600gt drivers I  can find the 173 the 96 and I'm trying to put in 260.19.36  but I  haven't been able to get it in yet.and I believe that the nouveau  drivers was installed from [[COLOR=blue][COLOR=blue ! important][FONT=inherit ! important][COLOR=blue ! important][FONT=inherit ! important]Ubuntu[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.tomshardware.com/forum/forum2.php?config=tomshardwareus.inc&cat=50&post=237416&page=1&p=1&sondage=0&owntopic=1&trash=0&trash_post=0&print=0&numreponse=0&quote_only=0&new=0&nojs=0#")  10.10 when I put the 6600gt card in the computer. With all those three  drivers listed as kernel modules could or do I have a conflict. And the  reason I'm doing this is, the drivers that I have now are freezing the  system.

---

### Post by mrhhug on 2011-03-07
I go to the source for my drivers, especially graphics. Nvidia is linux friendly they have a script written to install the drivers.

[http://www.nvidia.com](http://www.nvidia.com)

last time installing my Nvidia drivers it was terminal based, meaning that you can run the installer even when gnome fails to start. I know the Nvidia website is running asp; lynx is hard to navigate on their site. Even though your asking for instructions from terminal, i would recommend that you download the drivers with a fully functional browser then transport them over to the computer stuck in terminal mode

---

### Post by grahammechanical on 2011-03-07
I have experienced conflicts between Nvidia drivers due to not deactivating the present driver before activating the next driver. I think that the configuration files get mixed up. A re-installation and format cleaned everything out and then when I activated the recommended driver enhanced effects worked fine. Before that dialogs boxes would lose their control buttons and not be moved across the screen.

Regards.

---

