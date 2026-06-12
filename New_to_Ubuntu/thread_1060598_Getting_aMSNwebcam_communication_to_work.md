---
title: "Getting aMSN/webcam communication to work"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by tomsax on 2009-02-04
My wife used to use Messenger to communicate with lots of her friends and family, using webcam and audio, communicating with people who use Messenger and would probably not change to anything else.

On a suggestion on this forum I have installed aMSN which is meant to &#7765;rovide the same funtionality.

Unfortunately I can't get the webcam to work properly.  Sporadically they have been able to see us and on other occasions we have seen them but not together.  Also we have never been able to hear them or them hear us.

I'm not sure if my laptop is just too old.  I used to have rather slightly disjointed webcam and audio when I had WindowsXP on the same computer so I am surprised Xubuntu can't at least offer the same or better service.

If I can't sort this out it looks like I'll have to abandon Xubuntu and go back to Windows which would be a shame as I like Xubuntu and it works fine or quicker than Windows XP for web surfing, which is about the only other thing we use the laptop for.

---

### Post by Temposs on 2009-02-04
hi tom,
   You should detail:
1) Which version of Xubuntu are you using?
2) What model webcam do you have?
3) Try installing a program(from Add/Remove) called Cheese and test the webcam on that. What parts work?

---

### Post by tomsax on 2009-02-04
> **Temposs said:**
> hi tom,
   You should detail:
1) Which version of Xubuntu are you using?
2) What model webcam do you have?
3) Try installing a program(from Add/Remove) called Cheese and test the webcam on that. What parts work?

1) Good question.  I can't remember and can't find an "about Xubuntu" icon or whatever.  I downloaded the latest and installed around a month and a half ago so I think its the latest ' 8.10.

2) Another good question!  It's got "Creative" written on the side but that's it!  

3) It works fine in Cheese and also in the aMSN webcam set up function.  It sometimes works when we communicate with someone but very infrequently and it has never worked both ways, ie us seeing them on webcam and them seeing us.

---

### Post by Temposs on 2009-02-04
What kind of internet connection do you have?

---

### Post by tomsax on 2009-02-05
wireless

---

### Post by Temposs on 2009-02-05
Hmm, wireless isn't exactly a kind of internet connection. Your choices are dial-up, dsl, cable, or satellite, being the most common consumer connections.

Also, please paste the output of the terminal command:

```
lsusb
```

---

### Post by tomsax on 2009-02-05
Sorry Temposs. I replied quickly this morning and seems I didn't actually know what you were asking.

It is a dsl connection, that is via the telephone.

I'll run that command in Terminal when I get home from work and post the results!

---

### Post by tomsax on 2009-02-05
Here's what I get


tom@tom-laptop:~$ lsusb
Bus 001 Device 002: ID 041e:4057 Creative Technology, Ltd Live! Cam Optia
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-laptop:~$ 



So I guess my webcam is being recognised.

---

### Post by Temposs on 2009-02-05
And importantly, it gives us the model(Creative Technology, Ltd Live! Cam Optia) of webcam that you have, so let's both google around and see if people have dealt with this webcam and amsn on ubuntu.

EDIT: Also, the device identifier is given as: 041e:4057
This gives us an identifier for this kind of webcam, which you can also google for.

---

### Post by tomsax on 2009-02-06
I&#7743; looking for clues on google.

I found a page which says which webcams work with Skype on linux

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

that says my webcame works fine with Works fine after installing the uvc (link) driver 

I go to the link and get this page  

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

which then says I can download from this page

[http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

on this page I have no idea on what I click on to get a download!

---

