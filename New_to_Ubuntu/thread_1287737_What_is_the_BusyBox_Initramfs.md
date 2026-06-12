---
title: "What is the BusyBox Initramfs?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by GaretJax on 2009-10-10
I have seen lots of threads trying to resolve a initramfs prompt, but I have yet to learn what it is.  What is the BusyBox?  How is it a part of Ubuntu and what makes it necessary to have it?  Why does Ubuntu drop a user to the BusyBox prompt? What logical process should a person follow when they are at the prompt?

I just upgraded my Dell Mini 9 to 9.04 UNR and after I insatlled 200+ updates and rebooted, I ended up at the infamous prompt.  Not knowing what to do, I reinstalled.  Now I am a bit concerned about installing any updates.

---

### Post by SkyNet2029 on 2009-10-10
a full description of what and why busybox is capable (and not pable of) can be found at the busybox site...
[http://www.busybox.net/about.html](http://www.busybox.net/about.html)
 
Here is what is included, to help you rescue a broken system:
 
        [, [[, acpid, addgroup, adduser, adjtimex, ar, arp, arping, ash,
        awk, basename, beep, blkid, brctl, bunzip2, bzcat, bzip2, cal, cat,
        catv, chat, chattr, chgrp, chmod, chown, chpasswd, chpst, chroot,
        chrt, chvt, cksum, clear, cmp, comm, cp, cpio, crond, crontab,
        cryptpw, cut, date, dc, dd, deallocvt, delgroup, deluser, depmod,
        devmem, df, dhcprelay, diff, dirname, dmesg, dnsd, dnsdomainname,
        dos2unix, dpkg, du, dumpkmap, dumpleases, echo, ed, egrep, eject,
        env, envdir, envuidgid, expand, expr, fakeidentd, false, fbset,
        fbsplash, fdflush, fdformat, fdisk, fgrep, find, findfs, flash_lock,
        flash_unlock, fold, free, freeramdisk, fsck, fsck.minix, fsync,
        ftpd, ftpget, ftpput, fuser, getopt, getty, grep, gunzip, gzip, hd,
        hdparm, head, hexdump, hostid, hostname, httpd, hush, hwclock, id,
        ifconfig, ifdown, ifenslave, ifplugd, ifup, inetd, init, inotifyd,
        insmod, install, ionice, ip, ipaddr, ipcalc, ipcrm, ipcs, iplink,
        iproute, iprule, iptunnel, kbd_mode, kill, killall, killall5, klogd,
        last, length, less, linux32, linux64, linuxrc, ln, loadfont,
        loadkmap, logger, login, logname, logread, losetup, lpd, lpq, lpr,
        ls, lsattr, lsmod, lzmacat, lzop, lzopcat, makemime, man, md5sum,
        mdev, mesg, microcom, mkdir, mkdosfs, mkfifo, mkfs.minix, mkfs.vfat,
        mknod, mkpasswd, mkswap, mktemp, modprobe, more, mount, mountpoint,
        mt, mv, nameif, nc, netstat, nice, nmeter, nohup, nslookup, od,
        openvt, passwd, patch, pgrep, pidof, ping, ping6, pipe_progress,
        pivot_root, pkill, popmaildir, printenv, printf, ps, pscan, pwd,
        raidautorun, rdate, rdev, readlink, readprofile, realpath,
        reformime, renice, reset, resize, rm, rmdir, rmmod, route, rpm,
        rpm2cpio, rtcwake, run-parts, runlevel, runsv, runsvdir, rx, script,
        scriptreplay, sed, sendmail, seq, setarch, setconsole, setfont,
        setkeycodes, setlogcons, setsid, setuidgid, sh, sha1sum, sha256sum,
        sha512sum, showkey, slattach, sleep, softlimit, sort, split,
        start-stop-daemon, stat, strings, stty, su, sulogin, sum, sv,
        svlogd, swapoff, swapon, switch_root, sync, sysctl, syslogd, tac,
        tail, tar, taskset, tcpsvd, tee, telnet, telnetd, test, tftp, tftpd,
        time, timeout, top, touch, tr, traceroute, true, tty, ttysize,
        udhcpc, udhcpd, udpsvd, umount, uname, uncompress, unexpand, uniq,
        unix2dos, unlzma, unlzop, unzip, uptime, usleep, uudecode, uuencode,
        vconfig, vi, vlock, volname, watch, watchdog, wc, wget, which, who,
        whoami, xargs, yes, zcat, zcip

---

### Post by damis648 on 2009-10-10
Busybox is a very basic and simple unix shell that ubuntu boots into if something fails when trying to boot the main system. If this ever happens, you need to see the error message that led to dropping to busybox. To do this, at the grub prompt, press 'e' on the ubuntu option and then press 'e' again on the kernel line. At the end of the line, remove the last two words 'quiet' and 'splash'. Press enter and then press 'b' and now ubuntu is booting verbose. Right before you get to the busybox, you should see an error, you can post that and go from there.

---

### Post by ibuclaw on 2009-10-10
busybox is built into the system init ramdisk image that grub uses to boot the system.

If for whatever reason Linux is unable to mount the root fs (/) then it falls back to busybox to allow low system fixing.

Reasons why this happens include bad blocks/sectors on the filesystem preventing data to be read, an encrypted filesystem that failed to decrypt, or the some key system files are missing that otherwise leave the system in an unbootable state.

Regards
Iain

---

