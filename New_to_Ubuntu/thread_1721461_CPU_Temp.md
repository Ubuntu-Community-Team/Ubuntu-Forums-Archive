---
title: "CPU Temp"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-04-04
As I had been having a computer that frozze now and then, I came up with the idea that maybe the cpu may be over heating

Does any one know of an app that I can install on ubuntu 64 to run at all times in the top pannel just to watch and see what emp my cpu is running at?

Dave

---

### Post by WannabeFantasma on 2011-04-04
try typing "sensors" in the terminal
It gives you some temperatures...

---

### Post by Dutch70 on 2011-04-04
Just curious, what video/graphics card do you have?
Run this command to find out if you're not exactly sure.
```
lspci | grep VGA
```

---

### Post by Enigmapond on 2011-04-04
You can also just install screenlets. There is one that will monitor that, you can set to always be up.

Cheers!

---

### Post by Dutch70 on 2011-04-04
> **WannabeFantasma said:**
> try typing "sensors" in the terminal
It gives you some temperatures...

I think you have to install lm_sensors for that to work.
[https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto")

---

### Post by madmax75 on 2011-04-04
From your Synaptic package manager, install the Gnome Sensors Applet (search Synaptic for *sensors-applet*). You can then install it to your top panel by right-clicking it and choosing "Add to panel..."

You might also want to check out *cpulimit*. It's a command-line program for restricting processes to hog processor resources, thus preventing overheating. It should also be in the software repositories (available through Synaptic/Software Center).

[http://cpulimit.sourceforge.net/](http://cpulimit.sourceforge.net/)

---

### Post by bodhi.zazen on 2011-04-04
An alternate method, you can often display temp from the bios.

---

### Post by WannabeFantasma on 2011-04-04
> **Dutch70 said:**
> I think you have to install lm_sensors for that to work.
[https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto")

Ow think my laptop showed them even without doing that...

---

### Post by DaveMcC on 2011-04-04
> **Dutch70 said:**
> Just curious, what video/graphics card do you have?
Run this command to find out if you're not exactly sure.
```
lspci | grep VGA
```

See that funny thing just in front spci
Where does that live on a keybrd?
Dave

> **WannabeFantasma said:**
> try typing "sensors" in the terminal
It gives you some temperatures...
Yip, that shows the temp's OK,
But I want it running all the time up in top pannel

Dave

---

### Post by Joe of loath on 2011-04-04
> **DaveMcC said:**
> See that funny thing just in front spci
Where does that live on a keybrd?
Dave

...

It's called a lower case L.

---

### Post by DaveMcC on 2011-04-04
> **madmax75 said:**
> From your Synaptic package manager, install the Gnome Sensors Applet (search Synaptic for *sensors-applet*). You can then install it to your top panel by right-clicking it and choosing "Add to panel..."

You might also want to check out *cpulimit*. It's a command-line program for restricting processes to hog processor resources, thus preventing overheating. It should also be in the software repositories (available through Synaptic/Software Center).

[http://cpulimit.sourceforge.net/](http://cpulimit.sourceforge.net/)

Some where between install, "which I done" and right clicking to add to pannels
I lost it, or it lost me, or we both lost the plot
Try a reboot, while waiting for reply

Dave

Err, no,,, reboot made no difference 
still can't see a thing to show cpu temps

Dave

> **Dutch70 said:**
> Just curious, what video/graphics card do you have?
Run this command to find out if you're not exactly sure.
```
lspci | grep VGA
```

Going by the code up top its a 

```
boss@boss-desktop:~$ lspci I grep VGA
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
boss@boss-desktop:~$ ^C
boss@boss-desktop:~$ 
```

Or as the box puts it, its only new to me
GeForce 8400 GS 256MB PCI-E Graphics Card

Dave

---

### Post by Joe of loath on 2011-04-04
That | symbol is a pipe, not an I or whatever you replaced it with. On a UK keyboard it's bottom left, on a US keyboard it's just left of the return key IIRC.

---

### Post by Dutch70 on 2011-04-04
> **DaveMcC said:**
> See that funny thing just in front spci
Where does that live on a keybrd?
Dave


All you need to do is copy & paste the command into a terminal. I'ts safe, I plomise. :)

Btw, the link I gave, also has an option of putting it on your desktop, and there is always... Conky.

---

### Post by DaveMcC on 2011-04-04
> **Dutch70 said:**
> All you need to do is copy & paste the command into a terminal. I'ts safe, I plomise. :)

Btw, the link I gave, also has an option of putting it on your desktop, and there is always... Conky.

Yip that got the short version and the correct one

02:00.0 VGA compatible controller: nVidia Corporation Device 10c3 (rev a2)

I like the ksensors bit, it just don't want to install. then maybe its for Kubuntu

As for "The easiest way of installing a package is to click **Applications** &#8594; **Add/Remove...**. Fin"

I don't have  [B]Add/Remove

Dave
[/B]

Update, I do have add remove its just renamed to Ubuntu Software Centre

Getting back to the cpu temp app that I would like to see installed on the task bar, pannels
Its good to see that ubuntu true to form, it don't work, none of them do
Let's see
Google earth don't work
CPU temp app don't work
I just hope that virus don't work
Or maybe they do work, and that stops the rest from working
Being a nooooooobiiiee to ubuntu it ain't a great start

Dave

---

### Post by bodhi.zazen on 2011-04-04
Sorry you are having a problem, but that is why I mentioned yoru BIOS.

lm_sensors can sometimes be problematic on some CPU and / or debugging lm_sensors can take more time then it is worth.

I suggest you :

1. Take a look at top to see if any process is using a high percentage of your CPU.

Top is command line only , so run it in a terminal.

2. Boot to your BIOS (hit F2 , esc, F8, or whatever you need to get into your BIOS as you boot). Many bios will show you your CPU temp (bios vary, you will need to look through the menu).

If you are still having a problem, most problems with over heating are due to dirt / dust.

Shut your computer off, unplug it, and open the case. Carefully clean the air vent and fan. I personally use a vacuum cleaner =)

The restart it and see if it helps with the temp.

---

### Post by Zanderist on 2011-04-04
Is there a way to  force the CPU fan on;
```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C                                    

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +60.5°C  (high = +70.0°C, crit = +115.5°C)  

```

---

### Post by DaveMcC on 2011-04-05
> **bodhi.zazen said:**
> Sorry you are having a problem, but that is why I mentioned yoru BIOS.

lm_sensors can sometimes be problematic on some CPU and / or debugging lm_sensors can take more time then it is worth.

I suggest you :

1. Take a look at top to see if any process is using a high percentage of your CPU.

Top is command line only , so run it in a terminal.

2. Boot to your BIOS (hit F2 , esc, F8, or whatever you need to get into your BIOS as you boot). Many bios will show you your CPU temp (bios vary, you will need to look through the menu).

If you are still having a problem, most problems with over heating are due to dirt / dust.

Shut your computer off, unplug it, and open the case. Carefully clean the air vent and fan. I personally use a vacuum cleaner =)

The restart it and see if it helps with the temp.

Thanks for all the info, but I just wanted to see what temp the thing runs at when under load
And to go to the PITA of rebooting to bios , na, ain't worth the hassle
When I am running winxp "needed" the icore temp runs along side win in task bar
I just wanted the same in ubuntu

> **Zanderist said:**
> Is there a way to  force the CPU fan on;
```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C                                    

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +60.5°C  (high = +70.0°C, crit = +115.5°C)  

```

Yes, plug in a new one
Fan don't run it's done, even if it is running, it could be way too slow

---

### Post by Razorback on 2011-04-05
This looked interesting.  Nice front end but not sure about compatibility:

[http://computertemp.berlios.de/](http://computertemp.berlios.de/)

[http://ubuntuforums.org/showthread.php?t=1679070&highlight=computertemp](http://ubuntuforums.org/showthread.php?t=1679070&highlight=computertemp)

---

### Post by psusi on 2011-04-05
60C, when under load, is not that hot.  If you want to continuously monitor it in the gui, you can install the sensors-applet package and add it to the gnome panel.

If you install lm-sensors and run sudo sensors-detect, it may be able to detect and configure the chip on your motherboard to monitor and possibly control the speed of the fans, but usually control is limited to only the cpu fan.

---

### Post by DaveMcC on 2011-04-05
Razorback
I see what you mean, me thinks

Dependency is not satisfiable: python-gnome2-desktop

And I have just spent the 30min chasing my (tail?)

Oh woe is Ubuntu
I wish this could work
To see my temp
NO! not me, just my cpu

Dave

Some day I may be rich and famous, until then poor lines I write you must read

---

### Post by Joe of loath on 2011-04-05
What happens when you try install python-gnome2-desktop? ;)

---

### Post by Zanderist on 2011-04-05
I decided to use a highlight to prop up the back of my laptop to allow airflow to the fan.

It seems to be hovering around 40C ( then again I just started up the machine for the first time today)

---

### Post by DaveMcC on 2011-04-06
> **Joe of loath said:**
> What happens when you try install python-gnome2-desktop? ;)

Don't know what that is, don't know where to find it, don't know how to install it
Don't know if I want to try and install it, does it work on 64 bit?

Dave

> **Joe of loath said:**
>  There's no place like ~/  			

And there I was thinking that many years ago, the DOS prompt was allowed to die
Wish it would die in Linux, cuz there be some stupid commendsments

---

### Post by Joe of loath on 2011-04-06
> **DaveMcC said:**
> And there I was thinking that many years ago, the DOS prompt was allowed to die
Wish it would die in Linux, cuz there be some stupid commendsments

Hey I tell you what, I'll give you my servers to administer, but will only give you VNC to do it by. Lets see how far you get that way ;) The terminal is the most powerful way to use *NIX based OSes, after a while using Linux you'll find that out.

See what happens when you open a terminal and type ```
sudo apt-get install python-gnome2-desktop
```

---

### Post by DaveMcC on 2011-04-06
> **Joe of loath said:**
> Hey I tell you what, I'll give you my servers to administer, but will only give you VNC to do it by. Lets see how far you get that way ;) The terminal is the most powerful way to use *NIX based OSes, after a while using Linux you'll find that out.

See what happens when you open a terminal and type ```
sudo apt-get install python-gnome2-desktop
```

sudo apt-get install python-gnome2-desktop
Nothing happen
Opened Terminal up, copy / paste that in, hit enter
Still waiting

My 20 gauge VNC shot gun can fix any server, even if it don't power up

---

### Post by Joe of loath on 2011-04-06
Did it prompt you for your password, even?

---

### Post by DaveMcC on 2011-04-06
> **Joe of loath said:**
> Did it prompt you for your password, even?

Yes, put that in still nothing,

---

### Post by Razorback on 2011-04-06
hmmm....maybe this one.

[http://forums.linuxmint.com/viewtopic.php?t=53278&f=142](http://forums.linuxmint.com/viewtopic.php?t=53278&f=142)

---

### Post by DaveMcC on 2011-04-06
There we go, some thing else that don't work, mind you,,, when I do type my password into "Terminal" nothing at that point happens

Know what I think,,, "Terminal" It thinks its MS Windows XP or 7, maybe even 8 nice to look at, talk about and say how good it is, just don't ask it to do any thing

Joe of loath, you wrote
The terminal is the most powerful way to use *NIX based OSes, after a while using Linux you'll find that out.

 (you'll find that out) it don't work

I think you may work for micro shaft

Dave

went into "Editing profile default" clicked on title and command
unchecked update log in records when command is launched

Then ran sensors-detect and got this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
boss@boss-desktop:~$  sensors-detect
You need to be root to run this script.
boss@boss-desktop:~$ 
```

Then done this, got this as reply

```
boss@boss-desktop:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
boss@boss-desktop:~$
```

I then done this

```
sudo apt-get install python-gnome2-desktop
```

And got this
[code]boss@boss-desktop:~$ sudo apt-get install python-gnome2-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gnome2-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-gnome2-desktop' has no installation candidate
boss@boss-desktop:~$ [/code

Dave

---

### Post by Joe of loath on 2011-04-06
> **DaveMcC said:**
> 
boss@boss-desktop:~$  sensors-detect
You need to be root to run this script.
boss@boss-desktop:~$ 


Dave

Hence you need to be root. Try ```
sudo sensors-detect
``` instead.

---

### Post by DaveMcC on 2011-04-06
Two things
1 I thought I was root,

2 every time I type password, (when asked) into "Terminal" nothing happens, hit enter and I get

boss@boss-desktop:~$ sudo sensors-detect
[sudo] password for boss: 
Sorry, try again.
[sudo] password for boss:

---

### Post by Joe of loath on 2011-04-06
1. Nope. you're a regular user, for security reasons. This isn't Windows we're talking about ;)

2. It won't show your password on screen. Type it out carefully and hope you got it right ;)

---

### Post by DaveMcC on 2011-04-06
when I type in my password nothing, not a thing,  dam all, happens the cursors just sits and blinks

Dave

---

### Post by Kixtosh on 2011-04-06
Alright, I have exactly what you are asking for (a temperature monitor in the top panel all the time) on at least three laptops. I think this link should help you get it.

[http://sensors-applet.sourceforge.net/index.php?content=packages](http://sensors-applet.sourceforge.net/index.php?content=packages)

If I then right click on my top panel, and choose "Add to panel", I simply choose from the list displayed:

"Hardware Sensors Monitor."

The "About" script, when I right click on the temperature display shows:

"GNOME Sensors Applet 2.2.3"

I'm not sure how to figure out exactly how I got it there,  since it was a while ago, but now that you already seem to have lm-senors, the sensors-applet is also available from the Ubuntu Software Center if you do a search for it.

To add to what has been said already, some CPU's run hotter than others. My coolest is an ancient PIII mobile, that runs around 50°C to 65°C. My hottest is a Pentium M (ULV) that runs normally at 60°C and tops out at 75°C when watching video. If I'm not watching video it immediately drops down below 70°C again, and the fan stops whirring so fast. At 60°C or below, the fan doesn't even turn on. A lot of CPU's aren't even considered critical until they reach 90°C or beyond, from what I've read.

---

### Post by MartyBuntu on 2011-04-06
I also use **xsensors** for temperature monitoring.

It's in the repositories.

---

### Post by Joe of loath on 2011-04-07
> **DaveMcC said:**
> when I type in my password nothing, not a thing,  dam all, happens the cursors just sits and blinks

Dave

That's the point. See my post above.

---

### Post by DaveMcC on 2011-04-07
> **Joe of loath said:**
> That's the point. See my post above.

Seen that!
I am trying not to **** you off here, but and its a big but,, I could play "Bat out of Hell, the entire album" on the keybrd, and the blinking black point of the cursor, will not move, not one stoke of the keybrd goes into it

Terminal is dead, it will ask for a password, I slowly type it in, nothing happens

That is why I am claiming it works for micro shaft, good to meet you, but no work today

Dave

> **Kixtosh said:**
> Alright, I have exactly what you are asking for (a temperature monitor in the top panel all the time) on at least three laptops. I think this link should help you get it.

[http://sensors-applet.sourceforge.net/index.php?content=packages](http://sensors-applet.sourceforge.net/index.php?content=packages)

If I then right click on my top panel, and choose "Add to panel", I simply choose from the list displayed:

"Hardware Sensors Monitor."

The "About" script, when I right click on the temperature display shows:

"GNOME Sensors Applet 2.2.3"

I'm not sure how to figure out exactly how I got it there,  since it was a while ago, but now that you already seem to have lm-senors, the sensors-applet is also available from the Ubuntu Software Center if you do a search for it.

To add to what has been said already, some CPU's run hotter than others. My coolest is an ancient PIII mobile, that runs around 50°C to 65°C. My hottest is a Pentium M (ULV) that runs normally at 60°C and tops out at 75°C when watching video. If I'm not watching video it immediately drops down below 70°C again, and the fan stops whirring so fast. At 60°C or below, the fan doesn't even turn on. A lot of CPU's aren't even considered critical until they reach 90°C or beyond, from what I've read.

Thankyou, not one person said the magic words of HOW TO

"If I then right click on my top panel, and choose "Add to panel", I simply choose from the list displayed:"

I had the app installed from ??:confused:?? 

My bios reports the cpu's to run at 45 deg C, the apps are reporting 24 - 27 deg C dual processor and the GPU at 41deg C

But I can now turn my fan speed down watch the temp, if this computer starts to freeeeze again at least I can see the cpu temps either rule them out or in, if it ain't them it may be faulty mem sticks I have 3gb

Dave

---

### Post by MartyBuntu on 2011-04-07
> **DaveMcC said:**
>  I slowly type it in, nothing happens



Nothing is supposed to happen. The password is being entered, but "invisibly".

Type the password correctly...hit ENTER.

---

### Post by MartyBuntu on 2011-04-07
> **DaveMcC said:**
> ...if this computer starts to freeeeze again...

I'm going to go out on a limb and say your freezing problem might not necessarily be temperature related.

Run MEMTEST. Post your system specs as well.

---

### Post by DaveMcC on 2011-04-07
Three times I have typed in my password correctly   I DO KNOW MY PASSWORD

```
boss@boss-desktop:~$ sudo sensors-detect
[sudo] password for boss: 
Sorry, try again.
[sudo] password for boss: 
Sorry, try again.
[sudo] password for boss: 
Sorry, try again.
sudo: 3 incorrect password attempts
boss@boss-desktop:~$ 
```

Where does memtest live at ? 

```
boss@boss-desktop:~$ memtest
memtest: command not found
boss@boss-desktop:~$ MEMTEST
MEMTEST: command not found
boss@boss-desktop:~$ PASSWORD
PASSWORD: command not found
boss@boss-desktop:~$ 
```


Dave

---

### Post by Joe of loath on 2011-04-07
reboot, hold down shift as the PC boots, and memtest will be in the boot menu.

---

### Post by Kixtosh on 2011-04-07
> **DaveMcC said:**
> Thankyou, not one person said the magic words of HOW TO ...Ah good (and you're very welcome)! So, does this mean that it's working the way you want it now?

In case you haven't tried it yet, if you right click on the applet itself, you can adjust the preferences. I have it display a label with a value, rather than an icon or a graphic, so it displays as: CPU 64°C. 

If you open the "sensors" tab from within the preferences window, you can decide which sensors to show, of those that are available to you. I checked only the the ACPI THERM sensor, which enables me to monitor fan use compared to CPU temperature, but you may want to try others.

If you do use an icon or graph display (instead of a label), you may need to adjust the properties to  determine what will be considered a high or low temperature (to change  the color to red appropriately, for example).

---

### Post by DaveMcC on 2011-04-07
Kixtosh
I like the icon with value cpu1 runs at 43C cpu2 runs at 39C Vgc 54C its the hottest, cooling fan runs at 3-500 up 5500rpm

I like it now that it works, nly took six pages to get here / there? what ever when ever

Dave

---

### Post by Kixtosh on 2011-04-07
Yes, it's a problem I've noticed, even here in the Absolute Beginner Talk threads. Details that seem completely obvious to some users just don't occur to us lowly beings, so they don't get explained clearly.

Don't forget to mark your thread as "solved". That's in the [COLOR=DarkRed]**Thread Tools **[/COLOR]menu, right above the first post on your screen, to the right of the screen. Only the person who started a thread can mark it as solved.

---

### Post by DaveMcC on 2011-04-07
> **Joe of loath said:**
> reboot, hold down shift as the PC boots, and memtest will be in the boot menu.


Guess what, it ain't there
[IMG]http://i7.photobucket.com/albums/y282/dtmcc/ubuntu00.jpg[/IMG]

I found out how to edit grub and removed it, bit silly I suppose now that I want to check my mem modules
Or,, or do it the old way, get wife on my / this computer on e-bay, that is when it used to freeeze
The other computer beside this one both joined by a KVM unit never froze, it was 1 I found in a dump / recycling plant, which I took home out of the rain, put more ram into it removed winxp and installed ubuntu 9 

I think I seen some thing some where in system for testing the system

Dave

---

### Post by bodhi.zazen on 2011-04-07
> **DaveMcC said:**
> Guess what, it ain't there


If you wish, you can run memtest from most any live CD.

---

### Post by Joe of loath on 2011-04-07
> **DaveMcC said:**
> Guess what, it ain't there
[IMG]http://i7.photobucket.com/albums/y282/dtmcc/ubuntu00.jpg[/IMG]

I found out how to edit grub and removed it, bit silly I suppose now that I want to check my mem modules
Or,, or do it the old way, get wife on my / this computer on e-bay, that is when it used to freeeze
The other computer beside this one both joined by a KVM unit never froze, it was 1 I found in a dump / recycling plant, which I took home out of the rain, put more ram into it removed winxp and installed ubuntu 9 

I think I seen some thing some where in system for testing the system

Dave

Is that a screenshot of your grub menu? Because that's memtest I see right there ;)

---

### Post by DaveMcC on 2011-04-07
Yip thats a photo of the screen, taken at boot up which shows ubuntu 10 10? 32 bit, I have since put on 64bit and done the grub edit, must try screenshot now just for the crack you understand also mark this as solved

Dave

---

### Post by Razorback on 2011-04-07
> **Kixtosh said:**
> Yes, it's a problem I've noticed, even here in the Absolute Beginner Talk threads. Details that seem completely obvious to some users just don't occur to us lowly beings, so they don't get explained clearly.

Reading up on things available all over this site and the internet doesn't hurt either.  ;)

---

### Post by DaveMcC on 2011-04-07
> **Razorback said:**
> Reading up on things available all over this site and the internet doesn't hurt either.  ;)
Thats one way of wasting your life, sitting in front of a computer when you should beoutside enjoying life

Dave

---

