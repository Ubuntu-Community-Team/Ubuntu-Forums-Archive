---
title: "Another PPTP Question"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by markisoot on 2006-10-30
Hi all

I have seen quite a few threads around for the PPTP issues folk have had over the past, but sadly, I have not found one to assist in my problem here.  I am a mainly windows sysadmin but with expereince on RHEL (up2date and yum use)

Basically, I cannot fully install a pptp client yet I have all the packages.

I keep getting dependency problems and when they are resolved, I get more dependancies.

I have the following:
-rw-r--r-- 1 root root  194294 2004-06-19 14:26 php-gtk-pcntl_1.0.0-2_i386.deb
-rw-r--r-- 1 root root  635988 2004-07-26 10:54 php-pcntl_4.3.8-2_i386.deb
-rw-r--r-- 1 root root   32572 2006-08-21 07:20 pptpconfig_20060821-0_all.deb

Which is allegedely all I should need to get a working pptp client running but alas, not so.

I have tried adding the following to my apt listquozl.us.netrek.org/pptp/pptpconfig/ but the apt-get pptp-client (or any incarnation of that) fails.  So I tried downloading teh individual packagesd, but as I said above, this has led to further dependency issues.

As far as I can see, apt-get -f install and apt-get -f upgrade all end successfully but with no required packages.

SO) far I have:
root@bidean:/etc/X11# apt-get install pptpconfig
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages
root@bidean:/etc/X11# apt-get install php-gtk-pcntl
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  php-gtk-pcntl: Depends: libglade0 but it is not installable
                 Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
                 Depends: libxml1 (>= 1:1.8.14-3) but it is not installable
E: Broken packages


There has to be an easier way to get one silly little program installed.  I went to ubuntu as most of the servers I manage are RHEL and having a linux desktop to manage them is great, but if I can`t get this apt-get stuff to work.

Please help the debian noob.

Ta in advance

Mark

---

### Post by mgregg on 2006-11-10
I had the same problems.

To fix, start by editing your /etc/apt/sources.list

uncomment the lines in this section:
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe


Add the following lines at the bottom:
# pptpconfig
#deb http://quozl.netrek.org/pptp/ pptpconfig/
#deb http://quozl.netrek.org/pptp/ php-gtk/
deb http://quozl.linux.org.au/pptp/pptpconfig ./


Notice the new apt source for pptpconfig.

Now, do a

apt-get update.

After that works, 
apt-get install pptpconfig 
sould work again.

---

