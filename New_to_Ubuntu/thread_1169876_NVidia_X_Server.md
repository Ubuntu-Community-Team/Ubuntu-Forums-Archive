---
title: "NVidia X Server"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by koconnor100 on 2009-05-25
```
You do not appear to be using the NVIDIA X driver. 
Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the 
X server.

```

I got the basic video card thats built into the mother board , and I got an add on card , Geo Fx 5500 ... trying to get the add on working. 

I suppose the first question is ... how do i edit this x configuration file ?

---

### Post by kwacka on 2009-05-25
Open terminal

Type ```
sudo nvidia-xconfig
```

Press 'Enter'

Type in password.

'OK' to the query about using makers code.

---

### Post by Bölvaður on 2009-05-25
> **koconnor100 said:**
> You do not appear to be using the NVIDIA X driver. 
Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the 
X server.

press Alt+F2
type: gksu nvidia-xconfig

you can also edit the file your self, you can find it here: /etc/X11/xorg.conf

or Press Alt+F2
type: gksu gedit /etc/X11/xorg.conf

but you might want to take backup of the file before doing anything crazy. so open the terminal (Applications &#8594; Accessories &#8594; Terminal)
type:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bckup
```
and then to edit it like before:
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by presence1960 on 2009-05-25
> **koconnor100 said:**
> ```
You do not appear to be using the NVIDIA X driver. 
Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the 
X server.

```

I got the basic video card thats built into the mother board , and I got an add on card , Geo Fx 5500 ... trying to get the add on working. 

I suppose the first question is ... how do i edit this x configuration file ?

I am not up to speed on vid cards simply because I have never had a problem with my Nvidia cards. I would try what it says - open a terminal and run ```
gksu nvidia-xconfig
``` I tried that command and it backed up my x config file and wrote a new one. restarted x server & all is well.

---

### Post by koconnor100 on 2009-05-25
> **kwacka said:**
> Open terminal

Type ```
sudo nvidia-xconfig
```

Press 'Enter'

Type in password.

'OK' to the query about using makers code.

After posting this I realized that "run as root" meant the sudo command. :D and so I did so. and it just went down to the next command line waiting for input. And I didn't know how to "restart the x server" so I settled for rebooting the computer. 

Still don't work. 

Examining the log file , way way at the bottom (it was in a special boot mode so I couldn't copy and paste) it said fatal error , no screens found ...

I suppose it could mean no monitor ? Because I had it plugged into the other port , but plugging it into the nvidia port just gets me a blank screen no matter how long I wait , and switching back gives me that annoying boot up error about it couldn't find a monitor or somethign like that so it was switching to low graphics mode.

---

### Post by presence1960 on 2009-05-25
did you install the drivers for the add on card? probably a dumb question but I will assume nothing.

---

### Post by felixkookie on 2010-10-17
i still encounter problem on this.. still won't get it.. what should I do with the 'getit' editor popping out? I am about to adjust screen resolution using NVidia X Server Setting .. but this won't happen for now.

---

### Post by kuckunniwi on 2012-02-07
> **felixkookie said:**
> i still encounter problem on this.. still won't get it.. what should I do with the 'getit' editor popping out? I am about to adjust screen resolution using NVidia X Server Setting .. but this won't happen for now.

I'm having the same problem. Current nvidia drivers (NVIDIA-Linux-x86_64-285.05.09) for my video card (GT 520M) proved messy and caused system start-up issues ([http://ubuntuforums.org/showthread.php?t=1860854](http://ubuntuforums.org/showthread.php?t=1860854) and [http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled](http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled)), so I'm using nvidia-current. 

When I open Nvidia X server settings, I get the message  

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I've tried $ sudo nvidia-xconfig

```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

and after reboot, I had the same issues with system start-up, which were solved by:

```
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg
sudo dpkg-reconfigure xserver-xorg
sudo reboot
```

Any ideas what it could be/what I can do to solve it?

Thanks guys! If in my proprietary driver issue-solving quest I come across a solution somewhere, I'll make sure to post here!

---

