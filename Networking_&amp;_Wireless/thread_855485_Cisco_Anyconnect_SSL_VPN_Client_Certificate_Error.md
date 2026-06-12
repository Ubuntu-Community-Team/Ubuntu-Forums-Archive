---
title: "Cisco Anyconnect SSL VPN Client Certificate Error"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by SupaRice on 2008-07-10
I have a SSL VPN Connection to a Cisco ASA firewall (v8.03) and from my Ubuntu 7.1 box it works fine.  That box has Firefox 2.4, but my Ubuntu 8.04 box fails to connect, which I'm pretty sure is because the ASA doesn't have a publicly signed cert.  I have installed the cert in Firefox so that it doesn't gripe when I connect to login, but it appears that Java doesn't like the cert.

Where should I start looking to fix this?

:confused:

---

### Post by SupaRice on 2008-07-10
Anybody?

---

### Post by casevh on 2008-07-18
Are your running 32-bit or 64-bit version of Ubuntu?

If you are running 32-bit, do the following:

sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so

If you are running 64-bit, it's a little more complicated. You will need to install 32-bit Firefox and make a few other changes. The following steps work for me, but I'm not using certificates (yet).

1) Install "ia32-libs"
2) Install "lib32nss-mdns"
3) Install 32-bit Firefox. It MUST be installed into the /usr/local/firefox directory.
4) Several files from /usr/local/firefox must be copied or linked to either /usr/lib32 or /opt/cisco/vpn/lib.

libnssutil3.so
libplc4.so
libplds4.so
libnspr4.so
libsqlite3.so
libnssdbm3.so
libfreebl3.so

If this doesn't help, please give the exact error message.

casevh

---

### Post by brianw311 on 2008-07-23
I was having the same issue. I used the above 32bit steps and it resolved the issue. Thanks!

---

### Post by SupaRice on 2008-08-25
Late replying, I'm on 32bit.  It seems to work now, but I don't know what changed.

When I tried your 32bit instructions, it said "File exists" for each. Oh well, it's working.... :confused:

---

### Post by casevh on 2008-08-25
It's possible that you've installed another application that created those links. For example, installing FireFox 2 will create those links.

---

### Post by btmspox on 2008-09-17
> **casevh said:**
> 
3) Install 32-bit Firefox. It MUST be installed into the /usr/local/firefox directory.

What method do you use to do this? Compiling from source would produce another x86_64 binary. Did you download the 32bit deb, unpack it, and move specific files there?

---

### Post by casevh on 2008-09-18
Yes, I actually used firefox-3.0.1.tar.bz2 from mozilla.com.

