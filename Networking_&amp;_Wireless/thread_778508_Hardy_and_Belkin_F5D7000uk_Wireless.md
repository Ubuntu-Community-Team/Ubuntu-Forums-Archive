---
title: "Hardy and Belkin F5D7000uk Wireless"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Hatticus on 2008-05-02
Hi all, complete Linux/Ubuntu newbie here, and am getting a bit stuck! 

I'm aware that this has probably been covered to death, but cannot find anything that I've been able to get to work... I've installed Hardy alongside Windows for now, but am unable to access the internet via my wireless. I have a Belkin F5D7000uk PCI card. I've tried following [these]("http://forums.jinx.com/topic.asp?TOPIC_ID=45498") instructions, but it tells me that ndiswrapper is not installed, enter 'sudpo agp-something install ndiswrapper-common' (can't remember exactly...), which I do, but then it says E: Cannot locate ndiswrapper-common.

I also tried **kevdog's** How To, but it was a little over my head TBH.

Can anyone give me any pointers as to what I need to do?

If it makes any difference, I've tried PCLOS and cannot connect with that either...

Thanks all

Tom

---

### Post by Hatticus on 2008-05-02
Any suggestions guys?

---

### Post by Hatticus on 2008-05-02
Sorry for the bump, but any help would be appreciated! :)

---

### Post by dstew on 2008-05-02
Can you connect to the internet through a wired connection? The apt-get command requires you to be connected first. If you cannot connect to the internet, you can still do it, but you need to use different techniques.

---

### Post by Hatticus on 2008-05-02
> **dstew said:**
> Can you connect to the internet through a wired connection? The apt-get command requires you to be connected first. If you cannot connect to the internet, you can still do it, but you need to use different techniques.
No, not able to get on the internet any other way

---

### Post by dstew on 2008-05-02
OK, first check to see if you have ndiswrapper already installed. On a command line enter```
ndiswrapper -v
```If you have ndiswrapper, that will print out the version you have. If you don't have ndiswrapper, you will need to install it "off-line", that is, by downloading the package on another internet PC, copying it to your Ubuntu PC, and installing.

Ubuntu is a Debian system, and software packages are complex things that have lots of files in them, and also have lots of dependencies, that is, other programs and files that they depend on. Usually, you cannot just download a package and install it, you also need to check for the dependencies and install those too. The apt-get program does this automatically, but since you aren't connected to the internet you can't use it.

To install packages off-line, and get all the dependencies too, I recommend the [nonetdebs]("http://nonetdebs.homeip.net/") service. You upload to them a text file of your current Ubuntu software status, and then request programs to install, or even full updates. They give you a list of links to all the packages you need. You download the packages onto an internet PC, transfer them to your Ubuntu PC, and install them using the dpkg program.

In your case, you need to install the package ndiswrapper-utils-1.9. Use nonetdebs to install it. You might also do a system update while you are at it.

The other thing you need to get your internet working is the Windows drivers. You can usually get them from the driver disk, or from a Windows system that was using the wireless card before, or off the internet somewhere. You need a .sys file, and a .inf file.

Once you have ndiswrapper installed, and have the Windows drivers, you can set up ndiswrapper. See [this thread]("http://sudan.ubuntuforums.com/showthread.php?t=617297") for an example.

---

### Post by Hatticus on 2008-05-02
Managed to get ndiswrapper from System>Administration>Software Sources. Also installed the ndisgtk and that got everything working! Yay!

---

