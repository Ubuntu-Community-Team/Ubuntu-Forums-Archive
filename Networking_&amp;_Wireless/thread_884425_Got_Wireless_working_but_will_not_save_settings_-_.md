---
title: "Got Wireless working but will not save settings - Lose on reboot"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by zachoeser on 2008-08-09
I finally got my wireless working - thanks to everyone who helped out....howerver
 after i run the sudo modprobe -ndiswrapper and everthing works good

then i reboot

and i have to re do that entire section of steps over again... is there anyway to save this so i dont have to keep retyping that whole 
sudo modprobe ndiswrapper
sudo modprobe -ndiswarpper 

every time i want to use wireless

---

### Post by prshah on 2008-08-09
> **zachoeser said:**
> 
and i have to re do that entire section of steps over again... is there anyway to save this so i dont have to keep retyping that whole 


1) You can add the word ```
ndiswrapper
``` at the end of your "/etc/modules" file

== OR ==

2) you can add the phrase ```
modprobe ndiswrapper
``` at the last but one line of your "/etc/rc.local"

Both are system protected files, you'll need sudo to edit either one. Do any one, don't do both! :)

---

