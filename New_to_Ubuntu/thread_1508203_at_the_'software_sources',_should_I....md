---
title: "at the 'software sources', should I..."
date: 2010-06-12
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-06-12
Hi
I recently noticed that I dont have the Java Runtime Environment installed on Lucid (Ubuntu stopped working since I upgraded to 10.04), so when searching for info on JRE, I found a suggestion to include this on 'software sources'...
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid
Although, do not know how to... and dont know if it is actually recommendable.

for any ideas... many thanks
b.

---

### Post by SlidingHorn on 2010-06-12
for most java-based apps, the restricted extras tend to work just fine...if not you can get the actual version from Sun directly.  For now, try:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by DougieFresh4U on 2010-06-12
I added it to my sources list and updated and was able to get Java.
Don't think it will harm MY system
It's in the 'partner' repo now.

---

### Post by mikewhatever on 2010-06-12
Check out the link below.
[http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html)

---

### Post by DougieFresh4U on 2010-06-12
> **mikewhatever said:**
> Check out the link below.
[http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html)

Thank you for making it more clear. :)

---

### Post by bilbo.san on 2010-06-13
Thanks!!!
I got it working with JDK!

@mikewhatever: thanks for the link, that solved it!

---

