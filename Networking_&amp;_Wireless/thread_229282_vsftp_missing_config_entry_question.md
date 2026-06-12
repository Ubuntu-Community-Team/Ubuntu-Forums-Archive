---
title: "vsftp missing config entry question"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by jmirick on 2006-08-04
I have had vsftp running before on a different machine, no problems. I have created a new machine and entered what I believe is a correct config file, but it won't connect, and when I try to start it via "vsftpd" at the shell it says,

500: vsftpd: missing value in config file:

and that's all, folks. What's missing?? I've looked at it for a few hours with no luck, it looks good to me.  Everything else works fine.  I assume it is looking for some parameter but it escapes me.

Firewall is off, nmap shows ports 20 & 21 not open (since I assume vsftpd isn't started) so I'm stumped.

config file is:


    listen=YES
    tcp_wrappers=yes

    # Allow anonymous FTP? (Beware - allowed by default if you comment this out).

    anonymous_enable=no

    # The following enables users with a local account to log into FTP. In this
    # current configuration, all FTP users must have a local account on this
    # machine -- there is a way to do this without a local account, though.

    local_enable=YES

    # When local users have logged in, jail them in their own home directory:

    chroot_local_user=yes

    write_enable=YES

    # Default umask for local users is 077. You may wish to change this to 022,
    # if your users expect that (022 is used by most other ftpds)

    local_umask=022

    # Activate directory messages - messages given to remote users when they
    # go into a certain directory.

    dirmessage_enable=YES
    ftpd_banner=Welcome to the AMS Ubuntu2 FTP service

    # Make sure PORT transfer connections originate from port 20 (ftp-data):

    connect_from_port_20=YES

    # Activate logging of uploads/downloads.

    xferlog_enable=YES
    xferlog_file=/var/log/vsftpd.log
    xferlog_std_format=YES


    # Debian customization
    #
    # Some of vsftpd's settings don't fit the Debian filesystem layout by
    # default. These settings are more Debian-friendly.
    #
    # This option should be the name of a directory which is empty. Also, the
    # directory should not be writable by the ftp user. This directory is used
    # as a secure chroot() jail at times vsftpd does not require filesystem
    # access.

    #secure_chroot_dir=/var/run/vsftpd
    #
    # This string is the name of the PAM service vsftpd will use.

    pam_service_name=vsftpd
    #
    # This option specifies the location of the RSA certificate to use for SSL
    # encrypted connections.
    rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
    #
    # This option specifies the location of the RSA key to use for SSL
    # encrypted connections.
    rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

Edit/Delete Message

---

### Post by cstudent on 2006-08-04
How exactly did you start the server?

Was it like this?
```

sudo /etc/init.d/vsftpd start

```

---

### Post by jmirick on 2006-08-04
I've been saying    vsftpd     because I believe "listen=yes" means is running standalone and not part of inetd.

So I tried as you suggested, and it said "starting . . .   [ok]

. . . but the ports are still not open (via nmap) and it still rejects a connection.  I'm connecting internally on our network, so there's no outside issues, and samba etc. are all running fine.

---

### Post by cstudent on 2006-08-04
I don't think that setting vsftpd up to listen to port 21 opens the port. That has to be done through the iptables or using a firewall tool like Firestarter. I personally use Firestarter to manage ports, etc. But Frodon has written a very nice how-to on dealing with the iptables manually.

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Either way, I think you need to open the port in the iptables for your server to work.

---

### Post by jmirick on 2006-08-04
I have allowed 20 - 21 through Firestarter, then I also just turned IPTABLES off with Firestarter, seems to make no difference.  (I'm being driven to drink . . .).

Maybe I should turn "listen=yes" off, maybe its confused?

---

### Post by cstudent on 2006-08-04
You will want listen="yes" enabled. You also want port 21 opened in Firestarter at least set to be accessable from your local network. You may have to restart vsftpd after setting the ports to open.
```

sudo /etc/init.d/vsftpd restart

```

When all else fails I reboot. Sometimes that has done the trick for me in situations like this when nothing else seemed to be working.

There is also a good how-to on vsftpd I used when I first set up the software. I no longer use vsftpd. I installed proftpd and gproftpd. gproftpd is a gui frontend to proftpd and allows me to deal with setting up the server graphically. 


The vsftpd how-to can be found here:
[http://ubuntuforums.org/showthread.php?t=91887](http://ubuntuforums.org/showthread.php?t=91887)

---

### Post by phitoo on 2006-08-04
Maybe you're missing

background=YES

Also remember to setup tcpwrappers.

---

### Post by jmirick on 2006-08-04
[sigh . . .]

I have Firestarter in "firewall off" mode.

When I tell vsftp to restart, I get the following:

[INDENT]sudo /etc/init.d/vsftpd restart

 * Stopping FTP server: vsftpd No /usr/sbin/vsftpd found running; none killed.
                                                                         [ ok ]

 * Starting FTP server: vsftpd                                           [ ok ][/INDENT]

Then, if I just repeat the command, I get the same response -- it really doesn't have a copy of vsftpd running, even though it said [OK].

I looked in /usr/sbin for vsftpd, its there.  I tried reloading vsftpd this morning via package manager, it did it OK; maybe I should have "completely removed" it and then reloaded.

On a different machine, the same config file runs and all is well.

---

### Post by jmirick on 2006-08-04
I have included background=yes.

I haven't done anything with tcpwrappers, don't know anything about it, I haven't had to touch anything on this in my other installations.

---

### Post by cstudent on 2006-08-04
I never had to install tcpwrappers when I was using vsftp.

Have you tried?:
```

sudo dpkg-reconfigure vsftpd

```

---

### Post by phitoo on 2006-08-04
> sudo /etc/init.d/vsftpd restart
> 
> * Stopping FTP server: vsftpd No /usr/sbin/vsftpd found running; none killed.
> [ ok ]
> 
> * Starting FTP server: vsftpd [ ok ]

There is a problem with the /etc/init.d/vsftpd file somehow. The pid of vsftpd as listed by ps is different from the contents of the /var/run/vsftpd/vsftp.pid file. That's why you get the above message. (Incidentally, I filed a bug on that.)

You'll have to manually kill it first, then restart it.

Hope that helps.

---

### Post by jmirick on 2006-08-04
Well, finally I went out and just completely scrubbed the vsftp application -- "completely removed" it -- and reinstalled it.  Then I followed the approach from here:  [http://www.netadmintools.com/art355.html](http://www.netadmintools.com/art355.html) and "restarted" after each change, and lo and behold it works after each.  So then I added one or two things unique to us (our banner, etc.) and so I'm fixed.

I'm still not really sure what was wrong although there was a file in /var/run/vsftpd called (oddly enough) vsftpd.pid that the de-installer couldn't remove, so I clobbered it, and I don't know if that helped but, well, I'm running.

Thanks to everybody for suggestions, hope I'm smart enough to be on your side of the transaction for somebody else, some day.

jim

---

### Post by jmirick on 2006-08-04
I was writing my summary while Phitoo was writing his, I guess that's what I ultimately found . . .  thanks for bug-reporting for me!

"Live and learn."

---

### Post by Shawn Nelson on 2006-09-29
I found an easier solution that worked for me, as was said before the problem resides with the pid.  If you doa  complete removal it will fail when it tries to wipe the /var/run/vsftpd/ folder which is where the vsftpd.pid file is.  So just go in and blow away the folder yourself and then reinstall vsftpd and it should work fine.

---

