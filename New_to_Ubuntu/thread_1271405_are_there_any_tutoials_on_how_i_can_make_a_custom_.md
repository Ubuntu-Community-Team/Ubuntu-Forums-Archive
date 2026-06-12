---
title: "are there any tutoials on how i can make a custom ubuntu dvd?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by cosmoshell on 2009-09-20
are there any tutoials on how i can make a custom ubuntu dvd from scratch? no tutorials that ive found has shown me what the dvd needs to have the extra install options that the dvds have.

---

### Post by ankspo71 on 2009-09-20
Hi,

Doesn't Ubuntu have a suitable DVD that you could use as your project? I think they have DVDs for version 8.10, and I think they have DVDs that includes alternate/additional languages.

Try remastersys to build an ISO. I found it very easy to create my own personalized ubuntu, and it uses the original graphical installer that comes with the same Ubuntu release. I believe it downloads the installer from Ubuntu.

Creating the ISO was the easy part for me. However, I'm stumped on how to create system-wide start menu entries, so I put it off for now. Then I have to figure out how to display all extended ASCII codes, which is probably a package I overlooked somewhere. Maybe I will work on it after Karmic is released. As far as tutorials go, I haven't found any that suit me. Instead I install the mini Ubuntu CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and download only the packages I want. Then install remastersys, and create the custom ISO. The mini cd has no desktop to work from, so it requires some experience with apt-get by command line (or aptitude, but I haven't tried that way yet). If you require the DVD version installer, then it's probably best to work from a DVD version of Ubuntu. Modifying an installer probably requires modifying and compiling the source packages, which I don't know how to do. 

So if you haven't tried remastersys yet, or haven't attempted to create an ubuntu based/debian based cd/dvd yet, give it a try. 
I hope this gives you a starting point to work from.
James

---

### Post by linux_tech on 2009-09-20
Here is a How-To on Customizing your Ubuntu Live CD -
[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)

---

### Post by ankspo71 on 2009-09-21
And here is another...
[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

