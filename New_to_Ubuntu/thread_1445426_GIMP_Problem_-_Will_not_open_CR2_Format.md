---
title: "GIMP Problem - Will not open CR2 Format"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by brentavius on 2010-04-02
Hi.  I am a Windows user who is currently trying out Linux Ubuntu as an alternative.  I have Windows and Ubuntu installed in the side-by-side format.  For the most part, I really like Ubuntu:  it loads faster, runs faster, and I know it is safer.  I have a couple of issues, though, that I need to resolve before I can convince myself to make the switch permanent.

The first is the most problematic and most curious.  One of my primary home computing purposes is my digital photography hobby.  As a GIMP user, I thought moving to Ubuntu would be a plus, but I'm having a problem.  In Ubuntu, GIMP will not open my CR2 files (Canon RAW format).  I have installed UFRaw, and it recognizes and opens these files with no problem.  But when I try to move from UFRaw to GIMP,  it will not open.  I get an error message that just tells me GIMP can't open it for an 'Unknown Reason'.  Likewise, I cannot open the images directly from the GIMP.

Here's the most puzzling piece of this, though:  if I reboot and start Windows, that version of GIMP/UFRaw works just fine for the same images.  I've tried uninstalling and reinstalling both applications, and I've searched helps and forums, etc.  No dice.  This is a deal killer for me, which is disappointing because I think I would otherwise be very happy with Ubuntu.  I can't imagine why these Linux-based applications would seem to operate better in Windows than in Linux. . . . .

Any ideas?

---

### Post by achase79 on 2010-04-02
This may be a version issue.  What version of Gimp do you have in Windows and which in Ubuntu.  You may need a newer version of Gimp to the same version as your Windows install to get that functionality.

---

### Post by PhilGil on 2010-04-02
Check that the version of UFRaw you have installed supports your camera.

Also, I believe there are two versions of UFRaw: stand-alone and a plug-in/add-on version.  Perhaps you need to install the plug-in version (if you haven't already).  I have the plug-in version and raw files from my Rebel XT open fine in Gimp.

---

### Post by brentavius on 2010-04-02
Thanks for your quick responses.

@ achase79:  I believe I'm actually running a newer version of GIMP on the Ubuntu side.  I'm running version 2.6.2 in Windows and version 2.6.7-1ubuntu1.1 on the Ubuntu side.

@ PhilGil:  1)  I think the version of UFRaw supports my Rebel XTi  because it will open and edit the files.  It is only when I try to move them to the GIMP that I get the failure.

2)  You may be onto something with the stand-alone versus plug-in versions.  I loaded UFRaw from the Ubuntu Software Center.  It didn't give me any options as to which version.  It is quite possible that is loaded the stand-alone version rather than the plug-in, and I can see how that might possibly cause my problem.  I don't know how to load it so I'm sure I load the plug-in version, but I'll keep trying to make my way down that path.  If you (or anyone else) have any suggestions on this, I would sure appreciate them.  

Here are my issues with trying to load the plug-in version:

When I go to the UFRaw website, it links me to this page:  [http://packages.ubuntu.com/search?keywords=ufr](http://packages.ubuntu.com/search?keywords=ufr), and there are links at the bottom of that page that seem to offer alternative installation packages for the UFRaw plug-in version, but as a brand-new user of Ubuntu (and Linux for that matter), I'm a little intimidated by them.  Which one should I choose?  And whichever I choose, when I scroll to the bottom where it invites me to install, there are two or more components ([amd64]("http://packages.ubuntu.com/dapper/amd64/gimp-ufraw/download") or [i386]("http://packages.ubuntu.com/dapper/i386/gimp-ufraw/download"), for example) .  When I click one of the components, it directs me to a page that 'strongly suggests' I use a package manager such as Synaptic or Aptitude rather than downloading from that page.  I'm not usually scared to experiment, but I'm so new to this software. . . .

---

### Post by achase79 on 2010-04-02
Try searching UFRaw in the Synaptic Package Manager (it is in system->administration)
there is a gimp-ufraw package that may not be installed

---

### Post by brentavius on 2010-04-02
EUREKA!  That seems to be it.  Thanks so much to both of you for helping me along!

---

### Post by TaoBoogie on 2010-05-31
Exactly the advice I needed too. Great stuff achase79 and brentavius.

---

### Post by tom3k493 on 2010-07-04
just a little problem  - whenever i open a cr2 image in gimp, it simply opens up in ufraw, not actually in gimp itself :(

---

### Post by Perfect Storm on 2010-07-04
> **tom3k493 said:**
> just a little problem  - whenever i open a cr2 image in gimp, it simply opens up in ufraw, not actually in gimp itself :(

Right click on the file, click properties.

Open with tab and choose gimp. If it's not there click the 'add' button.

---

### Post by USERspooner on 2010-07-04
I use a Canon 350D DSLR and also use it's CR2 RAW format.

My software combination for RAW files in GIMP is "GIMP" (obviously) and "gimp-dcraw" which is a "GIMP plug-in for loading RAW digital photos".

Works perfectly for me.

---

### Post by USERspooner on 2010-07-04
I guess I should add that "gimp-dcraw" is simply available in the Software Centre...

---

### Post by Machiavelli on 2011-09-27
> **achase79 said:**
> Try searching UFRaw in the Synaptic Package Manager (it is in system->administration)
there is a gimp-ufraw package that may not be installed

Wow that did the trick for me, thanks!

---

### Post by I2k4 on 2011-09-27
I'm using GIMP 2.6 with UFRaw installed as a plug-in from the Synaptic Package Manager.  The only icon I have is for GIMP.  I start GIMP and find and open the RAW file in its menu - the file is then automatically loaded in UFRaw's window, and when I OK the processing UFRaw shuts down and the new image is automatically in GIMP's window - since UFRaw is non-destructive, GIMP is dealing with a new image to then be saved as JPEG or TIFF.  This has worked great, even on my Live USB installations.

I hadn't heard of a "stand alone" UFRaw but if there is one, it might not "play" with GIMP the same way.

---

