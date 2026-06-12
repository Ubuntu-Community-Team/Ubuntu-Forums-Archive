---
title: "SSH Questions"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-07-26
I've discovered the amazing SSH protocol and have been using it ever since. I just got a couple of questions. I've been reading up on the SSH manual and various articles on the internet but still have some questions;

1. I've messed around with setting up a tunnel and using it as a proxy in Firefox to surf the web securely when I'm at work etc. I've followed a youtube tutorial on this, which told me to use port 7070 for the 'Source Port' and set Destination to Dynamic in Putty. I understand 7070 is just a random port which is not being used at the moment, but why Dynamic? I don't understand the logic behind it, i'd love to understand why it works. Basicly all trafic on port 80 will be forwarded on port 7070 on the SSH server right?

2. Is it secure enough to use the default port 22 for SSHing? Or is random port more secure?

3. On my server, besides having an OpenSSH server running, I've got a WinXP VM which I can connect to remotely on my internal network. Is there a way to tunnel the trafic for remote desktop (port 3389 I believe)? So I can create a tunnel when I'm somewhere else and connect to the VM securely?

Thanks in advance :)

---

### Post by Bucky Ball on 2009-07-26
Remote desktop is default port 5900. Check the last post here:

[http://ubuntuforums.org/showthread.php?t=1219102](http://ubuntuforums.org/showthread.php?t=1219102)

... there is a link to a page which gives you good instructions for Remote Desktop through SSH. I have just set it up myself, as you'll see from that thread. My next step is getting it up over WAN (currently experimenting with computers on my LAN only) so interested to hear how you go.

Good luck. :)

---

### Post by dvdhaar on 2009-07-26
> **Bucky Ball said:**
> Remote desktop is default port 5900. Check the last post here:

[http://ubuntuforums.org/showthread.php?t=1219102](http://ubuntuforums.org/showthread.php?t=1219102)

... there is a link to a page which gives you good instructions for Remote Desktop through SSH. I have just set it up myself, as you'll see from that thread. My next step is getting it up over WAN (currently experimenting with computers on my LAN only) so interested to hear how you go.

Good luck. :)

Thanks :)
Isn't the default port for Windows Remote Desktop 3389? Probably if I open that port in my router to the VM I can connect to it when at work but I want (if possible) to connect through an SSH tunnel.

---

### Post by Bucky Ball on 2009-07-26
Sorry, vncserver (which is for both OS) default 5900. There is a link on the link for ssh tunneling.

---

### Post by Liolikas on 2009-07-26
Oioi that is beginner question go networking or other real man question. ;)

---

### Post by snova on 2009-07-26
> **dvdhaar said:**
> 2. Is it secure enough to use the default port 22 for SSHing? Or is random port more secure?

SSH itself is quite secure (use keys though, or at least strong passwords), and I don't see how changing the port will affect that. But it will make it less obvious for script kiddies, and that is a good thing for your logs (having asked someone who knows more about this than I, SSH is the only service he suggests changing the port for).

---

### Post by LookTJ on 2009-07-26
You can use putty as a ssh tunnel and then setup firefox to use the socks port. 

:)

or if you use Linux

```
ssh -D port-number user@host
```and still setup firefox to use the socks port

EDIT:

The socks port can be set in the proxy settings

EDIT 2: More info on the -D flag, which should explain why dynamic

```
   -D [bind_address:] port
              Specifies a local ``dynamic'' application-level port forwarding.
              This works by allocating a socket to listen to port on the local
              side,  optionally bound to the specified bind_address.  Whenever
              a connection is made to this port, the connection  is  forwarded
              over  the  secure  channel, and the application protocol is then
              used to determine where to connect to from the  remote  machine.
              Currently the SOCKS4 and SOCKS5 protocols are supported, and ssh
              will act as a SOCKS server.  Only root  can  forward  privileged
              ports.   Dynamic  port  forwardings can also be specified in the
              configuration file.

              IPv6 addresses can be specified with an alternative syntax:
               [bind_address/] port or by  enclosing  the  address  in  square
              brackets.   Only the superuser can forward privileged ports.  By
              default, the local port is bound in accordance with the Gateway&#8208;
              Ports setting.  However, an explicit bind_address may be used to
              bind the connection to a specific address.  The bind_address  of
              ``localhost''  indicates  that  the  listening port be bound for
              local use only, while an empty address or `*' indicates that the
              port should be available from all interfaces.
