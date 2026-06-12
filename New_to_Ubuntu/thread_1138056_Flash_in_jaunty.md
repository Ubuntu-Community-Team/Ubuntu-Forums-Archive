---
title: "Flash in jaunty"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-04-26
Hi,

I just installed jaunty in my system.. i wanted to install flash player in it.. so downloaded the deb file from the adobe website and tried to to install it.. but it says.. the depedancy "libcurl3" is not satisfied.. what should i do.. 
when i went to synaptic and made a search for libcurl3, it is not available in it...

what should i do to make the flash work in my system...

---

### Post by ScottBurnham on 2009-04-26
I just went to add/remove software and searched for Flash and the installed flash from there.

---

### Post by Efros on 2009-04-26
If its the 64 bit version of Jaunty try the tutorial here, it got my new installs working well.

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by talsemgeest on 2009-04-26
> **luckydeveloper said:**
> Hi,

I just installed jaunty in my system.. i wanted to install flash player in it.. so downloaded the deb file from the adobe website and tried to to install it.. but it says.. the depedancy "libcurl3" is not satisfied.. what should i do.. 
when i went to synaptic and made a search for libcurl3, it is not available in it...

what should i do to make the flash work in my system...
Also, the easiest way to get everything running smoothly, including flash, java, and video codecs is to install the package "ubuntu-restricted-extras". You can install it from the add/remove menu, or by typing into the terminal ```
sudo apt-get install ubuntu-restricted-extras
```

Hope this helps :)

---

### Post by 3rdalbum on 2009-04-26
You can just open up the Debian package in File Roller. You'll find three .tar.gz files inside it - open the "data.tar.gz". Inside this one will be a file that is the actual Flash plugin - drag that to the Firefox plugins directory and you're good to go.

---

### Post by presence1960 on 2009-04-26
> **Efros said:**
> If its the 64 bit version of Jaunty try the tutorial here, it got my new installs working well.

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

+1

Have used this for Hardy, Intrepid and now Jaunty with zero problems.

---

