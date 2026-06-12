---
title: "HOW TO: Connect to VPN with vpnc and Hybrid IKE Authorization"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by brommage on 2008-05-29
If you're like me (and I hope you're not), you enjoy the ability to connect to the VPN server at the university to do research.  After days of searching the web (and some runaround from the "help" desk at the university), I was able to configure vpnc to work with my VPN server at the University of South Florida.  I begin with general instructions, and provide some USF specific instructions below.

[CENTER]*_Do I need this?!?_*[/CENTER]

Symptom 1: Check your .pcf file provided by your institution. If you see the following lines:

```
AuthType=5
CertStore=1
```

Then you need to do this.

Symptom 2: If you think you have everything configured properly, but you keep getting the nagging "No response from target" message, this may also apply.


Symptom 3: You are a USF student or faculty trying to connect.  See below.

If any or all of these apply, then you need Hybrid IKE authorization.  It's not too much trouble, but it requires you to compile vpnc from source.  The package in the repository will not work.

[CENTER]*_General Directions_*[/CENTER]

1. Download the source code from [http://packages.debian.org/source/testing/vpnc]("http://packages.debian.org/source/testing/vpnc")

2. Extract the files from the tarball in any directory which you have access (I picked /home).

3. Open the Makefile from the package in a text editor

4.  Find the following lines of code in the file:
```

# Comment this in to obtain a binary with certificate support which is
# GPL incompliant though.
# OPENSSL_GPL_VIOLATION = -DOPENSSL_GPL_VIOLATION
# OPENSSLLIBS = -lcrypto
```

Uncomment (remove the pound signs) the last two lines.  It should look like this:

```

# Comment this in to obtain a binary with certificate support which is
# GPL incompliant though.
OPENSSL_GPL_VIOLATION = -DOPENSSL_GPL_VIOLATION
OPENSSLLIBS = -lcrypto
```

5. Compile the package
```

sudo ./make
```

Make sure you have the following packages installed before you compile:

debhelper (>= 4.0.0)
dpatch
libgcrypt11-dev 

6. When it is finished compiling, install.

```
sudo make install
```

7.  You will now need to edit the /etc/vpnc/default.conf file to correspond to the settings provided by your institution

```
sudo gedit /etc/vpnc/default.conf
```

Here it is in general.
```

# /etc/vpnc/default.conf
IPSec gateway **1.2.3.4**
IPSec ID **Group ID**
IPSec secret **password**
Xauth username **USERNAME**
Xauth password **password1**
IKE Authmode hybrid
CA-File **/location/of/certificate/rootcert**
```

Replace the boldface terms with the info from your .pcf file provided by your institution (it is helpful to install the Windows based VPN program to get these files).  For USF specific instructions, see below.

You can safely omit listing your username and password.  If you do, vpnc will prompt you for them when it tries to connect.

You need a cleartext group password.  If your password is encrypted (it's a long hexidecimal string), plug it in to the following webform to decrypt it: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode]("http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode")

Any info you need is available in the .pcf file provided by your institution.  If not, call tech support and ask.

8.  Connect!

```
sudo vpnc
```

[CENTER]*_Optional: GUI for VPNC_*[/CENTER]

You can patch the network-manager-vpnc package to easily connect with a few mouse clicks.  See [https://launchpad.net/~sroecker/+archive]("https://launchpad.net/~sroecker/+archive") to download the deb.  Or, add the following repositories to your /etc/apt/sources.list

```
deb http://ppa.launchpad.net/sroecker/ubuntu hardy main
deb-src http://ppa.launchpad.net/sroecker/ubuntu hardy main
```

And let synaptic do the work for you!  You want to import your windows-based pcf file and the certificate, but it's super easy!



[CENTER]*_For those on the USF network_*[/CENTER]

Here are the relevant settings for USF students and faculty:

```
# /etc/vpnc/default.conf
# Based on University of South Florida.pcf
IPSec gateway 131.247.250.33
IPSec ID USF-Hybrid
IPSec secret Hcaimms!
Xauth username **email address**
Xauth password **password**
IKE Authmode hybrid
CA-File /home/tom/.wine/drive_c/temp/USF/rootcert
```

I had installed the Windows VPN client to try it out with WINE.  It did not work, but I was able to use it to point easily to the certificate. You may want to do so also.  Not that the location of your certificate may vary (unless your username happens also to be "tom").

Enjoy!

---

