---
title: "Can't mount HTC Desire Z - not authorised"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by phoenixdust on 2011-04-23
Hey,

I am very very new to Ubuntu, and have just hooked my phone up to transfer files as per a mountable disk drive, and I get a message saying "Unable to mount 7.9 GB File system - Not Authorized"

Why?! How do I prove to my computer that I am authorised?

PD xx

---

### Post by pi3.1415926535... on 2011-04-23
In order to mount certain disk drives, one needs to be root. In order to mount the drive, assuming that you are an administrator of the computer, is to find its location in it's properties. Next press "alt" and "F2". A pop up window should appear, then type into "gksu mount <location>". Next another pop up should appear, type in the administrator password. Now it should be mounted.

---

### Post by madjr on 2011-04-23
or try: gksu nautilus

---

### Post by RJ12 on 2011-04-23
Make sure that when you are browsing as root, not to go to your home directory... you can cause many problems by doing that.

---

### Post by heyandy889 on 2011-04-23
I have a Droid X and I occasionally connect the Droid to Ubuntu to transfer files to and from the SD card. On the Droid X, there are some goofy USB options to select in order to make everyone happy. 

When you connect the phone to a USB cable, do you get any sort of menus? On the Droid X, there's this default menu with a battery icon and the time. USB notifications also show up there, selecting those notifications let you connect the phone as "USB Storage," "Charge Only," and some other options like PC mode that I don't understand. :-D

So, when you connect the computer via USB to the phone, do any menus pop up on the phone?

---

### Post by phoenixdust on 2011-04-24
Thank you lovely people! And pi3.1^n - twas your advice that fixed it. 

Many thanks :)

PD

---

### Post by phoenixdust on 2011-04-27
Just a query,

How would I do this via a terminal?

PDxx

---

### Post by GaryTheCat on 2011-04-27
I've got a different android phone that requires me to enable USB debugging on the phone before it'll mount the phone as a USB device (settings ---> applications ---> development ... it should be in there)

Don't know if that helps?

G

---

### Post by dpwilson on 2011-04-27
> Make sure that when you are browsing as root, not to go to your home directory... you can cause many problems by doing that.


I have never heard that before.  Can you elaborate as to the implications?

---

### Post by TeoBigusGeekus on 2011-04-27
> **dpwilson said:**
> I have never heard that before.  Can you elaborate as to the implications?

It's not that bad. You just have to make sure that you won't change any permissions to root, cause then you won't be able to do some tasks as a normal user. But a chown will fix everything.

---

### Post by the-new-x on 2011-08-13
> **TeoBigusGeekus said:**
> It's not that bad. You just have to make sure that you won't change any permissions to root, cause then you won't be able to do some tasks as a normal user. But a chown will fix everything.

I'm sorry, but I'm kind of a noob to Ubuntu, and i think that i might use to reset the privileges, cause i can't do some things except when i am a root (and i do not even know how to login as the root), so how can do a "chown"?

Thanks.

---

