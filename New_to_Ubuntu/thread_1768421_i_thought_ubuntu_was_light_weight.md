---
title: "i thought ubuntu was light weight?"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by picorex on 2011-05-26
hi all,

a long time curiousity prompted me to install ubuntu 10.10 desktop on my asus 1015pem. the install went without a hitch, wifi and audio drivers installed automatically so it was ready to go straight away, which was nice.

but the thing that has surprised me is that it really isn't very fast. granted, it boots quicker than win7 ultimate did but after that it really lags. it's by no means unusable but i find myself closing applications constantly, just to try and get a bit more speed out of it... something that was never a problem under win7.

am i doing something wrong or is this just the way it is? perhaps i should try another distribution better orientated towards netbooks? i did look at the ubuntu netbook edition but i want a full desktop evironment so decided against it. is mint linux worth a try?

also, the constant asking for passwords is infuriating... i've followed a few instructions to disable both keyring and the admin password requirement but nothing i've tried has done the trick. anything i can do here?

thanks for reading.

---

### Post by wolfen69 on 2011-05-26
> **picorex said:**
> 

am i doing something wrong or is this just the way it is?

No, you're probably not doing anything wrong, and no, that's not just the way it is. Ubuntu has always been pretty fast for me. Give us your pc specs and we can go from there.

---

### Post by picorex on 2011-05-26
> **wolfen69 said:**
> No, you're probably not doing anything wrong, and no, that's not just the way it is. Ubuntu has always been pretty fast for me. Give us your pc specs and we can go from there.

it's an asus 1015pem. it's a crappy netbook with a dual core 1.5ghz atom n550 and 1GB of RAM. if i had nothing to compare, i'd accept that the netbook is the bottle neck, but when win7 runs so substantially quicker than ubuntu does it makes me wonder where the problem lies.

cheers for the fast reply.

---

### Post by jramshu on 2011-05-26
Do you have hyperthreading enabled in bios?

---

### Post by galacticaboy on 2011-05-26
If you want lightweight, try Xubuntu or Lubuntu. Ubuntu is not really lightweight but usually runs fast.

---

### Post by Allavona on 2011-05-26
The Atom processor was specifically designed for small netbooks. Most of these netbooks run Win7 Starter Edition. Win7 Starter is the lightweight version of 7.


Agree w/ galacticaboy, go lightweight. Xubuntu, Lubuntu, or one of the many lightweight distros out there.

---

### Post by nemilar on 2011-05-26
As stated above, Ubuntu Desktop isn't really lightweight.  It's a bit much for your atom-based netbook (I have something similar).  Netbook edition might run better, but in my experience (I have an HP Mini), Xubuntu was best.  You may want to give Ubuntu Netbook a try though, and see how you like it.  There's no harm in checking out the different options, if you've got a few hours to dedicate to experimentation.

You're probably using Windows 7 Starter.  Comparing Windows 7 Starter to Ubuntu Desktop isn't really fair; Windows 7 Professional would be a better comparison.

Good luck!

---

### Post by lightstream on 2011-05-26
throw another 1 Gig (if not 2) of RAM in there, should make it run silky smooth.

---

### Post by dFlyer on 2011-05-26
> **picorex said:**
> it's an asus 1015pem. it's a crappy netbook with a dual core 1.5ghz atom n550 and 1GB of RAM. if i had nothing to compare, i'd accept that the netbook is the bottle neck, but when win7 runs so substantially quicker than ubuntu does it makes me wonder where the problem lies.

cheers for the fast reply.

You might try adding an extra gig or two of ram.

---

### Post by LowSky on 2011-05-27
Ubuntu isn't as light weight as it used to be. 11.04 is the worst offender but the editions before have some things that can slow things down.

Try turning off desktop effects (right click on a empty desktop, choose change desktop then, go to the effects tab, click on none).

Other things you can do is go to System > Preferences > and turn off thing you may bot be using, like Evolution. Use lighter apps, For webbrowsing google chrome or Chromium are lighter and are usually faster than Firefox. Abiword is lighter than open/libre office.

