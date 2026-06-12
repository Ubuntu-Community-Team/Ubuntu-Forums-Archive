---
title: "Concise OpenVPN installation. . .?"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by michwill on 2008-05-29
Hi All,

My apologies for posting such a question when there is a plethora of information available, but I need something much more concise if possible.  A client of mine just had a meltdown of their Win 2K3 VPN server -- they're starting from scratch and they're *very* open to Linux and especially OpenVPN.

That said, I need a *Linux Based* OpenVPN instructional/tutorial that is both concise and accurate.  Does such exist?

Thus far, I've encountered and gathered a great quantity of excellent information about OpenVPN, but nothing less than about 30 pages.

My requirements are simple.  I need the functional equivalent of their old PPTP server.  Now, I don't necessarily want to set up a PPTP server, but I *do* want as many of the capabilities that came along with it as possible.  Most importantly, I need outside computers to behave as though they are *on* the network with little to no interference, so I'm guessing I'll need a bridged setup.  Also, I'd like Username/Password authentication as opposed to shared keys.  My client isn't interested in having to provide keys for each login.

Anyway, all that said, I'd appreciate some amazingly concise direction on setting up a bridged OpenVPN server on Linux.

As a sidenote, their server hardware is as follows:

HP ML350 G5 Server (Quad-core Xeon)
9 GB DDR2
250GB Raid1


Best Regards!

---

### Post by SpaceTeddy on 2008-05-29
mhm... have you had a look at this [[COLOR="Blue"]howto[/COLOR]]("http://openvpn.net/index.php/documentation/howto.html#pki") yet ? that pretty much explains on how to do the job. But then i've been doing this so often i tend to forget how overwhelming OpenVPN can be to people... 

But in general - i don't think there is a tutorial on how to do this in less than 30 pages, because openvpn is way to complex and has way too many options and tweaks to possibly fit it in anything under 100 pages. Not if you want to really understand what is going on. 

i'll just throw some bones now, and i can provide sample configurations and commands on how to manage openvpn server (I acctually earn money with these things)

1.) routing of subnets.
Openvpn can be bridged or tunneld. I personally perfer the tunnels way, as it puts the clients into their own ip subnet and does not mess with the real network the server is attached to. Of course, that is a little harder to setup, as you do need ip_forwarding as well as some (basic) route settings and possibly nat to make it work. But it does work, and it does work without briding !

As an example think of the openvpn clients to have their own swicth (the openvpn process) with their own ip's and subnets. So the OpenVPN server can be thought of as to be only a router... really. 

Also, it is possible to redreict all traffic via the VPN, or only specific networks/ip-ranges that are to be used. For example, i have setup multiple VPN's that only set the routes for the internal networks on the client, and leave the rest to the client. You probably want to read about the --redirect-gateway vs. push "route ip/mask" commands to understand what is happening here.

2.) Authentification
OpenVPN can authenticate against any and everything. Build in modules are for a normal PKI strucutre with or without password for the client certificates. But it also works against PAM (Plugable Authentification Modules ?) as well as LDAP and a lot of others. 
And if all fails, OpenVPN has a hook for auth scripts that you can write yourself ! So if you really want to, you can even authenticate against a textfile... 

3.) ports
This is a real beauty. OpenVPN uses ONE port - and one only. It work on UDP and TCP and has no other requirement. Just one Port. No GRE protocoll, no special port 500 ********. Just one Port. (i think you got the point now :) )

4.) your server
is more than enough. I've ran OpenVPN server on P-II pro with 128 mbyte ram with more than 60 clients. It's not the fastest, but the users didn't notice that. Altought, on a small machine like that, i never did redirect ALL traffic over it. 

So, i am sorry for not being able to point you to a more... specific howto, but wrote an advertisment post instead - but i just love openvpn. It's simple, it's powerfull and it is slim. 

If you have any specific question about how to setup, or if you get stuck anywhere, just ask.

hope it helps :)

---

### Post by michwill on 2008-05-30
> **SpaceTeddy said:**
> mhm... have you had a look at this [[COLOR="Blue"]howto[/COLOR]]("http://openvpn.net/index.php/documentation/howto.html#pki") yet ? that pretty much explains on how to do the job. But then i've been doing this so often i tend to forget how overwhelming OpenVPN can be to people... 


Yeah, that was the first item I checked out when looking at OpenVPN.  But it is amazingly detailed and I'm on a *very* short time table.  I am currently beginning to read it *again* while waiting for a shorter response, however.

I just need a 10-line 10-step tutorial. :)

---

### Post by SpaceTeddy on 2008-05-30
here we go... let's see if i can compact it into 10 steps :)
NOTE: all commands run as root. i will skip the sudo everywhere. To fully become root, use ```
sudo su
```

[SIZE="5"]1.) preparing the PKI[/SIZE]
copy the easy-rsa from /usr/share/doc/openvpn/examples/easy-rsa/the examples into the /etc/openvpn/easy-rsa folder.
```
cp -R /usr/share/doc/openvpn/examples/easy-rsa /ect/openvpn
```
then go into that folder, and edit the vars to match your enviroment. i'd also suggest you remove all comments after you read them.
The settings in that file are the defaults.
once that is done, load the file with this command
```
source vars
```

NOTE: every time you want to do something on the PKI, you *MUST* load the vars again. 

[SIZE="5"]2.) creating the keys[/SIZE]
first, let the scripts inititialize the enviroment (all commands run in the directory /etc/openvpn/easy-rsa) :
```
./clean-all
```
first, create a diffie-hellman key (not sure if it is needed - create it anyway)
```
./build-dh
```
then create a CA
```
./build-ca
```
now, build a server key
```
./build-server %name
```
with %name as it's common name. All Clients will always be referenced with their common name, NOT with any filename or dns name. So make sure you choose the common names of anything wisely. Also, they are in no relation to dns names (like they are in SSL certs) so you can choose them freely

[SIZE="5"]3.) configuring the server[/SIZE]
here is a sample config of a server that (should) work. create a file in /etc/openvpn calles vpn1.conf (the vpn1 can be changed to anything, really, stick with the .conf tho - that IS needed):
```
daemon
port 1194
proto udp
dev tun0

[I]ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/dh2048.pem[/I] 

server 10.20.30.0 255.255.255.0
ifconfig-pool-persist openvpn.dhcp

keepalive 10 120
comp-lzo

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log
verb 4
mute 20

;push "route 192.168.0.0 255.255.255.0"
;push "route 192.168.173.0 255.255.255.0"
;push "redirect-gateway def1"

;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-to-client
; max-clients 10

# plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
# client-cert-not-required
# username-as-common-name

```
i will not go into detail on this (that would make me use 30 pages aswell)... so if you are unsure about any option, just read up what it does. However you *MUST* change the italic options to correspond to the real filenames (you should have created them in the step beforehand).

lastly, make sure the log directory exists and it is owned by nobody. Othewise, openvpn will fail to write to it's log and will fail to start.
So, create the directory and chown it with these comands:
```
mkdir /var/log/openvpn
chown nobody.nogroup /var/log/openvpn
```

[SIZE="5"]4.) starting the server[/SIZE]
All set, the server should come up fine now...
start it with this command:
```
/etc/init.d/openvpn start vpn1
```
where the vpn1 corresponds to the filename. If anything fails, check the logs in /var/log/openvpn to what failed. If i've made no typos, this should work. 

[SIZE="5"]5.) allowing passthrough traffic on the VPN server[/SIZE]
This is a very tricky point. Since i could write about a book here too, i will just assume some default settings and hope they (kind of) fit your environment. 

enable ip_forwarding:
```
sysctl -w net.ipv4.ip_forward=1
```
and enable it so it loads on boot via the /etc/sysctl.conf

Also, masquerade the traffic that leaves the machine, so the pakets can find their way back (this is the *easiest* solution, it is by far not the best !):
```
iptables -A POSTROUTING --tabe nat -o ! tun0 -j MASQUERADE
```

and this line to the /etc/rc.local to make the settings load on boot-up
```
/sbin/iptables -A POSTROUTING --tabe nat -o ! tun0 -j MASQUERADE
```

This should give your vpn clients full connectivity to all networks that are pushed to be accessed over the VPN.

[SIZE="5"]6.) client certificates[/SIZE]
every client needs it's own certificate. you can generate them the same way you have done all the other generation if certificates. go into the the /etc/openvpn/easy-rsa folder, make sure you run the source vars (if this is a new console) and then type
```
./build-client %client
```
where %client is the filename of the client, NOT the common name!

