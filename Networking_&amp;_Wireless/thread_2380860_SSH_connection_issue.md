---
title: "SSH connection issue"
date: 2017-12-23
forum: Networking &amp; Wireless
---

### Post by marc raes on 2017-12-23
Hello. I'm Flemish. Excuse my English, as I will have to use a lot of words. I'll do my very best.

I have a small network at home. A ubuntu-computer (16.04), a macnotebook and a printer.
I managed to make the computer and the macbook communicate via SSH, installed on both machines.

Then I wanted to experiment and try to reach my ubuntu-computer at home, with my notebook via SSH from an other location (i.e. the place where I have my job).
It didn't work.
So, my question is: is this at all possible?

I did some reading [here]( https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding).

My provider is Telenet.
At home, on my Telenet-router, I forwarded port 22 and port 5900 (as recommended in the above documentation).
The known_hosts file in my ~/.ssh map on my mac, of course, has accepted the ip of my ubuntu-computer.
At my work-place I've a wifi-connection to a telenet-homespot. That I can't manipulate, of course. No port forwarding possible or whatever necessary.

At my work-place the notebook has an other ip. So I looked that up and proceeded, using the information of the documentation.

I tried: ```
ssh -R 5900:localhost(ip notebook at my work-place):5900 username@ip ubuntu-pc
```
No connection, there was a timeout.

Then I tried: ```
ssh -R 22:localhost(ip notebook at my work-place):22 username@ip ubuntu-pc
```
No connection, there was a timeout. 

So: 2 questions.

1. Can this überhaupt work?
2. If so, what did I do wrong, or what has to be done?

Thanks.

---

### Post by mikewhatever on 2017-12-23
To connect from work, you only need to know the external IP address of the router at home, and then:

```
ssh username@externalIP
```

, or

```
ssh -p portnum username@externalIP
```

if you want to specify a port other then the default 22. There is no need for local port forwarding.
The router at home should redirect connection requests on forwarded ports to internal IPs.

---

### Post by marc raes on 2017-12-23
That was the first thing I tried, but there was a timeout and it failed.
Is it then a question of giving the thing more time?

And then: what also puzzles me:
the difference between the ip of the router and the ip of the ubuntu-pc?

If I scan my lan, I find that the router ip=192.168.0.x
and that of the ubuntu-pc ip=192.168.0.xxx

On my lan I use the machine ip to log in.

So... do you mean I have to use the first one, when I log in from work?

And what about the fact that the notebook has another ip address on my work-place. I thought 
this did matter.
But I did a little experiment at home.
Originally, I made de ssh connection from mac to ubuntu, when the mac was on wifi.
Now, I connected the mac with the cable, and, of course, it acquired an other ip address.
So I connected to the ubuntu machine with ```
ssh my_user_name@ip_ubuntu_pc
``` and it works perfectly.

So, I conclude that the change of ip address of the mac on my work-place doesn't influence the procedure.

What is the matter then? I suppose the telenet-hotspot-server doesn't allow SSH-traffic... Is that it?

---

### Post by Hadaka on 2017-12-23
Hi..this is how it works...providing your ISP allows port forwarding..
*To access your home network/server from a remote/outside of your network
  i.e work,friends machine,other network.
*EXAMPLE..
Internet service provider ip... 123.456.789.10   <-your home network ISP

Local Router ip 192.168.0.1                            <-your home router ip

computer ip  192.168.0.230                             <-your home network computer/server

***FIRST**..find  YOUR isp address
Search  to find your isp address                       <-search from your home computer/server
```
www.whatismyip.com
```

***Then port forward Router**
**Router** port forward **PORT** to **COMPUTER** **IP ADDRESS**
*EXAMPLE                                                                      <-Your home router
**Router** port forward port **5900** to [B]192.168.0.230
[/B]
Then do..
***Command** 
```
ssh -p [ port ] [USERNAME@ISP Address]
```         <-from client -outside your network i.e from work

FOR ABOVE EXAMPLE..
```
**ssh -p5900 username@****123.456.789.10**
```  <- this should work for you
* provided you port forwarded port 5900 in the router to 192.168.0.230
*Your ISP allows port forwarding
*You added-allowed port 5900 in /etc/ssh/sshd_config
~# What ports, IPs and protocols we listen for
Hope this clears it up for you.
*Note..you CANNOT access your different machines within your lan with this method...i.e port forwarding
the above method is for accessing your server remotely.
*To access locally..within the lan ...
      simply do ssh -p5900 username@local_IP
 .............ssh -p5900 [email]marc@192.168.0.xxx[/email]

---

### Post by marc raes on 2017-12-24
@mikewhatever & @Hadaka,

Thank you very much for helping me out.

It's the first time that I tried to log in from outside my local network.

I simply did not realise you have to connect to the public address of your network router (and not to the ip of the local machine!... a fatal beginners mistake). And then make it forward to the local machine.
Thanks for pointing this out to me.

So I found the public address of my router, and also forwarded the default port for SSH - that is 22 - to the ip address of my local ubuntu-pc. And also uncommented portnumber 22 in the /etc/ssh/ssh_config file.
Then I simply used the command: ```
ssh <my user name>@<public ip address of my router>
```
And the connection was established.

After that I was also able to connect to my ubuntu-pc graphically, using FileZilla.

So... it seems the problem has been solved.

---

### Post by Hadaka on 2017-12-24
Glad to help , enjoy !...and
Thank you for marking your thread Solved.

---

