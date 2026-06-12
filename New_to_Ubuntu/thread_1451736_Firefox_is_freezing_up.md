---
title: "Firefox is freezing up"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Excedio on 2010-04-10
I recently did an update to my Firefox (3.6.4pre) and it seems to have broken something. Ubuntuforums is the only website that I have been able to go to without Firefox freezing up and going dark.

Is anyone else seeing this problem? Anyone have a possible solution?

---

### Post by yabbadabbadont on 2010-04-10
Just a generic firefox trouble-shooting tip: try disabling all plugins/add-ons and/or create a new profile and see if the problem persists.

---

### Post by Excedio on 2010-04-10
Ran through a terminal. Got this...

> ** (firefox-bin:5728): WARNING **: Serious fd usage error 14

** (firefox-bin:5728): WARNING **: Serious fd usage error 12

---

### Post by Excedio on 2010-04-10
Disabled all add-ons, no luck.

**Edit: **Found the Plug-In that is causing the problem. Shockwave Flash 10.0.r32. I also have Shockwave Flash 10.0.r45 installed and when r45 is Enabled, I have zero problems. However, I cannot watch Flash videos without r32. :-/

r45 alone will give me a white screen with no video on YouTube, Any ideas?

---

### Post by yabbadabbadont on 2010-04-10
When starting it from a terminal, try using the "-safe-mode" option.

---

### Post by Excedio on 2010-04-10
> **yabbadabbadont said:**
> When starting it from a terminal, try using the "-safe-mode" option.

Same problem

```
excedio@excedio-desktop:~$ firefox -safe-mode

(firefox-bin:6414): GLib-WARNING **: g_set_prgname() called multiple times

** (firefox-bin:6437): WARNING **: Serious fd usage error 14

** (firefox-bin:6437): WARNING **: Serious fd usage error 12
```

---

### Post by lvleph on 2010-04-10
I am having the same issue.

---

### Post by Excedio on 2010-04-10
I'm going here ([https://www.mozilla.com/en-US/plugincheck/](https://www.mozilla.com/en-US/plugincheck/)) to check if updates are available. It detects my Shockwave Flash 10.0.r32 as being out of date. However, as we all know, going to Adobe's website and getting the latest flash is not the easiest thing when your computer is 64bit. Plus, I have r45 and it doesn't play flash on it's own.

---

### Post by Excedio on 2010-04-10
Thanks for the help, I solved my problem. Went to /usr/lib/mozilla/plugins and deleted libflashplayer.so

When I restarted Firefox, 10.0.r32 was gone and 10.0.r45 still remained. Tested YouTube successfully.

Marking this thread "Solved"

---

### Post by madhi19 on 2010-04-12
That pretty much did it thank for the help!

---

### Post by Samemax on 2010-04-12
> **Excedio said:**
> Thanks for the help, I solved my problem. Went to /usr/lib/mozilla/plugins and deleted libflashplayer.so

When I restarted Firefox, 10.0.r32 was gone and 10.0.r45 still remained. Tested YouTube successfully.

Marking this thread "Solved"

I'm having exactly the same problem and wanted to follow your instructions, but:
1. under /usr/lib/mozilla/plugins there is no libflashplayer.so
2. I found libflashplayer.so under usr/lib/flashplugin-installer but I can't delete it.
Someone can please help me?

---

### Post by lovinglinux on 2010-04-12
> **Samemax said:**
> I'm having exactly the same problem and wanted to follow your instructions, but:
1. under /usr/lib/mozilla/plugins there is no libflashplayer.so
2. I found libflashplayer.so under usr/lib/flashplugin-installer but I can't delete it.
Someone can please help me?

