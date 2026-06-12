---
title: "A PDF reader that speaks the text like Adobe Reader 7.0"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by andrew222 on 2008-12-29
Today I was using a relative's laptop which has Vista and was reading an eBook with Adobe Reader, I discovered the option to have the text read to the user ( like /gps talking to a driver ).  I love it!!

  Can Adobe Reader 7.0 run on Ubuntu and have the text read to us? If not is there an open source equivilent with this capability?

---

### Post by TheLions on 2009-01-02
yes you can install Adobe Reader to Ubuntu and yes it can read text a loud.:D
pick you language and download it:
[http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

if you have x32 version of Ubuntu just install it with Package manager otherwise 

type this in terminal (i assume that you downloaded Reader to Desktop)
```
cd ~/Desktop
sudo dpkg --force-architecture -i <packagename>
```

---

