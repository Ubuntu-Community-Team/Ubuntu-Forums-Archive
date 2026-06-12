---
title: "Some easy security questions"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by jorge ortega on 2009-01-14
Hi, I'm new to Ubuntu (3 months). I've tried hard to understand the security issues but I don't seem to be any wiser. I've scanned the forums, used Wikipedia and many other places Goolgle took me to,and I still don't understand. I know now that I won't get viruses (great)and that by default Ubuntu doesn't open any ports so no need for firewall. Problem is:I don't know if I've open or will open any ports that need proteccion. I've got a pc, my uses that conect with internet are or will be: browser, pidgin, maybe skype, evolution or thunderbird, bit torret or similar. Is this opening ports that i will need to protect or not? I installed Firestarter -just in case- and then i read somewhere in the forums that it is not good to have it on all the time as it works with root access and this is a vulnerability?! Is this right? I tried to install Tor for anonymity and didn't success but probably will try again. If it uses a proxy server, is that opening ports too? I think this is pretty much all the internet services that i will be running. Am I opening ports or am i not?

Thanks for your help in advance

---

### Post by whoop on 2009-01-14
[www.probemyports.com](www.probemyports.com)
netstat

What I also do is (from another *nix computer outside of my local network):
sudo nmap -A <myipaddress>

---

### Post by jorge ortega on 2009-01-14
Thanks Whoop, If I understand well that site will check that my firewall is in place? I'm not at home at the moment so that is a job for tomorrow, but still doesn't answer my question, It isn't so much reasurance as understanding that I am after, I don't just want to secure my computer I would like to understand the process.

---

### Post by oldos2er on 2009-01-14
Firestarter is only a GUI front-end to iptables, so it's not necessary to always have it open. gufw is better, in my opinion.

---

### Post by whoop on 2009-01-14
As I see it a default ubuntu installation has a firewall installed (without a graphical frontend) and all ports are closed.
Now if you install applications and run them ports may open up. Like if you run transmission bittorent client this will open a port. This port needs to be open if you want efficient torrent transmissions.
The more programs you have installed that open ports the more unsecure you are. That's just the way it is. It's not that an open port makes your system unsecure it just makes it less secure. With a closed port there's no way of getting in; with an opened port theres still no way of getting in unless the service running behind that port is exploitable. Exploitable services are the result of: not updating your system, mis configuring your service (or not configuring it enough). 

So as a rule of thumb: keep your system updated, don't install (internet related) services unless you absolutely have to, configure your services to be as secure as possible).

So watch out when running stuff like (ssh, http, mysql, mail, irc) servers and the like

---

### Post by jorge ortega on 2009-01-15
Thanks again for your reply, now i know bit torrent opens a port. What about Evolution/Thunderbird, pidgin, Skype, or any so-called proxy server? Do they open ports aswell? A clarification would be welcome, thanks

---

### Post by hyper_ch on 2009-01-15
> **whoop said:**
> a default ubuntu installation has a firewall installed
correct

> **whoop said:**
> and all ports are closed.
wrong

Nothing hinders the ports being used. However no services are running by default - unlike Windows. If you install some daemon or soemthing that listens to incoming connection there is no additional step required to "open" the port.

> **whoop said:**
> The more programs you have installed that open ports the more unsecure you are.
Theoretically... practially an attacker will be required to find a vulnerability in the application that is running that has opened the port. This is not very often the case.

> **whoop said:**
> Exploitable services are the result of: not updating your system, mis configuring your service (or not configuring it enough).
Potentially no software is free of bugs... so if an attacker is fast enough at exploiting before there's a patch available you can't do much about it.

> **whoop said:**
> So watch out when running stuff like (ssh, http, mysql, mail, irc) servers and the like
well, only running the according servers and not the protocol itself.

---

### Post by jorge ortega on 2009-01-15
> **drumroll said:**
> My best advice to give to you: 

Forget Ubuntu/Linux. Unless you have zero life.

Not much use whatever you mean

---

### Post by hyper_ch on 2009-01-15
he's a troll, ignore him ;)

---

### Post by jorge ortega on 2009-01-15
Going back to the issue, anyone else with the answers I'm needing?

---

### Post by mc4100 on 2009-01-15
As hyper_ch says: there's no additional steps to "open" the port.
Ubuntu doesn't ship with services listening on any ports (unlike Windows which has historically had things like file sharing services, etc, wide open) , the only way that would happen is if you installed a daemon which is designed to be connected to (from elsewhere on the internet), like an SSH server.

In terms of applications, like Pidgin or Skype, they will listen for incoming "messages" on the port, because thats how it works; if the IM client was not listening, you could **send** messages but not receive any, which makes for very boring conversations. 
If a program is listening on a port, like an IM client, it stops listening when the application in closed. Of course, if some vulnerability was found in pidgin, then someone could exploit that -- which is why it's important to apply security updates.

Your web browser isn't really listening, since it's not a server -- it does however listen for a reply to it's request for a web page (which you have sent to a web service somewhere that will a have a sevice listening on port 80), otherwise how would you be able to retrieve the web page!

Evolution, i think, isn't going to be listening, merely going out and checking the mail server for new mail.

