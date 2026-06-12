---
title: "scp, sftp and fish hang in IPv4"
date: 2023-08-12
forum: Networking &amp; Wireless
---

### Post by Fabimaru on 2023-08-12
I'm trying to copy a 200Mo file from one local machine to another and either it does not transfer anything or it transfers 64ko and hangs.
The setup:
[LIST]
[*]both machine are running 22.04.3
[*]the one getting the file is connected in wi-fi. (let's call it "desktop")
[*]the one hosting the file is connected in ethernet (let's call it "server")
[/LIST]
I'm not sure when it started being a problem. Both machines have the same sshd config (the default). I cannot see anything special in journalctl.

Various tests I have done:
[LIST]
[*]If I try to change the MTU*on the source and target machine, it does not change anything.
[*]I also tried to download from my Android phone and from a laptop with sftp using Ghost Commander, but I get the same symptoms. But the phone and the laptop can download from the desktop machine.
[*]I used scp and sftp in command line, the integration of sftp in Dolphin/KDE and curl, without success.
[*]I can list the files using sftp.
[*]If I use IPv6, it works.
[*]Same problem in the other way around (from ethernet machine to wi-fi machine).
[*]Very small files work.
[*]I tried to reboot both machines, it did not change anything.
[*]I tried to use "scp -l 1" to limit the bitrate, same thing.
[*]On the target machine, I*used "Subsystem sftp internal-sftp" in "/etc/ssh/sshd_config" but it did not change anything.
[*]If I transfer the file with ssh it works: ```
ssh user@server cat /path-to/my-file > my-file
```
[*]If tested local transfers on the two machines and it works.
[*]I transferred using sftp over a ssh tunnel ( ssh -v fab@server -L 2222:localhost:22 -N) and it worked.
[*]If I do a scp with "-v -v -v", the last thing I see are ```
Sink: C0644 227681801 toto.dat
toto.dat
cp: debug2: fd 7 setting O_NONBLOCK
```
[*]With strace, I get a loop with
[/LIST]
```

*read(7, 0x5571d506e400, 16384) = -1 EAGAIN (Resource temporarily unavailable)*
*poll([{fd=7, events=POLLIN}], 1, -1)    = ? ERESTART_RESTARTBLOCK (Interrupted by signal)*
```

Any idea what it could be or what to look?

---

### Post by TheFu on 2023-08-12
Please run commands, show the exact command + the output and wrap all of that with forum code tags.  Don't reformat. Don't type any of that stuff in again.

In the sshd_config file, check that the 
```
AddressFamily any
```
isn't commented out.

From the manpage:
```
     AddressFamily
             Specifies which address family should be used by sshd(8).  Valid arguments
             are any (the default), inet (use IPv4 only), or inet6 (use IPv6 only).

```
I recall a few years ago, I had to set it to "inet", since I don't have any IPv6 anywhere on my network. I block it from the kernel.

The errors make me think it is related to a cable or switch port that is failing.  Try a different cable and a different switch port.
I haven't seen any issues with scp or rsync (which uses ssh tunnels by default) recently and I've moved multiple TBs of data between systems over wired networks.  OTOH, none of my core systems run 22.04, but all are patched to the correct ssh version for the OS they do run, which has that latest ssh fix from a few weeks ago.  That's 1:8.9p1-3ubuntu0.3 on 22.04 and 1:8.2p1-4ubuntu0.9 on 20.04 systems.

I don't use sftp much internally, but have used scp a number of times this week.  I don't really use any GUI tools with ssh - my local LAN is setup with NFS for most systems to access storage on 2  central servers.

I've used Ghost Commander on android for sftp, but not recently. I tend to use Nextcloud sync more than other tools to get data to Android. Nothing against sftp, just not how I work.

---

### Post by Fabimaru on 2023-08-13
**sshd_config and AddressFamily**
```
AddressFamily any
```
It was commented out, I removed the # sign but it did not change anything. It does not surprise me: when I had the issue with scp/sftp/fish, I specified in the command line a hostname that could be resolved only as an IPv4 address (the host name and IP are specified in /etc/hosts). When I tried with IPv6, I explicitly used the IPv6 address in the scp or sftp command.
in ~/.ssh/config, I changed forced the use of IPv6 that I specified in /etc/hosts and now it always works:
```
Host server
        AddressFamily inet6

```
(well, unless the IPv6 address changes, my knowledge is limited in that area, and it's using default configuration from Ubuntu and my ISP router, but that's another story)

**Cable and port**
I tried to change the port and the cable and it did not change anything.

**Versions installed**
On the server, the version of ssh is:
```
1:8.9p1-3ubuntu0.3
```

---

### Post by Fabimaru on 2023-08-13
More tests:
[LIST]
[*]If I limit the bitrate to 190ko/s and the buffer size to 10ko with ```
sftp -l 190 -B 10000 -v -v -v -v &#8230;
``` then it works (slowly)
[*]I tried to make the sftp client connect to a local TCP proxy that would itself connect to the remote ssh/sftp server, but it did not change anything: ```
simpleproxy -L 2222 -R 192.168.1.2:22
```.
[*]I tried to run the sftp client from a laptop connected by ethernet, same result
[*] I decreased the MTU on both sides to 1280, same result.
[*]I tried to add more logs to see if the issue comes from the client or the server. In "/etc/ssh/sshd_config", I replaced ```
Subsystem       sftp    /usr/lib/openssh/sftp-server
``` by ```
System sftp /usr/sftp
``` , which is a script that add more logs: ```
exec /usr/lib/openssh/sftp-server -l DEBUG3
```. During a transer, in journalctl, I can see ```
debug1: request 7: sent data len 261120
```, but in the client the last thing logged is ```
Request range 0 -> 261119 (0/1)
```. With strace, I can see ```
writev(3, [{iov_base="\0\0\0\31", iov_len=4}, {iov_base="\5\0\0\0\7\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\3\374\0", iov_len=25}], 2) = 29
read(3, "\0\3\374\t", 4)                = 4
mmap(NULL, 262144, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fc634057000
read(3, "g\0\0\0\7\0\3\374\0\23&\221\371\214%\344\4\347,\253@\341\300\264\335\242\25yX\372h\16"..., 261129) = 32764
read(3, 0x7fc63405f00c, 228365)         = ? ERESTARTSYS (To be restarted if SA_RESTART is set)
--- SIGALRM {si_signo=SIGALRM, si_code=SI_KERNEL} ---
alarm(1)                                = 0
rt_sigreturn({mask=[]})                 = -1 EINTR (Appel système interrompu)
getpgrp()                               = 20698
ioctl(1, TIOCGPGRP, [20698])            = 0
```In IPv6, I can see that the read attempt of 261129 bytes gives 32764 bytes, but it is followed by a suit of successful reads.
[/LIST]

---

### Post by TheFu on 2023-08-13
What's in /etc/nsswitch.conf?
Are you using avahi?  Does hostname.local work?
Does using the IPv4 address directly work?

My gut tells me this isn't a name resolution issue, but a bad NIC, bad NIC driver, somewhere in the chain, assuming you've tried different cables and different switch ports already.  I've had realtek NICs go flaky on me.  I've seen cracked motherboards need replacement (or just get a new NIC) to avoid using the onboard NIC that was acting badly.

Simplify and test over and over until you are left with 1 component that has to be the problem and cannot be simplified any smaller.

---

### Post by Fabimaru on 2023-08-13
Thanks. With Wireshark on both sides, I can see:
[LIST]
[*]On the service side a number of "TCP Retransmission", then "TCP Spurious Retransmission" and "TCP Dup ACK".
[*]On the destop side, corrupted HTTP headers, and packets received from IP "1.0.0.2" on the ssh port (which I changed to 2222 to be sure that no interactive ssh shell on port 22*interfere).
[/LIST]
So I agree with your intuition: I guess that either the router has a problem, or the NIC of the server has a problem. I'll try to do transfers between my desktop and a laptop connected by ethernet to the router, or to configure a wi-fi dongle on the server.

---

### Post by TheFu on 2023-08-13
I hope you are running denyhosts or fail2ban with ssh protection enabled if the ssh port is open to the internet.  I tend to leave ssh on port 22 on the LAN, but use my router's port-translation to put ssh on a very high, random, port, for WAN access.

WAN_IP:64300 ---> LAN_IP:22

That will probably drop the bogus attempts 1000%, but a few places will still find the high port and make attempts. That's where fail2ban comes in.  Of course, never allow passwords to be used for WAN connections. Use either ssh-keys or ssh-certs.

---

### Post by Fabimaru on 2023-08-13
ssh is only available on the LAN and through a Wireguard VPN, so no worries.

I just tested with a laptop, it shows the issue on ethernet but not in wifi. So either the router has a problem, or several of my cables have a problem. So in the end it was not a problem with a configuration or a bug of ssh. (but that's sad to have a hardware issue)

---

### Post by Fabimaru on 2023-08-13
There is definitively something wrong with the Zyxel modem-router VMG8924-B10D:
[LIST]
[*]Someone reported the same problem 2 years ago.
[*]It works if I only have wi-fi machines.
[*]When I plug an ethernet machine (the target machine or another one), I start having the problem.
[/LIST]
So not an Ubuntu problem.

---

