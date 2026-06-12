---
title: "How can I reinstall Network Mnager from Ubuntu cd?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-06
I uninstalled network manager out of frustration at trying to get my internet working and thought I could reinstall from the Ubuntu cd. I tried synaptic but it won't get it off the cd. Any help would be appreciated.

---

### Post by Methuselah on 2010-01-06
Insert the CD.
In the System->Administration->Software sources menu option, check the CD in the **installable from CD section**.
You can then try to reinstall Network-Manager.

---

### Post by iponeverything on 2010-01-06
I don't think that you need to get it from CD as the system should have it cached already.

from the prompt:

```

cd /var/cache/apt/archives
sudo dpkg -i network-manager*

```

---

### Post by ThePinkWitch on 2010-01-06
I checked the install from cd and it didn't work :)

---

### Post by ThePinkWitch on 2010-01-06
> **iponeverything said:**
> I don't think that you need to get it from CD as the system should have it cached already.

from the prompt:

```

cd /var/cache/apt/archives
sudo dpkg -i network-manager*

```

I tried this but it said no such file or directory..I think when i uninstalled Network manager I purged the cache as well :( guess I'll have to reinstall Ubuntu AGAIN (third time) Getting a lil grumpy now. I've been trying to resolve the issues with the internet for days now. Thanks guys.

---

### Post by iponeverything on 2010-01-06
> **ThePinkWitch said:**
> I tried this but it said no such file or directory..I think when i uninstalled Network manager I purged the cache as well :( guess I'll have to reinstall Ubuntu AGAIN (third time) Getting a lil grumpy now. I've been trying to resolve the issues with the internet for days now. Thanks guys.

A reinstall is overkill.

Do this. Open a terminal.

```
cd /etc/apt
sudo mv sources.list sources.list.original
sudo cat > sources.list

```
paste in the following line modified for your release and hit ctrl-c
(just edited it to be 9.10)

```

deb cdrom:[Ubuntu 9.10_Karmic_Koala - Release i386 (20070419.1)]/ karmic main restricted

```

Then do:

```
sudo apt-get install network-manager-gnome network-manager
```

After you install install network-manager put your original sources.list back into place.

---

### Post by Cheesemill on 2010-01-06
If it's the Live CD your using then I'm afraid network-manager isn't on it.

---

### Post by ThePinkWitch on 2010-01-06
"After you install network-manager put your original sources.list back into place." S

Sorry say what? :D

---

### Post by ThePinkWitch on 2010-01-06
> **Cheesemill said:**
> If it's the Live CD your using then I'm afraid network-manager isn't on it.

Oh because Network Manager was on when I first installed I thought it was :D ok ty :)

---

### Post by iponeverything on 2010-01-06
> **ThePinkWitch said:**
> "After you install network-manager put your original sources.list back into place." S

Sorry say what? :D


```

cd /etc/apt
sudo cp sources.list.original sources.list 

```

---

### Post by ThePinkWitch on 2010-01-06
When I do this 
cd /etc/apt
sudo mv sources.list sources.list.original
sudo cat > sources.list
I get Bash permission denied

---

### Post by iponeverything on 2010-01-06
> **ThePinkWitch said:**
> When I do this 
cd /etc/apt
sudo mv sources.list sources.list.original
sudo cat > sources.list
I get Bash permission denied


try this instead..
```

cd /etc/apt
sudo bash
cp sources.list.original sources.list.original2
mv sources.list sources.list.original
cat > sources.list

```
paste in the line. hit Ctrl-C and do:
```

exit
```

---

### Post by ThePinkWitch on 2010-01-06
Ok I did that...what wa supposed to happen? it just went back to etc/apt ius that right? I may have made a mistake it's quite a lot to write down then type

---

### Post by iponeverything on 2010-01-06
now do:

```
sudo apt-get install network-manager-gnome network-manager
```

---

### Post by iponeverything on 2010-01-06
> **ThePinkWitch said:**
> Ok I did that...what wa supposed to happen? it just went back to etc/apt ius that right? I may have made a mistake it's quite a lot to write down then type

You could paste the lines into a file save it onto a thumb drive and open the file on the other machine..

---

### Post by ThePinkWitch on 2010-01-06
> **iponeverything said:**
> You could paste the lines into a file save it onto a thumb drive and open the file on the other machine..
ok If I need to start over I'll do that...TY so much for helping with this. It's really nice of you :)

---

### Post by Cheesemill on 2010-01-06
> **iponeverything said:**
> now do:

```
sudo apt-get install network-manager-gnome network-manager
```

This isn't going to work as he doesn't have internet access, the Live CD doesn't have the network-manager package on it.

---

### Post by nothingspecial on 2010-01-06
Assuming you have working wireless internet and have just removed network manager by mistake, you could get a connection and install from the command line.
```

sudo ifconfig wlan0 up

sudo iwconfig wlan0 essid networkname_here


sudo iwconfig wlan0 key passphrase_here

sudo dhclient

sudo apt-get install network-manager
```

---

### Post by ThePinkWitch on 2010-01-06
> **iponeverything said:**
> You could paste the lines into a file save it onto a thumb drive and open the file on the other machine..

