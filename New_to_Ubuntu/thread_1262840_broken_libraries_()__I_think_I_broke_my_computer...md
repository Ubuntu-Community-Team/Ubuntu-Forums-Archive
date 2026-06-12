---
title: "broken libraries (?)  I think I broke my computer..."
date: 2009-09-10
forum: New to Ubuntu
---

### Post by karasuman on 2009-09-10
I'm in the process of trying to get dmtcp to work on my netbook for work.  My professor suggested copying the files in /usr/lib from a computer that had it working to mine and seeing if that helped.  Well, that didn't help, and now I can't do things like load synaptic package manager or even gedit.  I get errors like:

```
beth@cheerbear-netbook:~$ gedit
gedit: error while loading shared libraries: liblaunchpad-integration.so.1: cannot open shared object file: No such file or directory

```

and

```
beth@cheerbear-netbook:~/Desktop$ svn co https://dmtcp.svn.sourceforge.net/svnroot/dmtcp dmtcp
svn: error while loading shared libraries: libdb-4.6.so: cannot open shared object file: No such file or directory

```

Help.  Please.  I don't even know what's going on.  :-/

Here are some things I tried and what happened:

```
beth@cheerbear-netbook:~/Desktop$ sudo aptitude install -f
[sudo] password for beth: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Locale/gettext/gettext.so: undefined symbol: Perl_Tstack_sp_ptr
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done

beth@cheerbear-netbook:~/Desktop$ sudo aptitude update
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly

```

---

### Post by NoaHall on 2009-09-10
Try "sudo ldconfig" and then try using apt-get again. See what happens.

---

### Post by karasuman on 2009-09-10
Thanks for the quick reply.  Here's the output from what you suggested:

```
beth@cheerbear-netbook:~/Desktop$ sudo ldconfig
/sbin/ldconfig.real: file /usr/lib/libgstreamer-0.10.so.0.16.0 is truncated

beth@cheerbear-netbook:~/Desktop$ sudo aptitude update
Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com jaunty-security Release [49.6kB]
Get:3 http://security.ubuntu.com jaunty-security/main Packages [88.9kB]
Get:4 http://us.archive.ubuntu.com jaunty Release.gpg [189B]
Get:5 http://security.ubuntu.com jaunty-security/restricted Packages [2589B]                                                 
Get:6 http://security.ubuntu.com jaunty-security/main Sources [24.4kB]                                                       
Get:7 http://security.ubuntu.com jaunty-security/restricted Sources [623B]                                                   
Get:8 http://security.ubuntu.com jaunty-security/universe Packages [34.5kB]                                                  
Get:9 http://security.ubuntu.com jaunty-security/universe Sources [7109B]                                                    
Get:10 http://security.ubuntu.com jaunty-security/multiverse Packages [1662B]                                                
Get:11 http://security.ubuntu.com jaunty-security/multiverse Sources [588B]                                                  
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                                                               
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US                                                         
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US                                                           
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US                                                         
Get:12 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]                                                        
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US                                                       
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US                                                 
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US                                                   
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US                                                 
Hit http://us.archive.ubuntu.com jaunty Release                                                                              
Get:13 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]                                                          
Hit http://us.archive.ubuntu.com jaunty/main Packages                                                                        
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                                                                  
Hit http://us.archive.ubuntu.com jaunty/main Sources                                                                         
Hit http://us.archive.ubuntu.com jaunty/restricted Sources                                                                   
Hit http://us.archive.ubuntu.com jaunty/universe Packages                                                                    
Hit http://us.archive.ubuntu.com jaunty/universe Sources                                                                     
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages                                                                  
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources                                                                   
Get:14 http://us.archive.ubuntu.com jaunty-updates/main Packages [169kB]                                                     
Get:15 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [2589B]                                               
Get:16 http://us.archive.ubuntu.com jaunty-updates/main Sources [48.7kB]                                                     
Get:17 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [623B]                                                 
Get:18 http://us.archive.ubuntu.com jaunty-updates/universe Packages [54.4kB]                                                
Get:19 http://us.archive.ubuntu.com jaunty-updates/universe Sources [14.9kB]                                                 
Get:20 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [6717B]                                               
Get:21 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [2040B]                                                
Fetched 559kB in 24s (22.4kB/s)                                                                                              
Reading package lists... Done

Current status: 7 updates [+7].

```

I'm still getting the same errors trying to run programs:

```
beth@cheerbear-netbook:~/Desktop$ gedit
gedit: error while loading shared libraries: liblaunchpad-integration.so.1: cannot open shared object file: No such file or directory
beth@cheerbear-netbook:~/Desktop$ synaptic
synaptic: error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file or directory

```

---

### Post by NoaHall on 2009-09-10
Right, so apt-get works now? My advice is to try and reinstall gedit - it should automatically add the libs you need for it.

"sudo apt-get remove --purge gedit"
"sudo apt-get install gedit"

---

### Post by karasuman on 2009-09-10
I don't really understand what works and what doesn't or why.  gedit and synaptic are examples of things that don't work, but I don't know of anything that DOES other than firefox.

I did try to remove/uninstall gedit and synaptic, but I can't.  When I see if apt-get does anything even after these errors, I am informed that (whatever) is already the latest version, so it seems like the uninstaller is failing.

```
beth@cheerbear-netbook:~/Desktop$ sudo apt-get remove --purge gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gedit*
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
After this operation, 1929kB disk space will be freed.
Do you want to continue [Y/n]? y
/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Locale/gettext/gettext.so: undefined symbol: Perl_Tstack_sp_ptr
(Reading database ... 190288 files and directories currently installed.)
Removing gedit ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: gconf_schema_set_gettext_domain
dpkg: error processing gedit (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 gedit
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I also can't view manual entries without being a superuser, for instance:

```
beth@cheerbear-netbook:~/Desktop$ man gedit
bash: /usr/bin/man: Permission denied
beth@cheerbear-netbook:~/Desktop$ sudo man gedit

