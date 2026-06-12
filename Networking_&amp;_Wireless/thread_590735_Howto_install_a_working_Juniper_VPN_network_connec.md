---
title: "Howto install a working Juniper VPN network connect on Ubuntu 7.10 gutsy gibbon?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by stmau on 2007-10-25
Hi,

I was wondering if someone can make a simple to follow howto for a fresh ubuntu 7.10 install.
I have tried the other tutorials in this forum and searched the web without making it work.
I had it working on one of the previous versions but not for this release.
I know you need ssh and java but which versions etc... Probably dependent on which Juniper IVE
release you are running on to? If anyone from Juniper sees this post please ask internally. 
I will create a case at juniper support and get back to this forum with the info. 

Best regards: Stian

---

### Post by mindlight on 2007-10-25
Hi,
I connected 2 mins ago.

I used this tutorial: [http://ubuntuforums.org/showthread.php?t=232607&highlight=vpn](http://ubuntuforums.org/showthread.php?t=232607&highlight=vpn)

Its not perfect but it works on my gutsy.

I do get a question about su password everytime but it doesnt matter. if I dont type in any password it fails but since the tutorial helped me to install the NC once it works anyway after that question appeared.

If you start your firefox session with gksudo or sudo you wont be needing to change root password etc... but then you always need to gksudo firefox when you need to connect.

---

### Post by stmau on 2007-10-25
Hi!

Thanks I'll try it once I get back on my ubuntu.
Best regrads: Stian

---

### Post by casuarina on 2007-10-29
This script will install Juniper on Ubuntu feisty and Gutsy

untar the attachment and execute
**./Install-Juniper-Ubuntu **

or type

**cat > Install-Juniper-Ubuntu << "EOF"**

paste this in your terminal

[I]#!/bin/bash
echo "Juniper connect will ask for your root password"
echo "Do you have a root Password installed"
read -p "(yes/no) "
if [ "$REPLY" != "yes" ]; then
	if [ "$REPLY" != "no" ]; then
	read -p "Type yes or no : "
	fi
fi
if [ "$REPLY" = "yes" ]; then
echo "yes"
sudo apt-get update
sudo apt-get install firefox openssl libstdc++2.10-glibc2.2 sun-java6-bin sun-java6-jre
jre=$(ls /usr/lib/jvm/java-6-sun-*/jre/plugin/i386/ns7 | grep libjavaplugin_oji.so)
plugins=$(ls /usr/lib/firefox | awk 'length < 8' | grep plugins)
	if [ "$jre" = "libjavaplugin_oji.so" ] & [ "$plugins" = "plugins" ]; then
	cd /usr/lib/firefox/plugins
	sudo ln -s /usr/lib/jvm/java-6-sun-*/jre/plugin/i386/ns7/libjavaplugin_oji.so
	sudo ln -s /bin/true /usr/bin/rpm
	cd /usr/lib/i686/cmov/
	sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so
	fi
echo "Start firefox and connect to server:"
fi
if [ "$REPLY" = "no" ]; then
echo "no"
sudo passwd root
sudo apt-get update
sudo apt-get install firefox openssl libstdc++2.10-glibc2.2 sun-java6-bin sun-java6-jre
jre=$(ls /usr/lib/jvm/java-6-sun-*/jre/plugin/i386/ns7 | grep libjavaplugin_oji.so)
plugins=$(ls /usr/lib/firefox | awk 'length < 8' | grep plugins)
	if [ "$jre" = "libjavaplugin_oji.so" ] & [ "$plugins" = "plugins" ]; then
	cd /usr/lib/firefox/plugins
	sudo ln -s /usr/lib/jvm/java-6-sun-*/jre/plugin/i386/ns7/libjavaplugin_oji.so
	sudo ln -s /bin/true /usr/bin/rpm
	cd /usr/lib/i686/cmov/
	sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so
	fi
echo "Start firefox and connect to server:"
fi
exit 0
EOF[/I]

and execute
**./Install-Juniper-Ubuntu **

---

### Post by shcodip on 2007-10-29
Script worked great for me. Thanks a bunch

---

### Post by sebutler2 on 2007-12-03
Do you use the above script before or after you install the java and the firefox java plugin?

---

### Post by casuarina on 2007-12-28
You can use the script after a fresh ubuntu install.

---

### Post by toddward on 2008-01-06
Was having issues but this worked perfectly.  Thanks for the script!

---

### Post by gusboy on 2008-02-05
Hi All,

I've been able to make a successful VPN connection after installing the script, thanks for the help.

But after logon, I get a shortcut in a webpage and when I click on it, it should open a Remote desktop application. But I get an error message "This terminal session is not supported on your computer".....

How can I manage, that clicking the shortcut will open up the Ubuntu Terminal Server Client, instead of looking for a Windows terminal server client?

All help is welcome, thanks in advance.............

Kind regards,

Gusboy
the Netherlands

---

### Post by bikerTrash on 2008-03-29
Thanks for the script but I still can't connect via Juniper Network Connect to my employer's site. When I launch Netork Connect, I just get a thermometer and then a teeny little box that say's "error". No log that I can see. It works on my other linus box (Fedora 8) so I'm surprised. One odd thing that might be a hint, whenever I launch Synaptic Package Manager, I have to type in my password, not the root pw. I'm new to debian based distro's so maybe this is right.

Here's a screen capture of when I ran the script:

Thanks,

[B]Do you have a root Password installed
(yes/no) yes
yes
[sudo] password for rob:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 5B in 1s (3B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
openssl is already the newest version.
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
The following NEW packages will be installed:
  libstdc++2.10-glibc2.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 329kB of archives.
After unpacking 1384kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libstdc++2.10-glibc2.2 1:2.95.4-24 [329kB]
Fetched 329kB in 1s (171kB/s)                  
Selecting previously deselected package libstdc++2.10-glibc2.2.
(Reading database ... 99965 files and directories currently installed.)
Unpacking libstdc++2.10-glibc2.2 (from .../libstdc++2.10-glibc2.2_1%3a2.95.4-24_i386.deb) ...
Setting up libstdc++2.10-glibc2.2 (1:2.95.4-24) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Start firefox and connect to server:

[/B]

---

### Post by casuarina on 2008-04-01
Try this:

gehau@questular2:/usr/lib/firefox/plugins$ ls
libjavaplugin_oji.so       libtotem-mully-plugin.so
libtotem-basic-plugin.so   libtotem-mully-plugin.xpt
libtotem-basic-plugin.xpt  libtotem-narrowspace-plugin.so
libtotem-gmp-plugin.so     libtotem-narrowspace-plugin.xpt
libtotem-gmp-plugin.xpt    libunixprintplugin.so

if there is another link to a java-plugin, you need to remove it.

---

### Post by bikerTrash on 2008-04-02
Thanks. There was nothing in /usr/lib/firefox/plugins that didn't belong there. However, after running Sun's java executable from [here]("http://www.java.com/en/download/help/5000010500.xml#100") and setting up the soft link like tehy describe, all works well. Odd that the JRE from the synaptic repository doesn't work.

---

### Post by gsker on 2008-05-06
For hardy, you will have to get libstdc++2.10 manually to have the Install-Juniper-Ubuntu script work since it doesn't exist in the apt repository any more.

As of today it's still at

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb)

I did re-link the java plugin to the sun one, but I don't know if I had to.  Other than that, the script above worked fine.

```

cd /usr/lib/firefox/plugins
sudo ln -s -f /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin//i386/ns7/libi386/ns7/libjavaplugin_oji.so

```

Every time I disconnect from the VPN I have to do an ifup eth1 (my normal interface) or an ifdown and then an ifup in order to get my connection back.

Any clues there would be appreciated.

---

