---
title: "SSH and Proxy Questions"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by dieselpower on 2008-02-07
```

My office is connected with a 64KBit ISDN line to the internet, so the maximum transfer rate is about 7K/s. You can speed up the connection by compressing it: when I download files, Netscape shows up a transfer rate of up to 40K/s (Logfiles are compressable by factor 15). SSH is a tool that is mainly designed to build up secure connections over unsecured networks. Further more, SSH is able to compress connections and to do port forwarding (like rinetd or redir). So it is the appropriate tool to compress any simple TCP/IP connection. "Simple" means, that only one TCP-connection is opened. An FTP-connections or the connection between M$-Outlook and MS-Exchange are not simple as several connections are established. SSH uses the LempleZiv (LZ77) compression algorithm - so you will achieve the same high compression rate as winzip/pkzip. In order to compress all HTTP-connections from my intranet to the internet, I just have to execute one command on my dial-in machine:

ssh -l <login ID> <hostname> -C -L8080:<proxy_at_ISP>:80 -f sleep 10000

<hostname> = host that is located at my ISP. SSH-access is required.

<login ID> = my login-ID on <hostname>

<proxy_at_ISP> =the web proxy of my ISP

My browser is configured to use localhost:8080 as proxy. My laptop connects to the same socket. The connection is compressed and forwarded to the real proxy by SSH. The infrastructure looks like:

                  64KBit ISDN
My PC--------------------------------A PC (Unix/Linux/Win-NT) at my ISP
SSH-Client         compressed        SSH-Server, Port 22
Port 8080                             |
 |                                    |
 |                                    |
 |                                    |
 |10MBit Ethernet                     |100MBit
 |not compressed                      |not compressed
 |                                    |
 |                                    |
My second PC                         ISP's WWW-proxy
with Netscape,...                    Port 80
(Laptop)

```

I found this howto and am going to try it and see if it help our dialup speeds and some of our ISP's stupid port blocking, but I had a simple question first. My ISP does not allow SSH connections, so I need to change some things. Namely using one of my internet-connected servers instead of my ISP

I have not played with SSH and proxies before, so where it says <proxy_at_ISP>, can I just point it to my servers gateway, or do I need to set up some sort of proxy software on the server to make it work? If I do need a real proxy, what is best?

---

### Post by amo-ej1 on 2008-02-08
What ssh -L 1234:192.168.1.1:8080 user@1.2.3.4 does is the following.

* It will first ask you to log in to 1.2.3.4 with the password of user 
* Then it will open port 1234 on your local machine. 
* All traffic directed towards your local port 1234 will end up at port 8080 of host 192.168.1.1 which is BEHIND 1.2.3.4

So you setup a tunnel which puts all traffic which is directed to a local port to a remote host at a specific port behind a gateway. 

Btw, in the drawing -C is used for compression, but the main reason people want to use ssh tunnels is for encryption, not necesarily for compression.

So you're simply linking two ports together, it doesn't _need_ to be proxy, it can be anything, you could ssh to a certain host. Let's try a silly example

ssh -L 1234:[www.google.com:80](www.google.com:80) user@127.0.0.1

