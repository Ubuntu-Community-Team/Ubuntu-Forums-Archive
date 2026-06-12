---
title: "Lucid Lynx: Installation Failed on Desktop computer"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by astrobob.tk on 2010-07-11
hey guys,

Just yesterday, I installed WinXP & was installing Lucid Lynx. Thing I think were going fine until the power went off. The installation was in the mid of copying the files to my system when the power went off.

I attempted to reinstall but since then I have been getting an "Installation Falied" message as shown in the pic. 

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=6507[/IMG]

When I press OK the disc goes to live version which then gives me another error msg as shown in this pic:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=6508[/IMG]

In this live disc, things are very slow. The system is not very responsive.
I cleaned my disc & reinstalled WinXP & reattempted installing Lucid. Same thing. I then tried Jaunty which apparently has been installed. I tried upgrading from Jaunty to Lucid but It said that this is not possible.

I seek you help & analysis of my situation.

If it helps my desktop is quite old (bought in 2000):

1 GHZ
256 MB SD RAM
No ethernet card
56K dail up modem


I am currently trying to install it from the live disc though things are very slow.

hope to hear from u soon

thx

---

### Post by Naitsirhc Hsem on 2010-07-11
Maybe the alternate installer cd would work :
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#mirrors](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#mirrors)

---

### Post by Paddy Landau on 2010-07-11
> **astrobob.tk said:**
> 256 MB SD RAM
That's your problem. Not enough RAM for Ubuntu. You need at least 512Mb, recommend at least 1Gb.

I recommend that you install [Lubuntu]("http://lubuntu.net/") instead. It's an alternative distribution of Ubuntu especially for low-spec computers. I have it running on an old PC and it works just fine.

---

### Post by QLee on 2010-07-11
[QUOTE=astrobob.tk]hey guys,
...
In this live disc, things are very slow. The system is not very responsive.
...
1 GHZ
256 MB SD RAM
No ethernet card
56K dail up modem


I am currently trying to install it from the live disc though things are very slow.[/QUOTE]

From the 10.04 release notes:
> System Requirements The minimum memory requirement for Ubuntu 10.04 LTS is 256 MB of memory. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed. 
Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD. 
I've run the live cd on a system with a 1G celeron with 256MB and it is very slow, that would be normal behaviour from a low resource system running from live CD.

---

### Post by astrobob.tk on 2010-07-20
thx guys for you replies. Though I can't currently update or renew my system & need it fast for some report work, I tried Debian Lenny 5.0.1 which I had & its working great. I've upgraded of course to 5.05 & its also great though there's this little problem. I am using this WYSIWYM LaTeX-based software "LyX". On Ubuntu 10.04 it was version 1.6.5 & on Debian synaptic shows & installs version 1.5.5 so my files are not being read & thus I can't work with them. How can I update LyX on Debian to version 1.6.5 ?

I tried running: apt-get update lyx
&
apt-get install lyx 1.6.5 (after I removed the current version)
but i get a message that "update" doesn't take an option command. Basically I don't know how isntall a specific version of a software.

Hope that you can help though its not the right forum or place to ask about Debian.

thx

---

### Post by sandyd on 2010-07-20
> **astrobob.tk said:**
> thx guys for you replies. Though I can't currently update or renew my system & need it fast for some report work, I tried Debian Lenny 5.0.1 which I had & its working great. I've upgraded of course to 5.05 & its also great though there's this little problem. I am using this WYSIWYM LaTeX-based software "LyX". On Ubuntu 10.04 it was version 1.6.5 & on Debian synaptic shows & installs version 1.5.5 so my files are not being read & thus I can't work with them. How can I update LyX on Debian to version 1.6.5 ?

I tried running: apt-get update lyx
&
apt-get install lyx 1.6.5 (after I removed the current version)
but i get a message that "update" doesn't take an option command. Basically I don't know how isntall a specific version of a software.

Hope that you can help though its not the right forum or place to ask about Debian.

thx
Tank into debian squeeze -> [http://wiki.lyx.org/LyX/LyXOnDebian](http://wiki.lyx.org/LyX/LyXOnDebian)

If debian still isn't fast enough, and your patient, you can probably try gentoo or arch.

Their much faster due to the fact that all the programs are compiled from source
but still, I would advise grabbing an extra 256mb ram. Their really cheap now, since DDR 2/3 is practically standard now...
Gentoo aparently has an extremely high version...```

sandy@dolphinaura-laptop ~ $ emerge -pv lyx

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild  N    ] app-text/aiksaurus-1.2.1  USE="-gtk" 908 kB
[ebuild  N    ] dev-texlive/texlive-fontsextra-2008  USE="-doc -source" 116,509 kB
[ebuild  N    ] app-office/lyx-[COLOR=Red]1.6.6.1[/COLOR]  USE="X cups nls subversion svg -debug -dia -docbook -dot -html -latex -monolithic-build -rcs -rtf" LINGUAS="-ar -ca -cs -de -el -en -es -eu -fi -fr -gl -he -hu -id -it -ja -nb -nn -pl -pt -ro -ru -sk -tr -uk -zh_CN -zh_TW" 11,880 kB

Total: 3 packages (3 new), Size of downloads: 129,295 kB
sandy@dolphinaura-laptop ~ $ 

```but if you want a lower version....
```

sandy@dolphinaura-laptop ~ $ sudo autounmask app-office/lyx

 autounmask version 0.27 (using PortageXS-0.02.09 and portage-2.1.8.3)

 * Using repositories:
     /usr/portage
     /var/lib/layman/sunrise
     /var/lib/layman/x11
     /var/lib/layman/desktop-effects
     /usr/local/portage

 * The given category/package-version does not seem to exist. Listing existing versions:

[COLOR=Red] * gentoo (/usr/portage):
     app-office/lyx-1.5.7
     app-office/lyx-1.6.5
     app-office/lyx-1.6.6.1
     app-office/lyx-1.6.6
[/COLOR]
 * sunrise (/var/lib/layman/sunrise):
     none

 * x11 (/var/lib/layman/x11):
     none

 * desktop-effects (/var/lib/layman/desktop-effects):
     none

 *  (/usr/local/portage):
     none

 * Please pick one of the versions given above and try again.

```

---

### Post by astrobob.tk on 2010-09-15
thx Sandy,

I will check all this asap after configuring my new Dell Studio XPS :D

---

### Post by QLee on 2010-09-15
[QUOTE=astrobob.tk]..., I tried Debian Lenny 5.0.1 which I had & its working great. I've upgraded of course to 5.05 & its also great though there's this little problem. I am using this WYSIWYM LaTeX-based software "LyX". On Ubuntu 10.04 it was version 1.6.5 & on Debian synaptic shows & installs version 1.5.5 so my files are not being read & thus I can't work with them. How can I update LyX on Debian to version 1.6.5 ?
...[/QUOTE]
There is a Lenny backport for lyx 1.6.7-1.

---

