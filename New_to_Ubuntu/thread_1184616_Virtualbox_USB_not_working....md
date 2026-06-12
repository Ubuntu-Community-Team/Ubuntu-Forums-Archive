---
title: "Virtualbox USB not working..."
date: 2009-06-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-11
My Virtualbox USB isnt working for some reason... I'm using Vbox 2.2.4 r47978 on Jaunty AMD64 and I've already added myself to the vbox user group thing;) 

when I right click on the icon at the bottom all the USB connections are greyed out..

is this a bug? as it just updated today:(

---

### Post by keplerspeed on 2009-06-11
Have you enabled usb mount in fstab? See my post #2 here:

[http://ubuntuforums.org/showthread.php?p=7418143#post7418143](http://ubuntuforums.org/showthread.php?p=7418143#post7418143)

Post is as below:

The OSE edition does not have usb support. You will have to download and install the PUEL (non-free) version off the virtualbox website: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

A good guide for the above installation of the PUEL version is here [http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html)

Then follow this to enable usb: (Thanks rfs1970!!! [http://ubuntuforums.org/showthread.php?t=1155643](http://ubuntuforums.org/showthread.php?t=1155643))

Enter this into a terminal:
```
sudo gedit /etc/fstab

```
At the end of the file add this line:
```

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```
Now save the file, then:
```

sudo mount -a

```

Finally, go to system>administration>users and groups and click 'manage groups'. Find vboxusers and ensure you are added to this group (your box ticked). Let me know how it goes!

---

### Post by reeseslover531 on 2009-06-11
I am not positive if this is still true, but doesn't only the non-OSE version of VirtualBox allow USB? The one in the Ubuntu repos is the OSE version. Go check out their website and get the non-OSE version.

---

### Post by muteXe on 2009-06-11
Yeah i think the one you get from the repo's is OSE, which doesn't support usb. You want the PUEL version from virtualbox's webby.

---

### Post by kamitsukai on 2009-06-11
it's not from the repo's it's the one from the sun website.... and on the previous one I had USB working fine

and I added myself last time with:

```
sudo adduser carl vboxusers
```

and I've re-done that and it says everythings fine...

---

### Post by keplerspeed on 2009-06-11
Yep. Then you will need to add /proc/bus/usb to fstab as I have posted above.

---

### Post by kamitsukai on 2009-06-11
> **keplerspeed said:**
> Yep. Then you will need to add /proc/bus/usb to fstab as I have posted above.

yep all works now...

strange:)

Thanks

---

### Post by keplerspeed on 2009-06-11
Cheers. So did you have usb support back, say, a week ago, without having edited fstab?

I have always had to add those details to fstab to get usb working in virtualbox, for the last 3 releases anyway.

---

### Post by kamitsukai on 2009-06-11
> **keplerspeed said:**
> Cheers. So did you have usb support back, say, a week ago, without having edited fstab?

I have always had to add those details to fstab to get usb working in virtualbox, for the last 3 releases anyway.

I had it right up until I updated to the newer release infact I've never edited the fstab to get usb support:D

---

### Post by Turtleman on 2009-06-11
I had the same problems but I didn't mess with fstab at all. I just added myself to the vboxusers and then logged out and logged in and it worked fine.

---

