---
title: "Netgear MA101 and Internet Routing"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by soslack on 2005-04-17
Has anyone gotten MA101 to work with Hoary?  I tried the following:

```
sudo apt-get install at76c503a-source
``` 

and it return the message "Couldn't find package at76c503a-source"

Do I need to edit my /etc/apt/sources.list? If so how exactly?

Im trying to get my desktop to be an internet router.  My PCI eth0 is the internet portal and I want eth1 (MA101) to be the local.

Any help is greatly appreciated thank you.

---

### Post by {silver} on 2005-04-18
[QUOTE=soslack]Has anyone gotten MA101 to work with Hoary? [/QUOTE]  

Someone has got it working with the ndiswrapper: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

>  ```
sudo apt-get install at76c503a-source
``` 

and it return the message "Couldn't find package at76c503a-source" 

Make sure that you use apt-cache search blah so you are not just stabbing in the dark.

---

