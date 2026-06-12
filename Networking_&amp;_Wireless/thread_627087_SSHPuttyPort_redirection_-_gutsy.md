---
title: "SSH/Putty/Port redirection - gutsy"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by TechMansoor on 2007-11-29
I can actually get to the firewall that is running open ssh via putty and make changes to the firewall and such. But re-direction doesn't work on ubuntu via putty(tunnels section - 192.168.x.x:3389 or 5900 going out on port 3390). It works fine if I do the same thing via a windows workstation. Is there something I need to enable on my gutsy workstation?

---

### Post by TechMansoor on 2008-01-22
I still have yet to figure this one out.

You know in putty if you wanted to use remote desktop and assign a port to go out on, i.e 3345, 4456,3390 etc.? If I do that, and try local redirection, i.e 127.0.0.1:3345 in terminal services or krdc, I can't get to the workstation I need to get to.

Does anyone know what I mean, am I making myself clear? I want to make sure everyone understand this..

---

### Post by kirsche on 2008-01-22
i guess you want to do forwarding?

Machine1 will create a tunnel to machine2, which forward RDP to Machine3:

ssh -L 12345:192.168.0.2:3389 192.168.0.100

kirsche@cherry:~$ sudo netstat -anp | grep -i -E ".cp.*list.*"
tcp        0      0 127.0.0.1:12345         0.0.0.0:*               LISTEN     6261/ssh            
tcp6       0      0 ::1:12345               :::*                    LISTEN     6261/ssh            
kirsche@cherry:~$ 

I can then rdp to the target (Machine3) by connecting to 127.0.0.1:12345
If this is what you wanted to achieve...

---

### Post by TechMansoor on 2008-04-29
> **kirsche said:**
> i guess you want to do forwarding?

Machine1 will create a tunnel to machine2, which forward RDP to Machine3:

ssh -L 12345:192.168.0.2:3389 192.168.0.100

kirsche@cherry:~$ sudo netstat -anp | grep -i -E ".cp.*list.*"
tcp        0      0 127.0.0.1:12345         0.0.0.0:*               LISTEN     6261/ssh            
tcp6       0      0 ::1:12345               :::*                    LISTEN     6261/ssh            
kirsche@cherry:~$ 

I can then rdp to the target (Machine3) by connecting to 127.0.0.1:12345
If this is what you wanted to achieve...


This is exactly what I needed but, I needed to use putty doing it. The syntax you outputted was in relation to openssh right? I'm trying to have this done via putty and still can't do it correctly in herdy heron,but of course it works fine in windows.

---

### Post by gyterpena on 2008-05-09
I have similar problem port redirection is kind of broken I'm able to redirect port 9999 but nothing else. If I try any other port it will not shown open if I scan localhost with nmap.

---

### Post by kevdog on 2008-05-09
I dont get what you guys are trying to do?  Can you enlighten me?

---

