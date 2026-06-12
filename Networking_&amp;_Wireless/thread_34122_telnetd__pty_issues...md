---
title: "telnetd / pty issues..?"
date: 2005-05-13
forum: Networking &amp; Wireless
---

### Post by nautilus on 2005-05-13
i'm running a bbs, currently, which accepts connections via telnet.  i'm moving it from server X to server Y, Debian to Ubuntu, and have the following issue;

the software i'm using is DayDream BBS, latest everything...

my inetd is rlinetd, and i installed the default telnetd from hoary (apt-get install telnetd)

my rlinet.d/telnet file is as follows:

```

service "telnet_tcp" {
        protocol        tcp;
        port            23;
        instances       10;
        user            "bbs";
        group           "bbs";
        server          "/usr/sbin/tcpd";
        exec            "/usr/sbin/in.telnetd -L /bbs/.kickstart -h";
}

```

and produces this error;

```

$ telnet 127.0.0.1
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
telnetd: All network ports in use.
Connection closed by foreign host.

```

now, this as a straight scp of the entire bbs (all contained in a single directory) to the new system.  the only changes are the userid and groupid of the user and group 'bbs'.  once transferred, the bbs root was chown'd to bbs.bbs, and the modes were retained.

i've fiddled with this beast for long enough, and have seen many, many various errors.  in one configuration setup telnet just sat blankly, and in.telnetd ran-up the CPU to an impressive high, and didn't... seem to do anything at all.

right, all my pty's are there (and a load of pts's in /dev/pts/), but i shouldn't have to worry about this in today's day and age, do i?

...help?

--- added ---

please?

---

