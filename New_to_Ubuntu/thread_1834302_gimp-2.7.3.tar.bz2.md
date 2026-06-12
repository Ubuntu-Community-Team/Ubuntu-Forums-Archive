---
title: "gimp-2.7.3.tar.bz2"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-08-27
I just downloaded GIMP 2.7.3 beta from the GIMP website. It has been deposited in my Downloads folder as gimp-2.7.3.tar.bz2. Can you give me step-by-step terminal directions on how to install it?

[ftp://ftp.gimp.org/pub/gimp/v2.7/gimp-2.7.3.tar.bz2](ftp://ftp.gimp.org/pub/gimp/v2.7/gimp-2.7.3.tar.bz2)

---

### Post by ron999 on 2011-08-27
> **doppel.ganger said:**
> Can you give me step-by-step terminal directions on how to install it?

Hi
You have downloaded the '**source code**'.
It can't be installed until it's been compiled.

If you intend to compile it, unzip it and look at the file inside named **INSTALL**.

---

### Post by keithpeter on 2011-08-27
Hello doppel.ganger

It might be easier to use the binary package rather than compile and install from source.

[http://www.linuxnov.com/gimp-2-7-3-has-been-released-key-features-install-on-ubuntu-using-ppa/](http://www.linuxnov.com/gimp-2-7-3-has-been-released-key-features-install-on-ubuntu-using-ppa/)

This page has a run down on the features in 2.7.3 and has instructions on how to install from the Ubuntu personal package archive (PPA) that has been set up by GIMPers.

If you need help with the terminal commands just post back here.

---

### Post by SoFl W on 2011-08-27
Are you aware that the 2.7.x series are not stable releases of GIMP?  Meaning there could be problems.

---

### Post by Cpierce on 2011-08-27
I installed it by adding the PPA to software sources, then ran apt-get install gimp.

ppa:matthaeus123/mrw-gimp-svn

Loved the single window, but couldn't figure out how to make it default.

---

### Post by keithpeter on 2011-08-27
> **SoFl W said:**
> Are you aware that the 2.7.x series are not stable releases of GIMP?  Meaning there could be problems.

Good point, SoFl W

The 'stable' GIMP is in the Ubuntu Software Centre and runs solid. Just search for GIMP in the Ubuntu Software Centre search box and you will find it.

There is a lot of interest in the 2.7.3 and later releases as the GIMP team are providing a 'single window' option instead of the three windows that you usually have.

---

### Post by SoFl W on 2011-08-27
> **Cpierce said:**
> Loved the single window, but couldn't figure out how to make it default.

After installation you will get the multi-window interface by default. You can switch to the single window interface with **Windows** -> **Single-window mode**.

Via [this link]("http://digitizor.com/2010/07/06/get-gimp-with-a-single-window-in-ubuntu-10-04-lucid-lynx/")

---

### Post by anandharaja on 2011-10-18
Not able to install gimp 2.7.3 in Ubuntu 11.10, iam completely new to Ubuntu first time using so no idea what the error shows. 
[IMG]https://lh5.googleusercontent.com/-OgZ1kGJQP40/Tp2jxq-BYnI/AAAAAAAAAPM/2pcAKkaTAgo/s838/Screenshot%252520at%2525202011-10-18%25252021%25253A27%25253A22.png[/IMG]

---

### Post by azmyth on 2011-10-18
try:

sudo apt-get install gimp-data

then:

sudo apt-get install gimp

---

### Post by anandharaja on 2011-10-18
> **azmyth said:**
> try:

sudo apt-get install gimp-data

then:

sudo apt-get install gimp

Thanks the package downloaded when i use the "sudo apt-get install gimp" command i got the same error.

---

### Post by azmyth on 2011-10-18
Sorry, my last post won't work. You need to remove the older version first then install

sudo apt-get remove gimp*

then 

sudo apt-get install gimp

---

### Post by anandharaja on 2011-10-18
@azmyth Thanks for your reply but still no luck, got same error.
i freshly installed Ubuntu 11.10, no any previous version gimp installed

[IMG]https://lh5.googleusercontent.com/-nV_WVs921Aw/Tp40smvg2MI/AAAAAAAAAPg/qoZ7BnFaw3w/s732/Screenshot%252520at%2525202011-10-19%25252007%25253A47%25253A50.png[/IMG]

[IMG]https://lh4.googleusercontent.com/-qqrXJo2-oWY/Tp40se_cNTI/AAAAAAAAAPc/80zT9LtW_9k/s722/Screenshot%252520at%2525202011-10-19%25252007%25253A50%25253A36.png[/IMG]

---

### Post by alphacrucis2 on 2011-10-18
Probably easiest to fix the broken packages using synaptic before doing anything else.


BTW not sure what state the ppa mentioned earlier in the thread is in.  Appears that the gimp package failed to build on the latest attempt eight weeks ago. You could always compile the very latest from the git repo.

---

### Post by anandharaja on 2011-10-18
> **alphacrucis2 said:**
> Probably easiest to fix the broken packages using synaptic before doing anything else.


BTW not sure what state the ppa mentioned earlier in the thread is in.  Appears that the gimp package failed to build on the latest attempt eight weeks ago. You could always compile the very latest from the git repo.

i completely new to Ubuntu please guide me.

1. how to fix broken packages  using synaptic. 
2. how to compile the latest version.

---

### Post by azmyth on 2011-10-18
1. Open Synaptic, Under Edit -> Fix Broken Packages
2. Compiling is a bit tricky if you don't understand.

---

### Post by alphacrucis2 on 2011-10-18
> **anandharaja said:**
> i completely new to Ubuntu please guide me.

1. how to fix broken packages  using synaptic. 
2. how to compile the latest version.


If you are running the latest Ubuntu, synaptic is not installed by default. To get it enter the following command in a terminal window:

```
sudo apt-get install synaptic
```

Once installed you should be able to find it in the dash or else run it from the terminal:

```
sudo synaptic
```


The is a menu item under Edit called "Fix broken packages"

For compiling from source, this tutorial may help. 

[http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu]("http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu")

---

### Post by anandharaja on 2011-10-19
i fixed the broken packages using synaptic but still got the same error.

---

### Post by KingYaba on 2011-10-19
> **Cpierce said:**
> I installed it by adding the PPA to software sources, then ran apt-get install gimp.

ppa:matthaeus123/mrw-gimp-svn

Loved the single window, but couldn't figure out how to make it default.

The PPA is the easiest way to go. I, too, would love to know how to set single window as the default.

---

### Post by azmyth on 2011-10-19
> **KingYaba said:**
> The PPA is the easiest way to go. I, too, would love to know how to set single window as the default.
I just compiled. It's under Windows -> Single-Windows Mode. Once you check this it will stay like this until you uncheck.

---

### Post by KingYaba on 2011-10-19
> **azmyth said:**
> Once you check this it will stay like this until you uncheck.

I wish it would. I use 2.7.2 so do you think installing a newer version would make this work? I might as well try it.

---

### Post by alphacrucis2 on 2011-10-19
I just had a go at compiling it. The tutorial has a couple of little errors but easy enough to figure out. Setting the single user mode does appear to stick in this version. I compiled the 2.7.3 tarball but I might pull down the latest source from git and give that a go.

---

### Post by beew on 2011-10-19
> **SoFl W said:**
> After installation you will get the multi-window interface by default. You can switch to the single window interface with **Windows** -> **Single-window mode**.

Via [this link]("http://digitizor.com/2010/07/06/get-gimp-with-a-single-window-in-ubuntu-10-04-lucid-lynx/")

But it doesn't stay that way, you have to do this everytime you restart gimp.

---

### Post by anandharaja on 2011-10-19
iam not able to install the gimp 2.6 stable version from software center.

[IMG]https://lh3.googleusercontent.com/-pefTI8QtVlk/Tp7a7NP041I/AAAAAAAAAPs/_W-XU0rNTho/s1024/Screenshot%252520at%2525202011-10-19%25252019%25253A40%25253A56.png[/IMG]

How can i install atleast the stable version.

---

### Post by anandharaja on 2011-10-19
i try to install gimp with synaptic package manager but no luck.

[IMG]https://lh5.googleusercontent.com/-kH3rWww52JI/Tp7hBHfGtEI/AAAAAAAAAP0/q2yRbgUBh4s/s512/Screenshot%252520at%2525202011-10-19%25252020%25253A06%25253A02.png[/IMG]

Please guide me to install gimp its must.

---

### Post by Harry.k on 2011-10-19
> **azmyth said:**
> try:

sudo apt-get install gimp-data

then:

sudo apt-get install gimp

Yup. Its as simple as that. Dont bother with the betas if u are a beginner. Compiling the source is also a pain in the hindquarters.

---

### Post by azmyth on 2011-10-19
> **anandharaja said:**
> i try to install gimp with synaptic package manager but no luck.

[IMG]https://lh5.googleusercontent.com/-kH3rWww52JI/Tp7hBHfGtEI/AAAAAAAAAP0/q2yRbgUBh4s/s512/Screenshot%252520at%2525202011-10-19%25252020%25253A06%25253A02.png[/IMG]

Please guide me to install gimp its must.
You need to disable the ppa you activated for gimp 2.7

---

### Post by azmyth on 2011-10-19
> **KingYaba said:**
> I wish it would. I use 2.7.2 so do you think installing a newer version would make this work? I might as well try it.
I compiled from git and it worked.

---

### Post by anandharaja on 2011-10-19
how to disable ppa?

---

### Post by Harry.k on 2011-10-19
> **anandharaja said:**
> i try to install gimp with synaptic package manager but no luck.

[IMG]https://lh5.googleusercontent.com/-kH3rWww52JI/Tp7hBHfGtEI/AAAAAAAAAP0/q2yRbgUBh4s/s512/Screenshot%252520at%2525202011-10-19%25252020%25253A06%25253A02.png[/IMG]

Please guide me to install gimp its must.

Judging from the image, the gimp-data is not selected for installing. When you select gimp for install, it will ask whether to install the gimp-data package. Select yes. This package is a must. If it still doesnt work, try the command line.

---

### Post by dniMretsaM on 2011-10-19
I have GIMP 2.7.3 running just fine on Oneiric from [this]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn") PPA. Try the following:
```
 sudo apt-get purge gimp gimp-data libgimp2.0
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn to
sudo apt-get update
sudo apt-get upgrade install gimp
```NOTE: If you've already added that PPA, remove it first and then run the above commands.

> **beew said:**
> But it doesn't stay that way, you have to do this everytime you restart gimp.

It's actually working better now. I've had it stay in single window mode  after restarts. However, it won't work perfectly in the 2.7.x series.  It'll go up to 2.8 when it's stable.

---

### Post by anandharaja on 2011-10-19
> **dniMretsaM said:**
> I have GIMP 2.7.3 running just fine on Oneiric from [this]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn") PPA. Try the following:
```
 sudo apt-get purge gimp gimp-data libgimp2.0
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn to
sudo apt-get update
sudo apt-get upgrade install gimp
```NOTE: If you've already added that PPA, remove it first and then run the above commands.

Thank you how can i remove PPA?

---

### Post by dniMretsaM on 2011-10-19
> **anandharaja said:**
> Thank you how can i remove PPA?

```
sudo rm /etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-oneiric.list*
sudo apt-get update
```

---

### Post by anandharaja on 2011-10-19
again same error


anandharaja@anandharaja-desktop:~$ sudo apt-get upgrade install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anandharaja@anandharaja-desktop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: gimp-data (<= 2.6.11-z) but 2.7.3-2011082002~oo is to be installed
E: Unable to correct problems, you have held broken packages.

unable to install gimp?

---

### Post by alphacrucis2 on 2011-10-19
> **beew said:**
> But it doesn't stay that way, you have to do this everytime you restart gimp.

It does stay that way in the version I compiled.

---

### Post by alphacrucis2 on 2011-10-19
> **anandharaja said:**
> again same error


anandharaja@anandharaja-desktop:~$ sudo apt-get upgrade install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anandharaja@anandharaja-desktop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: gimp-data (<= 2.6.11-z) but 2.7.3-2011082002~oo is to be installed
E: Unable to correct problems, you have held broken packages.

unable to install gimp?

Go into synaptic. First fix broken packages as before. Then go into the software souces menu item in synaptic and disable the PPA there. Then click the reload button. Exit synaptic and install gimp as you were doing.

---

### Post by dniMretsaM on 2011-10-19
> **anandharaja said:**
> again same error


anandharaja@anandharaja-desktop:~$ sudo apt-get upgrade install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anandharaja@anandharaja-desktop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: gimp-data (<= 2.6.11-z) but 2.7.3-2011082002~oo is to be installed
E: Unable to correct problems, you have held broken packages.

unable to install gimp?

That's really weird. Never had a problem when I installed it.

---

### Post by anandharaja on 2011-10-19
it is possible to install gimp in my system :(.
Any one have downloaded link for gimp 2.7.3 means please provide the link.

---

### Post by anandharaja on 2011-10-19
i followed the instruction provided in this page. [http://www.omgubuntu.co.uk/2011/08/gimp-2-7-3-released-working-single-window-mode-layer-groups/](http://www.omgubuntu.co.uk/2011/08/gimp-2-7-3-released-working-single-window-mode-layer-groups/)   nothing will help to install gimp 2.7.3

---

### Post by anandharaja on 2011-10-20
Finally i installed gimp 2.6 stable version:D, now how can i update this version to 2.7.3:popcorn:

---

### Post by alphacrucis2 on 2011-10-20
> **anandharaja said:**
> Finally i installed gimp 2.6 stable version:D, now how can i update this version to 2.7.3:popcorn:


If the PPA doesn't work, then the only option is to compile from source. I did the later and have both 2.6.11 and 2.7.3 running. If you aren't reasonably confident with terminal commands then it's probably better to wait until the proper gimp 2.8 release comes out. I'm sure it will get packaged fairly quickly after that even if it doesn't make it into the official oneiric repos.

---

### Post by anandharaja on 2011-10-20
Can i know why PPA not work for me?

---

### Post by alphacrucis2 on 2011-10-20
> **anandharaja said:**
> Can i know why PPA not work for me?


The PPA doesn't work for me in Oneiric either. I suspect something is a bit broken. Possibly a dependency problem.

---

### Post by dniMretsaM on 2011-10-20
> **alphacrucis2 said:**
> The PPA doesn't work for me in Oneiric either. I suspect something is a bit broken. Possibly a dependency problem.

That seem weird, as I'm running GIMP 2.7.3 just fine on Oneiric from that PPA. After you add that PPA, what version of GIMP does the USC show as available?

BTW, did you guys do upgrades of fresh installs?

---

### Post by anandharaja on 2011-10-20
> **dniMretsaM said:**
> That seem weird, as I'm running GIMP 2.7.3 just fine on Oneiric from that PPA. After you add that PPA, what version of GIMP does the USC show as available?

BTW, did you guys do upgrades of fresh installs?

USC Show only gimp2.6

if it works for you means why it not works for me, what are the settings i need to change, can you tell the step by step procedure to install 2.7.3

---

### Post by dniMretsaM on 2011-10-20
I already did and apparently they aren't working for you, so I'm at a loss of what to do.

---

### Post by alphacrucis2 on 2011-10-20
> **dniMretsaM said:**
> That seem weird, as I'm running GIMP 2.7.3 just fine on Oneiric from that PPA. After you add that PPA, what version of GIMP does the USC show as available?

BTW, did you guys do upgrades of fresh installs?


My Oneiric was upgraded from natty at beta stage. I removed the PPA so I just get the official version. Anyway I don't really care about it as I compiled the latest version from git.

---

### Post by Bucic on 2011-10-23
> **anandharaja said:**
> @azmyth Thanks for your reply but still no luck, got same error.
i freshly installed Ubuntu 11.10, no any previous version gimp installed

[IMG]https://lh5.googleusercontent.com/-nV_WVs921Aw/Tp40smvg2MI/AAAAAAAAAPg/qoZ7BnFaw3w/s732/Screenshot%252520at%2525202011-10-19%25252007%25253A47%25253A50.png[/IMG]

[IMG]https://lh4.googleusercontent.com/-qqrXJo2-oWY/Tp40se_cNTI/AAAAAAAAAPc/80zT9LtW_9k/s722/Screenshot%252520at%2525202011-10-19%25252007%25253A50%25253A36.png[/IMG]
That's most probably because you use 64-bit version of ubuntu (amd64). It seems that currently there is no way to install GIMP 2.7.x on 64-bit Ubuntu 11.10. See here for confirmation [http://askubuntu.com/questions/68001/how-do-i-install-gimp-2-7](http://askubuntu.com/questions/68001/how-do-i-install-gimp-2-7)

Two questions though:
1. I could install GIMP 2.7.x on my 64-bit Ubuntu 11.04 just fine so can't we just use that "package"?
2. If someone has successfully compiled GIMP 2.7.x on 64-bit Ubuntu 11.10 can't he simply share that compiled version?

---

### Post by dniMretsaM on 2011-10-23
2.7.4 is in the PPA. Maybe it will work now.

---

### Post by anandharaja on 2011-10-24
> **dniMretsaM said:**
> 2.7.4 is in the PPA. Maybe it will work now.
oh my god its not working for me, i lost my gimp 2.6 installation:confused:,

are you using 64-bit version ubuntu.

```
anandharaja@anandharaja-desktop:~$ sudo apt-get purge gimp gimp-data libgimp2.0
[sudo] password for anandharaja: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenraw1 libwmf0.2-7 libumfpack5.4.0 libbabl-0.0-0 libgegl-0.0-0
  liblensfun-data liblensfun0 libamd2.2.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gimp* gimp-data* libgimp2.0*
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
After this operation, 23.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 144791 files and directories currently installed.)
Removing gimp ...
Purging configuration files for gimp ...
Removing gimp-data ...
Purging configuration files for gimp-data ...
Removing libgimp2.0 ...
Purging configuration files for libgimp2.0 ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme ...
anandharaja@anandharaja-desktop:~$ sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
You are about to add the following PPA to your system:
 PPA named mrw-gimp-svn for matthaeus123
 This is a repository for all of the Gimp trunk git builds that I want.
I guess this would be considered a nightly build PPA, but these builds are not build every night automatically rather built whenever I get around to it, which might be several builds per day or one build per week.


If you have any critical runtime errors that might be  caused by build config problems or have any ideas for patches, feel free to email me.


These packages do not include any patches were they built with any special configurations


GPG Key:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB


 More info: https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.4XfMK5o0tf --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv E84E77B023CADAAB7966690943BB102C405A15CB
gpg: requesting key 405A15CB from hkp server keyserver.ubuntu.com
gpg: key 405A15CB: "Launchpad PPA named mrw-gimp-svn for matthaeus123" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
anandharaja@anandharaja-desktop:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://in.archive.ubuntu.com oneiric InRelease                             
Ign http://in.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://in.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://in.archive.ubuntu.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://in.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:1 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://in.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://in.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://in.archive.ubuntu.com oneiric-updates Release                       
Get:2 http://ppa.launchpad.net oneiric Release [9,779 B]                       
Hit http://in.archive.ubuntu.com oneiric-backports Release                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:3 http://ppa.launchpad.net oneiric/main Sources [3,418 B]                  
Get:4 http://ppa.launchpad.net oneiric/main amd64 Packages [8,942 B]           
Get:5 http://ppa.launchpad.net oneiric/main i386 Packages [5,384 B]            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://in.archive.ubuntu.com oneiric/main Sources                          
Hit http://in.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://in.archive.ubuntu.com oneiric/universe Sources                      
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://in.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://in.archive.ubuntu.com oneiric/main amd64 Packages                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://in.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://in.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://in.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://in.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://in.archive.ubuntu.com oneiric/restricted i386 Packages              
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://in.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://in.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://in.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://in.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://in.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://in.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://in.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Sources            
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://in.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://in.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://in.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://in.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://in.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://in.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://in.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://archive.canonical.com oneiric Release                               
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://in.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://in.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://in.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://in.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://in.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://in.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://in.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://in.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://in.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://in.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://in.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Ign http://in.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://in.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Ign http://in.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://in.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://in.archive.ubuntu.com oneiric/main Translation-en         
Hit http://in.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://in.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://in.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://in.archive.ubuntu.com oneiric-updates/main Translation-en 
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Translation-en
Ign http://dl.google.com stable InRelease                                      
Hit http://in.archive.ubuntu.com oneiric-updates/universe Translation-en       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://in.archive.ubuntu.com oneiric-backports/main Translation-en_US      
Ign http://in.archive.ubuntu.com oneiric-backports/main Translation-en         
Ign http://in.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://in.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Ign http://in.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://in.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Ign http://in.archive.ubuntu.com oneiric-backports/universe Translation-en_US  
Ign http://in.archive.ubuntu.com oneiric-backports/universe Translation-en     
Get:6 http://dl.google.com stable Release.gpg [198 B]                          
Get:7 http://dl.google.com stable Release [1,347 B]                            
Get:8 http://dl.google.com stable/main amd64 Packages [1,204 B]                
Get:9 http://dl.google.com stable/main i386 Packages [1,233 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en
Fetched 31.8 kB in 1min 12s (441 B/s)
Reading package lists... Done
anandharaja@anandharaja-desktop:~$ sudo apt-get upgrade install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libbabl-0.0-0 libgegl-0.0-0 libilmbase6 libopenexr6 libtorrent-rasterbar6
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,118 kB/2,195 kB of archives.
After this operation, 1,888 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ oneiric/main libbabl-0.0-0 amd64 0.1.5-2011102204~oo [80.8 kB]
Get:2 http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/ oneiric/main libtorrent-rasterbar6 amd64 0.15.8+svn.r6128-0ubuntu1~oneiric [1,037 kB]
Fetched 1,118 kB in 35s (31.6 kB/s)                                            
(Reading database ... 143914 files and directories currently installed.)
Preparing to replace libbabl-0.0-0 0.0.22-1build1 (using .../libbabl-0.0-0_0.1.5-2011102204~oo_amd64.deb) ...
Unpacking replacement libbabl-0.0-0 ...
Preparing to replace libilmbase6 1.0.1-3build2 (using .../libilmbase6_1.0.2-3.4~oo_amd64.deb) ...
Unpacking replacement libilmbase6 ...
Preparing to replace libopenexr6 1.6.1-4.1 (using .../libopenexr6_1.7.0-4.3~oo_amd64.deb) ...
Unpacking replacement libopenexr6 ...
Preparing to replace libtorrent-rasterbar6 0.15.8+svn.r6088-0ubuntu4~oneiric (using .../libtorrent-rasterbar6_0.15.8+svn.r6128-0ubuntu1~oneiric_amd64.deb) ...
Unpacking replacement libtorrent-rasterbar6 ...
Preparing to replace libgegl-0.0-0 0.0.22-2ubuntu2 (using .../libgegl-0.0-0_0.1.7-2011090602~oo_amd64.deb) ...
Unpacking replacement libgegl-0.0-0 ...
Setting up libbabl-0.0-0 (0.1.5-2011102204~oo) ...
Setting up libilmbase6 (1.0.2-3.4~oo) ...
Setting up libopenexr6 (1.7.0-4.3~oo) ...
Setting up libtorrent-rasterbar6 (0.15.8+svn.r6128-0ubuntu1~oneiric) ...
Setting up libgegl-0.0-0 (0.1.7-2011090602~oo) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
anandharaja@anandharaja-desktop:~$ 

```
how to add gimp 2.7.4 PPA

---

### Post by anandharaja on 2011-10-24
iam not noticed gimp 2.7.4 available in software center:D, thank god i succesfully installed gimp 2.7.4, now working fine:popcorn:

---

### Post by Bucic on 2011-10-24
The PPA is now working with Ubuntu 11.10 x64! 
See [http://askubuntu.com/questions/68001/how-do-i-install-gimp-2-7/71153#71153](http://askubuntu.com/questions/68001/how-do-i-install-gimp-2-7/71153#71153)

---

