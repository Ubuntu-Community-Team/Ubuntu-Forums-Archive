---
title: "http:// goes to www.. ???"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by zafzen on 2009-12-15
Hi Everybody! I am a newbie to Ubuntu and I recently installed a server on which I have put a webpage.. I can access it from other machines running windows by typing [http://lampserver/](http://lampserver/).. etc but typing the same on my Ubuntu notebook takes me to [www.lampserver.com]("http://www.lampserver.com")

Why is that? I tried to clear DNS cache.. still :(

Any help will be greatly appreciated!!

Zafar,

---

### Post by llamabr on 2009-12-15
You mean other windows boxes on the same network, or in the same house?

The reason that firefox forwards you to lampserver.com is because of your dns settings.  This is a firefox setting, since in firefox, it treats something typed into the location bar as a google "I'm feeling lucky".

What behavior are you hoping to see?  Why do you want to see the webpage by typing this?  The sorts of changes you'll need to make to dns will make many differences, and you can easily see this webpage by typing the ip address.

---

### Post by zafzen on 2009-12-18
Thanks! I solved the issue temporarily by using ifconfig and directly typing the ip address. 

Is it necessary to have the common server on static ip??

---

### Post by joes7 on 2009-12-18
Oh, DNS settings can be annoying. Cheers!

---

### Post by Extract_Here on 2009-12-19
nice solution

---

