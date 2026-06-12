---
title: "ubuntu acting wierd"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by dpreed77 on 2009-07-20
Hi, I am fairly new to ubuntu (feb 09) and my T400 Think pad has 9.04 on it. Suddenly I have 2 problems..
1. when i start unikey (a Vietnamese typing program) my network icon disappears and I loose my connection. 
2. My webcam stopped working last week. 

I have not altered my system other than updating. I know enough to know not to mess with the terminal if I am not sure what I am doing! However, I am open to learning. Can someone please help me trouble shoot these problems? 
Thanks in advance!!

---

### Post by y-lee on 2009-07-20
Don't  know if i could be of any help but more information  would help. What do you mean by '*ntork icon*', do you mean your net work icon? And how did you install the **unikey** program? And has this network problem always happened since you installed **unikey** or is it something new? And lastly what sort of web cam do you have, manufacturer model number and so on? Is it a usb web cam?

---

### Post by dpreed77 on 2009-07-20
Hi Sorry for the typo! Yes my network icon on the right upper corner. I lose my internet connection. Unikey worked fine previously. I am sure because I remember using it to look-up words online. I used the gdebi (i think this is what it is called) package manager. So I downloaded the deb file from the unikey website, saved it to my desktop and used the package installer to install. Unikey itself works fine, but I am not sure why it would affect the network.
As for the webcam, now it is working again. I am not sure what happened, but it definitely was not working last week (Skype)
Thanks for the reply!I hope that this information helps.

---

### Post by y-lee on 2009-07-20
When the network icon disappears, try to restart it by opening a terminal and then type

```
nm-applet
```

Did it restart? And were you able to reconnect? Note that if it does restart this way then closing the terminal will kill the network icon and you will lose your connection.

EDIT
Press the key combination Alt+F2. This opens the Run Application window. now type nm-applet. this way the applet will stay ;)

---

### Post by dpreed77 on 2009-07-20
The command nm-applet works. I am able to connect to the internet and use Unikey at the same time. 
Any ideas on why this application (Unikey) would kill the network manager?

EDIT
The alt+F2 command also works. Thanks so much!

---

### Post by y-lee on 2009-07-20
> **dpreed77 said:**
> The command nm-applet works. I am able to connect to the internet and use Unikey at the same time.


Great, glad it worked :D

> **dpreed77 said:**
> 
Any ideas on why this application (Unikey) would kill the network manager?

EDIT
The alt+F2 command also works. Thanks so much!

And i have no idea why Unikey killed nm-applet, it might be a bug in Unikey and I would at least tell the developers of the program about your experience. ... But basically I don't know :confused:

---

