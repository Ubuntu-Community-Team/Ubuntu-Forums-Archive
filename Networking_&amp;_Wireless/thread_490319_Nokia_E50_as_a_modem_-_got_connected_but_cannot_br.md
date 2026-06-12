---
title: "Nokia E50 as a modem - got connected but cannot browse the Internet"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by srangelov on 2007-07-02
Hi, all!

My PC is using cable Internet connection but sometimes the Internet stops and I need an alternative provider. So, I managed to connect my Nokia E50 via USB data cable to my PC using several tutorials in this forum and wvdial. I successfully get IP address and DNS, but cannot browse the Internet or ping! Can anyone help me?
Here is what I get when start the wvdial:
```


Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jul  2 17:31:34 2007
--> Pid of pppd: 6439
--> Using interface ppp0
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> local  IP address 10.8.8.205
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> remote IP address 10.6.6.6
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> primary   DNS address 192.168.88.12
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]
--> secondary DNS address 192.168.88.13
--> pppd: &#65533;[08][06][08]&#65533;[10][06][08]&#65533; [06][08]


```

---

### Post by srangelov on 2007-07-03
Come on, guys!
I badly need your help!
I even bought a brand new phone, as I thought the problem was in the phone - see my other post: [http://ubuntuforums.org/showthread.php?t=470710]("http://ubuntuforums.org/showthread.php?t=470710") . (I tried this with nokia 6610i and the result is the same - wvdial connects and gets IP and DNS but I cannot browse the Internet.)
I really need a mobile Internet (sometimes). It is crucial for my job.

---

### Post by srangelov on 2007-07-05
OK, I found the answer. I cannot browser Internet because I have a Firewall - Firestarter.
To browser the internet:
1. Open Firestarter and stop it - just click on Stop Firestarter.
2. Open Terminal and write wvdial
3. Open Internet Browser and start browsing the net.

Of course, now comes the next question - How to avoid stopping Firstarter? - may be to include some rule?

P.S. I've just found a better solution:
"If you connect successfully but your Internet applications do not function (eg. web pages do not load in Firefox), you might need to add ```
replacedefaultroute
``` as a new line in the pppd option file."
To read the whole article, visit this page:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

P.P.S. Still I have to manually stop the Firestarter :( I started new thread on this as this is another matter. Please, if anyone can help me, see this thread:
[http://ubuntuforums.org/showthread.php?p=2972765#post2972765]("http://ubuntuforums.org/showthread.php?p=2972765#post2972765")

---

