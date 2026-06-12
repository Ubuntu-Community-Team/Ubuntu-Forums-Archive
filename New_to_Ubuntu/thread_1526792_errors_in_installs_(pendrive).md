---
title: "errors in installs (pendrive)"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by jaems-kun on 2010-07-08
I made a pendrive to run ubuntu 10.4 persistently via the instructions on the [_home page_]("http://www.ubuntu.com/desktop/get-ubuntu/download") and everytime I install something new, I get errors.

Things do install, but they hang at 90% for a long time and the errors are unsettling.

Here's the details from when I installed adobe flash:
[http://tinypaste.com/b755c](http://tinypaste.com/b755c)

Any advice?

thanks

---

### Post by okplayer02 on 2010-07-08
i dont know about instructions on the home page did you use the usb creator 

you go to system then administration then startup disk creator. 

and make your boot usb stick there

---

### Post by techunit on 2010-07-08
I assume you created the live thumbdrive from windows. Well what could be causing the error is that it wasn't created correctly. did you first download the Ubuntu.iso file or did you let the installer download it for you. If you let the installer do it you may have had a problem.

Another thing that could have happened is that you installed an application on the thumbdrive but got an error and didn't resolve it. If you think that this is the case please could you post the error your receiving by opening the terminal and typing the following:

```
sudo apt-get update
```

---

### Post by techunit on 2010-07-08
It looks like you had an error that messed up a bunch of things...

Open the terminal and type:

```
sudo dpkg --configure -a
```

---

### Post by RJARRRPCGP on 2010-07-08
Probably a bad sector on your USB stick. Sorry.

---

### Post by techunit on 2010-07-09
Generally this doesn't happen that much... Um if you haven't done what I have posted above yet please try this... boot from ubuntu on your main computer if you have it installed/Burn a CD for Ubuntu at 2x burn speed with Imgburn (just google imgburn) boot from a desktop/laptop and go system>administrative>Start-up disk creator. Then you will be given a wizard to install it on the thumbdrive. This is generally a sure bet. If you need help look at the videos [here]("http://ubuntuvideotutorials.wordpress.com/?s=usb+drive")

---

