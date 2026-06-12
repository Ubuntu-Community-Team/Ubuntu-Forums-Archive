---
title: "Kernel &amp; ATI driver question......"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Christopher on 2009-04-07
I just installed the new kernel today & rebooted and all seems well.

Question #1. Do i need to re-install my ATI drivers for my 9800 pro?
         #2. Whats the command to check kernel version
         #3. Whats the commnd to see if my drivers are installed

Thank you in advance.

---

### Post by linuxuser21 on 2009-04-07
You can install the latest kernel from Synaptic, it will also have the one you have installed checked.

---

### Post by WRDN on 2009-04-07
To find the kernel version, type:

```
uname -r
```

You can get more information by replacing "-r" with "-a".

---

### Post by Christopher on 2009-04-07
2.6.24-23-generic, is this the newest kernel ?     How do i check if i need to re-install my ATI drivers ?

---

### Post by WRDN on 2009-04-07
From the ubuntu stable repo's, the latest kernel version is 2.6.27-11.
To check the drivers, look in /etc/X11/xorg.conf. You should be able to find the default driver here. If everything is working OK, then you don't need to reinstall.

---

### Post by Christopher on 2009-04-07
> **WRDN said:**
> From the ubuntu stable repo's, the latest kernel version is 2.6.27-11.
To check the drivers, look in /etc/X11/xorg.conf. You should be able to find the default driver here. If everything is working OK, then you don't need to reinstall.

If I run glxgears and it works does that mean im good to go ? I can also open my catalyst control center with no issues as well.     I updated cause the red exclamtion at the top right corner of my screen said there was an update. When i go to System/Administration and then click on update manager its telling me im all up to date.

---

### Post by WRDN on 2009-04-07
If you can use those applications, then the driver is OK and you need not update.

---

### Post by Christopher on 2009-04-07
> **WRDN said:**
> If you can use those applications, then the driver is OK and you need not update.
 
Is there a console command to give me my ATI driver version?

Thank you very much for your help.

---

### Post by WRDN on 2009-04-07
If you got the driver from the repo's, you can check synaptic for the driver version. Just open it and search for "ati". You will find the installed version and latest version available.

---

### Post by Christopher on 2009-04-07
> **WRDN said:**
> If you got the driver from the repo's, you can check synaptic for the driver version. Just open it and search for "ati". You will find the installed version and latest version available.

I installed it via Envy.

---

### Post by Christopher on 2009-04-07
Is there a console command to give me my ATI driver version? I installed the driver via Envy. Thank you in advance.

---

### Post by markbuntu on 2009-04-07
The catalyst control center will give you that information.

---

### Post by Christopher on 2009-04-07
> **markbuntu said:**
> The catalyst control center will give you that information.

Awsome, thank you very much.

---

### Post by Zero Prime on 2009-04-07
If you installed using Envy then you don't have to re-install your ATI drivers.

---

### Post by Christopher on 2009-04-07
> **Zero Prime said:**
> If you installed using Envy then you don't have to re-install your ATI drivers.

Interesting, hows that work?

---

