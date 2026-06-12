---
title: "Internet connection lost"
date: 2005-07-10
forum: Networking &amp; Wireless
---

### Post by harwin on 2005-07-10
**I have a LAN connection to ADSL** 
Trouble started with Ubuntu after installing KDE parts. [ed] Think Samba had something to do with this[/ed] Strange thing is that suddently my internet connection does not seem to work after a short while.[ed] After just the second pageview[/ed]

My Wanadoo livebox [ed] Router ADSL VoIP modem[/ed] is working fine but it seems the connection between my PC and the livebox through a LAN connection does not go both ways. As if the LiveBox cannot 'see' my computer but I can still send messages to the Livebox. [ed] Router-Modem still is able to ping, so Gateway itself still seems to work[/ed]

After rebooting into XP I can resolve the problem by logging into the Livebox and rebooting it.[ed] From Ubuntu that does not work so I have to reboot into XP[/ed] After that I, also, have reset the LAN connection again from within XP. 

 ](*,) Now I wonder what is going wrong here. What does Ubuntu do that breaks up the internet connection. 

My guess it has something to do with DHCP.[ed] So I changed my DHCP to static, IP 192.168.5.10 mask 255.255.255.0 and gateway 192.168.5.1[/ed] :confused: I do not understand, the problem still is the same.

[ed]Removed all smb stuff, because the problem seemed to arise when I installed more software for Ubuntu, specially KDE stuff, but mostly, I guess SMB thinggies.[/ed]

---

### Post by harwin on 2005-07-11
:?  Installed Ubuntu again. And the problem is not there anymore, cough cough.
Now what should I not install now? That is the question.

Think I do not do KDE this time but keep Gnome only. 
Still I'm not shure what did cause the problem.

 ](*,)

---

### Post by magoo on 2005-07-11
I read somewhere that there is a problem with sagem's livebox with DNS request handling.
The users complaining had to reboot the modem every now-and-then.
The solution is to setup the DNS of wanadoo directly in the linux computer (/etc/resolv.conf) and not the IP the the livebox.
With this Q&D workaround, the problem disapeared.

---

### Post by harwin on 2005-07-11
@ Magoo,

Thx, that looks like the problem solved. 

With kind regards,

Harwin

[ed] It did solve the problem indeed, thx again![/ed]  \\:D/

---

### Post by SteelCore on 2007-05-24
> **magoo said:**
> I read somewhere that there is a problem with sagem's livebox with DNS request handling.
The users complaining had to reboot the modem every now-and-then.
The solution is to setup the DNS of wanadoo directly in the linux computer (/etc/resolv.conf) and not the IP the the livebox.
With this Q&D workaround, the problem disapeared.

I am having connection problems with my Wanadoo Sagem livebox.  Can someone please explain to me in detail how to apply the quoted solution.  Thanks

---

### Post by magoo on 2007-05-24
Hello,

you need to find out what the DNS server of Wanadoo are. 
I suggest that you use openDNS, they are quite faster than cable operator DNS.

Follow the intruction on this page:
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

If you want to use Wanadoo's DNS. simply change the DNS IPs in your configuration file.

--
magoo

---

### Post by SteelCore on 2007-05-27
> **magoo said:**
> Hello,

you need to find out what the DNS server of Wanadoo are. 
I suggest that you use openDNS, they are quite faster than cable operator DNS.

Follow the intruction on this page:
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

If you want to use Wanadoo's DNS. simply change the DNS IPs in your configuration file.

--
magoo

Thanks for your reply.  I did try the above instructions but still can't connect.  The strange thing is that I have not probs with Drapper or Etchy.  It is only Feisty that can't connect.  Took my computer today to a friend's house and was able to connect via pppoeconf on a Speedtouch modem.  It is clearly the (Wanadoo Sagem livebox) that is causing all the trouble.

---

