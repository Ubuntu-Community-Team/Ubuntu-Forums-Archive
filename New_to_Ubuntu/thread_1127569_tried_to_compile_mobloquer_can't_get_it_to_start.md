---
title: "tried to compile mobloquer can't get it to start"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-04-16
this is the first time i've ever tried to compile anything.  i managed to compile moblock control and i can run it in a terminal but really don't feel like it and would like to run mobloquer.  i managed to install it and it shows up in applications menu but it won't start and i get these error messages 

Required configuration file "/var/log/moblock.log" could not be found in the default path.
Please specify a different path.

Required configuration file "/etc/moblock/blocklists.list" could not be found in the default path.
Please specify a different path.

Required configuration file "/var/log/moblock-control.log" could not be found in the default path.
Please specify a different path.

Required configuration file "/etc/moblock/moblock.conf" could not be found in the default path.
Please specify a different path.

Required configuration file "/etc/default/moblock" could not be found in the default path.
Please specify a different path.

Required configuration file "/usr/bin/moblock-control" could not be found in the default path.
Please specify a different path.

can someone please help me?  i normally wouldn't compile but theres not a software source for jaunty yet and i tried replacing intrepid with jaunty and it didn't work

---

### Post by mamamia88 on 2009-04-16
anyone?  most of these directories seem to exist except with the name block control instead

---

### Post by lovinglinux on 2009-04-16
First of all, you shouldn't bump your thread so fast. Wait at least 24 hours, then you can bump it if you don't get any response.

The problem is that mobloquer is still using the old moblock-control paths, which have been changed with the addition of blockcontrol.

For example:

"/etc/moblock/blocklists.list" is now "/etc/blockcontrol/blocklists.list"

"/var/log/moblock-control.log" is now "/var/log/blockcontrol.log"

"/etc/moblock/moblock.conf" is now "/etc/blockcontrol/blockcontrol.conf"

The other paths giving errors have also changed, but I don't know exactly where they are.

Despite the fact that blockcontrol developer (jre) usually monitor threads with moblock content, it's a good idea to ask questions about moblock at [http://ubuntuforums.org/showthread.php?t=803183](http://ubuntuforums.org/showthread.php?t=803183)

---

### Post by jre on 2009-04-17
Yep, he's right. (A big thank you by the way for your work, lovinglinux!)

I guess you mixed up incompatible versions:
Either use
Recommended: moblock 0.9rc2 + **blockcontrol + mobloquer 0.6**
or Obsolete: moblock 0.9rc2 + moblock-control + mobloquer 0.5

The easiest way to achive this is to just use my packages from [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net)

Since you are on jaunty: A few days ago I would simply have suggested to use the "intrepid" files from my repo. But I have just started to use launchpad's PPA for jaunty. It's not complete yet and is currently populated with development versions, but they should work even better then the current releases.
Since blockcontrol is still missing in the PPA, I suggest to use both /etc/apt/sources.list entries:
```
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main
```

---

### Post by lovinglinux on 2009-04-17
> **jre said:**
> Yep, he's right. (A big thank you by the way for your work, lovinglinux!)

You are welcome and I'm glad to help. BTW, congrats for the excellent support and maintenance of the application.

---

### Post by mamamia88 on 2009-04-18
> **jre said:**
> Yep, he's right. (A big thank you by the way for your work, lovinglinux!)

I guess you mixed up incompatible versions:
Either use
Recommended: moblock 0.9rc2 + **blockcontrol + mobloquer 0.6**
or Obsolete: moblock 0.9rc2 + moblock-control + mobloquer 0.5

The easiest way to achive this is to just use my packages from [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net)

Since you are on jaunty: A few days ago I would simply have suggested to use the "intrepid" files from my repo. But I have just started to use launchpad's PPA for jaunty. It's not complete yet and is currently populated with development versions, but they should work even better then the current releases.
Since blockcontrol is still missing in the PPA, I suggest to use both /etc/apt/sources.list entries:
```
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main
```

