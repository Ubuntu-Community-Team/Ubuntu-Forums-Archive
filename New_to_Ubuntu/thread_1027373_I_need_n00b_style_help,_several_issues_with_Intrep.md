---
title: "I need n00b style help, several issues with Intrepid"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Brinstar on 2009-01-01
hello again Ubuntu Forums people,

I feel like i should know this stuff by this point since i am far from a newbie (you can tell from the date on my avatar), but i still am not clear about the way Ubuntu handles certain operations and also I have once again returned to Ubuntu after another year-long hiatus in the wonderful virus-filled world of XP, so i have gotten a bit rusty, shall we say...

I have recently gotten into web development and i am trying to build a system that can be used for development work, and have come across some issues.

1. Whats the best way to install the following programs without apt-get (lets assume i get stuck without a net connection on a regular basis), because the way they install themselves seems really haphazard. They don't seem to follow any set pattern. One might install itself to /opt, another will go in /usr/bin, yet another will install in /home?

Also what should i be using to install, my 'normal' user or sudo/root?

JDK 6
Netbeans
Postgresql
Mysql
Apache
Ruby

2. Uninstalling programs is not always as obvious as it is on Windows. How am i supposed to uninstall things that are not installed with apt-get, why is it so random? This is not meant to sound like a whinge, but i wish Linux would just get a standard package management system already! 

3. I find it incredulous that for whatever reason, licensing, the GPL, etc., that i can't play a MP3 out of the box on Intrepid. Am I the only one who finds this a bit unacceptable? I haven't kept up with different distros, but i remember there was one that was based on Ubuntu but that came with the all required codecs from the start. can someone tell me if they know?

4. is it possible to run dual-boot WinXP & Ubuntu without using Grub? im thinking about adding Mac OSX, would grub handle this?

5. where/how do i add new fonts?

---

### Post by mikewhatever on 2009-01-01
> 3. I find it incredulous that for whatever reason, licensing, the GPL, etc., that i can't play a MP3 out of the box on Intrepid. Am I the only one who finds this a bit unacceptable? I haven't kept up with different distros, but i remember there was one that was based on Ubuntu but that came with the all required codecs from the start. can someone tell me if they know?

I see this come up from time to time and always feel surprised. Do some people live on an island or what? The existence of patents has been known for quite some time. You may find it even more incredible to find out that MS doesn't provide mp3 codecs bundled with Windows where I live.

---

### Post by Brinstar on 2009-01-01
> **mikewhatever said:**
> I see this come up from time to time and always feel surprised. Do some people live on an island or what? The existence of patents has been known for quite some time. You may find it even more incredible to find out that MS doesn't provide mp3 codecs bundled with Windows where I live.

yes i live on a island :P

the version of XP i user must be a very incredible version since it actually does play mp3s out of the box.

thanks for your amazing contribution.

---

### Post by rs3 on 2009-01-01
> **Brinstar said:**
> yes i live on a island :P

the version of XP i user must be a very incredible version since it actually does play mp3s out of the box.

thanks for your amazing contribution.

The distribution that you might be thinking of is [Linux Mint]("http://www.linuxmint.com/download.html"), which is Ubuntu-based but includes codecs not shipped with plain ol' Ubuntu.

---

### Post by rs3 on 2009-01-01
> **Brinstar said:**
> 1. Whats the best way to install the following programs without apt-get (lets assume i get stuck without a net connection on a regular basis), because the way they install themselves seems really haphazard. They don't seem to follow any set pattern. One might install itself to /opt, another will go in /usr/bin, yet another will install in /home?

Also what should i be using to install, my 'normal' user or sudo/root?

2. Uninstalling programs is not always as obvious as it is on Windows. How am i supposed to uninstall things that are not installed with apt-get, why is it so random? This is not meant to sound like a whinge, but i wish Linux would just get a standard package management system already! 

5. where/how do i add new fonts?

When you install an application without super-user privileges, you are likely to find that application in your /home directory, as that is likely the one place where you have sufficient permission to install anything.  I rarely see software put itself in /opt lately; most stuff goes in /usr/bin or /usr/local/bin.

Installing without super-user privileges is a good idea if you are unsure as to whether you trust the package or wish to try it out.  Again, this means it'll likely drop the entire application somewhere in /home.

As far as uninstalling goes, it does indeed depend on the original method of installation.  apt-get remove and apt-get remove --purge (the latter removing all configuration information in addition to the program) serve this purpose well when dealing with repository applications and packages, but the stuff you install by hand may require a different means of removal.  If the package arrives in .deb format, you can apt-get remove it.  If you extracted it from a .tar or other archive, you can generally just delete the files you previously extracted, but check first to see if the program includes instructions for removal.

I am unsure just how to add fonts from an outside source, but there are several font packages in the repositories; search for "ttf" in synaptic or you can also type apt-cache search ttf

---

### Post by chrisod on 2009-01-01
2. If you need to uninstall manually, generally just deleting the folder, and the hidden config folder is all that is necessary. Linux doesn't bury stuff in six directories and the registry like Windows.


3. Ubuntu, and many other distros, have chosen to officially support only free and open source software. MP3 is neither. Because it's Linux, there is nothing to stop you from adding it on our own, and in fact Ubuntu has made it very easy to get all the restricted codecs with just a couple of clicks. 

4. You'll need some boot manager to dual boot, but it doesn't necessarily have to be Grub. I don't have any experience with alternate boot managers though. I've always used Grub.

5. [How to install fonts]("https://wiki.ubuntu.com/Fonts")

---

### Post by Captain_tux on 2009-01-01
> **Brinstar said:**
> yes i live on a island :P

the version of XP i user must be a very incredible version since it actually does play mp3s out of the box.

thanks for your amazing contribution.

So, wait... **can** or **can't** you play mp3 files?

I don't think he meant if you literally lived on an island... remember, Google is your friend.

---

### Post by Brinstar on 2009-01-02
> **Captain_tux said:**
> So, wait... **can** or **can't** you play mp3 files?

I don't think he meant if you literally lived on an island... remember, Google is your friend.

i meant WinXP plays MP3 out of the box. And i technically *do* live on an island (UK)

:D

Also many thanks for the helpful replies

---

### Post by chrisod on 2009-01-02
WinXP plays MP3s out of the box because Microsoft has paid for the right to include a proprietary format in the OS.

---

### Post by LowSky on 2009-01-02
XP can't play DVDs out of the box

besides typing ```
sudo apt-get install ubuntu-restricted-extras
``` will solve most of your issues with codec support

---

### Post by Brinstar on 2009-01-03
few more questions...

is there a way to empty trash as root? something always gets left behind that shouldnt have...

i like the 'Command prompt here' util on xp, is there a similar way to get this on Ubuntu?

---

### Post by rs3 on 2009-01-03
> **Brinstar said:**
> i like the 'Command prompt here' util on xp, is there a similar way to get this on Ubuntu?
[This is a link to a script that gives you this functionality]("https://help.ubuntu.com/community/NautilusScriptsHowto#Open%20terminal%20here").  At the top of the page are instructions for setting up the script--in short, anything you want to make into a right-click context menu item in nautilus can be scripted and placed in ~/.gnome2/nautilus-scripts.

I assume you're using standard Ubuntu with GNOME?  I don't know how this would be done in KDE if that's your desktop environment.

---

