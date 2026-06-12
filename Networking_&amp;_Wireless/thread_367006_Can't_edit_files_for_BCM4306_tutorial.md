---
title: "Can't edit files for BCM4306 tutorial"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by Wowl on 2007-02-21
I'm following the fantastic tutorial ([http://www.ubuntuforums.org/showthread.php?t=340689](http://www.ubuntuforums.org/showthread.php?t=340689)) telling me how to set up my wireless card, but I'm sturggling when it says sudo nano /etc/iftab
I get a different looking terminal opened with GNU nao 1.3.12 at the top and many options at the bottom (^G Ge Help ^O Writeout etc) but there's no where for my to remove the # as the tutorial says.

Please can anyone help?

---

### Post by teaker1s on 2007-02-21
do you have gnome desktop?
if so
[COLOR="Red"]gksudo gedit /etc/iftab[/COLOR]

then use file tab and select "save as"

---

### Post by Wowl on 2007-02-21
Thanks

I've come across another problem for me: my laptop ahs no internet access and I can only tranfer files to it via USB pen drive. 

So when it says to download build-essentials, it can't get them from the internet. Are they essential and is there a way round this?

Thanks

---

### Post by teaker1s on 2007-02-21
you need build-essential to compile, now I know the alternate.iso has all the packages to install without internet access, I'm not sure about live cd. We could check if you like by
[COLOR="Red"]gksudo synaptic[/COLOR]
hit edit tab
click on ADD-CDrom
follow prompt and hit reload tab

select search tab
search name and description
type ndiswrapper
search

p.s If you rather compile your ndiswrapper,you would be better following the one in my link as it's far more comprehensive

---

### Post by maclenin on 2007-02-21
**Wowl:**

Thanks for the feedback on the bcm4306 tutorial - I designed it with ease of use in mind.... However, I agree with teaker1s that should you need more detail - i.e. greater explication re: the various steps in the process - take a peek at the "howto" link at the top of my [tutorial]("http://www.ubuntuforums.org/showthread.php?t=340689"), as it leads to the same guide teaker1s references, here (and the same guide to which teaker1s sent me when I was first trying to get my wireless card up and running)....

**teaker1s:**

As for the compiling comment - I assume that what I show in my tutorial is a compile of ndiswrapper - as I've taken the steps, fairly gratuitously, from FrodoB's Überguide. If this is not the case, please enlighten, as I am always accepting suggestions for (guide) betterment....

---

### Post by teaker1s on 2007-02-21
> As for the compiling comment - I assume that what I show in my tutorial is a compile of ndiswrapper - as I've taken the steps, fairly gratuitously, from FrodoB's Überguide. If this is not the case, please enlighten, as I am always accepting suggestions for (guide) betterment


First my I apologize for my poorly worded comments, I think people making howto's is great for the community. 
What concerns me is howto's not on wiki get buried and also if on wiki they get refined by various people. I wonder if you would like to incorporate your work into the wiki  and update your howto?

As I see it both current wiki and your howto have one common issue:-we assume that people have internet access, now this isn't such an issue until we realise they don't have internet access.
Now maybe we could work together and distill a precise section on adding cdrom sources to gain build essential?

---

### Post by Wowl on 2007-02-22
Thanks so much guys, this is one of the reasons I'm switching to ubuntu - the community. If I had a Windows problem I'd spend a couple of hours speaking to someone who knows about as much as me reading from a dialogue in a foreign call centre!

I want to easiest and fastest way to get my wifi card working - its a Linksys WPC545:
WifiCard: 02:00.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:00.0 0280: 14e4:4320 (rev 02)

I don't particularly need to compile my own ndiswrapper (indeed I'm new to Linux and the idea of making my own code-based installers is quite daunting). I now have both the alternate iso and the main iso. If possible, could you please recommend the best (well, easiest) way to get my drivers working. @teaker - will you guide still apply even though its for BCM4311 and my chipset is BCM4306 without any changes?

EDIT: have just installed ndiswrapper from the CD (and build-essential frmo the alternate ISO) but I don't know if I need to rebuild the headers to continue?

---

### Post by teaker1s on 2007-02-22
It is possible to do it without internet access or a cdrom drive, we will have to manually satisfy dependencies though (dependencies are packages required before the main package will install)

So I'm guessing we are still going the usb pen drive route ?

this section in link scroll to installing driver and the rest will be advice on what to do next
[link]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f1b6201d0b5822506a2df08fa5b8314f4237e765")

---

### Post by Wowl on 2007-02-22
Ok thanks for all the help. I think I'm nearly there.

I've got a hi-speed connection on this computer so I've downloaded both the live ISO and alternate. I've also installed the build-essential from the alternate (inc all dependencies) and the ndiswrapper (inc common and utils) and it all went fine.

