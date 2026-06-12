---
title: "Gwibber /memenu/empathy"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by vivek40 on 2010-05-02
Hii! My Memenu,gwibber,empathy .. all these three dont work properly at all. Gwibber is just too buggy it is not working at all. I have always prefferred pidgin to empathy ... Well now I would want to integrate pidgin and tweetdeck with memenu, and remove gwibber and empathy from it... can someone please help...or if it can be done at all.

Regards
Vivek

---

### Post by vivek40 on 2010-05-03
bump!

---

### Post by madjr on 2010-05-03
actually i find gwibber good, am using it with facebook

it's little confusing to setup at first

[http://www.omgubuntu.co.uk/2010/04/dont-like-ubuntu-application-swap-it.html](http://www.omgubuntu.co.uk/2010/04/dont-like-ubuntu-application-swap-it.html)

---

### Post by dionysius on 2010-05-03
Empathy can easily be replaced with Pidgin

```
sudo apt-get remove empathy
```

Then 

```
sudo apt-get install pidgin
```

If you search for Pidgin in Synaptic it will return a long list of plug-ins and other useful things, too. 


I don't know whether it integrates with the Me Menu, but for Twitter you could have a look at twitux - [http://sourceforge.net/projects/twitux/](http://sourceforge.net/projects/twitux/)
It's in the repositories:

```
sudo apt-get install twitux
```

---

### Post by madjr on 2010-05-03
you should ask for integration of deck as feature request

[https://wiki.ubuntu.com/MeMenu](https://wiki.ubuntu.com/MeMenu)

the author of tweetdeck could also be interested, is 2 way street, check at their forum

---

