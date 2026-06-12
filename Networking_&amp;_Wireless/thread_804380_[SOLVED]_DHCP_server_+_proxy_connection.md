---
title: "[SOLVED] DHCP server + proxy connection"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by fmpfmpf on 2008-05-23
OK, this is sort of a continuation from a previous thread, but with a different scenario.

I have 2 laptops, A and B.
both laptops have WLAN.

Laptop A is connected to the internet through an ethernet cable through "Manual proxy configuration".
Both laptops are already communicating with each other.
Tests using the "ping" command shows that.
However, laptop B cannot surf the internet.

What should i do to enable laptop B to surf the internet?

TQ

---

### Post by sonofusion82 on 2008-05-23
There are 2 options:
1. On laptop A, bridge the two wired and wireless connection. I am not really good at this in linux so I cant really help you on this, perhaps someone else might be able to help?
2. Install a proxy in laptop A such as polipo and configure it to use the parent proxy that you set in "Manual proxy configuration". Then in laptop B, set the "Manual proxy configuration" to laptop A

---

### Post by fmpfmpf on 2008-05-23
> 2. Install a proxy in laptop A such as polipo and configure it to use the parent proxy that you set in "Manual proxy configuration". Then in laptop B, set the "Manual proxy configuration" to laptop A

example:- in A, i open mozilla firefox and in the "connection settings", i use "Manual proxy configuration.
HTTP Proxy: abc.123.com
Port: 5000

So, i whould install polipo, and fix its configuration to:-
HTTP Proxy: abc.123.com
Port: 5000
Is this correct?

What configuration should i setup in B?

thank you

---

### Post by sonofusion82 on 2008-05-23
> **fmpfmpf said:**
> example:- in A, i open mozilla firefox and in the "connection settings", i use "Manual proxy configuration.
HTTP Proxy: abc.123.com
Port: 5000

So, i whould install polipo, and fix its configuration to:-
HTTP Proxy: abc.123.com
Port: 5000
Is this correct?

What configuration should i setup in B?

thank you

yes
in laptop A, polipo configuration file (/etc/polipo/config)
parentProxy=abc.123.com:5000

in B,  set the "Manual Proxy Configuration" to laptop A's IP address and port 8123 (polipo's default port). also ensure that laptop A's firewall has port 8123 is open.

---

### Post by fmpfmpf on 2008-05-23
i see this in the "config" file
# parentProxy = "squid.example.org:3128"

do i need to remove the # symbol?


> in B, set the "Manual Proxy Configuration" to laptop A's IP address
how do i do this?
how do i determine laptop A's address?

tqtqqt

---

### Post by sonofusion82 on 2008-05-23
yes, remove the # symbol.

the laptop's A's IP address is the IP address u used to ping from laptop B to laptop A. alternatively, type "ifconfig" in laptop A's command line.

---

### Post by fmpfmpf on 2008-05-23
it doesnt seem to work

laptop A
eth2:- inet addr:10.10.10.1

this is my firefox config in laptop B
Mnual proxy configuration checked
HTTP Proxy: 10.10.10.1
Port: 8123

what is wrong?

tq

---

