---
title: "Acer Aspire One ZA3 microphone issue"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by james.exe on 2009-08-20
I know thisissue has already been resolved but the explanation is not exactly user friendly to newbies such as myself. I'm running UNR9.04 on my AAOZA3 11.6. In reference to the Aspire One community page: So far, getting the right resolution has been a no-brainer because all I had to do was copy/paste commands into the terminal. What frustrates me is how all of the guides assume that you have a profound knowledge of terminal commands and linux code in general. **To cut to the chase...** can someone tell me what I have to do, word-for-word, to get my microphone working. I don't exactly know what Download alsa-driver-1.0.20 from [www.alsa-project.org]("http://www.alsa-project.org") and *"compile it with ./configure --with-cards=all"* means. Believe me, I've google searched "how to compile software" and it has not been of any help.

---

### Post by james.exe on 2009-08-20
bump

---

### Post by LewRockwell on 2009-08-20
it might be of some additional value if you could include links directly to the pages you're following and referencing with respect to the corrective actions you desire to incorporate

.

---

### Post by running_rabbit07 on 2009-08-20
> **james.exe said:**
> bump

Is it plugged in?

[Try this thread.]("http://ubuntuforums.org/showthread.php?t=566524")
[And this one.]("http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html")
[And here?]("http://www.ocztechnologyforum.com/forum/showthread.php?t=56925")
[And here, too.]("http://ubuntuforums.org/showthread.php?t=963032")

---

### Post by LewRockwell on 2009-08-20
> **running_rabbit07 said:**
> Is it plugged in?

it's internal so it's doubtful that the trouble-call originator will completely disassemble his netbook to check the internal connections

fyi...

.

---

### Post by james.exe on 2009-08-20
I have been following this:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
[]("https://help.ubuntu.com/community/AspireOne#Notes%20about%20Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20desktop%20and%20UNR%20%28Netbook%20Remix%29")ctrl+F: AspireOne D250 Microphone Issue

Thanks for the replies, guys. I need all the help I can get. I don't want to have to switch back to Windows.

---

### Post by james.exe on 2009-08-21
Can anyone help?

---

### Post by james.exe on 2009-08-22
I was finally able to resolve the issue. This is for anyone else that may need the easy-to-follow instructions:
You need to download this file: [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2) and save it somewhere.
Next, open a terminal and change to the directory where you saved it. If you saved it on your desktop, you can do:
**cd ~/Desktop**
Next you can do:
**tar jxvf alsa-driver-1.0.20.tar.bz2**
This will unpack the driver files into a folder, probably named alsa-driver-1.0.20, you should change into that directory and then run the configure command:
**cd alsa-driver-1.0.20/ && ./configure --with-cards=all**
I had another look at that section of the guide and it seems to mis two more steps you run after the configure part, which is:
**make && sudo make install**

Note, the "&&" lets you execute another command after the first, eg: *command1 && command2*
I haven't bothered to setup the microphone for me, as the AspireOne's I have are used in a warehouse, but I'm fairly sure the steps I explained above should work. I assume that once it is installed, you may have to reboot.

---

