---
title: "IRC server: can only connect via localhost"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by DarknessNL on 2008-10-30
Hello, i have a problem with ircd-hybrid irc server, i can't connect via network or internet, only via localhost. I can't find it in the .conf file and all ports in router are open.  Can somebody solve this? :frown::confused:

---

### Post by DarknessNL on 2008-10-30
> **DarknessNL said:**
> Hello, i have a problem with ircd-hybrid irc server, i can't connect via network or internet, only via localhost. I can't find it in the .conf file and all ports in router are open.  Can somebody solve this? :frown::confused:

solved :P

---

### Post by kennedy7 on 2008-11-14
I got a question man, does ircd-hybrid work even after reboot?
If so email me the source code of ircd.conf.
My irc works untill i reboot the server computer.
tyspage.doesntexist.com channel #help
thats my irc.
Like i said "works fine untill reboot server".

---

### Post by kennedy7 on 2008-12-02
Ok, when you get to /etc/ircd-hybrid/ircd.conf line host= "127.0.0.1"
                                                    port = 6665..6669
change that to #host = "127.0.0.0.1"
And then set your port to 6667 or whatever you want.

---

### Post by theluddite on 2009-04-18
> **DarknessNL said:**
> solved :P

How?

---

### Post by theluddite on 2009-04-18
Nevermind.  I could only connect to the localhost for a while until I changed this:
> 	/* port: listen on all available IPs, ports 6665 to 6669 */
	host = "192.168.1.1;	# change this!
	port = 6665 .. 6669;
};

to this

> 	/* port: listen on all available IPs, ports 6665 to 6669 */
	#host = "192.168.1.1;	# change this!
	port = 6667;
};

Now the port is open and I can connect from an external IP.

---

