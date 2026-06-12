---
title: "video driver problems"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by mapman88 on 2010-03-01
Hello, 

I have a driver problem with my graphics card. I _was_ using Ubuntu 9.10 32 bit. I was doing something or other and a message told me I needed to update my video driver. There were three choices so I chose version 185(recommended). After that, whenever I booted up my screen was flashing and blurry, and other odd things. Sometimes it would take a couple boots, or I would cycle power on my monitor to get logged in. Fast forward, I decided to go to Ubuntu 9.10 64 bit. My problem disappeared, but in 64 bit I was limited to 800 x 600 on my display. Searching the forums, I came up with a fix that suggested upgrade my nVidia driver. This time I chose version 1.73. The same problem came back, only worse. I barely got to a login screen, was able to deactivate the driver, rebooted, now I'm back to 800 x 600, but no other problems. Any ideas? thanks,

---

### Post by mapman88 on 2010-03-01
Bump, or
 
since I got no response, the answer must be in front of me.... I will keep looking

---

### Post by morrcahn on 2010-03-01
Try using the tty's (Ctrl+Alt+F1-6) when it is booted up as far as it goes. Once to one of them log in there and type

envyng -t

Follow the directions. That might work for you.

---

### Post by lyall on 2010-03-01
> **mapman88 said:**
> Hello, 

I have a driver problem with my graphics card. I _was_ using Ubuntu 9.10 32 bit. I was doing something or other and a message told me I needed to update my video driver. There were three choices so I chose version 185(recommended). After that, whenever I booted up my screen was flashing and blurry, and other odd things. Sometimes it would take a couple boots, or I would cycle power on my monitor to get logged in. Fast forward, I decided to go to Ubuntu 9.10 64 bit. My problem disappeared, but in 64 bit I was limited to 800 x 600 on my display. Searching the forums, I came up with a fix that suggested upgrade my nVidia driver. This time I chose version 1.73. The same problem came back, only worse. I barely got to a login screen, was able to deactivate the driver, rebooted, now I'm back to 800 x 600, but no other problems. Any ideas? thanks,

Hi mapman88

using the 32 bit should have worked just fine for you
but since you are having a problem or two

first start by look and the two following links

[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")
it does not show the GeForce 6100 in the listing, but it does show the GeForce 6 series

this link show how to use the BinaryDriverHowto
[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")

I help this helps you
it is a place to start
if not search the forums for your video card and you might found the answer you are looking for

I am still using the 32 bit ver.

good luck and have fun learning

---

