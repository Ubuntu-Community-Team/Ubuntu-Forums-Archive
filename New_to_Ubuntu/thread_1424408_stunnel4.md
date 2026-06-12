---
title: "stunnel4"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Dimoutlook on 2010-03-07
Not sure if this is right but could someone look at the stunnel4 log and tell if it is working correctly

thanks to all

2010.03.07 22:39:17 LOG7[2274:140090779911920]: PRNG seeded successfully
2010.03.07 22:39:17 LOG7[2274:140090779911920]: SSL context initialized for service nntp
2010.03.07 22:39:17 LOG5[2274:140090779911920]: stunnel 4.27 on x86_64-pc-linux-gnu with OpenSSL 0.9.8g 19 Oct 2007
2010.03.07 22:39:17 LOG5[2274:140090779911920]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2010.03.07 22:39:17 LOG6[2274:140090779911920]: file ulimit = 1024 (can be changed with 'ulimit -n')
2010.03.07 22:39:17 LOG6[2274:140090779911920]: poll() used - no FD_SETSIZE limit for file descriptors
2010.03.07 22:39:17 LOG5[2274:140090779911920]: 500 clients allowed
2010.03.07 22:39:17 LOG7[2274:140090779911920]: FD 10 in non-blocking mode
2010.03.07 22:39:17 LOG7[2274:140090779911920]: FD 11 in non-blocking mode
2010.03.07 22:39:17 LOG7[2274:140090779911920]: FD 12 in non-blocking mode
2010.03.07 22:39:17 LOG7[2274:140090779911920]: SO_REUSEADDR option set on accept socket
2010.03.07 22:39:17 LOG7[2274:140090779911920]: nntp bound to ::1:119
2010.03.07 22:39:17 LOG7[2280:140090779911920]: Created pid file /stunnel4.pid
2010.03.07 22:39:30 LOG7[2280:140090779911920]: nntp accepted FD=13 from ::1:45260
2010.03.07 22:39:30 LOG7[2280:140090780035344]: nntp started
2010.03.07 22:39:30 LOG7[2280:140090780035344]: FD 13 in non-blocking mode
2010.03.07 22:39:30 LOG7[2280:140090780035344]: TCP_NODELAY option set on local socket
2010.03.07 22:39:30 LOG7[2280:140090780035344]: Waiting for a libwrap process
2010.03.07 22:39:30 LOG7[2280:140090780035344]: Acquired libwrap process #0
2010.03.07 22:39:30 LOG7[2280:140090780035344]: Releasing libwrap process #0
2010.03.07 22:39:30 LOG7[2280:140090780035344]: Released libwrap process #0
2010.03.07 22:39:30 LOG7[2280:140090780035344]: nntp permitted by libwrap from ::1:45260
2010.03.07 22:39:30 LOG5[2280:140090780035344]: nntp accepted connection from ::1:45260
2010.03.07 22:39:30 LOG7[2280:140090780035344]: FD 14 in non-blocking mode
2010.03.07 22:39:30 LOG6[2280:140090780035344]: connect_blocking: connecting 216.168.3.30:563
2010.03.07 22:39:30 LOG7[2280:140090780035344]: connect_blocking: s_poll_wait 216.168.3.30:563: waiting 10 seconds
2010.03.07 22:39:31 LOG5[2280:140090780035344]: connect_blocking: connected 216.168.3.30:563
2010.03.07 22:39:31 LOG5[2280:140090780035344]: nntp connected remote server from 10.0.0.4:53362
2010.03.07 22:39:31 LOG7[2280:140090780035344]: Remote FD=14 initialized
2010.03.07 22:39:31 LOG7[2280:140090780035344]: TCP_NODELAY option set on remote socket
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): before/connect initialization
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 write client hello A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 read server hello A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 read server certificate A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 read server done A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 write client key exchange A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 write change cipher spec A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 write finished A
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 flush data
2010.03.07 22:39:31 LOG7[2280:140090780035344]: SSL state (connect): SSLv3 read finished A
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    1 items in the session cache
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    1 client connects (SSL_connect())
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    1 client connects that finished
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 client renegotiations requested
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 server connects (SSL_accept())
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 server connects that finished
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 server renegotiations requested
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 session cache hits
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 session cache misses
2010.03.07 22:39:31 LOG7[2280:140090780035344]:    0 session cache timeouts
2010.03.07 22:39:31 LOG6[2280:140090780035344]: SSL connected: new session negotiated
2010.03.07 22:39:31 LOG6[2280:140090780035344]: Negotiated ciphers: AES256-SHA SSLv3 Kx=RSA Au=RSA Enc=AES(256) Mac=SHA1
2010.03.07 22:40:03 LOG7[2280:140090780035344]: Socket closed on read
2010.03.07 22:40:03 LOG7[2280:140090780035344]: SSL write shutdown
2010.03.07 22:40:03 LOG7[2280:140090780035344]: SSL alert (write): warning: close notify
2010.03.07 22:40:03 LOG6[2280:140090780035344]: SSL socket closed on SSL_shutdown
2010.03.07 22:40:03 LOG7[2280:140090780035344]: Socket write shutdown
2010.03.07 22:40:03 LOG5[2280:140090780035344]: Connection closed: 250 bytes sent to SSL, 1902889 bytes sent to socket
2010.03.07 22:40:03 LOG7[2280:140090780035344]: nntp finished (0 left)

---

### Post by iponeverything on 2010-03-07
Is it passing traffic? If so, that along with:

```
SSL connected: new session negotiated
```

would mean yes.

---

### Post by Dimoutlook on 2010-03-08
Thank you 
it was a bit difficult to set up with karmic/64 just wanted to be sure.

---

### Post by iponeverything on 2010-03-08
I have setup several vpn's and it has never been strait forward. Seems like I have have re-invent the wheel every time because there are so many ways of doing it.

---

