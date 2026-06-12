---
title: "Where is the LTSP server in 10.04"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by TEVERTH on 2010-06-18
I downloaded edubuntu 10.04 iso and booted. LTSP is part of the LIVE CD environment but when you install it to HD its gone. I tried getting the LTS packages which seemed to install but nothing actually changed. No LTS no GUI for anything and the cookbook is only for command line junkies - command lines are so yesterday!!!!

---

### Post by bodhi.zazen on 2010-06-18
I do not think the server side of Ubuntu comes with a gui.

Most linux server do not run graphical interfaces.

It does not appear as if the edubuntu pages have been fully updated for 10.04, ouch.

This page explains the various options :

[http://edubuntu.org/Download](http://edubuntu.org/Download)

---

### Post by TEVERTH on 2010-06-18
Well the Edubuntu folks say that their distro is an LTSP one. But their website points to a download that is a workstation one with a LTSP trial in the LIVE CD which works great.
Now I am trying the ubuntu 10.04 cd to see if that works....

---

### Post by haddog on 2010-06-23
> **TEVERTH said:**
> I downloaded edubuntu 10.04 iso and booted. LTSP is part of the LIVE CD environment but when you install it to HD its gone. I tried getting the LTS packages which seemed to install but nothing actually changed. No LTS no GUI for anything and the cookbook is only for command line junkies - command lines are so yesterday!!!!


**NOTE: Read this in it's entirety before attempting. It is a step-by-step of how I got a Lucid Lynx 10.04 LTSP server up and running and the thin-clients able to connect to the LTSP server and run.**

On 06/19/2010, I wanted an LTSP server running on Ubuntu 10.04 Lucid Lynx. First I installed Lucid Lynx using the Ubuntu alternate CD which includes an LTSP installation.

[http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent")

Once you boot up the CD, hit F4. The "Modes" menu will pop up. Select "Install an LTSP Server". Now just move on with the install and complete the installation.

Next I got all my updates installed for the server using:

sudo apt-get update

sudo apt-get upgrade

After all updates were installed I rebooted the LTSP server. Next I set up the LTSP client image using the following command:

sudo ltsp-build-client

Despite getting no error messages during installing and configuring, at the end I got this error:

LTSP client installation ended abnormally

And then it stopped. I searched around and found a solution. The solution was to use the following set of commands instead of sudo ltsp-build-client command:
	
sudo -s

su -

ltsp-build-client

sudo ltsp-update-sshkeys

ltsp-update-image

I rebooted the LTSP server, started up a thin-client and all was good.

---