i want to thank you i managed to get it to start now but i get this error message when i start it up Required configuration file "/var/log/moblock.log" could not be found in the default path.
Please specify a different path.  do you know what the problem might be?  it still seems to start up fine and works

---

### Post by lovinglinux on 2009-04-18
> **mamamia88 said:**
> i want to thank you i managed to get it to start now but i get this error message when i start it up Required configuration file "/var/log/moblock.log" could not be found in the default path.
Please specify a different path.  do you know what the problem might be?  it still seems to start up fine and works

As far as I remember, if you click to restore the default settings for the log path in mobloquer interface it should stop giving the error.

---

### Post by Jerriy on 2009-04-18
> As far as I remember, if you click to restore the default settings for the log path in mobloquer interface it should stop giving the error.Well how on earth do you do that? 

Namely when I want to start Mobloquer I don't get the mobloquer interface at all - instead I get 2 separate pop-up/dialogue boxes which go something like:> Required configuration file "/var/log/blockcontrol.log" could not be found in the default path.
Please specify a different path. and> Required configuration file "/var/log/moblock.log" could not be found in the default path.
Please specify a different path. 

---

### Post by Jerriy on 2009-04-18
What on earth means specify a different path? What I did is just clicking the self-installed and self-configured MENU BUTTON that appeared insede" Ubuntu application panel!

