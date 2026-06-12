---
title: "dvd burns with brasero but computer still says it's blank"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by emwall on 2011-04-03
Hi!  I am trying to burn avi movie files to DVD discs on my laptop using Brasero.  It burns the data DVD fine but my computer still says the disc is blank.  I put it in my regular DVD player and it plays fine.  Tried again in the computer and it still says it is blank.  Any ideas why and what I can do to solve this?  Thanks!

---

### Post by garvinrick4 on 2011-04-03
I would say you do not have codecs installed to play DVD's on your Ubuntu box.
Try installing this just to be sure: Make sure your repositorys are open in "software sources"
```
sudo apt-get install ubuntu-restricted-extras 
```To play most DVD's will need to install medibuntu repository and key. 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then:
```
sudo apt-get install libdvdcss2
``````
Package: ubuntu-restricted-extras        
State: installed
Automatically installed: no
Version: 43
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 36.9 k
Depends: ubuntu-restricted-addons
Recommends: gstreamer0.10-plugins-ugly-multiverse, ttf-mscorefonts-installer,
            unrar, gstreamer0.10-plugins-bad-multiverse, libavcodec-extra-52,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See http://www.ubuntu.com/ubuntu/licensing for
 more information.
``````
Package: libdvdcss2                      
State: installed
Automatically installed: no
Version: 1.2.10-0.3medibuntu1
Priority: optional
Section: free/libs
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Uncompressed Size: 111 k
Depends: libc6 (>= 2.7)
Replaces: libdvdcss-dev (<= 0.0.3-3), libdvdcss0 (<= 1.0.0-0.0), libdvdcss2-dev
          (<= 1.2.10-0.0)
Provides: libdvdcss
Description: Simple foundation for reading DVDs - runtime libraries
 To allow applications to access some of the more advanced features of the DVD
 format.
Homepage: http://download.videolan.org/


```

---

### Post by emwall on 2011-04-04
Ok, I installed everything you suggested but my computer still says the dvd is blank.  My laptop plays most dvds I put in including dvd's I have burned using a friends EZDUB burner.  It is only the dvds that I am burning with my computer that are not working.  Any more ideas?

---

### Post by garvinrick4 on 2011-04-05
> Hi!  I am trying to burn avi movie files to DVD discs on my laptop using Brasero.Seems not all home optical drives can read .avi because of its compression: 
Link below shows it has to be converted first: Hope this helps you out.
[http://tips4pc.com/articles/dvd%20movie/conver t_your_avi_movie_file_to_d.htm]("http://tips4pc.com/articles/dvd%20movie/convert_your_avi_movie_file_to_d.htm")

---

