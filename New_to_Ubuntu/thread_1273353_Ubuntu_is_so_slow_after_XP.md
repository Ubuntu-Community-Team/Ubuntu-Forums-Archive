---
title: "Ubuntu is so slow after XP"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by dgub on 2009-09-23
I have been trying out 8.04 for a week or so and have managed to get it configured to my liking (almost) but it is just so slow after XP

Firstly I auto hide the toolbars. They are slow to respond and then creep out of hiding.

Firefox and Opera are very slow. I use auto scroll a lot and scrolling down a page is slow and jerky.

Is there anyway around this please.

For info
Amd 64 6000+ on ASUS board
Sole use of 320 SATA drive
Generic NVIDIA downloaded driver for it.
Upgraded latest patches to 8.04

---

### Post by philinux on 2009-09-23
How much memory is installed?

---

### Post by dgub on 2009-09-23
> **philinux said:**
> How much memory is installed?

I knew I had forgotten something

4GB

---

### Post by Mornedhel on 2009-09-23
Your specs look comfortably fast enough to run a normal Ubuntu installation and then some. If you're using desktop effects, make sure you have enabled your NVidia restricted drivers ; if you have, try disabling desktop effects.

As an aside : why do people keep comparing the speed and response time of recent Linux distributions (even Hardy is only about one year old) to an OS that came out eight years ago ?

---

### Post by philinux on 2009-09-23
> **dgub said:**
> I knew I had forgotten something

4GB

Ok with no apps running open a terminal. Apps>accessories>terminal.

Type in 

```
top
```

Press enter. See if anything hogging cpu.

---

### Post by dgub on 2009-09-23
> **philinux said:**
> Ok with no apps running open a terminal. Apps>accessories>terminal.

Type in 

```
top
```

Press enter. See if anything hogging cpu.

Thanks

There is nothing there. Enclosing screenshot

---

### Post by XCan on 2009-09-23
> **Mornedhel said:**
> 
As an aside : why do people keep comparing the speed and response time of recent Linux distributions (even Hardy is only about one year old) to an OS that came out eight years ago ?

I guess because people don't really expect MS to write neat code anymore. 

On topic: I certainly find Ubuntu faster on my machines even compared with freshly installed XP+SP3+Updates.

---

### Post by ibuclaw on 2009-09-23
[Windows XP Requirements]("http://www.microsoft.com/windowsxp/sysreqs/pro.mspx"):
> **Published: August 24, 2001]
&#8226 said:**
> 

