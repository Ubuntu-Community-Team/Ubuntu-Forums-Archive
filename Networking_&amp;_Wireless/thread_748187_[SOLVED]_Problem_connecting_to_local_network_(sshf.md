---
title: "[SOLVED] Problem connecting to local network (ssh/ftp)"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by fitzbuntu on 2008-04-07
Hi, I'm semi-experienced on Ubuntu - another Windows Vista refugee. We use Linux at work, but I'm not an SysAdmin, it's mainly for the applications that run on it so some things are alien to me.

I'm having problems with my home network and I wonder if someone can help?

I'm runing Ubuntu on my desktop and Kubuntu on my laptop. I can ssh to my laptop fine but for some reason ssh is not working (hanging) when I try to ssh to my desktop or local virtual machine I am running. I tried ftp through Filezilla and this didn't work either.

Kubuntu was working fine previously, I can still log onto the internet and, oddly, I can log into the web front-end of my local (host) vm through the internet (using the IP address).

Here's the debugging info from ssh:

```
OpenSSH_4.6p1 Debian-5ubuntu0.2, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.65 [192.168.1.65] port 22.
```

I have no firewall running, I've tried rebooting and restarting ssh to no avail. Here are the contents of my ssh_config file:

```
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
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```

I haven't edited this and I never checked it previously either, as I said it was working fine till today.

---

### Post by fitzbuntu on 2008-04-07
*bump*

Sorry, I've googled as much as possible and tried a few different solutions which have not worked so far...

---

### Post by Eiríkr on 2008-04-07
If your desktop and VM are default Ubuntu installs, the **ssh** package doesn't come included by default, so you'll have to install it yourself.  If it's already installed and you *still* can't ssh in, there's something else going on.  

HTH,

Eiríkr

---

### Post by fitzbuntu on 2008-04-07
I have a downloaded VMware Server package as the default that came in the Ubuntu repositories wouldn't allow me to install.

I also have openssh-client and openssh-server installed, and like I said, it was working (Friday) and I just ran **sudo apt-get install ssh** which tells me I already have the latest version.

---

### Post by zekica on 2008-04-07
you should install:
**sudo apt-get install openssh-server**

---

### Post by fitzbuntu on 2008-04-07
Yep that's installed.

Thanks for the responses, I think this is something other than an ssh problem. I can't ftp either, but I can connect to the net and I can enter a local ip address in my browser and get the test apache page.

I have a virtual machine which launches a web based application- I have no problem reaching the web-based app through my browser, it seems to be other non http connections. However aMsn is working.

Before you ask I don't currently have a firewall installed.

Cheers,
Fitz.

---

### Post by fitzbuntu on 2008-04-07
Just need to add that I can ftp (and possibly ssh external- ie the web) I'm just having trouble on the internal network- that is both my vm and my desktop (my desktop will ssh to me know problem).

Thanks

---

### Post by Eiríkr on 2008-04-07
@zekica -- 

The ssh package in the repositories is a redirector for the openssh package, so there's no real difference between what fitzbuntu ran and your suggestion.  

@fitzbuntu --

Is it possible that the issue might be the type of network you have set up for your VM?  It's been a while since I've poked around with my copy, but I dimly recall three networking types: bridged (VM connection goes straight to the outside), NAT (using the host as a router), and host-only (which I think is what you need).  I also recall that it's possible to have multiple virtual NICs, so you should be able to configure all three of these options at once if so desired.  

Cheers,

Eiríkr

---

### Post by fitzbuntu on 2008-04-07
Eiriker,

Thanks for the response. I have host-only setup currently but have previously been able to switch back and forth between the two.

The thing is it's not just my vm, it's my desktop pc I can't reach either (which uses Ubuntu 7.10). My desktop will ssh just fine to my Kubuntu 7.10 laptop, just not the other way round.

---

### Post by Eiríkr on 2008-04-07
Could you perchance post the terminal text of an attempt at ssh-ing into your desktop?

---

### Post by fitzbuntu on 2008-04-07
OK I'm a doof.

Since my VM and Desktop pc had stopped working I assumed there was a problem with my laptop, but on a hunch I just went and lowered the firewall to my desktop and hey-ho it worked! #-o

So I added my laptop ip address to the firewall and now it's fine. Still can't connect to the VM.

So it looks like I just need to modify iptables to allow ssh connections, but I'm not sure how to do that if anyone can give me a hand?

---

### Post by fitzbuntu on 2008-04-08
OK I finally fixed it for my VM by removing the vmware-server package and re-installing it.

I did discover a problem when I tried to do a fresh install using **vmware-config.pl**.

It originally gave me this error:

```
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

```

I found the solution somewhere else on this forum but essentially I needed to run:

```
update-rc.d -f vmware-server remove
```

To remove existing startup links from the previous installation.

Thanks for all the help offered, I never really discovered the original reason why vmware-server stopped allowing ssh but a clean install fixed it.

I'm now using vmware-player which I've found to be quite useful.

---

