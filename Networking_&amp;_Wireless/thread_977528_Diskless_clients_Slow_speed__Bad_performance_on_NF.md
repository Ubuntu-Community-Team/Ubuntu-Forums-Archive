---
title: "Diskless clients: Slow speed / Bad performance on NFS root export?"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by jorno on 2008-11-10
Hello.

Our company has delivered a couple of "Diskless public computer" systems.
It consists of a server (at least 3ghz cpu, 2gb ram, a fast scsi disk, GB nic), with between 5 and 15 "diskless clients" (2ghz+, 1gb ram, GB nic), connected via a GB switch.

It worked perfectly with Ubuntu 7.04 and 7.10. But after upgrading to 8.04 (and also now 8.10) we experience some trouble...


The machines are set to auto-login in Gnome, and bring up Firefox with a pre-defined homepage. Ready to go for the public.


But, when many machines are booted at once, we experience these problems (randomly):
1) One or more of the computers quits before getting GDM running, with this error: "Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that you have a problem with the installation, or that you are low on disk space".
2) Sometimes we get a blue screen (not BSOD) with a text telling us that X could not start on F7 (screen 0:0), and asks if we want to try again. (A reboot fixes this).
3) And if the computers boot all the way into Gnome, Firefox almost never opens automatically. (We have inserted this into the "Session"-settings in Gnome. However, if one move the mouse around and press any key, Firefox suddenly pops up.


The systems generally works good when booted OK, and the public is happy to use them. But our customers (libraries in norway) complains to us when problems like these occurs. And we are not able to figure out why this happens. But we are able to reproduce the errors at our lab.


We did the installation of these systems according to the guide at [https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto")


One adjustment we have made is adding a "template"-user, where we login to configure the public desktop. And then a "public"-user, which automatically gets logged on to. We have a script in /etc/gdm/PostLogin/Default , which at logon executes these commands:
```
umount -f /home/public    (/home/public is mounted as a tmpfs on each diskless station)
mount /home/public
cp -av /home/template/. /home/public
chown -R public:public /home/public
chmod 775 /var/run
```

So that after each logout/login, the public home-directory gets wiped, and then a new copy is executed.



I did suspect this had to do with NFS, so I have played with the variable "RPCNFSDCOUNT" in /etc/default/nfs-kernel-server on the server, without much luck. (Tried both increasing and decreasing it).


[SIZE="2"]
**This is our configs:**[/SIZE]

/etc/dhcp3/dhcpd.conf (SERVER)
```
authoritative;
next-server 192.168.0.1;
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.10 192.168.0.250;
  option domain-name "CUSTOMER.DOMAIN.no";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;
  use-host-decl-names on;
  filename "/diskless/pxelinux.0";
  option root-path "/opt/diskless";
}
```

/etc/default/tftpd-hpa (SERVER)
```
RUN_DAEMON="yes"
OPTIONS="-l -s /tftpboot"
```

/etc/exports (SERVER)
```
/opt/diskless             192.168.0.0/255.255.255.0(rw,no_root_squash,async,no_subtree_check,no_acl)
```

/tftpboot/diskless/pxelinux.cfg/default (SERVER)
prompt 0
  label linux
  kernel vmlinuz-2.6.27-7-generic
  append quiet splash rw root=/dev/nfs initrd=initramfs-2.6.27-7-generic ip=dhcp


/etc/fstab (CLIENT)
```
proc            /proc           proc    defaults        0       0
/dev/nfs        /               nfs     rw,hard,rsize=8192,wsize=8192,nolock  0 0
temp            /tmp            tmpfs   defaults        0       0
vartemp         /var/tmp        tmpfs   defaults        0       0
hometynn        /home/tynn      tmpfs   defaults        0       0
media           /media          tmpfs   defaults        0       0
varrun          /var/run        tmpfs   defaults        0       0

```

/etc/initramfs-tools/initramfs.conf (CLIENT)
```
MODULES=most
BUSYBOX=y
BOOT=nfs
DEVICE=eth0
NFSROOT=auto
```

/etc/gdm/PostLogin/Default (CLIENT)
```
cd `dirname $0` 
if test $LOGNAME = "public"
then
        exec 2> gdm.log
        env > gdm.log
       
        set -x
        umount -f /home/tynn
        mount  /home/tynn
        cp -av /home/template/. /home/public
        chown -R public:public /home/public
        chmod 775 /var/run
fi

```


Also, the icons on the desktop is arranged differently sometimes on each client... So to me, it seems like maybe something is failing when copying the home-directory from the server? (This could also explain why Firefox doesn't startup before some user-interaction is done on the client?). But when inserting ie "Gnome-terminal" in the autostart-section of "Sessions" in Gnome, this pops up at once after bootup without problems.




Ok, this turned into a long post, with lots of questions and me trying to explain this in bad english. Sorry for the language, english isn't my mother tongue... But please, feel free to ask if something is unclear.


Hints and tips to what I should try are welcome! Please tell if you would need more logs, or if I should turn on some extensive logging.


Thanks in advance.

---

