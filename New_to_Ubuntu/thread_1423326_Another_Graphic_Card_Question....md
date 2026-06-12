---
title: "Another Graphic Card Question..."
date: 2010-03-06
forum: New to Ubuntu
---

### Post by SecretFace on 2010-03-06
I have in my machine now a nvidia 7900 gtx...and am upgrading to nvidia 250 gts 1gb. I need to know what procedure to do in Linux? I know how to do this in windows xp.Do I deactivate the drivers for the old card in Ubuntu before I power down and remove? Not sure how to do this in Linux...I play my games on my other hard drive with windows xp and I know what needs to be done...just not familiar with how to do it in Linux...Please help. ;)

---

### Post by patchwork on 2010-03-06
EDIT:  I think this is a moot point because I believe they can use the same driver..


You should disable the old driver first ( though the installer will attempt to remove the old driver if it senses it). 
If you intend to use a driver not provided with ubuntu (such as the 195.30 or 190.53), download the driver now, and make it executable using:

```
 cd Downloads
sudo chmod +x <name of nvidia .run file> 
```Next, you must stop the X server 

```
sudo service gdm stop
```This will drop you to console.  Next, remove the nvidia module:

```
 sudo rmmod nvidia 
```Shutdown 

```
 sudo shutdown -h now 
```Replace your card, and restart.

If you are using a driver from ubuntu (through jockey) , select it from the restricted drivers window.  If you are installing from the downloaded nvidia file, stop the x server again (using sudo service gdm stop), login at the console prompt, cd to the Download location, and execute the .run file:

```
 ./<name of .run file>
```after installation is complete, run the command

```
 lsmod | grep nvidia 
```If nvidia is not displayed, you will need to hotplug it into the kernel using 

```
 sudo modprobe nvidia
```After the modprobe, lsmod | grep nvidia should show the module as being loaded.

Restart x using 
```
 startx 
```

---

### Post by kouter on 2010-03-06
you could always just send me the card, I'll figure out how to work it =P

if you are using the proprietary nvidia drivers, it should be a seamless transition. I could be wrong though.

---

### Post by SecretFace on 2010-03-06
> **patchwork said:**
> EDIT:  I think this is a moot point because I believe they can use the same driver..


You should disable the old driver first ( though the installer will attempt to remove the old driver if it senses it). 
If you intend to use a driver not provided with ubuntu (such as the 195.30 or 190.53), download the driver now, and make it executable using:

```
 cd Downloads
sudo chmod +x <name of nvidia .run file> 
```Next, you must stop the X server 

```
sudo service gdm stop
```This will drop you to console.  Next, remove the nvidia module:

```
 sudo rmmod nvidia 
```Shutdown 

```
 sudo shutdown -h now 
```Replace your card, and restart.

If you are using a driver from ubuntu (through jockey) , select it from the restricted drivers window.  If you are installing from the downloaded nvidia file, stop the x server again (using sudo service gdm stop), login at the console prompt, cd to the Download location, and execute the .run file:

```
 ./<name of .run file>
```after installation is complete, run the command

```
 lsmod | grep nvidia 
```If nvidia is not displayed, you will need to hotplug it into the kernel using 

```
 sudo modprobe nvidia
```After the modprobe, lsmod | grep nvidia should show the module as being loaded.

Restart x using 
```
 startx 
```


Thank You, I will give this a go...I'll let you know how it goes. I wont have time today to do this...will get back. Thanks! ;)

---

