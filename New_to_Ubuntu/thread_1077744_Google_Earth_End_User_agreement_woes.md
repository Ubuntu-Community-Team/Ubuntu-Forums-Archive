---
title: "Google Earth End User agreement woes"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Thacker on 2009-02-22
Installing Google Earth in Intrepid using the Terminal, have got as far as the End User Agreement and am now stuck1 How on earth (no pun intended) do I agree? clicking on 'OK' does nothing and there's nothing in the installation guide I was using that even mentions it?
On top of all this during the install I noticed that loads, and I mean loads, of libraries were being removed, including Gnome desktop stuff.
How do I reinstall al the libraries that have gone or is this all part and parcel of the Google Earth Install?

---

### Post by steveneddy on 2009-02-22
I thought you could install that from Synaptic?

Are you installing a version that you DLed?

---

### Post by mkvnmtr on 2009-02-22
Try using the arrow keys to highlight ok and then click on enter.

---

### Post by bodhi.zazen on 2009-02-22
Or the tab key ;)

---

### Post by Thacker on 2009-02-22
Thanks for replying- I used:    sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

    sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
and then: sudo aptitude install googleearth-4.3

and then no matter what I tried couldn't highlight the 'ok'

---

### Post by Thacker on 2009-02-22
Have installed with synaptic now with no problems - but found my Nvidia graphics driver was no more! So God knows how much more was removed - why didn't I do it the easy way in the first place!!

---

### Post by donaldt on 2009-02-22
I have Google Earth installed, but when I launch it I get 10 seconds of the program and then it disappears from the screen.  Is this a video driver issue?  I have NVidia GeForce 8400M GS on my portable Sony.

---

