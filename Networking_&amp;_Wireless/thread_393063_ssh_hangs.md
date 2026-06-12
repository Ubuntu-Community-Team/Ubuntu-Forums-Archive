---
title: "ssh hangs"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by bb4r on 2007-03-25
I'm not even sure where to start to troubleshoot this, but it is really annoying at best and at worst prevents me from doing much remotely.  

When I try to ssh into my 6.10 box, it takes around 2 minutes for a response.  Some times the connection times out before I get a response.  Once connected, the terminal will sporadically hang for a few minutes.  When this happens, traffic on other ports (e.g., 80) is unaffected.  Just ssh.

In general, this problem may be related to mythtv.  I've setup several combined front/backend boxes on Ubuntu 6.10, but this is the first time I've experienced this problem.  I think it started after installing mythtv and mysql.

I tried killing all mysql processes and mythbackend, but the problem still persists.

Can anyone assist?

---

### Post by souki on 2007-03-25
do you have the same symptoms when connecting to localhost ?
do you have duplicate ip adresses ?
do you have good ethernet cable ?

---

### Post by bb4r on 2007-03-25
> **souki said:**
> do you have the same symptoms when connecting to localhost ?
do you have duplicate ip adresses ?
do you have good ethernet cable ?

Wow, thanks!  never thought to try and ssh to localhost!  Connects immediately, so not an ssh server problem I guess.

No duplicate IP address

AFAIK, cable is good.  When ssh hangs, I can open a browser and connect immediately to /mythweb and transfer a recording at ~ 11 MB/s.  I've not tried any other ports.  If it was a cable or router problem, I'd figure that port 80 would also be unresponsive.  

hmm...  What could make port 22 hang over the LAN, but not port 80?

---

### Post by souki on 2007-03-25
can you double check your cable ?
I can't explain why but it could be this

if the cable is ok, try to isolate the problem, change the sshd port number, and try to connect to this new port

---

### Post by thornomad on 2007-03-25
Have you tried logging in from other machines on the network?  Narrowing down if the problem is the client or the server?

It may have something to do with resolving the DNS address of the machine ... or the way that SSH is looking up the IP address that is making it take so long ... I don't know much about that, but I have seen that cause a problem before.

---

### Post by souki on 2007-03-25
> **thornomad said:**
> 
It may have something to do with resolving the DNS address of the machine ... or the way that SSH is looking up the IP address that is making it take so long ... I don't know much about that, but I have seen that cause a problem before.

yes, you can have a long delay at connect, but not after
anyway, to eliminate the dns problem, use the ip address

---

