---
title: "Use variables in /etc/network/iptables"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by bz-dev on 2014-09-17
I'm a OpenBSD refugee and have been used to working with the BSD packet filter for a long time.
Currently im working on both Ubuntu server's and Debian machines so, my questions relate to both of these platforms.

When creating packet filter rule sets i've always used a lot of variables in the file (pf.conf), e.g:

internal_net="10.12.23.0/24"
web_ports="80,443,8080:8081"

It was also possible to specify a file that contained a list of ip addresses or address ranges.

This helped me to create a firewall configuration that kept the lines on a reasonable length and was easy to read.
When  using iptables i've found that the lines in /etc/network/iptables can  become extremely long, which makes them harder to read.
I've tried reading the documentation of iptables but, havent found anything that appears to make this possible.
I know its possible to use both variables and external files when building a iptables script, this is not what i am looking for.

Is there a way to use variables, in a similar way, with iptables?
Is it possible to have iptables include a external file?

---

### Post by Lars Noodén on 2014-09-17
> **bz-dev said:**
> Is there a way to use variables, in a similar way, with iptables?
Is it possible to have iptables include a external file?

Which version of Ubuntu do you have on your Ubuntu machines?  Which script on your machine is generating your /etc/network/iptables file?  Perhaps there  is a script in [s]/etc/if-pre-up.d/[/s]  /etc/network/if-pre-up.d/

Anyway, if your scripts are using iptables-save and iptables-restore, there is not much of a way to use variables in the data file itself. If so, then you can have a script write out your file, using variables as a normal shell or perl script, and then load that.

Edit: that's not quite what you were hoping for, but that is what is available in iptables. PF is easier in that regard and several others.

---

### Post by bz-dev on 2014-09-17
(Sorry for my complete lack of knowledge here, Ubuntu is slightly  different than OpenBSD, still trying to get used to the new environment.)

Hi Lars,

thanks for your reply.

> **Lars Noodén said:**
> Which version of Ubuntu do you have on your Ubuntu machines?


I'm currently using Ubuntu server 14.04.

> **Lars Noodén said:**
> Which script on your machine is generating your /etc/network/iptables file?

All my servers are installed using preseeding.
The /etc/network/iptables file is generated before the server is installed and added to the /etc/network directory during the installation together with the /etc/network/interfaces file.

> **Lars Noodén said:**
> Perhaps there  is a script in /etc/if-pre-up.d/

A question about if-pre-up.d.
Theres two instances of the if-pre-up.d directory:
[LIST]
[*]/etc/if-pre-up.d 
[*]/etc/network/if-pre-up.d 
[/LIST]
Which one are we talking about and whats the (short version) difference?

> **Lars Noodén said:**
>  Anyway, if your scripts are using iptables-save and iptables-restore, there is not much of a way to use variables in the data file itself. If so, then you can have a script write out your file, using variables as a normal shell or perl script, and then load that.

Edit: that's not quite what you were hoping for, but that is what is available in iptables. PF is easier in that regard and several others.

I'm basically looking for a way to acheive the following tasks
[LIST]
[*]add/remove certain DROP rules that concerns ranges of ip addresses (this is where the use of external files comes in) 
[*]add/remove lists containing ports 
[*]on the NAT devices i have: adjust the values of the internal network (e.g: change 10.11.12.0/24 to 10.20.30.0/24) 
[/LIST]

It surely must be a way of doing this in iptables as well but, i just havent figured out how to do this yet.
I'm guessing that i might be a bit "stuck" in the PF way of things here... :)

---

### Post by Lars Noodén on 2014-09-17
> **bz-dev said:**
> 
A question about if-pre-up.d.
Theres two instances of the if-pre-up.d directory:
[LIST]
[*]/etc/if-pre-up.d 
[*]/etc/network/if-pre-up.d 
[/LIST]
Which one are we talking about and whats the (short version) difference?

The former was a typo (omission) on my part when typing.  I've fixed it above..

> **bz-dev said:**
> 

I'm basically looking for a way to acheive the following tasks
[LIST]
[*]add/remove certain DROP rules that concerns ranges of ip addresses (this is where the use of external files comes in) 
[*]add/remove lists containing ports 
[*]on the NAT devices i have: adjust the values of the internal network (e.g: change 10.11.12.0/24 to 10.20.30.0/24) 
[/LIST]

It surely must be a way of doing this in iptables as well but, i just havent figured out how to do this yet.
I'm guessing that i might be a bit "stuck" in the PF way of things here... :)

Sadly, iptables is harder to use than PF, more complex, *and* does not have as good documentation. 
 
The way I settled on to do approximately what you are also doing was to have a  shell script generate a file that was then fed into iptables-restore  Another way would be to call iptables directly from the script but that seems to create the possibility for race conditions.  

Which guides have you found so far?  The one I learned the most from was Oskar Andreasson's but it is now more than a few years old and there have been a few changes.

[https://www.frozentux.net/documents/iptables-tutorial/](https://www.frozentux.net/documents/iptables-tutorial/)

The man page for iptables-extensions also has a list of options.  

And if you haven't seen it yet, but are working on remote machines, iptables-apply can be useful.  I had used at jobs previously to keep from getting locked out -- after the first time.

---

### Post by bz-dev on 2014-09-17
> **Lars Noodén said:**
> Sadly, iptables is harder to use than PF, more complex, *and* does not have as good documentation. 

...Which is something i find rather strange. From the Ubuntu side of the fence i've been told this is more true about PF :P
 
> **Lars Noodén said:**
>  The way I settled on to do approximately what you are also doing was to have a  shell script generate a file that was then fed into iptables-restore  Another way would be to call iptables directly from the script but that seems to create the possibility for race conditions.  

It looks like this is the best way of doing it, for now at least.

> **Lars Noodén said:**
>  Which guides have you found so far?  

I can honestly not give you the name of a single guide i have read, ther are to many. Most of the information i've gotten about iptables have been found trough Google and the man pages.

The most interesting are the ones i'm using for my [honeypot project]("http://honeynet.org/node/1191"), which relates to blocking certain attacks, rate limiting and so on.
[LIST]
[*][port scanning and smurf attack']("http://sharadchhetri.com/2013/06/15/how-to-protect-from-port-scanning-and-smurf-attack-in-linux-server-by-iptables/")s 
[*][neat tricks with iptables]("http://newartisans.com/2007/09/neat-tricks-with-iptables/") 
[*][defend from attacks]("http://security.stackexchange.com/questions/4603/tips-for-a-secure-iptables-config-to-defend-from-attacks-client-side") 
[/LIST]

While i'm using this rules in a different manner than described in the articles, they still gave me a lot of insight into how iptables can be used.

> **Lars Noodén said:**
> The one I learned the most from was Oskar Andreasson's but it is now more than a few years old and there have been a few changes.

[https://www.frozentux.net/documents/iptables-tutorial/](https://www.frozentux.net/documents/iptables-tutorial/)

Thanks for that! :D
I haven't read that one yet, nice!

> **Lars Noodén said:**
>  The man page for iptables-extensions also has a list of options.  

And if you haven't seen it yet, but are working on remote machines, iptables-apply can be useful.  I had used at jobs previously to keep from getting locked out -- after the first time.

Oh yes, i got locked out once, then i learnt about the iptables-apply. Great tool i must say.

---

