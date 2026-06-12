---
title: "cannot upload to file hosting sites like mediafire"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by That Person on 2009-05-31
when i try to upload a file to any file hosting site,
example:megaupload, mediafire,
mozilla freezes and i have to close it,and not able to upload the file(s) to the site.
Version of Mozilla:3.0.10
i need help with this problem.I dont know why it does it.
To see the pics and not have o download 'em, just right click and open in new tab.

---

### Post by nhasian on 2009-05-31
Hello That Person,

i just created an account on mediafire just to test the upload that you were having problems with.  here's the 40 megabyte photo of mars from the phoenix lander i just uploaded.  it looks like my backyard here in Arizona.

[http://www.mediafire.com/?sharekey=03118185f334c615d8f14848abf485dde04e75f6e8ebb871](http://www.mediafire.com/?sharekey=03118185f334c615d8f14848abf485dde04e75f6e8ebb871)

I used the regular upload tool but i should point out that i have installed sun's java 6.  that may be why it worked for me and not for you.  alternatively you may want to try their basic uploader tool instead.

---

### Post by bacardiandwatermelon on 2009-05-31
Same thing happens to me, but if you let it do its thing it still works :-)

---

### Post by That Person on 2009-05-31
I have just installed Sun Java 6 Runtime and Sun Java 6 broswer plugin and still get the freeze, guess i have to stick to the basic uploader

---

### Post by kostkon on 2009-05-31
> **That Person said:**
> I have just installed Sun Java 6 Runtime and Sun Java 6 broswer plugin and still get the freeze, guess i have to stick to the basic uploader
Did you set it to be the defautl jvm in your system? To do it, open a terminal and give:
```
sudo update-java-alternatives -s java-6-sun
```
restart firefox and then check if the advanced uploader now works.

Hope that helps.

---