[SIZE="5"]7.) Windows XP Clients[/SIZE]
Download the openvpn-gui from [[COLOR="Blue"]http://openvpn.se/[/COLOR]]("http://openvpn.se/") and install it. 
Then open the config folder (usually C:\programm files\OpenVPN\config) and create a file with the ovpn extension. this is also a normal textfile. fill it up with this sample configuration:
```
float
client
dev tun
proto udp

*remote %vpn-server*
;redirect-gateway

resolv-retry infinite
nobind
persist-key
persist-tun
[I]ca ..\\cert\\ca.crt
cert ..\\cert\\client.crt
key ..\\cert\\client.key
[/I]ns-cert-type server
comp-lzo
verb 3
;mute 20

```
again, make sure that the italic bits are changed to your setup and filenames. the relative path ..\\ will bring your into the c:\program files\openvpn folder - i usually create a new folder there called cert where i store the keys and certificates.
Also, as you can see, the client needs three files from the server (all found in /etc/openvpn/easy-rsa/keys) - the ca.crt, it's own certificate and its own key. Make sure it's got it. 
NOTE: Vista clients need a small change in the config as well as a way to start the openvpn-gui as administrator and not unprivilegdes user. I have yet to find a way to do this without problems... 

Now, after the config is created, the files are copied and the openvpn-gui is loaded, tell it to connect. If your firewall is not blocking anything, this should work and you should be able to connect to the server. Once that is done, the client should be able to ping the 10.20.30.1 (if you kept my subnet) and the server should be able to ping the 10.20.30.6

that's pretty much the simplest, shortest way of doing this i can think of. i hope it works, and if it does i will turn this into a howto and paste it in a new thread on this forum. 

If anything fails or any questions arise, just ask :)

PS: only took me seven steps :)

---

### Post by michwill on 2008-05-30
> **SpaceTeddy said:**
> 
PS: only took me seven steps :)

First and foremost:  WOW!   I appreciate all that.  I haven't had time to try it yet, but hopefully I will have by 5 pm EST today. :)

That said, after glancing over this, it seems to be missing reference to two things:

[INDENT]1) Password authentication (key distribution is kinda out of the question as it's not sufficiently "agile")

2) Network Bridging, but I suppose I can check out links like [this]("http://openvpn.net/index.php/documentation/miscellaneous/ethernet-bridging.html") to get me going.[/INDENT]


. . .again, WOW! and thank you.

---

### Post by SpaceTeddy on 2008-05-30
> **michwill said:**
> 
1) Password authentication (key distribution is kinda out of the question as it's not sufficiently "agile")

ok - that was a possiblity :) check the server config. there are some commeted lines down the bottom. the ones i am refering to are these
```
# plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
# client-cert-not-required
# username-as-common-name
```
this will overwrite the PKI structure and use pam to authenticate the users on the system. i.e. anybody being able to log in as a "normal" user on the machine will be able to use that user/password combination to also log into the server. 
On the client side, the following lines are cancelled:
```
cert ..\\cert\\client.crt
key ..\\cert\\client.key

```
that should do the trick 

if you do not want to authenticate against PAM, then i can also provide a sample script to authenticate against plain text files. btw: this example is taken from a server that has ldap integreated into pam - so the real auth is against LDAP via PAM.
> **michwill said:**
> 

