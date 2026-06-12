---
title: "NFS: Feisty Serv&amp;client, = 'mount: RPC: Timed out'"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by virgiltibbs on 2007-06-18
Hi there,
I've been googling and reading through these forums for about an hour now and I think its probably time to admit defeat and ask for help.
I'm relativly proficient user going on power user with ubuntu, I understand bash and its various wrappers in different desktops and likewise with text editors. 
[ie I can substitute terminal for konsole, vi for kwrite & vice versa]

I am trying to set up a NFS share on a Feisty XUbuntu box, just pretend its a regular ubuntu dont bother to give me anything special for it.
I am trying to mount the share on a Feisty Kubuntu box.
Just in case it matters to you, what i am trying to achieve by this is sharing(read+write) the '/var/www' folder of the dev server(xubuntu) to the workstation/desktop(kubuntu). This is intended to have the effect of making web dev very neat and tidy.

Ok, because i believe I am getting an error which is not 'standard', I am going to follow [this]("http://ubuntuforums.org/showthread.php?t=249889") guide, to the word, and put down the responses here:

Install NFS Server Support
[I]
ok this is easy, i just apt get the things it said.
type the config command choose not to bind loopback then restart it.[/I]

sudo mousepad /etc/exports
in there i put
/var/www 192.168.1.1/24(rw,no_root_squash,async)

-ie share /var/www to local network with read write

then restart the nfs server and ,make exports file be used or something    
> timmy@devserv:~$ sudo mousepad /etc/exports
Password:
timmy@devserv:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export " 192.168.1.1/24:/var/www".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]
timmy@devserv:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export " 192.168.1.1/24:/var/www".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
timmy@devserv:~$              
I dont know if these subtree checks make any difference but your bet might be better than mine.
anyway
so by then the server should be good, up and running.

Now the kubuntu client.
> sudo apt-get install portmap nfs-common 
sudo mkdir /var/www -Gets created &stuff gets installed.
I'm going to try mounting it manually, before i do fancy stuff with fstab 
> timmy@timmy-desktop:~$ sudo mount 192.168.1.110:/var/www /var/www
Password:
mount: RPC: Timed out
timmy@timmy-desktop:~$

the error is **mount: RPC: Timed out**
a quick [search]("http://www.google.co.uk/search?num=100&hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&as_qdr=all&q=nfs+mount++%22mount%3A+RPC%3A+Timed+out%22+ubuntu&btnG=Search&meta=") on google has proven inconclusive:
there are several theories I have seen:
Bug in package - v unlikly as this does not seen to be a widespread problem
firewall - I have dissabled + wiped ip tables for client, i will for server if you think this is problem but both client and server were on default installs... so ... ?
also it is possible portmap services are not running but i have run
> sudo /etc/init.d/portmap start
sudo /etc/init.d/nfs-common start
sudo /etc/init.d/nfs-kernel-server start and it is evident that they are running....

