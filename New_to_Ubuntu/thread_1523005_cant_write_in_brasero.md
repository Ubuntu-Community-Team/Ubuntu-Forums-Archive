---
title: "cant write in brasero"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by mallan on 2010-07-02
ive installed 10.04.. when i try to burn a video dvd in brasero it says

All required applications and libraries are not installed.
Please install the following manually and try again:
mplex (GStreamer plugin).

any one give me a soluton

---

### Post by stderr on 2010-07-02
Try running this command in a terminal:

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

The package went througha period of not having the mplex plugin contained within it, but from the changelog I reckon it's back now:

```
Version: 0.10.11-0ubuntu1.1 	2009-11-23 14:01:32 UTC

gst-plugins-bad-multiverse0.10 (0.10.11-0ubuntu1.1) jaunty-proposed; urgency=low

  * debian/rules
    - Enable mplex plugin that was previously disabled.
  * debian/gstreamer-plugins-bad-multiverse.install
    - Include mplex plugin.
  (LP: #[270976]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976"))

 -- Onkar Shinde   Sat, 21 Nov 2009 21:10:11 +0530
```

 - from [http://www.ubuntuupdates.org/packages/show/154966]("http://www.ubuntuupdates.org/packages/show/154966")

And I just checked the files within my installation of gstreamer0.10-plugins-bad-multiverse on Karmic (9.10) - mplex is there:

```
sudo dpkg -L gstreamer0.10-plugins-bad-multiverse
[sudo] password for ace: 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/NEWS.gz
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/AUTHORS
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/README.Debian
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/copyright
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/README.gz
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/changelog.Debian.gz
/usr/lib
/usr/lib/gstreamer-0.10
/usr/lib/gstreamer-0.10/libgstxvid.so
/usr/lib/gstreamer-0.10/libgstfaac.so
/usr/lib/gstreamer-0.10/libgstmpeg2enc.so
[COLOR="Green"]**/usr/lib/gstreamer-0.10/libgstmplex.so**[/COLOR]
```


If you still have problems, the Launchpad (LP) [bug report]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976") linked to above contains further details and packages to try to install. Should after attempting to install gstreamer0.10-plugins-bad-multiverse & the other packages mentioned (dvdauthor, gstreamer0.10-plugins-bad, ...) you still encounter the same issue, you may want to leave a comment on the bug report.

---

### Post by hansdown on 2010-07-02
Hi mallan.

You may need to install some xtras.

[http://www.medibuntu.com/](http://www.medibuntu.com/)

```
sudo apt-get libdvdcss2
```

```
sudo apt-get ubuntu restricted extras

```

+ stderr's post.

---

### Post by Keith Fox on 2010-07-12
> **hansdown said:**
> Hi mallan.

You may need to install some xtras.

[http://www.medibuntu.com/](http://www.medibuntu.com/)

```
sudo apt-get libdvdcss2
```

```
sudo apt-get ubuntu restricted extras

```

+ stderr's post.

I think you mean...
```
sudo apt-get install libdvdcss2
```

---

### Post by hansdown on 2010-07-12
> **Keith Fox said:**
> I think you mean...
```
sudo apt-get install libdvdcss2
```

Yes, thankyou Keith Fox.

---

### Post by Tonyr63 on 2010-07-13
Hi

I have the same problem and tried your solution but got the following response

"Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate"

How do I fix?

Kind Regards

:)

---

### Post by hansdown on 2010-07-13
Hi Tonyr63.

You need to add the medibuntu repository.

Copy and paste this in a terminal.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update



```

You should get the package now.

---

### Post by Twitch6000 on 2010-07-13
To install libdvdcss2 without adding the repo just do this -

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

---

### Post by green69 on 2010-07-19
> **hansdown said:**
> Hi Tonyr63.

You need to add the medibuntu repository.

Copy and paste this in a terminal.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update



```

You should get the package now.

This solution works perfectly for me. Thanx!

---

### Post by hansdown on 2010-07-19
Nice!

Glad you fixed it, green69.

---

### Post by chad_anderson on 2011-04-01
Can anyone help me? i followed all the previous steps. but i still get two errors...

      All required applications and libraries are not installed.

           Please install the following manually and try again:
            mplex (GStreamer plugin)
            dvdauthor (application).

---

### Post by hansdown on 2011-04-02
Hi chad_anderson.

```
sudo apt-get install dvdauthor
```

in a terminal.

Or click system> administration> synaptic package manager.

Search for dvdauthor, and install.

I'm not fammiliar with the mplex plugin.

---

### Post by BiG_Weasel on 2011-06-19
Googled and found this, too.  Thanks for the help!

---

### Post by wonk4rol on 2012-05-21
It's works for me. Thanx
> **stderr said:**
> Try running this command in a terminal:

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```The package went througha period of not having the mplex plugin contained within it, but from the changelog I reckon it's back now:

```
Version: 0.10.11-0ubuntu1.1     2009-11-23 14:01:32 UTC

gst-plugins-bad-multiverse0.10 (0.10.11-0ubuntu1.1) jaunty-proposed; urgency=low

  * debian/rules
    - Enable mplex plugin that was previously disabled.
  * debian/gstreamer-plugins-bad-multiverse.install
    - Include mplex plugin.
  (LP: #[270976]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976"))

 -- Onkar Shinde   Sat, 21 Nov 2009 21:10:11 +0530
``` - from [http://www.ubuntuupdates.org/packages/show/154966](http://www.ubuntuupdates.org/packages/show/154966)

And I just checked the files within my installation of gstreamer0.10-plugins-bad-multiverse on Karmic (9.10) - mplex is there:

```
sudo dpkg -L gstreamer0.10-plugins-bad-multiverse
[sudo] password for ace: 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/NEWS.gz
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/AUTHORS
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/README.Debian
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/copyright
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/README.gz
/usr/share/doc/gstreamer0.10-plugins-bad-multiverse/changelog.Debian.gz
/usr/lib
/usr/lib/gstreamer-0.10
/usr/lib/gstreamer-0.10/libgstxvid.so
/usr/lib/gstreamer-0.10/libgstfaac.so
/usr/lib/gstreamer-0.10/libgstmpeg2enc.so
[COLOR=Green]**/usr/lib/gstreamer-0.10/libgstmplex.so**[/COLOR]
```
If you still have problems, the Launchpad (LP) [bug report]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976") linked to above contains further details and packages to try to install. Should after attempting to install gstreamer0.10-plugins-bad-multiverse & the other packages mentioned (dvdauthor, gstreamer0.10-plugins-bad, ...) you still encounter the same issue, you may want to leave a comment on the bug report.

---

### Post by oldos2er on 2012-05-22
Old thread closed.

---

