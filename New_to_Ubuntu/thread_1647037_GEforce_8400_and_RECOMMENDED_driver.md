---
title: "GEforce 8400 and RECOMMENDED driver"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by oxygenfarm on 2010-12-16
I'm using the NVIDIA GEforce 8400 card with Ubuntu 10.10 and stupidly went to "System-Administration-Additional Drivers" and told it to install the RECOMMENDED driver, Now Ubuntu won't load. Is there anyway to backdate or remove that RECOMMENDED driver?
Help appreciated. I'd rather not have to reinstall.

---

### Post by py8elo on 2010-12-16
Hi Charlie,
You could remove all installed drivers and blacklist noveau driver. Then, You can reinstall the latest driver from nvidia site.
To do it,press Ctrl+Alt+F1.
$ sudo service gdm stop
$ sudo apt-get --purge remove xserver-xorg-video-*
$ sudo gedit /etc/modprobe.d/blacklist.conf
Insert this code:
blacklist vga16fb
blacklist nouveau
Save and exit
$ sudo service gdm stop
$ sudo apt-get --purge remove xserver-xorg-video-nouveau
$ reboot
After restart:
$ sudo service gdm stop
Go to the folder where You has saved the new Nvidia driver and insert the code:
$ sudo sh NVIDIA-Linux-x86-xxx.xx.xx.run
It will start the driver installation.
After installations has finished You can start X inserting the code:
$ sudo service gdm start
Or You can restart your PC.

I hope it can help You!!!

Best Regards,

Silva.
PY8ELO

---

### Post by oxygenfarm on 2010-12-17
Thank you......but I can't even get into Ubuntu. Must I simply reinstall?

---

### Post by Frogs Hair on 2010-12-17
When you try to boot I'm guessing you get a black screen. Ctrl + Alt + F1 , should open the tty login screen/terminal where you can follow the steps posted by py8elo. If not then you my have to reinstall .

---

### Post by khelben1979 on 2010-12-17
That driver which you installed will not be activated upon reboot if you have/had the possibility to boot from a different kernel.

Once the non-free graphics driver have been installed it get's configured to the booted kernel and having at least 2 linux kernels to switch to would or can solve your current issue, depending on how it looks like.

If it looks really bad and the display gets locked on a black screen before the X server have been started, then you can press ctrl + c in the boot process and login from there if you manage to do it correctly.

On the nVidia website they got recommended [drivers]("http://www.nvidia.com/Download/index.aspx?lang=en-us") for your graphic card and in my opinion, they are better than what is recommended by the Ubuntu distribution.

---

### Post by py8elo on 2010-12-17
I has noticed the Ubuntu 10.10 have a issue with Nvidia drivers and I think to reinstall it is not the solution...
Just install the Nvidia recommended driver for your VGA card.
I use the GEforce 8400 GS and run it under Ubunt 10.04 with the latest Nvidia driver for it.
Good Luck!!!

Best Regards,

Silva.
PY8ELO

---

### Post by py8elo on 2010-12-18
Many peaples are having problems to install Nvidia drivers on Ubuntu.
Then, I decide to put here the step bye step I get my GEforce 8400 GS runing under Ubunt 10.04.
1st- Download the latest driver Nvidia for your card from Nvidia website and save on your home directory.
Go to terminal by pressing Ctrl+Alt+F1 and log as root.
CODE:
#Sudo service gdm stop (or "sudo service kdm stop" if You use Kubuntu)
$sudo gedit /etc/modprobe.d/blacklist.conf
Insert this code:
blacklist vga16fb
blacklist nouveau
Save exit and reboot
CODE:
#Sudo service gdm stop
#sudo apt-get --purge remove xserver-xorg-video-nouveau
#sudo apt-get --purge remove xserver-xorg-video-*
#sudo apt-get --purge remove nvidia-*
Restart PC and go to a terminal again.
#sudo init 3
#cd /your home directory or to the place where You has saved the new Nvidia driver
#sudo sh NVIDIA-Linux-x86.xxx.xx.xx
Now follow the instructions on the installation screens and be Happy!!!

I hope it can help somebody!!!

Best Regards!

Silva.
PY8ELO

---