Any suggestions, or even solutions would be very welcome,
[Here is google's finds]("http://www.google.co.uk/search?hl=en&lr=&client=firefox-a&rls=com.ubuntu:en-US:official&as_qdr=all&q=+site:ubuntuforums.org+nfs+mount+ubuntu+%22mount:+RPC:+Timed+out%22") of previous mentions of this problem on ubuntuforum, you might find it useful, - i didnt.

If it is a small, stupid mistake on my behalf, my utmost apologies in advance.

cheers
-tim

---

### Post by Mr. C. on 2007-06-18
Run and show output from:

```
rpcinfo -p timmy-desktop
rpcinfo -p devserv
```

---

### Post by virgiltibbs on 2007-06-18
timmy@devserv:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32790  status
    100024    1   tcp  52046  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32798  nlockmgr
    100021    3   udp  32798  nlockmgr
    100021    4   udp  32798  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  35229  nlockmgr
    100021    3   tcp  35229  nlockmgr
    100021    4   tcp  35229  nlockmgr
    100005    1   udp   1003  mountd
    100005    1   tcp   1006  mountd
    100005    2   udp   1003  mountd
    100005    2   tcp   1006  mountd
    100005    3   udp   1003  mountd
    100005    3   tcp   1006  mountd

---

### Post by virgiltibbs on 2007-06-18
timmy@timmy-desktop:~$ rpcinfo -p timmy-desktop
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  33226  nlockmgr
    100021    3   udp  33226  nlockmgr
    100021    4   udp  33226  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  37993  nlockmgr
    100021    3   tcp  37993  nlockmgr
    100021    4   tcp  37993  nlockmgr
    100005    1   udp    970  mountd
    100005    1   tcp    973  mountd
    100005    2   udp    970  mountd
    100005    2   tcp    973  mountd
    100005    3   udp    970  mountd
    100005    3   tcp    973  mountd
    100024    1   udp   1030  status
    100024    1   tcp   1770  status

---

### Post by Mr. C. on 2007-06-18
I should have been more clear.  Run both from the client.

MrC

---

### Post by virgiltibbs on 2007-06-18
no, its probably my fault interpretting what you put differently from how it was written...
anyway
> 
timmy@timmy-desktop:~$ rpcinfo -p devserv
rpcinfo: devserv is unknown host
timmy@timmy-desktop:~$ rpcinfo -p timmy-desktop
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  33226  nlockmgr
    100021    3   udp  33226  nlockmgr
    100021    4   udp  33226  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  37993  nlockmgr
    100021    3   tcp  37993  nlockmgr
    100021    4   tcp  37993  nlockmgr
    100005    1   udp    970  mountd
    100005    1   tcp    973  mountd
    100005    2   udp    970  mountd
    100005    2   tcp    973  mountd
    100005    3   udp    970  mountd
    100005    3   tcp    973  mountd
    100024    1   udp   1030  status
    100024    1   tcp   1770  status
timmy@timmy-desktop:~$            

thanks for the help... :)

---

### Post by Mr. C. on 2007-06-18
Ok, we're still missing info from the server, because its host name can't be translated from the desktop.  We're trying to see if your portmapper is reachable from the client.  Assuming your server's IP is 192.168.1.110, run :

rpcinfo -p 192.168.1.110

from your desktop.  Change the IP if my assumption is incorrect.

Save yourself some trouble, add

192.168.1.110:  devserv 

to your /etc/hosts file in the desktop machine.  Then you can refer to the host by name as well as by IP.

MrC

---

### Post by virgiltibbs on 2007-06-18
you are right... that is the IP
> timmy@timmy-desktop:~$ rpcinfo -p 192.168.1.110
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32790  status
    100024    1   tcp  52046  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32798  nlockmgr
    100021    3   udp  32798  nlockmgr
    100021    4   udp  32798  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  35229  nlockmgr
    100021    3   tcp  35229  nlockmgr
    100021    4   tcp  35229  nlockmgr
    100005    1   udp   1003  mountd
    100005    1   tcp   1006  mountd
    100005    2   udp   1003  mountd
    100005    2   tcp   1006  mountd
    100005    3   udp   1003  mountd
    100005    3   tcp   1006  mountd

good idea - i'll add it to hosts now... cheers for advice...

---

### Post by Mr. C. on 2007-06-18
Good, portmap is reachable. Ensure the mountd is running on the server.  It needs to be running.

Next, try disabling iptables on the server and retest.

This may be a fragmentation issue as well.  This can occur when NFS is using UDP.  You can try using TCP instead on the server.  Here's a little info:

[http://lists.trustix.org/pipermail/tsl-discuss/2004-July/011448.html](http://lists.trustix.org/pipermail/tsl-discuss/2004-July/011448.html)

MrC

---

### Post by virgiltibbs on 2007-06-18
I flushed the whole of Iptables on the server
then on the client:
> timmy@timmy-desktop:~$ sudo mount 192.168.1.110:/var/www /var/www
Password:
mount: RPC: Timed out
timmy@timmy-desktop:~$              
would you suggest, as per the list suggested, I try something like:
> mount -t nfs -o rw,intr,hard,wsize=1500,rsize=1500 devserv:/var/www /var/www?

---

### Post by virgiltibbs on 2007-06-18
well i tried that as well..:
> timmy@timmy-desktop:~$ sudo mount -t nfs -o rw,intr,hard,wsize=1500,rsize=1500 devserv:/var/www /var/www
mount: RPC: Timed out
timmy@timmy-desktop:~$     

---

### Post by Mr. C. on 2007-06-18
Sure, give it a try.  You call alternatively try using tcp, as in:

sudo mount -t nfs -o rw,intr,hard,tcp devserv:/var/www /var/www

MrC

---

### Post by virgiltibbs on 2007-06-18
oh, of course...> timmy@timmy-desktop:~$ sudo mount -t nfs -o rw,intr,hard,tcp devserv:/var/www /var/www
mount: RPC: Timed out
timmy@timmy-desktop:~$   
:(
Thank you, for trying t help me, - I really appreciate it... do you have any other ideas? 
Again i really appreciate you having a go at this. :)

---

### Post by Mr. C. on 2007-06-18
What's in your /etc/hosts.deny and /etc/hosts.allow ?

MrC

---

### Post by virgiltibbs on 2007-06-18
i think you may have come across a similar piece of documantation to the piece i found;
I found something which told me to create hosts.allow and put *rpc.mountd: 192.168.1.** in it
-thats what the case is for me
hosts.deny does not exist.

---

### Post by Mr. C. on 2007-06-18
Something is blocking or causing failure in your client's attempt to connect to the mountd on the server.  The portmapper sets up a random port for mountd to listen on; the client then attempts to connect on this port.  This will fail if:

1) mountd is not running on the server
2) some tcpwrapper entry blocks access
3) a firewall blocks access

