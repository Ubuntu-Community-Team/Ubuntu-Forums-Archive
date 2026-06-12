---
title: "ssh via dyndns to network server?"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by passonno on 2007-03-14
Hello,

I am attempting to do the following:

I just registered a hostname at dyndns, and am trying to access the file server on my network, but i am honestly s tiny bit confused about how to do this.

The files server contains, well, files, and is running apache as well.

Any ideas?


Thanks

---

### Post by netztier on 2007-03-14
> **passonno said:**
> Hello,

I am attempting to do the following:
I just registered a hostname at dyndns, and am trying to access the file server on my network, but i am honestly s tiny bit confused about how to do this.

The files server contains, well, files, and is running apache as well.

Any ideas?


Thanks

On your network, there'll have to be some system sending an update to dyndns.org (containing your login information, your chosen <yourname> and the currently valid IP address of your internet connection), so they (rather: their nameservers) know what IP address to give as answer when someone queries them for <yourname>.dyndns.org.

[COLOR="Navy"]**Server directly connected to broadband:**
If your server is connected directly to your cable/dsl device and has an "official" IP address on it's external NIC, it can send the update itself. There's scripts that can accomplish this, search the repositories with Synaptic for "dyndns". Additionally, should you run a firewall on this directly connected server, it must of course allow incoming connections to tcp/22.[/COLOR]

[COLOR="DarkGreen"]**With a Broadband router**
If you have a broadband router connected to your DSL or Cable device, check if it supports dyndns directly. Most of the newer ones do. Configure it to update your account with  dyndns.org.

In addition to that, you will have to configure the router to do port-forwarding for tcp/22 to the internal address (most probably a 192.168.0.x address) of your server. On some routers you have to configure the firewall and the port-forwarding features separately: the firewall to allow incoming connections to tcp/22, the port-forwarding to forward these packets to the correct internal IP address.[/COLOR]
[INDENT][SIZE="1"]
A sideword on using tcp/22 for ssh-servers on broadband networks: **don't**. Worms, viruses and other malware are keen on trying to access well-known ports and try brute-force attacking. And their owners know the customer IP ranges of the large broadband providers, and that's where they start looking for open ports. When I left my SSH on tcp/22 open for a few days, the logs on my internal server started to grow very fast... 

Instead, configure your SSH server to listen on some additional random high port (like.. 42424 or up in the 50000's), you can do this in /etc/ssh/sshd_config, by adding a second "Port" line. Then, configure your broadband router to forward only this port towards the inside. 

Yes, it won't help against someone that wants to attack you specifically, he'll find out the port your SSH is listening on anyway. But there's no need to expose your SSH to the port scanners.

If you want it really secure, disable password and keyboard-interactive authentication for SSH and rely on public/private key authentication, but this has implications on flexiblity and you'll have to have your private key as a file with you wherever you go. That's not always practical...
[/SIZE][/INDENT]

Now as soon as the server or the broadband router have sent the update (containing the current IP address of your home connection), you can access it from outside by connecting with SSH to <yourname.dyndns.org>. If you use a nonstandard port as suggested above, don't forget to change the port in the connection definition, too.

If you configure the router to port-forward tcp/80, too, you can access your apache also with http://<yourname>.dyndns.org/.  Be wary though: Malware is even keener on port 80 than on port 22 ... and maybe your ISP blocks port 80 anyway, as many of them do today. Consider using a different port, too, or even better switch over to SSL (http**s**://...) in any case.


best regards

Marc

---

### Post by passonno on 2007-03-14
Thanks for your help,

As soon as I have the free time, I will set it up, and get back to you.

Thanks again.

---

