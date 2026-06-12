---
title: "Atheros AR5006EG won't work in Gutsy under ndiswrapper, can't get madwifi"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by missingno on 2007-10-21
Every driver .inf I try with ndiswrapper installs fine and ndiswrapper says it recognizes the hardware, but I can't actually connect wirelessly under the network config panel. Google also pointed to Madwifi, which says on its site that it's available in the Ubuntu repositories, but I can't find it among any of the Gutsy repositories in Synaptic. So I tried downloading it off the site and following the readme, which said to cd to the directory and type 'make'. That just spit out several pages of errors. How can I get this chip working?

---

### Post by Jimerson on 2007-10-25
I FINALLY got my Atheros AR5006EG wireless card working on my Acer 5610z by following this thread. [http://ubuntuforums.org/showthread.php?t=580672&page=2](http://ubuntuforums.org/showthread.php?t=580672&page=2)

Go down to the fourth post and follow his instructions.
Be aware that some of the code he asks you to copy and paste will not work because the version number is missing or the folder is named something else.. so if you find a bit of code not working it's probably because he replaced a version number with an  * or something. 

At the end of his instructions he sends you to another thread, be sure to follow those instructions as well or your AR5006EG won't work. (he also has a bit of code that may need to be altered by you to reflect your actual directory and file/folder names)

Good luck! If you can't get it to work let me know and I'll try to help you.. I know how frustrating this process can be.

---

