---
title: "LOCATE finds files that are not there(?)"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by jfbooth on 2010-05-11
Could someone explain this, please?

I used LOCATE to find all .old files.  I deleted them and their links, but LOCATE still 'finds' them as shown below:

jb@jb-desktop:~/Desktop$ locate *.old
/initrd.img.old
/vmlinuz.old
/etc/motd.tail.old
/etc/sgml/catalog.old
/etc/sgml/docbook-xml.cat.old
/etc/sgml/sgml-data.cat.old
/etc/xml/catalog.old
/etc/xml/docbook-xml.xml.old
/etc/xml/rarian-compat.xml.old
/etc/xml/sgml-data.xml.old
/etc/xml/xml-core.xml.old
/home/jb/.xsession-errors.old
/usr/share/info/dir.old
/var/lib/belocs/hashfile.old
/var/log/Xorg.0.log.old

So, if I understand this, I should have initrd.img.old and vmlinuz.old in the ROOT directory.

jb@jb-desktop:/$  ls
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var
jb@jb-desktop:/$

I don't see any .old files here.

I should have several .old files here:

jb@jb-desktop:/$ cd etc
jb@jb-desktop:/etc$ ls
a2ps.cfg                grub.d               passwd-
a2ps-site.cfg           gshadow              pcmcia
acpi                    gshadow-             perl
adduser.conf            gtk-2.0              pm
akonadi                 gtkmathview          pnm2ppa.conf
alternatives            hal                  PolicyKit
anacrontab              hdparm.conf          polkit-1
apm                     host.conf            popularity-contest.conf
apparmor                hostname             power
apparmor.d              hosts                ppp
apport                  hosts.allow          printcap
apt                     hosts.deny           profile
at.deny                 hp                   profile.d
avahi                   ifplugd              protocols
bash.bashrc             inetd.conf           psiconv
bash_completion         init                 pulse
bash_completion.d       init.d               purple
bindresvport.blacklist  initramfs-tools      python
blkid.conf              inputrc              python2.6
blkid.tab               insserv              rc0.d
bluetooth               insserv.conf         rc1.d
bogofilter.cf           insserv.conf.d       rc2.d
bonobo-activation       iproute2             rc3.d
byobu                   issue                rc4.d
ca-certificates         issue.net            rc5.d
ca-certificates.conf    java-6-openjdk       rc6.d
calendar                java-6-sun           rc.local
chatscripts             kbd                  rc.local.origami
complete.tcsh           kernel               rcS.d
computer-janitor.d      kernel-img.conf      resolvconf
ConsoleKit              kerneloops.conf      resolv.conf
console-setup           keys                 rmt
console-tools           ksysguarddrc         rpc
cron.d                  laptop-mode          rsyslog.conf
cron.daily              ldap                 rsyslog.d
cron.hourly             ld.so.cache          samba
cron.monthly            ld.so.conf           sane.d
crontab                 ld.so.conf.d         scim
cron.weekly             legal                screenrc
crypttab                lftp.conf            securetty
csh                     libpaper.d           security
csh.cshrc               locale.alias         sensors3.conf
csh.login               localtime            sensors.conf
csh.logout              logcheck             sensors.d
cups                    login.defs           services
dbus-1                  logrotate.conf       sgml
debconf.conf            logrotate.d          shadow
debian_version          lsb-base             shadow-
default                 lsb-base-logging.sh  shells
defoma                  lsb-release          skel
deluser.conf            ltrace.conf          sound
depmod.d                magic                ssh
dhcp3                   magic.mime           ssl
dictionaries-common     mailcap              sudoers
dkms                    mailcap.order        sudoers.d
doc-base                manpath.config       sysctl.conf
dpkg                    mime.types           sysctl.d
emacs                   mke2fs.conf          terminfo
environment             modprobe.d           thunderbird
esound                  modules              timezone
firefox                 mono                 ts.conf
firefox-3.0             motd                 ucf.conf
firefox-3.5             mtab                 udev
fonts                   mtools.conf          ufw
foomatic                mysql                updatedb.conf
fstab                   nanorc               update-manager
fstab~                  netscsid.conf        update-motd.d
fuse.conf               network              update-notifier
gai.conf                NetworkManager       usplash.conf
gamin                   networks             vim
gconf                   nsswitch.conf        w3m
gdb                     ntp.conf             wgetrc
gdm                     obex-data-server     wodim.conf
gimp                    odbc.ini             wpa_supplicant
gnome                   odbcinst.ini         X11
gnome-app-install       openoffice           xdg
gnome-system-tools      opt                  xml
gnome-vfs-2.0           PackageKit           xul-ext
gnome-vfs-mime-magic    pam.conf             xulrunner-1.9.1
gre.d                   pam.d                xulrunner-1.9.2
groff                   pango                zsh_command_not_found
group                   papersize
group-                  passwd
jb@jb-desktop:/etc$

None there either.  Why is LOCATE lying to me??  Thanks in advance.

---

### Post by philinux on 2010-05-11
Did you run this.

```
sudo updatedb
```

This updates the locate database.

---

### Post by jfbooth on 2010-05-11
No, Sir.  Was not aware this needed to be done.  Thank you.  Will give it a try ASAP.  Thank you VERY much.

---

### Post by kerry_s on 2010-05-11
if you want a lite gui try "catfish" you won't have to update each time.

oops, for got to switch it to "locate" in the pic, but with catfish you can select what you want to search with, the default is "find".

---

### Post by jfbooth on 2010-05-12
> **kerry_s said:**
> if you want a lite gui try "catfish" you won't have to update each time.

oops, for got to switch it to "locate" in the pic, but with catfish you can select what you want to search with, the default is "find".

Being a Linux noob is painful.  Turns out, CATFISH comes with Xubuntu .. I just did not remember it was there.  Wanted to find .old files, .. Googled 'find files in linux' and hit on LOCATE .. which did not mention updatedb which lead to more confusion.  Being it is installed, I will use CATFISH in the future.  Thank you.

---

### Post by TwoEars on 2010-05-12
From the command line, you'd need to run ```
ls -la
``` it sounds like they are hidden.

---

### Post by jfbooth on 2010-05-12
> **TwoEars said:**
> From the command line, you'd need to run ```
ls -la
``` it sounds like they are hidden.

No, they were not hidden .. they were deleted, .. but I did not update the db to reflect that they were deleted.  LOCATE uses a database which has to be up to date to be accurate (so I have just learned).

---

