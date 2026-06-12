---
title: "Trying to install alien"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by yuriheclipse on 2009-02-09
Hello all,

When I try to do an "apt-get update" I get 404 errors. It's as if the "/feisty" folder doesn't exist... which is confirmed by entering the URL into a browser. There doesn't seem to exist "http://archive.ubuntu.com/ubuntu/dists/feisty" is this correct? If that is correct is there somewhere else I can point to?

(Noob - have patience)

Cheers!

Y

---

### Post by drs305 on 2009-02-09
Welcome to the ubuntu forums!

The feisty repositories were removed when it reached it's end of life last fall and you should seriously consider upgrading to a more recent version.

If you really don't want to upgrade you may be able to find what you are looking for at:
[http://old-releases.ubuntu.com/]("http://old-releases.ubuntu.com/")

---

### Post by bodhi.zazen on 2009-02-09
If at all possible you are best off either upgrading to 8.04 (LTS).

What are you trying to install with alien ? IMO you aer almost always better off either installing from the repos (see above) or from source, using alien only as a last resort.

---

### Post by yuriheclipse on 2009-02-09
Thank you both...

This is a bit of a long story. The reason I am running Kubuntu 7.04 is because it is mandated by the Software mfg of the package this box will be running... and the reason I'm trying to get Alien running is because this box is a DL185. 

A DL185 comes with a standard HP SmartArray Controller (e200) but unfortunately the linux drivers are problematic and write performance is <20MB/s! So I installed an Adaptec 3805 Raid controller and the write perf went to 120MB/s. I guess everything would be OK except that the 3805 doesn't support "inband" LED signaling so I never see the lovely and reassuring flicker of the drive LEDs... which again I could live without, until one of the drives drops dead and I have no idea what to swap... So... I figured I'd install the Adaptec Manager Pkg. which should provide some visibility (and maybe email me) to see what's happening with the RAID but it only comes as a RPM... which brings us back to Alien...

I told you it was a long story...

I guess I'll first try and get the software mfg to provide a more recent version of Kubuntu... if that fails I'll try the old repositories (thanks for the link).

I'm a windows fella... so this has been a bit of a struggle for me. Thanks for helping.

---

### Post by kansasnoob on 2009-02-09
> **bodhi.zazen said:**
> If at all possible you are best off either upgrading to 8.04 (LTS).

What are you trying to install with alien ? IMO you aer almost always better off either installing from the repos (see above) or from source, using alien only as a last resort.

+1! Feisty is history!

As far as alien goes, I know it's in the repos since Gutsy. I have, for instance, found that XNView installs better using the .rpm w/alien!

I dunno why???????????

---

