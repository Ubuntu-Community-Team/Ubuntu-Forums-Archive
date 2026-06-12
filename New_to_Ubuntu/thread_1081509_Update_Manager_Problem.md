---
title: "Update Manager Problem"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by familyweare on 2009-02-26
Having recovered from a failed upgrade to 8.10 because of hardware compatibility problems, I'm up and running again with 8.04. I used the utility at UNetbootin that was downloaded on a usb stick to reinstall ubuntu 8.04.

However, not long after that I started getting messages from the Update Manager. The following is the message I get;



Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.



It seems to be asking for my original CD-ROM of the program, but I really don't know what this message means, as I used an usb stick to install the program and I didn't keep the program on the stick. 

Also, it seems to have caused updates to not occur, as the update manager now says my last update was 19 days ago.

What does this mean?

What am I suppose to do with this message?

Thanks

---

### Post by smani on 2009-02-26
Look in System -> Administration -> Software Sources if by any chance the CDROM is checked under Ubuntu Software - it should not be.

---

### Post by familyweare on 2009-02-26
I went to System -> Administration -> Software Sources and unchecked CD-ROM under the tab "Third-Party Software".

I know it says third party software and probably isn't what you meant but under Ubuntu Software tab there doesn't seem to be anything to "uncheck".

However on the "Ubuntu Software" tab is a box entitled "Installable from CD-ROM/DVD", and inside of it is written this;

"To install from a CD-ROM or DVD, insert the medium into the drive." 


Is this what you meant? If so what do I do, since I'm not seeing a box to check?

---

### Post by smani on 2009-02-26
Oh, they must have moved it in intrepid - anyway, uncheck everything that has to do with a cd rom ;)

---

### Post by familyweare on 2009-02-26
Ok thanks I'll let you know what happens.

---

### Post by familyweare on 2009-03-03
Thanks it's working now.

---

