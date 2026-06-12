---
title: "Help - I can't ready any DVDs =("
date: 2010-01-05
forum: New to Ubuntu
---

### Post by LadySapphira on 2010-01-05
Version: Ubuntu Karmic Koala


I have typed in codes into the terminal for libdvdread4 and earlier versions too because at the time I didn't realize earlier ones were for earlier versions of ubuntu.

I have installed random gstream stuff from other articles hoping it would help.  I just can't get this to work...

This is important to me.  As a windows user wanting to switch to ubuntu, I fear I'll have to use my XP partition as my primary one

---

### Post by PRC09 on 2010-01-06
Hope this helps....

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Bright_View on 2010-01-06
I've always used the medibuntu repository to enable watching DVDs, and it has worked great.  Go to:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and follow their directions.  You'll be able to watch DVDs and install w32codecs or w64codecs depending on what you need.

Hope this helps!

---

### Post by HappyFeet on 2010-01-06
Very easy.

Just copy and paste the following into a terminal.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
enjoy your movies.

---