Edit: I restarted the whole computer just to make sure and now the interface also showed up. But I still get one of the previous pop-ups (blockcontrol.log not being found) so I tried to rename the "moblock-contrtol.log" into "blockcontrol.log" but failed (I get the message that I don't have the permissions necessary to edit/create/rename such file (despite me being an admin on my own ubuntu PC!).

Now what?? Lemme guess, the solution involves going to the dos-prompt thing, right? (i.e. solving Moblocquer by solving Moblock? Is that a possibility or a pipe-dream?

---

### Post by Jerriy on 2009-04-18
> **mamamia88 said:**
> i want to thank you i managed to get it to start now but i get this error message when i start it up Required configuration file "/var/log/moblock.log" could not be found in the default path.
Please specify a different path.  do you know what the problem might be?  it still seems to start up fine and worksI also have that exact problem and I am on Intrepid Ibex. 

The mobloquer settings specifies all of the paths except the moblock.log path
.

---

### Post by jre on 2009-04-19
Please post the output of ```
dpkg -l moblock moblock-control mobloquer blockcontrol
```.

---

### Post by Jerriy on 2009-04-21
Thanks but problem is now solved, mr J

See, I unfortunately installed all of the pakages that you provided (i.e at moblock "deb") But by doing so "moblock-control log" ended up being in the settings, which, thanks to "lovinglivux" I now know was a bad thing.

---

### Post by UltraAnders on 2009-07-31
Took me a while to figure out so thought I'd share. After un-installing the version from the Jaunty repo, following the advice in post [4](http://ubuntuforums.org/showpost.php?p=7088191&postcount=4) to use the Intrepid repo, and re-installing I got the interface up with only one error message about moblock.log. Tried applying default settings from the interface, but that didn't work. So I created the missing file "/var/log/moblock.log" and no error now. (This directory needs root privileges to create files.) :)

So ... should I stick with the Intrepid version (I'm using Jaunty)? I'm loathed (scared) to un-install now it appears to be working!

---

### Post by jre on 2009-07-31
Can you explain to me what the problem is or was? I had no reports about installation problems recently, so I thought all repositories are in a working state. And I just had a look at both repos mentioned in post#4 and I can´t see any problems.
So for jaunty I´d suggest jaunty packages. But as long as intrepid works, there´s no immediate necessity to update.

---

### Post by UltraAnders on 2009-08-01
When I installed from the Jaunty repo Mobloquer wouldn't open, in the same way as mentioned in post 1, but I only got 2 errors (sorry I didn't note which). It was not until I'd installed the Ibex version that I thought about simply creating an empty file to try fixing the issue.

---

### Post by jre on 2009-08-02
Hmm, don´t know what was happening. Perhaps you experienced another, already known, but unrelated bug.

I will release a new version soon. This will bring ALL repositories back in sync. And it will fix that other bug. So I´d suggest keep as it is, and when you get offered an update next time (blockcontrol 1.5 and mobloquer 0.6+svn200908xx) swithc to the jaunty repository.

---

### Post by UltraAnders on 2009-08-02
Sounds like a plan, thanks for your help. Great program BTW.

---

### Post by neurotopia on 2010-06-07
the way i fixed it was pretty simple. probably not the best way, but it worked for me (and since i'm kind of a moron i figure it will be an easy solution for others as well).
i just made symbolic links for the files that were not found based on some of the information in earlier posts:
from command line:

```
mkdir /etc/moblock
ln /etc/blockcontrol/blocklists.list /etc/moblock/blocklists.lst
ln /etc/blockcontrol/blockcontrol.conf /etc/moblock/moblock.conf
ln /var/log/blockcontrol.log /var/log/moblock.log
ln /var/log/blockcontrol.log /var/log/moblock-control.log
```

i'm using 10.04 lucid lynx, btw.

---

### Post by jre on 2010-06-07
Glad that you solved it, but I'm surprised that you experienced any problems at all.

Can you tell me which versions you have installed now, and if possible what you had before the update.
You get the version numbers after the update by issuing:
```
dpkg -l moblock moblock-control mobloquer blockcontrol
```

---

### Post by mad_jester on 2010-06-19
Wrll, jre, I didn't ask the initial question, but I am also having the same problem. I am running Lucid and installed Moblock from the repository and am getting the same problem when I try to start it (message about missing "moblock.log" and another file as well). I followed the directions on your site to add the launchpad repository, updated, and installed by copy-and-pasting the apt-get command on your site ("sudo aptitude install moblock blockcontrol mobloquer"). The only setting that I changed while working through the configuration was to not have it start at startup...other than that, everything is the default. I had this problem at first and I purged all of the packages and reinstalled them from Synaptic and had the same result.

I'm new to using Linux as my everyday desktop, BUT I will still try to help you out by posting the output of the dpkg command that I noticed you have asked for several times but never received. Here it is:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  blockcontrol   1.6.10-1~lucid Manage IP blockers
ii  moblock        0.9~rc2-24~luc An IP blocker for Linux
un  moblock-contro <none>         (no description available)
ii  mobloquer      0.6+svn2009081 GUI for MoBlock, an IP blocker for Linux
```Like I said, I personally can't make anything out of it since I'm kind of new to the inner workings of Linux, but I hope that it helps you. If you need any other information, just let me know and I'll try to help you out...it's the least I can do in exchange for you helping me!

---

### Post by jre on 2010-06-20
Hi. Thanks for your report. Your problem is another one than the original one. But the good thing is I have a solution for you:
Since you chose not to start moblock there is no moblock logfile, but mobloquer needs one to start. The quick fix for this is to issue once:
```
sudo touch /var/log/moblock.log
```

Since I liked your report I decided to add this fix to the package and also backport some goodies from pgl. So there will be a new blockcontrol package soon.

EDIT: I am just building new blockcontrol and mobloquer packages. I added support for blocklists in
list.iblocklist.com/lists/<author>/<list> format. So the blocklist dialog in mobloquer is really uasble again, instead of only showing cryptic names as before. See people, giving the information I asked for as mad_jester did really makes a difference. I didn't intend to make new packages before, or even backport changes from pgl otherwise.

---

### Post by mad_jester on 2010-06-20
> **jre said:**
> See people, giving the information I asked for as mad_jester did really makes a difference.

I noticed right away as I was reading the thread that you asked for that info a couple times and it wasn't provided...I work in a HelpDesk, so I spend a lot of time collecting information to help other people fix problems. Glad I was able to help!

By the way, your advice about touch-ing the file worked perfectly and Mobloquer is up and running. Thanks for all of your work on this software (and for providing better support than I've ever had for any software I've paid for)! =D>

---

