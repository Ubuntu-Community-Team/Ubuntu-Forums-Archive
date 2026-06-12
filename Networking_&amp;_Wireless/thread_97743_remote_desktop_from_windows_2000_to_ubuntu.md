---
title: "remote desktop from windows 2000 to ubuntu"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by tonysathre on 2005-12-01
i have set up a domain with a linux client and want to be able to remote desktop to the ubuntu client from windows 2000, i installed the ltsp package but i think i need something more. maybe need to start terminal services but its not in the services menu, any help would be great.... thanks

---

### Post by Appolusionist on 2005-12-01
[quote=tonysathre]i have set up a domain with a linux client and want to be able to remote desktop to the ubuntu client from windows 2000, i installed the ltsp package but i think i need something more. maybe need to start terminal services but its not in the services menu, any help would be great.... thanks[/quote]
 
You have a few options here...personally I use FreeNX and here is a [howto]("https://wiki.ubuntu.com/FreeNX") and you can also do the same thing using vnc, but it is not as secure and I find freenx to be quite faster but of course YMMV. :) Here is a [howto ]("http://ubuntuguide.org/#vncfromwindows")for VNC.

---

### Post by tonysathre on 2005-12-01
ya i just finished setting up vnc, but it is to slow, ill try freenx

---

### Post by tonysathre on 2005-12-01
i followed the guide for FreeNX but get this error:

t0ny@ubuntu:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:6 [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release.gpg [307B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:8 [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release [12.5kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Get:10 [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/freenx Packages [2560B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 74.8kB in 2s (33.7kB/s)
Reading package lists... Done
W: GPG error: [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
t0ny@ubuntu:~$ gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg: directory `/home/t0ny/.gnupg' created
gpg: new configuration file `/home/t0ny/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/t0ny/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/t0ny/.gnupg/secring.gpg' created
gpg: keyring `/home/t0ny/.gnupg/pubring.gpg' created
gpg: requesting key 1135D466 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Connection refused
gpgkeys: HKP fetch error: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
t0ny@ubuntu:~$  gpg --export --armor 1135D466 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
t0ny@ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release.gpg [307B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/freenx Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 311B in 1s (218B/s)
Reading package lists... Done
W: GPG error: [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
t0ny@ubuntu:~$ sudo apt-get install gpg
Reading package lists... Done
Building dependency tree... Done
Package gpg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gpg has no installation candidate
t0ny@ubuntu:~$

---

### Post by Appolusionist on 2005-12-05
[quote=tonysathre]i followed the guide for FreeNX but get this error:
 
t0ny@ubuntu:~$ sudo apt-get update
Password:
W: GPG error: [http://seveas.ubuntulinux.nl]("http://seveas.ubuntulinux.nl") breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
[/quote]
 
I am stuck on a Windows PC right now, but you can ignore that error and apt-get freenx or any other program.

---

### Post by tonysathre on 2005-12-05
ya i figured that out right after i posted, thanks for the replies, it works sweet... is there a way to shut off the mouse movement on the remote machine to speed things up

---

### Post by Appolusionist on 2005-12-08
[quote=tonysathre]ya i figured that out right after i posted, thanks for the replies, it works sweet... is there a way to shut off the mouse movement on the remote machine to speed things up[/quote]

Not that I am aware of, but then again I have never looked. If you find one, please post it here.

---

