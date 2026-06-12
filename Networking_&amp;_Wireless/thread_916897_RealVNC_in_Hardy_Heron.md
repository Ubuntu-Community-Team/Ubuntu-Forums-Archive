---
title: "RealVNC in Hardy Heron"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by NicMagic on 2008-09-11
This posting is for all those Ubuntu users who would love to have the old VNC from gutsy in hardy Heron.

I am a network engineer and VNC is one of the cornerstone's our my support framework...

I loved working with VNC in Gutsy (7.10) as it used RealVNC's ver 4 edition viewer which gave me the option to turn down colours, choose encoding levels and compression levels etc. it was fast, customisable and easy to use.

When i upgraded to Hardy Heron i noticed Vinagre had replaced VNC in ubuntu and while it is beautiful in concept it is still quite young as an app.
I love the bookmarking, saved passwords and the tabs. I Loathe the fact that I cannot turn down the colour level in Vinagre which, if you connect to some slower networks or over a WAN as i almost always do, is essential.

No problem, i thought i would just re-install vncviewer from the Repo's and I could have the best of both worlds...
So after a quick ```
sudo apt-get install vncviewer
``` i could use a command line vncviewer <IP Address> and be done. The problem comes in that the version that get's installed via the repos is xTightVNCViewer which doesn't have the same customisations available...
I want RealVNC and after  fair amount of traulling through forums etc. I finally found how to install the (Gutsy) RealVNC Viewer...

Firstly you have to download RealVNC from their website [www.realvnc.com]("http://www.realvnc.com") GOTO Downloads, choose free edition and then the i386 Linux tar file... (btw I am running Hardy Heron 8.04.1 x86_64 [64-bit] and used the i386 file with no probs)

Once you have the file downloaded, extract the contents then open a terminal and cd to the extracted folder and run the install script:
*NOTE - Make sure you have no "vncviewer" currently installed 
```
./vncinstall /usr/local/bin 
```

!!(The Following library is not necessary if running Intrepid Ibex [8.10]) Once VNC has been installed you need to install some dependencies:
In terminal:
```
 sudo apt-get install libstdc++6-pic 
```

There is one more shared library you need which is not available in the repo's (Or it wasn't for me) - libstdc++2.10-glibc2.2 which is available at [http://packages.debian.org/stable/libs/]("http://packages.debian.org/stable/libs/") Download the i386 version or open Terminal and type:

```
 wget http://ftp.uk.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb 
```

Once downloaded you can install through package manager as it's a .deb

*NOTE* If you are running Ubuntu x86_64 as i am you will get an error saying the package is for the wrong architecture... You need to force the install :
```
dpkg -i --force-architecture libstdc++2.10-glibc2.2_2.95.4-27_i386.deb

```

To test your installation type:
```
vncviewer --help
```
You should get no errors and see a list of available options for the command...

I hope this helps anyone else who's missing the VNC we had in Gutsy Gibbon

Regards,
Nic
:))

---

### Post by KEdas on 2008-10-14
RealVNC in Hardy is renamed to "xvnc4viewer", so to install it simply type:
```
sudo aptitude install xvnc4viewer
```

Why bother with compiling from source? ;)

---

### Post by NicMagic on 2008-11-11
If you read the document you will notice that I wanted the functionality that comes with RealVNC i.e. ability to change compression / colour levels shared etc... which xtightvnc does not offer...

It works perfectly as a viewer just simply install the native vncviewer in the repos but i wanted the RealVNC installation that was included in Gutsy...

---

