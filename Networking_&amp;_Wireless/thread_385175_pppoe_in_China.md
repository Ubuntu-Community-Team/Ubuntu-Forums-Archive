---
title: "pppoe in China"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by Zorfa on 2007-03-15
Hi! I'm running Ubuntu 6.10 off a cd to test if I can connect to the internet with it. I'm sick of windows and dying to let it go. If I can get the internet to work on Ubuntu, I'm saying a permanent bye-bye to Windows.

Unfortunately, I'm in China (Henan Province) and I don't speak Chinese. Even if I did, china netcom (my provider) does not support linux so it's impossible to get help from them.

Anyway... after running pppoeconf, using the default settings and entering my username and password, I get the message "CHAP authentication failed". I thought maybe I need to use PAP and not CHAP (both of which I am not very familiar with). I wasn't sure how to switch between them, so I renamed the chap-secrets file to something else so that it wouldn't be found. After doing that I get something like:
.
.
.
... peer from calling number 00:12:34:56:78:90 authorized
... LCP terminated by peer
... Connection terminated
... Modem hangup

Does anyone have any ideas at all? If there is anyone from Henan, China reading this message, could you please confirm whether or not you can use the internet on Ubuntu? I would be eternally grateful for any help!!

---

### Post by Jefferythewind on 2007-04-12
Hi, I also am living in China, and i speak some Chinese but most Chinese people here, in Yunnan have never heard about Linux.  Anyway, i did the same thing as you i think.  pppoeconf.  and actually after messing with the capital and lower case settings of my username and password got it to work.  and i was online for a couple days.  then all of a sudden i can't go online anymore.  and i get the same thing

CHAP authentication failed: Status-Err

I have gotten into the CHAP and PAP secrets files.  Can Somebody tell why CHAP authentication would fail, please.

---

### Post by Zorfa on 2007-04-29
Ok, I've figured it out... finally...

First of all, in order to connect to the internet using PPPoE on Linux, try the procedure outlined at [http://forum.ubuntu.org.cn/viewtopic.php?p=15502](http://forum.ubuntu.org.cn/viewtopic.php?p=15502). If that fails, then, as a last measure, try this guide. I spent over 2 months trying to figure out the reason why I couldn't connect to the internet on Linux (Ubuntu 6.10 and Fedora Core 6)... here is what I discovered. In most parts of the world, this procedure should be unnecessary. However, I live in Henan Province in China. The local ISP provides Windows-only software in order to connect to the internet. Connection works great on Windows, but doesn't work on Linux. After some splitting headaches, I finally figured out the reason was that the ISP's software was automagically changing my username! Why? I don't know. But that's the truth of it. In other words... find out the modified username, plug it into pppoeconf (or adsl-setup or any other such program) and connecting on Linux isn't a problem anymore. How do you find out the modified username? Use a network analyzer. 

In order to follow this guide, you're going to need a network analyzer such as [Ethereal]("www.ethereal.com/"). Ethereal is the software that I used while creating this guide and, hence, is the software shown in the following screenshots.

1. Download and install Ethereal on your Windows machine.
2. Start up Ethereal. (Your internet connection should NOT be active at this point!)
3. Go to Capture -> Interfaces or click on the button circled in black in the picture below.
[IMG]http://www.shangqiuonline.net/img/List_interface.JPG[/IMG]

4. You should see a new window similar to the one below (but with your network card listed). Click on the “Capture” button next to your network card. Please remember, you must still be disconnected from the internet at this point. If your network card is not listed, try restarting your computer and start again from step 1.
[IMG]http://www.shangqiuonline.net/img/select_interface.JPG[/IMG]

5. You will see a window similar to the following figure.
[IMG]http://www.shangqiuonline.net/img/Capture.JPG[/IMG]

6. Now, start up your internet connection. Ethereal will start capturing any and all packets sent from and received by your computer. Allow Ethereal to capture packets until your connection is safely established (usually takes under 15 seconds, but this could vary). Then click “Stop” as shown below.
[IMG]http://www.shangqiuonline.net/img/stop_capture.JPG[/IMG]

7. You now have a screen filled with a crazy amount of numbers and information. Look for a line under the “Info” section which reads something like “Response (NAME='xxxxxxxxxxx', VALUE=0x.........)”. (In case you're using China Netcom in some parts of China, the string MIGHT be of the form “x:xxxxxxxxxxx”. All characters in it are alphanumeric in nature. Again, this might NOT always be true!) The “NAME” string is your modified username! Write it down, start up your Linux partition (or machine) and try using the username you noted down along with your given password. I have done this on 2 separate machines with 2 different internet accounts from the same ISP and it worked beautifully both times!
[IMG]http://www.shangqiuonline.net/img/username.JPG[/IMG]


If it so happens that the NAME string in the Response packet is the same as your given username, then I'm afraid the solution for the problem with your connection lies elsewhere. Sorry! Once again, as far as I know, doing all this should be completely unnecessary with any sane ISP. Hopefully, this can save someone else a couple of months of sleepless nights. Looks like that ol' Windows machine can sometimes be useful after all!

Acknowledgment:
I would like to thank Julien Mary of [Progression-Asia]("http://progression-asia.com") for providing the moment of inspiration which led me to discover this crazy behavior. Thanks Julien!

---

### Post by DalianDragon on 2007-09-20
Hey, 

I'm from Dalian, China and just installed ubuntu on my comp.

I'm getting an error message, also.  but it's a "PAP Authorization Failed" instead of CHAP.

I tried to download Ethereal, but when i try to open it, my comp says that the file's corrupted !  MAN !


what do I do, NOW ?!

---

### Post by mips on 2007-09-20
Another option if you are using Ethernet would be to get rid of pppoe and simply let the router/modem do the authentication.

---

### Post by nobodie on 2007-10-01
Hi China folks,
I'm in Zhoushan, Zhejiang Province. same same stuff. I got told that you couldn't do it in linux. That went over well with me. I've been working through some stuff through another thread (i can't link to it right now, but search either my name or pppoe in this forum to find it). 

What I have done is to use roaring penguin to set things up and i have a ping return and can trace route to my connection, but then it breaks. this would be consistent with the naming protocol idea. 
I will try to use ethereal within my ubuntu environment and see if it will work without the windows connection. then i'll try the brute force letter change method. 

some thoughts on what could be the problem with the username: windows for china was deliberately broken by MS to make it less usable through piracy. in other words, a pirated windows from china is so bad westerners wouldn't use it. 

They also use UTF8 instead of ASCI by default, which could cause some problems in some situations. 

Oh and hello to the friend from Yunnan, I lived in Kunming for 2 years and loved it. And the Henan friend, where in Henan are you and how is it? Are we all teachers???

more later when i finish the above stuff.

---