2) Network Bridging, but I suppose I can check out links like [this]("http://openvpn.net/index.php/documentation/miscellaneous/ethernet-bridging.html") to get me going.
i don't see any real need to bridge the network... really. Briding brings the heavy disadvantage of layer 2 broadcasts. This means, that your network can possibly be swamped by one client as even arp requests (which are generated automaticially to resolve ip-addresses) will be sent out via the link.
i'd strongly advise against briding if you do not need the layer 2 support (i.e. if you need broadcasts for "lan" games or protocolls like IPX to run, then you will need briding) in favor of saving bandwidth and increasing the performance. 
Stick with IP based routing for as long as you can - at least that is my motto. Also, i have written a howto on ethernet network bridging. I think the bridge configuration in my case is more sufficient and closer to the operating system than the scripts mentioned in the tutorial... but that is only my opinion about my work. The thread can be found [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127") - you are probably interested in part 2 if you want to do bridging.

---

### Post by michwill on 2008-05-30
> **SpaceTeddy said:**
> 
i don't see any real need to bridge the network... 
...
i'd strongly advise against briding if you do not need the layer 2 support (i.e. if you need broadcasts for "lan" games or protocolls like IPX to run, then you will need briding) in favor of saving bandwidth and increasing the performance. 
Stick with IP based routing for as long as you can - at least that is my motto. Also, i have written a howto on ethernet network bridging. I think the bridge configuration in my case is more sufficient and closer to the operating system than the scripts mentioned in the tutorial... but that is only my opinion about my work. The thread can be found [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127") - you are probably interested in part 2 if you want to do bridging.



Well, the thing is, we need all logged-in clients to be *on the network*.  Initially they will only need to access "internal" web pages.  However, eventually (meaning before the end of summer), they will need to access network resources like printers, other computers via VNC, and file (with the likelihood of music) sharing across the "office".  For all intents and purposes they need to be verifiably *on* the network.

What capabilities does routing alone provide?

---

### Post by SpaceTeddy on 2008-05-30
routing can do anything that requires an IP connection. Accessing shares, printing via IP or vnc is not a problem (as long as it runs on ip and not any other protocoll).

With "on the network" you just mean access to the internal networks - that is NOT a problem... at all. 

hope it helps :)

---

### Post by michwill on 2008-05-30
Excellent!  I'll actually end up setting this up over the weekend.  One more question: given that my client will likely want to be able to manage this setup without having to call me every week, he's going to want some type of interface.  Are there any quality graphical interfaces (web-based or otherwise) for managing OpenVPN?

Thanks again btw!

---

### Post by SpaceTeddy on 2008-05-31
i only know of a management for the PKI based VPN - that one has a webmin module which is not really finished yet, but works good enough for the guys i installed the VPNs for. The module can be found [[COLOR="Blue"]here[/COLOR]]("http://freshmeat.net/projects/webmin-openvpnadmin/").

how that works for non PKI structures i don't know, since then you need some kind of management tool for either the useraccounts on the machine itself, or something that will edit your OpenVPN useraccount. The only other management i have worked with as a domino 6.5.3 server which has an LDAP backend that is used by PAM to authenticate local users. OpenVPN then authenticated against PAM, this against LDAP and therefore against domino 6.5.3.

---

### Post by michwill on 2008-06-02
Hrm.  Ok, it would seem that Windows makes no concession for *only* using username and password.  It would appear that it desperately wants you to have a key.

There is apparently the ability to change the password on a key, but it doesn't explicitly mention how to validate solely via "user/pass".

Surely I'm missing something.  I will actually *try* it within the next couple of hours to see what the truth is.

---

### Post by SpaceTeddy on 2008-06-03
no - i have an OpenVPN config running that uses username and Password only.  Given, you sill need a ca (to identify the server), but that does not change from user to user so it can just be included into a selfbuild installer (real easy to do with nsis). All tutorials for that are found on openvpn.net and openvpn-gui.se

If you need any help, i can setup a sample server for you so you can see how it works (if that is what you desire).

cheers

PS: would have answered last night, but the forums were down.

---

### Post by michwill on 2008-06-03
I appreciate the offer.  Actually, I've got the VPN up and running (still working through the CA stuff though).

One problem I'm having now is that the VPN server loses its network connection (internet, sharing, and all) after about 10 minutes or so.  It's as if the VPN "stack" (for lack of a more appropirate term) is breaking the network.  Any idea what could be causing this?  I used your script exactly, but I changed to a "192.168" subnet.

---

### Post by michwill on 2008-06-04
Ok, this is very strange.  Contrary to my previous statement, I'm losing connection immediately.  My logs are as follows:

```

Wed Jun  4 15:55:35 2008 us=808954 Current Parameter Settings:
Wed Jun  4 15:55:35 2008 us=809134   config = '/etc/openvpn/vpn1.conf'
Wed Jun  4 15:55:35 2008 us=809164   mode = 1
Wed Jun  4 15:55:35 2008 us=809190   persist_config = DISABLED
Wed Jun  4 15:55:35 2008 us=809214   persist_mode = 1
Wed Jun  4 15:55:35 2008 us=809238   show_ciphers = DISABLED
Wed Jun  4 15:55:35 2008 us=809262   show_digests = DISABLED
Wed Jun  4 15:55:35 2008 us=809286   show_engines = DISABLED
Wed Jun  4 15:55:35 2008 us=809310   genkey = DISABLED
Wed Jun  4 15:55:35 2008 us=809334   key_pass_file = '[UNDEF]'
Wed Jun  4 15:55:35 2008 us=809359 NOTE: --mute triggered...
Wed Jun  4 15:55:35 2008 us=809401 198 variation(s) on previous 10 message(s) suppressed by --mute
Wed Jun  4 15:55:35 2008 us=809430 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May 14 2008
Wed Jun  4 15:55:35 2008 us=809585 PLUGIN_INIT: PRE
Wed Jun  4 15:55:35 2008 us=809612 ARGV[0] = '/usr/lib/openvpn/openvpn-auth-pam.so'
Wed Jun  4 15:55:35 2008 us=809634 ARGV[1] = 'login'
Wed Jun  4 15:55:35 2008 us=809656 ENVP[0] = 'config=/etc/openvpn/vpn1.conf'
Wed Jun  4 15:55:35 2008 us=809677 ENVP[1] = 'proto=udp'
Wed Jun  4 15:55:35 2008 us=809699 ENVP[2] = 'local_port=1194'
Wed Jun  4 15:55:35 2008 us=809720 ENVP[3] = 'verb=9'
Wed Jun  4 15:55:35 2008 us=809741 ENVP[4] = 'daemon=1'
Wed Jun  4 15:55:35 2008 us=809762 ENVP[5] = 'daemon_log_redirect=1'
AUTH-PAM: BACKGROUND: INIT service='login'
Wed Jun  4 15:55:35 2008 us=810404 PLUGIN_INIT: POST /usr/lib/openvpn/openvpn-auth-pam.so '[/usr/lib/openvpn/openvpn-auth-pam.so] [login]' intercepted=PLUGIN_AUTH_USER_PASS_VERIFY 
Wed Jun  4 15:55:35 2008 us=810597 /usr/sbin/openssl-vulnkey -q /etc/openvpn/easy-rsa/keys/mGreg.key
Wed Jun  4 15:55:35 2008 us=810624 SYSTEM[2] '/usr/sbin/openssl-vulnkey -q /etc/openvpn/easy-rsa/keys/mGreg.key'
Wed Jun  4 15:55:36 2008 us=97805 SYSTEM return=0
Wed Jun  4 15:55:36 2008 us=103233 Diffie-Hellman initialized with 1024 bit key
Wed Jun  4 15:55:36 2008 us=104327 WARNING: This configuration may accept clients which do not present a certificate
Wed Jun  4 15:55:36 2008 us=104413 MTU DYNAMIC mtu=0, flags=1, 0 -> 138
Wed Jun  4 15:55:36 2008 us=104444 TLS-Auth MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Jun  4 15:55:36 2008 us=104468 MTU DYNAMIC mtu=1450, flags=2, 1542 -> 1450
Wed Jun  4 15:55:36 2008 us=104698 GDG: route[1] 192.168.1.0/255.255.255.0/0.0.0.0 m=0
Wed Jun  4 15:55:36 2008 us=104741 GDG: route[2] 172.16.63.0/255.255.255.0/0.0.0.0 m=0
Wed Jun  4 15:55:36 2008 us=104777 GDG: route[3] 192.168.189.0/255.255.255.0/0.0.0.0 m=0
Wed Jun  4 15:55:36 2008 us=104813 GDG: route[4] 0.0.0.0/0.0.0.0/192.168.1.1 m=0
Wed Jun  4 15:55:36 2008 us=104848 GDG: route[5] 0.0.0.0/0.0.0.0/172.16.63.2 m=0
Wed Jun  4 15:55:36 2008 us=104898 GDG: best=192.168.1.1[4] lm=0
Wed Jun  4 15:55:36 2008 us=104937 ROUTE DEBUG: default_gateway=192.168.1.1
Wed Jun  4 15:55:36 2008 us=106317 TUN/TAP device tun0 opened
Wed Jun  4 15:55:36 2008 us=106369 TUN/TAP TX queue length set to 100
Wed Jun  4 15:55:36 2008 us=106432 ifconfig tun0 192.168.1.1 pointopoint 192.168.1.2 mtu 1500
Wed Jun  4 15:55:36 2008 us=106461 SYSTEM[2] 'ifconfig tun0 192.168.1.1 pointopoint 192.168.1.2 mtu 1500'
Wed Jun  4 15:55:36 2008 us=116552 SYSTEM return=0
Wed Jun  4 15:55:36 2008 us=116721 route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.2
Wed Jun  4 15:55:36 2008 us=116748 SYSTEM[0] 'route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.2'
Wed Jun  4 15:55:36 2008 us=122485 SYSTEM return=0
Wed Jun  4 15:55:36 2008 us=122607 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Jun  4 15:55:36 2008 us=124582 GID set to nogroup
Wed Jun  4 15:55:36 2008 us=124789 UID set to nobody
Wed Jun  4 15:55:36 2008 us=124864 Socket Buffers: R=[122880->131072] S=[122880->131072]
Wed Jun  4 15:55:36 2008 us=124911 UDPv4 link local (bound): [undef]:1194
Wed Jun  4 15:55:36 2008 us=124935 UDPv4 link remote: [undef]
Wed Jun  4 15:55:36 2008 us=124976 MULTI: multi_init called, r=256 v=256
Wed Jun  4 15:55:36 2008 us=125124 IFCONFIG POOL: base=192.168.1.4 size=62
Wed Jun  4 15:55:36 2008 us=125212 IFCONFIG POOL LIST
Wed Jun  4 15:55:36 2008 us=125260 PO_INIT maxevents=4 flags=0x00000002
Wed Jun  4 15:55:36 2008 us=125307 Initialization Sequence Completed
Wed Jun  4 15:55:36 2008 us=125329 SCHEDULE: schedule_find_least NULL
Wed Jun  4 15:55:36 2008 us=125361 PO_CTL rwflags=0x0001 ev=6 arg=0x0044deb8
Wed Jun  4 15:55:36 2008 us=125384 PO_CTL rwflags=0x0001 ev=7 arg=0x0044deb4
Wed Jun  4 15:55:36 2008 us=125420 I/O WAIT TR|Tw|SR|Sw [10/0]
Wed Jun  4 15:55:36 2008 us=128476 PO_WAIT[1,0] fd=7 rev=0x00000001 rwflags=0x0001 arg=0x0044deb4 
Wed Jun  4 15:55:36 2008 us=128534  event_wait returned 1
Wed Jun  4 15:55:36 2008 us=128560 I/O WAIT status=0x0004
Wed Jun  4 15:55:36 2008 us=128789  read from TUN/TAP returned 1500
Wed Jun  4 15:55:36 2008 us=128854 GET INST BY VIRT: 192.168.1.108 [failed]
Wed Jun  4 15:55:36 2008 us=128879 SCHEDULE: schedule_find_least NULL
Wed Jun  4 15:55:36 2008 us=128904 NOTE: --mute triggered...
Wed Jun  4 15:56:32 2008 us=740773 121 variation(s) on previous 10 message(s) suppressed by --mute
Wed Jun  4 15:56:32 2008 us=740911 event_wait : Interrupted system call (code=4)
Wed Jun  4 15:56:32 2008 us=740940 I/O WAIT status=0x0010
Wed Jun  4 15:56:32 2008 us=740988 MULTI: REAP range 0 -> 256
Wed Jun  4 15:56:32 2008 us=741359 TCP/UDP: Closing socket
Wed Jun  4 15:56:32 2008 us=741421 route del -net 192.168.1.0 netmask 255.255.255.0
Wed Jun  4 15:56:32 2008 us=741446 SYSTEM[0] 'route del -net 192.168.1.0 netmask 255.255.255.0'
SIOCDELRT: Operation not permitted
Wed Jun  4 15:56:32 2008 us=747836 SYSTEM return=1792
Wed Jun  4 15:56:32 2008 us=747919 ERROR: Linux route delete command failed: shell command exited with error status: 7
Wed Jun  4 15:56:32 2008 us=747975 Closing TUN/TAP interface
Wed Jun  4 15:56:32 2008 us=814746 PLUGIN_CLOSE: /usr/lib/openvpn/openvpn-auth-pam.so
AUTH-PAM: close
Wed Jun  4 15:56:32 2008 us=815031 PID packet_id_free
Wed Jun  4 15:56:32 2008 us=815099 SIGTERM[hard,] received, process exiting
AUTH-PAM: BACKGROUND: received command code: 1
AUTH-PAM: BACKGROUND: EXIT


```

Any idea as to why I'd lose my network connection?  Is there something that isn't getting properly routed or set?  At this point I'm willing to try nearly anything to get this server out the door.

---

### Post by SpaceTeddy on 2008-06-04
mhm - there are a few errors in there. 
first, what is your real network configured as ? is that 192.168.1.0/24 too ?
second, can you please past the config you are using for the server. I just wanna see it so i can make sure there are no flaws in there. Also, it looks like you have some permission problems with. 
this line suggests you are running as non-root user ?
```
Wed Jun  4 15:56:32 2008 us=741446 SYSTEM[0] 'route del -net 192.168.1.0 netmask 255.255.255.0' SIOCDELRT: Operation not permitted

```

i can't really say more than that without seeing the config of the server (vpn1.conf)

---

### Post by michwill on 2008-06-04
1) I'm not sure what you mean by your first question.
2)  The configuration file is as follows

