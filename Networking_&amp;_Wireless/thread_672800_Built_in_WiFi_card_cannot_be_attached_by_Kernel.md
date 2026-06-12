---
title: "Built in WiFi card cannot be attached by Kernel"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Contess on 2008-01-20
Hello
I am trying to get WiFi to work on a Acer Aspire 5052. The built in WiFi card shows up under Device Manager:
RS 480 PCI Bridge / AR 5006 EG 802.11 b/g Wireless PCI Express adapter
On the right hand side in the Device Tab, it states the following:
Vendor: Atheros COmmunications
Device: AR 5006 EG 802.11 b/g Wireless PCI Express adapter
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

My system does not assign an interface to the device as well, the only ones I can see are lo0 and eth0 but not ath0 or wifi0

After much drama getting this thing to work, digging through all available help forums and so on, I noticed now the following entry in /var/log/syslog :
Jan 20 00:22:27 ubuntu kernel: [  120.052595] wifi%%d: unable to attach hardware: 'Hardware revision not supported'  (HAL Status 13)

Does that mean I am out of luck with this device and really need to buy a pcmcia wifi card or could there be a workaround ?

Would be great if anyone could shed some light into this.

Thank you very much

Contessa

---

### Post by Contess on 2008-01-20
Sorry,, I forgot to mention that the Ubuntu version is 7.10

---

### Post by tturrisi on 2008-01-20
in a root terminal:

```
apt-get install subversion build-essential linux-headers-`uname -r`
cd /usr/src
svn -r 2834 checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make
make install
depmod -ae
modprobe ath_pci

```

---

### Post by Contess on 2008-01-20
> **tturrisi said:**
> in a root terminal:

```
apt-get install subversion build-essential linux-headers-`uname -r`
cd /usr/src
svn -r 2834 checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make
make install
depmod -ae
modprobe ath_pci

```

Hello
thanks for your reply. I tried that but something doesn't quite work with that:

Here the steps I have taken:

(pwd is /)
########################
root@eng:/# apt-get install subversion build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate
root@eng:/#

root@eng:/# cd /usr/src
root@eng:/usr/src# 

root@eng:/usr/src# svn -r 2834 checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng
The program 'svn' is currently not installed.  You can install it by typing:
apt-get install subversion
bash: svn: command not found
root@eng:/usr/src# 
#################

obviously, I didn't do the rest:
cd madwifi-ng
make
make install
depmod -ae
modprobe ath_pci



What am I missing here.

Thanks for the help, it is very much appreciated

Contessa

---

### Post by kevdog on 2008-01-20
That's really weird.  Try the following

sudo aptitude update
sudo aptitude install subversion

---

### Post by Contess on 2008-01-20
contessa@eng:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB      
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://www.mumblyworld.info](http://www.mumblyworld.info) gutsy Release.gpg                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB [4405B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages               
Ign [http://www.mumblyworld.info](http://www.mumblyworld.info) gutsy/main Translation-en_GB                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://www.mumblyworld.info](http://www.mumblyworld.info) gutsy Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://www.mumblyworld.info](http://www.mumblyworld.info) gutsy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                     
Hit [http://www.mumblyworld.info](http://www.mumblyworld.info) gutsy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                           
Fetched 4978B in 8s (585B/s)                                                    
Reading package lists... Done
contessa@eng:~$ sudo aptitude install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for subversion
The following packages are unused and will be REMOVED:
  erlang-base libpq5 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.2MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 90881 files and directories currently installed.)
Removing erlang-base ...
Searching for services which depend on erlang and should be stopped...none found.
Killing epmd...it is not running.
Removing libpq5 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
contessa@eng:~$ 

#
#
#
# Then I did the same again:

contessa@eng:~$ su
Password: 
root@eng:/home/contessa# apt-get install subversion build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate
root@eng:/home/contessa# cd /usr/src
root@eng:/usr/src# svn -r 2834 checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng
The program 'svn' is currently not installed.  You can install it by typing:
apt-get install subversion
bash: svn: command not found
root@eng:/usr/src# apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate
root@eng:/usr/src# 


## There seems to be something seriously wrong huh ?!


Contessa

---

### Post by kevdog on 2008-01-20
Is subversion in the universe or multiverse repository?  I'm not sure of the answer.  Its really strange.

Here is the subversion homepage:
[http://subversion.tigris.org/](http://subversion.tigris.org/)

Maybe that will help you.  Ive never had problems installing subversion before.

---

### Post by Contess on 2008-01-20
I'll have a look at that. thx

---

### Post by Contess on 2008-01-21
Hello again

I reinstalled ubuntu but the problem remains the same.

Then I checked out [http://subversion.tigris.org/](http://subversion.tigris.org/)
and downloaded the package and the dependencies tar.gz but it was beyond me to successfully install subversion:

this is what happens when I do ./configure in the untared Subversion dir:

contessa@contessa:~/Desktop/subversion-1.4.6$ ./configure
configure: Configuring Subversion 1.4.6
configure: creating config.nice
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


Well.,, I am utterly frustrated. Thanks for trying to help me out, I am sorry that I am unable to follow even simple steps, which makes helping me difficult. I really liked the look and feel of Ubuntu and admittedly it is the most user friendly UNIX derived OS I've ever looked at.  

Thanks and regards

Contessa
..about to give up :-(

---

### Post by Contess on 2008-01-21
Hello again

I reinstalled ubuntu but the problem remains the same.

Then I checked out [http://subversion.tigris.org/](http://subversion.tigris.org/)
and downloaded the package and the dependencies tar.gz but it was beyond me to successfully install subversion:

this is what happens when I do ./configure in the untared Subversion dir:

contessa@contessa:~/Desktop/subversion-1.4.6$ ./configure
configure: Configuring Subversion 1.4.6
configure: creating config.nice
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


Well.,, I am utterly frustrated. Thanks for trying to help me out, I am sorry that I am unable to follow even simple steps, which makes helping me difficult. I really liked the look and feel of Ubuntu and admittedly it is the most user friendly UNIX derived OS I've ever looked at.  

Thanks and regards

Contessa
..about to give up :-(

---

### Post by tturrisi on 2008-01-21
Well the drivers you need are in the restricted mioduloes package, madwifi-ng.  Try & find then using synaptic and installl them that way.

---

### Post by Contess on 2008-01-21
Hi

..ok I try that. thx for the hint.

---

### Post by Contess on 2008-01-25
> **tturrisi said:**
> in a root terminal:

```
apt-get install subversion build-essential linux-headers-`uname -r`
cd /usr/src
svn -r 2834 checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make
make install
depmod -ae
modprobe ath_pci

```

Hello again

after installing subversion, the above commands, installing madwifi worked all fine :-)
Going to do a reboot now and report back again asap

---

