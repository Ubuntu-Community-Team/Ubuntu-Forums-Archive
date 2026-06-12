---
title: "Apache / Firewall Help"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by superkAyjnr on 2007-05-06
Hello everyone, Im using Ubuntu 6.06 Dapper Drake Desktop Version but I just have a problem with my Apache web server ( Or another program ). Other people outside my LAN cannot access my website, streamed music server, and photo gallery. I have already forwarded ports 80 & 8888 On my DI-524 D-Link router. I used Firestarter and made Policy's allowing Ports 80 & 8888. But after all that, No one can still connect to my website.

I can connect to my website by typing in localhost in my Web Browser, My DynDNS also works and i can access my Website on my LAN. I have tried typing in my IP as well and i can connect. It seems That apache is only allowing LAN connections? Because i have used my other PC in my Network & it connected just fine. Im abit lost here, Im sorta new to the Ubuntu Server things. So could anyone help me out here please?

Im not sure of what logs / information you want so if you need anything, Just ask me & ill try to put it up.

Im having thoughts about My ISP Blocking Port 80, But i cant be sure because after opening port 80, I did an online port scan of Port 80 and got results that it was on Stealth. What do you guys think? If so, How can i change my Apache's default port to another port?

Here are screenies of my Router, Firestarter Rules & A port Scan

IM just curious though. In the Firestarter Policy Section. Theres also a section on the bottom called " Forward Service, Firewall Port, To, & Port " I currently only added the Ports 8888 & 80 to the " Allow service, Port, For " section, Am i inputting the ports into the wrong section? Also, Do i have to add the ports to Both sections?

Thanks for taking the time to look at this :)

---

### Post by superkAyjnr on 2007-05-06
Added a Port scan to show that Port 80 Is opened

---

### Post by netztier on 2007-05-06
> **superkAyjnr said:**
> Added a Port scan to show that Port 80 Is opened

That just shows that port 80 is reachable from localhost.

**netstat -napt** might have told you the same:

Example from my internal server:
```

marc@blaze:~$ **sudo netstat -napt**
Password:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:672             0.0.0.0:*               LISTEN     3882/rpc.statd      
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     3831/smbd           
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3375/portmap        
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     3753/hddtemp        
tcp        0      0 0.0.0.0:664             0.0.0.0:*               LISTEN     4301/rpc.mountd     
tcp        0      0 0.0.0.0:32925           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     3831/smbd           
tcp        0      0 172.20.125.30:445       172.20.125.31:40866     ESTABLISHED11308/smbd          
[COLOR="Red"]tcp6       0      0 :::80                   :::*                    LISTEN     11066/apache2       [/COLOR]
tcp6       0      0 :::22                   :::*                    LISTEN     3847/sshd           
tcp6       0      0 :::443                  :::*                    LISTEN     3847/sshd           
tcp6       0   0 ::ffff:172.20.125.30:22 ::ffff:172.20.125.31:45912 ESTABLISHED11309/sshd: marc [p 
marc@blaze:~$ 
```

This shows that the apache2 process has port in "LISTEN" state on your system. This is a combined IPv4/IPv6 system, so the output on your server might look a little different.

> **superkAyjnr said:**
> Im having thoughts about My ISP Blocking Port 80, But i cant be sure because after opening port 80, I did an online port scan of Port 80 and got results that it was on Stealth. What do you guys think? If so, How can i change my Apache's default port to another port?

I think your ISP is most probably blocking Port 80, as a lot of them do today - this protects the large number of people inadvertedly running an unpatched and unmaintained IIS on their Windoze boxes. What does the online port scan tool say about the meaning of "stealth" - how should "stealth" be interpreted? I presume that your ISP is just silently dropping incoming TCP SYNs for port 80/tcp 

Check the file **/etc/apache2/ports.conf**. You'll have to figure out via apache2 documentation which syntax the entries to this file must adhere to - it's either one line per port, or maybe it's a comma-separated list per line.

best regards

Marc

---

