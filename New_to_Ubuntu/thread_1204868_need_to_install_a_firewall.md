---
title: "need to install a firewall"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-05
i know that the 80% of the people who will see this thread will say i dont really need a firewall....but i still want one
right now i have firestarter,which is no longer maintained.
so i'd like to install an up-to-date one

any recommendations?

also just to note i find the firestarter's feature with active connections really nice.

---

### Post by H4F on 2009-07-05
hey really firestarter si not supported any more ?

---

### Post by dmizer on 2009-07-05
Ubuntu has a firewall by default. It's called IPtables.

Install GUFW in order to configure it via a graphical interface. Much better than Firestarter (IMHO) :)

---

### Post by LewRockwell on 2009-07-05
> **dmizer said:**
> Ubuntu has a firewall by default. It's called IPtables.

Install GUFW in order to configure it via a graphical interface. Much better than Firestarter (IMHO) :)

Seconded

.

---

### Post by sasho_zl on 2009-07-05
Also Shorewall is strong and easy to use iptables configuration tool. I have being using it for some time now and it works perfectly. This is the homepage: [http://www.shorewall.net/index.htm](http://www.shorewall.net/index.htm)
If you decide to try it I would recommend to download and install it from the official site because the version in the repositories is old. A ready to use deb packages can be found here:  [https://launchpad.net/%7Ebmonty/+archive/ppa]("https://launchpad.net/%7Ebmonty/+archive/ppa")

---

### Post by heyyy on 2009-07-05
as an absolute beginner i ask
because i've been using the firestarter for a some time now, i find the network monitoring feature very use because i can set the rules of the firewall based on that.
has any of those firewalls that feature?

---

### Post by heyyy on 2009-07-05
i mean those specific features:
# Real time firewall events view
# View active network connections, including any traffic routed through the firewall 
does any firewall except firestarter have them?

---

### Post by sasho_zl on 2009-07-05
> **heyyy said:**
> as an absolute beginner i ask
because i've been using the firestarter for a some time now, i find the network monitoring feature very use because i can set the rules of the firewall based on that.
has any of those firewalls that feature?
Well, firestarter indeed is very useful for that, but you can track what connections have been rejected by the firewall in the /var/log/messages logs. To see your current active connections you can use this command: [B]lsof | grep TCP
[/B]At the moment I'm using Shorewall with Webmin and host intrusion detection system called OSSEC. I'm configuring and checking the firewall logs through the Webmin modules and it's really good way to track what is going on in your system. Also OSSEC is checking all the system logs and it mails me if something is out of the ordinary. Ossec also has a active response module which blocks attackers automatically.
For now this security setup has been working great for me, but have in mind that I have applied those measures because I have anonymous FTP server and it's very important to keep a close eye on what is going on.

---

### Post by heyyy on 2009-07-05
if i keep firestarter will i have any "problems" because its outdated?

---

### Post by sasho_zl on 2009-07-05
> **heyyy said:**
> if i keep firestarter will i have any "problems" because its outdated?
I don't think so, but you can try a few online port scanners to check if everything is ok.
I would suggest those: [http://nmap-online.com/](http://nmap-online.com/)    and [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by lovinglinux on 2009-07-05
> **heyyy said:**
> if i keep firestarter will i have any "problems" because its outdated?

There a few threads on the forum that recommend you shouldn't run Firestarter all the time, which I believe you do, since you like the monitoring feature. It seems, although I'm not an expert and can't confirm, that Firestarter has bugs that could be exploited and since it requires root privileges to run, the attacker could get control of your entire system.

So you should configure the firewall rules and close Firestarter or any other firewll-manager you use. The real firewall (iptables) will run in the background, so you don't need Firestarter open all the time to be protected.

Anyways, why do you need to change the rules so often?

I would recommend using [gufw](apt:gufw) [apt-get] as already suggested and use another tool for monitoring, like [iptstate](apt:iptstate) [apt-get] 

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by heyyy on 2009-07-05
> **lovinglinux said:**
> There a few threads on the forum that recommend you shouldn't run Firestarter all the time, which I believe you do, since you like the monitoring feature. It seems, although I'm not an expert and can't confirm, that Firestarter has bugs that could be exploited and since it requires root privileges to run, the attacker could get control of your entire system.

So you should configure the firewall rules and close Firestarter or any other firewll-manager you use. The real firewall (iptables) will run in the background, so you don't need Firestarter open all the time to be protected.

Anyways, why do you need to change the rules so often?

I would recommend using [gufw](apt:gufw) [apt-get] as already suggested and use another tool for monitoring, like [iptstate](apt:iptstate) [apt-get]

ok i'll try it

but since firestarter was such a good programm why did it stop?
is there a clone or something to continue it?

---

### Post by lovinglinux on 2009-07-05
> **heyyy said:**
> ok i'll try it

but since firestarter was such a good programm why did it stop?

I don't know. I guess the developers priorities changed :) Some people argue that it doesn't need further development, but problems with Firestarter are becoming more common here in the forums. So why bother with it.

> **heyyy said:**
> is there a clone or something to continue it?

I'm afraid not. When I switched to Linux I also like it, because it feels like Windows firewalls, but now I have my own iptables rules and I rarely monitor the connections :)

I recommend that you read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial. Understanding how things work and how to correctly secure your system will give you more peace of mind than Firestarter ;)

---

### Post by dmizer on 2009-07-05
Firestarter hasn't exactly stopped. It's just been dropped from the Ubuntu support tree so it's not integrated well. It was dropped in favor of GUFW because Firestarter tends to be disruptive to typical networking tasks.

---

### Post by heyyy on 2009-07-05
> **sasho_zl said:**
> I don't think so, but you can try a few online port scanners to check if everything is ok.
I would suggest those: [http://nmap-online.com/](http://nmap-online.com/)    and [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

running the nmap gave me:
```
All 1000 scanned ports on ... are filtered
```
which means...?

---

### Post by sasho_zl on 2009-07-05
> **heyyy said:**
> running the nmap gave me:
```
All 1000 scanned ports on ... are filtered
```which means...?
It means that the firewall is doing it's job ;)
But I totally agree with **lovinglinux **and I also recommend that you change your iptables configuration tool.

---

### Post by heyyy on 2009-07-05
> **dmizer said:**
> Firestarter hasn't exactly stopped. It's just been dropped from the Ubuntu support tree so it's not integrated well. It was dropped in favor of GUFW because Firestarter tends to be disruptive to typical networking tasks.

ok could you give me some begginer instructions to do a pre-set up? (in gufw)

---

### Post by heyyy on 2009-07-05
> **heyyy said:**
> ok could you give me some begginer instructions to do a pre-set up? (in gufw)

i mean does the gufw set up some basic rules by on its own?

---

### Post by ishmael2k on 2009-07-05
> **heyyy said:**
> i mean does the gufw set up some basic rules by on its own?

I went ahead and got the latest Gufw for 9.04 (Gufw 9.04.2) and it auto set to: samba  allow   from: anywhere  I then added a rule to allow my network to be accessed and all seems to be working fine. 

[Here]("http://www.dedoimedo.com/computers/gufw.html") are some easy to follow directions.

---

### Post by Chemical Imbalance on 2009-07-05
> **heyyy said:**
> i know that the 80% of the people who will see this thread will say i dont really need a firewall....but i still want one
right now i have firestarter,which is no longer maintained.
so i'd like to install an up-to-date one


Of course no operating system on this planet should ever be without a firewall, period--if it is connected to the internet obviously.
Fortunately the linux kernel includes iptables.

Also fortunately, Ubuntu has ufw installed but not enabled.

Just read the man page for ufw.  You don't even really need gufw as ufw is very simple to use.

---

