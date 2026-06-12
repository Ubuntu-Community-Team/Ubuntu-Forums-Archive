---
title: "video plugin needed."
date: 2009-05-17
forum: New to Ubuntu
---

### Post by bob brazie on 2009-05-17
V9.04

When I try to play the video at [http://www.thepittsburghchannel.com/video/19461935/index.html](http://www.thepittsburghchannel.com/video/19461935/index.html)

and try to install a package as requested to view it I get this message:

No packages with requested plugins found.

Microsoft Media Service (MMS) protocol source.

I then try to open it for viewing in media player and the loop starts again. Can anyone suggest a solution so I can view this video?

Thanks in advance. Bob.

---

### Post by tuxxy on 2009-05-17
It runs fine here I wonder if you installed the correct codecs specifically the ubuntu-restricted-extras package and also VLC application will include some.

---

### Post by hatalar205 on 2009-05-17
Look at the link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
I think this will solve.

---

### Post by bob brazie on 2009-05-17
I added this line and it still is not working. Is that the step you were thinkg of?

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

---

### Post by bob brazie on 2009-05-17
Where might I find the ubuntu-restricted-extras package and also the VLC application?

---

### Post by bob brazie on 2009-05-18
I added:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

And i still cannot view the movie. Do you see anything else I could try?

---

### Post by perlluver on 2009-05-18
> **bob brazie said:**
> I added:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

And i still cannot view the movie. Do you see anything else I could try?

Also ```
sudo apt-get install w32codecs ubuntu-restricted-extras
```

---

### Post by Nixie Pixel on 2009-05-18
Hi Bob, my video tutorial should show you everything you need to know:

[http://www.youtube.com/watch?v=NT7urt5UcQg](http://www.youtube.com/watch?v=NT7urt5UcQg)

---

### Post by hatalar205 on 2009-05-20
> **Nixie Pixel said:**
> Hi Bob, my video tutorial should show you everything you need to know:

[http://www.youtube.com/watch?v=NT7urt5UcQg](http://www.youtube.com/watch?v=NT7urt5UcQg)

Wow! An amazing video. Good job. I think it will be very helpfull.

---