```
mode server
;daemon
port 1194
proto udp
dev tun0

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/mGreg.crt
key /etc/openvpn/easy-rsa/keys/mGreg.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem 

server 192.168.1.0 255.255.255.0
ifconfig-pool-persist openvpn.dhcp

keepalive 10 120
comp-lzo

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log
verb 9
mute 10

push "route 192.168.1.0 255.255.255.0"
;push "route 192.168.173.0 255.255.255.0"
;push "redirect-gateway def1"

;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-to-client
; max-clients 10

;plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
plugin /usr/lib/openvpn/openvpn-auth-pam.so login

client-cert-not-required
username-as-common-name
auth-user-pass-verify rtest.rb via-file
```


Perhaps it's due to the "openvpn.dhcp" item?  I don't actually have a file with that name.  Does the server create it?  If I should provide it, what should it look like?

I'll reconfigure the server in any manner necessary.  Perhaps there are some assumptions being made on server configuration that I'm not meeting?  It is a 100% new install (reinstalled yesterday) of Ubuntu 8.04 with nothing special installed.

---

### Post by SpaceTeddy on 2008-06-04
> **michwill said:**
> 1) I'm not sure what you mean by your first question.
 gimme a "ifconfig" is what i meant :) sorry for being not clear on that :(

> **michwill said:**
> 
*mode server* <--- never seen that before - what does it do ?
;daemon
port 1194
proto udp
dev tun0

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/mGreg.crt
key /etc/openvpn/easy-rsa/keys/mGreg.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem 

server 192.168.1.0 255.255.255.0
ifconfig-pool-persist openvpn.dhcp

keepalive 10 120
comp-lzo

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log
verb 9
mute 10

*push "route 192.168.1.0 255.255.255.0"* <--- this is in the way of your server configuration. NEVER push the vpn-network itself. It is pushed automiaticially !
;push "route 192.168.173.0 255.255.255.0"
;push "redirect-gateway def1"

;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-to-client
; max-clients 10

;plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
plugin /usr/lib/openvpn/openvpn-auth-pam.so login

client-cert-not-required
username-as-common-name
*auth-user-pass-verify rtest.rb via-file* <--- what does the rtest.rb do ?

can't see anything else... really

---

### Post by michwill on 2008-06-04
IFCONFIG
```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5d:ad:69  
          inet addr:192.168.1.182  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe5d:ad69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36331 (35.4 KB)  TX bytes:18868 (18.4 KB)
          Interrupt:253 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140248 (136.9 KB)  TX bytes:140248 (136.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.189.1  Bcast:192.168.189.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.63.1  Bcast:172.16.63.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```



"rtest.rb"  (this is a temporary ruby file that authenticates user/password. . .I actually create a hash inside that contains the user/password combinations)
```

#!/usr/bin/ruby

#METHOD DECLARATION
def authorized(username,password)
	pass_hash={}
	pass_hash["michael"] = "c0r3"
	pass_hash["bob"] = "easy"
	pass_hash["kevin"] = "test"
	pass_hash["alex"] = "hacked"
	
	if pass_hash[username] == password
		return 1
	else
		return 0
	end
end

def parse_file(filename)
  ret_hash ={}
  
  f = File.new(filename)
  begin
      username = f.readline.to_s
      username.chomp!
      
      password = f.readline.to_s
      password.chomp!
      
      return username,password
  rescue EOFError
      puts "There was an I/O error before USERNAME and PASSWORD were collected."
      f.close
      exit 0
  end
end


def usage
  puts "Usage: \n\n"
  puts "ruby #{$0} path_to_file"
end




#BEGIN MAIN
filepath = ARGV[0]

if !filepath
  usage()
  exit 0
end
  

username,password = parse_file(filepath)


if (username && password)
	answer = authorized(username.to_s,password.to_s)
	
	#if answer == 1
	#	puts "Username:  " + username
	#	puts "Password:  " + password
	#	return 1
	#else
	#	puts "INVALID COMBINATION!!!"
	#end
  exit answer
else
	#puts "YOU GOTTA HAVE A USERNAME AND PASSWORD IDIOT!!!"
	exit 0
end


```


FYI, I've got two 64-bit Ubuntu servers running atm.  I just now freshly installed one and am running updates on it.  If you have any ideas for that fresh system, by all means let me know.  I'm not averse to wiping/reinstalling 'til I get this right.  Hopefully though it's simply a matter of tracking down configuration info.

Thanks again.

---

### Post by SpaceTeddy on 2008-06-04
and here we have the problem

```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5d:ad:69  
          inet addr:**192.168.1.182**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe5d:ad69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36331 (35.4 KB)  TX bytes:18868 (18.4 KB)
          Interrupt:253 Base address:0xc000 
```
your network card has the same subnet as the vpn. this does not work in a tunneled enviroment... only in a bridged one. 
choose a different subnet for the vpn and keep pushing the 192.168.1.0/24 network to the clients.

your config could look like this :
> mode server
;daemon
port 1194
proto udp
dev tun0

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/mGreg.crt
key /etc/openvpn/easy-rsa/keys/mGreg.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem 

**server 192.168.128.0 255.255.255.0**
ifconfig-pool-persist openvpn.dhcp

keepalive 10 120
comp-lzo

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log
verb 9
mute 10

push "route 192.168.1.0 255.255.255.0"
;push "route 192.168.173.0 255.255.255.0"
;push "redirect-gateway def1"

;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-to-client
; max-clients 10

;plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
plugin /usr/lib/openvpn/openvpn-auth-pam.so login

client-cert-not-required
username-as-common-name
auth-user-pass-verify rtest.rb via-file

---

### Post by michwill on 2008-06-04
> **SpaceTeddy said:**
> 
your network card has the same subnet as the vpn. this does not work in a tunneled enviroment... only in a bridged one. 


And that's what I was kinda getting at in the beginning.  I believe I need a bridged network because the machine on which the OpenVPN Server is configured will not be on or have access to any private subnets.  All machines will be created equal.  It will not be a DHCP server, it will not be a DNS server.  It is simply a machine sitting there to allow outside users to access the "192.168" internal network it is already a part of.

I can't overstate how much I appreciate your help.  That said, could you point me in the proper direction from this point on?  As I said, I'm willing to reinstall or whatever I must do to get this to work.




To restate:

-- The OpenVPN server will be behind a router.
-- The router will control all DHCP and DNS (not the OpenVPN hardware)
-- The router will forward port 1194 to the OpenVPN Server
-- The OpenVPN server will simply be giving access to all machines that "dial in". . .and providing IP addresses *only* to those machines.

---

### Post by SpaceTeddy on 2008-06-04
yes, i understood all that. i think we have just different points of view. Here is what i think you should do.

use the config i supplied in my last post.
add another push statement that looks like this:

> push "dhcp-option DNS 192.168.1.55"
where the ip is the ip of your internal dns server (i hope 192.168.1.55 is your dns server - if not, change it:) )

now, your clients have a route to your internal network 192.168.1.x via the vpn, they have your internal dns and know how to access it. lets configure the vpn server to allow passthrough traffic from the vpn into the internal network:

enable ip_forwarding
```
sudo sysctl -w net.ipv4.ip_forward=1
```
masquerade the vpn so client on the interal network can send pakets back into the vpn
```
sudo iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE
```

and voila - we are done. You know have a vpn-subnet which has the 192.168.128.0/24 address pool, all clients know the 192.168.1.0/24 and know to access it via the vpn. The vpn-server will let the pakets pass, and due to the masquerading the clients on the internal network are able to send answers back through the vpn.

i *know* this works - i am using a setup like that at the moment to look at the configs i wrote about a year ago for a customer :)

the trick here is that you use routing at the vpn-server and not birdging. That's why you have two different subnets, but essentially they are one...

does it make sense ?
[B]
[SIZE="4"][EDIT][/SIZE][/B]

your network logicially looks like this now:

Internet
|
Router
|
switch -> 192.168.1.0/24 network
|
vpn-server (192.168.1.182, 192.168.128.1)
|
vpn-clients (192.168.128.0/24)

so with this setup you create a network attached to your internal network...

---

### Post by michwill on 2008-06-04
That absolutely makes sense.  I'm going to take a break and fix a sandwich.  I will give this a try over the next couple of hours and let you know how it works out.

I absolutely appreciate it!

---

### Post by michwill on 2008-06-05
Alright, so we've got a bit of progress.  These are the steps I've taken:

```

1) created CA and server keys (but no client keys as this will be strictly user/pass)
2) copied the ca.crt to all relevant clients
3) successfully started VPN server
4) created a temporary "authentication" ruby script that *ALWAYS* exits with a 1 for test purposes
5) attempted logon from Windows client with valid network communication

```




My server config looks like so:

