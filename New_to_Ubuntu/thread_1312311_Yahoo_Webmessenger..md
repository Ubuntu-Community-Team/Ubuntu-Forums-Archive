---
title: "Yahoo Webmessenger."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by viladkarab on 2009-11-03
Hello, 

I have recently updated my system from 8.10 to 9.04. Now, I am unable to load yahoo webmessenger in my firefox browser window. In 8.10, I never had this problem. What could have gone wrong? When I enter [http://in.webmessenger.yahoo.com/](http://in.webmessenger.yahoo.com/),  Screen just remains blue blank, with nothing there. Is any plug in etc. missing? 

Kindly help. 


Aniruddha Viladkar:(

---

### Post by konqueror7 on 2009-11-03
try reinstalling flash-player again, and go to 'web.im'...see if that works...

---

### Post by viladkarab on 2009-11-03
I did the same, with no use. Now what? Have I forgotten to load any extra plug ins, add ons etc ?

Thanks.

---

### Post by NickJones on 2009-11-03
Try using Pidgin instead of Webmessenger!

---

### Post by viladkarab on 2009-11-03
I am using Pidgin only. But this is also important for me. Thats why I am asking. 

Regards.

---

### Post by desperado665 on 2009-11-03
Have you installed the restricted extras package? I just checked your web link and it seems to be flash driven, but works fine for me.

Enable the medibuntu repositories by running these in a terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
and
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Once you have the medibuntu repositories enabled, try running in a terminal ```
 sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by viladkarab on 2009-11-03
I did as per your instructions and loaded ubuntu restricted packages, but no use. 

Regards.

---

### Post by konqueror7 on 2009-11-03
have you considered maybe the fault is from the region? the servers? its hard to identify the issue since its not in our reach anymore...

why not just use pidgin instead if it work, you can also login to multiple accounts there...

---

