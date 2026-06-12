---
title: "Ubuntu vs. debian 4"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by joe6966 on 2009-09-13
Hi all,
I have Debian 4 installed on its own hard drive on my desktop PC. I have Ubuntu 9.04 installed on my HP laptop. I have a few questions.
Why is Debian on 3 full DVDs, and Ubuntu fits on a single CD?
Are any of the programs on the Debian DVDs usable in Ubuntu?
I was able to do mostly anything with Debian as a new user that I did with Winblows; however, I didn't learn how to mount my drives so I could access my Windows files in Linux. With Ubuntu, I didn't have to learn how; it was done.

I also recommended Ubuntu to my neighbours who are planning to buy a laptop. Is it true that Linux is safe from malware, spyware, viruses etc.?

---

### Post by ibizatunes on 2009-09-13
Basic debain has more packages install by default, ubuntu have very few, yes linux debain, ubuntu, red hat, or any distro cant really get a virus. linux in general doesnt have the same security flaws as windows
I run linux with NO antivirus

---

### Post by Malta paul on 2009-09-13
Debian comes on multiple disks because it includes a lot of programs.

Ubuntu comes on one disk with essential programs, other programs that you require can be down loaded from the Internet. 

Most Debian file will run on ubuntu but not all.

Don't worry about Viruses the is a built-in firewall in Ubuntu and ClamAv
if you want a scanner.

Check out:[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) 

Have fun

---

### Post by snowpine on 2009-09-13
> **joe6966 said:**
> Hi all,
I have Debian 4 installed on its own hard drive on my desktop PC. I have Ubuntu 9.04 installed on my HP laptop. I have a few questions.
Why is Debian on 3 full DVDs, and Ubuntu fits on a single CD?
Are any of the programs on the Debian DVDs usable in Ubuntu?
I was able to do mostly anything with Debian as a new user that I did with Winblows; however, I didn't learn how to mount my drives so I could access my Windows files in Linux. With Ubuntu, I didn't have to learn how; it was done.

I also recommended Ubuntu to my neighbours who are planning to buy a laptop. Is it true that Linux is safe from malware, spyware, viruses etc.?

Hi Joe,

1. Debian 4 is an older version... Debian 5 "Lenny" is the current version.
2. You only need the first CD/DVD to install Debian; the multi-DVD sets are for users who do not have internet access to install additional applications. Assuming you have a network connection, I recommend the small (100mb) "netinstall" CD, which pulls the latest versions of applications from the web.
3. No; you should never install Debian applications in Ubuntu. You should install Ubuntu applications from the official repository using "Add/Remove Programs" or "Synaptic Package Manager."
4. This guide might help you mount your Windows drive: [http://beginlinux.wordpress.com/2009/03/18/mounting-an-ntfs-drive-in-debian/](http://beginlinux.wordpress.com/2009/03/18/mounting-an-ntfs-drive-in-debian/)
5. Linux is more secure than Windows for most users. You should still follow common sense. :) For example, install applications using Add/Remove or Synaptic (as I mentioned above) rather than downloading random things from the internet... that's the best way to run into trouble with any operating system.

Good luck!

---

### Post by shae on 2009-09-13
With debian, only one CD is required for the desktop install, but they create CD sets that contain all packages from their repositories.  Ubuntu does not do this.

Yes, Linux is generally safer from malware, spyware, viruses, etc. than Windows, but Linux does not offer any additional protection from Phishing, so use OpenDNS and make sure Firefox is checking sites against Google's database.

---

### Post by Hallvor on 2009-09-13
> **ibizatunes said:**
> Basic debain has more packages install by default, ubuntu have very few, yes linux debain, ubuntu, red hat, or any distro cant really get a virus. linux in general doesnt have the same security flaws as windows
I run linux with NO antivirus

Debian does not have many packages installed by default. The Gnome desktop is almost identical to Ubuntu`s.

However, if you want a completely clean slate and a very snappy system you could uncheck the desktop environment box during install. You will then get a command line after the installation is finished. Just type (as root):

```
apt-get update
apt-get install xserver-xorg-core gdm gnome-core
```

After that, start gdm with:

```
/etc/init.d/gdm start
```

... and add the applications you want.

---

