---
title: "Synaptic Opens ...  and closes"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by expatCM on 2009-02-04
What happens is that Synaptic opens and gives a message saying that something is incomplete and to run dpkg --configure -a   Synaptic then quickly closes.

So I run sudo dpkg --configure -a

The command does not run.  It gives an error

> dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

There are quite a lot of instances of this error in google but there does not appear to be any cause / solution identified.

I then run sudo apt-get update and it is uneventful apart from the end when about seven lines similar to the following are reported

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

I do not know what has caused this since I tend to install updates as they arrive.  I was wondering how to fix it?

---

### Post by apjone on 2009-02-04
Have you added any new software repos lately?

---

### Post by expatCM on 2009-02-04
Yes I have .....  this one ........

> deb [http://debian.vogelweith.com/](http://debian.vogelweith.com/) intrepid zgegthemes # Themes of ZgegBlog

---

### Post by apjone on 2009-02-04
Ok just found this, hope it helps

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)
and
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by expatCM on 2009-02-04
The screencast is quite a nice presentation ….  it explains what is going on and why.  The only problem there is that it works on the basis of adding a new item rather than fixing problems with what is there.

However …...  the rest of the link does explain how to find and add keys to existing repositories …...  so that part of the problem I have solved …...  thank you for your information :)

This has now helped to surface the issue which appears to be that libxine1-bin is duplicated and has a problem …..

My approach was to run the following but I did not like the look of what was about to be removed and so aborted.
> 
sudo apt-get remove libxine1-bin

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  openoffice.org-java-common python2.4-minimal vamps libmozjs0d

Use 'apt-get autoremove' to remove them.

The following packages will be REMOVED:

  gxine gxineplugin k9copy libxine1 libxine1-bin libxine1-console

  libxine1-ffmpeg libxine1-gnome libxine1-misc-plugins libxine1-x mandvd

  totem-xine xine-ui

0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.

After this operation, 21.5MB disk space will be freed.

Do you want to continue [Y/n]? n

Abort.


I then ran sudo apt-get update followed by sudo apt-get upgrade and ….  no errors are reported which I find to be a total mystery....... At this point I do not know whether the problem is solved or not.....  but if not, where it has gone

---

### Post by apjone on 2009-02-06
Hey good to hear and thanks for posting your solution!!! I am sure it will help others who run across this!

---

### Post by forger on 2009-02-07
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by expatCM on 2009-02-07
That looks like a very interesting script forger.  I will try it out on Monday :)   Thanks for making the post.

---

### Post by forger on 2009-02-07
Let me know if anything doesn't work as expected :)

---

### Post by expatCM on 2009-02-10
Hi forger,  I have run the script on two machines with two very different results.

On the first machine it ran very well …..  detected all the keys and downloaded and installed as required.  No problems at all …....  very very good :)

On the second machine it was not so good.  The script ran and got to the point where the message was “Will retrieve keys for ….......”  and then “Attempting to get Launchpad key for ….......” for each entry on a new line.

The problem is that is all it did.  The process terminated and returned a command prompt without doing any more.  I then ran sudo apt-get update and confirmed that keys were still missing.

I thought that perhaps this may be to do with having added a proxy to /etc/apt/apt.conf.d and so I commented the line out but after rebooting I tested and found that this did not result in any change.  So ..  I know that there is a problem but I am not sure what it is …......

---

### Post by forger on 2009-02-10
The script doesn't take care the /etc/apt/sources.list.d/* files unfortunately.

Can you post the output of these commands (in terminal):
```
cat /etc/apt/sources.list
perl -v

```
Also try the script again, and post the full output?

It might be a different PPA link, the regular expression to detect the link is:
```
^deb(?:-src)?\s+http://ppa.launchpad.net/(\S+)/ubuntu
```
In short, it detects a line that begins with "deb" or "deb-src" then spaces (one or more) and then gets the username between "http://ppa.launchpad.net/" and "/ubuntu".

Thanks for trying it out!

---

### Post by expatCM on 2009-02-10
thank you for following through, I hope the following helps ...

cat /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
#
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
#
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
#
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
#
## Medibuntu
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
#
#  Open Office
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
#
#  Wine
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu intrepid main
#
#  Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
#
#  VLC
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu intrepid main
#
#  Scan2pdf
deb http://ppa.launchpad.net/jeffreyratcliffe/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/jeffreyratcliffe/ppa/ubuntu intrepid main
#
# Ubuntu Tweak
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu intrepid main
#
# Google
deb http://dl.google.com/linux/deb/ stable non-free
#
# Gnome-Do
deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main
#
# Mozilla
deb http://ppa.launchpad.net/mozillateam/ppa/ubuntu intrepid main universe
#
# Network Manager
deb http://ppa.launchpad.net/network-manager/ppa/ubuntu intrepid main
#
# Themes
deb http://ppa.launchpad.net/kwwii/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kwwii/ppa/ubuntu intrepid main
#
# DropBox
deb http://linux.getdropbox.com/ubuntu intrepid main
deb-src http://linux.getdropbox.com/ubuntu intrepid main
#
# Compiz
deb http://ppa.launchpad.net/compiz/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/compiz/ppa/ubuntu intrepid main
#
# Firefox
deb http://ppa.launchpad.net/fta/ppa/ubuntu intrepid main