```

mode server
;daemon
port 1194
proto udp
dev tun

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/mGreg.crt
key /etc/openvpn/easy-rsa/keys/mGreg.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem

server 192.168.128.0 255.255.255.0
ifconfig-pool-persist openvpn.dhcp

keepalive 10 120

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append /var/log/openvpn/openvpn.log
verb 9
mute 10

;push "route 192.168.1.0 255.255.255.0"
;push "route 192.168.173.0 255.255.255.0"
;push "redirect-gateway def1"

;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-to-client
; max-clients 10

;plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
plugin /usr/lib/openvpn/openvpn-auth-pam.so login

client-cert-not-required
username-as-common-name
auth-user-pass-verify authscript.rb via-file

```



My Windows client (OpenVPN GUI v1.0.3) config looks like so:

```

dev tun
proto udp
remote 192.168.1.182 1194
ca ca.crt
auth-user-pass
client

```


I'm trying to connect from a windows client but am getting 100% failure with the following error:
```

Thu Jun 05 05:29:34 2008 OpenVPN 2.0.9 Win32-MinGW [SSL] [LZO] built on Oct  1 2006
Thu Jun 05 05:29:37 2008 ERROR: could not read Auth username from stdin
Thu Jun 05 05:29:37 2008 Exiting

```


Since my authentication script always exits with a 1, it should always successfully authenticate. . .correct?

---

### Post by SpaceTeddy on 2008-06-05
here is a script that i toyed around with until i got the ldap to work properly with openvpn... 

> #!/usr/bin/perl

sub trim($)
{
	my $string = shift;
	$string =~ s/^\s+//;
	$string =~ s/\s+$//;
	return $string;
}

my $prefix = "AUTH-SCRIPT";
my $config = "/etc/openvpn/script/auth.conf";

my $user = $ENV{username};
my $passwd = $ENV{password};


if ($passwd eq "") {
  printf("$prefix ERROR - empty password\n");
  exit 1;
};

open(DAT, "$config") || die("Could not open conf file!");
@data=<DAT>;
close(DAT);

foreach $context(@data){
  $context = trim($context);
  my $command = "/usr/bin/ldapsearch -x -D cn=$user,$context -w \'$passwd\' cn=$user";
  system("$command &> /dev/null"); 
  #printf("$command\n");
  my $exit_value  = $? >> 8;
  if ($exit_value == 0) { 
    printf("$prefix SUCCESS - connected $user from context $context\n");
    exit 0; 
  };
};
printf("$prefix FAILURE - $user was not found or password was wrong\n");
exit 1;


the first thing i notice is that on a success, this script exists 0 (non error), while on an error, it will exit 1. So i think that might be the problem. 

also, are you being asked for the username and password on the windows side ?



I am an absolute noob when it comes to ruby... so i don't know how and if your script acctually works.

---

### Post by michwill on 2008-06-05
Actually I created a simple bash script that always exits 0.  I still receive a failure 100% of the time.  

I've been toying with the "PAM" authentication lines in the server config.

I tried running "openvpn.exe" from the command line on the Windows box and receive the following in the connection window:


```

Thu Jun 05 10:18:39 2008 OpenVPN 2.0.9 Win32-MinGW [SSL] [LZO] built on Oct  1 2006
Thu Jun 05 10:18:43 2008 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Thu Jun 05 10:18:43 2008 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Thu Jun 05 10:18:43 2008 UDPv4 link local (bound): [undef]:1194
Thu Jun 05 10:18:43 2008 UDPv4 link remote: 192.168.1.182:1194
Thu Jun 05 10:18:45 2008 [mGreg] Peer Connection Initiated with 192.168.1.182:1194
Thu Jun 05 10:18:46 2008 AUTH: Received AUTH_FAILED control message
Thu Jun 05 10:18:46 2008 SIGTERM[soft,auth-failure] received, process exiting
Thu Jun 05 10:18:46 2008 OpenVPN 2.0.9 Win32-MinGW [SSL] [LZO] built on Oct  1 2006

```


So, I'm currently using 2.1_rc7 on the server, but 2.0.9 on the client.  Is *that* the problem?  If not, how exactly do I go about verifying the certificate?

Please see the attached "openvpn.log.zip" for the server log.

Thanks.

---

### Post by michwill on 2008-06-05
Just updated the Windows client to 2.1_rc7 and still unsuccessful.

---

### Post by SpaceTeddy on 2008-06-05
ok, you have me seriously doubting myself now...
give me a few hours and i will setup a vpn like i *think* you want it. when i am done, i will pm you the details to login and test it. I am sure it is something trivial, but i cannot see it either... at least at the moment. 
It's easier for me to start from scratch work from there. And it is better for you to have a working example to be able to copy off. 

like i said, a few hours... gimme two or three

cheers :)

---

### Post by michwill on 2008-06-05
That would be amazing!

I've been working with both config files over the last couple of hours, but still have nothing.  It is now verifying the CA but I'm still getting refusal on auth.

---

### Post by SpaceTeddy on 2008-06-05
ok server is up and running, you have the details in your private messages. If there are any questions about the setup or what i have done, just ask.

Btw, it's a Ubuntu 8.04 LTS Server in a vm. fresh and clean install.

cheers

---

### Post by michwill on 2008-06-05
> **SpaceTeddy said:**
> ok server is up and running, you have the details in your private messages. If there are any questions about the setup or what i have done, just ask.

Btw, it's a Ubuntu 8.04 LTS Server in a vm. fresh and clean install.

cheers

Alright!  Thank you!

After much PMing and going back through your previous notes, I have my server up and running with internet connectivity.  I will post a final tutorial as soon as time allows.


SIDE NOTE: Now, I'll actually need to test it in a real scenario.  All my current routers prevent "loopback" traffic. For whatever reason, all of my newer routers won't allow traffic that initiated from inside the network back in so I can't "fake" a real-world VPN scenario without going to another location (e.g. a neighbor's house) and "dialing" back in.

SIDE SIDE NOTE:  I *really* need to get in the know regarding iptables and the like (whether old technology or not).  I don't have a clear understanding of iptables, tun/tap, or any of that.  If you have suggestions I'm all for some heavy reading.

---

### Post by SpaceTeddy on 2008-06-05
sorry, i have no tutorials for that. I have been doing this so long, i have no idea anymore where i picked it up. So you will either have to search yourself or hope someone else will answer that question. 

What i can suggest for basic network understanding is the book "computer networks" by Andrew Tannenbaum. Great piece of work, explains pretty much everything that you need to know to work with networks. 

sorry i am of no help here :(

PS: i will take the vm offline again. If you still need it, i can fire it up again.

---

### Post by michwill on 2008-06-09
Ok, this is odd.  Just to check my sanity, I installed OpenVPN a few times to make sure I had it correct.  I *then* went to the actual production machine to set it up and I am now getting this error.

```
* Starting virtual private network daemon.
/etc/init.d/openvpn: 181: STATUS: not found
```

However, if I perform a "force-reload" the vpn seems to start fine. Oddly enough, nothing makes it to any log files and I am unable to authenticate from any clients.  It's as if the VPN is actually not running at all.  My initial guess is that it has something to do with VMWare being installed and fooling with the TUN/TAP stuff.

I might just end up virtualizing the VPN instead of installing it on the primary hardware.

Thoughts?

---

### Post by SpaceTeddy on 2008-06-09
mhm - that sounds to me as if the start/stop script is buggy (which is highly unlikely, but you never know).

can you start the server manually with a 
> sudo openvpn --config /path/to/conf/file

if this works, then it is the start/stop script. What distro are you using Maybe a pruge of openvpn and complete reinstall helps. I can also load the VM again and you can copy the start/stop script from there...

cheers

---

### Post by michwill on 2008-06-09
At this point, I'm not sure what's going on.  I ran the command:

```

sudo openvpn --config config_file

```

...and I got no visible errors.  But nothing is getting logged and I'm not sure what is occurring.  Are there any system logs that I might check?  This is sooooo amazingly re-frustrating!!! :confused:

I'm going to pursue a virtualized solution over the next hour and see where that takes me.  I still have another system that works just fine, but I see no difference between the two other than 32-bit vs 64-bit Ubuntu.  32-bit is working, 64-bit isn't.  *shrug*

Thanks again in advance.

---

### Post by SpaceTeddy on 2008-06-09
can you please post the output of the command. Also, please remote any daemon and log file from the config if you want to run it manually, as you do not want the logs to be written but the openvpn to log onto the console. 

you might also want to have a look at the "script" command to log your output while typing.

---

### Post by michwill on 2008-06-09
Ok, the whole "STATUS: not found" thing was due to my log directory being named "opevpn" instead of "openvpn" (yup I need a vacation!!! :P).

For some reason I can't allow the vpn server to start automatically.  I must "misname" the ".conf" file then once the system is up I must start it manually.  Otherwise I end up with no network connection on the vpn server itself.  *shrug*

---

### Post by michwill on 2008-06-09
. . .and finally (I hope).


I've got the VPN server running well with user/pass auth working.  *Now* I'm having an issue of conflicts.

The following two lines cause trouble with my VMWare installation:

```

/sbin/iptables -A POSTROUTING --table nat -o ! tun0 -j MASQUERADE
/sbin/iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE

```


Whenever those are enabled, I am unable to access the "VMWare Server 2 Beta 2" on the machine that also runs the VPN. VMWare actually gives me a "Web Service Not Available" error.  However, if I'm understanding properly, the converse is that if I disable those two lines I won't have network communications (or internet access) between connected machines.

Obviously the next option is to really virtualize the VPN, but Ubuntu Hardy won't install on the server, and OpenVPN 2.1 looks to be a pain to set up on on earlier versions of Ubuntu (which will install).

So, unless I can somehow get around this "iptables" issue, I will have to do one of two things in virtualization:


1) Resort to an older version of Ubuntu and pain myself to install OpenVPN
2) Succumb to a Windows installation of OpenVPN and pain myself to configure it

