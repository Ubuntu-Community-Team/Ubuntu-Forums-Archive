---
title: "No sound after updates"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by stape on 2009-04-19
Hi,

My sound was working fine up until I did the update offered today. Now I have a red icon on the speaker and when I click this it says:

No volume control GStreamer plugins and/or devices found.

Can anyone help?, is this a known bug that could be fixed soon.

Thanks in advance

---

### Post by stape on 2009-04-19
OK I have done a lot of searching since the above post, to no avail. This does seem to be a recurring theme, that after updating this problem occurs.

Is there a way of reverting back to the un-updated version I have, or finding each update and then removing the problem one?

---

### Post by stape on 2009-04-25
I have been trying all week with this and will have to hope that an update will fix it.

It does seem to be disappointing that a mere update screwed my sound.

Having said that, I am totally new to Ubuntu and, whilst it can be a little intimidating, using the command line to tinker, this has helped me successfully sort out the over sensitive touchpad by installing the controls for it, thanks to those that posted help on that issue.

---

### Post by NightwishFan on 2009-04-25
Try this first, just in case. (If you are using ubuntu-desktop)

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

```


If you get any errors try this,however post the errors before you do, so I can help. Make sure you read what it is going to do, if it lists a bunch of packages you think you need and asks to remove them, do not do it.

```

sudo apt-get -f install

```


If not, then try this: (replace the file name with any ogg vorbis music file.

```

pulseaudio -D --log-target=syslog
paplay /name/of/ogg/file.ogg

```

See if there is any error or if the sound plays. If so then your problem is not pulseaudio.


Try (i am not on linux right now, I think you can use a wild card in dpkg reconfigure) This will "reinstall" gstreamer.:

```

sudo dpkg-reconfigure gstreamer*

```

See what you get from this, make sure you ask and report any errors or if you need any help. Some of these commands can make or break your system if you are careless.

---

### Post by kansasnoob on 2009-04-25
Not sure if I can help or not but I need some more info. Was this an upgrade from Intrepid to Jaunty?

Would you please post the output of the following commands:

```
cat /etc/issue
```

```
aplay -l
```

---

### Post by stape on 2009-04-25
Thanks, here is the result so far:> phil@TOSHIBA-User:~$ sudo dpkg-reconfigure gstreamer*
[sudo] password for phil: 
Package `gstreamer*' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gstreamer* is not installed.
phil@TOSHIBA-User:~$ sudo apt-get update
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy Release.gpg
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/main Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/universe Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/multiverse Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/restricted Translation-en_GB
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates Release.gpg
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/main Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/universe Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/multiverse Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/restricted Translation-en_GB
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security Release.gpg
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/main Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/universe Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/multiverse Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/restricted Translation-en_GB
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/main Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/universe Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/restricted Translation-en_GB
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix Release.gpg
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/main Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/universe Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/multiverse Translation-en_GB
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/restricted Translation-en_GB
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy Release
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates Release
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security Release
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base Release
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix Release
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/main Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/universe Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/multiverse Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/restricted Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/main Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/universe Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/multiverse Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/restricted Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/main Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/universe Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/main Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/universe Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/main Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/universe Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/restricted Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/main Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/universe Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-security/restricted Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/main Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/universe Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/multiverse Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/restricted Packages
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/main Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/universe Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/multiverse Sources
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/restricted Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/main Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/universe Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/multiverse Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/restricted Packages
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/main Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/universe Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/multiverse Sources
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix/restricted Sources
Reading package lists... Done
phil@TOSHIBA-User:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@TOSHIBA-User:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fast-user-switch-applet gnome-system-tools pulseaudio
Suggested packages:
  xnest ntp padevchooser paman paprefs pavucontrol pavumeter
Recommended packages:
  libasound2-plugins
