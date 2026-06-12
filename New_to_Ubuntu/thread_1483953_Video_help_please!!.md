---
title: "Video help please!!"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by recycledhippy on 2010-05-15
Hello all! upgraded to Ubuntu 10.04 recently and have been having some video issues ever since. It's been slow, choppy, low quality. I've tried different players, like vlc, Mplayer, and I get the same results. My graphic card is a ATI Radeon 9250. I think it my be driver issue,but not sure. Can someone point me in the right direction to find what driver I am using now, and what driver should I be using for the best results and how to get it? Thanks in advance.

Jason

---

### Post by 4Orbs on 2010-05-15
System>> Administration>> Hardware Drivers and select to activate the recommended driver (if there is one available for your card). You might want to run your system Update Manager and install updates before doing the driver.

---

### Post by recycledhippy on 2010-05-15
Hardware Driver brings up my onboard Nvidia graphics which I'm not using. I cant disable in my bios either. It doesn't seem to see my ATI but it's working right now.

---

### Post by cascade9 on 2010-05-15
As far as UI know, there are no ATI provided linux drivers for the 9250. So System-> Administration-> Hardware Drivers wont give you the option. 

The 9250 will be using the open source driver.

---

### Post by recycledhippy on 2010-05-15
I still could use some help on this. Is there a better driver to use over another?

---

### Post by 4Orbs on 2010-05-15
Well, I was kinda watching the thread for more replies but nothing new yet. So here goes. Since cascade9 says there are no Linux drivers available for your ati card, and I believe him/her, the only advice I can offer is to go to your Preferences>> Appearance menu, click on the Effects tab and make sure the desktop effects are turned off (I think they will already be off because you are using the Nouveau open source driver now). If they were on and you turn them off you should get smooth video playback. Another thing you might try, if you're using VLC media player is to go into those preferences and turn of interlacing. Sorry I can't be more helpful.

You also might want to go over to the Multimedia and Video section of these forums and run through the Comprehensive Multimedia and Video how-to sticky thread to be sure all your media stuff is in order.

---

