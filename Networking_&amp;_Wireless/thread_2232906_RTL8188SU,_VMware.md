---
title: "RTL8188SU, VMware"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by Jay_O on 2014-07-05
Hey guys...so the other day I decided to start experimenting with moving along in the PC/OS, Until yesterday I didn't even know what ubuntu was, So I wen't along and did some reading , purchased and installed VMware, thinking I'd test it out and see if I like it...I'm okay with computers although my terminal lingo and know how has to improve. My final goal is to learn wifi penetration, since I wan't to go to school to study Computer forensics,and wan't to test things out between my pc and ubuntu and vice versa... plus I read somewhere that the chipset  RTL8188SU works with ubuntu and Beini, so that's my goal. Anyway once I installed ubuntu and vmware gives you the option to switch the wireless cards/adapter back and forth between host, and ubuntu...I did this and of course nothing happened. So I did a little reading and the last post on my problem was with version 10.0 or so, I'm currently running the newest which is 14. something...I went along and downloaded the linux driver for the Engenius EUB9603H ([https://wikidevi.com/wiki/EnGenius_EUB9603H](https://wikidevi.com/wiki/EnGenius_EUB9603H)) that's the model in case you guys need more info.. I wen't along and opened the installaltion file in ubuntu and clicked on install.ini (don't really remember the file but BAM ,the terminal window opened and all that jabber that I don't understand was written there, you should have seen my face...I thought I was the smartest guy on the planet...now I don't have to sumo,dudo or NDIS Wrapper (forgive me if I misspelled anything). That moment of triumph was short lived. Every few minutes I have to disconnect my adapter and reconnect it. It continually asks me for my password and even though I retyped it, it repeats the process. I think this thread ([http://ubuntuforums.org/showthread.php?t=2105572&highlight=rtl8188s](http://ubuntuforums.org/showthread.php?t=2105572&highlight=rtl8188s)) shows my same problem and I even tried reading others,but once again my whole technical jargon sucks. I mean if it's something I could copy and paste yeah...so any help at this point would be appreciated. I'm a pretty fast learner and hope you guys have the patience to answer this old question again...thanks in advance!

---

### Post by squakie on 2014-07-05
Are you running a Windows host and running Ubuntu in the virtual machine?  If so, the network will be (I believe by default) bridged - the host has the wireless connection, the VM just sees it as a network connection.  No need to deal with wireless things like the driver in a virtual machine.

BTW - virtualbox is free and works well. Many of us use it as our virtual machine manager and it works great.

---

### Post by Jay_O on 2014-07-05
Yeah I do run it on Vmware...problem is I acually got it connected. With vmware I can disconnect the adapter from host and connect it to ubuntu. before that the connection on ubuntu is bridged and I'm guessing it uses my Pc's wifi. Once I switch it over you see the small wifi icon on ubuntu,before I couldn't see it no matter what I did. Problem is a few minutes in the icon shows that the wireless is connected but the led light starts flashing, not in the random network traffic pattern but on and off and ubuntu starts asking me for the password again. i click continue..it "tries" to connect and process starts all over. Only thing that solves this for a few minutes is me unplugging the cord and "manually" (literally)resetting the network...minutes later, whole thing starts over. I can use the bridged network, but the purpose of me learning wifi and wifi penetration is why I need it..so I can study and experiment with the network on ubuntu ..(my own) and the other on my windows 7 also mine, but eventually I wan't to set up a different network inside of my own...run that on ubuntu and my pc on other....to which I have another adapter,problem is I gotta get ubuntu wifi up and running. (Cute cat btw...i have two...love em) Thanks for reply

---

### Post by squakie on 2014-07-06
Any possibility of just going to a dual-boot?  I don't know how much of a difference, but it may help not having the vm as a middle man and instead having ubuntu directly controlling the hardware.

---

