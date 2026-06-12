---
title: "Xsane thinks my new digital camera is my scanner"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Irish1 on 2010-04-19
I've used xsane before without any problems and have the proper backend installed, but I recently bought a logitech digital camera and now all of the xsane features go to the camera.  I unplugged the camera, but then xsane can't find the scanner.  

Any thoughts?

---

### Post by sandyd on 2010-04-19
> **Irish1 said:**
> I've used xsane before without any problems and have the proper backend installed, but I recently bought a logitech digital camera and now all of the xsane features go to the camera.  I unplugged the camera, but then xsane can't find the scanner.  

Any thoughts?
try
```

rm -rf ~/.sane

```
p.s. Dont think it has anything to do with you plugging the camera in. I got a HD webcam plugged in all the time. It shows up in xsane, but doesnt interfere at all w/ the scanner.

---

### Post by no2498 on 2010-04-20
try your cam in cheese see if it works

---

### Post by Irish1 on 2010-04-21
The digital camera works fine with Cheese.

And the code provided above doesn't do anything in the terminal.

What is a .drc file?  I think Xsane recognizes the camera because it is this file type.  

Also, when I try to scan I get the error message Invalid Argument'

Thanks for all the help/advice I do really appreciate it.

---

### Post by Irish1 on 2010-04-21
Xsane seems to recognize my camera because it's a .drc file and when I try to load xsane.rc I get the error message '.sane/xsane.rc is not a device-rc file' - What does this mean?

I have oslo 3071b2.usb file in the gtxx folder; I got the file from the sane backend page.  

This all used to work fine until I got the digital camera hooked up to the PC and now only the camera is recognized.

---

