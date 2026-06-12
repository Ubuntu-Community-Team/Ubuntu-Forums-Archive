---
title: "NAT, can't make remote connections by public (external) ip"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by redmorning on 2009-04-23
Hi,i created a small LAN at home,on my laptop i have a ubuntu 8.10 as host and two of my guests are windows server 2003 and an xp.on my desktop xp as host with another xp and ubuntu(8.10) as guests.There are sql server 2005 on all windows os (that's for my project).

my aim is to reach all of these machines remotely by any ip and for this i made some configuration on my routers interface (i don't use iptables for this moment).

Before using sql servers(1433) i want to control (also want to use) this port forwardings by ssh and rdesktop,basically i forwarded ports 22 (ssh) and 3389 (rdesktop) to my local ips.

router(AirTies RT-205):
Target ip______|__WAN port__|__Target LAN port__|__Packages
192.168.2.2___|____22______|______22___________|___TCP&UDP
192.168.2.3___|___3389_____|_____3389__________|___TCP&UDP

here are some of(neccessary) my private ip
laptop->ubuntu->192.168.2.2
desktop->xp->192.168.2.3
desktop->ubuntu->192.168.2.4

these two machines are enough to explain my situation.

i can remotely connect to my xp(desktop host) in LAN:
rdesktop -g 1250x700 192.168.2.3
i can ssh to my ubuntu on desktop(guest) in LAN:
ssh piratejackus@192.168.2.4
of course i can ssh my own ubuntu(laptop host) too.

i check my ports, if they are open,with my public (external) ip by 
[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/),
both,22 and 3389,seems open.

after local tries i use my public ip for ssh to my ubuntu (laptop):

piratejackus@gemi:~$ ssh -v [email]piratejackus@XX.XX.XX.XX[/email]
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to XX.XX.XX.XX [XX.XX.XX.XX] port 22.
debug1: Connection established.
debug1: identity file /home/piratejackus/.ssh/identity type -1
debug1: identity file /home/piratejackus/.ssh/id_rsa type -1
debug1: identity file /home/piratejackus/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

and try rdesktop:

piratejackus@gemi:~$ rdesktop -g 1260x730 XX.XX.XX.XX
Autoselected keyboard map en-us
ERROR: XX.XX.XX.XX: unable to connect

i made some changes in /etc/hosts.allow and /etc/hosts_deny but it didn't change anything.

i opened my ports on router and checked them,made NAT to my local computers,but no joy and need help.

---

### Post by Peter09 on 2009-04-23
What do you see in syslog on the target machine?

---

### Post by redmorning on 2009-04-23
i checked my syslog (laptop-host ubuntu) and nothing about ssh or my public ip,what can i look for in syslog about this issue?

---

### Post by redmorning on 2009-04-24
any other idea please?

---

### Post by Peter09 on 2009-04-24
Sanity Check - confirm your external IP is what you think.

---

### Post by redmorning on 2009-04-24
no problem with public ip,already checked for many times..

---

### Post by Peter09 on 2009-04-24
Just a thought - in this line

piratejackus@gemi:~$ ssh -v [email]piratejackus@XX.XX.XX.XX[/email]
are you expecting to hit 'piratejackus' (thats the same machine thats issuing the command)

or you other hosts?

---

### Post by OneMixDJ on 2009-04-24
piratejackus,

Can you specify how you are verifying your public ip?

Go to [www.ipchicken.com](www.ipchicken.com) from ether of the inside machines and verify your public ip. 

Also, what kind of router do you have?

In addition (for troubleshooting purposes), I would suggest reverting the changes made in /etc/hosts.allow and /etc/hosts_deny back to default before testing again.

---

### Post by redmorning on 2009-04-24
Peter09;

piratejackus is a common user on my ubuntu boxes
ssh -v -l piratejackus 88.235.125.240
i am expecting for an password prompt as usual..

---

### Post by The Cog on 2009-04-24
You are trying to connect from your home LAN to your homes public internet address? That would involve two machines on your local LAN talking via your router and one being NATted in the process. I don't believe this can ever work. 

Suppose that machine A tries to connect to machine B by connectng to the public address (P). Even if the router sees the connect request, translates the destination address from P to B and forwards it (most routers won't do this) you will have problems. Machine A has sent a connect request from A to P. Machine B sees a connect request from A to B. But B is on teh same LAN as A so it will reply directly. Machine A will then get a connect confirm from B to A. But it didn't try to connect to B, it tried to connect to P. As far as machine A is concerned, its connect request went unanswered, and as a completely independent event, it received an unexpected connect confirm from B which it rejects.

You will only be able to test your NAT setup from another internet site, not locally.

You may want to consider using OpenVPN to gain full access to your home network from elsewhere.

---

### Post by redmorning on 2009-04-24
OneMixDJ;

i have a dynamic ip so i got a domain from dyndns.com,i use(for SSH and rdeskto) my ip or my domain for public ip and same result for both of them.
i am getting my ip from my router (as i mentioned before:AirTies RT-205) interface and everytime i reboot my router i check for my new public ip which my ISP provides.
i also reverted /etc/hosts.allow and /etc/hosts.deny files to default.

---

### Post by djtnz on 2009-04-24
The Cog is right, you can't test your NAT settings from the LAN side using your external IP. 

Your best bet is to test it from another site that is not behind your router

---

### Post by redmorning on 2009-04-24
The Cog and djtnz;

The Cog's explanation seems logical,i thougt that:

In my LAN i can connect form A to B and if i make port forwarding (NAT) for the port (ex:22-SSH-) to B i can connect to B from A using my public ip,due to reasons (The Cog mentioned) it may not work,i am at the university now and try in a little while from here and inform you.

---

### Post by redmorning on 2009-04-24
i'm back (still at the university).i learned my ip from my router interface (dyndns-domain) and checked port 3389 (default port for rdesktop) from :

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

and it is opened,after that i tried to rdesktop:

piratejackus@gemi:~$ rdesktop XX.XX.XX.XX
Autoselected keyboard map en-us
ERROR: XX.XX.XX.XX: unable to connect

still no joy and i still need help.

---

### Post by redmorning on 2009-04-24
i also post my very very simple router NAT configuration

[ATTACH]110814[/ATTACH]

to inform again;
192.168.2.3 -> LAN(home)desktop xp
192.168.2.2 -> laptop(at university with me now(: ) ubuntu

---

### Post by Peter09 on 2009-04-24
You seem to have a router setup problem. If you want to get from laptop (external) to desktop (local 192.168.2.3) then your port forwarding should show ssh->192.168.2.3.

It appears that you are forwarding locally to 192.168.2.2?

Am I misreading this?

---

### Post by redmorning on 2009-04-24
> i'm back (still at the university).i learned my ip from my router interface (dyndns-domain) and checked port 3389 (default port for rdesktop) from :

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

and it is opened,after that i tried to rdesktop:

piratejackus@gemi:~$ rdesktop XX.XX.XX.XX
Autoselected keyboard map en-us
ERROR: XX.XX.XX.XX: unable to connect

still no joy and i still need help.

yes my friend you're,now i'm trying rdesktop to reach my xp in home-lan,did try ssh when i was at home.
My aim is just to see one of these forwardings working,rdesktop or ssh.
as i told in earlier post:
rdesktop(3389) to 192.168.2.3
is what i'm trying now university-home

---

### Post by Peter09 on 2009-04-24
Ok lets confirm this.

You are at UNI. with your laptop - its IP address is does not matter.

you are trying

ssh -X <yourusername>@<yourhome external_ip>

this will go from UNI and hit your router on its external IP port. It will say ahh--- ssh I am instructed to forward ssh to an IP address on the local LAN which is....(from what I can see 192.168.2.2).

This is your laptop address.... which happens to be at University.... ain't going to work. Please tell me where this is wrong.

Yours in Confusion..

---

### Post by redmorning on 2009-04-24
Peter09

this thread looks a little complicated because of me i think,i am sorry,i will try to fix this situation.

last night i did those:
ssh <username>@<192.168.2.2>    (192.168.2.2-my laptop-host-ubuntu private ip in LAN)
works of course,
then i thougt if i forward port 22 to my laptop-host(ubuntu) maybe i can ssh again,i made changes in router as you can see from png i uploaded,
ssh <username>@<my_external_ip>
but it didn't work.

Then The Cog told me that i can't check NAT configuration inside the LAN so now i'm trying from universtiy.

hope it is fine till here Peter09 (:

In my LAN i could connect with private ip:
rdesktop 192.168.2.3(Desktop-host-xp)
Now the only box in my LAN is Desktop-host-xp which i can check if my NAT is working or not.I'm ijust interested with port 3389(for rdesktop) for now,not 22(SSh). I think: i made NAT,my port on router is opened and i can connect remotely to my xp (LAN) but can't.

&#304;f it is still not clear just say,this is the simplest way i can explain my problem and situation.

thanks..

---

### Post by Peter09 on 2009-04-24
Ok Thanks - so you are using remote desktop to connect to your local Desktop machine which is 192.168.2.3. For that your router is fine.

To be pedantic - the command you are using is:

rdesktop <your external ip address> (which is not 192.168.2.3)

---

### Post by redmorning on 2009-04-24
(:

yes,i am using that command,not my private ip of course (:

so,do you have any idea? it looks so simple but still no solution by my side.

---

### Post by Peter09 on 2009-04-24
Sorry for the detail, but its difficult to help from a distance, and you can spend a lot of time trying and then find out that it was a basic problem that a person did not understand.

First check, try to ping your external ip address.

```
ping <external ip address>
```

It should respond. (unless your router is set not to?)

Second test try

```
whois <external ip address>
```

Although you will not see any personal details you should see reference to your isp.

---

### Post by redmorning on 2009-04-24
you're absolutely right,it's not easy to understand the problem and help form distance,thank you again for your time,now,

i can ping,no need to post ping result here (:

piratejackus@gemi:~$ whois XX.XX.XX.XX
connect: Connection refused

makes sense?

---

### Post by Peter09 on 2009-04-24
Does not seem to make sense as whois should respond with information about your IP address.

Would you like to email me your IP address? I could check from here as well. I won't be offended if you refuse.

---

### Post by redmorning on 2009-04-24
ok,i sended my public ip as private message and mail too.

---

### Post by Peter09 on 2009-04-24
Hi, ok

I did a rdesktop<you external ip> and got a windows XP login-in screen, so it is working from here. The problem you have is either with your laptop or the University is blocking rdesktop protocols.

---

### Post by redmorning on 2009-04-24
really!i am surprised,i am able to connect in LAN with private ip,despite that you think it can be because of my laptop(ubuntu)? if it is,how can i solve that?

---

### Post by Peter09 on 2009-04-24
More likely that the University is not allowing remote desktop protocols outbound. May be a security decision.

---

### Post by redmorning on 2009-04-24
Peter09,

thanks to take time for me,now i know that my simple NAT is working,it is enough for me,i m gonna try this from different points and hope got it work as you did (:

bye.

---

