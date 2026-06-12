---
title: "Laptop getting very hot after jaunty upgrade"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by llamabr on 2009-04-18
Since upgrading to Jaunty, my gateway laptop has been getting very hot, with the fan coming on much more often than before the upgrade.

How do I troubleshoot this problem?

---

### Post by swoll1980 on 2009-04-18
> **llamabr said:**
> Since upgrading to Jaunty, my gateway laptop has been getting very hot, with the fan coming on much more often than before the upgrade.

How do I troubleshoot this problem?

Easy things first. Take it apart, and clean it out.

---

### Post by eeeandrew on 2009-04-18
This can happen if the fan is clogged with dust. I'd open the laptop up and give it a good clean. Remember and ground yourself and not to touch any of the circuitry. You could also wear rubber gloves to prevent the problem of static shocking your equipment.

Hope this helps,
Andrew

---

### Post by llamabr on 2009-04-18
Thank you both.  But before I break out a screwdriver, I'd like to check the software.  It's pretty new, worked fine in 8.04, I did an upgrade, and so now it's getting hot.

I've already blown compressed air in there, and it didn't seem to make much difference.

---

### Post by Elegia on 2009-04-18
Maybe there is some process (like an indexing tool for example) running in the background? I don't think it's anything too basic, as the fans are kicking in when needed.

---

### Post by MrWES on 2009-04-18
> **llamabr said:**
> Since upgrading to Jaunty, my gateway laptop has been getting very hot, with the fan coming on much more often than before the upgrade.

How do I troubleshoot this problem?

Same here, and there are several reports of such in #ubuntu+1. On my laptop it's certainly coming from the RAM -- the cover to the RAM is very very hot, although my CPU temp is around 41C and spikes to high 50's when running something like flash video. My hhdtemp is Ok too around 45-47C. I don't seem any performance issues because of, but something is definitely going on. 

Several of us are keeping our eyes open for additional reports.

Bill

---

### Post by llamabr on 2009-04-18
There's nothing running in the background, though it's true when I leave something open in firefox with flash or something, it heats up.

My hddtemp seems ok, too, and mind is coming from the ram, seemingly.  I don't think it's any danger, but it makes it uncomfortable, and I don't feel good leaving it on when I'm not around.

It'd be nice to see a fix.  Or at least some troubleshooting ideas.

Thanks

---

