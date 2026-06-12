---
title: "Broken Package"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Jonathan E-D on 2009-03-16
Sorry, I'am an absolute beginner.  My first thread was apparently incorrectly saved so I'm sending another.  I wanted to view my videos and so, as instructed performed the Sudo apt-get install ubuntu-restricted-extras routine.  I was stopped by JAVA that wanted me to click on OK, but OK was inactive.  After 15 minutes I figured it had been installed and closed everything.  Now I'm told that I have a broken package and am instructed to get manually 'dpkg --configure -a'.  I don't understand any of this.  Please tell me what to do.:(

---

### Post by orethrius on 2009-03-16
> **Jonathan E-D said:**
> Sorry, I'am an absolute beginner.  My first thread was apparently incorrectly saved so I'm sending another.  I wanted to view my videos and so, as instructed performed the Sudo apt-get install ubuntu-restricted-extras routine.  I was stopped by JAVA that wanted me to click on OK, but OK was inactive.  After 15 minutes I figured it had been installed and closed everything.  Now I'm told that I have a broken package and am instructed to get manually 'dpkg --configure -a'.  I don't understand any of this.  Please tell me what to do.:(
(cross-reply from previous thread)

You can't click OK because the UI was programmed in ncurses.  You have to hit the right arrow key (or space, per bill) to select OK before hitting enter to agree to the EULA.

As for the broken package, run this (hold Alt and hit F2 to bring up the Run prompt) to fix the situation:
```
xterm -e 'gksudo dpkg --configure -a'
```

With any luck, that'll fix the broken extras package or pull it entirely, allowing you to try again.

---

### Post by S.A.A on 2009-03-16
Open Applications > Accsessories > Terminal, and Type:
```
 sudo dpkg --configure -a 
```

---

### Post by sahabcse on 2009-03-16
Hi

Run in terminal

sudo dpkg --configure -a

or 
system>>administration>>synaptic package manager select Fix broken packages in edit menu

---

### Post by Jonathan E-D on 2009-03-16
Sorry, I've tried everything the 3 of you have indicated with no result.  Oh and by the way, Synaptic manager is not accessible either. Any other ideas?

---

### Post by taurus on 2009-03-16
What happens when you run that command from a terminal?

And by the way, you need to press the **Tab** key to highlight the <OK> and then Return to accept java license agreement.

---

### Post by stalkingwolf on 2009-03-16
when  grub starts hit ESC. select recovery mode hit enter.
when recovery finishes select fix broken packages in the menu and hit enter.
reboot.

---

### Post by Jonathan E-D on 2009-03-16
In the case of the solution proposed by Orethius, nothing happens.  In the solutions without xterm a password line appears, but it I am unable to type my password.  Third case proposed, i.e. repair via synaptic manager, is not possible.

---

### Post by taurus on 2009-03-16
Have you tried all these?

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Jonathan E-D on 2009-03-16
I can't test solutions proposed by Taurus as in all three cases when I'm invited to type password, and I try, nothing happens (I type but nothing happens, i.e. the password is not typed).

---

### Post by Jonathan E-D on 2009-03-16
When I tried to access the synaptic manager again I was informed that I had 4 broken packages!  I was very pleased with Linux until I tried to do something by myself; sorry to be putting you to so much trouble.

---

### Post by Jonathan E-D on 2009-03-16
For some reason the Synaptic Package Manager suddenly opened and I asked to repair broken packages. It indicated it had done so and so I returned to Totem to try to view my videos again and I received a message that I didn't have the right CODECS and asking whether it should search.  I approved, it began to search and then I received the following message: "This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."  What should I do now?

---

### Post by Jonathan E-D on 2009-03-16
I took a risk and tried on my own (via synaptic package manager) to install and update package.  Surprisingly it worked and even asked me to approve installation of JAVA.  But when I once again tried to open a video I received a very different message: "Could not open location; you might not have permission to open the file."  Any ideas?

---

### Post by mikechant on 2009-03-16
> I can't test solutions proposed by Taurus as in all three cases when I'm invited to type password, and I try, nothing happens (I type but nothing happens, i.e. the password is not typed).
It's perfectly normal for 'nothing to happen' when you type your password in this case. Just type your password anyhow and hit enter as normal. This is a paranoid security measure - if '*'s were produced in the normal way, someone watching would see how many chars were in your password!
People have complained about this before and it may get changed shortly.

---

### Post by Belliinator on 2010-03-20
Ive had a similar problem to the aithor of this thread, i tried to do the steps reccomended and got this

```

bellman@project-ubuntu:~$  sudo dpkg --configure -a
[sudo] password for bellman: 
Setting up libfftw3-3 (3.2.1-2ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libfftw3-3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libavutil49 (4:0.5+svn20090706-2ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libavutil49 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libenca0 (1.9-7) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libenca0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libavcodec52:
 libavcodec52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
 libavcodec52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
dpkg: error processing libavcodec52 (--configure):
 dependency problems - leaving unconfigured
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libwildmidi0 (0.2.2-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libwildmidi0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenspc0 (0.3.99a-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenspc0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libcdaudio1 (0.99.12p2-7) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libcdaudio1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdirac0c2a (1.0.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdirac0c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liba52-0.7.4 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libquicktime1:
 libquicktime1 depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not configured yet.
  Package libavcodec-extra-52 is not installed.
dpkg: error processing libquicktime1 (--configure):
 dependency problems - leaving unconfigured
Setting up libgsm1 (1.0.13-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgsm1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmms0 (0.4-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmms0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpcdec3 (1:1.2.2-2.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpcdec3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-bad:
 gstreamer0.10-plugins-bad depends on libcdaudio1 (>= 0.99.12p2); however:
  Package libcdaudio1 is not configured yet.
 gstreamer0.10-plugins-bad depends on libdirac0c2a; however:
  Package libdirac0c2a is not configured yet.
 gstreamer0.10-plugins-bad depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
 gstreamer0.10-plugins-bad depends on libgsm1 (>= 1.0.13); however:
  Package libgsm1 is not configured yet.
 gstreamer0.10-plugins-bad depends on libmms0 (>= 0.3-4); however:
  Package libmms0 is not configured yet.
 gstreamer0.10-plugins-bad depends on libmpcdec3; however:
  Package libmpcdec3 is not configured yet.
 gstreamer0.10-plugins-bad depends on libopenspc0; however:
  Package libopenspc0 is not configured yet.
 gstreamer0.10-plugins-bad depends on libwildmidi0; however:
  Package libwildmidi0 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-bad (--configure):
 dependency problems - leaving unconfigured
Setting up libdca0 (0.0.5-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdca0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libass3:
 libass3 depends on libenca0 (>= 1.9); however:
  Package libenca0 is not configured yet.
dpkg: error processing libass3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-ffmpeg:
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not configured yet.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
dpkg: error processing gstreamer0.10-ffmpeg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libswscale0:
 libswscale0 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
 libswscale0 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
dpkg: error processing libswscale0 (--configure):
 dependency problems - leaving unconfigured
Setting up flashplugin-installer (10.0.45.2ubuntu0.9.10.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsoundtouch1c2 (1.3.1-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsoundtouch1c2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libschroedinger-1.0-0 (1.0.8-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libschroedinger-1.0-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libofa0:
 libofa0 depends on libfftw3-3; however:
  Package libfftw3-3 is not configured yet.
dpkg: error processing libofa0 (--configure):
 dependency problems - leaving unconfigured
Setting up libkate1 (0.3.3-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libkate1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdc1394-22 (2.1.2-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdc1394-22 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libiptcdata0 (1.0.3-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libiptcdata0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxvidcore4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmimic0 (1.0.4-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmimic0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libdvdnav4:
 libdvdnav4 depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
dpkg: error processing libdvdnav4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavformat52:
 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is not configured yet.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is not configured yet.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
 libavformat52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
dpkg: error processing libavformat52 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpostproc51:
 libpostproc51 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
 libpostproc51 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is not configured yet.
  Package libavutil-extra-49 is not installed.
dpkg: error processing libpostproc51 (--configure):
 dependency problems - leaving unconfigured
Setting up libfaac0 (1.26-0.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libfaac0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libmjpegtools-1.9:
 libmjpegtools-1.9 depends on libquicktime1 (>= 2:1.1.0+debian); however:
  Package libquicktime1 is not configured yet.
dpkg: error processing libmjpegtools-1.9 (--configure):
 dependency problems - leaving unconfigured
Setting up libfaad0 (2.6.1-3.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libfaad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmodplug0c2 (1:0.8.7-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmodplug0c2 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-bad-multiverse:
 gstreamer0.10-plugins-bad-multiverse depends on libfaac0 (>= 1.26); however:
  Package libfaac0 is not configured yet.
 gstreamer0.10-plugins-bad-multiverse depends on libmjpegtools-1.9 (>= 1:1.9.0); however:
  Package libmjpegtools-1.9 is not configured yet.
 gstreamer0.10-plugins-bad-multiverse depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-bad-multiverse (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libfftw3-3
 libavutil49
 libenca0
 libavcodec52
 libdvdread4
 libwildmidi0
 libopenspc0
 libcdaudio1
 libdirac0c2a
 liba52-0.7.4
 libquicktime1
 libgsm1
 libmms0
 libmpcdec3
 gstreamer0.10-plugins-bad
 libdca0
 libass3
 gstreamer0.10-ffmpeg
 libswscale0
 flashplugin-installer
 libsoundtouch1c2
 libschroedinger-1.0-0
 libofa0
 libkate1
 libdc1394-22
 libiptcdata0
 libxvidcore4
 libmimic0
 libdvdnav4
 libavformat52
 libpostproc51
 libfaac0
 libmjpegtools-1.9
 libfaad0
 libmodplug0c2
 gstreamer0.10-plugins-bad-multiverse


```what should i do?
thanx in advance.

---

### Post by Trandre on 2010-03-20
I had a similar challange and solved it through these posts:

Locating the problem:
[http://ubuntuforums.org/showthread.php?t=1429144](http://ubuntuforums.org/showthread.php?t=1429144)

Resolved issues helped:
[http://ubuntuforums.org/showthread.php?t=1430660](http://ubuntuforums.org/showthread.php?t=1430660)
[http://ubuntuforums.org/showthread.php?t=1434436](http://ubuntuforums.org/showthread.php?t=1434436)


Trandre

---

### Post by Belliinator on 2010-03-21
Hey thanx for the links.

Im just not sure what you were editing out of the sources list, and how that will help.

Ive tried sudo apt-get update multiple times but have no result.I tried  sudo dpkg-reconfigure-a
dpkg-query but it a gave me a command not found response. I am unsure of what to do next. I have also tried to fix broken packages in synaptic but it said fixed broken packages after about a second. Im not sure what to do next. Anyone got any ideas?

---

### Post by Belliinator on 2010-03-23
I get broken dependencies with everything I try and install now. Some of the programs work anyway. Anyone got any ideas?

---

### Post by Trandre on 2010-03-23
I was editing out the conflicts displayed. In my case it was xorg something, so I removed the whole part. 

Do you get any conflict messages?
Do you have a red sign in the upper right corner?
If so, click and the warning will say what line the conflict is in.
You can also try to update synaptics under system--> administration


Trandre

---

