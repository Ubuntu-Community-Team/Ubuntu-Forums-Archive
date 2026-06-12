---
title: "web server root and subdirectories"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by plditallo on 2009-12-30
Hi Techies--
I just downloaded a Ubuntu LAMP jumpbox to work with on vmware's player. This is waaayyy cool!:-)  I have a php voice app i want to move over from one of my other servers. I did this--creating a subdirectory tree under the /var/www/ web server root. So i have this app sitting under /var/www/voice/demo  . I want to be able to call this demo up in a browser with the url:

[http://MetroLAMPDev/voice/demo/index.html](http://MetroLAMPDev/voice/demo/index.html)  

or 

[http://192.168.2.8/voice/demo/index.html](http://192.168.2.8/voice/demo/index.html)

...but the page won't come up.  :sad:

However, if I type:

[http://MetroLAMPDev/](http://MetroLAMPDev/)

or

[http://192.168.2.8/](http://192.168.2.8/)

 the default site server index page does come up! :razz:  

I'd like to leave the web server root directory for the full blown version of the app later--but-- still be able to access the demo app under a subdirectory tree.

Any advice on how I can set this up?

---

### Post by halitech on 2009-12-30
did you confirm there is an index.html file in that folder?

---

