---
title: "Problem with natulius!!"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by ravi_buz on 2010-10-19
For the past few days, when ever i start my system natulius is not starting...i have to start it up manually and after starting it i am unable to see the mini,max,close button on the top right corner. 

PS. i tried to change between gnome and Kde with out logging in and so wrote 2 script and used it for few days. this problem started after this..

Now i am not changing between these two so i want natulius to run properly when i start my system 

this script i used was 

#!/bin/bash

killall fusion-icon
killall gnome-panel
killall plasma-desktop
gnome-panel &
fusion-icon &


and 


#!/bin/bash

killall fusion-icon
killall gnome-panel
killall plasma-desktop
plasma-desktop &
fusion-icon &

---

