---
title: "Nvidia graphics driver updateing"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by JPB666 on 2009-02-11
I can't get the latest Nvidia driver (180.29) to install. I used terminal and followed instructions but I get error message, can't open or file doesn't exist.
Is there a way to just upgrade the video driver from within the gui?

When I look in administrator folder for hardware update, it's not there?
I'm using the latest version of ubuntu. I'm using an Nvidia Geforce 6600.
Thanks

---

### Post by RomeReactor on 2009-02-11
Hi. Which driver are you currently running? What version of Ubuntu do you have--8.04, 8.10, etc? Is it 32 bit or 64?

Regarding the driver installation, make sure that either:

A) The driver is in your home folder; or

B) You navigate in the terminal (using the cd command) to the actual location of the driver.

Then you install it like so:
```
sudo ./NVIDIA_INSTALLER.run
```
Just change NVIDIA_INSTALLER.run to the actual name of the file.

---

### Post by Tatty on 2009-02-11
> **JPB666 said:**
> Is there a way to just upgrade the video driver from within the gui?

AFAIK, no.  It would be nice though, hopefully its on the cards for some point.

Whats the exact error message you are getting? What instructions are you following?  At which step is it failing?

---

### Post by JPB666 on 2009-02-11
It says can't open binary file or can't open file.

---

### Post by JPB666 on 2009-02-11
I'm using version 8.1 updated.

---

### Post by LastWho on 2009-02-11
take a look [here]("http://ubuntuforums.org/showpost.php?p=6426397&postcount=7") plz, i explained how i did it manually .. and Bodhi.zazen proposed to use envy

---

### Post by RomeReactor on 2009-02-11
> **JPB666 said:**
> It says can't open binary file or can't open file.

Try making it executable:
```
chmod +x NVIDIA_INSTALLER.run
```
again, change NVIDIA_INSTALLER.run to the actual name of the file; then try installing it. Also, remember that you must stop GDM before you install the driver.

---

### Post by Crafty Kisses on 2009-02-11
Once you have downloaded the NVIDIA driver you need to stop your X server, so press Cntrl-Alt-F2. Once you have done that you need to run the following:
```
sudo /etc/init.d/gdm stop
```
Then once you've done that you need to run the following, remember I'm just guessing the file is called **NVIDIA-Linux** and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Once the installation is done, restart the X server with:
```
sudo /etc/init.d/gdm start
```

---

