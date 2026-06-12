---
title: "How to install Latest Official Nvidia Driver in 11.04?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by rez182 on 2011-05-04
they say the latest nvidia driver supports the new ubuntu. its a .run file how can i install it? the default driver freezes my ubuntu and i cant even access the login screen to select classic mode. so ill try the latest driver directly from nvidia. right now i have no driver installed. so if this does not work... ill go back to 10.10

---

### Post by topnaught on 2011-05-04
> **rez182 said:**
> the latest nvidia driver ...... its a .run file how can i install it? 
The driver is packaged as a shell script. Additional details and instructions are available in the readme me file.  Here's a link nvidia's download site and the chapter with installation instructions: [http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/installdriver.html)

---

### Post by rez182 on 2011-05-04
how do i stop the x server?

thanks

---

### Post by rez182 on 2011-05-06
nvm i re-installed 10.10 :(

---

### Post by rklapp on 2011-05-06
To stop the x server, I used the Recovery Mode option then select Normal Boot. This gives me the tty screen at the home folder so i can run the .run file in Downloads. It then gave me a message that the server is still in use (high res) and will install a command that will turn it off (but may not work on all installations). It rebooted and the fix worked so I was able to continue with the install.

---

### Post by EagleG33k on 2011-05-06
This may be too late, but if not...  I just recently updated my NVIDIA driver, and figured out that to stop the X server:
```

# stop gdm

```

Then you can use the .run file to install the driver

---

### Post by cuki_cuki on 2011-10-17
gdm stop? for ubuntu 11?
it´s not working here =(

---

### Post by fractalman on 2011-10-17
Go to synaptic package manager and install the nvidia-current package,  usually does it all for me with no probs :-)

---

### Post by CalemBendell on 2011-10-18
That'd be a negative for me.  Already used to running in tty1, but for some reason the normal commands for shutting down the gdm aren't working at all...

any help?!

Thanks!

---

