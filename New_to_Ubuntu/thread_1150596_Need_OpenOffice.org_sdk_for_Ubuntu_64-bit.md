---
title: "Need OpenOffice.org sdk for Ubuntu 64-bit"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Bibi_Watson on 2009-05-06
Hi everybody!

Can you point me to the location where I can download OO sdk for Ubuntu 64?
Have tried to install sdk from PRM file but failed miserably :-(
(For those curious: the error message looks like
```
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/ooobasis3.0-sdk
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libuno_sal.so.3 needed by debian/ooobasis3.0-sdk/opt/openoffice.org/basis3.0/sdk/bin/cppumaker (its RPATH is '/opt/openoffice.org/basis3.0/sdk/bin/../../ure-link/lib').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: `ooobasis3.0-sdk-3.0.1': No such file or directory
```

)

Or

will greatly appreciate if someone can help me to make *.deb file out of the sdk source. BTW, where to get the source is also a question to me :-(

/*sigh*/

---

### Post by Hospadar on 2009-05-06
isn't the "openoffice.org-dev" package the sdk?  I would think so. 

Also did you try here? [http://download.openoffice.org/3.0.0/sdk.html](http://download.openoffice.org/3.0.0/sdk.html)

As for the full source, you should probably get that from the openoffice website, they probably have source tarballs or a public read-only svn/git/whatever that you can get it from.

---

### Post by Bibi_Watson on 2009-05-06
> **Hospadar said:**
> isn't the "openoffice.org-dev" package the sdk?
  That I do not know. Will try to investigate. Thank you for the input! 

> Also did you try here? [http://download.openoffice.org/3.0.0/sdk.html](http://download.openoffice.org/3.0.0/sdk.html)
 Yes, they have either Windows or Linux/Solaris 32- bit distribution. Which I have tried to use, but the result was miserable (see above).

> As for the full source, you should probably get that from the openoffice website, they probably have source tarballs or a public read-only svn/git/whatever that you can get it from.
Will keep that in mind. Have tried to download smth from openoffice that looked Greek to me.

---

### Post by calc on 2009-05-06
It appears your build is looking in the wrong directory for it...

dpkg-shlibdeps: failure: couldn't find library libuno_sal.so.3 needed by debian/ooobasis3.0-sdk/opt/openoffice.org/basis3.0/sdk/bin/cppumaker (its RPATH is '/opt/openoffice.org/basis3.0/sdk/bin/../../ure-link/lib').

Nothing in Ubuntu is installed into /opt by default.

libuno_sal.so.3 on Ubuntu is in:

uno-libs3: /usr/lib/ure/lib/libuno_sal.so.3

---

### Post by Bibi_Watson on 2009-05-06
> **calc said:**
> It appears your build is looking in the wrong directory for it...

Nothing in Ubuntu is installed into /opt by default.

Very fair comment! I've seen an empty directory, but tried to set the variable LD_LIBRARY_PATH to point to /ure/... No effect.

Being a blue-eyed newbie risk to ask:
Shall I manually copy the library then into /opt/... ? Or is it a known procedure to solve such an issue?

---

