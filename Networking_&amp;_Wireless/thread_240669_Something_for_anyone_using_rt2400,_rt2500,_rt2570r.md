---
title: "Something for anyone using rt2400, rt2500, rt2570/rt2500usb, rt61 WLAN adapters"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by lupine_nickt on 2006-08-21
Hi,

I've started a tiny (really tiny) repository for the chipsets mentioned in the title. As of now, there are packages to match Dapper's stock 2.6.15-23-386 and 2.6.15-26-386 kernels, as well as one for those of you who've been brave enough to roll your own 2.6.17.9 kernel. There is also a package for the RutilT config program (ralink-config). 

sources.list line is as follows:-
```
deb http://ubuntu.lupine.me.uk/ dapper main
```

Package names are of the format ralink-drivers-<kernel-version>  - they're based on the CVS code, so updates will appear about once per day, around 6.30am. Whatever you do, don't try to install or update between around 5:50 and 6:10 because you could get caught in the middle of the update, and that would probably not be pretty. 

I'll be getting amd64 binaries up once I work out how to get them compiled; in addition, I'll update the kernels I compile for as Ubuntu update theirs (and as I update mine, for the .17.9 one!)

[size=+1]Update: amd64-generic and amd64-k8 support has been added for the -23 and -26 kernels. I've also compiled the config utility.[/size]

Note that I'm pretty sure that they should work, but as with anything GPL, there are no guarantees. The sole warranty provided is "well it worked for me!" ;)

Let me know of any successes/failures, or if there are any other **native** WLAN drivers not included by default in Ubuntu that you'd like to see up here. If I can compile them, I'll put them up :D

All the .deb packages themseleves are directly downloadable from [http://ubuntu.lupine.me.uk/pool](http://ubuntu.lupine.me.uk/pool)

Note that I'm hosting this from my house, so the upload is a mere(!) 100KB/sec. However, the packages are all pretty small, so d/l's won't take all that long...

xF,

...Nick

---

### Post by lupine_nickt on 2006-08-21
Quick note, before about... erm, 10 minutes ago ;)... the dependencies of the -drivers- packages were foobar'd, meaning that they were looking for (e.g.) package linux-image-2.6.15-26-386-386

D'oh!

Fixed now, anyway. Revision 2 uploaded :).

Now we just have to wait until tomorrow to see if the upgrade feature works properly. It should... ;)

xF,

...Nick

---

### Post by dsjas297 on 2006-08-21
I tried to install the configuration utility from Synaptic. It unfortunately failed producing this message:

Failed to fetch [http://ubuntu.lupine.me.uk/main/binary-i386/ralink-config_0.12-2_i386.deb](http://ubuntu.lupine.me.uk/main/binary-i386/ralink-config_0.12-2_i386.deb)

I was able to get the package directly from your site, so everything's OK.

Thank you for hosting these packages.

---

### Post by greatmetal on 2006-08-21
Very nice even though they have no use to me

[http://ubuntuforums.org/showthread.php?t=189509](http://ubuntuforums.org/showthread.php?t=189509)

---

### Post by lupine_nickt on 2006-08-21
Broken Packages.gz - fixed now :). Thanks for telling me.

xF,

...Nick

---

### Post by lupine_nickt on 2006-08-21
Bump!

Don't suppose this is sticky-worthy, is it admins...?

xF,

...Nick

---

### Post by mrfreddy on 2006-08-22
As far as compiling the rt61 driver for AMD64 or even Intel you might benefit from my own experiences here:
[http://www.ubuntuforums.org/showthread.php?p=1407558#post1407558]("http://www.ubuntuforums.org/showthread.php?p=1407558#post1407558")

HTH

---

### Post by lupine_nickt on 2006-08-22
Hi,

Thanks for the heads-up - I'll look into it :). So would you say that the x86 rt61 CVS is usable? Or does it definitely need this patch?

Anyone who's actually installed a package from the repository should be aware that the auto-update isn't working properly right now. I expect to have it fixed by the next update (6am on the 23rd August), so watch this space :)

xF,

...Nick

---

### Post by lupine_nickt on 2006-08-22
Righty, now we're getting somewhere. The versions for yesterday's packages were in a slightly different format to those being used today... so remove any packages you did install, do an update, then re-install. That won't affect your current internet settings/etc. in any way.

The build process for the 2.6.17.9 kernel is still a PITA... but I managed to get one made and it's sat there waiting (mind you, I'm likely the only person using it ;) )

