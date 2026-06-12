---
title: "temp sensors in panel"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by albert s on 2010-05-01
hi, just had to do a total install of 10.04, and now Ive lost my temp sensors from my panel.
they are not in the list after right clicking either, though I am pretty sure I have them.
thanks,

---

### Post by cairnzi on 2010-05-01
just a rough guess as i dont use 10.04 but try " apt-get install lmsensors"
it may reboot them.

---

### Post by albert s on 2010-05-01
thanks, but as I said, Im pretty sure I have them  

#
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


but they just arent showing up in my add to panel list.......

---

### Post by BrokeMahPC on 2010-05-01
You have to reinstall it and reconfigure it after an Ubuntu install.

Check you have lm-sensors installed in synaptic package manager, then:
```
sudo sensors-detect
```-Answer YES to all YES/no questions.
-At the end of sensors-detect, a list of  modules that needs to be loaded will displayed. 
-Type "yes" to have  sensors-detect insert those modules into /etc/modules, or edit  /etc/modules yourself.
-Next,  run 
```
sudo /etc/init.d/module-init-tools restart
```This will read the  changes you made to /etc/modules, and insert the new modules  into the kernel. (If it does not work reboot - the modules will be loaded at startup)

Open a terminal and run:
```
sensors
```should give you a voltage, temperature, fanspeed output as here:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
(All this info is in this how to)

For the Panel:
Check you have sensors-applet installed in synaptic, with a reinstall it may not be there.
Right click the panel and choose Add to Panel... it's listed as Hardware Sensors Monitor.

Graphics Temperature
If you use the ATI fglrx driver you can also get the GPU temperature by:
```
sudo aticonfig --odgt
```

---

### Post by albert s on 2010-05-01
thank you [BrokeMahPC]("http://ubuntuforums.org/member.php?u=974676") 
sorted now, :D
you are a  :KS

---

