---
title: "Firewall not working in 13.10 anymore ..."
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2013-11-13
It did work in 12.04 ... now there's a wifi site login I use that doesn't seem to log in with ufw enabled.  After running 

sudo ufw disable

it works fine.

The rules I used both times I got from:

[http://ubuntuforums.org/showthread.php?t=1876124&highlight=gufw+restrictive+policies](http://ubuntuforums.org/showthread.php?t=1876124&highlight=gufw+restrictive+policies)

I did it again to see if I made an error the 1st time.  It acted exactly the same way.

Now, are there any ufw/gufw guides that actually explain it without assuming you're already a wireless expert and don't need proper examples that explain why you're doing this and don't just throw things in as an example without explaining whether it's appropriate to use it?

Please don't tell me I don't need a firewall in linux if I'm not running a server.  I want one.

Please don't tell me to learn iptables.  I'd actually rather use *Windows* than learn iptables unless I'm going to get paid for it.

Frankly, the state of guides for this sort of thing for those of us who aren't willing to dig that deep into the system, or those who aren't capable of it, is pathetic.

If someone could point me to a reliable guide that won't drive users back to windows, I'd be ecstatic.

---

### Post by Rob Sayer on 2013-11-14
OK, I reset ufw preferences back to the defaults in terminal.

Having read about many issues with gufw, and considering the stuff I've been able to find on it is out of date, I then tried the steps in the link in my first post ... which worked *just fine* iin 12.04 BTW ... using ufw.

Same results.  The hotspot I'm using right now has a login.  It didn't connect until I disabled the firewall in the terminal.

This is a netbook.  I don't use it much at home.  I use it in public hotspots usually.  I want a firewall.  Any ideas?

---

### Post by jansdejager on 2013-11-15
i don't know much about iptables except for tutorials i've followed, but frontends are regularly just scripts of tutorials and the shortcuts they take sometimes become redundant (like gksu in recent releases, although I can't get pkexec to work but anyway). Just consult the latest iptables documentation, there is a chapter on ssh only: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Rob Sayer on 2013-11-15
Thanks, but I feel that having to use iptables to set up a firewall in ubuntu ... which claims to be the linux distro for non techies ... is just *preposterous*.

I'm definitely not incapable of learning that stuff but I'm not willing to do it unless I'm going to get paid to do so.  I'd rather use windows.

The thing is, all the guides on setting up a firewall in ubuntu I can find either:

- don't tell you anything beyond how to install it and find it on the menus or

- are written in language such that if I could understand it I wouldn't have had to ask in the first place.

Can't anyone direct me to something reasonably understandable that actually works in 13.10?

---

### Post by Rob Sayer on 2013-11-15
OK, I tried seeing what  may be different in 13.10.  Samba isn't installed by default like it was in 12.04.  I installed it and added a rule in ufw to enable it.

No joy.  I still have to disable ufw to connect to this particular hotspot.

Is there a way to tell which port is being blocked when I make an unsuccessful attempt to log in with ufw enabled?

Once again, this is ridiculously cockeyed.  Even worse than audio configuration and finding out that the ubuntu install partitioner doesn't properly support 4K hard drives (which have been around for at least three years).

---

### Post by jansdejager on 2013-11-16
get rid of ufw unless it's supported by ubuntu officially (otherwise it will just give you headaches)

[h=2]Allowing Incoming Traffic on Specific Ports[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]You could start by blocking traffic, but you might be working over SSH, where you would need to allow SSH before blocking everything else.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]To allow incoming traffic on the default SSH port (22), you could tell iptables to allow all TCP traffic on that port to come in.[FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Referring back to the list above, you can see that this tells iptables:[FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]append this rule to the input chain (-A INPUT) so we look at incoming traffic[FONT=inherit][/FONT]
[*=left]check to see if it is TCP (-p tcp). [FONT=inherit][/FONT]
[*=left]if so, check to see if the input goes to the SSH port (--dport ssh).[FONT=inherit][/FONT]
[*=left]if so, accept the input (-j ACCEPT).[FONT=inherit][/FONT][FONT=inherit][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu]Lets check the rules: (only the first few lines shown, you will see more)[FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo iptables -L
[FONT=inherit][/FONT]Chain INPUT (policy ACCEPT)
[FONT=inherit][/FONT]target     prot opt source               destination
[FONT=inherit][/FONT]ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
[FONT=inherit][/FONT]ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Now, let's allow all incoming web traffic[FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Checking our rules, we have[FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo iptables -L
[FONT=inherit][/FONT]Chain INPUT (policy ACCEPT)
[FONT=inherit][/FONT]target     prot opt source               destination
[FONT=inherit][/FONT]ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
[FONT=inherit][/FONT]ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
[FONT=inherit][/FONT]ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]We have specifically allowed tcp traffic to the ssh and web ports, but as we have not blocked anything, all traffic can still come in.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[h=2]Blocking Traffic[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Once a decision is made to accept a packet, no more rules affect it. As our rules allowing ssh and web traffic come first, as long as our rule to block all traffic comes after them, we can still accept the traffic we want. All we need to do is put the rule to block all traffic at the end.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo iptables -A INPUT -j DROP
[FONT=inherit][/FONT]sudo iptables -L
[FONT=inherit][/FONT]Chain INPUT (policy ACCEPT)
[FONT=inherit][/FONT]target     prot opt source               destination
[FONT=inherit][/FONT]ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
[FONT=inherit][/FONT]ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
[FONT=inherit][/FONT]ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
[FONT=inherit][/FONT]DROP       all  --  anywhere             anywhere[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Because we didn't specify an interface or a protocol, any traffic for any port on any interface is blocked, except for web and ssh.[/FONT][/COLOR]

---

### Post by Rob Sayer on 2013-11-16
Hmm.  That was actually rather understandable.  Have to read it some more.  Thanks.

I have been questioning ufw/gufw myself actually.

---

### Post by Rob Sayer on 2013-11-16
OK.  I had a more in depth look at iptables guides.

It's totally ridiculous to expect the average user to have to learn all that to just have a non server firewall.  *Preposterous*.  I have some background and am more knowledgeable than many ubuntu users whose posts I've read here.  I just don't have the patience ... and I don't believe it should be necessary ... but people who don't even know enough not to trust 3rd party ppa's would be completely baffled.

If ubuntu wants to call itself the distro for the average non geek user they're going to have to do a lot better than this.

---

### Post by jansdejager on 2013-11-18
probably there can't be so many user-friendly tweaking tools because the core functions are always improving on new releases of the daemon-based tools, and Ubuntu wants to stay up to date in order to retain the support of advanced users. If you use LTS then it is more likely to be user-friendly and predictable. Especially if you use don't update too often. Unless there is some new features on saucy that you would like to use. I think the iptables tool is very easy to use. If you learn the basics then you will feel less deterred next time you want to attempt a more complicated setup.

---

### Post by Rob Sayer on 2013-11-18
> **jansdejager said:**
> ... probably there can't be so many user-friendly tweaking tools because the core functions are always improving on new releases of the daemon-based tools, and Ubuntu wants to stay up to date in order to retain the support of advanced users.... 

I'm having trouble with the notion that "core functions are always improving" if basic tools like ufw and gufw are no longer working in the latest version.  How would having those work deter advanced Linux users?

> If you use LTS then it is more likely to be user-friendly and predictable. Especially if you use don't update too often. Unless there is some new features on saucy that you would like to use. I think the iptables tool is very easy to use. If you learn the basics then you will feel less deterred next time you want to attempt a more complicated setup.

I use LTS on 2 other machines.  I *would* use it on this netbook if the GPU kernel drivers for 12.04 worked properly on it.  LTS is just not always an option for everyone.

Whether you (or anyone else) finds iptables easy to use is irrelevant.  I don't want to *have* to learn it.  I studied Unix/C before linux was written and am not incapable of learning iptables, just seriously disinclined to do so.  And I don't give a tinker's damn about geek points.  Maybe I got a bit burnt out on the subject but there it is ...

And what about all those newer users who still think in Windows and automatically assume every problem they're having in Ubuntu is a virus?  And who don't have a clue why Linux viruses are virtually non existent?  How far are they going to get with iptables?  Straight back to Windows I suspect.

Does anyone have useful diagnostic steps I could take in ufw/gufw?

---

### Post by jansdejager on 2013-11-19
if i'm not mistaken ufw/gufw just interfaces with iptables anyway, so why don't you retrieve the iptables setup that has been generated on your lts machines and copy it in full on your netbook? if you type iptables -l on one of your ufw/gufw machines it will give you a readout of the iptables rules, then just reproduce it with iptables again.

from [https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)
> [UFW]("https://help.ubuntu.com/community/UFW")[COLOR=#333333][FONT=Ubuntu] (Uncomplicated Firewall) is a front-end for iptables and is particularly well-suited for host-based firewalls. UFW was developed specifically for Ubuntu (but is available in other distributions), and is also configured from the terminal.[/FONT][/COLOR]
I'm sorry UFW is not yet supported on saucy but perhaps you can try and contact the author or find somebody on [https://launchpad.net/ufw](https://launchpad.net/ufw) who can recompile the code for you. The author hasn't been active since 2007 there

---

### Post by Rob Sayer on 2013-11-19
That first suggestion is good but I'm afraid that for my netbook ... I'm quite happy with 12.04 on my others but it doesn't work properly with this netbook ... I'm looking at other distros at this point.  Perhaps one that *does* have a properly supported firewall GUI?

The thing is, I'm finding that ufw/gufw is far from the only package that's broken for 13.10.

---

### Post by jansdejager on 2013-11-20
also try the official ubuntu release. it might just be that gufw is not supported on kde (the g usually stands for gnome).

---

### Post by bashiergui on 2013-12-10
Don't know if you have solved this yet. 
What are your rules set to in ufw when it blocks wifi? 


There are no simple guides because the configuration depends entirely on what your use case is. I gather that this is on a home Ubuntu desktop with no services running. If so, then a very simple yet robust configuration would be to deny all in and allow all out. That configuration would also allow your wifi to work.

---

