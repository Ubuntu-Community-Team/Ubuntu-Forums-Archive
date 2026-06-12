---
title: "Unable to connect to wifi with correct password"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by ethandt on 2017-03-05
I have been using Ubuntu for the last couple of years, and this is the biggest problem I've ever had with Ubuntu. I created this account just to ask this question.

I was using Ubuntu until a few days ago, until I decided to try out Ubuntu MATE. I installed it and got it running fine, except for one thing: I cannot connect to wifi. I can see all the nearby networks. When I try to connect,  it asks me for the password, which I put in. After it seems to be connecting, it stops and tells me that I have been disconnected. 

I have tried everything that I could find like this on AskUbuntu and the forums and got nowhere. Any help would be appreciated.

Output of iwconfig: [IMG]https://anonimag.es/i/imagef10a6.md.jpg[/IMG]

---

### Post by opsusec on 2017-03-06
run :~$ifconfig and post output.

then :~$netstat -i and output.

then you'll be able to diagnose it. it seems to me that you might have to internally bridge your hardware depending on what is inside it.

---

### Post by kc1di on 2017-03-06
What is your wireless card? and what driver are you using?
Also it may be helpful if you have an internet connection some other way?
to install inxi ```
sudo apt-get install inxi
```
then run the following command and post the output here.
```
inxi -Fxz
```
also the output from the commands list by opsusec above.

---

### Post by ethandt on 2017-03-06
I fixed it the lazy way. I downgraded from 16.10 to 16.04 and it works now. I'll update the title.

---

