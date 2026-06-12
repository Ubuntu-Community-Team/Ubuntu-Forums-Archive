---
title: "does this make any sense at all?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-17
so alsa doesn't launch on startup anymore. what's worse, if i open terminal and 
```
sudo /etc/init.d/alsa-utils start
```

i get: 
```
bash: alsa-utils: command not found
```

thinking i might have mis-spelled the name, i do
```
cd /etc/init.d/
```

then
```
ls
acpid                            mountoverflowtmp
acpi-support                     mtab.sh
alsasound                        networking
**alsa-utils**                       NetworkManager
anacron                          pcmciautils
apparmor                         policykit
apport                           powernowd
atd                              powernowd.early
atieventsd                       pppd-dns
avahi-daemon                     procps
binfmt-support                   pulseaudio
bluetooth                        rc
boinc-client                     rc.local
bootlogd                         rcS
bootmisc.sh                      readahead
brltty                           readahead-desktop
checkfs.sh                       README
checkroot.sh                     reboot
console-screen.kbd.sh            rmnologin
console-setup                    rsync
cron                             screen-cleanup
cups                             sendsigs
dbus                             single
dkms_autoinstaller               skeleton
dns-clean                        stop-bootlogd
gdm                              stop-bootlogd-single
glibc.sh                         stop-readahead
hal                              sysklogd
halt                             system-tools-backends
hostname.sh                      timidity
hotkey-setup                     udev
hwclockfirst.sh                  udev-finish
hwclock.sh                       ufw
keyboard-setup                   umountfs
killprocs                        umountnfs.sh
klogd                            umountroot
laptop-mode                      urandom
linux-restricted-modules-common  usplash
loopback                         vbesave
module-init-tools                vboxdrv
mountall-bootclean.sh            virtualbox-ose
mountall.sh                      winbind
mountdevsubfs.sh                 wpa-ifupdown
mountkernfs.sh                   x11-common
mountnfs-bootclean.sh            xserver-xorg-input-wacom
mountnfs.sh

```

i see it. alsa-utils is right there. how can terminal just deny it exists?
can anyone help me on this one?

---

### Post by unutbu on 2009-04-17
Could you post
```

ls -l /etc/init.d/alsa-utils
```

---

### Post by asuastrophysics on 2009-04-17
```
girdy@girdy-desktop:~$ ls -l /etc/init.d/alsa-utils
-rwxr-xr-x 1 root root 9770 2008-11-26 02:29 /etc/init.d/alsa-utils

```

i went ahead and reinstalled all the ALSA packages that were already installed in the synaptic package manager. ill do a reboot here in a bit and tell you how it goes.

---

### Post by asuastrophysics on 2009-04-17
still have the same problem. i think this is happening because last time the computer was on, i followed this thread: 
[http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268)

to update ALSA drivers. on one part of the installation, it says ..."with cards=<your sound card here>
thinking i knew what my sound card was called, i keyed in: SB0090

for sound blaster audigy. this probably wasn't right. 

how do i know what to put for my sound card, so i put that. is there a code i can put in terminal that will display the correct name?

---

### Post by unutbu on 2009-04-17
Sorry, I'm stumped. I don't see how any command you could have run,
such as 
```

sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes

```
would cause the problem you are experiencing.

As for what you should put after "--with-cards": 
Read the configure script, or any documentation that comes in the tar.gz package. It should explain what values are admissible.

There is a small chance that typing
```
./configure --help
``` will explain more about the --with-cards option.

The command "lspci" should give you information on what kind of sound card you have, but you'll have to read the tar.gz documentation to translate your sound card type into the right string to put after "--with-cards".

---