```

perl -v
```

This is perl, v5.10.0 built for i486-linux-gnu-thread-multi

Copyright 1987-2007, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using "man perl" or "perldoc perl".  If you have access to the
Internet, point your browser at http://www.perl.org/, the Perl Home Page.

```

Also try the script again, and post the full output?

```
perl change.pl
Looking into file /etc/apt/sources.list
Detected/Correct: deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/c-korn/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/jeffreyratcliffe/ppa/ubuntu intrepid main
Detected/Correct: deb-src http://ppa.launchpad.net/jeffreyratcliffe/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/mozillateam/ppa/ubuntu intrepid main universe
Detected/Correct: deb http://ppa.launchpad.net/network-manager/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/kwwii/ppa/ubuntu intrepid main
Detected/Correct: deb-src http://ppa.launchpad.net/kwwii/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/compiz/ppa/ubuntu intrepid main
Detected/Correct: deb-src http://ppa.launchpad.net/compiz/ppa/ubuntu intrepid main
Detected/Correct: deb http://ppa.launchpad.net/fta/ppa/ubuntu intrepid main
Saving temporarily to /tmp/lp_change.list
Moving temporary file as /etc/apt/sources.list
INFO: Enter your administrator password if asked

[sudo] password for peter: 
Will retrieve keys for: openoffice-pkgs ubuntu-wine c-korn jeffreyratcliffe tualatrix do-core mozillateam network-manager kwwii compiz fta
Attempting to get Launchpad key for openoffice-pkgs: http://launchpad.net/~openoffice-pkgs/+archive/ppa
Attempting to get Launchpad key for ubuntu-wine: http://launchpad.net/~ubuntu-wine/+archive/ppa
Attempting to get Launchpad key for c-korn: http://launchpad.net/~c-korn/+archive/ppa
Attempting to get Launchpad key for jeffreyratcliffe: http://launchpad.net/~jeffreyratcliffe/+archive/ppa
Attempting to get Launchpad key for tualatrix: http://launchpad.net/~tualatrix/+archive/ppa
Attempting to get Launchpad key for do-core: http://launchpad.net/~do-core/+archive/ppa
Attempting to get Launchpad key for mozillateam: http://launchpad.net/~mozillateam/+archive/ppa
Attempting to get Launchpad key for network-manager: http://launchpad.net/~network-manager/+archive/ppa
Attempting to get Launchpad key for kwwii: http://launchpad.net/~kwwii/+archive/ppa
Attempting to get Launchpad key for compiz: http://launchpad.net/~compiz/+archive/ppa
Attempting to get Launchpad key for fta: http://launchpad.net/~fta/+archive/ppa
```

.....  and the end of sudo apt-get update

```
Fetched 276kB in 1min11s (3837B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: Duplicate sources.list entry http://packages.medibuntu.org intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by forger on 2009-02-11
Hm... there's no "Found key:" output after "Attempting to get Launchpad key". This means that either your network or my script/perl fail to connect to launchpad.

Can you paste the output of:
```

apt-cache policy openssl libio-socket-ssl-perl
wget http://launchpad.net/~openoffice-pkgs/+archive/ppa --verbose -O /tmp/lp_test_nossl.html
wget https://launchpad.net/~openoffice-pkgs/+archive/ppa --verbose -O /tmp/lp_test_withssl.html
```

I think it needs this package as well:
```
sudo apt-get install libio-socket-ssl-perl
```

Then try the script once more :)

---

### Post by expatCM on 2009-02-11
Did everything without any change in the outcome.  For some reason it looks like lauchpad.net is not found.  I just tried to ping and got the unknown host message returned.   I do not quite understand why though since I can get there with a browser...  Perhaps this is a home server challenge.


apt-cache policy openssl libio-socket-ssl-perl

```
apt-cache policy openssl libio-socket-ssl-perl
openssl:
  Installed: 0.9.8g-10.1ubuntu2.1
  Candidate: 0.9.8g-10.1ubuntu2.1
  Version table:
 *** 0.9.8g-10.1ubuntu2.1 0
        500 http://security.ubuntu.com intrepid-security/main Packages
        500 http://archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     0.9.8g-10.1ubuntu2 0
        500 http://archive.ubuntu.com intrepid/main Packages
libio-socket-ssl-perl:
  Installed: (none)
  Candidate: 1.13-1
  Version table:
     1.13-1 0
        500 http://archive.ubuntu.com intrepid/main Packages
W: Duplicate sources.list entry http://packages.medibuntu.org intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)

```