```

---

### Post by scorp123 on 2009-07-26
> **dvdhaar said:**
>  I understand 7070 is just a random port which is not being used at the moment, but why Dynamic? I don't understand the logic behind it, i'd love to understand why it works. Basicly all trafic on port 80 will be forwarded on port 7070 on the SSH server right? Try the following experiment:

1.) open a terminal window

2.) open Firefox, start surfing. Yes. Just that. Surf around. Open tons of web pages ...

3.) While the web pages are loading, type this into your terminal:
```
netstat -tlan
```

**_Question:_**  What do you see?


**_Answer:_**

Probably something like this (taken from my computer):

```
tcp        0      0 192.168.1.2:34440       72.233.69.4:80          ESTABLISHED
tcp        0      0 192.168.1.2**[COLOR="Red"]:56277[/COLOR]**       82.165.83.254**:80**        TIME_WAIT  
tcp        0      0 192.168.1.2**[COLOR="Red"]:52336[/COLOR]**       91.189.90.211**:443**       ESTABLISHED
tcp        0      0 192.168.1.2**[COLOR="Red"]:34435[/COLOR]**       72.233.69.4**:80**          TIME_WAIT  
tcp        0      0 192.168.1.2:52333       91.189.90.211:443       ESTABLISHED
tcp        0      0 192.168.1.2:52337       91.189.90.211:443       ESTABLISHED
tcp        0      0 192.168.1.2:56291       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:52339       91.189.90.211:443       ESTABLISHED
tcp        0      0 192.168.1.2:56296       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:34438       72.233.69.4:80          ESTABLISHED
tcp        0      0 192.168.1.2:56295       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:56288       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:51365       208.43.202.10:80        ESTABLISHED
tcp        0      0 192.168.1.2:34437       72.233.69.4:80          TIME_WAIT  
tcp        0      0 192.168.1.2:34436       72.233.69.4:80          TIME_WAIT  
tcp        0      0 192.168.1.2:56293       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:34441       72.233.69.4:80          ESTABLISHED
tcp        0   1477 192.168.1.2:46335       174.36.30.67:443        ESTABLISHED
tcp        0      0 192.168.1.2:52338       91.189.90.211:443       ESTABLISHED
tcp       38      0 192.168.1.2:36656       174.36.30.67:443        CLOSE_WAIT 
tcp        0      0 192.168.1.2:46240       188.121.36.239:80       TIME_WAIT  
tcp        0      0 192.168.1.2:56297       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:52310       91.189.90.211:443       ESTABLISHED
tcp        0      0 192.168.1.2:56289       82.165.83.254:80        TIME_WAIT  
tcp        0      0 192.168.1.2:52335       91.189.90.211:443       ESTABLISHED
tcp        0      0 192.168.1.2:34434       72.233.69.4:80          ESTABLISHED
tcp        0      1 192.168.1.2:46336       174.36.30.67:443        SYN_SENT   
tcp        0      1 192.168.1.2:34439       72.233.69.4:80          FIN_WAIT1  
tcp        0      0 192.168.1.2:51481       64.4.241.49:443         ESTABLISHED
tcp        0      0 192.168.1.2:52334       91.189.90.211:443       ESTABLISHED
tcp       38      0 192.168.1.2:57843       174.36.30.66:443        CLOSE_WAIT 
tcp        0      1 192.168.1.2:46337       174.36.30.67:443        SYN_SENT   
tcp        0      0 192.168.1.2:56294       82.165.83.254:80        TIME_WAIT 
```

See the output above?  192.168.1.2 is my computer. I am surfing. You can tell by the many many connections that have port 80 and 443 open on the connection's destination ...

But what about the origin of the connection? Bingo. Look at those numbers. What ports are open? 56294, 46337, 57843, 52334 ...

taaadaaaa ....

There is your answer. Yes, port 80 is used **_on the target_** for HTTP communication. But the connection can originate on **_any port_** **between 1024 and 65535** ... And that's why you need to use the "Dynamic" option :D  (... unless you have talents at Tarot cards or a really really good crystal ball it will not be possible to foretell the TCP port your browser will use to initiate the connection ... !! )

---

### Post by dvdhaar on 2009-08-23
Thanks alot for the explanation :) I realy appreciate it. I get it now! 

Most of the time I'm using Windows to SSH into my server and use a proxy. How would I go about forwarding, for example port 3389 to the Windows machine I'm working on? So I can use Remote Desktop via localhost:3389? I'm not sure if it works that way though?!

Thanks alot :)

---

### Post by HiImTye on 2009-08-23
I dont believe that vinagre understands the windows remote desktop protocol so you will need to use VNC most likely

---

