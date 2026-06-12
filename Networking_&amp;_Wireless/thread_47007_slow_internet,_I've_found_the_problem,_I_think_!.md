---
title: "slow internet, I've found the problem, I think !"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by railz68 on 2005-07-06
My dsl has always been slower to react to commands then windows. Clicking on web pages, launching games, checking mail. Anything to do with Internet is  very slow compared to WinXP.

Both on my PC and my Father-in-Law's PC, living in the same house, WinXP is very quick to respond to internet access.

Using both Ubuntu and Mandrake, any internet request is very slow. I believe I've narrowed it down to "dns server".

Can someone tell me how to back up what I have now (works, but slow), to what my ISP suggests -

   >  * DNS should be "disabled" in the TCP/IP window, and IP address should be set to Obtain automatically:
          o Click Start, point at Settings, then click Control Panel
          o Double-click the Network icon
          o Locate and then double-click the TCP/IP -> yournetworkcard entry
          o Click the IP Address tab, then click to select Obtain an IP address automatically
          o Click the DNS Configuration tab, then click to select Disable DNS
          o Click OK, then OK again. Restart your computer when prompted.


There is a big delay launching anything "internet related" with ubuntu (also mandrake 10). I believe (and hope), it's a dns issue that can be fixed.
Both my wife and daughter complain to me windows is faster internet access then ubuntu. Well I finally saw it for myself and I think I've found out why. Any help with this, big thanks.


edit: I see settings for MAC that may be revelent to linux ?

> DNS settings in Macintosh TCP/IP Control Panel:

Mac OS 8.1-9.2

    * Power Macintoshes with OS 8.1-9.2 requires DNS "dummy" settings in the TCP/IP window, otherwise you may not be able to surf after connecting:
          o Click the Apple menu icon at the upper-left of your screen
          o Point at Control panels
          o Click TCP/IP
          o Click Connect via, then click Ethernet or Access Manager
          o Click Configure, then click Using PPP server
          o In Name Server Addr: box, type 2.3.4.5 then press the return key and type 6.7.8.9 on the next line
          o Close the window and Save settings if prompted.


Any help getting same speed/service with ubuntu vs windows would be great.

---

### Post by scoon on 2005-07-07
Hey there, 

Do a search on disabling ipv6.  That also has been posted as being a problem. 

regards, 

scoon

---

### Post by gruepig on 2005-07-07
[QUOTE=railz68]My dsl has always been slower to react to commands then windows. Clicking on web pages, launching games, checking mail. Anything to do with Internet is  very slow compared to WinXP.

Both on my PC and my Father-in-Law's PC, living in the same house, WinXP is very quick to respond to internet access.

Using both Ubuntu and Mandrake, any internet request is very slow. I believe I've narrowed it down to "dns server".

Can someone tell me how to back up what I have now (works, but slow), to what my ISP suggests -

   


There is a big delay launching anything "internet related" with ubuntu (also mandrake 10). I believe (and hope), it's a dns issue that can be fixed.
Both my wife and daughter complain to me windows is faster internet access then ubuntu. Well I finally saw it for myself and I think I've found out why. Any help with this, big thanks.


edit: I see settings for MAC that may be revelent to linux ?




Any help getting same speed/service with ubuntu vs windows would be great.[/QUOTE]
 DNS configuration is in /etc/resolv.conf. Most likely, you should be using whatever DNS servers your ISP provides.

To determine whether DNS is the cause of the problem ... You have some working DNS or else you wouldn't be getting to any web sites, etc. by hostname. A delay would be caused if you have multiple DNS servers listed and one of them (probably the first) is failing to resolve. See what DNS servers you are currently using ('cat /etc/resolv.conf'). Then, try DNS lookups against each host.  For example, if your DNS servers are 192.168.0.53 and 192.168.0.54, run 'host [www.google.com](www.google.com) 192.168.0.53' and 'host [www.google.com](www.google.com) 192.168.0.54'. If one of those fails to return IPs for google, you have a DNS problem.

---

### Post by railz68 on 2005-07-08
thanks for the replies.
I didn't know about ipv6 and what it does. After a search I've seen some say it fixed the trouble they were having. I haven't tried this yet as I checked the suggestion with the host dns lookup.

> 
Then, try DNS lookups against each host. For example, if your DNS servers are 192.168.0.53 and 192.168.0.54, run 'host [www.google.com](www.google.com) 192.168.0.53' and 'host [www.google.com](www.google.com) 192.168.0.54'. If one of those fails to return IPs for google, you have a DNS problem.


I have 2 "nameservers" in /etc/resolv.conf.  The first one fails, the second responds very quickly. For fixing this, do I need to find a different nameserver or comment out the one that fails ?.

Is winXP also using this, if so, where could I find it and copy it for ubuntu.
Or do I need to start searching my ISP site for this ?

thanks for your help with this.

---

### Post by adwait on 2005-07-08
u can comment out the one that fails in resolv .conf
sudo gedit /etc/resolv.conf

---

### Post by railz68 on 2005-07-08
I did it, and with a reboot, seems it changed it back to the way it was. Guess I'll try again as "root".

---

### Post by railz68 on 2005-07-08
ok, changed it with "sudo" and "root". When I reboot, it's back to the way it was. Any help on getting the changes to stay ?

---

### Post by railz68 on 2005-07-08
found out howto edit this, I hope - 

[http://www.ubuntuforums.org/showthread.php?t=39606](http://www.ubuntuforums.org/showthread.php?t=39606)

Called my ISP for dns nameservers, while the second one works, they said it wasn't one of from them.

So I now have both primary and secondary from them, hope it works.

---

### Post by railz68 on 2005-07-08
changed it all just like the instructions in that post I found. When I reboot, the nameservers go back to the old ones. Can anyone tell me what file to edit to make the changes stay.  ](*,)

---

