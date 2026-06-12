---
title: "Remote Desktop software"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by wishingstar on 2010-08-10
Hi,

I have a few questions regarding remote desktops. I have an internet connection at work (on all the time), and similarly at home. Is there a software i can download (whether in the software center or elsewhere on the web) that enables me to control my home computer from work? I would like to be able to control my Jdownloader downloads and move/copy files.

Also, is there a remote desktop software that allows you to do the following:

1- Move files to an external drive connected to your remote computer, in this case a backup drive in my home?
2- Control a VM in VMware or VirtualBox on my home pc?
3- Does it work while my home computer is 'locked' with "CTRL+ALT+L" or does it need to be unlocked to be able to control it, also, if someone is sitting behind my home pc, can they work on it as a different user, or would the things i'm doing take up the screen?

Sorry if some of my questions are noobish, but i don't have any experience in controlling a remote desktop, i've never used one before :)

Thanks for the help in advance.

PS: My machine at work is a windows vista machine, while my home machine runs Lucid, in case that makes a difference.

---

### Post by bodhi.zazen on 2010-08-10
ssh will do all those things.

ssh is command line only, but you can control your VM with the command line.

Make sure you secure your ssh server (use keys, disable passwords).

On windows , use putty

---

### Post by dca on 2010-08-10
If it's at home, be sure to make any necessary adjustments, precautions, etc to your home firewall a'la VPN or port forwarding.
 
If you use Windows @ work and Linux @ home, then use PuTTY as suggested.  Or Ubuntu offers Vinagre and tsclient to start a VNC or RDP session.

---

### Post by hudsonl on 2010-08-10
> **wishingstar said:**
> Hi,

I have a few questions regarding remote desktops. I have an internet connection at work (on all the time), and similarly at home. Is there a software i can download (whether in the software center or elsewhere on the web) that enables me to control my home computer from work? I would like to be able to control my Jdownloader downloads and move/copy files.

Also, is there a remote desktop software that allows you to do the following:

1- Move files to an external drive connected to your remote computer, in this case a backup drive in my home?
2- Control a VM in VMware or VirtualBox on my home pc?
3- Does it work while my home computer is 'locked' with "CTRL+ALT+L" or does it need to be unlocked to be able to control it, also, if someone is sitting behind my home pc, can they work on it as a different user, or would the things i'm doing take up the screen?

Sorry if some of my questions are noobish, but i don't have any experience in controlling a remote desktop, i've never used one before :)

Thanks for the help in advance.

PS: My machine at work is a windows vista machine, while my home machine runs Lucid, in case that makes a difference.


**FreeNX** ....

I've been using it on multiple sites for long time ... VERY reliable and fast.

Built on top of ssh connection ... so it's secure. (recommend changing the port number, as mentioned in the docs)

I can connect Windows to Linux and Linux to Linux ... no problem.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by wishingstar on 2010-08-10
Thank you all for responding so quickly, please bear with me.
As I'm relatively new to linux, i'm slowly picking up terminal commands, and usually shy away from non-GUI software. so installing SSH just like that would be hard for me to operate, i think (unless there is a step-by-step manual page). The FreeNX frontend sounds good, there's still commands as per the ubuntu wiki page in Hudsonl's post, would i be able to run it safely and efficiently if i use that FreeNX page step by step through copy and paste? should i change port numbers? I have no idea!

Also, I run Guayadeque as my main music player in my ubuntu machine at home, would i be able to stream media through my work speakers? how? and what commands to use to control VM from work via SSH or FreeNX? (I guess a manual page for either would be the solution to all my questions at this point, so i anyone has one for reference, please direct me to it!)

Thank you all, your help is much appreciated :)

---

### Post by bodhi.zazen on 2010-08-10
> **wishingstar said:**
> Thank you all for responding so quickly, please bear with me.
As I'm relatively new to linux, i'm slowly picking up terminal commands, and usually shy away from non-GUI software.

