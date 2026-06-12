---
title: "installing graphic driver - drivers for suse/fedora"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by tadcan on 2009-05-11
Ubuntu has just been installed on a computer with an ati radeon 9200 graphics card. They have linux drivers for suse and fedora, but no .deb file or source code to compile from. 

[http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

Ati catalyst control was installed from the repos, but needs the drivers to use.

Is there a way around this?

---

### Post by AndThenWhat on 2009-05-11
Yeah if you install a program called "alien" I think it converts .rpm's for Fedora into .deb's for Ubuntu.

---

### Post by Cheesemill on 2009-05-11
You shouldn't have to download anything from the ATI website, just go to System > Administration > Hardware Drivers and select the appropriate driver from the list.

Cheesemill

---

### Post by tadcan on 2009-05-11
> **Cheesemill said:**
> You shouldn't have to download anything from the ATI website, just go to System > Administration > Hardware Drivers and select the appropriate driver from the list.

Cheesemill

I tried that and it wasn't listed.

---

### Post by tadcan on 2009-05-11
Alien was unable to build a deb. Here is the out put. 

Any suggestions? 

```
martine@martine-desktop:~/Desktop$ alien fglrx64_6_8_0-8.28.8-1.x86_64.rpm
Must run as root to convert to deb format (or you may use fakeroot).
martine@martine-desktop:~/Desktop$ sudo alien fglrx64_6_8_0-8.28.8-1.x86_64.rpm
Warning: Skipping conversion of scripts in package fglrx64_6_8_0: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/fglrx64-6-8-0
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libc.so.6 needed by debian/fglrx64-6-8-0/usr/X11R6/lib64/libfglrx_dm.so.1.0 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'i386' does not appear in package's architecture list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: `fglrx64_6_8_0-8.28.8': No such file or directory
```

---

### Post by Michael Dooley on 2009-05-11
> **tadcan said:**
> Is there a way around this?
It looks like you are working with 9.04 64-bit. Please see [this]("http://http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") page for instructions on how to proceed with a Jaunty installation of the ATI drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by alexandari on 2009-05-11
How about Envy? It`s a rly cool software for installing ATI and NVIDIA drivers (the latest) You`r just 2 clicks away from the driver installation ((((:

---

### Post by tadcan on 2009-05-11
I didn't download the iso, so maybe it was x64 bit. I'll check that. The package name has x86_64 at then end, so is the package for 64 bit and not the OS. The other options on the ati website are not for xorg, so I presumed it wouldn't work.

Thanks for the links. 

The ati graphic cards are discontinued, so, hopefully 'new' still works.

---

### Post by tadcan on 2009-05-17
So I tried the ati program in the repos and the GUI crashed afterwards, so I reinstalled Ubuntu from a 32bit CD.

I installed EnvyNG and none of the drivers were compatible. 

I tried again with alien and I got the same out put as above. 

With lspci I found out the graphic card.

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
```

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

The above link says that the listed cards are not supported. This card is not listed, but is a previous model, so I presume it wouldn't be supported. 

Any more suggestions.

---

### Post by waspbr on 2009-05-17
the situation looks rather grim at the moment, I guess that you have a few options here that are not ideal.

1 - use the openSource Drivers - tho 3d acceleration is not supported yet
2 - wait and hope that the 9.5 drivers solve the issue (they should come out soon)
3 - roll back to intrepid

I am on a similar situation, I will use the open source drivers until the new drivers come out. 

/me keeps his fingers crossed

---

### Post by markbuntu on 2009-05-17
That card is no longer supported by ati so the driver from ati will not work. Give it up, you are just wasting your time.

The open source ati driver should work just fine for that card with Jaunty.

---

