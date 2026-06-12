---
title: "[SOLVED] vm ware on 8.10"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by jboy012000 on 2008-12-29
Hi All,

Hope everyone had a nice Christmas, I was wondering if anyone was able to install succesfully vmware on Ubuntu 8.10, I have tried virtual box but it will not install my guest os, it gets so far then freezes my entire computer so I have to pull the plug. So I really need vmware.

Thanks

John

---

### Post by Malalo on 2008-12-29
Hi John,

I've been running VMWare successfully for the past 3 months now. It works perfectly well, except for one little "inconvenience", namely that I have 2 monitors, with a spanned desktop. I open 2 windows of VMWare and put each of them on a different monitor, with a different Virtual Machine on each window. If I click on a Menu in VMWare, then click elsewhere to cancel, the second windows disappears and both my VMs are in the same window. If I select an item within the menus, then no problem.
It is really a very small inconvenience but when it happens, it's really frustrating as I need to close both VMs, then restart VMWare to get my 2 separate windows again...
Other than that, nooooo problems.... running version 6.5.1 build-126130

---

### Post by jboy012000 on 2008-12-29
are you running ubuntu 8.10?

---

### Post by Malalo on 2008-12-29
Yes, updated from 8.04 (not a fresh install)

---

### Post by DGortze380 on 2008-12-29
What guest are you trying to install?

---

### Post by jboy012000 on 2008-12-29
Hi All,

ok I have got vmware running on my machine running Ubuntu 8.10, please see below how I did it.

ok first of all the version of vmware I am installing is vmware server edition 2

first of all goto [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/) when the vmware website page comes up click on the download link.

On the next page, log in with your existing vmware account or create a new one

Follow the on-screen instructions. At the end, you should receive an email with a link to your download page. On the download page, you should see two license numbers, one for Windows and one for Linux. Write down or save the one for Linux and scroll down.

Then download the VMware Server for Linux TAR image (not the RPM image!) to your desktop

Then open a terminal window and run the following command to install some necessary packages:

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

Then go to the location where you saved the VMware Server .tar.gz file, e.g. /home/your user name/Desktop

cd /home/john/Desktop

Unpack the VMware Server .tar.gz file and run the installer:

tar xvfz VMware-server-*.tar.gz
cd vmware-server-distrib
sudo ./vmware-install.pl

The installer will ask you a lot of questions. You can always accept the default values simply by hitting <ENTER>.

When the installer asks you

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines]

you can either accept the default value or specify a location that has enough free space to store your virtual machines.

At the end of the installation, you will be asked to enter a serial number:

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:

Fill in your serial number for VMware Server.

Now be careful with this, I got confused and wiped off all my desktop icons but lets be honest no major problem.

After the successful installation, you can delete the VMware Server download file and the installation directory:

cd /home/your user name/Desktop
rm -f VMware-server*
rm -fr vmware-server-distrib/

Now you have to create a password for VMware, the username is "root" but to create the password follow the command below

sudo passwd root

Create your password and your done.

Now VMware Server 2 does not have a desktop application for managing your virtual machines it runs through a web browser, to access it open a web browser session and type in the address bar [http://127.0.0.1:8222](http://127.0.0.1:8222)

This will bring up the login screen, type in root as the username and whatever password you created for the password.

Click ok

Big smiles jobs a good one.

---

### Post by weigh2tall on 2009-01-22
Thanks for this post.  I was trying to figure out why my password wouldn't work for root.  Hadn't run into this problem with previous VMWare Server editions.  This works for me Using VMWare Server 2 and Ubuntu 7.10

---

### Post by maxheartless on 2009-02-10
Hi, has anyone managed to install VMWare Server on 8.10?
I'm trying to install on an AMD quad-core based system, but no joy.

Install halts because it's unable to build the 'vmmon' module. 

Please help!

---