Let me know if it works for you. I need to support AnyConnect on multiple Linux distributions so I've gotten pretty good at troubleshooting it. It's not fun. :(

casevh

---

### Post by rosv on 2008-09-26
I just can't get the AnyConnect client to work. I followed your advice but without any luck.

Any help is greatly appreciated

thanx
//robert

---

### Post by casevh on 2008-09-26
I haven't seen that error message.

Are you running 32 or 64 bit Ubuntu?

Are there any error messages in /var/log/syslog?

Do you get any more useful errror messages by starting the command line version: /opt/cisco/vpn/bin/vpn?

Hopefully we can get some error messages that help isolate the issue.

casevh

---

### Post by rosv on 2008-09-27
Hi,
I'm using the 32-bit version of 8.04
I get the same error message if I start the client from the command line.
I don't have access to the ubuntu machine right now so I can't post the log out put. Will do that as soon as I'm able to.

---

### Post by rosv on 2008-09-29
Hi,
I', using the 32-bit client. I get the same error message if I run AnyConnect for the command line or the GUI.

This is the output of my syslog:
Sep 29 13:41:53 localhost vpnui: warning - i18n/MsgCatalog.cpp:274 (0) MsgCatalog::setCatalog The message catalog <AnyConnect> is corrupt or could not be found.
Sep 29 13:41:53 localhost vpnui: ClientIfc.cpp:66 (0) vpnapi vpnapi version 2, 1, 0 Initializing.
Sep 29 13:41:53 localhost vpnui: error - Certificates/NSSCertUtils.cpp:301 (ffffe8a7) NSS_Init
Sep 29 13:41:53 localhost vpnui: warning - SDI/SDI.cpp:52 (fe2e0001) CRSASecurIDSDI
Sep 29 13:41:53 localhost vpnui: warning - SDIMgr.cpp:103 (fe2e0001) CSDI::createInstance
Sep 29 13:41:53 localhost vpnui: ClientIfc.cpp:153 (0) ClientIfc :: attach Client successfully attached.
Sep 29 13:42:03 localhost vpnui: warning - ProfileMgr.cpp:302 (0) ProfileMgr :: getHostInitSettings Profile settings not available for testsite.test.intra.
Sep 29 13:42:03 localhost vpnui: warning - ProfileMgr.cpp:302 (0) ProfileMgr :: getHostInitSettings Profile settings not available for testsite.test.intra.
Sep 29 13:42:03 localhost vpnui: error - Certificates/CollectiveCertStore.cpp:326 (fe210005) CCertStore::Enumerate
Sep 29 13:42:03 localhost vpnui: warning - Certificates/CertHelper.cpp:442 (fe21000e) CCertStore::Enumerate
Sep 29 13:42:03 localhost vpnui: error - ApiCert.cpp:113 (fe21000e) CCertStore::Enumerate
Sep 29 13:42:03 localhost vpnui: ConnectMgr.cpp:363 (0) ConnectMgr :: connect Initiating connection to: testsite.test.intra
Sep 29 13:42:03 localhost vpnui: error - Certificates/NSSCertStore.cpp:207 (fe220005) CNSSCertificate::Open
Sep 29 13:42:03 localhost vpnui: error - Certificates/NSSCertStore.cpp:396 (fe220005) OpenCertificate
Sep 29 13:42:03 localhost vpnui: warning - Certificates/CertHelper.cpp:131 (fe220005) CCertStore::VerifyServerCertificate
Sep 29 13:42:03 localhost vpnui: error - ConnectIfc.cpp:551 (fe000022) SendRequestToPeer
Sep 29 13:42:03 localhost vpnui: error - ConnectMgr.cpp:449 (fe000022) ConnectIfc::connect
Sep 29 13:42:03 localhost vpnui: error - ConnectMgr.cpp:586 (0) ConnectMgr :: processIfcData Unrecognized content type (Unknown) received.
Sep 29 13:42:03 localhost vpnui: error - ConnectMgr.cpp:607 (0) ConnectMgr :: processIfcData Unable to process response from testsite.test.intra. 
Sep 29 13:42:03 localhost vpnui: ConnectMgr.cpp:626 (0) ConnectMgr :: processIfcData Connection attempt has failed due to server certificate problem.


Any ideas?

---

### Post by casevh on 2008-09-29
First, let's double-check that vpnagentd is running. It should be listed in the output from "ps -ef | grep vpn". If not, start it with "sudo /etc/init.d/vpnagentd_init start"

The AnyConnect client depends on several libraries distributed by FireFox. The following list of libraries must exist on your system:

libnss3.so
libplc4.so
libnspr4.so
libsmime3.so
libsoftokn3.so
libnssdbm3.so
libfreebl3.so
libnssutil3.so
libplds4.so
libsqlite3.so

Some of these files may have a slightly different name so you will need to create a symbolic link for the names the client is looking for.

If that doesn't help, it gets difficult. You'll need to use the command line version but run it using the strace utility. That will output all the operating system call. Then look for the last series of "not found" messages to see what file it is missing. The command is:

strace /opt/cisco/vpn/bin/vpn connect server_name 2>/tmp/debug.txt

Then look in debug.txt starting from the end and working to the front.

casevh

---

### Post by rosv on 2008-09-29
Hi,
The vpn service is running and all the files you listed are present.

I've attached the output of the strace. It seems like there's a lot of "not founds" in the output file.
I think my problem will be solved if I create symbolic links from wherever the AnyConnect thinks the files are located to where they actually are, no?

For example:
The file libnssdbm3.so is locate at /usr/lib/nss/ but AnyConnect is looking for it at /lib/i686/sse2/cmov/. So a ln -s /usr/lib/nss/libnssdbm3.so /lib/i686/sse2/cmov/ should solve it right?

---

### Post by casevh on 2008-09-29
"not founds" are fairly common. What you need to verify is that each file is eventually found. Typically, several directories are searched before the file is found.

On a 64-bit platform, I've needed to resort to a brute force approach. The AnyConnect client appears to always look in either /opt/cisco/vpn/lib or /usr/local/firefox first. So on 64-bit machines, I've downloaded the firefox binary from mozilla.com, untarred it and placed it in /usr/local/firefox, and then created symbolic links in /opt/cisco/vpn/lib for a few of the files. See a prior post for the names of the files.

What version of the client are you using? I'm currently using 2.2.0136. If you are using an older version, it may not support FireFox 3.0. (Just a guess.)

casevh

---

### Post by rosv on 2008-09-30
I'm using version 2.1. I would love to get my hands on 2.2 for Linux but Cisco do not appear to very keen on giving their software away. I guess you need a partner account at cisco.com to access the latest version

---

### Post by jerich007 on 2008-10-20
Just wanted to say casevh's instructions worked for me on 64-bit Hardy.
[LIST]
[*]I installed the latest AnyConnect client (v.2.2).
[*]Installed latest Firefox3 from [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)
[*]copied the firefox install directory to /usr/local/firefox.
[*]Created the links, as indicated by casevh.
[/LIST]

Now the pesky server certificate error went away.  Instead, I was prompted to acknowledge the self-signed cert presented by my ASA firewall.  Now I'm successfully connected to my network via SSLVPN.

Thanks!
- Jericho

---

### Post by MRDutton on 2008-11-30
I'm running Intrepid 64bit. I just wanted to note that you don't need Firefox 32-bit to get this to work. The libraries that casevh lists can also be found in the 32-bit Intrepid repo's.

The deb's that I got the 32-bit libs from were:
libnspr4-0d
libnss3-1d
libsqlite3-0

(Note: I'm using AnyConnect version 2.2.0140)

This list of files that need symlinks in the /usr/local/firefox directory could probably be paired down if someone gets the time. I haven't got around to it yet.

---

### Post by btmspox on 2008-12-04
I downloaded the 32bit libraries from the deb's from:

[http://packages.ubuntu.com/intrepid/i386/libnspr4-0d/download](http://packages.ubuntu.com/intrepid/i386/libnspr4-0d/download)
[http://packages.ubuntu.com/intrepid/i386/libnss3-1d/download](http://packages.ubuntu.com/intrepid/i386/libnss3-1d/download)
[http://packages.ubuntu.com/intrepid/i386/libsqlite3-0/download](http://packages.ubuntu.com/intrepid/i386/libsqlite3-0/download)

# decompress
```
for deb in `ls *deb` ; do dpkg -x $deb /tmp/cisco ; done
```
# find and copy libraries
```
mkdir /usr/local/firefox
for lib in libnssutil3.so libplc4.so libplds4.so libnspr4.so libsqlite3.so libnssdbm3.so libfreebl3.so libnspr4.so.0d libnss3.so.1d libplc4.so.0d libsmime3.so.1d ; do find /tmp/cisco -name $lib -exec cp '{}' /usr/local/firefox \; ; done
```

```
/usr/local/firefox# file *
libfreebl3.so:   ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnspr4.so:     ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnspr4.so.0d:  ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnss3.so.1d:   ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnssdbm3.so:   ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnssutil3.so:  ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libplc4.so:      ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libplc4.so.0d:   ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libplds4.so:     ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libsmime3.so.1d: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
```

Installing and running 2.2.0140 produces the continual certificate error with an OK button that doesn't do anything, 2.3.0142 (BETA) produces a pop-up that allows you to hit accept but it keeps coming back.

Ubuntu Intrepid 8.10 amd64, recent install.

strace output attached.

---

### Post by btmspox on 2008-12-04
Also tried:

```
tar -xvjf firefox-3.0.4.tar.bz2 -C /usr/local
cd /opt/cisco/vpn/lib
for lib in libnssutil3.so libplc4.so libplds4.so libnspr4.so libsqlite3.so libnssdbm3.so libfreebl3.so ; do ln -s /usr/local/firefox/$lib $lib ; done
file -L *
libcrypto.so.0.9.8: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, not stripped
libfreebl3.so:      ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnspr4.so:        ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnssdbm3.so:      ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libnssutil3.so:     ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libplc4.so:         ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libplds4.so:        ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libsqlite3.so:      ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libssl.so.0.9.8:    ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, not stripped

```

2.2.0140 produces the same certificate error. Debug.txt attached from this run.
This produces

---

### Post by Yoann Juet on 2008-12-07
I've just upgraded to Ubuntu 8.10 (32bits) and notice that AnyConnect version 2.2.0140 doesn't work anymore. I get a certificate error...

VPN> jdoe@aspire:opt/cisco/vpn/bin$ strace ./vpn connect mygateway 2>/tmp/1.txt
Cisco AnyConnect VPN Client (version 2.2.0140).

Copyright (c) 2004 - 2008 Cisco Systems, Inc.
All Rights Reserved.


  >> state: Disconnected
  >> notice: VPN Service is available.
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN>   >> contacting host (mygateway) for login information...
  >> notice: Contacting mygateway.
  >> warning: Unable to process response from mygateway.
  >> error: Connection attempt has failed due to server certificate problem.
  >> state: Disconnected


This issue is solved by adding the following symlink :

sudo ln -s /usr/lib/nss/libnssdbm3.so /usr/lib/libnssdbm3.so

Hope this helps
Regards,

---

### Post by pacmansyu on 2008-12-10
Hello all, I'm running Ubuntu 8.10, 32 bit, installed the vpnagent and started the daemon via sudo /etc/init.d/vpnagentd_init start... it starts fine. When I attempt to run /opt/cisco/vpn/bin/vpn connect xxxx.com, I get the following:

Cisco AnyConnect VPN Client (version 2.2.0140).

Copyright (c) 2004 - 2008 Cisco Systems, Inc.
All Rights Reserved.


  >> warning: No profile is available.  Please enter host to "Connect to".
  >> state: Disconnected
  >> notice: VPN Service is available.
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN> connect xxxxx.com
  >> contacting host (xxxxx.com) for login information...
  >> notice: Contacting xxxxx.com.
  >> notice: Downloading Cisco Secure Desktop ...
VPN> shift: 16: can't shift that many
  >> error: Unable to launch Cisco Secure Desktop. If you are already on the
Secure Desktop, use the "Launch Login Page" button on the desktop.
  >> state: Disconnected
VPN>



.... has anyone seen this (the shift error in particular)? I've run an strace on the command, and found all the calls to various libraries (which seems to be a common issue), but the system is always able to find every lib. Any help is appreciated. Thanks.

---

### Post by casevh on 2008-12-11
I've seen it. ;)

It is a bug in the current production versions of the AnyConnect client and Secure Desktop(*). I've tested the beta releases of the AnyConnect client and Secure Desktop and they do work. At the moment, I've only tested on 32-bit Ubuntu. I will test with 64-bit Ubuntu over the weekend. I will post an update to this thread then.

casevh

(*) Roughly speaking, Secure Desktop is a plugin for the AnyConnect client (or a web browswer) that allows the remote access server to do host scan (checking for firewall and anit-virus software, for example) or provide a very secure web browser environment (i.e. prevent other applications from running at the same time, erase all files from the browswer cache, etc.)

---

### Post by casevh on 2008-12-12
Update: I am able to connect successfully from 32-bit (8.10) and 64-bit (8.04) using Cisco's latest beta AnyConnect client 2.3.0167 and beta Secure Desktop 3.4.0369.

On the 64-bit platform, I needed to add an additional 32-bit library - libcurl.so.4.1.0 - to /usr/lib32.

casevh

---

### Post by btmspox on 2008-12-17
Made another pass on a separate amd64 / x86_64 intrepid workstation and got it working.

**Do not run the 'vpn' or 'vpnui' binaries as root (or via sudo).**

```

# downloaded the latest Linux Anyconnect client from http://www.cisco.com
tar -xvzf anyconnect-linux-2.3.0185-k9.tar.gz
cd ciscovpn/
sudo ./vpn_install.sh 

# Downloaded latest firefox from http://www.mozilla.com/en-US/firefox/
sudo tar -xvjf firefox-3.0.5.tar.bz2 -C /usr/local

for lib in libnssutil3.so libplc4.so libplds4.so libnspr4.so libsqlite3.so libnssdbm3.so libfreebl3.so ; do sudo ln -s /usr/local/firefox/$lib /opt/cisco/vpn/lib/$lib ; done

```

This was with 2.3.0185 with a public signed certificate. I then went back to the [earlier workstation]("http://ubuntuforums.org/showpost.php?p=6304866&postcount=19") and ran 'vpn connect' not as root and it worked as well. That workstation has 2.2.0140 installed.

---

### Post by wanchai on 2009-02-01
Thanks to your postings here, especially casevh, I got my Cisco Annyconnect working as well. I was able to get rid of the certificate error rather quickly, but then the client would tell me that it is connected, but no traffic went through. In the terminal where I launched the agent, I saw some error that looked like "compr!Err" with no further explanation. A look into /var/log/syslog showed that the agent was looking for /usr/lib/libz.so. Another symlink and I was in business.

The only thing that's left is an error
> XmlElement::translateWideToChar - memory leak
that sounds a bit scary. Both clients, vpn and vpnui, produce that. Any idea? I see this with Annyconnect version 2.0.0343 (sorry, my company doesn't have anything more recent and I don't have access to Cisco) running on Jaunty Alpha 3 (32 bit), but also on Gutsy.

---

### Post by dishwishy on 2009-02-21
I am running 64-bit 8.10 and the below instructions worked like a charm. I am using cert based authentication. Thanks to Casevh!:KS



> **casevh said:**
> Are your running 32-bit or 64-bit version of Ubuntu?

If you are running 32-bit, do the following:

sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so

If you are running 64-bit, it's a little more complicated. You will need to install 32-bit Firefox and make a few other changes. The following steps work for me, but I'm not using certificates (yet).

1) Install "ia32-libs"
2) Install "lib32nss-mdns"
3) Install 32-bit Firefox. It MUST be installed into the /usr/local/firefox directory.
4) Several files from /usr/local/firefox must be copied or linked to either /usr/lib32 or /opt/cisco/vpn/lib.

libnssutil3.so
libplc4.so
libplds4.so
libnspr4.so
libsqlite3.so
libnssdbm3.so
libfreebl3.so

If this doesn't help, please give the exact error message.

casevh

---

### Post by unk626 on 2009-04-11
Here's the error I'm seeing after following the advice above:

sergio@lenobo:~$ /opt/cisco/vpn/bin/vpn connect [ip address]
Cisco AnyConnect VPN Client (version 2.3.0254) .

Copyright (c) 2004 - 2009 Cisco Systems, Inc.
All Rights Reserved.


  >> state: Disconnected
  >> warning: No profile is available.  Please enter host to "Connect to".
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN>   >> contacting host (*.*.*.*) for login information...
  >> notice: Contacting *.*.*.*
VPN> 
  >> Please enter your username and password.

Username: [*****] *****
Password: 
  >> notice: Establishing VPN - Checking for updates...
  >> state: Connecting
VPN> /bin/sh: Can't open /tmp/vpnnspZL3/vpndownloader.sh
  >> error: Unable to establish VPN.
  >> state: Disconnected

From Syslog:

Apr 11 05:47:32 lenobo vpn: [p:29153  pp:26307]: ConnectMgr.cpp:1128 (0) processIfcData Authentication succeeded
Apr 11 05:47:32 lenobo vpn: [p:29153  pp:26307]: warning - ConnectIfc.cpp:1178 (0) ConnectIfc::getUpdateFileContent Unable to locate Update file
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: warning - ConnectIfc.cpp:1009 (0) ConnectIfc::getDownloader Unable to locate downloader
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: ConnectMgr.cpp:4443 (0) ConnectMgr :: launchdownloader Successfully downloaded the downloader
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: ConnectMgr.cpp:4495 (0) ConnectMgr :: launchdownloader Successfully launched the downloader
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: error - ConnectMgr.cpp:4512 (2) ProcessApi :: WaitForProcess Downloader terminated abnormally



I've tried using 2.3.0185 and 0254


Any ideas?

---

### Post by wanchai on 2009-04-11
Sergio, do you have the option to use a Web SSL? Does that work for you?

I had a similar problem not too long ago. What happened was that the company changed the Anyconnect version on the switch and they provided only the Windows client on their side. The clients that can be downloaded from the switch need to be installed somehow. When I tried to use the command line VPN I saw messages just like yours. When I logged in to the Web SSL VPN and tried to download the client from there it became very obvious that the Linux client was missing on the switch.

---

### Post by casevh on 2009-04-14
Wanchai is correct. In addition to installing the AnyConnect client on your computer, a similar version needs to be installed on the Cisco ASA box. When you connect via Web SSL and the AnyConnect client is not available for download, then it is not installed on the Cisco ASA. I found out the hard way when I tested a new version of AnyConnect on my computer before installing on the ASA.

casevh

---

### Post by sungtakdh on 2009-04-16
> **unk626 said:**
> Here's the error I'm seeing after following the advice above:

sergio@lenobo:~$ /opt/cisco/vpn/bin/vpn connect [ip address]
Cisco AnyConnect VPN Client (version 2.3.0254) .

Copyright (c) 2004 - 2009 Cisco Systems, Inc.
All Rights Reserved.


  >> state: Disconnected
  >> warning: No profile is available.  Please enter host to "Connect to".
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN>   >> contacting host (*.*.*.*) for login information...
  >> notice: Contacting *.*.*.*
VPN> 
  >> Please enter your username and password.

Username: [*****] *****
Password: 
  >> notice: Establishing VPN - Checking for updates...
  >> state: Connecting
VPN> /bin/sh: Can't open /tmp/vpnnspZL3/vpndownloader.sh
  >> error: Unable to establish VPN.
  >> state: Disconnected

From Syslog:

Apr 11 05:47:32 lenobo vpn: [p:29153  pp:26307]: ConnectMgr.cpp:1128 (0) processIfcData Authentication succeeded
Apr 11 05:47:32 lenobo vpn: [p:29153  pp:26307]: warning - ConnectIfc.cpp:1178 (0) ConnectIfc::getUpdateFileContent Unable to locate Update file
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: warning - ConnectIfc.cpp:1009 (0) ConnectIfc::getDownloader Unable to locate downloader
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: ConnectMgr.cpp:4443 (0) ConnectMgr :: launchdownloader Successfully downloaded the downloader
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: ConnectMgr.cpp:4495 (0) ConnectMgr :: launchdownloader Successfully launched the downloader
Apr 11 05:47:33 lenobo vpn: [p:29153  pp:26307]: error - ConnectMgr.cpp:4512 (2) ProcessApi :: WaitForProcess Downloader terminated abnormally



I've tried using 2.3.0185 and 0254


Any ideas?
I got the same error messages, but solved/worked around it by setting the right permission on vpndownloader.sh:

cd /opt/cisco/vpn/bin
sudo chmod +x vpndownloader.sh

Hope this helps!

---

### Post by rcsheets on 2009-06-23
I'm also getting this message:

VPN> /bin/sh: Can't open /tmp/vpnhtjJJI/vpndownloader.sh

But the /opt/cisco/vpn/bin/vpndownloader.sh file is already executable.

---

### Post by crobitaille on 2009-06-26
I am also on 8.10. I got the package from the ASA server so it should be in synch. with whatever is in the server. I am with the lastest FIreFox (3.0.11). I get the infamous empty certificate "Accept" request:


Cisco AnyConnect VPN Client (version 2.3.0254) .

Copyright (c) 2004 - 2009 Cisco Systems, Inc.
All Rights Reserved.


  >> state: Disconnected
  >> warning: No profile is available.  Please enter host to "Connect to".
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN>   >> contacting host (XXXXXXX) for login information...
  >> notice: Contacting XXXXXXXX.
  >> warning: Unable to process response from XXXXXXXX.
  >> notice: Please respond to Server Certificate Acceptance Request.
VPN> 
Warning: The following Certificate received from the Server could not be verified:


accept? [y/n]: 


I did an strace as recommended. Looking at all the opens, I find that all the libraries mentioned in this thread are accessible (I did the various required ln -s) except for libc.mo

Any sggestion on where to look?

Thanks



> **pacmansyu said:**
> Hello all, I'm running Ubuntu 8.10, 32 bit, installed the vpnagent and started the daemon via sudo /etc/init.d/vpnagentd_init start... it starts fine. When I attempt to run /opt/cisco/vpn/bin/vpn connect xxxx.com, I get the following:

Cisco AnyConnect VPN Client (version 2.2.0140).

Copyright (c) 2004 - 2008 Cisco Systems, Inc.
All Rights Reserved.


  >> warning: No profile is available.  Please enter host to "Connect to".
  >> state: Disconnected
  >> notice: VPN Service is available.
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN> connect xxxxx.com
  >> contacting host (xxxxx.com) for login information...
  >> notice: Contacting xxxxx.com.
  >> notice: Downloading Cisco Secure Desktop ...
VPN> shift: 16: can't shift that many
  >> error: Unable to launch Cisco Secure Desktop. If you are already on the
Secure Desktop, use the "Launch Login Page" button on the desktop.
  >> state: Disconnected
VPN>



.... has anyone seen this (the shift error in particular)? I've run an strace on the command, and found all the calls to various libraries (which seems to be a common issue), but the system is always able to find every lib. Any help is appreciated. Thanks.

---

### Post by ctothej on 2009-07-13
Thanks everyone. A combination of all the above comments got this working for me on Fedora 10. You guys rock, thanks.

I attached a text file that has the instructions that worked for me.

---

### Post by washakie on 2009-07-13
Casevh and btmspox, thank you!

These instructions ultimately worked perfectly for Jaunty 9.04 with AnyConnect 2.3.0254

WTF Cisco? Couldn't they make it a little easier?


> **btmspox said:**
> Made another pass on a separate amd64 / x86_64 intrepid workstation and got it working.

**Do not run the 'vpn' or 'vpnui' binaries as root (or via sudo).**

```

# downloaded the latest Linux Anyconnect client from http://www.cisco.com
tar -xvzf anyconnect-linux-2.3.0185-k9.tar.gz
cd ciscovpn/
sudo ./vpn_install.sh 

# Downloaded latest firefox from http://www.mozilla.com/en-US/firefox/
sudo tar -xvjf firefox-3.0.5.tar.bz2 -C /usr/local

for lib in libnssutil3.so libplc4.so libplds4.so libnspr4.so libsqlite3.so libnssdbm3.so libfreebl3.so ; do sudo ln -s /usr/local/firefox/$lib /opt/cisco/vpn/lib/$lib ; done

```

This was with 2.3.0185 with a public signed certificate. I then went back to the [earlier workstation]("http://ubuntuforums.org/showpost.php?p=6304866&postcount=19") and ran 'vpn connect' not as root and it worked as well. That workstation has 2.2.0140 installed.

---

### Post by rolls20s on 2009-07-23
> **washakie said:**
> 

WTF Cisco? Couldn't they make it a little easier?


lol. Ever wonder why so many sentences begin with, "WTF Cisco??!!"

But, to be fair, Cisco says that they only support the 32bit version of Ubuntu, probably for this very reason.  That's not a defense, it's just a "can't say they didn't warn you" kind of thing.  They really do need to get on the ball though, because Ubuntu isn't the only OS stricken with this issue, and eventually they'll all be 64bit.  It was a dumb move to make it rely on libraries that may not reliably exist in the necessary form/location.  

Thanks for all those contributing on this thread. Helped us out a bunch.

---

### Post by shemtovo on 2009-08-02
hi,

i tried all the tips above, and put all the liberys in place and still nothing. im using version 2.3.2010 and when i try to connect i get that error:

Warning: The following Certificate received from the Server could not be verified:

and that's it.
any idea?

---

### Post by ivrhall on 2009-10-09
Hi everyone,

I tried every permutation of solutions I found for this problem in these forums and elsewhere and did not have any luck. However, I found a very simple solution. I gave up on using Firefox to make my SSL VPN connection. Instead I use Opera. Worked first time, right out of the box. Opera has a .deb of their current version browser available for download. I still have Firefox and still use it, but for making my SSL VPN connection I launch Opera and I'm in. First time every time. Plus the Opera browser rocks.

---

### Post by ajnachakra on 2009-10-20
> **casevh said:**
> Are your running 32-bit or 64-bit version of Ubuntu?

If you are running 32-bit, do the following:

sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so

If you are running 64-bit, it's a little more complicated. You will need to install 32-bit Firefox and make a few other changes. The following steps work for me, but I'm not using certificates (yet).

1) Install "ia32-libs"
2) Install "lib32nss-mdns"
3) Install 32-bit Firefox. It MUST be installed into the /usr/local/firefox directory.
4) Several files from /usr/local/firefox must be copied or linked to either /usr/lib32 or /opt/cisco/vpn/lib.

