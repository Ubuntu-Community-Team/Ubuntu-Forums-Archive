---
title: "Screen Flicker upon Resume from Suspend to RAM"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Melk79 on 2009-05-19
I'm actually trying out Mandriva on an old desktop right now, but can't get an answer on their [forums]("http://forum.mandriva.com/viewtopic.php?t=111162")...

Does anyone here have any thoughts? When I resume from a suspend on my older Dell Dimension 4500S with Intel integrated AGP graphics, my screen will flicker/shudder/shake particularly while idle and especially when I gray the screen with the restart dialog.

All specs are [here]("http://support.dell.com/support/edocs/systems/dim4500s/specs.htm") .

I am using a Hanns-g HW191DPB 19" widescreen LCD.

The flickering will very briefly show the ghost image of what's on the right side of my screen on the left side and slide it very quickly back and forth. It will then become stable for a few minutes if you're using Firefox, etc, but continue to flicker until restart. Perfect upon restart. Logout/Logon doesn't fix it, only restart.

---

### Post by cek1227 on 2009-05-29
> **Melk79 said:**
> I'm actually trying out Mandriva on an old desktop right now, but can't get an answer on their [forums]("http://forum.mandriva.com/viewtopic.php?t=111162")...

Does anyone here have any thoughts? When I resume from a suspend on my older Dell Dimension 4500S with Intel integrated AGP graphics, my screen will flicker/shudder/shake particularly while idle and especially when I gray the screen with the restart dialog.

All specs are [here]("http://support.dell.com/support/edocs/systems/dim4500s/specs.htm") .

I am using a Hanns-g HW191DPB 19" widescreen LCD.

The flickering will very briefly show the ghost image of what's on the right side of my screen on the left side and slide it very quickly back and forth. It will then become stable for a few minutes if you're using Firefox, etc, but continue to flicker until restart. Perfect upon restart. Logout/Logon doesn't fix it, only restart.

Same problem here on a simple Dell Dimension with a CRT. Does not occur on my Dell laptop. I suspect that it's related to having CRT instead of LCD.

---

### Post by HeWhoE on 2009-09-13
I have the same problem with a Dell Inspiron 4500s.  I have an LCD monitor attached to it.  The integrated video device as printed by lspci is

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by GeneralSpecific on 2009-10-10
Here is a similar topic.

[http://ubuntuforums.org/showthread.php?p=8085630#post8085630]("http://ubuntuforums.org/showthread.php?p=8085630#post8085630")

I posted a possible solution...though I'm not yet sure why it works or how to make good use of it.

Try:

```
sudo /etc/acpi/sleep.sh
```


I don't know Mandriva at all, so you may need to search for the /acpi directory to find the sleep.sh script.

-Ryan

---

### Post by cajual on 2009-12-22
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456)

---

### Post by kishanbhat on 2010-04-01
GeneralRepublic,

Thanks to your post - [http://ubuntuforums.org/showpost.php?p=8085657&postcount=4](http://ubuntuforums.org/showpost.php?p=8085657&postcount=4), I tried "/etc/acpi/sleep.sh" when I saw incessant flickering. The machine went into suspend mode. I woke it up and the ***flickering is gone***!! I think lot of users are having this problem and GeneralRepublic has an easy solution.

Otherwise it was so stressfull in seeing this flicker and keep moving the mouse to avoid the flickering.

Xubuntu 9.10 + Fluxbox (from ubuntu rep). Compaq nc6220
*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0

---

