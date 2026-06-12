---
title: "Movie player dosen't work anymore"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-03
I've installed the PPA for openshot video editor ([http://www.openshotvideo.com/2008/04/ppa-instructions.html](http://www.openshotvideo.com/2008/04/ppa-instructions.html)), and now movie player dosen't work, here is the console output when i installed open shot
```
jamie@jamie-kubuntu:~$ sudo apt-get install openshot                           
Reading package lists... Done                                                  
Building dependency tree                                                       
Reading state information... Done                                              
The following extra packages will be installed:                                
  frei0r-plugins libavcodec-extra-52 libavformat-extra-52 libavutil-extra-50   
  libcv1 libcvaux1 libdirac0c2a libgavl1 libgoocanvas-common libgoocanvas3     
  libhighgui1 libmlt++2 libmlt-data libmlt1 libmp3lame0 libopenjpeg2           
  libquicktime1 libsox-fmt-alsa libsox-fmt-base libsox1a libswscale-extra-0    
  libx264-76 libxvidcore4 python-mlt python-pygoocanvas                        
Suggested packages:                                                            
  libsox-fmt-all openshot-doc                                                  
The following packages will be REMOVED                                         
  libavcodec52 libavformat52 libswscale0                                       
The following NEW packages will be installed                                   
  frei0r-plugins libavcodec-extra-52 libavformat-extra-52 libavutil-extra-50   
  libcv1 libcvaux1 libdirac0c2a libgavl1 libgoocanvas-common libgoocanvas3     
  libhighgui1 libmlt++2 libmlt-data libmlt1 libmp3lame0 libopenjpeg2           
  libquicktime1 libsox-fmt-alsa libsox-fmt-base libsox1a libswscale-extra-0    
  libx264-76 libxvidcore4 openshot python-mlt python-pygoocanvas               
0 upgraded, 26 newly installed, 3 to remove and 5 not upgraded.                
Need to get 20.7MB of archives.                                                
After this operation, 38.6MB of additional disk space will be used.            
Do you want to continue [Y/n]? y                                               
Get: 1 http://gb.archive.ubuntu.com karmic/universe libdirac0c2a 1.0.2-0ubuntu1 [410kB]                                                                         
Get: 2 http://ppa.launchpad.net karmic/main libavutil-extra-50 4:0.5+svn20090926-0ubuntu3~tj~ppa1k [100kB]                                                      
Get: 3 http://ppa.launchpad.net karmic/main libx264-76 1:076+git031e25d8cc-0ubuntu1~tj~ppa1k [272kB]                                                            
Get: 4 http://gb.archive.ubuntu.com karmic/multiverse libmp3lame0 3.98.2+debian-0ubuntu1 [254kB]                                                                
Get: 5 http://ppa.launchpad.net karmic/main libavcodec-extra-52 4:0.5+svn20090926-0ubuntu3~tj~ppa1k [4,625kB]                                                   
Get: 6 http://gb.archive.ubuntu.com karmic/universe libopenjpeg2 1.3+dfsg-4 [79.3kB]                                                                            
Get: 7 http://gb.archive.ubuntu.com karmic/multiverse libxvidcore4 2:1.1.2-0.1ubuntu4 [217kB]                                                                   
Get: 8 http://gb.archive.ubuntu.com karmic/universe libcv1 1.0.0-6.2ubuntu1 [1,001kB]                                                                           
Get: 9 http://gb.archive.ubuntu.com karmic/universe libcvaux1 1.0.0-6.2ubuntu1 [314kB]                                                                          
Get: 10 http://gb.archive.ubuntu.com karmic/universe libgavl1 1.1.0-2 [3,367kB] 
Get: 11 http://ppa.launchpad.net karmic/main libavformat-extra-52 4:0.5+svn20090926-0ubuntu3~tj~ppa1k [818kB]                                                   
Get: 12 http://gb.archive.ubuntu.com karmic/universe libhighgui1 1.0.0-6.2ubuntu1 [108kB]                                                                       
Get: 13 http://gb.archive.ubuntu.com karmic/main libgoocanvas-common 0.15-0ubuntu1 [20.6kB]                                                                     
Get: 14 http://gb.archive.ubuntu.com karmic/main libgoocanvas3 0.15-0ubuntu1 [108kB]                                                                            
Get: 15 http://ppa.launchpad.net karmic/main libswscale-extra-0 4:0.5+svn20090926-0ubuntu3~tj~ppa1k [206kB]                                                     
Get: 16 http://gb.archive.ubuntu.com karmic/universe libquicktime1 2:1.1.1+debian-1build1 [317kB]                                                               
Get: 17 http://ppa.launchpad.net karmic/main frei0r-plugins 1.1.22git20090914-0ubuntu1~tj~ppa1k [267kB]                                                         
Get: 18 http://gb.archive.ubuntu.com karmic/universe libsox1a 14.3.0-1build1 [262kB]                                                                            
Get: 19 http://ppa.launchpad.net karmic/main libmlt1 0.4.4+git20090927-0ubuntu3~tj~ppa1k [455kB]                                                                
Get: 20 http://gb.archive.ubuntu.com karmic/universe libsox-fmt-alsa 14.3.0-1build1 [7,566B]                                                                    
Get: 21 http://gb.archive.ubuntu.com karmic/universe libsox-fmt-base 14.3.0-1build1 [37.2kB]                                                                    
Get: 22 http://gb.archive.ubuntu.com karmic/universe python-pygoocanvas 0.14.1-0ubuntu1 [146kB]                                                                 
Get: 23 http://ppa.launchpad.net karmic/main libmlt++2 0.4.4+git20090927-0ubuntu3~tj~ppa1k [41.8kB]                                                             
Get: 24 http://ppa.launchpad.net karmic/main libmlt-data 0.4.4+git20090927-0ubuntu3~tj~ppa1k [1,394kB]                                                          
Get: 25 http://ppa.launchpad.net karmic/main python-mlt 0.4.4+git20090927-0ubuntu3~tj~ppa1k [371kB]                                                             
Get: 26 http://ppa.launchpad.net karmic/main openshot 0.9.43-0ubuntu3~ppa1k [5,491kB]                                                                           
Fetched 20.7MB in 35s (584kB/s)                                                 
dpkg: libswscale0: dependency problems, but removing anyway as you requested:   
 gstreamer0.10-ffmpeg depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however:                                       
  Package libswscale0 is to be removed.                                         
  Package libswscale-extra-0 is not installed.                                  
(Reading database ... 135186 files and directories currently installed.)        
Removing libswscale0 ...                                                        
dpkg: libavformat52: dependency problems, but removing anyway as you requested: 
 gstreamer0.10-ffmpeg depends on libavformat52 (>= 3:0.svn20090303-1) | libavformat-extra-52 (>= 3:0.svn20090303-1); however:                                   
  Package libavformat52 is to be removed.                                       
  Package libavformat-extra-52 is not installed.                                
Removing libavformat52 ...                                                      
dpkg: libavcodec52: dependency problems, but removing anyway as you requested:  
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:                                     
  Package libavcodec52 is to be removed.                                        
  Package libavcodec-extra-52 is not installed.                                 
Removing libavcodec52 ...                                                       
Processing triggers for libc-bin ...                                            
ldconfig deferred processing now taking place                                   
Selecting previously deselected package libavutil-extra-50.                     
(Reading database ... 135147 files and directories currently installed.)        
Unpacking libavutil-extra-50 (from .../libavutil-extra-50_4%3a0.5+svn20090926-0ubuntu3~tj~ppa1k_i386.deb) ...                                                   
Selecting previously deselected package libdirac0c2a.                           
Unpacking libdirac0c2a (from .../libdirac0c2a_1.0.2-0ubuntu1_i386.deb) ...      
Selecting previously deselected package libmp3lame0.                            
Unpacking libmp3lame0 (from .../libmp3lame0_3.98.2+debian-0ubuntu1_i386.deb) ...
Selecting previously deselected package libopenjpeg2.                           
Unpacking libopenjpeg2 (from .../libopenjpeg2_1.3+dfsg-4_i386.deb) ...          
Selecting previously deselected package libx264-76.                             
Unpacking libx264-76 (from .../libx264-76_1%3a076+git031e25d8cc-0ubuntu1~tj~ppa1k_i386.deb) ...                                                                 
Selecting previously deselected package libxvidcore4.                           
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.1.2-0.1ubuntu4_i386.deb) ...
Selecting previously deselected package libavcodec-extra-52.                    
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5+svn20090926-0ubuntu3~tj~ppa1k_i386.deb) ...                                                 
Selecting previously deselected package libavformat-extra-52.                   
Unpacking libavformat-extra-52 (from .../libavformat-extra-52_4%3a0.5+svn20090926-0ubuntu3~tj~ppa1k_i386.deb) ...                                               
Selecting previously deselected package libswscale-extra-0.                     
Unpacking libswscale-extra-0 (from .../libswscale-extra-0_4%3a0.5+svn20090926-0ubuntu3~tj~ppa1k_i386.deb) ...                                                   
Selecting previously deselected package libcv1.                                 
Unpacking libcv1 (from .../libcv1_1.0.0-6.2ubuntu1_i386.deb) ...                
Selecting previously deselected package libcvaux1.                              
Unpacking libcvaux1 (from .../libcvaux1_1.0.0-6.2ubuntu1_i386.deb) ...          
Selecting previously deselected package libgavl1.                               
Unpacking libgavl1 (from .../libgavl1_1.1.0-2_i386.deb) ...                     
Selecting previously deselected package libhighgui1.                            
Unpacking libhighgui1 (from .../libhighgui1_1.0.0-6.2ubuntu1_i386.deb) ...      
Selecting previously deselected package frei0r-plugins.                         
Unpacking frei0r-plugins (from .../frei0r-plugins_1.1.22git20090914-0ubuntu1~tj~ppa1k_i386.deb) ...                                                             
Selecting previously deselected package libgoocanvas-common.                    
Unpacking libgoocanvas-common (from .../libgoocanvas-common_0.15-0ubuntu1_all.deb) ...                                                                          
Selecting previously deselected package libgoocanvas3.                          
Unpacking libgoocanvas3 (from .../libgoocanvas3_0.15-0ubuntu1_i386.deb) ...     
Selecting previously deselected package libquicktime1.                          
Unpacking libquicktime1 (from .../libquicktime1_2%3a1.1.1+debian-1build1_i386.deb) ...                                                                          
Selecting previously deselected package libsox1a.                               
Unpacking libsox1a (from .../libsox1a_14.3.0-1build1_i386.deb) ...              
Selecting previously deselected package libmlt1.                                
Unpacking libmlt1 (from .../libmlt1_0.4.4+git20090927-0ubuntu3~tj~ppa1k_i386.deb) ...                                                                           
Selecting previously deselected package libmlt++2.                              
Unpacking libmlt++2 (from .../libmlt++2_0.4.4+git20090927-0ubuntu3~tj~ppa1k_i386.deb) ...                                                                       
Selecting previously deselected package libmlt-data.                            
Unpacking libmlt-data (from .../libmlt-data_0.4.4+git20090927-0ubuntu3~tj~ppa1k_all.deb) ...                                                                    
Selecting previously deselected package libsox-fmt-alsa.                        
Unpacking libsox-fmt-alsa (from .../libsox-fmt-alsa_14.3.0-1build1_i386.deb) ...
Selecting previously deselected package libsox-fmt-base.                        
Unpacking libsox-fmt-base (from .../libsox-fmt-base_14.3.0-1build1_i386.deb) ...
Selecting previously deselected package python-mlt.                             
Unpacking python-mlt (from .../python-mlt_0.4.4+git20090927-0ubuntu3~tj~ppa1k_i386.deb) ...                                                                     
Selecting previously deselected package python-pygoocanvas.                     
Unpacking python-pygoocanvas (from .../python-pygoocanvas_0.14.1-0ubuntu1_i386.deb) ...                                                                         
Selecting previously deselected package openshot.                               
Unpacking openshot (from .../openshot_0.9.43-0ubuntu3~ppa1k_all.deb) ...        
Processing triggers for software-center ...                                     
Processing triggers for packagekit-backend-apt ...                              
Generating mime/codec maps...                                                   
Processing triggers for shared-mime-info ...                                    
Unknown media type in type 'all/all'                                            

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libavutil-extra-50 (4:0.5+svn20090926-0ubuntu3~tj~ppa1k) ...

Setting up libdirac0c2a (1.0.2-0ubuntu1) ...

Setting up libmp3lame0 (3.98.2+debian-0ubuntu1) ...

Setting up libopenjpeg2 (1.3+dfsg-4) ...

Setting up libx264-76 (1:076+git031e25d8cc-0ubuntu1~tj~ppa1k) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...

Setting up libavcodec-extra-52 (4:0.5+svn20090926-0ubuntu3~tj~ppa1k) ...

Setting up libavformat-extra-52 (4:0.5+svn20090926-0ubuntu3~tj~ppa1k) ...

Setting up libswscale-extra-0 (4:0.5+svn20090926-0ubuntu3~tj~ppa1k) ...

Setting up libcv1 (1.0.0-6.2ubuntu1) ...

Setting up libcvaux1 (1.0.0-6.2ubuntu1) ...

Setting up libgavl1 (1.1.0-2) ...

Setting up libhighgui1 (1.0.0-6.2ubuntu1) ...

Setting up frei0r-plugins (1.1.22git20090914-0ubuntu1~tj~ppa1k) ...
Setting up libgoocanvas-common (0.15-0ubuntu1) ...
Setting up libgoocanvas3 (0.15-0ubuntu1) ...

Setting up libquicktime1 (2:1.1.1+debian-1build1) ...

Setting up libsox1a (14.3.0-1build1) ...

Setting up libmlt1 (0.4.4+git20090927-0ubuntu3~tj~ppa1k) ...

Setting up libmlt++2 (0.4.4+git20090927-0ubuntu3~tj~ppa1k) ...

Setting up libmlt-data (0.4.4+git20090927-0ubuntu3~tj~ppa1k) ...
Setting up libsox-fmt-alsa (14.3.0-1build1) ...
Setting up libsox-fmt-base (14.3.0-1build1) ...
Setting up python-mlt (0.4.4+git20090927-0ubuntu3~tj~ppa1k) ...

Setting up python-pygoocanvas (0.14.1-0ubuntu1) ...

Setting up openshot (0.9.43-0ubuntu3~ppa1k) ...
Update the Add/Remove... list
Caching application data...
Generating mime/codec maps...
Update XDG application registrations

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
jamie@jamie-kubuntu:~$

```


The dependencies open shot requires are:
FFmpeg, MLT, Frei0r, and x264

On another forum i saw this post:> vlc -vvv --no-plugins-cache --list |grep avcodec.

Most likely you installed some new libavcodec libraries from a PPA which are not compatible. But i don't know what to do with this information.

---

### Post by darkxman on 2009-10-03
This worked for me.

> **mc4man said:**
> easiest way is first make sure the ppa isn't in your sources anymore.

Then search ffmpeg in synaptic and mark for removal any or all of the libs
(libavcodecXX, libavformatXX, ect. and ffmpeg itself if the ppa version.
(scroll down to ck them all, last one would be libswscale0 ( using X's cause not sure what version #'s you have in jaunty, 52, 51 ect.

You'll lose vlc and some plugins, but they can be re-installed

After removing, then install the "unstripped" versions of the same lib's you just removed, and vlc, plugins ect.

You're the 3rd or 4th person in the last day with same problem - those openshot ppa ffmpeg and  libs are junk if you want to use media players

edit
if vlc gives you any trouble afterwards then start with this to reset
```

vlc --reset-config --reset-plugins-cache
```

---

### Post by Falc7 on 2009-10-03
Thanks that worked :) is there no way to have open shot installed, and totem media player working on the same machine?

---

