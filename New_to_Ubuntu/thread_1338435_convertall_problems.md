---
title: "convertall problems"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-11-26
just installed convertall there and i cant seem to use it i know that it will be something very basic that i am overlooking but how do i actually convert one thing to another. is there a button to press because all that shows up at the bottom left corner is ' calculating ' which it never seems to be able to do, i can't even get it to convert from US gallons to imperial gallons any ideas
thanks in advance.

---

### Post by abcuser on 2009-11-26
pendulum101, I haven't installed convertall, but there are plenty of converting tools on the web. Just write to Google like "convert us gallons imperial gallons" and you will get a converter like:
[http://www.csgnetwork.com/fuelvolumeconverter.html](http://www.csgnetwork.com/fuelvolumeconverter.html)

---

### Post by everythingsround on 2009-11-30
Don't know why it's crashing: some AttributeError 

[https://bugs.launchpad.net/ubuntu/+source/convertall/+bug/455001](https://bugs.launchpad.net/ubuntu/+source/convertall/+bug/455001)

Installing the latest from the authors site fixes the bug though:

[http://convertall.bellz.org/download.html](http://convertall.bellz.org/download.html)

---

### Post by sharobim on 2009-12-20
> **everythingsround said:**
> Don't know why it's crashing: some AttributeError 

[https://bugs.launchpad.net/ubuntu/+source/convertall/+bug/455001](https://bugs.launchpad.net/ubuntu/+source/convertall/+bug/455001)

Installing the latest from the authors site fixes the bug though:

[http://convertall.bellz.org/download.html](http://convertall.bellz.org/download.html)
I am a very ignorant Ubuntu user and found out that even when I downloaded the ConvertAll file to solve the freezing problem from the site I do not know what to do with it. 
Can you help? (NEED DETAILS) Thanks

---

### Post by Sir Jasper on 2009-12-20
Hi,

The picture below used the a Portable Windows version of ConvertAll via Wine.

[[img]http://i.imagehost.org/t/0987/convertall-1.jpg[/img]](http://i.imagehost.org/view/0987/convertall-1)

Type gallons in the top left box and choose US then type gallons in the top right box and choose imperial. Then type the number you want to convert in the box on the bottom left.

I assume your screen looks something like my picture?

My regards

---

### Post by Ubunthree on 2010-03-02
I believe I have the same issue; here is a shot of how it looks on my Karmic UNR screen:

[IMG]http://ubuntuforums.org/picture.php?albumid=1465&pictureid=5716[/IMG]

The from/to units are entered, but the conversion won't complete. The same thing happens on my desktop system, also Karmic. I've used ConvertAll on previous Ubuntu installations, and it's worked really well.

I also have no idea how to use whatever fix comes from the author's site.

EDIT...

Ok, I managed it finally, after finding a README.html file in the package:

1) Download convertall-0.4.3.tar.gz into a folder (I created ~/Downloads/convertall for this; replace that path in the following instructions with whatever folder you are using)

2) Open the .gz to extract the files (this creates the subfolder ~/Downloads/convertall/ConvertAll with the installation files in it)

3) Open a terminal and type: cd ~/Downloads/convertall/ConvertAll (or whichever folder your extraction ended up in)

4) sudo python install.py (After you give your password, this should install ConvertAll 0.4.3 for you)

5) If the terminal's last output is "Install complete," then it worked, and ConvertAll is updated and fixed. If it isn't, then your issue is different from mine.

Good luck!

Many thanks to everythingsround for the download link.

---

### Post by alvenegas on 2010-05-04
I am amazed that 3 yrs after this problem surfaced again.  ConvertAll was doing the same thing on KKoala.  I went to convertall site and d/l the newest version.  Installed it and it worked.

Thanks!

---