If you dont mind not using Gnome. XFCE or LXDE are lighter desktop environments (DE). Both can be easily added to an existing install. Then choose the DE from the login screen.

---

### Post by picorex on 2011-05-27
> **jramshu said:**
> Do you have hyperthreading enabled in bios?

yup

> **nemilar said:**
> 
You're probably using Windows 7 Starter.  Comparing Windows 7 Starter to Ubuntu Desktop isn't really fair; Windows 7 Professional would be a better comparison.

Good luck!

it was definitely running ultimte, i installed it myself. it came with starter edition but i didn't like it.

> **lightstream said:**
> throw another 1 Gig (if not 2) of RAM in there, should make it run silky smooth.

i could, but you're missing the point that win7 ultimate ran just fine on 1GB of RAM. i'm just surprised that ubuntu runs worse, and wondered what i'm doing wrong for it to be like this.

> **LowSky said:**
> Ubuntu isn't as light weight as it used to be. 11.04 is the worst offender but the editions before have some things that can slow things down.

Try turning off desktop effects (right click on a empty desktop, choose change desktop then, go to the effects tab, click on none).

Other things you can do is go to System > Preferences > and turn off thing you may bot be using, like Evolution. Use lighter apps, For webbrowsing google chrome or Chromium are lighter and are usually faster than Firefox. Abiword is lighter than open/libre office.

If you dont mind not using Gnome. XFCE or LXDE are lighter desktop environments (DE). Both can be easily added to an existing install. Then choose the DE from the login screen.

thanks, i did already try to use the most light weight apps i could find... ie chromium and transmission etc. maybe i'll try lubuntu or xubuntu next then... and if all else fails i'll switch back to win7.

---

### Post by potat on 2011-05-27
If you're not too concerned about other people breaking into your account, try just making your password shorter. Make it something quick to type (for example, something you can type using only the "home row" (asdfghjkl;').
Hope this helps.

---

### Post by picorex on 2011-05-27
so is there no way to disable the password requirement at all? does that stand in all varieties of linux?

---

### Post by LowSky on 2011-05-27
> **picorex said:**
> so is there no way to disable the password requirement at all? does that stand in all varieties of linux?

We can't say yes to that.

In other distros that use a root use, the only time a password is required is for logging in.

Ubuntu doesn't use root but instead uses Sudo. Sudo give a normal user root ability for short sessions.

How often do you really need a password really? I enter mine only when logging in,  and when I do an update or install new software. Beyond that its very rare. Yes the keyring is annoying, and you can set it to require no password.

But Linux in general uses a password. Even if you don't type anything, a blank password is still a password.

I too was frustrated at first on the amount of passwords typing I need at first but think of it this way: The chance that something bad gets installed onto your PC is reduce to nearly zero with password protection. The reason Windows has so many viruses and malware was the result of open access for an app to self install.

To be fair Ubuntu password is less annoying than Windows Vista's and 7's "are you sure" every time an application starts up or installs.

---

### Post by el_koraco on 2011-05-27
> **picorex said:**
> so is there no way to disable the password requirement at all? does that stand in all varieties of linux?

There is, it's just not recommended. Google Root/Sudo. You can disable thhe keyrig password by not setting the autologin feature, or by going to "Passwords and Encryption Keys", clicking on the "default" and possibly "login" tab, choosing edit, entering the password and leaving the next two boxes blank.

---

### Post by picorex on 2011-05-27
well perhaps because it's a new install i'm still tinkering around with it, so the password is being asked of me more than it would in a couple of months time. the thing is, on my windows machines i set UAC to 'never notify' and i've never had an issue with rogue software or malware. and that's with over 12 years of 24/7 uptime (bar upgrades) on at least 3 machines simultaneously. it feels as though i'm being treated like a child with the constant password requirements in linux.

