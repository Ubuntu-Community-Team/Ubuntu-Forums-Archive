---
title: "Graphics problem recurred"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-10-15
Suddenly the size of the fonts and icons has gone bigger 
I am using 9.04
I faced the similar problem on 8.04 a few days back

What is the problem

---

### Post by vipulkelkar on 2009-10-15
I have a nvidia geforce 6150 card 
and nividia driver version 180 installed

---

### Post by Niko Johnson on 2009-10-15
you might have to check your resultion... what graphics card are you using... to quickly check your resolution just go to system >> administration >> display or maybe its prefences >> display.... eaither way play around with your choices and see if that works. it should do the trick if its not a driver problem. other wise there are a few more steps to installing and using a driver, but there not hard

---

### Post by Niko Johnson on 2009-10-15
then run this code as root then log out and back in to restart the settings and see how it works ```
 nvidia-xconfig 
```

---

### Post by vipulkelkar on 2009-10-15
When i go to pref->display
It says
-------------------------------------------------------------------------------------------------------------------------
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

yes   no
--------------------------------------------------------------------------------

It when i say yes..it opens the nvidia xserver settings

---

### Post by achase79 on 2009-10-15
open the terminal from applications -> accessories -> terminal and type 
```
sudo nvidia-xconfig;sudo nividia-settings
```
In settings set your resolution and save settings. (this should correctly update your /etc/Xll/xorg.conf file)

---

### Post by achase79 on 2009-10-15
BTW driver 180 is still slightly experimental and it by itself may be glitchy

---

### Post by vipulkelkar on 2009-10-15
i am not able to find where to change the reslolution
The resolution is set to 1024x768 as shown in the pref->display

---

### Post by Niko Johnson on 2009-10-15
try using the nvidia settings to change your resultion run this as root ```
 nvidia-settings 
```. if it gives you a pop up saying run some other command first then go ahead and do that then go back to the settings... change your resultion according to your monitor documentation and log out and back in and see how that works

---

### Post by vipulkelkar on 2009-10-15
so shall i go with 173 ??

---

### Post by Niko Johnson on 2009-10-15
its possable... just beacuse the 180 is newer doesnt mean its better... i got the 180 to work for me but every mechine is different.. just give it a try and see how it works out. its always good to keep your eyes open to new solutions

---

### Post by vipulkelkar on 2009-10-15
I was able to change my resolution and save it to the config file...
but i m not able to see the changes after reboot

Can u give me the command to set the x config file to default..as it is when we install the OS

---

