---
title: "Software Sources, clicked, no response."
date: 2010-04-06
forum: New to Ubuntu
---

### Post by Isyaltut on 2010-04-06
Hi there, I'm running Ubuntu Kamic and I have this little problem that is pretty annoying. The problem is that I can't access the Software Sources anymore (System-Administration-Sources). When I click on that, nothing happened, nada, no response at all. I access Software Sources mainly to choose my best mirror server, because from my experience, the speed vary from time to time (I'm from Indonesia anyway, and we have some mirror here for Ubuntu). I like to change the server (with "choose best server" option) to get the fastest speed. And now, because of this, my download speed to install application or updating is reduced greatly to 9-10 Kb/s (usually it's about 120-150 Kb/s (it's not really fast I know, but comparing 10 to 150 Kb/s?). What annoys me is that, I can't do anything to change this.


This little problem happened after I played around with my desktop environment. I want to try kubuntu-desktop after about a year my experience with ubuntu-gnome, and following the guide from psychocats.net [http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde") , I can login to KDE session and to find out what the fuss is all about regarding KDE 4.3. I must admit  it's really good, but it's not as responsive as my gnome desktop and eating up about 1 ½ of my Ram (I don't want to start another debate about &#8220;the best&#8221; desktop environment, it really is personal preference and I prefer Gnome). After about a month, I decided to remove my KDE desktop and  following the guide from the same source  (I'm more of a minimalist guy, and I don't like those K application cluttering my menu (and of course, disk space issue)) [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome"). I've read the element to be removed, and I think it is safe to do this operation without breaking my Ubuntu installation. 


After that, some weird things hapenned. My VLC, and SMplayer was missing. And of course, the Software Sources thing. Well, this maybe is not really a big problem for me because my Ubuntu box is already compete to satisfy my needs and don't really need to install additional application (except for VLC and SMplayer). But what if I want to try Xubuntu-desktop?:p:p 


I can not find a solution to my problem after searching to Google and Ubuntu Forum, so if any of you have advice for me, I greatly appreciate that. (and maybe there is command-line solution for this?)

---

### Post by philinux on 2010-04-06
Open a terminal and use this command, use copy and paste. See if any errors are reported.

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

---

### Post by Isyaltut on 2010-04-06
> **philinux said:**
> Open a terminal and use this command, use copy and paste. See if any errors are reported.

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

I tried it, still no response. Got this in terminal instead: SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

---

### Post by philinux on 2010-04-06
> **Isyaltut said:**
> I tried it, still no response. Got this in terminal instead: SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

Try selecting a default theme. Also can you run synaptic package manager?

---

### Post by Isyaltut on 2010-04-06
> **philinux said:**
> Try selecting a default theme. Also can you run synaptic package manager?

I've restored the original theme, and the problem is still happening. About synaptic, I still can run it. Now I must say that I haven't touch synaptic in a long time (command line is faster for me to install application), but as fas as i remember, isn't there software sources option in synaptic? I tried setting-repositories, but it just say "Repositories Changed.
The repository information has changed. You have to click on the "Reload" button for your changes to take effect".

Any other suggestion?

---

### Post by philinux on 2010-04-06
> **Isyaltut said:**
> I've restored the original theme, and the problem is still happening. About synaptic, I still can run it. Now I must say that I haven't touch synaptic in a long time (command line is faster for me to install application), but as fas as i remember, isn't there software sources option in synaptic? I tried setting-repositories, but it just say "Repositories Changed.
The repository information has changed. You have to click on the "Reload" button for your changes to take effect".

Any other suggestion?

Yes under the settings pull down that gets you Software Sources. Click the Reload button after.

---

### Post by Isyaltut on 2010-04-06
> **philinux said:**
> Yes under the settings pull down that gets you Software Sources. Click the Reload button after.

Yep, alrady reloaded, clicked the setting-repositories. And the reload pop up appeared again.

---

### Post by Isyaltut on 2010-04-06
What about command line though? Is there CLI way to change software sources (and pick the best mirror server)?

---

### Post by philinux on 2010-04-06
> **Isyaltut said:**
> What about command line though? Is there CLI way to change software sources (and pick the best mirror server)?

To edit the sources list use this. Best mirror can only be detected but the software sources gui I reckon. I've never researched a cli way.
```
gksudo gedit /etc/apt/sources.list
```

Go careful with any edit. Best to make a backup of the file first.

---

### Post by Isyaltut on 2010-04-06
> **philinux said:**
> To edit the sources list use this. Best mirror can only be detected but the software sources gui I reckon. I've never researched a cli way.
```
gksudo gedit /etc/apt/sources.list
```

Go careful with any edit. Best to make a backup of the file first.

I've no problem with sources list, just sudo add-apt-repository (add sources or ppa) and sudo add-purge-repository. So I guess there is no other method to choose best server huh? Well, maybe I must content downloading application with only 10 Kb/s speed. :(

---

### Post by philinux on 2010-04-06
> **Isyaltut said:**
> I've no problem with sources list, just sudo add-apt-repository (add sources or ppa) and sudo add-purge-repository. So I guess there is no other method to choose best server huh? Well, maybe I must content downloading application with only 10 Kb/s speed. :(

Can you use synaptic to get at Software Sources and from there select the best server.

---

### Post by Isyaltut on 2010-04-06
> **philinux said:**
> Can you use synaptic to get at Software Sources and from there select the best server.

No, as I've written in my previous post, it just show the reload option.

---

### Post by philinux on 2010-04-06
> **Isyaltut said:**
> No, as I've written in my previous post, it just show the reload option.

Ok how about this.

```
gksudo software-properties-gtk
```

And post the result of this.

```
cat /usr/share/python-apt/templates/Ubuntu.info
```

---

### Post by Isyaltut on 2010-04-06
The first code didn't work.
This is the second code result:
```
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: intrepid
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports

```

---

### Post by philinux on 2010-04-06
You seem to be missing the karmic bit from your file. Very odd. This is my file. Maybe make a backup of this file and paste in just the karmic bits.
```

cat /usr/share/python-apt/templates/Ubuntu.info
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: karmic
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 9.10 'Karmic Koala'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: karmic
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.10
MatchURI: cdrom:\[Ubuntu.*9.10
Description: Cdrom with Ubuntu 9.10 'Karmic Koala'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: karmic-security
ParentSuite: karmic
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: karmic-updates
ParentSuite: karmic
RepositoryType: deb
Description: Recommended updates

Suite: karmic-proposed
ParentSuite: karmic
RepositoryType: deb
Description: Pre-released updates

Suite: karmic-backports
ParentSuite: karmic
RepositoryType: deb
Description: Unsupported updates

Suite: jaunty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: intrepid
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports

```

---

### Post by Isyaltut on 2010-04-06
Hi, Phil, thanks for all your suggestion. 
But I'm still can not access the software sources. I already did your suggestion to change the /usr/share/python-apt/templates/Ubuntu.info file (after I back it up of course). And yet the problem is still persist. I log out hoping that maybe this will make a change, but apparently it isn't.

---

### Post by philinux on 2010-04-06
> **Isyaltut said:**
> Hi, Phil, thanks for all your suggestion. 
But I'm still can not access the software sources. I already did your suggestion to change the /usr/share/python-apt/templates/Ubuntu.info file (after I back it up of course). And yet the problem is still persist. I log out hoping that maybe this will make a change, but apparently it isn't.

I would try creating a new user with admin rights of course. Log in to that user and see if you can access sources.

Searching for part of the error message gives a lot of hits with same problem. Hope you find a solution soon.

[http://www.google.co.uk/search?q=aptsources.distro.NoDistroTemplateException%3A+Error%3A+could+not+find+a+distribution+template&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=aptsources.distro.NoDistroTemplateException%3A+Error%3A+could+not+find+a+distribution+template&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

