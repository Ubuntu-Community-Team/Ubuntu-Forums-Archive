---
title: "error upgrading to kde 4.2"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-02-07
im getting this error in adept

```
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --configure, -a ], 
    Sup-process returned error code 1, 
    Error processing kate : dependency problems - leaving unconfigured., 
    Error processing kdeplasma-addons : dependency problems - leaving unconfigured.
```

im not sure how to fix this

---

### Post by SuperSonic4 on 2009-02-07
Have you added ```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
``` to /etc/apt/sources.list ?

To add the key: ```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```

If not do so and then ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by abn91c on 2009-02-07
did you have plasmoids running when you started the upgrade? Look at this [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

### Post by PatrickMoore on 2009-02-07
i have closed all the plasmoids. i dont know how to remove or disable plasmoids any help with that?

---

### Post by PatrickMoore on 2009-02-07
im having another go at it and as i update i get this message

```
Commit failed.
To continue, hit ok and we will try to recover. If you close the application now, we will not do anything and you may try to resolve the problem manually.
(If you suspect this is a bug in Adept, please also provide the following exception description in the report).

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --unpack, /var/cache/apt/archives/libglib2.0-0_2.18.2-0ubuntu2_amd64.deb, /var/cache/apt/archives/libqtgui4_4.4.3-0ubuntu1.1_amd64.deb, /var/cache/apt/archives/libqtcore4_4.4.3-0ubuntu1.1_amd64.deb, /var/cache/apt/archives/libphonon4_40x0.0000001e8f9f8p-10224.3.0-0ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libpulse0_0.9.10-2ubuntu9.3_amd64.deb, /var/cache/apt/archives/libgnutls26_2.4.1-1ubuntu0.2_amd64.deb, /var/cache/apt/archives/libldap-2.4-2_2.4.11-0ubuntu6.1_amd64.deb, /var/cache/apt/archives/libwbclient0_20x0.0000001e8b828p-10223.2.3-1ubuntu3.4_amd64.deb, /var/cache/apt/archives/libsmbclient_20x0.0000001e8b828p-10223.2.3-1ubuntu3.4_amd64.deb, /var/cache/apt/archives/libxine1_1.1.15-0ubuntu3.1_amd64.deb, /var/cache/apt/archives/libxine1-x_1.1.15-0ubuntu3.1_amd64.deb, /var/cache/apt/archives/libxine1-console_1.1.15-0ubuntu3.1_amd64.deb, /var/cache/apt/archives/libxine1-misc-plugins_1.1.15-0ubuntu3.1_amd64.deb, /var/cache/apt/archives/libxine1-bin_1.1.15-0ubuntu3.1_amd64.deb, /var/cache/apt/archives/phonon-backend-xine_40x0.0000001ea26d8p-10224.3.0-0ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libsoprano4_2.1.64+dfsg.1-0ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/soprano-daemon_2.1.64+dfsg.1-0ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libxml2_2.6.32.dfsg-4ubuntu1.1_amd64.deb, /var/cache/apt/archives/libxml2-utils_2.6.32.dfsg-4ubuntu1.1_amd64.deb, /var/cache/apt/archives/kdelibs-bin_40x0.0000001ea26d8p-10224.2.0-0ubuntu2~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libssl0.9.8_0.9.8g-10.1ubuntu2.1_amd64.deb, /var/cache/apt/archives/strigi-daemon_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/strigi-client_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libstrigihtmlgui0_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libstreamanalyzer0_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libstreams0_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libpoppler3_0.8.7-1ubuntu0.1_amd64.deb, /var/cache/apt/archives/poppler-utils_0.8.7-1ubuntu0.1_amd64.deb, /var/cache/apt/archives/libstrigiqtdbusclient0_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libsearchclient0_0.6.3-1ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/kdelibs5-data_40x0.0000001f26998p-10224.2.0-0ubuntu2~intrepid1~ppa1_all.deb, /var/cache/apt/archives/kdelibs5_40x0.0000001f26998p-10224.2.0-0ubuntu2~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/kdebase-runtime_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa3_amd64.deb, /var/cache/apt/archives/kdebase-runtime-bin-kde4_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa3_amd64.deb, /var/cache/apt/archives/kdebase-runtime-data-common_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa3_all.deb, /var/cache/apt/archives/kdebase-runtime-data_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa3_all.deb, /var/cache/apt/archives/libkdecorations4_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb, /var/cache/apt/archives/libkwineffects1_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb, /var/cache/apt/archives/kde-window-manager_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb, /var/cache/apt/archives/phonon_40x0.0000001f26998p-10224.3.0-0ubuntu1~intrepid1~ppa1_all.deb, /var/cache/apt/archives/libkonq5-templates_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa2_all.deb, /var/cache/apt/archives/libkonq5_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa2_amd64.deb, /var/cache/apt/archives/plasmoid-quickaccess_0.7.1-0ubuntu6~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/ksysguard_40x0.0000001f26998p-10224.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb, /var/cache/apt/archives/libboost-program-options1.34.1_1.34.1-11ubuntu1_amd64.deb, /var/cache/apt/archives/libakonadiprivate1_1.1.0-0ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/libical0_0.43-2ubuntu1~intrepid1~ppa1_amd64.deb, /var/cache/apt/archives/kdepimlibs-data_40x0.0000001f278c8p-10224.2.0-0ubuntu1~intrepid~ppa4_all.deb, /var/cache/apt/archives/kdepimlibs5_40x0.0000001f278c8p-10224.2.0-0ubuntu1~intrepid~ppa4_amd64.deb, /var/cache/apt/archives/libpam-runtime_1.0.1-4ubuntu5.3_all.deb ], 
    Sup-process returned error code 1, 
    Error processing /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb : trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kdebase-workspace-bin.
```

---

### Post by PatrickMoore on 2009-02-07
if i run sudo apt-get -f install    i get

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kate kde-window-manager kdebase-plasma kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-libs4+5 libplasma3
Recommended packages:
  dontzap
The following packages will be REMOVED:
  kdeplasma-addons-libs4 libplasma2
The following NEW packages will be installed:
  libplasma3
The following packages will be upgraded:
  kate kde-window-manager kdebase-plasma kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-libs4+5
6 upgraded, 1 newly installed, 2 to remove and 186 not upgraded.
3 not fully installed or removed.
Need to get 0B/16.8MB of archives.
After this operation, 6623kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 92353 files and directories currently installed.)
Preparing to replace kde-window-manager 4:4.1.2-0ubuntu12 (using .../kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb) ...
Unpacking replacement kde-window-manager ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kdebase-workspace-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by evan2645 on 2009-02-07
I am having the same problems as Patrick. Any insight?

