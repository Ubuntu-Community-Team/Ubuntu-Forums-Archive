---
title: "network connections"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by ianmaxwell on 2008-12-24
in the top right of my screen, there is a network icon of two computer screens. when i right click on the icon i no longer get the option to enable wireless networking. i used to. how can i change it to enable wireless networking?

thanks

---

### Post by ianmaxwell on 2008-12-24
also, there is no wireless network option in network settings

---

### Post by ercferret18 on 2008-12-24
what does the output of "iwconfig" say?

---

### Post by ianmaxwell on 2008-12-24
ian@ian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by ianmaxwell on 2008-12-24
i think before there may have been a wlan0 there aswel, but it isn't there now

---

### Post by ianmaxwell on 2008-12-24
i was trying to get wireless to work in the first place to this is pretty annoying
any help from anywhere?

---

### Post by retskrad on 2008-12-24
Iammaxwell, I have exactly the same problem as you. UI have tried wubi, still no internet. I have tried live cd, still no internet. I also got wired and networking doesnt work in ubuntu, but it works in windows.. still I can't find the solution..

---

### Post by ugm6hr on 2008-12-24
Give more info: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

### Post by anewguy on 2008-12-24
If your wireless is not showing at all, it probably means that there is no driver currently loaded for it.  I will assume unless you say otherwise that your wireless adapter is internal - not something like USB.

Open a terminal window (Applications/Accessories/Terminal) and do the following:

lspci <press enter>

copy down what comes from that (a copy and paste would be best) and we can go from there to try to find a driver for you.

I was just as "guilty" of this when I started with Linux, so I'm making the following comment not at you but as a general word to all newbies to Linux, and Ubuntu in particular:

- If something like wireless "works" in Windows but you see no sign of it in Ubuntu (installed or LiveCD), don't give up!  The manufacturer supplied a driver for the adapter for Windows.  Ubuntu comes with some, but by no means any where near all, wireless drivers.  Sometimes they work, sometimes they don't.  But Linux/Ubuntu provides a package called ndiswrapper which allows some Windows network/wireless drivers to be used in Linux/Ubuntu.  You'll see wireless and video adapters as the 2 major "problems" people run into with Linux/Ubuntu.  This is because most of the hardware manufacturers do not provide support for Linux (is this a licensing ploy by Microsoft?) because of 2 factors:  Linux/Ubuntu is free and based on open software - software whose source is available to all and can be openly modified - and we know they don't want to "give away" anything; the 2nd factor is the installed base (e.g., demand) of the OS and therefore the amount of effort they want to extend on it.

So, don't give up - post back the lspci.  If using USB, post back lsusb.  If possible, post back the maker/model of your adapter.

Dave :)

---

### Post by ianmaxwell on 2008-12-24
yeah i got the wireless option back up now.
but i'm having a lotta trouble installing ndiswrapper.
i've followed loadsa guides but keep getting errors.

---

### Post by anewguy on 2008-12-24
If you are having problems installing ndiswrapper, please keep this in mind:

(1) you do not under normal circumstances need to compile ndiswrapper.  There are some older post out there that say you need to, but it normally works fine with the package from synaptic package manager

(2) if you are having trouble trying to download it, it is also available for install on the LiveCD in the /pool/main/n folder.  Just click on it to install it.  Ndisgtk is also in the same place, and I would recommend you try installing it also.  It is a gui'd front end to ndiswrapper, so if you are having trouble with the command line stuff, try it.

Post back with problems/questions.  Being the holiday, I'll be away for a while tonight, but will check back late.

dave :)

---

### Post by ianmaxwell on 2008-12-24
thanks much.
i installed those three things from the ubuntu cd and  am still getting the error 'Could not find a network configuration tool'
is there a specific order which i should be following when installing ndis?
what is the network configuration tool?
would a fresh install be useful as i was messing around with the kernal earlier and maybe that has had some effect...
thanks again for your help.

ian

---

### Post by anewguy on 2008-12-24
Well, I don't know anything about mesing around with the kernel - did that for years on big machines but have been away from that for too long and Linux is just a different animal, so I don't know if any messing around might have hurt it.  

If you don't mind just installing again, by all means do so.  Myself, and I'm sure countless others, have done so a lot more than just 1 time. 

Wish I could help you more, but I'm not exactly what's going on at this point.  If you do a fresh install and can direct connect without the wireless, post back and I'll see if I can help you or not from a fresh start.

Happy holidays!

Dave :)

---

