---
title: "Ubuntu Firefox : Keyboard shortcut for Back &amp; PDF Loader"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by just_ken_here on 2011-03-17
Hi

I used to be Windows user.

I had firefox on windows and the back button was just [backspace]
I searched online and found : [http://www.mouserunner.com/FF_Shortcuts1Printable.html](http://www.mouserunner.com/FF_Shortcuts1Printable.html)

I liked the Windows [backspace] shortcut since I dont have to press 2 things..
Is there any way to modify the shorcuts ?

----------------------------------------------------------------------------

In windows my firefox has automatic .pdf viewer from adobe..

So I can view .pdf documents directly on the browser without having to saving the .pdf into temp or downloading it.

My default .pdf viewer is evince.. Is there a way for evince to do like adobe did to my firefox in windows.

I am not sure if adobe is in my ubuntu system.

So far I have enjoyed ubuntu 10.10, but these two things would make life closer to perfect.

Thanks for the help.

---

### Post by xptional on 2011-03-18
yes you can do it . as I have done on my system with Ubunut 10.10
run
```
sudo apt-get install adobereader
```

after completion, restart the system. I hope you will find adobereader in your firefox :)

---

### Post by just_ken_here on 2011-03-20
Yeah.. there is actually adobe reader on Ubuntu software center too.

thx though
=}

---

### Post by mikewhatever on 2011-03-20
To set the BackSpace button the way it was on Windows, type [noparse]about:config[/noparse] in the address bar, then search for **browser.backspace_action** and change its value to 0.

Edit: I believe Adobe Reader in Ubuntu goes under the name of Acroread and lives in the Ubuntu partner repository.
[http://www.liberiangeek.net/2010/09/install-adobe-reader-acroread-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-adobe-reader-acroread-ubuntu-10-10-maverick-meerkat/)

---

### Post by alexis44 on 2011-03-20
When you mentioned Backspace, I was wondering what you meant.  With WIndows, it would take you back to the previous page in the Firefox browser.  In a Linux system it's different.  It doesn't.  You have to type about:config in the address bar.  From there you would see browser. backspace-action   The default is 2.  You have to change it to "0".  That will change it so you can backspace in your Firefox to the previous page.  If that's not what you meant, then, you'll have to be more specific.

---

### Post by alexis44 on 2011-03-20
I was a minute or two too late. :)

---

