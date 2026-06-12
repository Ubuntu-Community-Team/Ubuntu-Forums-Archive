---
title: "Additional Driver and Nvidia"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by beew on 2011-06-07
Hi,

I noticed Additional Drivers reported that noveau experimental 3d driver is in use (11.04) I thought Additional Drivers is for installing proprietary drivers and the noveau one should be activated and in use by default. Why does it show up in the AD dialogue at all?

---

### Post by seawolf167 on 2011-06-08
The additional drivers is for open source drivers for your system. The only proprietary part which may be installed is Fglrx. If you want entire proprietary driver suite you'll have to manually download and install that from your graphics card manufacturer's website.

---

### Post by Paqman on 2011-06-08
> **seawolf167 said:**
> The additional drivers is for open source drivers for your system. The only proprietary part which may be installed is Fglrx. If you want entire proprietary driver suite you'll have to manually download and install that from your graphics card manufacturer's website.

Eh? You can use it for the proprietary Nvidia drivers, too. I believe it also does some of the wifi chipsets.

---

### Post by seawolf167 on 2011-06-08
> **Paqman said:**
> Eh? You can use it for the proprietary Nvidia drivers, too. I believe it also does some of the wifi chipsets.

Hmmm, I must have missed that, I've always installed the proprietary drivers directly from AMD/Intel for graphics cards. Thanks for the info!

---

### Post by beew on 2011-06-08
> **seawolf167 said:**
> The additional drivers is for open source drivers for your system. The only proprietary part which may be installed is Fglrx. If you want entire proprietary driver suite you'll have to manually download and install that from your graphics card manufacturer's website.

??? I think Additional Drivers are for proprietary drivers which cannot be bundled with the iso for legal and technical reasons. I always install Nvidia closed driver and things like broadcom wifi card with AD. 

My question is why would you need AD to install the Nouveu experimental 3D driver, which is open source?

---

### Post by seawolf167 on 2011-06-08
> **beew said:**
> ??? I think Additional Drivers are for proprietary drivers which cannot be bundled with the iso for legal and technical reasons. I always install Nvidia closed driver and things like broadcom wifi card with AD. 

My question is why would you need AD to install the Nouveu experimental 3D driver, which is open source?

Not all are proprietary and closed source - [Nouveu ]("http://nouveau.freedesktop.org/wiki/")is open source, its the [Fglrx ]("http://www.thinkwiki.org/wiki/Fglrx")component that is proprietary. The "official" proprietary items are in the ubuntu-restricted-extras package. Maybe you have unsupported releases under software sources checked and it decided you want Beta & experimental drivers as well? I'm not sure.

---

### Post by 3rdalbum on 2011-06-08
> **beew said:**
> Hi,

I noticed Additional Drivers reported that noveau experimental 3d driver is in use (11.04) I thought Additional Drivers is for installing proprietary drivers and the noveau one should be activated and in use by default. Why does it show up in the AD dialogue at all?

The Nouveau 2D driver is enabled by default in Ubuntu. The 3D driver is experimental and needs to be enabled using Additional Drivers.

Additional Drivers is not only for proprietary drivers, that's why they renamed it from 'Restricted Drivers Manager" to "Additional Drivers".

---

### Post by seawolf167 on 2011-06-08
> **3rdalbum said:**
> The Nouveau 2D driver is enabled by default in Ubuntu. The 3D driver is  experimental and needs to be enabled using Additional Drivers.

That makes sense - thanks for the info; I went and looked it up to read more about it [here]("http://nouveau.freedesktop.org/wiki/MesaDrivers").

---

