---
title: "no sound in firefox now."
date: 2009-06-25
forum: New to Ubuntu
---

### Post by tsuchang on 2009-06-25
Hi agai
I came back from vacation and did an update on my ubuntu.  there were a bunch of them.
Now my firefox isn't giving sound to the you tube videos.  I have sound with other applications.
I'm sure I'm not providing enough information so please ask the pertinent questions for me.

---

### Post by rampageoberon on 2009-06-25
> **tsuchang said:**
> Hi agai
I came back from vacation and did an update on my ubuntu.  there were a bunch of them.
Now my firefox isn't giving sound to the you tube videos.  I have sound with other applications.
I'm sure I'm not providing enough information so please ask the pertinent questions for me.

Try installing the package "libflashsupport".

```
suode aptitude install libflashsupport
```

Hope this works.

---

### Post by lovinglinux on 2009-06-25
> **rampageoberon said:**
> Try installing the package "libflashsupport".

```
suode aptitude install libflashsupport
```

Hope this works.

The command it's not *suode*, but *sudo*.

The package *libflashsupport* is not available in Jaunty, where it has been replaced with *flashplugin-nonfree-extrasound*. Anyway, while this package was able to solve some issues with flash videos in Hardy, it is very unstable and can cause Firefox to crash while viewing videos.


> **tsuchang said:**
> Hi agai
I came back from vacation and did an update on my ubuntu.  there were a bunch of them.
Now my firefox isn't giving sound to the you tube videos.  I have sound with other applications.
I'm sure I'm not providing enough information so please ask the pertinent questions for me.

Which flash plug-in are you using? To check this, open Firefox "Tools >> Addons >> Plugins" and check the name of the flash related plugins.

Also, go to "System >> Preferences  >> Sound" and select "ALSA - Advanced Linux Sound Architecture" in the first 3 menus.

---

### Post by tsuchang on 2009-06-25
"Which flash plug-in are you using?"
Shockwave Flash.

"select "ALSA - Advanced Linux Sound Architecture" in the first 3 menus. "

Ok I did that too.  I just tested the You Tube but no sound.  I will restart the puter and see if that does it.

Thanks.

Nope.  after restart still no joy.

---

### Post by lovinglinux on 2009-06-25
> **tsuchang said:**
> "Which flash plug-in are you using?"
Shockwave Flash.

"select "ALSA - Advanced Linux Sound Architecture" in the first 3 menus. "

Ok I did that too.  I just tested the You Tube but no sound.  I will restart the puter and see if that does it.

Thanks.

Nope.  after restart still no joy.

Try this from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

> **lovinglinux said:**
> 

**Problems:**

[list][*] 
[*] **Can't play streaming videos**
[*] **Flash videos display only a symbol and won't start**[/list]

**Solution:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content. You can disable plug-ins through the Addons window. Open "Tools >> Addons", then select the "Plug-ins" icon, then select the plug-in you want to disable and click the "Disable" button. Unfortunately, this not work every time, so the best procedure is to remove the conflicting plug-ins.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

To solve additional video issues, visit the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It solves most of the problems related to video codecs and plug-ins.

Please tell me if it works, so I can add your problem to the troubleshooting section of that tutorial.

---

### Post by tsuchang on 2009-06-25
Oki smokes.  I pasted in the line of code you gave me and BINGO!
this came back

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libclucene0ldbl sword-text-arasvd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo: unable to resolve host steph-desktop

Nope.  Still no sound on you tube.  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl sword-text-arasvd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steph@steph-desktop:~$ 

I'm going to try it after I reboot.

---

### Post by lovinglinux on 2009-06-25
> **tsuchang said:**
> Oki smokes.  I pasted in the line of code you gave me and BINGO!
this came back

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libclucene0ldbl sword-text-arasvd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo: unable to resolve host steph-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl sword-text-arasvd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steph@steph-desktop:~$ 

I'm going to try it after I reboot.

It won't make any difference. You already have the correct package, according tho the command output.

---

### Post by tsuchang on 2009-06-25
Oki Doki

but still no sound on you tube.  Other than that I have sound on other programs.

crumb.  It's times like this that I just want to go play warcraft and veg a bit.

---

### Post by lovinglinux on 2009-06-26
> **tsuchang said:**
> Oki Doki

but still no sound on you tube.  Other than that I have sound on other programs.

crumb.  It's times like this that I just want to go play warcraft and veg a bit.

Ok. Let's try the suggestion of the second post.

Run this command on a terminal [see footnote]

```
sudo apt-get install libflashsupport flashplugin-nonfree-extrasound
```

Paste the output here.

Please keep in  mind that these packages might cause instability and crash Firefox when viewing flash content.

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by billgoldberg on 2009-06-26
There seem to be a lot of these posts all of the sudden.

Maybe an update caused problems on some hardware configurations.

---

### Post by lovinglinux on 2009-06-26
> **billgoldberg said:**
> There seem to be a lot of these posts all of the sudden.

Maybe an update caused problems on some hardware configurations.

Yep.

[http://ubuntuforums.org/showthread.php?t=1197505](http://ubuntuforums.org/showthread.php?t=1197505)
[http://ubuntuforums.org/showthread.php?t=1197227](http://ubuntuforums.org/showthread.php?t=1197227)
[http://ubuntuforums.org/showthread.php?t=864375](http://ubuntuforums.org/showthread.php?t=864375)

---

### Post by lovinglinux on 2009-06-26
@ tsuchang

What version of Ubuntu you are running?

---

### Post by tsuchang on 2009-06-26
BINGO!!!!
That did it.  
Yipee!!
Thanks. 
You all are champions in my book.  My friend who talked me into using Linex instead of windoz said he would help me if i had any problems.  Now he says.."you try to figure it out."  No help at all.

Now how do i mark this as solved?

---

### Post by tsuchang on 2009-06-26
aaaaaaaaaaaaaaa crumb it isn't working again.  I reentered the code line and still no joy.  aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa!
windoz was a pain but this is too.

---

### Post by kansasnoob on 2009-06-26
Assuming this is 9.04 (Jaunty) I'd first go to Synaptic and click on Search (**not** quick search or rebuilding search). Then type **flash** and make certain the only things installed are **adobe-flashplugin** & **ubuntu-restricted-extras**.

Does ubuntu-restricted-extras have a "31" after it?

---

### Post by kansasnoob on 2009-06-26
> **lovinglinux said:**
> @ tsuchang

What version of Ubuntu you are running?

That's a "must know"!

---

### Post by lovinglinux on 2009-06-26
> **kansasnoob said:**
> That's a "must know"!

Open "System >> Administration >> System Monitor", look this info on the "System" tab.

---

### Post by tsuchang on 2009-06-26
Ubuntu 8.10

---

### Post by lovinglinux on 2009-06-26
Try this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kansasnoob on 2009-06-26
> **tsuchang said:**
> Ubuntu 8.10

Well, IMHO Intrepid was always problematic, but if you're happy with Intrepid I'd suggest running thru the appropriate steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

But honestly, unless your hardware is incompatible, I'd upgrade to Jaunty.

---

### Post by kansasnoob on 2009-06-26
> **lovinglinux said:**
> try this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

+++1!

---

### Post by tsuchang on 2009-06-27
ok did that.

got this in the terminal 

[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474;                                  

still no sound.

---

