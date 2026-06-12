---
title: "NIC doesn't start properly"
date: 2023-09-16
forum: Networking &amp; Wireless
---

### Post by peyre on 2023-09-16
I'm running the Xubuntu LTS on desktop computer connect via ethernet to a switch.  Everything seemed to be going ok until I did a complete removal of python3 in Synaptic.  I partly sorted this out in thread 

[https://ubuntuforums.org/showthread.php?t=2490617&page=3](https://ubuntuforums.org/showthread.php?t=2490617&page=3)

but not entirely.  As it is, whenever I start my computer, the light on the switch port that this plugs into is dead, and I have no connectivity.  If I run **dhclient -r** followed by **sudo dhclient** everything's good, but next time I start up my computer I have to do it again.  Anyone have any ideas?  lspci reports the NIC as

```
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
```

Also my shares are no longer available, probably I suppose because the network wasn't active/available on startup.  These are the relevant lines in my /etc/samba/smb.conf:

```
[HomeFolder]
   comment = Home folder share
   path = /home/leon
   read only = no
   browsable = yes

[Storage]
   comment = Storage share
   path = /media/Storage
   read only = no
   browsable = yes
```

---

### Post by #&amp;thj^% on 2023-09-16
So this is still going on humm?
It has to be some setting you changed then and that's just a guess for now.
But show this please:
```
modinfo r8169 | grep 8136

```
I hope it returns with:
```
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*

```
I use the same Nic:
```
inxi  -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169

```
@ peyre I just read your first line removing python3, This should get you back in shape:
```
sudo apt-get install --reinstall python python-chardet python-colorama python-distlib python-django python-django-tables2 python-six python-html5lib python-lxml python-minimal python-pkg-resources python-setuptools python-urllib3 python-requests python-pip python-virtualenv
```

---

### Post by peyre on 2023-09-16
Yes, it returns ```
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
```
```
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
```

Uh oh!  your solution returned this.
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  2to3 python2-minimal:i386 python2:i386 python2-minimal python2 dh-python
  python-is-python3

Package python-minimal is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2-minimal:i386 python2-minimal python-is-python3

Package python-chardet is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python3-chardet

Package python-urllib3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package python-virtualenv is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python' has no installation candidate
E: Package 'python-chardet' has no installation candidate
E: Unable to locate package python-colorama
E: Unable to locate package python-distlib
E: Unable to locate package python-django
E: Unable to locate package python-django-tables2
E: Unable to locate package python-html5lib
E: Unable to locate package python-lxml
E: Package 'python-minimal' has no installation candidate
E: Package 'python-urllib3' has no installation candidate
E: Unable to locate package python-requests
E: Package 'python-virtualenv' has no installation candidate
```

Just to check, I rebooted and same issue.

---

### Post by #&amp;thj^% on 2023-09-16
Dang i hate working with self inflicted system python packages, it just mucks up the whole OS, package-manager, network, and the ability to update.
python so important to so many system related workings. (Best to tread lightly removing even installing python package versions)
Gosh I'm sorry that failed, now i can only suggest:
```
sudo apt-get install --reinstall python
``` 

If that don't work, then I [COLOR="#FF0000"]*cautiously*[/COLOR] did I mention [COLOR="#FF0000"]caution[/COLOR], yep this is a forceful approach:(Use at your own risk)
```
sudo dpkg --remove --force-remove-reinstreq --force-depends python3
sudo apt-get -f install
```
In fact the more i look at that, it "should" work,**_ but try a dry run first._**
>>This was removed on my end:
```
e*&#57520;*~*&#57520;*2*&#57520;*sudo dpkg --remove --force-remove-reinstreq --force-depends python3 
dpkg: python3: dependency problems, but removing anyway as you requested:
 zfsutils-linux depends on python3.
 xpra depends on python3 (<< 3.12).
 xpra depends on python3 (>= 3.11~).
 xpra depends on python3:any.
 xpra depends on python3 (<< 3.12).
 xpra depends on python3 (>= 3.11~).
 xpra depends on python3:any.
 xpra depends on python3 (<< 3.12).
 xpra depends on python3 (>= 3.11~).
 xpra depends on python3:any.
 xfce4-helpers depends on python3.
 xapps-common depends on python3.
 xapps-common depends on python3:any.
 xapps-common depends on python3.
 xapps-common depends on python3:any.
 wolflandbuilder depends on python3:any (>= 3.3~).
 virtinst depends on python3:any.
 virt-manager depends on python3:any.
 ubuntu-release-upgrader-core depends on python3:any.
 ubuntu-minimal depends on python3.
 ubuntu-drivers-common depends on python3:any (>= 3.2~).
 ubuntu-advantage-tools depends on python3:any.
 ubiquity-frontend-gtk depends on python3:any (>= 3.1~).
 ubiquity depends on python3:any (>= 3.1~).
 system-monitoring-center depends on python3:any.
 system-monitoring-center depends on python3 (>= 3.6).
 system-monitoring-center depends on python3:any.
 system-monitoring-center depends on python3 (>= 3.6).
 system-config-printer-udev depends on python3:any (>= 3.3.2-2~).
 system-config-printer-common depends on python3:any.
 system-config-printer depends on python3:any.
 speedtest-cli depends on python3:any.
 software-properties-gtk depends on python3.
 software-properties-gtk depends on python3:any.
 software-properties-gtk depends on python3.
 software-properties-gtk depends on python3:any.
 software-properties-common depends on python3.
 software-properties-common depends on python3:any.
 software-properties-common depends on python3.
 software-properties-common depends on python3:any.
 screen-resolution-extra depends on python3:any (>= 3.2~).
 samba-common-bin depends on python3.
 samba-common-bin depends on python3:any.
 samba-common-bin depends on python3.
 samba-common-bin depends on python3:any.
 samba depends on python3.
 samba depends on python3:any.
 samba depends on python3.
 samba depends on python3:any.
 python3-zipp depends on python3:any.
 python3-zeroconf depends on python3:any.
 python3-yaml depends on python3 (<< 3.12).
 python3-yaml depends on python3 (>= 3.11~).
 python3-yaml depends on python3:any.
 python3-yaml depends on python3 (<< 3.12).
 python3-yaml depends on python3 (>= 3.11~).
 python3-yaml depends on python3:any.
 python3-yaml depends on python3 (<< 3.12).
 python3-yaml depends on python3 (>= 3.11~).
 python3-yaml depends on python3:any.
 python3-xkit depends on python3:any (>= 3.2~).
 python3-xdg depends on python3:any.
 python3-xapian depends on python3 (<< 3.12).
 python3-xapian depends on python3 (>= 3.11~).
 python3-xapian depends on python3:any.
 python3-xapian depends on python3 (<< 3.12).
 python3-xapian depends on python3 (>= 3.11~).
 python3-xapian depends on python3:any.
 python3-xapian depends on python3 (<< 3.12).
 python3-xapian depends on python3 (>= 3.11~).
 python3-xapian depends on python3:any.
 python3-wheel depends on python3:any.
 python3-webencodings depends on python3:any.
 python3-wadllib depends on python3:any.
 python3-wadllib depends on python3:any.
 python3-urllib3 depends on python3:any.
 python3-uritools depends on python3:any.
 python3-update-manager depends on python3:any.
 python3-unidiff depends on python3:any.
 python3-tdb depends on python3 (<< 3.12).
 python3-tdb depends on python3 (>= 3.11~).
 python3-tdb depends on python3:any.
 python3-tdb depends on python3 (<< 3.12).
 python3-tdb depends on python3 (>= 3.11~).
 python3-tdb depends on python3:any.
 python3-tdb depends on python3 (<< 3.12).
 python3-tdb depends on python3 (>= 3.11~).
 python3-tdb depends on python3:any.
 python3-talloc:amd64 depends on python3 (<< 3.12).
 python3-talloc:amd64 depends on python3 (>= 3.11~).
 python3-talloc:amd64 depends on python3 (<< 3.12).
 python3-talloc:amd64 depends on python3 (>= 3.11~).
 python3-speechd depends on python3:any.
 python3-software-properties depends on python3.
 python3-software-properties depends on python3:any.
 python3-software-properties depends on python3.
 python3-software-properties depends on python3:any.
 python3-six depends on python3:any.
 python3-simplejson depends on python3 (<< 3.12).
 python3-simplejson depends on python3 (>= 3.11~).
 python3-simplejson depends on python3:any.
 python3-simplejson depends on python3 (<< 3.12).
 python3-simplejson depends on python3 (>= 3.11~).
 python3-simplejson depends on python3:any.
 python3-simplejson depends on python3 (<< 3.12).
 python3-simplejson depends on python3 (>= 3.11~).
 python3-simplejson depends on python3:any.
 python3-setuptools depends on python3:any.
 python3-setproctitle:amd64 depends on python3 (<< 3.12).
 python3-setproctitle:amd64 depends on python3 (>= 3.11~).
 python3-setproctitle:amd64 depends on python3:any.
 python3-setproctitle:amd64 depends on python3 (<< 3.12).
 python3-setproctitle:amd64 depends on python3 (>= 3.11~).
 python3-setproctitle:amd64 depends on python3:any.
 python3-setproctitle:amd64 depends on python3 (<< 3.12).
 python3-setproctitle:amd64 depends on python3 (>= 3.11~).
 python3-setproctitle:amd64 depends on python3:any.
 python3-secretstorage depends on python3:any.
 python3-samba depends on python3 (<< 3.12).
 python3-samba depends on python3 (>= 3.11~).
 python3-samba depends on python3:any.
 python3-samba depends on python3 (<< 3.12).
 python3-samba depends on python3 (>= 3.11~).
 python3-samba depends on python3:any.
 python3-samba depends on python3 (<< 3.12).
 python3-samba depends on python3 (>= 3.11~).
 python3-samba depends on python3:any.
 python3-rich depends on python3-typing-extensions (>= 3.7.4) | python3 (>> 3.9); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-rich depends on python3:any.
 python3-rich depends on python3-typing-extensions (>= 3.7.4) | python3 (>> 3.9); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-rich depends on python3:any.
 python3-requests depends on python3:any.
 python3-reportlab-accel:amd64 depends on python3 (<< 3.12).
 python3-reportlab-accel:amd64 depends on python3 (>= 3.11~).
 python3-reportlab-accel:amd64 depends on python3 (<< 3.12).
 python3-reportlab-accel:amd64 depends on python3 (>= 3.11~).
 python3-reportlab depends on python3:any.
 python3-rencode depends on python3 (<< 3.12).
 python3-rencode depends on python3 (>= 3.11~).
 python3-rencode depends on python3:any.
 python3-rencode depends on python3 (<< 3.12).
 python3-rencode depends on python3 (>= 3.11~).
 python3-rencode depends on python3:any.
 python3-rencode depends on python3 (<< 3.12).
 python3-rencode depends on python3 (>= 3.11~).
 python3-rencode depends on python3:any.
 python3-pyudev depends on python3:any.
 python3-pyrsistent:amd64 depends on python3 (<< 3.12).
 python3-pyrsistent:amd64 depends on python3 (>= 3.11~).
 python3-pyrsistent:amd64 depends on python3:any.
 python3-pyrsistent:amd64 depends on python3 (<< 3.12).
 python3-pyrsistent:amd64 depends on python3 (>= 3.11~).
 python3-pyrsistent:amd64 depends on python3:any.
 python3-pyrsistent:amd64 depends on python3 (<< 3.12).
 python3-pyrsistent:amd64 depends on python3 (>= 3.11~).
 python3-pyrsistent:amd64 depends on python3:any.
 python3-pyqt5.sip depends on python3 (<< 3.12).
 python3-pyqt5.sip depends on python3 (>= 3.11~).
 python3-pyqt5.sip depends on python3 (<< 3.12).
 python3-pyqt5.sip depends on python3 (>= 3.11~).
 python3-pyqt5 depends on python3 (>= 3~).
 python3-pyqt5 depends on python3:any.
 python3-pyqt5 depends on python3 (>= 3~).
 python3-pyqt5 depends on python3:any.
 python3-pyparsing depends on python3:any.
 python3-pymacaroons depends on python3:any.
 python3-pyinotify depends on python3:any.
 python3-pygments depends on python3:any.
 python3-pyatspi depends on python3:any.
 python3-ptyprocess depends on python3:any.
 python3-psutil depends on python3 (<< 3.12).
 python3-psutil depends on python3 (>= 3.11~).
 python3-psutil depends on python3:any.
 python3-psutil depends on python3 (<< 3.12).
 python3-psutil depends on python3 (>= 3.11~).
 python3-psutil depends on python3:any.
 python3-psutil depends on python3 (<< 3.12).
 python3-psutil depends on python3 (>= 3.11~).
 python3-psutil depends on python3:any.
 python3-problem-report depends on python3:any.
 python3-powerline depends on python3:any.
 python3-pkg-resources depends on python3:any.
 python3-pip depends on python3:any.
 python3-pil:amd64 depends on python3 (<< 3.12).
 python3-pil:amd64 depends on python3 (>= 3.11~).
 python3-pil:amd64 depends on python3:any.
 python3-pil:amd64 depends on python3 (<< 3.12).
 python3-pil:amd64 depends on python3 (>= 3.11~).
 python3-pil:amd64 depends on python3:any.
 python3-pil:amd64 depends on python3 (<< 3.12).
 python3-pil:amd64 depends on python3 (>= 3.11~).
 python3-pil:amd64 depends on python3:any.
 python3-pexpect depends on python3:any.
 python3-parted depends on python3 (<< 3.12).
 python3-parted depends on python3 (>= 3.11~).
 python3-parted depends on python3:any.
 python3-parted depends on python3 (<< 3.12).
 python3-parted depends on python3 (>= 3.11~).
 python3-parted depends on python3:any.
 python3-parted depends on python3 (<< 3.12).
 python3-parted depends on python3 (>= 3.11~).
 python3-parted depends on python3:any.
 python3-paramiko depends on python3:any.
 python3-pam depends on python3 (<< 3.12).
 python3-pam depends on python3 (>= 3.11~).
 python3-pam depends on python3 (<< 3.12).
 python3-pam depends on python3 (>= 3.11~).
 python3-opengl depends on python3:any.
 python3-oauthlib depends on python3:any.
 python3-numpy depends on python3 (<< 3.12).
 python3-numpy depends on python3 (>= 3.11~).
 python3-numpy depends on python3:any.
 python3-numpy depends on python3 (<< 3.12).
 python3-numpy depends on python3 (>= 3.11~).
 python3-numpy depends on python3:any.
 python3-numpy depends on python3 (<< 3.12).
 python3-numpy depends on python3 (>= 3.11~).
 python3-numpy depends on python3:any.
 python3-ntp depends on python3.
 python3-ntp depends on python3:any.
 python3-ntp depends on python3.
 python3-ntp depends on python3:any.
 python3-nftables depends on python3:any.
 python3-netifaces:amd64 depends on python3 (<< 3.12).
 python3-netifaces:amd64 depends on python3 (>= 3.11~).
 python3-netifaces:amd64 depends on python3 (<< 3.12).
 python3-netifaces:amd64 depends on python3 (>= 3.11~).
 python3-nacl depends on python3 (>= 3~).
 python3-nacl depends on python3:any.
 python3-nacl depends on python3 (>= 3~).
 python3-nacl depends on python3:any.
 python3-more-itertools depends on python3:any.
 python3-monotonic depends on python3:any.
 python3-mechanize depends on python3:any.
 python3-mdurl depends on python3:any.
 python3-markupsafe depends on python3 (<< 3.12).
 python3-markupsafe depends on python3 (>= 3.11~).
 python3-markupsafe depends on python3:any.
 python3-markupsafe depends on python3 (<< 3.12).
 python3-markupsafe depends on python3 (>= 3.11~).
 python3-markupsafe depends on python3:any.
 python3-markupsafe depends on python3 (<< 3.12).
 python3-markupsafe depends on python3 (>= 3.11~).
 python3-markupsafe depends on python3:any.
 python3-markdown-it depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-markdown-it depends on python3:any.
 python3-markdown-it depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-markdown-it depends on python3:any.
 python3-markdown depends on python3:any.
 python3-markdown depends on python3:any.
 python3-mako depends on python3:any.
 python3-mako depends on python3:any.
 python3-magic depends on python3:any.
 python3-lzo:amd64 depends on python3 (<< 3.12).
 python3-lzo:amd64 depends on python3 (>= 3.11~).
 python3-lzo:amd64 depends on python3 (<< 3.12).
 python3-lzo:amd64 depends on python3 (>= 3.11~).
 python3-lz4 depends on python3 (<< 3.12).
 python3-lz4 depends on python3 (>= 3.11~).
 python3-lz4 depends on python3:any.
 python3-lz4 depends on python3 (<< 3.12).
 python3-lz4 depends on python3 (>= 3.11~).
 python3-lz4 depends on python3:any.
 python3-lz4 depends on python3 (<< 3.12).
 python3-lz4 depends on python3 (>= 3.11~).
 python3-lz4 depends on python3:any.
 python3-louis depends on python3:any.
 python3-lockfile depends on python3:any.
 python3-libxml2:amd64 depends on python3 (<< 3.12).
 python3-libxml2:amd64 depends on python3 (>= 3.11~).
 python3-libxml2:amd64 depends on python3:any.
 python3-libxml2:amd64 depends on python3 (<< 3.12).
 python3-libxml2:amd64 depends on python3 (>= 3.11~).
 python3-libxml2:amd64 depends on python3:any.
 python3-libxml2:amd64 depends on python3 (<< 3.12).
 python3-libxml2:amd64 depends on python3 (>= 3.11~).
 python3-libxml2:amd64 depends on python3:any.
 python3-libvirt depends on python3 (<< 3.12).
 python3-libvirt depends on python3 (>= 3.11~).
 python3-libvirt depends on python3:any.
 python3-libvirt depends on python3 (<< 3.12).
 python3-libvirt depends on python3 (>= 3.11~).
 python3-libvirt depends on python3:any.
 python3-libvirt depends on python3 (<< 3.12).
 python3-libvirt depends on python3 (>= 3.11~).
 python3-libvirt depends on python3:any.
 python3-libevdev depends on python3:any.
 python3-lib2to3 depends on python3:any (>= 3.10.8-0~).
 python3-lib2to3 depends on python3:any (<< 3.12).
 python3-lib2to3 depends on python3:any (>= 3.10.8-0~).
 python3-lib2to3 depends on python3:any (<< 3.12).
 python3-ldb depends on python3 (<< 3.12).
 python3-ldb depends on python3 (>= 3.11~).
 python3-ldb depends on python3:any.
 python3-ldb depends on python3 (<< 3.12).
 python3-ldb depends on python3 (>= 3.11~).
 python3-ldb depends on python3:any.
 python3-ldb depends on python3 (<< 3.12).
 python3-ldb depends on python3 (>= 3.11~).
 python3-ldb depends on python3:any.
 python3-lazr.uri depends on python3:any.
 python3-lazr.uri depends on python3:any.
 python3-lazr.restfulclient depends on python3:any.
 python3-lazr.restfulclient depends on python3:any.
 python3-launchpadlib depends on python3:any.
 python3-keyring depends on python3:any.
 python3-kerberos depends on python3 (<< 3.12).
 python3-kerberos depends on python3 (>= 3.11~).
 python3-kerberos depends on python3 (<< 3.12).
 python3-kerberos depends on python3 (>= 3.11~).
 python3-jwt depends on python3:any.
 python3-jsonschema depends on python3-importlib-resources | python3 (>> 3.9); however:
  Package python3-importlib-resources is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3:any.
 python3-jsonschema depends on python3-importlib-resources | python3 (>> 3.9); however:
  Package python3-importlib-resources is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3:any.
 python3-jsonschema depends on python3-importlib-resources | python3 (>> 3.9); however:
  Package python3-importlib-resources is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3:any.
 python3-jsonschema depends on python3-importlib-resources | python3 (>> 3.9); however:
  Package python3-importlib-resources is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-jsonschema depends on python3:any.
 python3-jeepney depends on python3:any.
 python3-jaraco.classes depends on python3:any.
 python3-importlib-metadata depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-importlib-metadata depends on python3:any.
 python3-importlib-metadata depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-importlib-metadata depends on python3:any.
 python3-ifaddr depends on python3:any.
 python3-idna depends on python3:any.
 python3-icu depends on python3 (<< 3.12).
 python3-icu depends on python3 (>= 3.11~).
 python3-icu depends on python3:any.
 python3-icu depends on python3 (<< 3.12).
 python3-icu depends on python3 (>= 3.11~).
 python3-icu depends on python3:any.
 python3-icu depends on python3 (<< 3.12).
 python3-icu depends on python3 (>= 3.11~).
 python3-icu depends on python3:any.
 python3-ibus-1.0 depends on python3:any.
 python3-httplib2 depends on python3:any.
 python3-html5lib depends on python3:any.
 python3-gssapi depends on python3 (<< 3.12).
 python3-gssapi depends on python3 (>= 3.11~).
 python3-gssapi depends on python3:any.
 python3-gssapi depends on python3 (<< 3.12).
 python3-gssapi depends on python3 (>= 3.11~).
 python3-gssapi depends on python3:any.
 python3-gssapi depends on python3 (<< 3.12).
 python3-gssapi depends on python3 (>= 3.11~).
 python3-gssapi depends on python3:any.
 python3-gpg depends on python3 (<< 3.12).
 python3-gpg depends on python3 (>= 3.11~).
 python3-gpg depends on python3:any.
 python3-gpg depends on python3 (<< 3.12).
 python3-gpg depends on python3 (>= 3.11~).
 python3-gpg depends on python3:any.
 python3-gpg depends on python3 (<< 3.12).
 python3-gpg depends on python3 (>= 3.11~).
 python3-gpg depends on python3:any.
 python3-gnupg depends on python3:any.
 python3-gi-cairo depends on python3 (<< 3.12).
 python3-gi-cairo depends on python3 (>= 3.11~).
 python3-gi-cairo depends on python3 (<< 3.12).
 python3-gi-cairo depends on python3 (>= 3.11~).
 python3-gi depends on python3 (<< 3.12).
 python3-gi depends on python3 (>= 3.11~).
 python3-gi depends on python3:any.
 python3-gi depends on python3 (<< 3.12).
 python3-gi depends on python3 (>= 3.11~).
 python3-gi depends on python3:any.
 python3-gi depends on python3 (<< 3.12).
 python3-gi depends on python3 (>= 3.11~).
 python3-gi depends on python3:any.
 python3-gdbm:amd64 depends on python3 (>= 3.10.8-0~).
 python3-gdbm:amd64 depends on python3 (<< 3.12).
 python3-gdbm:amd64 depends on python3 (>= 3.10.8-0~).
 python3-gdbm:amd64 depends on python3 (<< 3.12).
 python3-future depends on python3:any.
 python3-firewall depends on python3:any.
 python3-fasteners depends on python3:any.
 python3-dnspython depends on python3:any.
 python3-dns depends on python3:any.
 python3-distutils depends on python3:any (>= 3.10.8-0~).
 python3-distutils depends on python3:any (<< 3.12).
 python3-distutils depends on python3:any (>= 3.10.8-0~).
 python3-distutils depends on python3:any (<< 3.12).
 python3-distupgrade depends on python3:any.
 python3-distro-info depends on python3:any.
 python3-distro depends on python3:any.
 python3-dev depends on python3 (= 3.11.2-1).
 python3-defer depends on python3:any (>= 3.2~).
 python3-decorator depends on python3:any.
 python3-debian depends on python3:any.
 python3-debconf depends on python3:any.
 python3-dbus.mainloop.pyqt5 depends on python3 (>= 3~).
 python3-dbus depends on python3 (<< 3.12).
 python3-dbus depends on python3 (>= 3.11~).
 python3-dbus depends on python3:any.
 python3-dbus depends on python3 (<< 3.12).
 python3-dbus depends on python3 (>= 3.11~).
 python3-dbus depends on python3:any.
 python3-dbus depends on python3 (<< 3.12).
 python3-dbus depends on python3 (>= 3.11~).
 python3-dbus depends on python3:any.
 python3-dateutil depends on python3:any.
 python3-cupshelpers depends on python3:any.
 python3-cups:amd64 depends on python3 (<< 3.12).
 python3-cups:amd64 depends on python3 (>= 3.11~).
 python3-cups:amd64 depends on python3 (<< 3.12).
 python3-cups:amd64 depends on python3 (>= 3.11~).
 python3-cryptography depends on python3 (>= 3~).
 python3-cryptography depends on python3:any.
 python3-cryptography depends on python3 (>= 3~).
 python3-cryptography depends on python3:any.
 python3-cpuinfo depends on python3:any.
 python3-commandnotfound depends on python3:any.
 python3-colorama depends on python3:any.
 python3-click depends on python3:any.
 python3-click depends on python3:any.
 python3-chardet depends on python3:any.
 python3-cffi-backend:amd64 depends on python3 (<< 3.12).
 python3-cffi-backend:amd64 depends on python3 (>= 3.11~).
 python3-cffi-backend:amd64 depends on python3 (<< 3.12).
 python3-cffi-backend:amd64 depends on python3 (>= 3.11~).
 python3-certifi depends on python3:any.
 python3-cap-ng depends on python3 (<< 3.12).
 python3-cap-ng depends on python3 (>= 3.11~).
 python3-cap-ng depends on python3:any.
 python3-cap-ng depends on python3 (<< 3.12).
 python3-cap-ng depends on python3 (>= 3.11~).
 python3-cap-ng depends on python3:any.
 python3-cap-ng depends on python3 (<< 3.12).
 python3-cap-ng depends on python3 (>= 3.11~).
 python3-cap-ng depends on python3:any.
 python3-cairo:amd64 depends on python3 (<< 3.12).
 python3-cairo:amd64 depends on python3 (>= 3.11~).
 python3-cairo:amd64 depends on python3:any.
 python3-cairo:amd64 depends on python3 (<< 3.12).
 python3-cairo:amd64 depends on python3 (>= 3.11~).
 python3-cairo:amd64 depends on python3:any.
 python3-cairo:amd64 depends on python3 (<< 3.12).
 python3-cairo:amd64 depends on python3 (>= 3.11~).
 python3-cairo:amd64 depends on python3:any.
 python3-brotli depends on python3 (<< 3.12).
 python3-brotli depends on python3 (>= 3.11~).
 python3-brotli depends on python3:any.
 python3-brotli depends on python3 (<< 3.12).
 python3-brotli depends on python3 (>= 3.11~).
 python3-brotli depends on python3:any.
 python3-brotli depends on python3 (<< 3.12).
 python3-brotli depends on python3 (>= 3.11~).
 python3-brotli depends on python3:any.
 python3-brlapi:amd64 depends on python3 (<< 3.12).
 python3-brlapi:amd64 depends on python3 (>= 3.11~).
 python3-brlapi:amd64 depends on python3 (<< 3.12).
 python3-brlapi:amd64 depends on python3 (>= 3.11~).
 python3-blinker depends on python3:any.
 python3-bcrypt depends on python3 (>= 3~).
 python3-bcrypt depends on python3:any.
 python3-bcrypt depends on python3 (>= 3~).
 python3-bcrypt depends on python3:any.
 python3-attr depends on python3:any.
 python3-async-timeout depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-async-timeout depends on python3:any.
 python3-async-timeout depends on python3-typing-extensions | python3 (>> 3.8); however:
  Package python3-typing-extensions is not installed.
  Package python3 is to be removed.
 python3-async-timeout depends on python3:any.
 python3-asn1crypto depends on python3:any.
 python3-aptdaemon.gtk3widgets depends on python3:any (>= 3.2~).
 python3-aptdaemon depends on python3:any (>= 3.2~).
 python3-apt depends on python3 (<< 3.12).
 python3-apt depends on python3 (>= 3.11~).
 python3-apt depends on python3:any.
 python3-apt depends on python3 (<< 3.12).
 python3-apt depends on python3 (>= 3.11~).
 python3-apt depends on python3:any.
 python3-apt depends on python3 (<< 3.12).
 python3-apt depends on python3 (>= 3.11~).
 python3-apt depends on python3:any.
 python3-apport depends on python3:any.
 python-is-python3 depends on python3.
 printer-driver-sag-gdi depends on python3:any.
 printer-driver-pxljr depends on python3:any.
 printer-driver-ptouch depends on python3:any.
 printer-driver-postscript-hp depends on python3:any.
 printer-driver-m2300w depends on python3:any.
 printer-driver-fujixerox depends on python3:any.
 printer-driver-foo2zjs-common depends on python3:any.
 printer-driver-escpr depends on python3:any.
 printer-driver-dymo depends on python3:any.
 powerline depends on python3:any.
 onboard-common depends on python3.
 onboard depends on python3 (<< 3.12).
 onboard depends on python3 (>= 3.11~).
 onboard depends on python3:any.
 onboard depends on python3 (<< 3.12).
 onboard depends on python3 (>= 3.11~).
 onboard depends on python3:any.
 onboard depends on python3 (<< 3.12).
 onboard depends on python3 (>= 3.11~).
 onboard depends on python3:any.
 nvidia-prime depends on python3:any.
 ntpsec-ntpdig depends on python3 (>= 3.3).
 ntpsec depends on python3.
 networkd-dispatcher depends on python3:any.
 netplan.io depends on python3.
 mugshot depends on python3:any.
 mintstick depends on python3.
 menulibre depends on python3:any.
 lite-welcome depends on python3.
 lightdm-gtk-greeter-settings depends on python3:any.
 libwacom-bin depends on python3:any.
 libglib2.0-dev-bin depends on python3:any.
 language-selector-gnome depends on python3:any.
 language-selector-common depends on python3:any.
 ibus depends on python3:any.
 hplip-data depends on python3:any.
 hplip depends on python3:any.
 hplip depends on python3 (<< 3.12).
 hplip depends on python3 (>= 3.11~).
 hplip depends on python3:any.
 hplip depends on python3 (<< 3.12).
 hplip depends on python3 (>= 3.11~).
 hplip depends on python3:any.
 hplip depends on python3 (<< 3.12).
 hplip depends on python3 (>= 3.11~).
 gobject-introspection depends on python3 (<< 3.12).
 gobject-introspection depends on python3 (>= 3.11~).
 gobject-introspection depends on python3:any.
 gobject-introspection depends on python3 (<< 3.12).
 gobject-introspection depends on python3 (>= 3.11~).
 gobject-introspection depends on python3:any.
 gobject-introspection depends on python3 (<< 3.12).
 gobject-introspection depends on python3 (>= 3.11~).
 gobject-introspection depends on python3:any.
 gnome-menus depends on python3:any.
 gir1.2-xapp-1.0 depends on python3:any.
 gdebi-core depends on python3:any (>= 3.3~).
 gdebi depends on python3:any (>= 3.3~).
 gconf2 depends on python3:any.
 foomatic-db-compressed-ppds depends on python3:any.
 firewalld depends on python3:any.
 firewall-config depends on python3:any.
 firewall-applet depends on python3:any.
 duplicity depends on python3 (<< 3.12).
 duplicity depends on python3 (>= 3.11~).
 duplicity depends on python3:any (>= 3.7~).
 duplicity depends on python3 (<< 3.12).
 duplicity depends on python3 (>= 3.11~).
 duplicity depends on python3:any (>= 3.7~).
 duplicity depends on python3 (<< 3.12).
 duplicity depends on python3 (>= 3.11~).
 duplicity depends on python3:any (>= 3.7~).
 dput depends on python3:any.
 dh-python depends on python3:any.
 dh-python depends on python3:any.
 devscripts depends on python3:any.
 cifs-utils depends on python3.
 catfish depends on python3:any.
 blueman depends on python3 (<< 3.12).
 blueman depends on python3 (>= 3.11~).
 blueman depends on python3:any.
 blueman depends on python3 (<< 3.12).
 blueman depends on python3 (>= 3.11~).
 blueman depends on python3:any.
 blueman depends on python3 (<< 3.12).
 blueman depends on python3 (>= 3.11~).
 blueman depends on python3:any.
 aptdaemon depends on python3:any (>= 3.2~).
 apt-xapian-index depends on python3.
 apt-xapian-index depends on python3:any.
 apt-xapian-index depends on python3.
 apt-xapian-index depends on python3:any.
 apt-clone depends on python3:any.
 apt-clone depends on python3.
 apt-clone depends on python3:any.
 apt-clone depends on python3.

```
That Removal List should scare the crap out of anyone wanting to play around with python.
lesson to all.

---

### Post by #&amp;thj^% on 2023-09-16
Well I'll be damned, it did work after all, I'll fix the post above in a minute.
running some more checks.
Good to Go now everything works as before the removal. :)
EDIT:All this was done after a reboot, all systems go.

---

### Post by peyre on 2023-09-17
Ok, sudo apt-get install --reinstall python returned
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  2to3 python2-minimal:i386 python2:i386 python2-minimal python2 dh-python
  python-is-python3
```

So I tried the next part.  Good news, it doesn't seem to have done any harm.  However it didn't fix it either. :(

If this were my laptop I'd just wipe and install from scratch, but my desktop is more complex to configure everything on.

---

### Post by #&amp;thj^% on 2023-09-17
> **peyre said:**
> 
If this were my laptop I'd just wipe and install from scratch, but my desktop is more complex to configure everything on.

Is this a work laptop?
Yep fastest solution, backup important files via a live usb, and reinstall. 

I know now is not the time, but why do you not have a back-up solution.
I've thrown everything I possibly can suggest here, I feel bad your in this mess. I can relate though, some of my hardest lessons came from not having a back-up solution in place with complex Desktop/Server setups.
Now all I have is:
```
sudo apt install --reinstall xubuntu-desktop
```
Stop on any errors it throws and paste them back here, I'll hang in here to help if possible.
```
cd /usr/bin/ && ls | grep python
dh_python3
dh_python3-ply
python
python3
python3.10
python3.10-config
python3.11
python3.11-config
python3-config
python3-futurize
python3-pasteurize
python3-unidiff
x86_64-linux-gnu-python3.10-config
x86_64-linux-gnu-python3.11-config
x86_64-linux-gnu-python3-config

```

---

### Post by peyre on 2023-09-17
Oh no, this is my desktop, not a laptop - I was just saying that if this were happening on the laptop it wouldn't be much of a problem.  And no, these are both personal items.  On a side note, a computer from work would be much more powerful than the old rebated stuff I use at home.  This is an old machine from 2009 running a Core 2 Duo processor (slightly overclocked).

I have backups.  I back up to a portable hard drive using a shell script (and batch file on the wife's computer).  Then every few months I take it to the office and bring home the other portable drive.   That way I keep offsite backups too.  It's just that for my desktop, I have a lot of customizations that are time-consuming to make after an install from scratch.

Thanks! The reinstall command returned
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 21 not upgraded.
Need to get 2,538 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 xubuntu-desktop amd64 2.241 [2,538 B]
Fetched 2,538 B in 1s (2,106 B/s)                    
(Reading database ... 277438 files and directories currently installed.)
Preparing to unpack .../xubuntu-desktop_2.241_amd64.deb ...
Unpacking xubuntu-desktop (2.241) over (2.241) ...
Setting up xubuntu-desktop (2.241) ...
```

So...the issue's still ongoing.  I wonder if we could implement a workaround, have the system run **dhclient -r** and **sudo dhclient** on startup.  That should keep network functioning, though it leaves the other issue, that my shares no longer function.  I sometimes copy files (sometimes ISOs) between this and my son's computer, and I hate to use a flash drive when we have a gigabit wired connection.

---

### Post by #&amp;thj^% on 2023-09-17
> **peyre said:**
> Oh no, this is my desktop, not a laptop - I was just saying that if this were happening on the laptop it wouldn't be much of a problem.  And no, these are both personal items.  (On a side note, a computer from work would be much more powerful than the old rebated stuff I use at home.

I have backups.  I back up to a portable hard drive using a shell script (and batch file on the wife's computer).  Then every few months I take it to the office and bring home the other portable drive.   That way I keep offsite backups too.  It's just that for my desktop, I have a lot of customizations that are time-consuming to make after an install from scratch.

Thanks! The reinstall command returned
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 21 not upgraded.
Need to get 2,538 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 xubuntu-desktop amd64 2.241 [2,538 B]
Fetched 2,538 B in 1s (2,106 B/s)                    
(Reading database ... 277438 files and directories currently installed.)
Preparing to unpack .../xubuntu-desktop_2.241_amd64.deb ...
Unpacking xubuntu-desktop (2.241) over (2.241) ...
Setting up xubuntu-desktop (2.241) ...
```
Understood, and Thanks for clearing that up, please try the above then.
EDIT: I just saw your edit, now run:
```
sudo apt install --reinstall xfce4
```
If you want it all throw in:
```
sudo apt install --reinstall xfce4-goodies 
```
Which will bring in:
```
This package will install the following Xfce4 related plugins:
   * Extra artwork (xfce4-artwork)
   * Battery levels monitor (xfce4-battery-plugin)
   * Clipboard history (xfce4-clipman-plugin)
   * CPU frequency management plugin (xfce4-cpufreq-plugin)
   * CPU utilisation graphs (xfce4-cpugraph-plugin)
   * Date and time plugin (xfce4-datetime-plugin)
   * Disk performance display (xfce4-diskperf-plugin)
   * Filesystem monitor (xfce4-fsguard-plugin)
   * Generic monitor, for displaying any command result (xfce4-genmon-plugin)
   * Mail watcher (xfce4-mailwatch-plugin)
   * Network load monitor (xfce4-netload-plugin)
   * Notes plugin (xfce4-notes-plugin)
   * Quick access to bookmarked folders, recent documents and removable
     media (xfce4-places-plugin)
   * Sensors plugin, frontend to lm-sensors (xfce4-sensors-plugin)
   * Smartbookmarks plugin (xfce4-smartbookmark-plugin)
   * System load monitor (xfce4-systemload-plugin)
   * Timer plugin (xfce4-timer-plugin)
   * Command line with history (xfce4-verve-plugin)
   * Wireless lan monitor (xfce4-wavelan-plugin)
   * Weather monitor (xfce4-weather-plugin)
   * Keyboard configuration (xfce4-xkb-plugin)
   * Archive management for Thunar (thunar-archive-plugin)
   * Media tags editor for Thunar (thunar-media-tags-plugin)
   * Alternate menu plugin (xfce4-whiskermenu-plugin)
 .
 It'll install some standalone applications too:
   * Tiny text editor (mousepad)
   * Images viewer (ristretto)
   * CD/DVD burner (xfburn)
   * Frontend to dictionaries (xfce4-dict)
   * Notification daemon (xfce4-notifyd)
   * Tool to take screenshots (xfce4-screenshooter)
   * Task manager (xfce4-taskmanager)
   * Terminal emulator (xfce4-terminal)

```
Good Luck I'll be here if needed for a couple of hours.

---

### Post by peyre on 2023-09-17
Thanks for those ideas!  Sadly they didn't fix it.  This issue sure is being stubborn!

---

### Post by #&amp;thj^% on 2023-09-17
Stubborn is putting it lightly, possessed is more like it.
What shows here:
```
sudo systemctl restart systemd-networkd

```

---

### Post by peyre on 2023-09-17
Shoot!  It ran without returning anything, and on reboot, still no networking until I do the dhclient trick. :(

I appreciate your patience through this whole situation!

---

### Post by #&amp;thj^% on 2023-09-17
> **peyre said:**
> Shoot!  It ran without returning anything, and on reboot, still no networking until I do the dhclient trick. :(

I appreciate your patience through this whole situation!

Bingo We found it.
Mine:
```
systemctl status systemd-networkd
&#9679; systemd-networkd.service - Network Configuration
     Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled-runt>
     Active: active (running) since Sun 2023-09-17 12:06:13 MDT; 10min ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
   Main PID: 146840 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18144)
     Memory: 1.6M
        CPU: 26ms
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;146840 /lib/systemd/systemd-networkd

Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: virbr0: Link UP
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: enx70b3d55c01b3: Link UP
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: enx70b3d55c01b3: Gained carr>
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: eno1: Link UP
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: lo: Link UP
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: lo: Gained carrier
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: surfshark_ipv6: Gained IPv6LL
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: enx70b3d55c01b3: Gained IPv6>
Sep 17 12:06:13 lvm-lite systemd-networkd[146840]: Enumeration completed
Sep 17 12:06:13 lvm-lite systemd[1]: Started systemd-networkd.service - Network>

```
So now we a direction to follow, one step at a time:
```
systemctl enable systemd-networkd

```
should look something like:
```
Created symlink /etc/systemd/system/dbus-org.freedesktop.network1.service &#8594; /lib/systemd/system/systemd-networkd.service.
Created symlink /etc/systemd/system/multi-user.target.wants/systemd-networkd.service &#8594; /lib/systemd/system/systemd-networkd.service.
Created symlink /etc/systemd/system/sockets.target.wants/systemd-networkd.socket &#8594; /lib/systemd/system/systemd-networkd.socket.
Created symlink /etc/systemd/system/sysinit.target.wants/systemd-network-generator.service &#8594; /lib/systemd/system/systemd-network-generator.service.
Created symlink /etc/systemd/system/network-online.target.wants/systemd-networkd-wait-online.service &#8594; /lib/systemd/system/systemd-networkd-wait-online.service.

```
I'll need to see that first thing.

---

### Post by peyre on 2023-09-17
Yes, it showed just that!
```
Created symlink /etc/systemd/system/dbus-org.freedesktop.network1.service &#8594; /lib/systemd/system/systemd-networkd.service.
Created symlink /etc/systemd/system/multi-user.target.wants/systemd-networkd.service &#8594; /lib/systemd/system/systemd-networkd.service.
Created symlink /etc/systemd/system/sockets.target.wants/systemd-networkd.socket &#8594; /lib/systemd/system/systemd-networkd.socket.
Created symlink /etc/systemd/system/sysinit.target.wants/systemd-network-generator.service &#8594; /lib/systemd/system/systemd-network-generator.service.
Created symlink /etc/systemd/system/network-online.target.wants/systemd-networkd-wait-online.service &#8594; /lib/systemd/system/systemd-networkd-wait-online.service.
```

---

### Post by #&amp;thj^% on 2023-09-17
Good Now be very careful to not upset that demon that is now with:
```
systemctl start --now systemd-networkd
```
Fingers Crossed

---

### Post by peyre on 2023-09-17
I ran that and rebooted, but still no networking on startup. :(

---

### Post by #&amp;thj^% on 2023-09-17
peyre will you run the system-info script in my signature, I'm now on a mission to solve this>
Please run it with --details for the flag, and post back the link it gives you here.
ie:
```
./system-info --details
```

---

### Post by peyre on 2023-09-17
Shoot!  It says "Failed to contact the server: <urlopen error unknown url type: https>" then Upload failed.  I've archived it; here are the contents:

```
Starting the Ubuntu Forums 'system-info' Report: 2023-09-17  11:55:34 PDT (-0700)
	Part of the Ama-gi Project
	Version: 02.00-08, Script Date: 2023.05.24

---------------------------------------------------------------
Main Complaint: NIC no longer starts on bootup
Problem Description:  After doing a complete removal of python3, the network card no longer starts on bootup.
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
    Vendor: Intel Corp.
    Physical id: 4
    Bus info: cpu@0
    Version: 6.23.6
    Slot: Socket 775
    Size: 1709MHz
    Capacity: 4GHz
    Width: 64 bits
    Clock: 200MHz
    Capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
        sse2 ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts 
        rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 
        cx16 xtpr pdcm lahf_lm pti dtherm cpufreq
    Configuration: microcode=1551

computer
    Description: Desktop Computer
    Product: G31M-ES2L
    Vendor: Gigabyte Technology Co., Ltd.
    Width: 64 bits
    Capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         Award Software International Inc.
Bios Version:        F10
Board Vendor:        Gigabyte Technology Co. Ltd.
Board Name:          G31M-S2L
Board Version:       x.x
Board Serial:        

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
   --- SecureBoot Status from 'mokutil':
EFI variables are not supported on this system


Further details from BIOS:
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: F10
	Release Date: 09/29/2009
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: G31M-ES2L
	Version:  
	Serial Number:  
	UUID: 00000000-0000-0000-0000-00241d1db733
	Wake-up Type: Power Switch
	SKU Number:  
	Family:  

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket 775
	Type: Central Processor
	Family: Other
	Manufacturer: Intel
	ID: 76 06 01 00 FF FB EB BF
	Version: Pentium(R) Dual-Core CPU E5
	Voltage: 1.2 V
	External Clock: 200 MHz
	Max Speed: 4000 MHz
	Current Speed: 2500 MHz
	Status: Populated, Enabled
	Upgrade: Socket 478
	L1 Cache Handle: 0x0008
	L2 Cache Handle: 0x0009
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number:  


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:            3910        1826         121          52        1962        1773
Swap:           2047           0        2047

---------- Swap Information:
  --- Info from 'fstab'
/swapfile                                 none            swap    sw              0       0

  --- Info from '/proc/swaps'
Filename				Type		Size		Used		Priority
/swapfile                               file		2097148		256		-2

  --- System Swapiness Settings
Valid swappiness settings are from 10 - 60 . 
Current setting in '/proc/sys/vm/swappiness': 15 
Current configuration setting in '/etc/sysctl.conf file: 
vm.swappiness=15

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

For more detailed wireless information, get and run the script at https://github.com/UbuntuForums/wireless-info 

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: peyre


---------- Storage Controller Information From 'lspci':
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [ISA Compatibility mode controller, supports both channels switched to PCI native mode, supports bus mastering])
	Subsystem: Gigabyte Technology Co., Ltd 82801G (ICH7 Family) IDE Controller
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at 000001f0 (32-bit, non-prefetchable) [virtual] [size=8]
	Region 1: Memory at 000003f0 (type 3, non-prefetchable) [virtual]
	Region 2: Memory at 00000170 (32-bit, non-prefetchable) [virtual] [size=8]
	Region 3: Memory at 00000370 (type 3, non-prefetchable) [virtual]
	Region 4: I/O ports at f900 [virtual] [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi


00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 8f [PCI native mode controller, supports both channels switched to ISA compatibility mode, supports bus mastering])
	Subsystem: Gigabyte Technology Co., Ltd NM10/ICH7 Family SATA Controller [IDE mode]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at f800 [size=8]
	Region 1: I/O ports at f700 [size=4]
	Region 2: I/O ports at f600 [size=8]
	Region 3: I/O ports at f500 [size=4]
	Region 4: I/O ports at f400 [size=16]
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi


---------- File system specs from 'df -h':
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb3      ext4  468G  138G  307G  31% /
/dev/sdb2      vfat  512M  6.1M  506M   2% /boot/efi
/dev/sdc1      ext4  1.4T  841G  464G  65% /media/Storage

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sdb: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: SanDisk SDSSDH3 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D97721F3-3F4A-4148-BC34-4777DD1DD73A

Device       Start        End   Sectors   Size Type
/dev/sdb1     2048       4095      2048     1M BIOS boot
/dev/sdb2     4096    1054719   1050624   513M EFI System
/dev/sdb3  1054720 1000214527 999159808 476.4G Linux filesystem

Disk /dev/sdc: 1.36 TiB, 1500300828160 bytes, 2930275055 sectors
Disk model: SAMSUNG HD154UI 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x27e9bfe8

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1        2048 2930274303 2930272256  1.4T 83 Linux


---------- Disk/Partition Information From 'lsblk':
NAME     SIZE FSTYPE   LABEL   MOUNTPOINT                                   MODEL
fd0        4K                                                               
sda        0B                                                               ZIP 100
sdb    476.9G                                                               SanDisk SDSSDH3 512G
|_sdb1     1M                                                               
|_sdb2   513M vfat             /boot/efi                                    
|_sdb3 476.4G ext4             /                                            
sdc      1.4T                                                               SAMSUNG HD154UI
|_sdc1   1.4T ext4     Storage /media/Storage                               
sdd        0B                                                               SD/MMC
sde        0B                                                               Compact Flash
sdf        0B                                                               SM/xD-Picture
sdg        0B                                                               MS/MS-Pro
sdh        0B                                                               ZIP 250
sr0     1024M                                                               TSSTcorpDVD-ROM TS-H352C
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
fd0          1                                      
sda          1                                      
sdb          0                                      
|_sdb1       0 bd1cdd33-7bd0-4ea8-875f-919082077168 
|_sdb2       0 51faa525-363a-42f3-b7b2-d31dcc099c7a 3D1B-BAAB
|_sdb3       0 10aa21fd-b991-47f7-8484-f24525102f08 8784334d-51f5-4d7e-8c64-c2b42719abe4
sdc          0                                      
|_sdc1       0 27e9bfe8-01                          2c2262cb-3edb-4003-ba6a-4ed7aa4c03e7
sdd          1                                      
sde          1                                      
sdf          1                                      
sdg          1                                      
sdh          1                                      
sr0          1                                      

----------  BTRFS Information:
There are no BTRFS vdev's present.

----------  LVM2 Information:
There are no LVM2 volumes present.

----------  mdadm RAID Information:
No active md devices present.


---------- Mount Details of '/etc/fstab':
UUID=8784334d-51f5-4d7e-8c64-c2b42719abe4 /               ext4    errors=remount-ro 0       1
UUID=3D1B-BAAB  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=2c2262cb-3edb-4003-ba6a-4ed7aa4c03e7 /media/Storage ext4 defaults 0 2
/dev/fd0 /media/floppy0 auto rw,user,sync,noauto,exec,utf8 0 0
tmpfs /home/user/.cache tmpfs nodev,nosuid,nodiratime,size=2048M 0 0

---------- Current Mount Details of 'mount':
/dev/sdb2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sdb3 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime,errors=remount-ro)
/dev/sdc1 on /media/Storage type ext4 (rw,relatime)

For more detailed disk Information, please run the 'boot-info' script 
from: (STABLE) https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair 

---------- USB Information from 'lsusb -t -v':
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    /sys/bus/usb/devices/usb5  /dev/bus/usb/005/001
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 12M
        ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)
        /sys/bus/usb/devices/5-1  /dev/bus/usb/005/002
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    /sys/bus/usb/devices/usb4  /dev/bus/usb/004/001
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    /sys/bus/usb/devices/usb3  /dev/bus/usb/003/001
    |__ Port 2: Dev 2, If 0, Class=Vendor Specific Class, Driver=btusb, 12M
        ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
        /sys/bus/usb/devices/3-2  /dev/bus/usb/003/002
    |__ Port 2: Dev 2, If 1, Class=Vendor Specific Class, Driver=btusb, 12M
        ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
        /sys/bus/usb/devices/3-2  /dev/bus/usb/003/002
    |__ Port 2: Dev 2, If 2, Class=Vendor Specific Class, Driver=btusb, 12M
        ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
        /sys/bus/usb/devices/3-2  /dev/bus/usb/003/002
    |__ Port 2: Dev 2, If 3, Class=Application Specific Interface, Driver=, 12M
        ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
        /sys/bus/usb/devices/3-2  /dev/bus/usb/003/002
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    /sys/bus/usb/devices/usb2  /dev/bus/usb/002/001
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/8p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    /sys/bus/usb/devices/usb1  /dev/bus/usb/001/001
    |__ Port 3: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
        ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
        /sys/bus/usb/devices/1-3  /dev/bus/usb/001/002
    |__ Port 3: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 480M
        ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
        /sys/bus/usb/devices/1-3  /dev/bus/usb/001/002
    |__ Port 6: Dev 4, If 0, Class=Hub, Driver=hub/4p, 480M
        ID 2109:2812 VIA Labs, Inc. VL812 Hub
        /sys/bus/usb/devices/1-6  /dev/bus/usb/001/004
        |__ Port 2: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            ID 0461:4e22 Primax Electronics, Ltd Dell Mouse, 2 Buttons, Modell: MS111-P
            /sys/bus/usb/devices/1-6.2  /dev/bus/usb/001/007
        |__ Port 1: Dev 6, If 0, Class=Hub, Driver=hub/3p, 12M
            ID 413c:1002 Dell Computer Corp. Keyboard Hub
            /sys/bus/usb/devices/1-6.1  /dev/bus/usb/001/006
            |__ Port 1: Dev 8, If 1, Class=Human Interface Device, Driver=usbhid, 12M
                ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
                /sys/bus/usb/devices/1-6.1.1  /dev/bus/usb/001/008
            |__ Port 1: Dev 8, If 0, Class=Human Interface Device, Driver=usbhid, 12M
                ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
                /sys/bus/usb/devices/1-6.1.1  /dev/bus/usb/001/008

---------- Video Details from 'lspci':
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X] (rev c7) (prog-if 00 [VGA controller])
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at cfe00000 (64-bit, prefetchable) [size=2M]
	Region 4: I/O ports at ae00 [size=256]
	Region 5: Memory at fdc80000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	CorrErr- NonFatalErr- FatalErr- UnsupReq-
			RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ NonFatalErr- FatalErr- UnsupReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 8GT/s, Width x8, ASPM L1, Exit Latency L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
		LnkCtl:	ASPM Disabled; RCB 64 bytes, Disabled- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s (downgraded), Width x8 (ok)
			TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis- NROPrPrP- LTR+
			 10BitTagComp- 10BitTagReq- OBFF Not Supported, ExtFmt+ EETLPPrefix+, MaxEETLPPrefixes 1
			 EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
			 FRS-
			 AtomicOpsCap: 32bit+ 64bit+ 128bitCAS-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- OBFF Disabled,
			 AtomicOpsCtl: ReqEn-
		LnkCap2: Supported Link Speeds: 2.5-8GT/s, Crosslink- Retimer- 2Retimers- DRS-
		LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete- EqualizationPhase1-
			 EqualizationPhase2- EqualizationPhase3- LinkEqualizationRequest-
			 Retimer- 2Retimers- CrosslinkRes: unsupported
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee02004  Data: 0028
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150 v2] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
		AERCap:	First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
			MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap-
		HeaderLog: 00000000 00000000 00000000 00000000
	Capabilities: [200 v1] Physical Resizable BAR
		BAR 0: current size: 256MB, supported: 256MB 512MB 1GB 2GB 4GB
	Capabilities: [270 v1] Secondary PCI Express
		LnkCtl3: LnkEquIntrruptEn- PerformEqu-
		LaneErrStat: 0
	Capabilities: [2b0 v1] Address Translation Service (ATS)
		ATSCap:	Invalidate Queue Depth: 00
		ATSCtl:	Enable-, Smallest Translation Unit: 00
	Capabilities: [2c0 v1] Page Request Interface (PRI)
		PRICtl: Enable- Reset-
		PRISta: RF- UPRGI- Stopped+
		Page Request Capacity: 00000020, Page Request Allocation: 00000000
	Capabilities: [2d0 v1] Process Address Space ID (PASID)
		PASIDCap: Exec+ Priv+, Max PASID Width: 10
		PASIDCtl: Enable- Exec- Priv-
	Capabilities: [320 v1] Latency Tolerance Reporting
		Max snoop latency: 0ns
		Max no snoop latency: 0ns
	Capabilities: [328 v1] Alternative Routing-ID Interpretation (ARI)
		ARICap:	MFVC- ACS-, Next Function: 1
		ARICtl:	MFVC- ACS-, Function Group: 0
	Capabilities: [370 v1] L1 PM Substates
		L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
			  PortCommonModeRestoreTime=0us PortTPowerOnTime=170us
		L1SubCtl1: PCI-PM_L1.2- PCI-PM_L1.1- ASPM_L1.2- ASPM_L1.1-
			   T_CommonMode=0us LTR1.2_Threshold=0ns
		L1SubCtl2: T_PwrOn=10us
	Kernel driver in use: amdgpu
	Kernel modules: amdgpu


   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: XFCE 
The Current Desktop Session is: xubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 16384 x 16384
DisplayPort-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+  75.02  
   1280x800      60.02  
   1152x864      75.00  
   1280x720      60.02  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-A-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+  75.02  
   1920x1080     60.00    59.94  
   1280x800      60.02  
   1152x864      75.00  
   1280x720      60.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
The Current Session Type is: x11 
The Current Display Manager is: lightdm
The Current Desktop Theme: 'Greybird'
The Current Virtual TTY's being used are:
	TTY#	Used By
	tty7	Xorg
	tty1	agetty
	pts/1	bash
	pts/0	bash
	pts/0	system-info
	pts/0	system-info
	pts/0	sed
	pts/0	system-info
	pts/0	ps
	pts/0	awk

---------- Sound Device Information From 'lspci':
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
	Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD (Realtek ALC887)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee02004  Data: 0027
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0
			ExtTag- RBE- FLReset-
		DevCtl:	CorrErr- NonFatalErr- FatalErr- UnsupReq-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr+ TransPend-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=1 ArbSelect=Fixed TC/VC=80
			Status:	NegoPending- InProgress-
	Capabilities: [130 v1] Root Complex Link
		Desc:	PortNumber=0f ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c000
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin B routed to IRQ 26
	Region 0: Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D3 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	CorrErr- NonFatalErr- FatalErr- UnsupReq-
			RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ NonFatalErr- FatalErr- UnsupReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 8GT/s, Width x8, ASPM L1, Exit Latency L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
		LnkCtl:	ASPM Disabled; RCB 64 bytes, Disabled- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s (downgraded), Width x8 (ok)
			TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis- NROPrPrP- LTR+
			 10BitTagComp- 10BitTagReq- OBFF Not Supported, ExtFmt+ EETLPPrefix+, MaxEETLPPrefixes 1
			 EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
			 FRS-
			 AtomicOpsCap: 32bit+ 64bit+ 128bitCAS-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- OBFF Disabled,
			 AtomicOpsCtl: ReqEn-
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete- EqualizationPhase1-
			 EqualizationPhase2- EqualizationPhase3- LinkEqualizationRequest-
			 Retimer- 2Retimers- CrosslinkRes: unsupported
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee01004  Data: 0027
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150 v2] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
		AERCap:	First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
			MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap-
		HeaderLog: 00000000 00000000 00000000 00000000
	Capabilities: [328 v1] Alternative Routing-ID Interpretation (ARI)
		ARICap:	MFVC- ACS-, Next Function: 0
		ARICtl:	MFVC- ACS-, Function Group: 0
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


   --- More Sound Device info from 'aplay' ----
null
    Discard all samples (playback) or generate zero samples (capture)
default
    Playback/recording through the PulseAudio sound server
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hw:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC883 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC883 Digital
    Hardware device with all software conversions
sysdefault:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front output / input
surround21:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC883 Digital
    Direct sample mixing device
usbstream:CARD=Intel
    HDA Intel
    USB Stream Output
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA ATI HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA ATI HDMI, HDMI 2
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 3
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=4
    HDA ATI HDMI, HDMI 4
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dmix:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Direct sample mixing device
dmix:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Direct sample mixing device
dmix:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Direct sample mixing device
dmix:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Direct sample mixing device
usbstream:CARD=HDMI
    HDA ATI HDMI
    USB Stream Output
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

For more detailed audio information, get and run the script at: http://www.alsa-project.org/alsa-info.sh 

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-jammy.list:
deb https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/ jammy main
/etc/apt/sources.list.d/google-chrome.list:
deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main

---------- KeyMap and Locale Information from from various sources:
   --- Keymap Info from 'setxkbmap' ----
rules:      evdev
model:      pc105
layout:     us

   --- More Keymap Info from 'xset' ----
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  no    allow exposures:  no
  timeout:  1800    cycle:  1800
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 600    Suspend: 600    Off: 600
  DPMS is Disabled

   --- More Keymap Info from 'gsettings' ----
gsettings input-sources:  @a(ss) [] 

   --- Locale Info from 'localectl' ----
   System Locale: LANG=en_US.UTF-8
       VC Keymap: n/a
      X11 Layout: us
       X11 Model: pc105

   --- More Locale Info from 'locale' ----
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---------- Other Details from 'Various':
The current kernel version is:       5.15.0-83-generic 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 22.04.3 LTS 

Original Installation Date:          2022-10-22+08:31:28 
Original Installation Media: Xubuntu 22.04 LTS "Jammy Jellyfish" - Release amd64 (20220419)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 6.2.0.32.32
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.25.27

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-22.04 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
android-file-transfer
apt-xapian-index
at
audacious
bluetooth
cmake
cpu-x
debsums
dist
dolphin
dosbox
firefox
flowblade
freecol
gimp-help-es
gimp-help-fr
git
gmtp
gnome-usage
google-chrome-stable
gparted
gpicview
handbrake
hunspell-en-au
hunspell-en-ca
hunspell-en-gb
hunspell-en-za
hunspell-es
hunspell-fr
hunspell-fr-classical
hunspell-oc
hyphen-en-ca
hyphen-en-gb
hyphen-es
hyphen-fr
iat
k3b
kdeconnect
kindleclip
language-pack-es
language-pack-es-base
language-pack-fr
language-pack-fr-base
language-pack-gnome-es
language-pack-gnome-es-base
language-pack-gnome-fr
language-pack-gnome-fr-base
language-pack-gnome-oc
language-pack-gnome-oc-base
language-pack-oc
language-pack-oc-base
liballegro4-dev
libboost-dev
libjsoncpp-dev
libogg-dev
libopenblas0-pthread
libpng-dev
libprotobuf-dev
libreoffice-help-en-gb
libreoffice-help-en-us
libreoffice-help-es
libreoffice-help-fr
libreoffice-l10n-en-gb
libreoffice-l10n-en-za
libreoffice-l10n-es
libreoffice-l10n-fr
libreoffice-l10n-oc
libtheora-dev
libvorbis-dev
mythes-en-au
mythes-es
mythes-fr
nerolinux
net-tools
net.downloadhelper.coapp
protobuf-compiler
smplayer
smplayer-l10n
smplayer-themes
steam-installer
thunderbird-locale-en-gb
thunderbird-locale-es
thunderbird-locale-es-ar
thunderbird-locale-es-es
thunderbird-locale-fr
traceroute
veracrypt
wfrench
wine
winetricks
wspanish
xfce4
xfce4-goodies
xsane

   --- Installed Snap Package List:
audacity
bare
chromium
core
core18
core20
core22
cups
firefox
gaming-graphics-core22
gedit
gimp
gnome-3-28-1804
gnome-3-38-2004
gnome-42-2204
gnome-system-monitor
gtk-common-themes
gtk2-common-themes
kde-frameworks-5-96-qt-5-15-5-core20
kf5-5-105-qt-5-15-9-core22
kf5-5-108-qt-5-15-10-core22
okteta
samba4-manager
skype
smplayer
snapd
solitaire
steam
stellarium-daily
supertuxkart
vlc

   --- Installed Flatpak Package List:
Flatpak is not installed

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
leon     tty7         Sep 17 11:43 (:0)

The User running this script was: leon
uid=1000(leon)
gid=1000(leon)
groups=1000(leon),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),
27(sudo),29(audio),30(dip),44(video),46(plugdev),120(netdev),
122(lpadmin),127(scanner),132(lxd),133(sambashare)

The 'system-info' script was booted from an installed system

The 'system-info' script seems to be running locally

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-5.15.0-83-generic root=UUID=8784334d-51f5-4d7e-8c64-c2b42719abe4 ro quiet splash vt.handoff=7

---- Required Programs For Report.
    All required programs installed for report. 

*** End Of Report ***
```

---

### Post by #&amp;thj^% on 2023-09-17
peyre, have you tried linux-image-generic-hwe-22.04, Kernel Version: 6.2.0.32.32
My Nic had off and on problems with 5.15
I'm now using:
```
*apt policy linux-image-6.2.0-32-generic
linux-image-6.2.0-32-generic:
  Installed: 6.2.0-32.32
  Candidate: 6.2.0-32.32
  Version table:
 *** 6.2.0-32.32 500
        500 http://archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu lunar-security/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by peyre on 2023-09-17
I'd be happy to try it, though I'm not sure how to go about it.

---

### Post by #&amp;thj^% on 2023-09-17
Here is a one liner:
```
sudo apt install linux-image-6.2.0-32-generic  linux-headers-6.2.0-32 linux-modules-6.2.0-32-generic   linux-modules-extra-6.2.0-32-generic  
```

---

### Post by peyre on 2023-09-17
I did it and rebooted, and.......nothing.  I'm having a sad.

---

### Post by #&amp;thj^% on 2023-09-18
> **peyre said:**
> I did it and rebooted, and.......nothing.  I'm having a sad.

What dose nothing mean? Same result no network, or blank screen.
At this point it just seems the wisest thing to do is back-up and re-install.

---

### Post by peyre on 2023-09-18
That's correct: same result, no network.

I suppose a reinstall from scratch would be the way to go.  Too bad; it's a pretty big hassle.  I'll have to go at it this weekend I guess; image the machine to an external drive first and start over.

---