libnssutil3.so
libplc4.so
libplds4.so
libnspr4.so
libsqlite3.so
libnssdbm3.so
libfreebl3.so

If this doesn't help, please give the exact error message.

casevhaccept? [y/n]:



When I tried to make those symbolic links it told me they alrady existed. I did it anyway and I am still getting "Warning: The following Certificate received from the Server could not be verified:" over and over again despite accepting it every tme. Using Cisco AnyConnect 2.3.0254 and 32-bit Jaunty (same thing happens in the Fedora Core 2 box i had lying around). 

Any suggestions? 
Thanks!

---

### Post by washakie on 2009-10-24
Man! 

I just installed Karmic, clean. I followed the previous instructions we've all mostly gotten to work, but so far .... there's a NEW CATCH!

Since now Ubuntu ships with firefox 3.5, and I couldn't seem to find an older 32bit version of firefox to download from mozilla, it's important to keep your older /usr/local/firefox folder in tact, so you can install it to your new machine.

So basically, as before:
1) follow the instructions I reference in a previous post: [#35]("http://ubuntuforums.org/showpost.php?p=7611316&postcount=35")
2) copy over your old /usr/local/firefox directory to you new machine

The second step doesn't seem to hurt the existing firefox installation, but.. let's just say, it doesn't seem such a good idea. "Thanks Cisco".

