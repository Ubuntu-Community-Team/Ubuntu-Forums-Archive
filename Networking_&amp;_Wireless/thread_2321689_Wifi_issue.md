---
title: "Wifi issue"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by Rocky_Kilgore on 2016-04-23
I am new to unbuntu.   I installed 15.1 alongside windows  and it's not seeing my wireless card.  I installed the driver through  ndiswrapper and still not working.  I'm using rlt8190

---

### Post by wildmanne39 on 2016-04-23
Thread moved to its own thread!

Please do not post in someone else's thread, always start your own so your and the other person can get the best possible help. Aslo use a descriptive title to attract the attention of the right people to answer your question.
Thanks

---

### Post by Rocky_Kilgore on 2016-04-23
Ok.  Thanks I'm just new here

---

### Post by slickymaster on 2016-04-23
Rocky_kilgore, welcome to the forums.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. This will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Rocky_Kilgore on 2016-04-24
I don't see a download link for the script.   And how to u run a script.   I've never done that

---

### Post by Rocky_Kilgore on 2016-04-24
I don't see a download link for the script.   And how do I run the script?   I've never ran a script before

---

### Post by slickymaster on 2016-04-26
Open a terminal window and run the following commands:```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```This will download and run the script

---

### Post by Rocky_Kilgore on 2016-04-27
I can't.   My only source of Internet is wifi and it's not detecting my wireless card

---

### Post by slickymaster on 2016-04-27
If you cannot connect to the internet with your computer, including via a wired connection, you will have to move files between it and a computer connected to the internet.

---

### Post by Rocky_Kilgore on 2016-04-27
My only source of Internet is my phone as a Hotspot.   My computer has a wireless card in it.  It will connect when using windows but not when using ubuntu 15.1

---

### Post by jeremy31 on 2016-04-27
Rocky_Kilgore

[https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) using windows and save it as wireless-info, put it on a USB drive and transfer it to the Ubuntu partition in your home folder

Then boot into Ubuntu and open terminal then ```
chmod + x wireless-info && ./wireless-info
```

Then transfer the wireless-info.txt file to the USB drive and post the contents in code tags

---

### Post by Rocky_Kilgore on 2016-04-28
It is letting me save it as html.  How do I save it as txt?

---

### Post by jeremy31 on 2016-04-28
If the file looks correct, I would just rename it in Ubuntu and then run the other commands

---

### Post by Rocky_Kilgore on 2016-04-30
When I type in that command I get this
Chmod : cannot access ' x ' : no such file or directory 
Chmod : cannot access ' wireless-info ' no such file or directory 
I have the txt file saved in my home folder

---

### Post by howefield on 2016-04-30
> **Rocky_Kilgore said:**
> When I type in that command I get this

Try it again without the space between "+" and "x"

```
chmod +x wireless-info && ./wireless-info
```

---

