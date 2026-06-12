---
title: "A few things to do after installing Ubuntu"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by josephmills on 2011-03-18
I would like to know what you do after you install ubuntu. Here is a list of things that I do if you see anything else that needs to be done to make ubuntu more user friendly please post 
0) install ubuntu 
1) upgrade 
2) Update 
3) look for additional drivers 
4) Install compiz and simple compiz settings 
5) put on library so I can watch dvd's 
6) install vlc 
7) install firewall and clam
8) install flash player 
9) install cairo dock and screenlets
10) install opera
11) Install virtual box and guest-add-ons 
12) install Gimp
13) Install google chrome 
14)  install eSpeak 
15) set up evolution email 
Like I said above if you can think of anything else to make ubuntu more user friendly then please post or if you see something on my list that could be updated please post. At any-rate I look forward to hearing what you have to say! Thanks

---

### Post by mikewhatever on 2011-03-18
Hm..., which of the above makes Ubuntu more user friendly?

---

### Post by garvinrick4 on 2011-03-18
First thing is to make sure all your repositories are installed in Software Sources.
Then:
```
sudo apt-get install ubuntu-restricted-extras aptitude libdvdcss2 gparted && sudo apt-get update && sudo apt-get upgrade
``````
rick@rick-HP:~$ aptitude show ubuntu-restricted-extras
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

rick@rick-HP:~$ aptitude show libdvdcss2
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

rick@rick-HP:~$ aptitude show aptitude
Package: aptitude                        
State: installed
Automatically installed: no
Version: 0.6.3-3.2ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 7,348 k
Depends: libapt-pkg4.10, libboost-iostreams1.42.0 (>= 1.42.0-1), libc6 (>= 2.4),
         libcwidget3, libept1, libgcc1 (>= 1:4.1.1), libncursesw5 (>=
         5.7+20100313), libsigc++-2.0-0c2a (>= 2.0.2), libsqlite3-0 (>= 3.7.3),
         libstdc++6 (>= 4.5), libxapian22
Recommends: sensible-utils, apt-xapian-index, libparse-debianchangelog-perl
Suggests: aptitude-doc-en | aptitude-doc, tasksel, debtags
Conflicts: ia32-apt-get (< 22)
Description: terminal-based package manager (terminal interface only)
 aptitude is a package manager with a number of useful features, including: a
 mutt-like syntax for matching packages in a flexible manner, dselect-like
 persistence of user actions, the ability to retrieve and display the Debian
 changelog of most packages, and a command-line mode similar to that of apt-get.
 
 aptitude is also Y2K-compliant, non-fattening, naturally cleansing, and
 housebroken. 
 
 This package contains a version of aptitude compiled with only the classic
 terminal-based interface (using curses).  For an experimental graphical
 interface, see the package aptitude-gtk.

rick@rick-HP:~$ aptitude show gparted
Package: gparted                         
State: installed
Automatically installed: no
Version: 0.7.0-1ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,708 k
Depends: libatkmm-1.6-1 (>= 2.22.0), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1),
         libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.27.94), libgtk2.0-0
         (>= 2.14.0), libgtkmm-2.4-1c2a (>= 1:2.24.0), libpangomm-1.4-1 (>=
         2.27.1), libparted0debian1 (>= 2.2-1), libsigc++-2.0-0c2a (>= 2.0.2),
         libstdc++6 (>= 4.5)
Recommends: gksu
Suggests: xfsprogs, reiserfsprogs, reiser4progs, jfsutils, ntfsprogs,
          dosfstools, yelp, kpartx, dmraid, dmsetup
Description: GNOME partition editor
 GParted uses libparted to detect and manipulate devices and partition tables
 while several (optional) filesystem tools provide support for filesystems not
 included in libparted.
Homepage: http://gparted.sourceforge.net

rick@rick-HP:~$ 

```This will give you a good start you can read what each package gives you.
Also what repository package is in that you need to open in Software Sources.

---