I did that and this is what I got
kayte@kaytesRocket:~$ sudo apt-get install network-manager-gnome network-manager[sudo] password for kayte: 
E: Type 'c' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
kayte@kaytesRocket:~$ cd /etc/apt
kayte@kaytesRocket:/etc/apt$ 
kayte@kaytesRocket:/etc/apt$ sudo bash
root@kaytesRocket:/etc/apt# 
root@kaytesRocket:/etc/apt# cp sources.list.original sources.list.original2
root@kaytesRocket:/etc/apt# 
root@kaytesRocket:/etc/apt# mv sources.list sources.list.original
root@kaytesRocket:/etc/apt# 
root@kaytesRocket:/etc/apt# cat > sources.list^C
root@kaytesRocket:/etc/apt# exit
exit
kayte@kaytesRocket:/etc/apt$ sudo apt-get install network-manager-gnome network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package network-manager-gnome is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package network-manager-gnome has no installation candidate
kayte@kaytesRocket:/etc/apt$ 

I must have done something wrong :(

---

### Post by iponeverything on 2010-01-06
You left out one step. After:

```
cat > sources.list


```

type this line:

> deb cdrom:[Ubuntu 9.10_Karmic_Koala - Release i386 (20070419.1)]/ karmic main restricted

Hit Ctrl-C 

then do:
```
sudo apt-get install network-manager-gnome network-manager

```

---

### Post by ThePinkWitch on 2010-01-06
I downloade Network Manager on the other computer. Its a tar.bz2 file. How would I use this? Thanks all for your help. If this doesn't work i'll have to reinstall Ubuntu for the third time. BTW..I'm am a she not a he :)

---

### Post by iponeverything on 2010-01-06
> **Cheesemill said:**
> This isn't going to work as he doesn't have internet access, the Live CD doesn't have the network-manager package on it.

The live CD and the install CD are one and the same. A fresh install from the CD has the network-manager installed. So.. I fail to see why you think that the .deb is not on the CD.

---

### Post by iponeverything on 2010-01-06
> **ThePinkWitch said:**
> I downloade Network Manager on the other computer. Its a tar.bz2 file. How would I use this? Thanks all for your help. If this doesn't work i'll have to reinstall Ubuntu for the third time. BTW..I'm am a she not a he :)

I don't think that is going to do you much good, as your going to be missing the build dependencies.  If you pull down .deb you can install it with:

```
dpkg -i network-manager* 


``` 

when you are in the same directory as the .deb.

---

### Post by iponeverything on 2010-01-06
I left out a step.. 

After you add the line to your sources.list do:

```
sudo apt-get update


```

Then do the 

```
sudo apt-get install network-manager-gnome network-manager
```

---

### Post by ThePinkWitch on 2010-01-06
oh ok :( it was just a thought seeing as I can't seem to get it loaded even tho I tried theose commands. I must have made a mistake somewhere. Maybe the last bit when you said press control c then exit. It makes sense to me that if Network Manger is already installed when I first use ubuntu it must be on the cd. Thanks again for helping me :) I'll try to install from the dowloaded file..if not I'll try your commands once more. Its 11:30pm so one last try.

---

### Post by ThePinkWitch on 2010-01-06
> **iponeverything said:**
> I don't think that is going to do you much good, as your going to be missing the build dependencies.  If you pull down .deb you can install it with:

```
dpkg -i network-manager* 


``` 

when you are in the same directory as the .deb.

it produced this message: requested operation requires superuser priviledge.

---

### Post by ThePinkWitch on 2010-01-06
> **iponeverything said:**
> I left out a step.. 

After you add the line to your sources.list do:

```
sudo apt-get update


```

Then do the 

```
sudo apt-get install network-manager-gnome network-manager
```

is that for the code you gave me earlier? where i press control C and exit?

---

### Post by iponeverything on 2010-01-06
find the package here:

[http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=karmic&section=all)

put "sudo" in front of the command to execute it with supervisor privileges.

BTW -- You are very tenacious.  ;)

If you reinstall ---- 
You might try install 9.04 instead of 9.10 some people are having much better luck with it..

---

### Post by ThePinkWitch on 2010-01-06
"BTW -- You are very tenacious." 
Is that a nice way of saying I'm stubborn :D

You are very patient..thankyou :)

---

### Post by lotharmat on 2010-01-06
> **ThePinkWitch said:**
> "BTW -- You are very tenacious." 
Is that a nice way of saying I'm stubborn :D

You are very patient..thankyou :)

Tenacious - Determined to get what you want. Persistent!

It is a good quality!:)

---

### Post by ThePinkWitch on 2010-01-06
"Tenacious - Determined to get what you want. Persistent!

It is a good quality!" Thanks :) 
I'm giving up now :D I'm going to reinstall in the morning (it's 12:45am) and continue to bang my head on a brick wall and try to get my wireless internet working again. Which started this whole saga LOL. G'night evryone especially iponeverything who has helped me so much :)byeeeeeee

---