Good luck.

---

### Post by ukchucktown on 2009-10-27
I'm working this problem on Karmic. I wasn't sure if you needed the Firefox 3.0.x libraries. I thought it might work with the 3.5 libraries but so far I keep getting errors from Anyconnect cpp files in my system log. You actually don't need to copy the libs from an old install. Most firefox versions are available via ftp. I linked the address for the latest 3.0.14 Linux version.

[ftp://ftp.mozilla.org/pub/firefox/releases/latest-3.0/linux-i686/en-US/]("ftp://ftp.mozilla.org/pub/firefox/releases/latest-3.0/linux-i686/en-US/")

---

### Post by ukchucktown on 2009-10-27
I also tried Anyconnect on Karmic 32 and 64 release candidates. The old workaround never worked. I installed the libraries from Firefox 3.0.14 (same ones I have on Jaunty that work fine) in /usr/local/firefox, created the symbolic links to /opt/cisco/vpn/lib and it fails with the errors shown below in the log. I also tried installing Opera and that did work the first time I tried it. It's failing now so no real solution yet for 9.10.

Oct 27 04:31:07 vpn: [p:2556  pp:1985]: error - ConnectIfc.cpp:362 (fe01002e) ConnectIfc::connect Send request to peer failed
Oct 27 04:31:07 vpn: [p:2556  pp:1985]: error - ConnectIfc.cpp:2953 (fe01002e) ConnectIfc::TranslateStatusCode timeout
Oct 27 04:31:07 vpn: [p:2556  pp:1985]: error - ConnectMgr.cpp:869 (fe01002e) ConnectIfc::connect
Oct 27 04:31:07 vpn: [p:2556  pp:1985]: error - ConnectMgr.cpp:1002 (fe000009) ConnectMgr :: processIfcData Unrecognized content type (Unknown) received.
Oct 27 04:31:07 vpn: [p:2556  pp:1985]: error - ConnectMgr.cpp:1024 (fe000009) ConnectMgr :: processIfcData Unable to process response from ...
Oct 27 04:31:07 vpn: [p:2556  pp:1985]: error - ConnectMgr.cpp:1078 (fe000009) processIfcData Unable to contact ...

---

### Post by casevh on 2009-10-28
I just installed 64-bit Karmic and have the AnyConnect client running properly. I followed these steps. (They also work for 9.04 64-bit.)

Install, or verify they are installed, the following packages:
   1) ia32-libs
   2) lib32nss-mdns
   3) libcurl3
   4) libxml2

