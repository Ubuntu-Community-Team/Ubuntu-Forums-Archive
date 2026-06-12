---
title: "How do i install skype on 9.04"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by hanzj on 2009-04-24
I've just upgraded from 8.10 to version 9.04. How do i install skype? I tried 
```
sudo apt-get install skype
```

but got
> Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


Help.

---

### Post by Sef on 2009-04-24
Are you using a 32-bit or 64-bit system?

---

### Post by hanzj on 2009-04-24
32 bit.

[http://www.geek.com/articles/chips/ubuntu-904-officially-released-available-for-free-download-20090423/](http://www.geek.com/articles/chips/ubuntu-904-officially-released-available-for-free-download-20090423/) says that Ubuntu 9.04 **includes **latest Skype.
I'm puzzled.

---

### Post by hanzj on 2009-04-24
FYI: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/) doesn't have Ubuntu 9.04 yet.

---

### Post by Trekrider58 on 2009-04-24
> **hanzj said:**
> FYI: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/) doesn't have Ubuntu 9.04 yet.

I installed under 8.04 with no problems, upgraded to 8.10 and Skype stopped working, just upgraded to 9.04 and it works again :P

---

### Post by stwschool on 2009-04-24
I installed the 8.04 version from [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/) in 8.10 so would hazard a guess that it'd be fine in 9.04 as well.

Edit: D'oh, just remembered I installed it on my boss's laptop on 9.04 and it worked fine.

---

### Post by meeples on 2009-04-24
i installed skype on jaunty from theyre website last night and it works great :D

---

### Post by kiwisparkles on 2009-05-03
Have you enabled third party software in the software sources? I wasn't aware that you could install skype through apt... (am still on 8.04 here)

---

### Post by d3v1us on 2009-05-18
I just installed 9.04 64-bit.  I'm having trouble getting Skype installed though, any ideas?

---

### Post by Miljet on 2009-05-18
If you go to software sources and enable medibunti under "third party software." Then you can use synaptic or apt-get in the terminal to install Skype.

I just installed it on my new Jaunty machine to make sure it worked.

---

### Post by Paqman on 2009-05-18
> **Miljet said:**
> If you go to software sources and enable medibunti under "third party software." Then you can use synaptic or apt-get in the terminal to install Skype.


More info about [Medibuntu]("http://www.medibuntu.org/").

Damned if I can get my microphone to work in Skype on Jaunty though.

---

### Post by Shriner on 2009-05-18
> **Miljet said:**
> If you go to software sources and enable medibunti under "third party software." Then you can use synaptic or apt-get in the terminal to install Skype
I have it enabled and am unable to install Skype......It was working, after upgrading to JJ (original install was on 8.10) but it just disappeared after rebooting my lappy.

UPDATE: I just noticed that the authentication key had failed.....updated according to _[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)_[]("http://www.medibuntu.org/sources.list.d/jaunty.list") and install was allowed

---

### Post by Miljet on 2009-05-18
I'm sorry, I should have given more explicit instructions. Here are the instructions for 9.04 (Jaunty).

Open a terminal (Applications -> Accessories ->  Terminal). Copy the following code and paste it into the terminal.

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Then to get the GPG key

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

And finally

```
apt-get install skype
```

After it installs, you can find Skype under Applications -> Internet -> Skype

Hope this helps.

---

### Post by mattalexx on 2009-05-18
> **Miljet said:**
> If you go to software sources and enable medibunti under "third party software."

I'm not seeing "medibuntu".

EDIT: Nevermind, we were writing at the same time.

---

### Post by Arup on 2009-05-18
Skype works very well here on x64 Jaunty installed via medibuntu repos. Make sure to set the default audio to your hardware and not PULSE and give Skype an inbound port.

---

### Post by Arup on 2009-05-18
> **mattalexx said:**
> I'm not seeing "medibuntu".

Go to [www.medibuntu.org](www.medibuntu.org) and check on repository how to.

---

### Post by MontelEdwards on 2009-05-18
Simply enter these commands in terminal
```
wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb
```

and then run 
```
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
```


But it is also a good idea to install medibuntu repositories because they give you great applications like Adobe Reader and other crap.

---

### Post by rlj399 on 2009-05-21
> **Arup said:**
> Skype works very well here on x64 Jaunty installed via medibuntu repos. Make sure to set the default audio to your hardware and not PULSE and give Skype an inbound port.


how do i give skype an inbound port?

---

### Post by shanti.satellite on 2009-05-26
Hey -- I need some help with Skype, too. Before I go any further, I need to put out the disclaimer that I know almost NOTHING about Ubuntu, and **tech jargon is extremely confusing to me**. If you have an explanation to offer, please use very rudimentary terms.

Okay, so I have the Skype software installed properly, but when I try to make a call, I get a 'Problem with Audio Playback' message. After some [investigating]("http://skype.com/help/guides/soundsetup_linux.html"), I think I've figured out the origin of the problem... Skype natively supports OSS, but my system uses ALSA. So, I need to install an OSS emulator, right? My question, then, is: **How do I install an OSS emulator?**

I asked on a different forum, and I was simply told to "use my package manager and search for OSS." I did that, and ended up finding and installing package oss-compat version 0.0.4.

But Skype still won't work. :|

Anyone have some guidance? Thanks!!

---

### Post by slowtrain on 2009-12-13
I've tried a couple ways of putting medibuntu (and its authentication) in my software sources, including the command line suggested at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) as well as instructions that put the necessary information into the Software Sources GUI.  This seems to work--medibuntu becomes a 3rd party software source in the GUI.  And, I get no error messages when I update my software.  But, I just don't see Skype in Synaptic after all this.  Interestingly, I don't see Skype listed in the Medibuntu packages list here: [http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html).  On the other hand, I don't see some other packages that are supposed to be part of Medibuntu either such as libdvdcss2.  Wish I knew what was going on--is Skype no longer a part of Medibuntu, or is there something wrong w/ my Medibuntu repository install?

I'm on a 64-bit version of Jaunty.  Perhaps complicating this, I'm also running Ubuntu within Windows using VirtualBox (though I can't seem to get Skype either for my work desktop, which has Medibuntu installed).

---

### Post by macmaster on 2009-12-13
I tried installing skype 8.04 on ubuntu 9.10 and it had some error messages, i rebooted the computer and it showed another error message, i went into terminal and typed in "sudo apt-get install -f" and it solved the problem. Sorry if someone else has said this I just joined and haven't had time to read the replys.    :)

Hope i helped, btw skype isn't in the ubuntu software centre so that might be why it wouldn't install.

---

### Post by slowtrain on 2009-12-13
hi macmaster:  i'll bite.  the -f option sounds like a good idea--it'll fix broken dependencies, which should help if there are missing packages in your installation.  

i'm curious, were you able to install skype via the medibuntu repositories?

---

### Post by prj44 on 2010-02-01
Well, I have followed each of these instructions.  Some have worked, some have not.  The net result is that I don't have Skype installed.
Could somebody please point to a complete set of instructions that are explained somewhat.  Blindly typing in code that doesn't work is ... unsettling.

---

### Post by slowtrain on 2010-02-01
prj44:  I got Skype working, but by downloading the Debian package from skype.com and then double-clicking it to activate the debian gui installer.  Am still surprised I didn't find it in Medibuntu (or perhaps I don't have the right restricted software activated in Medibuntu?)

---

### Post by LowSky on 2010-02-01
Medibuntu doesn't have skype in it's repos anymore. You have to get it from Skype.com

---

### Post by slowtrain on 2010-02-01
Huh, well that explains a lot.  I wonder why Medibuntu decided not to carry Skype any longer?

---

