---
title: "ssh outside local network"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by miceagol on 2007-04-06
I've configured my Ubuntu PC such that it's possible to use ssh to get into it from any computer on the Local network with
```

ssh <user name>@<ip address of computer>

```
This works great. But I'm also trying to log onto the computer from outside the LAN, and therefore have to go through a router. I've configured "port forwarding" (through port 22) on the router, so that I'm automatically forwarded to the PC I want to go to. I'm using the command 
```

ssh <user name>@<ip address of router>

```
but it doesn't work. It then hangs before it times out. **What am I forgetting?** I found my ip address through [this website]("http://checkip.dyndns.org/").

---

### Post by MeneM on 2007-04-06
Hi,

As far as I can tell you, you need to indeed port forward TCP port 22 from the outside to the inside.

It is therefore also desirable to have your computer inside the network on a static lease instead of a DHCP lease.

You see, when DHCP gives your computer a new IP address, the port forward no longer works, and it could indeed result in a connection attempt to "time out" seeing as that there is no longer a pc listening on the older ip address.

Check out [this]("http://portforward.com/routers.htm") site for help about your particular router.

Also try [grc.com]("https://www.grc.com/x/ne.dll?bh0bkyd2") on your LAN pc to see if the port forward is indeed working.

---

### Post by miceagol on 2007-04-06
> **MeneM said:**
> Hi,

As far as I can tell you, you need to indeed port forward TCP port 22 from the outside to the inside.

It is therefore also desirable to have your computer inside the network on a static lease instead of a DHCP lease.

You see, when DHCP gives your computer a new IP address, the port forward no longer works, and it could indeed result in a connection attempt to "time out" seeing as that there is no longer a pc listening on the older ip address.


I didn't really get this. The ip address given to the computer doesn't change that fast. In fact, the router tends to give each computer the same address as it previously gave it. The ip address of my computer did correspond to the port forwarding setup at the time of testing. Do you mean that this has nothing to say, and that I should make it static anyway?

What are the disadvantages of having static ip addresses?

> **MeneM said:**
> 
Check out [this]("http://portforward.com/routers.htm") site for help about your particular router.

Also try [grc.com]("https://www.grc.com/x/ne.dll?bh0bkyd2") on your LAN pc to see if the port forward is indeed working.


I actually already used those websites. :) I used the first one to set up port forwarding on my router. Port 22 is now forwarded to the ip address I wish. I also used the other one to check out port 22, but I don't really understand the result. I clicked "user specified custom port probe", and it told me that port 22 was in stealth mode and that this was good. What does this mean in connection with my issues?

---

### Post by MeneM on 2007-04-07
> I didn't really get this. The ip address given to the computer doesn't change that fast. In fact, the router tends to give each computer the same address as it previously gave it. The ip address of my computer did correspond to the port forwarding setup at the time of testing. Do you mean that this has nothing to say, and that I should make it static anyway?

Ah good then, you already tried that route. You see, it's something many overlook. A static lease has the same properties as a DHCP lease. There are no differences in operation.
Only one: Static never changes IP address. DHCP could, in the future, change ip adresses.

> ...and it told me that port 22 was in stealth mode and that this was good. What does this mean in connection with my issues?

From that I gather that either your router is not forwarding the connections (however unlikely due to the fact you seem to have extensively checked this part) or your computer is not answering to connection attempts.

It would be handy if we could see the contents of ```
/etc/hosts.deny
``` if it exists;
The output of executing ```
sudo iptables -L
``` on the command line;
And the contents of ```
/etc/ssh/sshd_config
```
(attach the results of the above as attachments if you could please.)

And anything else you may feel is appropriate.

---

### Post by miceagol on 2007-04-07
I've attached all the files you asked for, including hosts.allow. The output of iptables is:
```

target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Both hosts.allow and hosts.deny seem to be empty.

> 
Static never changes IP address. DHCP could, in the future, change ip adresses.


Ok, just what I thought. :) If it gets annoying I will go static, but first the port forwarding should work with the current setup.

---

### Post by MeneM on 2007-04-07
So there's no firewall, nothing stopping the connection.

Is the server actually running? try: ps ax | grep sshd. You should see something like:
```
vserver:/home/mark# ps ax | grep sshd
 3979 ?        Ss     0:00 /usr/sbin/sshd
 8467 ?        Ss     0:00 sshd: mark [priv]
 8479 ?        S      0:00 sshd: mark@pts/0
 8753 pts/0    S+     0:00 grep sshd

```

The first line shows "/usr/sbin/sshd" meaning my sshd server is running. Do you get that as well?
(I think you will as it is running when you connect from the inside of the network)

If that does not help figuring this out. Then I'm getting fresh out of idea's. Try a different port number to forward, setup a quick apache server and see if you reach your temporary webserver from the outside (if so, you know it is the sshd config somewhere)

Oh, try setting "ListenAddress" to ListenAddress <the_ip_address_of_the_sshd_server>

---

### Post by miceagol on 2007-04-07
> **MeneM said:**
> 
So there's no firewall, nothing stopping the connection.


To be honest, I think this is the problem. The router is a SMC 2804WBRP-G with a built-in firewall. Port forwarding is in order, and I've enabled the ssh port under "special applications". I thought this might open the port if it's being blocked by the firewall. My settings under special applications is:

```

Trigger Port  	Trigger Type  	Public Port  	Public Type  	Enabled
<ssh port>       TCP              <ssh port>      TCP                X
<ssh port>       UDP              <ssh port>     UDP                X  

