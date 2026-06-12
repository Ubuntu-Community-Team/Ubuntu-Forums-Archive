---
title: "How can I increase Ubuntu virtual hard disk partition?"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by Fanatico on 2011-04-18
I have Ubuntu 10.10 running as guest OS via Vmware player on Windows 7 host.

I need to increase size of Ubuntu virtual disk. I've increases size of virtual hard disk via VMware olayer and now able to see extra unallocated space in Ubuntu Gparted utility.

But obviously I am not able to re-size partition I am running from:( How can I increase Ubuntu virtual hard disk partition?

Thanks

---

### Post by spikoley on 2011-04-21
Since its been a couple of days and nobody has answered you yet I will give you somethings to look into.

1.  You probably could create a new partition and put your data on it.

2.  I think you use Gparted to resize.  VMware give you the option to boot from an iso.  Try booting the iso from file and resize it with Gparted.  Make sure you back up the VMware image first.

---

### Post by seawolf167 on 2011-04-21
I'm assuming you are using Wubi since you said Ubuntu virtual hard disk, so [here is the how-to ]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")for increasing the Wubi install size.

---

### Post by srs5694 on 2011-04-21
> **seawolf167 said:**
> I'm assuming you are using Wubi since you said Ubuntu virtual hard disk, so [here is the how-to ]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")for increasing the Wubi install size.

Fanatico explicitly stated that he's using VMware, so your pointer is inapplicable.

---

### Post by seawolf167 on 2011-04-21
Guess I missed that - disregard my post then

---

### Post by bcbc on 2011-04-21
> **Fanatico said:**
> I have Ubuntu 10.10 running as guest OS via Vmware player on Windows 7 host.

I need to increase size of Ubuntu virtual disk. I've increases size of virtual hard disk via VMware olayer and now able to see extra unallocated space in Ubuntu Gparted utility.

But obviously I am not able to re-size partition I am running from:( How can I increase Ubuntu virtual hard disk partition?

Thanks

Not sure about vmware, but when I was using virtual box, I pointed the CDROM to an Ubuntu ISO (file on my harddrive) and then told virtual box to boot from CD. Then I could reinstall/run gparted etc. 

Here's a link that talks about booting from a CD using vmware: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=102](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=102)

Edit: I just noticed spikoley already mentioned that - I gotta read more carefully too :)

---

