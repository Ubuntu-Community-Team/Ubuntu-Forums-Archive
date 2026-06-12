---
title: "How can I install VirtualBox?"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-01-19
I can't find it in the Ubuntu Software Center even though every repository is enabled.

Can I install it from Terminal? How?

---

### Post by fugaki on 2010-01-19
try sudo apt-get install virtualbox-ose

---

### Post by drs305 on 2010-01-19
Or to get the non-OSE version, go here, download the .deb for your system and double click on the file to install it.
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

When you double click, the file should install. If it doesn't, you can install it by changing to the directory of the downloaded file and run:
```

sudo dpkg -i /path/filename.deb

```

There are also instructions on the page for adding the repository and public key, which will be allow you to use Synaptic to install and update it.

Also see the note about the **dkms** file.

---

### Post by baddog144 on 2010-01-19
If you install the ose version, it may be necessary to run 
```

sudo /etc/init.d/qemu_kvm stop

```
in terminal before you start virtualbox. I had an issue with vbox today, and running that fixed it. Just a heads up ;)

---

### Post by phillychease on 2010-01-19
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
from Vbox's website. the deb files there. choose you're ubuntu version. download. easy!

oh i believe that the ose  version doesnt have USB support.
correct me if im wrong.

---

### Post by thatguruguy on 2010-01-19
> **phillychease said:**
> 
oh i believe that the ose  version doesnt have USB support.
correct me if im wrong.

You're right.  It's better to go get the version from the virtualbox site.

---

### Post by Goveynetcom on 2010-01-19
Yes, assuming you want the added support of USB you need the one off of the VirtualBox website but
```
sudo get-apt install virtualbox
```
should work. The OSE (Open Source Edition) version does not support USB but both are free.

---

### Post by PenguinInside on 2010-01-20
Other than the USB thing, open-source VirtualBox works great.

Note: If you have a USB mouse, it works on a passthrough basis in VirtualBox.

---

### Post by Bryan55 on 2010-02-02
Hi

I have just install VirtualBox direct from their site.

I all so ran the **dkms** packages and got this

-------------------------------------------------------------------------------

bryan@Bydand:~$ sudo apt-get install dkms
[sudo] password for bryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libdigest-sha1-perl libnet-ip-perl libnet-dns-perl
  libfile-find-rule-perl libdate-calc-perl libcarp-clan-perl libtext-glob-perl
  libconfig-tiny-perl libtommath0 libdigest-hmac-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bryan@Bydand:~$ 
----------------------------------------------------------------------------------------------

My question is should I remove the used packages?

( I'm very new to Linux)

Thanks for any help.

Bryan.

---

### Post by Flimm on 2010-02-02
If I were you I would remove them, by running this in a terminal:
```
sudo apt-get autoremove
```

All those packages have "lib" at the start of their names, which mean they are libraries. They're required by some programs to run correctly but they're not useful in themselves as applications. apt-get autoremove is smart enough to only remove packages like these that you don't need any more, maybe you've uninstalled a program that used to need it.

If you install a package yourself, apt-get will never suggest you remove it as it marks it as "manually installed", so you needn't worry.

---

### Post by ikt on 2010-02-02
> **Bryan55 said:**
> Hi

I have just install VirtualBox direct from their site.

I all so ran the **dkms** packages and got this

-------------------------------------------------------------------------------

bryan@Bydand:~$ sudo apt-get install dkms
[sudo] password for bryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libdigest-sha1-perl libnet-ip-perl libnet-dns-perl
  libfile-find-rule-perl libdate-calc-perl libcarp-clan-perl libtext-glob-perl
  libconfig-tiny-perl libtommath0 libdigest-hmac-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bryan@Bydand:~$ 
----------------------------------------------------------------------------------------------

My question is should I remove the used packages?

( I'm very new to Linux)

Thanks for any help.

Bryan.

Use 'apt-get autoremove' to remove them.

Yeah should be fine, running 'sudo aptitude' instead of 'sudo apt-get' takes care of these small issues by default.

---

### Post by Bryan55 on 2010-02-02
Hi 
Just saw my typo. I did mean the unused ones.

I have now removed them

Thanks.
Bryan.

---

