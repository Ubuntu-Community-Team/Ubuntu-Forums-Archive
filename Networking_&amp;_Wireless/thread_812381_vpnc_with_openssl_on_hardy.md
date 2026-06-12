---
title: "vpnc with openssl on hardy"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by CactusWren on 2008-05-29
Hello,

I just installed hardy on my gateway desktop system. I need to use vpn to connect with a cisco concentrator at work, and I cannot get cisco's vpn client to compile on hardy.

Idid some research and it looked like vpnc was a good alternative. I got vpnc working on fedora 9 without much difficulty.

When I installed vpnc via:

apt-get install vpnc

The version installed did not have ssl support (due to licensing issues), so I knew I had to compile it myself.

So, I ran:

apt-get source vpnc
apt-get install openssl

Next I cd'ed to the vpnc source directory and ran:

apt-get build-dep


So far so good. 
Next I ran:
dpkg-buildpackage

all was good the package built fine, but still no ssl support.

Next step:
I edited Makefile and uncommented the two OPENSSL lines that are annotated in the comments in the makefile.

I ran:

dpkg-buildpackage

This time Iget errors as follows:

---- build log ----
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package vpnc
dpkg-buildpackage: source version 0.5.1r275-1
dpkg-buildpackage: source changed by Eduard Bloch <blade@debian.org>
dpkg-buildpackage: host architecture i386
 debian/rules clean
dpatch  deapply-all  
reverting patch 04_debianitis from ./ ... ok.
reverting patch 03_vpnc.8 from ./ ... ok.
rm -rf patch-stamp patch-stampT debian/patched
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/root/vpnc-0.5.1r275'
gcc -MM sysdep.c vpnc-debug.c isakmp-pkt.c tunip.c config.c dh.c math_group.c supp.c decrypt-utils.c vpnc.c cisco-decrypt.c -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION > .depend
make[1]: Leaving directory `/root/vpnc-0.5.1r275'
make[1]: Entering directory `/root/vpnc-0.5.1r275'
rm -f sysdep.o vpnc-debug.o isakmp-pkt.o tunip.o config.o dh.o math_group.o supp.o decrypt-utils.o vpnc.o cisco-decrypt.o vpnc cisco-decrypt tags
rm -f vpnc-debug.c vpnc-debug.h vpnc.ps vpnc.8 .depend
make[1]: Leaving directory `/root/vpnc-0.5.1r275'
dh_clean 
 dpkg-source -b vpnc-0.5.1r275
dpkg-source: building vpnc using existing vpnc_0.5.1r275.orig.tar.gz
dpkg-source: building vpnc in vpnc_0.5.1r275-1.diff.gz
dpkg-source: warning: executable mode 0755 of 'debian/patches/04_debianitis.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/03_vpnc.8.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'vpnc-script' will not be represented in diff
dpkg-source: building vpnc in vpnc_0.5.1r275-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
test -d debian/patched || install -d debian/patched
dpatch  apply-all  
applying patch 03_vpnc.8 to ./ ... ok.
applying patch 04_debianitis to ./ ... ok.
dpatch  cat-all  >>patch-stampT
mv -f patch-stampT patch-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/root/vpnc-0.5.1r275'
LANG=C perl -w ./enum2debug.pl isakmp.h >vpnc-debug.c 2>vpnc-debug.h
gcc -MM sysdep.c vpnc-debug.c isakmp-pkt.c tunip.c config.c dh.c math_group.c supp.c decrypt-utils.c vpnc.c cisco-decrypt.c -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION > .depend
make[1]: Leaving directory `/root/vpnc-0.5.1r275'
make[1]: Entering directory `/root/vpnc-0.5.1r275'
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o sysdep.o sysdep.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o vpnc-debug.o vpnc-debug.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o isakmp-pkt.o isakmp-pkt.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o tunip.o tunip.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o config.o config.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o dh.o dh.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o math_group.o math_group.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o supp.o supp.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o decrypt-utils.o decrypt-utils.c
gcc -Wall -g -O2 -W -Wall -Wmissing-declarations -Wwrite-strings     -DVERSION=\"0.5.1\" -DOPENSSL_GPL_VIOLATION  -c -o vpnc.o vpnc.c
vpnc.c:45:26: error: openssl/x509.h: No such file or directory
vpnc.c:46:25: error: openssl/err.h: No such file or directory
vpnc.c: In function â€˜do_phase1â€™:
vpnc.c:1186: error: â€˜X509â€™ undeclared (first use in this function)
vpnc.c:1186: error: (Each undeclared identifier is reported only once
vpnc.c:1186: error: for each function it appears in.)
vpnc.c:1186: error: â€˜current_certâ€™ undeclared (first use in this function)
vpnc.c:1188: warning: implicit declaration of function â€˜STACK_OFâ€™
vpnc.c:1188: error: â€˜cert_stackâ€™ undeclared (first use in this function)
vpnc.c:1188: warning: implicit declaration of function â€˜sk_X509_new_nullâ€™
vpnc.c:1351: warning: implicit declaration of function â€˜d2i_X509â€™
vpnc.c:1352: warning: implicit declaration of function â€˜sk_X509_pushâ€™
vpnc.c:1571: error: â€˜x509â€™ undeclared (first use in this function)
vpnc.c:1572: error: â€˜EVP_PKEYâ€™ undeclared (first use in this function)
vpnc.c:1572: error: â€˜pkeyâ€™ undeclared (first use in this function)
vpnc.c:1573: error: â€˜RSAâ€™ undeclared (first use in this function)
vpnc.c:1573: error: â€˜rsaâ€™ undeclared (first use in this function)
vpnc.c:1574: error: â€˜X509_STOREâ€™ undeclared (first use in this function)
vpnc.c:1574: error: â€˜storeâ€™ undeclared (first use in this function)
vpnc.c:1576: error: â€˜X509_STORE_CTXâ€™ undeclared (first use in this function)
vpnc.c:1576: error: â€˜verify_ctxâ€™ undeclared (first use in this function)
vpnc.c:1581: warning: implicit declaration of function â€˜OpenSSL_add_all_ciphersâ€™
vpnc.c:1582: warning: implicit declaration of function â€˜OpenSSL_add_all_digestsâ€™
vpnc.c:1583: warning: implicit declaration of function â€˜OpenSSL_add_all_algorithmsâ€™
vpnc.c:1585: warning: implicit declaration of function â€˜ERR_load_crypto_stringsâ€™
vpnc.c:1590: warning: implicit declaration of function â€˜ERR_print_errors_fpâ€™
vpnc.c:1593: warning: implicit declaration of function â€˜X509_subject_name_hashâ€™
vpnc.c:1593: warning: format â€˜%08lxâ€™ expects type â€˜long unsigned intâ€™, but argument 2 has type â€˜intâ€™
vpnc.c:1597: warning: implicit declaration of function â€˜X509_STORE_newâ€™
vpnc.c:1601: warning: implicit declaration of function â€˜X509_STORE_load_locationsâ€™
vpnc.c:1604: warning: implicit declaration of function â€˜X509_STORE_set_default_pathsâ€™
vpnc.c:1623: warning: implicit declaration of function â€˜X509_STORE_CTX_newâ€™
vpnc.c:1628: warning: implicit declaration of function â€˜X509_STORE_CTX_initâ€™
vpnc.c:1632: warning: implicit declaration of function â€˜X509_verify_certâ€™
vpnc.c:1642: warning: implicit declaration of function â€˜X509_get_pubkeyâ€™
vpnc.c:1648: warning: implicit declaration of function â€˜EVP_PKEY_get1_RSAâ€™
vpnc.c:1654: warning: implicit declaration of function â€˜RSA_public_decryptâ€™
vpnc.c:1654: error: â€˜RSA_PKCS1_PADDINGâ€™ undeclared (first use in this function)
vpnc.c:1675: warning: implicit declaration of function â€˜EVP_PKEY_freeâ€™
make[1]: *** [vpnc.o] Error 1
make[1]: Leaving directory `/root/vpnc-0.5.1r275'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

