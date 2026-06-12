---
title: "Koala Display Konumdrum"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by nnjond on 2010-02-03
Hi,

9.10 live on my pen drive or cd finds my appropriate scrn res by default, however on my clean install,  9.10 warns me, each time I boot:

"Ubuntu is running in low graphics mode 

The following error was encountered. You may need to update your config to solve this. 

(EE) NVIDIA (0) FAILED TO LOAD NVIDIEA MODULE 
(EE) ***ABORTING*** 
(EE) SCREENS FOUND, BUT NONE HAVE USEUABLE CONFIGS" 

Then i get 4 options: 

"Run in low graphics mode 

Reconfig graphics 

Troubleshoot error 

exit console" 


Troubleshoot error leads to four more options 

"Review Xserver log file 

Review startup errors 

Edit config files 

Archive config and log" 

I don't really understand these options and am hoping someone can give me some simple advice

---

### Post by cariboo on 2010-02-05
Do you have the restricted drivers installed. Go to System->Administration->Hardware Drivers to check. If they are installed, start in recovery mode, and once at the menu, use the arrow keys to select drop to root prompt. Once at the prompt type:

```
nvidia-xconfig
```

This will create a new /etc/X11/xorg.conf file. Once the new file has be created, type:

```
exit
```

Then select resume from the menu. This should take you to a working desktop.

---