### Post by adduds on 2011-03-18
> **garvinrick4 said:**
> First thing is to make sure all your repositories are installed in Software Sources.
Then:
```
sudo apt-get install ubuntu-restricted-extras aptitude libdvdcss2 gparted && sudo apt-get update && sudo apt-get upgrade
``````
rick@rick-HP:~$ aptitude show ubuntu-restricted-extras
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

rick@rick-HP:~$ aptitude show libdvdcss2
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

rick@rick-HP:~$ aptitude show aptitude
Package: aptitude                        
State: installed
Automatically installed: no
Version: 0.6.3-3.2ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 7,348 k
Depends: libapt-pkg4.10, libboost-iostreams1.42.0 (>= 1.42.0-1), libc6 (>= 2.4),
         libcwidget3, libept1, libgcc1 (>= 1:4.1.1), libncursesw5 (>=
         5.7+20100313), libsigc++-2.0-0c2a (>= 2.0.2), libsqlite3-0 (>= 3.7.3),
         libstdc++6 (>= 4.5), libxapian22
Recommends: sensible-utils, apt-xapian-index, libparse-debianchangelog-perl
Suggests: aptitude-doc-en | aptitude-doc, tasksel, debtags
Conflicts: ia32-apt-get (< 22)
Description: terminal-based package manager (terminal interface only)
 aptitude is a package manager with a number of useful features, including: a
 mutt-like syntax for matching packages in a flexible manner, dselect-like
 persistence of user actions, the ability to retrieve and display the Debian
 changelog of most packages, and a command-line mode similar to that of apt-get.
 
 aptitude is also Y2K-compliant, non-fattening, naturally cleansing, and
 housebroken. 
 
 This package contains a version of aptitude compiled with only the classic
 terminal-based interface (using curses).  For an experimental graphical
 interface, see the package aptitude-gtk.

rick@rick-HP:~$ aptitude show gparted
Package: gparted                         
State: installed
Automatically installed: no
Version: 0.7.0-1ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,708 k
Depends: libatkmm-1.6-1 (>= 2.22.0), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1),
         libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.27.94), libgtk2.0-0
         (>= 2.14.0), libgtkmm-2.4-1c2a (>= 1:2.24.0), libpangomm-1.4-1 (>=
         2.27.1), libparted0debian1 (>= 2.2-1), libsigc++-2.0-0c2a (>= 2.0.2),
         libstdc++6 (>= 4.5)
Recommends: gksu
Suggests: xfsprogs, reiserfsprogs, reiser4progs, jfsutils, ntfsprogs,
          dosfstools, yelp, kpartx, dmraid, dmsetup
Description: GNOME partition editor
 GParted uses libparted to detect and manipulate devices and partition tables
 while several (optional) filesystem tools provide support for filesystems not
 included in libparted.
Homepage: http://gparted.sourceforge.net

rick@rick-HP:~$ 

```This will give you a good start you can read what each package gives you.
Also what repository package is in that you need to open in Software Sources.

buddy that's a massive- post thanks :) helps!
 EDIT:

more so on the aptitude post :) that's a savvy tool!

---

### Post by mikewhatever on 2011-03-18
No, josephmills, I won't waist any more of your time.

---

### Post by josephmills on 2011-03-18
> **garvinrick4 said:**
> First thing is to make sure all your repositories are installed in Software Sources.
Then:
```
sudo apt-get install ubuntu-restricted-extras aptitude libdvdcss2 gparted && sudo apt-get update && sudo apt-get upgrade
``````
rick@rick-HP:~$ aptitude show ubuntu-restricted-extras
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

rick@rick-HP:~$ aptitude show libdvdcss2
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

rick@rick-HP:~$ aptitude show aptitude
Package: aptitude                        
State: installed
Automatically installed: no
Version: 0.6.3-3.2ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 7,348 k
Depends: libapt-pkg4.10, libboost-iostreams1.42.0 (>= 1.42.0-1), libc6 (>= 2.4),
         libcwidget3, libept1, libgcc1 (>= 1:4.1.1), libncursesw5 (>=
         5.7+20100313), libsigc++-2.0-0c2a (>= 2.0.2), libsqlite3-0 (>= 3.7.3),
         libstdc++6 (>= 4.5), libxapian22
Recommends: sensible-utils, apt-xapian-index, libparse-debianchangelog-perl
Suggests: aptitude-doc-en | aptitude-doc, tasksel, debtags
Conflicts: ia32-apt-get (< 22)
Description: terminal-based package manager (terminal interface only)
 aptitude is a package manager with a number of useful features, including: a
 mutt-like syntax for matching packages in a flexible manner, dselect-like
 persistence of user actions, the ability to retrieve and display the Debian
 changelog of most packages, and a command-line mode similar to that of apt-get.
 
 aptitude is also Y2K-compliant, non-fattening, naturally cleansing, and
 housebroken. 
 
 This package contains a version of aptitude compiled with only the classic
 terminal-based interface (using curses).  For an experimental graphical
 interface, see the package aptitude-gtk.

rick@rick-HP:~$ aptitude show gparted
Package: gparted                         
State: installed
Automatically installed: no
Version: 0.7.0-1ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,708 k
Depends: libatkmm-1.6-1 (>= 2.22.0), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1),
         libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.27.94), libgtk2.0-0
         (>= 2.14.0), libgtkmm-2.4-1c2a (>= 1:2.24.0), libpangomm-1.4-1 (>=
         2.27.1), libparted0debian1 (>= 2.2-1), libsigc++-2.0-0c2a (>= 2.0.2),
         libstdc++6 (>= 4.5)
Recommends: gksu
Suggests: xfsprogs, reiserfsprogs, reiser4progs, jfsutils, ntfsprogs,
          dosfstools, yelp, kpartx, dmraid, dmsetup
Description: GNOME partition editor
 GParted uses libparted to detect and manipulate devices and partition tables
 while several (optional) filesystem tools provide support for filesystems not
 included in libparted.
Homepage: http://gparted.sourceforge.net

rick@rick-HP:~$ 

```This will give you a good start you can read what each package gives you.
Also what repository package is in that you need to open in Software Sources.

