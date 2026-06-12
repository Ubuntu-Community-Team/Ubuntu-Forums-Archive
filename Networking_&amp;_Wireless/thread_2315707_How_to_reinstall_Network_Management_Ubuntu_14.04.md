---
title: "How to reinstall Network Management Ubuntu 14.04"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by simon114 on 2016-03-01
Hi there. 
For some reason Wired Network stopped working on my pc.
I looked up how to reinstall - So I started by downloading the deb Package as I knew that when I uninstalled I would be unable to connect to the internet.
With the Package downloaded, I continued to Uninstall network management on ubuntu 14.04
I then Clicked the .deb package to reinstall, which sent me to the software center in ubuntu... but obviously there must be files missing in the deb file. so now I have NO internet at all on ubuntu.

My question is

I have no Internet on Ubuntu partition, I do have internet on the windows 7 partition. where can I download the complete network deb package for ubuntu 14.04 with windows and then using ubuntu copy the deb file to ubuntu partition and install from ubuntu to recover network to ubuntu. 

Thank you - I hope someone can please help as i no longer use windows and a loving the whole ubuntu experience. thankyou community

---

### Post by houstonbofh on 2016-03-02
Get the install CD and mount that as a repository.  That will help you find the missing debs.  In the future, you can reinstall from the command line without actually removing or downloading the package... [http://manpages.ubuntu.com/manpages/raring/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/raring/man8/dpkg-reconfigure.8.html)

---

### Post by simon114 on 2016-03-02
Thanks...you know...I have no idea how I fixed it. I think it was a mix of downloads. And a post I found about -- bootstrap. Or something like that...managed to get internet somehow using live CD and then with bootstrap something or other did a sudo apt-get etc etc rebooted and it worked. I know it's not a technical reply..at all...but in the madness of getting  it fixed..I can't remember what I did. But it is fixed. Oh yeah And somewhere I had to change  conf file from managed false to managed true And also another conf file add the google DNS ...

---

