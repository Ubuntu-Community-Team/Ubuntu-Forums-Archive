---
title: "&quot;Please check port 47887 UDP is open&quot;"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Mariane on 2010-08-12
Hi,

I have no router nor firewall. Yet Azureus wants me to check port 47887 is open. 

What should I do, please?

---

### Post by cj.surrusco on 2010-08-12
It wants you to forward the port on your router so that peers can easily connect. I'm assuming that you are connected directly to a modem? If so, then I believe that all ports are already forwarded to your computer. I'm not 100% sure, but I think that's how it works.

---

### Post by silverglade00 on 2010-08-12
How are you connected to the Internet? It could be blocked by your ISP. Do you have other computers in your house that work ok with Azereus?

---

### Post by Mariane on 2010-08-12
We share a wifi router and there is Azureus on another computer, which functions fine as far as I know. Before I was using ktorrent and it worked fine, I switched because Azureus downloads faster.

---

### Post by cj.surrusco on 2010-08-12
> **Mariane said:**
> We share a wifi router and there is Azureus on another computer, which functions fine as far as I know. Before I was using ktorrent and it worked fine, I switched because Azureus downloads faster.

First you said that you have no router, now you say that you have one. Which is it?

---

### Post by Mariane on 2010-08-12
Sorry, I meant on the computer. There is one wifi router in the building.

---

### Post by cj.surrusco on 2010-08-12
> **Mariane said:**
> Sorry, I meant on the computer. There is one wifi router in the building.

But your computer is connected to it, right?

---

### Post by jtarin on 2010-08-12
If it works on the other computer with the same router, then it will be forwarded on your Ubuntu install.

you can run the command  ```
netstat -an | more
``` and see if your application is listed by that port number.
(Piping the command through more will prevent the information from scrolling off the screen.) The following information should be displayed:

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State
tcp 0 0 127.0.0.1:1125 0.0.0.0:* LISTEN
tcp 0 0 127.0.0.1:1230 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN
tcp 0 0 192.168.1.1:22 192.169.3.1:1189 ESTABLISHED

The amount of information displayed will vary depending on your operating system.

---

### Post by Mariane on 2010-08-13
Thank you jtarin. 

What on Earth is all that??? :confused: 

After running jtarin's command I did:

```

netstat -an | grep 47887

```

This gave me:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State 
tcp6       0      0 :::47887                :::*                    LISTEN     
udp6       0      0 :::47887                :::*                               

(Header lines added after copying the result)

How do I interpret this? And how can I possibly have so many internet connections?

---

### Post by jtarin on 2010-08-13
That command is [netstat]("http://www.computerhope.com/unix/unetstat.htm#01"). It shows network status.There are more than several ways to use it.In this example you have used grep to find within netstat the port number 47887 and determine if it is open.You can also enter it like this ```
netstat -an |grep :47887 |wc -l
```

---

### Post by Mariane on 2010-08-15
Thanks. So when it says "LISTEN" it means it is opened, is that right?

---

### Post by jtarin on 2010-08-15
Yes......to listen is to be open, to be aware, to be quiet and hear.

---

### Post by KirbySmith on 2010-08-15
For Azureus (or for that matter Deluge) to fully work under Ubuntu, the same incoming port has to be opened on both the router AND on the PC.  This is because the PC under Ubuntu does not allow incoming connections without modifying whatever application (iptables maybe?) is controlling port access.  

I recall downloading from the software repository a program that allowed one to modify the access so Deluge would work.  I don't recall its name at the moment, and don't see anything that looks like it in the list of installed software.  I'll try to look for it further. 

kirby

---

### Post by KirbySmith on 2010-08-15
"Firestarter" R Us

kirby

---

### Post by jtarin on 2010-08-15
> **KirbySmith said:**
> For Azureus (or for that matter Deluge) to fully work under Ubuntu, the same incoming port has to be opened on both the router AND on the PC.  This is because the PC under Ubuntu does not allow incoming connections without modifying whatever application (iptables maybe?) is controlling port access.  

I recall downloading from the software repository a program that allowed one to modify the access so Deluge would work.  I don't recall its name at the moment, and don't see anything that looks like it in the list of installed software.  I'll try to look for it further. 

kirby
 I have no problems using torrent clients in Ubuntu using any port I've desired with my router. Whatever I have configured on my PC it is allowed. You can go into your router and explicitly set up one port for torrents but that negates the usage of random ports when it starts to prevent your IP from blocking on a certain port number.

---

### Post by KirbySmith on 2010-08-16
Ah! Perhaps the difference is that you allow Plug-n-Play to control what port opens in your router, and I deny permission for Plug-n-Play activity in the router.  This is a holdover from layered Windows security.  Fortunately,  (so far) I don't have an ISP that objects to my using the bandwidth I pay for.

kirby

---

