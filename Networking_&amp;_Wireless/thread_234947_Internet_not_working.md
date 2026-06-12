---
title: "Internet not working"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by dmglouis on 2006-08-12
I just now installed Ubuntu 6.06 on my old comp and have discovered that the Internet is not working. When I booted with the live CD it worked, though. Can anyone help?

---

### Post by mhkhosravi on 2006-08-12
I have this problem too.
Somebody help please :(

---

### Post by drtvasudevan on 2006-08-12
> **mhkhosravi said:**
> I have this problem too.
Somebody help please :(
first try this
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox. 
\\:D/ 
if still no connection post here again.
8-[

---

### Post by mhkhosravi on 2006-08-12
the problem still exists!
in live cd we have a icon in menues that refere to dial up connection.
but when we install ubuntu this icon disappears and I dont know where it is. :confused:

---

### Post by slakkie on 2006-08-12
> **drtvasudevan said:**
> first try this
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox. 
\\:D/ 
if still no connection post here again.
8-[

This is bad advice. You are assuming that the internet is firefox only. And you assume the problem is ipv6 related. Both are not mentioned in the posts mentioning the problem.

@ the problem owners ;)
Please have a look at the following thread: [http://www.ubuntuforums.org/showthread.php?p=1370905#post1370905](http://www.ubuntuforums.org/showthread.php?p=1370905#post1370905)

Please also tell us if you are using DHCP or if you are using staticly assigned IP addresses.

---

### Post by drtvasudevan on 2006-08-12
try:
open terminal
type
sudo pppoeconf
will ask for password type that.
try to connect.

---

### Post by drtvasudevan on 2006-08-12
> **slakkie said:**
> This is bad advice. You are assuming that the internet is firefox only. And you assume the problem is ipv6 related. Both are not mentioned in the posts mentioning the problem.

@ the problem owners ;)

.

firefox is th default browser in ubuntu.
this seems to be infested with this ipv6 problem.
since there is nothing much lost if one tries this i suggest this.
better than messing up with files.
if this does not work as in this case xperts such as you can pitch in.
i bow off!

---

### Post by mhkhosravi on 2006-08-12
I want to use Dial up internet
I have a serial modem (D-Link DFM-560EL) and it worked in PCLinuxOS and Fedora.
but there is no program to dial using this serial modem,

I tried "sudo pppoeconf" but it said that your network card is not detected and asks me if I want to detect it immediatly. when I say "yes" the error appears again :confused: 

to Slakkie : I dont think that "ping" do anything because I am not connected to any network. my modem is a dial up serial modem . 

I know that my modem must not be detected, it is serial and it only needs to recieve some AT commands via TTYS1.

but I dont know how ??? ](*,)

---

### Post by Dylan103 on 2006-08-12
System > Administration > Networking
Then choose Modem connection and click Activate, then edit the prefrences and restart you're computer.

---

### Post by mhkhosravi on 2006-08-12
I dont know what happend but now I have GPPP.
(I tried to install it before but I dont think I did it.)

but a new problem rised. after connection it disconnects after a few seconds. the firefox does not bring anything in this few seconds.

what is the solution for this problem ?

---

### Post by dmglouis on 2006-08-12
Okay, I connect to internet via a router which is through an ethernet cable. And whenever I try pinging, it says host unreachable.

---

### Post by drtvasudevan on 2006-08-13
mhkhosravi 
* To configure dialup


```

sudo pppconfig
```


* To connect dialup

```

sudo pon provider_name
```


* To disconnect dialup


```

sudo poff
```

---

### Post by mhkhosravi on 2006-08-13
Great! It works!!! 
Thanks alot <<drtvasudevan>>.

---

### Post by drtvasudevan on 2006-08-13
> **mhkhosravi said:**
> Great! It works!!! 
Thanks alot <<drtvasudevan>>.

=D>

---

### Post by dmglouis on 2006-08-13
Yes! I finally got internet working. I just did sudo dhclient and then tried pinging and that worked. So, I went to Firefox and google works perfectly!

---

