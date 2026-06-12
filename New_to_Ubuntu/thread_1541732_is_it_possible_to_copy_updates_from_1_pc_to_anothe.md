---
title: "is it possible to copy updates from 1 pc to another?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by brotherlouie on 2010-07-29
hi! just jumped into ubuntu recently, 10.04 yey!!
now i want to convert all my computers to ubuntu. 
is there a way i can copy downloaded updates from one computer to another?
instead of downloading them every time i fresh install on a new computer
it takes me 2-3hours to update after a fresh install.
i was hoping to find a faster way to update if im going to install ubuntu on about 5computers.
hoping i could just download the updates on one computer and just copy it to the rest.
tnx!

---

### Post by itisbasi on 2010-07-29
aptonCD is just what you're looking for!

---

### Post by brotherlouie on 2010-07-29
tnx! sounds promising!
what does it do? and how do i get it?

---

### Post by itisbasi on 2010-07-29
> **brotherlouie said:**
> tnx! sounds promising!
what does it do? and how do i get it?

Search for it in synaptic package manager and install it. Go to system>admi nistration and start aptoncd. You will be able to create discs/ISOs with all the updated packages. Use this CD on other ubuntu machines to update all the packages. You can install aptoncd on the other ubuntu machines and restore/update packages using the ISOs.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by philinux on 2010-07-29
> **brotherlouie said:**
> hi! just jumped into ubuntu recently, 10.04 yey!!
now i want to convert all my computers to ubuntu. 
is there a way i can copy downloaded updates from one computer to another?
instead of downloading them every time i fresh install on a new computer
it takes me 2-3hours to update after a fresh install.
i was hoping to find a faster way to update if im going to install ubuntu on about 5computers.
hoping i could just download the updates on one computer and just copy it to the rest.
tnx!

If the pc's are on a network then install this. It is in the repo. You set up the main pc and the others a clients I think. If the pc's are not on a network then aptoncd would be the best. This is also in the repos.

**Apt-cacher** performs caching of .deb and source packages which have been
downloaded by local users. It is most useful for local area networks with slow
internet uplink.

When a package is requested, the cache checks whether it already has the
requested version, in which case it sends the package to the user immediately.
If not, it downloads the package while streaming it to the user at the same
time. A local copy is then kept for use by other users.

Apt-cacher has been optimized for best utilization of network bandwidth and
efficiency even on slow low-memory servers. Multiple ways of installation are
possible: as a stand-alone HTTP proxy, as a daemon executed by inetd or as a
CGI program. Client machines are configured by changing APT's proxy
configuration or modification of access URLs in sources.list.

The package includes utilities to clean the cache (removing obsolete package
files), generate usage reports and import existing package files.  Experimental
features include a simple package checksum verification framework, optional
IPv6 support and pre-fetching of new packages (upgrade candidates).

Apt-cacher can be used as a replacement for apt-proxy, with no need to modify
client's /etc/apt/sources.list files (and even reusing its config and cached
data), or as an alternative to approx.

---

### Post by brotherlouie on 2010-07-29
souds just like what im lookin for! 
im reading up on apt-cacher right now,
altho, my computers are not on a network.
i would just like to have a copy of the updates in a usb
and copy it to every pc as i move along.

---

### Post by brotherlouie on 2010-07-29
i found this in another topic 

go to 

/var/cache/apt/archives

get al the *.deb files and put them on your usb stick.

does this actually work?

---

### Post by howefield on 2010-07-29
Yes, it will work. Just copy them to the same folder in the other machines.

You'll need to copy them over with elevated rights.

---

### Post by brotherlouie on 2010-07-29
cool! now what are elevated rights?
when i paste the contents archive folder over to another pc
will it automatically begin installing the updates?
or do i need a command for it?
tnx guys!

---

### Post by howefield on 2010-07-29
> **brotherlouie said:**
> cool! now what are elevated rights?

You won't be able to copy from the /var/cache/apt/archive folder without using root permissions.

Either by opening nautilus with gksudo nautilus or by preceding a terminal command to copy the files with sudo.

I'd use the terminal, least danger of doing damage.

---

### Post by gandaran on 2010-07-29
you can copy them without being root but you will need to be root to paste them in the same directory on the second computer and the computer will need internet connection just to update the software data then install the updates normally just like you did on the first computer.

---

### Post by brotherlouie on 2010-07-30
> **howefield said:**
> You won't be able to copy from the /var/cache/apt/archive folder without using root permissions.

Either by opening nautilus with gksudo nautilus or by preceding a terminal command to copy the files with sudo.

I'd use the terminal, least danger of doing damage.

ok, now im confused. 
is this the same as having ADMIN rights in windows?

wat is gksudo nautilus? is that an apt i should download?

---

### Post by JackNocturne on 2010-07-30
this thread helped me:p

---

### Post by brotherlouie on 2010-07-30
> **gandaran said:**
> you can copy them without being root but you will need to be root to paste them in the same directory on the second computer and the computer will need internet connection just to update the software data then install the updates normally just like you did on the first computer.

does this mean that i don't save any time by doing this process?

all i wanna do is speed up my installation process since:
a. i fresh install ubuntu 10.04
b. i run update manager (which takes me 2-3hrs) 
(just want a quick and simple way to transfer updates from an updated computer to a not updated computer)

tnx folks! really tryin to absorb all of this.

---

### Post by brotherlouie on 2010-07-30
> **JackNocturne said:**
> this thread helped me:p

did u get to do what i was tryin to do brotha?
could you lay it down for me real simple?
hehe. tnx!

---

### Post by Elfy on 2010-07-30
If the computers are networked then apt-cacher type apps work well - I used apt-cacher-ng

If they are not networked then apton-cd or a simple copy of the apt cache will work.

[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by Jahid65 on 2010-07-30
brotherlouie, install aptoncd via synaptic or SC. You will find it system->administration menu. launch it. Create ISO with it. Then install aptoncd on other pc. Launch it, but this time choose restore option. Then show the path of your ISO. It will automatically restore all updates of your pc to other pc. Then update the system with update manager. see the following link
[http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html](http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html)

---

### Post by brotherlouie on 2010-07-30
> **forestpiskie said:**
> If the computers are networked then apt-cacher type apps work well - I used apt-cacher-ng

If they are not networked then apton-cd or a simple copy of the apt cache will work.

[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

nope, they are not on a network. 
so its apton-cd then.

it says on the website that it saves package from /var/cache/apt/archives/ by default.
and i can save it as .iso and have it on a usb.

so what do i do once i get it to the other pc?
"Restore a media created by APTonCD Note: This action requires administrative privileges."
is this another way of saying, i only need to input my password?

and when i do get it there...will it install itself automatically or do i need to type in a code for it?
"using apt-get, aptitude or synaptic without need to download them."

---

### Post by itisbasi on 2010-07-30
> **brotherlouie said:**
> nope, they are not on a network. 
so its apton-cd then.

it says on the website that it saves package from /var/cache/apt/archives/ by default.
and i can save it as .iso and have it on a usb.

so what do i do once i get it to the other pc?
"Restore a media created by APTonCD Note: This action requires administrative privileges."
is this another way of saying, i only need to input my password?

and when i do get it there...will it install itself automatically or do i need to type in a code for it?
"using apt-get, aptitude or synaptic without need to download them."
Does the other computer have internet access? If yes, you will have to install aptonCD. Open aptponCD,,,,,click restore, navigate to the ISO on your pen drive and that's pretty much it.

---

