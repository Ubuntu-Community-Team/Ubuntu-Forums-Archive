---
title: "Setting up NVIDIA driver to lower resolution?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Cp6uja on 2009-09-27
I am Ubuntu novice. Just installed version 9.04 and already like it. However screen resolution is quite low (800x600). So I installed  'nvidia-glx-180' driver package that should support my GeForce 7650 GS card. Nothig really happened and  	 	 	when I ran 'Nvidia X Server Settings' from System>Administration got: “You do not appear to be using NVIDIA X driver. Run 'nvidia-xconfig' and restert X server". I have and that changed xorg.conf file in /etc/X11, but following reboot I ended up with blank screen and floating message which reads - resolution of 1600x1200 is out of the range (as it is). Can I resolve this without having to buy monitor that supports 1600x1200 resolution? To get OS working again I had!-- 		@page { margin: 2cm } 		P { margin-bottom: 0.21cm }* to restart it – this time in recovery mode and ran “xfix". This replaced xorg.cong file previously created with some default one which gives me no more than 800x600 resolution. 
Thanks
P.S. Can't restart X server with <Ctrl><Alt><BckSp> and waisted hours on reboots.

---

### Post by Cp6uja on 2009-09-27
_**Anyone?**_

---

### Post by overdrank on 2009-09-27
> **Cp6uja said:**
> _**Anyone?**_

Hi and welcome, please be patient.
If you can reach the command line with the ctrl, alt, F1 keys at the out of range screen you can use the command 
```
sudo /etc/init.d/gdm stop
```
Then try and reconfigure you xorg
```
sudo dpkg-reconfigure xserver-xorg
```
The try and restart x
```
sudo /etc/init.d/gdm restart
```

The restart of x with the ctrl, alt, backspace keys was disabled in Jaunty 9.04.

---

### Post by Cp6uja on 2009-09-27
Thanks for your reply. Now I've learned how to restart X server without rebooting machine :-)
I did everything as per your instructions. That changed my 'xorg.cong' file and when X server was restarted got this error message:
**Ubuntu is running in the low graphic mode**
The following error was encountered. You may need to update your configuration to solve this.
(EE) NV(0): FBIOPUT_VSCREENINFO succeeded but modified mode
See error logs for details.
Many thanks for your time

---

### Post by TombKing on 2009-09-28
I just went through the same problem setting up a pc for a neighbor's kid. I got a desktop back with the above instructions and removed the driver, rebooted and back to 800x600. I then loaded version 96 rather than 180 and all is happyland now.

---

### Post by Cp6uja on 2009-09-28
Thanks guys. Will try new drivers when I get back home. Hopefully it will work. Will let you know anyway.

---

