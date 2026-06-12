---
title: "Nvidia GeForce 9200 trouble"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by sauma on 2009-09-11
I've recently started using Ubuntu 9.04 and it's nice, but I've had some graphics issues. 

Running the proprietary Nvidia driver version 180 - I can't have any windows full screen or the whole desktop freezes up and I have to do a hard reboot. 

Running the older version 173 windows don't completely freeze when maximized but they don't stretch correctly, if that makes any sense. And Firefox has bizarre parsing issues. 

Any ideas?

---

### Post by Liolikas on 2009-09-11
Conclusion proprietary sux. Joke. Try 185.

---

### Post by SigmaSanti on 2009-09-11
You can upgrade to Nvidia driver version 185, I had problems with my 8200 integrated card with nvidia driver 180. 
If you dont know how, here are some ways of doing this (I will assume that you have very little experience with this)

You can install the 185 driver or newer beta drivers(not recommended) by searching for a guide in the tutorial section of the forums (there is a good one but i cant find it right now i will post again if i find it). 

This way difficult for newer users since it requires command line instructions and related things that, while not difficult, can be confusing and may result in breaking your system.

Or you can add this ppa to your software sources, and get constant updates when a new driver becomes available. Again, something bad can happen but less of a chance, 

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

is a page were you can find info and directions for installing - here is an abreviated version
add this to your software sources (if dont know search it)

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main 


then download the key on the previous webpage (look at Signing Key) and download that file, or the file linked on the next page (i dont know, link was not working for me at time)

then update and go to the hardware driver install window and you should have a new option for 185

If you have any questions, at all, then just ask
I know how frustrating graphics drivers are and spent almost a month trying to get something similar to your problem fixed. There are people better then me at explaining this and hopefully they will post and correct all of the errors i might have made in my post (spelling and punctuation not included) I just wanted to point you in the right direction real quick, so you now have some possible fixes.
Good luck

---

### Post by sauma on 2009-09-12
Well that was easy. No more weird firefox problems and no more full screen freezing. Thanks!

---

### Post by SigmaSanti on 2009-09-12
It worked?
Great glad to help.

---

