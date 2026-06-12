---
title: "Power management in lucid lynx 10.04"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by wanna_try on 2010-04-28
need help
Hi, today i start my very own experience in ubuntu 10.04.
I install it on my notebook HP G7000
Can anyone help me with finding tools for power management while working?
I mean tool or utility for
make less cpu frequency for battery life
make less brightness
less RAM using (or smth)

in my previuos Vista there was program in tray whuch helps me.

Becouse without this tools my note is overheated and fan makes very noisy

Vista was absolutely quite then I set power management in econom mode.
Anybody knows this kind of issue??

:guitar::popcorn:

---

### Post by ubunterooster on 2010-04-28
Right click on panel. Select add to tray. Add "Brightness applet" and "CPU frequency scaling monitor"

---

### Post by wanna_try on 2010-04-29
thanks, It works, notebook makes less noise, but in windows it was noiseless.
I suppose may be any tools to make fan slowly?

---

### Post by ubunterooster on 2010-04-29
try ```
sudo apt-get computer temp
```Then "add to panel" computer temperature monitor.
It may, *may*, show you temps. This will help figure out if the problem is heat. I actually have very little knowledge of fans so I wish you all the best and hope someone else can help here
edit, get also: sudo apt-get ksensors

---

### Post by wanna_try on 2010-04-30
not working

---

### Post by Franc Kaos on 2010-05-03
> **ubunterooster said:**
> Right click on panel. Select add to tray. Add "Brightness applet" and "CPU frequency scaling monitor"

Just wanted to offer my thanks for this info, starting to love Ubuntu, but battery life did seem awful, but this, along with powertop is def helping. Gonna check out Debian Laptop Mode Tools as well - when I feel comfortable about installing.

:popcorn:

---

### Post by sripplinger on 2010-05-27
I just barely installed Kubuntu 10.04 on my laptop and the fans were running constantly.  Once I installed the ATI fglrx drivers this changed.  I'm not sure if this was coincidental or it the graphics drivers are helping things run cooler now.  Just a thought in case this helps.

---

### Post by lidex on 2010-05-27
> Since  Lucid 10.04 laptop-mode-tools is deprecated and conflicts with standard packages.

To manually activate laptop-mode type:

sudo laptop_mode start

however this will only last until next reboot.

Laptop mode is disabled by default in Ubuntu. To enable it open terminal shell and type:

sudo gedit /etc/default/acpi-support

At the bottom of the file, there is ENABLE_LAPTOP_MODE variable, set this to true. A restart is required to enable this setting.

Read through this file to see some of the other options.

Ensure you have laptop-mode-tools installed:

sudo apt-get install laptop-mode-tools laptop-detect

Linux can use different power management profiles called “governors.” By default, Ubuntu does not allow you to change which governor it uses, however you can enable the option with one command:

sudo dpkg-reconfigure gnome-applets

After that, make sure you have the “CPU Frequency Monitor” applet running in your Gnome panel. Right click on the applet and go to the Preferences. Under “Frequency Selector” section, make sure the “Show menu” is selected on “Frequencies and Governors.”

Then you can left click on the applet and from here, choose which governors or frequencies to use.

You can change this via the command line without having to enable anything. Just go to /sys/devices/system/cpu/cpu0/cpufreq/ (if you have multiple processors/cores/hyperthreading change cpu0 to cpu1, cpu2, etc. for each cpu you have listed) and edit the file (use sudo) “scaling_governor”, just change the governor that is listed to whatever governor you want to use. Available governors are listed in “scaling_avail_governors”

man laptop-mode.conf

and edit /etc/laptop-mode/laptop-mode.conf

Consider installing also powertop which could easily help you reducing energy consumption by analyzing actual energy wasts and give you useful tips on how to save.

sudo apt-get install powertop



Also see this page:
[http://linux.aldeby.org/linux-laptop-power-saving-customization.html]("http://linux.aldeby.org/linux-laptop-power-saving-customization.html")

---

### Post by sripplinger on 2010-05-28
Interesting.  What exactly is this 'laptop mode' supposed to do?  On my laptop (running lucid) things seem to be running pretty well.  For instance, my speakers turn off when I plug in the headphones, which I thought was a laptop only feature (that I had to manually enable in previous versions).  I guess I'm just curious what I might be missing.

---

### Post by screaminj3sus on 2010-05-28
afaik laptop-mode mainly deals with spinning down hard disks when they are idle, its disabled by default because there has been problems with that feature in the past.

---

### Post by sripplinger on 2010-05-28
Okay, thanks for the info.  Looks like if things are running okay for me now I won't want to install something that could potentially cause me problems later.

---

### Post by lavinog on 2010-05-28
> **sripplinger said:**
> I just barely installed Kubuntu 10.04 on my laptop and the fans were running constantly.  Once I installed the ATI fglrx drivers this changed.  I'm not sure if this was coincidental or it the graphics drivers are helping things run cooler now.  Just a thought in case this helps.

In lucid, the open source ati drivers have all power saving features disabled.  The fglrx driver has them all available and enabled.

The open source drivers needs a 2.6.34 kernel, or modesetting needs to be disabled.

---

### Post by squiddy on 2010-06-01
> **lavinog said:**
> In lucid, the open source ati drivers have all power saving features disabled.  The fglrx driver has them all available and enabled.

The open source drivers needs a 2.6.34 kernel, or modesetting needs to be disabled.

and lucid won't have 2.6.34 kernel, right?

---

### Post by lavinog on 2010-06-01
> **squiddy said:**
> and lucid won't have 2.6.34 kernel, right?
Correct.

There is a ppa to install later versions:
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)
Make sure you read the whole thing.

Or you can compile your own.

One issue that occurs if you use a later kernel is that ureadahead will fail.

You might be able to use the maverick kernel, but I haven't looked into it yet.

If you are still new to linux / ubuntu, you may want to try disabling kms instead:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

