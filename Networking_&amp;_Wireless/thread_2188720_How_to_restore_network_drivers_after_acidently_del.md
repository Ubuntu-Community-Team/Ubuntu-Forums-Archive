---
title: "How to restore network drivers after acidently deleted"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by bitesh_sharma7 on 2013-11-18
I accidently deleted the network manager in Ubuntu 13.04. I do not want to reinstall it, can i recover it?? are there any solutions??

---

### Post by varunendra on 2013-11-20
Hello Bitesh, Welcome to the forums !

There is no way to actually 'Recover' deleted/removed applications except reinstalling them. Installer files of applications that are manually downloaded via apt/synaptic/software-center etc. are cached in /var/cache/apt/archives directory, so you don't need to download them again if needed to reinstall. But the default applications once removed can only be restored by downloading from net.

If using a wired connection, it is as easy to configure manually as running two commands -
```
sudo ifconfig eth0 <IP address>
sudo route add default gw <gateway's IP address>
```
..assuming your ethernet interface's logical name is eth0.

If it is a wireless connection, it is a bit more work to make it work. This one seems to be a perfect comprehensive guide for that : [http://askubuntu.com/a/16588](http://askubuntu.com/a/16588)

You may also try this to do an offline installation of the required packages (for NM's re-installation) -
```
apt-get install --print-uris network-manager-gnome
```
It will give the download URIs of all the required packages at the bottom of the output. Use these to download the packages on a different computer with internet access > copy them back to your Ubuntu computer > install with "dpkg -i *" (while being in the same directory where the downloaded .deb files are copied).

---

