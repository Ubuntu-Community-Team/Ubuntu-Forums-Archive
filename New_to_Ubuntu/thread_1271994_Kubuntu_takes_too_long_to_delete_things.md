---
title: "Kubuntu takes too long to delete things"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Falc7 on 2009-09-21
It really takes darn ages, i have about 10mb of files, and it takes about a minute and a half to move to the wastebin. I installed this as ubuntu, then now instaled the kubuntu-desktop package and use that now if it makes a difference.

---

### Post by Perfect Storm on 2009-09-21
Update your kubuntu to the latest version will solve your problem (did for me); 

[http://www.kubuntu.org/news/kde-4.3.1](http://www.kubuntu.org/news/kde-4.3.1)

---

### Post by Falc7 on 2009-09-21
I put
 deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main 
Into the 3rd party software sources and reloaded the software updates in KDE control panel, it found 3 new updates, none of which look like the one to upgrade KDE to the newest version, perhaps i did something wrong?

---

### Post by Perfect Storm on 2009-09-21
## Kubuntu Backports
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

## Kubuntu Beta Backports
deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) jaunty main

Remeber to add the gpg key.

---

### Post by sandyd on 2009-09-21
you can also go to the trashcan settings, uncheck the maximum size limits

then try deleting again.

---

### Post by Falc7 on 2009-09-21
I got some strange message after installing the updates for KDE, that ended with the words "you need to fork", and now KDE won't load up, it loads the first 4 pictures after the password is entered, then i get a message about plasma crashing, and something about backends, it didn't make much sense to me. I am writing this from gnome atm



EDIT: Back in gnome and i used the update manager, it advised me to do a partial upgrade, and i get this message:
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages
And it listed a bunch of KDE applications

---

### Post by sandyd on 2009-09-21
run this
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [8AC93F7A]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xE4DFEC907DEDA4B8A670E8042836CB0A8AC93F7A&op=index")

```

---

### Post by Falc7 on 2009-09-21
```
jamie@jamie-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
[sudo] password for jamie: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jamie@jamie-laptop:~$ 

```

Still can't use KDE :(

---

### Post by Falc7 on 2009-09-22
I tried uninstalled kubuntu-desktop package so i could reinstall it, but when i tried to reinstall i got this message:

E: kubuntu-docs: subprocess post-installation script returned error exit status 1

Not all changes and updates succeeded

I removed kubuntu-docs, and tried reinstalling, and got this message, when i tried to press control + C to copy the error messages :/
This will end the operation and may leave the system in a broken state.  Are you sure that you want to do that?

---

### Post by Falc7 on 2009-09-22
Okay i am getting frustrated with this now, is there some way to install the old kubuntu desktop? I am have semi-useable kubuntu 4.3.1 desktop but there are problems with kubuntu-docs, wireless networks, and the notification area's colours seem strange, and disjointed on my system. I can't be bothered to work out how to fix these problems, i don't think i am going to be able to use the new KDE until it comes out in KK unfortunately.

I did some research and also tried this:
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install kubuntu-desktop
But it didn't help, i still get errors about kubuntu-docs

I also tried making a new partition, installing kubuntu afresh, and tried upgrading that to KDE 4.3.1, it also didn't work

I am also getting crashes with this info 

```
Application: Plasma Workspace (kdeinit4), signal: Segmentation fault
[Current thread is 0 (LWP 14208)]

Thread 2 (Thread 0xa83cfb90 (LWP 14209)):
#0  0xb7ef7430 in __kernel_vsyscall ()
#1  0xb640d0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb65ed2ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7cf3172 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb7630ac2 in ?? () from /usr/lib/libQtNetwork.so.4
#5  0xb7cf2132 in ?? () from /usr/lib/libQtCore.so.4
#6  0xb64094ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb65de49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5f16a10 (LWP 14208)):
[KCrash Handler]
#6  0xb6eaa8fa in QGraphicsItem::isWidget () from /usr/lib/libQtGui.so.4
#7  0xb6ee4667 in QGraphicsScene::event () from /usr/lib/libQtGui.so.4
#8  0xb68a3d3c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#9  0xb68ac03e in QApplication::notify () from /usr/lib/libQtGui.so.4
#10 0xb73b485d in KApplication::notify () from /usr/lib/libkdeui.so.5
#11 0xb7de6bcb in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#12 0xb6ef6a75 in QGraphicsView::viewportEvent () from /usr/lib/libQtGui.so.4
#13 0xb6d4e235 in ?? () from /usr/lib/libQtGui.so.4
#14 0xb7de5dea in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
#15 0xb68a3d1a in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#16 0xb68ac122 in QApplication::notify () from /usr/lib/libQtGui.so.4
#17 0xb73b485d in KApplication::notify () from /usr/lib/libkdeui.so.5
#18 0xb7de6bcb in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#19 0xb68fa44d in QWidget::event () from /usr/lib/libQtGui.so.4
#20 0xb6caba53 in QFrame::event () from /usr/lib/libQtGui.so.4
#21 0xb6d4c72d in QAbstractScrollArea::event () from /usr/lib/libQtGui.so.4
#22 0xb6ef36a6 in QGraphicsView::event () from /usr/lib/libQtGui.so.4
#23 0xb68a3d3c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#24 0xb68ac122 in QApplication::notify () from /usr/lib/libQtGui.so.4
#25 0xb73b485d in KApplication::notify () from /usr/lib/libkdeui.so.5
#26 0xb7de6bcb in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#27 0xb68aac6b in QApplication::setActiveWindow () from /usr/lib/libQtGui.so.4
#28 0xb691a7b5 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#29 0xb694637a in ?? () from /usr/lib/libQtGui.so.4
#30 0xb6456b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#31 0xb645a0eb in ?? () from /usr/lib/libglib-2.0.so.0
#32 0xb645a268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#33 0xb7e122f8 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#34 0xb6945a75 in ?? () from /usr/lib/libQtGui.so.4
#35 0xb7de51fa in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#36 0xb7de5642 in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#37 0xb7de7ae9 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#38 0xb68a3bb7 in QApplication::exec () from /usr/lib/libQtGui.so.4
#39 0xb3b08310 in kdemain () from /usr/lib/libkdeinit4_plasma-desktop.so
#40 0x0804e27d in _start ()
```


Another edit: I am going to try once more, fresh installed kubuntu, upgraded to KDE4.3.1, if it works i could grab all my files over from the other partition

---

