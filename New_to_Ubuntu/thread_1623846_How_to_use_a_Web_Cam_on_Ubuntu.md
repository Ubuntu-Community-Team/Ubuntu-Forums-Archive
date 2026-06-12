---
title: "How to use a Web Cam on Ubuntu?"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by ian19jam on 2010-11-17
I wish to use a web cam for Skype. My screen does not have a web cam. Si bought recently a Logitech Webcam C160 but it comes with all the Microsoft software which is no good for Ubuntu. I use Ubuntu 10.10 and so is there any way that I can use this Webcam on Ubuntu?  Is there a programme for me to download to make this work; Any suggestions and please in simple terms;. Thanks

---

### Post by TNT1 on 2010-11-17
I have a logitech webcam. I made it work by plugging it in to a usb port. That's it.

---

### Post by toekneewood on 2010-11-17
Give this a go.  Unplug the USB webcam.  Open a Terminal and type the following so that you can see what is going off
```

tail -f /var/log/messages

```
Then plug your webcam back in and 
```

sudo apt-get install cheese

```
Then go to the menu and select
```

> Applications > Sound & video > Cheese Webcam Booth

```
You should now see yourself in the webcam

Just for background in your terminal you should see something like "/dev/video0" if it is working. So if you do the following in a terminal you should see the device listed.  if you had 3 web cams they would be "/dev/video0" "/dev/video1" & "/dev/video2".  If you want to run more than one camera at a time then good luck as most of the hardware now days only has one USB controller that is powerful enough to support one camera.  Even if you have lots of USB ports.  To get around this you just install another USB controller card.  Like I said, this bit is just for extra info
```

ls -l /dev/video*

```

---

### Post by mastablasta on 2010-11-17
> **toekneewood said:**
> Give this a go. Unplug the USB webcam. Open a Terminal and type the following so```

sudo apt-get install cheese

```

 can i ask why he needs to install chese?

---

### Post by TNT1 on 2010-11-17
> **mastablasta said:**
> can i ask why he needs to install chese?

To see it working presumably, although there are a multitude of other things that could do that.

---

### Post by toekneewood on 2010-11-17
> **mastablasta said:**
> can i ask why he needs to install chese?

It is a very simple bit of software that I use to confirm that my camera is working that way I want it to, as over the years I have had lots of problems getting my logitech 9000 working

---

### Post by toekneewood on 2010-11-17
> **TNT1 said:**
> To see it working presumably, although there are a multitude of other things that could do that.

woops, sorry I did not spot that you had answered this one, thanks :-)

---

### Post by olddai on 2010-11-17
Just do as TNT1 said and plug it into an empty USB socket.

To see it working just open up Skype -> Options -> Video Devices and click on Test. Job done!

---

### Post by TNT1 on 2010-11-17
> **olddai said:**
> Just do as TNT1 said and plug it into an empty USB socket.

To see it working just open up Skype -> Options -> Video Devices and click on Test. Job done!

That's exactly what I did with my Logitech, which I since got rid of, but the exact same thing worked fine on the 5usd Labtec camera I now use.

---

### Post by toekneewood on 2010-11-17
Just found a link that might come in handy "Ubuntu Wiki SkypeWebCams"
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by ian19jam on 2010-11-17
Thanks for all your advice and with the combination of Mastablasta and TNT1 it now works -  so simple when you know how. Thanks again

---

### Post by mastablasta on 2010-11-17
why not just use gstreamer-properties to do a test and set up the device?

---

### Post by whoey on 2010-12-20
I also picked up one of these Logitech c160 webcams for my desktop (Ubuntu 10.10) machine, initially it wasn't working, but I was using a usb port off my g15 keyboard, after rereading toekneewood's solution I plugged direct to one of the main usb ports on the tower itself, video works fine, however, I don't know how to get the built in mic to work...

---