Create the directory /usr/local/firefox and create symlinks for the following files: /usr/lib32/libnss3.so, /usr/lib32/libplc4.so, /usr/lib32/libnspr4.so, /usr/lib32/libsmime3.so, and /usr/lib32/nss/libsoftokn3.so.

You may need to reboot or run ldconfig so the symlinked libraries can be found.

```
sudo apt-get install ia32-libs lib32nss-mdns libcurl3 libxml2
cd /usr/local
sudo mkdir firefox
cd firefox
sudo ln -s /usr/lib32/libnss3.so
sudo ln -s /usr/lib32/libplc4.so
sudo ln -s /usr/lib32/libnspr4.so
sudo ln -s /usr/lib32/libsmime3.so
sudo ln -s /usr/lib32/nss/libsoftokn3.so
sudo ldconfig
```

Then just untar the AnyConnect client file and run

```
sudo sh ./vpn_install.sh

```

The GUI client is automatically installed under Applications -> Internet.

casevh

---

### Post by ukchucktown on 2009-10-28
Those steps did not work correctly for me personally. Step by step this is what I did to install the latest Anyconnect under Kubuntu 9.10. I finally got this working with the 2.4.0202 client from Cisco and Karmic 64-bit updated today. Cisco should try harder to support 64-bit Linux in their products.