Either way, there appears to be pain.  ;)

Any thoughts?

---

### Post by SpaceTeddy on 2008-06-09
is the vm-server bridged or nat'ed ? Also, can you draw me (another) picture what the real setup looks like now... i might be able to "see" what the problem is by looking at the network setup. 

Thanks..

PS: the last thing you want is a windows installation of openvpn. THAT is a pain. Done it once, still regret it...

---

### Post by michwill on 2008-06-09
I'm not sure.  I just installed the VMWare server on the same hardware as the OpenVPN server. To my knowledge everything is bridged on the VM.  It creates several ("/dev/vmnet1", "/dev/vmnet2", etc.) network connections for its own use and I'm not sure how to effectively check to see what is being affected.

I've attached an image of the network.  You'll notice that there is nothing special going on.


SIDE NOTE:  I don't know why I'm having such a time wrapping my head around the TUN and TAP concepts.  Perhaps I need a basic look at what is really occurring instead of approaching it from any particular group's paradigm.  I need to know what is actually happening at a generally lower level.

QUESTION (A BIT OF FRUSTRATION, A BIT OF IGNORANCE):  Is it really necessary for the networking paradigm to be this convoluted?  It would seem that one should simply be able to create a "virtual adapter" and manage it as a single unit.  I can see the need for a separate "bridge" object at times, but why the need for TUN vs TAP (or TUN + TAP, rather)?  Oh well, c'est la vie. ;)

---

### Post by SpaceTeddy on 2008-06-10
mhm... ok, let me ask differently. Is the IP of the VM the in the same subnet as the rest of the machines ? or does it have a shared connection with the host only and uses the hosts IP to connect to anything.
The reason i am asking is - if you are bridged, then the VM will act (network wise) completely independent of the host machine. Even iptables on the host is ignored. I think that is what you want as a setup. On the other hand, if you are nat'ed, you might run into the problem that vm does simply not allow connections inbound to a nat'ed vm. I've never tested this theory... this is only a guess.

For simplicty reasons, i will not explain what is happening at the lower levels (first and foremost, because i am not 100% sure either, and second, this would be a VERY LONG post if i tried), in in the end, understand the tun device as a completly seperate device. It is handeled as any other network card would be. The only different is, that you cannot plug a network cable into it - since it is virtual. Or different, the network cable you plug into it is the vpn connection that you initiate. So, as for understanding it - think of it as a real network card, and think of the VPN as a real network. 
with iptables, the tun device is handeled as any other network card. The same applies for routes. essentially, the VPN becomes a net network, which is attached to your tun device. 

And now to the picture. I am assuming that your network has a range of 192.168.0.0/24 (as you did not provide one in your picture, i am just guessing). Also, i will assume that your vpn still uses the 10.8.16.0/24 network.
Now, lets in asci your network looks like this
> 
Internet
|
Router
|
Switch - Other devices(Mac Book, windows xp, etc)
|
VPN Server

now, lets fill on some network card names. I will *guess* them, you will need to match them to acctual setup as i do not know them

> 
Internet
|
(ppp0)
Router
(en0)
|
Switch - Other devices (Mac Book, Windows xp, etc)
|
(eth0)
VPN Server
(tun0)


this is still the same setup, just has some added details. NOTE: i have added the tun0 device, which is (phsycially) not attached to anything, it just exists yet !!! we will use it later 

The next step is that i will add ip's to the network devices as we will need them later on. here is the (again modified) view on the network:

> 
Internet
|
(ppp0 - 34.45.56.67)
Router
(en0 - 192.168.0.1)
|
Switch - Other devices (Mac Book - 192.168.0.5, Windows xp - 192.168.0.6, etc)
|
(eth0 - 192.168.0.2)
VPN Server
(tun0 - 10.8.0.1)


Ok, and here comes the trick. The tun0 device is virtual and has no physical network attached. Therefore, one seems to *think* this is not a real  network device... which is wrong. See it as a real network card, see the vpn clients to be a real network. To illustrate that, i will (again) extend the picture that i have drawn.


> 
Internet
|
(ppp0 - 34.45.56.67)
Router
(en0 - 192.168.0.1)
|
Switch - Other devices (Mac Book - 192.168.0.5, Windows xp - 192.168.0.6, etc)
|
(eth0 - 192.168.0.2)
VPN Server
(tun0 - 10.8.0.1)
|
Switch - (tun0 - 10.8.0.10) Client2
|
(tun0 - 10.8.0.6)
Client1 


Now THIS s what i think of when i do vpns. Attached to the server is another switch which holds all the vpn clients. Leave the real connection out for a while, just try to wrap your head around this. 

Now... we have the pictures like i want it. Let's discuss the routes first.
A client on the 192.168.0.0/24 network needs to know what to connection a client in the 10.8.16.0 network ? it needs a route to find the client. This route can either be added on any client, or it can be added on the router. I personally always prefer the router, as it means i don't have to do any changes to the clients and don't have to think about it when i am adding new clients. 
So, lets add a route to the router saying that the 10.8.16.1 network can be found at the ip 192.168.0.2 (which is the vpn server). Any paket from any client on the 192.168.0.0/24 network who whishes to contact a vpn-client now sends it's paket to the router, which forwards it to the vpn-server, which then send it to the appropriate client. 
The next step is making sure that a vpn client can answer this request. As they do not know where the internal network is, they will NOT send it back via the vpn, but via their local lan. So we have to tell them that a client with the ip 192.168.0.0/24 is to be contacted via the vpn. For that, the push "route 192.168.0.0/24" comes into the openvpn server. This will ensure that any vpn client who tries to contact an ip address in that range will be forced to use the vpn link. The next hop is then the vpn-server, which is already connected to the right network and can therefore deliver the paket normally. 
I hope that was understandable :)

We know the routes are right. What else do we need ? IP Forwarding. As i said, the tun device is handled as any other network card. So, for a paket to pass from eth0 to tun0 or vice versa, the vpn-server MUST be allowed ip_forwarding. This can be enabled temporarily with 
```
sudo sysctl -w net.ipv4.ip_forward=1
```
checked with
```
sudo sysctl net.ipv4.ip_forward
```
and enabled upon boot in the /ect/sysctl.conf file. 

Of course, the whole thing can be seen this abstract, but then you are forgetting that you still need the acctual vpn connection. But i'd rather view that in a different context - like accessing a web-server. The connection to the VPN only has to be established once and once that is done the abstract view can be used (this is not 100% true as there are a few gotchas where they interact, but we'll leave that out for now).

I have written way more than i wanted, but i hope that helps you get a better grasp of what is happening with the vpn. 

i hope it helps :)

---

### Post by michwill on 2008-07-26
Ok, after just over a month away from this project, I'm baaaaaaack...

I know, I know.  :rolleyes:


Alright, let's see where we are:

1)  All of the machines involved are on the 192.168.1.0 subnet

2) I can access the VPN just fine now, however, I can't access any "local" machines except the VPN server itself

	-- Also, despite the "eth0" ip address of the server being 192.168.1.5, I must communicate via the "tun0" connection to 192.168.128.1 (I guess this is expected?)

3) All *REMOTE* machines connected to the VPN can talk amongst one another (as expected), however they can't communicate with machines on the local network, and vice versa.

4) If I perform the "/sbin/iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE" I seem to lose the internet connection on the VPN server itself.

	-- Do I need to create a bridge of some sort and place "eth0" in promisc mode then have the magic happen there, or is that paradigm completely wrong?

5) I receive "Web service not available" on my VMWare Server Administrative Interface when performing *any* of the "iptables" commands.

	-- If I could get internal and external routing taken care of, access to the Administrative Interface wouldn't be such a huge issue (although I'd still like to eventually have it accessible)


My apologies for the vagary of this comment.  I'm just getting back into this project and I wanted to get something posted as soon as possible .




Best.

---

### Post by SpaceTeddy on 2008-07-27
You're one lucky dude. Usualy i unsubscribe from threads after they have gone inactive for more that a week. Didn't have time to clean up in the past weeks tho.
Anyways, before i go into answering your questions i feel like i should point out that all your problem now do do not lie with the vpn itself, but with the routes in your local network as well as the vpn. To Me, this does not sound like any VPN problem anymore.

