---
title: "Internet not working"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by ashish_envy on 2010-05-27
I m using ubuntu 10.4 & using ubuntu first time....
Having 2 lan Card (1st onboard , 2nd external )
I have filled the IP address , netmask , gateway .
DNS server and next option is blank...
what to do now ?

I hav type few comnds in terminal 

mii-tool 

SIOCGMIIPHY on 'eth0' failed: Operation not permitted 
SIOCGMIIPHY on 'eth1' failed: Operation not permitted 
SIOCGMIIPHY on 'eth2' failed: Operation not permitted 
SIOCGMIIPHY on 'eth3' failed: Operation not permitted 
SIOCGMIIPHY on 'eth4' failed: Operation not permitted 
SIOCGMIIPHY on 'eth5' failed: Operation not permitted 
SIOCGMIIPHY on 'eth6' failed: Operation not permitted 
SIOCGMIIPHY on 'eth7' failed: Operation not permitted 
no MII interfaces found 


ashish@ashish-desktop:~$ ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:84:be:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:19:d1:13:4c:1f  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:4d:84:be:e8  
          inet addr:169.254.11.135  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:803 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:803 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:66948 (66.9 KB)  TX bytes:66948 (66.9 KB) 


now tell me what should i DO ....
pls help me ?
PLs .....

---

### Post by germanix on 2010-05-27
I am not I understand what you are doing. What do you mean you are using two LAN cards? Normally you would only have to plug the LAN cable from your router to you PC and Ubuntu will automatically connect you to your router and you will only need to enter your network password. So what is different from your system? I have never had to do what you seem to be trying? Pleas give more information on how your setup is before anyone could really help.

---

### Post by ashish_envy on 2010-05-28
Hey pls help ........
is there is no one who can solve my problem 
my Internet is not working in ubuntu 10.4.
and i am new to ubuntu & don't know how to figure it out .......
Pls help me

---

### Post by skippuff54 on 2010-05-28
Provide us with some additional information about your setup and your goals.

Are you trying to do anything special like make your own router or do you just need an Internet connection? These are both wired interfaces, correct?

What kind of Internet service do you have (i.e. cable or DSL)?

---

### Post by Jakiejake on 2010-05-28
> **ashish_envy said:**
> I m using ubuntu 10.4 & using ubuntu first time.....

Then how come your accounts 2 years old???

---

### Post by Elfy on 2010-05-28
> **Jakiejake said:**
> Then how come your accounts 2 years old???

Perhaps they started account and then went away and have now come to use ubuntu.

Your post is pointless and bean chasing and brings nothing whatsoever to the OPs issue - don't do it - thank you.

---

### Post by Jakiejake on 2010-05-28
> **forestpiskie said:**
> Perhaps they started account and then went away and have now come to use ubuntu.

Your post is pointless and bean chasing and brings nothing whatsoever to the OPs issue - don't do it - thank you.

Excuse Me but how fast do you browse the fourms? I was just on a thread with you on it and now your on this one... Anyway I know... Off Topic :confused:

---

### Post by Elfy on 2010-05-28
> **Jakiejake said:**
> Excuse Me but how fast do you browse the fourms? I was just on a thread with you on it and now your on this one... Anyway I know... Off Topic :confused:

:lol:

Not been up long - sitting here with a cup of tea waiting for the day to start

I sit in this and the General Help forum when I escape from the Cafe :p

That's enough off-topic for now methinks :)

---

### Post by krtica on 2010-05-28
Did you try it without manual configuration?
Just by using auto/DHCP option?

---

### Post by ashish_envy on 2010-05-29
Ubuntu is totally new for me .....
ya i agree that my account is 2 yr old at dat time i had made an account because i am having shell scripting in my course , so for dat reason i made an account .

bt now i don't know wat to do....
my net is not working in ubuntu bt working fine in window's 
is there's any one who can tell me the whole procedure by which i just wanted to connect through d net...
i have type some cmds 

mii-tool
ifconfig -a 

bt not know wat to do ...
pls help me in this ....

---

### Post by dineshs on 2010-05-29
Are you using both ethernet ports? Do you have a DSL modem connected to one port?

---

### Post by ashish_envy on 2010-05-29
i m using only one port and ADSl2 modem of beetel is connected to it.

---

### Post by dineshs on 2010-06-01
Method-1
You can configure NM  using the DSL tab.There is provision for filling username and password
Method-2
Use pppoeconf command
ref
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) 
Method-3
Configure your modem for always on internet connection.For this open firefox and type 192.168.1.1 in the address bar and proceed.
ref
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

---

