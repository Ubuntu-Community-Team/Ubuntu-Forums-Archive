---
title: "Install local packages using synaptic"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-06-18
hello
I wonder if i can install packages that already exist in local directory using synaptic
for example:

I downloaded a set of programs with there dependencies and stored them in whatever folder, and i'd reinstalled my distro and i need to install just google chrome browser for instance, it's will be very difficult to install it among other packages.

it will be very useful if i forced synaptic to install chrome locally instead of downloading and installing them from the internet.

if some one tell me how to accomplish these approach i will be very grateful to him
Thank you in advance

mahmoud

---

### Post by mc4man on 2010-06-18
> if i can install packages that already exist in local directory using synaptic
Not really..

You can use dpkg to do so if you meet certain conditions -
Ex.
I take package 'A' and any other packages it depends on that I have locally, place them all **in another folder**, cd to that folder and run 
```
sudo dpkg -i *.deb
```

If all other dependencies are already installed, (if any), then the install will succeed, if something is missing then broken packages will result. (not always the worst thing, can usually be fixed in synaptic.

( the same can be achieved by cd'ing to your dir. of local packages and 
sudo dpkg -i package A package B ect.

Again the same as before - if any dep is missing, either in list of local packages to install or already installed then your install will fail

===========================================================================================


A far better way to manage local packages (and have available in synaptic) is to create a local repo and add to your sources list.

(If you've just chrome to install then I'd certainly ignore this

The condition there is they need to be properly made and either not available in your default repos or of a higher version.


I use a local repo in all my installs - atm this is what's in my lucid install
> doug@doug-desktop:~/repo$ ls *.deb
abcde_2.4.2-2_all.deb
faac_1.28-0.3_i386.deb
ffmpeg-doc_0.5+svn21686-1_all.deb
gstreamer0.10-plugins-gl_0.10.1-3_i386.deb
libavcodec52_0.5+svn21686-1_i386.deb
libavcodec-dev_0.5+svn21686-1_i386.deb
libavdevice52_0.5+svn21686-1_i386.deb
libavdevice-dev_0.5+svn21686-1_i386.deb
libavfilter1_0.5+svn21686-1_i386.deb
libavfilter-dev_0.5+svn21686-1_i386.deb
libavformat52_0.5+svn21686-1_i386.deb
libavformat-dev_0.5+svn21686-1_i386.deb
libavutil50_0.5+svn21686-1_i386.deb
libavutil-dev_0.5+svn21686-1_i386.deb
libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
libfaac0_1.28-0.3_i386.deb
libfaac-dev_1.28-0.3_i386.deb
libgstreamer-plugins-gl0.10-0_0.10.1-3_i386.deb
libmediainfo0_0.7.29-1_i386.Ubuntu_9.10.deb
libmp4v2-1_1.9.1-0.1_i386.deb
libpostproc51_0.5+svn21686-1_i386.deb
libpostproc-dev_0.5+svn21686-1_i386.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
libswscale0_0.5+svn21686-1_i386.deb
libswscale-dev_0.5+svn21686-1_i386.deb
libtotem-plparser12_2.28.1-1_i386.deb
libvlc2_1.0.6-2ubuntu2_i386.deb
libvlccore2_1.0.6-2ubuntu2_i386.deb
libxine1_1.1.18-1ubuntu2_i386.deb
libxine1-all-plugins_1.1.18-1ubuntu2_all.deb
libxine1-bin_1.1.18-1ubuntu2_i386.deb
libxine1-console_1.1.18-1ubuntu2_i386.deb
libxine1-dbg_1.1.18-1ubuntu2_i386.deb
libxine1-doc_1.1.18-1ubuntu2_all.deb
libxine1-ffmpeg_1.1.18-1ubuntu2_i386.deb
libxine1-gnome_1.1.18-1ubuntu2_i386.deb
libxine1-misc-plugins_1.1.18-1ubuntu2_i386.deb
libxine1-plugins_1.1.18-1ubuntu2_all.deb
libxine1-x_1.1.18-1ubuntu2_i386.deb
libxine-dev_1.1.18-1ubuntu2_i386.deb
libzen0_0.4.11-1_i386.Ubuntu_9.10.deb
mediainfo_0.7.29-1_i386.Debian_5.deb
mediainfo-gui_0.7.29-1_i386.Debian_5.deb
pana_1.4.16-2_i386.deb
pana-common_1.4.16-2_all.deb
pana-engine-xine_1.4.16-2_i386.deb
pana-engine-yauap_1.4.16-2_i386.deb
rubyripper_0.6b.2_all.deb
smplayer_0.6.9-SVN-r3500_i386.deb
vlc_1.0.6-2ubuntu2_i386.deb
vlc-data_1.0.6-2ubuntu2_all.deb
vlc-nox_1.0.6-2ubuntu2_i386.deb
vlc-plugin-pulse_1.0.6-2ubuntu2_i386.deb
vlc-plugin-sdl_1.0.6-2ubuntu2_i386.deb
w32codecs_20071007-0medibuntu5_i386.deb

And as screen shows they are available for install in synaptic - plus any other deps are auto installed as normal

( not sure this is Ab stuff, if you want to try a local repo say so ( though again you'll need to meet the conditions

---

### Post by requeth on 2010-06-18
If the packages are .deb files you can just click on them and they will open. Alternately you can run gdebi package.deb and the package will install.

In the specific instance of Google Chrome, when Chrome is installed using the .deb a synaptic software source is added to allow for updates through Synaptic. If you want to install Chrome specifically through Synaptic you can add the software source:

Go to System: Administration: Software Sources
Go to Other Software
Add New
Type: Binary
URI: [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/)
Distribution: Stable
Components: Main
Select Ok.
Choose Close.

Go to System: Administration: Synaptic Package Manager
Choose Reload (blue circle arrow in upper left corner)
Search for Google Chrome. It should show up now to be installed.

---

### Post by Paqman on 2010-06-18
> **MBG1987 said:**
> 
it will be very useful if i forced synaptic to install chrome locally instead of downloading and installing them from the internet.


If the most up-to-date copy available is the .deb file is sitting in the local APT cache (var/cache/apt/archives) then that's exactly what it will do. It only downloads a new .deb if the version online is newer.

---

### Post by MBG1987 on 2010-06-18
> 
A far better way to manage local packages (and have available in synaptic) is to create a local repo and add to your sources list.




Awesome that's exactly what i'm searching for, local repo, would you please  show me how to add a local repo 

thank you in advance

---

### Post by mc4man on 2010-06-19
Here's the how-to I base my method on
[http://ubuntuforums.org/showthread.php?t=42862&highlight=local+repo](http://ubuntuforums.org/showthread.php?t=42862&highlight=local+repo)

I laid out the exact way I use on this page - post 39

[http://ubuntuforums.org/showthread.php?t=42862&highlight=local+repo&page=4](http://ubuntuforums.org/showthread.php?t=42862&highlight=local+repo&page=4)

Keep in mind about only adding properly created debian packages and versioning.(generally speaking checkinstall packages can't be used.

Small note - 
packages added will always be available in synaptic and from apt-get.
Thru lucid they will also be installable from the update manager.

Starting in maverick the update manager and software center in any release will not allow installs from a local repo unless you authenticate it.
( a real pita, at least in my attempts...


Overall a local repo can prove very useful - when I redid my lucid it only took a few minutes to restore everything I'd done previously.

---

