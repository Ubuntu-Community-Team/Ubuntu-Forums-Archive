---
title: "Menus stuck in Japanese won't go to English"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Vandrian on 2010-02-10
Majorly frustrated with Ubuntu right now. 

Set up:
9.04 scim bridge Menus = English / Log In = English

I was trying to get this thing to output Japanese. Now all my menu's are in Japanese and won't go back to English. I have gone to the same menu to change back to English, but it won't change on startup. I change the menu output to English, I go back into the settings after exiting and English is there for Menus and LogIn screen however when I log back in everything is in Japanese. 

Furthermore I still can't type in Japanese which is what I wanted to do to begin with.

SOrry for the displacement, but I'm just mad as hell right now. As much as I'm not a Windows person a drop down list for output like they have makes so much sense.:evil:

---

### Post by Vandrian on 2010-02-10
Solved 

with a hell of lot of dictionary looking up...!!!!

System -> Administration -> Language Support -> Install Remove Langauges -> uncheck Japanese. 

It uses dpkg to remove the font from the system which then defaulted to English.

<sigh>

Maybe I'll just switch this computer to Fedora for Japanese projects.

---

### Post by spamless on 2010-06-17
> **Vandrian said:**
> Solved 

with a hell of lot of dictionary looking up...!!!!

System -> Administration -> Language Support -> Install Remove Langauges -> uncheck Japanese. 

It uses dpkg to remove the font from the system which then defaulted to English.

No, it's actually not solved, and it's a very annoying bug.  The thing is, when you switch a user's language the first time, it lets you rename the $HOME folders to the desired language and it changes the menus.  After that, if you try to change, e.g., a different user back to the first language, it won't work.  It changes the keyboard layout fine, but not the language for menus or $HOME folders.

I configured a new installation of Lucid for my girlfriend.  I am a native English speaker, but I am fluent in German.  My girlfriend is the reverse.  I initially used an English-language CD to install Lucid.  Then I added language modules and switched GF's account to German.  When I next logged in, it asked if the folders under $HOME should be renamed to German, and I said OK.  I set German as the systemwide language, because GF will use it most of the time.  The boot screen can be in German.

Now I set up my own account and set my prefs to English.  I am not given the opportunity to have my $HOME folders renamed to English, though.  And the menus stay in German.  This is very annoying!  It is the third installation I've had to deal with this on.  I solved it before by temporarily changing the system language back to English.  That caused the menus on my account to be in English.  I still had to rename the folders manually.  Then I set the system language back to German again so the boot screen would be German.  Aargh!

---

### Post by kimangroo on 2010-06-21
Hi spamless, it seems I have a slightly different problem to you and Vandrian.

I have set up a multi-language system for myself but I only use one account. My system-wide language is English, so my boot login is English. However I have a bunch of other languages installed and when I want to work in Japanese, I log out and choose Japanese from the language options at the boot screen (keeping an English keyboard layout) and then (almost) everything is in Japanese and I can input Japanese as well. The only thing that doesn't change are the names of the home, video, downloads folders etc, which is not a biggie, but seeing as it seems that you should be able to change them automatically everytime, I would like to know how to use that function.

I'm not sure if I quite understood the problems you were having, but have you tried changing the language options from the login screen as opposed to from the settings menu (I've never used that to change the language).

There are a few strange bugs or quirks when you have this multi-language set up though, Firefox for one sometimes decides that the name of my bookmarks toolbar should be in French or Russian etc. I have a strange auto-logon problem now but I'm not sure that's related.

---

### Post by spamless on 2010-10-30
> **kimangroo said:**
> Hi spamless, it seems I have a slightly different problem to you and Vandrian.
. . . .
I'm not sure if I quite understood the problems you were having, but have you tried changing the language options from the login screen as opposed to from the settings menu (I've never used that to change the language).

This stuff has never, ever been fixed, and it's annoying as hell.  I'm now in a new Maverick installation.  I installed it in German so the main user would have German.  Then I went to change my, admin, account to English.  The menus stay in German no matter what I do.  The date and time, and keyboard, are now in US English for me, though (which is what I want).  The personal folders never offered to change to English, by the way.

I want the menus in English for my login.  Why is that so hard?

By the way, this is the 4th time I've installed Maverick on this computer in 4 days.  It's still not right.  I had a kernel panic yesterday when I tried to install German after having installed the system in English.  The download locked along with the process.  I rebooted to kernel panic.  Lovely.

I also cannot get the Broadcom Legacy WLAN cardbus to work.  The driver won't install.  (It worked in Lucid.)

I spent the first two days trying to get Gnome to load my Desktop!  I could not figure out what was wrong.  Finally I read somebody's comment from two years ago that compiz can cause problems on some older machines.  I uninstalled compiz and, lo, the Desktop loaded.

---

### Post by nackery on 2010-12-26
This is an old thread, but I have just encountered the same problem (stuck language and scrambled language settings) when setting Japanese language on a 10.10 system.

There is a solution.

The following bug report describes the problems and solution (in excruciating detail).

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553162](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553162)

The upshot of it all is that you can install a patched version of GDM which resolves previous inconsistencies in the way GDM handles language and locale settings. Having installed the updated version, I can say that it appears to make everything function sensibly from an end-user perspective. 

You can download the updated deb package from here:

[https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu2/+build/2097121/+files/gdm_2.32.0-0ubuntu2_i386.deb](https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu2/+build/2097121/+files/gdm_2.32.0-0ubuntu2_i386.deb)

Although it's a package for Natty Narwhal, it seems to install and function without issue in 10.10 (use at your own risk!).

---

