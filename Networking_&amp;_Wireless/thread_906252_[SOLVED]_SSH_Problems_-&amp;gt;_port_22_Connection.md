---
title: "[SOLVED] SSH Problems -&amp;gt; port 22: Connection refused"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by ny_NEx on 2008-08-31
Hi :)

I need some assistance, i have installed openssh-server, i can connect using ssh localhost and i can connect using any other computer inside my lan network.

The problem is when i try to connect from outside the lan.
I have set up port forwarding to forward port 22 to my internal ip address which is 192.168.1.8 

(router is 192.168.1.1)

error is;

ssh: connect to host xxx.xxx.xxx.xxx port 22: Connection refused

When i use telent, same problem, but when using telnet without port i can connect to my router.

I scan my computer with GRC ShieldsUP! and port 22 is OPEN

I have attached output of ssh_config,sshd_config and netstat.

Please help me, this is driving me crazy :mad:

Thanks anyway !!

---

### Post by handaxe on 2008-08-31
This is methinks, a router issue regarding NAT.  You have proved ssh works behind your router, so sshd.conf etc have no relevance here, unless you set limitations on what IPs can connect.

So, look to your router docs... You want to forward your local IP port to your WAN IP port.  That being so, you ```
ssh User@WANip
``` not 192.168.1.1

If you know this,my apologies but it is not clear.

BTW, when you get this working, think about disabling password login and use shared key as well as shifting the ssh port to another.  That way you will be saved from the brute-force bots which WILL have a go at you (assuming your router is world visible).

rgrds,

HA

---

### Post by ny_NEx on 2008-08-31
ssh works perfect locally!! 

When i use this 

ssh User@WANip -> 

connect to host xxx.xxx.xxx.xxx port 22: Connection refused

My ROUTER is ZyXEL P-660HW-D3, im very sure that port forwarding is set up correctly (NAT)

As described here

[http://portforward.com/english/routers/port_forwarding/ZyXEL/P-660HW-D1/SSH.htm](http://portforward.com/english/routers/port_forwarding/ZyXEL/P-660HW-D1/SSH.htm)

Is there any way to see if this is router problem or...?

I out of ideas :(

---

### Post by handaxe on 2008-08-31
sorry in a rush....

2 things, try ```
ssh -vvv user@WANIP 
```.  This will give verbose output.

Also, you can kill the sshd daemon ```
sudo /etc/init.d/ssh stop 
``` and then run 

```
sudo /usr/sbin/sshd -d
```. This will keep the server in the foreground and print debug to the terminal.

Combined, both should reveal anything that the sshd does not like.  If nothing registers in the sshd terminal then you are not getting through to it and the router NAT is prolly the issue.

HA

---

### Post by ny_NEx on 2008-08-31
No problem :) thx for helping me out....

This time i changed the port on router and on ssh (443), working locally!

output of....--->

ssh -vvv [email]ivan@xxx.xxx.xxx.xxx[/email] -p 443
OpenSSH_5.1p1 Debian-2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 443.
debug1: connect to address xxx.xxx.xxx.xxx port 443: Connection refused
ssh: connect to host xxx.xxx.xxx.xxx port 443: Connection refused




And output of this....

/usr/sbin/sshd -d
debug1: sshd version OpenSSH_5.1p1 Debian-2
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: Bind to port 443 on ::.
Server listening on :: port 443.
debug1: Bind to port 443 on 0.0.0.0.
Server listening on 0.0.0.0 port 443.

And when i try to connect nothing happens, is this meaning that i cannot pass by router?

---

### Post by handaxe on 2008-08-31
> **ny_NEx said:**
> And when i try to connect nothing happens, is this meaning that i cannot pass by router?

Yes.  The router is rejecting the connect instead of passing it to your PC. If it had done so, then the sshd invoked with the -d option would have shown the interaction that led to the rejection or acceptance of the connection.

If your router does logging of its firewall rejects there may be clues.  I do not know the ZyXEL P-660HW-D3 personally and it may not log stuff at all. Try tis though, but be quick. Turn off the firewall altogether if you can. You should be able to connect then.

When you try to connect, are you  trying from within your LAN but using the external IP address as opposed to logging in to an external PC and trying to ssh back in? If the former, I wonder about routing...

HA

---

### Post by ny_NEx on 2008-08-31
Hm i will try to find logs if any.... When i try to conect im using external ip within LAN

(im trying that from the same computer i want to connect using ssh)

,maybe this is the problem, i will look into it a let you know!

Till then thanks for your help!

P.S. 

Firewall if OFF, so i dont understand rejecting part!

---

### Post by ny_NEx on 2008-08-31
I think that problem is solved!!

Apparently it is impossible to test ssh connection in this way (from inside the LAN)

ssh externalIP(wan IP) -p xxxx

only 

ssh localhost -p xxxx

or

ssh internal (LAN IP) -p xxxx


So im not sure is this router problem, or something else but its solved for now :)