Try configuring your mountd to run on a specific port (eg -p option, see man rpc.mountd) and find the startup daemon in your /etc/init.d/ scripts.

Its a fairly straightforward process, so there's something that's being overlooked.

MrC

---

### Post by virgiltibbs on 2007-06-18
Ok i'll take a look at that, but considering that where i am its 12:30 I'm going to bed; i'll tackle it in the morning.
 thank you very much for your patience and help
I might have a go at attempting to go through the wholee procedure again just in case i have overlooked something several times.

Just thinking, it might be something else... - i tried to set up a very similar system using the timmy-desktop and downstairs-desktop (another different feisty kubuntu box) and followed the same instructions and got the same error. 
(Just that wasn't really important [media share] so i didn't bother starting a thread)

anyway 

thankyou

-Tim

---

### Post by HugoMelo on 2007-07-10
I solved my problem changing the /etc/exports field async to sync.
Run 
$ sudo exportfs -a
 after that!
Good luck!

---

### Post by virgiltibbs on 2007-07-10
i'll give that a try, Thanks!

---

### Post by dkirk on 2007-07-10
Hey,

> **virgiltibbs said:**
> 
/var/www 192.168.1.1/24(rw,no_root_squash,async)

-ie share /var/www to local network with read write


Are you sure this is sharing to the whole network?  192.168.1.1 is a host address not a network address.  I don't know definitively if adding the /24 at the end will treat it as a network address, but I wouldn't count on it.

I would change it to the network address 192.168.1.0/24 and see if that makes any difference.

-- 
Later

David Kirk

---

### Post by virgiltibbs on 2007-07-12
thanks to dkirk and hugomelo for trying to help out, but i have tried both your suggestions on their own and together and it seems to have had no difference.
The strange thing is that ssh works fine... (I am using it with sshfs to do what nfs should be doing...)
has anyone any other ideas?
has anyone the same problem...?
any clue as to whether its client, server [router?] problem?
cheers for any help!!
-Tim

---

### Post by virgiltibbs on 2007-07-17
I think i might have loosly worked out what the problem is:

when i ping my router( who should respond to it)
this is the result:

