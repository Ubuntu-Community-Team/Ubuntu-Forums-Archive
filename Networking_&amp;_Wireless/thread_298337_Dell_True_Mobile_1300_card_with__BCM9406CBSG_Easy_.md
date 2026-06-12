---
title: "Dell True Mobile 1300 card with  BCM9406CBSG Easy Fix"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by diverjustjim on 2006-11-12
Xubuntu 6.10

Hi all I have a fix for Dell True Mobile 1300 card with  BCM9406CBSG. I am using ndiswrapper which I installed from Synaptic Package Manager,

ndisgtk
ndiswrapper-common
ndiswrapper-utils
ndiswrapper-utils-1.1
ndiswrapper-utils-1.8

after install you should find in your System Menu "Windows Wireless Driver" use this to install your .inf file.
This is where the fun begins I used the  bcml5.inf  file that came with my Dell True Mobile CD it does not work with Linux on Ubuntu, Mandriva and others. So I unistalled it. I then borrowed a bcmwl5-94306.inf  from a Linspire/Freespire install. Installed it with  "Windows Wireless Driver" took out my wireless card pluged it back in and hey presto it started to shine and flicker. Went to networking and activated it. Works with full signal. 

So it would seem that the same .inf file will not work for both linux and windows. I have opened both files to view and they are totally different.

I could not get my card to work with bcm43xx-fwcutter so I have blacklisted it in,

/etc/modprobe.d/blacklist

# bcm43xx
blacklist bcm43xx

The above might give light to other problems.

All the best.

Jim

---

