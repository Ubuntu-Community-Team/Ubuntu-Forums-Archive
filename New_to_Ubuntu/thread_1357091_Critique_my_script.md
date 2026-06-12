---
title: "Critique my script"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by CharlesA on 2009-12-16
It's going to be used to reinstall all the services and apps that I use after a clean install.

I followed the advice from bodhi.zazen:

> **bodhi.zazen said:**
> I am not sure where the problem is , but I suggest a few things :

1. add a "shebang" at the top of the script :

```
#!/bin/bash
```

2. Rather then using sudo, simply write your commands and run the script with sudo ./script

3. Use the full path to commands

/usr/bin/apt-get rather then apt-get


Any way I can make it more efficient?

```
#!/bin/sh

WEBMIN=webmin_1.500_all.deb
RAID1=rr2640-linux-src-v1.2-090925-0932.tar.gz
RAID2=WebGui-Linux-v1.4-10-091124.tgz
BIT=BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

#Update System
/bin/echo "Updating System..."
/usr/bin/apt-get update && /usr/bin/apt-get upgrade --assume-yes
#Create group raid
/bin/echo "Creating group raid..."
/usr/sbin/addgroup -gid 1004 raid
#Create user karen and add to group raid
/bin/echo "Creating user Karen..."
/usr/sbin/useradd karen -u 1001 -M -d /dev/null -s /dev/null -U -G raid
#Create user htpc and add to group raid
/bin/echo "Creating user HTPC..."
/usr/sbin/useradd htpc -u 1002 -M -d /dev/null -s /dev/null -U -G raid
#Create user clone and add to group raid
/bin/echo "Creating user Clone..."
/usr/sbin/useradd clone -u 1003 -M -d /dev/null -s /dev/null -U -G raid
#Add charles to karen, clone and raid groups
/bin/echo "Adding Charles to groups..."
/usr/sbin/usermod -a -G karen,clone,raid charles
#Create array directory and change owner and permissions
/bin/echo "Creating /array and setting permissions..."
/bin/mkdir /array && /bin/chown charles:raid /array && /bin/chmod 770 /array
#Create DVD backup directory and change owner and permissions
/bin/echo "Creating /dvdback and setting permissions..."
/bin/mkdir /dvdback && /bin/chown charles:charles /dvdback && /bin/chmod 770 /dvdback
#Create Doc backup directory and change owner and permissions
/bin/echo "Creating /docback and setting permissions..."
/bin/mkdir /docback && /bin/chown charles:charles /docback && /bin/chmod 770 /docback
#Install Webmin dependencies
/bin/echo "Installing Webmin dependencies..."
/usr/bin/apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl --assume-yes
#Download Webmin and install
/bin/echo "Installing Webmin..."
if [ -f $WEBMIN ];
then
  /bin/echo "$WEBMIN already exists. You will need to install it manually by running ./webmin" && /bin/echo "/usr/bin/dpkg -i webmin_1.500_all.deb" > webmin && /bin/chmod 777 webmin && /bin/sleep 10
else
  /usr/bin/wget http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb && /usr/bin/dpkg -i webmin_1.500_all.deb
fi
#Install Highpoint Tech 2640-x1 RAID driver
/bin/echo "Installing RAID driver dependencies..."
/usr/bin/apt-get install build-essential linux-headers-`uname -r` --assume-yes
/bin/echo "Creating RAID Driver..."
if [ -f $RAID1 ];
then
  /bin/echo "$RAID1 already exists. ou will need to install it manually by running ./raid1" && /bin/echo "/bin/tar -xf rr2640-linux-src-v1.2-090925-0932.tar.gz && cd ~/rr2640-linux-src-v1.2/product/rr2640/linux && /usr/bin/make && /usr/bin/make install" > raid1 && /bin/chmod 777 raid1 && /bin/sleep 10
else
  /usr/bin/wget http://www.support-highpoint-tech.com/Main/rr26xx/264x/Linux/opensrc/rr2640-linux-src-v1.2-090925-0932.tar.gz && /bin/tar -xf rr2640-linux-src-v1.2-090925-0932.tar.gz && cd ~/rr2640-linux-src-v1.2/product/rr2640/linux && /usr/bin/make && /usr/bin/make install
fi
#Install Highpoint Tech Web GUI
/usr/bin/apt-get install libc6 alien --assume-yes
/bin/echo "Installing Web GUI..."
if [ -f $RAID2 ];
then
  /bin/echo "$RAID2 already exists. You will need to install it manually by running ./raid2" && /bin/echo "/bin/-tar -xf WebGui-Linux-v1.4-10-091124.tgz && cd WebGui-Linux-v1.4-10-091124 && /usr/bin/alien -d --scripts hptsvr-https-1.4-10.x86_64.rpm && /usr/bin/dpkg -i https-1.4-11_amd64.deb" > raid2 && /bin/-chmod 777 raid2 && /bin/sleep 10
else
  /usr/bin/wget http://www.support-highpoint-tech.com/Main/HRM/Linux/WebGui-Linux-v1.4-10-091124.tgz && /bin/tar -xf WebGui-Linux-v1.4-10-091124.tgz && cd WebGui-Linux-v1.4-10-091124 && /usr/bin/alien -d --scripts hptsvr-https-1.4-10.x86_64.rpm && /usr/bin/-dpkg -i https-1.4-11_amd64.deb
fi
#Install Samba, SSH and Mailutil
/bin/echo "Installing Samba, SSH and Mailutils..."
/usr/bin/apt-get install samba ssh mailutils --assume-yes
#Configure Exim4
/usr/bin/dpkg 
/bin/echo "Configuring Exim4..."
/bin/cat ~/exim4.conf.template > /etc/exim4/exim4.conf.template
/bin/cat ~/passwd.client > /etc/exim4/passwd.client
update-exim4.conf
#Configure TCP Wrappers
/bin/echo "Installing DenyHosts..."
/usr/bin/apt-get install denyhosts --assume-yes
/bin/echo "Configuring hosts.allow and hosts.deny"
/bin/cat ~/hosts.allow > /etc/hosts.allow
/bin/cat ~/hosts.deny > /etc/hosts.deny
#Configure iptables
/bin/echo "Configuring iptables"
/bin/cat ~/iptables.up.rules > /etc/iptables.up.rules
#Configure SSH
/bin/echo "Configuring SSH"
/bin/cat ~/sshd_config > /etc/ssh/sshd_config
/bin/cat ~/id_rsa.pub ~/.ssh/authorized_keys
/bin/cp ~/id_rsa ~/.ssh/
/bin/cp ~/id_rsa.pub ~/.ssh/
/etc/init.d/ssh restart
#Configure Samba
/bin/echo "Configuring Samba"
/bin/cat ~/smb.conf /etc/samba/smb.conf
/etc/init.d/samba restart
#Install and configure ddclient
/bin/echo "Configuring ddclient"
/usr/bin/apt-get install ddclient --assume-yes
/bin/dpkg-reconfigure ddclient
/bin/cat ~/ddclient.conf > /etc/ddclient.conf
#Install BitDefender AV
/bin/echo "Installing BitDefender AntiVirus"
if [ -f $BIT ]
then
  echo "$BIT already exists. You will need to install it manually by running ./$BIT" && /bin/chmod 755 $BIT
else
  /usr/bin/wget http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run && /bin/chmod 755 BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run && /bin/sh ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
fi
#Clean up
/bin/echo "Clean up time..."
/bin/rm ~/$WEBMIN
/bin/rm ~/$RAID1
/bin/rm ~/$RAID2
if [ -f webmin ]
then
  /bin/rm ~/webmin
fi
if [ -f raid1 ]
then
 /bin/rm ~/raid1
fi
if [ -f raid2 ]
then
  /bin/rm ~/raid2
fi
/bin/rm -rf ~/rr2640-linux-src-v1.2
/bin/rm ~/ddclient.conf
/bin/rm ~/exim4.conf.template
/bin/rm ~/hosts.allow
/bin/rm ~/hosts.deny
/bin/rm ~/id_rsa
/bin/rm ~/id_rsa.pub
/bin/rm ~/iptables.up.rules
/bin/rm ~/passwd.client
/bin/rm ~/smb.conf
/bin/rm ~/sshd_config
/bin/rm ~/clean
#Completed
/bin/echo "Completed"

```

