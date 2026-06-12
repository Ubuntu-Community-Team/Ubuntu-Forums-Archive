---
title: "how to configure localepurge?"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Jouke S on 2011-02-25
Hey,

Since a day or two my terminal keeps insisting I configure localepurge. I however have no idea what I'm supposed to do exactly.

I think I understand the basic gist of configuring localepurge; localepurge wants me to delete unnecessary/redundant language packages.
I want to have my system in English (preferably British English), which files do I need to delete? 
I'm quite afraid of messing something up - especially because there's little to be found about the subject using google. 

Added a picture that shows my localepurge gui(still in terminal):
[IMG]http://img15.imageshack.us/img15/738/selection005b.png[/IMG]

Hope someone can help me!

---

### Post by jimmyjones on 2011-02-25
Found this wiki

[http://crunchbanglinux.org/wiki/howto/localepurge](http://crunchbanglinux.org/wiki/howto/localepurge)


Says  en_GB 



**

Under System > Administration > Language Support

I see an option for English(United Kingdom)


It's been a long time since I configured LP, to

en
en_US

---

### Post by Jouke S on 2011-02-25
> **jimmyjones said:**
> Found this wiki

[http://crunchbanglinux.org/wiki/howto/localepurge](http://crunchbanglinux.org/wiki/howto/localepurge)


Says  en_GB 



**

Under System > Administration > Language Support

I see an option for English(United Kingdom)


It's been a long time since I configured LP, to

en
en_US

Thanks, that solved it

---

### Post by Rytron on 2012-02-22
> **Jouke S said:**
> Hey,

Since a day or two my terminal keeps insisting I configure localepurge. I however have no idea what I'm supposed to do exactly.

I think I understand the basic gist of configuring localepurge; localepurge wants me to delete unnecessary/redundant language packages.
I want to have my system in English (preferably British English), which files do I need to delete? 
I'm quite afraid of messing something up - especially because there's little to be found about the subject using google. 

Added a picture that shows my localepurge gui(still in terminal):
[IMG]http://img15.imageshack.us/img15/738/selection005b.png[/IMG]

Hope someone can help me!

Do you put an * next to the ones you want to keep or get rid of? How do you launch this window from the terminal?

---

### Post by oldos2er on 2012-02-22
Been awhile since I installed localepurge, but I think its configuration screen comes up either at the time it's installed or the first time it's run. Mark (with asterisk) the language packs you want to keep.

Since this thread is a year old, I'm going to close it. If you have further questions please start a new thread.

---

