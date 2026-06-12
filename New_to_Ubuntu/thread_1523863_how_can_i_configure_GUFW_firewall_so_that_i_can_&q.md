---
title: "how can i configure GUFW firewall so that i can &quot;see&quot; other pc's on home network?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-07-04
hey i'm having a problem.  when my gufw firewall is enabled i can't "see" network shares or other pc's on my network.  within a minute of disabling the firewall i can then "see" the other pc's in Places>>> Network>> windows network>>> workgroup  (by the way the name workgroup is my workgroup for simplicity) i am unsure as to how to do the exception.  I had it working by doing the ip address from the other computer(s) to my IP and vice versa though I have dhcp enabled and sometimes I get a different ip address.  there are less than 10 pc's and other wireless devices in my home.  is there a way to write an exception like 192.168.1.1/10 ?? or what would i do?  i'm confused cuz I had this working and now it's not.  thanks! ps do i need to use a certain port? is that what the little box to the right of the area for the ip address is used for?  i don't believe i did that last time. i'm trying to use the new ip address i got that's listed when i do a "ifconfig" command.  i don't understand i thought i could just go and put in my new ip and it would work but it's not. i know it a firewall issue on this linux box because as soon as i disable i can see the rest of the pc's on the network!!!!!!! arrrgggghhhh!! please help lol

---

### Post by handydan918 on 2010-07-04
On most home networks, you are behind a router, which likely uses NAT (network address translation). This makes it virtually meaningless to even have a firewall, since the network is not visible from outside the router. 
All of that aside, since a default install of Ubu has no services listening on any ports, there is no need for a firewall anyway.
Not sure what sort of issue you're trying to address, but if it's just post-Windows trauma, relax.

If you want to see how visible you are from the outside, go to [www.grc.com](www.grc.com)

---

### Post by bodhi.zazen on 2010-07-04
Yes you can whitelist your LAN , 

```
sudo ufw allow from 192.168.0.0/24 to your_ip_address
```

See :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

See also the post above.

It is better if you understand  the traffic you need to allow to "see" your other computers. What protocol are you wanting to allow ? ping ? samba ?

---

### Post by bradmayne04 on 2010-07-05
> **bodhi.zazen said:**
> Yes you can whitelist your LAN , 

```
sudo ufw allow from 192.168.0.0/24 to your_ip_address
```See :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

See also the post above.

It is better if you understand  the traffic you need to allow to "see" your other computers. What protocol are you wanting to allow ? ping ? samba ?

i tried what you said from the bash and then enabled my firewall.  no good.  I tried to mount a share from the windows computer and i received an error message saying that it couldn't mount the share.  I tried what you said anyways just using the direct ip address instead of /24.  (this was before your post.)  neither your /24 or my direct ip exception worked.  i disabled the firewall and can mount other pc shares as normal... Anyone else have any idea's???  I also understand what your saying about coming from windows.  What I am trying to figure out though is why did this work before (using a direct ip of the other pc(s) on my network and it doesn't work now?) or using the /24 as the gentleman suggested as well?

---

### Post by bradmayne04 on 2010-07-05
no good.  see above....

---

### Post by bodhi.zazen on 2010-07-06
Well, your network is 192.168.1.0/24 ....

```
sudo ufw allow from 192.168.1.0/24 to your_ip_address
```

---

### Post by bradmayne04 on 2010-07-06
> **bodhi.zazen said:**
> Well, your network is 192.168.1.0/24 ....

```
sudo ufw allow from 192.168.1.0/24 to your_ip_address
```

dude don't take this the wrong way cuz i know your trying to help but you already said that.  I know that.  instead of repeating we have to try other idea's.  This doesn't make sense that it worked before when i gave a direct ip address from the windows box and then stopped working like that. it's very strange because nothing and i mean nothing changed on that windows box that controls the printer and nothing has changed on my laptop that is running ubuntu.  I tried your bash command like you said a few times IT DOES NOT WORK WE HAVE TO MOVE ON TO ANOTHER IDEA.  I got my ip from the ifconfig command which gives this output:
eth1      Link encap:Ethernet  HWaddr c4:17:fe:4f:12:19  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fe4f:1219/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1395 errors:0 dropped:0 overruns:0 frame:4
          TX packets:1314 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1203135 (1.2 MB)  TX bytes:258765 (258.7 KB)
          Interrupt:17 
so my address is 192.168.1.4 there's something wrong but i don't know what.

---

### Post by mastablasta on 2010-07-06
Can you ping the windows computer?
 
Go to Windows console and type ipconfig to see the win computer address. then try to ping it from linux. Also the address you get you can whitelist it in the firewall and that should get you access.
 
maybe he means like this?:
```
sudo ufw allow from 192.168.1.0 to 192.168.1.4 
```
 
This would (should - i am guessing here) open access to all computers from IP range 192.168.1.0 to 192.168.1.4 (which is home network)

---

### Post by frodon on 2010-07-06
You should find the answer to your issue there :
[https://answers.launchpad.net/gui-ufw/+question/72444](https://answers.launchpad.net/gui-ufw/+question/72444)

---

### Post by 3rdalbum on 2010-07-06
1. Dude, if you're on a LAN, then you are behind some sort of NAT filtering firewall anyway and you do not need a firewall on the client.

2. bodhi.zazen's second post in this thread has a slightly different command that may work, if you persist in running a firewall on your client PC.

---

### Post by bodhi.zazen on 2010-07-06
> **mastablasta said:**
> Can you ping the windows computer?
 
Go to Windows console and type ipconfig to see the win computer address. then try to ping it from linux. Also the address you get you can whitelist it in the firewall and that should get you access.
 
maybe he means like this?:
```
sudo ufw allow from 192.168.1.0 to 192.168.1.4 
```This would (should - i am guessing here) open access to all computers from IP range 192.168.1.0 to 192.168.1.4 (which is home network)

Can you provide more details ?

Post your ufw rules

```
sudo ufw status verbose
```

Enable your logs and see what is being dropped.

---

### Post by vedovatti on 2011-03-02
Hi there,
I know that the threat is a little bit old but I just wanted to help to anybody that has this problem.

I had the problem that I couldn't see the other PC through Samba using nautilus if "gufw" is activated. 

The problem for me was that adding preconfigured rule automatically with gufw >Edit>Add Rule in the tab "Preconfigured" it will add: on the rules
```

135,139,445/tcp    ALLOW IN    Anywhere
137,138/udp        ALLOW IN    Anywhere

```
**So basically UFW doesn't undertand rules with more than one port on the rule.** or at least with my UFW on Ubuntu 10.04 it didn't.
So what I did is to added one by one >Edit>Add Rule on the "Simple" tab:
```

135/tcp     ALLOW IN    Anywhere
139/tcp     ALLOW IN    Anywhere
445/tcp     ALLOW IN    Anywhere 
137/udp     ALLOW IN    Anywhere
138/udp     ALLOW IN    Anywhere

```
Finally I can access to Samba but when I make a request to other Windows machines, they don't use these ports to communicate back so you have to allow that from the IP under your submask. Unfortunately I couldn't do it with GUFW so in a Terminal:
```
sudo ufw allow from 192.168.2.0/24
```
Adapt the IP number to your submask and that would do the trick. At least for me it worked it out and I can see and share Samba and have the firewall activated.
Hope it helps to somebody

---

