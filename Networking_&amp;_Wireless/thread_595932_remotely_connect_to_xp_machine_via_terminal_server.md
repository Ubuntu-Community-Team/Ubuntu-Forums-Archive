---
title: "remotely connect to xp machine via terminal server client"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by eekfonky on 2007-10-29
I have a colleague in France running XP on his PC. I need to remotely access his PC from my Ubuntu machine in Scotland. I know I can use Terminal Server Client, but how does he configure his PC to let me in? I have his IP address and he's trying to use TightVNC - any ideas?
After a while at my end it says connection timed out (110)

---

### Post by wolfsta on 2007-10-29
Hi Eekfonky

If you want to use terminal server client on your machine.  He will have to right click properties on my computer, then goto remote, and chose allow remote desktop connections.  It will allow the user he was logged in as to access his machine remotely.

Then he must forward the ports on his router to his desktop machine and this is different depending on what type of router he has.  Then you connect to his ip address.

If its just a once off connection try using something like [http://www.techinline.com/](http://www.techinline.com/) where you both connect to each other via the site. i have had good results with this site and think they allow a few free trials. 

Wolfsta

---

### Post by eekfonky on 2007-10-29
He has a 'SpeedTouch alcatel home' router and I cannot find out how to, or which port to forward. If Ihe can set this up does it mean that everytime he's online and I need access to his PC I can get it?
If so someone please explain how to allow remote access and how to port forward from his router. I can then post this conversation to him and we'd be sorted.
Thanks for any help

---

### Post by wolfsta on 2007-10-29
Go and find the specific router you need to forward ports on here and this page tells you how to do it :)

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

for remote desktop you need to forward port 3389  

NOTE  This is not recommended to do as it is a big security risk  remote desktop is not secured in anyway and if you know how its advisable to secure it with a vpn or tunnel it through ssh.

Those are kind of beyond the scope of this answer but ill try find some good links for you :)

Wolfsta

---

### Post by wolfsta on 2007-10-29
Just found this guide.

Looks pretty good.  I skimmed it but think it covers installing a windows ssh server and tunneling through that.

Have a nosey :)

[http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html](http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html)

Wolfsta

---

### Post by zaphod777 on 2007-10-29
> **wolfsta said:**
> Just found this guide.

Looks pretty good.  I skimmed it but think it covers installing a windows ssh server and tunneling through that.

Have a nosey :)

[http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html](http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html)

Wolfsta

I think you are getting it a little bit complicated. 

There should be a prety strait forward spot to forward the port 3389 to his ip address. just curiouse what ip address did he give you if it starts with a 192.168.X.X this is an internal ipaddress. you will need his external ip address he can get this by going to whatismyip.com 

in his router he can probably turn on romot administration under the admin tabe so you can can connect with port 8080 to his router using his public ip address. if he calls the support number for his router they can walk him through that or also forwarding port 3389.

---

### Post by zaphod777 on 2007-10-29
I think this link 

[http://theillustratednetwork.mvps.or...esktopSSH.html](http://theillustratednetwork.mvps.or...esktopSSH.html)

is for making RDP more secure but more complicated than what you need for your purposes.

---

### Post by wolfsta on 2007-10-29
Yeh it is getting complicated but like i said he can just forward the port if he wants.. sorry bit tired probably didnt word it right.

was just trying to give him the option of following that if he wanted to make it secure.

:)

---

### Post by zaphod777 on 2007-10-29
what time is it in new zeland? I have been here at work since 3 AM here in CA.

---

### Post by eekfonky on 2007-10-29
Ok, how does he forward the correct ports for his SpeedTouch Alcatel Home router?
IF someone can tell me that, you're saying I should be able to connect through Terminal Server Client easily - is that correct?

---

### Post by zaphod777 on 2007-10-29
Every router is slightly different. You need to check his default gateway 

start -> run -> cmd -> ok
ipconfig

check his ipaddress and default gateway by typing thedefault gateway into IE it will bring the config page for the router. 

if his IP address is anything other than a 192.168.x.x address it is a public ip address. From the looks of it it looks like that is a modem not a router if it is a modem then you should be able to use Remote Desktop to connect to his machine as long as RDP is enabled on his machine the username you are connecting with is an administrator and the firewall is disabled or RDP is added as an exception. 

[http://www.thomson.net/EN/Home/MiniSites/BAP/Telecom/SubCategory.html?category=DSL%20Modems](http://www.thomson.net/EN/Home/MiniSites/BAP/Telecom/SubCategory.html?category=DSL%20Modems)

If he is infact on;y using a modem I recomend he buy a router for the firewall properties.

---

### Post by eekfonky on 2007-10-29
I'll get him to try this, I'll let you know
Thanks for the help

---

### Post by wolfsta on 2007-10-29
@eekfonky

Go and find the instructions for you specific router on this page :)

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)


@ zaphod777

It was about 2AM when I sent that last post i think. its 9am now and im late for work hehe

---

### Post by zaphod777 on 2007-10-30
> **wolfsta said:**
> @eekfonky

Go and find the instructions for you specific router on this page :)

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)


@ zaphod777

It was about 2AM when I sent that last post i think. its 9am now and im late for work hehe

no worries. I was just a little confused why we were making it a lot more complicated for him when he was having troubles so far. Once he gets it working to begin with he can try and make it more secure. Have you actually heard of someone exploiting RDP(man in the middle or somthing)? I thought it was more of theoreticaly possible than proven proof of concept.

---

