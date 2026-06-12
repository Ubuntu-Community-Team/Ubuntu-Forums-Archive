---
title: "Trouble running ProRealTime web-based Java app"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by China Diapers on 2011-07-26
Hi, 

I have recently installed Ubuntu 11.04 - the Natty Narwhal on my old Celeron machine

I am having difficulties running the Java charting package at [www.prorealtime.com](www.prorealtime.com).

I click to launch the workstation, the .jnlp file is downloaded, and this is where I would expect the workstation to start loading but it does not, no error, just doesn't start.

It ran the first few times I tried, albeit slowly, but for the last fews days it is not working at all.

Any ideas how to approach troubleshooting this?

Thanks

---

### Post by skatinjj on 2011-07-26
Anytime I plan on using java I install openjdk-6-jre and the browser plugin icedtea6-plugin

---

### Post by China Diapers on 2011-07-28
Hey thanks for the reply. 

I have both of those installed. The application doesn't actually run in the browser, it's launched form the browser, I a file with a jnlp extension gets downloaded and the software starts loading. 

Very weird. Any other ideas?

---

### Post by skatinjj on 2011-07-28
I would have to sit down and play with it myself.

I won't be able to til tomorrow though as I have prior arrangements for tonight.

---

### Post by China Diapers on 2011-07-28
Ah thanks mate, that would be most kind of you :)

---

### Post by skatinjj on 2011-07-28
Wrong topic =)

---

### Post by China Diapers on 2011-07-28
Chrome and Firefox

---

### Post by China Diapers on 2011-07-28
oh

---

### Post by skatinjj on 2011-07-28
Ok.  So I made an account and launched the simplified work station with no problems in firefox.

When asked if I wanted it to run, I clicked Always trust from this publisher button and clicked run.

---

### Post by China Diapers on 2011-07-28
I really appreciate you helping me man.

Yes, strangely the simplified workstation works for me too, but the complete workstation doesn't. I need to access the complete workstation for some of the features I need.

---

### Post by skatinjj on 2011-07-28
I can not help with that as I can not run it.  Are there any errors that come up?

---

### Post by China Diapers on 2011-07-28
No nothing, just doesn't run.
 
OK thanks I will try their support peeps.

---

### Post by China Diapers on 2011-07-29
Apparently, according to the Java website, there is a newer version of Java available than the one I am running.

So if I want to install the more recent version, how to I uninstall the version I currently have?

---

### Post by skatinjj on 2011-07-29
Open the terminal and type:

```
sudo apt-get remove openjdk-6-jre
```

It will ask you if you want to remove, type y and hit enter.

---

### Post by China Diapers on 2011-07-29
Thanks. Got the most recent version now, still not working, pissing me off now.

---

### Post by China Diapers on 2011-07-29
OK, I got it working, god knows what it was that I did that fixed it. Persistence pays off.

Thanks for the help.

---

### Post by skatinjj on 2011-07-29
Thats great!

---

### Post by skatinjj on 2011-07-29
If it is solved, remember to mark the thread as solved using thread tools at the top right =)

---

### Post by SmurfieMigration on 2011-09-04
[LEFT][COLOR=black]Hi I'm new to Ubuntu and still evaluating it via a usb pen drive, I was having the same issue as you until I found a package called "[/COLOR]IcedTea Java 6 Web Start" after downloading & installing it I can now run ProRealTime's complete workstation, it does seem a bit clunky with the graphics when mousing over a chart but that maybe because of the usb install I'm using.:P
I hope you can get a similar result and get it going.

[/LEFT]

---