xF,

...Nick

---

### Post by mrfreddy on 2006-08-22
> **lupine_nickt said:**
> Hi,

Thanks for the heads-up - I'll look into it :). So would you say that the x86 rt61 CVS is usable? Or does it definitely need this patch?
I can't comment as I haven't installed Ubuntu on an x86 box yet sorry. I don't even have the iso.

Let me re-iterate my amd 64bit experiences:
For a D-Link DWL-G510 RevC1 PCI card the beta driver at [http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b1.tar.gz?download]("http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b1.tar.gz?download")
is the one to work in the AMD X2 3800+ dapper 6.06.1 amd-server box. Neither the default supplied with the kernel nor RaLink drivers worked with the dual core box. 

The default kernel & beta driver from [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com") would lock up my A64 3000+ single core box (with dapper 6.06.1 amd64-desktop). I didn't bother testing the RaLink v1.04 version on the single core box, I went straight to the serialmonkey daily cvs driver & applied the patch. This driver finally worked.
   The patch might still work when applied against the beta driver however.

And finally: This patch will introduce a memory leak
> About every 10 minutes You loose RAM at the size of about one network packet. 

So it's not production ready. ;)

---

### Post by lupine_nickt on 2006-08-24
Thanks for the extra details. I'm still working on getting amd64 to build. 

Quick update on status:-
Support for the 2.6.15-23-* kernels has been removed, in order to broaden the range of -26 kernels supported. I've now got packages for 2.6.15-26-386, -686 and -k7 kernels built. 

Starting from now, when a new kernel comes out, I'll leave one package for each old kernel in the repos, and switch the daily builds to the new kernel. 

If anyone needs the -25*,-24*, -23* packages, let me know and I'll build them.

Oh, and the dependency on the linux-image package has been removed... it was causing too much hassle ;)

xF,

...Nick

---

### Post by misGnomer on 2006-08-31
How should one manually locate and download the files for sneaker-netting to a system with broken wifi?

Please also announce if/when these drivers get included in Edgy (Knot, daily or beta). It would be nice to have bootable media with network access :-)

PS. Is RutilT a replacement for Network-Manager or an alternative tool?

---

### Post by misGnomer on 2006-09-01
Could someone kindly provide direct links to the files for downloading?

The machine in need of these files can't connect to the internet (not even the rt2x00 repository! <g>) until its wifi gets working.

Thanks.

---

### Post by JaggedKnife on 2006-09-01
[http://ubuntu.lupine.me.uk/dists/dapper/main/binary-i386/]("http://ubuntu.lupine.me.uk/dists/dapper/main/binary-i386/")

---

### Post by misGnomer on 2006-09-02
Thanks for the link JaggedKnife. It's an AMD64 system so I hope the i386 driver works alright.

---

### Post by ArneB on 2006-09-02
Please, my Good Ubuntu, bear with this absolute beginner.

I just installed Ubuntu on my newly built AMD64  2x 3800+, and cannot get my wireless PCI to talk (Zonet; uses Ralink). What would you recomend as the best course of action. (Please bear in mind this is my first LINUX experience...)

ArneB

---

### Post by misGnomer on 2006-09-03
Seems like we could use a native AMD64 version of the driver and the setup tool. Any progress on that front Nick?

The box in question (public use, rt2570 wifi connection only) had Dapper 6.06.1 installed from the i386 Desktop media, but uname gave the kernel as "AMD64 generic" and the packaged (386, K7) drivers wouldn't install.

If the rt2x00-CVS doesn't build on AMD64, what about the chipset-specific rt2570-CVS etc.?

---

### Post by lupine_nickt on 2006-09-04
Hi,

Currently the repository *does not have* amd64 builds of the module; and the i386 modules *will not work*

I'm in the process of getting access to an amd64 machine so that I can build the modules - I'm expecting to be able to get that up and running in the next 2-3 days, at most. 

In the meantime, building the modules (and the utility) is as simple as downloading the appropriate source files from [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) (it's recommended that you not use rt2x00 yet - it's still very experimental - go for rt2400, rt2500, rt2570 or rt61 as appropriate. That's what's in the ralink-drivers package, btw), making sure you have the right packages installed (sudo apt-get install build-essential linux-headers-`uname -r`), then unpacking the source, cd'ing to the created directory, and running 'make && sudo make install'

RutilT is an alternative to network-manager (and kwifimanager) - as I understand it, these drivers use a different type of interface than the standard tools use, so GUI config tools often fail with them... I'm not aware of all the details, though. 

As soon as Edgy is stable enough, I'll be upgrading... and then we'll see some modules :). TBH, I'd have to be insane to upgrade to Edgy right now ;)