### Post by cwgatling on 2008-05-23
Looks like you're nearly there. So you can ping 10.10.10.1 from Laptop B? 
If yes, you need to make sure the port 8123 is accepting connections. The only way I know on Linux is nmap. (I don't think telnet 10.10.10.1 8123 would work).

```
sudo apt-get install nmap
```

```
nmap 10.10.10.1 -p 8123
```

Do you see an entry for port 8123 with status 'Open'?

---

### Post by fmpfmpf on 2008-05-23
yes, i can ping from laptop B
so i install nmap in laptop A or B?

---

### Post by cwgatling on 2008-05-23
Cool. On Laptop B.

---

### Post by fmpfmpf on 2008-05-23
This is the output i get from B after typing "nmap 10.10.10.1 -p 8123

Starting Nmap 4.20 ([http://insecure.org](http://insecure.org)) at 2008-05-23 13:57 CEST
Interesting ports on 10.10.10.1:
PORT   STATE   SERVICE
8123/tcp filtered unknown
MAC Address: zz:zz:zz:zz:zz (VIA Networking Technologies)

Nmap finished: 1 IP adress (1 host up) scanned  in 13.337 seconds

so there is a connection, right?
so what should i fo next?

---

### Post by cwgatling on 2008-05-23
Good work. The port is filtered though! You are running a firewall on 10.10.10.1. You can install Firestarter to have a look at iptables and open up 8123.

---

### Post by fmpfmpf on 2008-05-23
i already haev Firestarter isntalled.
How do i open up port 8123?

---

### Post by cwgatling on 2008-05-23
Have a look at this -> [http://ubuntuforums.org/showthread.php?t=483902](http://ubuntuforums.org/showthread.php?t=483902)

I'm not at my Ubuntu machine now, unfortunately.

---

### Post by fmpfmpf on 2008-05-23
ok
btw, Firestarter in comp A, correct?

---

### Post by cwgatling on 2008-05-23
That's it exactly. :)

---

### Post by fmpfmpf on 2008-05-23
Have a look at this screenshot.
i have no idea what to fill in.
For Name, there is a scroll table and 1 of the options is DHCP, should i choose DHCP?
What should i fill in for the rest?

thank you

---

### Post by cwgatling on 2008-05-23
No, this is nothing to do with DHCP (so far!). I'd say don't choose a name if you don't have to.

Port - 8123
LAN clients only

---

### Post by fmpfmpf on 2008-05-23
laptop B still cant surf the internet.
btw, laptop A and B are communicating through WLAN

---

### Post by cwgatling on 2008-05-23
Can you run the nmap command again from Laptop B? Let's hope the port is open...

---

### Post by fmpfmpf on 2008-05-23
This is the output i get from B after typing "nmap 10.10.10.1 -p 8123

Starting Nmap 4.20 ([http://insecure.org](http://insecure.org)) at 2008-05-23 14:35 CEST
Interesting ports on 10.10.10.1:
PORT STATE SERVICE
8123/tcp closed unknown
MAC Address: zz:zz:zz:zz:zz (VIA Networking Technologies)

Nmap finished: 1 IP adress (1 host up) scanned in 13.337 seconds



it now says "closed unknown" instead of "filtered unknown"

---

### Post by cwgatling on 2008-05-23
:) That's a step backwards. That rule you created was to open a port, right?

---

### Post by fmpfmpf on 2008-05-23
Yes
it is under the "Allow service" rule.

i have deleted the rule, but it still shows "closed unknown"

---

### Post by fmpfmpf on 2008-05-23
ok, i have deleted the rule.
And also restarted both comps.
Now it says "filtered unknown".
What should i do from here onwards?
tqtqtq

---

### Post by cwgatling on 2008-05-23
You could try allowing just the IP address of laptop B. Sorry man, I've never used firestarter.
If you have a NAT router, you could even allow all hosts in that rule because the port would be blocked on your router,keeping you safe.

---

### Post by fmpfmpf on 2008-05-26
sorry for the late reply.
i was away.
how do i set the rule to allow just IP address from B?
i dont have any router
no problem, i really appreciate all your help =)

---

### Post by cwgatling on 2008-05-26
Ok, best to just allow B then. Type 'ifconfig' at a terminal window and note the address (I'd guess at 10.10.10.2 :)). You need to allow this in firestarter. Port 8123, host = IP address of Laptop B.

---

### Post by lecter255 on 2008-05-26
> **sonofusion82 said:**
> There are 2 options:
1. On laptop A, bridge the two wired and wireless connection. I am not really good at this in linux so I cant really help you on this, perhaps someone else might be able to help?


hey guys, is there a way to do option one? i really need to get that working.

---

### Post by fmpfmpf on 2008-05-26
facing some old problems again
will get back after i fix them
thanks

---

### Post by fmpfmpf on 2008-05-26
ok, old problem finally fixed.
i have set the rule for Firestarter but comp B still cannot surf the internet.

my firefox setting in comp B is:-
Manual proxy configuration
HTTP-Proxy: 10.10.10.1
Port:8123

any other suggestions?
TQ

---

### Post by fmpfmpf on 2008-05-26
anyone?? pls help

---

### Post by helgman on 2008-05-26
> **fmpfmpf said:**
> anyone?? pls help

Desperation? Again? ;-)

And no, I'm not trying to hijack anything here.

Quick question to fmpfmpf, and I don't know a lot about proxy servers, unfortunately, but have you tried using the same settings on laptop B as on laptop A?

And to sonofusion82, if the above (using the same settings) don't work, do you have any idea as to why not?

> **lecter255 said:**
> hey guys, is there a way to do option one? i really need to get that working.

Depends on if it's bridging or "Internet sharing" your after. [Here](https://help.ubuntu.com/community/NetworkConnectionBridge) are Ubuntu instructions for bridging, they are for Dapper but they might still work. For "Internet sharing", take a look [here](https://help.ubuntu.com/community/Internet/ConnectionSharing?highlight=(internet)|(sharing)).

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-27
> Quick question to fmpfmpf, and I don't know a lot about proxy servers, unfortunately, but have you tried using the same settings on laptop B as on laptop A?

do u mean the proxy settings?
in laptop A, i did "ifconfig eth2 10.10.10.1"
in laptop B, i used 10.10.10.1 as the firefox proxy config

is this what u mean?

---

### Post by helgman on 2008-05-27
> **fmpfmpf said:**
> is this what u mean?

No, I wondered if you tried using the same settings on laptop B as on laptop A, the exact same proxy settings that is.

> **fmpfmpf said:**
> example:- in A, i open mozilla firefox and in the "connection settings", i use "Manual proxy configuration.
HTTP Proxy: abc.123.com
Port: 5000

That's the one!

Helgman

---

### Post by fmpfmpf on 2008-05-27
yeap, tried it and it didnt work

---

### Post by helgman on 2008-05-27
> **fmpfmpf said:**
> yeap, tried it and it didnt work

I'm gonna re-install Ubuntu today so I can try and follow the steps shown above and see if I get stuck at the same point. Hope I'll be back to post soon ... ;-)

---

### Post by fmpfmpf on 2008-05-27
that would be great
thanks =)

---

### Post by helgman on 2008-05-27
How have you configured polipo? Have you made sure that it accepts connections from clients?
These are the changes I did in /etc/polipo/config ... I uncommented the following lines:

```
proxyAddress = "0.0.0.0"    # IPv4 only

[...]

parentProxy = "squid.example.org:3128"
```

and then I set laptop A as proxy for laptop B. When surfing from laptop B i got the following when trying to connect to [www.google.com:](www.google.com:)

```
504 Host squid.example.org lookup failed: Host not found

The following error occured while trying to access http://www.google.com:

504 Host squid.example.org lookup failed: Host not found
```

generated by laptop A. I take that as proof that the polipo config is working (apart from the fact that I don't have a proxy).

I also started Firestarter and opened port 8123, when removing that "policy" laptop B complains that the proxy server is refusing connections.

Any questions?

Helgman

---

### Post by fmpfmpf on 2008-05-27
> **helgman said:**
> How have you configured polipo? Have you made sure that it accepts connections from clients?
These are the changes I did in /etc/polipo/config ... I uncommented the following lines:

```
proxyAddress = "0.0.0.0"    # IPv4 only

[...]

parentProxy = "squid.example.org:3128"
```

and then I set laptop A as proxy for laptop B. When surfing from laptop B i got the following when trying to connect to [www.google.com:](www.google.com:)


u mean i have to use

```
proxyAddress = "0.0.0.0"    # IPv4 only

[...]

parentProxy = "squid.example.org:3128"
``` ?

isnt squid.example.org:3128 wrong?

tq

---

### Post by helgman on 2008-05-27
> **fmpfmpf said:**
> isnt squid.example.org:3128 wrong?

Yes, it's wrong. You should have your own settings there ... my questions was if you are using both those settings (not what they are set to) on laptop A, sorry if that was unclear.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-28
yea....i have set the poliop setting in laptop A to my proxy setting

---

### Post by helgman on 2008-05-28
AND to accept client connections? The reason I'm asking is the way the port is handled and the fact that it worked for me "right out of the box" (not exactly right of the box but almost).

To sum up my experience:

1) You have to configure your manual proxy settings (as you have).
2) You must accept client connections in the polipo configuration (on laptop A).
3) You have to open port 8123 in Firestarter.

