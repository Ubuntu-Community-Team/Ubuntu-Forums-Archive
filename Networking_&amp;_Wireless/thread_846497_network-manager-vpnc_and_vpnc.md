---
title: "network-manager-vpnc and vpnc"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by cebesius on 2008-07-01
I've been having some difficulty getting vpnc to connect to our Cisco ASA 5510.  I've been going back and forth with some very helpful and knowledgeable folks on the vpnc-devel mailing list.  We narrowed it down to a handshake problem, where the ASA was wanting to use 1DES encryption, and vpnc was not.  If I enabled it to use 1DES, it worked, but since 1DES is insecure, I pressed on.  I finally got vpnc to connect with 3DES by commenting out the other cipher declarations in the vpnc source code, and recompiling. This little hack gets me going until the larger problem with vpnc's handshake code can be fixed.  Below is my diff, in case anyone else is having a similar issue:

```
Index: supp.c
===================================================================
--- supp.c	(revision 332)
+++ supp.c	(working copy)
@@ -43,13 +43,13 @@
 };
 
 const supported_algo_t supp_crypt[] = {
-	{"null", GCRY_CIPHER_NONE, IKE_ENC_NO_CBC, ISAKMP_IPSEC_ESP_NULL, 0},
-	{"des", GCRY_CIPHER_DES, IKE_ENC_DES_CBC, ISAKMP_IPSEC_ESP_DES, 0},
+//	{"null", GCRY_CIPHER_NONE, IKE_ENC_NO_CBC, ISAKMP_IPSEC_ESP_NULL, 0},
+//	{"des", GCRY_CIPHER_DES, IKE_ENC_DES_CBC, ISAKMP_IPSEC_ESP_DES, 0},
 	{"3des", GCRY_CIPHER_3DES, IKE_ENC_3DES_CBC, ISAKMP_IPSEC_ESP_3DES, 0},
-	{"aes128", GCRY_CIPHER_AES128, IKE_ENC_AES_CBC, ISAKMP_IPSEC_ESP_AES, 128},
-	{"aes192", GCRY_CIPHER_AES192, IKE_ENC_AES_CBC, ISAKMP_IPSEC_ESP_AES, 192},
-	{"aes256", GCRY_CIPHER_AES256, IKE_ENC_AES_CBC, ISAKMP_IPSEC_ESP_AES, 256},
-	{NULL, 0, 0, 0, 0}
+//	{"aes128", GCRY_CIPHER_AES128, IKE_ENC_AES_CBC, ISAKMP_IPSEC_ESP_AES, 128},
+//	{"aes192", GCRY_CIPHER_AES192, IKE_ENC_AES_CBC, ISAKMP_IPSEC_ESP_AES, 192},
+//	{"aes256", GCRY_CIPHER_AES256, IKE_ENC_AES_CBC, ISAKMP_IPSEC_ESP_AES, 256},
+//	{NULL, 0, 0, 0, 0}
 };
 
 const supported_algo_t supp_auth[] = {

```

Now the problem I have is getting network-manager-vpnc to connect.  It still fails to connect unless I force it to connect with 1DES.  You can see in the diff above that I commented out support for 1DES.  1DES shouldn't even work at all.

```
cebesius@cexbox:~/tmp/vpnc-svn/vpnc/trunk$ vpnc --version
vpnc version 0.5.1-332
Copyright (C) 2002-2006 Geoffrey Keating, Maurice Massar, others
vpnc comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of vpnc under the terms of the GNU General
Public License.  For more information about these matters, see the files
named COPYING.
Built without openssl (certificate) support.

Supported DH-Groups: nopfs dh1 dh2 dh5
Supported Hash-Methods: md5 sha1
Supported Encryptions: 3des
Supported Auth-Methods: psk psk+xauth
cebesius@cexbox:~/tmp/vpnc-svn/vpnc/trunk$ which vpnc
/usr/local/sbin/vpnc
```

Notice the supported encryptions does not include 1DES?  This tells me that network-manager-vpnc is not using the same binary as the vpnc I have been using in the terminal.  I can't figure out where network-manager-vpnc is looking for its vpnc binary.  Does anyone know?

---

### Post by cebesius on 2008-11-23
I solved this a while back.  It looks like network-manager-vpnc tries to run /usr/sbin/vpnc, regardless of any other vpnc that may be in PATH.  The vpnc source code from the official vpnc subversion repo (not ubuntu's vpnc source code) causes vpnc to copy into /usr/local/sbin/vpnc when you do "make install".  I made /usr/sbin/vpnc a symlink to /usr/local/sbin/vpnc and now all is well.

---

