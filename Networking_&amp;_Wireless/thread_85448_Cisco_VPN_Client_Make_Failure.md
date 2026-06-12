---
title: "Cisco VPN Client Make Failure"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by jdgiotta on 2005-11-02
I'm getting a number of errors with the vpnclient install.
Basically, a dozen or so missing files.

Is there something I'm over looking?

---

### Post by ape on 2005-11-02
You need to make sure you have both the kernel-source package installed for the kernel you are running as well as the kernel headers package for the kernel you are running.

On top of this, after installing the kernel source package, you need to go into the directory as root and run the `make` command.  You don't have to let this run all the way through the build, just enough to get the bootstrap scripts created.  You can then Ctrl-C out of the make command (after you see 20-30 lines of input go by you should be safe).

Once you've done this, retry the build of the VPN client.

---

### Post by miras on 2005-11-02
I can recommend vpnc (vpn for cisco). In my experience it works a lot better than Cisco's client. There is also a kde version available but I have never tried that. I best of all: It is available i universe so no compilation is required.
[http://www.yellowpigs.net/index.php?topic=computers/vpn](http://www.yellowpigs.net/index.php?topic=computers/vpn)

One note: If your group password is hashed you need to go to this page to have it decrypt - vpnc only accepts the ascii password.

---

### Post by miras on 2005-11-02
[QUOTE=miras]
One note: If your group password is hashed you need to go to this page to have it decrypt - vpnc only accepts the ascii password.[/QUOTE]

Sorry, forgot the link: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

---

### Post by jdgiotta on 2005-11-03
> I can recommend vpnc (vpn for cisco). In my experience it works a lot better than Cisco's client. There is also a kde version available but I have never tried that. I best of all: It is available i universe so no compilation is required.
Story of my life, I can't download  vpnc-0.3.3.tar.gz from [http://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.3.3.tar.gz](http://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.3.3.tar.gz)

I get a timeout.

---

### Post by miras on 2005-11-03
[QUOTE=jdgiotta]Story of my life, I can't download  vpnc-0.3.3.tar.gz from [http://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.3.3.tar.gz](http://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.3.3.tar.gz)

I get a timeout.[/QUOTE]
Why not: apt-get install vpnc? It is in universe

---

### Post by mlomker on 2005-11-03
> Is there something I'm over looking?

Should be just a matter of

```

sudo apt-get install linux-headers-$(uname -r) gcc-3.4

```

If you get errors after that then post them.  I've never found vpnc very easy to use when compared to cisco's client.

---

### Post by jdgiotta on 2005-11-04
This might be a problem.
> Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [8 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 70.3kB in 2s (23.9kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)


---

### Post by mlomker on 2005-11-04
[QUOTE=jdgiotta]This might be a problem.[/QUOTE]

I'd recommend using [one of the mirrors]("http://wiki.ubuntu.com/Archive") instead.  The main US mirror has more than its share of this.

---

### Post by jdgiotta on 2005-11-04
Thanks mlomker.

New problem, I get a message from vpnc
"binding to port 500: Permission Denied"

---

### Post by mlomker on 2005-11-04
> New problem, I get a message from vpnc "binding to port 500: Permission Denied"

I don't use vpnc.  My general advice with permissions errors would be to try running it with **sudo** or **gksudo** and see if that resolves it.

---

### Post by miras on 2005-11-04
[QUOTE=jdgiotta]Thanks mlomker.

New problem, I get a message from vpnc
"binding to port 500: Permission Denied"[/QUOTE]
This message tells you that the program needs to be run with root privileges in which case you should use sudo.

Reason: The program wants to bind to port 500 and every port < 1025 are privileges ports which only root are allowed to bind to.

---

### Post by jdgiotta on 2005-11-04
> This message tells you that the program needs to be run with root privileges in which case you should use sudo.

Reason: The program wants to bind to port 500 and every port < 1025 are privileges ports which only root are allowed to bind

Thanks miras, I did happen to figure this out.

---

### Post by UphillSkier on 2005-11-17
I've never tried to build a debian kernel.  Can you be more specific about the directory to run make from? 

I downloaded the kernel source package from synaptic, untarred it, cd'd to the kernel directory and tried make, only to bomb like this

```

root@grumpy:/usr/src/linux-source-2.6.12/kernel# make
make: *** No rule to make target `.config', needed by `/config_data.gz'.  Stop.
```

I would appreciate any suggestions:confused:

---

