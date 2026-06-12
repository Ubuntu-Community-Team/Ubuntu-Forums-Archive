---
title: "Ubuntu interface"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-11-03
Hello, I tried to configure my system so it supported 3D graphics and my graphics card is ATI driver and but then after restarting I faced a problem where when I enter Ubuntu it does not give the graphical interface to login it shows a text based interface where you login but I didn't know how to move to the graphical interface I tried a lot but I couldn't.

---

### Post by Tyke91 on 2009-11-03
login using your username.

then try this:
```
gdm
```if that doesn't do anything, make a note of the error. For kicks, try 
```
startx
```as well and see if it gives you the same error code.

if you still have the problem, do 
```
sudo dpkg-reconfigure xserver-xorg
```pay attention to what it does, and if you are STILL having the problem, please tell us what errors you got, as well as a printout of ```
sudo lspci
``` please :D


PS: Could you also link the guide that you were using to set up your 3D drivers? It should have been as simple as going into the restricted drivers manager.

---

### Post by mosaabJ on 2009-11-03
> **Tyke91 said:**
> login using your username.

then try this:
```
gdm
```if that doesn't do anything, make a note of the error. For kicks, try 
```
startx
```as well and see if it gives you the same error code.

if you still have the problem, do 
```
sudo dpkg-reconfigure xserver-xorg
```pay attention to what it does, and if you are STILL having the problem, please tell us what errors you got, as well as a printout of ```
sudo lspci
``` please :D


PS: Could you also link the guide that you were using to set up your 3D drivers? It should have been as simple as going into the restricted drivers manager.

Thank you for the reply I've sorted out the problem, I am writing this from Ubuntu I found a problem in the file xorg.conf which I fixed, thank you again you was of a good help.

---

### Post by Tyke91 on 2009-11-03
heh... writing an xorg.conf file can be a pain >.<

glad you got it sorted!

---

### Post by Tyke91 on 2009-11-03
I won't be on for very much longer. Please copy your private messages to me into this thread if you still need help ^_^
(installing that pesky ATI x1600 driver)

---

### Post by mosaabJ on 2009-11-03
> **Tyke91][quote=mosaabJ]Hello, sorry to disturb you again I just have another small problem, which is that I couldn't enable Normal or extra effects to my system even though before this problem I was using extra effects. Also is there any other way to install 3D graphics driver for my ATI Radeon X1650SE as I tried many ways but they didn't work and they crashed my system.
Best regards
MosaabJ[/quote]
There's an error when I do this
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic said:**
> http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English[/url]
download that and follow the instructions exactly.

when the instructions get to "open a terminal and navigate to the directory where you downloaded the driver" do this
Open a terminal and use the ```
cd
``` command to change directories to where it's downloaded.

SO if you downloaded it to your desktop then ```
cd /home/yourusername/Desktop
```

then execute their command ```
sh ./ati-driver-installer-9.2-x86.x86_64.run
```

if you get permission denied do ```
sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
```

if you STILL get permission denied do
```
chmod +x ./ati-driver-installer-9.2-x86.x86_64.run
```
then try 
 ```
sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
``` 
again.

I won't be on for very much longer. I hope this goes well for you ^_^
[COLOR="Red"][SIZE="4"]First I had to change[/SIZE][/COLOR]
```
sh ./ati-driver-installer-9.2-x86.x86_64.run
```
to
```
sh ./ati-driver-installer-9-3-x86.x86_64.run
```[COLOR="DarkOrange"][SIZE="4"]
And then there's an error after doing that and the error is: [/SIZE][/COLOR]
```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

---

