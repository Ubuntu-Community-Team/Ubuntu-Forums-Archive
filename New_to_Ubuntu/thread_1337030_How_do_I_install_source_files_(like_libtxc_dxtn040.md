---
title: "How do I install source files (like libtxc_dxtn040524.tar.gz)?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Dimitri_Sumlanacht on 2009-11-25
I'm new to Ubuntu, Linux and coding in general and I have no idea how to install this source file.  Like how to "Make" "Make Install" as I read somewhere else.  Please, I need this in the simplest step by step instructions possible.  The thing I am trying to install is from this website [http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html) to get certain videogames to work.  Apparently my video card lacks something necessary to run certain video games and I read on WineHQ that this will work.

Please remember to keep this step by step, as if you were trying to teach a five year old.

Thank you very much! :D

---

### Post by mlentink on 2009-11-25
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by Mr. Devil on 2009-11-25
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) - let us know if there's anything you don't understand.

---

### Post by Dimitri_Sumlanacht on 2009-11-25
alright, so I am a bit stuck.  I got to step 3 in the Ubuntu compilingeasyhowto tutorial and I'm not quite sure what it means when it says apt-file or what to do from there.  At this point it all turned in to gibberish for me.

---

### Post by Mr. Devil on 2009-11-25
> **Dimitri_Sumlanacht said:**
> alright, so I am a bit stuck.  I got to step 3 in the Ubuntu compilingeasyhowto tutorial and I'm not quite sure what it means when it says apt-file or what to do from there.  At this point it all turned in to gibberish for me.

Unless ./configure returns missing dependencies, you can skip that step.

---

### Post by Dimitri_Sumlanacht on 2009-11-25
ok, so how do i specify in terminal which files I wish to "make"?

---

### Post by dgoosens on 2009-11-25
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Installing_a_package_from_source](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Installing_a_package_from_source)

---

### Post by Mr. Devil on 2009-11-25
Standard compilation:
```
cd <source_directory>
./configure
make
sudo make install
```

By the way, check [this guide]("http://www.zdziarski.com/papers/s3tc.html") - might be exactly what you are looking for.

---