### Post by kg1 on 2007-03-25
To gather some detail about what ssh is actually doing, you can connect using the -v option with the ssh client.
```
$ ssh -v -v -v hostname
```
To be even more useful, you can stop and restart the sshd daemon with debugging output
[note: don't do this if you are connected to the box via ssh ;) ]
```
sudo /etc/init.d/ssh stop
sudo /usr/sbin/sshd -d -d -d 
``` 
When you are done testing, kill the sshd process and restart 
```
sudo /etc/init.d/ssh start
```
While this will give gobs of output, it should provide a clue as to where the problem is....

---

### Post by bb4r on 2007-03-25
Hi all, thanks for all the suggestions!
I am connecting via IP so DNS issues shouldn't be an issue.

OK now we are getting somewhere, though this doesn't explain why the terminal becomes temporarily unresponsive while connected, but first things first, right.

```
$ ssh -v -v -v 192.168.15.106
OpenSSH_4.2p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.15.106 [192.168.15.106] port 22.
debug1: Connection established.
debug1: identity file ~/.ssh/identity type -1
debug1: identity file ~/.ssh/id_rsa type -1
debug1: identity file ~/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2
debug2: fd 3 setting O_NONBLOCK
debug1: An invalid name was supplied
Cannot determine realm for numeric host address
```
At which point it hangs for a bit, then returns the following

```
debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error
```
Next comes a whole bunch of output, but best I can tell, it is trying different authentication methods after verifying the RSA key, finally getting to password, at which point, I get prompted for a password.  I've just pasted some of the output below.  I could paste it all, but it is pretty long. 

```
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
```
Then it is searching the ~/.ssh directory for private keys, doesn't find any in identity, id_rsa, or id_dsa

```
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
```
I get the same result with 2 different clients (both running Mac OS 10.4.8)  So, I guess I want to force it to just straight to password authentication by either specifying an argument (-o ?) or editing either config file (server?)

Thanks!

---

### Post by Mr. C. on 2007-03-25
DNS will matter even using an IP address, as tcpwrappers does reverse mapping to determine a name.

What's in your /etc/resolv.conf ?

If its your router's address, place the name servers that your ISP provides there instead, as in :

nameserver ip1
nameserver ip2

Place the fastest, most responsive server first.  After you've made this change, test ssh again.  No need to reboot.

MrC

---

### Post by bb4r on 2007-03-25
> **Mr. C. said:**
> DNS will matter even using an IP address, as tcpwrappers does reverse mapping to determine a name.

What's in your /etc/resolv.conf ?

If its your router's address, place the name servers that your ISP provides there instead, as in :

nameserver ip1
nameserver ip2

Place the fastest, most responsive server first.  After you've made this change, test ssh again.  No need to reboot.

MrC

Thanks for the suggestion, but, Hmm....  I tried of the ISP DNSs and no change.  I hadn't realized this could be an issue.  Shouldn't ssh work on a LAN with no connection to the outside world, like if I unplugged my cable modem from the router?  Does an ISP-supplied DNS every change?

---

### Post by Mr. C. on 2007-03-25
Sure, it will work fine without a connection.  Keep in mind, if you have your system configured to use DNS, it will try to do so.  With a link down, it will return an immediate failure, so there's no harm.

Here's a list in order of things to try or focus on:

1) have you disabled IPv6 ?  If not, do so and try again:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

If this fails to resolve, lets continue with 2.

2) have you ensured that there is no packet loss or other network trouble ?

3) can you maintain a sustained FTP transfer ?

4) Does mythtv install any SSL libraries that might have caused conflict with those in use by SSH ?

5) Have you tried UseDNS no in sshd_config ?

MrC

---

### Post by souki on 2007-03-26
I don't use dns on my lan, and have a default ubuntu config
I have no problem with sshd

maybe you could try to reconfigure sshd
sudo dpkg-reconfigure openssh-server

another thing: are you doing password auth or key auth ?
if you are doing key auth, maybe your keys are wrong

you need server side logs to debug this

---

### Post by afljafa on 2007-03-26
I have the same problems - takes about 30 seconds to connect. The remote machines are fine (putty test under windows) so I`m guessing it`s a client problem.

EDIT - Disabling IPV6 seems to do the trick.

---

### Post by bb4r on 2007-03-26
OK, at work now, but I'll dig into the server-side logs and post up the relevant parts.  I"ve not disable IPv6, so I'll do that as well.  Thanks again for the help!

regarding public key v. password auth, I may need to learn a bit more about ssh.  I see from my client logs (that I posted) that it is trying first public key auth but not finding my private key in ~/.ssh.  I guess another set of keys can be stored in ~/.ssh for authentication as opposed to server id verification and encryption?  I'd rather just do password auth, which I assume can be set in sshd?

---

### Post by Mr. C. on 2007-03-26
> **souki said:**
> 
maybe you could try to reconfigure sshd
sudo dpkg-reconfigure openssh-server
   This is poor advice.  Please resist the temptation to throw the baby out with the bathwater.
> **souki said:**
> 
another thing: are you doing password auth or key auth ?
if you are doing key auth, maybe your keys are wrong
 
This is irrelevant.  The OP can connect - but there are performance issues.  Incorrect keys would not allow a connection.
> **souki said:**
> 
you need server side logs to debug this
There is nothing in the logs that will assist in this problem.  IPv6 incompatibilities and DNS failures are not generally logged.

