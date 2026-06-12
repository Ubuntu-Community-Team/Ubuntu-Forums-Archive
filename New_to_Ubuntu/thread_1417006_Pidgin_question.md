---
title: "Pidgin question"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by e.jejcic on 2010-02-26
Good afternoon to everybody:I am using Pidgin 2.5.5 and I would like to have Pidgin 2.6.6 that supports video and sound.I went to add/remove and found that Pidgin doesn·t actulice . So I went to the developer page to dwnnload 2.6.6 and they said there is no public key (??). My question is:where I get this information. Or better, how to do the upgrade. Thanks in advance from Eduardo.

---

### Post by Enigmapond on 2010-02-26
Add this to your software sources..
```
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main
```and this in the terminal 

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
```then update.


[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by e.jejcic on 2010-02-27
Good afternoon: I mr4eally appeciated the realy fast answer.I did what you told me, but in reversed order because in the 3rd. party sources tab it didn·t take take the writting. After severals changes I could write the thing OK. That is why I did first the thing on terminal.
When I update  shows that I need a working Internet connection (??) .So, I went to the URL that shows where to update and was working (?) Anyway I still no video nor audio. At help still shows Pidgin 2:5.5 So I am stuck and thinking if the order is important or not (making the changes you told me ).
I hope you understand all this (my mother tongue is not English). Thank you for your help. Regards from Eduardo.

---

