---
title: "Ubuntu 10.4 Skype crash loop"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by aquapan on 2010-05-20
I upgraded last night to 10.4 and Skype was in a crash loop whenever I tried to start an instant message. I found this link [http://www.jaytag.co.uk/blog/index.php/archives/skype-crashes-after-upgrade-to-ubuntu-10-04-lucid-lynx](http://www.jaytag.co.uk/blog/index.php/archives/skype-crashes-after-upgrade-to-ubuntu-10-04-lucid-lynx) on how to fix it.

I de-installed the old skype and downloaded the latest as per instructions.

Now I can't install it and the package installer spits out this result:

[IMG]http://www.myhappybody.com/Screenshot-165.jpg[/IMG]

I went into that directory thinking the png might be locking the install for whatever reason and deleted the file. 

I then re-ran the deb installer and got the same message.

Any hints on how to make this happen will be very appreciated as I use skype all the time.

Cheers
Aquapan

---

### Post by Zyrtec on 2010-05-20
Try something like

```
sudo apt-get purge skype
```

or

```
sudo apt-get purge skype-common
```


Then try reinstalling

---

### Post by aquapan on 2010-05-20
Zyrtec... you ROCK!

That worked perfectly ... the second command that is... the first one found nothing.

Must have been some detritus left from the last install.

THANK YOU SO MUCH!

have a great daY!

---

