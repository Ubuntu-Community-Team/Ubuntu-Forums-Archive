---
title: "ssh on vmware"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by soaringfalcon on 2011-04-18
I have been banging my head on this, I am sure I am missing something simple.

I installed vmware (3.1.4 build-385536) and then installed of Ubuntu.  I then installed SSHD so that I could ssh into this box from work.  I was happy to see that when I 'ssh localhost' I connect.  So, SSH is working.  Then I go into my linksys router and set up port forwarding (keeping it simple on port 22 right now). 

I now test connecting. After timing out I tried:
ssh -vvvL [email]joe@xxx.xxx.xxx.xxx[/email]
and get the following:
Bad local forwarding specification 'joe@xxx.xxx.xxx.xxx
I run ipconfig and verify that I set up the right IP in my router settings:
192 . 168 . 1..xxx

I also have tried both nat and bridged connections.

I really am not sure what to try next, so any suggestions would be welcome

TIA

---

### Post by bodhi.zazen on 2011-04-18
Use your public IP address ;)

---

### Post by Leppie on 2011-04-18
if you want to use your vmware image to ssh into from your office, and want to test it from home you will have to use 2 network adapters, 1 natted and 1 bridged.
the natted adapter will allow you to connect from outside your home network (but you most probably require port forwarding on your router), the bridged adapter will allow you to connect from within your home network.

---

### Post by soaringfalcon on 2011-04-18
I am connecting from another shell, so it is like I am connecting from the outside world and this is where I am getting the error.  I tried again to change to natted but still getting the same error.  Are you saying I need two network cards to allow SSH connections into my vmware?

And I am trying to ssh to the outside IP, I think that ip forwarding  tells anything that tries to connect to port 22 on my public IP to go to the box I specified in the linksys set up.

---

### Post by bodhi.zazen on 2011-04-18
On vmware you only need 1 network interface and it needs to use bridged networking.

an additional thought, did you activate your firewall ?

---

### Post by Leppie on 2011-04-18
if you want to test your ssh setup from within your home network, you will need to use a bridged card for the vm and use the local ip address.

---

### Post by soaringfalcon on 2011-04-18
Thanks for the help!  I am sure it is something simple, Right now all I am trying to do is connect from a shell account I have to this vmware. From work I probably will just ssh, but if need be I can ssh to the shell I am testing with tonight.  I have it set up to bridged.   

I did not set up my firewall.  Any other ideas?

---

### Post by Leppie on 2011-04-18
anything in your sshd_config blocking access?

---

### Post by bodhi.zazen on 2011-04-18
Looking back at the original command, you have an extra "L"

ssh joe@ipaddress

If you want verbose output, use -vvv

ssh -vvv joe@ipaddress

The -L is to port forward, and to do that you must specify a port ;)

---

### Post by soaringfalcon on 2011-04-18
I didnt make any changes to the file, but just in case here it is:

root@ubuntu:/etc/ssh# cat ssh_config 

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
root@ubuntu:/etc/ssh#

---

### Post by bodhi.zazen on 2011-04-18
And the user "joe" has to exist on the server ;)

---

### Post by soaringfalcon on 2011-04-18
Yes, the user Joe exists. That is the user I used when setting up ubuntu.  Is there maybe somewhere I need to give him permission to ssh?

---

### Post by bodhi.zazen on 2011-04-18
> **soaringfalcon said:**
> Yes, the user Joe exists. That is the user I used when setting up ubuntu.  Is there maybe somewhere I need to give him permission to ssh?

Did you see my previous post regarding the -L option ?

---

### Post by soaringfalcon on 2011-04-18
sorry I missed that.  Here is the output without the -L

eris:/home/e/eldorado% ssh -vvv [email]joe@98.192.xx.xx[/email]
OpenSSH_5.1p1 FreeBSD-20080901, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 98.192.xx.xx [98.192.xx.xx] port 22.

And we hang here.  Until:
debug1: connect to address 98.192.xx.xx port 22: Operation timed out
ssh: connect to host 98.192.xx.xx port 22: Operation timed out

---

### Post by Leppie on 2011-04-18
could you post the sshd_config from the vmware? (the file you posted was ssh_config, the client config file)

---

### Post by soaringfalcon on 2011-04-18
I can only find the one, could it be called something else - or maybe there is something else I need to load?

root@ubuntu:/etc/ssh# find / -name sshd_config
/etc/ssh/sshd_config
/usr/share/doc/openssh-client/examples/sshd_config
root@ubuntu:/etc/ssh#

---

### Post by Leppie on 2011-04-18
was this output from the vmware image?

---

### Post by bodhi.zazen on 2011-04-18
> **soaringfalcon said:**
> sorry I missed that.  Here is the output without the -L

eris:/home/e/eldorado% ssh -vvv [email]joe@98.192.xx.xx[/email]
OpenSSH_5.1p1 FreeBSD-20080901, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 98.192.xx.xx [98.192.xx.xx] port 22.

And we hang here.  Until:
debug1: connect to address 98.192.xx.xx port 22: Operation timed out
ssh: connect to host 98.192.xx.xx port 22: Operation timed out

Is that the correct ip (98.192.xx.xx) ? I was expecting 192.168.xx.xx

If so, back to things such as a bridge vs NAT on VMWare , firewall on host ?

---

### Post by soaringfalcon on 2011-04-18
No, my outside address is 98.192.xxx.xxx (comcast)  The IP that I am forwarding it to behind the linksys is 192.168.xxx.xxx.

---

### Post by Leppie on 2011-04-18
try connecting to the 192.168.* address

---

### Post by bodhi.zazen on 2011-04-18
Well, step through the process ;)

Log into the Ubuntu ssh server.

Check the logs.

then ```
ssh joe@loclahost
```

Then, if that works, from your host,

```
ssh joe@192.168.xx.xx
```

Then, if that works, confirm your public ip address and try

```
 ssh joe@public_ip_address
```

---

### Post by soaringfalcon on 2011-04-18
no luck :(


eris:/home/e/eldorado% ssh [email]joe@192.168.xxx.xxx[/email]
ssh: connect to host 192.168.xxx.xxx port 22: No route to host
eris:/home/e/eldorado%

---

### Post by bodhi.zazen on 2011-04-18
It appears something is wrong with your virtual networking. Either you are not using a bridge, you have a firewall, or your host is not set up to forward packets, not sure.

---

### Post by soaringfalcon on 2011-04-18
I decided to start from scratch.  It is now working.  I really appreciate everyone who tried to help :)

---