Here are the steps...

1. Install Anyconnect (vpnsetup.sh)
2. Download getlibs-all.deb (Google it) and install with dpkg -i getlibs-all.deb
3. Install missing libraries with getlibs /opt/cisco/vpn/lib
4. Install sqlite3 with getlibs libsqlite3.so.0
5. Create directory /usr/local/firefox
6. Change directory to /usr/local/firefox and create symbolic links.
```

# ln -s /usr/lib32/libnss3.so
# ln -s /usr/lib32/libplc4.so
# ln -s /usr/lib32/libnspr4.so
# ln -s /usr/lib32/libsmime3.so

```
7. Reinstall Anyconnect (vpnsetup.sh)
8. Connect

---

### Post by biggsjm on 2010-02-10
Those steps worked for me, however, I received the following two errors now!

Posture Assessment: Failed

and

Hostscan Run error.

---

### Post by biggsjm on 2010-02-10
Ok, not sure what I did, but I closed out the AnyConnect client and ran it again, and those errors went away. Try re-installing AnyConnect to correct those errors if you run into them.

---

### Post by octoberdan on 2010-05-19
> **btmspox said:**
> Made another pass on a separate amd64 / x86_64 intrepid workstation and got it working.

**Do not run the 'vpn' or 'vpnui' binaries as root (or via sudo).**