Hope that helps.

xF,

...Nick

---

### Post by lupine_nickt on 2006-09-04
Alrighty then! Any brave souls (well, you don't have to be brave, I guess ;) ) willing to test out the brand-new packages?

Just added:-

ralink-config (0.12-1, amd64)
ralink-drivers-2.6.15-23-amd64-generic
ralink-drivers-2.6.15-26-amd64-generic
ralink-drivers-2.6.15-23-amd64-k8
ralink-drivers-2.6.15-26-amd64-k8

As usual, let me know how it goes. There shouldn't be any problems.

xF,

...Nick

---

### Post by Henry Rayker on 2006-09-04
I installed the following:
ralink-drivers-2.6.15-26-amd64-generic
ralink-config (0.12-1, amd64)

on my laptop (AMD Turion64) with a DWL 122G USB dongle and everything works now.

One little question I have is, how can I get the config tool to run on boot? I'd prefer it to just start up, not ask for a root password and start minimized in the tray, if at all possible...however, just starting on boot would be a definite start.

---

### Post by lupine_nickt on 2006-09-05
Hi,

Glad to hear it works :). Getting the config tool to run on start depends on which desktop you're using... unfortunately, it does require root priviliges, so does require you to add the root password. You're best checking in General Support, as TBH I don't have a clue.

If you just want the wireless itself to start working,  just edit /etc/network/interfaces appropriately.

Anyone else have any success/failures? (Particularly failure! :D) I believe that cards based on the rt61 chipset require a firmware, so I'm looking at adding that into a separate package once I work out the legalities of it.

xF,

...Nick

---

### Post by Henry Rayker on 2006-09-05
I also have an rt61 based card, I could look into trying it out, over the next couple of days. I'm busy today (work, then another project) but tomorrow evening, if no one else has, I'll give it a go.

---

### Post by lupine_nickt on 2006-09-05
That would be handy :). I've sent a request to Ralink so am waiting for a reply from them... in the meantime, you can grab the firmware from [here](http://www.ralinktech.com/drivers/Linux/RT61_Firmware_V1.2.zip)

xF,

...Nick

---

### Post by Cuppa-Chino on 2006-09-05
hi tried the config util, but no luck what-so-ever
```
sudo rutilt

(rutilt:10414): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(rutilt:10414): Gdk-CRITICAL **: gdk_window_move_resize: assertion `GDK_IS_WINDOW (window)' failed

(rutilt:10414): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(rutilt:10414): Gdk-CRITICAL **: gdk_window_move_resize: assertion `GDK_IS_WINDOW (window)' failed

(rutilt:10414): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(rutilt:10414): Gdk-CRITICAL **: gdk_window_move_resize: assertion `GDK_IS_WINDOW (window)' failed