---- end of build log ----

I am very new to ubuntu and debian derrivatives and know nothing about how dpkg works or how to troubleshoot this problem.

Any help would be greately appreciated :)

---

### Post by calraith on 2008-05-29
Try installing libssl-dev.  Does that change the outcome of dpkg-buildpackage?

---

### Post by CactusWren on 2008-05-29
Thanks that did it. the dpkg-buildpackage finished successfully and after  running dpkg -i on the package I can now vpnc to the work network!

---

### Post by Cuchaz on 2008-10-13
There's a few other steps after building the package that can make your life easier. Read about them here:

[Howto ignore an update POst #5]("http://ubuntuforums.org/showthread.php?p=5957867#post5957867")

The short version is, ubuntu will want to overwrite/update your custom .deb. The above thread explains ways to get around that.

---

### Post by lindenRathen on 2008-10-29
Thanks guys! You've helped me get this running on my asus eee (using ibex so nice and recent)

I've compiled a full list of what I did (including config set up) here
[http://folkloreofpitong.blogspot.com/2008/10/vpnc-with-certificates-on-asus-eee-900.html](http://folkloreofpitong.blogspot.com/2008/10/vpnc-with-certificates-on-asus-eee-900.html)

thank you for this post! I was getting very frustrated with this, hopefully next release will have some option for native support or similar.

---

### Post by tamman2000 on 2009-03-10
I got it built, I think, but for some reason I can't install it...


user@seacaptin:~/vpnc-0.5.1r275$ sudo dpkg -i vpnc
dpkg-deb: `vpnc' is not a debian format archive
dpkg: error processing vpnc (--install):
subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
vpnc
user@seacaptin:~/vpnc-0.5.1r275$


I am sure this means I screwed something up earlier in the process, but I don't really know my way around dpkg very well... Any ideas?

---

### Post by ourkid on 2009-04-05
I'm getting the same error when trying to install. The rest of the process appears to have gone smoothly.

---

### Post by pbuckley on 2011-09-25
I have natty and I couldn't figure out my error until I read this article, [http://www.nulldevice.de/2010/06/cisco-client-vpn-vpnc-ubuntu-linux-10-04/](http://www.nulldevice.de/2010/06/cisco-client-vpn-vpnc-ubuntu-linux-10-04/). The missing piece was spoofing or faking that my ubuntu machine was a windows client with this line in the /etc/vpnc/myconnection.conf:

Application version Cisco Systems VPN Client 5.0.07.0240:WinNT

---

