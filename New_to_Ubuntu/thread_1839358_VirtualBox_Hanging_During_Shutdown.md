---
title: "VirtualBox Hanging During Shutdown"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by mdavis1231 on 2011-09-05
Is anyone besides me having a problem with VirtualBox 4.1.2 hanging during Shutdown?:confused:

---

### Post by haqking on 2011-09-05
> **mdavis1231 said:**
> Is anyone besides me having a problem with VirtualBox 4.1.2 hanging during Shutdown?:confused:

Shutdown of what ? Virtual box itself or a guest ?

if its a guest then probably guest related, do you have another guest to try ? do they all do it ? maybe ACPI related in the guest settings

And no problems with 4.1.2 on my 10.10 system, and i run lots of different VM's

---

### Post by 2F4U on 2011-09-05
I am running Windows XP in VirtualBox 4.1.2 under Kubuntu 11.04 and it doesn't hang during shutdown of Windows. I have the latest guest additions installed.

---

### Post by Rebelli0us on 2011-09-22
I'm running VirtualBox 4.1.2 in Ubuntu 10.10 and **Windows 2000 guest hangs on shutdown**. Guest worked fine when I first installed it.  I recently installed newer version of *Guest Additions*, changed guest *computer name* and successfully started sharing Ubuntu-mounted NTFS partitions on the Windows network...

---

### Post by haqking on 2011-09-22
> **Rebelli0us said:**
> I'm running VirtualBox 4.1.2 in Ubuntu 10.10 and **Windows 2000 guest hangs on shutdown**. Guest worked fine when I first installed it.  I recently installed newer version of *Guest Additions*, changed guest *computer name* and successfully started sharing Ubuntu-mounted NTFS partitions on the Windows network...

If it is a single OS that is hanging on shutdown then it is likely to be that VM OS that has an issue.

check the event viewer in windows 2000, check the logs of VBox etc, change ACPI settings etc.

---

### Post by Rebelli0us on 2011-09-22
> **haqking said:**
> If it is a single OS that is hanging on shutdown then it is likely to be that VM OS that has an issue.

check the event viewer in windows 2000, check the logs of VBox etc, change ACPI settings etc.

Thank you. I'm simply reporting yet another "guest hangs on shutdown". Guest will no longer shutdown on its own, doesn't respond to VirtualBox's "*send the shutdown signal*" but "*power off the machine*" works. Windows event viewer shows errors re the computer name change, but these should not prevent normal shutdown. I'don't have time to debug VBox but I hope they fix this soon.

---

### Post by haqking on 2011-09-22
> **Rebelli0us said:**
> Thank you. I'm simply reporting yet another "guest hangs on shutdown". Guest will no longer shutdown on its own, doesn't respond to VirtualBox's "*send the shutdown signal*" but "*power off the machine*" works. Windows event viewer shows errors re the computer name change, but these should not prevent normal shutdown. I'don't have time to debug VBox but I hope they fix this soon.

hope who fixes it soon ?

My windows 2000 professional (which i have 2) and a couple of Windows 2000 server VM's all shut down fine

---

### Post by Rebelli0us on 2011-09-22
> **haqking said:**
> If it is a single OS that is hanging on shutdown then it is likely to be that VM OS that has an issue.

check the event viewer in windows 2000, check the logs of VBox etc, change ACPI settings etc.

I uninstalled Guest Additions and Guest **shuts down OK**. Reinstalled Guest Additions and Guest again hangs at shutdown. The older Additions worked fine. I'd originally installed VBox 3.2.8 through Ubuntu Software center, then upgraded to the latest VBox, leaving the older Additions. "power off the machine" works but is it harmful?

---

### Post by haqking on 2011-09-23
> **Rebelli0us said:**
> I uninstalled Guest Additions and Guest **shuts down OK**. Reinstalled Guest Additions and Guest again hangs at shutdown. The older Additions worked fine. I'd originally installed VBox 3.2.8 through Ubuntu Software center, then upgraded to the latest VBox, leaving the older Additions. "power off the machine" works but is it harmful?

So are you using the latest Vbox (4.1.2) and the latest additions ?

as for harmful, it is only a virtual machine, and you should have a clone or snapshots anyways.

And even if it was a real machine, lots of people just hold the power button to turn it off, though not the best way incase of open system files and such

---

### Post by Rebelli0us on 2011-09-23
> **haqking said:**
> So are you using the latest Vbox (4.1.2) and the latest additions ?

as for harmful, it is only a virtual machine, and you should have a clone or snapshots anyways.

And even if it was a real machine, lots of people just hold the power button to turn it off, though not the best way incase of open system files and such

Yes I'm using latest 4.1.2 vbox and additions, though 4.1.2 didn't crash with version 3.2.8 guest additions. Clearly 4.1.2 additions are causing the problem on my system. Oracle's installation guide also mentions **dkms**, I have it installed but Ubuntu software center shows many more **dkms** packages, so I'm not certain I have what's needed. And no I don't think it's normal for guest OS to be crashing.

---