```

> 
The first line shows "/usr/sbin/sshd" meaning my sshd server is running. Do you get that as well?
(I think you will as it is running when you connect from the inside of the network)


This seems to be allright. My output is
```

4270 ?        Ss     0:00 /usr/sbin/sshd
6047 pts/0    R+     0:00 grep sshd

```

> 
If that does not help figuring this out. Then I'm getting fresh out of idea's. Try a different port number to forward, setup a quick apache server and see if you reach your temporary webserver from the outside (if so, you know it is the sshd config somewhere)


I've changed ssh from the standard port to another port already for security reasons. I edited the sshd_config file accordingly, and restarted the sshd server.

How do you set up a quick Apache server? :confused: 

> 
Oh, try setting "ListenAddress" to ListenAddress <the_ip_address_of_the_sshd_server>

Is the ip address of the sshd server the same as the ip address to the router I'm trying to connect to?

If I try
```

ssh <user name>@<ip address of router> -p <ssh port>

```
at this point, I get the error message
```

ssh: connect to host <ip address of router> port <ssh port>: Connection refused

```
Does this imply a firewall problem? Btw, is it wrong to test this within the local network, i.e. using the PC I'm testing on also to test from?

---

### Post by miceagol on 2007-04-07
I seem to have solved this partially. :) In addition to my LAN router, I have a WAN router. The latter is sort of unecessary, since the LAN router can do the WAN router's function.

Anyhow, I configured port forwarding on the WAN router too, and now Shields up! reports the ssh port as being open. Still when I try to connect i get connection time-out. It's possible that I have configured the port forwarding on the WAN router incorrectly. I've told it to forward the ssh port to my LAN router, but I'm uncertain if this is the correct ip address. In my LAN router's WAN information, it lists a WAN IP and a Gateway IP. Is WAN IP the correct one?

---

### Post by miceagol on 2007-04-07
You can ignore my earlier questions. I've now investigated further, and tested that the port forwarding actually works. :)

I used a function on the ADSL modem called default server that forwards all ports to a specified ip address. I used the ip address of my router here. Shields up! now reports all ports as closed opposed to stealth before. The exception here is the ssh port which is open. If I now disable the port forwarding of this port on my router, Shields Up! reports the port as closed. All this must mean that port forwarding works all the way to my computer.

But still I get a time out when I try to connect. Any ideas? Is it wrong to test this inside the local network I'm trying to connect to and not from outside? Maybe I must use a static ip?

---

### Post by eentonig on 2007-04-07
Are you trying to connect to your public ip address from within your LAN network? Most routers/FW devices will always fail to allow this.

A better test would be to have a friend try if it works.

---

### Post by MeneM on 2007-04-07
["monotonous"]("http://www.freedict.com/onldict/onldict.php") (Saai betekent boring, eentonig is monotonous ;-) is right, if you try to connect to the public IP address from inside the network, you will get nothing. On most routers anyway.

If you'd like contact me via one of my chat networks so you can give me your ip. Do not need any passwords or anything like that, just to see if I can get a login prompt.

---

### Post by miceagol on 2007-04-07
MeneM and I managed to solve it. Conclusion: Don't try to connect to your PC from within the LAN. You have to do it from outside, unless you want time-outs. ;)

Thanks everyone for your help.

---

### Post by eentonig on 2007-04-07
> **MeneM said:**
> ["monotonous"]("http://www.freedict.com/onldict/onldict.php") (Saai betekent boring, eentonig is monotonous ;-) ....

Actually, both translations are correct. I hesitated a long time before picking one. Both boring just sounded more boring then monotonous. And I figured that more non-native english speakers would know the word boring.

---

### Post by MeneM on 2007-04-07
Yeah I guess you are right... But why the name "eentonig" though? Why would you call yourself that? :confused:

---

### Post by eentonig on 2007-04-07
Because I am?:lolflag: 

Long story short. Few years back, I needed a hotmail account to collect my spam. After trying all possible combinations with my name and numbers (which al were in use) I started to find it rather monotonous to keep trying names. I figured 'eentonig' would not be in use. And since I was right, I kept using that nick on all forums were I subscribe. And I keep using it for my spam accounts.

---

### Post by MeneM on 2007-04-07
Ah, So I keep sending you spam by replying to this post ;-P

In my case MeneM came from my real name: Mark M*******. Initials: M en M. When you say that quickly, you get: MeneM.

Later on it made even more sense as my wife also has the initials M and M.

I'm almost afraid to admit it, but my two sons also both have the same initials: MM. Oh dear, I just realised: I'm burgerlijk!! (translation: middleclass,)

...

#-o

---

### Post by miceagol on 2007-04-08
Hehe... Now I understand your Dutch comments. Btw, I'm a big Within Temptation fan, so I'm sort of used to try understanding Dutch here and there. ;)

While we're at it. My name is a mix between my real name Michael and Sméagol. It was during the Lord of the Rings hype I wrote down a bunch of mixes between Michael and Lord of the Rings characters. Chose Micéagol, and have used it ever since.

---

### Post by MeneM on 2007-04-08
This could get into a cool thread :) 
Although I never much cared for the Smeagol character, your nick is a nice combo / mash-up.

Perhaps we should move the remainder of the topic to the cafe? Any mod here that can do a topic split for us?

---

### Post by miceagol on 2007-04-10
Actually, there's already [such a thread]("http://ubuntuforums.org/showthread.php?t=347944&highlight=user+name") in the cafe... :KS

---

