---
title: "app installation tutorial"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Pedroparamo on 2009-05-19
Does anyone know of a basic step-by-step detailed tutorial on how to install an application in Ubuntu 9.04?  

For instance, I have downloaded a tar.gz file which is now sitting on my desktop and I want to install it.  Where should I put it in order to unpack it so that it creates it's own working directory and how do I make a 'launcher' to the executable file?  I know every app may be a little different as far as the installation process goes, but it also seems like there is also a basic process for installation of tar.gz files and I would like to know what that is.

As is obvious I am a newbie and I am trying to make the switch to ubuntu but find the process for installing applications that are NOT available in the Synaptic Package Manager a little frustrating and time consuming.

I am sold on opensource and want to make it work and try to implement ubuntu within my organization but we all have a very tight workflow/deadline schedule and not a lot of time to mess with the installation process.

Thanks.

Pedro

---

### Post by kanikilu on 2009-05-19
What is it that you are trying to install? If you have to compile it, see this page:

[http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

If it's a binary, just extract the contents somewhere and run the executable (there's no common name or extension) but the executable is usually called the same as the application name and/or in a "bin" directory...

---

### Post by Pedroparamo on 2009-05-19
I am trying to install LightZone.  Can I extract the contents to my desktop and then simply double click on the executable?

Thanks.

Pedro

---

### Post by superprash2003 on 2009-05-19
usually most tar.gz files come with an INSTALL note

---

### Post by Didius Falco on 2009-05-19
Here are a couple of other tutorials you might find useful. The first one is an easier, beginners guide:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

This one goes a little deeper into the process:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

I hope it helps...

Regards,

Didius

On Edit - according to this page, which I just ran across, you don't need to compile LightZone. The article linked below is a couple of years old, and refers specifically to version 2.1:

[http://www.linux.com/archive/feature/60084](http://www.linux.com/archive/feature/60084)[URL="http://www.linux.com/archive/feature/60084"]
[/URL]

---

### Post by Pedroparamo on 2009-05-19
I can't seem to find the ./configure file.  I have a directory /usr/local/src/LightZone which contains the following files

dcraw        libFASTJAI.so   libLCFileUtil.so  libLinux.so            LightZone          mlibwrapper_jai.jar
jh.jar       libfbf.so       libLCJNI.so       libmlib_jai.so         LightZone_16.png   
script-api.jar
jre          libJAI.so       libLCJPEG.so      libSegment.so          LightZone_32.png   substance-lite.jar
lcjai.jar    libLCArrays.so  libLCMS.so        lightcrafts.jar        LightZone-forkd
libDCRaw.so  libLCCache.so   libLCTIFF.so      lightcrafts-linux.jar  lightzonehelp.jar


How should I proceed?

Thanks.

Pedro

---

### Post by Celauran on 2009-05-19
Looks like precompiled Java. There might not be a need to install anything. Are there any subdirectories? There may be install scripts (install.sh, for example). There should also be a README file.

---

### Post by Didius Falco on 2009-05-19
Per that article linked in my post above:

> When the download is complete, you can untar the file to any location on your system and launch it with ./LightZone.Have you tried that? If yes, and it's not working, what version are you trying to use, and is it the free or full version?

Regards,

Didius

---

### Post by Pedroparamo on 2009-05-19
There are sub directories-- jre/lib which contains 

applet                                fontconfig.RedHat.3.properties.src  jvm.hprof.txt
calendars.properties                  fontconfig.RedHat.bfc               locale
charsets.jar.pack                     fontconfig.RedHat.properties.src    logging.properties
classlist                             fontconfig.Sun.bfc                  management
cmm                                   fontconfig.Sun.properties.src       management-agent.jar
content-types.properties              fontconfig.SuSE.bfc                 meta-index
deploy                                fontconfig.SuSE.properties.src      net.properties
deploy.jar.pack                       fontconfig.Turbo.bfc                oblique-fonts
desktop                               fontconfig.Turbo.properties.src     plugin.jar.pack
ext                                   fonts                               psfontj2d.properties
flavormap.properties                  i386                                psfont.properties.ja
fontconfig.bfc                        im                                  resources.jar
fontconfig.properties.src             images                              rt.jar.pack
fontconfig.RedHat.2.1.bfc             jce.jar                             security
fontconfig.RedHat.2.1.properties.src  jexec                               sound.properties
fontconfig.RedHat.3.bfc               jsse.jar.pack                       zi

and a bin subdirectory which contains 

ControlPanel  java_vm   keytool  pack200     rmid         servertool  unpack200
java          jcontrol  orbd     policytool  rmiregistry  tnameserv


& there is a readme 

       README

                Java(TM) Platform, Standard Edition
                        Runtime Environment
                             Version 6

I can't seem to find any scripts.  Can I try clicking on any executable files i find or is that a bad idea?

Pedro

---

### Post by Pedroparamo on 2009-05-19
./LightZone did the trick.  You're the man.

Thanks!

Pedro

---

### Post by Didius Falco on 2009-05-19
Happy to help!

Regards,

Didius

---

