---
title: "System program problem detected 11.4"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2011-06-02
Could anyone please tell me what this message means? "it keeps popping up and I have no idea why?

---

### Post by dFlyer on 2011-06-02
> **cheekymonky2010 said:**
> Could anyone please tell me what this message means? "it keeps popping up and I have no idea why?

please post your problem

---

### Post by wildmanne39 on 2011-06-02
> **cheekymonky2010 said:**
> Could anyone please tell me what this message means? "it keeps popping up and I have no idea why?Hi, we need to know what program and what is the error message, if any other then problem detected.

---

### Post by cheekymonky2010 on 2011-06-02
The main problem is not being able to watch dvds in full screen after upgrading to 11.4 from 10.4,"pc restarts itself every time"  but this message just pops up when I try to download pretty much any update or driver etc!

---

### Post by wildmanne39 on 2011-06-02
> **cheekymonky2010 said:**
> The main problem is not being able to watch dvds in full screen after upgrading to 11.4 from 10.4,"pc restarts itself every time"  but this message just pops up when I try to download pretty much any update or driver etc!

Hi, if you have a nvidia card and are using the 270 driver it will cause problems like that, if you are install the older driver and it will probably fix your problem. If not put this command in a terminal so we can see what hardware you have.
```
sudo lshw
``` After you type the command copy and paste the out put here by clicking new reply then above the window you click on # and put the information in between the 2 code boxes ```

```

---

### Post by cheekymonky2010 on 2011-06-03
Hi and thanks for your reply! I hope this helps! :    *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4040B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A106
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:e400(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:22 ioport:e800(size=256)
If I could download the drivers from 10.4 that would be great if they work the same because I never had any problems when it was 10.4,  please let me know what you think?

---

### Post by wildmanne39 on 2011-06-03
> **cheekymonky2010 said:**
> Hi and thanks for your reply! I hope this helps! :    *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4040B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A106
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:e400(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:22 ioport:e800(size=256)
If I could download the drivers from 10.4 that would be great if they work the same because I never had any problems when it was 10.4,  please let me know what you think?Hi. recheck that command I gave you to use, there should have been a lot of information, like your video card and much more.

---