> timmy@timmy-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3002ms (likwise it will not let me log into the http router config on port 80 - its just "no found"

-I think the problem is with IP tables or at least somewhere in the networking stack of one of the machines (probably in this case the client but it may be both

I have installed firestarter to manage ip tables and it shouldn't be a problem - the rules should allow everything from one ip

however it seems my computer is acting a bit strangly 
im not sure how exactly bu maybe you have seen this before??

it will ONLY connect to either the internet OR the local network.
when i fiddle with firestart & remove stuff & reboot it seems to switch....

any ideas??
(sorry its so vague - i would be happy to clear up anything you find unclear)

---

### Post by Mr. C. on 2007-07-17
Can I make a suggestion ?  

Get your NFS working without the firewall.  Once you have it working, re-enable the firewall.

You are trying to do too many things at once, that you don't understand.  It is simply not possible to diagnose what is wrong with so many random steps being taken.

MrC

---

### Post by virgiltibbs on 2007-07-17
sorry to sound... i dunno... sorry anyway:

i have been trying without personal firewalls (and still have failed)
I installed firestarter for the purpose of being able to control IP tables in a way i could visualise... (i know when i become familiar with the IP tables config it would be easy but for the moment, unless being walked through i prefere firestarter....

If i delete all rules in firestarter and then tell it to turn the firewall off IP tables should be set to allow on all ports...
NFS still doesnt work giving the tradiditonal error

if that doesnt clear up what i was saying i will elaborate further...

again sorry for being a bit blunt & thanks for getting back to me.

---

### Post by Mr. C. on 2007-07-17
Ok, but at this point, I'm not sure where we are now.

Your ping failure, and RPC timeouts indicate a firewall is blocking your traffic.  Until you get that fixed, we can't move forward.

Once that's done, spend a little time reviewing the Week 4 NFS lab and notes here:

[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by virgiltibbs on 2007-07-17
ah ok
well ill give the firewall a kick up the backside a few times and play with that...
and then ill give everythin a go again - sshfs really isnt ideal atm....
thanks
-Tim

btw
[http://www.linuxquestions.org/questions/showthread.php?t=22015](http://www.linuxquestions.org/questions/showthread.php?t=22015)

---

### Post by virgiltibbs on 2007-07-17
ok i think i may well have tracked the problem down(?) or at least the symptoms...
or at least the tracked **A** problem down
the machine *timmy-desktop* will not ping anything on local network, and if anything from the local network - ie *devserv* pings it, there is no response(unreachable).
i have tried to remove all rules with firesatarter to no avail, ive tired with guarddog & by flushing ipchins (i think) - i followed [http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html](http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html)
any helpful ideas on why this isnt having any impact to whether i can connect to machines on my local network?

---

### Post by virgiltibbs on 2007-07-17
exampolle of how it won't connect to anything...
all the machines which are being pinged should respond and on other machines Do respong
```
timmy@timmy-desktop:~$ ping 192.168.1.110
PING 192.168.1.110 (192.168.1.110) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.110 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5009ms
, pipe 3
timmy@timmy-desktop:~$ chmod +x /root/fw.stop
chmod: cannot access `/root/fw.stop': No such file or directory
timmy@timmy-desktop:~$ chmod +x flush
timmy@timmy-desktop:~$ sudo ./flush
Stopping firewall and allowing everyone...
timmy@timmy-desktop:~$ ping 192.168.1.110
PING 192.168.1.110 (192.168.1.110) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
From 192.168.1.101 icmp_seq=4 Destination Host Unreachable
From 192.168.1.101 icmp_seq=6 Destination Host Unreachable
From 192.168.1.101 icmp_seq=7 Destination Host Unreachable
From 192.168.1.101 icmp_seq=8 Destination Host Unreachable

--- 192.168.1.110 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8000ms
, pipe 3
timmy@timmy-desktop:~$ ping devserv
PING devserv (192.168.1.110) 56(84) bytes of data.
From timmy-desktop.local (192.168.1.101) icmp_seq=2 Destination Host Unreachable
From timmy-desktop.local (192.168.1.101) icmp_seq=3 Destination Host Unreachable
From timmy-desktop.local (192.168.1.101) icmp_seq=4 Destination Host Unreachable

--- devserv ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3000ms
, pipe 3
timmy@timmy-desktop:~$ ping 192.168.1.110
PING 192.168.1.110 (192.168.1.110) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
From 192.168.1.101 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.110 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4999ms
, pipe 3
timmy@timmy-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5009ms
, pipe 3
timmy@timmy-desktop:~$     
```

i have noticed ONE thing which may be causing problems - the IP of timmydesktop is not what i thought it was - it should be 192.168.1.100 and its .101 atm. i'm going to change this and see if this makes any difference though i severly doubt it will..........

---

### Post by Mr. C. on 2007-07-17
At this point, you're looking at a basic network problem.

The NFS chase has been a red herring.

Work through your inability to ping the remote machine, and then start afresh.

I'm continually amazed at how many people install various chunks of software, and have no idea how to operate them.  What's the point of a firewall, if one doesn't know how to control it ! 

MRC

---

### Post by Christof999 on 2007-07-17
Hello, 

I am having the same problem. Everytime I try to mount an NFS share I get the timed out message. I really need some help with this! I don;t know if I am running a firewall, unless it comes with Ubuntu...

Anyways this is seriously cutting into my productivity, and Im just about ready to ditch Ubuntu because I just cant share files no matter what!

Please let me know how I can fix this problem. Im completely at a loss. 

Thanks
C.

---

### Post by Mr. C. on 2007-07-17
You're going to have to go through the same diagnosis procedure.  Follow the requests starting at the beginning of the thread.

Also, what is the output of:

```
sudo iptables --list
```

Can each machine ping each other ?

MrC

---

### Post by Christof999 on 2007-07-17
> **Mr. C. said:**
> You're going to have to go through the same diagnosis procedure.  Follow the requests starting at the beginning of the thread.

Also, what is the output of:

```
sudo iptables --list
```

Can each machine ping each other ?

MrC

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Thats the result of that...

Damn.. This is so frustrating. Ive been trying different distrobutions for six months now just trying to get something friggin simple like sharing folders donw, but It still won't work. This is one thing that really ticks me off about Linux. You always have to do so much damn hacking for something that should be as simple as 

"right click, share"

Six months. Im still no closer.

---

### Post by Mr. C. on 2007-07-17
Christof999,

You're hijacking someone elses thread.  You really should start your own, because your situation may be different, and the original OP's problem is still ongoing.

I asked you a simple question at the end of my previous response - you ignored that request.  How can you place blame on Linux in general when you can't follow a paragraph ? If this is the way you followed the various HowTo's, I can see where the problem are occurring.  ;-)

You also need to run some basic diagnostics.  You *claim* you setup everything correctly, but a) it doesn't work so there is some failure in your setup, and b) nobody here has any clue what you did to your system.  So we have to dig and discover.  You haven't yet demonstrated that even basic networking between the two machines is functional, just as the OP had not.

MrC

---

### Post by Christof999 on 2007-07-17
> **Mr. C. said:**
> Christof999,

You're hijacking someone elses thread.  You really should start your own, because your situation may be different, and the original OP's problem is still ongoing.

I asked you a simple question at the end of my previous response - you ignored that request.  How can you place blame on Linux in general when you can't follow a paragraph ? If this is the way you followed the various HowTo's, I can see where the problem are occurring.  ;-)

You also need to run some basic diagnostics.  You *claim* you setup everything correctly, but a) it doesn't work so there is some failure in your setup, and b) nobody here has any clue what you did to your system.  So we have to dig and discover.  You haven't yet demonstrated that even basic networking between the two machines is functional, just as the OP had not.

MrC

I can certainly start my own thread.

As for linux. A user friendly system should be able to share folders in a local network easily, without the user having to edit configuration files, check ports, open ports, bring down firewalls, config firewalls, add new packages etc. 

What Linux Gurus need to understand is that, if they want and promote Linux as being user friendly, then when new users encounter massively complex procedures to share their photos between computers, you can't be suprised or upset that they are lost and confused. Point me to a step by step guide, or lay out the commands exactly as I need to type them and Ill be happy to follow instructions. But as of yet, I find the thread confusing. I find Linux annoying for making have to do all this when windows had me sharing files after two clicks!

Basic tasks like file sharing should be simple.

C

---

### Post by Mr. C. on 2007-07-17
> **Christof999 said:**
> As for linux. A user friendly system should be able to share folders in a local network easily, without the user having to edit configuration files, check ports, open ports, bring down firewalls, config firewalls, add new packages etc. 

What Linux Gurus need to understand is that, if they want and promote Linux as being user friendly, then when new users encounter massively complex procedures to share their photos between computers, you can't be suprised or upset that they are lost and confused. Point me to a step by step guide, or lay out the commands exactly as I need to type them and Ill be happy to follow instructions. But as of yet, I find the thread confusing. I find Linux annoying for making have to do all this when windows had me sharing files after two clicks!

Basic tasks like file sharing should be simple.


They are for many people; but you need to drop the idea that everyone's environment is the same, and that every other OS' sharing is always trivial to enable.  That's just plain incorrect.

It is not other people's jobs to make your life easier!  We help because we can and want to, but you are not *entitled* to hand-holding or step-by-step guides.

Now, let's move on and get your problem fixed.  Please start a new thread, with the output requested.

MrC

---

### Post by Christof999 on 2007-07-17
For anyone still having this problem...
I found a solution. I uninstalled all my samba packages, so samba, samba-common etc and then the NFS mounting simply worked. 

Give it a try, it might work for you as well. 

C.

---

### Post by virgiltibbs on 2007-07-18
@mr c

sorry for having a trivial problem rather than a complecated one, its a shame the original error message didnt point is in the right direction really...

anyway - thank you for the help you have given me...
i have now got to a point where i can ping said machines, i will give an nfs mount a o in a sec
I will give what you have said a good thought in the future...

-I do think that is one of the nastiest errors to get simply because it points you in a random direction when the problem is lying at your feet.
Still in my first post i mentioned it was likly to be like that
i agree about no knowing how to control software etc just my firewall didnt seem to want to be controlled (else i didnt know enough about it to control it)

again thank you

-tim

---

### Post by virgiltibbs on 2007-07-18
ok I thought i had found the root of the problem as being the firewall but it isnt - i dont think
```
timmy@timmy-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.699 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.695 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.693 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.770 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.718 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.701 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.704 ms

--- 192.168.1.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6007ms
rtt min/avg/max/mdev = 0.693/0.711/0.770/0.035 ms
timmy@timmy-desktop:~$ ssh timmy@devserv
The authenticity of host 'devserv (192.168.1.110)' can't be established.
RSA key fingerprint is 08:5b:fb:3d:65:d2:f3:9a:e4:9a:98:71:20:46:5b:53.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'devserv' (RSA) to the list of known hosts.
timmy@devserv's password:
Linux devserv 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Jul 17 21:40:06 2007
timmy@devserv:~$ 


timmy@timmy-desktop:~$ sudo mount 192.168.1.110:/var/www /var/www
Password:
mount: RPC: Timed out
timmy@timmy-desktop:~$ 
```
as you can see i have no problem with ssh
i can ping the box

if you weant to see the ip tables for each machine:

timmy-desktop
```
timmy@timmy-desktop:~$ sudo iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

devserv
```
timmy@devserv:~$ sudo iptables --list
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  ptn-cdns01.plus.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  ptn-cdns01.plus.net  anywhere
ACCEPT     tcp  --  ptn-cdns02.plus.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  ptn-cdns02.plus.net  anywhere
ACCEPT     0    --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       0    --  anywhere             255.255.255.255
DROP       0    --  anywhere             192.168.1.255
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.110        ptn-cdns01.plus.net tcp dpt:domain
ACCEPT     udp  --  192.168.1.110        ptn-cdns01.plus.net udp dpt:domain
ACCEPT     tcp  --  192.168.1.110        ptn-cdns02.plus.net tcp dpt:domain
ACCEPT     udp  --  192.168.1.110        ptn-cdns02.plus.net udp dpt:domain
ACCEPT     0    --  anywhere             anywhere
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
OUTBOUND   0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  192.168.1.100        anywhere
ACCEPT     0    --  192.168.1.90         anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh
ACCEPT     tcp  --  192.168.1.100        anywhere            tcp dpt:sunrpc
ACCEPT     udp  --  192.168.1.100        anywhere            udp dpt:sunrpc
ACCEPT     tcp  --  192.168.1.100        anywhere            tcp dpt:nfs
ACCEPT     udp  --  192.168.1.100        anywhere            udp dpt:nfs
ACCEPT     tcp  --  192.168.1.90         anywhere            tcp dpt:sunrpc
ACCEPT     udp  --  192.168.1.90         anywhere            udp dpt:sunrpc
ACCEPT     tcp  --  192.168.1.90         anywhere            tcp dpt:nfs
ACCEPT     udp  --  192.168.1.90         anywhere            udp dpt:nfs
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www
LSI        0    --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       0    --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  anywhere             anywhere
timmy@devserv:~$            
```


i can see in advance you are going to give me some flak over devserv's iptables - i'll go and flush them (EVEN though it is set to accept all inbound from 192.168.1.100)

unless you have a few clever ideas(?) 
[do you know where we are up to atm?]
i might try see fi can acess the said share from another kubuntu box i have (192.168.1.90)
- i then might be able to acertain whether the client is causing the problems...
if i can't connect to devser i could try connecvting to timmy-desktop from 192.168.1.90

on the other hand - you might think this was blurring the thread a bit.... ?

thanks for all the help mr c
but i dont want to do a load of stuff that you might think was not helpful....
what, in your humble opinion, do you think i should do?

---

