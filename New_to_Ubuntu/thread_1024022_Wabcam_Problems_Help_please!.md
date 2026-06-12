---
title: "Wabcam Problems Help please!"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by ShadowfoxXXX on 2008-12-28
I have a Microsoft Lifecam vx3000. EasyCam detects it, adn installs it, but for some reason it still won't work with cheese or camorama.

---

### Post by ShadowfoxXXX on 2008-12-28
bump

---

### Post by Michael.Godawski on 2008-12-28
hi, 

can you please post the output from this terminal command:

```
lsusb
```

---

### Post by ShadowfoxXXX on 2008-12-28
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 045e:0095 Microsoft Corp. IntelliMouse Explorer 4.0 (IntelliPoint)
Bus 002 Device 004: ID 046e:5542 Behavior Tech. Computer Corp. 
Bus 002 Device 003: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Michael.Godawski on 2008-12-28
Let's try the following:

download this drivers:
[gspcav1-20071224.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz")

Extract them to your /home directory for instance to /home/username/cam.

Open the terminal and change into the extracted driver directory:
```
cd /home/username/cam/gspcav1.....
```
Now we have to compile the drivers.
Make sure you have installed this package build-essential

```
sudo apt-get install build-essential
```
Now in the gspcav1..... directory execute:
```
make
sudo make install
```

When everything went fine add the new drivers to the modules:
```

gksudo gedit /etc/modules
```
add gspca to the end of the list, save the file.

Load the gspca with:
```
sudo modprobe gspca
```
Finished.

---

### Post by spiderbatdad on 2008-12-28
This camera is supposed to work with the gspca driver...which I think may be broken in Intrepid. You can try synaptic install gspca-source then sudo modprobe gspca-main

If it doesn't work, you may have to compile and patch your own driver.
This site talks about it...including the comments...It isn't too hard, but not easy for a beginner...a challenge maybe. Thanks MS.
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)
It talks about skype, but building the driver may be what you're after. Maybe someone else has a better solution.


EDIT: didn't mean to interrupt Michael.Gadowski, weren't sure you were coming back today.

---

### Post by cariboo on 2008-12-28
I have have a Logitech Quickcam Messanger that used the same driver up until Intrepid, Now it uses:

```
gspca_zc3xx 
gspca_main
```

I haven't been able to get it to work in Camorama or Cheese, but is does work in Xawtv, it actually works better in xawtv that i did in cheese.

---

### Post by ShadowfoxXXX on 2008-12-29
it works up until sud make install, then i get this.
> administrator@ubuntu:~/Cam/gspcav1-20071224$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
administrator@ubuntu:~/Cam/gspcav1-20071224$ gksudo gedit /etc/modules
administrator@ubuntu:~/Cam/gspcav1-20071224$ sudo modprobe gspca
FATAL: Module gspca not found.
administrator@ubuntu:~/Cam/gspcav1-20071224$ 
administrator@ubuntu:~/Cam/gspcav1-20071224$ 


---

### Post by ShadowfoxXXX on 2008-12-29
bump

---

### Post by aydinozdemir on 2009-02-10
Microsoft Corp. LifeCam VX-3000
I cant install gspca driver for my webcam. I download gspcav1-20071220.tar.gz file and make ./configure problem. How can we install webcam driver vx-3000 for ubuntu 8.10. I not professional linux user please advise all details.
thanks.

---