wget [http://launchpad.net/~openoffice-pkgs/+archive/ppa](http://launchpad.net/~openoffice-pkgs/+archive/ppa) --verbose -O /tmp/lp_test_nossl.html

```
 wget http://launchpad.net/~openoffice-pkgs/+archive/ppa --verbose -O /tmp/lp_test_nossl.html
--2009-02-12 11:29:31--  http://launchpad.net/~openoffice-pkgs/+archive/ppa
Connecting to 10.0.0.1:8080... connected.
Proxy request sent, awaiting response... 301 Moved Permanently
Location: https://launchpad.net/~openoffice-pkgs/+archive/ppa [following]
--2009-02-12 11:29:32--  https://launchpad.net/~openoffice-pkgs/+archive/ppa
Resolving launchpad.net... failed: Name or service not known.
wget: unable to resolve host address `launchpad.net'
peter@p4s800mx:~$ wget http://launchpad.net/~openoffice-pkgs/+archive/ppa --verbose -O /tmp/lp_test_nossl.html >test2.txt
--2009-02-12 11:30:04--  http://launchpad.net/~openoffice-pkgs/+archive/ppa
Connecting to 10.0.0.1:8080... connected.
Proxy request sent, awaiting response... 301 Moved Permanently
Location: https://launchpad.net/~openoffice-pkgs/+archive/ppa [following]
--2009-02-12 11:30:05--  https://launchpad.net/~openoffice-pkgs/+archive/ppa
Resolving launchpad.net... failed: Name or service not known.
wget: unable to resolve host address `launchpad.net'

```

wget [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) --verbose -O /tmp/lp_test_withssl.html

```
wget https://launchpad.net/~openoffice-pkgs/+archive/ppa --verbose -O /tmp/lp_test_withssl.html
--2009-02-12 11:32:34--  https://launchpad.net/~openoffice-pkgs/+archive/ppa
Resolving launchpad.net... failed: Name or service not known.
wget: unable to resolve host address `launchpad.net'
```

---

### Post by forger on 2009-02-12
Could you try:
1) ```
sudo /etc/init.d/networking restart
sudo /etc/init.d/avahi-daemon restart
```
2) reboot your machine?

It doesn't seem to be restricted to perl - the only thing I can do for the script is to use the html headers to see if it's successfully connected or not.

---

### Post by forger on 2009-02-12
By the way, do you use a proxy server or anything?
Try ```
netstat -t tcp
ping -c 5 google.com
```

---

### Post by expatCM on 2009-02-13
Yes, I am running a proxy browser (squid).  Would it help if I turn it off?

netstat -t tcp

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 p4s800mx.local:869      cmxfresh:nfs            ESTABLISHED
tcp        0      0 p4s800mx.local:36623    cmxfresh:ipp            TIME_WAIT  
tcp        0      0 p4s800mx.local:44822    cmxfresh:3128           ESTABLISHED
```


Google loads in the browser but ....

```
ping -c 5 google.com
ping: unknown host google.com
```

Interesting thing though is that the machine that works runs through the same server ....

---

### Post by forger on 2009-02-13
I don't know, it's definitely a proxy problem. :)
I could only suggest installing
```
sudo apt-get install gnome-network-admin
```

And setting up your proxy:
System > Administration > Network
System > Prefences > Network proxy

---

### Post by expatCM on 2009-02-15
Well thanks for ALL your efforts ....  appreciated :)

I think what I will do is change in the next few days is to change the network cable and IP address so that the connection is directly to the router ........  and then see what happens ..........

---

### Post by forger on 2009-02-15
I might fix this actually in 1.3, I think I need to request proxy for it, I'll let you know soon!

---

### Post by forger on 2009-02-15
I think you can set your proxy in terminal:
```
export http_proxy='proxy.domain:port'
```
and then execute your code, e.g.

```

echo $http_proxy
export HTTP_PROXY="http://username:password@host:port/"
export http_proxy="http://username:password@host:port/"
wget --verbose http://archive.ubuntu.com -O /tmp/test.html

```

From what I've read, don't test it with ping, since it doesn't use proxy, use the wget command above :)
Source:
- [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)
- [http://fedoraforum.org/forum/printthread.php?t=742](http://fedoraforum.org/forum/printthread.php?t=742)

---

### Post by forger on 2009-02-16
Added support for http_proxy environment variable (set by the system):
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by expatCM on 2009-02-23
I have tried this with a total of four machines all on the same network.  Three appear to work without issue, one will not.  I have zero idea what the problem could be (same machine as discussed earlier in the thread) and do not intend to occupy your time thinking about this...........

In two or three months time I will upgrade the network to 9.04 and at that time focus on any issues.

Thanks for your help forger and for putting together some code that helps users like me :)

---

### Post by forger on 2009-02-24
Well, at least we tried :)

---

