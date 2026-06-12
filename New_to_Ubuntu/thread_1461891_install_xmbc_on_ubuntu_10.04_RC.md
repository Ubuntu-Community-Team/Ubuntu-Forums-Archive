---
title: "install xmbc on ubuntu 10.04 RC"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by computerguts on 2010-04-24
I recently installed ubuntu 10.04 release candidate and it runs great, so far there have been no bugs that I have run into. The only problem is that I can't seem to install xmbc. I went the the xmbc website and they said that the xmbc release packages for ubuntu 10.04 have been avliable for quite sometime. I go through the steps using the command line but I can't seem to get xmbc to install. When I go to the ubuntu software center and try to download xmbc it says sorry, and what ever the name of the package is after it then it says is not avliable for this type of computer (i386)

How could I resolve this problem, any help would be greatly appreciated.

---

### Post by Georgia boy on 2010-04-24
Sorry, don't have a solution but do have a question. The RC is out already? Thought that it would be out the 29th of this month. Did they sneak it out early on us?

Tom

---

### Post by bowens44 on 2010-04-24
The release is on the 29th, this is the release candidate.

---

### Post by computerguts on 2010-04-24
go to ubuntu.com and download the RC or if you want to wait five days you can download the official release.

---

### Post by Georgia boy on 2010-04-24
My bad. Long day and mind wasn't thinking. Sorry bout that. Was thinking that it was the final release.
Tom

---

### Post by iMisspell on 2010-04-25
> **computerguts said:**
> How could I resolve this problem, any help would be greatly appreciated.

I followed the site directions with Lucid Beta2 and it worked for me.
[http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

```

sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update

```

    * Click System -> Administration -> Synaptic Package Manager
    * Click "Reload"
    * Search for "xbmc"
    * Mark xbmc and xbmc-standalone for installation and mark additional changes when prompted.
    * Click "Apply" and agree to the changes after reading them. 

    * First, download the SVN Repo Installer from:
    * [http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip](http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip)
    * Extract it to the ~/.xbmc/plugins/programs directory.
    * Select XBMC Media Center: Applications -> Sound & Video -> XBMC Media Center
    * Scroll down to Programs.
    * Select program plugins.
    * Select SVN Repo Installer
    * Select xbmc-addons
    * Select plugins
    * Choose the plugins that you want to add (i.e., videos)

---

### Post by computerguts on 2010-04-25
thanks, I will try that. If it does not work I will paste the code on this thread and go from there.

---

