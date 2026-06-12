---
title: "Synaptic packager, where did everything go? - Things already installed only showing"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by littlboz on 2010-05-29
Hello I know I've posted a lot of threads in the past 24 hours :p sorry about that.

I am using Macbook OS X 10.6.3 which I am dual booting with Ubuntu Karmic Koala

Whenever I go into synaptic package manager it only shows the things I've already installed (installed by default form installing Ubuntu OS that is). I can't find flash or wine.

---

### Post by drs305 on 2010-05-29
First make sure you have 'unfiltered' results. Click on the "Status" button in the left panel and make sure "ALL" is selected. If only "Installed" is selected you would see the results you are describing.

At the top right is a "Quick Search" window. If you type "flash" for instance, you should see results in the right hand panel - both installed and available packages which include "flash" in the name/description.

---

### Post by littlboz on 2010-05-29
nope, it remains blank...here is a screen shot 



now that I think about one of my packages was corrupted and I uninstalled it I believe it was this:
dksg-devel

or something similar to those jumble of letter. Maybe that will help idk

---

### Post by mkvnmtr on 2010-05-29
Try clicking reload.

---

### Post by drs305 on 2010-05-29
Open Synaptic via a terminal and also try to update your package lists/installs. It's possible a error in APT is causing problems and preventing Synaptic from correctly reporting what is available to it.

Please post any error messages from these commands:
```
gksu synaptic &
sudo apt-get update && sudo apt-get upgrade
```

Edit: As noted by *oldos2er*, you will need to close Synaptic before running the second set of commands.

---

### Post by littlboz on 2010-05-29
It didn't work. The last two lines have the "E:" thing. I have been noticing it on some other problems I've been having such as setting up my wireless.


matthew@Matt-Ubuntu:~$ gksu synaptic &
[1] 2600
matthew@Matt-Ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release [65.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [100.0kB]   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages [1,353kB]              
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [30.4kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [54.9kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [9,458B]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,519B] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages [7,969B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources [640kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources [3,270B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages [5,108kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages [185kB]         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources [116kB]          
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [221kB]       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [64.4kB]       
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]    
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [131kB]   
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [31.5kB]   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [10.9kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [4,932B] 
Fetched 11.0MB in 10s (1,096kB/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by littlboz on 2010-05-29
thought of one more thing that I should mention, how I made my partitions.

I partitioned 100GB from MAC OS X to create free space (using MAC OS X software). I then used the Ubuntu installation CD to partition 2GB of swap, then another for 10GB of / (root) and then the rest was for /home

---

### Post by oldos2er on 2010-05-29
Close Synaptic, then retry "sudo apt-get update && sudo apt-get upgrade"

---

### Post by littlboz on 2010-05-29
Okay I think it worked but I have this message, see screen shot. What is it and anyone have any suggestions on what I should do?

---

### Post by drs305 on 2010-05-29
> **littlboz said:**
> Okay I think it worked but I have this message, see screen shot. What is it and anyone have any suggestions on what I should do?

The screen shot link didn't show up in the post. Please edit that post or include it in a new one. You can also copy the error message from the terminal by highlighting it and putting it in memory with *CTRL-SHIFT-C*

---

### Post by littlboz on 2010-05-29
woops

---

### Post by drs305 on 2010-05-29
> **littlboz said:**
> woops

The screenshot is a message generated by an update to Grub. You are being asked if you want to keep your current Grub configuration files or want to accept the maintainer's (new) version.

Noramlly you would want to accept the new version, as it may contain improvements or fixes to bugs. If you want to accept the changes, arrow up to the top menu item then tab to OK and press ENTER.

If you have made a lot of customizations to the grub configuration files you may want to either make backup copies first, keep the existing local version (the default) or do a comparison (the lower options).

Select whichever option you desire and let grub update it's files. This may not be the cause of you synaptic problem, so afterward check synaptic. If it  is still not correct, close it and run the second line of commands again and see if you get any errors.

---

### Post by littlboz on 2010-05-29
It worked, thanks guys. Should I mark this thread as solved and if so how do I do it?

---

### Post by drs305 on 2010-05-29
> **littlboz said:**
> It worked, thanks guys. Should I mark this thread as solved and if so how do I do it?

Glad your problem has been resolved. 

You mark a thread SOLVED via the "Thread Tools" link at the top right of the first post. You can also remove the SOLVED tag if it becomes necessary.

Marking a thread solved let's helpers concentrate on unresolved posts and also assists those seeking help concentrate on threads that may offer a solution. Thanks for using this tool.

---

