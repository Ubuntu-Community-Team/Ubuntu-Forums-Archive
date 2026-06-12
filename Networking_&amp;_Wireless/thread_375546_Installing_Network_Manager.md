---
title: "Installing Network Manager"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by balls on 2007-03-03
Before I begin, I would like to say that I am aware of the hundreds of tutorials on how to install Network Manager.  However, none of them have worked.  I've downloaded the .tar archives on a separate computer and then moved them onto my Ubuntu desktop (which currently is not connected to the internet and is the reason why I'm trying to get Network Manager to work).  So please, if someone could give me THE MOST basic explanation of how to install it, I would truly appreciate it.  And just FYI, I am completely new to Linux,   I know pretty much nothing, so please be understanding.

Thanks.

---

### Post by RomeReactor on 2007-03-03
Hi. I think you downloaded the source package for Network-Manager; there are .deb files on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

[This]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.3-2ubuntu6_i386.deb&md5sum=522cade5b931785517c0fb2bb7035a1e&arch=i386&type=main")  package is Network-Manager and [this]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.3-2ubuntu6_i386.deb&md5sum=1f857fb5abaa57675e4695baf66289b5&arch=i386&type=main") one is Network-Manager-Gnome (a graphical frontend to NM). After you download those, first install Network-Manager by double-clicking on the .deb file; afterwards, install the other one the same way.

---

### Post by balls on 2007-03-03
I appreciate your prompt response, however when I tried executing the .deb files, i got the following error:

Error:  Dependency is not satisfiable:  libc6

Any additional information would help alot.

Thanks again.

---

### Post by RomeReactor on 2007-03-03
Most likely when a program mentions a "dependency is not satisfiable" it's because you need to install a library. So grab [this]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.4-1ubuntu12_i386.deb&md5sum=3d7d40e703e91d16e54e64525174d38f&arch=i386&type=main") .deb file and install it before trying to install NM.

---

### Post by fygaren on 2007-03-04
Im trying to get the network manager to work as well.

I found out I had to install the following packages first:
- libnl1-pre6
- libnm-util0
- dhcdbd

Now network-manager installs.

After installing network-manager-gnome, I get the following message when I boot:

"The Network manager applet could not find some required resources. It cannot continue"

Im now trying to find out what resources that might be.

If you get it to work, please let me know as mine isnt working either.

---

### Post by fygaren on 2007-03-04
Ive tried installing every package that Network-manager and Network-manager-gnome need, but I still get the same error:

"The Network manager applet could not find some required resources. It cannot continue"

Anyone out there that can give me a push in ANY direction it would make me very happy. Im totally lost now?

I have a clean install of dapper(tried edgy too, but I get the same error there)

---

### Post by FIONEX on 2007-03-04
Am I missing something?  THe most basic way to install network manager is to open Synaptic Package manager from the system menu.  THen search for network-manager, wpasupplicant, networm-manager-gnome, and network-manager-applet.  install all of them, and synaptic will take care of the dependencies.

---

### Post by RomeReactor on 2007-03-05
Hi fygaren and FIONEX. FIONEX, the problem they have is that they can't get internet access working in their Ubuntu systems, so they must download libraries in another computer (or booting into windows) and copying them over to Ubuntu. fygaren, in case you don't have internet access in your Ubuntu system either, try downloading all of Network-Manager's dependencies from [here]("http://packages.ubuntu.com/"). I just checked in Synaptic and the dependency list goes as follows:

> Depends: libc6 (>= 2.4-1), libdbus-1-3, libdbus-glib-1-2 (>= 0.71), libgcrypt11 (>= 1.2.2), libglib2.0-0 (>= 2.12.0), libgpg-error0 (>= 1.2), libhal1 (>= 0.5), libiw28 (>= 28), libnl1-pre6, libnm-util0, iproute, iputils-arping, dhcdbd (>= 1.12-2), lsb-base (>= 2.0-6), wpasupplicant (>= 0.4.8), dbus (>= 0.60), hal (>= 0.5.0)

So search for them in Synaptic first, to see if you're missing any, and try searching for the missing ones [here]("http://packages.ubuntu.com/").

---

### Post by fygaren on 2007-03-05
Thank you for your reply,
 I already went through the ubuntu.packages pages and downloaded all the dependencies for both network-manager, network-manager-gnome and the dependencies dependencies...I dunno, everything should work out of the box here..I think Ill try to wrap a driver in Ndis.

---

### Post by RomeReactor on 2007-03-07
fygaren, don't know if you'll get to read this, but [this]("http://www.ubuntuforums.org/showpost.php?p=1069792&postcount=8")  looks like a solution to the resources issue with Network Manager.

---

### Post by bbaaxx on 2008-01-09
Thanks for the pointing Rome, that solution worked for me. ... dammn bugs.

---

