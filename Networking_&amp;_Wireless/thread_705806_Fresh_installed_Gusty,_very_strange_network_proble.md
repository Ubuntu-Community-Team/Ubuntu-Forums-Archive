---
title: "Fresh installed Gusty, very strange network problem"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by cool2121 on 2008-02-23
I just installed successfully Gusty 7.10 on a AMD64 desktop. It worked fine at my home until i moved it to my friend's place. I connected it to D-Link DI-624 router, and got assigned IP fine. I can ping local IP and outside fine ([www.google.com](www.google.com)). 

However, i cant get access to the internet. Every other clients connected to the router connect to the internet fine tho.

I tried : apt-get , Firefox,...etc I cant get accessed at all. 

I disabled IPv6, still not working..

Can someone please help? 

This system will be running as TV server at my friend's house. It worked fine at home tho... strange. Also at the NM-applet (network applet), it doesnt show "Wired connection" when i left click on it. 

I used cmd line and checked, it seems fine (connected). My etc/network/interfaces shows what it should be with DCHP.

---

### Post by mrsteveman1 on 2008-02-23
Ok so going in order here:

You can ping local IPs, so the IP settings are correct
You can ping remote IPs, so the default route works
You can ping remote domain names, so the DNS servers are working

For DNS to work UDP traffic has to get through, so thats fine (At least port 53 is fine), and for ping to work ICMP traffic has to pass through the router, so that appears to be fine.

Is iptables setup with any rules? Check sudo iptables -L

If you can ping a domain name, all 7 layers of the network stack work, which means something is selectively blocking HTTP traffic, OR it means something on the system is selectively not working, perhaps proxy settings are wrong somewhere?

---

### Post by cool2121 on 2008-02-23
As far as i know, there is no proxies in the network. 

sudo iptables -L  just shows all policy accept. I dont understand what it means tho.

Also its not just HTTP, apt-get doesnt connect for update/install. 

I can ping any domains. But i cant even go into web configuration of the router (192.168.0.1)

Any ideas?

---

### Post by mrsteveman1 on 2008-02-23
It sounds like an application problem to me, like i said since pinging a domain works, the entire network stack works.

Is it possible that gnome has a proxy set somewhere? I know there are no proxys on the network but some apps might be trying to use one for some reason.

I can't think of anything else that would prevent apps from connecting even while you can ping a domain.

Iptables is the firewall on Linux, if it says accept on all of the 3 main classes, it means it shouldn't be blocking anything at all.

What happens if you boot into the livecd or into windows?

---

### Post by cool2121 on 2008-02-24
boot into Windows XP, then i can access internet like other clients. 

Even if its application error, then why nothing else can access the internet but ping? 

Apt-get doesnt get connected as well, and neither wget. 

And it worked fine back home with my DDWRT router.

ps. i forgot to bring the liveCD with me so i couldnt test it.

ps2. I dont know if this means anything but if the cable un plugged, FF quickly says "unable to connect" as opposed to "connecting......" for a long time.

---

### Post by kaginken on 2008-02-24
Post your iptables:

sudo iptables -L

---

### Post by cool2121 on 2008-02-24
My iptables -L show all policy accept. 

However here is a good news (might be not).....

IT MAGICALLY WORKS again. Here is what i did: 

I boot into windowsXP once again. I did some networking testing in WindowsXP to make sure its not hardware related. The Nic works perfectly fine. So i reboot into Gusty again. 

This time my network interface is not eth0 any more, Its eth1 with a NEW mac address.... (wth?)

I quickly notice nm-applet icon shows "Wired connection" if i left click on it. (i was like could it be.,...). Yes open up FF and it loads the homepage....(whoot), apt-get install/update etc... all connecting works fine now.

Nonetheless, i'm afraid to reboot my comp now. What would happen next? I'm guessing all this weird things are due to driver of the Nic. Its Realtek  8111/8168B, gigabit onboard NIC.

---

### Post by kaginken on 2008-02-24
I'll take full credit, must have been the iptables -L command I gave you  :lolflag:

Fortunately, linux can run for Years w/o a reboot, so - never reboot again!!!  

All joking aside - I'd bet you're good to go now - guess we'll find out next restart.

Rock on!  :guitar:

---

### Post by marcfell27 on 2008-02-24
I'm having exactly the same problem

[http://ubuntuforums.org/showthread.php?t=705905](http://ubuntuforums.org/showthread.php?t=705905)

cool212: what exact network tests in XP did you do???? Spent all day searching forums, and the overall response I've got is router is blocking port 80, but I don't know how to check this.

help, thanks

---

### Post by kaginken on 2008-02-24
to test port 80 being blocked - just telnet into the port on the host like so:

telnet <host-ip> 80

if it connects, you'll know because the screen will go blank and you'll just see a cursor.  To verify, type:

GET 

and hit <enter>.  You'll see the contents of the index.html page in text scroll by...

Conversely, if your router is blocking port 80, the telnet command will timeout after a minute or so, depending on your servers config...

hope this helps!

---

### Post by cool2121 on 2008-02-24
Very... embarassed to say this..,. 

I didnt have any network tools at the time because its a fresh installed windowsXP. So i used several ways to test the network. 

FTP
HTTP
bit torrent (uTorrent)
LAN sharing.

I just make sure everything works and the network bandwidth being tressed for an amount of time. 

Then i reboot...

Note that altho my problem has been fixed. But its not logically explained yet. I dont know why my ethernet is not the same. 

I would say your problem is driver related. Did it work with live CD?

---

### Post by kaginken on 2008-02-24
Not sure which is worse - still having a technical issue, or having it 'fix itself' and you don't know wtf happenned!  :D

---

### Post by marcfell27 on 2008-02-24
> **kaginken said:**
> to test port 80 being blocked - just telnet into the port on the host like so:

telnet <host-ip> 80

if it connects, you'll know because the screen will go blank and you'll just see a cursor.  To verify, type:

GET 

and hit <enter>.  You'll see the contents of the index.html page in text scroll by...

Conversely, if your router is blocking port 80, the telnet command will timeout after a minute or so, depending on your servers config...

hope this helps!

thanks, is the <host> the modem 10.0.0.138 or the router 192.168.30.1????

---

### Post by kaginken on 2008-02-24
<host> is the machine running the webserver, on the other side of the router from where you're trying to hit it.

I'm assuming you have something like this now:

pc/laptop  -->  router/firewall   -->  webserver (listening on port 80).

Is this correct?

---

### Post by marcfell27 on 2008-02-24
> **kaginken said:**
> <host> is the machine running the webserver, on the other side of the router from where you're trying to hit it.

I'm assuming you have something like this now:

pc/laptop  -->  router/firewall   -->  webserver (listening on port 80).

Is this correct?

ah ha not sure

laptop and PC --> router(voip) --> dsl modem --> outside world

This might be over my head and I don't want to waste more of your time on this when it might not even be the problem,  Thanks for the help. I'm just gonna wait and hope for some replies to my other thread... your welcome to read it

[http://ubuntuforums.org/showthread.php?t=705905](http://ubuntuforums.org/showthread.php?t=705905)

---