Thanks!

---

### Post by unmole on 2009-12-16
I know bodhi.zazen is far more experienced than me but i think it would be better to use sudo before each command in the script which needs to be run as root instead of running the entire script as root. 

From the Ubuntu Documentation > Be careful when using sudo; you might damage your system if you type the wrong command! As a general rule, only use sudo when absolutely necessary.

---

### Post by Chesamo on 2009-12-16
I disagree; if you execute all of the commands as sudo then all it will do is ask for your password for the first command then continue along happily in sudo mode. Better to not waste file space and smooth out the execution with a single sudo.

Though I also disagree with using the full path to the executables, in case a system happens to be unique and has its binaries configured differently. In almost all cases, it's safe to omit the full path as long as you can confirm the command both exists and works as expected.

---

### Post by CharlesA on 2009-12-17
Thanks.

I don't know why it wants "fi" at the end of the file...

Still need to figure out why the delete part at the end isn't working.. there must be something wrong, since if I remove everything except the "rm" parts, it runs fine, so there must be something wrong with this part:

```

[B]#Clean up
/bin/echo "Clean up time..."[/B]
if [ -f $WEBMIN ]
then
  /bin/rm /home/charles/$WEBMIN
fi
if [ -f $RAID1 ]
then
  /bin/rm /home/charles/$RAID1
fi
if [ -f $RAID2 ]
then
/bin/rm /home/charles/$RAID2
if [ -f webmin ]
then
  /bin/rm /home/charles/webmin
fi
if [ -f raid1 ]
then
 /bin/rm /home/charles/raid1
fi
if [ -f raid2 ]
then
  /bin/rm /home/charles/raid2
fi
/bin/rm -rf /home/charles/rr2640-linux-src-v1.2
/bin/rm /home/charles/ddclient.conf
/bin/rm /home/charles/exim4.conf.template
/bin/rm /home/charles/hosts.allow
/bin/rm /home/charles/hosts.deny
/bin/rm /home/charles/id_rsa
/bin/rm /home/charles/id_rsa.pub
/bin/rm /home/charles/iptables.up.rules
/bin/rm /home/charles/passwd.client
/bin/rm /home/charles/smb.conf
/bin/rm /home/charles/sshd_config
/bin/rm /home/charles/clean
#Completed
/bin/echo "Completed"
fi
```