Now, for the questions... 
> **michwill said:**
> 
2) I can access the VPN just fine now, however, I can't access any "local" machines except the VPN server itself

	-- Also, despite the "eth0" ip address of the server being 192.168.1.5, I must communicate via the "tun0" connection to 192.168.128.1 (I guess this is expected?)

Yes, this is expected. Your VPN clients only get told that the 192.168.128.0/24 network is reachable over the VPN. They do **NOT KNOW** that a 192.168.1.0/24 network exists there. In other words - you need to tell the vpn client where to find the 192.168.1.0/24 network, and you need to tell the clients on the local lan where to find the vpn.
Now, these are two seperate steps to be done here.
1.) tell the VPN where to find the local lan:
- for that, simply add the line *push route "192.168.1.0 255.255.255.0"* to your vpn server config and reload the openvpn process. This will tell every client that it shall look for the 192.168.1.0 network in the vpn and not the normal internet.

2.) However, this is only half the job done. The vpn can not send pakets to the local lan, but the local lan does not have any idea how to send a reply back to the vpn. For this, you can two choices again. I personally prefer b) :

a) use masquerading on the vpn server so that the clients on the local lan *think* the paket acctually came from the vpn. They can answer to it by sending the paket to the vpn - which is the only computer that can forward the paket through the vpn to the appropriate client. For this, you need something like the iptables rule you mentinoned in your question 4.)

b) Add a route to the default gateway of your local lan. Specifically, tell it that any paket for the 192.168.128.0/24 network reaching it shall NOT be send to the internet (default gateway) but instead to the vpn server. This way, the clients on the local lan don't acctually know where the vpn ist, but the first hop (your gateway to the internet) knows this and will direct the pakets accordingly. The beauty is that you only have to configure this one, and any new client on the local lan will automatically be able to find the VPN without any further configuration. 
Also, Only this setup will enable you to have backwards connection (i.e. from the local lan to the VPN) and there is no NAT hiding the VPN from the local lan

> **michwill said:**
> 
3) All *REMOTE* machines connected to the VPN can talk amongst one another (as expected), however they can't communicate with machines on the local network, and vice versa.

i think that already got a answered in my previous ramblings from question 2.)
> **michwill said:**
> 
4) If I perform the "/sbin/iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE" I seem to lose the internet connection on the VPN server itself.

	-- Do I need to create a bridge of some sort and place "eth0" in promisc mode then have the magic happen there, or is that paradigm completely wrong?

no, this sounds more like you are masquerading something wrong. Can you please give me the output of the following commands so that i can see if the iptables command is correct ? 
```
ifconfig
route -n
```
... 'cos it really looks like it should be working... 
> **michwill said:**
> 
5) I receive "Web service not available" on my VMWare Server Administrative Interface when performing *any* of the "iptables" commands.

	-- If I could get internal and external routing taken care of, access to the Administrative Interface wouldn't be such a huge issue (although I'd still like to eventually have it accessible)

i have no idea about that one. it sounds like something is wrong - but don't ask me what. Can you please explain a little further here so that i might understant what that question is accutally about ?
sorry for being thick :)
> **michwill said:**
> 

My apologies for the vagary of this comment.  I'm just getting back into this project and I wanted to get something posted as soon as possible .
Best.
yeah, as i said, usually i unsubscribe a week after a thread has gone inactive... Let's see if we can still figure this out :)

hope this helps :)

---

### Post by kevdog on 2008-07-27
Teddy

Wow -- you should be nominated king of OpenVPN in the forums:)

Regarding your advice:
> 
b) Add a route to the default gateway of your local lan. Specifically, tell it that any paket for the 192.168.128.0/24 network reaching it shall NOT be send to the internet (default gateway) but instead to the vpn server. This way, the clients on the local lan don't acctually know where the vpn ist, but the first hop (your gateway to the internet) knows this and will direct the pakets accordingly. The beauty is that you only have to configure this one, and any new client on the local lan will automatically be able to find the VPN without any further configuration.
Also, Only this setup will enable you to have backwards connection (i.e. from the local lan to the VPN) and there is no NAT hiding the VPN from the local lan


Can this be done if you are using dd-wrt on your router as your default gateway?  This assumes, and hopefully so, that you have used dd-wrt or openwrt in the past.

---

### Post by SpaceTeddy on 2008-07-27
thank you very much for your compliment. 

As for your question. I have worked with openwrt before - but it was a while ago (about a year or so) that i acctually configured one. So i might not be totally right. 

Generally, with the standard software coming from the vendor on your router box, i don't think this is really possible as most vendors don't seem to be too inclined to add real routing functions into their front ends (they must have the functionality - they simply don't share it :( )

Also, i have never worked with dd-wrt. So i cannot offer any help there, but my guess is that - since you have basic routing functionality - the way to configure it is pretty similar to a "full blown" Linux

As for openWRT - **yes**. I have seen this done, i even have a working openWRT box currently active on a VPN acting as a LAN gateway between networks. My configuration is a little different to the one discussed in this thread, yet i have seen the console and know that that the route command is acctually there - which is pretty much all you need. 
Taking the example from above, all you would need to do on your openWRT box is add the following command:
```
route add -net %network% netmask %mask% gw %vpn%
```
where
 %network% is your vpn net - in this case 192.168.128.0
 %mask% is the subnet mask of the network - in this case 255.255.255.0
 %vpn% is the IP address of the vpn server - in this case 192.168.1.5

That would be step b) as descibed in my last post

hope it helps :)

---

### Post by michwill on 2008-07-27
> **SpaceTeddy said:**
> You're one lucky dude.

Haha!  I don't feel the need to argue that one bit.  I absolutely appreciate your help.  I'm away from the office today and tomorrow, but I'll try to VPN in tomorrow afternoon and get you that info.  *That* I can do.  ;)

Also, my apologies for the semi-unrelated requests.  I just figured since I was having the issue(s) with the same overall project, I'd log the saga in one setting.

All hail King VPN! =D>

---

### Post by kevdog on 2008-07-27
> **michwill said:**
> 

all hail king vpn! 

+1

---

### Post by SpaceTeddy on 2008-07-28
i'll be away tomorrow and won't be back until sunday - meaning i will not answer until next monday.

Just to let you guys know :)

---

### Post by peap on 2008-08-09
I'm also giving OpenVPN a try to be able to swap backups with a few friends, access my files from school and for the occasional LAN over internet starcraft (or other oldie) gaming session.

Unfortunately I can't get very far with the installation. I'm failing at the ". ./vars" step. I get this message: 
```
"NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys"

```

I've edited the key values mentioned in the HOWTO like so:
```
export KEY_COUNTRY="SE"
export KEY_PROVINCE="SK"
export KEY_CITY="Lund"
export KEY_ORG="Snutt"
export KEY_EMAIL="johan@snutt.net"
```

And then I try to "sudo ./clean-all" and get:
```
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
```

Using "source ./vars" makes no difference. I'm using 8.04 server edition and the 2.0 easy-rsa subdirectory.

Feels like a pretty dumb problem, not even getting started with makeing the keys... especially as I've spent a few hours reading various documents over at the openvpn site before I started :-)

What am I missing/doing wrong?

Edit:
I just realised that OpenVPN was released a week ago and my installation is apparently 2.1. Perhaps something is different or perhaps broken in this version?
```
OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
```

---

### Post by SpaceTeddy on 2008-08-09
as far as i know, you will need to run the source ./vars in the same shell as the clean-all.

meaning. try the commands in this order:

```
sudo su
source vars
./clean-all
```

that should do the trick (i think)

