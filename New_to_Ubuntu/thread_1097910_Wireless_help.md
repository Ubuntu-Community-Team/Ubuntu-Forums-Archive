---
title: "Wireless help"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2009-03-16
* have just built a new box for my living room.  [I] have a linksys wireless card in the box and am trying to get connected to the net and have no idea how to do this on _buntu please and thanks for any help fixing this problem._*[/I]

---

### Post by ozbolt on 2009-03-16
Click on icon in panel where are 2 computers. Right click and enable wirelles and than it will find it by itself and no problem connecting to network.
If you don't have wirelles option than this means the card is not supported by ubuntu and you will have to install ndiswrapper (add/remove) and play with it.

---

### Post by leonardo_neo on 2009-03-16
> **DarkSaga70 said:**
> * have just built a new box for my living room.  [I] have a linksys wireless card in the box and am trying to get connected to the net and have no idea how to do this on _buntu please and thanks for any help fixing this problem._*[/I]

What difficulty are you experiencing? A lit bit more detail would help. :)

---

### Post by .:Justus:. on 2009-03-16
> **DarkSaga70 said:**
> * have just built a new box for my living room.  [I] have a linksys wireless card in the box and am trying to get connected to the net and have no idea how to do this on _buntu please and thanks for any help fixing this problem._*[/I]

I hope you don´t have the wpc300n its a pain to install.
If you don´t then you should try installing via ndsiwrapper like the other guy said. You will need to download the Windows drivers first, store them in your home folder. Then you follow the instructions that ndiswrapper gives you and it´s not too hard really.

ndiswrapper: [http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)

---

### Post by DarkSaga70 on 2009-03-16
> **.:Justus:. said:**
> I hope you don´t have the wpc300n its a pain to install.
If you don´t then you should try installing via ndsiwrapper like the other guy said. You will need to download the Windows drivers first, store them in your home folder. Then you follow the instructions that ndiswrapper gives you and it´s not too hard really.

ndiswrapper: [http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)

Thanks I will try that. Thanks for all the help.:popcorn:

---

### Post by halitech on 2009-03-16
since its an internal card, lets make sure the system is seeing it installed first. Open a terminal and post the output of```
lspci
```
this will give us a better idea of what driver you may need based on your chipset

---

### Post by .:Justus:. on 2009-03-16
> **DarkSaga70 said:**
> Thanks I will try that. Thanks for all the help.:popcorn:
No problem

> **halitech said:**
> since its an internal card, lets make sure the system is seeing it installed first. Open a terminal and post the output of```
lspci
```
this will give us a better idea of what driver you may need based on your chipset

The thing is he says he has a linksys card.
Most of the linksys cards aren´t supported in any linux distros because broadcom(they make the drivers) for some reason doesn´t feal like doing so. And i remember that i wasn´t able to install my Linksys wmp300n on my old comp even with ndiswrapper.
Times have changed though since then, i hope that the TS doesn´t have the same problems I and many others did.

---

### Post by halitech on 2009-03-16
> **.:Justus:. said:**
> 
The thing is he says he has a linksys card.
Most of the linksys cards aren´t supported in any linux distros because broadcom(they make the drivers) for some reason doesn´t feal like doing so. And i remember that i wasn´t able to install my Linksys wmp300n on my old comp even with ndiswrapper.
Times have changed though since then, i hope that the TS doesn´t have the same problems I and many others did.

but if its not physically installed properly (and thus not recognized) then no matter what he does its not going to work. And where its a new install on a new system, the card *may* not be seated properly. And please don't say it doesn't happen cause there was a guy on here a few weeks ago that didn't have his card seated and couldn't get it to work.

---

### Post by anewguy on 2009-03-16
Card seating problems are common, even with old systems.  Things happen, the card works a little loose.  Do be sure to check first that the card is properly seated - if it has a latch at the back of the socket make sure it's engaged.

Now, if that doesn't solve your problem, then we do indeed need to look at drivers.  While ndiswrapper may in the long run be the solution, we really do need to see the chipset to help get the right driver.  So, that being said, please do as was suggested earlier and try to provide the following information:

Since you just assembled it, what is the model of the adapter?

Using a terminal window (applications/accessories/terminal), type:

lspci <press enter>

and copy and paste the output from that back here.

Once everyone is working on a common page, we can get the correct answer for you.

Dave :)

---

