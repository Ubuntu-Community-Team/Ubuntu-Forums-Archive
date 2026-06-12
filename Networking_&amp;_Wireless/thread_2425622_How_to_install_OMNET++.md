---
title: "How to install OMNET++"
date: 2019-08-28
forum: Networking &amp; Wireless
---

### Post by zak100 on 2019-08-28
Hi,
 
 
 I am following the following web site:
 [https://computerscience247.wordpress.com/2018/12/15/how-to-install-omnet-in-ubuntu-18-04-1/](https://computerscience247.wordpress.com/2018/12/15/how-to-install-omnet-in-ubuntu-18-04-1/)
 
 
 
 
 I am trying to execute the following command:

~$ sudo apt-get -y install build-essential gcc g++ bison flex perl \qt5-default tcl-dev tk-dev libxml2-dev zlib1g-dev default-jre \doxygen graphviz libwebkitgtk-3.0–0 libopenscenegraph-dev \openscenegraph-plugin-osgearth openmpi-bin libopenmpi-dev \python python3 libqt5opengl5-dev openscenegraph-plugin-osgearth libosgearth-dev libpcap-dev gnome-color-chooser nemiver


 
 I am getting following error:
 
 
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 E: Unable to locate package libwebkitgtk-3.0–0
 E: Couldn't find any package by glob 'libwebkitgtk-3.0–0'
 E: Couldn't find any package by regex 'libwebkitgtk-3.0–0'

Somebody please guide me.

Zulfi.

---

### Post by again? on 2019-08-28
libwebkitgtk-3.0[COLOR="#FF0000"]&#8211;[/COLOR]0 in the guide seems to be using a dash instead of hyphen

Try
```
libwebkitgtk-3.0[COLOR="#FF0000"]-[/COLOR]0
```

Articles using wordpress often use the wrong syntax.

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt policy libwebkitgtk-3.0-0 **
libwebkitgtk-3.0-0:
  Installed: (none)
  Candidate: 2.4.11-3ubuntu3
  Version table:
     2.4.11-3ubuntu3 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
```

There is a pdf install guide from [omnetpp.org]("https://omnetpp.org/documentation/") 
[pdf install guide]("https://omnetpp.org/doc/omnetpp/InstallGuide.pdf") <---- DIRECT PDF DOWNLOAD

---

### Post by zak100 on 2019-08-31
Hi,
I am now getting following errors:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.4ubuntu1).
build-essential set to manually installed.
python is already the newest version (2.7.15~rc1-1).
python set to manually installed.
zlib1g-dev is already the newest version (1:1.2.11.dfsg-0ubuntu2).
zlib1g-dev set to manually installed.
libopenmpi-dev is already the newest version (2.1.1-8).
openmpi-bin is already the newest version (2.1.1-8).
openmpi-bin set to manually installed.
default-jre is already the newest version (2:1.11-68ubuntu1~18.04.1).
g++ is already the newest version (4:7.4.0-1ubuntu2.3).
g++ set to manually installed.
gcc is already the newest version (4:7.4.0-1ubuntu2.3).
gcc set to manually installed.
libqt5opengl5-dev is already the newest version (5.9.5+dfsg-0ubuntu2.1).
libqt5opengl5-dev set to manually installed.
perl is already the newest version (5.26.1-6ubuntu0.3).
python3 is already the newest version (3.6.7-1~18.04).
qt5-default is already the newest version (5.9.5+dfsg-0ubuntu2.1).
[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libosgearth-dev : Depends: libopenscenegraph-3.4-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Some body please guide me.

Zulfi.[/B]

---

### Post by again? on 2019-08-31
Firstly fix any errors...
```
sudo apt install -f
sudo apt update
```

Then from the pdf I linked. Ubuntu chapter 5.
```

sudo apt-get install build-essential gcc g++ bison flex perl python python3 qt5-default libqt5opengl5-dev tcl-dev tk-dev libxml2-dev zlib1g-dev default-jre doxygen graphviz libwebkitgtk-1.0
sudo apt-get install openscenegraph-plugin-osgearth libosgearth-dev
```

I don't get any errors to this stage in 18.04.

---

### Post by zak100 on 2019-09-01
Hi,
Thanks. I am able to install Omnet 5.5. i did the steps which you mentioned and also followed the other steps mentioned in the tutorial pointed by yourself. After that i followed the wordpress site : [https://computerscience247.wordpress.com/2018/12/15/how-to-install-omnet-in-ubuntu-18-04-the](https://computerscience247.wordpress.com/2018/12/15/how-to-install-omnet-in-ubuntu-18-04-the) omnet downloaded the omnet from the link provided in the site and followed all the remaining step to extract the contents of file and then executing the 'make" file. Finally I got following messages:


Creating executable: out/gcc-debug//osg-satellites_dbg

Now you can type "omnetpp" to start the IDE
:~/Downloads/omnetpp-5.5.1$ omnetpp
Starting the OMNeT++ IDE...
:~/Downloads/omnetpp-5.5.1$

---

