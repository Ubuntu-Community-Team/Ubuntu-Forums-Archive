---
title: "Linksys WAG54G Wired Connection Setup"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by Plague on 2006-12-15
Hi,

I have had Ubuntu installed for a little while now. I love it so far except when it come to connecting to the internet it pisses me off often.

When I installed Ubuntu, my Linksys (Cisco Systems) WAG54G Wireless-G ADSL Gateway, was on and connected to the net. After installation of Ubuntu (6.10) I was coinnected to the net and could surf the net. But the next time I turned on my comp and router, the router connected to the net, Ubuntu says it detects the connection, but when I tried to go on the net it doesn't connect. To fix this all I've done so far have been restarting my computer and router a few times till somehow magically the connection works again.

This process has become very tiresome and frustrating. I have searched on the web on ways to set up the internet connection properly but don't get anything beyond the obvious enabling of "Wired Connection' in Network Settinbgs. It doesnt solve the problem.

I'm not very familiar with Linux, nore am any good at understanding routers. When I was using windows xp all I had to do was to set up the router according to my ISP's instructions. At the moment I'm frankly hopelessly lost. If there's no solution to the problem I might have to reinstall windows xp.

---

### Post by ginkhao on 2006-12-15
We could narrow it down a bit by determining whether the connection problem is between your computer and the router or between the router and your ISP/internet.

Are you using a wired connection?
When you have a problem connecting:
What lights are lit on the front of your router?  One of 1,2,3 or 4?  DSL & Internet?
Can you reach the router's configuration screen by putting it's IP address (probably 192.168.1.1) in a browser address bar?
Check under System-Administration->Networking->DNS tab - are there one or more IP addresses listed there?

---

### Post by megamania on 2006-12-15
> **Plague said:**
> I'm not very familiar with Linux, nore am any good at understanding routers. When I was using windows xp all I had to do was to set up the router according to my ISP's instructions. At the moment I'm frankly hopelessly lost. If there's no solution to the problem I might have to reinstall windows xp.
I use exactly the same router as you do, and it works flawlessly.

If you didn't change the router settings after migrating from windows to linux, I would say that the problem lies in your specific Ubuntu install. Did you touch your network settings in linux for some reason? The system should work out-of-the-box with a clean install.

---

### Post by Plague on 2006-12-15
> **ginkhao said:**
> We could narrow it down a bit by determining whether the connection problem is between your computer and the router or between the router and your ISP/internet.

Are you using a wired connection?
When you have a problem connecting:
What lights are lit on the front of your router?  One of 1,2,3 or 4?  DSL & Internet?
Can you reach the router's configuration screen by putting it's IP address (probably 192.168.1.1) in a browser address bar?
Check under System-Administration->Networking->DNS tab - are there one or more IP addresses listed there?

Yes it is a wired connection. The router connects to net fine. and the light that indicates it's connected to my comp is lit as well. But I cannot reach the router's configuration screen, which means my comp is not connected to the router. Under the DNS tab there are 2 IP addresses listed. I have not made any modifications to the Networking settings. All the settings are as they were after installation. [The router settings uses PPPOA. If that's part of the equation in any way]

---

### Post by ginkhao on 2006-12-15
OK so let's troubleshoot the connection to your router.

Could you open a terminal and type **ifconfig** and post the output?

Then, under System->Administration->Networking
On the **Connections** tab highlight **Wired connection** and press **Properties** and post the details.

Can you reach the config screen from Windows?  If so, open the configuration and on the very first page you see after inputting the username and password, look for and post the following settings:

Local IP Address:
Subnet Mask:
Local DHCP Server:
DHCP Relay Server:
Starting IP Address
Maximum number of DHCP Users:

---

### Post by Plague on 2006-12-16
I have attached the settings you requested ginkhao. Hope you can make something out of it.

---

### Post by Handssolow on 2006-12-16
Just another thought. Some of the Linksys products run rather hot and can become unreliable. Check out the web and you'll find details of folks fitting extra cooling fans.

---

### Post by Plague on 2006-12-16
> **Handssolow said:**
> Just another thought. Some of the Linksys products run rather hot and can become unreliable. Check out the web and you'll find details of folks fitting extra cooling fans.

No heating problems.

---

### Post by ginkhao on 2006-12-18
Hi Plague,

I can't see anything in the settings which shows why this is occurring, and I certainly don't know any reason why it could only happen only in Linux.  My suggestions would be to:

1. Try setting a static IP address, this might help if there is a connection to the router but for some reason DHCP isn't working:
**System->Administration->Networking**
Select **Wired connection** and press **Properties**
Change **Automatic Configuration** to **Static IP address**
Use the following settings:
[B]IP address 192.168.1.99
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.1[/B]

My router sometimes goes funny when I change these network settings, the connection light goes out and other weird things happen.  You may want to disable and re-enable the connection using the check-box on the dialog box or even reboot if you want.

2. Try a different network cable. This might sound a bit of a stab in the dark but I've seen plenty of faulty ones cause problems like yours.

---

### Post by phuturism on 2007-03-10
Hey,

I had a very similar problem with the same modem/router model - I am using ADSL PPOE to connect to my ISP and found that if I had the ISP recommended domain name servers listed in the router wan interface, this was causing problems.  I was using the router as a DHCP server.

Try deleting these from the router wan (basic setup) interface and try to connect again.  I found the issue was not really linux related - except that you can't use an install disc to configure your router as you can with windows.   If you are still having problems, let me know - I am in Australia also so similar tech and terminology I guess.  This website [http://broadbandchoice.com.au](http://broadbandchoice.com.au) is also good for networking and broadband internet issues in Australia.  It has a forum area - one of the topic areas is broadband and linux in Oz.

antony

---