```

---

### Post by NoaHall on 2009-09-10
Can you post the output from "ls -a /usr/lib/" for me?

The problem is probably, at a guess, that some of  your files have been replaced/deleted when you copied the /usr/lib file across. "sudo ldconfig" should have fixed broken links - but as there are still some, then it's suggesting that they have just been deleted. This is why you shouldn't mess around with anything core unless you know exactly what you are doing ;)

---

### Post by karasuman on 2009-09-10
I knew it was a bad idea when I tried it, but I was told to do it anyway...

The output of that is waaaaaaay too long; I can't even view it all in the terminal.  Here's the last bit:

```
libass.so.1.1.0				    libgtk-x11-2.0.so.0.1200.9		   libSDL_image-1.2.so.0
libatk-1.0.a				    libgtk-x11-2.0.so.0.1600.1		   libSDL_image-1.2.so.0.1.5
libatk-1.0.la				    libgtop-2.0.so.7			   libSDL_mixer-1.2.so.0
libatk-1.0.so				    libgtop-2.0.so.7.1.1		   libSDL_mixer-1.2.so.0.2.6
libatk-1.0.so.0				    libgtop-2.0.so.7.2.0		   libSDL_ttf-2.0.so.0
libatk-1.0.so.0.2209.1			    libgtrtst.so.1			   libSDL_ttf-2.0.so.0.6.3
libatk-1.0.so.0.2609.1			    libgtrtst.so.1.0.0			   libseahorse.so.0
libatkmm-1.6.so.1			    libgucharmap.so.7			   libseahorse.so.0.0.0
libatkmm-1.6.so.1.0.30			    libgucharmap.so.7.0.0		   libsensors.so.3
libatlas.so.3gf				    libguile-ltdl.so.1			   libsensors.so.3.1.4
libatlas.so.3gf.0			    libguile-ltdl.so.1.0.1		   libsensors.so.3.1.6
libaudiofile.so.0			    libguilereadline-v-12.la		   libsexy.so.2
libaudiofile.so.0.0.2			    libguilereadline-v-12.so.12		   libsexy.so.2.0.4
libaudio.so.2				    libguilereadline-v-12.so.12.3.1	   libsgutils.so.1
libaudio.so.2.4				    libguilereadline-v-17.la		   libsgutils.so.1.0.0
libavahi-client.so.3			    libguilereadline-v-17.so.17		   libshout.so.3
libavahi-client.so.3.2.4		    libguilereadline-v-17.so.17.0.3	   libshout.so.3.2.0
libavahi-common.so.3			    libguile.so.12			   libsidplay.so.1
libavahi-common.so.3.5.0		    libguile.so.12.3.1			   libsidplay.so.1.0.3
libavahi-core.so.5			    libguile.so.17			   libsigc-2.0.so.0
libavahi-core.so.5.0.5			    libguile.so.17.2.0			   libsigc-2.0.so.0.0.0
libavahi-glib.so.1			    libguile-srfi-srfi-13-14-v-1.la	   libsilc-1.1.so.2
libavahi-glib.so.1.0.1			    libguile-srfi-srfi-13-14-v-1.so.1	   libsilc-1.1.so.2.1.0
libavahi-ui.so.0			    libguile-srfi-srfi-13-14-v-1.so.1.0.1  libsilcclient-1.1.so.2
libavahi-ui.so.0.1.0			    libguile-srfi-srfi-13-14-v-3.la	   libsilcclient-1.1.so.2.0.0
libavc1394.so.0				    libguile-srfi-srfi-13-14-v-3.so.3	   libsilcclient-1.1.so.2.0.1
libavc1394.so.0.3.0			    libguile-srfi-srfi-13-14-v-3.so.3.0.1  libslp.so.1
libavcodec.so.52			    libguile-srfi-srfi-1-v-3.la		   libslp.so.1.0.1
libavcodec.so.52.20.0			    libguile-srfi-srfi-1-v-3.so.3	   libSM.a
libavformat.so.52			    libguile-srfi-srfi-1-v-3.so.3.0.2	   libsmbclient.so.0
libavformat.so.52.31.0			    libguile-srfi-srfi-4-v-1.la		   libsmbios_c.so.2
libavutil.so.1d				    libguile-srfi-srfi-4-v-1.so.1	   libsmbios_c.so.2.2.1
libavutil.so.1d.49.3.0			    libguile-srfi-srfi-4-v-1.so.1.0.1	   libsmbios.so.1
libavutil.so.49				    libguile-srfi-srfi-4-v-3.la		   libsmbios.so.1.0.13
libavutil.so.49.15.0			    libguile-srfi-srfi-4-v-3.so.3	   libsmbios.so.2
libbeagle.so.1				    libguile-srfi-srfi-4-v-3.so.3.0.1	   libsmbios.so.2.1.0
libbeagle.so.1.0.0			    libguile-srfi-srfi-60-v-2.la	   libsmime3.so
libbfd-2.18.0.20080103.so		    libguile-srfi-srfi-60-v-2.so.2	   libsmime3.so.1d
libbfd-2.19.1.so			    libguile-srfi-srfi-60-v-2.so.2.0.2	   libSM.so
libbind9.so.30				    libgutenprint.so.2			   libSM.so.6
libbind9.so.30.1.0			    libgutenprint.so.2.0.0		   libSM.so.6.0.0
libbind9.so.40				    libgutenprint.so.2.0.3		   libsndfile.so.1
libbind9.so.40.0.5			    libgvc.so.4				   libsndfile.so.1.0.17
libblas.so.3gf				    libgvc.so.4.0.0			   libsnmp.so.15
libblas.so.3gf.0			    libgvfscommon-dnssd.so.0		   libsnmp.so.15.1.0
libbluetooth.so.2			    libgvfscommon-dnssd.so.0.0.0	   libSoundTouch.so.1
libbluetooth.so.2.9.6			    libgvfscommon.so.0			   libSoundTouch.so.1.0.0
libbluetooth.so.3			    libgvfscommon.so.0.0.0		   libsoup-2.4.so.1
libbluetooth.so.3.2.1			    libgweather.so.1			   libsoup-2.4.so.1.2.0
libbonobo-2.so.0			    libgweather.so.1.0.3		   libsoup-gnome-2.4.so.1
libbonobo-2.so.0.0.0			    libgweather.so.1.4.5		   libsoup-gnome-2.4.so.1.2.0
libbonobo-activation.so.4		    libHalf.so.2			   libspectre.so.1
libbonobo-activation.so.4.0.0		    libHalf.so.2.0.2			   libspectre.so.1.1.2
libbonoboui-2.so.0			    libHalf.so.6			   libspeexdsp.so.1
libbonoboui-2.so.0.0.0			    libHalf.so.6.0.0			   libspeexdsp.so.1.5.0
libboost_regex-gcc41-1_34_1.so.1.34.1	    libhal.so.1				   libspeex.so.1
libboost_regex-gcc41-mt-1_34_1.so.1.34.1    libhal.so.1.0.0			   libspeex.so.1.2.0
libboost_regex-gcc42-1_34_1.so.1.34.1	    libhal-storage.so.1			   libspeex.so.1.5.0
libboost_regex-gcc42-mt-1_34_1.so.1.34.1    libhal-storage.so.1.0.0		   libspi.so.0
libboost_signals-gcc41-1_34_1.so.1.34.1     libhdf5-1.6.6.so.0			   libspi.so.0.10.11
libboost_signals-gcc41-mt-1_34_1.so.1.34.1  libhdf5-1.6.6.so.0.0.0		   libsqlite3.so.0
libboost_signals-gcc42-1_34_1.so.1.34.1     libhdf5_cpp-1.6.6.so.0		   libsqlite3.so.0.8.6
libboost_signals-gcc42-mt-1_34_1.so.1.34.1  libhdf5_cpp-1.6.6.so.0.0.0		   libsqlite.so.0
libBPM.so.1				    libhdf5_hl-1.6.6.so.0		   libsqlite.so.0.8.6
libBPM.so.1.0.0				    libhdf5_hl-1.6.6.so.0.0.0		   libssl3.so
libBrokenLocale.a			    libhesiod.so.0			   libssl3.so.1d
libBrokenLocale.so			    libhpip.so.0			   libssl.so.0.9.8
libbsd-compat.a				    libhpip.so.0.0.1			   libstartup-notification-1.so.0
libbtf.so.3.2.0				    libhpmud.so.0			   libstartup-notification-1.so.0.0.0
libc.a					    libhpmud.so.0.0.2			   libstdc++.so.5
libcaca.so.0				    libhpmud.so.0.0.4			   libstdc++.so.5.0.7
libcaca++.so.0				    libhunspell-1.1.so.0		   libstdc++.so.6
libcaca++.so.0.99.13			    libhunspell-1.1.so.0.0.0		   libstdc++.so.6.0.10
libcaca.so.0.99.16			    libhunspell-1.2.so.0		   libstlport_gcc.so.4.6
libcaca++.so.0.99.16			    libhunspell-1.2.so.0.0.0		   libsvn_client-1.so.1
libcairo.a				    libhyphen.so.0			   libsvn_client-1.so.1.0.0
libcairo.la				    libhyphen.so.0.2.0			   libsvn_delta-1.so.1
libcairomm-1.0.so.1			    libI810XvMC.so			   libsvn_delta-1.so.1.0.0
libcairomm-1.0.so.1.1.0			    libI810XvMC.so.1			   libsvn_diff-1.so.1
libcairomm-1.0.so.1.2.0			    libI810XvMC.so.1.0.0		   libsvn_diff-1.so.1.0.0
libcairo.so				    libical.so.0			   libsvn_fs-1.so.1
libcairo.so.2				    libical.so.0.43.0			   libsvn_fs-1.so.1.0.0
libcairo.so.2.10800.6			    libicalss.so.0			   libsvn_fs_base-1.so.1
libcairo.so.2.17.3			    libicalss.so.0.43.0			   libsvn_fs_base-1.so.1.0.0
libcamd.so.3.2.0			    libicalvcal.so.0			   libsvn_fs_fs-1.so.1
libcamel-1.2.so.14			    libicalvcal.so.0.43.0		   libsvn_fs_fs-1.so.1.0.0
libcamel-1.2.so.14.0.0			    libICE.a				   libsvn_fs_util-1.so.1
libcamel-provider-1.2.so.11		    libICE.so				   libsvn_fs_util-1.so.1.0.0
libcamel-provider-1.2.so.11.0.0		    libICE.so.6				   libsvn_ra-1.so.1
libcamel-provider-1.2.so.14		    libICE.so.6.3.0			   libsvn_ra-1.so.1.0.0
libcamel-provider-1.2.so.14.0.0		    libicudata.so.38			   libsvn_ra_dav-1.so.1
libcanberra-0.11			    libicudata.so.38.0			   libsvn_ra_local-1.so.1
libcanberra-gtk.so.0			    libicudata.so.38.1			   libsvn_ra_local-1.so.1.0.0
libcanberra-gtk.so.0.0.4		    libicui18n.so.38			   libsvn_ra_neon-1.so.1
libcanberra.so.0			    libicui18n.so.38.1			   libsvn_ra_neon-1.so.1.0.0
libcanberra.so.0.1.4			    libicuio.so.38			   libsvn_ra_svn-1.so.1
libcblas.so.3gf				    libicuio.so.38.0			   libsvn_ra_svn-1.so.1.0.0
libcblas.so.3gf.0			    libicuio.so.38.1			   libsvn_repos-1.so.1
libccolamd.so.3.2.0			    libicule.so.38			   libsvn_repos-1.so.1.0.0
libcdaudio.so.1				    libicule.so.38.0			   libsvn_subr-1.so.1
libcdaudio.so.1.0.0			    libicule.so.38.1			   libsvn_subr-1.so.1.0.0
libcdda_interface.so.0			    libiculx.so.38			   libsvn_swig_perl-1.so.1
libcdda_interface.so.0.10.0		    libiculx.so.38.0			   libsvn_swig_perl-1.so.1.0.0
libcdda_interface.so.0.10.2		    libiculx.so.38.1			   libsvn_wc-1.so.1
libcdda_paranoia.so.0			    libicutu.so.38			   libsvn_wc-1.so.1.0.0
libcdda_paranoia.so.0.10.2		    libicutu.so.38.0			   libswfdec-0.8.so.0
libcdio_cdda.so.0			    libicutu.so.38.1			   libswfdec-0.8.so.0.0.0
libcdio_cdda.so.0.0.2			    libicuuc.so.38			   libswfdec-gtk-0.8.so.0
libcdio_paranoia.so.0			    libicuuc.so.38.1			   libswfdec-gtk-0.8.so.0.0.0
libcdio_paranoia.so.0.0.2		    libid3tag.so.0			   libswscale.so.0
libcdio.so.7				    libid3tag.so.0.3.0			   libswscale.so.0.7.1
libcdio.so.7.1.0			    libIDL-2.so.0			   libsysfs.a
libcdt.so.4				    libIDL-2.so.0.0.0			   libsysfs.so
libcdt.so.4.0.0				    libidn.la				   libt1.so.5
libcelt.so.0				    libidn.so.11			   libt1.so.5.1.2
libcelt.so.0.0.0			    libidn.so.11.5.30			   libt1x.so.5
libcgraph.so.4				    libidn.so.11.5.39			   libt1x.so.5.1.2
libcgraph.so.4.0.0			    libiec61883.so.0			   libtag.so.1
libcholmod.so.3.2.0			    libiec61883.so.0.1.0		   libtag.so.1.4.0
libchromeXvMCPro.so			    libieee1284.so.3			   libtag.so.1.5.0
libchromeXvMCPro.so.1			    libieee1284.so.3.2.2		   libtalloc.so.1
libchromeXvMCPro.so.1.0.0		    libieee.a				   libtalloc.so.1.2.0
libchromeXvMC.so			    libIex.so.2				   libtasn1.so.3
libchromeXvMC.so.1			    libIex.so.2.0.2			   libtasn1.so.3.0.16
libchromeXvMC.so.1.0.0			    libIex.so.6				   libtcl8.4.so.0
libcidn.so				    libIex.so.6.0.0			   libtdb.so.1
libck-connector.so.0			    libijs-0.35.so			   libtdb.so.1.1.3
libck-connector.so.0.0.0		    libIlmImf.so.2			   libtermcap.a
libclutter-glx-0.6.so.0			    libIlmImf.so.2.0.2			   libtermcap.so
libclutter-glx-0.6.so.0.600.0		    libIlmImf.so.6			   libthai.so.0
libclutter-glx-0.8.so.0			    libIlmImf.so.6.0.0			   libthai.so.0.1.1
libclutter-glx-0.8.so.0.808.0		    libIlmThread.so.6			   libtheoradec.so.1
libclutter-gtk-0.8.so.0			    libIlmThread.so.6.0.0		   libtheoradec.so.1.0.1
libclutter-gtk-0.8.so.0.802.0		    libImath.so.2			   libtheoraenc.so.1
libc_nonshared.a			    libImath.so.2.0.2			   libtheoraenc.so.1.0.1
libcolamd.so.3.2.0			    libImath.so.6			   libtheora.so.0
libcompizconfig.so.0			    libImath.so.6.0.0			   libtheora.so.0.3.2
libcompizconfig.so.0.0.0		    libImplicit.a			   libtheora.so.0.3.4
libcroco-0.6.so.3			    libImplicit.la			   libthread_db.so
libcroco-0.6.so.3.0.1			    libindicate.so.1			   libtic.a
libcrypt.a				    libindicate.so.1.0.0		   libtic.so
libcrypto.so.0.9.8			    libIntelXvMC.so			   libtiff.so.4
libcrypt.so				    libIntelXvMC.so.1			   libtiff.so.4.2.1
libcryptui.so.0				    libIntelXvMC.so.1.0.0		   libtk8.4.so.0
libcryptui.so.0.0.0			    libiptcdata.so.0			   libtotem-plparser-mini.so.12
libc.so					    libiptcdata.so.0.3.2		   libtotem-plparser-mini.so.12.2.5
libcsparse.so.3.2.0			    libisccc.so.30			   libtotem-plparser.so.10
libcspi.so.0				    libisccc.so.30.0.1			   libtotem-plparser.so.10.1.1
libcspi.so.0.10.11			    libisccc.so.40			   libtotem-plparser.so.12
libcucul.so.0				    libisccc.so.40.0.0			   libtotem-plparser.so.12.2.5
libcucul++.so.0				    libisccfg.so.30			   libtrackerclient.so.0
libcucul.so.0.99.13			    libisccfg.so.30.0.3			   libtrackerclient.so.0.0.0
libcucul++.so.0.99.13			    libisccfg.so.40			   libts-0.0.so.0
libcucul.so.0.99.16			    libisccfg.so.40.0.6			   libts-0.0.so.0.1.1
libcucul++.so.0.99.16			    libisc.so.45			   libtwolame.so.0
libcupsimage.so.2			    libisc.so.45.0.3			   libtwolame.so.0.0.0
libcups.so.2				    libjack0.100.0			   libumfpack.so.3.2.0
libcurl-gnutls.so.3			    libjack-0.100.0.so.0		   libungif.so.4
libcurl-gnutls.so.4			    libjackserver.so.0			   libungif.so.4.1
libcurl-gnutls.so.4.0.1			    libjackserver.so.0.0.28		   libungif.so.4.1.6
libcurl-gnutls.so.4.1.0			    libjack.so.0			   libuniconf.so.4.4
libcurl.so.4				    libjack.so.0.0.28			   libunique-1.0.so.0
libcurl.so.4.0.1			    libjasper.so.1			   libunique-1.0.so.0.2.6
libcurses.a				    libjasper.so.1.0.0			   libuniquewm-1.0.so.0
libcurses.so				    libjpeg.a				   libuniquewm-1.0.so.0.1.0
libcwidget.so.3				    libjpeg.la				   libuniquewm.a
libcwidget.so.3.0.0			    libjpeg.so				   libuniquewm.so
libcxsparse.so.3.2.0			    libjpeg.so.62			   libuno_cppuhelpergcc3.so.3
libdaemon.so.0				    libjpeg.so.62.0.0			   libuno_cppu.so.3
libdaemon.so.0.4.0			    libk5crypto.so.3			   libuno_purpenvhelpergcc3.so.3
libdatrie.so.0				    libk5crypto.so.3.1			   libuno_salhelpergcc3.so.3
libdatrie.so.0.0.1			    libkabc_file.so.1			   libuno_sal.so.3
libdatrie.so.0.0.3			    libkabc_file.so.1.0.0		   libusb-0.1.so.4
libdb-4.6.so				    libkabc_ldapkio.so.1		   libutil.a
libdb-4.7.so				    libkabc_ldapkio.so.1.0.0		   libutil.so
libdbus-1.so.3				    libkabc.so.1			   libv4l
libdbus-1.so.3.4.0			    libkabc.so.1.2.0			   libv4l1.so.0
libdbus-glib-1.so.2			    libkatepartinterfaces.so.0		   libv4l2.so.0
libdbus-glib-1.so.2.1.0			    libkatepartinterfaces.so.0.0.0	   libv4lconvert.so.0
libdc1394.so.22				    libkdecore.so.4			   libva.so.0
libdc1394.so.22.1.0			    libkdecore.so.4.2.0			   libva.so.0.29.0
libdca.so.0				    libkdeeducore.so.1			   libvisual
libdca.so.0.0.0				    libkdeeducore.so.1.2.0		   libvisual-0.4
libDCOP.so.4				    libkdeeduplot.so.1			   libvisual-0.4.so.0
libDCOP.so.4.2.0			    libkdeeduplot.so.1.2.0		   libvisual-0.4.so.0.0.0
libdecoration.so.0			    libkdeeduui.so.3			   libvorbisenc.so.2
libdecoration.so.0.0.0			    libkdeeduui.so.3.0.5		   libvorbisenc.so.2.0.3
libdes425.so.3				    libkdefakes.so.4			   libvorbisfile.so.3
libdes425.so.3.0			    libkdefakes.so.4.2.0		   libvorbisfile.so.3.2.0
libdirect-1.0.so.0			    libkdegames.so.1			   libvorbis.so.0
libdirect-1.0.so.0.1.0			    libkdegames.so.1.2.0		   libvorbis.so.0.4.0
libdirect.a				    libkdeinit_cupsdconf.so		   libvte9
libdirectfb-1.0.so.0			    libkdeinit_dcopserver.so		   libvte.so.9
libdirectfb-1.0.so.0.1.0		    libkdeinit_kaddprinterwizard.so	   libvte.so.9.2.17
libdirectfb.a				    libkdeinit_kcookiejar.so		   libvte.so.9.5.0
libdirectfb.so				    libkdeinit_kded.so			   libWand.so.10
libdirect.so				    libkdeinit_klauncher.so		   libWand.so.10.0.9
libdjvulibre.so.21			    libkdeinit_kolf.la			   libwavpack.so.1
libdjvulibre.so.21.0.0			    libkdeprint_management.so.4		   libwavpack.so.1.0.3
libdl.a					    libkdeprint_management.so.4.2.0	   libwbclient.so.0
libdl.so				    libkdeprint.so.4			   libWildMidi.so.0
libdmx.so.1				    libkdeprint.so.4.2.0		   libWildMidi.so.0.0.0
libdmx.so.1.0.0				    libkdesasl.so.1			   libwmf-0.2.so.7
libdns_sd.so.1				    libkdesasl.so.1.2.0			   libwmf-0.2.so.7.1.0
libdns_sd.so.1.0.0			    libkdeui.so.4			   libwmflite-0.2.so.7
libdns.so.45				    libkdeui.so.4.2.0			   libwmflite-0.2.so.7.0.1
libdns.so.45.0.4			    libkdnssd.so.1			   libwnck-1.so.22
libdrm_intel.so.1			    libkdnssd.so.1.0.0			   libwnck-1.so.22.3.18
libdrm_intel.so.1.0.0			    libkhtml.so.4			   libwnck-1.so.22.3.8
libdrm.so.2				    libkhtml.so.4.2.0			   libwpd-0.8.so.8
libdrm.so.2.3.0				    libkimproxy.so.0			   libwpd-0.8.so.8.0.12
libdrm.so.2.4.0				    libkimproxy.so.0.0.0		   libwpd-0.8.so.8.0.14
libdvdnavmini.so.4			    libkio.so.4				   libwpg-0.1.so.1
libdvdnavmini.so.4.1.3			    libkio.so.4.2.0			   libwpg-0.1.so.1.0.3
libdvdnav.so.4				    libkiten.so.1			   libwpg-stream-0.1.so.1
libdvdnav.so.4.1.3			    libkiten.so.1.0.0			   libwpg-stream-0.1.so.1.0.3
libdvdread.so.4				    libkjava.so.1			   libwps-0.1.so.1
libdvdread.so.4.1.3			    libkjava.so.1.0.0			   libwps-0.1.so.1.0.1
libdv.so.4				    libklu.so.3.2.0			   libwps-0.1.so.1.0.2
libdv.so.4.0.3				    libkmdi2.so.1			   libwps-stream-0.1.so.1
libebackend-1.2.so.0			    libkmdi2.so.1.0.0			   libwps-stream-0.1.so.1.0.1
libebackend-1.2.so.0.0.0		    libkmdi.so.1			   libwps-stream-0.1.so.1.0.2
libebook-1.2.so.9			    libkmdi.so.1.0.0			   libwvstreams.so.4.4
libebook-1.2.so.9.1.1			    libkmedia2_idl.so.1			   libwvutils.so.4.4
libebook-1.2.so.9.3.0			    libkmedia2_idl.so.1.0.0		   libwx_baseu-2.8.so.0
libecal-1.2.so.7			    libkmedia2.la			   libwx_baseu-2.8.so.0.5.0
libecal-1.2.so.7.2.0			    libkmid.so.0			   libwx_baseu_net-2.8.so.0
libecal-1.2.so.7.2.1			    libkmid.so.0.0.95			   libwx_baseu_net-2.8.so.0.5.0
libedata-book-1.2.so.2			    libknewstuff.so.1			   libwx_baseu_xml-2.8.so.0
libedata-book-1.2.so.2.4.1		    libknewstuff.so.1.0.0		   libwx_baseu_xml-2.8.so.0.5.0
libedata-cal-1.2.so.6			    libkntlm.so.0			   libwx_gtk2u_adv-2.8.so.0
libedata-cal-1.2.so.6.0.2		    libkntlm.so.0.0.0			   libwx_gtk2u_adv-2.8.so.0.5.0
libedataserver-1.2.so.11		    libkolf.la				   libwx_gtk2u_aui-2.8.so.0
libedataserver-1.2.so.11.0.0		    libkolf.so.1			   libwx_gtk2u_aui-2.8.so.0.5.0
libedataserver-1.2.so.9			    libkolf.so.1.2.0			   libwx_gtk2u_core-2.8.so.0
libedataserver-1.2.so.9.1.0		    libkpathsea.so.4			   libwx_gtk2u_core-2.8.so.0.5.0
libedataserverui-1.2.so.8		    libkpathsea.so.4.0.0		   libwx_gtk2u_fl-2.8.so.0
libedataserverui-1.2.so.8.1.0		    libkrb4.so.2			   libwx_gtk2u_fl-2.8.so.0.5.0
libedit.so.2				    libkrb4.so.2.0			   libwx_gtk2u_gizmos-2.8.so.0
libedit.so.2.11				    libkrb5.so.3			   libwx_gtk2u_gizmos-2.8.so.0.5.0
libedit.so.2.9				    libkrb5.so.3.3			   libwx_gtk2u_gizmos_xrc-2.8.so.0
libeel-2.so.2				    libkrb5support.so.0			   libwx_gtk2u_gizmos_xrc-2.8.so.0.5.0
libeel-2.so.2.22.2			    libkrb5support.so.0.1		   libwx_gtk2u_gl-2.8.so.0
libegroupwise-1.2.so.13			    libkresources.so.1			   libwx_gtk2u_gl-2.8.so.0.5.0
libegroupwise-1.2.so.13.0.1		    libkresources.so.1.2.0		   libwx_gtk2u_html-2.8.so.0
libelf-0.131.so				    libkscreensaver.so.4		   libwx_gtk2u_html-2.8.so.0.5.0
libelf.so.1				    libkscreensaver.so.4.2.0		   libwx_gtk2u_media-2.8.so.0
libemeraldengine.so.0			    libkscript.so.0			   libwx_gtk2u_media-2.8.so.0.5.0
libemeraldengine.so.0.0.0		    libkscript.so.0.0.0			   libwx_gtk2u_ogl-2.8.so.0
libenca.so.0				    libkspell2.so.1			   libwx_gtk2u_ogl-2.8.so.0.5.0
libenca.so.0.5.1			    libkspell2.so.1.0.0			   libwx_gtk2u_plot-2.8.so.0
libenchant.a				    libkspell.so.4			   libwx_gtk2u_plot-2.8.so.0.5.0
libenchant.la				    libkspell.so.4.2.0			   libwx_gtk2u_qa-2.8.so.0
libenchant.so				    libkwalletclient.so.1		   libwx_gtk2u_qa-2.8.so.0.5.0
libenchant.so.1				    libkwalletclient.so.1.0.1		   libwx_gtk2u_richtext-2.8.so.0
libenchant.so.1.4.2			    liblapack_atlas.so.3gf		   libwx_gtk2u_richtext-2.8.so.0.5.0
libept.so.0				    liblapack_atlas.so.3gf.0		   libwx_gtk2u_stc-2.8.so.0
libept.so.0.5.25			    liblapack.so.3gf			   libwx_gtk2u_stc-2.8.so.0.5.0
libesd.so.0				    liblapack.so.3gf.0			   libwx_gtk2u_svg-2.8.so.0
libesd.so.0.2.39			    liblaunchpad-integration.so.1	   libwx_gtk2u_svg-2.8.so.0.5.0
libespeak.so.1				    liblaunchpad-integration.so.1.0.0	   libwx_gtk2u_xrc-2.8.so.0
libespeak.so.1.1.36			    liblber-2.4.so.2			   libwx_gtk2u_xrc-2.8.so.0.5.0
libespeak.so.1.1.40			    liblber-2.4.so.2.0.5		   libX11.a
libevbackend.so.0			    liblber-2.4.so.2.4.1		   libx11globalcomm.so.1
libevbackend.so.0.0.0			    liblcms.so.1			   libx11globalcomm.so.1.0.0
libevdocument.so.1			    liblcms.so.1.0.16			   libX11.so
libevdocument.so.1.0.0			    liblcms.so.1.0.18			   libX11.so.6
libevview.so.1				    libldap-2.4.so.2			   libX11.so.6.2.0
libevview.so.1.0.0			    libldap_r-2.4.so.2			   libX11-xcb.so.1
libexchange-storage-1.2.so.3		    libldap_r-2.4.so.2.4.1		   libX11-xcb.so.1.0.0
libexchange-storage-1.2.so.3.0.0	    libldl.so.3.2.0			   libxapian.so.15
libexempi.so.3				    liblirc_client.la			   libxapian.so.15.5.1
libexempi.so.3.1.1			    liblirc_client.so.0			   libXau.a
libexempi.so.3.1.4			    liblirc_client.so.0.2.0		   libXau.so
libexif.so.12				    liblirc_client.so.0.2.1		   libXau.so.6
libexif.so.12.2.0			    liblockfile.so.1			   libXau.so.6.0.0
libexpat.a				    liblockfile.so.1.0			   libXaw7.so.7
libexpat.la				    libloginhelper.so.0			   libXaw7.so.7.0.0
libexpat.so				    libloginhelper.so.0.0.0		   libXaw.so.7
libexpat.so.1				    liblpint-bonobo.so.0		   libxcb.a
libexpat.so.1.5.2			    liblpint-bonobo.so.0.0.0		   libxcb-render.a
libexpatw.a				    liblrdf.so.0			   libxcb-render.so
libexpatw.la				    liblrdf.so.0.0.0			   libxcb-render.so.0
libexpatw.so				    libltdl.so.3			   libxcb-render.so.0.0.0
libexpatw.so.1				    libltdl.so.3.1.6			   libxcb-render-util.a
libexpatw.so.1.5.2			    libltdl.so.7			   libxcb-render-util.so
libexslt.so.0				    libltdl.so.7.2.0			   libxcb-render-util.so.0
libexslt.so.0.8.13			    liblua50.so.5.0			   libxcb-render-util.so.0.0.0
libextdate.so.1				    liblualib50.so.5.0			   libxcb-shape.so.0
libextdate.so.1.2.0			    liblwres.so.30			   libxcb-shape.so.0.0.0
libf77blas.so.3gf			    liblwres.so.30.0.5			   libxcb-shm.so.0
libf77blas.so.3gf.0			    liblwres.so.40			   libxcb-shm.so.0.0.0
libfaad.so.0				    liblwres.so.40.0.0			   libxcb.so
libfaad.so.0.0.0			    liblzo2.so.2			   libxcb.so.1
libfakekey.so.0				    liblzo2.so.2.0.0			   libxcb.so.1.0.0
libfakekey.so.0.0.1			    libm.a				   libxcb.so.1.1.0
libfam.so.0				    libmad.so.0				   libxcb-xv.so.0
libfam.so.0.0.0				    libmad.so.0.2.1			   libxcb-xv.so.0.0.0
libffado.so.0.0.0u			    libMagickCore.so.1			   libXcomposite.a
libffi.so.4				    libMagickCore.so.1.0.0		   libXcomposite.so
libffi.so.4.0.1				    libMagick.so.10			   libXcomposite.so.1
libffi.so.5				    libMagick.so.10.0.9			   libXcomposite.so.1.0.0
libffi.so.5.0.8				    libMagickWand.so.1			   libXcursor.a
libfftw3f.so.3				    libMagickWand.so.1.0.0		   libXcursor.so
libfftw3f.so.3.1.2			    libmagic.so.1			   libXcursor.so.1
libfftw3f_threads.so.3			    libmagic.so.1.0.0			   libXcursor.so.1.0.2
libfftw3f_threads.so.3.1.2		    libmbca.so.0			   libXdamage.a
libfftw3l.so.3				    libmbca.so.0.0.2			   libXdamage.so
libfftw3l.so.3.1.2			    libmb.so.1				   libXdamage.so.1
libfftw3l_threads.so.3			    libmb.so.1.0.9			   libXdamage.so.1.1.0
libfftw3l_threads.so.3.1.2		    libmcheck.a				   libXdmcp.a
libfftw3.so.3				    libmcop_mt.so.1			   libXdmcp.so
libfftw3.so.3.1.2			    libmcop_mt.so.1.0.0			   libXdmcp.so.6
libfftw3_threads.so.3			    libmcop.so.1			   libXdmcp.so.6.0.0
libfftw3_threads.so.3.1.2		    libmcop.so.1.0.0			   libXevie.so.1
libFLAC.so.8				    libmeanwhile.so.1			   libXevie.so.1.0.0
libFLAC.so.8.2.0			    libmeanwhile.so.1.0.2		   libXext.a
libfontconfig.a				    libmenu.a				   libXext.so
libfontconfig.so			    libmenu.so				   libXext.so.6
libfontconfig.so.1			    libmenu.so.5			   libXext.so.6.4.0
libfontconfig.so.1.3.0			    libmenu.so.5.6			   libXfixes.a
libfontenc.so.1				    libmenu.so.5.7			   libXfixes.so
libfontenc.so.1.0.0			    libmenuw.so.5			   libXfixes.so.3
libform.a				    libmenuw.so.5.6			   libXfixes.so.3.1.0
libform.so				    libmenuw.so.5.7			   libXfont.so.1
libform.so.5				    libmetacity-private.so.0		   libXfont.so.1.4.1
libform.so.5.7				    libmetacity-private.so.0.0.0	   libXft.a
libformw.so.5				    libmms.so.0				   libXft.so
libformw.so.5.7				    libmms.so.0.0.2			   libXft.so.2
libfreebob.so.0				    libmng.so.1				   libXft.so.2.1.13
libfreebob.so.0.1.0			    libmng.so.1.1.0.9			   libXft.so.2.1.2
libfreetype.a				    libmodplug.so.0			   libXi.a
libfreetype.la				    libmodplug.so.0.0.0			   libXinerama.a
libfreetype.so				    libMonoPosixHelper.so		   libXinerama.so
libfreetype.so.6			    libmono-profiler-aot.so.0		   libXinerama.so.1
libfreetype.so.6.3.20			    libmono-profiler-aot.so.0.0.0	   libXinerama.so.1.0.0
libfribidi.so.0				    libmono-profiler-cov.so.0		   libxine.so.1
libfribidi.so.0.0.0			    libmono-profiler-cov.so.0.0.0	   libxine.so.1.20.0
libFS.so.6				    libmono-profiler-logging.so.0	   libXi.so
libFS.so.6.0.0				    libmono-profiler-logging.so.0.0.0	   libXi.so.6
libfusion-1.0.so.0			    libmono.so.0			   libXi.so.6.0.0
libfusion-1.0.so.0.1.0			    libmono.so.0.0.0			   libxkbfile.so.1
libfusion.a				    libMonoSupportW.so			   libxkbfile.so.1.0.2
libfusion.so				    libmpcdec.so.3			   libxklavier.so.12
libg.a					    libmpcdec.so.3.1.1			   libxklavier.so.12.2.0
libgadu.so.3				    libmpeg2convert.so.0		   libxml++-2.6.so.2
libgadu.so.3.5				    libmpeg2convert.so.0.0.0		   libxml++-2.6.so.2.0.7
libgadu.so.3.9.0			    libmpeg2.so.0			   libxml2.a
libgailutil.so.18			    libmpeg2.so.0.0.0			   libxml2.la
libgailutil.so.18.0.1			    libmpfr.so.1			   libxml2.so
libgamin-1.so.0				    libmpfr.so.1.2.0			   libxml2.so.2
libgamin-1.so.0.1.9			    libmp.so.3				   libxml2.so.2.6.31
libgccpp.so.1				    libmp.so.3.1.13			   libxml2.so.2.6.32
libgccpp.so.1.0.2			    libMrm.so.2				   libXm.so.2
libgcj.so.81				    libMrm.so.2.0.1			   libXm.so.2.0.1
libgcj.so.81.0.0			    libm.so				   libXmu.so.6
libgcj-tools.so.81			    libmtp.so.7				   libXmu.so.6.2.0
libgcj-tools.so.81.0.0			    libmtp.so.7.1.0			   libXmuu.so.1
libgconf2-4				    libmtp.so.8				   libXmuu.so.1.0.0
libgconf-2.so.4				    libmtp.so.8.0.0			   libxplc.so.0.3.13
libgconf-2.so.4.1.5			    libmusicbrainz.so.4			   libxplc.so.0.3.13-unstable
libgcr.so.0				    libmusicbrainz.so.4.0.3		   libXpm.so.4
libgcr.so.0.0.0				    libmysqlclient_r.so.15		   libXpm.so.4.11.0
libgc.so.1				    libmysqlclient_r.so.15.0.0		   libXp.so.6
libgc.so.1.0.2				    libmysqlclient.so.15		   libXp.so.6.2.0
libgda-3.0.so.3				    libmysqlclient.so.15.0.0		   libXrandr.a
libgda-3.0.so.3.0.0			    libnautilus-burn.so.4		   libXrandr.so
libgda-report-3.0.so.3			    libnautilus-burn.so.4.1.0		   libXrandr.so.2
libgda-report-3.0.so.3.0.0		    libnautilus-extension.so.1		   libXrandr.so.2.1.0
libgdasql-3.0.so.3			    libnautilus-extension.so.1.1.0	   libXrandr.so.2.2.0
libgdasql-3.0.so.3.0.0			    libncurses.a			   libXrender.a
libgdata-1.2.so.1			    libncurses++.a			   libXrender.so
libgdata-1.2.so.1.0.0			    libncurses.so			   libXrender.so.1
libgdata-google-1.2.so.1		    libncurses.so.5			   libXrender.so.1.3.0
libgdata-google-1.2.so.1.0.0		    libneon-gnutls.so.27		   libXRes.so.1
libgdbm_compat.so.3			    libneon-gnutls.so.27.1.2		   libXRes.so.1.0.0
libgdbm_compat.so.3.0.0			    libneon.so.27			   libxslt.so.1
libgdbm.so.3				    libneon.so.27.0.2			   libxslt.so.1.1.22
libgdbm.so.3.0.0			    libneon.so.27.1.2			   libxslt.so.1.1.24
libgdict-1.0.so.5			    libnetpbm.so.10			   libXss.so.1
libgdict-1.0.so.5.0.15			    libnetpbm.so.10.0			   libXss.so.1.0.0
libgdict-1.0.so.6			    libnetsnmpagent.so.15		   libXTrap.so.6
libgdict-1.0.so.6.0.5			    libnetsnmpagent.so.15.1.0		   libXTrap.so.6.4.0
libgdiplus.so				    libnetsnmphelpers.so.15		   libXt.so.6
libgdiplus.so.0				    libnetsnmphelpers.so.15.1.0		   libXt.so.6.0.0
libgdiplus.so.0.0.0			    libnetsnmpmibs.so.15		   libXtst.so.6
libgdkglext-x11-1.0.so.0		    libnetsnmpmibs.so.15.1.0		   libXtst.so.6.1.0
libgdkglext-x11-1.0.so.0.0.0		    libnetsnmp.so.15			   libXvMC.so.1
libgdkmm-2.4.so.1			    libnetsnmp.so.15.1.0		   libXvMC.so.1.0.0
libgdkmm-2.4.so.1.0.30			    libnetsnmptrapd.so.15		   libXvMCW.so.1
libgdk_pixbuf-2.0.a			    libnetsnmptrapd.so.15.1.0		   libXvMCW.so.1.0.0
libgdk_pixbuf-2.0.la			    libnewt.so.0.52			   libXv.so.1
libgdk_pixbuf-2.0.so			    libnewt.so.0.52.2			   libXv.so.1.0.0
libgdk_pixbuf-2.0.so.0			    libnl.so.1				   libXxf86dga.so.1
libgdk_pixbuf-2.0.so.0.1200.9		    libnl.so.1.1			   libXxf86dga.so.1.0.0
libgdk_pixbuf-2.0.so.0.1600.1		    libnm_glib.so.0			   libXxf86misc.so.1
libgdk_pixbuf_xlib-2.0.a		    libnm_glib.so.0.0.0			   libXxf86misc.so.1.1.0
libgdk_pixbuf_xlib-2.0.la		    libnm_glib.so.0.1.0			   libXxf86vm.so.1
libgdk_pixbuf_xlib-2.0.so		    libnm_glib_vpn.so.0			   libXxf86vm.so.1.0.0
libgdk_pixbuf_xlib-2.0.so.0		    libnm_glib_vpn.so.0.0.0		   libz.a
libgdk_pixbuf_xlib-2.0.so.0.1600.1	    libnm-util.so.0			   libzephyr.so.3
libgdk-x11-2.0.a			    libnm-util.so.0.0.0			   libzephyr.so.3.0.0
libgdk-x11-2.0.la			    libnm-util.so.1			   libzlcore.so.0.8.17
libgdk-x11-2.0.so			    libnm-util.so.1.0.0			   libzlcore.so.0.9
libgdk-x11-2.0.so.0			    libnotify.so.1			   libzltext.so.0.8.17
libgdk-x11-2.0.so.0.1200.9		    libnotify.so.1.1.3			   libzltext.so.0.9
libgdk-x11-2.0.so.0.1600.1		    libnsl.a				   libz.so
libgdl-1.so.0				    libnsl.so				   locale
libgdl-1.so.0.0.0			    libnspr4.so				   lp_solve
libgdl-gnome-1.so.0			    libnspr4.so.0d			   man-db
libgdl-gnome-1.so.0.0.0			    libnss3.so				   mcop
libgd.so.2				    libnss3.so.1d			   Mcrt1.o
libgd.so.2.0.0				    libnss_compat.so			   memtest86+
libgettextlib-0.17.so			    libnss_dns.so			   menu
libgettextlib.la			    libnss_files.so			   metacity
libgettextlib.so			    libnss_hesiod.so			   midbrowser
libgettextpo.a				    libnss_nisplus.so			   mime
libgettextpo.la				    libnss_nis.so			   mono
libgettextpo.so				    libnssutil3.so			   mozilla
libgettextpo.so.0			    libnssutil3.so.1d			   mozilla-firefox
libgettextpo.so.0.4.0			    libodbccr.so.1			   nautilus
libgettextsrc-0.17.so			    libodbccr.so.1.0.0			   nautilus-cd-burner
libgettextsrc.la			    libodbcinst.so.1			   nautilus-sendto
libgettextsrc.so			    libodbcinst.so.1.0.0		   notification-daemon
libgfortran.so.3			    libodbc.so.1			   notification-daemon-1.0
libgfortran.so.3.0.0			    libodbc.so.1.0.0			   notify-osd
libggzcore.so.9				    libofa.so.0				   nss
libggzcore.so.9.0.0			    libofa.so.0.0.0			   ocaml
libggzmod.so.4				    libogg.so.0				   octave
libggzmod.so.4.1.0			    libogg.so.0.5.3			   octave-3.0.1
libggz.so.2				    liboil-0.3.so.0			   odbc
libggz.so.2.3.0				    liboil-0.3.so.0.2.0			   oem-config
libgif.so.4				    liboil-0.3.so.0.3.0			   openais
libgif.so.4.1				    liboobs-1.so.4			   openoffice
libgif.so.4.1.6				    liboobs-1.so.4.0.0			   openssh
libgij.so.81				    libopal.so.2.2			   orbit-2.0
libgij.so.81.0.0			    libopal.so.2.2.11			   pango
libgimp-2.0.so.0			    libopcodes-2.18.0.20080103.so	   pcmciautils
libgimp-2.0.so.0.400.5			    libopcodes-2.19.1.so		   perl
libgimpbase-2.0.so.0			    libopenal.so.0			   perl5
libgimpbase-2.0.so.0.400.5		    libopenal.so.0.0.0			   pidgin
libgimpcolor-2.0.so.0			    libopenobex.so.1			   pkgconfig
libgimpcolor-2.0.so.0.400.5		    libopenobex.so.1.3.0		   pm-utils
libgimpconfig-2.0.so.0			    libopenobex.so.1.5.0		   policykit
libgimpconfig-2.0.so.0.400.5		    libopenspc.so.0			   policykit-gnome
libgimpwidgets-2.0.so.0			    libopenspc.so.0.0.3			   pppd
libgimpwidgets-2.0.so.0.400.5		    libORBit-2.so.0			   ppr
libgio-2.0.a				    libORBit-2.so.0.1.0			   preloadable_libintl.so
libgio-2.0.la				    libORBitCosNaming-2.so.0		   psutils
libgio-2.0.so				    libORBitCosNaming-2.so.0.1.0	   pt_chown
libgio-2.0.so.0				    libORBit-imodule-2.so.0		   pulse-0.9
libgio-2.0.so.0.0.0			    libORBit-imodule-2.so.0.0.0		   pulseaudio
libgio-2.0.so.0.2000.1			    libotr.so.2				   purple-2
libgiomm-2.4.so.1			    libotr.so.2.2.0			   pwlib
libgiomm-2.4.so.1.0.25			    libpanel.a				   python2.3
libgiomm-2.4.so.1.2.0			    libpanel-applet-2.so.0		   python2.4
libgksu					    libpanel-applet-2.so.0.2.34		   python2.5
libgksu2.so.0				    libpanel-applet-2.so.0.2.54		   python2.6
libgksu2.so.0.0.2			    libpanel.so				   python3.0
libglade				    libpanel.so.5			   python-support
libglade-2.0.a				    libpanel.so.5.6			   qt3
libglade-2.0.la				    libpanel.so.5.7			   qt4
libglade-2.0.so				    libpanelw.so.5			   rhythmbox
libglade-2.0.so.0			    libpanelw.so.5.6			   ruby
libglade-2.0.so.0.0.7			    libpanelw.so.5.7			   sane
libGLEW.so.1.5				    libpango-1.0.a			   sasl2
libGLEW.so.1.5.0			    libpango-1.0.la			   scim-1.0
libglib-2.0.a				    libpango-1.0.so			   Scrt1.o
libglib-2.0.la				    libpango-1.0.so.0			   seahorse
libglib-2.0.so				    libpango-1.0.so.0.2002.3		   security
libglib-2.0.so.0			    libpango-1.0.so.0.2400.1		   sgt-puzzles
libglib-2.0.so.0.1600.4			    libpangocairo-1.0.a			   silc
libglib-2.0.so.0.2000.1			    libpangocairo-1.0.la		   sse2
libglibmm-2.4.so.1			    libpangocairo-1.0.so		   ssl
libglibmm-2.4.so.1.0.25			    libpangocairo-1.0.so.0		   sudo
libglibmm-2.4.so.1.2.0			    libpangocairo-1.0.so.0.2002.3	   swfdec-mozilla
libglibmm_generate_extra_defs-2.4.so.1	    libpangocairo-1.0.so.0.2400.1	   system-service
libglibmm_generate_extra_defs-2.4.so.1.2.0  libpangoft2-1.0.a			   tasksel
libglitz-glx.so.1			    libpangoft2-1.0.la			   tc
libglitz-glx.so.1.0.0			    libpangoft2-1.0.so			   thunderbird
libglitz.so.1				    libpangoft2-1.0.so.0		   tomboy
libglitz.so.1.0.0			    libpangoft2-1.0.so.0.2002.3		   totem
libglpk.so.0				    libpangoft2-1.0.so.0.2400.1		   totem-tv
libglpk.so.0.14.0			    libpangomm-1.4.so.1			   ts
libGL.so.1				    libpangomm-1.4.so.1.0.30		   tsclient
libGL.so.1.2				    libpangox-1.0.a			   ubiquity
libGLU.so.1				    libpangox-1.0.la			   udev
libGLU.so.1.3.070002			    libpangox-1.0.so			   update-manager
libGLU.so.1.3.070300			    libpangox-1.0.so.0			   update-notifier
libgmcop.so.1				    libpangox-1.0.so.0.2002.3		   upstart
libgmcop.so.1.0.0			    libpangox-1.0.so.0.2400.1		   ure
libgmime-2.0.so.2			    libpangoxft-1.0.a			   user-setup
libgmime-2.0.so.2.2.22			    libpangoxft-1.0.la			   usplash
libgmodule-2.0.a			    libpangoxft-1.0.so			   valgrind
libgmodule-2.0.la			    libpangoxft-1.0.so.0		   vino
libgmodule-2.0.so			    libpangoxft-1.0.so.0.2400.1		   w3m
libgmodule-2.0.so.0			    libpaper.so.1			   window-picker-applet
libgmodule-2.0.so.0.2000.1		    libpaper.so.1.1.2			   X11
libgmp.so.3				    libpathplan.so.4			   xen
libgmp.so.3.4.4				    libpathplan.so.4.0.0		   xf86-input-evtouch
libgmyth.so.0				    libpcap.so.0.8			   xine
libgmyth.so.0.0.0			    libpcap.so.1.0.0			   xml2Conf.sh
libgnome-2.so.0				    libpciaccess.so.0			   xorg
libgnome-2.so.0.2200.0			    libpciaccess.so.0.10.2		   xscreensaver
libgnome-2.so.0.2600.0			    libpci.so.3				   xulrunner
libgnomecanvas-2.so.0			    libpci.so.3.0.0			   xulrunner-1.9.0.13
libgnomecanvas-2.so.0.2001.0		    libpcreposix.so.3			   xulrunner-addons
libgnomecanvas-2.so.0.2600.0		    libpcreposix.so.3.12.1		   yp
libgnomecups-1.0.so.1			    libperl.so.5.10			   zlibrary
libgnomecups-1.0.so.1.0.0		    libperl.so.5.10.0
libgnome-desktop-2.so.11		    libpisock.so.9


