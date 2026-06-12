---
title: "MS 5000 Bluetooth Mouse"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by pmenefee on 2009-05-13
I just bought a MS 5000 Bluetooth mouse and I can't get it to work with Jaunty UNR.  Works fine with XP.

Suggestions?

---

### Post by coffeeaddict22 on 2009-05-13
Bluetooth works, I've got a logitech mouse going fine.  
Have you got the Bluetooth stack running?  If there's a Bluetooth icon in the top right corner panel, right click on that and choose add..
If that doesn't work, can you open a terminal and type in ```
hciconfig
``` and post the results back?
(The terminal isn't deep magic, it's just a bit less intuitive than an interface.  The huge benefit is you can post the output of a terminal a lot easier than a series of pictures of a screen)

---

### Post by pmenefee on 2009-05-14
I have the Bluetooth symbol in the upper right hand corner.  When I click on  that I get a set up wizard that tries to set up the mouse.  The answer I get is that it fails to pair with the mouse both on auto, and using 0000 as the pin.

The output you wanted is:

```
hci0:	Type: USB
	BD Address: 00:22:43:CF:0C:E6 ACL MTU: 1021:8 SCO MTU: 64:1
	UP RUNNING PSCAN ISCAN 
	RX bytes:1266 acl:0 sco:0 events:69 errors:0
	TX bytes:2700 acl:0 sco:0 commands:64 errors:0

```

Thanks for trying to help me.

---

### Post by coffeeaddict22 on 2009-05-14
You are pushing the button on the bottom of the mouse just before you try to pair it, aren't you?

---

### Post by rustutzman on 2009-05-14
Install bluez-compat from the repository. Then run ```
sudo hidd --search
``` It should see your mouse and you'll be good to go.

Russ

edit: I believe Ubuntu NBR has the kernel from [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) but you might want to look into that also. After I loaded that kernel everything on my 1000he worked. The mouse appeared to pair but didn't. After running the above instruction it successfully paired and now works great.

---

### Post by pmenefee on 2009-05-14
> **coffeeaddict22 said:**
> You are pushing the button on the bottom of the mouse just before you try to pair it, aren't you?


Yes, the instructions say to push the button and it blinks red and green, as it's supposed to do.  It's blinking away as the wizard tries to pair it, but no luck.

---

### Post by pmenefee on 2009-05-14
> **rustutzman said:**
> Install bluez-compat from the repository. Then run ```
sudo hidd --search
``` It should see your mouse and you'll be good to go.

Russ

Thanks!  Unfortunately I'm off to work, so it will be a few hours before I can report back.

---

### Post by pmenefee on 2009-05-14
:popcorn:  Beer and popcorn for all:popcorn:!!

I installed bluez-compat using the package manager and then ran ```
sudo hidd --search
```
 and after a few seconds of "searching" it found my mouse, which now works!

Thanks

---

### Post by Colt725 on 2009-05-16
Those instructions worked for me to.  ):P
My MS mouse worked fine before I did update manager updated some bluetooth files.  I uninstalled the bluetooth program rebooted and reinstalled the program.  But nothing UNTIL i followed the instructions provided here.
Thanks :D

---

