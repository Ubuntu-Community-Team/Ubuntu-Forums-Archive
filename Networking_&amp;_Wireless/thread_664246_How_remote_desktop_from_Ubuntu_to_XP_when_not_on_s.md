---
title: "How remote desktop from Ubuntu to XP when not on same network?"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by AegisTalons on 2008-01-11
So I have a laptop and a desktop that I'm pretty much always running Ubuntu unless I need SolidWorks in XP. The thing is sometimes I want to connect from my laptop to my desktop while I am at school. The school is obviously on a different network than my home network. 

How do I connect to the desktop from the laptop SECURELY? I know I can use Terminal Server Client  to Remote Desktop to XP or Ubuntu when on the same network. Any ideas?

---

### Post by stalker145 on 2008-01-11
> **AegisTalons said:**
> So I have a laptop and a desktop that I'm pretty much always running Ubuntu unless I need SolidWorks in XP. The thing is sometimes I want to connect from my laptop to my desktop while I am at school. The school is obviously on a different network than my home network. 

How do I connect to the desktop from the laptop SECURELY? I know I can use Terminal Server Client  to Remote Desktop to XP or Ubuntu when on the same network. Any ideas?

You should be able to use the same program to connect to your computer even on a different network. Just enter the IP address/domain name into the connection dialogue and connect. Another option is to use NoMachine, FreeNX, or the like. Those options require additional software to be installed, but they are secure also.

I use the TSC client to connect to the Win2K computer at my wife's work all the time. It's on a different, and very slow I might add, network and has worked flawlessly in the past.

---

### Post by AegisTalons on 2008-01-12
If I find my true IP address, will I be able to connect to the desktop securely? What protocol does TSC use to remote desktop to XP? Also would I have to do anything special for the router, such as port forwarding or something like that?

---

### Post by Zarathu on 2008-01-12
Open port 3389 TCP, and if you're using Windows XP Professional (which you should be), make sure those checkboxes are checked in "My Computer" > "Properties" > "Remote" tab.

:D

---

### Post by AegisTalons on 2008-01-12
Does anyone know what protocol Microsoft's Remote Desktop use? Is it some sort of propriatary protocol or SSH? Also does anyone know how secure is it remote desktoping when you are not on the same network?

Zarathu thanks for the TCP port!

Zarathu I tried out your recommendation and it works out. I looked up my IP address and used that. It took a lot longer as expected. I think it was considerably longer than normal because double of the amount of traffic going out to look for the ip address and in to the same ip address. (I was testing the connection from CAMPUS while I was at home. Hopefully, its faster on campus.) Thanks again everyone that helped.

---

### Post by Sektion9 on 2008-01-12
Most simple and easy to set up, [http://www.logmein.com](http://www.logmein.com)

-S9-

---

### Post by balaji.ramasubramanian on 2008-01-12
Can you or anyone please write a good HOW-TO on this? 

Let me explain the need for this:

1. Remote Desktop utility is not very well documented.
2. The real use of Remote Desktop is across the internet
3. Will Remote Desktop work on my home computer if it has DHCP connection? I want to access my laptop at home from office. Another case is access my mother's computer when she is close to a thousand miles away on the internet through an entirely different ISP
4. Any ports that need to be forwarded, any changes in configuration to Ubuntu, services that need to be started (like running an SSH server if needed) etc.
5. Recommended softwares for remote desktop on Ubuntu. The desktop I wish to connect to could be either a Windows xP/ Windows Vista/ Ubuntu machine. All three are possible.

It would be great if someone can kindly help and write a nice HOW-TO on this.

---

### Post by AegisTalons on 2008-01-13
I might write one up later tonight after I finish fixing my house.

---

### Post by Sektion9 on 2008-01-13
> **balaji.ramasubramanian said:**
> 
1. Remote Desktop utility is not very well documented.
2. The real use of Remote Desktop is across the internet
3. Will Remote Desktop work on my home computer if it has DHCP connection? I want to access my laptop at home from office. Another case is access my mother's computer when she is close to a thousand miles away on the internet through an entirely different ISP
4. Any ports that need to be forwarded, any changes in configuration to Ubuntu, services that need to be started (like running an SSH server if needed) etc.
5. Recommended softwares for remote desktop on Ubuntu. The desktop I wish to connect to could be either a Windows xP/ Windows Vista/ Ubuntu machine. All three are possible.


Actually it is very well documented.
[http://www.portforward.com/cports.htm](http://www.portforward.com/cports.htm)
[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Access)
[http://en.wikipedia.org/wiki/Remote_Desktop_Protocol](http://en.wikipedia.org/wiki/Remote_Desktop_Protocol)
[http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software](http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software)

These are just a few of the links that came up in searching Google in less than 60 seconds.

-S9-

---

### Post by AegisTalons on 2008-02-06
So I was looking around and I was having an issue with VNCing into my machine remotely because of my router. So I finally figured out that I need forward port 5900. I think I saw a security issue being discussed by forwarding VNC ports.

---

