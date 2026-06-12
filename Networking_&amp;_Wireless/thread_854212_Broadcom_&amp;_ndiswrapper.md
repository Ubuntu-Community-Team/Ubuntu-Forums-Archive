---
title: "Broadcom &amp; ndiswrapper"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by Maputo on 2008-07-09
Hello!

Just recently, I successfully installed the driver to my Broadcom wireless card, thanks to the steps posted here: [http://ubuntuforums.org/showthread.php?t=769990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=769990&highlight=wireless) , and my wireless finally started working.  However, there still is one issue that bugs me.  Every time I boot my computer, before getting wireless to work, I have to:
```

sudo modprobe -r b44 ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig eth1 up
```

Is there a way to automate this process, to have it already set up once the computer is booted?
I have a Dell laptop, with Hardy Heron installed.

Thanks.

---

### Post by chili555 on 2008-07-09
The kwik-n-durty way is to *sudo gedit /etc/rc.local* and add the following above 'exit 0':```
modprobe -r b44 ndiswrapper
modprobe ndiswrapper
ifconfig eth1 up
```Proofread, save and close. Let us know.

---

### Post by kevdog on 2008-07-09
Make sure ndiswrapper is not mentioned inside the /etc/modprode.d directory then do the following (if it is do the following: sudo rm -rf /etc/modprobe.d/ndiswrapper) then just cut and paste the following line to the command prompt -- boom your done -- won't need to do it again!:

echo -e '#Hardy ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b44; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

---

### Post by Maputo on 2008-07-09
> **kevdog said:**
> Make sure ndiswrapper is not mentioned inside the /etc/modprode.d directory then do the following (if it is do the following: sudo rm -rf /etc/modprobe.d/ndiswrapper) then just cut and paste the following line to the command prompt -- boom your done -- won't need to do it again!:

echo -e '#Hardy ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b44; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

The workaround worked :)!!!  Thanks a lot!

Also, it is nice to know where to put custom commands if I want them run on startup, so thank you, Chili555, too!

---

