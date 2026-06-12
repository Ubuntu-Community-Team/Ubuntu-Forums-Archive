---
title: "trickle ignoring trickled in Ubuntu 6.06 LTS?"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by aoakley on 2007-08-20
I'm trying to use trickle and trickled to manage bandwidth of some overnight archiving.

[http://monkey.org/~marius/trickle/](http://monkey.org/~marius/trickle/)
[http://packages.ubuntu.com/dapper/net/trickle](http://packages.ubuntu.com/dapper/net/trickle)

Under Ubunutu 6.06, **the trickle client seems to ignore the trickled server daemon and always uses the default 10kBps**. Here's proof:

```

# First, kill existing instance of trickled and double-check

aoakley@thoth:~/temp$ ls /tmp/.tr*
0 /tmp/.trickled.sock
aoakley@thoth:~/temp$ ps -e | grep trickled
11190 ?        00:00:50 trickled
aoakley@thoth:~/temp$ sudo kill 11190
Password:
aoakley@thoth:~/temp$ ps -e | grep trickled
aoakley@thoth:~/temp$ ls /tmp/.tr*
ls: /tmp/.tr*: No such file or directory

# Now start the trickled daemon with a download limit of 128kBps, up 32kBps

aoakley@thoth:~/temp$ sudo trickled -d 128 -u 32
aoakley@thoth:~/temp$ ps -e | grep trickled
11862 ?        00:00:00 trickled
aoakley@thoth:~/temp$ ls /tmp/.tr*
0 /tmp/.trickled.sock

# Next, download a 1.6MB file using trickled

aoakley@thoth:~/temp$ trickle wget ftp://ftp.demon.net/pub/test/fullfile16
--15:02:59--  ftp://ftp.demon.net/pub/test/fullfile16
           => `fullfile16'
Resolving ftp.demon.net... 194.159.255.135
Connecting to ftp.demon.net|194.159.255.135|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/test ... done.
==> PASV ... done.    ==> RETR fullfile16 ... done.
Length: 1,638,400 (1.6M) (unauthoritative)
100%[====================================>] 1,638,400      9.30K/s    ETA 00:00
15:05:51 (9.45 KB/s) - `fullfile16' saved [1638400]

# As you can see, this downloaded at only 10kBps, not 128kBps
# Next, run without trickle to prove we can take higher bandwidth

aoakley@thoth:~/temp$ wget ftp://ftp.demon.net/pub/test/fullfile16
--15:08:13--  ftp://ftp.demon.net/pub/test/fullfile16
           => `fullfile16.1'
Resolving ftp.demon.net... 194.159.255.135
Connecting to ftp.demon.net|194.159.255.135|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/test ... done.
==> PASV ... done.    ==> RETR fullfile16 ... done.
Length: 1,638,400 (1.6M) (unauthoritative)
100%[====================================>] 1,638,400    289.45K/s    ETA 00:00
15:08:20 (282.36 KB/s) - `fullfile16.1' saved [1638400]

# We got 290kBps without trickle
# Even if we specify the socket with -n it still defaults to 10kBps not 128kBps

aoakley@thoth:~/temp$ trickle -n /tmp/.trickled.sock wget ftp://ftp.demon.net/pub/test/fullfile16
--15:09:56--  ftp://ftp.demon.net/pub/test/fullfile16
           => `fullfile16.4'
Resolving ftp.demon.net... 194.159.255.135
Connecting to ftp.demon.net|194.159.255.135|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/test ... done.
==> PASV ... done.    ==> RETR fullfile16 ... done.
Length: 1,638,400 (1.6M) (unauthoritative)

100%[====================================>] 1,638,400     12.44K/s    ETA 00:00

15:12:35 (10.10 KB/s) - `fullfile16.4' saved [1638400]

# Check again that trickled is still running with same process number

aoakley@thoth:~/temp$ ps -e | grep trickled
11862 ?        00:00:00 trickled
aoakley@thoth:~/temp$ ls /tmp/.tr*
0 /tmp/.trickled.sock

# Now run trickle in standalone mode

aoakley@thoth:~/temp$ trickle -s -d 128 -u 32 wget ftp://ftp.demon.net/pub/test/fullfile16
--15:15:09--  ftp://ftp.demon.net/pub/test/fullfile16
           => `fullfile16.5'
Resolving ftp.demon.net... 194.159.255.135
Connecting to ftp.demon.net|194.159.255.135|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/test ... done.
==> PASV ... done.    ==> RETR fullfile16 ... done.
Length: 1,638,400 (1.6M) (unauthoritative)

100%[====================================>] 1,638,400    120.83K/s    ETA 00:00

15:15:23 (127.94 KB/s) - `fullfile16.5' saved [1638400]

# Works perfectly in standalone mode but ignores daemon in client mode!

```

Any clues, anyone?

---

### Post by aoakley on 2007-09-10
Anyone? Bueller?

---