```

it could do a site survey but told me my router was WEP instead of WPA, could not establish if I have link etc - I am using RT61 based EDIMAX card and have a good connection

---

### Post by lupine_nickt on 2006-09-05
So the conf utility refused to load up at all?

A few things you could try - 
1) Run it from the terminal as "gksudo rutilt" or "kdesu rutilt"
2) Run it from the Big K/Big Foot Menu->Run Command; with the commands above, or (if they don't work) tick the 'advanced' tickbox and run as user 'root'

Did you have to download and install the firmware manually?

xF,

...Nick

---

### Post by Henry Rayker on 2006-09-05
I'm sorry,  this maybe a stupid question, but how should I install that firmware?

I tried the setup tool with my current config and it recognized what card I had (the title bar said RT61) but I had no RT61 tab (I assume I should, based on my RT2500usb card's performance) and also I couldn't even scan.

---

### Post by lupine_nickt on 2006-09-06
To be honest, I have no idea regarding the rt61 devices - I don't have one myself, you see :(. 

The rt61 driver is still very much experimental, and the amd64 build won't work at all properly right now as I haven't been applying the aforementioned patch to the source before compilation. Like the developers, I'm somewhat uneasy about the patch as well... coders have a natural aversion to memory leaks ;). 

The firmware seems to want to go in /etc/Wireless/RT61STA however, so just unzip the file and put it all in there.

It looks like the firmware is redistributable, so I'll likely be including it in the packages from the next set of builds (I've had to stop building daily, for now)... I'll update when that is.

xF,

...Nick

---

### Post by Henry Rayker on 2006-09-08
I'm giving the k8 version a try right now, as well. I was a fool and installed the wrong kernel and I finally committed to fixing it. Here's to hoping not too much gets broken.

Trying the rt61 based card, I only get Link Status, Statistics, Profiles, Site Survey and Options tabs (not one for the card itself). When I try to scan (under site survey) I get a critical error: can't trigger scanning. Code : 100.

This card just seems to cause more trouble than it's worth. I have one wireless device working, but I want to get both...just in case :KS

Another quick question. Should WEP or WPA work? I've got nothin'.

---

### Post by Ralphthedog on 2006-09-08
Success!!!

Thankyou lupine_nickt, I'm using your driver/RutilT stuff for my (rt61) D-Link DWL-G510 C2 Firmware 5.00 successfully on my wireless network with no security(now to figure out getting WPA organised?!). It seems stable and I haven't had any problems the couple of days I've been mucking around - just basic surfing the net etc..

This is my first encounter with Linux of any kind(Ubuntu 6.06.1 i386 installed) so I'm just a little out of my depth trying to compile drivers etc., you really helped me out with the only hardware in my PC Ubuntu wouldn't play nice with.

Hope this feedback helps.

RTD.

EDIT:

WEP works(64bit so far), can't really identify what exactly caused it to start working due to me trying to configure unsuccessfully via iwconfig and iwpriv too. In the end it just worked via rutilt, ticking the ascii box and entered the key (lower case)....

@Henry Rayker - I got that same error trying to scan without the card enabled...

---

### Post by lupine_nickt on 2006-09-12
Looking forwards, Edgy is released soon...!

I've got it running in a VMWare machine at the moment, and a quick scan of the ralink drivers available reveals [this](http://www.ubuntuforums.org/showthread.php?t=192588)

So, I'm curious as to how people think I should update this repository. Currently, all the drivers are in one package, and are installed into the extra/ directory. I was considering splitting out each module into a separate package (e.g. rt2500-rt2x00-legacy-driver, rt2570-rt2x00-legacy-driver), and having them automatically overwrite the Edgy-provided modules (obviously, with backups made so that the edgy modules would be restored on removal of the package). 

Also, since it'll be a 2.6.17 kernel, we can now use the DeviceScape 80211 stack, and the rt2x00 drivers. Again, for these, was thinking about having the 80211 and rate_control (common modules) in a package like rt2x00-common, then the individual module files (and other module-specific things... like firmware) in, e.g. rt2400-rt2x00-driver, rt73-rt2x00-driver.

The ralink-config package I'd like to rename to rutilt, as that's the name of the software!

Somewhat more complex, I agree, but I think it's a better way to do it. HOWEVER, I'm not the one using the repo, so I'd appreciate any feedback, etc.

xF,

...Nick

---

### Post by Henry Rayker on 2006-09-13
lupine-nickt, that sounds great. I plan on installing Ubuntu on my girlfriend's computer (and I just finished installing the 32b version on my laptop, so I'm triple booting, 64b Dapper, 32b Dapper and Windows XP [for when I just HAVE to]) and yours will be the first packages I install.

after enabling my rt61 device, I can scan and see my network, but for some reason, it just won't connect...

EDIT: bah. ephing MAC filters.

---

### Post by Ralphthedog on 2006-09-14
@Henry Rayker, I don't know what I mean most of the time either.....I meant activated, turned on etc.(active in network manager?).

Sounds good @lupine_nickt, I think it's a good Idea to have per-chipset drivers, so long as it's clear which is which for those of us who don't have much of an idea what they're doing.:D 

RTD.

---

### Post by Henry Rayker on 2006-09-14
As far as per-chipset drivers go, I think it's a great idea. Would it be much more difficult to also maintain them in the same way you are now (all grouped together in one package) as well as the individual ones? My reason for asking is I do use both RT61 (now that I got it working) as well as rt2500usb. Having an extra driver or two around won't kill me.

If it is more trouble than it's worth for you to maintain the extra set of drivers, then, by all means, just do what's easiest for you!

---

### Post by lupine_nickt on 2006-09-18
OK, I've had a chat with one of the maintainers of the Edgy kernel, and he's agreed to update the 'legacy' drivers (rt2400,rt2500,rt2570). So that just leaves the rt2x00 drivers - rt61 and rt73 - at east, until the rt2400, rt2500 and rt2570 'new' drivers become stable.

So I'll likely drop those three modules, and maintain semi-regular updates of the other two (including the rt73 amd64 'fix' mentioned above), as separate packages, including firmware. I'll see if I can get the rutilt package put into universe for Edgy.

xF,

...Nick

---

### Post by lupine_nickt on 2006-09-20
Talk about a bad time for an ABI upgrade! (that's the -26 to -27 kernel upgrade in Dapper)! Sorry about the long delay in getting new packages up.

64-bit packages have just been uploaded. 32-bit packages are on the way in the next half hour or so - I'm just about to reboot to get them built. 

xF,

...Nick

---

### Post by Ralphthedog on 2006-09-21
Have the 2006-9-21 i386 drivers installed for my rt61, no problems.

WEP is also working really nicely now too :D ....as opposed to grudgingly,sooner or later,maybe.

Thanks Nick.

RTD.

---

### Post by HeinBehrens on 2006-09-22
My rt2500 driver stopped working after months of no problems turns out after some update the WEP has been enabled in the rt2500.dat file. Commented it out and it all now works.

---

### Post by videodrome on 2006-09-24
FYI the rutilt debain synaptic package installed fine, but absolutely would not accept my password when I tried to scan for available wireless networks, rendering the program absolutely useless.

So I downloaded the tarball and compiled it using the nopasswd flag and it installed, runs as root, as works perfectly on my fully updated Xubuntu / Fluxbox system with a rt2500 pcmcia G card.

---

### Post by Ralphthedog on 2006-09-24
You have to "sudo rutilt" in a terminal window, then the version here works OK, only asks for the password once. 

I guess it would be nice to be able to click a rutilt button in a menu or have it load at startup....but I haven't worked out how to accomplish those yet:) 

RTD.

---

### Post by videodrome on 2006-09-24
Yeah I am saying that if I install rutilt through synaptic, and run it without sudo, when it asks me for the password, I enter the password, and then it doesn't work. It doesn't accept the password no matter what.

---

### Post by asfx on 2006-09-25
Hi, I tried downloading the debs directly.
Then I installed the following debs: ralink-drivers_cvs2006-09-04-kernel2.6.17.9_386.deb
ralink-config_0.12-2_i386.deb
I was the nable to configure the Device
and it even saw my local network.
But I couldn't connect..(WPA encryption I think.)
Anyway I tried rebooting but now the boot sequence hangs
at: Configuring Network Interfaces.
And I can't gte into Ubuntu.
Any Idea how I can fix this?

---

### Post by mozetti on 2006-09-25
Are you using an smp kernel?  Do some searching about smp kernels and Ralink driviers -- I had the same problem and it was because the Ralink drivers I used conflicted with smp kernels. Research to see if this is the problem -- you'll either figure out that 1)it is the problem, or 2) it isn't the problem and you can move onto something else a your culprit.

---

### Post by Kurdt on 2006-09-25
Any news about using rt61 and WPA auth ? :confused: :( 

Thanks

---

### Post by ingo on 2006-09-26
right, I thought I was reasonably savvy at wireless... until my rt2500 decided not to want an IP address any more! So I read and tweaked and read and tweaked til I was ******

Your utility was a last resort: I entered my profile and it wouldn't connect as usual but when I did a site survey I got connected!!! Apart from many thanks for your wonderful tool I'd like to know what the site survey did in terms of the command line.

Any info is much appreciated!

Thanks a ton

Ingo

---

### Post by Lillis on 2006-09-28
After I've made a profile for my network and try to connect, Rutilt locks up and does not respond. I'm using rt61 atm. Could this be that I have the wrong drivers? I dont know if I have, but I'm not sure. How do I know which one to install?

---

### Post by Kurdt on 2006-09-29
> **Kurdt said:**
> Any news about using rt61 and WPA auth ? :confused: :( 

Thanks

I tried this drivers plus wpa_supplicant and they work! i hope it works after restart :P

---

### Post by alecjw on 2006-10-01
About to try it now! Is it just the rt61.ko drivers etc?

---

### Post by smadahar on 2006-10-07
[FONT="Verdana"]A whole day with my brand new WMP54G Linksys card. I was ready to go Bruce Lee on my machine, I can tell you....

Basically, I'm typing this message from my wireless connection now. Here's what I did......

1) I added the repo from Lupine into my /etc/apt/sources.list 
2) In Synaptic I searched for rt61 (the chipset of my card) and installed the driver (making sure I chose the same driver-kernel version as my uname -r version. I also installed the config utility
3) In System > Network I entered the details for my wireless connection (which still didn't allow me to connect)
4) In Terminal I typed rutilt to open up config utility
5) I entered all my details here, pressed connect and hey presto! 

A big BIG thanks to Lupine_nickt for such an amazing effort, for the drivers and the config util. [/FONT]:p

---

### Post by neveceral on 2006-10-09
Is it already possible to use this "lupine's" repository for ubuntu edgy with rt61 chipset and i386 kernel?

---

### Post by Ba|der on 2006-10-16
Thanks Lupine_nickt for making this SW easily available. Althoug I have not made it to work yet.

I have Ubuntu 6.06 Gnome with kernel 2.6.15-27-386. My networkadapter is a CNET USB CWD-854 version F, and the computer is a DeskNote A928. I added the repository (```
deb http://ubuntu.lupine.me.uk/ dapper main
```) to System-admin.program settings. Then I ran Synaptic and installed ralink-config 0.12-2 and ralink-drivers-2.6.15.27-386 2006-09-21-01.

Under System- Admin- Network I got a Wireless connection rausb0 not configured. Pressing the Properties button made ifconfig prosess go to 97% CPU utilization. Kill -9, halt -n etc did not work and I had to do a hard shutdown.

I removed the USB-unit that had been inserted all the time before this and restarted. Now the Wireless connection in Network program was not listed anymore. I rebooted again and inserted the usb-adapter. Now it was listed again. I also checked the System-Admin-network tools program, and there it was not listed.

Then I ran gksudo /usr/local/bin/rutilt and got an error: Critial error cannot get TX rate. Code: 100. This popped up several times but the rutilt program started, but pressing scan for networkrevealed nothink. Link light on USB adapter have not been on in Ubuntu either,so I guess the driver is not loaded (properly).

Any ideas how to solve this?

APPEND:
I now also installed the rt2500 from the multiverse repository and then deinstalled the packages from Lupine_nickt.
```
[...] Removing ralink-drivers-2.6.15-27-386 ...
ERROR: Module rt2400 does not exist in /proc/modules
ERROR: Module rt2500 does not exist in /proc/modules
ERROR: Module rt2570 does not exist in /proc/modules
ERROR: Module rt61 does not exist in /proc/modules

