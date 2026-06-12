---
title: "Update of Update Manager Causing Problems"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by PPPilot on 2010-08-10
After yesterdays update of the Update Manager I now have issues. This AM I ran it for the first time and it came back with an error and said it was doing a partial update, In the process it apparently uninstalled tragtor. When I try to reinstall tragtor I get this error:
Error: Cannot install 'ffmpeg' So then I went to Synaptic and tryed to mark ffmeg for install and get this error: ffmpeg:
 Depends: libavcodec52 but it is not going to be installed or
     libavcodec-extra-52 (>=4:0.6) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
 Depends: libavdevice52 but it is not going to be installed or
     libavdevice-extra-52 but it is not going to be installed
 Depends: libavdevice52 but it is not going to be installed or
     libavdevice-extra-52 but it is not going to be installed
 Depends: libavfilter1 but it is not going to be installed or
     libavfilter-extra-1 (>=4:0.6) but it is not installable
 Depends: libavfilter1 but it is not going to be installed or
     libavfilter-extra-1 (<4:0.6-99) but it is not installable
  Depends: libavformat52 (>=4:0.6-1~ppa1) but 4:0.5.1-1ubuntu1 is to be installed or
     libavformat-extra-52 but it is not going to be installed

It also says I have unresolved dependencies etc.

It would appear that the update uninstalled a bunch if stuff which I can not seem to reinstall.

---

### Post by kr651129 on 2010-08-10
can you run

```
sudo apt-get install ffmpeg
```

and give us the output?

---

### Post by praveenthivari on 2010-08-10
Do u hv ubuntu tweak installed if then update with tht. Or else try it from synaptic

---

### Post by PPPilot on 2010-08-10
Here is the output:
```
john@john-desktop:~$ sudo apt-get install ffmpeg
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (>= 4:0.6-1~ppa1) but it is not going to be installed or
                   libavcodec-extra-52 (>= 4:0.6) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
          Depends: libavdevice52 (>= 4:0.6-1~ppa1) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.6) but it is not going to be installed
          Depends: libavdevice52 (< 4:0.6-99) but it is not going to be installed or
                   libavdevice-extra-52 (< 4:0.6-99) but it is not going to be installed
          Depends: libavfilter1 (>= 4:0.6-1~ppa1) but it is not going to be installed or
                   libavfilter-extra-1 (>= 4:0.6) but it is not installable
          Depends: libavfilter1 (< 4:0.6-99) but it is not going to be installed or
                   libavfilter-extra-1 (< 4:0.6-99) but it is not installable
          Depends: libavformat52 (>= 4:0.6-1~ppa1) but 4:0.5.1-1ubuntu1 is to be installed or
                   libavformat-extra-52 (>= 4:0.6) but it is not going to be installed
E: Broken packages
john@john-desktop:~$ 
```
 Hope this helps you...

---

### Post by PPPilot on 2010-08-10
I tried Ubuntu Tweak and Synaptic and both errored out.

---

### Post by PPPilot on 2010-08-10
When I run Update Mananger it shows libavformat52 available for upgrade but it is greyed out. Really confusing....

---

### Post by QLee on 2010-08-10
From the error report the system thinks it needs a version of a package that it does not have available to it.

Check to make sure your repositories are all still correct. If you were attempting a distribution upgrade the "partner" repositories were probably commented out. 

After checking that repositories are correct, do an Update Manager, check, to  get the latest version numbers and then try the install updates again. ...or do an apt-get update; followed by apt-get upgrade if you want to use command line.

---

### Post by PPPilot on 2010-08-10
The source-list looks ok. The "partner" repositories are not commented out. When I ran "apt-get update" it displayed this error at the end: 
```
W: Failed to fetch http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Hope this helps....

---

### Post by -kg- on 2010-08-10
Strange.

I just ran "apt-get update" and everything was OK, including:

> Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]

I did experience a problem about duplicate entries, in which it was suggested that I run the same command to correct it.  I did, and it did...came out as a perfect update.

I just applied the update to Update Manager today, so I have the same version.  The only thing I can think of is that somehow your Medibuntu entry or key got borked.  Try "apt-get update" again, and if you have the same results, you might want to uninstall and then re-install the Medibuntu Repos.

---

### Post by PPPilot on 2010-08-10
Well after digging around in my list files, I found out both the mediabuntu and c-korn-vlc list files had been borked up. I have no idea how they got changed but I put them straight and I was able to install traGtor and Update Manager seems to work OK now.... Thanks for all the help everybody:D

---

### Post by -kg- on 2010-08-10
Great!  Glad we could help!

[IMG]http://www.freesmileys.org/smileys/smiley-happy088.gif[/IMG]

---