So what's the next step please? 
updating headers (or does synaptic do this automatically), installing the inf files etc (I'm using the driver file from this tutorial ([http://www.ubuntuforums.org/showthread.php?t=340689](http://www.ubuntuforums.org/showthread.php?t=340689)) but downloaded and put ona  usb pen drive)

Thanks

---

### Post by teaker1s on 2007-02-22
cd into directory containing the .inf file example

```
cd /home/daniel/drivers
```

install the driver
next ```
sudo  ndiswrapper -i  nameofdriver
```
start ndiswrapper
```
sudo modprobe ndiswrapper
``` 
check driver and hardware installed and present
```
sudo ndiswrapper -l
```

---

### Post by Wowl on 2007-02-22
It works! Thanks so much!

I can access the Internet!!!!

All the help and tutorials are very much appreciated. Now I can start my ubuntu journey.....
...just a pity I can't find the options menu in firefox! Isn't it usually under the tools tab?

---

### Post by Wowl on 2007-02-22
Sorry to be a pain again but since installing the updates as it told me and restarting, I now get "SIOCGIFFLAGS error: no such device" when I try to get on the network icon in the top right of the screen and it won't connect to the Internet.

I can fix this by typing: sudo modprobe ndiswrapper, then sudo ndiswrapper -l, but how can I automate this so it does it by default on boot?

Thanks

---

### Post by maclenin on 2007-02-22
**Wowl:**

Congratulations re: connecting!

As for the trobleshooting....

**Firefox:** I think the **Options** settings you are looking for can be found under **Edit > Preferences**.... The Windows version and Linux version of Firefox seem to place and name the "place to change settings" differently....

**SIOCGIFFLAGS:** Have you tried making the ndiswrapper permanent using:

```
sudo ndiswrapper -m
```

If not, give it a whirl and then check...

```
cat /etc/modprobe.d/ndiswrapper
```

...to make certain it contains:

```
alias wlan0 ndiswrapper
```

Reboot your computer and, hopefully, this will have taken you to ndiswrapper permanence!

**teaker1s:**

Thanks for the commentary - no worries re: compile wording - I just wanted to make certain I wasn't leading anyone astray (as I am also still (and will probably always be) learning the ropes)....

As for the wiki add - I am flattered - and also interested in making whatever changes would help keep the guide relevant. In the short term, I'll add a couple of lines (or make clear) that the guide requires an internet connection. As for the non-internet connection (alternate CD) route, I cannot comment/guide on that - as I have not tested that route, myself.... I like to test and retest and test again those steps I put into my guides.... What sorts of steps would you suggest be added in order to address the non-internet route? Is it, essentially, a LiveCD vs. alternateCD installation path issue?

Incidentally, I have tested the "copy the .conf file" command - and it seems to work, but I am not completely clear why we need to "copy the .conf file" - do you know what this step (step 12 in my guide) does?

Thanks (again) for the insights!

Cheers!

---

### Post by teaker1s on 2007-02-22
I haven't had any conf file editing, I'm using [COLOR="Red"]network-manager-gnome [/COLOR] on my laptop to deal with config issues.

One of the most fustrating things for people I think is the fustration of lots of terminal to get wireless.
As I see it we should explain that we can get you up and running with 
repository ndiswrapper and network-manager-gnome ,as a first option and then offer the compiled route and manual network config to either those the repository route failed or require a wireless connection without gui.

I'm still a fan of gui first, then terminal for those who want to-kind of like learning to walk before running

I think that for non internet connection we should suggest synaptic with the ADD-CDrom feature, it's both friendlier than apt-get and aptitude and it means that ticking boxes lowers the risk of failure through either miss typing or version change.

---

### Post by maclenin on 2007-02-23
**Wowl:**

Please let us know if you have any other questions - as we ramble here, we are not forgetting that we do so in your "space"! Interject at any time....

**teaker1s:**

I am a HUGE fan of the terminal.... Not that I am anti-gui (by any means), but I find the freedom afforded in feeling like I have "control" over (and am understanding) how the computer behaves, a breath of fresh air - certainly, after coming from the Windows world. The gui (feels exactly that, gooey and) it can get in the way of troubleshooting (for me).... With the terminal, I feel like I can go straight to the "source", to the "root" of the issue to which the gui is unable to penetrate - the terminal lays it all bare (i.e. mis-typing or resolving version / kernel update issues, modprobes, nanos, among other things - I love the terminal's aptitude!).... That's me.

Having said that, I see nothing wrong with your approach - as there are folks (such as yourself) who are gui fans (vs. terminal fans) - feeling more comfortable with one over the other. Guides could be prepared in all flavors.... I just think it important (across or within guides) to create "links" among them - sharing the benefits of all approaches - as you seem to mention (though I have yet to link gui, substantially, to mine)....

To me, it's a knowledge is power issue.... With the knowledge of how the terminal (and the gui) works you feel more confident in your own ability ("hey, this is cool") to build and troubleshoot (and are then more able to help others feel the same ("hey, this is cool"))!

This (access to the terminal) is one of the major reasons I am having such a great time with (this flavor of) linux!

Anyway - back to the guide concept:

Can you enumerate the steps you have in mind that would "wrap" around the wrapper guides already out there? These steps should be fleshed out and tested.... I see (from what you've already presented) where your steps might intersect - I'd just like to see more detail (so that I, hopefully, might better understand)....

---