### Post by iponeverything on 2010-01-06
Ok.. I found a 9.10 install CD. I had plenty of server install CD's, but no Desktop install CD's.

If you have not re-install by the time you read this:

pop the CD into the drive:

```

sudo mount /dev/cdrom
cd /media/cdrom0/pool/main/n/network-manager/
sudo dpkg -i network-manager*
cd /media/cdrom0/pool/main/n/network-manager-applet/
sudo dpkg -i network-manager*

```

---

### Post by ThePinkWitch on 2010-01-06
I broke apt-get :(

kayte@kaytesRocket:~$ apt-get
apt 0.7.23.1ubuntu2 for i386 compiled on Oct 15 2009 19:23:21
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
kayte@kaytesRocket:~$ sudo apt-get check
[sudo] password for kayte: 
E: Type 'sudo' is not known on line 2 in source list /etc/apt/sources.list
E: The list of sources could not be read.
kayte@kaytesRocket:~$

---

### Post by ThePinkWitch on 2010-01-06
Thanks for all the help...BIG CYBER HUG!!!!!! :) I give up now. I'll reinstall Ubuntu once more and If I can't get internet to work I'll have to go back to windoze :( Thanks again :D

---

### Post by nothingspecial on 2010-01-07
You didn`t break apt-get, you just edited your sources.list incorrectly.

Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by Cheesemill on 2010-01-07
> **iponeverything said:**
> The live CD and the install CD are one and the same. A fresh install from the CD has the network-manager installed. So.. I fail to see why you think that the .deb is not on the CD.
 
It's not on the Live CD because the Live CD doesn't have any packages on it.
 
The Live CD contains a squashed filesystem of an installed system which is decompressed onto your drive when you install, it doesn't have any packages in .deb format on it.
 
The Alternate CD contains all of the packages needed to install a system, it installs them one at a time from their .deb files (just  like one big apt-get install .... command).

---

### Post by slakkie on 2010-01-07
Setting up a wired connection from the command line isn't that hard: 

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

After you have setup a temp connection via the cli you can use the default sources.list:

```

### Karmic 9.10
# Required     
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
# Recommended                                                                                  
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse       
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse  
# Optional                                                                                     
deb http://packages.medibuntu.org/ karmic free non-free                                        
#deb-src http://packages.medibuntu.org/ karmic free non-free                                   
deb http://archive.canonical.com/ubuntu/ karmic partner                                        
#deb-src http://archive.canonical.com/ubuntu/ karmic partner                                   
deb http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse      
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse     
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

```

Repleace karmic with your particular release (lsb_release -cs). And install networkmanager.

In short, assuming you have a cable plugged in your network card:

```

sudo dhclient eth0 
sudo nano /etc/apt/sources.list # use the sources I posted above
sudo aptitude update
sudo aptitude install network-manager
# Restart your networking:
sudo ifdown eth0
sudo /etc/init.d/NetworkManager start
# Or reboot
# sudo reboot

```

---

### Post by iponeverything on 2010-01-07
> **Cheesemill said:**
> It's not on the Live CD because the Live CD doesn't have any packages on it.
 
The Live CD contains a squashed filesystem of an installed system which is decompressed onto your drive when you install, it doesn't have any packages in .deb format on it.
 
The Alternate CD contains all of the packages needed to install a system, it installs them one at a time from their .deb files (just  like one big apt-get install .... command).

Pop the "live CD" into drive. Now do:

```

sudo mount /dev/cdrom
cd /media/cdrom0/pool/main/n/network-manager/
ls

```

Now.. It does appear that perhaps you might be slightly misguided in your repeated assertions that the live CD does not contain .deb files and that everything is just slapped onto the system in one swoop. Observation of the install as well inspection of the log files left behind after the install and a direct inspection of the CD, does not seem to support your assertions.

---

### Post by Cheesemill on 2010-01-07
I was generalising when I said there were no packages, there are actually 22 on the Live CD (Karmic) which are packages needed for certain operations during installation (fakeroot, dkms, gcc, etc.)
 
There is no network-manager package on my Live CD, the only packages in /pool/main/n are ndisgtk and ndiswrapper.
 
This is also the reason why you can only update from the Alternate CD and not the Live CD, **because the Live CD doesn't contain the packages needed to install a system.**

---

### Post by iponeverything on 2010-01-07
I surrender - I am wrong! I respectfully request that you take mercy on your defeated opponent.  

I was indeed mounting the alternate install via loopback and seeing the debs. 

I mounted the squashfs filesystem via loopback and it does not contain a .deb

---

### Post by Cheesemill on 2010-01-07
> **iponeverything said:**
> I surrender - I am wrong! I respectfully request that you take mercy on your defeated opponent. 
 
I was indeed mounting the alternate install via loopback and seeing the debs. 
 
I mounted the squashfs filesystem via loopback and it does not contain a .deb
 
No worries mate :)

---

### Post by ThePinkWitch on 2010-01-07
I thank you all very much..I reinstalled now and still have problems with connecting to the internet, Still drops out often and says it's connected but won't load a webpage or download anything. I'm thinking of trying previous version of Ubuntu. Thanks for all your help. :):P

---