Use the tool from [this thread](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash then install the proper version according to your system architecture.

---

### Post by Samemax on 2010-04-12
> **lovinglinux said:**
> Use the tool from [this thread](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash then install the proper version according to your system architecture.

ok, I got this tool, but I don't know what exactly to remove. The libflashplayer.so? And where do I get the proper version after removing this one? Sorry for my lack of knowledge...

---

### Post by lovinglinux on 2010-04-12
> **Samemax said:**
> ok, I got this tool, but I don't know what exactly to remove. The libflashplayer.so? And where do I get the proper version after removing this one? Sorry for my lack of knowledge...

Extract the downloaded file somewhere you can find, then double click the extracted file. You will see a window with some options like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148039&stc=1&thumb=1&d=1266974995[/IMG]

Click the "Remove Flash" option and wait to receive a conformation message, then click the "Install Flash" button according to your system architecture.

---

### Post by Samemax on 2010-04-12
> **lovinglinux said:**
> Extract the downloaded file somewhere you can find, then double click the extracted file. You will see a window with some options like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148039&stc=1&thumb=1&d=1266974995[/IMG]

Click the "Remove Flash" option and wait to receive a conformation message, then click the "Install Flash" button according to your system architecture.

I downloaded the tar.gz file and extracted it. But when I double click the "adobe_flash_installer" executable file nothing happens. I also tried to open the downloaded tar archive and then double click on the file that's in (seems to be the same, I have extracted) but a window that opens doesn't have the option "remove flash" (see screenshot) just "remove", so I would have to type the file/programm by myself.

---

### Post by lovinglinux on 2010-04-12
> **Samemax said:**
> I downloaded the tar.gz file and extracted it. But when I double click the "adobe_flash_installer" executable file nothing happens.

Right-click on it, select Properties then tick the option to allow to run as executable.

---

### Post by deancasino on 2010-04-12
Ok, here's your issue. You should get Google Chrome, get Google Chrome at: 

*[www.google.com/]("http://www.google.com/chrome")*[B]*[chrome]("http://www.google.com/chrome")*

Enjoy the Chrome![/B]

---

### Post by lovinglinux on 2010-04-12
> **deancasino said:**
> Ok, here's your issue. You should get Google Chrome, get Google Chrome at: 

*[www.google.com/]("http://www.google.com/chrome")*[B]*[chrome]("http://www.google.com/chrome")*

Enjoy the Chrome![/B]

That's not what the OP wants. Suggesting another browser that works for you doesn't solve the problem. IMO, Firefox is way much better than Chrome. I know about the speed of rendering pages, but that is the only benefit. Anyway, please don't turn this thread into a browser war.

---

### Post by lovinglinux on 2010-04-12
> **Samemax said:**
> I downloaded the tar.gz file and extracted it. But when I double click the "adobe_flash_installer" executable file nothing happens. I also tried to open the downloaded tar archive and then double click on the file that's in (seems to be the same, I have extracted) but a window that opens doesn't have the option "remove flash" (see screenshot) just "remove", so I would have to type the file/programm by myself.

Anyway, if that is too complicated or doesn't work and if you have 32bit system, then follow my instructions from the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by deancasino on 2010-04-12
Take it easy! Just trying to help!

---

### Post by lovinglinux on 2010-04-12
> **deancasino said:**
> Take it easy! Just trying to help!

Is just that such comments tend to turn into a browser war and never solve the issue in the first place. 

Anyway, don't take it too seriously. It is just my [Mr. Hide](http://www.flamewarriors.com/warriorshtm/jekylhyde.htm) showing up :)

---

### Post by Samemax on 2010-04-18
Well, first of all: big thanks for all your help!

But: I have tried with the nice flash-tool several times to remove and reinstall flash, I have tried with your (lovinglinux) optimalization instructions, I have tried removing/ reinstalling flash within synaptic package manager - firefox is still freezing up :(

Perhaps I should try to reinstall it, or to install the former version of it - should I?

---

### Post by lovinglinux on 2010-04-18
> **Samemax said:**
> Well, first of all: big thanks for all your help!

But: I have tried with the nice flash-tool several times to remove and reinstall flash, I have tried with your (lovinglinux) optimalization instructions, I have tried removing/ reinstalling flash within synaptic package manager - firefox is still freezing up :(

Perhaps I should try to reinstall it, or to install the former version of it - should I?

What version of Ubuntu and Firefox you are using? What is your system architecture, 32bit or 64bit? What processor you have? How much CPU cycles flash uses when Firefox freezes?

---

