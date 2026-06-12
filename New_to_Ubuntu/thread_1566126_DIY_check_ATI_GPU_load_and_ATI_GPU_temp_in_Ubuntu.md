---
title: "DIY check ATI GPU load and ATI GPU temp in Ubuntu"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-09-02
i found something i want to share 

been looking for info how to get gpu load and temp in ubuntu there is no much info on internet took me whole day but i found it :)

i have ati hd4850 and catalyst 10.8

if u want to check GPU load in the terminal just type 

aticonfig --adapter=0 --od-getclocks

if you want to check gpu temp in the terminal type 

aticonfig --odgt


if you want to add gpu load to conky add this to conky conf.

${font verdana:size=8}${color green}${execi 1 aticonfig --adapter=0 --od-getclocks | grep -i GPU}

if you want to add gpu temp to conky add this to conky conf.

GPU Temp : ${color green} ${execi 1 aticonfig --adapter=0 --od-gettemperature | tail -n1 | gawk '{ printf $5 }'}°C

name color font execi grep is configurable 

in my laptop gpu usage is never more than 3% no matter what i do play hd clips use internet or vbox i dont play games so dont know what the load would be.

below is my conky

---

### Post by nhianho on 2010-10-24
Hi. I got an ATI 5650 in my laptop but I cannot check the infos using these commands. Hope you can help me find out what mistakes I've made.

Here are the results of the commands:
```
aticonfig --list-adapters
```
```
* 0. 01:00.0 ATI Mobility Radeon HD 5000 Series 

* - Default adapter
```
and
```
aticonfig --adapter=0 --od-gettemperature
```
```
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.

```

---

### Post by HittingSmoke on 2010-12-07
> **nhianho said:**
> Hi. I got an ATI 5650 in my laptop but I cannot check the infos using these commands. Hope you can help me find out what mistakes I've made.

Here are the results of the commands:
```
aticonfig --list-adapters
```
```
* 0. 01:00.0 ATI Mobility Radeon HD 5000 Series 

* - Default adapter
```
and
```
aticonfig --adapter=0 --od-gettemperature
```
```
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.

```

I just stumbled across this thread trying to do the same thing.

I'm getting the same error you are, and when I try to run *aticonfig --initial*, I get this:

```
$ aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections

```

Any ideas?

---

### Post by scifi.guy on 2010-12-31
> **HittingSmoke said:**
> I just stumbled across this thread trying to do the same thing.

I'm getting the same error you are, and when I try to run *aticonfig --initial*, I get this:

```
$ aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections

```Any ideas?


This command worked for me. I'd recommend backing up /etc/X11/xorg.conf before executing.

```
sudo aticonfig --initial -f 
```

Thanks Tracy177 for sharing the tip.

---

### Post by MestreLion on 2013-03-02
Some other useful AMD/ATI commands:

For usage % (along with clock speeds):
```
aticonfig --odgc
```

For temperature:
```
aticonfig --odgt
```

For fan speed:
```
aticonfig --pplib-cmd "get fanspeed 0"
```

And you can view them all in a single command:
```
aticonfig --odgc --odgt --pplib-cmd "get fanspeed 0"
```

Notice the absence of "--adapter=0". If not specified, it will pick your default adapter.

There are also 2 GUI apps that support ATI/AMD GPUs

AMDOverdriveCtrl
A complete Load/Temp/Fan control panel. I've never used, but looks awesome!
[http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

pSensor
Can be compiled with AMD GPU support. I use it myself, works great. But currently only Temperature and Fan speed, no GPU load
[http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)

---

### Post by QIII on 2013-03-02
Thank you for sharing.  Everyone&#8217;s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to the original thread in your new one if you think it might be helpful.

Best wishes!

**Thread closed.**

---

