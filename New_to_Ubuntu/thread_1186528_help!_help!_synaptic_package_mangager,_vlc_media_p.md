---
title: "help! help! synaptic package mangager, vlc media player and avant window problems"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-06-13
first off let tell you guys that Im really really new to unbuntu Ive had it for two days now.

****here are the problems Ive ran into

1))

synaptic packager gives me this message when I open it 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

last I used it I was trying reinstall awm to see if thatd help remove it but my notebook shut down because of low battery power.





2)) I installed vlc media player with synaptic and I don't see it anywhere






3))I can't uninstall advant windows manager!!! x_x

I uninstalled all the check boxes with synaptic but it wouldnt go away



and again Im very nubish so type in lamer terms and be very directive, heh.
if some brave soul could aim me at seuxnoose and help get used to linux or better yet help me with theses problems it would be greatly appreciated, sooo much :3

thank you

---

### Post by FishyFantasy on 2009-06-13
I'm new to Ubuntu too. But I hope I can help you. 

1. Do the command from the message. You can find terminal in Application > Accessories > Terminal
And type in:
```
 sudo dpkg --configure -a
```

2. Make sure you install the right packages? You can find VLC Media Player in Applications > Sound and Video 

3. You mean Avant Windows Manager? Right click on the software you want to un-install and choose "Mark for Removal" or "Mark for complete removal" to remove all configuration files. 


Hope that helps. 



Bad english :X

---

### Post by overdrank on 2009-06-13
Hi and welcome,
You can use the terminal and enter the command given in the error message.
```
sudo dpkg --configure -a
``` The terminal is located under applications, accessories.
VLC should be located under applications, sound and video. If it is not there you may have to right click on the applications and choose to edit and add then.
You may also try the command in the terminal to remove avant ```
sudo apt-get remove avant-window-navigator
```
then
```
sudo apt-get autoclean
```
Edit to slow :)

---

### Post by joyneo04 on 2009-06-13
Hi vlc comes under application>sound & videos> vlc...now how u have have checked that vlc is installed properly...

---

### Post by doleenovodno on 2009-06-13
hi, i am also very new to ubuntu, and i am having problems with the update manager as well as add/remove applications program. every time i go to install something, namely a gameboy advance emulator and limewire or frostwire, it will begin downloading the packages or whatever and then freeze. i dont know how to force quit it and the only way to stop and begin again is to restart the system. i am dual-booting Intrepid Ibex on a macbook.

---

### Post by joyneo04 on 2009-06-13
let me check out in my lappy practically...

---