```

# downloaded the latest Linux Anyconnect client from http://www.cisco.com
tar -xvzf anyconnect-linux-2.3.0185-k9.tar.gz
cd ciscovpn/
sudo ./vpn_install.sh 

# Downloaded latest firefox from http://www.mozilla.com/en-US/firefox/
sudo tar -xvjf firefox-3.0.5.tar.bz2 -C /usr/local

for lib in libnssutil3.so libplc4.so libplds4.so libnspr4.so libsqlite3.so libnssdbm3.so libfreebl3.so ; do sudo ln -s /usr/local/firefox/$lib /opt/cisco/vpn/lib/$lib ; done

```

This was with 2.3.0185 with a public signed certificate. I then went back to the [earlier workstation]("http://ubuntuforums.org/showpost.php?p=6304866&postcount=19") and ran 'vpn connect' not as root and it worked as well. That workstation has 2.2.0140 installed.

This was the solution, thank you! I got this running on 64-bit UbuntuStudio (Lucid) with Cisco AnyConnect VPN Client (version 2.4.1012) and Mozilla Firefox 3.6.3. I was using the CLI client and had no idea it cared about Firefox libraries!

Cheers!

---

### Post by llsecurity on 2010-05-23
This process worked for me on Ubuntu 10.04 64bit.

