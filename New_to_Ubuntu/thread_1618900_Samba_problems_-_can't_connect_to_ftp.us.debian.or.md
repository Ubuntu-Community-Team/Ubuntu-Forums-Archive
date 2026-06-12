---
title: "Samba problems - can't connect to ftp.us.debian.org"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-11
Good morning,

I am having problems updating Samba on my father's 10.10 install. I had no problems with my almost-identical install. I'm trying to share folders and the problems went something like this:

1. Right-click folder to share and it comes back 
> 
"Failed to execute child process "testparm" (No such file or directory)"
2. Some googling seems to suggest that the problem might be samba-common-bin is not installed. When I open Synaptic and attempt 'mark for upgrade' it comes back: 
> 
You are about to install software that can't be authenticated. I click the Mark button anyway, followed by Apply, It says "samba-common-bin (version 2:3.5.4~dfsg-1ubuntu8) will be upgraded to version 2:3.5.6~dfsg-1".Fine, so I hit 'apply'.

3. It starts to download the package files but comes back 
> "W: Failed to fetch [http://ftp.us.debian.org/debian/pool/main/s/samba/samba-common-bin_3.5.6~dfsg-1_i386.deb]("http://ftp.us.debian.org/debian/pool/main/s/samba/samba-common-bin_3.5.6%7Edfsg-1_i386.deb")
  Something wicked happened resolving 'ftp.us.debian.org:http' (-5 - No address associated with hostname)"4. I then tried "sudo apt-get update", which returns:

> 
Hit [http://ubuntu.datahop.net](http://ubuntu.datahop.net) maverick-security/multiverse i386 Packages
Fetched 835B in 1s (422B/s)
Reading package lists... Done
W: GPG error: [http://ftp.us.debian.org](http://ftp.us.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
5. Some research suggested getting this key by running:
> gpg --keyserver hkp://subkeys.pgp.net --recv-keys  9AA38DCD55BE302B
gpg --export --armor   9AA38DCD55BE302B| sudo apt-key add -It returned: 
> gpg: requesting key 55BE302B from hkp server subkeys.pgp.net
gpg: key 55BE302B: public key "Debian Archive Automatic Signing Key (5.0/lenny) <ftpmaster@debian.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
6. I then ran:
> sudo apt-get update && sudo apt-get upgrade
And it's still coming back with that "somthing wicked"
> Err [http://ftp.us.debian.org](http://ftp.us.debian.org) sid Release.gpg               
  Something wicked happened resolving 'ftp.us.debian.org:http' (-5 - No address associated with hostname)
Ign [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) sid/main Translation-en
Ign [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) sid/main Translation-en_GB
Hit [http://ftp.us.debian.org](http://ftp.us.debian.org) sid Release
Hit [http://ftp.us.debian.org](http://ftp.us.debian.org) sid/main Sources/DiffIndex
Hit [http://ftp.us.debian.org](http://ftp.us.debian.org) sid/main i386 Packages/DiffIndex
W: Failed to fetch [http://ftp.us.debian.org/debian/dists/sid/Release.gpg](http://ftp.us.debian.org/debian/dists/sid/Release.gpg)  Something wicked happened resolving 'ftp.us.debian.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Please, any clues? What I find odd is that I didn't have these problems on my machine but I did on my dad's. I presume I have different repos set up in Synaptic... or something.

Thanks in advance.

PS: Forgot to mention that I tried looking for alternative servers in Synaptic, to no avail.

---

### Post by QLee on 2010-11-11
[QUOTE=demonboy]...
And it's still coming back with that "somthing wicked"
Please, any clues? What I find odd is that I didn't have these problems on my machine but I did on my dad's. I presume I have different repos set up in Synaptic... or something.
...[/QUOTE]
Jamie, why are you using Debian Sid(unstable) repositories on your Ubuntu system, you're too inexperienced to do that successfully all the time, if you continue you risk getting some sort of "mixed" system that will only give you more grief.

[OT] On an unrelated topic, I like that wireless booster/ network interface combo at the top of your mast, I think I could use one myself.

---

### Post by QLee on 2010-11-11
Having a lot of trouble with my connection dropping this morning (stormy here), probably going to go dark after this but there will be somebody to help you with samba.

I hope having the sid repository hasn't already caused an issue. While it is possible to grab packages from outside one's own release version and/or distro, it is not something that can be explained easily or done easily until one has a good understand of what is involved (i.e. how a package manager works and how "holding" or "pinning" works), thus it is not suitable for beginners. Sometimes it is simple, sometimes it is quite complex.

I know you are in a hurry, probably want to get back where it is warm (my ex, does the "season" in India too). However, I hope you do consider reading the documentation I gave you the links for, sometimes hurrying is counter-productive and actually takes longer.

Om.

---

### Post by demonboy on 2010-11-11
Yep, I've been saving all the links to read when I return to India. That's when I'll have time to go through it properly.

The problem is my father's machine, which I have to sort out now. I thought it was set up identically to mine and I had no problems with Samba, so my confusion is why I should have this problem at all. 

BTW, the setup at the top of the mast was brilliant whilst it worked. A few storms later and I had to take it down. Still to be repaired!

---

