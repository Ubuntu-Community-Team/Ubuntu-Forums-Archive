---
title: "FF causing ubuntu to lock up?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by ssulaco on 2009-07-05
Periodically Firefox will dim out or "grayout"and when this happens Ubuntu locks up ,mouse wont move,I have to hard boot to get back into ubuntu,
any suggestions...Thanks in advance.

---

### Post by HermanAB on 2009-07-05
Howdy,

Disable the FF plugins one by one, starting with the atrocious Adobe Flash plugin.

---

### Post by ajgreeny on 2009-07-05
> **HermanAB said:**
> Howdy,

Disable the FF plugins one by one, starting with the atrocious Adobe Flash plugin.
Whilst I agree with your possible solution, I think that Adobe Flash Plugin is now pretty good in ubuntu.  In fact I have not had a major problem with it since Hardy, or even before that.

@ ssulaco - also disable your extensions and re-enable one by one as they can also cause problems some times.

---

### Post by ssulaco on 2009-07-05
Im in the process of running memtest just to rule out mem issue,I will disable (all) extensions and plugins and will test.....then will re-enable one at a time...Great suggestion....
Thank you Herman and ajgreeny

---

### Post by lovinglinux on 2009-07-05
Same problem and possible solutions being discussed [here](http://ubuntuforums.org/showthread.php?t=1203965) (I personally believe that the cause of this issue is flash and pulseaudio. Follow up that thread for updates on the situation.)

Also visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by ssulaco on 2009-07-06
lovinglinus....I keep system monitor at top panel so i can monitor cpu usage while in FF,when cpu usage started to skyrocket i opened terminal and got 'top' running,xorg and FF were the culprits,i started at my plugins one at a time disabling them and when i disabled flash cpu usage dropped way down,screenshots attached........I re-enabled all plugins except for flash and so far so good after 30 min......

under your "flash optimization" Quote:
To remove other flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

Code:

sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree

what does (CTRL+SHIFT+V) do?.....sorry....im pretty new to linux...Thanks

---

### Post by lovinglinux on 2009-07-07
> **ssulaco said:**
> lovinglinus....I keep system monitor at top panel so i can monitor cpu usage while in FF,when cpu usage started to skyrocket i opened terminal and got 'top' running,xorg and FF were the culprits,i started at my plugins one at a time disabling them and when i disabled flash cpu usage dropped way down,screenshots attached........I re-enabled all plugins except for flash and so far so good after 30 min......

Instead of disabling Flash, which you will need eventually, install Firefox extension [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and configure it to block flash. This way, flash content will not be displayed unless you click it, so it won't put an extra load on your browser while you do regular browsing. I strongly recommend NoScript, mainly for security reasons, but since it can also block flash you don't need another extension for that.


> **ssulaco said:**
> what does (CTRL+SHIFT+V) do?.....sorry....im pretty new to linux...Thanks

In Windows and also in Linux, you can copy stuff, like a text for example, by selecting it then hitting the keys **CONTROL (CTRL)** and the letter **C**. To paste the test on another document, you hit **CONTROL** and the letter **V**. You can do that from the application menu, but **CTRL+C**/**CTRL+V** is petty fast. 

But the terminal is an exception. You need to hit **CONTROL+SHIFT+V** to paste the text to it. To copy from terminal, you follow the logic and hit **CONTROL+SHIFT+C**. The key combination of **CTRL+C** without the **SHIFT** in the terminal is used for interrupting a command instead of copying.

---

### Post by ssulaco on 2009-07-07
Thanks.......Ive been using 'Flashblock' also in windows and have been real happy with it,I will give noscript a whirl,Right now my concern is the stability of my system,right after my last post with flash disabled FF went to 98% cpu usage,and when I finally got it shut down cpu was still high and found "eog" running 97%,I finally got it to reboot and I couldnt log in computer kept locking up....I booted into recovery and ran fsck so far everything is ok........Does Linux have something similar,like "system recovery" in windows?

---

### Post by cwmoser on 2009-07-08
Compiz might be culprit.

I disabled Compiz and it solved the problem of FireFox graying out.

Carl

---

### Post by Darkdelusions on 2009-07-08
I was similar issues with the stock ff that shipped with 9.04. FF was using 100 percent of my CPU. I tired several different things to get it to stop but eventually just install FF 3.5 and that solved my issue

---

### Post by Garyhans on 2009-07-08
Goto tools addons extensions. Disable Ubuntu Firefox Modifications. Exit  - Restart.

---

### Post by ssulaco on 2009-07-09
> **cwmoser said:**
> 
I disabled Compiz and it solved the problem of FireFox graying out.
Carl
I hate to give up Compiz....

> **Darkdelusions said:**
>  but eventually just install FF 3.5 and that solved my issue
What would be the best way to install FF3.5?

> **Garyhans said:**
> Goto tools addons extensions. Disable Ubuntu Firefox Modifications. Exit  - Restart.
I will give that a go for now and see what happens.......Thanks everyone.

---

### Post by lovinglinux on 2009-07-09
> **cwmoser said:**
> Compiz might be culprit.

I disabled Compiz and it solved the problem of FireFox graying out.

Carl

As far as I understand that just disable a plugin on compiz that greys out applications when they are busy, but does not prevent the application from becoming unresponsive. The application greying out is a feature of Compiz, to alert you that they are busy, not a problem. The problem is Firefox becoming busy too often and then freezing.

> **ssulaco said:**
> I hate to give up Compiz....


What would be the best way to install FF3.5?


I will give that a go for now and see what happens.......Thanks everyone.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by ssulaco on 2009-07-09
Thanks lovinglinux,before I do anything Im going to read your FF optimization thread.

---

### Post by cwmoser on 2009-07-18
I think I have a solution that will fix this.

I went to the nVidia website and downloaded the version 185 drivers.

Then I disabled the nvidia version 180 drivers via System -> Administration -> Hardware Drivers.

Booted in Recovery Mode and got a command prompt. 

Then I cd to the folder with the downloaded version 185 drivers and installed them via:
#  sh ./NVIDIA-Linux-x86_64-185.18.14-pkg2.run

The above were the 64 bit drivers - there are 32 bit drivers at the Nvidia website too.

Then I rebooted and logged in with low resolution graphics.

Then configured the new nVidia drivers via:
System -> Preferences -> NVIDIA X Server Settings
and set resolution to 1680x1050 and Twinview (dual monitors)

Then System -> Preferences -> Appearance -> Visual Effects
and enabled the Extra settings.

So far no more pauses, gray outs with Fire Fox or Open Office.
Keeping my fingers crossed - so far its been good.

Carl

---

