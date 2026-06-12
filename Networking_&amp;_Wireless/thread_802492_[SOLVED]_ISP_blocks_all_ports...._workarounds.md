---
title: "[SOLVED] ISP blocks all ports.... workarounds?"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by jacksmash on 2008-05-21
Hi,

I just found out from my ISP that they block all ports for incoming traffic. I've just been wanting to use SSH to connect to my server from another computer.

I did a port scan to see what info I could come up with. The scanner I used told me that ports 21 (ftp) and 110 (pop3) were open... so I suppose my ISP can't really be blocking everything.

Anyways, are there any suggestions as to how I can get around this?

---

### Post by bluefrog on 2008-05-21
ask your ISP to be sure and if yes, switch ISP

---

### Post by jacksmash on 2008-05-21
> **bluefrog said:**
> ask your ISP to be sure and if yes, switch ISP

I did ask my ISP. I'm out in the boondocks and do not have another option for high-speed. Am I outta luck?

---

### Post by YokoUno on 2008-05-21
You can force the ssh server to listen to another port than 22, e.g. 110
Have a look at /etc/ssh/sshd_config

Then use this on the machine you connect from:
```

ssh -p 110 username@xxx.xxx.xxx.xxx

```

---

### Post by jacksmash on 2008-05-21
> **YokoUno said:**
> You can force the ssh server to listen to another port than 22, e.g. 110
Have a look at /etc/ssh/sshd_config

Then use this on the machine you connect from:
```

ssh -p 110 username@xxx.xxx.xxx.xxx

```

Good thought... but 110 is used for pop3, so even if I change the sshd_config I still can't connect.

---

### Post by Luke has no name on 2008-05-21
> **jacksmash said:**
> Good thought... but 110 is used for pop3, so even if I change the sshd_config I still can't connect.

Sure you can, if you're not using your server for pop3.

---

### Post by jacksmash on 2008-05-21
> **Luke has no name said:**
> Sure you can, if you're not using your server for pop3.

Hmm... but when I try "ssh -p 110 user@xxxxxxxxx", it just sits there and does nothing. I changed the config file to listen to 110, and I did restart ssh.

---

### Post by YokoUno on 2008-05-21
Ok, so you have servers using your ports 21 and 110 already, right?
If so, sure you'll have a conflict if you try and make ssh listen to any of the two ports.

But on second thought, did you interpret correctly your port scan?
Do you have proof that your ISP filters out incoming traffic, on their behalf (docs, contract, reputation, and the like...)

Seems really odd that services allowed by your ISP are the same as those you implemented on your server. Even more so, it's odd that they don't allow a web server which is the most common service one can think of.

What I mean is: let ssh listen on port 22, but open and **forward** port 22 to your server's ip in the configuration panel of your modem/router. Then retry your port scan. The results should help you to conclude sensibly on what you can do...

But I could miss the point completely :biggrin:
Please tell us more about your ISP then.

Also, post the output of this command, executed on your server:
```

sudo netstat -tape

```
This will tell what daemons are listening, and on what ports.

---

### Post by SpaceTeddy on 2008-05-21
if your ISP blocks any incoming SYN Packets (um - those are the ones that establish TCP connections) you can open pretty much any port you want - you will not be able to get any connection - at all. 

The only thing i could (maybe) think of that could (maybe) work for you is to tunnel through a udp connection into your network, and then overlay the tcp connection on that one. 
And now so other understand what i am says : use openvpn. That can use UDP, which does not have the SYN packets, just raw data. But if your ISP is any good, they can filter those pakets aswell.

So the question is - do they block ALL ports, all PROTOCOLS or just below 1024 ? what exactly is their block policy ???

PS: i'd try to use a port above 1024, i.e. in the non-privilegdes range... for starters...

---

### Post by jacksmash on 2008-05-22
> **YokoUno said:**
> Ok, so you have servers using your ports 21 and 110 already, right?
If so, sure you'll have a conflict if you try and make ssh listen to any of the two ports.

But on second thought, did you interpret correctly your port scan?
Do you have proof that your ISP filters out incoming traffic, on their behalf (docs, contract, reputation, and the like...)

Seems really odd that services allowed by your ISP are the same as those you implemented on your server. Even more so, it's odd that they don't allow a web server which is the most common service one can think of.

What I mean is: let ssh listen on port 22, but open and **forward** port 22 to your server's ip in the configuration panel of your modem/router. Then retry your port scan. The results should help you to conclude sensibly on what you can do...

But I could miss the point completely :biggrin:
Please tell us more about your ISP then.

Also, post the output of this command, executed on your server:
```

sudo netstat -tape

```
This will tell what daemons are listening, and on what ports.

Ok... just to be clear, I called my ISP, and they had one of their techs call me back (it's just a local ISP for people out in the country, like myself). They said in their own words that they "block all ports for incoming traffic", and that if I want to get a connection I will have to connect from my server to another (remote) computer first.

So, I downloaded a piece of software that scans ports, and from my Windows box it showed 110 and 21 as being "open". This was from the windows partition of the computer which I have as a server - so the server wasn't running at the time.

Also, I did set up my router to forward ports 22 and 80 (using the server IP address 192.168.1.103.

Here is the output from netstat:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name   
tcp        0      0 *:imaps                 *:*                     LISTEN     root       17438      5511/dovecot        
tcp        0      0 *:pop3s                 *:*                     LISTEN     root       17440      5511/dovecot        
tcp        0      0 localhost:mysql         *:*                     LISTEN     mysql      16764      5026/mysqld         
tcp        0      0 *:pop3                  *:*                     LISTEN     root       17439      5511/dovecot        
tcp        0      0 *:imap2                 *:*                     LISTEN     root       17437      5511/dovecot        
tcp        0      0 *:www                   *:*                     LISTEN     root       17913      5716/apache2        
tcp        0      0 localhost:ipp           *:*                     LISTEN     root       22956      4902/cupsd          
tcp        0      0 *:smtp                  *:*                     LISTEN     root       17234      5323/master         
tcp        0      0 joel-ubuntu.local:58721 ohiggins.canonical.:www TIME_WAIT  root       0          -                   
tcp        0      0 joel-ubuntu.local:58722 ohiggins.canonical.:www TIME_WAIT  root       0          -                   
tcp        0      0 joel-ubuntu.local:58718 ohiggins.canonical.:www TIME_WAIT  root       0          -                   
tcp6       0      0 *:ssh                   *:*                     LISTEN     root       16411      4776/sshd           
tcp6       0      0 *:telnet                *:*                     LISTEN     root       17025      5173/inetutils-inet 

```

Also, I have tried ports above 1024 as mentioned by SpaceTeddy.

---

### Post by SpaceTeddy on 2008-05-22
ok, if your ISP tells you they block all incomming ports, then there is little you can do besides the thing the tech guys told you - have an external relay. This basicially means that you create a connection from your internal network to a server/computer somehwere on the internet, and use that connection to pass traffic from the internet to your. 
This is a lot of work, tho, and it requires a computer somewhere else (not in your house...)

or so i understood your post. 
What ports you have open doesn't matter at all if your ISP blocks anything. The traffic simply won't get through - at all... 

sorry to bring the bad news :(

---

### Post by jacksmash on 2008-05-22
Ok - that's kind of what I figured - just wanted to have someone verify my thinking.

Thanks everyone. I'll marked this as 'solved'.

---

