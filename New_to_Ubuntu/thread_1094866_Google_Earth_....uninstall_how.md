---
title: "Google Earth ....uninstall how?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-13
I cannot find the google earth folder that has the uninstall program in it.

I would like to try and remove it that way before doing something thru terminal.

---

### Post by martrn on 2009-03-13
> **ozark_hillbilly said:**
> I cannot find the google earth folder that has the uninstall program in it. I would like to try and remove it that way before doing something thru terminal.

Open a terminal and type :

```
dpkg -S googleearth-4.3
```

That will show you were a program is installed to and were the dpkg will remove files from.

You are **NOT** recommended to remove files by deleting directories.

The apt package-management system (eg using apt-get or gui equivalent) is one very strong strength of ubuntu (and of course debian where it came from).  The reason for this is because the way the apt package management system handles its dependencies.  An example of apt-get in action --

Suppose I say    "apt-cache show googleearth-4.3" I get :
[I]
Package: googleearth-4.3
Source: googleearth
Version: 4.3.7204.836-0medibuntu1
Architecture: i386
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Installed-Size: 47516
Pre-Depends: debconf (>= 1.4.69) | cdebconf (>= 0.39)
Depends: googleearth-4.3-data (= 4.3.7204.836-0medibuntu1), libc6 (>= 2.3.2), libfreetype6 (>= 2.3.5), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1, ttf-dejavu | ttf-bitstream-vera | msttcorefonts
Conflicts: googleearth (<< 4.3.7191.6508-0medibuntu2), googleearth-4.2
Homepage: [http://earth.google.com/](http://earth.google.com/)
.....
.....
blaugh blaugh blaugh blaugh......[/I]

Now google-earth is has dependencies listed above.  There maybe things listed above I no longer need, or some of those things I may need for other packages.

Keep track of your dependencies on your gnu/linux system and manage your applications installs through apt-get or synaptic.

---

### Post by ozark_hillbilly on 2009-03-13
martrn,

thanks for info.

I installed Google Earth as a downloaded bin file and ran archive manager on it. I discovered later that you could get the app thru synaptic I believe. It may of ran installing it that way as well. Dunno.

At this point I will heed your advice about dependencies and using apt-get or synaptic to keep things tidy.

dpkg -S googleearth-4.3 resulted in "not found"  ????

Ed

---

### Post by ozark_hillbilly on 2009-03-13
bgrand,

Newer version of GE is not found in the location your thread reference mentioned.

Ed

---

### Post by gandaran on 2009-03-13
> **ozark_hillbilly said:**
> I cannot find the google earth folder that has the uninstall program in it.

I would like to try and remove it that way before doing something thru terminal.
if you install GE from medibuntu repository you can use synaptic to remove it, if you installed from the google's bin file you have to go to the GE install directory and find the uninstall file, run that uninstall file in the terminal/console.

---

### Post by ozark_hillbilly on 2009-03-13
Whew that was a close one....had tried everything but voodoo 'til I discovered thru google and old ubuntu forum thread this:

eld@House:~$ sudo su -
[sudo] password for eld: 
root@House:~# sudo su -
root@House:~# cd /opt/google-earth/
root@House:/opt/google-earth# export DISPLAY=:0
root@House:/opt/google-earth# ./uninstall
Product: Google Earth
Installed in /opt/google-earth
Uninstalling desktop menu entries...
Uninstalling mimetypes...
Google Earth has been successfully uninstalled.

root@House:/opt/google-earth# 

That was a relief, thanks again to fakie_flip!

Ed

---

