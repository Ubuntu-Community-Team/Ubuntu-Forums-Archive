---
title: "switching drivers (restricted vs. ndiswrapper)"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by AhJah on 2008-02-12
Hi all

I use my wireless connection at two different places. I'm able to connect to each network but for one of them I need to use Intel 3945 restricted driver and for the other one I need to use ndiswrapper.

I have realized that I can just enable or disable the restricted driver without need for touching the ndiswrapper settings.

However I can only do that by the restricted driver manager that requires a reboot for every change.

Is there any way to change the configuration on the fly, without need for a reboot?

How can I find out which configuration files are involved in the change and how can I force a reload? I can use the terminal, I can even create an appropriate script if it is needed.
But I don't know which files are involved.

I use Feisty.

Many thanks
Leo

---

### Post by aeiah on 2008-02-12
you can load and unload modules on the fly via the terminal.

sudo modprobe -r NameOfModule
to remove one module

sudo modprobe -v NameOfOtherModule
to insert the other

use lsmod to determine the names of either of your modules. when inserting them, you may need to specify a path, but im not sure because im not sure if there's a default path that they reside in. it should be pretty simple to make a script or two for this, assign it to buttons on your panel etc

---

### Post by AhJah on 2008-02-12
Thanks aeyah, unfortunately this don't solve my problem. 

When I unload the module ipw3945 I completely lose wireless networking (infact there is no Wireless network in the Network Manager menu). Maybe it happens because unloading ipw3945 also unloads ieee80211 and ieee80211_crypt, however I'm not sure about that. 

I have tried also to load ieee80211 (which automatically loads ieee80211_crypt) after unloading ipw3945 but I didn't succeed, I still have no wireless networking.

I have also tried a different approach: with restricted driver disabled I do have wireless networking, so I tried to load ipw3945. This way I get an error saying  " ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection".

So I think I need to find out how to make this connection available to ipw3945 module before loading it. 

Of course the configuration without restricted driver works smoothly at the other place as per my initial post.

Thanks again for every further advice.
Leo

---