additionally i'm having problems when i leave the netbook alone or close the lid. i've set it to never sleep and never spin down disks even when the lid is closed, whether running on mains or battery. but still, when i re-open the lid the pc is locked (requiring the damn password again) and the wifi has shut off.

looks like linux might not be for me, which i am disappointed about because i was looking forward to learning a new OS. these niggles are small, but they add up. coupled with the lag compared to win7 i can see myself swapping back unless i can get it sorted.

thanks for all your replies.

edit: thanks el_koraco, i'll try that.

---

### Post by 3rdalbum on 2011-05-27
The password is being asked more of you because you're tinkering. The security system in Linux exists not only for your security, but also for the security of others on the Internet and on your local network. In fact, disabling or working around the security system might stop certain programs from working properly.

You really should get used to the password prompts. Disabling the security systems on any operating system is pretty terrible practice.

As for your speed problem, although Ubuntu isn't exactly "lightweight" it shouldn't "lag", even on a netbook. What's your CPU use like? If there's one core that seems to stay near 100% then it might be a runaway process that's causing high CPU use; killing that program would give you your speed back.

---

### Post by KoolDesign2 on 2011-05-27
Thats great

---

### Post by lightstream on 2011-05-27
> **picorex said:**
> ... and if all else fails i'll switch back to win7.

If you've splashed out all that money to buy a copy of Win7 Ultimate, then why not use it.

I'm sure of course you wouldn't be using an illegal pirate copy (even though MS would prefer you to do that than use Linux!)

---

### Post by Paqman on 2011-05-27
On a netbook you'll really want to switch to Unity-2D instead of the standard version. Open up Software Centre and install the package unity-2d, then log and select Unity 2D from the session menu at the bottom of the screen when you log back in. I use the standard desktop in 2D mode it on my netbook and performance is good. An alternative desktop like XFCE or LXDE is an option, but LXDE in particular isn't as polished an environment as Gnome is.

---

### Post by baljinder105 on 2011-05-27
Ya... me too have the same problem.... . I think win7 uses heavy graphics than Ubuntu ?? but...win7 boots 2-3 times faster than Ubuntu on my same machine..

---

### Post by Paqman on 2011-05-28
> **baljinder105 said:**
> Ya... me too have the same problem.... . I think win7 uses heavy graphics than Ubuntu ?? but...win7 boots 2-3 times faster than Ubuntu on my same machine..

Boot times aren't really related to how graphics-heavy the desktop is. It's mainly about how fast your hard drive is, and how efficiently the system carries out booting tasks. Older versions of Windows cheated a bit by throwing the desktop up before the system had finished booting. It *looked* like it was ready, but trying to do anything with it proved otherwise. I'm not sure if recent versions of Windows still do this, though.

---

### Post by 3rdalbum on 2011-05-28
> **baljinder105 said:**
> Ya... me too have the same problem.... . I think win7 uses heavy graphics than Ubuntu ?? but...win7 boots 2-3 times faster than Ubuntu on my same machine..

Ubuntu 11.04 appears to have totally regressed in terms of startup time. Pretty shocking when you consider that it was a priority for 9.10 and 10.04.

---

### Post by bodhi.zazen on 2011-05-28
"Light weight" and speed / performance are related, but somewhat separate.

What do you mean by "light weight" ? Amount of RAM used ? Size of the OS when installed on the hard drive ?

If Ubuntu is too heavy for you try xubuntu or lubuntu. You can also do a minimal install and build up.

Light weight also means extends to applications. gedit is light weight, open office is not.

Performance is also somewhat relative. In my experience I find the atom processors are somewhat under powered.

Performance is also influenced by drivers, and both your video driver and wireless driver can affect performance.

HTH

---

### Post by PhilGil on 2011-05-28
> **bodhi.zazen said:**
> Performance is also influenced by drivers, and both your video driver and wireless driver can affect performance.

HTH
This.

I don't run 11.04, but I'm assuming desktop effects are turned on by default. That could very well be your problem. The Linux graphics stack isn't as efficient as Windows on most machines. Turn off desktop effects, use Unity 2D or the classic desktop and you'll probably have a much better experience.

