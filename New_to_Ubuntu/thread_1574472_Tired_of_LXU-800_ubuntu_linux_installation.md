---
title: "Tired of LXU-800 ubuntu linux installation"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by raju50 on 2010-09-14
Can someone please tell me a step by step procedure to get Reliance Netconnect 1X LXU-800 working on the ubuntu linux. Kernel version: 2.6.32-24-generic

---

### Post by hhh on 2010-09-14
See if this thread leads to a solution...
[http://ubuntuforums.org/showthread.php?t=1224347](http://ubuntuforums.org/showthread.php?t=1224347)

---

### Post by raju50 on 2010-09-17
doesn't work.

---

### Post by abs_kkk on 2010-09-17
here r few links from my side...
[http://ubuntuforums.org/showthread.php?t=1224347](http://ubuntuforums.org/showthread.php?t=1224347)
[http://www.linuxquestions.org/questions/linux-hardware-18/problem-installing-reliance-netconnect-lg-lxu-800-usb-modem-744189/](http://www.linuxquestions.org/questions/linux-hardware-18/problem-installing-reliance-netconnect-lg-lxu-800-usb-modem-744189/)

---

### Post by raju50 on 2010-09-22
I have finally got it working.
Here is the step by step procedure:
1. cd to bin directory of the lxu800 linux driver folder. (I first opened the bin directory, right clicked 'setup.sh' and then properties, copy the location, paste it in accesories-gedit text editor, put inverted commas on the words separated by a space and then in terminal type cd location, where replace the 'location' with what is now written in gedit text editor. Example: cd /home/prashant/Documents/"LG LXU 800"/"Dialer SW Package and User Manual"/MAC_LINUX_usb_driver/LINUX/LXU800_V2.6.27-7-generic/LXU800_v1.0.812.21092/bin 
Press enter. )

2. type 'sudo -s', press enter, type password, press enter. 

3. type 'bash setup.sh', press enter. (Don't mind the error.) 

4. type 'modprobe usbserial vendor=0xeab product=0x9357' and press enter. Close the terminal.

5. System - Preferences - Network Connections. Click on tab 'Mobile Broaband'  tab. Click add. Click Forward and follow the instructions. Job done!

---

### Post by raju50 on 2010-09-22
But everytime you restart you need to repeat step2 and step4.

---

