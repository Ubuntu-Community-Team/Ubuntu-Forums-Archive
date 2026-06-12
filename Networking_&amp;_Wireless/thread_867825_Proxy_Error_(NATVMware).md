---
title: "Proxy Error (NAT/VMware)"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by JoneYee on 2008-07-23
I am having a problem with a proxy regarding update manager and the execution of any apt command from Terminal.  

This problem exists on an Ubuntu WS running in VMWare Server.  I have a NAT connection through the host machine's network connection which is proxy authenticated (at work).

I have configured Firefox with the necessary proxy information and I can browse via Firefox fine (otherwise I would not be typing here right now).  

However any use of Synaptic or attempts to install via terminal fail.   Update Manager tells me: 

1. My application list is out of date (that I need an internet connection to update it.

2. W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve '@proxy.us.companyname.com'

I have been scratching my heado n this for two days.  I have my System>Network Proxy Configured the same as Firefox.  i have pinged the proxy server and get excellent response.  I have tried to use the proxy server's direct i.p. with no change,

Any suggestions appreciated. 

I am using the VM at work to learn Ubuntu/Debian and then implementing what I learn at home in my new Ubuntu Network.  Just need this to work to install, among other things, Samba (for starters).

---

### Post by bapoumba on 2008-07-23
> **JoneYee said:**
> I am having a problem with a proxy regarding update manager and the execution of any apt command from Terminal.  

This problem exists on an Ubuntu WS running in VMWare Server.  I have a NAT connection through the host machine's network connection which is proxy authenticated (at work).

I have configured Firefox with the necessary proxy information and I can browse via Firefox fine (otherwise I would not be typing here right now).  

However any use of Synaptic or attempts to install via terminal fail.   Update Manager tells me: 

1. My application list is out of date (that I need an internet connection to update it.

2. W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve '@proxy.us.companyname.com'

I have been scratching my heado n this for two days.  I have my System>Network Proxy Configured the same as Firefox.  i have pinged the proxy server and get excellent response.  I have tried to use the proxy server's direct i.p. with no change,

Any suggestions appreciated. 

I am using the VM at work to learn Ubuntu/Debian and then implementing what I learn at home in my new Ubuntu Network.  Just need this to work to install, among other things, Samba (for starters).
On hardy, I did not have anything to do regarding the proxy I have to use at work. Synaptic is set to direct, and I just change the global proxy (System>Pref>Network Proxy). Fx is set to use the system proxy.
Have you tried using apt-get in the terminal? Please paste the error to:
```
sudo apt-get update
```
and your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by JoneYee on 2008-07-23
Running sudo apt-get update:

```
Err http://archive.canonical.com hardy Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com hardy/partner Translation-en_US               
  Unable to connect to archive.canonical.com http:
Err http://security.ubuntu.com hardy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com hardy-security/main Translation-en_US           
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US     
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/universe Translation-en_US       
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
  Unable to connect to security.ubuntu.com http:
0% [Connecting to archive.ubuntu.com (91.189.88.45)] [Connecting to us.archive.
```

...and so on

Contents of /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

I have tried apt-get multiple times but I have not set to system proxy.  The above results are from the unaltered proxy I described in my original post.

I will make the change and then reply again with result of apt-get under those settings.



UPDATE:

Changed FF to System proxy and connections timeout.

2nd UPDATE:
WIth FF configured with Proxy, System>Preferences>Network Proxy configured with the work proxy (same one that works in FF) and Synaptic set now to Direct, *sudo apt-get update* returns the following error:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

---

### Post by bapoumba on 2008-07-23
Okay thanks.
Just to add that prior to hardy, I had to set up the proxy in /etc/apt/apt.conf for synaptic, apt-get or aptitude to work. I was pleasantly surprised with hardy. This laptop goes back and forth twice a day between home settings (dhcp, no proxy, somtimes wireless) to work settings (static IP, proxy, sometimes wireless) without having to tweak any conf files manually any more.

---

### Post by JoneYee on 2008-07-23
I would edit that file, however ls -a of /etc/apt:

```

.   apt.conf.d   sources.list    sources.list.save  trusted.gpg
..  secring.gpg  sources.list.d  trustdb.gpg        trusted.gpg~

```

I am not seeing apt.conf to edit (apt.conf.g is a directory)

UPDATE

wget -v [www.google.com](www.google.com)
```
 wget -v www.google.com
--09:02:10--  http://www.google.com/
           => `index.html'
Resolving proxy.us.company.com... 143.166.99.244
Connecting to proxy.us.company.com|143.166.99.244|:80... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
09:02:10 ERROR 407: Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ).
```

So it would appear I am getting to the proxy, but failing to authenticate.  The proxy is resolving at least.

---

### Post by bapoumba on 2008-07-23
If the file does not exist, you can create it: [http://linux.die.net/man/5/apt.conf]("http://linux.die.net/man/5/apt.conf")
The Acquire group is the one you want to look at. But as I said, after a fresh hardy install, I did not have to use it any longer. I will look if I can find what has been changed, because that is not the first time I see people having trouble with proxies on hardy.

Edit, ah, an ISA proxy, let me look for some links :)

---

### Post by bapoumba on 2008-07-23
For the ISA proxy, please have a look at ntlmaps and /etc/apt.conf.d/proxy, [more here]("http://ubuntuforums.org/showthread.php?t=589854") for the conf files and additional links. Best of luck :)

---

### Post by JoneYee on 2008-07-23
The silliest of things.  Synaptic required the domain\user_name convention for Proxy Authentication whereas FF did not.

sudo apt-get update performs normally with that change. 

Thanks for the help, it led me to some commands the helped me diagnose the problem, but as it stands now I appear resolved.

---