Strictly speaking it's not quite an simple as this, if you're using a router (or wifi) then there's network address translation going on -- which complicates thing because unsolicited traffic is rejected, and skype etc will need to work around than (involving the use of a third party).

Firewalls are hard to understand ... but all you really need to know is:
```
sudo ufw enable
```
And you will be fine for day-to-day use of you're IM apps, and voip, etc.
If you're using wifi, or behind a router, you don't even need to do that.

---

### Post by 3rdalbum on 2009-01-15
Any programs that listen to INCOMING ports are something to watch out for. Pidgin only listens to an OUTGOING port - that is, one where Pidgin initiates the connection. Same with any e-mail program, same with Skype, same with Firefox.

Programs that listen to incoming connections (they allow unknown computers to connect) include web servers, FTP servers, Samba, NFS, SSH, VNC, and possibly some database servers. You can also configure CUPS (the printing system) to listen for incoming connections, although this is not the default and is not possible to do accidentally.

Bittorrent and other peer-to-peer programs also listen to incoming ports by design, but you are generally safe with them. A firewall won't protect Bittorrent anyway, as you need your firewall to allow Bittorrent ports anyway in order to upload to other computers.

Unless you are explicitly installing the sort of software I mentioned, you don't need a firewall. Additionally, you may already have a firewall in your ADSL modem/router that protects your whole network.

There is an online port scanner - do a Google search for "Shields Up". If you use this, you'll be able to see whether your computer is listening to any incoming ports.

---

### Post by jorge ortega on 2009-01-15
Thanks very much, that pretty much clarifies things for me. One last question. If I install Tor or for the matter any so-called proxy server should I somehow have to protect that? Would I be opening any ports there? That really is my last reminig doubt?

---

### Post by hyper_ch on 2009-01-15
tor is there to anonymize your origin - not to protect you from malicious things.

---

### Post by jorge ortega on 2009-01-15
> **hyper_ch said:**
> tor is there to anonymize your origin - not to protect you from malicious things.

Sorry, probly I should have clarifed my point: it seems that in order to install Tor you need to install Privoxy or other proxy server first. Like if I install a Internet filter (which i forgot to mention is other internet-related service i want to install) I need to do it by installing Dansguardian or other proxy servers. My question is about these proxy servers. Do they open any ports? Sorry if the question seems stupid, my guess is that a proxy server has nothing to do with a server but i just don't know. I'd like to be in control of my computer rather than the other way around. I hope it doesn't sound too paranoic.

---

### Post by whoop on 2009-01-22
> **hyper_ch said:**
> 

wrong

Nothing hinders the ports being used. However no services are running by default - unlike Windows. If you install some daemon or soemthing that listens to incoming connection there is no additional step required to "open" the port.

Really, they aren't closed? Well, they aren't open. they aren't stealth. They must be something so we're running out of options here ;-)
I said all ports are closed because when you (for instance) don't install web services and scan port 80 you get:
```

 nmap -p 80 <ipaddress>
Starting Nmap 4.62 ( http://nmap.org ) at 2009-01-22 22:58 CET
Interesting ports on <ipaddress>:
PORT   STATE  SERVICE
80/tcp **closed** http

```
However, like we said, you don't have to open it manually after you installed a service

> **hyper_ch said:**
> 
well, only running the according servers and not the protocol itself.

That's why I said:
> **whoop said:**
> 
So watch out when running stuff like (ssh, http, mysql, mail, irc) **servers** and the like


---

### Post by whoop on 2009-01-22
> **jorge ortega said:**
> Sorry, probly I should have clarifed my point: it seems that in order to install Tor you need to install Privoxy or other proxy server first. Like if I install a Internet filter (which i forgot to mention is other internet-related service i want to install) I need to do it by installing Dansguardian or other proxy servers. My question is about these proxy servers. Do they open any ports? Sorry if the question seems stupid, my guess is that a proxy server has nothing to do with a server but i just don't know. I'd like to be in control of my computer rather than the other way around. I hope it doesn't sound too paranoic.

I haven't used privoxy myself, but if I am not mistaken privoxy will open a port. Port 8118 according to [https://help.ubuntu.com/community/Privoxy](https://help.ubuntu.com/community/Privoxy)
If I read this documentation correctly you can however loopback the ip to 127.0.0.1 so the localhost will be the only one to have access to this port.

---

### Post by hyper_ch on 2009-01-23
> **whoop said:**
> I said all ports are closed because when you (for instance) don't install web services and scan port 80 you get:
```

 nmap -p 80 <ipaddress>
Starting Nmap 4.62 ( http://nmap.org ) at 2009-01-22 22:58 CET
Interesting ports on <ipaddress>:
PORT   STATE  SERVICE
80/tcp **closed** http

```
It's not closed - just nothing is running on it - nmap can't differentiate those two states ;)

---

### Post by whoop on 2009-01-23
> **hyper_ch said:**
> It's not closed - just nothing is running on it - nmap can't differentiate those two states ;)

Maybe we should introduce a new port state "blocked" :D
Then we could say a port can be:
```

open   -- has a service listening
closed -- has no service listening
blocked (has two substates):
  closed -- is actively being closed by a process (i.e. a firewall)
  stealth -- is actively being stealthed by a process (i.e. a firewall)

```

Or we could just introduce a "not listening" state

---

