---
title: "Can somebody help me please"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Deano92 on 2008-08-30
Well Hello Everyone !

This is my first post here so be kind:-P

Ok,down th the problem,I recently installed the most recent version of Ubuntu (Hardy Heron,I think)after a freind recommended it and I can see why.its great

I've had a few problems,all been resolved bar one,the wireless :(

I have a Broadcom BCM 4312 that will find wireless networks but once it trys to connect to them it just keeps asking for the network key,no matter how many times I enter

I think the driver is installed beacuse I can see it in the hardware drivers section along with my graphics card

The latop connects to the interneti  straight away once I have connected to the wired network.... any ideas whats wrong with it ?

(please excuse the confused post,I'm not sure how to word this sort of stuff)

Thanks in advance for any replies

Cheers,

Dean

---

### Post by cdtech on 2008-08-30
> I have a Broadcom BCM 4312 that will find wireless networks but once it trys to connect to them it just keeps asking for the network key,no matter how many times I enter
Maybe try "wicd" instead of "network manager". I found my wireless to work much better using "wicd"
```
sudo apt-get install wicd
```

**P.S.**
Welcome aboard and good luck.........

---

### Post by gmxgeek on 2008-08-30
There should be a save button in the Network Manager that will allow it to save your password

---

### Post by Deano92 on 2008-08-30
Thanks for the help guys,ill try those suggestions when I'm back at home.

---

### Post by Deano92 on 2008-08-30
> **cdtech said:**
> Maybe try "wicd" instead of "network manager". I found my wireless to work much better using "wicd"
```
sudo apt-get install wicd
```

**P.S.**
Welcome aboard and good luck.........

Another noob question,but where do I put that code ?

---

### Post by rashwan on 2008-08-30
> **Deano92 said:**
> Another noob question,but where do I put that code ?

[IMG]http://blog.racoon97.net/images/ubuntu/wicd_main.png[/IMG]

Cheer!

---

### Post by diafygi on 2008-08-30
> **Deano92 said:**
> Another noob question,but where do I put that code ?

The code cdtech gave you is actually a command you can put in the terminal. Just go to Applications > Accessories > Terminal. A command line prompt should appear, and you can copy and paste the code into it. Note: pasting into the Terminal is a different set of hotkeys (Ctl+Shift+V) because the normal ones are take by another command.

Also, if the command you are entering starts with a 'sudo', it will ask for your administrator password. Sudo will grant administrator privileges to that one command and nothing else, so please be aware of what your are entering after sudo. For this example, 'sudo apt-get install wicd' runs apt-get, which is a program to install packages from the Ubuntu repository (in this case wicd). Cheers!

---

### Post by rashwan on 2008-08-30
ohh... my bad i thought he is talking about the passphrase :p
LOL
actually its n00b answer based on n00b question

---

### Post by Deano92 on 2008-08-30
With my new found knowledge of how to work the [sudo]I am trying the soloution thats sticked at the top of the page

When I solve one problem another one starts,what I would like to know is how do I create a blacklist ?

Thanks for all the help so far guys :D

---

