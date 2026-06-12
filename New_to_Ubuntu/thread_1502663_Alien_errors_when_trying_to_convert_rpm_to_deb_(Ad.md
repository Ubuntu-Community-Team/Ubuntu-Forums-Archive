---
title: "Alien errors when trying to convert rpm to deb (Adaptec Storage Manager)"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by cf3232 on 2010-06-05
I am trying to convert an Adaptec RPM to DEB.  It is the Storage Manager package for RAID cards.  I would like to be able to monitor my RAID card from within the  OS.  If anyone can help that would be great.  The error I get when trying to convert to DEB is below.

The RPM is: asm_linux_x64_v4.30-16038.rpm


Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/storman
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: error: couldn't find library libstdc++-libc6.2-2.so.3 needed by debian/storman/usr/StorMan/libsoapclient.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/storman.substvars debian/storman/usr/StorMan/libSTORFSA.so debian/storman/usr/StorMan/libSTORUTIL.so debian/storman/usr/StorMan/libsoapclient.so debian/storman/usr/StorMan/libSTORIROC.so debian/storman/usr/StorMan/libSTORB.so debian/storman/usr/StorMan/libstdc++-libc6.2-2.so.3 returned exit code 2
make: [binary-arch] Error 9 (ignored)
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/storman.substvars -Pdebian/storman returned exit code 255
make: *** [binary-arch] Error 9
find: `StorMan-4.30': No such file or directory


Thanks

---

### Post by cf3232 on 2010-06-06
Figured it out.  was using an old RMP package.

---