```

APPEND:
According to [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) the RT2500 should work out of the box, and no extra install needed. Is there a way to check if my CWD-854 version F is based on the RT2500 chipset? (In windows I use RA-utility for it).

I have no also installed gcc 4.0 and via Synaptics rt2500, rt2500-2.6.15-27-386 and rt2500. I then did a "sudo bash" and unpacked the downloaded sourcefile. 
So I followed the instructions in the debian-readme:
module-assistant prepare
module-assistant get rt2500
module-assistant build rt2500
deb -i rt2500-2.6.15-27-386_1.1.0+cvs20051217-1+2.6.15-27.48_i386.deb

In System-Admin-Network only loopback and eth0 is listed and not the RA-adapter. There should also be some config utilities installed somewhere which I have not found yet. iwconfig gives this output:
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

APPEND;
I also tried to install the linux driver from RAlink (RT73_Linux_STA_Drv1.0.3.6.tar.gz) but I got lots of errors then compiling it, so I gave it up. I tried both the default Makefile and the Makefile.6 for kernel 2.6.x.

APPEND:
I got my card working using ndiswrapper and RT73 driver.

---

### Post by Tux Aubrey on 2006-10-26
Hi.

I'm in the process of setting up a new machine with a RT61 PCI wireless card (D-Link DWL-G510 Rev C) on edgy.

The debs don't seem to contain drivers for 2.6.17-10-generic kernel (which came with edgy RC1).  I tried the 2.6.17.9 drivers but they didn't work.

Is there an alternative or work-around?

Aubrey

---

### Post by Henry Rayker on 2006-11-12
I can't seem to get my RT61 card to work on Edgy...if anyone can, let us know!

---

### Post by neveceral on 2006-11-13
try this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=296822&highlight=rt61") , it is working very well

---

### Post by jetpeach on 2006-11-26
i got my hawking card (based on rt2500) working with WEP using the how-to in edgy (it worked kinda out of the box, but had some issues so i followed the how-to even though it's mostly from before edgy came out).  i didn't go through the steps for the configuration utility though, does anybody know if there is a simple deb file anywhere for the config utility?  
i have to type sudo dhclient ra0 to get it to get it to grab an ip address, wlassistant (kubuntu wireless manager) fails to get one, but otherwise all seems well.

---

### Post by Ralphthedog on 2006-12-02
> **Tux Aubrey said:**
> Hi.

I'm in the process of setting up a new machine with a RT61 PCI wireless card (D-Link DWL-G510 Rev C) on edgy.

The debs don't seem to contain drivers for 2.6.17-10-generic kernel (which came with edgy RC1).  I tried the 2.6.17.9 drivers but they didn't work.

Is there an alternative or work-around?

Aubrey

I'm finding myself in the same situation as Tux Aubrey - can't seem to get my ra61 up and running on Edgy, and Lupine Nickt's 2.6.17.9's won't work on my new Edgy installation......:(

---

### Post by rs3 on 2006-12-05
holy bat farts, batman--your packages got my wireless working!  i appreciate that!  thank you, thank you, thank you!

---

### Post by lupine_nickt on 2006-12-13
Heh, good to see people are still getting some use out of this :)

To clarify - do /not/ use the 2.6.17.9 packages. Trust me on this - it's a bad idea.

Edgy has rt61, rt73 support included OOTB and up-to-date rt2500, rt2570 as well so I haven't uploaded any packages for them.

---

### Post by Ralphthedog on 2007-01-08
My Kubuntu 6.10 install doesn't seem to agree regarding my(D-Link) ra61 wireless PCI card...... It steadfastly remained as an unknown device until I gave in and installed Ralink drivers?

The main reason I switched from 6.06 was the better wireless support:( 



RTD.

---

### Post by super.rad on 2007-03-23
Sorry total newb to ubuntu but if i add this respotorie (think thats what they're called) and then download the rt61 drivers will my wireless card (Belkin PCI using rt61) work straight away or will i need to configure the drivers first?

---

