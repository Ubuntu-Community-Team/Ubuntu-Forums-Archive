---
title: "How to Automate the Customization of Ubuntu for Mass Installation"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-17
I want to install Ubuntu -- along with my own custom configuration settings -- on a massive number of machines of all different types.

I don't want to use remastersys...   I think I'd prefer to do clean fresh installs of Ubuntu natively... for optimal results.

Thus, I need a way to automate the customizations I make.

There are at least eight things I don't know how to automate... like in a script.... or via a program or something.  They are:

[LIST]
[*]Adding some launcher icons to the top panel

[*]Changing / adding some Compiz Fusion settings

[*]Changing / adding some Ubuntu Tweaks settings

[*]Adding some Firefox Add-Ons

[*]Adding some Firefox "Customize" icons within Firefox to the top to toolbar area.

[*]Unchecking and / or Adding applications to the Startup Manager

[*]Changing the desktop background image.

[*]Changing the Screensaver and Power Management settings.
[/LIST]

Any ideas?   The simpler the better.   Can all these things be done with a terminal script of some sort?

---

### Post by readycarpenter on 2010-04-17
yes this is very doable. and what you are talking about is basically a custom linux distro, based on ubuntu.

the easiest way I believe is to create a script that runs each command to install extra packages etc. then use remastersys (I know you don't want to use it but it is easy) to add your script to the run at startup, this is the trick the finale snipet of the script to disable run at startup, so it only runs the first time.

all the things you want to add are scriptable easily, start with basic bash scripting, pretty much going to be running the same terminal commands you have been. As for the custom icons that is where remastersys comes in you can add custom icon and default desktop icons through remastersys's giu.

todo
script to install extra packages.
remastersys to add extra icons(or just physically replace the original with your custom).
remastersys to add script to startup

also if you are not aware of it, virtualbox a free open source virtual machine, used to run and test os's within your os desktop.

cheers

---

### Post by brucewagner on 2010-04-17
Yes.  

Up to now, I have been doing all the customizations I want..., then creating a new Live DVD using remastersys.  That works great and does exactly what I want to do.

To keep it under the 4GB limit, I only add the essential packages BEFORE creating the remastersys Live DVD...  Then, I created a very simple text file containing all the commands to add the additional needed repositories, and then install all the applications I want installed.  I run that file as an executable script AFTER the Live DVD Install completes.  

(I only install the applications that I want a launch icon on the panel.. BEFORE the remastersys creation of the Live DVD.)

HOWEVER, I am not happy with the results.

I find that installing from a remastersys Live DVD is NOT the same as installing a native Ubuntu Live CD.  The results DIFFER.  Things like proprietary video drivers perhaps (which I do not install before "mastering"), etc., are not the same.

Bottom Line:  The end result does NOT work the same when I use remastersys versus a native clean fresh Ubuntu install.  Using remastersys is maybe 95% effective.  I want 100% effective.  ( I have studied the remastersys forums for many months, and I read about all the issues that can arise from using remastersys.)

So....  That's why I need to know how to do these customizations in a script... rather than using remastersys  ...for a better, more reliable, end result.

Are these customizations really really difficult to do via a script?

---

### Post by Paqman on 2010-04-17
> **brucewagner said:**
> 
Are these customizations really really difficult to do via a script?

No, for most of what you want to do, you're just modifying some text files, so once you know the exact modification you want to make, getting a script to do it is pretty trivial.

What you might find a bit more difficult is things like Firefox addons, i'm not sure how easy that is to do from a script. If they're available as Ubuntu packages it's dead easy. I might be wrong though, Mozilla might have made it easy to install addons via the CLI.

Either way, you'll have to do a fair bit of research and testing to pull it off, but writing the actual script shouldn't be too hard. Bear in mind you're also commiting to maintaining it in the future, as it may break on future version of Ubuntu. 

Should be quite an interesting little project though.

---

### Post by HermanAB on 2010-04-17
The best way to do this is with Red Hat Kickstart.  Kickstart is the reason why all large deployments of Linux are RPM based (Mandriva, Suse, Red Hat).

However, Kickstart is slowly worming its way into Debian systems:
[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)

The simple advantage of Kickstart is that your hardware and software packages can change dramatically, without requiring any changes (or only very minimal changes) to the Kickstart setup.  So it is the only way to deploy many thousands of systems over multiple years without going stir crazy.

A similar system is called Replicator, but I have not used it, so I cannot vouch for it:
[http://replicator.sourceforge.net/](http://replicator.sourceforge.net/)

---

### Post by brucewagner on 2010-04-17
Very interesting.  So many options.  Remastersys.  Kickstart.  Replicator.

I wonder...  Does anyone know what Canonical's professional services uses if/when they do an install of 1000 Ubunutu desktops for a Fortune 500 company...?

---

### Post by lovinglinux on 2010-04-17
> **brucewagner said:**
> 
[LIST]
[*]Changing / adding some Compiz Fusion settings
[/LIST]

Compiz has an option to export the profile. I'm not using Compiz right now, but I always used that feature when installing new Ubuntu versions. It should be somewhere in the general preferences.

> **brucewagner said:**
> 
[LIST]
[*]Adding some Firefox Add-Ons
[/LIST]

Backup you extensions with [FEBE](https://addons.mozilla.org/en-US/firefox/search/?q=FEBE), then create a single installation package for all extensions with [CLEO](https://addons.mozilla.org/en-US/firefox/search/?q=CLEO).

Nevertheless, I think the best option would be to create a clean Firefox profile, configure it the way you want for all machines, then simply export the entire profile with FEBE. Install FEBE on the other machines and restore the backup.

> **brucewagner said:**
> 
[LIST]
[*]Adding some Firefox "Customize" icons within Firefox to the top to toolbar area.
[/LIST]

You can copy localstore.rdf from Firefox profile.

---

### Post by k3lt01 on 2010-04-18
You may want to [take a look at this]("http://www.informatik.uni-koeln.de/fai/") and [this]("http://m23.sourceforge.net/PostNuke-0.750/html/index.php?newlang=deu"). I haven't used either but may try it when Lucid is released

---

### Post by HermanAB on 2010-04-18
I have been using Kickstart for many years and installed many thousands of machines.  It really shines when you get a new batch of machines with different hardware, a new Linux release and a next day delivery deadline - you run Kickstart with some trepidation on twenty machines in parallel and it 'Just Works' - Woohoo!

You should try Replicator and report back - maybe it works too.

---

### Post by brucewagner on 2010-04-18
OK, Herman. :)  You've convinced me to try Kickstart. 

However, in my case, these machines will each be in different remote locations.  Can you tell me how to use Kickstart to do an automated install remotely.  Perhaps by creating a boot CD which either contains the ks.cfg file, or obtains it via my web server (http)...?  And then obtains the install ISO for Ubuntu via my web server as well (http)...?

How would I create the boot CD?  Would I then use a tool like masteriso to add the ks.cfg file to it?  Or could it be retrieved from my web server on the fly?

I'm scouring Google and finding very little information about using Kickstart to install Ubuntu desktops.

---

### Post by k3lt01 on 2010-04-18
Bruce, just go to the kickstart page, I think its Anaconda-kickstart from memory, and read up on it, all your answers can be answer there from my experience.

---

### Post by HermanAB on 2010-04-18
I make a central FTP server for the repository and then install over the network by booting off a CD or USB stick.  It is also possible to do a netboot.  

This is very easy to do with a RPM based distribution.  One simply does one manual install by booting off a CD/memory stick, then copy the file created by the installation system and use that as a starting point.  With Ubuntu it is not so easy, since there is no such file to use as a starting point.

Unfortunately, Debian is simply not designed for mass deployments, so some degree of pain is unavoidable.

---

### Post by m23project on 2010-12-02
Hi,

the new version of m23 the OpenSource Linux software distribution and management system was released a few days ago. It has official support for Ubuntu 10.04 LTS, Kubuntu 10.04 LTS and Xubuntu 10.04 LTS now.

There are many functions e.g. for mass installations. If the functionality doesn't match your requirements, you can extend it by scripts, that are written in the integrated script editor. There is a package builder included, that can convert archives to installable packages. This could be a possibillity to deploy your settings.

So it may be what you are searching for ;)

Short info about what you can do with m23:

m23 is a free software distribution system licensed under the GPL, that installs and administrates clients with, Debian, Ubuntu, Kubuntu and Xubuntu. m23 is controlled via webbrowser. The installation of a new m23 client is done in only three steps and the integration of existing clients is possible, too. Group functions and mass tools make managing a vast number of clients comfortable. Client backup and server backup are included to avoid data loss. With the integrated virtualisation solution, m23 can create and manage virtual m23 clients, that are run on real m23 servers and m23 clients. Scripts and software packages (for installation on the clients) are created directly from the m23 webinterface.

For more information visit the project page at SourceForge: m23.sf.net

PS. We are searching for testers of the LTS target plattforms. If you are interested: Please grab the new version form the project page and install some clients with is. Please report errors and inconsistence to the forum under m23.sf.net. Thank you!

---

### Post by gg234 on 2010-12-03
Try one of these they are very good

bcfg2 - [http://trac.mcs.anl.gov/projects/bcfg2](http://trac.mcs.anl.gov/projects/bcfg2)

puppet - [http://projects.puppetlabs.com/projects/puppet/wiki](http://projects.puppetlabs.com/projects/puppet/wiki)

cfengine - [http://www.cfengine.org/pages/what_is_cfengine](http://www.cfengine.org/pages/what_is_cfengine)

---

