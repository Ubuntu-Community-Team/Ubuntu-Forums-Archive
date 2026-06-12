---
title: "Ssh to computer behind a router"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Bobtheknight on 2007-03-03
Hi guys,

I started playing with linux, and of course one of the cool things I have to try is ssh.  So I set up my compy with ssh (can connect via ssh localhost).  Then I forwarded port 22 on my router to my network IP (192.168.0.3).

I ssh'd into my school's computer (not in my network) and tried to ssh back (same terminal) via ssh bob@ISP_IP.  It hangs there.

I then tried to ping my ISP_IP form ssh'd school terminal, then I remembered you can't ping a port (ICMP and tcp are different).  

I never tried to make sure my ssh on ubuntu box is alive from outside of my network.  So guys, what should I do next?  Is there a way to find out if port 22 is actually forwarded?  

Thanks in advance

Bob

---

### Post by kidders on 2007-03-03
Hi there,

You could port scan yourself ... at least, that's what I would do.

It's also worth checking that your SSH server is listening on an externally accessible network interface, rather than just the loopback (127.0.0.1). Again, if you're unsure, you can use **netstat** to take a look at what's happening.

---

### Post by RandomJoe on 2007-03-03
Forwarding the port should be all that's needed.  If this is a residential connection, it's possible the ISP is blocking port 22 although it's not common - they usually just get the ports like http/https, Windows filesharing, etc.  If they are blocking port 22, you could run a second ssh daemon on another port (I use 2222) instead.  To do that, I edited /etc/init.d/ssh and added a second line to run the second daemon.  I also disallow password auth / require RSA-based auth on my 'net-facing port, which is where the extra parameter comes from.  Here is the relevant snippet from my file:
```
case "$1" in
  start)
        log_begin_msg "Starting OpenBSD Secure Shell server..."
        check_for_no_start
        check_privsep_dir
        start-stop-daemon --start --quiet --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS || log_end_msg 1
        start-stop-daemon --start --quiet --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd -- -p 2222 -o PasswordAuthentication=no || log_end_msg 1
        log_end_msg 0
        ;;
  stop)
        log_begin_msg "Stopping OpenBSD Secure Shell server..."
        start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid || log_end_msg 1
        start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd2.pid || log_end_msg 1
        log_end_msg 0
        ;;

  reload|force-reload)
        log_begin_msg "Reloading OpenBSD Secure Shell server's configuration"
        check_for_no_start
        check_config
        start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd || log_end_msg 1
        start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd || log_end_msg 1
        log_end_msg 0
        ;;

  restart)
        log_begin_msg "Restarting OpenBSD Secure Shell server..."
        check_privsep_dir
        check_config
        start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
        start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
        check_for_no_start
        start-stop-daemon --start --quiet --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS || log_end_msg 1
        start-stop-daemon --start --quiet --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- -p 2222 -o PasswordAuthentication=no || log_end_msg 1
        log_end_msg 0
        ;;

  *)
        log_success_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart}"
        exit 1
esac


```
Basically, anywhere the original had a line referencing the sshd program I created a second copy to run another at port 2222.  (Be sure to use a different pidfile as well.)

---

### Post by RandomJoe on 2007-03-03
I have used GRC's ShieldsUP web-test to check open ports - [http://www.grc.com/default.htm](http://www.grc.com/default.htm)  Scroll down to ShieldsUP.  Select that, and pick the type of scan you want.

---

### Post by Bobtheknight on 2007-03-03
Port scan claimed my port 22 is "stealth."  I tried again to connect to my box using putty (and WINscp) from within the network, it does not work (I'm not sure if it ever did work anymore.)

So I'm wondering if I set up SSH right on the ubuntu box.  

I have connected with "localhost", and also from my virtual machine (windows xp) to ubuntu.  But I guess that counts as localhost as well.

Suggestions?

---

### Post by Mr. C. on 2007-03-04
Show that there is an SSH daemon listening on port 22:

netstat -an | grep :22

Show your sshd_config.

Finally, be sure nothing is disabling access in  /etc/hosts.allow and /etc/hosts.deny (tcpwrappers).

---

### Post by RandomJoe on 2007-03-04
Are you doing anything special with iptables?  Running a firewall config utility or something?  I didn't have to do anything to get sshd running properly beyond installing it in Synaptic.  The 'stealthed' port would indicate that iptables or some other firewall (such as the router) is blocking the port.  Otherwise you would get 'closed'.

---

### Post by Bobtheknight on 2007-03-04
I did the netstat and looked at /etc/hosts.deny and /etc/hosts.allow.  Results are below, I think everything checked out.  There's nothing there except comments.

When I ran shields UP port scan all my "common service port" (up to 1024) are stealth, except for one, port 113, IDENT, which is "closed.".  Funny thing is I did not forward this port so it must be my router responding and not ubuntu.

bob@ubuntu-desktop:~$ netstat -an | grep :22
tcp6       0      0 :::22                   :::*                    LISTEN     
bob@ubuntu-desktop:~$ 

Ah turns out pesky firestarter is blocking the port.  Thanks RandomJoe.  This should have been one of the first things I tried, shows what a newbie I am.  Thanks everyone for helping me.  I'll tag this as "resolved."

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and 
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#

---