The last thing it runs is: "Clean up time..." :confused:

Also, do I need to manually create ~/.ssh? It doesn't look like it's being created when I install ssh.

---

### Post by kansasnoob on 2009-12-17
I'm lazy, my post-installation "script" is just a bunch of commands:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get install abiword gnome-alsamixer gparted gphoto2 gthumb gtkam gtkam-gimp gufw hplip-gui mozilla-plugin-vlc  vlc-plugin-pulse startupmanager totem-plugins-extra totem-xine ubuntu-restricted-extras gnome-themes-more gnome-themes-extras shiki-colors-metacity-theme gnome-backgrounds nautilus-gksu sensors-applet ntfsprogs libdvdcss2 w32codecs
```

My mount and chroot "script"is similar:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I just like to keep things simple!

---

### Post by CharlesA on 2009-12-17
Hahaha. Does the --quiet argument for apt-get make much of a difference in the amount of crap that's displayed on screen?

---

### Post by kansasnoob on 2009-12-17
In that case "quiet" only causes the normal update indication to stay "silent" so you won't be notified of current updates available.

I do a lot of ISO testing and sometimes I just want to install my favorite programs without running and installing all of the updates.

The only reason I included medibuntu anyway is because I always just do that. I want it so I do it right away! It gives me great support for DVD playback and most Win media.

---

### Post by CharlesA on 2009-12-17
I see. Thanks!

---

### Post by falconindy on 2009-12-17
You need an extra 'fi' at the end because your line:
```
if [ -f $RAID2 ]
```
is unclosed. 

You could stand to do a fair bit of cleanup. IMO, if you're typing the same thing over and over, you're not using a computer effectively. If you really want to use the full path to a program (which I disagree with outside of init-stage scripts), assign the program path to a variable.
```
RM=/bin/rm
$RM /home/charles/$WEBMIN
```

Commands based on a boolean expression can be executed using short circuit logic. That is, you can use boolean operators in place of if/then structures:
```
if [ -f $afile ] then;
   $APTGET $somearg
fi

# Is functionally equivalent to:

[ -f $afile ] && $APTGET $somearg
```

---

### Post by CharlesA on 2009-12-17
Thanks! I "cleaned up" the script a bit, still looks messy as hell, but it runs without any problems.

---

