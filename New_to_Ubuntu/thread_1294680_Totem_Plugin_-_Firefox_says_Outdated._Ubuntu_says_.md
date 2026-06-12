---
title: "Totem Plugin - Firefox says Outdated. Ubuntu says NOT ! WTF !"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by CSHANKY on 2009-10-18
Checked the plugin via Firefox.com:

The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams. 					 					_**[COLOR=Red]Outdated Version[/COLOR]**_

So I did =>
~$ sudo apt-get install totem-gstreamer
[sudo] password for XXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]**totem-gstreamer is already the _newest version_.**[/COLOR] [COLOR=Red](WTF[/COLOR] :confused:)
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[COLOR=Magenta]Can someone help?[/COLOR]
Thanks

---

### Post by sync on 2009-10-18
Your Firefox may be outdated?
I would suggest typing 'sudo apt-get update', then 'sudo apt-get upgrade'.  This will go ahead and upgrade any software that has a newer version available.

---

### Post by zero-n on 2009-10-18
yesterday i have tried firefox plug-in  & ii had the same issue  as you my totem is the latest version.

can anyone help ?

---

### Post by CSHANKY on 2009-10-18
Didn't work... :confused:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_CA          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_CA                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_CA   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty Release.gpg                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by sync on 2009-10-18
According to the Ubuntu Support Page: ([https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04%20%28Jaunty%20Jackalope%29](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04%20%28Jaunty%20Jackalope%29)), you should try installing the Ubuntu-Restricted-Formats first.

Try typing this at the terminal:
'sudo apt-get install ubuntu-restricted-extras'

---

### Post by Sir Jasper on 2009-10-18
Hi,

There is an outside chance that using ¨Make All Compatible¨ under the ¨Tools¨ menu of the Firefox add-on MR Tech Toolkit may work.

My regards

---

### Post by CSHANKY on 2009-10-18
Sir: :)

You are talking to newbie's here....could you give us some step-by-step instructions please?

Thanks

---

### Post by Sir Jasper on 2009-10-18
Hi,

If your question was addressed to me try clicking on either or both of the links below (copied from a suggestion by Lynx in another forum). 

My regards

I would suggest the following Add-on, which makes many things easier including updates management  All-in-One Sidebar (AiOS)

Another healthy Add-on for our arsenal is Mr Tech Toolkit
With this one you can do management / installations / backups / etc. (Auto-Archiving will be back soon - see note there)
But one of the interesting features is: it can make some currently incompatible Add-ons (due to delays in development) completely compatible (tested on EverNotes Add-on)
Added:
The links may not be effective - if not google and install.

---

### Post by CSHANKY on 2009-10-18
> **Sir Jasper said:**
> Hi,

If your question was addressed to me try clicking on either or both of the links below (copied from a suggestion by Lynx in another forum). 

My regards

I would suggest the following Add-on, which makes many things easier including updates management  All-in-One Sidebar (AiOS)

Another healthy Add-on for our arsenal is Mr Tech Toolkit
With this one you can do management / installations / backups / etc. (Auto-Archiving will be back soon - see note there)
But one of the interesting features is: it can make some currently incompatible Add-ons (due to delays in development) completely compatible (tested on EverNotes Add-on)
Added:
The links may not be effective - if not google and install.
Thanks, Sir....

I didn't find any links in your message, but it must be me. Will Google.....

---

### Post by CSHANKY on 2009-10-18
> **Sir Jasper said:**
> Hi,

There is an outside chance that using ¨Make All Compatible¨ under the ¨Tools¨ menu of the Firefox add-on MR Tech Toolkit may work.

My regards

I installed Mr Toolkit....couldn't find any such option.

---

### Post by Sir Jasper on 2009-10-18
Hi,

Here is a screenshot (see red pointer) with both the sidebar an MR  Tech added:

My regards

---

### Post by CSHANKY on 2009-10-18
> **Sir Jasper said:**
> Hi,

Here is a screenshot (see red pointer) with both the sidebar an MR  Tech added:

[[img]http://i.imagehost.org/0662/Screen.png[/img]](http://i.imagehost.org/view/0662/Screen)

My regards
Thanks ! Will try and revert...right now on my "trusted" windows laptop ;-)....been wrestling with Ubuntu for hours...need a break. :)

---