### Post by Crandom on 2009-04-18
Get some blocks of woods or anything that shape and put them under the rubber "feet" on the bottom of your laptop. This will increase airflow. Alternative, buy a laptop cooler ([http://www.overclockers.co.uk/productlist.php?groupid=701&catid=57&subid=1406](http://www.overclockers.co.uk/productlist.php?groupid=701&catid=57&subid=1406) ). These blow cool air into your laptop and take about 10C off the temperature and I use them.

My temps: idle: ~63, flash: ~70, gaming ~90 (burns my hands). Serious damage at about 120, silicon melts at >1410. High due to pointless, irreversable laptop overclock.

My temps are lower after upgrade than before.

---

### Post by sarang on 2009-04-18
Just some ideas, not sure if they will help...

Install powertop and see what is causing the maximum wakeups. Kill that and see if your laptop gets as hot as before or not. Keep doing this-- I would expect to find some correlation between wakeups and dissipated heat.

Also, try booting into single user mode and then check if it gets as hot. It probably won't. Then comment out most services in some multiuser runlevel and then start them one by one. This might help in identifying the culprit.

Just out of curiosity, is your battery life down? By how much? What was it before?

---

### Post by llamabr on 2009-04-18
Thanks.  I'd like to avoid blocks of wood, or purchasing extra hardware, if possible.

I'll try single user mode, and that powertop, and see what happens.

The battery life seeems fine.

---

### Post by MrWES on 2009-04-18
> **sarang said:**
> Just some ideas, not sure if they will help...

Install powertop and see what is causing the maximum wakeups. Kill that and see if your laptop gets as hot as before or not. Keep doing this-- I would expect to find some correlation between wakeups and dissipated heat.

Also, try booting into single user mode and then check if it gets as hot. It probably won't. Then comment out most services in some multiuser runlevel and then start them one by one. This might help in identifying the culprit.

Just out of curiosity, is your battery life down? By how much? What was it before?

Thanks for the pointer on powertop -- nice package.

Definitely the source of the constant wakeups is Firefox -- even without running any flash. The only other double digit wakeup is beagled. 


Ok -- when running flash -- the bigest wakeup comes from my wireless nic card; so expected I guess.

  62.9% (342.7)       <interrupt> : ipw2200, Intel 82801DB-ICH4 


Bill

---

### Post by m4cph1sto on 2009-04-29
My laptop CPU is running 10-15 degrees C hotter idling, and 20-25 degrees C hotter under moderate load in Jaunty than it was in Hardy or Intrepid.  I use laptop-mode, and have checked powertop and iotop for problems, there are none.  The load on the CPU seems to be normal, no process is using too much CPU.  The fan is running harder in Jaunty than in Hardy or Intrepid, so it's not a fan issue. My CPU is a Pentium M Centrino, 2 ghz, and my laptop is a Toshiba Tecra M4.  I did a Jaunty clean install, using ext4 filesystems.  

There seems to be some kind of issue with Jaunty causing laptops to heat up big-time.  Time to file a bug?  I don't even know where to start for troubleshooting.

---

### Post by Qwerty_ on 2009-04-30
Can I ask if anyone is having battery problems im only get about 2 hrs out of 9.04.

---

### Post by thezood on 2009-04-30
I agree. My laptop is also running both hotter and with worse battery time. Since it's a low-end laptop (900 Mhz netbook) I've noticed a significant degradation in performance as well. Something seem to be taking resources, creating more heat and draining battery.

---

### Post by Qwerty_ on 2009-04-30
Heat does not seem to be a problem when im plugged into AC though. Only when running on battery.

---

### Post by jurojon on 2009-04-30
deleted

---

### Post by bm13084 on 2009-05-01
heat's worse on ac than on battery alone.

according to my widget (only temp gauge i have/know how to use) i used to run about 45-50c.  now im 55-60.  my laptops been shutting down due to heat.  it was perfectly fine before the upgrade.

and yes, worse battery time.

edit: have it plugged in now and it claims to have dropped back down to 45.  still feels warmish though

---

### Post by Brian_the_King on 2009-05-01
My battery time has been cut in half going from 8.10 to 9.04.. not really sure what to do

---

### Post by pastalavista on 2009-05-01
My laptop is also running hotter since upgrading to Jaunty. I assumed (possibly wrong)  that the reason for the increase in temp is because my ATI video card has no driver compatible with the new kernel and so my processor has to work much harder processing all the graphics. It is about 10 degrees hotter at idle and about 20 degrees hotter when processing video, especially in Firefox. I'm hoping that a driver fix will cool it back down.

---

### Post by lavinog on 2009-05-01
Maybe your video driver needs to be updated.

---

### Post by wedesoft on 2009-05-01
Maybe the frequency scaling (power management) does not work for some reason.

[https://help.ubuntu.com/community/InstallingUbuntuOnANexocOsiris609II](https://help.ubuntu.com/community/InstallingUbuntuOnANexocOsiris609II)

---

### Post by utnubuuser on 2009-05-01
I don't suppose tis an EXT4 issue?

Would it be possible to test these installs under ext3 as well as ext4, and show a comparison of results?

---

### Post by m4cph1sto on 2009-05-01
> **utnubuuser said:**
> I don't suppose tis an EXT4 issue?

Would it be possible to test these installs under ext3 as well as ext4, and show a comparison of results?

It's my understanding that ext4 should use less cpu than ext3 (but of course that may not be how it's behaving now).  I am using ext4, but this is my primary computer for work so I don't have the luxury of reinstalling to test this theory out.  Hopefully somebody else can.

---

### Post by llamabr on 2009-05-03
Well, I'm still running ext3, and still having the problems.

I'm not sure it's a video card issue.  It gets hot if I leave it in the terminal (alt-ctrl-f2), or if the screen blacks out from no use.

I'm stumped, and it's pretty annoying.

---

### Post by lavinog on 2009-05-03
Did you ever try cleaning the fan?
I worked on my neighbors gateway laptop, they were complaining about the heat. The fan housing opens up pretty easily and there isn't much to break in there. Thier issue turned out to be a piece of plastic jamming the fan. Not really sure how it got there.
Another friend of mine had his fan and heatsink completely coated in dust...his complaint was that his laptop was making a really bad noise...after cleaning the dust, the noise went away. (Of course he was blaming Ubuntu for the noise initially)

---

### Post by alphacrucis2 on 2009-05-03
> **llamabr said:**
> Well, I'm still running ext3, and still having the problems.

I'm not sure it's a video card issue.  It gets hot if I leave it in the terminal (alt-ctrl-f2), or if the screen blacks out from no use.

I'm stumped, and it's pretty annoying.

Which gpu does your laptop have?

---

### Post by spikoley on 2009-05-12
My laptop is also running hot after a clean install of Jaunty.  It was causing my laptop to freeze and gave me hard drive errors.  I cleaned it out and its running cooler but it is still hotter than normal.  The other 2 variables mentioned on the thread I have is the ATI card and EXT4.  In a couple of days I will do a clean install with EXT3 and see if it makes a difference.

---

### Post by norhild on 2009-05-12
I'm having the same problem. It can't be related to ext4, since I'm on a wubi clean install.

My laptop is an ACER 5930G (C2D P8400, Nvidia 9600GT, 4GB RAM DDR2@667).

With Vista GPU doesn't reach over 60ºC unless some hard work, either on Gutsy. Now with jaunty it's idle at 61ºC.

I know it can be related to compiz (which makes GPU work much more than Aero, but I don't think this is the only cause). But it seems to be also related to ventilation, or so it seems.

Any guesses on that?

---

### Post by Bölvaður on 2009-05-12
I am too one of those victims of jaunty.
Battery life was cut in half, if not more (it seems to empty abnormally fast)
And possibly 5-10°C higher than it was (never checked on hardy)

I have ext3.
No flash videos and such, as I mostly use the laptop to write down simple text in class and read lectures and books on it.
I have compiz disabled.
I thought the graphic card was working fine... might need to double check but my 5 year old laptop is getting higher resolution than my brand nvidia8800 on the desktop computer (Im using way lower resolution than max, 1024×786)
Voltage ranges from 13v to 30 sometimes without any apparant reason.


Potential faults. Tracker. But I'd think it would be disabled on battery power or be visible on powertop and ps -A

---

### Post by lavinog on 2009-05-12
What does the temp do at idle? (no mouse movements, videos, anything)

What video drivers are you all using?
I know the radeon driver is still lacking in acceleration, so 3d and video will make the cpu/gpu work much harder than normal.

I have hardy on my laptop still (compaq presario V5000 series). I have on occasion noticed that the fan will run for a while after a reboot into bios. It is as if the temps were too high. I can not recreate this every time though.

---

### Post by dsiddens on 2009-05-12
HP dv8000 AMD64.  Upgraded from Intrepid via Synaptic Package Manager.  According to "sensors-applet 2.2.1", Core 0 temp is about 198*F, 44*C.  Fan runs either full on or just one step down.  According to "System Monitor 2.26.0.1, Resources", CPU is 100%.  But under "Processes" the Load Averages For The Last 1, 5, 15 minutes are, respectively:  4.83, 4.68, 4.57.

In Intrepid the CPU load would run about 30%, unless some heavy demand was being called for.

This condition of a hot CPU after upgrading to Jaunty is not due to a dusty cooling system. This is a software issue.  Help please.
Doug

---

### Post by lavinog on 2009-05-13
> **dsiddens said:**
> Core 0 temp is about 198*F, 44*C.
That is weird: 198 degrees Fahrenheit = 92.2222222 degrees Celsius
44 degrees Celsius = 111.2 degrees Fahrenheit
Is this a bug?

> CPU is 100%.  But under "Processes" the Load Averages For The Last 1, 5, 15 minutes are, respectively:  4.83, 4.68, 4.57.

load averages >1 mean that your cpu cannot support the whole demand for all of the processes...looking at the rate of change in loads, it looks like you have a process on an infinite loop...you should find out what program that is.
post the output of:
```
 ps -eo %cpu,pid,user,args --sort %cpu|tail
```
you can also use top or htop to see processes, both seem to give you more accurate information than the system monitor
Also post the output of ```
free -m
```

---

### Post by thegreger on 2009-05-13
Same thing here, though it mostly shows up when I do stuff that takes some GPU power. My laptop isn't exactly top of the line, but still it's just half a year old. Idle temperature (probably CPU temperature. What is it that KTemperature is measuring?) is between 50 and 60, that's pretty fine. But as soon as I do anything related to graphics it goes up way too high. Just browsing a photo album too fast can get it to rise up to 80, and even though that isn't very much it gets worse when gaming. Playing Mafia on Wine rises the temperature to 95 in a couple of minutes, after which the computer beeps and shuts itself down (something about 95 being a "critical temperature"). Even playing Tux Racer with minimum settings brings it up to critical temperature and crashes the computer!
I never had any of these problems on Vista, but there I got a FPS drop when the computer were heating up (probably causing it to cool again). Jaunty doesn't seem to work in that way, just keeping up the maximum graphics quality until it crashes.

---

### Post by lavinog on 2009-05-13
thegreger: what video card do you have?

---

### Post by thegreger on 2009-05-13
> **lavinog said:**
> thegreger: what video card do you have?

It's a Nvidia 6150go. I've got driver version 180. Not the fastest card in the world, I suppose. But still, I think it's supposed to slow the computer down and let it cool rather than getting overheated.

I've actually tried putting ice packs below the computer! With an extra centimetre of air between to increase the airflow. It gives me an extra minute or two of gaming before the computer shuts down, but that's all. 

I'm not much of a gamer, so it's not a huge issue. But it would be interesting to hear if anyone else has got similar problems. It's really weird that the computer doesn't slow down at all until it reaches its critical temperature. The fans are kicking in after a while, but that isn't enough.

---

### Post by lavinog on 2009-05-13
what does
```
glxinfo|head
```
produce?

---

### Post by thegreger on 2009-05-13
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float

---

### Post by lavinog on 2009-05-13
It looks like a problem with your video driver. I have found many posts about nvidia cards overheating lately when using the proprietary driver. (try doing a forum search for nvidia overheating)
Do you know the full version number? There is a 180.51 which is the latest and 180.44 that came with jaunty. I would see if installing the latest driver would fix the issue.
This also seems to be affecting other distros too.

---

### Post by thegreger on 2009-05-13
It's 180.44, I think.
How would I go about to update it? Probably a slightly daft question, but since I'm new to Ubuntu I'm a bit paranoid about messing with my drivers without asking for advice. Last time I did that, it took me one day before I had any sound again. :)
Learning... Slowly.

---

### Post by lavinog on 2009-05-13
I don't have any experience with nvidia drivers to be honest.
you can install envyng. It will automate the install, but I don't know what driver it will install just yet.

Also can you post the output of 
```
dmesg|grep MMCONFIG
``` (case matters)
if you get a line that says: PCI: Using MMCONFIG
you should try rebooting, at the grub menu press 'e' then go to the kernel line and press 'e' again, then go to the end of the line and add:
```
pci=nommconf
```
hit esc, then b to boot

---

### Post by thegreger on 2009-05-13
Well, envyng only suggests 180.44. But I'll look around for info about updating it manually.

My output was PCI: Using MMCONFIG, so I've just done what you said. I just realised that you could probably ask me to stand on one leg while doing it, and I wouldn't suspect anything :)
Now when I type dmesg|grep MMCONFIG I don't get any output at all. Should I try firing a game up and see if the temperature is a bit more stable?

---

### Post by 67GTA on 2009-05-13
You might check your DSDT file. I can help with errors. [http://ubuntuforums.org/showthread.php?p=7260244#post7260244](http://ubuntuforums.org/showthread.php?p=7260244#post7260244)

---

### Post by lavinog on 2009-05-13
> **thegreger said:**
> Well, envyng only suggests 180.44. But I'll look around for info about updating it manually.

My output was PCI: Using MMCONFIG, so I've just done what you said. I just realised that you could probably ask me to stand on one leg while doing it, and I wouldn't suspect anything :)
Now when I type dmesg|grep MMCONFIG I don't get any output at all. Should I try firing a game up and see if the temperature is a bit more stable?

I guess I should have referenced the site I got that from:
[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)

See if it makes a difference...just so you know, it will go back to normal on next reboot. if it does make a difference let me know and I can show you how to make it permanent between boots.

---

### Post by thegreger on 2009-05-13
> **67GTA said:**
> You might check your DSDT file. I can help with errors. [http://ubuntuforums.org/showthread.php?p=7260244#post7260244](http://ubuntuforums.org/showthread.php?p=7260244#post7260244)

Thanks. I've mailed you the output of sudo dmidecode. Should I try to follow your guide on [http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt) ?

---

### Post by thegreger on 2009-05-13
Lavinog:
I've played Mafia in Wine for a while now, and the temperature was stable at 93-94 C for quite a while. But after around 30 minutes, the computer shut down itself. My syslog says:

```
May 13 22:58:46 simon-TX2020 acpid: client 4781[0:0] has disconnected 
May 13 22:58:46 simon-TX2020 acpid: client 4781[0:0] has disconnected 
May 13 22:58:46 simon-TX2020 kernel: [ 5115.649583] ACPI: Critical trip point
May 13 22:58:46 simon-TX2020 kernel: [ 5115.649593] Critical temperature reached (95 C), shutting down.
May 13 22:58:46 simon-TX2020 kernel: [ 5116.151466] ACPI: Critical trip point
May 13 22:58:46 simon-TX2020 kernel: [ 5116.151480] Critical temperature reached (95 C), shutting down.
May 13 22:58:47 simon-TX2020 kernel: [ 5116.652789] ACPI: Critical trip point
May 13 22:58:47 simon-TX2020 kernel: [ 5116.652803] Critical temperature reached (95 C), shutting down.
May 13 22:58:47 simon-TX2020 kernel: [ 5117.153153] Critical temperature reached (88 C), shutting down.
```

So it's possible that your method delayed the overheating, or perhaps I just had fewer processes running in the background than usual. But I should probably try to find some info about updating the driver, and see what 67GTA thinks about my DSDT file. (Also, I've just developed an addiction to Slingshot, which doesn't demand much performance)
Thanks for all your help!

---

### Post by heatpumpcontrol on 2009-05-13
Please see this [[COLOR="Red"]_link_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7273772&postcount=17"). 

I found that it has to do with Vino. My laptop was getting really hot as well and after some t/shooting I came to find that by killing vinoserver, my CPU would drop all the way down to about 3-5%. 

I first created another account on my l/top after an upgrade from ibex, and when I logged into that account I noted the lower CPU which led me to a personal config issue.

Went back to my account and ........ to make it short, it was vino. Go ahead, just try it. Turn it on and off. If it changes your CPU usage, then you'll know.


Good luck):P

---

### Post by lavinog on 2009-05-13
I don't think vino is active by default
top should show you processes that are using alot of cpu cycles
This command will give you the top 10 processes:
```
 ps -eo %cpu,pid,user,args --sort %cpu|tail
```

---

### Post by Ymerej on 2009-05-23
Having the same problem with Jaunty on a Dell Latitude D520.

The fan is coping and have only once reached shutdown temperature, but battery life is way down, I cannot use it on my lap (problem both when running on battery and on a/c) and I can't imagine the temperatures are doing much good for the machine. The heat is coming either from the memory module or the WLAN card. 

Top does not report any processes using significant amounts of cpu or memory. 

From the internet it seems to me like a LOT of people are having this problem, but nothing much is being done to resolve it. Please help if you can!

---

### Post by lavinog on 2009-05-23
I have noticed that while upgrading from intrepid to jaunty powernowd gets removed.
Could this have something to do with it.

---

### Post by 67GTA on 2009-05-23
The powernowd package is better for controlling AMD/Intel dual procs or other cpu's that have more than two step speeds. It might help to reinstall this if you fall in this category. The cpu speed is controlled by the kernel now. Powernowd will definitely help with heat from the procs.

---

### Post by lavinog on 2009-05-24
Well that sounds like the culprit then. I try installing it and see.
My laptop doesn't generate alot of heat though. Could someone affected by this issue install powernowd and see if it helps.

Do you think this applies to desktops too?

---

### Post by Sewje on 2009-05-26
No difference on my laptop. 40C idle

Jaunty does idle hotter on my laptop than Vista by 10C on the CPU.

I notice the temp is also higher on my desktop but during flash in firefox, the desktop doesn't budge where as on the laptop it can shoot up to 50+C
Guess it's an area to look into for future releases.

---

### Post by Payteer on 2009-05-26
I had the same problem last year after Hardy upgrade with heat after about two to three months in one of the updates the temperature went down again, now with Jaunty it id doing it again with the heat issue on my laptop.  Also since Jaunty from hardy, my laptop battery has lost 25 mins.

---

### Post by bobnutfield on 2009-05-27
In case someone does read this thread who can actually address this issue, I want to add that I am experiencing the same problem with Jaunty on my laptop.  Just upgraded this week and I am seeing about 10-15 degrees more heat than with Intrepid.  Core temps reach and stay at 55C.  I triple boot this laptop with Fedora and Slackware, and neither Fedora or Slackware creates this kind of heat, so it is definitely a Jaunty issue.

I don't want to damage my laptop, so for the time being I will use another distro on it and just check back in every now and then for updates.  Hopefully it will be corrected soon.

---

### Post by mike.thorton on 2009-05-28
I can confirm overheating (however don't know how to measure the temeratures)...

My laptop is HP 6510b with dualcore Intel Core 2 duo (still clocked to 800 MHz), 4 GB RAM, intel GPU, intel wifi (swithed off)...

I have Jaunty amd64 version installed.

---

### Post by lavinog on 2009-05-28
> **mike.thorton said:**
> I can confirm overheating (however don't know how to measure the temeratures)...

My laptop is HP 6510b with dualcore Intel Core 2 duo (still clocked to 800 MHz), 4 GB RAM, intel GPU, intel wifi (swithed off)...

I have Jaunty amd64 version installed.

install lm-sensors, then use sensors


i ran sensors on a script every minute and did various things.
at idle is stays about 50C
the fan doesn't kick on until about 55C
and speeds up at 70C
I don't have my laptop with me right now, but I think I found that the critical temp is 95C...I couldn't get my temps above 75C though (this is a single core turion 64 laptop)

---

### Post by bgreenaway on 2009-05-28
Experiencing same critical temperature issue at 85 degrees with Jaunty on my IBM ThinkPad G41 with Intel P4 3.2 GHz. Never experienced this issue at all with Intrepid.

---

### Post by ybytyruzu on 2009-05-28
I'm upgrade to Jaunty and note the same, laptop cooler more active and battery life very short and today I try this: add to panel Cpu Frecuency Scaling Monitor and there is by default Perfomance on my laptop, so I change to On demand and now the cooler is working normaly and battery duration is much much better...
With Hardy laptop battery mode was 1 hour (my battery is old!) but with Jaunty only 20 minutes or 30. Now I tested and obtained 1 hour again.

---

### Post by scb on 2009-05-30
Hello,

There is a bug about this topic here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)

Please, consider reporting your bug to see if we can catch some developer attention before our laptops catch fire.

Greetings.

---

### Post by breusshe on 2009-06-01
[FONT="Times New Roman"]You know, my laptop is getting very hot also.  In fact, it is so hot I can't even touch the area below the keyboard (where I normally rest my wrists as I type).  Everywhere I look, it's the same thing, "clean it out... clean it out."  So, before I bothered to post anything up here, I decided I better waste the time opening it up and clean it out.

After wasting about an hour of careful disassembly, all I have to show for it is a coat of cat hair and dirt that was thick enough to use as a blanket.:shock:  :oops:

CPU is running about 15°C cooler now and it isn't burning my hands to touch it.#-o:-\"

Thanks for stating the obvious, guys.=D>

Brett
[/FONT]

---

### Post by abhiroopb on 2009-06-02
I've been having the same problem.

HD temp starts out at about 30C, moves to about 38C and then goes up a few degrees every few minutes, until it hits 60C and the laptop dies.

It has gotten particularly hot where I live and this has added to the problem.

I assume that the laptop was getting hotter before, but since it wasn't dying I hadn't really noticed it (I used an external keyboard).

A solution would be really useful!

---

### Post by e13 on 2009-06-04
[https://bugs.launchpad.net/ubuntu/+bug/361123](https://bugs.launchpad.net/ubuntu/+bug/361123)

---

### Post by sam0vi on 2009-06-04
My laptop (LG e500) also gets quite hotter since i installed intrepid than running XP (which is very anoying for me), but in my case i think it's mostly due to the GPU, because it happens most commonly playing videogames or watching fulscreen flash videos. I'm upgrading to jaunty to see if there's any improvement. I'll let you know...

---

### Post by abhiroopb on 2009-06-04
The fix suggested at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173/comments/22) seems interesting.

Basically it suggests leaving the fan on forever or something along those lines. Any side effects to that?

---

### Post by abhiroopb on 2009-06-05
I have collated all the various posts regarding this overheating issue into one ubuntuforums post...please help advise there...

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

---

### Post by llamabr on 2009-06-08
Bump.  Any solutions yet?  I'm still having to turn this off periodically just to let it cool down.

---

### Post by doas777 on 2009-06-08
> **thegreger said:**
> Lavinog:
I've played Mafia in Wine for a while now, and the temperature was stable at 93-94 C for quite a while. But after around 30 minutes, the computer shut down itself. My syslog says:

```
May 13 22:58:46 simon-TX2020 acpid: client 4781[0:0] has disconnected 
May 13 22:58:46 simon-TX2020 acpid: client 4781[0:0] has disconnected 
May 13 22:58:46 simon-TX2020 kernel: [ 5115.649583] ACPI: Critical trip point
May 13 22:58:46 simon-TX2020 kernel: [ 5115.649593] Critical temperature reached (95 C), shutting down.
May 13 22:58:46 simon-TX2020 kernel: [ 5116.151466] ACPI: Critical trip point
May 13 22:58:46 simon-TX2020 kernel: [ 5116.151480] Critical temperature reached (95 C), shutting down.
May 13 22:58:47 simon-TX2020 kernel: [ 5116.652789] ACPI: Critical trip point
May 13 22:58:47 simon-TX2020 kernel: [ 5116.652803] Critical temperature reached (95 C), shutting down.
May 13 22:58:47 simon-TX2020 kernel: [ 5117.153153] Critical temperature reached (88 C), shutting down.
```So it's possible that your method delayed the overheating, or perhaps I just had fewer processes running in the background than usual. But I should probably try to find some info about updating the driver, and see what 67GTA thinks about my DSDT file. (Also, I've just developed an addiction to Slingshot, which doesn't demand much performance)
Thanks for all your help!

90 is already well into the red. something is seriously wrong there.

---

### Post by llamabr on 2009-06-09
This is a 7 page thread.  That means that either lots of people are having this problem, or that it ought to have been solved by now.

Can someone recommend a temporary fix, while the real problem is being worked out?

---

### Post by doas777 on 2009-06-09
> **llamabr said:**
> This is a 7 page thread.  That means that either lots of people are having this problem, or that it ought to have been solved by now.

Can someone recommend a temporary fix, while the real problem is being worked out?

I have not noticed any temp increase under jaunty specifically. Laptops ALWAYS run too hot in my world, regardless of OS. it's the fatal flaw of compact design. couple that with a clamshell that you can't open without voiding your warentee, and you are gaurenteed thermal problems.

---

### Post by abhiroopb on 2009-06-09
> **doas777 said:**
> I have not noticed any temp increase under jaunty specifically. Laptops ALWAYS run too hot in my world, regardless of OS. it's the fatal flaw of compact design. couple that with a clamshell that you can't open without voiding your warentee, and you are gaurenteed thermal problems.

Let me put it this way...

In Intrepid and all the Ubuntu versions before, I could comfortably keep my laptop on my bed with the base touching the sheets, and although it may get hot it never got hot enough to completely turn off.

Now I can't even do that for 5 minutes without the computer turning off.

---

### Post by mrbiggbrain on 2009-06-09
i have the same issue, my laptop overheats sometimes under 9.04, but didnt ever under ubuntu 8.10, does not under windows vista, and does not under the fedora live cd, puppy live cd, or slax live cd.

it gets so hot sometimes, it shuts itself down automaticly.

---

### Post by llamabr on 2009-06-09
> **abhiroopb said:**
> Let me put it this way...

In Intrepid and all the Ubuntu versions before, I could comfortably keep my laptop on my bed with the base touching the sheets, and although it may get hot it never got hot enough to completely turn off.

Now I can't even do that for 5 minutes without the computer turning off.

Yes, and this is my point.  Many people are insisting that it's simply a matter of cleaning the fan.  It worked fine, then I upgraded, and it gets very hot.

So short of someone discovering the solution and solving this, is there a temporary fix?  What can I do to cool this down?

---

### Post by e13 on 2009-06-11
[https://bugs.launchpad.net/ubuntu/+bug/361123](https://bugs.launchpad.net/ubuntu/+bug/361123)

main details for reading-challenged ones:

* starting from jaunty cpufreq-applet adjusts processor cores separately, setting one core to ondemand mode will not change the mode other core runs.
* because it seems to be impossible to find out who the **** messed in this departement, one can therefor only wonder, could it be that something went wrong with thresholds, that used to deceide when processors speed should be stepped up or down, separating cores for that kind of adjustment requires tweaking those thresholds also. which nobody seems to be able to do, for two months now...

/me copes with this just by putting two cpu-freq applets to my wateva-system-bar-that-was and limiting both cores to 70% of top speed. Even setting both of them ondemand is not enough to restore original behavior/temperature/responsiveness this same machine used to have just few months ago @ 8.10

---

### Post by emeraldgirl08 on 2009-06-11
What are peoples temps running here? My laptop feels warm so what is the best app to monitor temps for the HD and the CPU?

---

### Post by hessiess on 2009-06-11
> **llamabr said:**
> Yes, and this is my point.  Many people are insisting that it's simply a matter of cleaning the fan.  It worked fine, then I upgraded, and it gets very hot.

So short of someone discovering the solution and solving this, is there a temporary fix?  What can I do to cool this down?

If it worked well on Intrepid without overheating... downgrade to Intrepid ;)

---

### Post by doas777 on 2009-06-11
Standard Temps (Warning, your milage may vary; all temps in degrees Celsius):
CPU:
20 - 45  => Cool
45 - 60 => Warm
60 - 75 => Hot for CPUs prior to 2006, warm for Core2's and AMD dual cores
75 - 90 => Hot. Deadly for older CPUs. damaging for all CPUs if its there for long
90 - 100 => Really hot. shutdown RIGHT NOW.
100+ => replace your PC.

some newer CPUs are rated for temps in excess of 100C but I don't feel like testing the limits. My Core2 is rated for up to 100, but even after running at 100% for 72 hours, it stays below 70. going with a 65-watt chip was a good idea.

also be careful about hdd temps. hard disks cannot tolerate the same heat levels a cpu can, and should normally be kept below 50C. any smart enable hdd can tell you it's upper temp threshold. they vary widely from drive to drive, but 54 has been the highest I've seen to date.

---

### Post by doas777 on 2009-06-11
> **emeraldgirl08 said:**
> What are peoples temps running here? My laptop feels warm so what is the best app to monitor temps for the HD and the CPU?

I use lm-sensors and sensors-appplet (a gnome panel applet that shows lm sensors info).
check out this guide:
[http://blog.networkfoo.org/?p=53](http://blog.networkfoo.org/?p=53)

and don't bother to run script posted on this page. it has not been needed since fiesty.

good luck

---

### Post by llamabr on 2009-06-11
> **hessiess said:**
> If it worked well on Intrepid without overheating... downgrade to Intrepid ;)

Thanks.  I would have done just that on the first day, except I upgraded to solve an incompatibility issue with my internal wireless card.

For everyone else, this is the solution I'd recommend, too.

---

### Post by llamabr on 2009-06-11
> **doas777 said:**
> Standard Temps (Warning, your milage may vary; all temps in degrees Celsius):
CPU:
20 - 45  => Cool
45 - 60 => Warm
60 - 75 => Hot for CPUs prior to 2006, warm for Core2's and AMD dual cores
75 - 90 => Hot. Deadly for older CPUs. damaging for all CPUs if its there for long
90 - 100 => Really hot. shutdown RIGHT NOW.
100+ => replace your PC.

some newer CPUs are rated for temps in excess of 100C but I don't feel like testing the limits. My Core2 is rated for up to 100, but even after running at 100% for 72 hours, it stays below 70. going with a 65-watt chip was a good idea.

also be careful about hdd temps. hard disks cannot tolerate the same heat levels a cpu can, and should normally be kept below 50C. any smart enable hdd can tell you it's upper temp threshold. they vary widely from drive to drive, but 54 has been the highest I've seen to date.

Many others here are reporting that the heat is coming from the memory, not the cpu.  I guess I should take out a screwdriver and find out if that's true for me, too.

---

### Post by llamabr on 2009-06-11
Someone else who has collected similar complaints:

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

---

### Post by abhiroopb on 2009-06-11
> **llamabr said:**
> Someone else who has collected similar complaints:

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

Thanks for bringing up the post.

Unfortunately it seems like everyone has their own opinion about this problem.

I'm really considering downgrading if it isn't solved soon.

My temps are usually at:

HD: 54C
CPU: between 55C and 78C

So, these are clearly above average.

In addition I keep my CPU raised a few inches above the table.

---

### Post by lavinog on 2009-06-12
> **e13 said:**
> [https://bugs.launchpad.net/ubuntu/+bug/361123](https://bugs.launchpad.net/ubuntu/+bug/361123)

main details for reading-challenged ones:

* starting from jaunty cpufreq-applet adjusts processor cores separately, setting one core to ondemand mode will not change the mode other core runs.
* because it seems to be impossible to find out who the **** messed in this departement, one can therefor only wonder, could it be that something went wrong with thresholds, that used to deceide when processors speed should be stepped up or down, separating cores for that kind of adjustment requires tweaking those thresholds also. which nobody seems to be able to do, for two months now...

/me copes with this just by putting two cpu-freq applets to my wateva-system-bar-that-was and limiting both cores to 70% of top speed. Even setting both of them ondemand is not enough to restore original behavior/temperature/responsiveness this same machine used to have just few months ago @ 8.10

This doesn't explain why single core processors are over heating though.


[quote=llamabr]Many others here are reporting that the heat is coming from the memory, not the cpu. I guess I should take out a screwdriver and find out if that's true for me, too.[/quote]
The cpu temp isn't affected by the memory on my laptop. The memory isn't even attached to the heatsink.

---

### Post by e13 on 2009-06-12
> **lavinog said:**
> This doesn't explain why single core processors are over heating though.

well... it kinda could. if something was changed about those thresholds, same applies to watever processor. and as it happens, this looks to be the case - machine with jaunty and processor set to work with ondemand governor and running all the same applications in the very same way gets so mych hotter and jumps up the speed occur much often... compared to intrepid with same settings and same programs running.


thing, that is beyond me, is how the hell is it impossible for launchpad people to track down, who changed things in this area and just ask this guy... should be obvious place to start looking, given that settings for multiple cores are suddenly independent and those speed-jumps obiviously do happen earlier and last longer...

---

### Post by merlin666 on 2009-06-13
> **hessiess said:**
> If it worked well on Intrepid without overheating... downgrade to Intrepid ;)

Good one - except Ubuntu has no path for downgrading, you can only go up. Alternative is to uninstall everything and get a fresh installation of older version.

This may be the only option for me as Jaunty runs for only a few minutes on my Emachines M6811 (Mobile Athlon 3400), and then crashes. I assume that this is due to overheating. In XP the core temp. is around 63C and 75C under load (e.g. converting.burning DVD, but I don't know how to measure this in Jaunty. May not have enough time to setup a temp. monitor as it crashes quite quickly.

---

### Post by atom_box on 2009-06-16
> **67GTA said:**
> The powernowd package is better for controlling AMD/Intel dual procs or other cpu's that have more than two step speeds. It might help to reinstall this if you fall in this category. The cpu speed is controlled by the kernel now. Powernowd will definitely help with heat from the procs.

My Asus Eee900 Netbook with Jaunty was running super hot.  Per your suggestion I installed powernowd via the synaptic package manager and now things seem okay.  I installed lm-sensors and the cpu temperature stays right around 50 C.   The fan is noisy but that is an Asus issue!   Also, on my setup, the recommended emifreq-applet wouldn't install correctly.  Might be my system not doing java right, a friend suggested.   

 Thanks for this excellent thread, everyone -- for a beginner it was SUPER useful.

---

### Post by neomanaidin on 2010-06-03
Hi guys, 
I am having a similar problem here. I am using a dell XPS m1530 and untill last month I was using windows vista. I decided to use ubuntu 10.04 after its release and I totally removed vista and installed 10.04. It was the only OS in my computer. It worked great and I decided to use like forever. But I needed windows for a project and I had to partitiion my HDD and install windows there and I installed windows 7 and I also installed ubuntu 10.04 with dual-boot. However now my hdd is burning I can't touch the left side of the touchpad. In windows &#305;t does not heat like this. It is quite normal as it was before. And it was not getting hot like this with ubuntu as the only OS in the computer. Does it have anything to do with allocating the HDD? Or are there anything you can help me out? My cooling fans are perfectly clean since I replaced them recently.

---

### Post by lavinog on 2010-06-04
@neomanaidin
Try installing laptop-mode-tools
It should enable some of the power saving features of your laptop.

---