That was it for me.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-29
Does laptop A hae to b in Ad-Hoc mode?
and laptop B connected to A with Ad-Hoc

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> Does laptop A hae to b in Ad-Hoc mode?
and laptop B connected to A with Ad-Hoc

Huh?

My setup had laptop A connected via wire to the Internet-delivering network and then I set up a wireless ad-hoc network (on laptop A) that laptop B connected to. How laptop A and B connect are not the real issue here as long as they use TCP/IP etc.

But if laptop B connects to laptop A using ad-hoc mode then yes, laptop A should use ad-hoc mode as well.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-29
nono, i mean...u said that you successfully connect A n B and they both can surf the internet.
are they connected through Ad-Hoc mode?

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> nono, i mean...u said that you successfully connect A n B and they both can surf the internet.
are they connected through Ad-Hoc mode?

Yes, I made an ad-hoc connection.

---

### Post by helgman on 2008-05-29
You still can't connect?

Are you still configured as per the other thread and do you have connectivity between laptop A and B?

What is the problem (now) and can you please post your polipo configuration?

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-29
i am having some problem now.
Laptop B cannot detect the Ad-Hoc signal from A

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> i am having some problem now.
Laptop B cannot detect the Ad-Hoc signal from A

So then you have to retrace the steps in the ad-hoc setup and find what went wrong there. Once you are connected it's time to go head-on with the proxy-problem.

