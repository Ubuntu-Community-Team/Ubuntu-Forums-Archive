---
title: "cant get iptables to work"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by makenbaccon on 2011-05-01
I can't get my firewall up and running.  When I run my bash script, I get this message:

>  * Starting iptables                                                                                                     WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module ip_tables not found.
iptables v1.4.4: can't initialize iptables table `raw': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module ip_tables not found.
iptables v1.4.4: can't initialize iptables table `raw': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

my current kernel is 2.6.3-3

my current iptables is v1.4.4

If you need my bash script, I can post that too.

---

### Post by josephmills on 2011-05-01
> **makenbaccon said:**
> I can't get my firewall up and running.  When I run my bash script, I get this message:



my current kernel is 2.6.3-3

my current iptables is v1.4.4

If you need my bash script, I can post that too.

**Perhaps iptables or your kernel needs to be upgraded.**
first try 
```
sudo apt-get update 
```
then 
```
sudo apt-get upgrade 
```
what repos are you using?

---

### Post by makenbaccon on 2011-05-01
repos? what are these?

And after both updating and upgrading I have the same problem.

---

### Post by josephmills on 2011-05-01
> **makenbaccon said:**
> repos? what are these?

And after both updating and upgrading I have the same problem.
Please take a look at 
[http://en.wikipedia.org/wiki/Software_repository](http://en.wikipedia.org/wiki/Software_repository)
to see them in ubuntu there are a couple of ways the easy way is to go to ubuntu software center then edit then software sources then look at the tabs that will tell you what repos you have

---

### Post by alphacrucis2 on 2011-05-01
Goodness. That kernel is from 2004. Did Ubuntu exist then? Maybe the kernel version no is a typo.

---

### Post by makenbaccon on 2011-05-01
> Goodness. That kernel is from 2004. Did Ubuntu exist then? Maybe the kernel version no is a typo. 	

that's the kernel version, my version of ubuntu is 10.10

---

### Post by makenbaccon on 2011-05-01
by the way, I'm doing this through an ssh client, so any tips should not have anything to do with a GUI.

Anyone know how I can deal with this?

---

### Post by sandyd on 2011-05-01
> **makenbaccon said:**
> by the way, I'm doing this through an ssh client, so any tips should not have anything to do with a GUI.

Anyone know how I can deal with this?
it does not have anything to do with GUI.

Your kernel does not have the propper configuration in order to run Iptables.

Which means either
a) Too old.

b) Does not have
```

  &#9474; Symbol: IP_NF_IPTABLES [=y]                                                                            &#9474;   
  &#9474; Type  : tristate                                                                                       &#9474;   
  &#9474; Prompt: IP tables support (required for filtering/masq/NAT)                                            &#9474;   
  &#9474;   Defined at net/ipv4/netfilter/Kconfig:52                                                             &#9474;   
  &#9474;   Depends on: NET [=y] && INET [=y] && NETFILTER [=y]                                                  &#9474;   
  &#9474;   Location:                                                                                            &#9474;   
  &#9474;     -> Networking support (NET [=y])                                                                   &#9474;   
  &#9474;       -> Networking options                                                                            &#9474;   
  &#9474;         -> Network packet filtering framework (Netfilter) (NETFILTER [=y])                             &#9474;   
  &#9474;           -> IP: Netfilter Configuration                                                               &#9474;   
  &#9474;   Selects: NETFILTER_XTABLES [=y] 
```enabled in the kernel configuration.

Ill guess a).

post output of
```

[COLOR=Black]lsb_release -a[/COLOR]
```

---

### Post by makenbaccon on 2011-05-01
> **sandyd said:**
> it does not have anything to do with GUI.

Your kernel does not have the propper configuration in order to run Iptables.

Which means either
a) Too old.

b) Does not have
```

  &#9474; Symbol: IP_NF_IPTABLES [=y]                                                                            &#9474;   
  &#9474; Type  : tristate                                                                                       &#9474;   
  &#9474; Prompt: IP tables support (required for filtering/masq/NAT)                                            &#9474;   
  &#9474;   Defined at net/ipv4/netfilter/Kconfig:52                                                             &#9474;   
  &#9474;   Depends on: NET [=y] && INET [=y] && NETFILTER [=y]                                                  &#9474;   
  &#9474;   Location:                                                                                            &#9474;   
  &#9474;     -> Networking support (NET [=y])                                                                   &#9474;   
  &#9474;       -> Networking options                                                                            &#9474;   
  &#9474;         -> Network packet filtering framework (Netfilter) (NETFILTER [=y])                             &#9474;   
  &#9474;           -> IP: Netfilter Configuration                                                               &#9474;   
  &#9474;   Selects: NETFILTER_XTABLES [=y] 
```enabled in the kernel configuration.

Ill guess a).

post output of
```

[COLOR=Black]lsb_release -a[/COLOR]
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

---

### Post by sandyd on 2011-05-01
> **makenbaccon said:**
> No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick
```

sudo apt-get install linux-server [linux-image-2.6.35-28-server]("http://packages.ubuntu.com/maverick/linux-image-2.6.35-28-server")
```also, is this server in question on some web service such as Amazon EC2? Or VPS?
If yes, then ask technical support to upgrade your kernel. Or in the case of Amazon EC2, choose a newer AMI. There are some very annoying VPS providers these days where they don't set proper openvz/xen configurations, and when the kernel of a VPS is upgraded, everything screws up.

and also your running all of the commands through ssh right?

---

### Post by makenbaccon on 2011-05-02
> **sandyd said:**
> ```

sudo apt-get install linux-server [linux-image-2.6.35-28-server]("http://packages.ubuntu.com/maverick/linux-image-2.6.35-28-server")
```also, is this server in question on some web service such as Amazon EC2? Or VPS?
If yes, then ask technical support to upgrade your kernel. Or in the case of Amazon EC2, choose a newer AMI. There are some very annoying VPS providers these days where they don't set proper openvz/xen configurations, and when the kernel of a VPS is upgraded, everything screws up.

and also your running all of the commands through ssh right?
~$ sudo apt-get install linux-server linux-image-2.6.35-28-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-image-2.6.35-28-server
E: Couldn't find any package by regex 'linux-image-2.6.35-28-server'

Didn't quite work. yes, i'm using a vps provider, I don't remember the name though.

---

### Post by sandyd on 2011-05-02
> **makenbaccon said:**
> ~$ sudo apt-get install linux-server linux-image-2.6.35-28-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-image-2.6.35-28-server
E: Couldn't find any package by regex 'linux-image-2.6.35-28-server'

Didn't quite work. yes, i'm using a vps provider, I don't remember the name though.
Then open a support ticket at the VPS provider.
Upgrading kernels on a VPS is not something that you want to do when you don't know if they use customized kernels or not.

---