```

I've been trying to find ways around this and come across a few other interesting errors.  For one thing, emacs is broken in the same way.  I successfully did sudo apt-get install usb-imagewriter, but loading it gives me another library error--I can't actually run the program.  Also, gparted does this.

So far, it looks like I can use Firefox, terminal, and Wicd manager.

---

### Post by NoaHall on 2009-09-10
Well, it looks like the other person had KDE? Do you?

run "ls -a /usr/lib/ | grep perl"

---

### Post by karasuman on 2009-09-10
They do not have KDE, but I'm currently not allowed to touch the other laptop and get any version information.  It's running some kind of custom Dell thing, but it's definitely gnome.

```
beth@cheerbear-netbook:~/Desktop$ ls -a /usr/lib/ | grep perl
libperl.so.5.10
libperl.so.5.10.0
libsvn_swig_perl-1.so.1
libsvn_swig_perl-1.so.1.0.0
perl
perl5

```

---

### Post by NoaHall on 2009-09-10
They can have kde and not run it ;) Although their main interface can be gnome. It might just be the stuff they have installed.

Now can you post the result of "ls -a /usr/lib/perl15/auto/Locale/gettext/ | grep gettext"

---

### Post by karasuman on 2009-09-10
Well, I was just sent home for being unable to make the technology work, and disconnecting from campus internet has now left me unable to use the internet, so I'm posting from my laptop.

The output of the above command is

"ls: cannot access /usr/lib/perl15/auto/Locale/gettext/: No such file or directory"

---

### Post by NoaHall on 2009-09-10
Sent home? Seems harsh.

But anyway, I think your best bet is getting the live disk, and then either reinstalling or using the packages from it. Or Live USB, even.

---

### Post by ayenack on 2009-09-10
Gnome/Ubuntu uses some KDE libs.

---

### Post by karasuman on 2009-09-10
Thanks.  I had a feeling things were moving in that direction.  I'm in the process of trying to back things up on my netbook, and then I'm just going to do a clean install.  Thanks again for trying.

---

### Post by NoaHall on 2009-09-10
> **ayenack said:**
> Gnome/Ubuntu uses some KDE libs.

Yeah, but it doesn't often have the KDE games ones installed.

---

### Post by karasuman on 2009-09-10
It's really not even my job to make this stuff work.  I'm supposed to be a GSR in mathematics, not computer science.  He should have had everything up and running the programs he wanted us to use before we even started.  They aren't even fully functional on *his* computer.  

I'm working on dowloading the os so I can make a usb boot.  I solemnly swear that I will never screw around with libraries again, but could someone perhaps explain to me exactly what libraries are and what they're supposed to do?

---

### Post by NoaHall on 2009-09-10
Libaries are files used by several/one program. It's like, you have the main programs, and then you also have have the files they need to load to run.

---

### Post by jimsheep on 2009-09-10
> **NoaHall said:**
> Libaries are files used by several/one program. It's like, you have the main programs, and then you also have have the files they need to load to run.
so could that be analogous to a registry in winblows, or is it more like dynamically linked "program files?"

---

### Post by NoaHall on 2009-09-10
Well, think of it as the .exe in Windows are in /usr/bin/ in Linux. The rest of the files are put in their respective folders. For example, a .dll would be a library on Linux (in a sense.), a .dll is stored in either the program folder(if it's unique) and then the rest under the Windows/System folder. Linux, being open source, uses a lot more shared libraries, as several app builders can access them and therefore use them to develop apps.

Linux has no registry - but ldconfig makes sure that everything is linked up, ready to be loaded by a app.

---

### Post by RJARRRPCGP on 2009-09-10
Sounds like you must prepare to reformat and reinstall, thus doing a clean install. Sorry. :(

---

### Post by directhex on 2009-09-10
> **RJARRRPCGP said:**
> Sounds like you must prepare to reformat and reinstall, thus doing a clean install. Sorry. :(

This is probably the easiest solution - you'll sink many more hours into trying to fix this manually if you're not very well versed in dpkg and and ld

---