---

### Post by fmpfmpf on 2008-05-29
ok, Firestarter is up and running in laptop A.
B is connected to A via Ad-Hoc.
they can ping each other.
however, B cannot surf the internet.
Here is my configuration.

Laptop A
Firefox
> Manual proxy configuration
HTTP Proxy: abc.123.com
Port: 3100

etc/polipo/config
> parentProxy = abc.123.com:3100

Firestarter

Allow service|Port|For
> Name: Unknown
Port: 8123
IP,host or network: 10.10.10.100 (B is now set to 10.10.10.100)

Network settings
> Internal connected network device: eth0
Local network connected device: eth2
"Enable Internet connection sharing" checked
"Enable DHCP for the local network" NOT checked

Laptop B
Firefox
> Manual proxy configuration
HTTP Proxy: 10.10.10.1 (10.10.10.1 is laptop A's ip)
Port: 8123

What is wrong?
TQ

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> What is wrong?

Did you configure the proxy (polipo) on laptop A to accept client connections?

// Helgman

---

### Post by fmpfmpf on 2008-05-29
etc/polipo/config
> parentProxy = abc.123.com:3100  

is this what u mean?

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> is this what u mean?

No, that one tells laptop A what proxy to use. As I stated in [this post](http://ubuntuforums.org/showpost.php?p=5052672&postcount=38) you also need to tell polipo that it should accept connections from clients as per this line:

```
proxyAddress = "0.0.0.0"    # IPv4 only
```

Make sure that it's not commented out (has a # before it). Also read the comments (I think they are above it) in the config-file. And don't forget to restart polipo after the changes are made.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-29
ok, i will try that.
btw, is my other configuration correct?
tq

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> ok, i will try that.
btw, is my other configuration correct?
tq

As long as you don't intend to use DHCP then I guess so, but it's hard to be sure ...

// Helgman

---

### Post by fmpfmpf on 2008-05-29
aik???
as long as i dont intend to use DHCP??
i thought all this while i have been trying to create a DHCP server?

after the new poliop change, i get this new scenario
In laptop B, in firefox.
i type [www.google.com](www.google.com) and get this message:-

Access Denied (authentication_failed)
Your credentials could not be authenticated: "Credentials required". You will not be permitted access until your credentials can be varified.
This is typically caused by an incorrect username and/or passowrd, but could also be caused by network problems.

What is wrong?
TQ

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> aik???
as long as i dont intend to use DHCP??
i thought all this while i have been trying to create a DHCP server?

I just thought the "DON'T use DHCP in Firestarter line ... never mind ... if your DHCP is working as it should then don't worry. Might be my mistake (don't have Firestarter installed anymore).

> after the new poliop change, i get this new scenario
In laptop B, in firefox.
i type [www.google.com](www.google.com) and get this message:-

Access Denied (authentication_failed)
Your credentials could not be authenticated: "Credentials required". You will not be permitted access until your credentials can be varified.
This is typically caused by an incorrect username and/or passowrd, but could also be caused by network problems.

What is wrong?

It more or less tells you ... you don't provide any credentials and you are required to authenticate. Can you tell if it's the abc.123-proxy or laptop A that requires you to authenticate?

---

### Post by fmpfmpf on 2008-05-29
> **helgman said:**
> I just thought the "DON'T use DHCP in Firestarter line ... never mind ... if your DHCP is working as it should then don't worry. Might be my mistake (don't have Firestarter installed anymore).?

ah....u mean the DHCP option. Understood

> **helgman said:**
> Can you tell if it's the abc.123-proxy or laptop A that requires you to authenticate?

how can i check this?
i do know, if i want to proxy surf in laptop A, i need a username and password.

thanks

---

### Post by helgman on 2008-05-29
> **fmpfmpf said:**
> how can i check this?
i do know, if i want to proxy surf in laptop A, i need a username and password.

It usually says on the page (if it's not a pop-up, in that case I don't know).

And if you need username/password on laptop A you probably need it on laptop B as well.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-29
Oops, my bad
i left out 2 small sentences.
Here is the complete notice:-

> Access Denied (authentication_failed)
Your credentials could not be authenticated: "Credentials required". You will not be permitted access until your credentials can be varified.
This is typically caused by an incorrect username and/or passowrd, but could also be caused by network problems.

For assistance, contact your help desk.
Proxy server: abc.123.com



> And if you need username/password on laptop A you probably need it on laptop B as well.
Nothing prompts me to insert my username and password in laptop B

---

### Post by helgman on 2008-05-30
> **fmpfmpf said:**
> Nothing prompts me to insert my username and password in laptop B

So you are usually prompted on laptop A?

Anyway ... you could research the [polipo manual](http://www.pps.jussieu.fr/~jch/software/polipo/polipo.html) to see if it says anything about *username* and *password* (use the "find"-function in Firefox, Ctrl+f and just search for the word you want to find), I'm sure something will turn up ... maybe not on the first "hit" but eventually. ;-)

Just make sure that you know what you want to do, who you want to authenticate and against what.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-30
yes, i am always prompted in A.
i will see what i can do
thanks

---

### Post by helgman on 2008-05-30
Please keep us posted ...

Helgman

---

### Post by fmpfmpf on 2008-06-02
i am currently having problems accessing the polipo website.
kinda got blocked.
will let continue posting when i get this problem solved. :)

---

### Post by helgman on 2008-06-02
> **fmpfmpf said:**
> i am currently having problems accessing the polipo website.
kinda got blocked.

Blocked? Are you trying to do this over a corporate network without the permission of the administrators or the "owner" of the network?

From the [manual](http://www.pps.jussieu.fr/~jch/software/polipo/polipo.html):
> 3.10.1 HTTP parent proxies

The variable parentProxy specifies the hostname and port number of an HTTP parent proxy; it should have the form ‘host:port’.

If the parent proxy requires authorisation, the username and password should be specified in the variable parentAuthCredentials in the form ‘username:password’. Only Basic authentication is supported, which is vulnerable to replay attacks.

The main application of the parent proxy support is to cross firewalls. Given a machine, say trurl, with unrestricted access to the web, the following evades a firewall by using an encrypted compressed ssh link:

     $ ssh -f -C -L 8124:localhost:8123 trurl polipo
     $ polipo parentProxy=localhost:8124


Regards,
Helgman

---

### Post by fmpfmpf on 2008-06-03
> Blocked? Are you trying to do this over a corporate network without the permission of the administrators or the "owner" of the network?

yes. ok, it has been unblocked...hurray.

```
$ ssh -f -C -L 8124:localhost:8123 trurl polipo
$ polipo parentProxy=localhost:8124
```

where should i type this code?
and in which comp?

TQ

---

### Post by helgman on 2008-06-03
> **fmpfmpf said:**
> where should i type this code?
and in which comp?

Read the text again (and maybe look it up in the manual for "correct" formating). There are a two options presented. And I can't really say where and why the commands should be used but the configuration goes on the computer with polipo installed ...

Regards,
Helgman

---

### Post by fmpfmpf on 2008-06-03
What is trurl?
is it the admin name?

---

### Post by helgman on 2008-06-03
> **fmpfmpf said:**
> What is trurl?

Read the text in the manual, not just the commands, and it will all be explained to you ...

Regards,
Helgman

---

### Post by fmpfmpf on 2008-06-03
i did read the explanation.

> Given a machine, say trurl...

the word machine sounds like a hardware, but i googled trurl and didnt any machine results.
so i suspect maybe it is a username. Is that correct?
tq

---

### Post by helgman on 2008-06-03
> **fmpfmpf said:**
> the word machine sounds like a hardware, but i googled trurl and didnt any machine results.
so i suspect maybe it is a username. Is that correct?
tq

I read it as "given a machine/computer, let's call it trurl ..."

To implement that solution you really should read the manual for ssh as well and make sure that you fully understand how it is supposed to work and what it is supposed to do. That's what I would do anyway. It also says that trurl is a computer "with unrestricted access to the web" and do you have a machine with *unrestricted access*?

What about the first solution presented in the manual?

Regards,
Helgman

---

### Post by fmpfmpf on 2008-06-03
i want to try the trurl method. How would i know the name of my machine?

> What about the first solution presented in the manual?
the 2 solutions are HTTP and SOCKS, is that what you mean?

---

### Post by helgman on 2008-06-03
> **fmpfmpf said:**
> i want to try the trurl method. How would i know the name of my machine?

The name is mapped against an IP address, so you don't really need the name, just the address. As I said above ... read the SSH manual and the commands might start to making sense. As I tried to tell you above, "trurl" should be directly connected to the Internet ... and computer A in your case is not, so you might need to introduce another computer in the equation. But I'm not sure so you'll have to research that solution on your own.

> the 2 solutions are HTTP and SOCKS, is that what you mean?

From the [manual](http://www.pps.jussieu.fr/~jch/software/polipo/polipo.html):
> If the parent proxy requires authorisation, the username and password should be specified in the variable parentAuthCredentials in the form ‘username:password’.

---

### Post by fmpfmpf on 2008-06-04
i googled for ssh manual and i got OpenSSH
is ssh and openssh the same?

tq

---

### Post by helgman on 2008-06-04
> **fmpfmpf said:**
> i googled for ssh manual and i got OpenSSH
is ssh and openssh the same?

Open a terminal and type **ssh -v**, that will tell you what version of SSH you are using (or try **man ssh**).

---

### Post by x88a on 2008-06-04
1st one works

---

### Post by fmpfmpf on 2008-06-04
i got this

OpenSSH_4.3p2 Debian-8ubuntu1.1, OpenSSL 0.9.8c 05 Sep 2006
usage: ssh [-1246AaCfgKkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-w tunnel:tunnel] [user@]hostname [command]


what should i do next?

tq

---

### Post by helgman on 2008-06-04
> **fmpfmpf said:**
> what should i do next?

You should sit down, try to figure out just what it is you are trying to do and then try and find the best way to do it. You also need to sit back and analyze the information presented to you, then figure out how to use it and why you requested it in the first place. 

I don't want to be rude but it looks like you stare at the manual quote presented above, see the commands and go "yeah, that's what I'd like ..." without know what it is. Yes, it says it's a more secure way of doing it but what else does it say? Can you meet the requirements? And don't just ask if you can, for there really is no point in setting it up if you don't understand what you are doing. I could be a malicious hacker seeing a chance to get a good route into what I'm starting to presume is a company network with someone doing something that might really be compromising the security ...

So this is my advice to you:

a) Take a moment, sit back, and try to understand what you are trying to do and why.

b) If you still want to do it then you should really research the solutions presented to you and make sure you understand them. Yes, it's a little bit of work but in the end you know what you've done.

c) When you are sure you understand them and you've tried to implement them - and they are still giving you a hard time, then ask away for all you are worth. Then your questions might be more precise and that will give the person helping you a fair chance in giving you a straight answer.

Now, you can ignore my advice and jump straight at the gun, but then answer me this; Where is the machine with unrestricted access? On what machine(s) are you going to install/use polipo? Why do you want to use the SSH solution?

Regards,
Helgman

---

### Post by fmpfmpf on 2008-06-04
> **helgman said:**
> You should sit down, try to figure out just what it is you are trying to do and then try and find the best way to do it. You also need to sit back and analyze the information presented to you, then figure out how to use it and why you requested it in the first place. 

I don't want to be rude but it looks like you stare at the manual quote presented above, see the commands and go "yeah, that's what I'd like ..." without know what it is. Yes, it says it's a more secure way of doing it but what else does it say? Can you meet the requirements? And don't just ask if you can, for there really is no point in setting it up if you don't understand what you are doing. I could be a malicious hacker seeing a chance to get a good route into what I'm starting to presume is a company network with someone doing something that might really be compromising the security ...

So this is my advice to you:

a) Take a moment, sit back, and try to understand what you are trying to do and why.