The following NEW packages will be installed
  fast-user-switch-applet gnome-system-tools pulseaudio ubuntu-desktop
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3510kB/3846kB of archives.
After this operation, 11.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base/main gnome-system-tools 2.22.0-0ubuntu9usg2 [3236kB]
Get: 2 [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/main pulseaudio 0.9.10-1ubuntu1 [273kB]
Fetched 3510kB in 5s (683kB/s) 
Selecting previously deselected package gnome-system-tools.
(Reading database ... 108069 files and directories currently installed.)
Unpacking gnome-system-tools (from .../gnome-system-tools_2.22.0-0ubuntu9usg2_lpia.deb) ...
Selecting previously deselected package fast-user-switch-applet.
Unpacking fast-user-switch-applet (from .../fast-user-switch-applet_2.22.0-0ubuntu2_lpia.deb) ...
Selecting previously deselected package pulseaudio.
Unpacking pulseaudio (from .../pulseaudio_0.9.10-1ubuntu1_lpia.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.102netbook0unr6_lpia.deb) ...
Setting up gnome-system-tools (2.22.0-0ubuntu9usg2) ...

Setting up fast-user-switch-applet (2.22.0-0ubuntu2) ...

Setting up pulseaudio (0.9.10-1ubuntu1) ...

Setting up ubuntu-desktop (1.102netbook0unr6) ...
phil@TOSHIBA-User:~$ 



---

### Post by stape on 2009-04-25
> **kansasnoob said:**
> Not sure if I can help or not but I need some more info. Was this an upgrade from Intrepid to Jaunty?

Would you please post the output of the following commands:

```
cat /etc/issue
```

```
aplay -l
```

Thanks, but no the system is running Hardy? 8.o4

---

### Post by NightwishFan on 2009-04-25
I guess you cannot use wildcards in dpkg-reconfigure. Perhaps reinstall the the gstreamer packages using synaptic. The other poster can perhaps help more, but fear not you shall have sound or bust!

Try rebooting, or at least logging off and back in after the update.

If no sound, go to sound preferences, and configure all of the parts to use ALSA.

---

### Post by stape on 2009-04-25
Not sure what "wildcards in dpkg-reconfigure" is.

...have just rebooted but no change, I think reinstalling the gstreamer sound like a good idea.

How do I do that?

BTW I have all parts of the sound set to ALSA

---

### Post by stape on 2009-04-25
Tried this also:

> phil@TOSHIBA-User:~$ sudo apt-get -f install
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@TOSHIBA-User:~$ 


---

### Post by NightwishFan on 2009-04-25
Sorry, I was just talking to myself, an old habit of mine. I normally just choose the wisest person present to speak to.

A wild card is like a search enhancer. It simplifies command line work. The "*" after gstreamer means anything with the word gstreamer in front of it.  I guess it does not work in dpkg-reconfigure, or the packages are not called gstreamer-something.

By the way the top of this post was just a joke, if you got it.

Use:

System -> Administration -> Synaptic Package Manager (I think it is called that)

Then search "gstreamer" and right click the packages and choose reinstall. Although, I would prefer dpkg-reconfigure, it may just do the same thing in synaptic.

---

### Post by stape on 2009-04-25
OK I have found the synaptic package manager but when it loads I get the message below:

Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them.


Can I get around that? I did a search for gstreamer and it found a few things but it looks like I cannot change anything

---

### Post by kansasnoob on 2009-04-25
In Hardy I've had excellent luck following this guide:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

As it says: "Hardy users: Follow Part A & B."

---

### Post by kansasnoob on 2009-04-25
> **stape said:**
> OK I have found the synaptic package manager but when it loads I get the message below:

Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them.


Can I get around that? I did a search for gstreamer and it found a few things but it looks like I cannot change anything

What kernel version are you running? You can find out by running the command:

```
uname -a
```

edit: It concerns me that you were not prompted for a password when you opened synaptic. Do you still also have the terminal open?

---

### Post by NightwishFan on 2009-04-25
Make sure you do not have any other package management application running such as apt.

---

### Post by stape on 2009-04-25
Linux TOSHIBA-User 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux

Just checked again and I can upen synaptic through the terminal without a password but it is not in the menu

---

### Post by kansasnoob on 2009-04-25
> **stape said:**
> Linux TOSHIBA-User 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux

Just checked again and I can upen synaptic through the terminal without a password but it is not in the menu

Hmmm, I just booted into Hardy (multi-boot here) and I'm running 2.6.24-23-generic. 2.6.24-24 is available in "proposed" updates but I did encounter some problems with it.

I wonder why synaptic is not in the menu?

Why the old kernel?

I'm puzzled:confused:

---

### Post by kansasnoob on 2009-04-25
I'm looking for some more info on the netbook remix. It may be that it still uses the older kernel. Looking here:

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

led me here:

[https://answers.edge.launchpad.net/netbook-remix](https://answers.edge.launchpad.net/netbook-remix)

And that led me here:

[https://answers.edge.launchpad.net/netbook-remix/+question/66449](https://answers.edge.launchpad.net/netbook-remix/+question/66449)

Which is marked solved.

Edit: I see from this:

> /lib/modules/2.6.24-19-lpia/updates/sound

That netbook remix does still use the older kernel!

---

### Post by stape on 2009-04-25
Thanks, I'm not entirely sure what you are saying but is it that the Toshiba NB 100 uses a special type of Ubuntu?

That could explain the different login screen I now have. (I followed some intructions on this subject a while back and ended up in a right mess, I had to reinstall the desktop) now apart from the new login screen I have real problems booting this thing up: I get the message about the greeter application crashing then a black screen with just the curser,(over and over again).

It seems that accepting the updates has wrought havok.

Is there a way I can return the machine to its original configuration?

Thanks for your help so far BTW

---

### Post by stape on 2009-04-25
> **kansasnoob said:**
> I'm looking for some more info on the netbook remix. It may be that it still uses the older kernel. Looking here:

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

led me here:

[https://answers.edge.launchpad.net/netbook-remix](https://answers.edge.launchpad.net/netbook-remix)

And that led me here:

[https://answers.edge.launchpad.net/netbook-remix/+question/66449](https://answers.edge.launchpad.net/netbook-remix/+question/66449)

Which is marked solved.

Edit: I see from this:



That netbook remix does still use the older kernel!

Great, I followed the instructions you found and the sound is back, I also note the laptop re-booted OK although that could be a coincidence. I'll report back...

---

### Post by stape on 2009-04-25
OK the sound is back.

I am still having problems with starting the laptop:

It goes through various stages then I get the warning:

"The greeter application appears to be crashing, attempting to use another one".

I click OK then I get a black screen with just the cursor, this can happen
 many times before I just press the power button to shut down and then try again.

I guess we could mark this thread as solved and I'll do a bit of research on the greeter application business.

Thank you very much for your help, I am determined to get on with Ubuntu, I hate Microsoft having such a grip on the software market.

---

### Post by kansasnoob on 2009-04-25
> **stape said:**
> OK the sound is back.

I am still having problems with starting the laptop:

It goes through various stages then I get the warning:

"The greeter application appears to be crashing, attempting to use another one".

I click OK then I get a black screen with just the cursor, this can happen
 many times before I just press the power button to shut down and then try again.

I guess we could mark this thread as solved and I'll do a bit of research on the greeter application business.

Thank you very much for your help, I am determined to get on with Ubuntu, I hate Microsoft having such a grip on the software market.

Well, I fear that some of the instructions given previously may have been inappropriate for the netbook remix! That includes my instructions regarding the pulseaudio fixes!

That's why I started by asking for more info! Then I was a bonehead and had not read your post where you showed the output of updates!

But, yes, you're running the Ubuntu Netbook Remix, so my instructions about reconfiguring pulse audio could have been harmful as could installing the "out-of-box" Ubuntu-desktop!

I'm sorry about that!

My guess is that if you follow these instructions:

Ubuntu 8.04 (Hardy) UNR Package Installation
[https://wiki.ubuntu.com/UNR#Ubuntu%208.04%20(Hardy)%20UNR%20Package%20Installation](https://wiki.ubuntu.com/UNR#Ubuntu%208.04%20(Hardy)%20UNR%20Package%20Installation)

You'll get back to the remix desktop. Maybe! Safest bet is to ask questions here:

[https://answers.edge.launchpad.net/netbook-remix](https://answers.edge.launchpad.net/netbook-remix)

---

### Post by stape on 2009-05-04
Adding the text below for 'completeness', From post here:
 
[http://ubuntuforums.org/showpost.php?p=7151436&postcount=2](http://ubuntuforums.org/showpost.php?p=7151436&postcount=2)

************************

...Fixed but not sure how exactly:

After six or so goes of "The greeter application appears to be crashing" and clicking OK I had a new screen telling that "Something bad is happening" and something about "waiting two minutes".

I ended up with a new picture of a Hardy Heron and the screen seemed to revert to the day I bought the netbook with a request to input my name,
create a password and choose which city I am in etc..

After this the whole thing is working great and boots up OK (have tried it three times now)...

I think the answer was to go to the startup manager panel and select something to do with starting with the last used version of software.

...at least that is what I think happened.

Maybe someone can shed a little more light on this

************************

I'm still very interested in how the system seemed to reset itself, also if there is a way I can be assured the OS is intact after all my 'tinkering'. 

It seems to be OK and has performed faultlessly for the past week.

Many thanks to those that have assisted me.

---

