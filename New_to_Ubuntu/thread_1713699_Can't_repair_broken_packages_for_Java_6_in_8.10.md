---
title: "Can't repair broken packages for Java 6 in 8.10"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by grey1beard on 2011-03-24
I need to run Java applets(?) in my system that needs to have 8.10 installed, not later.
Having read the community page on Java, I have downloaded and installed the java 6 runtime via Applications,Add/Remove, and then tried to obtain the icedtea6-plugin by the same route.
This results in a "Fix broken packages first" message.

I then ran "sudo apt-get install -f" in Terminal, as per various threads I've read on this general problem, but that appears to have had no effect, in that I still get the same message.

If someone could guide me out of the hole I'm stuck in, I'd be most grateful.

John

---

### Post by mikewhatever on 2011-03-24
If you've downloaded and installed java6 runtime, why get another version afterwords?

---

### Post by TBABill on 2011-03-24
What's the point of having icedtea plugin? If you have the Sun Java plugin you can actually be creating a conflict, plus you need the rest of open java to support icedtea plugin if I'm not mistaken.

---

### Post by grey1beard on 2011-03-24
"Just following orders" :)

> To run Java applets using the plugin corresponding to OpenJDK, you must install the package icedtea6-plugin .

Some Java applications may experience problems or worse problems under other JREs. Trial may be necessary. 

from the Java community page [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

John

---

### Post by wojox on 2011-03-24
I would download from Sun and install and purge what you have. 8.10 is EOL so I don't know how you got that to install in the first place.

---

### Post by TBABill on 2011-03-24
That's probably because Ubuntu comes stock with Open JDK, but I always remove it and the icedtea plugin and install Sun Java because it works on all Java enabled sites I visit, when open java does not. It's pretty much a one or the other thing I believe, not a need for both.

---

### Post by grey1beard on 2011-03-24
I've just tried the same route that I took before, ie I followed the link to the applet that I'm trying to run, and then to the Sun Java site that told me there was something wrong with my installation of java.
However, this time a banner message from Firefox(?) appeared asking if I wanted to repair the icedtea plugin.
Following orders, all is now well, and I can run the applet.

Sorry to have wasted your time, but it may help anyone following behind.
John

---

### Post by grey1beard on 2011-03-24
> **wojox said:**
> ........ 8.10 is EOL so I don't know how you got that to install in the first place.

"There are more things in heaven and hell, Horatio....."

I need a system that can run 8.10 for good reasons to do with latency issues and machine control.
8.10 is "jus perfick" for this set up of EMC2 on the desktop that is controlling my cnc machine.

John

---

