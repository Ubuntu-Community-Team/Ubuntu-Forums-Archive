---
title: "Installing JAVA 6"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by bmtlol on 2011-02-13
Hi, I just installed a clean version of Ubuntu Desktop Edition and installed WINE. I want to play Minecraft, but I can't figure out how to install Java!

please help ;(

---

### Post by Miyavix3 on 2011-02-13
Identify your architecture (32bit or 64bit), then download.

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com)

When I say <TAB> I mean press the tab button

Open up the terminal
```

cd to where you downloaded the file
$ mkdir java_temp
$ mv jre<TAB> java_temp
$ cd java_temp
$ chmod +x jre*
$ ./jre<TAB>

$ sudo mv jre1.6.0_23 /usr/
$ export PATH=$PATH:/usr/jre1.6.0_23/bin
```

I haven't used ubuntu in a while; there could be an easier method so stick around.

Edit:
You can do this, which sounds easier.
[http://ubuntuforums.org/showpost.php?p=10452752&postcount=5](http://ubuntuforums.org/showpost.php?p=10452752&postcount=5)

---

