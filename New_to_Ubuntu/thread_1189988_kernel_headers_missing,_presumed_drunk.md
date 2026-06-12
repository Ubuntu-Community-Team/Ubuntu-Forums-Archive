---
title: "kernel headers missing, presumed drunk"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by super kim on 2009-06-17
i hope someone can help because i screwed it up a but at first but not content i continued and now i'm in a right pickle!

i was having problems with my laptop crashing since up updated from ubuntu 8.10, the freezes would be for no apparent reason and i found a post suggesting i needed to update the kernel to fix the problem.

I followed the instructions but upon rebooting my didsplay wouldnt load, i had to reset the graphics settings and now the correct nvida driver is not being used.

i tried to activate it and couldnt so after some help i installed EnvNG and when i selected the driver with EnvyNG it gave me an error message saying that the headers are missing from the kernel.

i'm thinking this is when i stop "learning" and start lstening to some experts. because i've been up all night now and i hope to fix this problem since i hate windows soooo much, please dont make me go back :(

---

### Post by Bachstelze on 2009-06-17
To install the headers for your current kernel:

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by super kim on 2009-06-17
$ sudo apt-get install linux-headers-`uname -r`
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.29-02062904-generic


what does this mean? oh god its totally broken now isnt it?

---

### Post by Bachstelze on 2009-06-17
Not really, you're just using a custom kernel. ;) Where did you get it from?

---

### Post by lavinog on 2009-06-17
Most likely the reason your laptop is crashing is because it is overheating.

What were you following when you updated the kernel? Did you compile your own kernel or did you download a package from another site...etc?

I think EnvyNG will only work with ubuntu kernels, so compiling a new kernel will not work with Envy. I know the latest ati driver isn't compatible with the newest kernel, it might also be the case with nvidia.

can you post the output of 
```

uname -a

```
Also: The overheating issue is not fixed in jaunty, and you might have no choice but to go back to 8.10
[url=http://ubuntuforums.org/showthread.php?t=1129135]Laptop getting very hot after jaunty upgrade
[/url]

---

### Post by super kim on 2009-06-17
> **lavinog said:**
> Most likely the reason your laptop is crashing is because it is overheating.

What were you following when you updated the kernel? Did you compile your own kernel or did you download a package from another site...etc?

I think EnvyNG will only work with ubuntu kernels, so compiling a new kernel will not work with Envy. I know the latest ati driver isn't compatible with the newest kernel, it might also be the case with nvidia.

can you post the output of 
```

uname -a

```Also: The overheating issue is not fixed in jaunty, and you might have no choice but to go back to 8.10
[URL="http://ubuntuforums.org/showthread.php?t=1129135"]Laptop getting very hot after jaunty upgrade
[/URL]


the output is:
$ uname -a
Linux ubuntu 2.6.29-02062904-generic #02062904 SMP Sat May 23 23:35:48 UTC 2009 x86_64 GNU/Linux

there is no problem with overheating, i'm sure of that. the machine is  an Acer Aspire 9304WSMi.
i suspected overheating a long time ago and kept my eye on the cpu temp and it never gets warmer than a sunny day in scotland.
I cant find the post i was following when i updated the kernel since it all went wrong since then.

---

### Post by super kim on 2009-06-17
> **HymnToLife said:**
> Not really, you're just using a custom kernel. ;) Where did you get it from?

[http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)

---

### Post by Bachstelze on 2009-06-17
All roght, so do:

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
sudo dpkg -i linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
```

---

### Post by super kim on 2009-06-17
$ sudo dpkg -i linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
[sudo] password for *****: 
Selecting previously deselected package linux-headers-2.6.29-02062904-generic.
(Reading database ... 120913 files and directories currently installed.)
Unpacking linux-headers-2.6.29-02062904-generic (from linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb) ...
dpkg: dependency problems prevent configuration of linux-headers-2.6.29-02062904-generic:
 linux-headers-2.6.29-02062904-generic depends on linux-headers-2.6.29-02062904; however:
  Package linux-headers-2.6.29-02062904 is not installed.
dpkg: error processing linux-headers-2.6.29-02062904-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.29-02062904-generic

i'm not sure it worked quite right?
EnvyNG reports the correct driver is activated but i'm still getting the missing header error??

---

### Post by Bachstelze on 2009-06-17
Sorry, do that first:

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb
sudo dpkg -i linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb
```

And then reinstall the other one.

---

### Post by achase79 on 2009-06-17
you need to install both [linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb") and [linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb")

---

### Post by super kim on 2009-06-17
> **HymnToLife said:**
> Sorry, do that first:

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb
sudo dpkg -i linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb
```And then reinstall the other one.

ok, i done all that:
$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.29-02062904-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.29-02062904-generic has no installation candidate
user@ubuntu:~$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb)
--2009-06-17 19:12:28--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb)
Resolving kernel.ubuntu.com... 91.189.94.216
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8918862 (8.5M) [application/x-debian-package]
Saving to: `linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb'

100%[======================================>] 8,918,862    312K/s   in 14s     

2009-06-17 19:12:42 (605 KB/s) - `linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb' saved [8918862/8918862]

$ sudo dpkg -i linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb
[sudo] password for ******: 
Selecting previously deselected package linux-headers-2.6.29-02062904.
(Reading database ... 120673 files and directories currently installed.)
Unpacking linux-headers-2.6.29-02062904 (from linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb) ...
Setting up linux-headers-2.6.29-02062904 (2.6.29-02062904) ...


well no errors so from the terminal but when i open EnvyNG to change the graphics driver:
ERROR
 p, li { white-space: pre-wrap; }  EnvyNG has detected that the headers for your kernel are missing and cannot be installed


so where did i go wrong?

---

### Post by super kim on 2009-06-17
> **achase79 said:**
> you need to install both [linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb") and [linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb")

what is the best way to do this? is this what hymntolife is saying also?

should i just give up and try to restore the old kernel? it's a shame because this new kernel seems to have fixed the sytem crashes, ive had this machine on for over 12 hours now and still no crash!!

---

### Post by super kim on 2009-06-17
I may have cracked it, i'm not sure how but i need to restart the system to make sure the drivers activated. i will let you know if it worked what happened in one final post so it might be of benefit to others :)
if i dont post again its because i'm a noob and my lap top blew up in my face lol

---

### Post by LewRockwell on 2009-06-17
{{sirens in the distance}}

---

### Post by super kim on 2009-06-17
well the drivers are working now thank you everyone for your help....

there is hust one thing tho, as i was typing out my reply before saying how eveything was fixed now. the thing froze on me, not done that since i followed these instructions [http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29) 
have i just set my kernel back to how it was before i started? if not then  what causes the freezes? could it be compiz or even the nvida driver?

oh i might have to give up and try again after som sleep i've been at this now since 11, last night lol oh 23 hours my eyes head and hands all ache :(

uname -a
Linux ubuntu 2.6.29-02062904-generic #02062904 SMP Sat May 23 23:35:48 UTC 2009 x86_64 GNU/Linux
 it seems i have the updated kernel.

so the problem is either with nvida, or compiz. i have turned off compiz and wil see which one dies first, me or the lap top!

tbh i'm just glad it didnt go bang!

---

### Post by super kim on 2009-06-17
well i turned compiz off, and it hung again.i can only assume the problem is with the nvida driver.

~$ sudo lshw -c display
[sudo] password for *****: 
  *-display               
       description: VGA compatible controller
       product: G72M [Quadro NVS 110M/GeForce Go 7300]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

so this is my graphics card right?

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_ARB_create_context, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7300/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 180.44
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
etc etc etc.

and thats my driver?

What do i do now? i will search the web for any known problems but if you get there before me please post as i'm checking every 5 minutes or so.
thanks in advance :p

---

### Post by super kim on 2009-06-21
well if anyone cares... the problem seems to be with the nvidia driver.
the latest and reccomended driver has been removed and i'm using the older (version 173) driver is doing the job well enough and so far not one single crash!!!! 3 days and nights the laptops been on and running a whole variety of applications.

i guess thats it, oh and as a double whammy i managed to get my friends ubunto to play sounds as well!! lol

---

