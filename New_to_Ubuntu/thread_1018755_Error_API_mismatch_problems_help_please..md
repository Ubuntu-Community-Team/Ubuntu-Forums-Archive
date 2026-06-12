---
title: "Error: API mismatch: problems help please."
date: 2008-12-22
forum: New to Ubuntu
---

### Post by yogo on 2008-12-22
I probably have multiple drivers installed, I am not sure how to remove ones that are extraneous. I had  a little trouble getting Compiz running.. Compiz would almost always run but the majority of time in low graphics mode, a few time desktop effects could not be enabled. All this had me trying several different methods and now extra stuff is installed, I finally have used EnvyNG-GTK but it has required installing and uninstalling a few times to get it with the right resolution.

So what I am afraid is my system is a mess with all kinds of crap left behind although it was supposed to be purged.

This is my card.
 lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)


This is an error

Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version..


and this I believe is left over garbage  I tried to remove some of those packages thru terminal but is says they are not installed.

dpkg-query -l | grep nvidia
ii  nvidia-glx-dev-envy                        1:96.43.05+2.6.24.503-503.30                         NVIDIA binary XFree86 4.x/X.Org driver devel
ii  nvidia-glx-envy                            1:96.43.05+2.6.24.503-503.30                         NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-new                             169.12+2.6.24.14-22.53                               NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-source-envy                  1:96.43.05+2.6.24.503-503.30                         NVIDIA binary kernel module source
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1                              Tool of configuring the NVIDIA graphics driv


My system works fine now as for resolution and Compiz but I think it needs some heavy cleaning. I did search quite a bit on the api mismatch but still have no idea how to remedy it.

Any help is greatly appreaciated and a Merry Chrismas to everyone in Ubuntu land.

---

### Post by yogo on 2008-12-22
Bump

---

### Post by yogo on 2008-12-22
I found this command and it cleaned up some of the mess.

[COLOR=SeaGreen]sudo apt-get --purge remove nvidia-glx* nvidia-settings[/COLOR]

which has got it to 1 driver but I still can not get rid of the 169....driver

dpkg-query -l | grep nvidia
rc  nvidia-glx-new                             169.12+2.6.24.14-22.53                               NVIDIA binary XFree86 4.x/X.Org 'new' driver


When I have tried to purge this (nvidia-glx-new )in terminal it says the package is not installed.

I still have the api mismatch going on.

---

### Post by IamReck on 2008-12-22
Why aren't you just using the Hardware Drivers?

Just go to System -> Administartion -> Hardware Drivers and select the newest driver, and you should be fine.

Once you do, restart your computer, go into terminal and run "compiz" copy and paste the output here.

---

### Post by yogo on 2008-12-22
> **IamReck said:**
> Why aren't you just using the Hardware Drivers?

.


That was one of the first steps I tried, it did not work, at least I did not get it to work properly.

Now when I check for hardware drivers, it says that there are no proprietary drivers on my system, although it has installed a driver before BUT I may not have done the right things to get it to work properly, it did not work out of the box.

Thanks

output

steve@steve-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0181 (rev c1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Comparing resolution (1280x960) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
present. 
Checking for Xgl: not present. 
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I know the 96.43.05 is from Envy, the 96.43.07 I downloaded and installed manually from the Nvidia site.

Can I just delete all files containing 96.43.07 or visa-versa 96.43.05 or will this effect the kernel? I guess both Envy and Nvidia's installer built their own kernel so I should be ok if I remove either one.

---

### Post by IamReck on 2008-12-22
Do you have the restricted repositories enabled?

---

### Post by yogo on 2008-12-23
> **IamReck said:**
> Do you have the restricted repositories enabled?


Yes.

I just got back in the country, I went over to Mexico yesterday and got stuck, the bridge wait was like three hours to cross so I just did more shopping and other things and waited til 2 am and all the traffic had died down and was easy to cross. I have not forgotten about this problem, just have not been able to post.

---

