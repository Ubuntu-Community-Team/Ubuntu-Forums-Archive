---
title: "Broadcom wireless adapter on Dell Inspiron 1521 (WORKING)"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by jrcolbert on 2014-12-04
Hello All,

I have been using Ubuntu Linux for a few years. Not a complete newbie, I am actually a computer tech. I hate command line in windows and terminal commands though. I use them when I have too. I am a 2 finger typer!!! anyway I have a client that brought me their computer that they use to connect to the internet and use the browser to check email, surf and use facebook. They don't do much else with it. So I figured I would pound Ubuntu on this for them and have it back to them in a few hours, no problem... well it was a little more involved than that. Crap, so here's the story.

I took time out of my day to install Ubuntu 14.04 LTS on this laptop (Dell Inspiron 1521) However I have a question that someone could probably answer easily.

I had only a wired connection after installing this and worked it all out to get wireless working using this thread "http://askubuntu.com/questions/474872/help-with-network-on-ubuntu-14-04/474875#474875"  and did as answer 1 suggested "sudo apt-get purge bcmwl-kernel-source" then did "sudo dpkg -i linux-firmware-nonfree_1.14ubuntu1_all.deb" rebooted and it works flawlessly...

Downloaded this file "linux-firmware-nonfree_1.14ubuntu1_all.deb" and got it install and like I said works great! 

Now, when ubuntu checks for updates it grabs the file "linux-firmware-nonfree_1.14ubuntu3_all.deb" and installs it and when I reboot the machine I have no internet access at all. Grrrrr!!!!!!!!!!

So I repeat everything again and get my connection up and running again. The problem with this is, This is not my laptop and I am gonna have to send it home with it's owner, who is not computer savvy at all! Is there a way for me to tell ubuntu to leave this file and it's driver alone and exclude it from updates in the future? 

The client will freak out if this happens, they need the internet to work, and I want to promote open source software because I always say that it is better than windows for most people. I have converted many folks over without these types of issues! I am very happy overall with linux and I know there is a way to accomplish this! Come on Linux Gods, please help me out! 

Thanks in advance for your help.

---

### Post by westie457 on 2014-12-04
Take a look at this page. It might give you a better chance of fixing things.

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

It has helped me several times with Broadcom chips.

---

### Post by jrcolbert on 2014-12-04
thanks for your reply westie457! 

Here is what I did to fix it, I found it here.... "http://askubuntu.com/questions/35560/ignore-package-in-update-manager"

[COLOR=#444444][FONT=UbuntuRegular]"Yes, I looked, and in [/FONT][/COLOR]Synaptic packagemanagement[COLOR=#444444][FONT=UbuntuRegular] (translation by hand from a german system) you mark a package, then in the menu [/FONT][/COLOR]package[COLOR=#444444][FONT=UbuntuRegular] you can [/FONT][/COLOR]lock version"

I performed install of synaptic package manager and I found the package "[COLOR=#000000]linux-firmware-nonfree_1.14ubuntu1_all.deb"[/COLOR]

and I locked it in place. Then to verify it in fact stayed locked not only in synaptic PM I ran the software updater manually and it said all software on my system was up to date and skipped right over it!

Mission accomplished.

Thanks everyone, you can mark this as SOLVED!

and you can share this with people trying to fix this problem, hopefully it will work for others as well!

---

### Post by chili555 on 2014-12-04
The real problem is that the package linux-firmware-nonfree is obsolete. The newer version actually *DELETES* the firmware that the Broadcom wireless device needs to work properly. That's why you get this:> Now, when ubuntu checks for updates it grabs the file "linux-firmware-nonfree_1.14ubuntu3_all.deb" and installs it and when I reboot the machine I have no internet access at all. Grrrrr!!!!!!!!!!The newer, correct method is to install firmware-b43-installer and be all set for life.

---

