---
title: "Help with a network SH file"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by Christ_Guard on 2007-09-14
hey guys, I have something that I need alot of help with! I am a network admin here at my Iniversity and I have been charged with the Job of updating our Fedora 6 machines to Ubuntu FF, my main problem is getting the computers networked(Connected to the Active Domain, we have internet on them already). We have an SH script that we run on the Fedora machines and was wondering if it would work on the new Ubuntu machines, or if you could give any other advice to a linux n00b like myself that would be great! 

Here is the script:

```
#!/bin/bash
############
if [ "$USER" != "root" ]
then
	echo "You must run this script as root."
	exit -1;
fi
CWD=`pwd`
echo "** Performing a full system update."
echo "   - This will take a couple hours to finish."

yum -y upgrade 
echo "** Finished with system updates."
echo


if [ `/bin/cat /boot/grub/grub.conf | /bin/grep "^hiddenmenu"` != "" ]
then
	echo "** Changing Grub menu options."
	gawk -v num=`gawk 'BEGIN { IGNORECASE = 1; entries = 0; xp = 0; } { line = $0 } /^[ \t]*default/ { line = "#" $1; } /^[ \t]*hiddenmenu/ { line = "#hiddenmenu"; } /^[ \t]*timeout=/ { line = "timeout=60"; } /^[ \t]*title/ { entries += 1; } /^[ \t]*title.+xp/ { xp = entries; } /^[ \t]*title.+dos/ { xp = entries; } { print line >> "/tmp/grub.conf2" } END { print xp-1 }' /boot/grub/grub.conf` 'BEGIN { IGNORECASE = 1; } {  line = $0; } /default\=/ { line = "default=" num; } { if (length(line) != 0 ) { print line >> "/tmp/grub.conf"; } }' /tmp/grub.conf2
	mv -f /tmp/grub.conf /boot/grub/grub.conf
	echo
fi


echo "** Setting up computer for domain authentication."
echo

echo "** Updating system configuration files."
cp -rf System\ Files/* /

echo "** Setting up hostname configuration."
echo
read -p "** Enter the name of this computer: (ex. OMH254-001L): " computername
echo "127.0.0.1	$computername 	$computername.labpcs.spu.local	localhost.localdomain	localhost" >> /etc/hosts
hostname "$computername.labpcs.spu.local"
echo "NETWORKING=yes" > /etc/sysconfig/network
echo "HOSTNAME=$computername.labpcs.spu.local" >> /etc/sysconfig/network
#echo "HOSTNAME=$computername.labpcs.spu.local" > /etc/sysconfig/networking/profiles/default/network

echo "** Finished updating system config files."
echo 

echo "** Starting Samba service and starting it by default."
/etc/init.d/smb start
/etc/init.d/winbind start

rm -f /etc/rc3.d/K91smb
rm -f /etc/rc4.d/K91smb
rm -f /etc/rc5.d/K91smb

ln -fs ../init.d/smb /etc/rc3.d/S91smb
ln -fs ../init.d/smb /etc/rc4.d/S91smb
ln -fs ../init.d/smb /etc/rc5.d/S91smb

rm -f /etc/rc3.d/K91winbind
rm -f /etc/rc4.d/K91winbind
rm -f /etc/rc5.d/K91winbind

ln -fs ../init.d/winbind /etc/rc3.d/S91winbind
ln -fs ../init.d/winbind /etc/rc4.d/S91winbind
ln -fs ../init.d/winbind /etc/rc5.d/S91winbind
echo 

echo "** Removing Network Caching deamon (nscd) from startup"
mv -f /etc/rc3.d/S74nscd /etc/rc3.d/K74nscd 2>&1 /dev/null
mv -f /etc/rc4.d/S74nscd /etc/rc4.d/K74nscd 2>&1 /dev/null
mv -f /etc/rc5.d/S74nscd /etc/rc5.d/K74nscd 2>&1 /dev/null
echo

echo "** Setting up domain authentication."
read -r -p "Enter domain admin username (ex:bkg@SPU.LOCAL for ACCOUNTS or bkg@LABPCS.SPU.LOCAL for LABPCS account (case sensitive)): " username
net ads join -U $username
echo 

echo "** You should be able to login using domain accounts now."
echo "** Push Ctrl-Alt-F1 to go to a console session, and login using a domain account. If it works just type 'exit' and hit Ctrl-Alt-F7 to get back here. If it doesn't work, ask someone to investigate the problem."
```


When I try to run it I get this message:
> student@CS223A-L-001:~$ sudo '/home/student/Desktop/Install System Files.sh' 
Password:
sudo: /home/student/Desktop/Install System Files.sh: command not found
student@CS223A-L-001:~$ 


---