If you open a browser now, and connect to [http://127.0.0.1:1234](http://127.0.0.1:1234) it will show google homepage. So here you use it for simple http forwarding.

So it all depends what you _really_ want to do, if you want  to forward a single port, ssh at your local and your remote computer is sufficient. If you want to be able to surf the internet you will need forwarding to a proxy (otherwise you would need to create an infinite amount of tunnels to visit each site your want).

---

### Post by HermanAB on 2008-02-08
Note that SSH can also provide a Socks 5 proxy.  So you could tunnel somewhere and tell SSH at the far end to run a Socks proxy and set your browser at your local end to use it transparently through the tunnel.  Read the man page and snail book for details.

---

### Post by dieselpower on 2008-02-08
Thanks, I'll try the socks proxy, because I am wanting to use it for compressing my dialup connection.

---

### Post by dieselpower on 2008-02-08
I've tried all different ways of doing this, but to no avail. Is there any other server setup required besides just being on the net? I mean, my servers have multiple IP adressess, serve pages, and work normally otherwise, but ssh/socks just won't work. This is the code I'm using.

```
ssh -fND9998user@orbwireless.net
```

and then configuring Firefox to use localhost:9998. Sometimes when trying to load bookmarks, firefox asks what I want to do with a PHP file, if I open it in kwrite it's empty. 

Also, how do I stop a connection started like this without killing my other ssh sessions?

Sigh, I wish my ISP would allow ssh logins...

---

### Post by kevdog on 2008-02-08
ssh [email]-fND9998user@orbwireless.net[/email]

should this be:
ssh -fND9998 [email]user@orbwireless.net[/email]

Within firefox or other brower just set the SOCKS proxy (not http or ftp -- leave these blank) to 127.0.0.1 port 9998.

---

### Post by dieselpower on 2008-02-09
Thanks! Sometimes I can be such a dumb*ss, I had the HTTP proxy set and the "all others" checkbox checked. it works great now.

---

### Post by dieselpower on 2008-02-10
OK this works great except for occasional timeouts in firefox. I can't find timeout settings anywhere in firefox, but it's definitely more liveable than plain old dialup. I get about 2.5 to 4 times the page load speed using this (actually that's basackwards, but you know what I mean), and I think it could be better if I could get it to accept no encryption, but I have not figured that out yet. I'm going to try it on my DSL connection at the office too. This beats any speed booster, ever.

Now I just need to figure out how to get my dialup server to only serve the SOCKS proxy on the local network so all the local PC's don't have to worry about proxy stuff..

Anyway, here is the command that I have found works best so far. Try it out!
```

ssh -carcfour -CfND9998 -oTCPKeepAlive=yes user@host

```

Actually, I'm thinking of writing some python code to allow compressing all web traffic with lzma e -d25 -si -so. It would probably make use of tun/tap interfaces. Anyone interested in helping? This is where I wish I knew C++.

Lawrence

---

### Post by kevdog on 2008-02-10
Im a little confused -- meaning you dont want to use a cipher to encrypt the data???

I see you are using the arcfour encryption algorithm -- is this the fatest of all the choices?: (aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,
arcfour256,arcfour,aes192-cbc,aes256-cbc,aes128-ctr,
aes192-ctr,aes256-ctr)

I dont know the answer to the above question!

Again for the DSL connection I would use no data compression.  For the dialup connection, what is wrong with the gzip compression scheme as used in ssh??

---

### Post by dieselpower on 2008-02-10
> **kevdog said:**
> Im a little confused -- meaning you dont want to use a cipher to encrypt the data???

I see you are using the arcfour encryption algorithm -- is this the fatest of all the choices?: (aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,
arcfour256,arcfour,aes192-cbc,aes256-cbc,aes128-ctr,
aes192-ctr,aes256-ctr)

I dont know the answer to the above question!

Again for the DSL connection I would use no data compression.  For the dialup connection, what is wrong with the gzip compression scheme as used in ssh??

I'm not worried about encryption, just a fast connection. After all, it's been plain ol HTTP until now.

From [http://www.employees.org/~satch/ssh/faq/manpages/ssh1_man.html](http://www.employees.org/~satch/ssh/faq/manpages/ssh1_man.html)
> 
arcfouris an algorithm published in the Usenet News in 1995.This algorithm is believed to be equivalent with the RC4 cipher fromRSA Data Security (RC4 is a trademark of RSA Data Security). This isthe fastest algorithm currently supported


Why no compression on DSL? If you have fast enough computers, it will still help. I would like to use lzma 26 on my dialup connection
See this for more info on network compression performance. [http://www.linuxjournal.com/article/8051](http://www.linuxjournal.com/article/8051) If you could double the speed of your DSL line, wouldn't you use compression? I'm going to experiment with my DSL line as soon as I get a chance and I'll report back.

lawrence

---

### Post by kevdog on 2008-02-10
Again your apparent bandwidth is going to be perceived by the actual transfer rate along with the overhead to decrypt/encrypt packets.  If your bandwidth is sufficient, why would you want to compress and add the extra processing?

---

### Post by dieselpower on 2008-02-12
Because we have some amazing processors at our fingertips today. BW is expensive, nobody has enough, and I think it's a great waste of a PC to give yourself half as much BW again as you had. In my case, I have a dialup line at home that is very slow, and 3Mb DSL lines at work. I pay $172/month for each DSL line, if I can get 4 Mb through it that makes $57 each month that I will not have to pay to the telco. I have tried OpenVPN before and it did slow the connection down, but I'm finding that SSH helps a lot. Now if you have a fast enough network, or slow enough procassor that SSH would slow it down, the of course, don't run it! Also, encryption is totaly different that compression, if I could keep SSH from encrypting the data I would, but it seems that SSH2 does not have that option anymore, that's why I'm writing a Python system to use LZMA for dialup acceleration. After all, there are STILL a lot of people stuck on dialup, and none of the commercial accelerators work.

---

### Post by lespaul_rentals on 2008-02-12
Sorry for hijacking the thread but I have a quick question.  At school/work I am behind an HTTP proxy.  I am able to SSH into my home server and use command-line browsers such as links2, lynx, w3m, etc. to access websites that would otherwise be blocked.  How would I go about accessing a SOCKS from behind the school/work proxy?  Right now, this setup works fine:

Workstation at school --> school proxy --> home server

In Putty (my workstation runs on XP..:() I tell it to use an HTTP proxy, just like you would use to browse with Firefox, Opera, you know.  So it goes through the HTTP proxy just fine, and I login and work on my server at home.  However, what I want to do is the following:

Workstation at school --> school proxy --> home server --> SOCKS tunnel --> workstation at school

Will I be able to bind a port to my localhost on my workstation, considering I have to go through the HTTP proxy?  Thanks.

---

