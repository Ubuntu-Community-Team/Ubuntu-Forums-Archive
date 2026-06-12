---
title: "Is my system safe"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-06
Hi Forum,

I saw the quote somewhere in the forum "Linux assumes you know what you're doing". I don't so I'm worried I might be opening my data to those that do.

I'm connected to the internet with a Fritzbox that has an internal firewall. I've got a NAS sevrer running some Debian variant that doesn't seem powerful, a desktop with Ubuntu and occasionally laptops with either Ubuntu or Windows Vista.

When I found out that the NAS allows ftp from outside the network, I set up a static IP with dyndns and installed that into the router. I used the router firewall to allow a port forward from a port (not 20 or 21) to the NAS port 21. I used a random generator to make a long password.

Now I'm considering installing LDAP and LAMP on the desktop and forwarding SSL port 636 and internet port 80 to the desktop. It will be a learning exercise so I plan to use the standard tasksel "lamp".

My concern is that I'll be making my computer or worse still my NAS open to people with greater computer knowledge and more time on their hands than me.

Any pointers to reliable information about safety and security of data? Does the opening of a webserver make my network less secure?

Any tips on making the NAS data more secure? What if I move it to the desktop and then open only an FTP over SSH to the outside world (the NAS doesn't support that). Can anyone point me in the direction of a suitable tutorial.

Thanks again for all the help.


Richard

---

### Post by dzark on 2009-03-06
to keep my NAS secure, i have it only connect to local machines, and i ssh into one of them from out in the big scary interweb.. FTP passwords are passed in plaintext across the web :( very easy to intercept

so close the open port to nas, infact dont let the nas see anything to/from the outside world..

then [http://www.howtogeek.com/howto/ubuntu/setup-openssh-server-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/setup-openssh-server-on-ubuntu-linux/)

---

### Post by RichardCL on 2009-03-06
Wow that seems simple.

I do have the possibility to SSH to the NAS. I can use Putty to execute commands on the NAS. I am still as secure if I disable FTP on the NAS and use SSH? I'm not getting wise from internet tutorials on that (hence I'm still on FTP).

Can you point me to a good how to on what to do with the SSH once I've installed it either on the NAS or desktop. I really don't have that much idea. I did try the FTP via SSH option in filezilla to try to get data from the NAS but only managed to get a whole stream of errors.

---

### Post by handydan918 on 2009-03-06
First, if you do not need to access your NAS across the Internet, don't forward ports on your router. That is probably your biggest security hole. 
Second, the comment about ftp passwords in plain text is a good one, but easily overcome by not using passwords on an ftp server.An anonymous read-only ftp server is pretty safe, especially on a lan behing a router.
Third, ssh is very good. You can use the scp command to copy files using ssh. The "server" machine must have the openssh-server package installed. The client is installed by default. scp uses syntax like:```
scp sourcefile targetfile
```
For more info, see man ssh and man scp.

---

