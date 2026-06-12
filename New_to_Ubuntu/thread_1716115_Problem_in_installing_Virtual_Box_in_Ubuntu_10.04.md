---
title: "Problem in installing Virtual Box in Ubuntu 10.04"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by rocky_siva on 2011-03-28
i have installed Ubuntu 10.04 and i needed virtual box installed to get into Windows XP. Downloaded virtual box 4.0 debian file and tried installing. Encountered dependency pblm like this


Unpacking replacement virtualbox-4.0 ...
dpkg: dependency problems prevent configuration of virtualbox-4.0:
 virtualbox-4.0 depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network is not installed.
 virtualbox-4.0 depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl is not installed.
 virtualbox-4.0 depends on libqtcore4 (>= 4:4.6.1); however:
  Package libqtcore4 is not installed.
 virtualbox-4.0 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing virtualbox-4.0 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 virtualbox-4.0



Kindly guide me regarding it. 
Thanks in Advance

---

### Post by robsoles on 2011-03-28
Welcome to UF.

If you don't need better/easier access to USB then you can get it out of the repository. Open "System"->"Administration"->"Synaptic Package Manager" and put 'virtualbox' into the search box near the top of the window that opens for Synaptic - if you don't see some valid virtualbox entries you could choose from then check your sources using the menus in Synaptic.

If you do need to get better/easier access to USB then please go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and read on until you find the instructions for using apt-get to install it rather than downloading any specific file for unpacking - this should get you into a workable situation as opposed to all those dependency errors you got before.

Any good?

---

### Post by ikt on 2011-03-28
> **robsoles said:**
> If you do need to get better/easier access to USB then please go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I just grab the .deb for ubuntu and install that, seems to work np, just make sure you have an active internet connection so it can grab any extras it needs.

---

### Post by rocky_siva on 2011-03-28
Still the pblm persists when trying "robsoles" second option,


The following packages have unmet dependencies:
  virtualbox-4.0: Depends: libqt4-network (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-opengl (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqtcore4 (>= 4:4.6.1) but it is not going to be installed
                  Depends: libqtgui4 (>= 4:4.6.1) but it is not going to be installed
                  Recommends: libsdl-ttf2.0-0 but it is not going to be installed
                  Recommends: dkms but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by robsoles on 2011-03-28
As advised by the output in the error from that command sequence, please execute
```
sudo apt-get -f install
```
in terminal and post back the output of that command if it seems 'interesting'

If the response/output of that command indicates only things being fixed or nothing very meaningful then retry the command you got the above response from using the '-f' (it means 'attempt to fix' not 'force' in this command) flag again.

---

### Post by robsoles on 2011-03-28
> **ikt said:**
> I just grab the .deb for ubuntu and install that, seems to work np, just make sure you have an active internet connection so it can grab any extras it needs.

yah, should work out if your system is 'hunky dory' but if there is an 'apt-get' path to follow you are so much better off for a variety reasons, the most obvious being that updates will prompt you rather than you having to chase them (yes, I know that VirtualBox will prompt you about updates as well :) :roll:).

---

### Post by rocky_siva on 2011-03-28
Pblms gone after tryin to re-install once more.... Virtual Box is up...

thanks mate

---