thanks Rick you :guitar:

---

### Post by wormyblackburny on 2011-03-18
Ubuntu-Tweak install. 
+1 on flash, DVD codecs, and chrome
I generally blow away open-java and install sun-java and plugins
Dockbar-x and compiz configuration
Gnomenu
MSfonts
Wine and playonlinux
VMWare workstation (i get free license through my school, otherwise it would be V-box)

---

### Post by josephmills on 2011-03-18
oh I forgot about . rar ark and 7zip

---

### Post by wormyblackburny on 2011-03-18
If you are trying to convert people, create a build with everything you need and use remastersys to make a custom iso to install when you do. Will save you a ton of time....

---

### Post by matt_symes on 2011-03-18
Hi

Why don't you create a distro using remastersys and just install that each time. Then you only need to create one base line.

BTW: I don't think mike was trying to offend you.

EDIT: Beaten to it.

Kind regards

---

### Post by josephmills on 2011-03-18
> **wormyblackburny said:**
> If you are trying to convert people, create a build with everything you need and use remastersys to make a custom iso to install when you do. Will save you a ton of time....
oh my this is a great idea thanks you so much

---

### Post by adduds on 2011-03-18
> **matt_symes said:**
> Hi

Why don't you create a distro using remastersys and just install that each time. Then you only need to create one base line.


+1

wormyblackburny how do you get rid of open java and install sun-java?

---

### Post by GrouchyGaijin on 2011-03-18
> **adduds said:**
> you should be a more respectful....especially to someone who's been on the forums for 5 years, has 10,000 posts, and is respected in on the forums, you're new here....be a little more friendly things will work better for you

I had the same thought.

---

### Post by GrouchyGaijin on 2011-03-18
> **matt_symes said:**
> Hi

Why don't you create a distro using remastersys and just install that each time. Then you only need to create one base line.


Where is remastersys? I don't see it in a menu, the terminal tells me the command is not recognized and I couldn't find it in synaptic.

---

### Post by matt_symes on 2011-03-18
Hi

> Where is remastersys? I don't see it in a menu, the terminal tells me the command is not recognized and I couldn't find it in synaptic

