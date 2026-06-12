---
title: "ubuntu, &quot;apt-get update&quot;"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by craigdele on 2005-12-05
I have recently installed ubuntu 5.10 but im unable to update.

I am able to browse the web using firefox (I had to disable ipv6) but the 'apt -get' command fails. I am absolutely certain the repositories are correct. I have a broadband connection through a D-Link DSL-G604T router.

Can anyone help!

Below is a copy of the errors i receive, etc/network/interfaces and etc/apt/sources scripts.

regards

Dele



cdelehanty@DeleHome:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy Release.gpg
Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates Release.gpg
Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports Release.gpg
Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu...ezy/Release.gpg](http://nz.archive.ubuntu.com/ubuntu...ezy/Release.gpg) Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu...tes/Release.gpg](http://nz.archive.ubuntu.com/ubuntu...tes/Release.gpg) Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu...rts/Release.gpg](http://nz.archive.ubuntu.com/ubuntu...rts/Release.gpg) Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/d...ity/Release.gpg](http://security.ubuntu.com/ubuntu/d...ity/Release.gpg) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outReading package lists... Done
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_main_bin ary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_restrict ed_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_universe _binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
cdelehanty@DeleHome:~$


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
auto eth0
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
iface eth0 inet dhcp


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by giloth on 2005-12-05
I'm having troubles getting my router to work as well. I had a similar experience trying to get the updates, connect to certain irc servers and trying to connect to certain webpages. I never had any problem with Windows (*gets smacked*). I'm just it's just a tiny setting in there. Until I have more time to figure it out, I've directly connected my cable modem to my comptuer.

My router is a Blitzz.

---

### Post by yoghurt on 2006-07-01
[QUOTE=giloth]I'm having troubles getting my router to work as well. I had a similar experience trying to get the updates, connect to certain irc servers and trying to connect to certain webpages. I never had any problem with Windows (*gets smacked*). I'm just it's just a tiny setting in there. Until I have more time to figure it out, I've directly connected my cable modem to my comptuer.

My router is a Blitzz.[/QUOTE]

Same thing here - with DapperDrake. No matter which repositories I have in /etc/apt/sources.list, they always have the IP address 1.0.0.0 

I've been looking on the forums for quite a while but haven't found any response that would make sense. The users all have similar problems:

- they can browse the web fine
- sudo apt-get update gives the repositories IP address 1.0.0.0

Does anybody have any ideas? Thanks a lot in advance...

---

### Post by mmcclure79 on 2006-07-02
I have a Blitzz router as well, I have smacked myslef several times for going the cheap route and buying a no name router.....

I'm having problems as well with apt-get, but I'm using breezy and I actually get IPs back, my connections just get refused. Could it be a case that the repository's server should be checked out? Probanbly not since not everyone is having a problem connecting. 
I have no problem getting to the internet, or my network, as soon as I run apt-get to upgrade and install stuff I get error 111 connectoin refused. I've used sources.list files that are known good so I know that that's not it. I get IP address returned with the URL for the repositories, I can even reach the repositories via a web browser. I even went through and disabled IPv6 because my router doesn't support it. All of this leads me to believe that there must be something wrong with apt-get, but I have no idea where to look for the source of the problem. 

Have you guys checked to see if your DNS server is messing up? Do you have problems surfing the internet? I mean 1.0.0.0 is a public address so I would think that DNS has been poisoned or something.

---

### Post by mmcclure79 on 2006-07-02
I took my computer over to my father's who has cable while I have DSL and everything worked just fine there. Leads me to believe that it's my provider. You guys might want to try that if it's feasable. Now to call the ISP tomorrow before I go to work...

---

### Post by g00n on 2006-07-08
ok people, search for my posts.. 

the 1.0.0.0 is coming from your router... it's responding to an IPV6 DNS query with the 1.0.0.0 reply.. remove your router from the /etc/resolv.conf to get past this.

Disabling IPV6 would be the solution, if anything that was to disable IPV6 would actually disable IPV6.. I have tried every thing i've found to disable IPV6 so far and have not made a difference.

If you don't want to believe me, start tcpdump or ethereal and capture some traffic from of a DNS request.

You'll see the DNS request, and the reply from your router of 1.0.0.0 (i've done this already, and sent the captures to other network engineers to verify).

Ultimately it's a problem with the DNS server.. but the problem comes from varying manufacturers, and versions.. I wish they would read forums like this and see these problems.

Hope this starts to help and we can make progress towards finding an actual working solution.

---

### Post by stonefeet on 2006-07-09
> **g00n said:**
> ok people, search for my posts.. 

the 1.0.0.0 is coming from your router... it's responding to an IPV6 DNS query with the 1.0.0.0 reply.. remove your router from the /etc/resolv.conf to get past this.

Disabling IPV6 would be the solution, if anything that was to disable IPV6 would actually disable IPV6.. I have tried every thing i've found to disable IPV6 so far and have not made a difference.

If you don't want to believe me, start tcpdump or ethereal and capture some traffic from of a DNS request.

You'll see the DNS request, and the reply from your router of 1.0.0.0 (i've done this already, and sent the captures to other network engineers to verify).

Ultimately it's a problem with the DNS server.. but the problem comes from varying manufacturers, and versions.. I wish they would read forums like this and see these problems.

Hope this starts to help and we can make progress towards finding an actual working solution.

i've had this same sort of problem, the repos, gaim, torrents will work after i do an nslookup on the address if i don't do that it will not work, 101 network unreachable, and when i do the nslookups it will only work for a few hours, nicotine and firefox work perfectly all the time everytime
i was thinking it was a dns problem, but no clue how to fix it
my resolv.conf only has my modems ip in it and no mention of the router

plugging in the modem directly to the computer yields the same result

any ideas?

---

### Post by g00n on 2006-07-09
I think i got it fixed last night... by fixed, i mean actually being able to disable ipv6..

/etc/modprobe.d/blacklist
add the line
blacklist ipv6

reboot, and i no longer load ipv6 , and nolonger have to play with my /etc/resolv.conf to get online.

---

### Post by yoghurt on 2006-07-13
What I'm using as a workaround at the moment is that I opened the "network settings", entered admin mode and in the Domain Name System entered my IPS's dns server IP address and removed my router's IP address (192.168.1.1).
I'm assuming this is the same as simply rewriting /etc/resolv.conf ;)

Anyway, it's far from perfect as with each restart (and I DO occasionally turn off the computer) this file gets re-written and modem's IP is there again.

I've followed Goon's instructions and have disabled the IPv6 (at least I think I did).

Any further advice guys?

---

### Post by kelvin_team on 2006-11-06
I got this problem solved finnaly by enabling "Disabling SPI Firewall" function in my WAN function in my netgear wireless router. I'm using ubuntu 6.06 LTS, and before also my apt-get can't work..

Hope this can help... chers,
Kelvin

---

### Post by albesan on 2006-11-30
hello team,

suffering from the same problem.
I wouldn't want to disable my firewall... there must be another way around it.
I found that with me is kind of intermitent, I do get a valid ip address, although nothing much else happens...

---

### Post by Thumper322 on 2006-11-30
Just a suggestion... You could look up the IP addresses of the update servers and add them to **/etc/hosts**--no disabling firewalls or killing ipv6 that way.

---