I you really want to learn Linux, I wouldn't give up just because Ubuntu runs slowly. Ubuntu is kind of a "kitchen sink" distro with heavy applications and lots of services turned on by default.

As others have suggested, you also might want to try something lighter. Lubuntu would probably scream on your machine, although functionality is a bit limited compared to Ubuntu. I run Debian Squeeze on my single-core ASUS netbook and it works very well. I still have all the functionality of a Gnome desktop but without the extra weight of Ubuntu.

---

### Post by snowpine on 2011-05-28
Ubuntu 11.04 flies on my crappy netbook (dell mini 9 with 1.6ghz atom processor, integrated intel 945 graphics, 8gb ssd, 1gb ram). Sounds like you're having some kind of driver issue that's slowing things down... I recommend using the forum Search feature to find other users with the same hardware, see if there are any existing discussion threads with suggestions.

---

### Post by Swagman on 2011-05-28
You can set the O/s to auto login at boot if you wish.. Also the Keyring can be adjusted to not ask for password.


In Fact... It's Linux.. **EVERYTHING** can be adjusted

---

### Post by ivanovnegro on 2011-05-28
> **picorex said:**
> well perhaps because it's a new install i'm still tinkering around with it, so the password is being asked of me more than it would in a couple of months time. the thing is, on my windows machines i set UAC to 'never notify' and i've never had an issue with rogue software or malware. and that's with over 12 years of 24/7 uptime (bar upgrades) on at least 3 machines simultaneously. it feels as though i'm being treated like a child with the constant password requirements in linux.

additionally i'm having problems when i leave the netbook alone or close the lid. i've set it to never sleep and never spin down disks even when the lid is closed, whether running on mains or battery. but still, when i re-open the lid the pc is locked (requiring the damn password again) and the wifi has shut off.

looks like linux might not be for me, which i am disappointed about because i was looking forward to learning a new OS. these niggles are small, but they add up. coupled with the lag compared to win7 i can see myself swapping back unless i can get it sorted.

thanks for all your replies.

edit: thanks el_koraco, i'll try that.

Linux is a real multiple user system, thats also one of the reasons you have to type the passwords.

> **3rdalbum said:**
> Ubuntu 11.04 appears to have totally regressed in terms of startup time. Pretty shocking when you consider that it was a priority for 9.10 and 10.04.

Unfortunateley that is right and this happens on all spins of 11.04 but the boot time is not that important, you boot once and thats all. Still the shut down time is great, under 5 seconds.

> **snowpine said:**
> Ubuntu 10.04 flies on my crappy netbook (dell mini 9 with 1.6ghz atom processor, integrated intel 945 graphics, 8gb ssd, 1gb ram). Sounds like you're having some kind of driver issue that's slowing things down... I recommend using the forum Search feature to find other users with the same hardware, see if there are any existing discussion threads with suggestions.

Then you are lucky but I dont thing it is a hardware issue in first place, 1 GB RAM is really not anymore so much to run Ubuntu 11.04 flawlessly. It will run but it will be slower as with more RAM. Maybe some people dont notice that their machine is not flying even if it is working good enough. In my experience, open Firefox, LibreOffice, Banshee and a heavy Java app, you will need something about 1.3 of RAM, then add Flash content in the browser and you will end up using 1.6 RAM of your machine, thats not lightweight of course but these apps also are not lightweight. But that is still good compared to Windows Vista. Just my experience and maybe of the OP.

I noticed always if something is not working on Ubuntu the people are blaming the hardware but its not always the hardware, its Ubuntu, accept this. ;)

To the OP, try to run Ubuntu 10.04, it is a stable version of Ubuntu and even has long term support not like the newer ones, or try Xubuntu or Lubuntu.

---

