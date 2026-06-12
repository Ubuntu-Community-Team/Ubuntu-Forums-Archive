---
title: "gdm doesn't start when booting"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by gabriel b on 2010-10-13
I've used ubuntu for a few years but I post this in the beginners session since I do not know what to do.

Yesterday when I booted my computer gdm didn't start, instead the splash screen was displayed shortly and I was in ttty1. There I could log in and run sudo gdm. I haven't found what causes this, and when rebooting I get the same problem,  so what should I do?

/Gabriel

---

### Post by Hippytaff on 2010-10-13
Have you looked at the log files to see if there is any indication of what is going wrong?

---

### Post by gabriel b on 2010-10-13
I looked through a few logs, trying to compare them to logs from previous start ups, but nothing stood out. But then I wasn't sure what to look for, and what logs I should check.

---

### Post by Hippytaff on 2010-10-13
The boot logs should show any errors that occur during the boot process...if an error is causing GDM not to start then you should find some info here.
 
Not on my Ubuntu box right now so can't check, but I think the path is /var/log/boot

---

### Post by gabriel b on 2010-10-13
Ok, I'll check the boot logs more carefully when I get home.

---

### Post by gabriel b on 2010-10-14
ok this is the content of boot.log

```

fsck från util-linux-ng 2.17.2 
/dev/sda1: rent, 231237/915712 filer, 1154178/3662812 block 
fsck från util-linux-ng 2.17.2 
/dev/sda3: rent, 28986/10797056 filer, 3217561/43172679 block 
init: ureadahead-other main process (781) terminated with status 4  
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 [74G[ OK ] 
 * Setting sensors limits       [80G  [74G[ OK ] 
 [33m*[39;49m Speech-dispatcher configured for user sessions 
 * Starting the Winbind daemon winbind       [80G  [74G[ OK ] 
 * Starting Common Unix Printing System: cupsd       [80G  [74G[ OK ] 
 [33m*[39;49m PulseAudio configured for per-user sessions 
 * Enabling additional executable binary formats binfmt-support       [80G  [74G[ OK ] 
 * Checking battery state...       [80G  [74G[ OK ]
 
```not much help to me...

---

### Post by Hippytaff on 2010-10-14
When you log in are you left with just command line, if so are you able to boot GDM with 'startx'?

---

### Post by gabriel b on 2010-10-14
yes, I'm in tty1 with a
login:

I can start gdm by "sudo gdm", haven't tried startx

found this in deamon.log:
```

gdm-binary[1228]: WARNING: Unable to load file '/etc/gdm/custom.conf': Filen eller katalogen finns inte
gdm-binary[1228]: WARNING: Unable to find users: no seat-id found
gdm-simple-slave[1234]: WARNING: Unable to load file '/etc/gdm/custom.conf': Filen eller katalogen finns inte

```means anything?

---

### Post by Hippytaff on 2010-10-14
Theres something up with your custom.conf file. Have a loook to see if it's there (CD or browse to the /etc/gdm/ directory)...if so take a look at it
 
 
 
```

sudo gedit /etc/gdm/custom.conf

```
 
if it's there post the contents and we'll have a look
 
afterthought - try running this command - gdmsetup - to see if its functioning

---