IMO this is a common mistake. Do not fear the command line, jump in and start learning it, especially via remote connections.

Look at ssh, screen, and linuxcommand. The first few pages are priceless, you can skim the scripting section and come back to it.

Review grep, cat, sed, find, and awk. These command may seem obscure at first, but they will help.

Tons of tutorials on screen (screen is in the repos) , but look here:

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Apostolique on 2010-08-10
You may also like teamviewer. [http://www.teamviewer.com/](http://www.teamviewer.com/)

This is what I use and I never got any problem with it. There is a version for Linux, Windows, Mac and iPhone and each one is compatible with the others so you can do cross platform connections.

Hope that helps.

Edit: [http://www.teamviewer.com/download/](http://www.teamviewer.com/download/)

---

### Post by wishingstar on 2010-08-11
Thank you all for the pointers, i will give it all a try, especially the cross-platform ones, as i think they would provide the best compatibility, one silly final question though

When bohdi.zazen said "Look at ssh, screen, and linuxcommand." Does that mean i go to terminal and type: "ssh --help"? or "man ssh"? and what about the others?

Thanks for the help everyone :)

---

### Post by bodhi.zazen on 2010-08-11
> **wishingstar said:**
> Thank you all for the pointers, i will give it all a try, especially the cross-platform ones, as i think they would provide the best compatibility, one silly final question though

When bohdi.zazen said "Look at ssh, screen, and linuxcommand." Does that mean i go to terminal and type: "ssh --help"? or "man ssh"? and what about the others?

Thanks for the help everyone :)

No, google search and read those topics , the documentation is quite good and you will get a hang of it quickly.

I also gave you some links to get started.

Learn to read the man pages. They appear quite cryptic at first, but it is similar to riding a bike, once it clicks you are good to go.

post back if you have specific questions.

---

### Post by hudsonl on 2010-08-11
> **wishingstar said:**
> Thank you all for responding so quickly, please bear with me.
As I'm relatively new to linux, i'm slowly picking up terminal commands, and usually shy away from non-GUI software. so installing SSH just like that would be hard for me to operate, i think (unless there is a step-by-step manual page). The FreeNX frontend sounds good, there's still commands as per the ubuntu wiki page in Hudsonl's post, would i be able to run it safely and efficiently if i use that FreeNX page step by step through copy and paste? should i change port numbers? I have no idea!

Also, I run Guayadeque as my main music player in my ubuntu machine at home, would i be able to stream media through my work speakers? how? and what commands to use to control VM from work via SSH or FreeNX? (I guess a manual page for either would be the solution to all my questions at this point, so i anyone has one for reference, please direct me to it!)

Thank you all, your help is much appreciated :)


FreeNX ... creates a new session when you login ... so it's all GUI and you would like that :)  

You should be able to step thru the docs without a problem.  Not sure what version of Ubuntu you are on.  I think I started using FreeNX back on 8 or 9 and I'm currently running 10.04 and FreeNX still works GREAT.

Make sure (as pointed out in the Docs ... that SSH is installed and running first)
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Speakers ... will "play at the house" ... never tried to get it to stream to my work speakers.  There may be a way ... though I've never tried.

You need to install on the "server" at home
 1. SSH 
 2. FreeNX server

You need to install at work PC
 1.  NX Client for Windows  ([http://download.cnet.com/NX-Client-for-Windows/3000-7240_4-10327975.html](http://download.cnet.com/NX-Client-for-Windows/3000-7240_4-10327975.html))

If you use custom keys ... then you need to copy / share it with the PC at work.  It all sounds a little confusing, but if you follow the Docs ... it's not bad.  Works well and it's secure.
    

Good Luck

---

### Post by wishingstar on 2010-08-11
Thanks a lot everyone, i'm gonna go for FreeNX/SSH combo, and report back if i have any problems :)

I'm marking this as solved for now, Thank you!

---

