---
title: "no pages loading even when eth0 is active"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Chikoo Blade on 2011-07-04
hi...
i recently installed ubuntu 10.04 after formatting the entire hdd.
i configured auto eth0(wired) with the required fields and the connection was detected and active.
but when i try to start firefox...no page loads...it keeps tryin...not loading...
i use adsl ethernet conection as well as wireless but currently wireless is turned off in my modem....
any help regarding both wired and wireless connections will be accepted gladly...
thanks in advance...

---

### Post by wildmanne39 on 2011-07-04
> **Chikoo Blade said:**
> hi...
i recently installed ubuntu 10.04 after formatting the entire hdd.
i configured auto eth0(wired) with the required fields and the connection was detected and active.
but when i try to start firefox...no page loads...it keeps tryin...not loading...
i use adsl ethernet conection as well as wireless but currently wireless is turned off in my modem....
any help regarding both wired and wireless connections will be accepted gladly...
thanks in advance...
Hi, the wire connection should have worked without the need to manually add configuration, can you undo the changes you made, and them make sure the lan is turned on in the bios setup. Make sure your cable is plugged in, then we will go from there.

---

### Post by Chikoo Blade on 2011-07-05
lan is turned on and plugged in...saves undone....now its on manual and ipv4 is on automatic(DHCP)....
and sorry for the late reply...i live in time zone gmt+5:30...so i usually sleep at that time...
ne way i will try to on today....

---

### Post by halibaitor on 2011-07-05
I had the same problem.  In my case, the default configuration for FireFox was to start in "offline mode".  (Is that normal?)

Click on _File_ at the top left corner of the page and look for the "Work Offline" checkbox, and make sure it _isn't_ checked.

---

### Post by Chikoo Blade on 2011-07-05
i tried unchecking work offline but it still isint working...

---

### Post by Chikoo Blade on 2011-07-05
can anyone please help me out with my issue on the non connectivity of internet i posted earlier....
 
i recently installed ubuntu 10.04 after formatting the entire hdd.
i configured auto eth0(wired) with the required fields and the connection was detected and active.
but when i try to start firefox...no page loads...it keeps tryin...not loading...
i use adsl ethernet conection as well as wireless but currently wireless is turned off in my modem....
any help regarding both wired and wireless connections will be accepted gladly...
thanks in advance...

---

### Post by dFlyer on 2011-07-05
can you post the /etc/network/interfaces

---

### Post by howefield on 2011-07-05
Duplicate threads merged.

---

### Post by Chikoo Blade on 2011-07-05
> **dFlyer said:**
> can you post the /etc/network/interfaces
 
tis is what is present:
 
auto lo
iface lo inet loopback

---

### Post by Chikoo Blade on 2011-07-05
> **howefield said:**
> Duplicate threads merged.
  
what does that mean???
solution??
simpler soln???

---

### Post by DawieS on 2011-07-05
I don't know if this is going to help you, but it is worth a try:
Click on **System** > **Preferences** > **Network Proxy**. Make sure **Direct Internet Connection** is ticked, then click on **Apply System-Wide...** Enter your password (twice I think).

I don't know why, but I have seen it bringing an otherwise dead network back to life...:wink:

---

### Post by wildmanne39 on 2011-07-05
> **Chikoo Blade said:**
> lan is turned on and plugged in...saves undone....now its on manual and ipv4 is on automatic(DHCP)....
and sorry for the late reply...i live in time zone gmt+5:30...so i usually sleep at that time...
ne way i will try to on today....Hi, when you say your lan is on, does that mean you checked in the Bios when you boot the computer and it was on there? two weeks ago I worked on a computer and installed ubuntu but the lan some how got turned of in bios like I said it should have work as soon as you booted, did it work when you tried ubuntu from the livecd before you installed ubuntu? we need to get the wired to work then we can work on the wireless.

---

### Post by Chikoo Blade on 2011-07-06
> **wildmanne39 said:**
> Hi, when you say your lan is on, does that mean you checked in the Bios when you boot the computer and it was on there? two weeks ago I worked on a computer and installed ubuntu but the lan some how got turned of in bios like I said it should have work as soon as you booted, did it work when you tried ubuntu from the livecd before you installed ubuntu? we need to get the wired to work then we can work on the wireless.
 
i dint use livecd....i installed it directly...recommended by my friends....
but yes.....i checked it on bios n lan is turned on.....
what do i do???i need net urgently....i cant do nething withowt it.....cant download nething in turn cant watch or listen to avis or wmas.....

---

### Post by Chikoo Blade on 2011-07-06
> **DawieS said:**
> I don't know if this is going to help you, but it is worth a try:
Click on **System** > **Preferences** > **Network Proxy**. Make sure **Direct Internet Connection** is ticked, then click on **Apply System-Wide...** Enter your password (twice I think).

I don't know why, but I have seen it bringing an otherwise dead network back to life...:wink:
direct internet connection was already checked.....

---

### Post by Perkins on 2011-07-06
Open a terminal and run ifconfig and post the results.  That will tell us what you're ending up with and make it easier to determine what's not working right.

---

### Post by Chikoo Blade on 2011-07-08
> **Perkins said:**
> Open a terminal and run ifconfig and post the results.  That will tell us what you're ending up with and make it easier to determine what's not working right.
Hey,
this is what appeared:

 chikoo@chikoo-laptop:~$ ifconfig
    eth0      Link encap:Ethernet  HWaddr 00:1a:a0:fd:fe:92  
              inet6 addr: fe80::21a:a0ff:fefd:fe92/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:2414 (2.4 KB)
              Interrupt:17 
     
   
  lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:8 errors:0 dropped:0 overruns:0 frame:0
              TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
     
   
  chikoo@chikoo-laptop:~$ ^C
    [FONT=&quot]chikoo@chikoo-laptop:~$ [/FONT]

---

### Post by AlphaNeil on 2011-07-08
You said you are using ADSL connection. Does it mean you need to use username and password for internet connection? If yes have you configured it?

---

### Post by Chikoo Blade on 2011-07-08
> **AlphaNeil said:**
> You said you are using ADSL connection. Does it mean you need to use username and password for internet connection? If yes have you configured it?

No....i need not.....no username or password....

---

### Post by Perkins on 2011-07-08
Ok.  Your connection only has an ipv6 address.  That is unusual.  So, for starters, try:

```
sudo dhclient eth0
```

That will tell your machine to try and get a new DHCP address.  If that fails, then we need to make sure your ADSL router is working properly.  There's usually a sticker on the bottom of them with their default settings, post back what it says.

---

### Post by Chikoo Blade on 2011-07-10
Thank you,
to all the people who helped me out......
the problem is solved.....
in fact,the problem was with my local telephone exchange.....
but i still cant figure out how internet worked with windows thru the same line in  a different comp....
but not in ubuntu....

---

### Post by wildmanne39 on 2011-07-10
> **Chikoo Blade said:**
> Thank you,
to all the people who helped me out......
the problem is solved.....
in fact,the problem was with my local telephone exchange.....
but i still cant figure out how internet worked with windows thru the same line in  a different comp....
but not in ubuntu....Hi, there is no telling,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by laidback on 2011-07-10
You might want to check FF settings. When I install a new version of Ubuntu I have to go to FF>about:config in the address line>accept warning>in filter line type ipv6>set value to true which can be done with a double click on the current setting which will probably be false i.e. you are disabling ipv6.

Why this is so I have no idea, but it could answer the question as to why your internet connection can work with Windows but not with Ubuntu.

---

