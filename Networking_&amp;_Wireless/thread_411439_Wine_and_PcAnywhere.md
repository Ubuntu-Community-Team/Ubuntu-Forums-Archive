---
title: "Wine and PcAnywhere?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-04-16
Has anybody had any success running PcAnywhere through Wine?

---

### Post by az on 2007-04-16
What's the difference between that and VNC?

VNC is included in Ubuntu.

---

### Post by lsutiger on 2007-04-16
All of our clients are using PcAnywhere....it would take A LOT of time to install and configure VNC on all of the computers.
I am looking for a solution to continue using the paid for software for the clients. At the moment, I RDP into my ofice maching and use PCAnywhere from there. Not too bad, but a bit of a hassle.
Thanx for your reply!

---

### Post by steven_vo on 2007-07-03
I have some problem, can you help me, guys 
--------------------------------------------------------
1/
I am using Ubuntu 7.04 Feisty Fawn.
I installed Wine and then pcAnywhere.
But the problem is, in the pcAnyWhere, I could not find the the Remote tools

2/
I removed Wine with **sudo apt-get --purge wine**
But then while I install it again using both methods: 
a/  **sudo apt-get install wine**

Or  using
 
b/ **wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -**
then
**sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list**

--------------------------
But then, I could not remove the pcAnywhere on Wine. It was just be in the Wine 
I dont know why ?
Can you explain for me? Thanks

3/ 
Can i install LogMeIn on Ubuntu and LogMein on XP , so then they can be connected?
They are in separate network
And how do i config it on Ubuntu

--------------------+ Thank you very much-------------------------------------------------
:popcorn:

---

### Post by VorDesigns on 2007-07-10
pcAnywhere has a web remote that will run fine through a java enabled browser.
I just got this running by adding the following to my installation:
```
apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```
You will need to add sudo if you don't run interactive root sessions.

The web remote became available in 10 or 10.5, I don't know if it is available in new installation.  There is also a host install for Linux.

The down side is that you don't get file transfer and at least for the Dapper desktop, you need to change the ctrl-alt-d hotkey to do nothing so that you can log into a locked Win system.  the Web tfs is buggy and the keyboard may become unresponsive on the host unless you send the ctrl-alt-del via the ctrl-alt-d keyboard combo

---

### Post by PaganBlasphemy on 2008-02-06
> **steven_vo said:**
> I have some problem...
..., in the pcAnyWhere, I could not find the the Remote tools

...But then, I could not remove the pcAnywhere on Wine. It was just be in the Wine 



I'm still working on this myself, but what I read on the Wine app list was that you should install the 'remote only' version of the application.  

As far as removing PCA, I couldn't do that either, so I just deleted my .wine directory and then re-configured Wine (deleting .wine removes all of the programs you have installed, all of the changes you made to the Wine configuration, and so on).  The .wine directory is found in your /home/USER/ directory, but it is hidden so you'll need to select "View" > "Show Hidden Files" to see it.  So, no need to uninstall and reinstall Wine itself, just the .wine directory.

If I figure out how to get the remotes working, I'll update this post or add a new post below.

---

### Post by carnivore1 on 2008-02-14
Anyone have any luck with this yet. I too am forced to use pcAnywhere for work and dont have the option of using another remote package so i have to get this working some how or <insert cringe here> reinstall XP :(

---

### Post by wizkey on 2008-04-30
Symantec has a cross platform java implementation of PcAnyhere. It's included when you buy PcAnywhere now. It doesn't have all the features of the Windows client, but if you just need to get into the desktop, it will do the job. You might have to fight with it a bit to work with java under Ubuntu, I seem to remember having to fuss with it a bit, but got it running.

As far as older versions of the Windows apps running under wine, I got 10.5 working with some success under wine. I really didn't have to do anything other than run the install.

What doesn't work:

1) Watermarks. This causes some insane refresh issue. Doesn't really affect anything, but irritating. You can turn them off on the view menu.
2) Creating and editing remotes. For me, it just throws an exception. Already existing .CHF files work. Not really an issue for me, as I don't have very many customers using PcAnywhere anymore and just copied my existing files from the Windows partition.

What does work:

1) Connecting into hosts
2) File transfer. I was pleasantly surprised by this, since this didn't even work under XP, lol.
3) Copy and paste
4) Ctrl-Alt-Delete button

Haven't really had a need to try out everything else, since this is all I really need.

---

### Post by cejack on 2008-06-16
I've got PCAW 12.1 and want to see it work on Ubuntu 8.04...

When I run the following command:

sudo java -jar SetupLinuxMac.jar

I get the following errors:

WARNING: could not delete temporary file /tmp/ismp002/5723167
WARNING: could not delete temporary file /tmp/ismp002/7113152


Any ideas?  sudo java -jar SetupLinuxMac.jarI'm a newbie Ubuntu but pretty savvy and have got a lot of other stuff working so far.  

Any obvious thing I'm doing wrong to get this error?  

Thx in advance.

---

### Post by Mach1US on 2008-06-16
Quick reply ;
I have used logmein free from logmein.com for some time and outside of getting the simple point and click setup in xp i did not need anything else on ubuntu side.
All i need to do to log into my free account, log into my other xp system and to do so all you need is to type it into a browser and i'm connected , no need for anythig else , what so ever .
One thing, you need java for this to function but you need flash and java just for anything else out there so i'm sure you got this coverd.

---

