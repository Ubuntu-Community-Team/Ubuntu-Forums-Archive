---
title: "Want to connect two laptops in adhoc mode, set up but they do not ping each other"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by sup on 2007-01-16
Hi, I have two laptops with Ubuntu 6.10 both with an built-in intel wireless adapter. I would like to connect them through wireless and share internet connection through it (only one cable can go from my modem), but I have not even managed to make them ping each other.

I killed nm on both of them and set them to 192.168.10.1 192.168.10.2 address respectively anb network mask 255.255.255.0. I set the essid to andulka on both and set them to adhoc mode. What more do I need to do in order to get them connect? Something with default gateway? I can ping google alright. BTW:there is also an ethernet adapter on both of these laptops, does it matter?

---

### Post by peabody on 2007-01-16
The ethernet adapters shouldn't matter unless you're getting the interface names mixed up somehow (you probably aren't).

I wish I could say I had more experience in ad-hoc mode on Linux.  What's the make of the cards, what drivers are you using?

---

### Post by corax on 2007-01-16
I messed with this for a day in summer :-) I think you need one more thing (everything you have done so far is good :-) except maybe shut down the wired card sometimes it confuses the system for me when it has no connected cable and IP ):

```
sudo ifconfig eth0 down
```

You can switch it back with :

```
sudo ifconfig eth0 up
```

For your problem the solution is i think :

```
sudo iwconfig eth1 essid andulka channel 11 key off mode Ad-hoc
```

The most important part is : "key off" !!! Have you typed that too ? ;-)

good luck, corax

---

### Post by sup on 2007-01-16
oh, key off - I never thought of that (but it probably is better that by default the connection is encrypted), and I thought the channels will be picked automatically, I will try that as soon as I get over to my girlfriend's again, should be soon:-). (BTW:I was not the one who converted her to linux). Thanks for your help.

As for the ethernet adapters, I can try to shut them down when trying to establish the connection between the two laptops, but eventually I will have to turn it on in order to get internet sharing working, I hope [this]("http://www.ubuntuforums.org/showthread.php?t=91370&highlight=shared+internet") will guide me through.

---

### Post by corax on 2007-01-17
It was my fault (I was tired :-) ) I missread your first post about the wired cards. Of course don't disable the card what you use for the internet, but maybe on the other machine :-). I scanned through the thread you mentioned I think it should work I haven't done such a thing (internet sharing) but one of my friends did on my machine (and he was so quick I couldn't follow ;-) ) but as I remember the masquerade was necessary :-)

What I did is a simple connection between the two machines to copy files, and I did it as I said above.

bye, corax

---

### Post by sup on 2007-01-20
well, so I did everything I did before and what you posted and it would not work, I have no idea why, can it be something with iptables? I tried to list rules that are applied (iptables -L -v and iptables -L -v -t nat) and nothing was listed...
I am a little bit hopeless, although i did not try much (you generally do not want to mess with a computer for three hours when at your girlfriend's I think):-(

---

### Post by corax on 2007-01-21
Hi !

I did it 3 months ago maybe I didn't remember all the tricks I did :-)

Can you please post what is the output of :
```
iwconfig
```

and

```
ifconfig eth1
```

(if eth1 is your WLAN card)

after you entered this  ? :
```
sudo iwconfig eth1 essid andulka channel 11 key off mode Ad-hoc
```

By the way is both of your WLAN cards operating well ? Can you connect to an access point for example ?

I 'm sorry I can't try to reproduce it here because now I have only one machine with WLAN and one access point :-( but as soon as I can I' ll make it again and post you an exact "mini-HOWTO"
about connecting to each other. Anyway I found this article may interest you ...

[HTML]http://www.cse.msu.edu/~minutsil/iptables.html[/HTML] at the end there is "Basic masquerading" <- that is your friend :-) but maybe it is useful to read it through ...

I don't know if this matters or not but I set the IP addresses AFTER iwconfig :-) 

No you should NOT mess with computers at girlfriends house mess with something else ;-)

bye

---

### Post by naikadit on 2008-02-20
hey guys... in regards to the same post... I am also experiencing the same problem... I have installed ubuntu 7.10 in 2 laptops we have changed the mode Ad-hoc, the frequency channel id , essid, netork name and cell id... but still we are not able to ping each other...we have taken a staitic address 10.10.0.1 and .2  respectively ...please guys i would be really glad if u could reply i am desperate i need it for a project....thansk in advance,,

---

