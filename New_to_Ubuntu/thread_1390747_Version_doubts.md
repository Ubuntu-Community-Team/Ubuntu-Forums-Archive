---
title: "Version doubts?"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by kapmsd on 2010-01-26
Hi guys!!
I downloaded the source code of apt using apt-get source apt.
The folder I got has the name apt-0.7.6ubuntu13.
But the version of apt my system has is 0.7.9ubuntu17.2 (found using dpkg -p apt).
Why I dint get the source code of apt currently in my system?

---

### Post by cariboo on 2010-01-26
Have you got all the repositories enabled in Software Sources?

You can get the source package you are looking for [here]("http://packages.ubuntu.com/search?keywords=apt&searchon=sourcenames&suite=all&section=all").

---

### Post by ibuclaw on 2010-01-26
Not just the repositories, but the Sources of those repositories too...

In /etc/apt/sources.list, you can determine these lines as they begin with **deb-src**.

Regards

---

### Post by kapmsd on 2010-01-27
Thanks a lot guys!!
I dint enable two urls in third party softwares tab in software sources.
Now I got the correct version of apt source code O:)

---

