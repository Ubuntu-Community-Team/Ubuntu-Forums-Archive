---
title: "how to stop BOINC from booting ?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by A2182 on 2008-12-19
hi, guys, I am new to Ubuntu, but somehow an old fans for seti@home.
anyway....

I just installed BOINC today via synaptic, including boinc-client and boinc-manager, the version is 6.2.12-1.

my Ubuntu is 8.10.

the default setting for BOINC is start with linux boot, but I want to disable it after installation.

I found the like from Berkeley:
[http://boinc.berkeley.edu/wiki/Stop_or_start_BOINC_daemon_after_boot]("http://boinc.berkeley.edu/wiki/Stop_or_start_BOINC_daemon_after_boot")

but it seems not working with me...:confused:

here is the response from command "sudo /sbin/chkconfig boinc-client off"

insserv: warning: script 'S01linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'K01gdm' missing LSB tags and overrides
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: script 'S10xserver-xorg-input-wacom' missing LSB tags and overrides
insserv: warning: script 'S05vbesave' missing LSB tags and overrides
insserv: warning: script 'S28NetworkManager' missing LSB tags and overrides
insserv: warning: script 'S10powernowd.early' missing LSB tags and overrides
insserv: warning: script 'S37udev-finish' missing LSB tags and overrides
insserv: warning: script 'S10udev' missing LSB tags and overrides
insserv: warning: script 'S08loopback' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: script 'xserver-xorg-input-wacom' missing LSB tags and overrides
insserv: warning: script 'powernowd.early' missing LSB tags and overrides
insserv: warning: script 'loopback' missing LSB tags and overrides
insserv: warning: script 'NetworkManager' missing LSB tags and overrides
insserv: warning: script 'vbesave' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: There is a loop between service umountnfs and networking
insserv:  loop involving service networking at depth 8
insserv:  loop involving service mountall at depth 7
insserv: There is a loop between service udev and mountall
insserv:  loop involving service checkfs at depth 7
insserv: There is a loop between service umountnfs and networking
insserv: There is a loop between service udev and hwclockfirst
insserv:  loop involving service hwclockfirst at depth 5
insserv:  loop involving service mountdevsubfs at depth 4
insserv:  loop involving service sendsigs at depth 2
insserv:  loop involving service umountnfs at depth 1
insserv:  loop involving service umountfs at depth 1
insserv:  loop involving service checkroot at depth 7
insserv:  loop involving service mountnfs at depth 13
insserv:  loop involving service avahi at depth 14
insserv:  loop involving service hwclock at depth 13
insserv:  loop involving service $network at depth 14
insserv:  loop involving service udev at depth 9
insserv: exiting without changing boot order!
/sbin/insserv failed, exit code 1


what's wrong with this ?

thanks....

---

### Post by Sef on 2008-12-19
moved to absolute beginners.

---

### Post by hyper_ch on 2008-12-19
try:
```

sudo update-rc.d -f boinc remove

```
and if that gives an error, have a look at /etc/init.d and find out the scriptname for "boinc" in there.

---

