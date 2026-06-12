---
title: "Downloading packages independently"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-09-29
I would like to test out Moblin on my netbook, but I don't have an ethernet port.  I found out that I could install the wireless drivers, but I have to follow these directions:

[http://slaine.org/_slaine/Dell_Mini_9.html](http://slaine.org/_slaine/Dell_Mini_9.html)

Could you tell me how (in Ubuntu) to get the required repository files onto a USB drive so that I could install them in Moblin?

Thanks!

---

### Post by x22 on 2009-09-29
you could purchase a usb-rj45 adapter,
so as to connect with a wire--such as
eBay item #400065653786

---

### Post by A_Fiachra on 2009-09-29
from the link you provided:

```
                       

6.

6)Now we’re ready to build and install the new broadcom drivers

wget http://slaine.org/files/moblinv2/wl-kmod-5.10.91.9.3-1.moblin.src.rpm

(This build will download the broadcom driver archive directly from their site)

rpmbuild --rebuild --target=i586 wl-kmod-5.10.91.9.3-1.moblin.src.rpm

7.

7)Install the resulting rpm,

sudo rpm -ivh ~/rpmbuild/RPMS/i586/wl-kmod-5.10.91.9.3-1.moblin.i586.rpm
                                                            

```
You could put the source rpm on a flash drive or CD, copy it into your home directory and follow steps 6 and 7.

HTH

---

### Post by mikeyphi on 2009-09-29
> **brandoncolorado said:**
> I would like to test out Moblin on my netbook, but I don't have an ethernet port.  I found out that I could install the wireless drivers, but I have to follow these directions:

[http://slaine.org/_slaine/Dell_Mini_9.html](http://slaine.org/_slaine/Dell_Mini_9.html)

Could you tell me how (in Ubuntu) to get the required repository files onto a USB drive so that I could install them in Moblin?

Thanks!

You can put the whole OS onto a USB drive.
Hopefully you will find all the answers here:
[http://linux.dell.com/wiki/index.php/Moblin](http://linux.dell.com/wiki/index.php/Moblin)

Good luck!

---

### Post by brandoncolorado on 2009-09-29
> **A_Fiachra said:**
> from the link you provided:

```
                       

6.

6)Now we’re ready to build and install the new broadcom drivers

wget http://slaine.org/files/moblinv2/wl-kmod-5.10.91.9.3-1.moblin.src.rpm

(This build will download the broadcom driver archive directly from their site)

rpmbuild --rebuild --target=i586 wl-kmod-5.10.91.9.3-1.moblin.src.rpm

7.

7)Install the resulting rpm,

sudo rpm -ivh ~/rpmbuild/RPMS/i586/wl-kmod-5.10.91.9.3-1.moblin.i586.rpm
                                                            

```
You could put the source rpm on a flash drive or CD, copy it into your home directory and follow steps 6 and 7.

HTH

Thanks.  I understand that part, but how do I get the necessary packages as well?  The ones listed that I would have to get from synaptic.

---

### Post by brandoncolorado on 2009-09-29
> **mikeyphi said:**
> You can put the whole OS onto a USB drive.
Hopefully you will find all the answers here:
[http://linux.dell.com/wiki/index.php/Moblin](http://linux.dell.com/wiki/index.php/Moblin)

Good luck!

I have the whole thing on a USB drive, but the distribution does not come with the necessary wireless drivers (similar to old Ubuntu).

---

### Post by mikeyphi on 2009-09-30
Is this the problem - you have the OS on a USB drive and want to install the wireless drivers into that OS/USB drive?

If yes - perhaps you need to use 'persistent mode' on the USB.

There's a guide here:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Once the USB drive is made 'persistent' you can make permanent alterations to the OS.

Please ask again if I've misunderstood the problem.

On second thoughts - perhaps you are looking for a method of downloading and storing packages to transfer to your OS?
Try this: [https://launchpad.net/aptoncd](https://launchpad.net/aptoncd)

---

### Post by brandoncolorado on 2009-09-30
> **mikeyphi said:**
> Is this the problem - you have the OS on a USB drive and want to install the wireless drivers into that OS/USB drive?

If yes - perhaps you need to use 'persistent mode' on the USB.

There's a guide here:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Once the USB drive is made 'persistent' you can make permanent alterations to the OS.

Please ask again if I've misunderstood the problem.

On second thoughts - perhaps you are looking for a method of downloading and storing packages to transfer to your OS?
Try this: [https://launchpad.net/aptoncd](https://launchpad.net/aptoncd)

Mikey,

Thanks for the help.  I think your second idea is more appropriate.  This netbook does not have an ethernet port.  I have Moblin on a USB drive, and I want to install it.  After installing it, I cannot install wireless drivers because the directions I linked above show that I must download packages from the repository (impossible without ethernet).

The AptOnCD option looks good, but this netbook doesn't have a CD drive either.  

Maybe I just can't install Moblin on here?

---

### Post by mikeyphi on 2009-10-01
Although aptoncd was built for CD - because of the total number of packages, there should be no reason why you can't use the procedure to 'only' store a small number of packages onto another USB stick.

---

