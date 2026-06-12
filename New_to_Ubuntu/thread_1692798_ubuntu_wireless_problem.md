---
title: "ubuntu wireless problem"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Zaffzaff on 2011-02-21
I've been having some issues with ubuntu. installed it/updated it/reinstalled it on a HP Pavilion dv2000 and the wireless will not work. bluetooth is on, drivers are updated, everything is enabled, but one day about 3 weeks ago the wireless just stopped picking up anything, it detects nothing. I've completely disassembled and resembled it yesterday to see if there was a broken bit of hardware but everything was in order, or at least as far as I can tell. The wireless assistant and wicd wont pick up any wireless networks, regardless of strength and location

tl;dr ubuntu wireless is picking up no networks, what do?

---

### Post by Old *ix Geek on 2011-02-22
I have an HP dv6000, so I think we're pretty similar. A couple of things come to mind:

Don't laugh, and don't get insulted: Are you sure you haven't accidentally moved the wireless slider to off? (On my laptop it's a slider on the front edge; it may be different on yours. And...*cough*...I speak from experience on this...I've actually done this before without realizing it, and then wondered why my wireless suddenly stopped working. ](*,) :lolflag:)

Which driver are you using? Have you tried the Broadcom STA driver? I use KDE and it's under **System | Hardware Drivers**.

---

### Post by seawolf167 on 2011-02-22
> **Old *ix Geek said:**
> Are you sure you haven't accidentally moved the wireless slider to off?

Hah, yea I've done this on one of my laptops (except its a little button on the front thats super easy to forget about)

Also, the new[er] STA drivers are much superior to the old B43 drivers, make sure to use those if you have a choice

---

### Post by Zaffzaff on 2011-02-22
> **Old *ix Geek said:**
> I have an HP dv6000, so I think we're pretty similar. A couple of things come to mind:

Don't laugh, and don't get insulted: Are you sure you haven't accidentally moved the wireless slider to off? (On my laptop it's a slider on the front edge; it may be different on yours. And...*cough*...I speak from experience on this...I've actually done this before without realizing it, and then wondered why my wireless suddenly stopped working. ](*,) :lolflag:)

Which driver are you using? Have you tried the Broadcom STA driver? I use KDE and it's under **System | Hardware Drivers**.

Yeah the switch is on, all hardware is on/active, and now i followed a link through another site and I'm attempting to download the driver through ndiswrapper, but i can;t figure out how to translate the .exe to .inf, which is what it's asking for(the driver installer ndisget)

---

### Post by Old *ix Geek on 2011-02-23
> **Zaffzaff said:**
> now i followed a link through another site and I'm attempting to download the driver through ndiswrapper, but i can;t figure out how to translate the .exe to .inf, which is what it's asking for(the driver installer ndisget)It's been a while since I had to go the ndiswrapper route. 2007, I think. Did you look under 'hardware drivers' (or whatever its equivalent is in GNOME)? This should be just a simple matter of clicking on the driver and activating it. If that's not an option, for whatever reason, and you're still having difficulties with ndiswrapper, post again. I'll see if I can dig out the instructions I wrote back then that made it a pretty easy process.

---

### Post by G4Oblivion on 2011-02-23
I'm currently using a dv2000.
Both B43 and STA drivers work, but STA is better.
(dv2000 has a BCM4311)

You should not have to use ndiswrapper.

Make sure network manager is a startup application.
System -> Preferences -> Startup Applications

Make sure either network manager or wicd is disabled.
I remember having issues when I first tried wicd and the only way to get it to work was to uninstall network manager. This was ~2 years ago, when I first tried ubuntu. I haven't used wicd since.

Do you remember if/what you did the day it stopped working?
Is the wireless switch on the bottom left corner of the laptop blue or orange?

---

