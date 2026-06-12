---
title: "firefox/internet connection problem"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by untitled.10 on 2009-06-26
I'm new to ubuntu.. and im having problem with my firefox/network ...the only site that i can open is google.com and other link that is inside google's website like google map.., while on other website like  yahoo , youtube etc .. the stat of the firefox always  says waiting..when i search yahoo on the search bar the results appear.. but when i click it it just says waiting..  i think there is something that is blocking other site to load.. pls help..i have my ubuntu for 3 days..

---

### Post by lovinglinux on 2009-06-26
Is this happennng since you installed Ubuntu or it just started to happen recently? Were you able to visit other web sites with Firefox and Ubuntu on the other 3 days?

What type of connection you have? Do you have a router or connect directly with a DSL modem?

This looks like a problem on your connection, like a DNS issue on your ISP.

Try to run the following command on a terminal [see note].

```
wget http://www.yahoo.com
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

Then copy what appears on the terminal screen and paste here. It should look like this:

```
$ wget http://www.yahoo.com
--2009-06-26 16:17:14--  http://www.yahoo.com/
Resolving www.yahoo.com... 69.147.76.15
Connecting to www.yahoo.com|69.147.76.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9490 (9.3K) [text/html]
Saving to: `index.html'

100%[=============================================>] 9,490       17.1K/s   in 0.5s    

2009-06-26 16:17:16 (17.1 KB/s) - `index.html' saved [9490/9490]
```

If it works, it will save a file called index.html on your home directory. You can delete that after doing this.

---

### Post by untitled.10 on 2009-06-26
After installing my ubutnu it works untill i update my system..i think there are 100+ update i made then after that the problem with my network starts and i cant configure what update cause that.. I'm using direct dsl.. here is the result of the code ..i tried to yahoo and google.. 
here is the result in yahoo :
code:

adrian@adrian-desktop:~$ wget [http://www.yahoo.com](http://www.yahoo.com)
--21:00:22--  [http://www.yahoo.com/](http://www.yahoo.com/)
           => `index.html.1'
Resolving [www.yahoo.com](www.yahoo.com)... 209.191.93.52
Connecting to [www.yahoo.com|209.191.93.52|:80](www.yahoo.com|209.191.93.52|:80)... connected.
HTTP request sent, awaiting response... 


and here is the result in google
code:
adrian@adrian-desktop:~$ wget [http://www.google.com](http://www.google.com)
--20:59:41--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 216.239.61.104
Connecting to [www.google.com|216.239.61.104|:80](www.google.com|216.239.61.104|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.com.ph/](http://www.google.com.ph/) [following]
--20:59:41--  [http://www.google.com.ph/](http://www.google.com.ph/)
           => `index.html'
Resolving [www.google.com.ph](www.google.com.ph)... 216.239.61.104
Reusing existing connection to [www.google.com:80](www.google.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 5,874         --.--K/s             

20:59:41 (73.59 KB/s) - `index.html' saved [5874]

I hope this help to configure the problem..thanks for replying my post:)

---

### Post by lovinglinux on 2009-06-26
> **untitled.10 said:**
> After installing my ubutnu it works untill i update my system..i think there are 100+ update i made then after that the problem with my network starts and i cant configure what update cause that.. I'm using direct dsl.. here is the result of the code ..i tried to yahoo and google.. 
here is the result in yahoo :
code:

adrian@adrian-desktop:~$ wget [http://www.yahoo.com](http://www.yahoo.com)
--21:00:22--  [http://www.yahoo.com/](http://www.yahoo.com/)
           => `index.html.1'
Resolving [www.yahoo.com](www.yahoo.com)... 209.191.93.52
Connecting to [www.yahoo.com|209.191.93.52|:80](www.yahoo.com|209.191.93.52|:80)... connected.
HTTP request sent, awaiting response... 


and here is the result in google
code:
adrian@adrian-desktop:~$ wget [http://www.google.com](http://www.google.com)
--20:59:41--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 216.239.61.104
Connecting to [www.google.com|216.239.61.104|:80](www.google.com|216.239.61.104|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.com.ph/](http://www.google.com.ph/) [following]
--20:59:41--  [http://www.google.com.ph/](http://www.google.com.ph/)
           => `index.html'
Resolving [www.google.com.ph](www.google.com.ph)... 216.239.61.104
Reusing existing connection to [www.google.com:80](www.google.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 5,874         --.--K/s             

20:59:41 (73.59 KB/s) - `index.html' saved [5874]

I hope this help to configure the problem..thanks for replying my post:)

At least we know now that is not a browser problem. I have no idea what could be causing this. Maybe DNS. Check with your ISP if there is any problem with the service.

---

### Post by superprash2003 on 2009-06-27
yes , it could be a DNS problem , try using opendns - 208.67.222.222 and 208.67.220.2220

for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by untitled.10 on 2009-06-27
> **superprash2003 said:**
> yes , it could be a DNS problem , try using opendns - 208.67.222.222 and 208.67.220.2220

for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)



thanks for the info.. i did the command on how to have an open dns like in the link that yiou've posted but the terminal said command not found and when i try to edit the file in the file system it said that i ndont have the permission to edit it.. T_T..i'm really confuse..coz i can open a webpage as long as it is in google..like google.org..gmail... gmaps... on other site i cant .

---

### Post by stevoo on 2009-06-27
what are the results of ifconfig ?

---

### Post by philcamlin on 2009-06-27
try rebooting your router 

and post ifconfig :popcorn:

---

### Post by untitled.10 on 2009-06-27
Here is my ifconfig
code:


adrian@adrian-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:5f:88:ad  
          inet addr:192.168.249.250  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::290:f5ff:fe5f:88ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:88 dropped:0 overruns:0 frame:88
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48335 (47.2 KB)  TX bytes:33300 (32.5 KB)
          Interrupt:3 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18000 (17.5 KB)  TX bytes:18000 (17.5 KB)

---

### Post by LewRockwell on 2009-06-27
does this happen while using the live-run test-drive function of Ubuntu?

or the firefox browser in Parted Magic's live-run utilities suite?

[http://www.partedmagic.com/](http://www.partedmagic.com/)

---

### Post by untitled.10 on 2009-06-27
> **LewRockwell said:**
> does this happen while using the live-run test-drive function of Ubuntu?

or the firefox browser in Parted Magic's live-run utilities suite?

[http://www.partedmagic.com/](http://www.partedmagic.com/)



Sorry sir.,, but i have no idea on live run test drive or parted magic's live-run..im noob to ubuntu.. need help pls.. i cant open other websites except google ..

---

