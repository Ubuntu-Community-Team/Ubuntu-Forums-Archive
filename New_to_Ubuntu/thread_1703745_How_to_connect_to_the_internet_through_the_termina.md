---
title: "How to connect to the internet through the terminal?"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by robro on 2011-03-09
Hello everyone,
Well I'm trying to find out a way to connect to the internet through the terminal, I have a ppp0 connection if it helps,

Thanks for your help :)

---

### Post by sanderd17 on 2011-03-09
what do you want? do you want download files? upload files? those are all different programs.

to download a file, you can use the wget command followed by the URL.

---

### Post by robro on 2011-03-09
no, what i want is the command (if there is one) to connect to the internet through the terminal.

---

### Post by pqwoerituytrueiwoq on 2011-03-09
i think it is something like 
ifconfig eth0 up

---

### Post by bkratz on 2011-03-09
> **pqwoerituytrueiwoq said:**
> i think it is something like 
ifconfig eth0 up

I believe you need a "sudo" in front of that command.

---

### Post by robro on 2011-03-09
I tried it (replacing eth0 with ppp0) and i got this error message: 
```
ppp0: ERROR while getting interface flags: No such device

```

Edit: I did do sudo

---

### Post by PunkLV on 2011-03-09
```
cat /etc/network/interfaces
```
```
sudo ifconfig
```
Please post.
Will delete my post later, however, grahammechanical most likely solved the problem.

---

### Post by grahammechanical on 2011-03-09
May I suggest that you go into the Ubuntu Software Centre and look at Gnome PPP. Do a search for Gnome PPP

Regards.

---

### Post by robro on 2011-03-09
ifconfig (just ppp0):
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.225.212.205  P-t-P:66.174.175.132  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:846051 (846.0 KB)  TX bytes:180773 (180.7 KB)

```

---

### Post by wojox on 2011-03-09
Try this:

```
w3m -v http://www.google.com
```

---

### Post by robro on 2011-03-09
i try'd it, it just loads google.com, it dosn't connect to the the internet.

---

### Post by rbishop on 2011-03-09
Where are you wanting to go?  What are you trying to do?  

Just saying >  it dosn't connect to the the internet. 	  isn't enough for anyone to help you.

Explain what you want to do so we can further help you.

---

### Post by wojox on 2011-03-09
> **robro said:**
> i try'd it, it just loads google.com, it dosn't connect to the the internet.

Well if it loads Google then technically your connected to the Internet.

---

### Post by PunkLV on 2011-03-09
Shooting in the dark: are you trying to get IM clients like skype running?
Otherwise I do not get the concept of "not connected to internet"

---

### Post by robro on 2011-03-09
alright heres what im trying to do:
I am trying to connect to the internet with a terminal, i can connect with a gui (i.e. the icon on the bottom left)

---

### Post by rbishop on 2011-03-09
If you run the command

```
ping www.google.com
```

What happens?  If you get a response, then you are online!

---

### Post by teward on 2011-03-09
I think he's looking for something like w3m, which is a console-based internet browser.  :/

---

### Post by robro on 2011-03-09
No im trying to figure out way to connect to the internet FROM A TERMINAL (e.g. the ctrl-alt-(1-6))

---

### Post by PunkLV on 2011-03-09
```
sudo apt-get install links2
```
```
links
```
Press **G** enter URL -- you ARE in internet from a terminal.
**Alt+F** for menu.

---

### Post by wojox on 2011-03-09
> **robro said:**
> No im trying to figure out way to connect to the internet FROM A TERMINAL (e.g. the ctrl-alt-(1-6))

Graphically? No.

---

### Post by el_koraco on 2011-03-09
you're just ******* with people, right?

---

### Post by pqwoerituytrueiwoq on 2011-03-09
are you trying to switch between two network profiles 
like switch from one person's wifi to another? or switch to and from hardwire

---

### Post by robro on 2011-03-09
Alright for some reason no-one can understand what i'm trying to do, so just forget it.

---

### Post by PunkLV on 2011-03-09
Do not delude yourself by pinning your inability to properly explain the matter on us.

---

### Post by MiThRaZoR on 2011-06-24
Lol. He asked the question just fine.

From looking elsewhere online. I found this.

Sorry to bump an old thread. But it can help others.

```
1) iwlist ra0 scan
2) iwconfig ra0 essid (ESSID)
3) iwconfig ra0 key open (WEP-KEY)
4) ifup ra0
```

With a sudo in front of each command

---