Thanks again for your help!

Good night!:KS

---

### Post by handaxe on 2008-08-31
Strange, as I can do it just fine. This is a router quirk perhaps, or setup.

In future you can try [https://www.nacs.uci.edu/ssh](https://www.nacs.uci.edu/ssh) for a web based (thus external) ssh client.

Change the "SSH Server/Alias: xxx.xxx.xxx.xxx" to your IP or FQDN. Have a go.

HA
I would change my password immediately afterwards, if not moving over to shared key (ie passwordless) login.

---

### Post by ny_NEx on 2008-09-01
I will do that!

Can you give me a short description how to do that with preshared key?

---

### Post by handaxe on 2008-09-01
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

Once done AND TESTED, in /etc/ssh/sshd_config on the server/host change entries to:
```
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication no
```You can also allow only certain users with:
```
AllowUsers xxxxxxx
```Restart sshd:

```
sudo /etc/init.d/ssh restart

```Now only the shared key route will work and passwords are not an option.  This frustrates common brute force probes from endlessly passing username password combos and eventually getting it right. You can also change the port in sshd_config:
```
Port xx
```Note; as in the above you are using shared key without a protective passphrase, your public : private key pair will be compromised should anyone malicious gain access to your PC/laptop. That is the risk of completely password-/phrase-less ssh.

HA

---

### Post by ny_NEx on 2008-09-04
Wow :) great!

 I aleady change the port, disabled root login, allow only two wrong password attempt and then you are disconnected and few other things i found on the net. I will try this as you described!

---

### Post by ny_NEx on 2008-09-04
I have another problem....

I want to use my mobile phone Nokia E90 to connect to my linux box at home, i use PuTTY to connect. 

Now everything is working but im not sure how to create keys, can i create keys on my linux box and then add the private key to my mobile phone and put my public key in authorized_keys2 on my linux box or not??

---

### Post by ny_NEx on 2008-09-04
I have managed to create keys and set everything up but now when i try to connect i get connection closed....

output of:  /usr/sbin/sshd -d


debug1: sshd version OpenSSH_5.1p1 Debian-2
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: Bind to port 12055 on ::.
Server listening on :: port 12055.
debug1: Bind to port 12055 on 0.0.0.0.
Server listening on 0.0.0.0 port 12055.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.1.36 port 49954
debug1: Client protocol version 2.0; client software version PuTTY-Local: Mar  4 2008 21:38:38
debug1: no match: PuTTY-Local: Mar  4 2008 21:38:38
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-2
debug1: permanently_set_uid: 112/65534
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: client->server aes256-cbc hmac-sha1 none
debug1: kex: server->client aes256-cbc hmac-sha1 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST_OLD received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user ivan service ssh-connection method none
debug1: attempt 0 failures 0
debug1: PAM: initializing for "ivan"
debug1: PAM: setting PAM_RHOST to "192.168.1.36"
debug1: PAM: setting PAM_TTY to "ssh"
Failed none for ivan from 192.168.1.36 port 49954 ssh2
debug1: userauth-request for user ivan service ssh-connection method publickey
debug1: attempt 1 failures 0
debug1: test whether pkalg/pkblob are acceptable
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: temporarily_use_uid: 1000/1000 (e=0/0)
debug1: trying public key file /home/ivan/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
buffer_get_ret: trying to get more bytes 4 than in buffer 0
buffer_get_int: buffer error
debug1: do_cleanup
debug1: PAM: cleanup
debug1: do_cleanup

---

### Post by ny_NEx on 2008-09-04
SOLVED! I think that the problem was in file i use 

.ssh/authorized_keys   -> for DSA
.ssh/authorized_keys2  -> for RSA

i mixed the two above.

Now everything is working with DSA...

---

### Post by ny_NEx on 2008-09-04
SOLVED! I think that the problem was in file i use 

.ssh/authorized_keys   -> for DSA
.ssh/authorized_keys2  -> for RSA

i mixed the two above.

Now everything is working with DSA...

---

### Post by ny_NEx on 2008-09-04
As i found on the internet RSA key must be created on the machine you wish to ssh from....?!

---

### Post by daqron on 2011-03-19
> **ny_NEx said:**
> Apparently it is impossible to test ssh connection in this way (from inside the LAN)
Thanks so much for figuring this out. I was pulling my hair out trying to SSH past my stupid DSL modem, and this turned out to be the problem. I'm using a ZyXEL PK5000Z, for the record, and all that was required was to setup port forwarding for the appropriate SSH ports I'm using. All SSH ports now forward to my router (192.168.0.2 on the DSL model's LAN) and the router's port forwarding takes over from there.

Cheers,
Jeremy

---

