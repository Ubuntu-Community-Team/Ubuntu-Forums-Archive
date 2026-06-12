---
title: "How do I know via what port my ip address is connected?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by swarup on 2011-06-15
How do I know via what port my ip address is connected?

I want to try using some remote desktop servers and viewers besides the one that comes standard in Ubuntu. Such as vnc, rdp, and there are some others. But when you install and then start up any of these, they always request the port the host computer is on. So, is there a terminal command to find this out? "ifconfig" only tells you the ip address; not the port.

---

### Post by _0R10N on 2011-06-15
when applications require the port of the host machine, they're telling you to fill the port number the server is using to listen connections, not your own port.

Tipically client applications use non-privileged ports (above 1024) and they tend to change them frequently.

If you want to know what port number your applications are using locally, you can check in their respective configuration files or run

```
netstat
```

If you want to know what port number the server is listening in, then you should conctact its administrator and/or try de default ones. For example, 5900 for VNC.

Regards!

---

### Post by swarup on 2011-06-15
With vnc, I tried 5900 and it didn't work. Now, my host computer is using the default "remote desktop server" application, and the guest is using xtightvncviewer, or xvnc4viewer. Is that alright? Or do both computers have to use the same software to connect with each other?

My computer is the host computer. When I type "netstat" in a terminal, I just get a page of code. No information as to what port the host computer is on.

---

### Post by wep940 on 2011-06-15
*If* you are trying to do this from outside your network, then the way I understand it you need one of the services that provides a go between to get the actual IP address of your network access point and your computer on that network.  Unfortunately I don't know what they are called - I know someone else will know immediately what I'm thinking about and can post the name(s).  Basically there is some free service where once you are on the net you log to and then it sets up an IP at their server which in turns points to your PC.

If you are only doing this on your own network, there shouldn't be a need for this unless some of the servers you want to connect to have their own net access point but no dedicated registered domain.

Someone will hopefully correct me if I'm wrong - just going by things I think I remember correctly from the forum.

---

### Post by swarup on 2011-06-15
I am doing this from within my own house and within my own network. But all of the remote desktop utilities aside from the one which comes default with Ubuntu, request the port. So something has to be put there. They won't connect without it.

---

### Post by uRock on 2011-06-15
Please be aware that the netstat command gives more than just networking info.

---

### Post by swarup on 2011-06-15
When someone in my network connects to my computer to see my desktop i.e. my computer is host, and theirs is guest, then two factors are there in the connection-- IP address, and port. Is this correct? The various available "viewer" (as opposed to "server") applications, when opened in the guest computer, request the "port" of the host computer. What number is supposed to be put there. As I recall, there is a way of finding out what the port is i.e. 5200 or 5900 or whatever it may be. It seems I need this number in order for the guest computer to connect to the host. So how does one get that port number?

---

### Post by crispy_420 on 2011-06-15
Doesn't the port depend on the server software install? RDP and VNC by default use different ports (3389 & 5900) so it would depend how the client connects to your local machine. The most common forms of connecting in Linux remotely are via ssh (port 22) or VNC.

If you are talking about the default tools installed then you are using vino as the VNC server so the listening port is 5900. I don't believe their is any form of encryption by default so try not use on public networks.

Try running 'netstat -lnptu' to see which port is listening for vino. Did you maybe disable server or change default port since you can't connect?

---

### Post by wep940 on 2011-06-15
> **swarup said:**
> I am doing this from within my own house and within my own network. But all of the remote desktop utilities aside from the one which comes default with Ubuntu, request the port. So something has to be put there. They won't connect without it.

Just a thought - didn't know if it was intra or inter net.  Looks like everyone has you covered.

Best of luck! ;)

---

### Post by sandyd on 2011-06-15
> **swarup said:**
> With vnc, I tried 5900 and it didn't work. Now, my host computer is using the default "remote desktop server" application, and the guest is using xtightvncviewer, or xvnc4viewer. Is that alright? Or do both computers have to use the same software to connect with each other?

My computer is the host computer. When I type "netstat" in a terminal, I just get a page of code. No information as to what port the host computer is on.

```

netstat -l
```
should output something similar to
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State        
tcp        0      0 localhost:mysql         *:*                     LISTEN     