[Ubuntu 8.10 and older Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"):
[QUOTE=last edited: 2009-09-04 14:27:29]
&#8226;	700 MHz x86 processor
&#8226;	384 MB of system memory (RAM) 
&#8226;	8 GB of disk space
&#8226;	Graphics card capable of 1024x768 resolution
&#8226;	CD-ROM drive or network card


Times have changed in 10 years, and so has our hardware specs...
Back in the day, Windows XP was once a slow, heavy system too.

Regards
Iain

---

### Post by lik3n on 2009-09-23
Wow...your computer is faster than mine & has more RAM. I have compiz running & just tested the autohide with very smooth results. I'm running 9.10 right now with no problems. I would say try upgrading to 9.04 & see if that helps your situation. Also download the restricted nvidia drivers. You'll probably see an increase in speed then, too.

---

### Post by scrooge_74 on 2009-09-23
Did you install 32 bit or 64 bit, I see you posted to have an AMD 64 processor. Try also not using the desktops effects, or maybe is the video cards drivers

---

### Post by dgub on 2009-09-23
Thanks for the replies

NVIDIA shws - 
> Proprietary drivers are being used to make this computer work properly

I assume that is what you mean by restricted drivers.

The Desktop Effects are set to None.

It is the 32 bit version.

Having spent an age setting up btnx to configure my mouse I find that it is not supported under later versions and don't want to get into scripting.

Thanks

---

### Post by scrooge_74 on 2009-09-23
you can use the 64 bit ver with that machine of yours

---

### Post by NightwishFan on 2009-09-23
Windows Xp kernel is terrible at memory management, i/o, and overly pages. Linux kernel is none of the above. Ubuntu is a system designed for modern hardware, I have never found it to be unresponsive.

To improve performance on a modern system try these tweaks:

Perhaps try a 64-bit edition of Ubuntu, though it is not necessary, 32-bit works fine. The performance enhancements will be there, but you may not notice much more responsiveness.

Install the package preload. Preload is an adaptive readahead daemon. That means it runs automatically in the background and actively pre-loads the programs you use in RAM. How to install? Open a terminal and type this command.
```
sudo apt-get install preload
```

Try this tweak. On a system with 4gb of RAM, you will likely never need paging. You can reduce the kernels priority to use swap like so:

Press ALT+f2 to open the run dialog box. Type this command and hit run:
```
gksudo gedit /etc/sysctl.conf
```
Do not edit anything in this file! Simply scroll down to the bottom, and add a new blank line. On the blank line add this:
```
vm.swappiness=10
```
Then save the file and reboot.

To test above command worked correctly, open a terminal and type:
```
cat /proc/sys/vm/swappiness
```
You should get a result of 10 if it worked correctly.

---

### Post by dgub on 2009-09-23
> **NightwishFan said:**
> Windows Xp kernel is terrible at memory management, i/o, and overly pages. Linux kernel is none of the above. Ubuntu is a system designed for modern hardware, I have never found it to be unresponsive.

To improve performance on a modern system try these tweaks:

Perhaps try a 64-bit edition of Ubuntu, though it is not necessary, 32-bit works fine. The performance enhancements will be there, but you may not notice much more responsiveness.

Install the package preload. Preload is an adaptive readahead daemon. That means it runs automatically in the background and actively pre-loads the programs you use in RAM. How to install? Open a terminal and type this command.
```
sudo apt-get install preload
```

Try this tweak. On a system with 4gb of RAM, you will likely never need paging. You can reduce the kernels priority to use swap like so:

Press ALT+f2 to open the run dialog box. Type this command and hit run:
```
gksudo gedit /etc/sysctl.conf
```
Do not edit anything in this file! Simply scroll down to the bottom, and add a new blank line. On the blank line add this:
```
vm.swappiness=10
```
Then save the file and reboot.

To test above command worked correctly, open a terminal and type:
```
cat /proc/sys/vm/swappiness
```
You should get a result of 10 if it worked correctly.

Thanks for that, and yes I  now get 10. 

That does seem to improve the speed of scrolling.

I wish now that I could get the taskbars to snap into position rather than sulk. Would there be an animation feature I can turn off somewhere?

---

### Post by LowSky on 2009-09-23
what mouse do you have that isn't supported in later versions? If anything Mouse support is much better than the old days of 7.04 and older.

I remember having to set up my Logitech MX518 and it being really annoying, now it just works

---

### Post by Bölvaður on 2009-09-23
> **dgub said:**
> 
Firstly I auto hide the toolbars. They are slow to respond and then creep out of hiding.
Do you mean that when you put your mouse at the end of the screen it takes the panel few seconds to come down?

For me it looks very smooth, but it takes about 1 second to show. I guess there must be a config file to change that time closer to 0.5 or 0.25s which might be a better choice.


> **dgub said:**
> 
Firefox and Opera are very slow. I use auto scroll a lot and scrolling down a page is slow and jerky.


For activating auto scroll in firefox go to [this website ]("about:config") and filter out autoScroll, change the parameter to **true**.

If you are meaning that internet is slow, then the new Opera might be right for you, it loads pages faster by compressing the content.
Or if you are saying there is screenlag when you scroll then there might be that you dont have the correct driver installed.

It is very difficult to know what you are asking for when you say something is slow... but now exactly how.:confused:

---

### Post by dgub on 2009-09-23
> **LowSky said:**
> what mouse do you have that isn't supported in later versions? If anything Mouse support is much better than the old days of 7.04 and older.

I remember having to set up my Logitech MX518 and it being really annoying, now it just works

I have Cherry Ergo Shark L. When I searched I could not find any support for it.

---

### Post by dgub on 2009-09-23
> **Bölvaður said:**
> Do you mean that when you put your mouse at the end of the screen it takes the panel few seconds to come down?

For me it looks very smooth, but it takes about 1 second to show. I guess there must be a config file to change that time closer to 0.5 or 0.25s which might be a better choice.




For activating auto scroll in firefox go to [this website ]("about:config") and filter out autoScroll, change the parameter to **true**.

If you are meaning that internet is slow, then the new Opera might be right for you, it loads pages faster by compressing the content.
Or if you are saying there is screenlag when you scroll then there might be that you dont have the correct driver installed.

It is very difficult to know what you are asking for when you say something is slow... but now exactly how.:confused:

With the previous post, the autoscroll speed issue is fixed, and I am using Opera 10. Internet speed is down to whatever comes down the line.

It is the toolbar which I would like to speed up. I agree it is smooth, just much slower than I am used to in XP. Is there a way of controlling this please.

---

### Post by sigurnjak on 2009-09-23
This is copy from my tip collection  regarding hiding gnome panels :

 HOWTO: Better Autohide Gnome Panel
When I first came to Ubuntu from windows, I was used to having my panel autohide: in gnome, it just felt clunky. I stumbled across this fix, but I doubt most new users would, so I made a howto. I figured it was something that Windows converts (or anyone for that matter) might want to work smoother.


1. Go to Applications> System Tools> Configuration Editor


Note: I think this menu item was removed in dapper. You can either use alacarte menu editor to put it back or it can be opened simply with the command gconf-editor in a terminal

2. In the configuration editor, go to apps/panel/top level

3. In this folder there will be a few folders called something like panel_0, panel_1, top_panel_screen0 or similar. These folders are the options for your respective panels. Find the ones with autohide checked: these are your panels that you have set to autohide (obviously).

4. Right click and "Edit Key..." on each of the fields listed below and set these values:

Name = Value

auto_hide_size = 0
hide_delay = 300
unhide_delay = 0

That's it! You can of course change these values to whatever you prefer.

auto_hide_size is how much of the panel you want to show when it is hidden
hide_delay is how long until the panel hides itself after your cursor leaves the panel
unhide_delay is how long until the panel unhides when you put your cursor over it.

Hope it helps !

---

### Post by dgub on 2009-09-24
> **sigurnjak said:**
> This is copy from my tip collection  regarding hiding gnome panels :

 HOWTO: Better Autohide Gnome Panel
When I first came to Ubuntu from windows, I was used to having my panel autohide: in gnome, it just felt clunky. I stumbled across this fix, but I doubt most new users would, so I made a howto. I figured it was something that Windows converts (or anyone for that matter) might want to work smoother.


1. Go to Applications> System Tools> Configuration Editor


Note: I think this menu item was removed in dapper. You can either use alacarte menu editor to put it back or it can be opened simply with the command gconf-editor in a terminal

2. In the configuration editor, go to apps/panel/top level

3. In this folder there will be a few folders called something like panel_0, panel_1, top_panel_screen0 or similar. These folders are the options for your respective panels. Find the ones with autohide checked: these are your panels that you have set to autohide (obviously).

4. Right click and "Edit Key..." on each of the fields listed below and set these values:

Name = Value

auto_hide_size = 0
hide_delay = 300
unhide_delay = 0

That's it! You can of course change these values to whatever you prefer.

auto_hide_size is how much of the panel you want to show when it is hidden
hide_delay is how long until the panel hides itself after your cursor leaves the panel
unhide_delay is how long until the panel unhides when you put your cursor over it.

Hope it helps !

Thanks - that's brilliant. Just what I have been looking for. I also disabled animation so now it just snaps in and out.

Cheers

---

