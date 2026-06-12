---
title: "SSH to Linux Machine behind a Router"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Tuxedo Mask on 2007-09-20
I've looked through various posts here that seem to deal with the same issues, but they all seem to solve the problem with steps I've tried, but to no avail.

The basic set-up I have at home is the following: Westel Versalink 327A router/modem connected to the internet.  My Ubuntu Desktop (nightscream) and a Windows XP desktop (Bahamut) are connected to the router.  Instead of initializing port 22 for SSH on the router, I created two "custom services" (as per [here]("http://www.portforward.com/english/routers/port_forwarding/Westell/Versalink327W/SSH.htm")), one for each of the machines, so that nightscream would listen on Port Y and Bahamut on port Z.  In nightscream, I configured /etc/ssh/sshd_config to listen on Port Y, and openssh is running in the background (I can talk between the two machines no problem).

Outside of the LAN, though, I get errors when I try to SSH into nightscream. If I use PuTTy and input the IP of the router along with Port Y for SSH, I get a "Connection Timed Out"; doing the same with WinSCP gives me "Connection Refused".  This is both using the IP address and an address assigned from dyndns.org, so I don't think it's an issue with finding the router (traceroute gets to it if I use either one), and the router uses the machine names versus the Dynamic IPs for the servers so I know THAT'S not it (at least, I don't think).

Is there anything else I can check when I get home?  Thanks.

---

### Post by robert_pectol on 2007-09-20
I saw nothing in the link you posted, that specifies which internal host, the port forwarding is established for.  It seems incomplete as listed.  It looks like you defined a forwarding service and specified the port(s), but then just left it at that.  The next logical step would seem to be, to assign that forwarding service to a specific internal host (in this case the IP assigned to nightscream).

---

### Post by Tuxedo Mask on 2007-09-20
*slaps own forehead*

I always forget that the page doesn't show that part -_-

I'll screen-cap the steps I did in establishing (to my knowledge) the fact that Port Y goes to Host "nightscream" etc and post them when I get home.  I'm PRETTY sure that that part's alright, but, again, since the link seems to use different firmware (or maybe doesn't take into account multiple computers on the other side of the router?) I can't quantify my steps any better :/

---

### Post by Tuxedo Mask on 2007-09-20
Ok, finally got the images up ^^;

[Here]("http://www.timelesswings.net/david/images/host_service.png") the router asks me whether I want to route incoming connections to a specific PC.

[Here]("http://www.timelesswings.net/david/images/host_select.png") I'm asked to select the PC to which the communications should be routed.  I select "nightscream" for this example.

Let me know what other information I can give you, or if there's any other clarification that might be needed.  Thanks again in advance.

---

### Post by Zack McCool on 2007-09-20
> **Tuxedo Mask said:**
> Ok, finally got the images up ^^;

[Here]("http://www.timelesswings.net/david/images/host_service.png") the router asks me whether I want to route incoming connections to a specific PC.

[Here]("http://www.timelesswings.net/david/images/host_select.png") I'm asked to select the PC to which the communications should be routed.  I select "nightscream" for this example.

Let me know what other information I can give you, or if there's any other clarification that might be needed.  Thanks again in advance.

Does the router know what the DNS names translate to?

Generally, the router is pointed to a DNS server at the ISP.  The ISP's DNS server does not know the name of your machines behind the router.  Most routers do not have a hosts file.

Try the same config, but use the actual IP's instead of names.  And if they are DHCP, can you set them in the router to get the same address each time?  If not, use static addressing.

---

### Post by Tuxedo Mask on 2007-09-20
> **Zack McCool said:**
> Does the router know what the DNS names translate to?

Generally, the router is pointed to a DNS server at the ISP.  The ISP's DNS server does not know the name of your machines behind the router.  Most routers do not have a hosts file.

Try the same config, but use the actual IP's instead of names.  And if they are DHCP, can you set them in the router to get the same address each time?  If not, use static addressing.

Heh, I used the internally-assigned IP for nightscream, but the summary screen that results says "nightscream" anyways ^^;

---

### Post by robert_pectol on 2007-09-21
Well, not knowing the particulars of your router and what it takes to successfully establish port forwarding, I don't know what else to suggest other than to double-check your port forwarding rules.  Here are a couple of things to keep in mind while setting it up:

[LIST]
[*]You cannot forward the same port to more than one internal host.
[*]The internal host must have a service listening on the port which the router is forwarding to.
[*]In some routers, it's not enough to just specify the port(s) and host(s).  Some require you to also, "enable" the port forwarding rules that you've established.
[/LIST]

To assist in your troubleshooting, you're welcome to use this:

[http://rob.pectol.com/component/option,com_wrapper/Itemid,34](http://rob.pectol.com/component/option,com_wrapper/Itemid,34)

Select the, "Port Scan Utility" link.  This can be used to test your port forwarding from the perspective of an external connection.  It allows you to scan single ports on a host you specify.  Simply enter your hostname or IP and the port you want to check for openness!  :-)

Good luck.  I hope you get your problem figured out.

---

### Post by netztier on 2007-09-21
> **robert_pectol said:**
> 
[LIST]
[*]You cannot forward the same port to more than one internal host.
[*]The internal host must have a service listening on the port which the router is forwarding to.
[*]In some routers, it's not enough to just specify the port(s) and host(s).  Some require you to also, "enable" the port forwarding rules that you've established.
[/LIST]


One more to add:
[LIST]
[*] On some routers, you also have to configure the firewall rule set to allow the desired incoming tcp connection to "hit" the external interface, so that port-forwarding can take over from there (in my case: ZyXEL 650HW).
[/LIST]

best regards

Marc

---

### Post by Tuxedo Mask on 2007-09-22
Ok, I have some answers but I think it just leaves another question in its wake ^^;

I tried disabling my custom "Forward to Port Y" service in the router and enabled the built-in "Forward to Port 22" one, and what do you know, it works quite nicely ^^  I was able to connect to my system at work just fine.  This leads me to believe that the issue is on the Ubuntu machine itself, so I went ahead and did an nmap and found the following:

```

Interesting ports on localhost (127.0.0.1):
Not shown: 1691 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
1234/tcp  open  hotline <- Port Y as I had originally intended
12345/tcp open  NetBus <- Another port I added to the sshd_config file; have not tested yet.

```

My concern is that this "hotline" service - whatever it is - is clogging up any attempts to talk to the machine using SSH at that port, and if that's the case,  I have no idea how to free it up ^^ The port forwarding rule is established (set up AND enabled, and the port testing link given earlier is able to show me that 1234 is, indeed, open) in the router, so again, I don't think that's the issue.  I just don't know what it is I need to do serverside to get things running on the port I want XD

---

