---
title: "Are the Repositories Down ?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-06
Hi,

I can't seem to connect to the repositories from ANY of my computers?

Neither through synaptic NOR if I copy and past the link.

I reach the repository server but it keeps saying it cannot locate the files on the server

For example this is what I get.....

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/php-net-socket/php-net-socket_1.0.8-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/php-net-socket/php-net-socket_1.0.8-2_all.deb)
  404 Not Found [IP: 91.189.92.170 80]

And if I enter the URL directly into the browser I get a server response that says the requested file is not on the server.

---

### Post by Hippytaff on 2010-11-06
Working fine here - which country are you in? perhaps the servers are down there?

---

### Post by uRock on 2010-11-06
Just copied and pasted the IP into the browser and it appears to be working, but when I click the link, it goes to the same error you mentioned.

Is this a repo you just added?

---

### Post by uRock on 2010-11-06
I see the problem. The version of the package that you are trying to install is not there. Here are the ones that are listed.
[ATTACH]174793[/ATTACH]

---

### Post by mistypotato on 2010-11-06
thx uRock.

That makes sense but I'm wondering why my systems are looking in the wrong repositories?

Also, I am thinking I can go to synaptic package manager and update it?

OR....

Are the repositories for **8.10 Intrepid** no longer available?

Did completely uninstalling AVAHI have anything to do with this ?

---

### Post by uRock on 2010-11-06
Intrepid's servers have been down for about six months now.

---

### Post by mistypotato on 2010-11-06
ahhhhh  :)

that splains it.

Does that mean that if you have Intrepid and you need to reinstall something like Avahi you're out of luck ?

---

### Post by Hippytaff on 2010-11-06
It means it's no longer supported, maybe install 10.04LTS or even 10.10 :-)

---

### Post by uRock on 2010-11-06
Unless it happens to be on the install disk or if you can find it on a trusted web page as a download.

I'd recommend upgrading, unless it is out of the question for some reason. Do keep in mind that if you want to upgrade, Jaunty(9.04) is no longer supported as well.

---

### Post by treacl on 2010-11-09
That bites.

I have an old laptop that runs 8.10 beautifully but won't run 10.04 to save its life. Hardly worth troubleshooting the install problem, but I do need to baby it along until it dies from hardware exhaustion.

---

### Post by Hippytaff on 2010-11-09
I'm just about to try Lubuntu on a really old laptop...lots of light options about
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by uRock on 2010-11-09
> **treacl said:**
> That bites.

I have an old laptop that runs 8.10 beautifully but won't run 10.04 to save its life. Hardly worth troubleshooting the install problem, but I do need to baby it along until it dies from hardware exhaustion.

Sorry to hear that. Maybe one of these close relatives will run on it.

Lubuntu
Peppermint(Lubuntu derivative)
Linux Mint Debian Edition aka LMDE
Puppy
Crunchbang- Debian version

---

### Post by Hippytaff on 2010-11-09
> 
Crunchbang- Debian version

not heard of that one...intrigued :-)

---

### Post by uRock on 2010-11-09
> **Hippytaff said:**
> not heard of that one...intrigued :-)

I think they have stopped remastering Ubuntu.

---

### Post by PhilGil on 2010-11-09
Don't forget about Debian Lenny (the current stable version) itself. It should share many characteristics with Ubuntu 8.04 and 8.10, and will be supported for at least a year after the next stable release (which won't happen until late 2010 or early 2011).

---

### Post by toekneewood on 2010-11-09
How about installing 10.10 on your best laptop? :)  It took me 6 months to convince my brother in law.  No I can't stop him talking about it.

---

### Post by waynefoutz on 2010-11-09
try this with intrepid:

```
sudo gedit /etc/apt/sources.list
```


then delete everything in the file and replace it with this


```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
```

this should get your synaptic working again. If it does work, you won't get any security updates, but you'll be able to install software again, even though the versions will be old and outdated. 

My suggestion, if you like Intrepid, and want to stay with a version close to it, Debian Lenny is the way to go. Go to their site and download the first dvd. You don't need all 5. Like the other guy said, the clock don't start ticking on Lenny until Squeeze replaces it as it's stable version, which is supposed to happen early next year. After that, you have a year to enjoy Lenny.

---

### Post by Hippytaff on 2010-11-09
This is also worth a look
[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)
you probably already know about it, but another option :-)

---

### Post by jackthecoiner on 2010-11-15
> **waynefoutz said:**
> try this with intrepid:

...

```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
```

this should get your synaptic working again...

It actually seems to be a problem with the repositories for Intrepid.  Even after updating sources.list to use old-releases.ubuntu.com, many packages still won't install or update, e.g.:
```
Err http://old-releases.ubuntu.com intrepid-security/main linux-image-2.6.27-17-generic 2.6.27-17.46
  404 Not Found
Err http://old-releases.ubuntu.com intrepid-security/main linux-image-generic 2.6.27.17.21
  404 Not Found
(Reading database ... 104549 files and directories currently installed.)
Removing linux-headers-2.6.27-17 ...
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-17-generic_2.6.27-17.46_i386.deb: 404 Not Found
```

They seem to have stumbled onto this issue over here as well:
[http://ubuntuforums.org/showthread.php?t=1622226](http://ubuntuforums.org/showthread.php?t=1622226)

This is making it impossible at the moment to dist-upgrade from Intrepid.  I'd love to hear if anyone has any solutions to offer.

---

### Post by jackthecoiner on 2010-11-15
It also appears the issue is being tracked here:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/673446](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/673446)

---

### Post by waynefoutz on 2010-11-15
```
deb http://old-releases.ubuntu.com/ubuntu/dists intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/dists intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/dists intrepid-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/dists intrepid-backports main restricted universe multiverse
```

try it with that instead.

---

### Post by mistypotato on 2010-11-18
I ended up UPGRADING all my ubuntu machines to 9.10 (from 8.10).

The update was surprisingly easy and went fine on all the machines.  (not a single glitch)

Kudos to the Ubuntu development team for superb work :KS:KS:KS:KS:KS

I'm totally blown away that they could implement all those changes on my 4 different machines (one being a server) and everything went 100% smooth.  Those folks are incredible.

I suppose going forward I need to update more often.

The hesitation was from reading so many others reports of problems after upgrading.

Team Ubuntu is awsome !

---