> **ukchucktown said:**
> Those steps did not work correctly for me personally. Step by step this is what I did to install the latest Anyconnect under Kubuntu 9.10. I finally got this working with the 2.4.0202 client from Cisco and Karmic 64-bit updated today. Cisco should try harder to support 64-bit Linux in their products.

Here are the steps...

1. Install Anyconnect (vpnsetup.sh)
2. Download getlibs-all.deb (Google it) and install with dpkg -i getlibs-all.deb
3. Install missing libraries with getlibs /opt/cisco/vpn/lib
4. Install sqlite3 with getlibs libsqlite3.so.0
5. Create directory /usr/local/firefox
6. Change directory to /usr/local/firefox and create symbolic links.
```

# ln -s /usr/lib32/libnss3.so
# ln -s /usr/lib32/libplc4.so
# ln -s /usr/lib32/libnspr4.so
# ln -s /usr/lib32/libsmime3.so

```
7. Reinstall Anyconnect (vpnsetup.sh)
8. Connect

---

### Post by dwmw2 on 2010-05-24
Ubuntu has proper native support for the AnyConnect VPN. Just install the openconnect and network-manager-openconnect packages. Then after a reboot you should be able to configure the VPN and connect using NetworkManager.

There's no need to mess around trying to get Cisco's own VPN client to work.

---

### Post by Cavillis on 2010-05-25
I got this working on 64bit 10.04 following the steps above.

Your mentioning of OpenConnect piqued my interest, I would love to use a more integrated and better supported client for Ubuntu however I could not get it to work.

To connect a new device, I have to login with vpn, and present a one time challenge password. This functionality didn't seem to work with openconnect and I would love some tips on getting it working.

---

### Post by dwmw2 on 2010-08-31
Cavillis, sorry for the delayed response. I don't spend much time trawling random web fora -- I usually expect people to come to the openconnect-devel mailing list if they need help.

Did you get openconnect working? Please send email if you still need help with it. It ought to work fine.

---

### Post by makonyy15 on 2011-06-14
> **dwmw2 said:**
> Ubuntu has proper native support for the AnyConnect VPN. Just install the openconnect and network-manager-openconnect packages. Then after a reboot you should be able to configure the VPN and connect using NetworkManager.

There's no need to mess around trying to get Cisco's own VPN client to work.

I was having all kinds of problems with AnyConnect and no solution until I saw this. Worked perfectly for one network that was giving me mild problems. Going to try it on my home network that was giving me the most problems and hopefully everything is fixed. Thanks for the help!

---

### Post by oneiric on 2011-07-03
For all who visit this thread:

--You do not need to install 32-bit Firefox or libs32
--You do not need to download or install the Cisco client, from their website or your IT provider
--You do not have to learn how to use x11vnc


Just
 

sudo apt-get install openconnect
sudo apt-get install network-mananger-openconnect-gnome


then go to "network manager " icon, which is located by the date and time in the upper right corner.

click "VPN Connections", choose "Configure VPN..."

Select the VPN tab

Click "Add"

When prompted to choose a VPN connection type, use Cisco Anyconnect compatible vpn (openconnect).

click "create"

Give it a connection name (e.g. Myvpn, or it can be anything)

Put the gateway name (e.g. vpnserver.company.com) 

click "Apply",  then "Close" Network connections


Go to "network manager" icon, in the upper right. 

click "VPN Connections", choose "Myvpn"

---

### Post by deepaknet on 2011-08-27
The OpenConnect was working till last week and from yesterday it is failing. The following is the output. Can someone help please?

Attempting to connect to 68.xx:443
SSL negotiation with 68.xx
Connected to HTTPS on 68.xx
GET [https://68.xx/](https://68.xx/)
GET [https://68.xx/+webvpn+/index.html](https://68.xx/+webvpn+/index.html)
Please enter your username and password.
USERNAME:corpssl
Password:
POST [https://68.xx/+webvpn+/index.html](https://68.xx/+webvpn+/index.html)
Error fetching HTTPS response
SSL negotiation with 68.xx
Connected to HTTPS on 68.xx
Error fetching HTTPS response
Creating SSL connection failed

---

### Post by dwmw2 on 2011-09-29
> **deepaknet said:**
> The OpenConnect was working till last week and from yesterday it is failing. The following is the output. Can someone help please?


I'll say it again, although I already said it earlier in this thread: 
 YOU NEED TO POST ISSUES LIKE THIS TO THE [EMAIL="openconnect-devel@lists.infradead.org"]openconnect-devel@lists.infradead.org[/EMAIL] MAILING LIST.

I do not spend my time trawling random web forums. Not very often, at least :)

I think this is already fixed in OpenConnect 3.12. Not sure if Ubuntu has update their package yet; I know Fedora has. Please try the latest version and send email to the mailing list if it fails.

---