---

### Post by evan2645 on 2009-02-07
PS>> this happens to me even on a fresh install (w/ all updates applied) of 8.1 on my hardware. It just happened again for the second time :(

---

### Post by PatrickMoore on 2009-02-07
i am as well i did two fresh installs and same issue

---

### Post by PatrickMoore on 2009-02-08
anyone? this is kind of frustrating

---

### Post by PatrickMoore on 2009-02-08
ok so trying synaptec like  another forum said got me this result
[/CODE]E: /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb: trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kdebase-workspace-bin[/CODE]

the only problem is that i have no clue how to remove that manually.

---

### Post by PatrickMoore on 2009-02-08
ok so i have 4.2. installed but im unsure of the stability 

basically i added the repository and key

then ran sudo apt-get -f update && sudo apt-get -f upgrade

that seemed to have forced it but i need to determine any issues ill let you know.

---

### Post by thechris on 2009-02-09
this doesn't work for me.  however I was able to take an ubuntu install and get kde4.2 working fairly painlessly, though things like konsole are missing by default.  This method also throws gnome-apps into kde's menus and vice versa, making both menus cluttered.

---

### Post by thechris on 2009-02-09
oh, and as a note, installing kde4.2 from kubuntu 8.10 seems to fail and then make kde unsuable.

---

### Post by evan2645 on 2009-02-09
Patrick - How is stability so far?

I was going to wait for Jaunty release but if you can confirm everything is good with the command you mentioned i will go ahead and give those a shot

I was only able to find one other person reporting the same error; it appears everyone suffering is running ati... maybe coincidence

---

### Post by evan2645 on 2009-02-11
> **thechris said:**
> oh, and as a note, installing kde4.2 from kubuntu 8.10 seems to fail and then make kde unsuable.

Did you see the same errors described by Patrick, or different?

---

### Post by Paul Mitchell on 2009-02-14
I think I've fixed this with something like:

> dpkg -i --force-all /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_amd64.deb

---

### Post by kannedheat on 2009-02-14
I've been having the same problems here.  I'll try Paul's suggestion> /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0unbunt1~intrepid1~ppa7-amd64.deb

---

### Post by jopa1234 on 2009-04-04
> **Paul Mitchell said:**
> I think I've fixed this with something like:

This worked for me also, thanks

---

