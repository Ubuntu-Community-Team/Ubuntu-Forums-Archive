---
title: "messenger"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by helphelp on 2011-05-26
Hi,
Does anyone know of a good messenger for the 11 04  that can send and receive web cam  .

---

### Post by Matt__ on 2011-05-26
aMSN works fine with webcam still,
or if you want a better version of skype then this is good [Ekiga](http://ekiga.org/)

---

### Post by helphelp on 2011-05-27
Hi,
I have got aMSN but  the cam is not detected .
Your link didn't work .I installed ekiga from software centre  ,the version i got only gives me call option.
I think i need the 3.2 version. Do you know which package would be suitable for the 11 04 ?
Thank you

---

### Post by 3rdalbum on 2011-05-27
Skype is usually pretty good, and it's cross platform.

Empathy (the default IM client in Ubuntu) can do webcam over certain networks.

Or you could try Meebo ([www.meebo.com](www.meebo.com)) as a web-based messenger that has webcam support you can use with non-Meebo users.

---

### Post by Matt__ on 2011-05-29
Skype is now owned by Microsoft...dont expect it to be maintained or have open documentation to be developed anymore.

[Ekiga](http://ekiga.org/) link fixed..sorry about that

or you could do
```
$ sudo add-apt-repository ppa:sevmek/ppa
$ sudo aptitude update
$ sudo aptitude install ekiga
```

which should give you v3.2.6 of ekiga 

no idea why your cam wont work with aMSN, is there an underlying issue with it? does it work in cheese?

---

### Post by uRock on 2011-05-29
> **Matt__ said:**
> Skype is now owned by Microsoft...dont expect it to be maintained or have open documentation to be developed anymore.

There is no need to spread FUD when offering help. [http://www.microsoft.com/Presspass/press/2011/may11/05-10CorpNewsPR.mspx](http://www.microsoft.com/Presspass/press/2011/may11/05-10CorpNewsPR.mspx)

---

### Post by durand on 2011-05-29
If you're not already using a specific messenger program, I'd recommend jabber. If you have a google account (gmail, gtalk, etc), you can use that.

1) First, start Empathy.

2) Then either follow the wizard to add your first account or go to Edit > Accounts and add a new one there.

3) Change the protocol to Jabber or google talk.

4) If you don't have a google account, just choose jabber.

5) Then change the selection to "Create a new account on this server"

6) In the Login ID textbox, make up a username like say [email]helphelp@**jabber.org[/email]**.

7) Click Login and follow that through. It should ask you for a password and then log you in. If your contacts then do the same thing or if they have gtalk, you can IM/call/video chat with each other.

More info: [https://wiki.ubuntu.com/Jabber](https://wiki.ubuntu.com/Jabber)

You could also use ekiga, skype, amsn, etc depending on your preference. They all work well but they also have their own weaknesses.

EDIT: Does your webcam definitely work? Try installing [Cheese]("apt://cheese") and see if that lets you use your webcam.

---