MrC

---

### Post by souki on 2007-03-27
> **Mr. C. said:**
> This is poor advice.  Please resist the temptation to throw the baby out with the bathwater.

maybe a bad configuration caused by mythtv.
There is no temptation here, just guessing mythtv has changed something, are you saying reseting a config file to default is 'evil' ?
 

> 
This is irrelevant.  The OP can connect - but there are performance issues.  Incorrect keys would not allow a connection.
right

> 
There is nothing in the logs that will assist in this problem.  IPv6 incompatibilities and DNS failures are not generally logged.
what proves it is an IPV6 or DNS problem ? symptoms ?
what is causing hang during the session ? ipv6 ? dns ? please explain
default config for me is ok (and so it is for the majority of the ubuntu users)

for what I understood, symptoms are : ssh working before and during mythtv, problem starting after uninstall

---

### Post by Mr. C. on 2007-03-27
> **souki said:**
> maybe a bad configuration caused by mythtv.
There is no temptation here, just guessing mythtv has changed something, are you saying reseting a config file to default is 'evil' ?
 
I'm saying that taking random approaches rarely solves problems reliably.  Problem isolation requires eliminating one variable at a time.  The Windows "reinstall" mentality is wasteful, and counter-productive.

> **souki said:**
> 
what proves it is an IPV6 or DNS problem ? symptoms ?
what is causing hang during the session ? ipv6 ? dns ? please explain
default config for me is ok (and so it is for the majority of the ubuntu users)

We have no proof yet; what we do have is a small amount of data, and an understanding that  specific configurations and hardware are likely to experience problems with IPv6 and/or caching DNS servers on commodity routers.  Since these are easy to eliminate as candidates, without hack and slash approaches, they should be eliminated or verified first.

> **souki said:**
> 
for what I understood, symptoms are : ssh working before and during mythtv, problem starting after uninstall

Then you need to re-read the posts - the problems also occurred *while* mythtv was installed.  Regardless, problem diagnosis doesn't occur by random multi-step methods.  This approach is of no value to someone who has a significant investment of time and energy preparing a system of some consequence.

MrC

---

### Post by bb4r on 2007-03-27
Greetings Mr. C and Souki - I've finally got some free time to continue troubleshooting.

OK, to recap and perhaps clarify:
1) I installed ssh on a fresh install of ubuntu.  Worked perfectly.
2) At some point, I started getting performance issues that consist of
a) a long time for initial connection, sometimes long enough to time out
b) terminal becoming intermittently unresponsive for a few minutes once connected.
3) I think the problem originated when I installed mythtv and mysql.  I did this at the same time, so I can't say the start of the problem corresponds to installation of one or the other.

I tried specifying my ISPs DNS and I just disabled IPV6.  Neither has fixed the problem.  I know that correlation does not prove causality, but since it worked fine with both the DNS set to my router and IPV6 enabled on a clean (plus ssh) instal, I am beginning to suspect mythtv and/or mysql.  However, given the wide usage of these apps, I can't imagine that others would not be reporting similar problems...

I do greatly appreciate both of you help and advice.  I've tried several other distros and found the online ubuntu community to be more responsive than the others with which I've fiddled.:)

---

### Post by Mr. C. on 2007-03-27
How did you install MythTV and MySql ?  Pre-built packages or source ?  And from where ?

MrC

---

### Post by bb4r on 2007-03-27
prebuilt packages from the ubuntu repositories (after adding the non-default ones)

installed using 
```
sudo apt-get install mythtv-frontend mythtv-backend mythtv-database mysql-server

```

I should add that I did this via ssh... with no performance issues.

---

### Post by tjansson on 2007-08-14
I had a somewhat similar problem and found the solution here:
[http://ubuntuforums.org/showthread.php?p=3189998#post3189998](http://ubuntuforums.org/showthread.php?p=3189998#post3189998)

---