```
and no, this is inside an datacenter intranet (non-internet facing), so I don't mind.

YOur looking for stuff under the local Address

---

### Post by swarup on 2011-06-15
```
:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 [::]:5900               [::]:*                  LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:48984                 *:*                                
udp        0      0 *:mdns                  *:*  
```

There is a lot more code that then goes on to follow this. But I do see the number "5900" here. --So I guess that is the port right?

I've also just tried the suggestion given by crispy_420, and that gives the following.

```

:~$ netstat -lnptu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::5900                 :::*                    LISTEN      3637/vino-server
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:48984           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
:~$
``` 

So seeing both, it looks like the port is 5900. But one question-- crispy_420 had mentioned that the port is set by the server software install. So that means that different software on the same host computer will use different ports? If so, what does the "5900" number seen in the above code mean. In the first code at least, it doesn't specify which software it is for. Also, in the second code, it reads "3637/vino-server". Does that mean that the port is 3637?

---

### Post by jtarin on 2011-06-15
Are you using a router?

---

### Post by swarup on 2011-06-15
Yes, it is a Cradlepoint brand, mobile broadband router-- which is in turn connected to the internet via a Novatel U720 usb modem.

---

### Post by jtarin on 2011-06-15
> **swarup said:**
> Yes, it is a Cradlepoint brand, mobile broadband router-- which is in turn connected to the internet via a Novatel U720 usb modem.Whatever port you decide to use you'll need to open your router to that port.

---

### Post by alphacrucis2 on 2011-06-15
> **swarup said:**
> 

So seeing both, it looks like the port is 5900. But one question-- crispy_420 had mentioned that the port is set by the server software install. So that means that different software on the same host computer will use different ports? If so, what does the "5900" number seen in the above code mean. In the first code at least, it doesn't specify which software it is for. Also, in the second code, it reads "3637/vino-server". Does that mean that the port is 3637?

Yes. Different Server software use different ports. The only way two different server software can listen on the same port is if they are bound to different ip addresses. The port - ip address combination has to be unique, otherwise the tcp/ip stack wouldn't know where to deliver the incoming packets. vino-server is the name of the vnc server. The port ipp (internet printing protocol)= 631 is probably related to cups.

To test basic connectivity from the other PC. 

1. Can you ping <address of the server> 
2. Can you telnet <address of the server> 5900

---

### Post by swarup on 2011-06-15
It's been several years since I did those ping and telnet commands, and don't remember how to type it into the terminal. I guess on the guest computer it might just be "ping" followed by the host computer's ip address, right? 

At any rate, the below information may also be useful to you in confirming the above: 


When we use the default Remote Desktop Server and Viewer in Ubuntu, the two computers see each and other and connect just fine-- in fact this is the connection we have been using every day for years. But since the guest computer got updated to Ubuntu 10.10, for some reason the connection has been slow. That is, if I scroll up or down text in the host computer, he gets the new text as a wave appearing at the top of the monitor screen and rippling down to the bottom of the screen like a wave coming into the beach from the ocean. That sort of slow transmission never happened before. In reading around the web, it seemed that perhaps some of the other software out there might transmit the information more quickly and rid us of this problem. Hence the need to try different software. --Unless there is a way to change the settings in the default software so that it transmits and receives more quickly?

---

### Post by crispy_420 on 2011-06-16
No the 3697 is related to the running process and not the port number:


"tcp6   0   0 :::**5900**   :::*   LISTEN   3637/vino-server" (I trimmed some space to stay small)

Your port number is 5900 as is bold from the command I gave you. The 3697 is like a tracking number to keep track of the running processes and every process has one. It also allows you to kill a process by identifying what to kill via command line but this is off topic.

So are you trying to connect remotely as in the client (you) wants to view/control a session on a server (the other PC) at a different location? Or is this all being done locally? If you are doing remotely you will need to mess the router's settings (open ports and reserve IP addresses) to make this work. Also if your ISP uses dynamic IPs (most do) you will need a means locating yourself online. For that we will need a dynamic host tracking system like DynDNS, don't worry it is free.

If that is the case could you provide the exact model number of your router so I could review the manual? Local is nothing but remotely will take a bit of work. But let me see the manual first to ensure this is possible. Also I assume you have rights to change router settings right? Some ISPs lock people out of the equipment as do owners.

But over the internet I must warn VNC may not be the best choice as I believe it provides no security so sessions can be captured by others. For this route I would suggest the NX client/server model but that is my opinion.

---

### Post by wep940 on 2011-06-16
Exactly what I why I was asking if they were trying to access from outside their network (i.e., on the internet side of the router).  If it's just local traffic, I'm not sure you need to open the ports on the router - for some reason I was thinking that was for incoming traffic on the internet side of the router - but I'm probably wrong.  At any rate, glad you mentioned DYNdns as that was the site I was thinking of but couldn't remember the name to!

---

### Post by swarup on 2011-06-16
@crispy_420: Thanks for helping out :)

We are working in the same house, in separate rooms i.e. in separate offices. Both pc's are connected to the router via a wired ethernet connection.

The router is Cradlepoint MBR 1000 Mobile Broadband Router.

We don't mind VNC, if it is simpler. We never have any problems with folks capturing our sessions (that I know of). If the other connection type really is just as easy as VNC--and as fast--then I don't mind using it.

---

### Post by crispy_420 on 2011-06-17
This makes things much easier than I thought then. The security issues of VNC are mitigated if kept local so we can keep this simple. This is starting to sound like network issue or router misconfiguration.

Can they ping each other?
What is each PCs IP address and subnet?
These are some simple details that can impact connectivity. Some of these units put the wireless on a different network than the wired. Lets make sure that is not the case.

Is this the router? [http://www.cradlepoint.com/products/mbr1000-mobile-broadband-039n039-router-3g4g-wireless-router](http://www.cradlepoint.com/products/mbr1000-mobile-broadband-039n039-router-3g4g-wireless-router)

---

### Post by swarup on 2011-06-17
The site you referenced is indeed our router.

The two computers ping each other no problem. And they are both hard-wired to the router via ethernet cable, so there is no question of putting the wireless on a different network from the wired. At any rate to check this, I tested the ping with a third computer connected via wireless. That ping also works fine.

my computer's IP address and subnet: 

```
eth0      Link encap:Ethernet  HWaddr 00:26:4a:18:e9:0a  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
         

