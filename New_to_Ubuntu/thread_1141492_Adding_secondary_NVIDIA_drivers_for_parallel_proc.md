---
title: "Adding secondary NVIDIA drivers for parallel proc"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by newport_j on 2009-04-28
I am looking to install an NVIDIA driver, and I want to control the installation to the extent that I can. 
 
1. I do not want to install the kernel driver. I am using the ancillary drivers in a effort to parallel process. The system already has a NVIDIA working graphics card and driver. That driver  is not going to be used for parallel processing. The newly installed NVIDIA driver will be used for parallel processing and only parallel processing. Hence, the kernel driver will not be installed on the new NVIDIA driver installation.

2. The X and GL libraries must be directed to new directories so as not to interfere with the current drivers. I am going to need to designate paths for these directories.

3. My command is




NVIDIA_Linux-X86-180-22-pkg1.run no-kernel-module  --x-library-path=/usr/parallel-x-libraries/ --open-libdir=/usr/lib/parallel-opengl-libraries/ 




1. the first option does not install the new graphics driver kernel, this stops it from interfering with the origally installed kernel as explained above.  

2. the second option redirects the NVIDIA  x libraries to a new directory (so as not to interfere with the current libraries operating the graphic card) I only want this second NVIDIA installation to be used in parallel processing. 

3. the third option redirects the opengl libraries to a new directory (so as not to interfere with the current libraries operating the graphic card) I only want the NVIDIA installation to be used in parallel processing. This is the same as reason 2, but now we are talking about different libraries : opengl and opposed to NVIDIA X.

Of course before I do this these new directories must be created per the post from yesterday. 

I want to do this and I do not want it to be irreversible, but it probably is so I must be very careful in issuing this complicated command.

Is the a way to do it in steps? I am afraid of doing it all at once. Something could backfire.

Newport_j

I realize this is complicated, but it is the only way I knew to present it. 

Any help appreciated.

---

### Post by Hospadar on 2009-04-28
What exactly is your setup and what are you trying to do?

If you're talking about having one video card use one driver for graphics processing, and another for cuda/openCL processing, I'm not sure that's possible, are you getting info from a guide somewhere that you could link?

---

### Post by newport_j on 2009-04-28
I am sure that I can add secondary NVIDIA drivers for my system. The trick is not to have them interfere with the existing drivers. The newly added drivers will be used only for parallel processing. The originally installed card must not be interferred with or we lose graphics capability on the computer.
 
However, using the NVIDIA run file with --advanced options will give a lot of options on customizing the installation of NVIDIA graphics drivers. 
 
In my case I chose to not install the kernel module because I obviously am not using these drivers for their graphics processing qualities, but for their parallel processing qualities. I am also putting NVIDIA X and opengl drivers from this second installation into a different directory from the one that the originally installed card and its software is using. 
 
Again, let me emphasize that I am using the second installation drivers in parallel processing - no graphics at all.
 
The can be done, but first run the NVIDIA installer with the --advanced-options, option enabled and then many new options become available.
 
Now when I compile I will let the compiler know where the paraellel proceesing drivers are. As stated here, they are different from the driver installed for the graphics card. 
 
One NVIDIA graphics card and one parallel processing NVIDIA card. But there is only one installation program and its assumes the installation is for graphics purposes - it must be modified when its installation is not for graphics, but for parallel processing. That is what I trying to do.
 
I am running Ubuntu 8.04
 
 
 
The command:
 
NVIDIA-Linux-x86-180.22-pkg1.run --advanced options
 
should show you what i am doing.
 
 
Newport_j

---

