---
title: "Can anyone help a complete ubuntu noob"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by chadbentley8 on 2008-12-28
i really didnt want to use vista for my new toshiba satellite l300.. so i took it off and added ubuntu. but ive never used it before. im having a bit of troubles. how do i find the drivers that came with windows and install them.. i really know nothing about this program but if someone wouldnt mind helping me out id really appreciate it... thank you 

ubuntu noob

---

### Post by Michael.Godawski on 2008-12-28
hey.

Brutal start. :P
 You cannot use the drivers you used with Windows in Linux.
But... most of your hardware should be recognized out of the box.

Go to System > Administration > Hardware Drivers
and see if there are any drivers inactive.
If yes try to activate them.

Are you having troubles with your display or your wlan?
Here are some basic starter pages which should help you:

[LIST]
[*][http://godawski.oxyhost.com/index.html](http://godawski.oxyhost.com/index.html)
[*][http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[*][https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[/LIST]

---

### Post by gettinoriginal on 2008-12-28
First, welcome to Ubuntu, these forums are great for any help you might need.  :P

In terminal (Applications > Accessories > Terminal), copy and paste these one at a time.

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

Then System > Admin > Hardware Drivers  let it seach for your driver, then activate it.

Then System > Pref > Appearance > Visual Effects  should be set to Extra or Custom.

---

### Post by chadbentley8 on 2009-01-16
Thanks you guys are great. i love the support here. i've been using ubuntu for a few weeks now and i've got most of the kinks worked out, im starting to really enjoy it. can't wait to learn more, maybe someday i'll be able to help someone  haha
thanks again.

---

### Post by NewJack on 2009-01-16
First off, Welcome to the Community!  Hope you like your experience here. Lots of good people that are willing to help out.  

Just a suggestion for you, if you find a solution to a problem please make sure to post it in your original help request thread.  It helps others that may have the same problem as you did.

---

### Post by chadbentley8 on 2009-01-16
i just did as these guys said, but if i were to find solutions else were i'll be sure to post them in the original thread, thanks.

---

