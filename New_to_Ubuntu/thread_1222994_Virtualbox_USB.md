---
title: "Virtualbox USB"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Tholley on 2009-07-25
I am following the instructions to add USB support in my virtualbox, before I create a new virtual drive, but need help in understanding the command lines.

I entered a root shell as instructed using sudo -i, but now how do I enter the next command? This is how it is shown in on this page, [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

vGid="`grep vboxusers /etc/group|cut -d\: -f3`" # Determine the devgid for the vboxusers group
 if [ "$vGid" ] && [ "`grep usbfs /etc/fstab`" == "" ] ; then
        echo "none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0" >>/etc/fstab
        mount -a
 fi

I tried just copy and pasting this but it just went back to the prompt. I'm thinking I missing something here. Do I need to change something, or do it as 2 or 3 commands?

---

### Post by llamabr on 2009-07-25
If it just went back to the prompt, it probably worked.  Step 3 is editing your /etc/fstab

Do 

```
cat /etc/fstab/
```

and at the end, you should see:

```
none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0
```

Look carefully at that command, and you'll see what it's doing.

---

### Post by Tholley on 2009-07-25
> **llamabr said:**
> If it just went back to the prompt, it probably worked.  Step 3 is editing your /etc/fstab

Do 

```
cat /etc/fstab/
```and at the end, you should see:

```
none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0
```Look carefully at that command, and you'll see what it's doing.

I copied and pasted your "Do" and got this... cat: /etc/fstab/: Not a directory

---

### Post by halitech on 2009-07-25
drop the trailing /

```
cat /etc/fstab
```

---

### Post by llamabr on 2009-07-25
Sorry.  my fingers type faster than my brain.  it should be:

```
cat /etc/fstab
```

fstab's not a dir.

---

### Post by Tholley on 2009-07-25
Ok! Thanks!

none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0
this is indeed at the bottom, it that all there is for USB support?

---

### Post by llamabr on 2009-07-25
> **Tholley said:**
> Ok! Thanks!

none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0
this is indeed at the bottom, it that all there is for USB support?

I don't know anything about virtualbox, but that was the result of step three of your instructions.

---