otherwise, i need more input in what you are trying to do :(

---

### Post by peap on 2008-08-09
Thank you, that solved my problem. I was logged in as administrator doing sudo commands, not as root.

I don't have time to continue the installation tonight but now I'm at least on my way.

Thanks again.

---

### Post by peap on 2008-08-11
Ok, I've got it working, sort of. 

I can connect to access my NFS shares and my TimeCapsule, this is the most important thing. I'm yet to test it from the physical outside but I'm pretty sure it works as I connected via my external ip.

The next issue is getting e.g. Starcraft to work. This game like a few others uses UDP broadcasts to find other gamers. It's not possible to specify an ip address for the connection.

Will my routed vpn work with this or do I need a bridged setup? My server and my desktop iMac both has double NICS, one connecting to the internet (using my ISP's DHCP) and one for my home LAN (using DHCP managed by my TimeCapsule).

---

### Post by peap on 2008-08-12
This info helped me with my bridging issues: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

I've setup my server to use openvpn-auth-pam logins and it works fins. Now I'm wondering what kind of users I should make for the logins? Will a basic user with no rights at all on the server still be able to use the VPN? I imagine that any user logged in to the VPN will be set to "nouser" & "nogroup" as soon as he is logged in so the type of user account shouldn't matter, is that correct?

Still to try LAN games but most other things seems to be working which is cool as its ubuntu, osx, winxp and vista involved. Gotta love my ubuntu server :-)

---

### Post by SpaceTeddy on 2008-08-13
sorry for not anwering earlier.

Firstly, if you want to use broadcast games, yes you need bridgeing, and you need to embed your vpn into your real internal network. This brings the problem that all broadcasts made on your internal network will also go out into the VPN as many times as you have clients. AS an example - you want to play starcraft (this uses udp broadcasts) and are opening a game. If i remember correctly, the update intervall is 0.5 seconds for starcraft and the packet should be about 1K in size. This would mean a 2K average on your internal network. Now, a LAN does not even care about this kind of traffic - that is just background static. But for the vpn - lets say you have three clients connected - each of them get the packets. Which means you need 6K alone for the broadcasts - mind you, a 6000kbits DSL line has only 24K upload - what means you are using 1/4 of your total upload just for the game to be found. 
I am not saying you should not do this - i am just pointing out that this can lead to bottle necks real quick :(

Now - PAM.
What you acctually do when you authenticate against pam is use the /etc/passwd and /etc/shadow to figure out of the credentials supplied match any of your users. The user rights on the machine as well as it's uid, gid, homedir and whatever else they have do not matter. OpenVPN only authenticates against those two files. There is no process for the user started, there is nothing that is done on the server. It is a plain username/password question. 
So, even the most unprivilegdes user, as soon as he/she has a username and a password, can login (maybe the shell is checked, but i even doubt that). As soon as they are in the /etc/passwd, they can log in. 

I personally do not think this to be a very good idea, aspecially when you are creating the users "just" for the vpn. I'd rather use the auth-script in this case, and write myself a little perl script that pulls the username/password from a text file. This way, the users have nothing to do with the system, and pure vpn user does not get an ssh login, a home-drive and such things. But again, that is me.

hope it helps :)

---

### Post by peap on 2008-08-13
Thanks for the answers once again. I'm sure this info can be as helpful to others as it is to me.

As for the bottleneck my connection is DSL 20/3MBit (actual upload is about 2MBit) so I hope a few clients should be no problem.

As for the auth I just thought that a text file could be insecure so I created my users like this:
```
useradd -g nogroup -s /bin/false -d /nonexistent <username>
```

The thing is that I want to be able to give some of the users access to NFS and SMB shares, for convenience I thought a unix account would be better than a text file. Is that a misconception or are my thoughts on this in the right direction? ( for once :) )

Thanks again for your patience and expertise.

---

### Post by SpaceTeddy on 2008-08-14
you are right there. If you want to use the users for some other services aswell, then you should create them on the system. Then it would make sense to have them authenticate against pam (although, as far as i remember, smb also need them in it's own smbpasswd backend for the logins to work - which fork off pam, but do not use pam. Maybe i am mistaken, as i have no configured a samba for a long time)

Also, your internet should be fast enough to handle basic broadcasting - i just hope you don't have too many clients or too many broadcast services running... arp can be really annoying when it is chewing bandwidth (there is a reason why this only runs on LAN - not WANS). Well, i guess you'll see eventually if this works for you or not. I just hope it does work for you :)

cheers

---

### Post by hkazemi on 2008-09-24
If you setup a bridging firewall between the OpenVPN interface(s) and the real internal network, you could filter out all broadcasts except those that you know you really need.  (You can probably figure out the *needed* broadcast ports/characteristics either from the program documentation or by using Wireshark.)

There is more on this topic here:
[http://www.securityfocus.com/infocus/1737](http://www.securityfocus.com/infocus/1737)
[http://www.debian.org/doc/manuals/securing-debian-howto/ap-bridge-fw.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-bridge-fw.en.html)
[http://bio3d.colorado.edu/tor/sadocs/tcpip/bridge.html](http://bio3d.colorado.edu/tor/sadocs/tcpip/bridge.html)

older docs:
[http://www.faqs.org/docs/Linux-mini/Bridge+Firewall+DSL.html#ss2.1](http://www.faqs.org/docs/Linux-mini/Bridge+Firewall+DSL.html#ss2.1)
[http://tldp.org/HOWTO/Bridge+Firewall.html](http://tldp.org/HOWTO/Bridge+Firewall.html)
[http://tldp.org/HOWTO/Bridge+Firewall-2.html#ss2.1](http://tldp.org/HOWTO/Bridge+Firewall-2.html#ss2.1)

---

### Post by qchapter on 2008-11-17
Kudos to SpaceTeddy for the knowledge sharing on OpenVPN.  If I had stumbled upon this thread a couple of weeks ago I would have saved hours when setting up my own vpn.  This thread is a perfect example of what makes the Ubuntu and the GNU/linux community at large so great.

Thanks again!

-Kevin

---

### Post by michwill on 2008-11-18
Wow, this thread has absolutely evolved.  Nice job SpaceTeddy.  Alright, I've actually got mine working well and all computers on the VPN can speak to one another just fine.  However, I still cannot communicate with machines that are on the same network as the VPN Server, and I need this feature.

I understand that there are multiple mechanisms for accomplishing this -- everything from rerouting at the router itself, to creating firewall rules on the VPN server.  My question is:  Which method (even of those not mentioned) is the most recommended for such?  I need all machines, local and VPN, to be peers.

Best.

---

### Post by SpaceTeddy on 2008-11-19
First of, thanks for the compliments !

Now to your question:
If you have trouble getting into networks that are reachable through the vpn (or should be) this is (most likely) not a vpn problem. This is mostly a problem with routing. 

I guess you are pushing routes through vpn connection to the client to your internal network, right ? But this is only half the work. Now your vpn-clients know where the internal network is - but how does the internal network know where your vpn is ? exactly - they don't.
There are two solution to this. 
1.) Masquerade the traffic on the vpn that passes from the vpn into the internal network. This way, the internal clients don't need to know where the vpn client is - they only need to know where the vpn server is. 
The downside of this that this will enable your vpn-clients to talk to your internal network - but nobody from the internal network will be able to talk to the vpn. This is a one-sided connection fix only.

2.) add a route to the vpn on your default gateway. This is the cleaner as it enables both side to talk to each other. Again, this works because now, a client still does not know where the vpn-client is, so it send the packet towards it's only known forwarder - your default gateway. Since that one now knows where the vpn is, the traffic get kicked back into your network to your vpn server which has the vpn attached - thus answering is possible. 
The downside of this is that you can possible generate more traffic, as the connection bounces inside your network once... 

I personally prefer solution 2.

and i hope my assumption is right :)

---

### Post by kevdog on 2008-11-19
Could you provide an example of #2 saying one network is 192.168.1.1 and the other is 10.6.0.8?

Thanks

---

### Post by SpaceTeddy on 2008-11-19
Ok, here is a typical setup of this scenario:
> 
[COLOR="Blue"](10.8.0.6)[/COLOR]
VPN-Client 
(y1.y2.y3.y4)
|
Internet
|
eth0 (x1.x2.x3.x4)
Def GW 
[COLOR="Red"]eth1 (192.168.0.254)[/COLOR]
|
Switch -> [COLOR="Red"](192.168.0.20)[/COLOR] OpenVPN server [COLOR="Blue"](10.8.0.1)[/COLOR]
|
[COLOR="Red"](192.168.0.10)[/COLOR]
Internal Server


The Blue IP's are able to talk to each other - they are (in this case) the vpn network. i.e. 10.8.0.1 can reach the 10.8.0.6 and vice versa. Likewise, the red ip's are on the same network (this is physical).

Now, the first step is to push the route to the internal network to the vpn client - this is done via
> push "route 192.168.0.0 255.55.255.0" 
in the vpn server configuration file. So, now the client knows where the internal network is (through the vpn). This is what i exepcted had been done before. 

But a client in the red network does not know where the blue network ist. Thus, it will send the answer to any query from the a vpn client (blue) not back into the red network - it will send it to the def GW (default Gateway) . The trick is to give this one a route to the blue network so that the packet does not go out into the internet, but instead is redirected to the vpn-server which can acctually send the reply to the vpn client (blue network again)

the route command for a temporary change would look like this here (to make it permanent, i would bind the route in the /etc/network/interfaces in the post-up of eth1):
```
route add -net 10.8.0.0 netmask 255.255.255.0 gw 192.168.0.20
```
now, the reply packet from the server will go the from the it's networkcard (192.168.0.10) to the def GW (192.168.0.254) to the vpn server(192.168.0.20) to the vpn process (10.8.0.1) and then via the tunnel to the client (10.8.0.6)

This is a basic routing scheme... All you have to do is tell the def.GW where the network acctually is - since that one is the only one that does not know anything about it...

hope it helps :)

PS: as a sidenote - if you have a firewall running on the def GW you cannot do this stateful here, as the GW NEVER sees a connection being established form the client to the server - it only sees the replies...

---

