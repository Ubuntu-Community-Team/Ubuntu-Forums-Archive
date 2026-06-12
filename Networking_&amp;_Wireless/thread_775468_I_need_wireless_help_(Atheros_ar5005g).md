---
title: "I need wireless help (Atheros ar5005g)"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by wwdd00 on 2008-04-30
First off, I should preface this by saying I am completely new to Linux, and that I have only just installed Ubuntu Hardy Heron.  So far, everything is beautiful, and I enjoy it immensely.  My laptop is an Acer Aspire 9503ewsmi, and I know that my wireless card is Atheros ar5005g.  I have tried to follow along with the threads in order to get my wireless working, and none of them have seemed to do anything.  I have tried doing it with ndiswrapper (which seems to be completely wrong for the type of card I have) and madwifi, and still nothing seems to be working.  What seems really strange to me is that it can see my wireless router (when I go to System>Administration>Network) but it still will not connect.  As I am unfamiliar with Linux on the whole, I don't know what else I can do.  Can someone please help me, and perhaps explain the steps as simply as possible?  I would greatly appreciate any help, and thank you in advance for your patience and understanding!

---

### Post by pro003 on 2008-04-30
ok go to System > Administration > Network > unlock (enter your pass) click on your wireless connection uncheck enable roaming mode, click at network namer ESSID, find your prefered network, chose password type i.e none, wep...and connection settings i.e. static ip or dhcp... click ok.

if you don't have home network, your computer connected to the other, then uncheck wired connection, save settings...

if you use username and password to connect then open terminal and type:

```
sudo pppoeconf
```


follow the instructions...

---

### Post by wwdd00 on 2008-04-30
I did everything and when i did the pppoeconf as you said, it had this on the screen:

> eth0
wlan0
wlan0:avahi

I said yes to the instructions, and it searched, and it found nothing, but had this message:

> Sorry I scanned 3 interfaces but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another pppoe process which controls the modem.

Any ideas?

---

### Post by pro003 on 2008-05-01
Ok. Do this, it may solve the problem.

```
sudo ifconfig eth0 down
```

```
sudo ifconfig ath0 up
```

```
sudo ifconfig wifi0 up
```

You should probably see available wireless networks ESSID, you can then choose your and after that try pppoeconf.

if nothing yet, go to System > Administration > Network - and uncheck eth0, check ath0 if unchecked. Get in properties of ath0 and uncheck "roaming mode enabled" and then chose your essid and dhcp or ip static, etc. Save that and get back in again and now check enable roaming mode and save... You should after couple of seconds see in your tray wifi icon status of your essid.

That's how I do these things, keep in mind that it may not necessarily work for you too.

---

### Post by wwdd00 on 2008-05-03
that did the trick, thank you so much for your help!

---

### Post by macro182 on 2008-08-31
Hi!

My friend has the same Atheros (AR5005G) and the same problem (he see AP, but he can't connect).
So when I can, I try to do for him the same trick...

But I would know one thing: did you try to use ath5k module? does it works?

Thanks!

---

### Post by zardosht on 2008-09-10
hi all
First I'm new to linux,
I installed ubuntu hardy on laptop Acer travelmate 2450 with atheros ar5005g 

It worked well after first login after installation I could to connect internet. but after shutdown in next time login it simply disappeared.

would you help me plz to find out the issue?

---

### Post by pro003 on 2008-09-10
Go to System > Administration > Network, unlock as root and do some research, turn off connections you may have and you don't use them and leave that one you use and set it to roaming or dhcp... should work.

---

### Post by zardosht on 2008-09-10
It worked, thank you so much. :)

---

### Post by zardosht on 2008-09-10
again me,

at the first sight the solution worked well, but after restart and loging again, the wireless connection disappeared and I have to restart the connection again to make it work. beside that upon the login, a proccess start named, " evolution-data" that sucks up %99 of CPU time. ofcourse I can kill the proccess. but it repeat after every login.

do you have any Idea?

---

### Post by hawksbill on 2008-09-10
What is wlan0:avahi doing in his interface list? According to madwifi's website he should have ath0 and wifi0 as interfaces.


Check out this thread.

[http://ubuntuforums.org/showthread.php?p=5375548](http://ubuntuforums.org/showthread.php?p=5375548)

---

