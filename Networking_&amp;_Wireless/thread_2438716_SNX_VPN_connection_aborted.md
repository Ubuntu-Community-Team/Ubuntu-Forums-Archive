---
title: "SNX VPN connection aborted"
date: 2020-03-17
forum: Networking &amp; Wireless
---

### Post by tritof on 2020-03-17
Hi there,

My company uses VPN checkpoints and I need to configure my ubuntu computer to access them. So I installed SNX (version 800007075 for CLI access). But when I execute the SNX command I get the following result:

```
~$ snx
Check Point's Linux SNX
build 800007075
Please enter your password:


SNX: Connection aborted.

```

I generated the following debug file (option -g):

```
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] snx: starting debug - Tue Mar 17 09:02:58 2020


[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] browser::browser(): called
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] snx_CCC_browser::snx_CCC_browser: called
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] snx_browser::auth: entering
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] gwinfo:gwinfo: entered!0x8a09520
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] creating the ssl layer
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::talkssl(): entered with chunk=512, opaque=89eb100, link_established=80d66a0, link_failure=80d6680, packet_receive=80d6650, verify_gw=80
d66c0
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::set_sslalg:  setting ssl alg to 2
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl:: init_ssl_neg: using 3DES
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSLctx_New: prefs = 1a
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] isExist: ProxyEntity didn't initiated yet
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::start_async: Creating a new connection
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::start_async: Connecting to gw: 0x041ed9d4, port: 443
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] fwasync_make_connection: d4d91e04/443: dowait is -1 sock is 5
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::start_async: Connection created successfully
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] fwasync_conn_params: <c0a80168,55403> -> <d4d91e04,443>
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::client_handler: state: CONN_INIT - entering
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::client_handler: start ssl negotaition
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::client_handler: start openSSL negotaition
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSL_PrepareConnection: verify mode: 0
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] My SSL Ciphers:
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] Cipher List:
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] 0: DES-CBC3-SHA            SSLv3 Kx=RSA      Au=RSA  Enc=3DES(168) Mac=SHA1


[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] 1: RC4-SHA                 SSLv3 Kx=RSA      Au=RSA  Enc=RC4(128)  Mac=SHA1


[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] 2: RC4-MD5                 SSLv3 Kx=RSA      Au=RSA  Enc=RC4(128)  Mac=MD5 


[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] 3: DES-CBC-SHA             SSLv3 Kx=RSA      Au=RSA  Enc=DES(56)   Mac=SHA1


[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::client_handler: Returning OK!!!
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSL_NegotiateStep: current state = before/connect initialization
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] is_initialized: new process or forked
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] rand_add_seedfile: Failed to read seed from registry.: Operation not permitted
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] fwrand_write_seed: Failed to read seed from registry.: Operation not permitted
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] CkpRegDir: Environment variable CPDIR is not set.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] GenerateGlobalEntry: Unable to get registry path
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] fwrand_write_seed: Failed to write seed.: Operation not permitted
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSL_NegotiateStep: should retry.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSL_NegotiateStep: current state = SSLv3 read server hello A
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] SSL e stack
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] 3564:error:1409442E:SSL routines:SSL3_READ_BYTES:tlsv1 alert protocol version:s3_pkt.c:1033


[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSL_NegotiateStep: Current step failed. Error is: 336151598
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] ckpSSL_fwasync_connected: no connections err -3
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] fwasync_end_conn: scheduling the end of connection 5
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] fwasync_do_end_conn: closing connection 5 (conn=8a12dc0)
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::end_handler: ending connection 
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] snx_browser::Failure: entering with code: 1
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] got link down!- exit
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] snx: quit.
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] snx_CCC_browser::~snx_CCC_browser: called
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] browser::~browser: called
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::~talkssl: delete link
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] talkssl::~talkssl: end
[ 3564 -141507584]@tritof-zenbook.PC-GE.fr[17 Mar  9:02:58] done

```

I thought it was a dependency error, but here is the result of the lld command:

```

~$ sudo ldd /usr/bin/snx
    linux-gate.so.1 (0xf7ee3000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7d79000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7d5a000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf7d42000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7d3d000)
    libpam.so.0 => /lib/i386-linux-gnu/libpam.so.0 (0xf7d2d000)
    libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf7d12000)
    libstdc++.so.5 => /usr/lib/i386-linux-gnu/libstdc++.so.5 (0xf7c53000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7a77000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf7a4b000)
    /lib/ld-linux.so.2 (0xf7ee4000)
    libaudit.so.1 => /lib/i386-linux-gnu/libaudit.so.1 (0xf7a21000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf791d000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf78ff000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf78fb000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf78f4000)
    libcap-ng.so.0 => /lib/i386-linux-gnu/libcap-ng.so.0 (0xf78ee000)
    libbsd.so.0 => /lib/i386-linux-gnu/libbsd.so.0 (0xf78d3000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf78c9000)

```



Could someone please explain to me why the connection was aborted or at least give me a clue?

---

### Post by josuesap on 2020-08-31
Hi, i have the same error on snx, did you could solve this problem?


Josue Neto

---

