---
title: "Remote Desktop Help"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by cfree on 2011-07-22
I am trying to get the remote desktop working on my computer but can only get it running locally. I am running 10.4 and I am using ubuntu's remote desktop application. I forwarded the port 5900 that didnt work and then I forwarded the port 3890. I forwarded both of these through my router is there anything that I need to do on Ubuntu's end?

---

### Post by cfree on 2011-07-22
Bump

---

### Post by e79 on 2011-07-22
I would not recommend such configuration as VNC is know to have quite few flaws that can be exploited, so opening port 5900 from the web to your PC might not be a good idea.

I would instead recommend you to install SSH  and change the forwarding port from the router; or better, if you could do it, install a [OpenVPN]("https://help.ubuntu.com/community/OpenVPN") server and then remote desktop into your PC.

just my $0.02

---

### Post by cfree on 2011-07-22
> **e79 said:**
> I would not recommend such configuration as VNC is know to have quite few flaws that can be exploited, so opening port 5900 from the web to your PC might not be a good idea.

I would instead recommend you to install SSH  and change the forwarding port from the router; or better, if you could do it, install a [OpenVPN]("https://help.ubuntu.com/community/OpenVPN") server and then remote desktop into your PC.

just my $0.02


Do you know of any SSH guides on how to set it up for remote access. I have openssh installed from apt-get install ssh

---

### Post by CharlesA on 2011-07-22
> **cfree said:**
> Do you know of any SSH guides on how to set it up for remote access. I have openssh installed from apt-get install ssh
Here you go:
[http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

---

### Post by e79 on 2011-07-22
> **cfree said:**
> Do you know of any SSH guides on how to set it up for remote access. I have openssh installed from apt-get install ssh

It is as simple as setting a rule in your firewall/router to redirect the traffic coming to a certain port on the Web side to the port 22 on the LAN side and forward it to your PC.

a bit as :

Action      Source     Destination/Port          Type   Protocol   Redirect To/Port:   
Forward    WAN        This gateway:52222    TCP    SSH        YourPC:22

(Port 52222 is just an example of a random port opened on the WAN side)

EDIT : ***CharlesA* suggestion is even easier**  :D 

Hope this helps

---

### Post by cfree on 2011-07-22
> **CharlesA said:**
> Here you go:
[http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

I followed that but was only able to connect to the terminal of the computer. Is there anyway that I could just use the remote desktop application that came with ubuntu and viewer that came with ubuntu to access remote computers?

---

### Post by doas777 on 2011-07-22
> **cfree said:**
> I followed that but was only able to connect to the terminal of the computer. Is there anyway that I could just use the remote desktop application that came with ubuntu and viewer that came with ubuntu to access remote computers?
simply put, no. you would likely be hacked within hours.

there are thousands of spiders crawling the internet looking for open vnc server ports. they have scripts for bruteforcing passwords, and often for automatically taking control of the machine (though most of those I've seen are for windows). 

VNC authentication is limited because it limits passwords to 8 characters and does not perform lockouts once a few bad passwords have been tried.


@op, if I might offer a slightly easier route for remote access, try [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX).

---

### Post by e79 on 2011-07-22
+ 1 for FreeNX, though I never tested it over internet, only over a LAN.

Once you have the SSH tunnel opened, you can try to forward VNC as stated in the Ubuntu documentation.

> When you have set up your SSH and VNC servers, you can use SSH to log in  to your computer over the Internet, start your VNC server, and use port-forwarding to securely access the VNC server. see [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by CharlesA on 2011-07-22
+1 to FreeNX too, altho I use the version over at Nomachine.com

---

### Post by cfree on 2011-07-22
This is the error that I am getting when I am trying to set up the ssh tunnelling:

ssh -L 5900:127.0.0.1:5900 -N -f -l guest xx.x.xxx.xxx
ssh: connect to host xx.x.xxx.xxx port 22: Connection refused

But when I ssh to my a computer own my network it goes through but gives me the error above when I try to ssh on one that I have set up outside of network.

---

### Post by doas777 on 2011-07-23
> **cfree said:**
> 
ssh: connect to host xx.x.xxx.xxx port 22: Connection refused

But when I ssh to my a computer own my network it goes through but gives me the error above when I try to ssh on one that I have set up outside of network.

have you forwarded port 22 on your router?
you can find instructions for most routers here:
[http://portforward.com/](http://portforward.com/)

---

### Post by CharlesA on 2011-07-23
FYI: You can forward vino over ssh, but it would be safer/easier to just use FreeNX. :)

Also some ISPs block ports, so you might have to pick a random high numbered port.

---

