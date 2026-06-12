---
title: "Trouble using ssvnc from Windows to xllvnc server on Ubuntu"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by y-tech on 2015-10-27
I have x11vnc 0.9.13 running on Ubuntu 14.04.03 at the office. I have set up TightVNC 2.7.10 for Windows to connect from my home laptop. The office router redirects port 4321 to port 5900 on the office workstation. This all works beautifully, surprisingly so.

The only problem is that the TightVNC viewer has no secure connection. I came across the program ssvnc which is suppose to provide a ssl/ssh security layer for TighVNC: [http://www.karlrunge.com/x11vnc/ssvnc.html](http://www.karlrunge.com/x11vnc/ssvnc.html). when I run ssvnc on the Windows computer, specifying myhost.com:4321, Use SSL, Verify All Certs. I get the message "Failed to connect to server (127.0.0.1::1912)". The x11vnc server output is below.

Interestingly, the server output shown below ends before I even get the "Unrecognized SSL Cert" message and before I have a chance to click "Continue as though I saved it" button. After clicking the button, there is no further output on the server side, but I get the "Failed to connect ..." message on the Windows side. I get the same error results even if I fetch and save the server cert.

Any idea what my problem is?

x11vnc server output:
The SSL VNC desktop is:  uCommon:0
PORT=5900
SSLPORT=5900

27/10/2015 22:19:41 SSL: accept_openssl(OPENSSL_VNC)
27/10/2015 22:19:41 SSL: spawning helper process to handle: 76.181.65.196:57112
27/10/2015 22:19:41 SSL: helper for peerport 57112 is pid 23768:
27/10/2015 22:19:41 connect_tcp: trying:   127.0.0.1 20000
27/10/2015 22:19:41 check_vnc_tls_mode: waited: 0.000022 / 1.40 input: SSL Handshake
27/10/2015 22:19:41 SSL: ssl_init[23768]: 11/11 initialization timeout: 20 secs.
27/10/2015 22:19:41 SSL: ssl_helper[23768]: SSL_accept() succeeded for: 76.181.65.196:57112
27/10/2015 22:19:41 SSL: ssl_helper[23768]: Cipher: TLSv1/SSLv3 AES256-SHA Proto: TLSv1
27/10/2015 22:19:41 SSL: ssl_helper[23768]: accepted client 76.181.65.196 x509 peer cert is null
27/10/2015 22:19:41 SSL: handshake with helper process[23768] succeeded.
27/10/2015 22:19:41   other clients:
27/10/2015 22:19:41 Normal socket connection
27/10/2015 22:19:41 incr accepted_client=1 for 127.0.0.1:41243  sock=11
27/10/2015 22:19:41 accept_openssl: renaming client '127.0.0.1' -> '76.181.65.196'
27/10/2015 22:19:41 client progressed=0 in 15/10 0.010387 s
27/10/2015 22:19:41 created   xdamage object: 0x1000036
27/10/2015 22:19:41 SSL: ssl_xfer[23768]: closing sockets 0, 11, 11
27/10/2015 22:19:41 SSL: ssl_helper[23768]: exit case 7 (ssl_xfer done)
27/10/2015 22:19:41 rfbProcessClientProtocolVersion: client gone
27/10/2015 22:19:41 client_count: 0
27/10/2015 22:19:41 sending SIGTERM to ssl_helper_pid: 23768
27/10/2015 22:19:42 Client 76.181.65.196 gone
27/10/2015 22:19:42 Statistics             events    Transmit/ RawEquiv ( saved)
27/10/2015 22:19:42  TOTALS              :      0 |         0/        0 (  0.0%)
27/10/2015 22:19:42 Statistics             events    Received/ RawEquiv ( saved)
27/10/2015 22:19:42  TOTALS              :      0 |         0/        0 (  0.0%)
27/10/2015 22:19:42 destroyed xdamage object: 0x1000036

---

### Post by y-tech on 2015-10-28
OK, I figured out my problem. On the ssvnc 'options' dialog I had 'Port Slot' set to my port number -- thinking that was where I needed to configure it. When I removed that, it connected just fine. 

The version of TightVNC viewer that ships with ssvnc 1.0.[29|30] is  1.3.9 which is older and painfully slower than the version 2.7.10 I  downloaded earlier. My solution was to copy the 2.7.10 executable into  the ..\ssvnc\Windows\util folder and rename it to the same as the 1.3.9  version. Odd that such an old version of TIghtVNC viewer is shipped with  ssvnc (the 2.7.10 itself is from 2013)

---