b) If you still want to do it then you should really research the solutions presented to you and make sure you understand them. Yes, it's a little bit of work but in the end you know what you've done.

c) When you are sure you understand them and you've tried to implement them - and they are still giving you a hard time, then ask away for all you are worth. Then your questions might be more precise and that will give the person helping you a fair chance in giving you a straight answer.

Now, you can ignore my advice and jump straight at the gun, but then answer me this; Where is the machine with unrestricted access? On what machine(s) are you going to install/use polipo? Why do you want to use the SSH solution?

Regards,
Helgman

ok, very sorry.
i will slowly do it.

i dont have any machine with unrestricted access.
polipo will be installed into comp A, which is connected to the internet using proxy

---

### Post by helgman on 2008-06-04
> **fmpfmpf said:**
> ok, very sorry.
i will slowly do it.

i dont have any machine with unrestricted access.
polipo will be installed into comp A, which is connected to the internet using proxy

Thank you.

Now, this is what I would do if I was in your position. I would open the polipo configuration file on computer A and then make sure that this line is added (don't know if there is an exact location but I'd put it somewhere near the parentProxy line)
```
parentAuthCredentials = *username*:*password*
```
Where *username* and *password* is the username and password that computer A uses to connect to it's proxy. After that I'd restart polipo and try to get on the Net from computer B. Just remember that the [manual](http://www.pps.jussieu.fr/~jch/software/polipo/polipo.html#HTTP-parent-proxies) says that:
> Only *Basic* authentication is supported, which is vulnerable to replay attacks.
Then again we don't know what kind of authentication is used by computer A at this very moment ... and since I've not worked that much with proxy servers I don't know how they normally function when it comes to authentication. If you feel the slightest bit unsure about using this method then don't. Research the current situation (what authentication is used by computer A, do I impose a new risk in the network etc) and then make a decision.

From my perspective, this is the "simplest" setup ... a fancier solution might need some more research, and maybe even the use of other tools then the once you are using now, I don't know ...

Regards,
Helgman

---

### Post by fmpfmpf on 2008-06-06
OMG
It workksss!!!!!!!!

THHAAANNNKKKKK YYYOOOUUUUUU!!!!!!!!!!!!

---