### Post by snowpine on 2011-05-28
> **ivanovnegro said:**
> Then you are lucky but I dont thing it is a hardware issue in first place, 1 GB RAM is really not anymore so much to run Ubuntu 11.04 flawlessly. It will run but it will be slower as with more RAM. Maybe some people dont notice that their machine is not flying even if it is working good enough. In my experience, open Firefox, LibreOffice, Banshee and a heavy Java app, you will need something about 1.3 of RAM, then add Flash content in the browser and you will end up using 1.6 RAM of your machine, thats not lightweight of course but these apps also are not lightweight. But that is still good compared to Windows Vista. Just my experience and maybe of the OP.

I noticed always if something is not working on Ubuntu the people are blaming the hardware but its not always the hardware, its Ubuntu, accept this. ;)

It's a netbook... I don't use it for serious multi-tasking or anything processor-intensive. Atom is comparable to Pentium 3 and should be used with that expectation in mind. I'm currently surfing the web, playing a couple of games, and running some commands from the terminal, I am using 53% of my 1gb ram.

Respectfully I've installed 20-30 different distros on my netbooks, 1gb ram is plenty for Ubuntu/Fedora/Debian/Slackware/etc... not saying more isn't better of course! :)

---

### Post by ivanovnegro on 2011-05-28
> **snowpine said:**
> It's a netbook... I don't use it for serious multi-tasking or anything processor-intensive. Atom is comparable to Pentium 3 and should be used with that expectation in mind. I'm currently surfing the web, playing a couple of games, and running some commands from the terminal, I am using 53% of my 1gb ram.

Respectfully I've installed 20-30 different distros on my netbooks, 1gb ram is plenty for Ubuntu/Fedora/Debian/Slackware/etc... not saying more isn't better of course! :)

For this purpose it will of course just run fine.

---

### Post by PhilGil on 2011-05-28
> **snowpine said:**
> ...8gb SSD...
SSD's are generally faster than HDD's. Your computer could perform considerably better than the OP's on this difference alone.

So, I tried out 11.04 on my netboox via USB. Speed oesn't seem that much different to me than 10.04, even with Compiz/Unity running. A bit sluggish, but it is a netbook. That may mean that the OP's performance standards are higher (nothing wrong with that) or that he/she does have a hardware compatibility issue.

---

### Post by snowpine on 2011-05-28
> **PhilGil said:**
> SSD's are generally faster than HDD's. Your computer could perform considerably better than the OP's on this difference alone.

Not this one. :)

---

### Post by cbowman57 on 2011-05-28
@picorex; when you bring up system monitor does it show that you're using the swap partition?

If so, something I always do is edit the sysctl.conf and adjust swappiness

sudo gedit /etc/sysctl.conf  add vm.swappiness=1 << that seems to keep more of Ubuntu in RAM but still allows it to swap when necessary, just waits longer before resorting to it.

Sorry, I made an error in my original reply, meant to say sysctl.conf, not rc.local

---

### Post by mardose on 2011-05-31
To be honest I'm not sure why your PC should be lagging. I own a Compaq with a Turion64 X2 1.6Ghz and have never needed  more than 1G of RAM for Ubuntu. Now if you have an Atom processor then in all actuality it uses HyperThreading technology and isn't a true dual core processor, but regardless your setup should chew through boot times and whatnot without much hassle. I would advise that you check for proprietary drivers that may need to be installed (you can do this by running from the command line "sudo jockey-gtk") as especially video drivers can dramatically impact system performance.

On another note though there are some things you can do to speed up your system. The first being that normally when Ubuntu boots, it loads up Bluetooth support as well as DSL  management and quite a few other things that your system may very well not even use. I would highly recommend that you look up an actual guide online (you could percievably mess up your install pretty bad with this tool) before attempting to use it but to install it simply type:

sudo apt-get update && sudo apt-get install sysv-rc-conf
(OR simply sudo apt-get install sysv-rc-conf)

To run the program call it's name from the command line (sysv-rc-conf)
Again, look up a guide online, it's much safer that way.

The second thing you can do (and this really does make a difference) is to install a daemon that prelinks shared user library files. For this one type:

sudo apt-get install prelink

And you will have to configure it a little before running the program... After the install completes, run the following command in the terminal:

sudo sed -i s/PRELINKING\=unknown/PRELINKING\=yes/g /etc/default/prelink

Then in order to run the program for the first time type:

sudo /etc/cron.daily/prelink

Depending on how much software you have installed it may take a while for the program to finish it's task. Just be patient, and after it's done the terminal will show the command line again. After that, reboot and your applications as well as boot times should experience an improvement. I hope this helps, God bless. :D

---

### Post by mardose on 2011-05-31
Let me correct myself. I just looked up the specs on your system and actually your processor should be a Dual Core with HyperThreading technology, which is actually not a bad processor at all despite it's low clock speed. I thought I'd mention though, keep in mind that it may be a hardware problem. If your PC gets too warm then there may be a problem with the power configuration drivers, or you may simply need to buy a can of compressed air and blow your CPU's HS out. I would say that in my experience the number one cause for poor system performance is... well... Windows... lol but the second most common cause is either an overheating CPU, or GPU (especially in laptops).

---

### Post by picorex on 2011-06-01
thanks for all the help guys but ultimately i just want a computer that runs quickly without too much faffing around. i did try kubuntu but wifi or audio didn't work out of the box (it did with ubuntu though) and it was just as sluggish as ubuntu. 
it might have been one of the many reasons listed above that was making linux slow, but unfortunately i don't have the time or inclination to get to the bottom of it.

i'm back on win7 and the difference in speed is very apparent, it absolutely flies compared to how ubuntu ran. thanks for the help though, maybe in future when i have a bit more time to tinker i'll try it out again and try to find out why it was so slow.

---

### Post by TenPlus1 on 2011-06-01
Do you use an ati or nvidia graphics card, if so have you gone into System -> Administration -> Additional Drivers to install the driver ?  This will speed a system up considerably...

I have a 2ghz amd single-core system that ran windows 7 and ubuntu 11.04 and no comparison, ubuntu always runs faster...

---

### Post by sbraz on 2011-06-01
> **mardose said:**
> To be honest I'm not sure why your PC should be lagging.
i agree. i have an aspire one 721: with 1.7G of ram (some is reserved for the graphic card) i can _use_ ubuntu with chromium and firefox, a 512MB ram virtual win7 ultimate 64bit, play a movie, copy files, folding@home, compile a kernel, all in 3 crammed workspaces with full desktop effects. i admit there was little ram left for caching, so i installed 4GB and now my system could withstand TWICE the workload...
...on a single core low power 1.7GHz cpu with a 5400rpm 8mb-cache drive (recently swapped with a WD3200BEKT for the sake of "my netbook is much better than yours!").


a friend of mine installed 10.04 on a more powerful laptop with 1G of ram and after a few months he asked for another gig: he plays zynga poker on facebook and AdobeFlashCrap is capable of leaking like 600MB of ram all alone so you know... :)




