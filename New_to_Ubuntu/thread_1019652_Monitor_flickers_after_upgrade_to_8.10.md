---
title: "Monitor flickers after upgrade to 8.10"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by dapissarenko on 2008-12-23
Hello!

I've upgraded my xubuntu 8.04.1 to 8.10 using the commands

```
sudo apt-get update
sudo apt-get dist-upgrade

```

After I rebooted the system, my monitor flickers (it did not before upgrade).

How can I fix the problem?

Thanks in advance

Dmitri

---

### Post by decoherence on 2008-12-23
when you say your monitor 'flickers' what do you mean? do you have a CRT or an LCD? if you have a CRT, it could be that the refresh rate has been dropped to 60Hz, which I find headache inducing. 

You may have to reconfigure X. How to do this may depend on your video hardware. Do you have an ATI, nVidia or Intel graphics card?

---

### Post by madsmaddad on 2008-12-23
I also have this problem. The screen keeps blacking out for a fraction of a second, usually when I am typing soemthing. 

The problem is finding the utility to set the monitor type and characterisitics. it is not available on the installation. 

Can you advise?

---

### Post by dapissarenko on 2008-12-23
Hello!

> **decoherence said:**
> when you say your monitor 'flickers' what do you mean? do you have a CRT or an LCD? if you have a CRT, it could be that the refresh rate has been dropped to 60Hz, which I find headache inducing.

I have a CRT and it seems that the refresh rate has been reduced. Exactly as you describe it.

> **decoherence said:**
> Do you have an ATI, nVidia or Intel graphics card?

I think, it is a SiS (Silicon Integrated Systems) graphics card, which is integrated into my mainboard.

How can I find out exact model of the graphics card?

Thanks!

Dmitri

---

### Post by mshipman on 2008-12-23
Find the exact model of your video card with: sudo lshw -C display

---

### Post by dapissarenko on 2008-12-23
Hello!

I have following graphics card:

```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 630/730 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller cap_list
       configuration: latency=0
```

How can I change xubuntu's display settings for this graphics card?

Thanks

Dmitri

---

### Post by madsmaddad on 2009-01-07
*-display UNCLAIMED
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
peterm@Intrepid:~$


I have a feeling there is some linkage between this and the keyboard, becasue teh screen only flickers when I am typing. I am using a Sony G220 CRT. 

MMD

---

### Post by madsmaddad on 2009-01-07
sorry for this, unable to delete.

---

### Post by dapissarenko on 2009-01-07
Hello!

In my case, sometimes (rarely) the monitor is configured with low resolution and flickering, and sometimes - with high resolution (1024x1024, I think) and no flickering.

I didn't change the configuration. The only thing I did was to download and install some updates.

So most of the time there is no flickering.

Best regards

Dmitri

---

