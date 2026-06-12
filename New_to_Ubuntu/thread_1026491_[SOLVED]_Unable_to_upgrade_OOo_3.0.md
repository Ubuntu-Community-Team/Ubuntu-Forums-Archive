---
title: "[SOLVED] Unable to upgrade OOo 3.0"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by ProgramErgoSum on 2008-12-31
To upgrade, I am following instructions from [How to Install OpenOffice.org 3.0 on Ubuntu 8.10]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml"). However, after adding the source line, I get a message about 'Partial Upgrade' (see screenshot below). When do I ask for 'Partial Upgrade', I get a message about authentication error (see screenshot below).

What am I missing ?

Advance wishes for New Year !

---

### Post by zika on 2008-12-31
don't go with apt-get or aptitude and don't accept partial! do it with Synaptic. add repositories, open Synaptic, Reload, Mark all updates and Apply. Answer Yes when asked about non-authenticated updates and ... enjoy!

---

### Post by abn91c on 2008-12-31
> **ProgramErgoSum said:**
> To upgrade, I am following instructions from [How to Install OpenOffice.org 3.0 on Ubuntu 8.10]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml"). However, after adding the source line, I get a message about 'Partial Upgrade' (see screenshot below). When do I ask for 'Partial Upgrade', I get a message about authentication error (see screenshot below).

What am I missing ?

Advance wishes for New Year !
it may be a previous package install failure, try sudo dpkg --configure -a followed by sudo apt-get install -f
also change repositories servers

---

### Post by ProgramErgoSum on 2008-12-31
Well, I *am* using Synaptic for upgrades.

> try sudo dpkg --configure -a followed by sudo apt-get install -f
What will that do ? And, will it affect non-OOo upgrades as well ? Just curious to know....

---

### Post by namdung on 2008-12-31
In terminal 
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

In *Synaptic Package Manger* Click on *Mark All Upgrades*. Look for any broken packages in *Custom Filters* and fix it.

Else try removing and reinstalling OO.

---

### Post by ProgramErgoSum on 2008-12-31
Things didn't work. So, I uninstalled OOo.

Synpatic shows the base-core. Selecting it and applying for changes does nothing. I mean, no message about downloading packages, installing them, etc. I tried adding the third party software source again and reload, etc. No luck.

What's wrong now ?

---

### Post by ProgramErgoSum on 2008-12-31
When I try to add OOo from Add/Remove, I get a message about dependency that is to be resolved using Synaptic. Ha !

Update Manager says system is up to date.

So, reboot the computer, perhaps ? ok, will try now.

---

### Post by ProgramErgoSum on 2008-12-31
Done that. No luck.

---

### Post by ProgramErgoSum on 2009-01-01
Maybe, I will have to learn to live with Ubuntu minus OpenOffice. Does not sound thrilling, but what else can I do...

---

### Post by Coder543 on 2009-01-01
If you aren't using 8.10, don't use the guide. If you are, this should work with no problems. I am using OOo 3.0.

---

### Post by 73ckn797 on 2009-01-01
> **ProgramErgoSum said:**
> Maybe, I will have to learn to live with Ubuntu minus OpenOffice. Does not sound thrilling, but what else can I do...


Follow this:
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org . You will need to select your language specific download file unless you wish the English version.

Created a directory in /home/name/whatever. **EDIT:** _*when extracting the files it will create it's own directories, DEBS and desktop-integration, within another directory with a cryptic looking name. You really only need to extract to /home or whatever you desire.*_

Extracted files using File Roller (default Gnome compression utility) to the created directory. Accomplished by double click on the downloaded file.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon.

---

### Post by ProgramErgoSum on 2009-01-01
hmm...I think, that should work. I will try out the next time I am in office.

BTW, isn't it possible at all to at least see what is wrong with Synaptic, etc. ? I mean, what if I get similar messages about conflict wrt some other s/w that I might be installing. Some pointers for investigation, if you could kindly provide....

---

### Post by hyperdude111 on 2009-01-01
That guide worked well for me. However if you NEED open office you can run the windows version in wine, It runs perfectly up to speed and with no errors.

---

### Post by ProgramErgoSum on 2009-01-02
Well.....guess what ?

When installing from Synaptic, I had the 'Download package files only' checked which did not initiate the download and installation. Unchecking it completed the download and installation.

Sorry people for diverting your time. :redfaced:

---

