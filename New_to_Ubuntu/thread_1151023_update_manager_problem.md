---
title: "update manager problem"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by kapi on 2009-05-06
keep getting this. 

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

could someone please advise

thanks

---

### Post by kapi on 2009-05-06
How do I fix the update manager? I keep getting this.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by darth_indy on 2009-05-06
That's not really much to worry about - it looks like you added the Medibuntu repository but didn't add the GPG key. All that means is that it's missing a layer of security

Open up terminal and paste this:
```

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

(in terminal, paste is ctrl+shift+v)

That should get rid of the first error.

The second error appears to be the fact that you have CD-ROM checked as a source. It's looking for your install CD, and is giving an error when it doesn't find it. I would recommend disabling that, as the CD repository is usually out of date.

To disable it: Go to System > Administration > Software Sources. Enter your password when it asks, and when the Software Sources window shows up, there should be a area that says "Installable From CD" - just uncheck the boxes next to any CDs in there.

Let me know if that worked!

---

### Post by cariboo on 2009-05-06
Have you run:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by kapi on 2009-05-07
keep getting this

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

updates not working - hope someone could assist please

thanks

Kapi

---

### Post by nimajiman on 2009-05-07
> **kapi said:**
> keep getting this

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

It looks like your cdrom is enabled as an update source/repository?

Try going into System -> Administration -> Software Sources, then at the bottom is an area labelled "Installable from CD-ROM/DVD". 
A Ubuntu cd should be listed in there with a check box next to it. If that check box has a tick in it, uncheck it then open a terminal and type 

```
sudo apt-get update
```

Hopefully it's that simple (i.e. no more error). If you still get the same error let us know.

---

### Post by kapi on 2009-05-07
thanks it worked

really appreciated

kapi

---

