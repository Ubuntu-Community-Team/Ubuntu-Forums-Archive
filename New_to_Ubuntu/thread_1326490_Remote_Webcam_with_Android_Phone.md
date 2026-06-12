---
title: "Remote Webcam with Android Phone"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-14
I have a logitech webcam (which works flawlessly with skype, etc.) on my ubuntu PC and I was wondering if there are any apps that allow me to view the camera feed on my Android phone.

Thanks

---

### Post by Jon Monreal on 2009-11-16
You could possibly try [android-vnc-viewer]("http://code.google.com/p/android-vnc-viewer/") in connection with VNC in Ubuntu, but you would have to have a window open with the webam's display and I imagine the framerates would be awful to the point that the entire ordeal might be completely infeasible.

---

### Post by abhiroopb on 2009-11-17
I'm really confused :P

---

### Post by Jon Monreal on 2009-11-17
> **abhiroopb said:**
> I'm really confused :P

Confused? Could you specify what you're confused about?

The suggestion is simple: have a program such as Cheese open on your Ubuntu desktop, and use android-vnc to view the desktop remotely so that you can see what Cheese is displaying. Whether or not this will work (or work well) is a completely different question.

---

### Post by ergosteur on 2010-06-11
Alternatively, you could install motion (in repos, apt-get install motion) which is a daemon that runs a little web server with a live feed from your webcam. It also has the option to save frames or video when motion is detected (hence the name, "motion"). I actually had it running with a Logitech usb cam on an old NSLU2 and it worked quite well.

---

### Post by ubudog on 2010-06-11
> **ergosteur said:**
> Alternatively, you could install motion (in repos, apt-get install motion) which is a daemon that runs a little web server with a live feed from your webcam. It also has the option to save frames or video when motion is detected (hence the name, "motion"). I actually had it running with a Logitech usb cam on an old NSLU2 and it worked quite well.

Sounds like the best option.

---

### Post by no2498 on 2010-06-11
motion does run all the time in the back ground
just a heads up for you

---

### Post by Tahakki on 2010-06-11
Which app would one use to access motion?

---

### Post by Jon Monreal on 2010-06-13
It's a live feed, so you'll need to access [http://[YOURIP]:8081](http://[YOURIP]:8081) from your Android. Beware of dynamic IP addresses that some broadband providers use (your IP might change over time).

You can test to make sure you have it working right by navigating to [http://localhost:8081](http://localhost:8081) on a browser on the machine (if you haven't started motion yet, you'll need to do so by going to a terminal, typing "sudo motion" minus the quotes, and pressing enter).

---