eth1      Link encap:Ethernet  HWaddr 00:26:bb:04:d6:a0  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
```

The other computer is the 192.168.0.198, with the same subnet mask.

My impression is that everything is working just fine. It is just that when using any software other than the default, those other softwares request information, such as the port, which I don't know.

There is also my question that do the two computers need to use the same remote desktop software. If mine is using the default software, than can the other one use any of these which I installed: Gnome-RDP, Grcm, Gtk VNC Viewer, QTNX, Remmina Remote Desktop Client/Viewer. Or for example, do both computers have to use RDP, or Gtk VNC Viewer, or whatever one.

edit: I got Gnome-RDP to work. And it is much, much faster than Ubuntu's default Remote Desktop software. So that basically solves the problem. Actually, a few days ago when I first installed it, I see that it was working fine then as well. It just tricked me, because when you click on "connect" from the guest computer, then a tiny "password screen" appears, where you have to type the host's password. And when you type in that screen, it doesn't show that you are typing anything-- but if you just type the password and hit ENTER, it works. The request to connect appears on the monitor of the host computer.

One last question with the Gnome-RDP, is that under preferences there is an option to type in the password and save it. Even though I do that, it still asks for the password. But let me check that again-- I should say that the tiny password screen appears as before, but perhaps it is sending the request on its own? I'll check and see if it does.

Now, the Gtk VNC Viewer I could not get to work. When I open that software on the guest computer, a window appears requesting 3 things: "Server (port), user name, password". When I put 5900 for port, and for user name I put the IP address (I also tried putting the user name "swarup" instead), and then the password and click on "connect", then immediately a message comes saying "You have been disconnected". It comes so quickly that it is obvious nothing was done, just the message came. So I must be putting some wrong information into the window I described?

Anyhow, Gnome-RDP is working-- and for that I am very happy and will mark this post as solved. If you have any further advice about the items I mentioned above, your suggestions and help are very welcome. :) Thank you.

---

### Post by wep940 on 2011-06-17
Glad you got things working!  It's much easier to do all of this when everything is local and not on the internet side of the router.  Be sure to thank crispy_420 as they worked great with you and had excellent advice.

---

### Post by swarup on 2011-06-18
Yes, you are right-- crispy_420 has been a great help. And others too who wrote in with suggestions. Thanks very much to you all! :)

---

