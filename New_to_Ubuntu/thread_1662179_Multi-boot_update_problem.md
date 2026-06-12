---
title: "Multi-boot update problem"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by yellowpike on 2011-01-07
Greetings and a Happy New Year to ALL!

I'm running a Thinkpad T-43 w/2GB ram, a 60GB HD with Peppermint (Linux) and Windows 7 along with a a second 40GB HD with Ubuntu 10.04 and Mint 10.
All OS's boot fine and I am able to use all 4 without any trouble. All Linux versions are properly listed in the boot menu, as is Win7, and all "recovery mode" versions for each Linux OS is also properly listed.
For Ubuntu, versions 2.6.32-26-generic through 2.6.32.21-generic are listed with 2.6.32-26 set as my default boot.

As of late attempts at updating Ubuntu (using Gnome or KDE) via Update Manager result in the following error:

E: linux-image-2.6.32-27-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-27-generic-pae: subprocess installed post-installation script returned error exit status 2
E: grub-pc: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

thus 2.6.32-27 is not installed and a crash report is generated.

The second HD was removed from another T-43 a while back and until now I've NOT had any problems booting or running anything. 
I would imagine the problem is caused by the fact that the second HD (which houses Ubuntu/Mint) was installed/configured on the former machine but frankly, being a newbie, I'm not able to nail this bad-boy.
I've tried update-grub
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
Is the result

Respectfully, I ask for your help.
Thank You
yellowpike

---

### Post by oldfred on 2011-01-07
I have been running the 64bit version, but I understand that if you have more than 3GB of memory it now defaults to the pae version. But then if you move it to a machine with only 2GB, it probably wants just the generic version.

I normally post this for a chroot but you can use sudo -i to avoid sudo on each line, this should refresh system:

in not chroot use sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by yellowpike on 2011-01-07
**oldfred** again I am but a newbie

Ran as follows
sudo -i
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

**Result as follows**


root@john-ubuntu10:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@john-ubuntu10:~# apt-get clean
root@john-ubuntu10:~# apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources                  
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources            
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,088B]       
Get:6 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                   
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,082B]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Fetched 7,457B in 5s (1,323B/s)
Reading package lists... Done
root@john-ubuntu10:~# apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-2.6.32-27-generic (2.6.32-27.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-27-generic-pae (2.6.32-27.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-27-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.98-1ubuntu9) ...
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-27-generic; however:
  Package linux-image-2.6.32-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.27.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.32-27-generic
 linux-image-2.6.32-27-generic-pae
 grub-pc
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@john-ubuntu10:~# 

**Your thoughts Sir? and thank you VERY MUCH**

---

### Post by oldfred on 2011-01-08
It did a lot of updates, but still has issues with the kernels. Not sure what the error is:
[PHP]Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution[/PHP]
Did you manually customize grub at all? You may be just missing a quote on a line in /etc/default/grub?? If you cannot find it then, I would totally uninstall grub2 and then reinstall it:

Do these then redo the kernel updates:
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
#redo kernel updates
apt-get upgrade
apt-get -f install
dpkg --configure -a
#finish grub update:
grub-install /dev/sda
grub-install --recheck /dev/sda

With grub uninstalled you will not be able to reboot, do be sure to rerun the reinstall of grub, hopefully that will reinstall ok.

---

### Post by yellowpike on 2011-01-08
[B]oldfred. Pasted text below from /etc/default/grub 
Perhaps a clue found here? I will try as directed and post results ASAP. 
I did not make any manual edits to grub.
Thanks again my friend!!! [/B] 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by oldfred on 2011-01-08
Quotes have to match.

I see this in yours - and it is not two singles, but one double:
GRUB_CMDLINE_LINUX="

And this is mine:
GRUB_CMDLINE_LINUX=""

Try adding a quote and see if it then works.

---

### Post by yellowpike on 2011-01-09
**Hope you are well my friend!**

Nada. Didn't do it. I think I screwed the pouch when I added the second drive into the mix (stupid/stupid/stupid)
I've opted for a session with Gparted and am going the "redo" route. I'd like to move Ubuntu onto the same drive as Win7 and put the other Linux distros on the 2nd drive anyway so...
To hell with it! LOL

** I Sincerely appreciate your help Sir. Stay healthy! **

---

