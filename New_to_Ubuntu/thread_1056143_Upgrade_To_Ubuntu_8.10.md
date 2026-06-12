---
title: "Upgrade To Ubuntu 8.10?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Apexnc on 2009-01-31
I have Ubuntu 6.06 LTS installed on this computer I am using now. It works fine, however I would like to upgrade to Ubuntu 8.10. I have downloaded and created an installation CD for Ubuntu 8.10 and even installed it on my desktop and it works great.  The problem is that for some reason I am unable to install it on this laptop which is already running 6.06 LTS.  Is it possible for me to automatically upgrade this distribution to 8.10.  I read the manual about using the command sudo apt-get distro-upgrade and tried it and it performed something but did not upgrade to 8.10.  Am I missing something? I don't even know how to uninstall the 6.06 LTS and start over!!!

---

### Post by overdrank on 2009-01-31
> **Apexnc said:**
>   Am I missing something? I don't even know how to uninstall the 6.06 LTS and start over!!!

Hi and welcome, I would suggest upgrading to 8.04 Hardy as it is LTS also. You may upgrade but you will need the [[COLOR="Red"]alternate cd[/COLOR]]("https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by utnubuuser on 2009-01-31
I was under the impression you have to upgrade from 6.06 >> 7.04  >> 7.10 >> 8.04 etc.

I never upgrade, because I've read nothing but posts about upgrade/update broke my this, or upgrade broke my that.  I usually make room an the hard drive, install a new release, import documents and settings, then delete the old version once the new one is up and running.
If you go through the upgrade path,  there's no recourse if something goes wrong, unless you're very capable on the command line.

---

### Post by Apexnc on 2009-01-31
/home/apexnc/Desktop/ubuntu-8.10-alternate-i386.iso
bash: /home/apexnc/Desktop/ubuntu-8.10-alternate-i386.iso: Permission denied

Hello; Thanks for your help: I downloaded and created the alternate installion disk for 8.10 however when I attempted to run it the terminal replied with Permission denied.

---

### Post by cwsnyder on 2009-01-31
The install disk, if you boot from it, will wipe your 6.06 installation, not perform an upgrade.  Canonical says to upgrade to 8.04 from 6.06, then you can upgrade to 8.10.

You probably want to go to the Canonical site to get the correct repository notes.

---

### Post by Paqman on 2009-01-31
> **utnubuuser said:**
> I was under the impression you have to upgrade from 6.06 >> 7.04  >> 7.10 >> 8.04 etc.

Normally yes, but with LTS versions you can go straight from the old one (6.06) to the new one (8.04).

---

### Post by utnubuuser on 2009-02-02
Cool...  Didn't know that.  Thanks.

---

### Post by stchman on 2009-02-02
> **Apexnc said:**
> I have Ubuntu 6.06 LTS installed on this computer I am using now. It works fine, however I would like to upgrade to Ubuntu 8.10. I have downloaded and created an installation CD for Ubuntu 8.10 and even installed it on my desktop and it works great.  The problem is that for some reason I am unable to install it on this laptop which is already running 6.06 LTS.  Is it possible for me to automatically upgrade this distribution to 8.10.  I read the manual about using the command sudo apt-get distro-upgrade and tried it and it performed something but did not upgrade to 8.10.  Am I missing something? I don't even know how to uninstall the 6.06 LTS and start over!!!

How did you originally install Dapper on that laptop.  I would also recommend installing Hardy over Intrepid as Hardy is an LTS version.

If your laptop worked fine under Dapper it will work fine under Hardy.

---