back on topic i have the feeling that the culprit is your ssd: kernel might think it's a classic hdd so it's causing an I/O request flood on the controller as it happened with the windows xp version (xp doesn't natively support ssd, partially with unsupported/dangerous 3rd part drivers) of the acer aspire one ZG5.

video drivers might interfere too.

does ubuntu 11.04 netbook edition work at least "fine" booting it in live (try ubuntu without installing) mode? an external hdd might offer a better comparison than a usb stick.

---

### Post by sbraz on 2011-06-01
also, try this on a terminal:

```
sudo su
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch
```

source + info + more tweaks && read comments:
[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

---

### Post by sbraz on 2011-06-01
> **cbowman57 said:**
> sudo gedit /etc/sysctl.conf  add vm.swappiness=1 << that seems to keep more of Ubuntu in RAM but still allows it to swap when necessary, just waits longer before resorting to it.

i partially disagree. :)

i read a lot about vm.swappiness parameter and honestly it's not an easy one as you might think.

i won't go indepth here or i'll never make it to the shower before 4AM, but after a lot of testing i've become one of those who are convinced that setting "vm.swappiness=1" (which practically disables swap entirely) is wrong.

try this: set swappiness to 1 and launch enough applications to fill out your ram ("stress" is an awesome program).
you will notice that as you approach 100% ram allocation your system will become so bogged down that you'll feel the urge to ctrl+alt+f1 ctrl+alt+canc ASAP.
well... now try the same with swappiness set to 100 and check your system's responsiveness.

by swapping out unneeded libraries programs and such, you free memory for applications _you are using now_ and more importantly there's a lot more file caching.

the underlying cause of what i (and many others) call "low responsiveness" or "perception of performance" is that there's not enough ram to run all the needed/required applications _altoghether_; setting swappiness=1 just makes it worse.

searching the net will return hundreds of more or less constructive discussions about this, all ending with the same quote:

*"basically, swappiness is deep personal choice"*

my personal preference settings on all boxes are
```
vm.swappiness=100
vm.vfs_cache_pressure=50
```

cheers :)

ps. sorry for triple posting, i go all new-reply-trigger-happy when i find an interesting topic. :D

---

### Post by bodhi.zazen on 2011-06-01
> **sbraz said:**
> i read a lot about vm.swappiness parameter and honestly it's not an easy one as you might think.

Nice post. The only information I would add is that it depends on how much RAM you have and your typical and maximal RAM usage.

If as a desktop user you have 3-4 Gb of RAM you are likely to find you do not use more then 1-2 Gb with many tasks. Multimedia (burning CD/DVD) and virtualization are less common applications that use a bit of your RAM, so it does vary buy usage. If you are not using all your RAM, the swappiness setting does not matter (as you pointed out in your post by suggesting one first test swapiness by maximizing ram use).

Also, the amount of ram used also varies by the amount of ram available. Boot the Ubuntu Live CD in Virtualbox with 512 Mb ram and compare the ram utilization to when you boot it with 1 Gb or more.

In general, if you are making heavy use of swap, your best option to boot performance is to install additional RAM.

Second would be to optimize the ram you have , swappiness being one option. Using light weight apps (gedit rather the open office) is a close #2.

---

### Post by krapp on 2011-06-02
> **picorex said:**
> it's an asus 1015pem. it's a crappy netbook with a dual core 1.5ghz atom n550 and 1GB of RAM.

Hardly crappy! I run a Debian net-install with GNOME 2 on the same netbook and it's fast! Nothing like on an i7 of course...

---

### Post by cbowman57 on 2011-06-02
> **sbraz said:**
> i partially disagree. :)

i read a lot about vm.swappiness parameter and honestly it's not an easy one as you might think.

i won't go indepth here or i'll never make it to the shower before 4AM, but after a lot of testing i've become one of those who are convinced that setting "vm.swappiness=1" (which practically disables swap entirely) is wrong.

try this: set swappiness to 1 and launch enough applications to fill out your ram ("stress" is an awesome program).
you will notice that as you approach 100% ram allocation your system will become so bogged down that you'll feel the urge to ctrl+alt+f1 ctrl+alt+canc ASAP.
well... now try the same with swappiness set to 100 and check your system's responsiveness.

by swapping out unneeded libraries programs and such, you free memory for applications _you are using now_ and more importantly there's a lot more file caching.

the underlying cause of what i (and many others) call "low responsiveness" or "perception of performance" is that there's not enough ram to run all the needed/required applications _altoghether_; setting swappiness=1 just makes it worse.

searching the net will return hundreds of more or less constructive discussions about this, all ending with the same quote:

*"basically, swappiness is deep personal choice"*

my personal preference settings on all boxes are
```
vm.swappiness=100
vm.vfs_cache_pressure=50
```

cheers :)

ps. sorry for triple posting, i go all new-reply-trigger-happy when i find an interesting topic. :D

