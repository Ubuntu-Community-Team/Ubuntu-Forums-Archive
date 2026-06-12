---
title: "SSH question (possibly firewall related)"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Miguellint on 2010-07-04
Hi all....Am new to ssh so apologies for the newbiness of the question.

I am having no success in trying to ssh into my brother's computer. I get the error message....

ssh: connect to host MY.BROTHERS.IP.ADDRESS port 22: Connection refused

He has run...

sudo /etc/init.d/ssh start

and in reply got the message....

"Starting OpenBSD Secure Shell server sshd"

However when he goes to canyouseemeDOTorg and runs their open port test on port 22 he gets the following error message....

Error: I could not see your service on port (22)
Reason: Connection refused

The port settings in ssh are the default port (22) so does this mean the firewall in his router (DSL-302G) is blocking his ssh server from seeing me. 

That was my assumption and I sent him to Shields Up at grcDOTcom which reported his port 22 as "Closed" (not stealth).

Does his firewall have to have port 22 open for me to connect. I'm fairly comfortable with opening a port on his firewall but this doesn't seem to be a suitable solution as it will be permanently open.

Any suggestions appreciated.

Regards
Miguellint

---

### Post by teejaybee on 2010-07-04
If he is behind a router, and that router uses NAT to provide him with internet access, then you will have to use the port forwarding configuration in his router to forward port 22 on the routers external / wan interface to his machine on the internal network. Usually you specifiy:

External inbound port (in this case, 22/tcp)
Machine's IP address on the internal network to forward to (eg. 192.168.1.50)
Port on the internal machine to forward to (eg. 22/tcp).

Your router's user manual or online help will be able to instruct you on how to achieve this.

---

### Post by Lucky. on 2010-07-04
Yep, in order to connect to a port, it needs to be exposed.  Seems kind of creepy, but it's how every publicly accessible service on the net works.

If you want to limit how many people it's available to, you might be able to block the port to everyone BUT your exact IP address.  But there's a good chance your IP address changes here and there, or you might want to connect to the server from someone else's place.  So that leaves you blocking the port to everyone but a range of addresses.  Then the day comes when you're on vacation and want to access the server from your hotel's ISP.  You can see how frustrating this could be.

The best place to add security is in the SSH login yourself.  Use a strong password, or better yet - use keys.  Once an SSH server is exposed to the net, it's only a matter of time before someone tries a dictionary attack against you.  And since the server is exposed 24/7, they have all the time in the world to try tons of password combinations.  Hence strong passwords or keys.

There's a good chance that it's not just a firewall holding that port back.  If the server is behind a router, then port forwarding or 1 to 1 NAT or a demilitarized zone needs to be enabled so you can log into your SSH server from the net (There's a number of names that home routers use for it).  Without some sort of forwarding, you'll just be trying to SSH into your router instead of your server - and that probably won't work.

Good luck!

EDIT:  Whoops, I took too long to write and teejaybee beat me to it!  Ah well, extra info never hurt anybody.

---

### Post by Miguellint on 2010-07-04
> **teejaybee said:**
> If he is behind a router, and that router uses NAT to provide him with internet access, then you will have to use the port forwarding configuration in his router to forward port 22 on the routers external / wan interface to his machine on the internal network.

Thanks teejaybee. I'm fairly sure this is the case.

So, if I forward port 22, does this mean that whenever he is online port 22 is open to the internet or is it only when his ssh server is running. It's seems unsafe to leave a port permanently open. 

If this is the case I might change his default ssh port to something less common.

Regards
Miguellint

---

### Post by CharlesA on 2010-07-04
Port 22 is only open when sshd is running. If you allow SSH access to the internet be sure that you are using a strong password and/or keys to login as it's one of the main ways servers/machines get compromised.

---

### Post by Miguellint on 2010-07-04
> **Lucky. said:**
> 

EDIT:  Whoops, I took too long to write and teejaybee beat me to it!  Ah well, extra info never hurt anybody.

Don't worry Lucky. The more brains I can pick the more I understand (I think). Thanks for the info.

And thanks CharlesA. Will look into keys. Have heard about them but don't really understand them. 

Regards
Miguellint

---

### Post by CharlesA on 2010-07-04
Also, if you want, you can block all connection attempts except those from your IP address by using gufw/ufw. That'll make it a bit more secure. :)

---

