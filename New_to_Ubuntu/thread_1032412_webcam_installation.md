---
title: "webcam installation"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by patman0623 on 2009-01-06
Hi everyone.

I've looked through all the documentation online for enabling my new Logitech webcam, and I must say I'm completely befuddled. The suggestions run everything from "oh just download this source code and make it, and everything will work" (I have no bleeping idea how to install source code; it never compiles right) to pages like [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech) which only tell me it works "out of the box" and to use uvcvideo as a driver(?).

However, this is patently untrue. Sites which use webcams cannot access the camera when it's plugged into the USB, and I have no idea whatsoever how to take a snapshot.

Could someone please lead me by the hand on how to install this camera? I'm going mad with the code talk I see in the Linux community. 

My information: 
Ubuntu 8.0.4 Hardy
x86_64
Logitech QuickCam E3500
046d:09a4

---

### Post by davideotape on 2009-01-06
After having a poke around on various websites, I am starting to think it might be something to do with the fact you are using 64 bit ubuntu. I have often run into software that is only supported on 32 bit ubuntu. However, wherever I look there seems to be no mention that the drivers work on only 32bit, or indeed that they don't work on 64bit. These are the steps I would try:

Open up the terminal (Applications,Accessories,Terminal), and type in ```
sudo apt-get install subversion
```

Press enter, and enter your password if prompted (your password will not appear, not even as asterisks, but this is the way the terminal works. As long as you press enter after entering your password it will work.)

Text will come up in the terminal, and you will be asked to confirm the installation. Enter "y" and press enter to continue.

When the installation is complete, enter this code:

```
sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
```

Once again, you may be asked to enter your password and confirm. If so, do as above.

Now plug in and try to use your webcam. To take a snapshot, go to add remove programs, search for "cheese", and install Cheese Webcam Booth" You can do this by clicking in the tick box next to the program, and then clicking "Apply changes"

If this doesn't work, I would try upgrading to 8.10, if this is at all possible. Here ([https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech")) the operating system version given for your webcam is 8.10. What this means, I can't be certain, but I am guessing that is the version needed to be installed for the webcam to work.

That is all the advice I can give you at the moment patman. I hope it proves useful, and you get your webcam fixed soon.

If anyone wants to correct me in any way, feel free. I have only been using ubuntu myself for less than a year, so I may be barking up the wrong tree completely. I am trying my best to give people the best advice I can give them though, and I hope that this is appreciated.

:D

---

### Post by patman0623 on 2009-01-06
This has, in fact, worked. The quality doesn't seem as good in Windows, though it might be in my head.

I'm not sure where you got that URL, or how it installed, but thank you.

As for subversion: can I use this package for other 32 bit programs? I've had a *lot* of problems with not being able to use (e.g., Amazon.com's mp3 downloading software).

---

### Post by davideotape on 2009-01-06
Glad it worked for you ;)

I got the link from your original post, followed it and searched around from there.

Subversion is not software allowing 32bit programs to run on 64 bit operating systems. It allows for the easier installation from source code (as far as I know) The problem obviously wasn't with the 64bit ubuntu, as the webcam is now working

Finally, I have just looked on the Amazon website, and there is not mention of a 64bit version, and nowhere do they say that the current software is only for 32bit ubuntu. I would send them an e-mail, asking them if there is a 64bit version. Otherwise, I don't have a clue whether it is possible to run 32bit software on 64bit systems.

---

