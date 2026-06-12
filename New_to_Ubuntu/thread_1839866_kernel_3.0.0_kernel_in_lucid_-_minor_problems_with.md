---
title: "kernel 3.0.0 kernel in lucid - minor problems with apparmor"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by blade4 on 2011-09-06
Hi all . I recently compiled a 3.0.0 kernel for my lucid and its running smoothly so far . The only troubling ( or rather irritating) thing is this message near the end of my boot : 

fsck from util-linux-ng 2.17.2
/dev/loop0: clean, 213931/752192 files, 1403467/3006464 blocks (check in 3 mounts)
 * Starting AppArmor profiles       [80G /etc/rcS.d/S37apparmor: 150: cannot open /sys/kernel/security/apparmor/features: No such file
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/gdm-guest-session (/etc/apparmor.d/gdm-guest-session line 47): profile /usr/share/gdm/guest-session/Xsession network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/sbin.dhclient3 (/etc/apparmor.d/sbin.dhclient3 line 70): profile /sbin/dhclient3 network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 162): profile /usr/lib/cups/backend/cups-pdf network rules not enforced
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 162): profile /usr/sbin/cupsd network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)


The system loads normally after this but its becoming an eyesore . Is there any way o fix this without having to bear the grief of recompiling my kernel ?

---

### Post by relgames on 2011-09-15
Hi, I have the same problem. Have you managed to solve it?

---

### Post by blade4 on 2011-09-15
Hi relgames , yes I did manage to fix it - by uninstalling apparmor . My system's doing ok since I did this but get a second opinion before you consider doing the same on your system . 

A potentially safer solution would be to install the apparomr compatibility patch that the boot mentions . I couldn't do this cuz its not made for lucid - but if you are running maverick and above , give this a go first .

---

### Post by ubukal on 2011-09-15
triing to understand the message:
 

 It seems to me there are two  main messages
 1 /dev/loop0 is fine
 2 something is wrong with apparmor:  "/.../features  >> no such file
   
  Cache then notes the reason and cure, 6 times, to fill the greater part of the message.
    it is because there is no "interface file" to "../../features"  (= it cannot be accessed  ?)
    Cure: patch kernel (or replace AppArmor 2.4 with higer version...?)
 

 The details all consern network rules (Note:  restrictive rules, if any)
 These are either not applied /gdm/.../Xsession, dhclient3, cups.d or skipped, ../firefox.
 As a  result everything runs smoothly, as blade4 notes -and to be expected with no restrictive rules applied.
 

 In the man page of apparmor in suse 11.1 I found the following. I undestand that it refers to somewhere where messages can be rejected.
 

 ......
 For confined processes running under a profile that has
        been loaded in complain mode, enforcement will not take
        place and the log messages reported to audit will be of the
        form:
 

                audit(1146868287.904:237): PERMITTING r access to
                  /etc/apparmor.d/tunables (du(3811) profile /usr/bin/du active
                  /usr/bin/du)
 

                audit(1146868287.904:238): PERMITTING r access to /etc/apparmor.d
                  (du(3811) profile /usr/bin/du active /usr/bin/du)
 

        If the userland auditd is not running, the kernel will send
        audit events to klogd; klogd will send the messages to
        syslog, which will log the messages with the KERN facility.
        Thus, REJECTING and PERMITTING messages may go to either
        /var/log/audit/audit.log or /var/log/messages, depending
        upon local configuration.
 .........
 

 Also googling Apparmor I read somewhere that apparmor could be disactivated by a bootoption  
 

 Though  this is not exactly what you aked for, I hope it is helpfull.

---

