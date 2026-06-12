---
title: "N-draft speed with iwl4965?"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by geraner on 2008-03-15
I have an Intel® Wireless WiFi Link 4965AGN in my notebook.
Network card is running fine with driver iwl4965 directly out of Ubuntu.
But when I check the connection information, there is written "Speed: 54 Mb/s".
My router is adjusted to use both N-draft and g .
How to get this higher speed under Ubuntu to work?

Regards
Geraner

---

### Post by mike984 on 2008-03-26
Does anyone know if the iwl4965 driver on Linux can even go faster than 54mbps?

I have looked everywhere.  I can get speeds of around 300mbps in Windows but Ubuntu holds steady at 54mbps.

Thanks

---

### Post by mike984 on 2008-03-28
Anybody?  I've googled and looked everywhere I can think of...

---

### Post by ZeroHimself on 2008-04-10
it seems that the linux driver module(for any wireless card?) cannot do anything above wireless g... :( .. however i read in another forum that people have achieved 100+ mbps by using the ndiswrapper with the windows  version of the driver, however they could not set a certain setting to obtain 300mbps....

link to guide about ndiswrapper with iwl4965
[http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794)

semi-sucess with ndiswrapper and speeds above 56 mbps:
[http://ubuntuforums.org/showthread.php?t=749351](http://ubuntuforums.org/showthread.php?t=749351)

---

