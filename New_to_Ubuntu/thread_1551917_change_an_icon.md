---
title: "change an icon"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by iceman30ad on 2010-08-12
ok i need some one to save my *** on this
installed ubuntu on my gf's computer fought with it to get the wireless working and went through a bunch of network managers she liked the look of wicd task bar icon and wants that back but shes needing network-manager to keep it running any help would be appreciated

stats 
hp dv7 series
running Ubuntu 10.4 
needing network-manager taskbar icon to look like the task bar icon from wicd 
using ambiance theme

in trouble if i dont get an answer soon

---

### Post by bodhi.zazen on 2010-08-12
Can you not right click on the icon and select properties -> set an icon ?

---

### Post by iceman30ad on 2010-08-13
sorry i mean notification area and she wants the bar to report the active signal strength 

and she under stands that i might not be able to get this done but i want to learn how if i can any way

---

### Post by friv_livs on 2010-08-13
If wicd is still installed:

"gksu nautilus" in terminal

search for all images related to 'wicd' in the filesystem,  see what filenames are used for the connectivity taskbar display, and copy those out to Desktop/"wicd_images_directories".

Then repeat above procedure, this time searching for 'network-manager' and using Desktop/"network-manager_images_directories".

Then rename the images in Desktop/"wicd_images_directories" to the equivalent names in Desktop/"network-manager_images_directories".

Finally copy the images in Desktop/"wicd_images_directories" to the corresponding directories in the filesystem for network-manager.

If this fails, just copy the Desktop/"network-manager_images_directories" back to original locations.

hope this helps.

---

### Post by iceman30ad on 2010-08-14
ok now i feel real stupid why didn't i think of that ....
such an easy  way and it completely zipped by me till you said it ill try it in the morning and give you a report

---

### Post by iceman30ad on 2010-08-15
women did it then had to change it back to the default icon  

thanks again

---