[http://ubuntuforums.org/showthread.php?t=1468782](http://ubuntuforums.org/showthread.php?t=1468782)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Kind regards

---

### Post by josephmills on 2011-03-18
> **mikewhatever said:**
> Hm..., which of the above makes Ubuntu more user friendly?

After thinking about this for a while I am still at a loss are you trying to say that ubuntu is not user friendly or why did you post this? at any rate I dont listen to blind faith even if you have "been around the block" there is always something more that you can learn and what am i going to learn from this? I dont want to offend anyone but what is this. 

I am just saying that just because you have been around the block dosent mean that you have to post things like this. and that I have to listen and not speak my mind. I am sorry that I used cuz words and I would still like to thank everyone that has posted yes even you mike. So with that being said thanks you  all

---

### Post by matt_symes on 2011-03-18
Hi

> Hm..., which of the above makes Ubuntu more user friendly?

I think he was suggesting Ubuntu is user friendly no matter what extra you add to it. (The emphasis on the word 'more' in the quote above)

That's the impression i got when i first read the quote.

Kind regards

---

### Post by josephmills on 2011-03-18
> **matt_symes said:**
> Hi



I think he was suggesting Ubuntu is user friendly no matter what extra you add to it. (The emphasis on the word 'more' in the quote above)

That's the impression i got when i first read the quote.

Kind regards

Cool I can see where you are coming from. I am saying that ubuntu is not that user friendly. I love linux/unix and I know that there are laws out there that stop people from having there freedoms. I am still wondering what else people put on there Ubuntu and I am making a iso as listed above and would like things to work out the box for my clients so if you can think of anything else that needs to be added please post you all are great thanks

---

### Post by SeijiSensei on 2011-03-18
> **josephmills said:**
> I am making a iso as listed above and would like things to work out the box for my clients so if you can think of anything else that needs to be added please post you all are great thanks

Are you selling these clients systems with the items you listed pre-installed?  I think you better go read the VirtualBox license again, especially as it pertains to the proprietary extensions.  I think you'll discover you have no license to redistribute that software for commercial purposes.

Next, if you live the US, distributing systems commercially that include things like libdvdcss2 are in violation of the Digital Millenium Copyright Act.  They are forbidden to be distributed in the US because they run afoul of the "anti-circumvention" provisions of that law.  You don't really think Ubuntu creates a "restricted-extras" repository just to confuse its users, do you?  There a legal reasons why Canonical can't ship things like libdvdcss2, or anything related to MP3 or H.264 for that matter, because these are all encumbered by patents or restricted by the DMCA.

Not everything that is "open source" can be freely redistributed.  Talk to your attorney about what you can and cannot redistribute legally to clients in your country.

---

### Post by josephmills on 2011-03-18
> **SeijiSensei said:**
> Are you selling these clients systems with the items you listed pre-installed?  no I am not > I think you better go read the VirtualBox license again, especially as it pertains to the proprietary extensions.  I think you'll discover you have no license to redistribute that software for commercial purposes.
yes I have re-read that and thank you I am not a big time shop very small.and Yes I have the client with me and yes I help them install some things (suns vbox) > 
Next, if you live the US, distributing systems commercially that include things like libdvdcss2 are in violation of the Digital Millenium Copyright Act.  They are forbidden to be distributed in the US because they run afoul of the "anti-circumvention" provisions of that law.  You don't really think Ubuntu creates a "restricted-extras" repository just to confuse its users, do you?  NO 4 freedoms >  There a legal reasons why Canonical can't ship things like libdvdcss2, or anything related to MP3 or H.264 for that matter, because these are all encumbered by patents or restricted by the DMCA.

Not everything that is "open source" can be freely redistributed.  Talk to your attorney about what you can and cannot redistribute legally to clients in your country.

thanks you so much this is why I posted this there is alot to learn out there and there are some real smart people here.

---

### Post by dFlyer on 2011-03-18
I add the following programs:

Ubuntu-restricted-extra
Gimp
UFRAW
Bibble5Pro
Lightzone3.9
GRAMPS
Tali
Frozen Bubble
PokerTH
gLabels
GNUCash
HPLIP Toolbox
Google Picasa
Xiphos Bible
Skype
Sun Java
Adobe Reader

---

### Post by josephmills on 2011-03-18
Ok so after thinking this over I think that it would be best if I just don't offer ubuntu at all. My clients think that it is confusing and I have been getting alot of complaints. Its a bummer I would love to offer a better product then windoz/osx. but with all the laws here in the usa I guess that it is a bad idea. maybe I will just offer gnewsence or something like that. But that it not going to go over with 90% of my clients. So that is not going to work either. I hate to say it but I guess 7 is the way to go. :(  if anyone can think of a way to help with this i would love to here from you. For right now I just got a-lot more busy because I have to go take ubuntu of 50 or so computers what a bummer

---

### Post by josephmills on 2011-03-18
> **dFlyer said:**
> I add the following programs:

Ubuntu-restricted-extra
Gimp
UFRAW
Bibble5Pro
Lightzone3.9
GRAMPS
Tali
Frozen Bubble
PokerTH
gLabels
GNUCash
HPLIP Toolbox
Google Picasa
Xiphos Bible
Skype
Sun Java
Adobe Reader

this is a great list thank you so much some of the things on here I had never heard of so once again thanks for you input

---

