---
title: "Installing Clam AV"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by abnordude on 2011-04-30
Now first,
I know you'll tell me that antivirus is not needed for ubuntu.
But I distribute CD's to people. [Most of them using windows].

So I need to have an antivirus.
_______________________________________________________________________________________

SO.
I downloaded clamAv from the official website.
Tis in tar.gz format.
I need to install it.
So, will anyone please give me DETAILED INFORMATION on how to do so?

---

### Post by 3rdalbum on 2011-04-30
Detailed information:

1. Don't download it from the ClamAV website, instead download it from the Ubuntu Software Center. You can do this by opening Software Center and doing a search for "klamav" (so you get a GUI user interface, too). Click the Install button. When it's done, you'll be asked if you want to add it to the Unity launcher, click Yes (if you want it in your Unity launcher; otherwise, click No and you can find KlamAV in your Applications lense).

2. I still fail to see why you need an anti-virus. If your system is Ubuntu, it's not going to transmit viruses to the CDs you burn for the Windows users.

---

### Post by abnordude on 2011-04-30
> **3rdalbum said:**
> Detailed information:

1. Don't download it from the ClamAV website, instead download it from the Ubuntu Software Center. You can do this by opening Software Center and doing a search for "klamav" (so you get a GUI user interface, too). Click the Install button. When it's done, you'll be asked if you want to add it to the Unity launcher, click Yes (if you want it in your Unity launcher; otherwise, click No and you can find KlamAV in your Applications lense).

2. I still fail to see why you need an anti-virus. If your system is Ubuntu, it's not going to transmit viruses to the CDs you burn for the Windows users.

Well, actually.
We're a group who download stuff, mainly softwares and exchange and distribute.
Most of my pals are using windows. And since I use linux, they told me to install an antivirus, as a precaution.
Hence.......

---

### Post by 3rdalbum on 2011-04-30
> **abnordude said:**
> Well, actually.
We're a group who download stuff, mainly softwares and exchange and distribute.
Most of my pals are using windows. And since I use linux, they told me to install an antivirus, as a precaution.
Hence.......

Okay cool. I just wanted to be sure that you weren't afraid of actually contracting viruses on Linux. If you send on files that were infected before you downloaded them, then you could have a detrimental effect on any Windows machines that run them.

---

### Post by VinDSL on 2011-04-30
> **abnordude said:**
> So I need to have an antivirus.[...]
Don't mean to confuse the situation, but...  You might want to consider using Avast!

Linkage:  [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)  (Download the Deb version)

Heh!  As usual, there are a couple of caveats:

Avast! requires a *free* key.

Linkage:  [http://www.avast.com/registration-free-antivirus.php](http://www.avast.com/registration-free-antivirus.php)

If you use Ubuntu Software Center to install the Deb file, it will throw a warning at you.  Ignore the warning and install it anyway.

SHM is set too low in Ubuntu (and many other distros).  To fix this:

[INDENT]Open a terminal
sudo gedit /etc/sysctl.conf
Add kernel.shmmax = 128000000 on the last line.
Save & reboot.[/INDENT]

This is how my /etc/sysctl.conf looks:

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#

**[COLOR="Red"]kernel.shmmax = 128000000[/COLOR]**

```

This is the result:

```

vindsl@Zuul:~$ sysctl -a | grep shm
error: permission denied on key 'kernel.cad_pid'
**[COLOR="Red"]kernel.shmmax = 128000000[/COLOR]**
kernel.shmall = 2097152
kernel.shmmni = 4096
error: permission denied on key 'vm.compact_memory'
error: permission denied on key 'fs.binfmt_misc.register'
vm.hugetlb_shm_group = 0
error: permission denied on key 'dev.parport.parport0.autoprobe'
error: permission denied on key 'dev.parport.parport0.autoprobe0'
error: permission denied on key 'dev.parport.parport0.autoprobe1'
error: permission denied on key 'dev.parport.parport0.autoprobe2'
error: permission denied on key 'dev.parport.parport0.autoprobe3'
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
vindsl@Zuul:~$ 

```

Anyway, it's a little more work, but I think you'll be happier using Avast!  ;)

---

### Post by abnordude on 2011-04-30
I downloaded clamtk from synaptic itself.
The version was out dated.
Well, I updated it.
Thanks everyone.

---

