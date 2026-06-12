---
title: "Ubuntu 11.04 install wireless detect problem"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by jplyons on 2011-07-20
Hi 

I have just installed Ubuntu 11.04 on an old dell Inspiron 1501.
the wlan is broadcom bcm4311 802.11b/g wlan .

Nothing wireless is detected at all, anywhere.

I have found a lot of confusing advice searching the web. I
thought I would try here.

Also, the wired connection works and another pc(running win7) 
also works with wireless. The wireless router is netgear wgr614.

Any ideas or places you can direct me?

Thank you very much.
Joe

---

### Post by MG&amp;TL on 2011-07-20
Have you tried 'additional drivers'-you may need to install a driver.

Press <super> then type 'additional' and look for the padlocked circuit board emblem. Launch that and then install what it recommends.Reboot. Of course, if there's nothing there, it gets more complicated. Post if they're not there.

---

### Post by wildmanne39 on 2011-07-21
Hi, here is a link that tells you how to get that card working if you need more help please post back, and if you get it working please mark thread solved.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wep940 on 2011-07-21
I haven't followed the link wildmanne39 provided, so this information may already be known to you.
 
Broadcom cards used to be a little tricky to get working a few releases ago.  Most had to resort to a tool called ndiswrapper.  For anyone who may be reading this thread and his seen threads for the need to use ndiswrapper, please be aware that this is not normally the case now with Broadcom adapters.  However, some drivers are restricted, in that they aren't open source, so they are not included with Ubuntu by default.  There is supposed to be an open source driver now for the Broadcom adapters, however most need to go through at least a minimum of the following steps:
 
- be sure your PC is connected by hardwire to the internet
 
- open a terminal (sometimes called command line because it is text based) via applications/accessories/terminal
 
- type:
 
sudo apt-get update <press enter>  When prompted for a password just enter your normal password.  It will not show on the screen but it is being accepted - just press enter after the last character of your password has been typed.  This may run a little while, so please wait for it to finish.
 
- next, go to system/administration/additional drivers.  This will start a search for a driver and may take a little while.  When it finishes the search there will hopefully be a driver showing in the window as available and all you need to do is click on the enable.  You may see more than 1 driver available - I *think* but not positive you will need the STA driver.
 
- wait about a minute or so, then click on network manager to be sure wireless is enabled.
 
- you should now be able to see any available networks and be able to connect
 
If you don't have a hardwire connection, there are options to use tools already available on the LiveCD or installation media for what is called the firmware cutter and associated.  There is also a large all-inclusive firmware file that can be downloaded on any PC and brought to the PC in question.
 
So, if you don't have a hardwired network connection, please post back and we'll give you the info on how to get this working.

---

### Post by linuxman94 on 2011-07-21
See this wiki page for several ways to get it to work.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by wildmanne39 on 2011-07-21
Hi, the problem is that the dirvers for the broadcom cards do not work in natty if they did wep940 method would be exactly right, he has done a great job with the instructions but you will need to use the link I gave you.

---

### Post by wep940 on 2011-07-21
> **wildmanne39 said:**
> Hi, the problem is that the dirvers for the broadcom cards do not work in natty if they did wep940 method would be exactly right, he has done a great job with the instructions but you will need to use the link I gave you.
 
You know, I've never tried a Broadcom adapter with 11.04, so I sure didn't know this! Thanks for enlightening me!
 
Dave ;)
 
EDIT:  You know, I followed that link and indeed I have used that before - I forgot I tried 11.04 on this laptop before I just stuck to Windows with it.  It does have a Broadcom card, and that link with the firmware cutter and the "all" firmware package is what I was trying to mention in the paragraph about "if you don't have internet access".  I just had completely forgotton I did try this and it worked great!  For myself, my adapter required the firmare cutter, etc., but still said the firmware was missing until I used the "all" firmware on that link.  I don't remember, but it may have even been you who pointed me to that link to get it to work back then!  Again - thanks!  Dave ;)

---

### Post by jplyons on 2011-07-21
> **MG&TL said:**
> Have you tried 'additional drivers'-you may need to install a driver.

Press <super> then type 'additional' and look for the padlocked circuit board emblem. Launch that and then install what it recommends.Reboot. Of course, if there's nothing there, it gets more complicated. Post if they're not there.
Hi,
Thanks for your reply. I found what I needed in [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

I hope this helps all who need it.

---

### Post by wildmanne39 on 2011-07-21
Hi, your welcome I am glad it is working.

Also I wanted to add a little more clarity to my last post about the broadcom drivers not working that install when you install them through additional drivers.

The problem is it installs the sta driver that does not work and in the link I provided you actually install broadcom drivers from synaptic but it is not the sta driver that one has to be uninstalled first, so it is not all broadcom drivers. I thought I had better make myself clear.

Would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by jplyons on 2011-07-24
Hi,
I am still concerned about my broadcom bcm4311 802.11b/g wlan driver not
detecting my wireless router.

I have success when I do  the following:

Remove these (below) using synaptic package manager.
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I then reboot.
I then re-install... 
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I reboot again and wireless networks are detected. I just connect.
It works!

Then I shut down. When I reboot wireless networks are gone!
If I do the above steps all over again, wireless comes back.

I lose it every time I re-boot after a successful install.
What is happening? Is there a login script I need to modify?

Where is the 11.04 login script.

Thank you for any help. I cannot close this issue yet.
Joe

---

### Post by wildmanne39 on 2011-07-24
Hi, uninstall the bcmwl-kernal-source and make sure that the sta driver is not installed using synaptic.

---

