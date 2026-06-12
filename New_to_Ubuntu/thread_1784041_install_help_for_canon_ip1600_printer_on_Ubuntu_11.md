---
title: "install help for canon ip1600 printer on Ubuntu 11.04"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Beyondthe48 on 2011-06-16
saw a few posts from a few years ago, but they were using older forms of ubuntu. canon no longer has the 2200 drivers on the site.

a walkthru would be most appreciated here. just got ubuntu after 20 years of windows torture.:D

---

### Post by Beyondthe48 on 2011-06-22
bump

---

### Post by doctorbighands on 2011-06-23
Hello, and welcome to Linux, a.k.a. Club Cool.

I think I found the driver you need. Look here: [http://software.canon-europe.com/software/0024301.asp?model=](http://software.canon-europe.com/software/0024301.asp?model=)

If you use that driver and follow the instructions on [this page]("http://ubuntuforums.org/showpost.php?p=6276893&postcount=1") (minus step 2, of course, since you'll already have it), you should be good to go. The only exception is the very last step, which has changed with the times. It should be this instead:

```
sudo service cups restart
```

I hope that helps! :)

---

### Post by A.dela on 2011-08-31
Actually it helped me, so thanks a lot!! Not perfect, anyway: now it recognises the printer but all I try to print keeps in an eternal queue... surfing for an answer rigth now

---

### Post by pmalvr on 2011-10-16
I had my canon pixma iP1600 printer working well in Ubuntu 11.04 (I followed the answer wrote [here ]("http://askubuntu.com/questions/41615/how-to-install-canon-pixma-ip1600")to accomplish that).

Then I upgraded my Ubuntu to version 11.10 but the upgrade went wrong and I was forced to reinstall Ubuntu 11.10 from scratch. After that, I tried to install my printer just as I did before but I wasn't able to print with success anymore.

I reinstalled Ubuntu 11.10 a second time, this time without encrypting my home folder and I was able to print successfully. To take any thoughts I reinstalled Ubuntu 11.10 a third time and again I could not print anything.

So, can someone help me to put my printer working in Ubuntu 11.10 with my home folder encrypted?

Thanks in advance.

---

### Post by dougw4 on 2011-11-09
I finally got my Canon Pixma ip1600 to work with Ubuntu 11.10. I basically followed the instructions located here: 

[http://askubuntu.com/questions/41615/how-to-install-canon-pixma-ip1600](http://askubuntu.com/questions/41615/how-to-install-canon-pixma-ip1600)

but with one exception. I reinstalled my ip1600 using the window titled "Printing - localhost". During the install process I was given the option to provide a PPD file. I told it to use: 

/usr/share/cups/model/canonip2200.ppd 

which I had previously modified using the instructions found at the link above.

Doug Witmer

---

### Post by pmalvr on 2011-11-10
And do you have your home folder encrypted? I'm asking this because I installed my printer just like you but I can't print if my home is encrypted.

---

### Post by dougw4 on 2011-11-10
No, My home folder is not encrypted.

---

### Post by pmalvr on 2011-11-10
> **dougw4 said:**
> No, My home folder is not encrypted.

Thanks for your reply. :)

Unfortunately this bug still persists for me. :(

---