But your proposed test isn't the way I use my computer, if it were you may be correct.  On my system, the way I use it, with the RAM I have available setting the swappiness higher gives me no advantage & swaps system to disk that would otherwise remain in RAM.  I very rarely use more than 40% of available RAM.

I know it is rather controversial, but the best advice I can give is to do as you did, experiment & find what works best. :)

---

### Post by sbraz on 2011-06-02
> **cbowman57 said:**
> On my system, the way I use it, with the RAM I have available setting the swappiness higher gives me no advantage & swaps system to disk that would otherwise remain in RAM.  **I very rarely use more than 40% of available RAM.**
in this case you'll probably never swap, regardless of how you set vm.swappiness. :)

---

### Post by cbowman57 on 2011-06-02
> **sbraz said:**
> in this case you'll probably never swap, regardless of how you set vm.swappiness. :)

You are probably right, but with the default, or even vm.swappiness=10, the system would start swapping to disk when it approached 60-65% which was overly conservative IMO.  It will still swap in the rare instance it is needed but not before it approaches 75-80% RAM usage.

---

### Post by iansane on 2011-06-02
Not surprised ultimate ran fine. I have to say MS really did a good job with 7. I think they actually took some lessons from Linux in coming up with a lighter weight faster running system. 

The UAC that started in Vista has options to make it prompt for password rather than that annoying "are you sure you want to do this?" pop-up. Either way, it's a pop-up prompting for elevation so the password thing in Linux is just something different to get used to. Both Linux and MS seem to agree that the password or prompt for elevation will keep your system more secure and I agree with them.

Ubuntu is getting more resource intensive (heavier and slower) with every dist. it seems. But in both Ubuntu and Win7 I turn off all the graphics affects and disable unnecessary startup and background processes and make them scream on some pretty junky hardware.

---

### Post by redspotss on 2011-06-02
nice and informing thread . i use a asus eee pc 1005 hac with an atom that once only had 1gb ram .i run a full desktop version of ubuntu 11.04 natty with alot of graphics like desktop cube 3d windows etc... wasn't very fast with the 1gb ram installed 2 gb runs really fast now but gets a little warm ended up getting one of those fan cooling mats which really helps keep it cooled off .anyhow the 2 gigs of ram helped with the speed of my asus

---

### Post by ivanovnegro on 2011-06-02
> **iansane said:**
> Not surprised ultimate ran fine. I have to say MS really did a good job with 7. I think they actually took some lessons from Linux in coming up with a lighter weight faster running system. 

The UAC that started in Vista has options to make it prompt for password rather than that annoying "are you sure you want to do this?" pop-up. Either way, it's a pop-up prompting for elevation so the password thing in Linux is just something different to get used to. Both Linux and MS seem to agree that the password or prompt for elevation will keep your system more secure and I agree with them.

Ubuntu is getting more resource intensive (heavier and slower) with every dist. it seems. But in both Ubuntu and Win7 I turn off all the graphics affects and disable unnecessary startup and background processes and make them scream on some pretty junky hardware.

If you really turn off all of the graphics effects then you cannot run Unity or Gnome 3, as this ones need 3D acceleration. KDE does not and so the lighter DEs/WMs.
As I dont use Windows, how this is working there, but I think Windows 7 doesnt require 3D acceleration to run? I would not be surprised then if Windows 7 would run smoother as Ubuntu 11.04 with Unity.

---

### Post by jtarin on 2011-06-02
> **picorex said:**
> 
i could, but you're missing the point that win7 ultimate ran just fine on 1GB of RAM. i'm just surprised that ubuntu runs worse, and wondered what i'm doing wrong for it to be like this.
That's a parameter that has large and small implications. For one I wouldn't have started with 11.04 to many idiosyncrasies to be tuned just yet. You should have started with 10.04 or 10.10. Then starting with a full-blown Ubuntu desktop on a little netbook is asking for problems. Linux will run on that netbook.....just run a different environment. Let me ask you a question.....if Win 7 ran so fine....why did you remove it?

---

