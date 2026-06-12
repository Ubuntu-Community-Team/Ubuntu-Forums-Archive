---
title: "Tenda Mini 11N (W311U)"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by S2UIRR3L on 2013-11-26
Hi all... I haven't been on the forums since it was hacked, but haven't run into any problems since then either. Now, I need a little help with a wireless USB thing.

_**Back Story**_:
I had an old laptop that I decided to use just as a streaming radio only. Long story short, Chili555 was trying to help me in a thread ([http://ubuntuforums.org/showthread.php?t=1444925](http://ubuntuforums.org/showthread.php?t=1444925)). Before we could progress, the hard drive crashed and I gave up on the laptop. I just scrapped it and moved on to something that already has built in wireless and works like a charm... No problems!

**_Current Story_**:
I still have the little Tenda Mini 11N (Model# W311U). I moved my mom's computer to the other side of the room and now the hard wire connection won't reach. I went into my junk box of goodies, pulled out the Tenda and I'm having very similar problems with this computer. I ran a few of the commands that were in the other thread, thought maybe it would fix my mom's computer (but it didn't). It took me a little time to remember my password and email sign up to get back on the forums, but I did it... and now I need help.

**_I'm asking for help_**:
I'm not sure what kind of computer this is (it was a custom build that I got from Craig's List for free). But it's running Ubuntu 10.04 (64-bit) on a Core-2-Duo with 2-Gigs of RAM. My mom loves this computer and has gotten VERY comfortable with this version of Ubuntu. She doesn't know how to use anything else, the newer versions of Ubuntu scare her and introducing her to Windows-8 is just not going to work with this build.

**_Long story short_**:
Can someone instruct me on what to do in Terminal to make this little Tenda work? What ever info you need, I can/will provide. I'm not very good with terminal commands, so please use simple paste/copy methods with me, if at all possible. Thanks a million everyone. I hope there's still someone who is old school and still knows a bit about an old OS (10.04 Lucid Lynx). I have the install cd, and it has Linux drivers on it. I just don't know how to "install" a .tar.bz2 on this computer.

Here's a copy of the file that's on the install cd that came with the Tenda... Please, instruct me on what to do, or how to do it?

---

### Post by chili555 on 2013-11-26
I don't believe my advice is any different than in post #52 in the link you gave. I suggest you copy and paste away and post back if you get stuck.

---

### Post by S2UIRR3L on 2013-11-26
Before I try that...

I've already "black listed" those three things at the bottom of the config file. I briefly showed up as looking for my wireless router and got the same issue... Clicked on my "RabidSquirrelNetwok" SSID, entered my encryption code, the little thing circled around for a while and failed to connect, resulting in it asking for my password again.

I've tried the copy/paste thing in post #52 of the other thread, and now it won't show up at all. It's like it's not even plugged in to the computer. Maybe I did it wrong because everything downloaded in terminal and at the end, it asked for the root password. After entering it and hitting the enter button, it just hung there until I closed it.

Now, when I try to "look" for my SSID in the list, NOTHING shows up, as if it's not even connected. **_MAIN QUESTION_: Should I try it again, and before trying it again, should I have the Tenda plugged in or should I take it out of the USB port and do it, THEN plug it back in when the terminal has finished moving and doing it's thing?**

Chili555 - I'm amazed that you've replied to this post. I was hoping for someone as great as you, and here you are. As in the other thread, I don't want to pester you. If this doesn't work after a few attempts, I won't pester you. I'll just toss the Tenda in the trash and go spend the $50 or $60 dollars for a Netgear or something.

Thanks man!

---

### Post by kurt18947 on 2013-11-27
One of the real benefits of newer versions is better WiFi support.  I understand about 'reluctant dragons' when it comes to changing what their computer screen looks like - SWMBO is the same.  Even the most recent Ubuntu releases can be made to very much resemble the 10.04 screen.  She is using Ubuntu 13.10 w/gnome-shell and a few extensions.  Yes, she has desktop launchers which is what are important to her, she doesn't want to know about docks.  There is also gnome-session-flashback in the repositories which should produce a desktop very reminiscent of 10.04s gnome2.  Yet another option would be linux mint with the Mate desktop. Mate is gnome2 reworked, I haven't tried it so have no idea about its foibles.  Personally I like to use supported OSs, 10.04 on the desktop is not so no updates.

If you do want to get a wifi adapter that will work on 10.04 with no tweaks, this should work and it's pretty cheap.  It is limited to G speeds if that matters:

Trendnet TEW-424UB
[http://www.amazon.com/s/ref=nb_sb_noss/178-5130854-5782300?url=search-alias%3Dcomputers&field-keywords=trendnet%20tew424ub](http://www.amazon.com/s/ref=nb_sb_noss/178-5130854-5782300?url=search-alias%3Dcomputers&field-keywords=trendnet%20tew424ub)

---

### Post by chili555 on 2013-11-27
Pester me?? This is one of the things I enjoy doing the most, getting newer users going with wireless so that they can move on to more fun; such as downloading and playing 24/96k flacs (mp3s are *SO* last century), editing video, gaming, etc. 

Let's gather some diagnostics before we proceed. Insert the device and show us:```
uname -r
modinfo rt3070sta
sudo modprobe rt3070sta
dmesg | grep -e rt2 -e rt3
```

---

### Post by S2UIRR3L on 2013-11-27
I thank you for being so understand, especially for being so patient with me!
On my personal gaming computer, I also have 10.04 and Win7Ult because I
play SimCity and it's on-line only and it's incredibly difficult to run in WINe.

ANYWAY...

I started up the computer this morning, the Tenda plugged into the rear 2.0 USB
and the CAT-5 disconnected. I'm getting the list of available wireless routers, but
again, it won't connect. But now, there's an error message at the bottom. It says:

"[I]An error occurred, please run Package Manager from the right-
click menu or apt-get in a terminal to see what it wrong.
The error message was: ' Error: BrokenCount > 0'This usually
means that your installed packages have unmet dependencies[/I]"

After taking a screen shot of that (it's attached at the bottom, if you need it),
I decided to run the commands that you told me to do in the last post above.
Here is what the terminal put out:

```
rose@rose-desktop:~$ uname -r
2.6.32-53-generic
rose@rose-desktop:~$ modinfo rt3070sta
ERROR: modinfo: could not find module rt3070sta
rose@rose-desktop:~$ sudo modprobe rt3070sta
[sudo] password for rose: 
FATAL: Module rt3070sta not found.
rose@rose-desktop:~$
```

Could it have something to do with the black listed items?
BY THE WAY - LOOK AT THE SCREENSHOT - I HAVE THE DRIVERS
SITTING ON THE DESKTOP - THEY CAME WITH THE TENDA DISC
Should I just ignore the actual drivers that came with the Tenda?

---

### Post by chili555 on 2013-11-27
Let's take one problem at a time. First, let's try to fix the unmet dependencies issue. Please get a working wired ethernet connection, open a terminal and do:```
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
```If there are problems, post them and we'll work to fix them. We need to get this done correctly before we can proceed further. Any discussion of the wireless driver is, until then, moot.

---

### Post by S2UIRR3L on 2013-11-28
Okay - I left the Tenda in the rear 2.0 USB port, and ran the hard wire ethernet connection across the room. Here's the output:

```

rose@rose-desktop:~$ sudo apt-get update
[sudo] password for rose: 
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
rose@rose-desktop:~$

```

---

### Post by chili555 on 2013-11-28
> **S2UIRR3L said:**
> Okay - I left the Tenda in the rear 2.0 USB port, and ran the hard wire ethernet connection across the room. Here's the output:

<snip>
So far, so good. How about the other two?

---

### Post by S2UIRR3L on 2013-11-28
Oops... okay...
I left everything plugged in and did the other two commands.

OUTPUT #2
```

rose@rose-desktop:~$ sudo apt-get -f install
[sudo] password for rose: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  dkms fakeroot patch
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 293kB of archives.
After this operation, 1,106kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main patch 2.6-2ubuntu1 [121kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main dkms 2.1.1.2-2ubuntu1 [70.8kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main fakeroot 1.14.4-1ubuntu1 [101kB]
Fetched 293kB in 0s (523kB/s)   
Selecting previously deselected package patch.
(Reading database ... 214457 files and directories currently installed.)
Unpacking patch (from .../patch_2.6-2ubuntu1_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-2ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dkms (2.1.1.2-2ubuntu1) ...

Setting up rt3070 (2.3.0.2-0ubuntu1~ppa1~lucid2) ...
Adding module to DKMS build system
Doing initial module build
Installing initial module
Done

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

rose@rose-desktop:~$ 

```

OUTPUT #3
```

rose@rose-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rose@rose-desktop:~$ 

```

After doing this, I pulled the ethernet out and did a reboot with only the Tenda plugged in. The first thing that I got on the screen was a dialogue box that said something like: "Unlock Login Keyring" and "The login keyring did not get unlocked when you logged into your computer"

I'm "guessing" this happened because my mom's computer doesn't need a password to get on it. So I entered the password that I initially set as the root password when I installed Ubuntu on this machine. I think it's the same password that was disabled in settings so she doesn't have to put it in every time she turns on the computer?

I entered "that" password into the dialogue that asked to unlock the keyring, and it went away. The little error message at the bottom of the screen (in the screen shot a few posts ago) is no longer there. The Tenda tried logging into my wireless, but the same thing happened, resulting in it asking for my wireless encryption code again.

---

### Post by chili555 on 2013-11-29
>     The Tenda tried logging into my wireless, but the same thing happened, resulting in it asking for my wireless encryption code again. Let's see what's going on under the hood. Please detach the ethernet, open a terminal and do:```
lsmod > wifi.txt
dmesg >> wifi.txt
iwconfig >> wifi.txt
cat /var/log/syslog | grep etwork | tail -n20 >> wifi.txt
```Connect the ethernet and get a connection. Find the file wifi.txt in your user directory and paste it here and give us the link. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Have you considered updating from the ancient and creaky 10.04? We have made a lot of progress in 3 1/2 years!

---

### Post by S2UIRR3L on 2013-11-29
Okay, I've left the Tenda plugged in... I've disconnected the ethernet wire, did the terminal copy/paste...
And then I plugged the ethernet wire back in and did the terminal copy/paste again. Both times, I get this:

```

rose@rose-desktop:~$ lsmod > wifi.txt
rose@rose-desktop:~$ dmesg >> wifi.txt
rose@rose-desktop:~$ iwconfig >> wifi.txt
lo        no wireless extensions.

eth0      no wireless extensions.

rose@rose-desktop:~$ cat /var/log/syslog | grep etwork | tail -n20 >> wifi.txt

```

I'm at the point where I'm just going to chuck this little thing in the trash. I have a Netgear N600 Dual Band
on my gamer upstairs (she's NOT getting it). I think she's going to get the 50-foot CAT-5 ethernet wire instead.
No drivers needed... Just a few of those little grommets that Comcast Cable uses to nail the cable to the wall.
As for upgrading, I'm not going to. Ubuntu has lost my support until they make something that's decent, or...
I'll just move on to XFCE or Mint or something. The developers/designers of Ubuntu have lost their minds when
they did away with Gnome-2. It wasn't broken, why did they fix it? Until I learn XFCE/Mint, I'm going Windows-7.

[B]Chili555 - You're a saint for trying to help me. The Ubuntu Forums are very lucky to have you with them and
we all owe you a great deal of gratitude for all you do. Sincerely, you're fantastic. Thank you very much, sir.[/B]

---

### Post by chili555 on 2013-11-30
Thank for your kind words. 

I am sorry you didn't paste the results of the commands so we could analyze the problem...> Find the file wifi.txt in your user directory and paste it here and give us the link. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)I am quite confident that the device would work perfectly well in 12.04 LTS and I'm sorry you never tried it.

---

