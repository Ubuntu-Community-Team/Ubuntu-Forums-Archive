---
title: "No Access on server running in my guest OS."
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by kernelalive on 2013-11-22
Hello guys.

I have a problem troubling me that i would like to share.I have set up a web server on my guest os (kali/backtrack) that i would like to access by my external ip address but i can't.The host os (ubuntu) can communicate with the guest os using the private ip address so no problem there.When i hit my external ip address, browser shows me my router login screen .I shortly figured out that i have to redirect the outcoming traffic  to the guest os internal ip but that didn't work.So after some internet search i found that i also have to port forward the ip address of my guest os in the nat virtual adapter (by editing the nat.conf on /etc[COLOR=#000000][FONT=Ubuntu Mono]/vmware/vmnet8/nat/).So after i did that (not sure if it actually works) the result is the same my external ip gives me router login screen.It's obvious that i m missing something here but what.Any help would be appreciated .

Additional info i use vmware workstation 10 and my router is some stupid alcatel lucent cellpipe piece[/FONT][/COLOR]](*,)](*,)](*,).
thx in advance

---

### Post by drmrgd on 2013-11-22
That's odd that you're hitting your router admin page like that.  On my router, the remote management option (which I have disabled for security sake) would be listening over port 8080.  This is customizable on my router.  Can you point the remote management to a different port, leaving 80 open to listen for web traffic to your webserver?  

Otherwise, the process as I've done it is to forward all port 80 traffic coming into my outward facing IP address to the local IP address of my webserver.

---

### Post by steeldriver on 2013-11-22
From where are you trying to access using the public IP? if you are actually still inside the LAN, does your router support NAT loopback?

[http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback](http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback)

---

### Post by kernelalive on 2013-11-23
hello guys 
and thx for the response.I was indeed trying to access my server using my external ip from ubuntu pc(host) so steeldriver you are right and thx for pointing me the truth.Searching my routers configuration i wasn't able to find something like nat loopback  so i think i need a new router .Anyways thx for the answers guys .Internet cookie to steeldriver.

---

