---
title: "Webcam Trouble"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Cloud Wolf on 2009-02-17
I have a Trust 120 Spacec@m, and I am having trouble getting it to work under ubuntu. I have tried Easycam and camstream, and I am really stuck!

Any help would be appreciated.

---

### Post by Crafty Kisses on 2009-02-17
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post the results of this command:```
lsusb
```

---

### Post by Cloud Wolf on 2009-02-18
Ekiga doesn't show a thing, It is not detected :(
I know this one :D
for my webcam it is:
Bus 002 Device 002: ID 0c45:600d Microdia

I have already worked out I need a driver apparently (what is it?) but I have  no idea where from.

Was this what you wanted?

---

### Post by Roving Sign on 2009-02-18
> **Cloud Wolf said:**
> Ekiga doesn't show a thing, It is not detected :(
I know this one :D
for my webcam it is:
Bus 002 Device 002: ID 0c45:600d Microdia

I have already worked out I need a driver apparently (what is it?) but I have  no idea where from.

Was this what you wanted?

Check your user priviliges -  make sure the check box referencing webcams is checked...

System > Administration > Users and Groups

(user)Properties > User Priviliges

---

### Post by Cloud Wolf on 2009-02-18
> **Roving Sign said:**
> Check your user priviliges -  make sure the check box referencing webcams is checked...

System > Administration > Users and Groups

(user)Properties > User Priviliges

Has no reference to webcams at all. All the boxs are checked anyway (see the attachment)

---

### Post by Cloud Wolf on 2009-02-20
Bump.

---

### Post by carml on 2009-02-21
Sorry,I have no idea,because I don't use a webcam.Did you try also by google?
By the way,to find the other post,you can also access the homepage of the forum and search into the Absolute Beginner section.

---

