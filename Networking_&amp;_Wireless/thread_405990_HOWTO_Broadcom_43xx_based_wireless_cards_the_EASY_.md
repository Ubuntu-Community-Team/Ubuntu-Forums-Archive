---
title: "HOWTO: Broadcom 43xx based wireless cards the EASY way."
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by DarkN00b on 2007-04-10
[SIZE=3][COLOR=Red]_This method is no longer supported and could possibly cause more problems than it fixes. I'm going to leave it up, but just remember - use it at your own risk._

This application is in no way supported by Canonical, the Ubuntu forums or its staff. Use of this application is at your own risk.

You should also know that the code maintainer for this project has moved on to bigger and better things. Unfortunately I don't know anything about programming in python (or any other language.) Thus, the installer available here for download is no longer maintained. Also be advised that the offline installer _will not_ work with Gutsy Gibbon. The online installer may or may not, I haven't tried it. [/COLOR]

[COLOR="Blue"]A note for anyone wanting to install these drivers: If you are using Gutsy Gibbon, it is recommended that you either use the restricted drivers manager to install the firmware or install ndiswrapper yourself. This installation method has already outlived its intended life cycle. If you want to contribute to the next phase of bmartin's work, have a look [here]("http://sourceforge.net/projects/wifix/") That project needs your support, and by support I mean testing. bmartin needs people to run the script available there. Just running the script will not make any changes to your machine but error reports would be appreciated.[/COLOR][/SIZE]

[SIZE="3"][COLOR=Blue]IMPORTANT!!! Before you run any of the scripts in this post, read the entire post before doing anything else![/COLOR][/SIZE]

[SIZE="3"][COLOR=Red]For those of you using WEP, WPA etc. encryption, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=202834"). You'll find some great info there.[/COLOR]
[/SIZE]
Speaking of encryption -- If you decide to use the WICD wifi connection manager (and we suggest you do), then you should set the WPA Supplicant driver to "wext" without the quotes. It can be found by clicking the Preferences button in WICD and selecting the drop-down box that shows up there..

Now first of all, thank you for using this HOWTO to try and get your Broadcom card working. Your patronage is appreciated :) . So here's what we need from you the user. All we ask is that you vote in the poll above. The numbers appear to be skewed very badly and I think they do not reflect the actual usefulness of bmartins great scripts. As an example, from 16 Sept. 2007 to 26 Sept. 2007, about 390 people downloaded the installer, yet the poll indicates that only 463 people have voted in total since this project started on 10 April 2007. For those interested that's 546.3 MB, just over 1/10 my allowed bandwidth for 30 days.

New update! bmartin has updated Python based GTK installer for the firmware and ndiswrapper. We have now gone from v0.3.1 to v0.3.2. See the changelog included with the download for new features. There is a description of the software [here]("http://blakecmartin.googlepages.com/index.html").

This howto has been split into two sections. The first is for Gnome / XFCE users and the second is for KDE users. Neither bmartin or I have been able to figure out how to get a Python script to run on double click in KDE. If anyone out there can help with this, please post a message, or PM bmartin or email him. For the time being, see the section for your desktop environment for instructions on how to install these drivers.

The installer checks for a compatible chipset. If it finds that your chipset is compatible it will tell you. If it finds that your chipset is not compatible, it will tell you. I have tested it and this detection seems to work fine. Either way, it is your choice as to which way you want to go. Just choose the method you want to use and click install. It is that easy. If your chipset is found to be incompatible, you will be given the option to install NDISwrapper and the correct Windows driver. The installer     now does some automatic logging and includes some information from your kernel log and your system log.

Before you get started, open a terminal and type ```
sudo aptitude update
sudo aptitude upgrade
```
Now before you start installing anything, make sure your card is turned on. Laptops with built-in wifi usually have a key combination (most often fn+F2), check your manual. If you are not using a mobile computer, check your BIOS to see if you need to enable detection of PCI devices. You can enter the BIOS of your computer by pressing a button as it boots up, and the machine will tell you which button(s) to use. You will only have a second or two to see what you need to press. Most computers use one of the following keys to enter BIOS: ESC, DEL, F1, F2, F10. Just have a look through your BIOS, but heed this warning! Don't change anything unless you know what you are doing! Mess this up and you could be left with an unbootable computer! If this happens all is not lost though. Just hard reset your machine, enter BIOS, and find the option to reset BIOS to factory defaults and that will fix your problem.

[U][SIZE="5"]
**[COLOR="Blue"]Section 1 - Gnome / XFCE[/COLOR]**[/SIZE]
[/U]
1. Download one of the installers. It is easiest to save this file to your home folder but it doesn't really matter where you put it:
[LIST]
[*][Online (0.3.2) installer]("http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz")
[*][Offline (0.3.2)Installer]("http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-offline.tar.gz") - (Not all kernels supported)
[*]If there is a problem downloading the offline installer, please use the alternate link at the end of this post and send me a PM so I can fix it.[/LIST]

2. Right click the .tar.gz file and click Extract Here. It should extract into its own directory.

3. Go into the bcm43xx-gtk-installer-* folder and double click the installer.py file and click the _R_un button when prompted.

4. The installer should detect which installation method is appropriate for you.

5. Click the install button to install the appropriate driver.

6. Now enter your password and press the Enter key.

The driver should now be installed. Note that you may have to restart your system depending on which method you chose.

[U][SIZE="5"]
**[COLOR="Blue"]Section 2 - KDE[/COLOR]**[/SIZE]
[/U]

I'm afraid for the time being that KDE users are going to have to use the terminal -- at least until we can figure out how to execute Python scripts in KDE. So here we go:

In a terminal window type the following lines, hitting the enter key at the end of each line. **NOTE**: only use one of the wget lines. Choose the installer you want to use and wget that one file. If it doesn't work, you can try the other one.

1. 
```
cd ~
wget http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz
wget http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-offline.tar.gz
tar xvf bcm43xx-*.tar.gz
cd bcm43xx-*
./installer.py
```
[LIST]The * needs to be replaced by version number of the file you downloaded.[/LIST]

2. The installer should detect which installation method is appropriate for you.

3. Click the install button to install the appropriate driver.

4. Now enter your password and press the Enter key.

Follow the prompts and choose the method that is best for you

The driver should now be installed. Note that you may have to restart your system depending on which method you chose.

If you are a KDE user and know how to get Python scripts to execute as a program, please let us know. At the moment, the default mime type for .py files in KDE is text-plain and we are not able to figure out how to execute them. Simply setting them to executable does not work.

[COLOR=Red]**-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**[/COLOR]
Thanks to [COLOR=Red]bmartin[/COLOR] and his hard work to improve this whole process.

If you are helped by this howto, you might consider giving a donation to the bcm43xx folks [here]("http://bcm43xx.berlios.de/?go=donations"). Please note that bmartin and I are not affiliated with these guys.

**Frequently Asked Questions:**
Q: I've installed the firmware (or ndiswrapper) and I can see networks, but I can't connect. What can I do?
A: Many people encounter this problem. It's unlikely that reinstalling the firmware or ndiswrapper will solve it. Your best bet is to install wicd. For several users, wicd solves this problem.

Q: How can I get WPA to work?
A: There's a link to a stickied HOWTO for this topic right at the top of this post after the disclaimer (third line, red text). If you feel uncomfortable with those instructions, wicd has built-in WPA support. Your WPA driver should be set to "wext".

Q: I have a blog and I want to link to your instructions. Is that OK?
A: Yep. I encourage it.
[COLOR=Red]**-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**[/COLOR]

There is an offline installer available [here]("http://darkn00b1971.googlepages.com/bcm43xx-0.3.2-offline.tar.gz"). Use it if you have a machine than has no physical access to the internet. If too many people use this installer though, be aware that I may exceed my Google Pages bandwidth and the file may become unavailable.

---

### Post by jeffisawesome on 2007-04-10
Works like a charm.  Thanks so much.

---

### Post by DarkN00b on 2007-04-11
Glad to hear it! Its good to have independent verification that this actually works.

---

### Post by Duffcase on 2007-04-11
works like a charm on my HP dv2140 with feisty. Thank you! :)

---

### Post by dbott67 on 2007-04-11
Another happy guy over here:
[http://ubuntuforums.org/showthread.php?p=2437223#post2437223](http://ubuntuforums.org/showthread.php?p=2437223#post2437223)

-Dave

---

### Post by DarkN00b on 2007-04-12
> **dbott67 said:**
> Another happy guy over here:
[http://ubuntuforums.org/showthread.php?p=2437223#post2437223](http://ubuntuforums.org/showthread.php?p=2437223#post2437223)

-Dave

That's really cool. [img]http://scosoft.com/s/d/62a82059.gif[/img]

It feels good to know you helped someone.

---

### Post by zamBeeK on 2007-04-16
Thank you so much. Came off without a hitch.

BK

---

### Post by Madmoose on 2007-04-16
Hey, 

How do I fix this?

```
sudo: ./installbcm43xx.sh: command not found
```


Thanks 

moose

---

### Post by dbott67 on 2007-04-16
The command should be:
```
sudo /path/to/file
```(there shouldn't be a colon after 'sudo').

You also need to be in the directory where the script is saved before running the command:
```
sudo ./installbcm43xx.sh
```-Dave

---

### Post by DarkN00b on 2007-04-16
The above post is correct. You need to be in the directory where you extracted the files. The firmware should be copied as soon as you put in your password.

---

### Post by VitaliyNYC on 2007-04-16
Just bought a Linksys WPC54G which uses Broadcom Corporation BCM4318 [AirForce One 54g], this worked great! :)

---

### Post by stiv2k on 2007-04-16
Hi, I have tried your instructions and althought everything works fine, I have noticed my connection is now SLOWWWWWWW.  Speedtests dont top 150 kbps, i have 90% signal strength being in the same room as the router.  None of the other computers on my network experience this problem so it can't be my connection.  This happened as soon as I used your driver instead of ndiswrapper.  I have a broadcom 4311 chipset on my HP pavilion dv9009us laptop.

Any help is appreciated, thanks!

---

### Post by Floppyjoe on 2007-04-16
> **stiv2k said:**
> Hi, I have tried your instructions and althought everything works fine, I have noticed my connection is now SLOWWWWWWW.  Speedtests dont top 150 kbps, i have 90% signal strength being in the same room as the router.  None of the other computers on my network experience this problem so it can't be my connection.  This happened as soon as I used your driver instead of ndiswrapper.  I have a broadcom 4311 chipset on my HP pavilion dv9009us laptop.

Any help is appreciated, thanks!
Not all speeds are supported by the experimental bcm43xx drivers for every different chipset yet.
These are reverse engineered drivers that are sometimes not stable.

The developer of the driver has a site which might explain more fully:
[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

---

### Post by neorab on 2007-04-16
Thanks a ton for this.  After a few failed attempts at setting up my 4318 wireless card, I found this and it worked in under 2 minutes.  Good stuff.

---

### Post by DarkN00b on 2007-04-17
You're welcome, but the real credit should go to the OP in [this]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") thread. All I did was tar.gz the firmware extracted from the wl_apsta.0 package there and add a script to install it. I did not originate the firmware.

---

### Post by plinny on 2007-04-18
WOW!  I've been trying to get wireless working with ndiswrapper for almost three days...you my friend are a life saver!  thanks, from noobs everywhere!

---

### Post by micdhack on 2007-04-18
Another happy person here :) My only problem is that in my wireless i have WPA key but i will try the wpasupplicant...

---

### Post by kirab on 2007-04-18
Wow awesome! This really works! My issue with the other methods on this forum was that I don't have enough experience with Linux to do some of the steps (and there were a lot more steps than in this tut) so I had trouble. Thanks a lot.

---

### Post by ]Nbx*cmD[ on 2007-04-18
Hi all,

I may be doing something stupid... I followed your instructions and I had my wifi working perfectly. 
Then I rebooted and nothing worked anymore, I have networkmanager installed and running, but it doesn't show my device anymore... my card is a LinkSys WPC54G ver. 3.1 PCMCIA.

---

### Post by DarkN00b on 2007-04-18
> **']Nbx*cmD[ said:**
> Hi all,

I may be doing something stupid... I followed your instructions and I had my wifi working perfectly. 
Then I rebooted and nothing worked anymore, I have networkmanager installed and running, but it doesn't show my device anymore... my card is a LinkSys WPC54G ver. 3.1 PCMCIA.

What did your connection show up as in networking? Was it something like eth0, eth1 or wlan0?

Whatever it was, try this (example).

In a terminal, type ```
ifup eth0
```

Use whatever your connection was if it wasn't eth0.

---

### Post by benson444 on 2007-04-18
Chalk up another success! Booted from Feisty desktop cd, copied the firmware from a USB stick, installed it, clicked on nm-applet, entered network name and WPA key and off we go! Fantastic, man.

Using a BT Voyager 1040 pci wireless card.

Thank you!

---

### Post by DarkN00b on 2007-04-18
You know this one thing really irritated me about Feisty. When I created a dual-boot with windows on my desktop, Feisty asked me if I wanted to install the BCM43xx firmware with fwcutter automatically. I don't have wireless on my desktop.

When I installed Feisty on my laptop, i wasn't even prompted. I had my card plugged in and everything.

Oh well, I ain't too worried. Great community beats a little problem every time. You guys (and gals) are great, and I'm glad I was able to help make things a little easier for you.

---

### Post by ]Nbx*cmD[ on 2007-04-18
> **DarkN00b said:**
> What did your connection show up as in networking? Was it something like eth0, eth1 or wlan0?

Whatever it was, try this (example).

In a terminal, type ```
ifup eth0
```

Use whatever your connection was if it wasn't eth0.

Yeah, that's what i first tried several times.

Now i got wireless working, but nm doesn't show my card either i can choose the wireless essid, i've got to configure it using system&#8594;administration&#8594;networking... any solution?

---

### Post by DarkN00b on 2007-04-18
> **']Nbx*cmD[ said:**
> Yeah, that's what i first tried several times.

Now i got wireless working, but nm doesn't show my card either i can choose the wireless essid, i've got to configure it using system&#8594;administration&#8594;networking... any solution?

Not that I know of. 

NM never recognizes my card and I have to configure it the same way. It probably has something to do with the fact that my connection shows up as wired (eth0) and not wireless (wlan0). I choose to ignore it and just go with what works for me.

---

### Post by ]Nbx*cmD[ on 2007-04-18
nice... but the funny thing is that i got it working when i tried it first... weird stuff :P
Anyhow, tomorrow i'll be using feisty stable so no need to bother much ;)

---

### Post by jpyanowski on 2007-04-18
I'm on my lunch at work right now. I have a new HP dv2000 that I want to dual boot with Fiesty. When I use the Live CD I can't get any wireless. I'll use this thread to see if I can get things working now. Wish me luck.:popcorn:

---

### Post by dashnak on 2007-04-18
Has anyone tried this out in a Dell 1501?

---

### Post by xhentil on 2007-04-19
I did run the script and right away I was able to pick up wireless networks in Network Manager (Feisty). However, it does have a key on it, which i know, but I cannot connect to it. Any ideas before I move on and try the ndiswrapper *shudder*?

---

### Post by thetortoise on 2007-04-20
Wow!  After weeks of struggle this worked on my fresh install of Feisty in all of 5 seconds without even rebooting.  BCM4318 on a dv8000 laptop.  I can't believe it.  Nice work!  

For those struggling with the path the program is probably on your desktop right?  So open the Terminal program and type: ~$ cd Desktop/bcm43xxfirmware (make sure you capitalize the D in Desktop, welcome to the world of case sensitivity)

That will get you to the right directory to execute DarkNOObs excellent script.  Thank you again.

---

### Post by trav5 on 2007-04-20
Another satisfied customer! Thanks darknoob. I did have to remove and replace card to connect:confused:

---

### Post by coolguy2k on 2007-04-20
perfect!  thank you thank you.  This was the easiest time i have had for the 43xx card on any distro.  Thanks much.

---

### Post by ShdwNova on 2007-04-20
Worked perfectly on my Acer TravelMate 2480. Thx DarkN00b.

---

### Post by DarkN00b on 2007-04-20
> **xhentil said:**
> I did run the script and right away I was able to pick up wireless networks in Network Manager (Feisty). However, it does have a key on it, which i know, but I cannot connect to it. Any ideas before I move on and try the ndiswrapper *shudder*?

What kind of key is it? WEP, WPA? Feisty supports WEP and WPA can by\e added with WPA Supplicant. I know nothing about WPA Supplicant though.

In case anyone is wondering, the reason you have to reinsert your card is that the firmware has to be loaded into it on initialization. That's why I always install it before I insert my card for the first time.

---

### Post by xhentil on 2007-04-20
> **DarkN00b said:**
> What kind of key is it? WEP, WPA? Feisty supports WEP and WPA can by\e added with WPA Supplicant. I know nothing about WPA Supplicant though.

In case anyone is wondering, the reason you have to reinsert your card is that the firmware has to be loaded into it on initialization. That's why I always install it before I insert my card for the first time.

It's a WPA run through my school, so i have no access beyond the key. Before I got this new laptop (Dell Latitude d620 with the Dell Truemobile 1390/Broadcom 4311 chipset) I had a Linksys WPC11v4 PCMCIA card that worked through everything in Dapper. Can't get said card to work on this thing either.

I do believe I butchered a few things however in trying to get ndiswrapper to work. The wireless light is no longer on and network-manager no longer picks anything up. ifconfig reveals no wireless interfaces (previously eth1). So now I'm even deeper without wireless!

Honestly, i'll continue this for a bit, but I'm contemplating just buying a card with an Atheros chipset or something that is known to work.

---

### Post by DarkN00b on 2007-04-20
Well that's the beauty of Linux. Some things work well for some people and not for others. Use what works best for you. I'm sorry if this solution doesn't work.

---

### Post by danish77 on 2007-04-21
worked perfectly with 7.04 on a Dell Inspiron 1150 with Broadcom BCM4306. thanks

edit: well only 11mbps so not perfect. but it's a start

---

### Post by _lucutus on 2007-04-21
thanks a lot it works very well - i was already desperate ..

---

### Post by firstc624 on 2007-04-21
this is  agreat little script to get wireless working fairly easy.  the only reservation i have, and i am not complaning, is that the bcm firmware only hits 11M a sec.  which is fine in most cases, esp here in teh states unless you have huge lines, but data transfers are less that desirable.

O well.  does anyone know if there will ever be native linux support for a 54M transfer rate?

Great job to teh devs btw   :-)

---

### Post by Tuxi on 2007-04-21
TYVM for this HOW TO.  I've finally gotten my WPC 54G to work again.  (It hasn't been usable since 5.10, IIRC).

---

### Post by DarkN00b on 2007-04-21
> **firstc624 said:**
> this is  agreat little script to get wireless working fairly easy.  the only reservation i have, and i am not complaning, is that the bcm firmware only hits 11M a sec.  which is fine in most cases, esp here in teh states unless you have huge lines, but data transfers are less that desirable.

O well.  does anyone know if there will ever be native linux support for a 54M transfer rate?

Great job to teh devs btw   :-)

My thoughts exactly. It works, so no complaining from me. :) 

And yes, the devs(not me) rock.

---

### Post by NewbornPenguin on 2007-04-21
Thank you so much. No more ndiswrapper. Works on Gateway 7330 GZ laptop.

---

### Post by lzydba on 2007-04-21
This worked great for me on a fresh install of Kubuntu 7.04 Fiesty. I loaded the files you provided onto a thumb drive and transfered them that way and then just followed the instructions you gave. I didn't have to do anything else. Works like a charm.

Thanks!

---

### Post by dimeotane on 2007-04-21
Unfortunately this nice simple script didn't work for my Dell M1210...
well it did 'work' but it was about as fast as my old 14.4 modem =p
 
which has the "Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)"

If you want to know what card you have you can enter in the terminal:
$ lspci | grep -i network
$ lspci  grep  -i wireless

according to this document:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
it is the broadcom 4311 which is now listed in Ubuntu v7.04 'feisty' as the dell wireless 1390.

In the end I went back to using ndiswrapper method.

---

### Post by bridd on 2007-04-22
Thankyou for this -got my Dell  D400 latitude's wireless working on Fiesty 7.04 straight away :guitar:

---

### Post by beastly on 2007-04-22
Brilliant, works a treat for me! Using WPA-AES too via network manager with no probs.

Many thanks!

---

### Post by AlfaSub on 2007-04-22
Great job dude! Works perfect w/ my laptop, Belkin Wireless G connector.
Now I finally know what my signal strength is :)

---

### Post by Linuturk on 2007-04-23
for some reason, your script wouldn't copy over the files for me. I simply opened the script and ran the two copy commands, and it worked like a charm!

Thanks!

---

### Post by OneSeventeen on 2007-04-23
It worked!
HP Pavilion zv6000 from the US with Broadcom 4306 (rev03).

I used fwcutter on 6.10 and only got the networking to work half the time, and even then after 10 or 15 minutes of repeating the same commands until it finally got a dhcp lease from the access point and access to a dns server of some sort.  (wifi always worked on this laptop using ndiswrapper in 5.04 and 6.04, but dapper drake didn't like my wifi card for some reason)

Getting the same download speeds from wifi as I do from wired while here at work (which is about 2.4 Mbps).  I'll edit this post with speed results at home which range from 7 to 10 Mbps normally.

Thanks for the post!

---

### Post by DarkN00b on 2007-04-23
Did you run it through the terminal with Sudo? If so it should have worked just fine. Clicking and selecting the 'Run' button it won't work. 

It occurs to me now that if I had used **sudo** before the **cp** commands in the script it would have prompted for your password. I think I'll fix that right now... :)

---

### Post by henriklundh on 2007-04-23
HI when i hit enter in step three noghing happends... im not even asked for password...

i have an acer ferrari 1005wlmi

grateful to replys

---

### Post by heinig on 2007-04-23
Sorry if the question is dumb (I'm new to linux :-)) but... could someone say to me if there is any difference between this script and if I just "sudo aptitude install bcm43xx-fwcutter"?  The fwcutter in the repositories seems to extract the firmware from your card automatically....

---

### Post by KeighleHawk on 2007-04-23
Add me to the list of slap-happy customers.  This was a beautiful thing!  Perhaps suggest/submit for inclusion in the standard distro?  I was prepared for all kinds of pain to get this running, and it just plain worked.  Very niiiiccceee.....!

Success on:  Dell M60, internal Broadcom 4306

P.S.  It may just be a couple simple commands, but as the old joke goes, $1 for the script, $99 for knowing how to write it...

---

### Post by srt5 on 2007-04-23
Thank you so much for this guide. I used to have to find the drivers and go through Ndiswrapper - this method is so much more straight forward! Great Work!

---

### Post by benfeldman on 2007-04-23
Thank you SO much! I'd been trying all the other workarounds to getting my 4310 working, but they didn't work...

I just tried your re-package and within moments I had wifi working. It is *quite* slow compared to being wired, but I'm not going to complain--honestly. 

I guess we can only hope full-support for these chips will come eventually, if that's possible. If not ... well, that's just fine, too.

If you care to know for putting down what computers work, here are my laptop's details:
Dell Inspiron 1501
AMD Turion 64 x2
Ubuntu Feisty 32-bit
2gb of ram

Thank you very much!

---

### Post by clapper65 on 2007-04-23
Ok, What am I missing?  I installed the script, I install my card (Linksys wpc54g ver3) and it shows up.  AWESOME!  I bring up the network manager and the enable roaming box is checked.  I don't broadcast my home SSID so I uncheck the box and it asks for the network name.  I key that in.  Then it asks for a WEP key, but I am using WPA.    The dropdown only shows WEP ascii and WEP hex, but no WPA.  What am I missing?

---

### Post by DarkN00b on 2007-04-24
Ok I'll try to answer some questions here. :)

**henriklundh**: Did you use the newly uploaded script, and if you did not, did you use the SUDO command? I uploaded a slightly different version this morning and it should ask for a password. Hmm, I checked and it doesn't. It does work through the terminal though. I will change the original post to reflect this.

**heinig**: You are correct. This is mainly for people who are still running Dapper or Edgy.

**clapper65**: WPA encryption isn't included in Ubuntu installs by default, AFAIK. You can use WPASupplicant if you use WPA, but I know nothing about it.

Everyone else, thanks for the input. It is very much appreciated.

---

### Post by henriklundh on 2007-04-24
what should happend after i hit enter when ive typed in my password?

---

### Post by DarkN00b on 2007-04-24
Nothing that you can see. There should now be a bunch of bcm43xx firmware (*.fw) files in your /lib/firmware folder as well as in the folder there for your latest kernel. For example your /lib/firmware.2.6.20.15-generic folder if that is the kernel you're running. If those files exist in those locations then you need to unplug your card and plug it back in, then configure your connection through System->Administration->Networks. 

Do you have a PCMCIA xard, a USB dongle or a desktop computer where the card is inserted into the motherboard? Also please type ```
iwconfig
``` into a terminal window, hit enter and post the output here and I'll see what I can do to help from there.

BTW: I'm going to bed in about 20 minutes, see y'all in the morning.

---

### Post by lord_nelson on 2007-04-24
I tried this on my Dell Inspiron 1501 and it worked but my wireless internet speeds are dog slow. My wireless speed under  windows is around 300kbs but when I use wireless under Ubuntu it clocks at 20kbs. Is there a way to fix this problem?

---

### Post by alkonet on 2007-04-24
Thanks a ton for your fix on linksys (broadcom) chipset cards.  Your post had me up and running in 10 minutes.  :) Thanks from Jacksonville, Fl.

---

### Post by DarkN00b on 2007-04-24
> **lord_nelson said:**
> I tried this on my Dell Inspiron 1501 and it worked but my wireless internet speeds are dog slow. My wireless speed under  windows is around 300kbs but when I use wireless under Ubuntu it clocks at 20kbs. Is there a way to fix this problem?

I don't think there is. This seems to be a problem that plagues some people for some reason. My download speeds range from 40bps to around 190 bps. Maybe when the firmware matures a little more things will get better.

I am however doing a lot of reading on sites found on [Google Linux]("http://www.google.com/linux"). It looks like there might be some progress soon.

---

### Post by JohnnyKurtz on 2007-04-24
WOW, DarkNOOB, you are a master! :KS 

This worked perfectly for me on my Gateway 7422GX x64 Laptop, with a Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 03) - A.K.A Intel Pro/Wireless Colexico II internal card.

I am new to Linux, and for the past three days have gone from Ubuntu Feisty, to Fedora 6, to SUSE 10, and back to Ubuntu Feisty. After all of these installs, I came to your guide, and am now sticking with Ubuntu; what a great community! Well, now I have two install DVD's I will not be needing.....

Now all I need is some way to switch easily between my three access points at home and some kind of signal strength doo-dad, any suggestions form the forum?

Cheers,
Johnny

---

### Post by jasper2408 on 2007-04-24
My wireless is now working thanks to you, DarkN00b. 

I am dual-booting Feisty on an HP zv5255 laptop with a bcm4306 chipset. 

I got this to work both on the LiveCD and after I installed it. The properties show only 11Mb/s but my downloads are right up there where they were before when I was using ndiswrapper w/Edgy. 

You made this so easy.

thanks again,

jasper

---

### Post by Dieter1967 on 2007-04-24
Working like a charm, so far!  Tried another "how-to" from a different thread, and things worked for a while.  However, when I rebooted, everything more or less fell apart.

Thanks for the info, and taking the time to do the leg work!  Maybe, someday, I'll be able to help.  Right now, I'm a total noob for Ubuntu (or anything related to Linux).  I've used some Unix (as a Mac owner, you have to), but I'm still a novice at it.

Thanks much for keeping things "monkey simple" -- read a step, do a step, eat a banana!!

---

### Post by DarkN00b on 2007-04-25
> **JohnnyKurtz said:**
> WOW, DarkNOOB, you are a master! :KS 

This worked perfectly for me on my Gateway 7422GX x64 Laptop, with a Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 03) - A.K.A Intel Pro/Wireless Colexico II internal card.

I am new to Linux, and for the past three days have gone from Ubuntu Feisty, to Fedora 6, to SUSE 10, and back to Ubuntu Feisty. After all of these installs, I came to your guide, and am now sticking with Ubuntu; what a great community! Well, now I have two install DVD's I will not be needing.....

Now all I need is some way to switch easily between my three access points at home and some kind of signal strength doo-dad, any suggestions form the forum?

Cheers,
Johnny

Thanks for the compliment, but I am *far* from being a master. :lolflag: 

Y'all need to understand that I didn't do anything special here. All I did was repackage the naked firmware from the fwcutter method. I'm not even sure it was OK for me to do that. I originally did it just for myself, but then thought it might be good to share. Now I have to provide support in this thread and meet new, cool people. :)

---

### Post by dermann on 2007-04-25
Thanks buddy, this is the first time working with Ubuntu that the external wireless LED has shown blue (on, working) on my dv2000. 
Instead of *-network DISABLED in the lshw screen, the card seems to be enabled now.
Hardware stats look like this now:
```

 *-network
             description: Wireless interface
             product: Dell Wireless 1390 WLAN Mini-PCI Card
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@01:00.0
             logical name: eth1
             version: 01
             serial: 00:14:a5:e1:81:5e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15
```

---

### Post by kyle_fransham on 2007-04-25
Thanks a ton for this howto darkNoob.  My Broadcom 4306 internal card now works perfectly.  I can even connect to the (unencrypted) network at work, something I couldn't do using edgy and ndiswrapper.  

I  don't know if this is important, but for those of you that have messed around with ndiswrapper previously, you may want to do the following, which I did before attempting this howto:

```

sudo aptitude remove ndiswrapper-utils-1.9

```
(change 1.9 to 1.8 if you're using edgy)

```

sudo gedit /etc/modprobe.d/blacklist

``` 
if there's an entry for bcm43xx, comment it out

Reload the bcm43xx module: 
```

sudo modprobe bcm43xx

```

Now proceed with the guide and everything should work.

---

### Post by bigspottycat on 2007-04-25
Thanks very much for this guide; this kind of thing normally takes me ages to solve but this worked first time. Much appreciated.This kind of community is what makes it all worthwhile...

---

### Post by mekas2024 on 2007-04-27
> **dimeotane said:**
> Unfortunately this nice simple script didn't work for my Dell M1210...
well it did 'work' but it was about as fast as my old 14.4 modem =p
 
which has the "Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)"

If you want to know what card you have you can enter in the terminal:
$ lspci | grep -i network
$ lspci  grep  -i wireless

according to this document:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
it is the broadcom 4311 which is now listed in Ubuntu v7.04 'feisty' as the dell wireless 1390.

In the end I went back to using ndiswrapper method.

Hey dude, could u tell me if ndiswrapper worked 4 u ? because im using this great script and it work but its too slow... and i wanna see if ndiswrapper work 4 u , and how u did it?

THX And thx for this script too :D

Mekas

---

### Post by ineksuyu on 2007-04-28
It worked flawlessly for me (4306 rev 03). I would buy you many beers if you were around.

Thanks a lot, I was almost gonna go back to Windows!

---

### Post by snizzitch on 2007-04-28
So cool - thanks.

---

### Post by scrivener on 2007-04-29
I just wanted to add that this worked flawlessly for me.  I didn't use the script.  I just copied the firmware to the appropriate directories and rebooted. 

I'm using an HP zv6000 series laptop (zv6015us to be exact) with AMD64 Feisty.  lspci lists my card as a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03).

---

### Post by Gabes Dad on 2007-05-03
Sadly, this did not work for me.  I am very new to Ubuntu just a frame of reference.  I have installed Feisty on an old Dell Latitude CPx H450GT and am using the Broadcom 4306 based Belkin F5D7010 Ver.1000v.  Anytime I insert the card into PCMCIA slot, the system becomes unresponsive until I remove the card and it goes back to normal just like nothing happened.  It did this before and after I install DarkN00b's script and similarly when I tried the NDISwrapper method ([described here]("http://ubuntuforums.org/showthread.php?t=201902")), which I tried after DarkN00b's script.

Also, something else that might help diagnose my problem, when installing Feisty from the Alternate install disc, it had me enter in something like "except 0x800 - 0x8ff" because it said my PCMCIA slot was conflicting with the CD drive and it couldn't read the disc.  After that the installation went fine.  I don't have any other PCMCIA devices to try out on the laptop to see if it is an issue with the slot.

If I were to try the ndiswrapper method do I first need to uninstall the drivers offered here?  If so, how do I do that?  Any help would be much appreciated as I am on a mission to make Ubuntu the main operating system on my and my wife's home computers and move Windows to the secondary position.

Thanks!

---

### Post by DarkN00b on 2007-05-04
> **Gabes Dad said:**
> Sadly, this did not work for me.  I am very new to Ubuntu just a frame of reference.  I have installed Feisty on an old Dell Latitude CPx H450GT and am using the Broadcom 4306 based Belkin F5D7010 Ver.1000v.  Anytime I insert the card into PCMCIA slot, the system becomes unresponsive until I remove the card and it goes back to normal just like nothing happened.  It did this before and after I install DarkN00b's script and similarly when I tried the NDISwrapper method ([described here]("http://ubuntuforums.org/showthread.php?t=201902")), which I tried after DarkN00b's script.

Also, something else that might help diagnose my problem, when installing Feisty from the Alternate install disc, it had me enter in something like "except 0x800 - 0x8ff" because it said my PCMCIA slot was conflicting with the CD drive and it couldn't read the disc.  After that the installation went fine.  I don't have any other PCMCIA devices to try out on the laptop to see if it is an issue with the slot.

If I were to try the ndiswrapper method do I first need to uninstall the drivers offered here?  If so, how do I do that?  Any help would be much appreciated as I am on a mission to make Ubuntu the main operating system on my and my wife's home computers and move Windows to the secondary position.

Thanks!

It would be a good idea to remove the firmware before trying ndiswrapper. Look in /lib/firmware and the folders inside it and delete the bcm43xx_*.fw files.

A question for anyone who knows:

I'm always wary of executing recursive delete commands, but if I were to [COLOR="Red"]rm -r Specific_Filename.fw[/COLOR] for each file installed by this script, is that likely to harm the system as a whole? That is, recursively deleting each specific firmware file installed by this script - by name - from a script, would I be likely to damage my (Feisty, Edgy, Dapper, etc.) install?

---

### Post by scohar70 on 2007-05-05
Hallelujiah!!  After six long hours, this was the first thing that ACTUALLY WORKED!!!

THANKS!

Now, I noticed in the README that this limits me to 11 Mbps.  Does anybody have an "easy" answer to getting to 54 Mbps?

I'm using a Linksys WPC54G PCMCIA card on my Dell laptop.

---

### Post by velozoom on 2007-05-05
After struggling with Edgy and wireless for a long time, I installed Feisty this morning, ran the script, set up my network parameters, and blamo i had wireless.  So first off, THANKS for the firmware!!!!!  

The only issue is that I am limited to 11mbps.  iwconfig won't let me add any more speed.  from earlier posts it looks like I may be SOL on this, but just in case......I have an HP dv9000z laptop with a broadcom BCM4310 UART wireless card (integrated).  Has anyone had any luck getting this piece of [insert appropriate euphemism for fecal matter here] card to work at speed shigher than 11?  

Grazie.....

---

### Post by trivix on 2007-05-05
> **kyle_fransham said:**
> Thanks a ton for this howto darkNoob.  My Broadcom 4306 internal card now works perfectly.  I can even connect to the (unencrypted) network at work, something I couldn't do using edgy and ndiswrapper.  

I  don't know if this is important, but for those of you that have messed around with ndiswrapper previously, you may want to do the following, which I did before attempting this howto:

```

sudo aptitude remove ndiswrapper-utils-1.9

```
(change 1.9 to 1.8 if you're using edgy)

```

sudo gedit /etc/modprobe.d/blacklist

``` 
if there's an entry for bcm43xx, comment it out

Reload the bcm43xx module: 
```

sudo modprobe bcm43xx

```

Now proceed with the guide and everything should work.

Wow, I was having problems activating my wireless card with ndiswrapper... then I tried using the script by dark_n00b and i still didnt get anything.  Follow these instructions _first_ and you should be on your way to some sweet wireless.  You guys are chill!

---

### Post by hypersire on 2007-05-06
Took me all of 1 minute, didn't even have to reboot!

Thank you very much sir!

---

### Post by DarkN00b on 2007-05-06
Excellente! I'm glad it worked for y'all.

---

### Post by dthomsen on 2007-05-06
Worked awsome!  One thing, if you screwed around with the "manual" configuration set the wireless back to "Roaming" and remove and re-insert the card.  Then config the card using the icon at the top of the desktop.  I wasted a few hours becuase of that.

---

### Post by Tael on 2007-05-06
I used this, but I don't think it worked. Then again, I'm using Xubuntu Dapper Drake, so I suppose that would have an impact on it. :/

---

### Post by dazcon5 on 2007-05-06
.
Okay this did not work at first, I had forgotten that I blacklisted the module while trying other solutions.  After re-enabling the module everything worked GREAT!!!!!
I am working on a Dell Latitude D600 using the Dell 1370 MiniPCI card.

Many thanks for this solution.  Thanks to all the gurus who take the time to make it easy for us noobs to enjoy a tasty fresh Feisty install


:)

---

### Post by frediship on 2007-05-06
i have no clue what i am doing/ doing wrong
but this is what i typed in the terminal 


[SIZE="2"]
james@james-laptop:~$ cd /home/james/bcm43xxfirmware
james@james-laptop:~/bcm43xxfirmware$ sudo ./bcm43xxfirmware.sh
sudo: ./bcm43xxfirmware.sh: command not found[/SIZE]

---

### Post by Doneko on 2007-05-06
Thank you for saving me hours on getting my Linksys card working! This is my first day in Linux world, I guess I timed my conversion right! :-)

---

### Post by DarkN00b on 2007-05-06
> **frediship said:**
> i have no clue what i am doing/ doing wrong
but this is what i typed in the terminal 


[SIZE="2"]
james@james-laptop:~$ cd /home/james/bcm43xxfirmware
james@james-laptop:~/bcm43xxfirmware$ sudo ./bcm43xxfirmware.sh
sudo: ./bcm43xxfirmware.sh: command not found[/SIZE]

Type ```
./]installbcm43xx.sh
```

That is the correct install command.

There should now be no reason to use the sudo command because it is included in the script.

---

### Post by dionisi on 2007-05-06
ok here i am hope that someone helps me. i have a fiesty fawn kubuntu installed on my hp pavillion dv 9025ea
that has a WLAN Broadcom 802.11 wireless card. Kubuntu recognizes me everything from the first installation, but not my wireless card. As i have done with others linux distributions try to use ndiswrapper to get it work. The result was nothing i have followed all the possible guides presented in this forum and even in others but nothing. Tried even with the blacklisting method even that didnt turn on the blue light of my card. The problem is that i tried this method installing the script made by darknoob and finally smth changed, the famous command

> iwconfig

shows me the wireless card ( smth that before didnt even happen), but the blue light still dont appear. After that the KNetworkManager finally recognized the the wireless card with the name    eth1   and when i entered the essid of my network it starts doing smth but stopped at 28 % doing the procces: Configuriing the device....
I repeat all this was done with the light blue off. Tried to enable it from the network manager but i couldnt get it enabled because after the command enable it still remain disable. So kubuntu recognize the card (after doing what darnoob said) but cant get it enable, what i think is that i have messed up everything following too many guides , installing and disinstalling to many ndiswrapper and many drivers that now i cant get it work. 
My card is bcm4310 based. 
After all this huge post what i ask is that step by step you ask me what do u want to know , ex. what comands should i do and stuff like that and i give u the information so u can find the problem if there is any.
thanks

---

### Post by DarkN00b on 2007-05-06
First of all, I know nothing about KDE so I'll stick to things that should work independently of your DE.

That blue light may never work, but just to be sure, what do you get when you type in ```
iwlist eth1 scan
```

Also, try these two commands to take down the connection and then bring it back up:

```
sudo ifdown eth1

and

sudo ifup eth1
```

Once you've done that, try configuring your card again. This is because you need to initialize your card so the firmware can be loaded into it.

---

### Post by Jonathan Harford on 2007-05-07
Alas, the script did not work for my HP V5101US laptop.

Well, that's not entirely true. After running the script, my WPA router started to show up under knetworkmanager and I was able to connect to it. AND I was even able to get to google.com!

But moments later -- though nothing had apparently changed -- I couldn't get to a single website. Looking at my System logs, I saw a lot of "CCMP: received packet without ExtIV flag"  errors had begun to crop up.

To make matters worse, as soon as I had installed the firmware, my mouse started acting all flaky (as described here: [https://bugs.launchpad.net/ubuntu/+bug/84119)](https://bugs.launchpad.net/ubuntu/+bug/84119)). When I added "i8042.nomux=1" to GRUB, this flakiness went away, but the mouse and keyboard started to hang at random.

I feel like I'm so close! Advice?

---

### Post by scalvin on 2007-05-07
:) Yes this worked for me. I'm not sure if the card is working at full speed but good enough. These forums need a crew a folks like DarkNoob, he really is what its all about.

---

### Post by victory2007 on 2007-05-10
I got my blue light to come on but past that I cant connect to the internet.  I have used this before with this same computer but with a clean install it just doesnt seem to want to work.  Ubuntu 6.10 with a broadcom 4318.

---

### Post by Nrbelex on 2007-05-11
So aside from removing the bcm_xxx files from lib/firmware, how do you uninstall whatever is installed by this script?

~ Brett

---

### Post by bmartin on 2007-05-11
Strangely, I didn't need to do any of this in Sabayon; my wireless worked without any tinkering. This process worked beautifully. Thanks a lot!

My computer is a Compaq V5101US with a built-in Broadcom 4318 chipset and hardware switch. Both the hardware switch and the wireless chipset are function using the script. To enable the chipset after installing the firmware, use **ifdown** and **ifup**.

---

### Post by DarkN00b on 2007-05-12
> **Nrbelex said:**
> So aside from removing the bcm_xxx files from lib/firmware, how do you uninstall whatever is installed by this script?

~ Brett

That is half of the removal. **You need to remove the same files from the folders contained within that directory.** The script doesn't install anything except the *.fw files so once you remove them everything is gone.

---

### Post by whitetrash on 2007-05-12
Awesome guide.

Worked perfect for me (running a Compaq Presario R4000 Notebook). I have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

:guitar:

---

### Post by jtarp on 2007-05-12
I've been reading threads and trying this-that-and the other for two days...This is the solution! I am up and surfin'!   :)  
Thanks
I'm using a Linksys WMP54GS PCI adapter w/Speedbooster (Broadcom BCM4306).

---

### Post by whoKnew on 2007-05-13
Thanks for posting this!

I just have a quck  question: I am a complete linux/ubuntu newbie, and i want to try and set up wireless as painlessly as possible. Do you think this method will work for Dapper, too? I want an opinion before I go card shopping. Much appreciated. :: wK

---

### Post by DarkN00b on 2007-05-13
> **whoKnew said:**
> Thanks for posting this!

I just have a quck  question: I am a complete linux/ubuntu newbie, and i want to try and set up wireless as painlessly as possible. Do you think this method will work for Dapper, too? I want an opinion before I go card shopping. Much appreciated. :: wK

This should work fine with Dapper. It really is meant to be for people who are not using Feisty because this firmware is available in the repos (I think). This would be of the most use to pre-Feisty users.

I used this on a Linksys wpc54g version 3.0 card and it works like a charm.

---

### Post by fugative on 2007-05-14
OK, sorry to spoil the party but it's not really working for me. I got a zv5000 with 4301 802.11b built-in. the little install worked a treat and my wireless light came on .... then off... then on again. I got it to pick up my ad-hoc network but as i try to connect the light goes out. tried configuring with iwconfig but no joy. 
device shows as eth1.

any help would be appreciated as I had trouble before with this machine. I had edgy on it and ndiswrapper handling the broadcom but it made the machine really sluggish so i had to reinstall 'doze.
trying to go complete ubuntu but this machine won't give up the Gates.

cheers

---

### Post by kowkary on 2007-05-14
I have a HP Pavillion zv6000 and when it goes ndiswrapper -l it comes up with bcmwl5 install but not valid
I can't to work is there any more I can do I followed the wifiDocs Broadcom BCM4311 speckces

---

### Post by kibmcz on 2007-05-15
Worked on my Dell Latitude C610 that has a Dell True Mobile 1370 installed.

Thanks

---

### Post by hoistyler on 2007-05-15
I don't know if it really works.. It looks like its working for me (I can control my wireless with the switch!) but it appears to be unable to connect to the home wireless network (which I can connect from Windows XP). Instead of showing my home network ( its set to open by the way), it shows some network named "bcmXXXX" where Xs are a bunch of numbers. Since I can't see that network on Windows XP, I think I didn't set up my network properly. 

My guess is that its behaving as an access point and detecting itself.. (maybe not)

My laptop is presario v3000 and its got bcm4311 built in.

---

### Post by liberalist on 2007-05-15
I followed your steps, but could not install the firmware on an iMac Intel. When entering the line ./installbcm43xx.sh , the Terminal goes back to the prompt and never asks for a password. Does this mean that the firmware is installed? Either way, I still cannot connect to the internet.

Please help. Thank you very much in advance.

---

### Post by HybridGhost on 2007-05-15
Ok, what am I doing wrong here...?

I know in windows you go C: Or D:  to change directorys, how do I do that with Ubuntu?

I open the terminal and I write what I think should work, I've tried SEVERAL different variations...



sudo home/jory/bcm43xxfirmware/./installbcm43xx.sh
sudo home/jory/./installbcm43xx.sh
sudo ./installbcm43xx.sh

I just can't seem to :

A) Get it right.
B) I really just don't know what I'm doing.

Regards,

---

### Post by bmartin on 2007-05-15
> **kowkary said:**
> I have a HP Pavillion zv6000 and when it goes ndiswrapper -l it comes up with bcmwl5 install but not valid
I can't to work is there any more I can do I followed the wifiDocs Broadcom BCM4311 speckces
I wouldn't try this method without uninstalling the ndiswrapper stuff first. I've also tried the ndiswrapper method with no luck, but after uninstalling ndiswrapper and using this method, I haven't had any problems. My computer has a hardware switch, as well, and everything works perfectly with this method.

---

### Post by bmartin on 2007-05-15
> **HybridGhost said:**
> Ok, what am I doing wrong here...?

I know in windows you go C: Or D:  to change directorys, how do I do that with Ubuntu?

I open the terminal and I write what I think should work, I've tried SEVERAL different variations...

Assuming you used Firefox and the GUI extraction method, the files should be on your Desktop.

cd ~/Desktop/
./installbcm43xx.sh

~ stands for your home directory. If you type in **pwd** after using **cd ~** command, it'll tell you where your home directory is located. In UNIX/Linux, everything is mounted to the same file structure. You can find out what is mounted and where it's mounted by typing **mount** in the terminal.

---

### Post by HybridGhost on 2007-05-15
Nice, that helped a lot :)

Now I'm at the directory "~/Desktop/bcm43xxfirmware$. ./"

I now type "./installbcm43xx.sh" and it just goes down one line, doesn't say it's done or worked or anything?

Just making sure that's what it is supposed to do.

Regards,

---

### Post by bmartin on 2007-05-15
Yep, it simply copies some files for you. If there's a light on your wireless device, it should come on. If not, try doing the following two commands, or restart your computer if all else fails:

```
sudo ifdown eth1
sudo ifup eth1
```

Where eth1 is the name of your wireless device. If you're not sure which one it is, try using **iwconfig**. I recommend looking up some basic terminal instructions if you plan on becoming a Linux power user, but it's not necessary if you're planning on using the GUI for most things.

---

### Post by bunoire14 on 2007-05-16
Dude,

you just saved my life, this is a great fix for a annoying bug, thanks very much, very easy to install especially for us NEWBIE linux users.

Once again thanks alot
:guitar: :) :KS

---

### Post by dcwilliams on 2007-05-16
It worked for a while.

I have a Compaq Presario R3000, and was able to get the wireless up and running. I was able to connect to my DLink 2000AP WAP and surf the internet, get updates etc.

The installation did not work the same way it did in windows. I have a button on the laptop that turns the wireless card on and off. When the laptop ran windows the blue light used to indicate if the wireless card is activated or not. I could push a button to activate or deactivate the wireless card, and it would turn on or turn off the light as an indicator. Running Ubuntu, the button does not work. When I first installed the driver, I could tell that it was working because the light turned on. However, since then, it does not turn on fully. When accessing the network the light flickers as if it were a TX/RX traffic indicator, the weird thing is, the light didn't work all the time, it always flickered when connecting to the WAP, but not always when surfing the internet or downloading updates.

Then yesterday I booted up, I was unable to connect to the network. I use WEP to secure the network and I am prompted to enter a password to connect, but only have a few seconds to do so before the password screen disappears. Once it disappears, there is no way to get it back. There is a spinning icon in the tray that shows it is trying to connect, and that will run for quite a while before it times out. So I tried a manual config of the wireless card to connect to the WAP, by clicking on the spinning icon, it failed, I tried logging out and logging back in, it did not prompt for a password. I tried <CTRL><ALT><BACKSPACE>, it did not prompt for a password. So I rebooted.

Poof, no more wireless card. 

The network icon (which spins when trying to connect or turns into bars when connected), shows no connection, when I click on it, it and wireless has been removed (I can not even manually config). I type ndiswrapper in the console it shows the driver is still installed, but there is no other indicator that I have a wireless card in the machine.

---

### Post by bmartin on 2007-05-16
> **dcwilliams said:**
> The network icon (which spins when trying to connect or turns into bars when connected), shows no connection, when I click on it, it and wireless has been removed (I can not even manually config). I type ndiswrapper in the console it shows the driver is still installed, but there is no other indicator that I have a wireless card in the machine.
That might be part of your problem. If you're using this method, you shouldn't be using ndiswrapper. Try uninstalling it. This method **does not** require ndiswrapper.

---

### Post by DarkN00b on 2007-05-16
> **dcwilliams said:**
> It worked for a while.

I have a Compaq Presario R3000, and was able to get the wireless up and running. I was able to connect to my DLink 2000AP WAP and surf the internet, get updates etc.

The installation did not work the same way it did in windows. I have a button on the laptop that turns the wireless card on and off. When the laptop ran windows the blue light used to indicate if the wireless card is activated or not. I could push a button to activate or deactivate the wireless card, and it would turn on or turn off the light as an indicator. Running Ubuntu, the button does not work. When I first installed the driver, I could tell that it was working because the light turned on. However, since then, it does not turn on fully. When accessing the network the light flickers as if it were a TX/RX traffic indicator, the weird thing is, the light didn't work all the time, it always flickered when connecting to the WAP, but not always when surfing the internet or downloading updates.

Then yesterday I booted up, I was unable to connect to the network. I use WEP to secure the network and I am prompted to enter a password to connect, but only have a few seconds to do so before the password screen disappears. Once it disappears, there is no way to get it back. There is a spinning icon in the tray that shows it is trying to connect, and that will run for quite a while before it times out. So I tried a manual config of the wireless card to connect to the WAP, by clicking on the spinning icon, it failed, I tried logging out and logging back in, it did not prompt for a password. I tried <CTRL><ALT><BACKSPACE>, it did not prompt for a password. So I rebooted.

Poof, no more wireless card. 

The network icon (which spins when trying to connect or turns into bars when connected), shows no connection, when I click on it, it and wireless has been removed (I can not even manually config). I type ndiswrapper in the console it shows the driver is still installed, but there is no other indicator that I have a wireless card in the machine.

What bmartin says is true. NDISwarpper may interfere with this method. If The native Linux firmware and NDISwrapper are trying to connect at the same time you'll probably get a conflict and as a result the card won't work. 

One thing that tells me this might be the case is that you said your blue light came on for a while. This light almost never works with the firmware I've provided here, so NDISwrapper is probably trying to connect and conflicting with this firmware.

---

### Post by DarkN00b on 2007-05-16
> **hoistyler said:**
> I don't know if it really works.. It looks like its working for me (I can control my wireless with the switch!) but it appears to be unable to connect to the home wireless network (which I can connect from Windows XP). Instead of showing my home network ( its set to open by the way), it shows some network named "bcmXXXX" where Xs are a bunch of numbers. Since I can't see that network on Windows XP, I think I didn't set up my network properly. 

My guess is that its behaving as an access point and detecting itself.. (maybe not)

My laptop is presario v3000 and its got bcm4311 built in.

Try typing ```
iwconfig
``` or ```
iwlist scan
``` into a terminal.

That should give you a lot of info about your network, which should help you get up and running. Post here if you need more help, I try to stay around... :)

---

### Post by bmartin on 2007-05-16
> **DarkN00b said:**
> One thing that tells me this might be the case is that you said your blue light came on for a while. This light almost never works with the firmware I've provided here, so NDISwrapper is probably trying to connect and conflicting with this firmware.
Funny you should mention that; I have a Compaq V5101US laptop, which has a hardware switch, much like the one described by dcwilliams, and the light comes on with the firmware you've provided. The hardware switch actually works properly, like it did in Windows. Maybe I'm an exception to the rule, but you might be underestimating the utility of the firmware solution you've provided. The only annoying thing is that I have to press the hardware switch to activate my wireless again every time my laptop comes out of hibernation.

---

### Post by DarkN00b on 2007-05-16
I think that's a regular issue with Ubuntu. Feisty has some hibernate/suspend issues and I've seen posts about problems. Heck, I closed the lid a few times recently on my laptop and I got one of two results:

1. The laptop powered off, and asked for a password on power on -- basically hibernation.

2. Nothing. The only difference was that the lid was closed. LCD stayed on -- no power saving.

Oh well, I still like it better than Windows.

---

### Post by Average_Jake on 2007-05-16
Hello,
Im using Ubuntu Dapper, I had ndiswrapper + windows driver and had it working just fine.  But i wanted to get it working without the windows driver (i hate windows) altogher as my 4306 rev 03 is suppose to be supported.  I ran your script however (after uninstalling ndiswrapper), then restarting but I still do not see any wireless service avaialble.

iwconfig shows: "no wireless extensions"

Please advise...

---

### Post by bmartin on 2007-05-16
The Broadcom chipset requires both the firmware and the kernel module to work.

Try doing the following:
```
sudo depmod -ae
sudo modprobe bcm43xx
```

EDIT: My question was answered. The post has been updated to reflect that.

---

### Post by Average_Jake on 2007-05-16
Yep that did it! (whatever it was) - many thx for your quick reply!

---

### Post by bmartin on 2007-05-16
You're welcome. It was a good guess, I suppose.

One thing to note: you may have to do the modprobe steps every time a new kernel is released. Sorry, but that's how kernels often work. There might also be a place you can put the kernel module's name so that it loads up with Ubuntu every time, bypassing this annoyance; I know how to do that in Gentoo, but not in Ubuntu.

DarkNoob's method is straight-forward and it helped me get this chipset working, whereas I've never known a way that worked before now. My goal is to help as many people get this working as I can. I hope that this solves the problem for some of the people who haven't had luck with this method in the past. Perhaps the script should be amended as follows:

1. ndiswrapper should be uninstalled, if it's in use (requires root).
2. depmod and modprobe should be run after the files are copied (requires root).
3. Optionally, a method to remove the drivers could be included (like checking for $1 = "-r").

DarkN00b, would you please amend your instructions on the first page of this thread to include the steps of removing ndiswrapper (that probably should be the first step) and running depmod/modprobe (should be the last step)? If you want me to write a robust script for you that checks for root permissions and does all of the steps at once, I would be happy to do that for you.

---

### Post by DarkN00b on 2007-05-17
> **bmartin said:**
> You're welcome. It was a good guess, I suppose.

One thing to note: you may have to do the modprobe steps every time a new kernel is released. Sorry, but that's how kernels often work. There might also be a place you can put the kernel module's name so that it loads up with Ubuntu every time, bypassing this annoyance; I know how to do that in Gentoo, but not in Ubuntu.

DarkNoob's method is straight-forward and it helped me get this chipset working, whereas I've never known a way that worked before now. My goal is to help as many people get this working as I can. I hope that this solves the problem for some of the people who haven't had luck with this method in the past. Perhaps the script should be amended as follows:

1. ndiswrapper should be uninstalled, if it's in use (requires root).
2. depmod and modprobe should be run after the files are copied (requires root).
3. Optionally, a method to remove the drivers could be included (like checking for $1 = "-r").

DarkN00b, would you please amend your instructions on the first page of this thread to include the steps of removing ndiswrapper (that probably should be the first step) and running depmod/modprobe (should be the last step)? If you want me to write a robust script for you that checks for root permissions and does all of the steps at once, I would be happy to do that for you.

That would be great bmartin. I really just knocked this together for a quick and dirty install. If you could do that then I will include it in the download (crediting you of course :) ). In the meantime I will make the recommended amendments. Thanks for the offer and the help in this thread. I really don't know a heck of a lot about shell scripting so I kept it simple. 

I don't know if you read all the way through this whole thread but I asked in an earlier post about recursively removing the firmware from a command line via ```
sudo rm -R bcm43xx_X.fw
``` where X is the rest of the filename. Basically, I want to have a script recursively remove all the BCM43xx files by specifically listed filename. I haven't done this because I am afraid of the script possibly following symlinks and screwing something up. Do you have any idea how safe/dangerous this might be?

---

### Post by dcwilliams on 2007-05-17
> **DarkN00b said:**
> Try typing ```
iwconfig
``` or [iwlist scan[/code] into a terminal.

That should give you a lot of info about your network, which should help you get up and running. Post here if you need more help, I try to stay around... :)


Removing the ndiswrapper seems to have fixed the flakeyness, the wireless light is on (or off), it no longer flickers, and I can turn the light on or off with the button. I still can not connect to my network (via wireless) though.

Clicking System > Administration > Network shows wireless and wired connections (both set to roaming mode). Clicking the network connection icon in the task bar gives wired connection and manual configuration (when wireless is working, wireless appears in the list).  If I manually config select wireless and enter  the SSID of my WAP and enter my WEP key the network connection icon does not connect.  

dave@Cocytus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:0D:88:BE:BA:6B   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dave@Cocytus:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


dave@Cocytus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:0B:21:B8  
          inet addr:192.168.0.11  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe0b:21b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1396795 (1.3 MiB)  TX bytes:187271 (182.8 KiB)
          Interrupt:17 Base address:0xa800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:61:D3:4F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256 (256.0 b)  TX bytes:20612 (20.1 KiB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1700 (1.6 KiB)  TX bytes:1700 (1.6 KiB)

---

### Post by DarkN00b on 2007-05-17
I can't imagine why it won't connect. If you temporarily disable WEP, does it connect? Maybe "Password _t_ype" needs to be set to ASCII? It is 1 in the morning here and my brain is working kinda slowly. :)

I'll sleep on it and check back in the morning, maybe it'll make more sense then.

---

### Post by dcwilliams on 2007-05-17
Reconfigured WAP to 
Authentication: Open System (was Shared Key)
WEP: Disabled

No difference.

Dave

---

### Post by bmartin on 2007-05-17
In regard to the first step, I got an error when removing only ndiswrapper-common; it stated that the ndiswrapper-utils-1.9 package would be broken. You might want to remove both of them at once.

I attached the script. I added in some comments so you know what it does, and it addresses the possibility of following symlinks. The find command doesn't follow symlinks; that's it's default behavior, but I put in the "don't follow symlinks" flag anyway.

The method of installation is the same; simply run the script. If you add a -r flag, it'll remove the firmware, but it doesn't currently remove the kernel module. A message is displayed to the user after installation, describing how to remove the firmware. Various messages are displayed during installation, and the user is notified of which files are being removed during the uninstall; they will be only bcm43xx_ files that end in .fw.

Also, despite the fact that you used aptitude in your instructions and I recommend that everyone use aptitude and never touch apt-get, I used apt-get in the script because that's what I thought people would be more familiar with. I though you might want to make that change; having the script use aptitude should only affect people that normally use aptitude; apt-get users won't benefit from or be harmed by it.

---

### Post by bmartin on 2007-05-17
Try using the wifi-radar program (install with **sudo apt-get install wifi-radar** and see if your results are any better. Your Broadcom device seems to be detected and working.

---

### Post by bung33 on 2007-05-17
I tried using ndiswrapper so many different times, but without success. This approach worked the first time. I only had to restart my computer one time, connect to the network, and then scream! It works! Thanks so much... =D>

---

### Post by dcwilliams on 2007-05-17
> **bmartin said:**
> Try using the wifi-radar program (install with **sudo apt-get install wifi-radar** and see if your results are any better. Your Broadcom device seems to be detected and working.

Thanks! Wifi Radar seems to have fixed it. 

I was dubious at first, the Wifi Radar saw my two WAP (I have an old 802.11ab and a newer 802-11bg), the ab WAP's bars in Wifi Radar would intermittently blink, turning on for a second and then off for much longer periods, the bg WAP showed no signal (bars were white). However, I am able to connect to both WAPs using WEP (without having to reconfigure anything).

Of course, my tray icon (Network Manager applet 0.6.4) is now causing problems. Once I connected with Wifi Radar, Network Manager immediately picked up the connection and asked me to connect. I tried connecting and it disconnected my already working connection. 

I disconnected my network cable, and used Wifi Radar to reconnect to the network, and Network Manager is indicating there is no network connection (two computers with an X between them).

If I right click on Network Manager and select Connection Information it says:
Interface: Wireless Ethernet (eth1)
Speed: 11 Mb/s
Driver: bcm43xx
<all addresses, IP, broadcast, mask, route, dns>: 0.0.0.0

Wifi Radar is showing my IP address is 192.168.0.5

If I remove Network Manager will that break anything? Is there a signal strength or connection speed indicator applet for Wifi Radar? Is there a way to tell if I am connected at 54 or 11Mb/s?

---

### Post by bmartin on 2007-05-17
> **dcwilliams said:**
> If I right click on Network Manager and select Connection Information it says:
Interface: Wireless Ethernet (eth1)
Speed: 11 Mb/s
Driver: bcm43xx
<all addresses, IP, broadcast, mask, route, dns>: 0.0.0.0

Wifi Radar is showing my IP address is 192.168.0.5

If I remove Network Manager will that break anything? Is there a signal strength or connection speed indicator applet for Wifi Radar? Is there a way to tell if I am connected at 54 or 11Mb/s?
I'd try removing Network Manager; I've seen it recommended on other forums because it causes problems in certain cases. As far as the speed goes, 11 Mb/s seems to be the limit with this method; Network Manager is correct. I don't know what the speed limitation is due to; probably either the firmware or the bcm43xx module (my guess would be the latter, but I don't know much about the module itself).

---

### Post by JSThePatriot on 2007-05-17
Hey guys!

I just wanted to post my success with this firmware upgrade! I really appreciate you DarkN00b!! [-o< (Answer to prayer!)

One thing I would like to mention. If you find that after restarting your machine (PCI installation), your internet still isn't working. I saw in another forum to restart twice, and that is what worked for me!!

I GREATLY APPRECIATE YOU TAKING THE TIME TO DO THIS FOR EVERYONE!!
JS

---

### Post by bmartin on 2007-05-17
This message is to everyone who has blacklisted the bcm43xx module, which normally loads up with Ubuntu:

If you've used these instructions to get your Broadcom wireless device to work **and** you edited your **/etc/modprobe.d/blacklist** file and added **blacklist bcm43xx** to it, you should remove that line, considering you're now using that module. Otherwise, you might start having wireless problems (e.g. after a kernel upgrade).

You can check for that line in the file by typing the following in a terminal:
cat /etc/modprobe.d/blacklist | grep bcm43xx

If the output is empty or the line starts with a pound sign (#), you're all set. If it simply says **blacklist bcm43xx**, it's in your best interest to remove that line or comment it out.

---

### Post by DarkN00b on 2007-05-17
bmartin -

Your script has been uploaded with the firmware and is now available. I am amending the original post to reflect this. Thanks for your help.

---

### Post by DarkN00b on 2007-05-17
> **dcwilliams said:**
> Thanks! Wifi Radar seems to have fixed it. 

I was dubious at first, the Wifi Radar saw my two WAP (I have an old 802.11ab and a newer 802-11bg), the ab WAP's bars in Wifi Radar would intermittently blink, turning on for a second and then off for much longer periods, the bg WAP showed no signal (bars were white). However, I am able to connect to both WAPs using WEP (without having to reconfigure anything).

Of course, my tray icon (Network Manager applet 0.6.4) is now causing problems. Once I connected with Wifi Radar, Network Manager immediately picked up the connection and asked me to connect. I tried connecting and it disconnected my already working connection. 

I disconnected my network cable, and used Wifi Radar to reconnect to the network, and Network Manager is indicating there is no network connection (two computers with an X between them).

If I right click on Network Manager and select Connection Information it says:
Interface: Wireless Ethernet (eth1)
Speed: 11 Mb/s
Driver: bcm43xx
<all addresses, IP, broadcast, mask, route, dns>: 0.0.0.0

Wifi Radar is showing my IP address is 192.168.0.5

If I remove Network Manager will that break anything? Is there a signal strength or connection speed indicator applet for Wifi Radar? Is there a way to tell if I am connected at 54 or 11Mb/s?

According to the creators and maintainers of this firmware, you are limited to 11 Mb/s max at this time.

---

### Post by bmartin on 2007-05-17
> **DarkN00b said:**
> Thanks to [COLOR="Red"]bmartin[/COLOR] and his (her?) excellent suggestions to improve this whole process. See them at post #118 of this thread.
I'm male, not that it really matters. My goal is to get as many of those Broadcom chipsets working as possible, since I know what a pain it can be. I've posted a link to this page on other forums and in other threads with the hope that others' wounds can be healed, as well.

You didn't mention that using -r will remove the firmware, but I guess people will find out when they run the script. I was leery about removing the module.

Feel free to look through the script and see what it does. I've added comments for people who'd like to learn more about the process (i.e. what the individual steps are). If the script causes problems for you or you have a suggestion, please post it on this thread, or if you know BASH scripting, go ahead and modify and post it. I won't pretend that my work is flawless.

[QUOTE=DarkN00b]According to the creators and maintainers of this firmware, you are limited to 11 Mb/s max at this time.[/QUOTE]
I tried manually setting it to 54Mb/s; it stopped functioning immediately. The ndiswrapper is much more painful, but for those who need 5x the speed, it might be necessary. I use my laptop exclusively for WAN exclusively, so it's a non-issue for me.

---

### Post by krisbowen on 2007-05-18
worked for me but only enables 11 mbps connection on a 802.11b/g router.

---

### Post by alienseer23 on 2007-05-18
cool, I need to try this on my laptop...just wanted to say thanks in advance!

---

### Post by whoKnew on 2007-05-18
so..i tried the above instructions and i think i've  gotten it half right...

the problem now being that when i plugin my new linksys card (wpc54g), neither of the two lights go on, and i have a sinking feeling that my computer doesn't really respond to the card in general.

following the instructions gave me this:

> copying firmware...
cp:cannot stat 'bcm43xx_*.fw': No such file or directory  
cp:cannot stat 'bcm43xx_*.fw': No such file or directory
The Broadcom firmware and kernel module have been installed. You may need to restart your computer.

which gives me hope. but...the card is still not responding. and there is no card or wireless options in the networking menu.

amazingly newbie-ish question: would this have something to do with my dhcp server? i just upgraded to edgy from the alternate install cd and opted not to configure the server during the install, both because i don't really know what i'm doing and because i didn't have a connection to begin with.. could this be the problem? also..since i'm completely new to this -- how would i go about doing that? 

sorry to pester you with a newbie crisis :) but i would love nothing more than to abandon my windows pc if i could go wireless on my linux box.

thanks for your help + patience. :: wK

---

### Post by bmartin on 2007-05-19
The script and the firmware (.fw files) have to be in the same directory. Did you download my script? I'm gonna remove it from that post. You need to use the steps on the first page.

---

### Post by whoKnew on 2007-05-19
ok just to verify,

the script file is installbcm43xx.sh ?

if that's the case, then the script and firmware files are located in the same directory; it was a self-extract.

---

### Post by bmartin on 2007-05-19
Are you doing this from a terminal or by clicking on the script? You should be in the same directory as the script when it executes. It assumes the files are in the current directory. If you double-click on the file and select "Run in Terminal", this also works, but you should **NOT** simply select run, as the prompts won't be displayed when sudo is used and the program will hang. I altered the script so that it will display graphical prompts if it isn't run from within a terminal, but it isn't published yet.

---

### Post by whoKnew on 2007-05-19
the first few times i tried the instructions on the first page, i used a terminal.

after reading your last post i tried the double-click route. i got messages that the firmware was being copied ("copying firmware..."), and then the window closed automatically without any sort of conclusionary statement.
i took a screenshot just in time if you'd like to see the message.

would  following the instructions on the first page  cause me to be in the same directory as the firmware when the script runs by default?

the command i used in the terminal  was:

> /home/username/bcm43xxfirmware/installbcm43xx.sh

followed by:
> sudo depmod -ae
sudo modprobe bcm43xx
as instructed on the first page.

i'm just frustrated because i feel like the firmware has been installed successfully a number of times by now, and i'm not sure if there is some other problem/reason this may not be working (and knowing my luck..it's probably the latter).

is there any file or terminal messages i could show you to give more info?

thanks for your help.

---

### Post by bmartin on 2007-05-19
You're welcome. If you type the bold command into a terminal, you should get output similar to the following. If you don't, the firmware files weren't copied for some reason:

$ **ls -l /lib/firmware/bcm43xx_***
-rw-r--r-- 1 root root  3504 2007-05-19 00:26 /lib/firmware/bcm43xx_initval01.fw
-rw-r--r-- 1 root root    16 2007-05-19 00:26 /lib/firmware/bcm43xx_initval02.fw
-rw-r--r-- 1 root root  3504 2007-05-19 00:26 /lib/firmware/bcm43xx_initval03.fw
-rw-r--r-- 1 root root    16 2007-05-19 00:26 /lib/firmware/bcm43xx_initval04.fw
-rw-r--r-- 1 root root  2536 2007-05-19 00:26 /lib/firmware/bcm43xx_initval05.fw
-rw-r--r-- 1 root root   248 2007-05-19 00:26 /lib/firmware/bcm43xx_initval06.fw
-rw-r--r-- 1 root root  2536 2007-05-19 00:26 /lib/firmware/bcm43xx_initval07.fw
-rw-r--r-- 1 root root  2536 2007-05-19 00:26 /lib/firmware/bcm43xx_initval08.fw
-rw-r--r-- 1 root root   248 2007-05-19 00:26 /lib/firmware/bcm43xx_initval09.fw
-rw-r--r-- 1 root root   248 2007-05-19 00:26 /lib/firmware/bcm43xx_initval10.fw
-rw-r--r-- 1 root root 21672 2007-05-19 00:26 /lib/firmware/bcm43xx_microcode11.fw
-rw-r--r-- 1 root root 16352 2007-05-19 00:26 /lib/firmware/bcm43xx_microcode2.fw
-rw-r--r-- 1 root root 20088 2007-05-19 00:26 /lib/firmware/bcm43xx_microcode4.fw
-rw-r--r-- 1 root root 22272 2007-05-19 00:26 /lib/firmware/bcm43xx_microcode5.fw
-rw-r--r-- 1 root root  1312 2007-05-19 00:26 /lib/firmware/bcm43xx_pcm4.fw
-rw-r--r-- 1 root root  1312 2007-05-19 00:26 /lib/firmware/bcm43xx_pcm5.fw

---

### Post by DarkN00b on 2007-05-19
Navigate to /lib/firmware and see if the bcm43xx_*.fw files are there. Also look in the kernel folders inside /lib/firmware. If the files are there then they were installed correctly.

EDIT: ^^bmartin beat me to it, and with a better way too. Nevermind. :) The *.fw files should also be located in the kernel directory.

---

### Post by whoKnew on 2007-05-19
check.

i've put that command into my terminal, and it appears that all firmware have been installed...

would this have anything to do with the fact that i haven't configured my dhcp network?
clearly i think i'm just stoking my paranoia right now :)

sigh.

---

### Post by DarkN00b on 2007-05-19
Yeah, if your network isn't configured to assign IP addresses that would cause a problem. :lolflag:

Try setting it up and see what happens then.

---

### Post by bmartin on 2007-05-19
To check if the module's loaded: **lsmod | grep ^bcm43xx**

Any output at all indicates that the Broadcom module is loaded. If it's a removable device, remove it and reinsert it and see if that helps, or try a restart. That has helped for most people. If the light on the device isn't coming on, something's not right. I looked up your wireless device and it seems this method should work for you.

You can grab an IP address with **sudo dhclient**. If you know the name of your device, you can use something like **sudo dhclient eth1** to get the IP address. You can use **iwconfig** to ensure that your device is detected and find out what the device name is.

This method worked great for me. I have no wireless hiccups. I've been playing Unreal Tournament in Wine for hours without a problem. And to top it off, it looks like I'm not quitting my job. They kept  threatening to extend my stay in NJ </3. I had to threaten my boss to get him to stop extending my allocation at a job I hate.

Don't you think it'd be nice for Ubuntu to include some "restricted driver" method to fetch the firmware? If it simply can't be done, Automatix might be willing to offer the option. Either way, wireless support in Ubuntu is a bit of a setback. With Sabayon, my wireless worked right out of the box. Unfortunately, my emerge world failed miserably. It might have something to do with the 1500 packages installed by default :-(

---

### Post by DarkN00b on 2007-05-19
Thats what comes right after step 5. The card must be reinitialized for the firmware to be loaded.

---

### Post by hakimaki on 2007-05-19
It works initially and then just hangs... HP dv6000...

---

### Post by whoKnew on 2007-05-19
this is weird:

**lsmod grep | ^bcm43xx** gives
> bcm43xx 127252
albeit out of nowhere...

but

**sudo dhclient** gives
> No broadcast interfaces found - exiting.

**sudo dhclient eth1** gives
> SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

and finally, **iwconfig** gives
> lo             no wireless extensions.
irda0            no wireless extensions.
sit0            no wireless extensions.

it seems that my card is simultaneously loaded, but also not detected?
does that make sense?

hmmm maybe it's my pcmcia port?

thanks for being troopers, guys.

---

### Post by qzplx on 2007-05-19
Hello guys...

After i follow the DarkN00b's Instruction, im able to detect wifi, now my cards works like a charm, but i have problem here, i cant connect to my AP, the configuration mode is by enabling WPA and TKIP, after i insert manually the configuration from network manager its nothing happening, and i still cannot connect to my ap, after i modified the AP configuration into  "broadcast ssid" now my Wifi can see the AP, but still cannot connect...

Is there any suggestion ?

Appreciate for the advise.....

---

### Post by bmartin on 2007-05-19
> **whoKnew said:**
> this is weird:

**lsmod grep | ^bcm43xx** gives
> bcm43xx 127252
albeit out of nowhere...
That means that the kernel module is loaded, which I suspected. That's good. The problem is further down.

> **whoKnew said:**
> **sudo dhclient** gives [...]
**sudo dhclient eth1** gives [...]
These tell us something's wrong, but not what.

> and finally, **iwconfig** gives [...]
The firmware is installed correctly and the module is loaded. I've verified that these drivers are the correct ones for your device. It could be the PCMCIA port, but it's unlikely.

There are a couple things left to do, I suppose. Go to System > Administration > Network and see if your wireless connection is listed there. If it is, the box next to it should have a check mark in it. 

If you don't see anything there, try looking for the Broadcom device using the **lspci** or **lcpcmcia** commands. If it's not listed under one of those two programs, it isn't being detected at all, and that's the main problem. You tried any other wireless cards in your PCMCIA slot to see if they work?

---

### Post by bmartin on 2007-05-19
qzplx,

Have you followed the instructions for setting up wpa_supplicant [here]("http://ubuntuforums.org/showthread.php?t=318539"). WPA requires some extra steps. After you set your WPA stuff correctly, try going to System > Administration > Network and disabling/reenabling your wireless device.

---

### Post by whoKnew on 2007-05-19
so at first i thought it could be my pcmcia port because i'm using a really old ibm thinkpad (used) that i just bought for a song. but, i tried both lspcmcia and lspci commands and they detected the card, although **lspci** detected the card as:

> 2:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface , which kind of surprised me because i thought it would be listed as Broadcom instead. I shuffled the card in both pcmcia slots and managed to get the same reading. phew!

The problem still being, though, that under System > Admin > Networking there is no network connection there. The only network listed is a dialup modem connection which hasn't yet been configured.  also, the card still won't turn on. 

when i try **sudo dhclient** again it still gives me "no broadcast interfaces found - exiting", but also "There is already a pid file /var/run/dhclient.pid with pid0."   i'm just wondering what this means, as an aside.

i tried **sudo dhclient[/B with [B]lo, irda0, and sit0** as these were the listed using **iwconfig**, and got > No DHCPOFFERS received at the end of it all. granted, i don't even know if that would be a logical step to take, but i'm just trying to learn as much as i can from command line output right now.

this is the first wireless card i've tried using in this slot (i just got the computer),so i suppose i could return it within the next few days and try a different card? i just feel like the wpc54g card has the most support on these forums so it's the best bet. it could be a defective card, but..i think that's kind of unlikely.

would this have anything to do with the fact that i just upgraded to edgy with the alternate install cd? am i missing some important files/drivers/etc?

thanks again for all the help.

---

### Post by whoKnew on 2007-05-19
i also just want to verify if these cards should work right out of the box?
i only ask because they do come with windows-only installation software, and some part of me is wondering if there is any kind of similar activation/installation procedure for ubuntu. no? just unwrap, plug in, and go?

supplmentary:
the dude who sold me the laptop included a linksys WUSB54GC card. would the setup process be similar for this card, too? i haven't looked into it because i only have one usb port and wanted a pcmcia card instead. i probably should have mentioned that earlier, sorry...:)

is there still hope?

---

### Post by DarkN00b on 2007-05-19
> **whoKnew said:**
> so at first i thought it could be my pcmcia port because i'm using a really old ibm thinkpad (used) that i just bought for a song. but, i tried both lspcmcia and lspci commands and they detected the card, although **lspci** detected the card as:

 , which kind of surprised me because i thought it would be listed as Broadcom instead. I shuffled the card in both pcmcia slots and managed to get the same reading. phew!

The problem still being, though, that under System > Admin > Networking there is no network connection there. The only network listed is a dialup modem connection which hasn't yet been configured.  also, the card still won't turn on. 

when i try **sudo dhclient** again it still gives me "no broadcast interfaces found - exiting", but also "There is already a pid file /var/run/dhclient.pid with pid0."   i'm just wondering what this means, as an aside.

i tried **sudo dhclient[/B with [B]lo, irda0, and sit0** as these were the listed using **iwconfig**, and got  at the end of it all. granted, i don't even know if that would be a logical step to take, but i'm just trying to learn as much as i can from command line output right now.

this is the first wireless card i've tried using in this slot (i just got the computer),so i suppose i could return it within the next few days and try a different card? i just feel like the wpc54g card has the most support on these forums so it's the best bet. it could be a defective card, but..i think that's kind of unlikely.

would this have anything to do with the fact that i just upgraded to edgy with the alternate install cd? am i missing some important files/drivers/etc?

thanks again for all the help.

If this card is actually using a Texas Instruments chipset, it won't work with this method. Just because it is a wpc54g card doesn't automatically mean it has a Broadcom chipset. Look on the back of the card and see if you can find the version number and post it here.

> **whoKnew said:**
> i also just want to verify if these cards should work right out of the box?
i only ask because they do come with windows-only installation software, and some part of me is wondering if there is any kind of similar activation/installation procedure for ubuntu. no? just unwrap, plug in, and go?

supplmentary:
the dude who sold me the laptop included a linksys WUSB54GC card. would the setup process be similar for this card, too? i haven't looked into it because i only have one usb port and wanted a pcmcia card instead. i probably should have mentioned that earlier, sorry...:)

is there still hope?

No, the card should not work right out of the box. I was made for Windows and needs a little help to get going on Ubuntu. :) Anyway, if you want to try the WUSB54GC card, search the forums for WUSB54 and you will find other threads related to that adapter.

Just to make sure people know -- Feisty users do not need to use this method because the firmware is available in the repos. You just use "sudo aptitude install bcm43xx_fwcutter" in a terminal. That will install the same thing we are doing here. This howto is mainly for users of Edgy, Dapper and earlier.

---

### Post by bmartin on 2007-05-19
Try this post on [linuxquestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=408685"). We've hit the root of the problem; this isn't a Broadcom chipset. I failed to note that there are multiple chipsets in use; that explains a lot. Sorry about all this confusion, and I hope the link helps.

---

### Post by qzplx on 2007-05-20
> **bmartin said:**
> qzplx,

Have you followed the instructions for setting up wpa_supplicant [here]("http://ubuntuforums.org/showthread.php?t=318539"). WPA requires some extra steps. After you set your WPA stuff correctly, try going to System > Administration > Network and disabling/reenabling your wireless device.

Thanks martin, i will try this steps....

---

### Post by whoKnew on 2007-05-20
ahh..things are making sense to me now!

the pcmcia card is version 2. if that helps.

i'm going to see what searching for the usb card can yield.

thanks guys!

---

### Post by Gateman on 2007-05-20
Just want say that for almost a year and half. Been going crazy trying to get my Linksys card to work.
The card is a WPC54GS with speedbooster. I followed your instructions to the letter.
Now I can roam anywhere in the house. My many thanks to you:p
By the way I am using kubuntu 7.04.
Have good range and no error messages.Again thank you

---

### Post by VVTek20v on 2007-05-20
I have followed all of the steps for this, and my wireless connection shows up in Network Settings, but I can't get an address. When I run 'iwconfig', my access point shows up as "Invalid" I am using a Linksys Wireless Router(WRT54GS).

---

### Post by bmartin on 2007-05-20
Did you try configuring your [WAP]("http://encyclopedia.thefreedictionary.com/Wireless%20Access%20Point") manually? I removed **network-manager-gnome** in favor of **wifi-radar**. I'd recommend the same to you if you're having problems. If you keep both of them installed, it can lead to problems.

---

### Post by VVTek20v on 2007-05-20
How do I remove the Network Manager? I do have wifi-radar already installed.

---

### Post by bmartin on 2007-05-20
sudo aptitude remove network-manager-gnome

Don't use apt-get... use aptitude, always. They can be used in place of one another, but aptitude has many advantages, such as tracing what packages depend on a given package. If you have packages which were installed only to support other packages (e.g., obscure libraries), aptitude can detect when it's safe to remove them. You end up with less software on your computer that you don't need. I've also had less problems installing certain packages with aptitude.

---

### Post by VVTek20v on 2007-05-20
Nothing was removed, so I am guessing it is not the cause of my problem.

---

### Post by whoKnew on 2007-05-20
so now that i realize the source of my problem is that my version 2 card is actually a texas instruments chipset, i think i'm going to return it (it's still under store policy by now) to try and get a version 3 (broadcom chip, yes?).

i'm just wondering:
i couldn't seem to find any indication on the card box of the version number, only the model number, which we've established doesn't always indicate a broadcom chip. does anyone know of a way to tell the version of the card/chipset on the box? is there a number i'm missing? i want to avoid having to blindly buy new cards only to return them once i open the box and find out that they aren't version 3.

thanks!

---

### Post by bmartin on 2007-05-20
Buy a card that works out-of-the-box. People tend to have better luck w/ PCMCIA cards than USB ones. A list of cards known to work can be found [here]("http://ubuntuforums.org/showthread.php?t=370108"). Your best bet is probably a [Linksys]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys") or [Netgear]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") if you can get your hands on one, but be careful; there are a couple that don't work. Be sure to read the comments section carefully for each card.

---

### Post by jazzdaughter on 2007-05-22
Oh man, thanks a ton!  Better wireless capability was the main reason I updated to Feisty, but I was discouraged when it turned out not to work as easily as I thought.  Huzzah for your awesomeness!
=D>

---

### Post by jglen490 on 2007-05-22
Not to step on Bmartin, but please be cautious about blanket statements concerning supported manufacturers or vendors.  Some are generally better than others, but  it's always the the wifi chip that matters most, and as you have seen one given vendor will often use different chips within a given model/version.

Most vendors will not announce the specific chip that they use on their spec sheets because for the larger Windows world, it simply doesn't matter.  The vendor includes the right driver for the chip, on the CD that comes with the card.  That's why if you don't find a card that has an Atheros or other Linux friendly chip, then ndiswrapper, fw-cutter, and other solutions are so important.

---

### Post by DarkN00b on 2007-05-23
You know, I check this thread every time there is a new batch of posts -- just in case I can help. I think it is great that we have helped 80% of the people who try this. This whole mess started with me making a simple script for my own use and then deciding to share. I see grateful people on here every day and bmartin basically taking over support as well as providing that great install script.

I want everyone here to know how much I appreciate your thanks. You guys/gals are the greatest.

[img]http://img186.imageshack.us/img186/1091/yourock1xg3.gif[/img]

---

### Post by bmartin on 2007-05-23
The last script I sent you uninstalls ndiswrapper and performs the depmod and modprobe commands, so those steps shouldn't be necessary anymore.

---

### Post by DarkN00b on 2007-05-23
Gotcha. Fixed.

---

### Post by JBK617 on 2007-05-23
Just made the change to ubuntu and a tough time figuring all the terminal talk out, so on a whim I right clicked on the file installbcm43xx.sh and had it open in terminal and then ran the last 2 lines of code as instructed, restarted by laptop (Dell Inspiron 1501) finally by network showed, entered the info i need and am now on the web.

If I did something wrong or not in the corect order let me know I am new to this

FYI running latest unbuntu 7.04 Fiesty fawn

---

### Post by bmartin on 2007-05-23
It sounds like you did everything right. I'm glad your wireless is working. Congratulations!

The last two steps were unnecessary (as the script now performs them), but they won't hurt anything. I'm glad everything went well.

---

### Post by spvo on 2007-05-23
First off, thanks for all the work you guys have put into this script.  I do have a problem tho.  When I first run the script and restart, everything works perfectly.  I'm able to connect to my wireless network, no problem.  However, the next time I reboot it will not work at all.  If I rerun the script then it works again until the next time I reboot.

Do you have any idea why this is?

---

### Post by bmartin on 2007-05-23
My first guess, and this is a naive one, is that the module being unloaded every time is the cause.

[quote=first page]If you edited your /etc/modprobe.d/blacklist file and added blacklist bcm43xx to it, you should remove it, considering you're now using that module. Otherwise, you might start having wireless problems.[/quote]

I'll try to think of something else in case that isn't the problem, but it's the only thing that comes to mind right now.

You can also verify that it's the problem by typing **sudo modprobe bcm43xx** after a restart; if that fixes it, the problem is that the module's not loading.

---

### Post by spvo on 2007-05-23
This is kind of wierd.  If I have the laptop connected via a cable when it first boots up the bcm43xx driver loads fine, and I can connect to any wireless network I want.  If there isn't a cable plugged in, then the driver doesn't load.

bmartin, the command you gave me does make it work correctly every time.  Do you know of any way to make it always load this driver?

---

### Post by bmartin on 2007-05-23
Did you ever add the module to your blacklist file? See my previous post.

Normally, the module loads up every time after Ubuntu is installed. After you use modprobe, the module should be loaded every time. If you've followed other instructions (e.g. the ndiswrapper method) to get your wireless to work, they probably had you blacklist the bcm43xx module, which is required in this case.

There are other ways to get the module to load up every time, but this is the simplest way.

To see if it's blacklisted, type **cat /etc/modprobe.d/blacklist | grep bcm43xx** into a terminal. If it prints out anything, then the module is blacklisted.

To unblacklist the module:
1. Type **sudo gedit /etc/modprobe.d/blacklist** in a terminal.
2. Look for a line that says **blacklist bcm43xx**. Remove that line.
3. Save the file.

Then the module should load every time.

---

### Post by spvo on 2007-05-23
"blacklist bcm43xx" is not listed in the blacklist file.  Also all the ndiswrapper items have been completely removed.

---

### Post by bmartin on 2007-05-23
Okay, here's the way I'd fix the problem. This manually loads the module using a script that's run at the end of your computer's boot sequence.

Type this into a terminal: **sudo gedit /etc/init.d/rc.local**

At the bottom of that file, insert the line **modprobe bcm43xx**

I'm not sure if that's the correct path to the file. If it's empty, try /etc/rc.local. Can someone else verify this for me?

---

### Post by spvo on 2007-05-23
the /etc/init.d/rc.local file is some sort of script that seems to just run the commands in /etc/rc.local

I tried adding the modprobe bcm42xx command there, but it didn't there was no change.  It still, after booting up, didn't work until I put the command into the terminal.

---

### Post by stchman on 2007-05-23
I used the method laid out by the Edgy and Feisty guide to get 43xx Broadcom wireless working in Ubuntu.

---

### Post by DarkN00b on 2007-05-24
> **spvo said:**
> the /etc/init.d/rc.local file is some sort of script that seems to just run the commands in /etc/rc.local

I tried adding the modprobe bcm42xx command there, but it didn't there was no change.  It still, after booting up, didn't work until I put the command into the terminal.

Try this:

```
gksudo gedit /etc/modules
```

Add "bcm43xx" (without quotes) to the end of that file and save. Reboot and see if that helps. Everything I've read indicates that this should do the trick.

---

### Post by DarkN00b on 2007-05-24
Sorry for the double post, but I felt this needed its own space. For those of you wanting to use some kind of encryption (WEP, WPA etc.), have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=202834"). They seem to be having quite a bit of success over there.

---

### Post by uranous on 2007-05-26
Just perfect, thnx DarkN00b :)

But a noob like me, can't get this step:
> **DarkN00b said:**
> 
3. Open a terminal window and navigate to the directory where you extracted the *.fw files. 
So noobs out there with the same problem, to navigate in the terminal just write:
```
cd ~/AndTheDirectory
```

---

### Post by bmartin on 2007-05-26
> **uranous said:**
> Just perfect, thnx DarkN00b :)

But a noob like me, can't get this step:

So noobs out there with the same problem, to navigate in the terminal just write:
```
cd ~/AndTheDirectory
```
Go to your home directory under the "Places" menu (in Gnome), then go to the Desktop directory. Look for the installbcm43xx.sh file and double-click it. That should run the installer for you. You'll be prompted to enter your password once.

---

### Post by DarkN00b on 2007-05-26
> **bmartin said:**
> Go to your home directory under the "Places" menu (in Gnome), then go to the Desktop directory. Look for the installbcm43xx.sh file and double-click it. That should run the installer for you. You'll be prompted to enter your password once.

It will now. Your last e-mail was flagged as spam by gmail. I got the new script and it is now uploaded.

---

### Post by Factory on 2007-05-26
This worked perfectly on my inspiron 6400. If you're hesitating using this guide, DON'T HESITATE ANY LONGER. This is the only guide I've used so far that has worked.


Now all of use with dell laptops have to do is wait 'till dell releases linux drivers :). Then the fun will REALLY begin.

---

### Post by DarkN00b on 2007-05-26
@Factory:  Is that Ubuntu Bread in your avatar? Can I have the recipe? :D

---

### Post by Factory on 2007-05-26
> **DarkN00b said:**
> @Factory:  Is that Ubuntu Bread in your avatar? Can I have the recipe? :D

Certainly :).

1 CUPS foo
1 CUPS bar
2 CUPS kernel
10 TBSP community
1 CUPS flour

---

### Post by bmartin on 2007-05-26
Recipe for Ubuntu Bread (I'm serious! from [this document](http://www.phptr.com/content/images/0132435942/samplechapter/Hill_ch06.pdf)):

To create this bread you will need the following ingredients:
3 eggs
1 teaspoon of yeast
3/4 cup warm water (40 degrees Celsius)
pinch of salt
1/4 cup oil
1/4 cup sugar
3 to 5 cups flour

First put the yeast in the warm water while you gather the other ingredients. Beat the three eggs in a bowl and save a teaspoon of the egg mixture for later. Add three cups of flour to a big bowl along with the egg, sugar, oil, and salt. When the yeast is bubbly, add it in too.

Knead. If it is crumbly, add water. If it is too sticky, add more flour. The dough should be firmer than your average bread dough to keep its shape.

Cover the bowl with a damp towel, and let the dough rise in a warm place.When it has doubled in size, punch it down, and roll it out into three ropes.

Make the ropes less than one inch thick (2.5cm) so that it will cook evenly. Do this on a large surface. You need a lot of room. Use a bit of oil if things are sticky. Your dough should be somewhat stiff, so this should not be a problem.

You should end up with three ropes that are a little less than three feet long (75 cm). Pinch them together on one end and then braid them.

Take the lowermost rope and place it in between the other two. The middle rope is now the lowest rope, move it into position by bringing it down to where the other rope (lowermost) used to be. Take the topmost rope and place it in between the other two. Take the rope that is now highest and pull it up to its position as topmost rope. Place the lowermost rope in between the two others. You get the picture. . . .

When you have a long braid, snip off the ends, and join the ends to form a circle. Try to join the individual ropes together as best as you can. Place it on an oiled cookie sheet. Take the snipped off bits and form two long strands. Intertwine them together by putting
them side-by-side and holding one end while rolling the other end with the palm of your hand. Stretch this out around the bottom of the big braid and join the ends together.

Cover the kalach with a damp towel and let it double in size (about an hour, maybe less, on a hot day). Brush it with the egg mixture. You should have enough to cover it completely. Cook at 350° Fahrenheit until it becomes dark brown. Let it cool.

---

### Post by jmeridth on 2007-05-27
> **VVTek20v said:**
> Nothing was removed, so I am guessing it is not the cause of my problem.

VVTek20v or bmartin, was there a suggested solution about a PC that got the blue wireless going, the interface setup but couldn't receive an IP?

PC: Compaq Presario C500
Wifi: Broadcom 43xx

Install script worked great, got blue light and the interface is editable in the network manager.

Unable to obtain IP from my Linksys Wireless Access Point.  Is wifi-radar the fix?  Is it in the synaptic package manager?

Thanks for any help.

If it's any motivation, this is the last step for me to get Feisty on a friend's laptop after convincing him to get away from Windows Vista. :)  XP I can support and stand, but Vista is just horrible (personal opinion).

---

### Post by MrLaister on 2007-05-27
worked beautifully and was simple to use!

I like that ubuntu enables the option to pull away from the terminal if you choose to (at least until I become savvy with it :) )

---

### Post by tomco on 2007-05-27
DarkNOOb

You are a star! I have been wrestling with getting wireless on any form of Ubuntu for six months - countless hours!! This just worked

Cheers

---

### Post by GBee on 2007-05-27
I'm a newbie, and found this post brilliant, but....... i get 98%, it says connected, but nothing connects (Firefox) this was with a WPA, so i tried a WEP, connected, good signal, but nothing, disabled all security, still, strong signal, but nothing loading. Any thoughts? Or am i just one of the unlucky ones. As i'm a newbie, do please dumb it down for me!

Thanks in advance

---

### Post by DarkN00b on 2007-05-27
> **GBee said:**
> I'm a newbie, and found this post brilliant, but....... i get 98%, it says connected, but nothing connects (Firefox) this was with a WPA, so i tried a WEP, connected, good signal, but nothing, disabled all security, still, strong signal, but nothing loading. Any thoughts? Or am i just one of the unlucky ones. As i'm a newbie, do please dumb it down for me!

Thanks in advance

You should definitely try to get connected with no encryption first. I'm not sure why you can't connect. I'll post a pic of my Network Settings applet below. That is all that is really needed to get connected once the firmware is loaded. Also, make sure encryption is turned off on your router as well. When you go to enable encryption, have a look at [this]("http://ubuntuforums.org/showthread.php?t=202834").

---

### Post by sinbad#1 on 2007-05-27
I followed your instructions and it seemed to work but my card keeps getting stuck trying to connect to my  wireless network.

sinbad

---

### Post by jmeridth on 2007-05-27
With the help of bcmartin the following post:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

solved my broadcom problems on a friend's Presario C500 laptop.

The firmware solution gave me a blue light and made the wireless card recognized, but I could never obtain an IP view DHCP.

"lspci | grep Broadcom" was:
06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Hope this helps everyone else.

Tip:  once I ran the scanning line (the last one in the post) the blue light came on the laptop.

Thank you bcmartin.

---

### Post by bmartin on 2007-05-27
That method has a lot more steps, but if you can follow them, it's worth it. A lot of my problems went away after using ndiswrapper. I think that the Broadcom firmware works well for a select group of the Broadcom chipsets; however, the ndiswrapper drivers work pretty flawlessly for most of the 43xx series chips.

You called me bcmartin instead of bmartin. How'd you know my middle initial is C? :-$

---

### Post by mwf on 2007-05-27
I was so excited that maybe wireless would finally work with Linux. But...

The install as explained went perfectly. The files are all located in the /lib/firmware directory. The red "X" on the network icon on the top bar is gone. Yet, there is no connection to any outside site, ping doesn't get out either. Very depressing.

For the record, I have a full install (no dual boot) on an HP ze4900 using a Broadcom 4306 Rev 3 built-in wireless card.

The school was going to extend support to Linux but the continuing wireless problems put that idea in the garbage. We are becoming an "all wireless" campus. Only Windows and Mac seem to handle wireless without doing any extra work so thiose are the only two systems that will be official. In fact, without any hardwired ethernet, I am writing this on a Vista machine that did all the networking on its own.

I am a Linux newbie and just can't understand why, in 2007, Linux still has problems with wireless. Does anyone know if BSD Unix variants have the same wireless problems?

Oh well, maybe next year!

---

### Post by bmartin on 2007-05-27
Did you try the ndiswrapper method? It works for more than just the Dell wireless; my compy's a Compaq and it worked on there. Use ndiswrapper and your Windows wireless drivers and you're up and surfing.

---

### Post by DarkN00b on 2007-05-27
I've got another resource for everyone if you're interested. [OVER HERE]("http://bcm43xx.berlios.de/?go=devices") is the compatibility list for the BCM43xx firmware. Check there before installing this firmware, and if you have already tried it check there also. It might not be supported.

---

### Post by Factory on 2007-05-28
> **jmeridth said:**
> VVTek20v or bmartin, was there a suggested solution about a PC that got the blue wireless going, the interface setup but couldn't receive an IP?

PC: Compaq Presario C500
Wifi: Broadcom 43xx

Install script worked great, got blue light and the interface is editable in the network manager.

Unable to obtain IP from my Linksys Wireless Access Point.  Is wifi-radar the fix?  Is it in the synaptic package manager?

Thanks for any help.

If it's any motivation, this is the last step for me to get Feisty on a friend's laptop after convincing him to get away from Windows Vista. :)  XP I can support and stand, but Vista is just horrible (personal opinion).

If your router is using WPA encryption, wifi-radar (for the time being) won't cut it. Just use newtwork-manager-gnome... You can bring it up by using nm-applet.

---

### Post by bmartin on 2007-05-28
If the wireless light comes on with this method, but you're still having trouble, I wrote a script that can install the Broadcom wireless drivers using the ndiswrapper method instead of the firmware. The thread is [here]("http://ubuntuforums.org/showthread.php?t=457371"). Post there if you have any troubles with it.

---

### Post by mossbronson on 2007-05-29
Dark,
This worked well for me. I usa a Gateway nx200 notebook with a PCMCIA USR 5411 card. I tried ndiswrapper with the usr11gv40q driver but I could never get the card to come on. Probably some little something I did not do. I reset every thing to the original bcm 43xx settings and installed the firmware as you said and my card lights came on without even without removing and reinstalling the card or rebooting. It connected right away to my usr wireless router after I entered the PW. Not able to view my shared files yet on my desktop but I think maybe that is a network config issue. Not sure if I can use the Internet over the card yet since I only have Dial-up and I found it impossible to share a Dialup connectionover my home wireless. The only issue so far is my green transmit light on my card is constantly lit up, whereas in M$ xP it only comes on when the card is actually tx or rx  ing. 
Anyway, kudos on the info you have in this forum. I especially like the point-and-click ease of this firmware. Things like this are gouing to make ubuntu a major thorn in M$'s side.

---

### Post by omghax on 2007-05-29
Ah, thanks so much!

I've never understood why people have to install the ndiswrapper thing until my Mom gave me her laptop with a built-in wifi card. After searching just once I found this and instantly worked, I'm amazed. :)

Thanks again, :D!

---

### Post by DarkN00b on 2007-05-30
NDISwrapper works better for some people, this method works best for some people. They choose whatever works for them - this is the Linux way, you as the user are given the power to choose. :)

---

### Post by bmartin on 2007-05-30
> **omghax said:**
> Ah, thanks so much!

I've never understood why people have to install the ndiswrapper thing until my Mom gave me her laptop with a built-in wifi card. After searching just once I found this and instantly worked, I'm amazed. :)

Thanks again, :D!
As one of the proponents of this method over the ndiswrapper method, I'll gladly answer that for you.

I have a Broadcom 4318 chipset built into my Compaq V5101US laptop. While this method gave me some connectivity, I had several issues with it. First of all, my connectivity was flaky; I'd appear to have a great connection to the router, but when accessing the internet, my DNS lookup times were ridiculous. After coming out of hibernation, I had to restart to get my wireless back; ifdown/ifup didn't work and sometimes the network-admin program didn't work, either; modprobe also didn't help.

With ndiswrapper, none of these issues occur. My card also operates at 54Mbps, which I could care less about. My connection is much more responsive. Many people also use ndiswrapper for other reasons, such as a lack of Linux drivers for their wireless chipset. It's also a quick-fix; it works almost every time. You simply need to grab the correct drivers and load them into ndiswrapper.

The firmware method works well for at least 4 chipsets (which can be seen on [this page]("http://bcm43xx.berlios.de/?go=devices"), posted originally by DarkN00b). I've also written my own set of instructions and script for people wishing to use the ndiswrapper method [here]("http://ubuntuforums.org/showthread.php?p=2749951"). It's much simpler than doing all the steps manually, and I wrote a specific script for the people who have Broadcom 43xx chipsets.

My advice to everyone is this: if your chipset is one of the functional ones on the list, use the bcm43xx + firmware method. If it's listed as unstable, use ndiswrapper. If it's not listed at all, try using the firmware first; if that doesn't work, use ndiswrapper. I'll switch back to the firmware method after the necessary support exists.

---

### Post by Kuraboy on 2007-05-30
Hi!

I tried to run the script but I got this error.

```
monty@monty-laptop:~/Desktop/bcm43xxfirmware$ sudo ./installbcm43xx.sh
Password:
Removing ndiswrapper...
./installbcm43xx.sh: line 20: gksudo: command not found
Copying firmware...
./installbcm43xx.sh: line 24: gksudo: command not found
./installbcm43xx.sh: line 25: gksudo: command not found
./installbcm43xx.sh: line 29: gksudo: command not found
./installbcm43xx.sh: line 30: gksudo: command not found
The Broadcom firmware and kernel module have been installed. You may need to restart your computer.
To remove the firmware, run "./installbcm43xx.sh -r" from this directory.
```


what is wrong? is it because that I run Kubuntu 7?

thank you in advance :)

---

### Post by bmartin on 2007-05-30
> **Kuraboy said:**
> what is wrong? is it because that I run Kubuntu 7?

thank you in advance :)
Hahaha yes. You have a good sense of humor. gksudo is a Gnome command. I'm not at home to try this, but there are three ways to fix the problem:

-Install gksudo. It's the Gnome program that displays a graphical prompt asking for your password before performing things that require root permissions. The command to install it is probably **sudo apt-get install gksudo**.

-If that doesn't work, or it requires a lot of stuff that you don't want to download, and you know how to edit scripts, simple modify the script to use the sudo command (it's in one of the variables in the script; you could also replace **gksudo** with **kdesu**) and run the script from the command line. The reason gksudo is used is so people can double-click on the installer instead of running it from the command line. I'll modify the script when I get home to check for the presence of gksudo; if it's not present, I'll have it use KDE's graphical sudo prompt, which is kdesu.

---

### Post by Kuraboy on 2007-05-31
Hi.

thank you for the advice, your script worked (I think) but I got these errors:

```
monty@monty-laptop:~/Desktop/bcm43xxfirmware$ kate installbcm43xx.sh
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

[2]+  Stopped                 kate installbcm43xx.sh
monty@monty-laptop:~/Desktop/bcm43xxfirmware$ bg
[2]+ kate installbcm43xx.sh &
monty@monty-laptop:~/Desktop/bcm43xxfirmware$ sudo ./installbcm43xx.sh
Removing ndiswrapper...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Copying firmware...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
The Broadcom firmware and kernel module have been installed. You may need to restart your computer.
To remove the firmware, run "./installbcm43xx.sh -r" from this directory.

```

did it do what it was intended to do? 

I have another problem, I get blue light which should mean that the wifi card works. (it was red before :) )

It connects to both open channel, and protected with password channel (I have a Fon wireless)

I even tried to connect to a password protected NETGEAR, it just takes too long to connect.

the signal was always 100%

but I couldn't surf or anything, is it because of the errors I got? 

I am really mad at my laptop (HP PADV2140ea), bought it for about 2 months ago and still cant get wireless to work on linux :(

Is it a problem with Ubuntu? Or all other distro?

thank you again :)

---

### Post by bmartin on 2007-05-31
> **Kuraboy said:**
> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
I've never seen that error message before. That happened as soon as your ran the script and not at any other time? I'm guessing there's something wrong with X; that might be related to the Broadcom problem. Were you running something else at the time?

Are you sure you have a Broadcom chipset? After searching Google, I found the wireless to be "Intel 2200BG". If you're convinced that it indeed is a Broadcom, try [this page]("http://ubuntuforums.org/showthread.php?t=457371"). This uses the ndiswrapper method and may work better for you.

The problem is not any specific distro, but rather a lack of hardware vendors providing either drivers for Linux or an open specification so that drivers can be written.

---

### Post by Kuraboy on 2007-05-31
the error is when I ran the script, I don't know why, but it seems like something is wrong with the X server? So it shouldn't be a big problem right?

yes I think I have a broadcom, HP site only says '802.11a/b/g WLAN'... so can Ubuntu assign wrong name to it? I am not sure now :S 

```
monty@monty-laptop:~/Desktop$ lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```

may I ask how did you find about Intel 2200BG?

I don't think an AMD laptop comes with an intel wireless, or do they? :P

thnx for the link to the other post, I will check it later, I must go to sleep now ^_^;

thank you again.

---

### Post by patsfan on 2007-05-31
after working on this for days , being new to linux i am now online wireless.thanks

---

### Post by DarkN00b on 2007-06-01
> **Kuraboy said:**
> the error is when I ran the script, I don't know why, but it seems like something is wrong with the X server? So it shouldn't be a big problem right?

yes I think I have a broadcom, HP site only says '802.11a/b/g WLAN'... so can Ubuntu assign wrong name to it? I am not sure now :S 

```
monty@monty-laptop:~/Desktop$ lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```

may I ask how did you find about Intel 2200BG?

I don't think an AMD laptop comes with an intel wireless, or do they? :P

thnx for the link to the other post, I will check it later, I must go to sleep now ^_^;

thank you again.

Have a look at the [compatibility list]("http://bcm43xx.berlios.de/?go=devices"). The BCM4310 is not listed there. It is possible that it won't work with this method. If it turns out that it doesn't, have a look at [this thread]("http://ubuntuforums.org/showthread.php?p=2749951"). bmartin has written a script to install NDISwrapper and I hear it works well. 
[img]http://img.gamespot.com/gamespot/shared/emoticons/razz.gif[/img]

Seriously though, if this doesn't work for you give it a try.

---

### Post by bmartin on 2007-06-01
> **Kuraboy said:**
> ```
monty@monty-laptop:~/Desktop$ lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```

may I ask how did you find about Intel 2200BG?
I did a Google search on your computer model and it came up with that WiFi, but you're definitely right on both counts. I hope you get your WiFi working.

---

### Post by jpennin5 on 2007-06-03
I just wanted to say that I am a complete newbie to ubuntu and linux in general.  I had almost given up on getting my wireless card to work when I found this tutorial and had it up and running perfectly in less than 10 minutes.  You're a lifesaver :D

---

### Post by ProfessorMembrane on 2007-06-04
Just to clear something up: Is this a driver for ubuntu, or a firmware patch for a chip on the network card?

Isn't changing the firmware really risky, and could end up ruining the card permanantly? Especially if the patch is only in the experimental stages? I have a dual-boot with winXP, will it still work on winXP, at full speed (54 mbps)?

Has the speed problem been fixed yet by any chance?

Cheers

---

### Post by qzplx on 2007-06-04
Hi Darknoob

I got problem with my laptop, i  already follow all your instruction, and its all succedd but the problem is when i come to connect tp AP with Wep encryption i made it and i got the IP but the problem is i cannot ping to gateway, after i checked to the route, reoute its seems fine...

---

### Post by duchovny on 2007-06-04
DarkNoob (or anyone else out there):

How to I uninstall this firmware? I noticed that before I installed it I could connect at 54Mb/s, but since the firmware update I can only connect at 11Mb/s. I have a Belkin Wireless G Plus notebook card 54g+ [F5D7011, ver. 1] (that can connect at 125Mb/s to my Belkin router, but I don't expect that miraculous speed in Ubuntu 7.04).

I'm pretty much a newbie at this, but I'm gathering I run a rmmod command, I just need to know the exact things I should be removing.

Thanks!

---

### Post by DarkN00b on 2007-06-04
> **ProfessorMembrane said:**
> Just to clear something up: Is this a driver for ubuntu, or a firmware patch for a chip on the network card?

Isn't changing the firmware really risky, and could end up ruining the card permanantly? Especially if the patch is only in the experimental stages? I have a dual-boot with winXP, will it still work on winXP, at full speed (54 mbps)?

Has the speed problem been fixed yet by any chance?

Cheers

This is a set of firmware for Linux and will not harm your card. The firmware is loaded upon initialization and unloaded upon ejecting the card. It works the same way in Windows, and will continue to work fine with Windows. As to the question of speed, at this time the firmware is limited to 11Mbs. The firmware developers are working on this and as soon as there are improvements I will post it here along with any new firmware released. Please be aware that I am not affiliated with the developers.

> **qzplx said:**
> Hi Darknoob

I got problem with my laptop, i  already follow all your instruction, and its all succedd but the problem is when i come to connect tp AP with Wep encryption i made it and i got the IP but the problem is i cannot ping to gateway, after i checked to the route, reoute its seems fine...

I really don't know anything about encryption as I have never used it. Have a look [here]("http://ubuntuforums.org/showthread.php?t=202834") for help with connecting to a secured network.

> **duchovny said:**
> DarkNoob (or anyone else out there):

How to I uninstall this firmware? I noticed that before I installed it I could connect at 54Mb/s, but since the firmware update I can only connect at 11Mb/s. I have a Belkin Wireless G Plus notebook card 54g+ [F5D7011, ver. 1] (that can connect at 125Mb/s to my Belkin router, but I don't expect that miraculous speed in Ubuntu 7.04).

I'm pretty much a newbie at this, but I'm gathering I run a rmmod command, I just need to know the exact things I should be removing.

Thanks!

Open a terminal window and CD to the directory containing the install script. Once there, type

```
./installbcm43xx.sh -r
```

hit enter and put in your password. The firmware will be uninstalled.

If you want to try ndiswrapper, I suggest using [this HOWTO]("http://ubuntuforums.org/showthread.php?p=2749951"). Bmartin has been active over there and has been working on automating the installation process. Good luck to you and I hope you get your wireless working.

---

### Post by el_poderoso on 2007-06-04
I used a similar method from another poster, but it worked for me. I'm only getting 45% signal, but this POS card rarely gave a strong signal in WinXP either.  Works good enough for websurfing, email and streaming audio, so no complaints. Fortunately for me, my install was pretty fresh (just commissioned my Compaq Presario 2200 to Ubuntu from WinXP home yesterday) and I hadn't fiddled with the network settings much,

To your credit, with these instructions, I got the Linksys card working easier in Linux than I did in Windows. Won't it be cool when the OEMs are kind enough to put this stuff on the CD so we don't have to hunt for it?

---

### Post by lefloresg80 on 2007-06-04
Can someone please post what they get when running the iwconfig command?
thanks!

---

### Post by iceportal on 2007-06-05
Bloody brilliant. I just unzipped, ran the script, and restarted, and immediately everything was working great!

I love you. :D

---

### Post by DarkN00b on 2007-06-05
> **lefloresg80 said:**
> Can someone please post what they get when running the iwconfig command?
thanks!

```

lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:"*myessid*"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:49:3C:2D:EA   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=48/100  Signal level=-54 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Mikk Lukk on 2007-06-05
Didn't even require so much as a reboot, Fabulous on a Compaq Presario running x64 Ubuntu with a Broadcom 4318.  Cheers!

---

### Post by duchovny on 2007-06-05
> **DarkN00b said:**
> This is a set of firmware for Linux and will not harm your card. The firmware is loaded upon initialization and unloaded upon ejecting the card. It works the same way in Windows, and will continue to work fine with Windows. As to the question of speed, at this time the firmware is limited to 11Mbs. The firmware developers are working on this and as soon as there are improvements I will post it here along with any new firmware released. Please be aware that I am not affiliated with the developers.



I really don't know anything about encryption as I have never used it. Have a look [here]("http://ubuntuforums.org/showthread.php?t=202834") for help with connecting to a secured network.



Open a terminal window and CD to the directory containing the install script. Once there, type

```
./installbcm43xx.sh -r
```

hit enter and put in your password. The firmware will be uninstalled.

If you want to try ndiswrapper, I suggest using [this HOWTO]("http://ubuntuforums.org/showthread.php?p=2749951"). Bmartin has been active over there and has been working on automating the installation process. Good luck to you and I hope you get your wireless working.

Thank you DarkNoob! That did the trick. I uninstalled the firmware and reinstalled ndiswrapper and I'm actually connecting at 125Mb/s!!! (which I really hadn't expected on Linux (*hangs head low and will never gripe about slow again*). :popcorn:

Much thanks DN. You rock!

D

---

### Post by Guns90 on 2007-06-05
I too thank you DarkNoob.  I have had my linksys wmp54gs working with Windoze in my kids' 64bit machine for 6 months, but I only installed a second hard drive and Feisty AMD64 on the second hard drive three days ago.  I had been getting headaches grande.  Thank you very much for the the info.  Gary

---

### Post by jpennin5 on 2007-06-06
Saw how to fix the 'gksudo not found' error on page 21

---

### Post by Guns90 on 2007-06-06
Maybe I kind of spoke too soon......  I'm getting the connection alright, but the rate is extremely slow.  I mentioned before that I had just installed Ubuntu AMD64 on the hdb1.  The first time you boot up after getting on line the update manager prompts you to update.  I clicked on the link and right now it is downloading 1 of 51 programs at a download rate of 218 B/s (it says time remaining is 3d19h38m18s).  I tried downloading on this 32bit computer at the same time as the 64 bit computer, and the download rate was was very fast.  Any suggestions?

---

### Post by bmartin on 2007-06-06
> **Guns90 said:**
> Maybe I kind of spoke too soon......  I'm getting the connection alright, but the rate is extremely slow. [...] this 32bit computer [...] the 64 bit computer, and the download rate was was very fast.  Any suggestions?
1. 64-bit Ubuntu doesn't have the same kind of support that 32-bit does. I run the 32-bit version on my 64-bit PC; so does my girlfriend. I don't really understand the draw to the 64-bit version, but if it's a new install... I'd read up on the pros and cons of 64-bit before I went ahead with it.

2. Try [the ndiswrapper method]("http://ubuntuforums.org/showthread.php?p=2749951") to get your wireless working. Only a few of the Broadcom chipsets (I think 03, 06, 11, and 12) work flawlessly with the firmware. It's a work-in-progress. I was using the firmware with a 4318 chipset and it was slow and flaky. Put a post on that thread as to whether it worked for you or not; it needs bumping.

---

### Post by Guns90 on 2007-06-06
bmartin, thanks for the info.

> 1. 64-bit Ubuntu doesn't have the same kind of support that 32-bit does. I run the 32-bit version on my 64-bit PC; so does my girlfriend. I don't really understand the draw to the 64-bit version, but if it's a new install... I'd read up on the pros and cons of 64-bit before I went ahead with it.


I understand the work in progress thing and that 64bit doesn't have the support that 32bit does as of yet. I use a 32bit computer on a daily basis.  I built a 64bit system for my kids because, well, if you're going to build a new system, I think that you should build for the future.  I'll still use my 32bit mostly, but this will be a good way for me to learn 64bit linux whenever I 'periodically' go on this machine.  As I mentioned before, this is my kids' 64bit machine and they only use Windoze.

> I was using the firmware with a 4318 chipset and it was slow and flaky. Put a post on that thread as to whether it worked for you or not; it needs bumping.

I'm using the 4318 chipset also, so I guess it's just going to continue to be a work in progress.:)  I'm not sure what you meant though when you said to 'put a post on that thread'.  I'd be happy to post knew info, but I'm not sure which thread you're talking about.

---

### Post by bmartin on 2007-06-06
The words "the ndiswrapper method" in my post are a hyperlink to a thread I started that uses ndiswrapper instead of the firmware. It might be a solution to your wireless problem. It fixed a lot of problems for me.

---

### Post by streetlightout on 2007-06-08
wow, thank you so much for this. i've been trying to get my wireless to work for at least 3 hours now, and your way was so simple and took like 3 minutes. thanks again!!

---

### Post by verdomde on 2007-06-08
wow, like magic, quick and painless!

---

### Post by hoistyler on 2007-06-09
> **DarkN00b said:**
> Try typing ```
iwconfig
``` or ```
iwlist scan
``` into a terminal.

That should give you a lot of info about your network, which should help you get up and running. Post here if you need more help, I try to stay around... :)

Hi, again

I was away for 3 weeks and I am back sitting in front of my laptop seeing my wireless still not working :(.

these are the outputs of iwconfig and iwlist scan

*** iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

*** iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


My other PC using windows XP can connect to the router AP without no problem. 

Can anyone help?

---

### Post by DarkN00b on 2007-06-09
> **hoistyler said:**
> Hi, again

I was away for 3 weeks and I am back sitting in front of my laptop seeing my wireless still not working :(.

these are the outputs of iwconfig and iwlist scan

*** iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

*** iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


My other PC using windows XP can connect to the router AP without no problem. 

Can anyone help?

If you have a look at the [compatibility list]("http://bcm43xx.berlios.de/?go=devices") you'll notice that the 4311 chipset is only supported on the PCI-Express bus. Unless your card is running on that bus it probably won't work with this method. I suggest using the [NDiSwrapper method]("http://ubuntuforums.org/showthread.php?p=2749951"). You'll probably get better results and have less of a headache getting it working.

---

### Post by hoistyler on 2007-06-09
Oh didn't notice the PCI-E part there...

I will try the ndiswrapper method and post the results :)

do I have to un-do the firmware method before changing to the ndiswrapper method?

---

### Post by DarkN00b on 2007-06-09
Unless I'm mistaken, bmartin's script will uninstall the firmware before it installs ndiswrapper. Good luck.

---

### Post by chantzzzzz on 2007-06-09
Thanks for this. It works like a charm now. Although the light flickers. Not sure what that's all about, but I'm thinking it does that whenever it's sending/receiving data. Thanks again!

---

### Post by jes on 2007-06-10
Thanks man! This did the trick.
JES

---

### Post by suibhne on 2007-06-11
right, i have spent DAYS on trying to get this work......i've tried this method and the ndiswrapper method and i cant get to the final stage of connecting to my network. 

Ubuntu recognizes the available network, but is unable to connect. A network password is requested, but then the system just sits trying to connect before requesting a passphrase again

I have tried [_[COLOR="Blue"]this[/COLOR]_]("http://ubuntu1501.blogspot.com/") method but without success, although i see here that it is supposed to be possible.

does anyone have any suggestions? 

Am I doing something imbecilic?

Am I missing something?

(Dell Inspiron 1501, Feisty)

---

### Post by Undeadwolf on 2007-06-11
Hi there,

This worked great! The little wireless light went on and everything. The only problem is, after I restart I have to reinstall this driver every time. I think it may be something weird with the security.

I've been using Ubuntu for about 2 weeks so pardon the newbie-ness.

---

### Post by bmartin on 2007-06-11
> **Undeadwolf said:**
> The only problem is, after I restart I have to reinstall this driver every time. I think it may be something weird with the security.
Another person had a similar problem. My guess is that the bcm43xx kernel module isn't getting loaded when your computer starts. Did you try using any other instructions before these ones to get the wireless working? If so, can you post a link to the forum or page?

It could be that your Broadcom wireless device isn't automatically detected by Ubuntu and that's why the module's not getting loaded. Let me know and I'll see if I can fix your problem and figure out how to make sure this doesn't happen to anyone else.

---

### Post by Undeadwolf on 2007-06-11
> **bmartin said:**
> Another person had a similar problem. My guess is that the bcm43xx kernel module isn't getting loaded when your computer starts. Did you try using any other instructions before these ones to get the wireless working? If so, can you post a link to the forum or page?

It could be that your Broadcom wireless device isn't automatically detected by Ubuntu and that's why the module's not getting loaded. Let me know and I'll see if I can fix your problem and figure out how to make sure this doesn't happen to anyone else.

I used ndiswrapper, [here is the tutorial]("http://www.linuxquestions.org/questions/showthread.php?t=462995"). Perhaps that's the problem? It says to blacklist bcm43xx.

---

### Post by bmartin on 2007-06-11
Yes, you should un-blacklist that module.

1. Open a Terminal window
2. Type **sudo gedit /etc/modprobe.d/blacklist**
3. Remove the line that says **blacklist bcm43xx**

Then the module should load every time. Strangely, that's what I recommended to the other user who had this problem, but it apparently wasn't the case for him.

---

### Post by mjrwingnut on 2007-06-13
I installed the patch and restarted my pc and it worked great, but the next time I logged on it didnt work. It shows the wireless nic working but nothing.

any help will be appreciated

---

### Post by bmartin on 2007-06-13
> **mjrwingnut said:**
> I installed the patch and restarted my pc and it worked great, but the next time I logged on it didnt work. It shows the wireless nic working but nothing.

any help will be appreciated
It could be the fact that a new kernel just came out, which means that everyone with the new kernel will have to install the firmware. It could also be a problem with your chipset and the firmware; the firmware only works well for a very small number of chipsets. The compatibility list is [here]("http://bcm43xx.berlios.de/?go=devices") Also, quoting DarkN00b: "If your card is not on that list, it probably won't work. As a rule of thumb if your chipset is listed as unstable I recommend you use NDISwrapper and the Windows drivers
([thread here]("http://ubuntuforums.org/showthread.php?p=2749951"))."

To check which chipset you have, type **lspci | grep Broadcom** into a terminal. If it's a USB device, you might need to try **lsusb | grep Broadcom**. One of those should output a line of text.

---

### Post by dave-ubu on 2007-06-13
works a charm on Broadcom 4306 Version 1

Thank you!

---

### Post by bluvy on 2007-06-13
Thank you SO much!
This was so much easier....worked awesome!

---

### Post by DarkN00b on 2007-06-13
> **bmartin said:**
> ...Also, quoting DarkN00b: "If your card is not on that list, it probably won't work. As a rule of thumb if your chipset is listed as unstable I recommend you use NDISwrapper and the Windows drivers
([thread here]("http://ubuntuforums.org/showthread.php?p=2749951"))...

That was bmartin's Idea though. Seriously - he's put more work into this than I have. I started with an idea, he made it what it is today.

---

### Post by Undeadwolf on 2007-06-14
> **bmartin said:**
> Yes, you should un-blacklist that module.

1. Open a Terminal window
2. Type **sudo gedit /etc/modprobe.d/blacklist**
3. Remove the line that says **blacklist bcm43xx**

Then the module should load every time. Strangely, that's what I recommended to the other user who had this problem, but it apparently wasn't the case for him.

Sorry for the late reply...Beryl distracted me ;)

anyway, that worked, thanks for confirming.

---

### Post by DarkN00b on 2007-06-15
Just dropping in to announce that bmartin has created a Python based GTK installer. The bash script will still be available but the installer is much more full featured and takes care of all the blacklisting/unblacklisting and adding/removing of ndiswrapper -- basically anything you need to do for a clean install.

I am about to start writing the new **two part** HOWTO. The instructions for the new installer will be listed at the top of the first post of this thread, followed by the old instructions for the bash script (which will remain unchanged).

So watch the OP in this thread and you'll soon see a change. 

Also - if you haven't done so already - give a big thanks to bmartin for all the time and effort he has put into this project. As I said, he started with my little script and made what we have here today.

[img]http://smilies.sofrayt.com/fsc/bow.gif[/img]

EDIT: Oh yeah - If you use the new installer, please post here what problems (if any) you have. bmartin won't be around for a while for personal reasons, and I'll try to fill his shoes as best I can but if anyone here sees a post reporting a problem and you think you can help, please do by all means.

EDIT2: OK, the new installer is uploaded and instructions for installation are posted in the HOWTO. Please note that this script is conservative in detecting your chipset compatibility. It detects my BCM4318 Airforce1 chipset and flags it as incompatible even though that chipset will work with this firmware, but is not fully supported. So download the Python installer if you are new to this thread and please provide feedback if you have problems. We also like positive feedback, so don't hold back. :D

---

### Post by bmartin on 2007-06-15
Here's how the chipset detection works (note: no matter what the installer detects, you can try either of the installation options):

On the page with the hardware compatibility list, they list 4303, 06, 11, 12, XG as fully compatible. If you have one of these chipsets, your card will be detected as compatible with the firmware and the firmware will be the default install option.

All of the other chipsets are listed as unstable or unsupported. As more chipsets are supported, the installer can be easily modified to accomodate these changes. These chipsets will be detected as unsupported by the installer and the ndiswrapper will be selected by default. DarkN00b and I have the same chipset, but the firmware is a bit flaky on my machine and ndiswrapper works flawlessly, whereas he's never had a problem with the firmware.

*Note: the Dell Wireless 1390 chipset (or whatever it's called) should be detected as unsupported, but it should be detected nonetheless. I wasn't able to test this chipset. If someone could post what the installer message says for this chipset, that'd be great.

If the installer doesn't detect your chipset at all, don't despair. You can still try using either the firmware or ndiswrapper.

If you're going to install ndiswrapper and you're currently using the firmware, make sure you remove the firmware first (the ndiswrapper installer doesn't remove the firmware). However, if you use the firmware, ndiswrapper will be automatically uninstalled.

---

### Post by MStublefield on 2007-06-15
Worked brilliantly on my laptop! I'm going to try installing Ubuntu on my desktop at home tonight (replacing OpenSUSE 10.2) and see if I can figure it out. I'm extremely happy with how my lappy's working now. Thanks so much for yours and bmartin's work on this! :KS

---

### Post by bitstreams on 2007-06-15
At last, I have a wireless connection working - amazing. Thank you so much - was about to wipe Ubuntu and give up.

many thanks

Simon

---

### Post by Fenrirwulf on 2007-06-15
:D Woot! Same here. You guys rock! I tried Paper Diesel's instructions 4 times even with a clean install of Fiesty and still could not get the wireless to successfully connect to my network even though I could see it and a neighbor's. It was really weird. Your script worked perfectly and I just had to reboot is all. Thank you sooooo much!!!

---

### Post by Cilionelle on 2007-06-16
Hi!  After voting "no" to the poll question - since there was nothing happening - the wireless connection reset itself (wow, have no idea how), and now I am sitting on my couch, away from my connected connection connector and everything is sweet!  Thanks so much! (And I'm changing my vote!)

---

### Post by bitstreams on 2007-06-16
Well it seems I spoke too soon.

Having got a wireless connection working I installed all the available updates and rebooted. This added another entry in my boot list. When I boot from that, the broadcom wireless card isn't even listed.

I've gone down to the next boot item and reconfigured the wireless again - but does this mean I cant do updates (and how do I get rid of the faulty installation from the boot list?)

Simon

---

### Post by DarkN00b on 2007-06-16
> **bitstreams said:**
> Well it seems I spoke too soon.

Having got a wireless connection working I installed all the available updates and rebooted. This added another entry in my boot list. When I boot from that, the broadcom wireless card isn't even listed.

I've gone down to the next boot item and reconfigured the wireless again - but does this mean I cant do updates (and how do I get rid of the faulty installation from the boot list?)

Simon

Are you saying the installation of this firmware added something to your startup? Or has a new entry been added to /boot/grub/menu.lst? If you are selecting a different kernel in grub (which it sounds like) you just need to reinstall the firmware. Some people need to do this after a kernel update.

---

### Post by jrtpaul on 2007-06-16
Thanks sooo much Darkn00b! i have been trying forr weeks to get this to work, all this ndiswrapper crap and finally got it going! Yeah!. Except right now i can only see my neighbours network, not mine.....

Anyway ill see whats happening with it in the morning. .... yeah!

---

### Post by Dalton.Salisbury on 2007-06-16
It worked. After a few hours of looking elsewhere. Thanks so much! Now I don't have to have my DWL-G650 PCMCIA card hanging off the side of my laptop!

---

### Post by jpyanowski on 2007-06-17
Anotdher satisfied customer. HP Pavillion dv2120 with Dell wireless. (does happy dance).

---

### Post by gregnor on 2007-06-20
Success! Thanks DarkN00b.

---

### Post by Tulip on 2007-06-21
Im having trouble, can anyone shed some light on what Im doing wrong please?

I have a Compaq nx9010 with a Feisty Fawn fresh install.
 
```
lspci | grep Broadcom
```

00:09.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

Downloaded and extracted the .tar.gz file to my desktop. Ran the installer.py in a terminal. It displays
Compatible Broadcom chipset found. Installation of firmware is recommended.
Clicked on install and

Traceback (most recent call last):
  File "/home/rob/Desktop/bcm43xx-gtk-installer-0.1/installer.py", line 21, in run_installer
    os.system("xterm -e \"" + perform + ' ; echo \'Press CTRL+C to close this window\' ; tail -f 2> /dev/null\"')
NameError: global name 'perform' is not defined

is displayed in the terminal window. Can anyone shed light on what this means please?

---

### Post by DarkN00b on 2007-06-21
> **Tulip said:**
> Traceback (most recent call last):
  File "/home/rob/Desktop/bcm43xx-gtk-installer-0.1/installer.py", line 21, in run_installer
    os.system("xterm -e \"" + perform + ' ; echo \'Press CTRL+C to close this window\' ; tail -f 2> /dev/null\"')
NameError: global name 'perform' is not defined

is displayed in the terminal window. Can anyone shed light on what this means please?

It looks like a missed single quote to me, but I don't know anything about Python. Try running the .sh script in a terminal window and see how that works out.

---

### Post by dudenamedsteve on 2007-06-21
worked like a dream with Dell Truemobile 1300 PCMCIA on IBM T23 Thinkpad.  This after weeks of suffering through trying to get an ndiswrapper around a USR MAXg.  Many thanks!!!

---

### Post by bobby_barrett on 2007-06-21
Noob - thank you my friend!  This worked like a champ on a Compaq Presario 2200 w/BCOM 4306!  I struggled for several hours before finding your script...thanks again!  :KS:KS:KS

---

### Post by Tulip on 2007-06-21
> **DarkN00b said:**
> It looks like a missed single quote to me, but I don't know anything about Python. Try running the .sh script in a terminal window and see how that works out.

Im a little unsure how to do this - this is what I tried.

Navigated to the correct directory within a terminal window and typed

sudo sh installbcm43xx.sh

The result was

* Backing up current configuration
installbcm43xx.sh: 54: pushd: not found
* Removing old ndiswrapper
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
installbcm43xx.sh: 54: popd: not found
* Copying firmware...
The Broadcom firmware and kernel module have been installed. You may need to restart your computer.
To remove the firmware, run "installbcm43xx.sh -r" from this directory.
rob@rob-laptop:~/Desktop/bcm43xx-gtk-installer-0.1$

Restarted the machine, and still cant see the wireless network :(

---

### Post by DarkN00b on 2007-06-22
> **Tulip said:**
> Im a little unsure how to do this - this is what I tried.

Navigated to the correct directory within a terminal window and typed

sudo sh installbcm43xx.sh

The result was

* Backing up current configuration
installbcm43xx.sh: 54: pushd: not found
* Removing old ndiswrapper
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
installbcm43xx.sh: 54: popd: not found
* Copying firmware...
The Broadcom firmware and kernel module have been installed. You may need to restart your computer.
To remove the firmware, run "installbcm43xx.sh -r" from this directory.
rob@rob-laptop:~/Desktop/bcm43xx-gtk-installer-0.1$

Restarted the machine, and still cant see the wireless network :(

The command you used seems to have worked, but I would recommend using **sudo ./installbcm43xx.sh**.

Please post the output of ```
lsmod |grep bcm
```

You should get something like this:
```
bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac

```

Also look in /lib/firmware and /lib/firmware/(kernel version) <- kernel version will vary, look in the latest one. See if the bcm43xx_*.fw files are there. If they are there, you just need to load the kernel module and initialize the card by typing ```
sudo modprobe bcm43xx
``` into a terminal. Let me know what happens, I'll be glad to help.

---

### Post by Tulip on 2007-06-22
Thanks for the quick replies, I do appreciate your help.

sudo ./installbcm43xx.sh 

* Backing up current configuration
* Removing old ndiswrapper
* Copying firmware...
The Broadcom firmware and kernel module have been installed. You may need to restart your computer.
To remove the firmware, run "./installbcm43xx.sh -r" from this directory.

Much tidier

```
lsmod |grep bcm
```[B]

bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac[/B]

The bcm43xx_*.fw files are present in the lib/firmware and lib/firmware/kernel version directories.

All looks in order. 

Ive restarted the computer, sudo modprobe bcm43xx, and still nothing unfortunately. Network is not detected. Oops, quick edit - restarted again, unplugged the network cable and my wireless network is now being detected. Unfortunately I can't connect to it. I have disabled the wireless security, rebooted the router and have tried a static IP address without success so far.

Could my wireless network be at fault? I have a Linksys WRT-54GL running a DD-WRT firmware. I currently have an XP and a Mac laptop connecting to it okay. I normally have WEP security running on it, but even with it turned off the Ubuntu machine can't connect.
Any more thoughts? Once again I do appreciate your help.
Cheers

---

### Post by DarkN00b on 2007-06-22
Check your /etc/modprobe.d/blacklist file and see if there is a line in there that says **blacklist bcm43xx**. 
```
sudo gedit /etc/modprobe.d/blacklist
```
Its a long shot but the script may not have removed the blacklist entry. If it is present, delete that one line, save the file and type these lines into a terminal (substitute your connection name if it is not wlan0):

```
sudo ifdown wlan0
sudo ifup wlan0
```

This allows you to take down an reinitialize your card without having to restart.

---

### Post by sgt49 on 2007-06-22
The procedure failed to install the bcm4306 driver with the following error:  global name 'Perform' is not defined.  I was able to install ndiswrapper and windows drivers. Blue wireless light lit and it found my network.  However, it will not connect. I entered the WEP key properly but there is no connection to the network.  Does my Linksys WRT45GS not like Linux?

Steve T.

---

### Post by Boipster on 2007-06-22
I got the same results as Steve when I chose to install the firmware. I tried just doubleclicking and running the script from the command line via sudo...
```
Traceback (most recent call last):
  File "./installer.py", line 21, in run_installer
    os.system("xterm -e \"" + perform + ' ; echo \'Press CTRL+C to close this window\' ; tail -f 2> /dev/null\"')
NameError: global name 'perform' is not defined

```

Steve, I've had this card (wpc54gs v1.1) and router (WRT54GS) working on previous versions of Ubuntu.  You might disable WEP temporarily and see if you can pull DHCP without any security.

Attempting the ndis method...

It can see my router, but won't connect, removed all security on the router and powercycled, still no connect. Noticed the network-manager doesn't see the new ssid of the router.  disabled and re-enabled networking.  Now it sees the new ssid and I'm able to connect.  Disconnected and Lan and posted this update.

Working on WEP...

Redid WEP then disabled/re-enabled networking, had to choose to connect to a different wireless network and enter the ssid and key in manually.  Posting this update with WEP Encrypted wifi connection only to laptop.

iwconfig confirms 54Mb/s

Anyone have any hints for getting WPA going? LOL

---

### Post by russtopher on 2007-06-22
Bloody brilliant! I've been fighting with this Thinkpad with Belkin 7010 card for a week. ndiswrapper with the Belkin driver saw the network, but would not connect, even with WPA turned off. I broke so much trying different workarounds, I started fresh tonight with a clean Feisty install, and this worked like a charm. No need to do anything different for WPA - I logged in perfectly. Thanks for this!

---

### Post by quickshade on 2007-06-23
great program...worked perfectly twice. should be stickied.

---

### Post by SDL on 2007-06-24
I downloaded the second method onto a USB pen and it worked perfectly for Feisty. Good work!

---

### Post by DarkN00b on 2007-06-24
bmartin has been at work. He has fixed the bug in the Python installer and it should work now so if you had trouble with it before, download and try it again. It should work now.

Thanks you bmartin! :D

---

### Post by philipt1969 on 2007-06-24
Hi all

Nooby having slight problem!

I have installed and now have a wirelss card that is detecting wireless networks, but which unfortunately cannot connect to my wireless network. I had already disabled wpa in favour of wep, as I believe wpa isn't fully supported, but that didn't work, so tried disabling security altogether, and still cannot connect.

Any advice as to how to proceed?

---

### Post by mjezell on 2007-06-25
Great how-to!! This was easy to understand and works fantastic.  I now have a wireless connection for the first time on my acer laptop.  Thanks a bunch for the time and effort to help the community.

---

### Post by Helmi on 2007-06-25
hi,

thanks for the great howto. unfortunately after all i have still one problem left: Wireless connection is working with the firmware-version and the ndiswrapper variant perfectly but the connection quality is rather bad. lot's of packet losses and breakdowns.

Everything works fine under windows on the same machine (dual boot) so this couldn't be a hardware issue on the network adapter nor on the router.

any idea?

---

### Post by mayra on 2007-06-25
just downloaded the gtk-installer and while trying to run it i get a lot of errors during compile and install. Starting from stdio.h: no such file... what am i missing?

---

### Post by mayra on 2007-06-25
ok got it now... didn't say anywhere that i need to have the original install cd mounted while installing. now to see if it works -->

---

### Post by independent8847 on 2007-06-27
ok so whenever i run that file, my wireless will turn on...but when i shut down my laptop, i have to keep running that file everytime i startup the pc...any help??

---

### Post by DarkN00b on 2007-06-28
> **independent8847 said:**
> ok so whenever i run that file, my wireless will turn on...but when i shut down my laptop, i have to keep running that file everytime i startup the pc...any help??

You should check one file to start with, to quote bmartin:

[QUOTE=bmartin]**SNIP**

1. Open a Terminal window
2. Type **gksudo gedit /etc/modprobe.d/blacklist**
3. Remove the line that says **blacklist bcm43xx**

Then the module should load every time. **SNIP**[/QUOTE]

I changed **sudo** to **gksudo** because using sudo on a graphical application can cause permissions issues within your home folder.

Post back here is that doesn't work.

---

### Post by ChrisJG on 2007-06-28
Awesome HOWTO!  Followed the steps closely and it worked a treat.

Can't thank you enough :)

---

### Post by tymewyse on 2007-06-30
I just updated my HP ZV5000 to Feisty and the wireless went away. Just did the VERY SIMPLE install here and it works perfectly. Thanks ...

---

### Post by khelu on 2007-07-01
been looking for while and it worked like a charm on my compaq nx9010
thanx a bunch for this release.
thanx a lot

---

### Post by brightwood93 on 2007-07-01
Free at last, at last.  Wow!  HP pavilion zv5000 series, Broadcom 4306 chipset, free from Gates.

Thanks,

brightwood93

---

### Post by john blagg on 2007-07-01
absolutely awesome  worked perfect for ndis wrappe and i had been trying for ever to figure out how to do it . 


     I am complete noob to Linux and was having a hard time with this - Thanks

---

### Post by aasodi on 2007-07-01
After 4 days trying to make this thing work good (4318 ) I was ready to give up and this was my final hope and IT WORKS!!!

THANKS!!!

---

### Post by arashiko28 on 2007-07-01
Worked wonderfully until I shut it down and turned it back on, I don't have the enable wireless option anymore:( what went wrong? do i need to activate something every time I turn it on??? forgive my ignorace, I'm a newbie...

UPDATE: I'm very happy! I now have internet! But, could someone tellme if I need to reistall it everytime I turn on my computer? and I have some problem, it kinda freezes like every 30 minutes and i have to make a forced restart! Please, somebody, help!!!

---

### Post by talon4g63 on 2007-07-02
It took me a couple of tries to get  it working on a hp  ze5500. Thanks i couldn't get it working the wrapper method., i kept  getting and error that was getting me frustrated.

---

### Post by qzplx on 2007-07-03
Hi darkn00b;

How to uninstall this things, i need to find another workaround, cuz still not work for me..

---

### Post by DarkN00b on 2007-07-04
> **qzplx said:**
> Hi darkn00b;

How to uninstall this things, i need to find another workaround, cuz still not work for me..

You should be able to run installer.py again and remove the firmware.

---

### Post by EvilRobotDrew on 2007-07-04
THANK YOU

i am a n00b, i have never touched Linux before, but i wanted to try it. 

i worked for about 2 weeks to get my wireless working, and was about to give up. i was climbing the walls in frustration as different tutorials and programs failed to work, then i found this thread, installed your program, rebooted, and now i can watch internet porn anywhere in the house.

all joking aside, your little installer program is awesome, the Firmware installer didn't work (i have the wrong kind of card i guess), but the NdisWrapper portion of the program worked perfectly.

broadcom blows, but u guys rock!!

---

### Post by Goliath! on 2007-07-05
Darkn00b and bmartin, thank you!

The Python graphical thing didn't work for me.  It told me I should install ndiswrapper and when I clicked install it brought up a black terminal saying "Press ctrl-C to close this window."  I let it sit there, but nothing happened, so I ctrl-C'd and both windows closed.  Nothing was installed.

So I looked at the Python code and found out it was supposed to be running install-ndis-broadcom.sh.  So I ran that as root from the terminal and it worked fine.

This is on a Dell 1501 laptop AMD 64 dual core with 7.04.  I had just installed the OS not 10 minutes before.  I realized afterwards that I forgot to let Update Manager update everything from my install.  THis may be why the Python script didn't run.  It also may have had something to do with the fact that I untarred the files in home, not on the Desktop.  Who knows.

So, no, the Python GUI didn't work, but the script did.  Thanks a million!!!!

---

### Post by zeeHesh on 2007-07-07
Excellent script.  After two complete system wipes trying to fix the wireless problem, this got my 4318 back up in no time.

Much appreciated!

---

### Post by puppetj on 2007-07-07
well i'am glad to getting it working also, but i had to use the _**BASH script installer method**_
because my wired nic is dead, so is there way to get this 11mps to at least 54mps this way, it would be alot more helpful, sorry i didnt see it tin the posting, but i did skip thru them quickly since there are some many replies.

---

### Post by LauraB on 2007-07-07
I must say that I am once again disappointed. Over the years, I have tried now and then to install a distro to use as a desktop only to discover that hardware and features that I need will not work. I was excited to try Ubuntu and thought perhaps enough time had passed and it would work.

Wireless networking will not work for me. I tried it on two different systems actually. One gets a little further than the other. Both have Belkin G pci cards. The system in question has Belkin unknown device 700f (rev 20) when I list lspci.

I have tried ALL the scripts and instructions listed including several ways to install ndiswrapper, which for whatever reason had not seemed to even install properly. Maybe it did with the first option in this thread, it said it did but there is nothing on iwconfig. 

I planned to pay the $20 for the one script available out there and it did not even install properly.


So, wireless is not an option. I am not buying new cards just to make this work.

And then there is the DVD issue. One would think that the standard desktop install would allow the user to insert a dvd movie and watch it. Nope. I installed xine and vlc and neither of those work either. I've followed instructions here and there and it seems like another wild goose chase.

Now I bet you think I am a beginner and can not follow instructions. I have been using linux for over 7 years now. I still have a server running red hat 9 - gasp!  I can configure sendmail, apache, mysql, mailman for example and I think I may still have an opennap server running..hmmm.

Linux is awesome for servers. It does not seem to like me for anything else.

The desktop I installed Ubuntu on is a back up PC that I use to store files on because it is the newest hdd ( the little redhat server is 7 years old). I have a TV tuner card, which I use to watch TV and I play movies on it from time to time. It is my bedroom TV/DVD.

This is all I wanted to do and it will not work. Maybe I will try it again in a couple of years. My life is too busy now, I just do not have the countless hours it takes to MAYBE get it to work. It should be simple by now.

---

### Post by LauraB on 2007-07-09
Did I mention that I am persistent? I just couldn't let it go this time. I found tvtime and got that working. Next, I switched wireless cards and kept at it and voila, I am online.

I kept using the script and putting the card in and out. Finally, an interesting pop up box logging a password came up. Not only am I on wireless, I am using wep, too.

Seriously though, I wish this was easier. Newbies shouldn't have to suffer. Maybe one day...


Time to crash and watch TV on 'blackbox' (creative, I know) using Ubuntu instead of a cracker jack version of XP pro!

---

### Post by asonetuh on 2007-07-11
Thanks so much bmartin and darknoob. I've been trying to get this working off and on for months, and thanks to this, I've finally got it working. Another happy ubuntu newb!

---

### Post by bmartin on 2007-07-15
> **LauraB said:**
> And then there is the DVD issue. One would think that the standard desktop install would allow the user to insert a dvd movie and watch it. Nope. I installed xine and vlc and neither of those work either. I've followed instructions here and there and it seems like another wild goose chase.
Unfortunately, propriety will never go away. You can't watch DVDs in the default Ubuntu install. It's a crock, but it's something the devs have had to put up with to make Ubuntu what it is today.

---

### Post by doutdes on 2007-07-17
This worked great, bmartin rocks :guitar:
used suse sled10, but moved into ubuntu, but where having to many troubles setting the wireless until I found this thread

---

### Post by projektdrift on 2007-07-19
THANK YOU!  I've been trying to get my wireless working on my old hand-built amd box for two days, scouring these forums, attempting various deb packages and ndiswrapper methods.  I was so stoked to use ubuntu, but I almost gave up on it because of lack of wireless, as the router is on the other side of the house.

I'm very adept w/windows, but this is my first dip into any linux install and I'm excited to explore it.  Thanks again!

---

### Post by DarkN00b on 2007-07-19
> **projektdrift said:**
> THANK YOU!  I've been trying to get my wireless working on my old hand-built amd box for two days, scouring these forums, attempting various deb packages and ndiswrapper methods.  I was so stoked to use ubuntu, but I almost gave up on it because of lack of wireless, as the router is on the other side of the house.

I'm very adept w/windows, but this is my first dip into any linux install and I'm excited to explore it.  Thanks again!

Kinda different from what you're used to isn't it? :) Anyway I'm glad to see it working for you! Keep with it and you won't regret it. If you have any problems don't hesitate to ask in the appropriate section of the forums.

---

### Post by lolo67 on 2007-07-19
I first installed BCM43XX firmware, it work but was slow at 11 mb/s.
I then tried the install ndiswrapper and Broadcom windows driver, it worked great.
I know get 54 mb/s. This package is easy to use to install drivers.:o
[http://ubuntuforums.org/images/smilies/icon_surprised.gif](http://ubuntuforums.org/images/smilies/icon_surprised.gif)
thanks lolo67

---

### Post by bmartin on 2007-07-19
I just installed the RT73 drivers for the Belkin F5D7050 USB device. Considering it's my parents' computer and they've had nothing but virus/spyware problems, I can't have them compiling kernel modules... so I wrote a script that compiles all of the needed kernel modules. It was all in vain; the RT73 module seems to dislike the 2.6.20 kernel :-( I was able to get the wireless to work in an older kernel, so I simply put the required kernel version in GRUB above my automagic kernel list in menu.lst file. I simply couldn't get ndiswrapper to work.

I'm glad to see so many people having success with this. Is there anything the script needs? Has anyone noticed a problem with upgrading from Edgy to Feisty after using this method? Do the firmware files or ndiswrapper files need to be reinstalled?

---

### Post by DarkN00b on 2007-07-20
> **lolo67 said:**
> I first installed BCM43XX firmware, it work but was slow at 11 mb/s.
I then tried the install ndiswrapper and Broadcom windows driver, it worked great.
I know get 54 mb/s. This package is easy to use to install drivers.:o
[http://ubuntuforums.org/images/smilies/icon_surprised.gif](http://ubuntuforums.org/images/smilies/icon_surprised.gif)
thanks lolo67

Yeah, that is one limitation of using the firmware over ndiswrapper. The firmware is limited to 11 Mb/s. Hopefully they will update this in the future.

---

### Post by darkfame on 2007-07-20
The installer worked great. Thanks.

---

### Post by MikeDK on 2007-07-20
hi yaar it works great.
my laptop is a Hp Pavilion dv9000eu series
really nice installer

Kind Regards MikeDK

---

### Post by MadMardigan on 2007-07-20
Works great! Dell Inspiron 5160 laptop here. You know, the reason I uninstalled ubuntu last time was because of this issue. Now that it's fixed, I think I'll keep it longer :D

---

### Post by funkshun on 2007-07-23
WOW!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! after reinstalling the os two times due to trying to configure the wireless network. I did this in five mins. Thanks.

---

### Post by kbuika on 2007-07-24
Please help! I ran the script and it worked to some degree. I can not see the network. However it is wep encrypted and when I put in the correct info it does not connect... I must have something wrong somewhere. Please help.

Results of iwconfig:
kbuika@kyoldlinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"lbpaulb"  Nickname:"lbpaulb"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:63:8A:96   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=95/100  Signal level=-37 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:56  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also my /etc/network/interfaces file has no eth1 in it. Is this wrong?

---

### Post by bmartin on 2007-07-24
> **kbuika said:**
> Please help! I ran the script and it worked to some degree. I can not see the network. However it is wep encrypted and when I put in the correct info it does not connect... I must have something wrong somewhere. Please help.
Is this the first time you've tried to install the firmware? I'm assuming you used the firmware and not ndiswrapper at this point. Did you try to use ndiswrapper at all? What program are you using to set your wireless settings (or are you using a terminal)?

You shouldn't have to touch the interfaces file at all. Your card's detecting the network (hence the signal strength being at 95%). If you using the terminal to set this, I noticed your iwconfig didn't mention an encryption key. You can use **sudo iwconfig enc XXXX-XXXX-XX open** to do that. I don't know if you can set ASCII keys from the terminal.

---

### Post by kbuika on 2007-07-24
Thanks for your reply BMartin. I had only been trying the code in one of the three wep formats, (i.e. hex, ascii, etc). I tried the others and one of them worked! So it had nothing to do with the script here. I'd like to point out that I had been trying to get my wireless working for 5 days with no luck whatsoever. I tried this script and immediately got a signal, I just had another problem to work around. Thank you guys so much!

---

### Post by herteljt on 2007-07-24
Thank you so much for this post.  I have a new Dell Inspiron 531 with a Broadcom 4318 wireless card and I have been struggling for several days to get ndiswrapper to work.  Your script worked perfectly!

---

### Post by kbuika on 2007-07-25
Please help, I have encountered another problem. I am dual booting windows xp home and ubuntu on a hp ze4430us with a broadcom 4306 (rev 2). I ran this script 2 days ago and it got my wireless working. However, as soon as my wireless started working on ubuntu, my wireless stopped working on windows when it was booted. When I am in windows it says I am connectedto the network, but nothing works. Any ideas? Hopefully someone has encountered this problem before.

---

### Post by DarkN00b on 2007-07-25
The BCM4306 chipsets seem to have issues with the firmware. Try using the installer to install ndiswrapper. I honestly can't say why this would mess up your Windows network. The firmware loaded is only in memory until you restart your computer.

---

### Post by bmartin on 2007-07-25
> **kbuika said:**
> as soon as my wireless started working on ubuntu, my wireless stopped working on windows when it was booted. When I am in windows it says I am connectedto the network, but nothing works. Any ideas? Hopefully someone has encountered this problem before.
I don't know as these problems are related, but it could have something to do with the firmware in Linux interfering with the Windows drivers. If you use the graphical installer, there's an option to remove the firmware. Do that, then try ndiswrapper.

I can't try this myself for a couple reasons. I don't have Windows on this laptop (the one w/ my Broadcom device) and I normally use ndiswrapper. Let us know if this solves your problem; it's the first time I've heard of this happening.

You might want to try reinstalling your Windows drivers. When I used Windows, I had driver troubles at random. Reinstallation usually does the trick.

---

### Post by DarkN00b on 2007-07-25
This should not affect Windows at all. The firmware is removed from memory every time the computer is shut off or restarted.

---

### Post by kbuika on 2007-07-25
I tried ndiswrapper several times before using this script with no luck. I guess I'm just going to have to tweak with settings and see if something changes. Let me know if you think of anything.

---

### Post by kavani on 2007-07-25
I just wanted to say thanks!  It worked like a champ.  This is the first time I've had my wireless card work in Ubuntu.  Now to see if the WPA trouble is in my router...  ;)

---

### Post by salvador_luna on 2007-07-27
Hey thank you!

You saved me a lot of time trying to configure mi wirless card the old way...

I know, my english is bad, because my native language is spanish :D

---

### Post by starkruzr on 2007-07-27
Hi,

I cannot get ndiswrapper to work no matter what I do.

I think I have the firmware working, but I also cannot figure out how to set the WEP key... no matter what I do.

iwconfig does not appear to be able to set ASCII keys.

The gnome-network application doesn't seem to DO anything when I change the key, it just sits there for a while.

I have a 2WIRE router, if that helps.  The default key is a 10 digit number found on the bottom of the router.

EDIT: Okay, so when I do this:

iwconfig eth1 essid "2WIRE417" key 0123-4567-89

I get a green link light and I notice that the number of "Rx invalid crypt" messages stops going up.  Good, right?

Except it absolutely refuses to pick up an IP address.  Messages simply get sent out into the ether with no response.  This is enormously frustrating.

Help?  How do I troubleshoot this?

---

### Post by Fallen_62 on 2007-07-28
I did the BASH script and it worked beautifully.  Thanks!!!

---

### Post by Herman on 2007-07-28
Hey thanks, DarkN00b and bmartin, 
I used bmartin's bcm43xx-gtk-installer-0.1 and it worked perfectly for me, the hardest part was finding this thread. :)
I'm typing to you now via my wireless connection, that was really fast and simple! Excellent! Thanks very much! :)

May I add a comment and a link to this thread to my Networking web page? :)

Regards, Herman  :):):)

---

### Post by bmartin on 2007-07-28
> **Herman said:**
> May I add a comment and a link to this thread to my Networking web page? :)
Of course. I'm glad it worked for you.

> **starkruzr said:**
> EDIT: Okay, so when I do this:

iwconfig eth1 essid "2WIRE417" key 0123-4567-89

I get a green link light and I notice that the number of "Rx invalid crypt" messages stops going up.  Good, right?

Except it absolutely refuses to pick up an IP address.  Messages simply get sent out into the ether with no response.  This is enormously frustrating.

Help?  How do I troubleshoot this?
Have you tried using the wifi-radar program? If you have the universe (or maybe it's the multiverse) repo enabled, you can install it with **sudo aptitude install wifi-radar**.

---

### Post by siralphred on 2007-07-28
this is awesome....saved me tons of time  \m/  am using HP Pavilion dv6000 just in case anyone is interested

---

### Post by DarkN00b on 2007-07-29
> **siralphred said:**
> this is awesome....saved me tons of time  \m/  am using HP Pavilion dv6000 just in case anyone is interested

A little off-topic, but I have a .deb package for the old ZyDas 1201 chipset if anyone needs it or knows anyone who needs it.

Oh, and I'm glad this is working so well for most people!

---

### Post by proze on 2007-07-30
The BASH script worked for me nicely! :) Dell Latitude D600. Thanks very much.

---

### Post by carpespasm on 2007-07-30
Thanks a ton, worked for my presario 2195us, had to reboot then try a couple times, but i'm posting this over wireless, so it looks like i'm good to go!

---

### Post by Collin White on 2007-07-30
Thanks for the install app and advice.  I installed Feisty on a Dell Latitude D600, and this was the only snag.  Well, that and the fact that now that I have wireless again it won't accept my WEP key, but that's not Ubuntu's fault. 

Much thanks.

---

### Post by v604mustangjoe on 2007-08-03
so i got the firmware installed (or so i think). I am able to see the blue wifi light come on on my computer when i press the button. I go to my internet connections at the top right and i can see my wifi network. I click on it and press connect. When it tries to connect the blue light on my wifi button on my computer starts blinking, then it never connects.

Can someone help me with this please.

---

### Post by Sand Lee on 2007-08-03
I think an easier way would be to just download bcm43xx from synaptic. You might need to open the command line to see what's going on.

---

### Post by circuz_phreak on 2007-08-04
My wifi button on the side of my laptop lights up, when I configure my network with the right name and password it shows a status bar beside it with 100%.  But it still won't connect, just spends a couple minutes trying and no luck.  The network uses WPA2 personal encryption.  I did try the terminal method before this one typing in the following two lines

sudo apt-get install build-essential...went fine until I was prompted to put the cd in and hit enter, would not recognize either cd's i mounted iso's on, (live cd or text installer).

sudo apt-get install bcm43xx-fwcutter...Couldn't find package bcm43xx-fwcutter

could the first command screwed up some settings???or maybe I have to set up the same network again?

---

### Post by DarkN00b on 2007-08-05
Ubuntu doesn't do WPA natively. You'll need to install WPA_Supplicant for it to connect. Try looking at [this thread]("http://ubuntuforums.org/showthread.php?t=202834") for a good way to get it working.

---

### Post by meth on 2007-08-05
I have installed the driver, and can scan my home wifi network, but when i try to connect with the netkwor manager i cant connect, and cant scan my wifi network.

> 
$ lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:57:2d:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d0002000-d0003fff irq:10


> $ lsmod | grep bcm
bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac


Someone can help me?

---

### Post by coughlin on 2007-08-05
As this thread is somewhat long (to say the least), it would help folks, if you could edit/update the first post to the latest directions.

For example, aside from the gtk step 3 version change from -0.1 to -0.2, step #3 says "double click the installbcm43xx.sh file."  On a fresh install, nothing happened when I did that.  I had to open a terminal, change into the extract directory and type:
```
sudo ./installbcm43xx.sh
```
Then, the script ran.  I re-booted and lived happily ever after!  :)

... a B I G thanks to bmartin
You've saved the world a LOT of misery!  :KS

---

### Post by DarkN00b on 2007-08-05
> **coughlin said:**
> As this thread is somewhat long (to say the least), it would help folks, if you could edit/update the first post to the latest directions.

For example, aside from the gtk step 3 version change from -0.1 to -0.2, step #3 says "double click the installbcm43xx.sh file."  On a fresh install, nothing happened when I did that.  I had to open a terminal, change into the extract directory and type:
```
sudo ./installbcm43xx.sh
```
Then, the script ran.  I re-booted and lived happily ever after!  :)

... a B I G thanks to bmartin
You've saved the world a LOT of misery!  :KS

How odd. The .sh script uses gksudo. It should have prompted for a password.

---

### Post by andylsu on 2007-08-06
Thank you...I was pulling my hair out trying to get my Broadcom wireless to work on my laptop. Installing the firmware worked great.:)

---

### Post by v604mustangjoe on 2007-08-06
I can find my network, and when i try to connect my network button/light on my laptop blinks, and i get no connection. anyone know whats the problem. I have a broadcom 4306

---

### Post by BmwStreetRacer on 2007-08-06
Great post you saved my wireless!!!

Thank's


By the way can i use this driver to work with aircrack?

:popcorn:

---

### Post by DarkN00b on 2007-08-07
> **v604mustangjoe said:**
> I can find my network, and when i try to connect my network button/light on my laptop blinks, and i get no connection. anyone know whats the problem. I have a broadcom 4306

Have you installed any of the drivers in this howto? Are you using any sort of encryption? More details are needed for us to help you.

---

### Post by andrewapeterson on 2007-08-07
Thank You So Much!
I spent all day yesterday just trying to figure out what and what not to google to figure out how to fix this crap!  Part of my problem is that I'm working with xubuntu 6.06 I think.  Plus, I don't have a working ethernet card so... Synaptic wasn't helping.  I couldn't get all the dependancies for ndiswrapper worked out from another machine etc... 

What a headache.  Finally found this post after like 10 hours of obsessing and reinstalling and trying this and that...

THIS IS EASY!  THANK YOU!

---

### Post by v604mustangjoe on 2007-08-07
Well i ran the install program that was written in python it then asked me if i wanted to use one of two options. I chose one, didnt work, retried and chose the other and it only found my network and attempted to connect. I disabled WEP, and made my router an unsecure connection (not really worried about my neighbors too much as they barely know how to turn a computer on) 

When i tried connecting it would flash my lights on my laptop where the physical wifi button is. in windows this never happens. This is the only main issue i am having with linux right now. Once i get cadega i should be on track to getting rid of windows.

---

### Post by bmartin on 2007-08-07
> **BmwStreetRacer said:**
> Great post you saved my wireless!!!

Thank's


By the way can i use this driver to work with aircrack?

:popcorn:
I don't see why not. It should work fine. Go for it.

> **v604mustangjoe said:**
> I can find my network, and when i try to connect my network button/light on my laptop blinks, and i get no connection. anyone know whats the problem. I have a broadcom 4306
A Broadcom 4306 should work flawlessly with either driver. Which driver does it detect the network with?

Have you tried using the wifi-radar program? I personally don't care for Network Manager.

> How odd. The .sh script uses gksudo. It should have prompted for a password.
gksudo only prompts for a password if the program isn't run with root privileges. Since using **sudo** runs the program as root, a prompt isn't required.

---

### Post by DarkN00b on 2007-08-08
](*,) I really shouldn't try to answer posts at two in the morning...

---

### Post by ponderosajoe20 on 2007-08-08
Thank you, Thank you, THANK YOU!!!  This worked like a charm.  I spent a day and half trying the other methods with now success.  This worked the first try.  Thank you again!

Best Regards,

Ponderosajoe20

---

### Post by hyg71886 on 2007-08-09
I just want to start off by saying thanks for this thread, life saver. I have it installed and i put my wep key in, but i still cant connect wirelessly, do i need to enter the connection settings manually because it doesnt have anything in it accept for DHCP under config.

---

### Post by bmartin on 2007-08-09
> **hyg71886 said:**
> I just want to start off by saying thanks for this thread, life saver. I have it installed and i put my wep key in, but i still cant connect wirelessly, do i need to enter the connection settings manually because it doesnt have anything in it accept for DHCP under config.
I'm currently adding debugging information to the installation script to help people like you. A lot of people get to this stage and get stuck.

I'm currently reading over the entire 35 pages of posts to see what people have been doing to get around the problem you're having.

Are you using the firmware or ndiswrapper? If you're using the firmware, did the graphical installer suggest ndiswrapper? Have you tried using each of them?

Spoiler alert: I'm working on a version of the installer that outputs a lot more information, including which kernel you're running and all sorts of logs that'll help diagnose the problem.

---

### Post by hyg71886 on 2007-08-09
> **bmartin said:**
> I'm currently adding debugging information to the installation script to help people like you. A lot of people get to this stage and get stuck.

I'm currently reading over the entire 35 pages of posts to see what people have been doing to get around the problem you're having.

Are you using the firmware or ndiswrapper? If you're using the firmware, did the graphical installer suggest ndiswrapper? Have you tried using each of them?

Spoiler alert: I'm working on a version of the installer that outputs a lot more information, including which kernel you're running and all sorts of logs that'll help diagnose the problem.

It suggested ndiswrapper and i went with that. I know the os is reading my wireless card because the wireless on/off button on my laptop turned on, like i said i just dont know how to get it to connect now. I appriciate the help, and if theres ANYTHING i can do to help solve it please let me know because I wanna help every1 who is also having this problem.

---

### Post by bmartin on 2007-08-09
What program are you using to connect? Are you using the built-in network manager program? I find my wireless works much more nicely with the **wifi-radar** program, and some people have had more success with **knetworkmanager**. If you have a wired connection available, you can download them using apt.

I'd try wifi-radar. What happens when you put your settings in and try to connect in that program? (Install it first with **sudo apt-get install wifi-radar** from a terminal; you have to have the universe repository enabled, then run **sudo wifi-radar**.)

---

### Post by hyg71886 on 2007-08-09
> **bmartin said:**
> What program are you using to connect? Are you using the built-in network manager program? I find my wireless works much more nicely with the **wifi-radar** program, and some people have had more success with **knetworkmanager**. If you have a wired connection available, you can download them using apt.

I'd try wifi-radar. What happens when you put your settings in and try to connect in that program? (Install it first with **sudo apt-get install wifi-radar** from a terminal; you have to have the universe repository enabled, then run **sudo wifi-radar**.)

I tried to install it through the file, and it installed but its telling me it cant find my ip address. Im using wifi-radar

---

### Post by bmartin on 2007-08-09
I read through the entire previous 35 pages of success and struggle. The only thing I've found that was any use was the following, which a user posted (sorry, I didn't note the name) as a possible fix for a detected device that won't connect to the network:
```
sudo iwlist scanning
```
I'm not sure whether this has any impact at all; it displays available WiFi networks and enables scanning, which most of us will want on anyways.

This command will be present in both installation scripts in the future and its output will be logged.

---

### Post by hyg71886 on 2007-08-09
> **bmartin said:**
> I read through the entire previous 35 pages of success and struggle. The only thing I've found that was any use was the following, which a user posted (sorry, I didn't note the name) as a possible fix for a detected device that won't connect to the network:
```
sudo iwlist scanning
```
I'm not whether this has any impact at all; it displays available WiFi networks and enables scanning, which most of us will want on anyways.

This command will be present in both installation scripts in the future and its output will be logged.

it wonst let me type in a password or paste it

---

### Post by hyg71886 on 2007-08-09
YEESSS I GOT IT!!! I was trying to tell what i did to get it to work but i just played around with some settings in networking. Try that if you did what i did and it still doesnt work. Now I just gotta figure out how to get all my wma files(music, vids, etc) to play lol. there is one problem though, on my little internet box it has a red minus through it n the error messsage says 
Please Contact your system admin to resolve the following problem:
SIOCGIFFLAGS error: No such device

update:
fixed it, i had changed the name to wireless without going into networking and changing that to. It works fine now. thanks

O this is what i did to fix it, i went into wi-fi radar, click on your connection and click edit, then go into wifi options and change it to what ever wifi radar says under mode for your connection and that should fix it:) If you need help im me.

---

### Post by hyg71886 on 2007-08-09
Ok new problem, I downloaded and installed all the updates and rebooted. Now my system is not registering my wireless card. When i go to network settings it just has the ethernet port no wireless. And the wifi radar isnt reading my router either, the connection bar is all grey.

---

### Post by bmartin on 2007-08-09
> **hyg71886 said:**
> Ok new problem, I downloaded and installed all the updates and rebooted. Now my system is not registering my wireless card. When i go to network settings it just has the ethernet port no wireless. And the wifi radar isnt reading my router either, the connection bar is all grey.
Re-run the installer. You probably have a new kernel and need the drivers to be installed again. You may have to do this for every new kernel.

---

### Post by hyg71886 on 2007-08-09
> **bmartin said:**
> Re-run the installer. You probably have a new kernel and need the drivers to be installed again. You may have to do this for every new kernel.

tried it and then went in the terminal n type this

hyg71886@Vanessa:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by rederic4 on 2007-08-09
HI,

I'm very much a newbie and have been trying wihtout success to get my broadcom 4318 to connect, I now connect but only at 11mps. I hav ssen other discussions of this issue but they all go over my head. Do I need to reinstall feisty and start over? is another version better (dapper, edgy?). Willing to work b  tnot sure what to do or where to go. thanks

---

### Post by hyg71886 on 2007-08-09
ok i restarted and the wireless card is now showing up again, It shows up in the networking screen now, but it wont connect. I checked it with wifi radar again and its still not reading the connection from my modem

---

### Post by bmartin on 2007-08-09
> **rederic4 said:**
> HI,

I'm very much a newbie and have been trying wihtout success to get my broadcom 4318 to connect, I now connect but only at 11mps. I hav ssen other discussions of this issue but they all go over my head. Do I need to reinstall feisty and start over? is another version better (dapper, edgy?). Willing to work b  tnot sure what to do or where to go. thanks
I have a Broadcom 4318, as well. Did you run the graphical installer? It recommends ndiswrapper (not the bcm43xx firmware). If you use the ndiswrapper method, you'll get 54mbps.

If you use the firmware, you can only achieve 11mbps. It's a limitation of the firmware.

Run the graphical installer again and select ndiswrapper (it should be selected by default). This should solve your problem.

---

### Post by hyg71886 on 2007-08-09
ok i restarted agaon and the wireless card is now showing up again, It shows up in the networking screen now, but it wont connect. I checked it with wifi radar again and its still not reading the connection from my modem. Ive been playing with it for over 2hrs im lost

---

### Post by rederic4 on 2007-08-09
bmartin

Thanks! I know this will sound stupid but where can I get the driver? The one I downloaded from Gateway appears to not be the correct one as it isn't accepted. Thanks for the help.

---

### Post by hyg71886 on 2007-08-09
wat kind of card is it

---

### Post by rederic4 on 2007-08-09
4318 air force

---

### Post by hyg71886 on 2007-08-09
did u download wifi radar n try the other steps already posted?

---

### Post by bmartin on 2007-08-10
> **rederic4 said:**
> 4318 air force
That's a Broadcom chipset, right? Just run the **installer.py** file (found in the archive on the first page) and select the ndiswrapper installation. It'll take care of everything for you. The driver's included.

---

### Post by DarkN00b on 2007-08-10
> **rederic4 said:**
> HI,

I'm very much a newbie and have been trying wihtout success to get my broadcom 4318 to connect, I now connect but only at 11mps. I hav ssen other discussions of this issue but they all go over my head. Do I need to reinstall feisty and start over? is another version better (dapper, edgy?). Willing to work b  tnot sure what to do or where to go. thanks

Hello rederic4. Just as bmartin said, the installer recommends ndiswrapper. This is because the firmware that you installed is limited to 11Mb/s. This is not a failing of Ubuntu, it is a limitation in the firmware itself.

I have the same Airforce1 chipset you have and I use the firmware out of preference, despite the slower speed. I'm with bmartin in this case. You should use ndiswrapper. It supports this chipset better than the firmware.

---

### Post by nickajeglin on 2007-08-10
Thank you so much. Lack of wireless support has been the only reason I never upgraded to linux from windows before. Now every computer in my house shall run Ubuntu. :)

---

### Post by bmartin on 2007-08-10
> **nickajeglin said:**
> Thank you so much. Lack of wireless support has been the only reason I never upgraded to linux from windows before. Now every computer in my house shall run Ubuntu. :)
I hear this comment all too often. I'm glad it worked for you.

I feel that wireless is the single most important thing that the Ubuntu team needs to address to ease the mass-migration from Windows to Ubuntu. Madwifi is a start, but there's a lot of work that still needs to be done. It'd be nice if a single program could be set up to install ndiswrapper, firmware, Madwifi, etc. as necessary. I've posted this on the Ubuntu dev forums, but no one bites (not even a nibble). It's disheartening; I feel that they don't care.

Then there's the 17% or so of people that this method doesn't work for. That's about 1 in every six people; they often get to the stage where they see the server but can't connect, or less often, their wireless device disappears and reappears.

If anyone has had success with this method but had to do some tinkering to get it working, **please let us know what you did to get it working**. Getting this working for the majority of people isn't good enough; even if it's something people have to do themselves to fix the problem, we'd like to make our method more bullet proof. Thank you in advance.

---

### Post by bmartin on 2007-08-11
I've read all over the forums and all over the internet, trying to find out why wireless seems to work for some people and not others, as well as what people do to fix their wireless problems. I have but three conclusions:

Many people are convinced that when Windows updates their wireless drivers, their WiFi stops working in Ubuntu. If the [firmware]("http://en.wikipedia.org/wiki/Firmware") is modified by the upgrade, this could be the case. Users have solved this problem by rolling back their Windows XP or Vista drivers. If you dual boot and your WiFi suddenly stops working, it's probably a good idea to try rolling back your wireless driver. The firmware **may be more immune** to this hazard.

Feisty Fawn has serious issues with wireless connectivity. While other distros have their issues, many of them have better support for WiFi (in general) than Ubuntu does. If you simply can't get it working, try PCLinuxOS or Sabayon or some other distro.

There is no "easy fix" for people whose WiFi device is detected but won't connect. I've looked through hundreds of pages today. A fresh reinstall might help; running Linux only might help; using a different OS might help. Sometimes it's just a matter of time until it seems to magically work out of nowhere.

---

### Post by woopud on 2007-08-11
I have a Belkin F5D7010 v7 PCMIA card for my laptop, will this work for me ?   So far I cannot get it to work in Feisty.

Bert

---

### Post by bmartin on 2007-08-11
> **woopud said:**
> I have a Belkin F5D7010 v7 PCMIA card for my laptop, will this work for me ?   So far I cannot get it to work in Feisty.

Bert
If you go to a terminal and type **lspci | grep -i wireless**, it should tell you whether or not you have a Broadcom chipset. If you do have one, this should work. If you run the installer, it should detect that you have a supported or unsupported Broadcom and select the WiFi or ndiswrapper installation as appropriate.

---

### Post by woopud on 2007-08-11
It tells me the following:

02:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)

Bert

---

### Post by bmartin on 2007-08-11
No, but you might find some help [here]("http://ubuntuforums.org/showthread.php?p=2743900").

---

### Post by Tomkin on 2007-08-11
I have a problem...

```
Traceback (most recent call last):
  File "/home/ben/bcm43xx-gtk-installer-0.2.1/installer.py", line 12, in <module>
    import pygtk
ImportError: No module named pygtk
```

How do I get pygtk?

---

### Post by bmartin on 2007-08-11
> **Tomkin said:**
> I have a problem...

```
Traceback (most recent call last):
  File "/home/ben/bcm43xx-gtk-installer-0.2.1/installer.py", line 12, in <module>
    import pygtk
ImportError: No module named pygtk
```

How do I get pygtk?
Did you just install Ubuntu? You should update your packages before trying this installer. Put this in a terminal:
**sudo apt-get update && sudo apt-get upgrade**

If that doesn't do the trick, I think the package is python-gtk2.
**sudo apt-get install python-gtk2**

---

### Post by bensibensa on 2007-08-11
Thank you

---

### Post by Tomkin on 2007-08-11
Fixed. Sorry for being such a newb. I've never used Linux before.

---

### Post by bmartin on 2007-08-11
> **Tomkin said:**
> Fixed. Sorry for being such a newb. I've never used Linux before.
There's no need to apologize. I'm not going to talk down to you.

I assume everyone's a newb. That's why there's a graphical installer in the first place. It's a simple matter of adding an instruction on the first page telling people that they should update their packages before running the installer.

I hope the installer works smoothly for you and you get your WiFi up-and-running with ease. If you have any more questions, please don't hesitate to ask.

---

### Post by songhk on 2007-08-11
1. Download the GTK installer from here. It is easiest to save this file to your home folder but it doesn't really matter where you put it. (okay)

 2. Right click the .tar.gz file and click Extract Here. It should extract into its own directory. (0kay)

 3. Go into the bcm43xx-gtk-installer-0.2.1 folder and double click the installer.py file and click the Run button when prompted.
; When I double click the installer.py I can't see the Run button.
  It just show installer.py-Kate (look like word file)  

 Please help me, 

Regards.
Hyun.

---

### Post by bmartin on 2007-08-11
> **songhk said:**
> When I double click the installer.py I can't see the Run button.
  It just show installer.py-Kate (look like word file)
Try right-clicking on it and selecting "Run" or "Execute". If that kind of option isn't available, open up a terminal and put in the following:
```
cd ~/Desktop/bcm43xx-gtk-installer-0.2.1/
./installer.py
```
Did you extract the file before you double-clicked on it? If you didn't, it might be the default behavior of the extraction program to open the file in a text editor.

---

### Post by songhk on 2007-08-11
Yes, I used terminal and finished the installation as it recommended.
(incompatible Broadcom Chipset found, Ndiswrapper installation is highly recommended).

After installation, I restared my laptop, but I can't see wireless mark.
What do I do?   thank you for your help.

-----------------------------------------------------------------------------------------------------------------
I already finished the wireless setup (ID, key).
I partitioned my laptop as 2 part (window- wireless work)
Now I try to do this at Linux.

My laptop is Dell Inspiron B129
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by woopud on 2007-08-11
> **bmartin said:**
> No, but you might find some help [here]("http://ubuntuforums.org/showthread.php?p=2743900").

Followed these instructions and it's working like a charm !

Bert

---

### Post by bmartin on 2007-08-11
> **songhk said:**
> After installation, I restared my laptop, but I can't see wireless mark.
What do I do?   thank you for your help.
02)
Try typing **iwlist scanning** into a terminal and see if your wireless network shows up. If so, you can use the **wifi-radar** program to connect to your wireless network (I've had better success with that than with the built-in wireless program). You need to have your universe repository enabled first, then type **sudo apt-get install wifi-radar** to install it.

---

### Post by songhk on 2007-08-11
I attached the iwlist scanning
Is it okay? please check this. thanks.

Hyun.

-----------------------------------------------------------------------------------------------------------------------
songhk@Random:~$  iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:E1:C3:83
                    ESSID:"Garage"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:16:01:16:4D:69
                    ESSID:"001601164D68"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:E7:14:4D:E8
                    ESSID:"oryx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: AE:31:E9:3F:A2:26
                    ESSID:"dlhost"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:0/100  Signal level:-98 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by bmartin on 2007-08-11
> **songhk said:**
> After installation, I restared my laptop, but I can't see wireless mark.
What do I do?   thank you for your help.
I don't understand what you're saying. You "can't see wireless mark"? Is your SSID not showing up? Can you see the network? Are you unable to connect?

---

### Post by songhk on 2007-08-11
Thank you bmartin for kind reply.

Actually, I am almost Linux beginner. My friend installed Kubuntu at my laptop, not ubuntu.

1. Did you extract the file before you double-clicked on it? If you didn't, it might be the default behavior of the extraction program to open the file in a text editor.
; yes, before I double click it, I extracted.
 I think that my extraction program have some default behavior.
 
2. I don't know whether the installation of bcm43xx-gtk-installer-0.2.1 in my laptop is successful or not. When I right click on installer.py  I just can see below content
   open in new window
   open in new tap
   cut
   copy 
   rename 
   move to trash
   open with
   preview in 
   actions
   compress
   copy to 
   move to 
   properties

I can't see Run or Execute, so i used terminal to install it.
I saw the message, installaion is complete and may need to reboot. 
but when I reboot, I can't see wireless mark, SSID, network

Now, I live in dorm. Just in this building, school wireless service is not available.
But sometimes I saw some signals(some company) before I use Linux (at window)
at daytime, I go to department office, at there I can detect school wireless signal

I need Linux for  my research. But many people don't know Linux 
Many people told me that Linux wireless is one of the hardest. 

Until I see the wireless, I will keep in touch. Later I will report what is my problem.
Monday I will try again. Thanks again.

Regards.
Hyun.

---

### Post by DarkN00b on 2007-08-12
> **songhk said:**
> But many people don't know Linux 
Many people told me that Linux wireless is one of the hardest. 

This is unfortunately true. bmartin and I are discussing your right now via IM. Press Fn + F2 and then try again to connect. When you're at a place you can connect from...

---

### Post by DarkN00b on 2007-08-12
> **bmartin said:**
> There's no need to apologize. I'm not going to talk down to you.

I assume everyone's a newb. That's why there's a graphical installer in the first place. It's a simple matter of adding an instruction on the first page telling people that they should update their packages before running the installer.

I hope the installer works smoothly for you and you get your WiFi up-and-running with ease. If you have any more questions, please don't hesitate to ask.

D'oh! I just noticed this...

Will do...

---

### Post by nickajeglin on 2007-08-13
It occours to me that it may be a good idea to sticky this thread. Because I wasted several days trying to configure ndiswrapper or the firmware thing on my own before I found this. I didn't even see this thread show up on google anywhere, whereas the ndiswrapper one was all over the place. I don't know what's involved in convincing somebody around here to sticky a thread, but I think it should be considered to give this script more visibility to new Ubuntu users.

---

### Post by bmartin on 2007-08-13
> **nickajeglin said:**
> It occours to me that it may be a good idea to sticky this thread.[...] I don't know what's involved in convincing somebody around here to sticky a thread, but I think it should be considered to give this script more visibility to new Ubuntu users.
I kind of feel the same way. However, there are some things to consider:
[LIST=1]
[*]Legality: I highly doubt it's legal to distribute drivers in the way we're currently doing, and I'm equally convinced that the Ubuntu team isn't ready to back such a thread. There are issues with our methods that I'm sure we'd have to work out before we could be "stickied".
[*]Objectivity: Broadcom makes many chipsets. However common they may be, why should this forum promote a thread on one chipset over all others? Furthermore, why should our thread be promoted instead of all the other Broadcom HOW-TOs out there? I've made suggestions about our thread on other threads, and I've received a lot of grief from other "thread owners" out there.
[*]Robustness: I'm not convinced that our installation methods are bulletproof, or even that they work better than the other ones out there.
[/LIST]
It is an interesting idea, and perhaps it's something we should look into. I have some ideas on how to get around the legality issues, but I've opted for simplicity thus far. Anyways, if you want to begin the negotiations, contact a forum moderator and see what they think. It's my opinion (and DarkN00b may feel differently) that we don't own this thread; we're simply here to help people get their wireless chipsets working. I'd like to get this "solution" out to more people, but I don't think out solution is special to the point where it should be promoted over others.

---

### Post by nickajeglin on 2007-08-13
I wasn't saying it should be promoted over others, I was saying that compared to others it's practically invisible.

---

### Post by bmartin on 2007-08-13
Fair enough. [Here's a page]("http://blakecmartin.googlepages.com/index.html") I put up in an attempt to drive more traffic to this page.

---

### Post by songhk on 2007-08-13
Thanks DarkN00b and bmartin. for your help.

I tried again and it works well.
Wow, now I use wireless at my office and speed is good.
Today I'm really happy. 

Hyun.

---

### Post by ikman on 2007-08-13
Still no joy.... This is about the 4th different HowTo I have tried. My system is a Compaq R4000 with Feisty i386 installed. On initial OS install I had no wireless. After using synaptic package manager to install bcm43xx-fwcutter. It worked great for about 2 days. I then had to "completely remove" bcm43xx-fwcutter and reinstall--which worked for about 2 or 3 days. after a couple weeks of this, it didn't start working again this time.

So I uninstalled fwcutter and tried the ndiswrapper method using synaptic (ndisgtk, ..commons, utils-1.9). I still saw no wireless LANs in the network manager.  Most recently I tried the howto at:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Your howto was obviously simpler, but it didn't work either. I think the bcmwl5.* drivers I have are faulty somehow, because when I run ndiswrapper -l,  it tells me "invalid driver". (With one of the first howtos, I got a n error message that said it could not extract manufacturer information from driver.)

Any quick fixes?  In lieu of those, can you tell me how to completely remove the bcmwl5.* drivers so I know I am using the newest ones as I download them again from specific howto sites?

Your install.log should be attached (but I can't tell). Here are some highlights and other command outputs:

$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
wireless_setup : invalid driver!

$ sudo modprobe -l |grep 43xx
/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko


$lshw ..
 *-network:0 UNCLAIMED
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@03:02.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: latency=64
                resources: iomemory:b0204000-b0205fff irq:10

$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
.
.
.
At least with bcm43xx-fwcutter installed I get an eth1. But when I do an iwconfig the Access Point: value is "Invalid". The only thing I can see that may be out of sync is that the frequency channel corresponds to CH 14 (2.484GHz) which is a non-US channel. (And I'm in the US).

When I just tried resintalling bcm43xx-fwcutter after removing the ndiswapper packages, I got this error message dialog:
E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1


Any suggestions appreciated...

Thank you.


Here is the install.log:

Compatible Broadcom chipset found. Installation of firmware is recommended.
** Kernel info: Linux tasha-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
 * ndiswrapper installation attempted
Installed ndiswrapper drivers:
 * ndiswrapper installation was successful
** uname -a
Linux tasha-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)
wireless_setup : invalid driver!

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

** tail /var/log/kern.log
Aug 13 13:54:51 tasha-laptop kernel: [ 1763.164000] usbcore: deregistering interface driver ndiswrapper
Aug 13 13:55:37 tasha-laptop kernel: [ 1808.956000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.124000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.124000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 21
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.132000] ndiswrapper: using IRQ 21
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.340000] wlan0: ethernet device 00:90:4b:a5:b1:41 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: '', 14E4:4320.5.conf
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.344000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.344000] usbcore: registered new interface driver ndiswrapper
Aug 13 13:55:38 tasha-laptop kernel: [ 1809.376000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Aug 13 13:55:38 tasha-laptop kernel: [ 1809.684000] ADDRCONF(NETDEV_UP): eth1: link is not ready

** tail /var/log/syslog
Aug 13 13:55:37 tasha-laptop kernel: [ 1808.956000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.124000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.124000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 21
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.132000] ndiswrapper: using IRQ 21
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.340000] wlan0: ethernet device 00:90:4b:a5:b1:41 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: '', 14E4:4320.5.conf
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.344000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 13 13:55:37 tasha-laptop kernel: [ 1809.344000] usbcore: registered new interface driver ndiswrapper
Aug 13 13:55:38 tasha-laptop kernel: [ 1809.376000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Aug 13 13:55:38 tasha-laptop NetworkManager: <debug info>^I[1187031338.326872] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_90_4b_a5_b1_41'). 
Aug 13 13:55:38 tasha-laptop kernel: [ 1809.684000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Compatible Broadcom chipset found. Installation of firmware is recommended.
 * Firmware installation attempted
 * Firmware installed successfully
** uname -a
Linux tasha-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
./stats-logger: line 4: ndiswrapper: command not found

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

** tail /var/log/kern.log
Aug 13 15:50:39 tasha-laptop kernel: [   36.864000] Time: acpi_pm clocksource has been installed.
Aug 13 15:50:51 tasha-laptop kernel: [   49.504000] eth0: no IPv6 routers present
Aug 13 15:52:09 tasha-laptop kernel: [  128.384000] ieee80211_crypt: registered algorithm 'NULL'
Aug 13 15:52:09 tasha-laptop kernel: [  128.388000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 13 15:52:09 tasha-laptop kernel: [  128.388000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 13 15:52:09 tasha-laptop kernel: [  128.432000] bcm43xx driver
Aug 13 15:52:09 tasha-laptop kernel: [  128.432000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 21
Aug 13 15:52:10 tasha-laptop kernel: [  128.884000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 13 15:52:10 tasha-laptop kernel: [  128.908000] ieee80211_crypt: registered algorithm 'WEP'
Aug 13 15:52:58 tasha-laptop kernel: [  176.800000] APIC error on CPU0: 00(40)

** tail /var/log/syslog
Aug 13 15:52:45 tasha-laptop avahi-autoipd(eth1)[5559]: fopen() failed: Permission denied
Aug 13 15:52:45 tasha-laptop avahi-autoipd(eth1)[5559]: Starting with address 169.254.7.31
Aug 13 15:52:50 tasha-laptop avahi-autoipd(eth1)[5559]: Callout BIND, address 169.254.7.31 on interface eth1
Aug 13 15:52:50 tasha-laptop avahi-daemon[4718]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.31.
Aug 13 15:52:50 tasha-laptop avahi-daemon[4718]: New relevant interface eth1.IPv4 for mDNS.
Aug 13 15:52:50 tasha-laptop avahi-daemon[4718]: Registering new address record for 169.254.7.31 on eth1.IPv4.
Aug 13 15:52:54 tasha-laptop avahi-autoipd(eth1)[5559]: Successfully claimed IP address 169.254.7.31
Aug 13 15:52:54 tasha-laptop avahi-autoipd(eth1)[5559]: fopen() failed: Permission denied
Aug 13 15:52:58 tasha-laptop kernel: [  176.800000] APIC error on CPU0: 00(40)
Aug 13 15:53:05 tasha-laptop ntpdate[5589]: adjust time server 82.211.81.145 offset -0.002072 sec

** Kernel info: Linux tasha-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
Compatible Broadcom chipset found. Installation of firmware is recommended.
 * Firmware removal attempted
 * Firmware removed successfully
** uname -a
Linux tasha-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)
wireless_setup : invalid driver!

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by bmartin on 2007-08-13
> **ikman said:**
> Any quick fixes?  In lieu of those, can you tell me how to completely remove the bcmwl5.* drivers so I know I am using the newest ones as I download them again from specific howto sites?
**ndiswrapper -r bcmwl5** removes them from memory. To remove them from your hard drive, use [B]sudo rm /etc/ndiswrapper/bcmwl5/*. However, both of them installed correctly and your wireless chipset was recognized. A lot of people get to that stage and can't connect... no one's really sure why. Sorry about that.

> **ikman said:**
> $ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
wireless_setup : invalid driver!

> **ikman said:**
> ** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
You had eth1 after the firmware and after the ndiswrapper, and each one (in the installer you just used) removes the other... so both of them can give you an eth1 connection. Also, you might have mistyped something a while back, because wireless_setup refers to the name of a driver. However, the Broadcom driver used by ndiswrapper is valid. So there's really nothing wrong with either one.

The fact that there are no scan results means that there are no broadcasting networks in range of your chipset. Either you need to connect to one that's hiding its ID, or there simply isn't one in range... or the Channel 14 thing isn't working out.

> **ikman said:**
> At least with bcm43xx-fwcutter installed I get an eth1. But when I do an iwconfig the Access Point: value is "Invalid". The only thing I can see that may be out of sync is that the frequency channel corresponds to CH 14 (2.484GHz) which is a non-US channel. (And I'm in the US).
Sorry if I'm misunderstanding you... the frequency on the router corresponds to channel 14? Or the network you're trying to connect to? Either of those is probably a problem. I don't know what to tell you there, unless you can change which channel you're using.

---

### Post by DarkN00b on 2007-08-14
> **bmartin said:**
> [COLOR="Red"]**SNIP**[/COLOR]
It is an interesting idea, and perhaps it's something we should look into. I have some ideas on how to get around the legality issues, but I've opted for simplicity thus far. Anyways, if you want to begin the negotiations, contact a forum moderator and see what they think. It's my opinion (and DarkN00b may feel differently) that we don't own this thread; we're simply here to help people get their wireless chipsets working. I'd like to get this "solution" out to more people, but I don't think out solution is special to the point where it should be promoted over others.

I agree completely. This thread shouldn't get special status as a sticky and for precisely the reasons you gave. I halfway look for this thread to be mentioned in one of the podcasts I listen to every week. :lolflag: That would probably be a bad thing because I might get in some legal trouble then...

Oh, and for those of you whom are having trouble connecting to networks that are detected -- try wifi-radar if you haven't already. songhk was able to connect after many problems just by trying wifi-radar.

Peace.

---

### Post by spaceW on 2007-08-14
thank you so much DarkN00b and bmartin!  it took me a long time to decide which HOWTO forum to try to follow and which method (bcm43xx or ndiswrapper) to use.  but eventually i chose this thread with ndiswrapper.  and it worked perfectly!

i guess i would prefer using a native driver, but all of the complaints about slow speeds deterred me.

btw, i have a bcm4310.

---

### Post by bmartin on 2007-08-14
> **spaceW said:**
> but eventually i chose this thread with ndiswrapper.  and it worked perfectly!

i guess i would prefer using a native driver, but all of the complaints about slow speeds deterred me.

btw, i have a bcm4310.
The firmware driver doesn't claim to fully support your chipset. I have the same situation. You made the right decision; I hope it works well for you.

---

### Post by b52doc on 2007-08-14
I followed all the steps in the guide and it installed without a hitch it seemed. But when I restarted, the option for wifi in the network manager was gone and I am at my wits end trying to get wifi to work. I am going to reinstall Ubuntu to reverse whatever I did and try something else I guess :(
I typed in lspci in terminal and this is what I get: 
Broadcom Corporation BCM43xG 802.11b/g (rev 02)

---

### Post by bmartin on 2007-08-14
Did you install the firmware or did you use ndiswrapper?

If ndiswrapper, try **sudo modprobe ndiswrapper**
If the firmware, try **sudo modprobe bcm43xx**

Also, what's the output of **iwlist scanning**? Run that last and let me know what it says.

---

### Post by gr8member on 2007-08-15
Bravo !! I was very close to switching back to windows because of the wireless issues. I am a huge fan of open source, but could never ever get started because of installation problems. I even tried fedora 7 before this. Thanks to the community for this script, I was able to get the wireless up and running in my DELL LATITUDE 131L (AMD TURION 64_X2) with Dell 1490 wireless(BCM4310 UART).  

I had to go through 2 fresh installs & 15 different help and forum entires before i could see  success. Any way to get this link to ubuntu wifi docs ?

Additional info: It did not detect my chipset and asked me to install ndiswrapper. I followed the steps, rebooted my system and wireless was up in Ubuntu 7.04 (2.6.20-19.29)

---

### Post by bmartin on 2007-08-15
> **gr8member said:**
> Bravo !! I was very close to switching back to windows because of the wireless issues.
I find this to be the case with a lot of people. It makes me sad. That's why I do what I do.

> **gr8member said:**
> I had to go through 2 fresh installs & 15 different help and forum entires before i could see  success. Any way to get this link to ubuntu wifi docs ?
We could try, I suppose. I'm not familiar with the docs. Could you send me a link to the page where you think they should go? I'd be happy to ask them to consider this thread, and I'd make a page with this installer and the relevant instructions if necessary. We've been discussing similar topics on here lately.

> **gr8member said:**
> Additional info: It did not detect my chipset and asked me to install ndiswrapper. I followed the steps, rebooted my system and wireless was up in Ubuntu 7.04 (2.6.20-19.29)
Thank you for pointing this out. You even posted the important part of the **lspci** output for me :) I looked at the logic of the detection part of the program... and I see why it didn't detect this. ndiswrapper was the appropriate selection in this case. I look for a bunch of chipsets and 4310 wasn't mentioned; perhaps I should look for just "BCM43", followed by two digits... I'm glad this worked for you.

---

### Post by anotherjoe on 2007-08-15
I'm so noob at ubuntu I'm still in the wrapper with the price tag on me. 
Here's what I got trying to install on my acer aspire 5000 notebook. Help?!

Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended.
** Kernel info: Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
 * ndiswrapper installation attempted
Installed ndiswrapper drivers:
 * ndiswrapper installation was successful
** uname -a
Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
./stats-logger: line 4: ndiswrapper: command not found

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


** tail /var/log/kern.log
Aug 14 19:55:12 joe-laptopubuntu kernel: [   81.464000] sd 2:0:0:0: Attached scsi removable disk sdb
Aug 14 19:55:12 joe-laptopubuntu kernel: [   81.464000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug 14 19:55:14 joe-laptopubuntu kernel: [   83.376000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 14 19:55:38 joe-laptopubuntu kernel: [  107.256000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 14 19:56:01 joe-laptopubuntu kernel: [  130.748000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 14 19:56:24 joe-laptopubuntu kernel: [  154.148000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 14 19:56:35 joe-laptopubuntu kernel: [  164.024000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Aug 14 19:56:35 joe-laptopubuntu kernel: [  164.024000] ieee80211_crypt: unregistered algorithm 'NULL'
Aug 14 19:57:10 joe-laptopubuntu kernel: [  199.624000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 19:57:10 joe-laptopubuntu kernel: [  199.652000] usbcore: registered new interface driver ndiswrapper

** tail /var/log/syslog
Aug 14 19:56:24 joe-laptopubuntu firmware_helper[5315]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Aug 14 19:56:24 joe-laptopubuntu kernel: [  154.148000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 14 19:56:28 joe-laptopubuntu NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
Aug 14 19:56:35 joe-laptopubuntu NetworkManager: <debug info>^I[1187135794.836870] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_14_a4_30_f6_b8'). 
Aug 14 19:56:35 joe-laptopubuntu NetworkManager: <information>^IDeactivating device eth1. 
Aug 14 19:56:35 joe-laptopubuntu NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on eth1: No such device 
Aug 14 19:56:35 joe-laptopubuntu kernel: [  164.024000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Aug 14 19:56:35 joe-laptopubuntu kernel: [  164.024000] ieee80211_crypt: unregistered algorithm 'NULL'
Aug 14 19:57:10 joe-laptopubuntu kernel: [  199.624000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 19:57:10 joe-laptopubuntu kernel: [  199.652000] usbcore: registered new interface driver ndiswrapper

Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended.
 * Firmware installation attempted
 * Firmware installed successfully
** uname -a
Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
./stats-logger: line 4: ndiswrapper: command not found

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device


** tail /var/log/kern.log
Aug 14 19:56:24 joe-laptopubuntu kernel: [  154.148000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 14 19:56:35 joe-laptopubuntu kernel: [  164.024000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Aug 14 19:56:35 joe-laptopubuntu kernel: [  164.024000] ieee80211_crypt: unregistered algorithm 'NULL'
Aug 14 19:57:10 joe-laptopubuntu kernel: [  199.624000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 19:57:10 joe-laptopubuntu kernel: [  199.652000] usbcore: registered new interface driver ndiswrapper
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.276000] ieee80211_crypt: registered algorithm 'NULL'
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.280000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.280000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.284000] bcm43xx driver
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.284000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22

** tail /var/log/syslog
Aug 14 19:58:23 joe-laptopubuntu dhclient: send_packet: No such device
Aug 14 19:58:37 joe-laptopubuntu dhclient: No DHCPOFFERS received.
Aug 14 19:58:37 joe-laptopubuntu dhclient: No working leases in persistent database - sleeping.
Aug 14 19:58:40 joe-laptopubuntu gconfd (root-8939): GConf server is not in use, shutting down.
Aug 14 19:58:40 joe-laptopubuntu gconfd (root-8939): Exiting
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.276000] ieee80211_crypt: registered algorithm 'NULL'
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.280000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.280000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.284000] bcm43xx driver
Aug 14 19:59:21 joe-laptopubuntu kernel: [  330.284000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22

Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended.
 * Firmware removal attempted
 * Firmware removed successfully
** uname -a
Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
./stats-logger: line 4: ndiswrapper: command not found

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


** tail /var/log/kern.log
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.556000] Bluetooth: HCI device and connection manager initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.556000] Bluetooth: HCI socket layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.600000] Bluetooth: L2CAP ver 2.8
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.600000] Bluetooth: L2CAP socket layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.728000] Bluetooth: RFCOMM socket layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.728000] Bluetooth: RFCOMM TTY layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.728000] Bluetooth: RFCOMM ver 1.8
Aug 14 20:01:10 joe-laptopubuntu kernel: [   45.896000] NET: Registered protocol family 10
Aug 14 20:01:10 joe-laptopubuntu kernel: [   45.896000] lo: Disabled Privacy Extensions
Aug 14 20:01:10 joe-laptopubuntu kernel: [   45.896000] ADDRCONF(NETDEV_UP): eth0: link is not ready

** tail /var/log/syslog
Aug 14 20:01:17 joe-laptopubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Aug 14 20:01:17 joe-laptopubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): starting (version 2.18.0.1), pid 5098 user 'root'
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 14 20:02:20 joe-laptopubuntu gconfd (root-5098): GConf server is not in use, shutting down.
Aug 14 20:02:21 joe-laptopubuntu gconfd (root-5098): Exiting

Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended.
** Kernel info: Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
 * ndiswrapper installation attempted
Installed ndiswrapper drivers:
 * ndiswrapper installation was successful
** uname -a
Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
./stats-logger: line 4: ndiswrapper: command not found

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


** tail /var/log/kern.log
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.600000] Bluetooth: L2CAP ver 2.8
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.600000] Bluetooth: L2CAP socket layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.728000] Bluetooth: RFCOMM socket layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.728000] Bluetooth: RFCOMM TTY layer initialized
Aug 14 20:01:00 joe-laptopubuntu kernel: [   35.728000] Bluetooth: RFCOMM ver 1.8
Aug 14 20:01:10 joe-laptopubuntu kernel: [   45.896000] NET: Registered protocol family 10
Aug 14 20:01:10 joe-laptopubuntu kernel: [   45.896000] lo: Disabled Privacy Extensions
Aug 14 20:01:10 joe-laptopubuntu kernel: [   45.896000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 14 20:04:24 joe-laptopubuntu kernel: [  239.588000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 20:04:24 joe-laptopubuntu kernel: [  239.608000] usbcore: registered new interface driver ndiswrapper

** tail /var/log/syslog
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): starting (version 2.18.0.1), pid 5098 user 'root'
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 14 20:01:50 joe-laptopubuntu gconfd (root-5098): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 14 20:02:20 joe-laptopubuntu gconfd (root-5098): GConf server is not in use, shutting down.
Aug 14 20:02:21 joe-laptopubuntu gconfd (root-5098): Exiting
Aug 14 20:04:24 joe-laptopubuntu kernel: [  239.588000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 20:04:24 joe-laptopubuntu kernel: [  239.608000] usbcore: registered new interface driver ndiswrapper

Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended.
** Kernel info: Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
 * ndiswrapper installation attempted
Installed ndiswrapper drivers:
 * ndiswrapper installation was successful
** uname -a
Linux joe-laptopubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
./stats-logger: line 4: ndiswrapper: command not found

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


** tail /var/log/kern.log
Aug 14 20:14:47 joe-laptopubuntu kernel: [   35.768000] Bluetooth: L2CAP socket layer initialized
Aug 14 20:14:48 joe-laptopubuntu kernel: [   35.900000] Bluetooth: RFCOMM socket layer initialized
Aug 14 20:14:48 joe-laptopubuntu kernel: [   35.900000] Bluetooth: RFCOMM TTY layer initialized
Aug 14 20:14:48 joe-laptopubuntu kernel: [   35.900000] Bluetooth: RFCOMM ver 1.8
Aug 14 20:15:02 joe-laptopubuntu kernel: [   50.348000] NET: Registered protocol family 10
Aug 14 20:15:02 joe-laptopubuntu kernel: [   50.348000] lo: Disabled Privacy Extensions
Aug 14 20:15:02 joe-laptopubuntu kernel: [   50.348000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 14 20:22:05 joe-laptopubuntu kernel: [  472.588000] usbcore: deregistering interface driver ndiswrapper
Aug 14 20:22:24 joe-laptopubuntu kernel: [  492.088000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 20:22:24 joe-laptopubuntu kernel: [  492.116000] usbcore: registered new interface driver ndiswrapper

** tail /var/log/syslog
Aug 14 20:18:25 joe-laptopubuntu gconfd (root-5234): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 14 20:18:25 joe-laptopubuntu gconfd (root-5234): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 14 20:18:25 joe-laptopubuntu gconfd (root-5234): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 14 20:18:25 joe-laptopubuntu gconfd (root-5234): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 14 20:18:25 joe-laptopubuntu gconfd (root-5234): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 14 20:18:55 joe-laptopubuntu gconfd (root-5234): GConf server is not in use, shutting down.
Aug 14 20:18:55 joe-laptopubuntu gconfd (root-5234): Exiting
Aug 14 20:22:05 joe-laptopubuntu kernel: [  472.588000] usbcore: deregistering interface driver ndiswrapper
Aug 14 20:22:24 joe-laptopubuntu kernel: [  492.088000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 14 20:22:24 joe-laptopubuntu kernel: [  492.116000] usbcore: registered new interface driver ndiswrapper

---

### Post by gr8member on 2007-08-15
Please find the link. [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by bmartin on 2007-08-15
anotherjoe, I'm at a loss to explain what happened. It appears that ndiswrapper didn't compile correctly for some reason. You're connected to the internet while running this program, right? The only reason I can think of why ndiswrapper would fail to compile is that you're missing the build-essential or linux-headers-`uname -r` package.

---

### Post by bmartin on 2007-08-15
> **gr8member said:**
> Please find the link. [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
I created a page [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29").

Thanks for the link :)

---

### Post by MarkLori on 2007-08-15
This worked perfectly on my Dell C640 with a Linksys WPC54GS PCMCIA card.  Thanks!  They should incorporate this into the next version of Ubuntu.  That's the last major setup hurdle for me.

---

### Post by bmartin on 2007-08-15
> **MarkLori said:**
> They should incorporate this into the next version of Ubuntu.  That's the last major setup hurdle for me.
In the Universe repository, perhaps? Maybe that's the next step for this "project". I do know how to create DEBs (although they're not very high quality DEBs). I don't currently distribute this as a DEB package because it would be less convenient for most users if I did.

I tried contacting Broadcom about the "distributing their drivers" issue, but I got either a bot or a canned response. I think that would be the last major stumbling block. If I displayed a license agreement every time the script was run, this would be quite legal to distribute widely. The firmware could be extracted from the Windows driver as needed.

---

### Post by rainwalker on 2007-08-15
I'm trying to set up a Linksys WPC54G card in Feisty, but I seem to be having issues with this "fwcutter" thing. 
It's a fresh install, so there were loads of updates. It got to this point:
> Unpacking replacement mesa-utils ...
Setting up bcm43xx-fwcutter (006-1) ...
--20:04:23--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:04:24 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python2.5 (2.5.1-0ubuntu1) ...

I've gotten that (or a very similar) error every time I try to use this fwcutter thing. Every time, there is an "error processing bcm43xx-fwcutter (--configure):" after that bit with boredklink.googlepages.com. 
I really don't know what I'm doing, but this fwcutter stuff just does not want to work. Any ideas?
I have all of the repositories enabled.

EDIT:
Things just finished updating, and this is the message I got:
> Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--20:12:05--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:12:05 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

---

### Post by bmartin on 2007-08-15
I'm sorry, but this isn't the place for fwcutter questions. If you want to install the firmware, there's an installer on the first page. Download that and it'll take care of everything for you.

---

### Post by rainwalker on 2007-08-15
Sorry to be a bother, but I DID use that script. 
The person changed their website, that "wl_apsta.o" file is gone.

---

### Post by bmartin on 2007-08-15
The firmware is in the bcm43xx directory. You can get it from there. Then you won't have to struggle with fwcutter.

---

### Post by rainwalker on 2007-08-15
Um...what do you mean?
Sorry, I'm not the most educated in these things

---

### Post by bmartin on 2007-08-15
If you extracted the package on your desktop, it created a folder called bcm43xx-gtk-installer-0.2.1 (or 0.2, or whatever)... in the bcm43xx folder (which is inside that folder) is the firmware. It's already been run through fwcutter.

Assuming you extracted the package on your desktop, if you go to a terminal and type:
```
cd ~/Desktop/bcm43xx-gtk-installer-0.2.1/bcm43xx/
```
It should take you to the directory where the firmware is.

Then you can type the following two lines:
```
sudo cp *.fw /lib/firmware/
sudo cp *.fw /lib/firmware/`uname -r`
```

And that installs the firmware. Then you might have to unplug/reinsert your wireless device (if it's not built in), or run **modprobe bcm43xx** to load the kernel module. The graphical installer does the same exact thing.

---

### Post by boomcat on 2007-08-16
This worked like a CHARM on my Linksys PCI wireless card with the Broadcom 4306 chipset. It worked the first time and it was fast, and never returned any cryptic error messages. I just cut and pasted the commands from the browser; didn't even retype (beware misplaced carriage returns on your display!) Did the procedure, restarted, and the Wireless manager (I use wicd) immediately found my network (and no less than SEVEN others!). All I had to do was enter my static IP numbers and the WEP password and press "Connect".

THANKS!

---

### Post by rainwalker on 2007-08-16
> **bmartin said:**
> If you extracted the package on your desktop, it created a folder called bcm43xx-gtk-installer-0.2.1 (or 0.2, or whatever)... in the bcm43xx folder (which is inside that folder) is the firmware. It's already been run through fwcutter.

Assuming you extracted the package on your desktop, if you go to a terminal and type:
```
cd ~/Desktop/bcm43xx-gtk-installer-0.2.1/bcm43xx/
```
It should take you to the directory where the firmware is.

Then you can type the following two lines:
```
sudo cp *.fw /lib/firmware/
sudo cp *.fw /lib/firmware/`uname -r`
```

And that installs the firmware. Then you might have to unplug/reinsert your wireless device (if it's not built in), or run **modprobe bcm43xx** to load the kernel module. The graphical installer does the same exact thing.


Ohhh! Thank you, I'll try that :)
I'm guessing I don't have to be connected to the internet for that, right?

---

### Post by bmartin on 2007-08-16
If you've already downloaded the installer and extracted it, then no, you don't need an internet connection. The firmware is included with the installer as of 0.2.1. That will change with 0.3.0.

---

### Post by rainwalker on 2007-08-16
YES! It worked, thank you so much!

Will it continue to work even if I upgrade to Gutsy when it comes out, or will I have to do this again?

---

### Post by bmartin on 2007-08-16
You might have to run the program again. Here's the reason:

The bcm43xx kernel module (which uses the firmware to run your wireless connections) looks in either /lib/firmware/ or /lib/firmware/`uname -r`/ (where `uname -r` is your kernel version); I'm not really sure which one it uses. When a new kernel comes out, if it's looking in the `uname -r` directory, then you need to place the firmware there again.

You could prevent having to copy the firmware again by creating a script that executes at every boot. In fact, I think that's a great idea, and I'm going to write such a script right now. It'll be installed by default in the future... it might even make it into 0.3.0.

I'll post instructions and a link to the file when I'm done, in case anyone wants to use it.

---

### Post by rainwalker on 2007-08-16
Okay, I rebooted and for some reason the computer always wants to use the wired connection rather than the wireless one. Is it alright if I ask for help on this thread or should I make a new one?

---

### Post by bmartin on 2007-08-16
What do you mean by "it always wants to use the wired connection"? If you have both available, then Ubuntu will use your wired connection by default.

---

### Post by rainwalker on 2007-08-16
What I mean is, in the network manager window, the box for "Wired Connection" is checked my default, rather than the "Wireless Connection" one.
I know that it can be set to use the wireless by default because it does on my laptop (my sister's is the one I'm working on). Hers is an old Inspiron 7500, though, so the wired connection is through some card plugged into the side of the computer, above where you slide in the wireless card. On my laptop, there's an ethernet port on the back. I don't know if that's why it's confused or not.
If it's any help, here are the two "/etc/network/interfaces" files:

Mine:> auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid xxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx

auto ath0


Hers:> auto lo
iface lo inet loopback

iface eth0 inet dhcp
wireless-essid xxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxx

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by bmartin on 2007-08-16
Try adding the following configuration:
```
auto lo
iface lo inet loopback

**auto eth0**
iface eth0 inet dhcp

**auto ath0**
iface ath0 inet dhcp
wireless-essid xxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx

```

---

### Post by rainwalker on 2007-08-16
That's my interfaces file, the one that works the way I want it to. Hers is the second one.

I was going to just change it so it looks like mine, but you clearly know more about this stuff than I do.

---

### Post by bmartin on 2007-08-16
Sorry, my mistake.
```
auto lo
iface lo inet loopback

**auto eth0**
iface eth0 inet dhcp
wireless-essid xxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxx

**auto eth1**
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by rainwalker on 2007-08-16
Alright, I'll reboot and tell you what happens...

---

### Post by rainwalker on 2007-08-16
Arg, it didn't work.
For some reason, I still have to go into the Network Settings and disable the wired connection before it will work.

---

### Post by Chepe on 2007-08-16
I just have to say thank you to the maker of this thread! Finally I got my wireless card working, I've been trying for a pretty long time now the get online. As a novice user this HOWTO was perfect!! :)

---

### Post by bmartin on 2007-08-16
> **rainwalker said:**
> YES! It worked, thank you so much!

Will it continue to work even if I upgrade to Gutsy when it comes out, or will I have to do this again?
I wrote a script that'll copy the firmware over automatically when a new kernel is used. That way, you don't have to install the firmware every time your kernel is updated. It installs itself as an init process. **Note: this program does not install the firmware; if the firmware is already installed, this program will ensure that it exists in all kernels.**

Here's how to install it:
```
wget http://blakecmartin.googlepages.com/S05firmware-init-script
chmod 755 S05firmware-init-script
sudo ./S05firmware-init-script
rm S05firmware-init-script
```

To remove it, run **sudo /etc/init.d/S05firmware-init-script remove**. Note that this won't remove the firmware; it merely removes the init script that copies the firmware over to all kernels. You could also keep the original installer (instead of removing it, like in the code above) and use that to remove the init script.

Unless I decide this script is unwise for some reason, in future installers, this script will be installed when the firmware is installed and removed when the firmware is removed.

---

### Post by rockballad on 2007-08-17
Hic, don't know why after following the first post, in Network Settings dialog, there're only 2 types of connection: Wired Connection and Modem Connection, missing Wireless connection as before. Could you tell me how to do next? Thanks so much!

---

### Post by bmartin on 2007-08-17
If you haven't restarted yet, try restarting your computer.

If that doesn't work, type **dmesg | less** into a terminal and look for output related to your wireless device. Either there was an error loading the drivers or you don't have a Broadcom wireless device. Post all the lines related to your WiFi device in here.

---

### Post by b52doc on 2007-08-17
I got my wireless network to work finally. I have a Microsoft MN-720 card with a BCM 43xG chipset. I first tried running the program from this thread and it didn't work at all. I then tried downloading the  firmware from ubuntu.cafuego.net / Installed the firmware and I could see networks but couldn't connect consistently, slow speeds, dropping connection etc. I installed Wicd network manager and then ran the program from this thread and it selected firmware as my best choice. Since then everything has been working! :) Not exactly sure why it worked, but I am not complaining.:KS

---

### Post by bmartin on 2007-08-17
What do you mean "it didn't work at all"? Did you get an error of some kind?

---

### Post by b52doc on 2007-08-17
No error message. Couldn't detect any wireless networks, it was like it had no effect.

---

### Post by IndyBart on 2007-08-18
Thank you so much - I had been working on this for days with no success. Your solution work instantly!!!

One question - is there a way to configure a static IP address instead of DCHP?

Thanks - IndyBart

---

### Post by bmartin on 2007-08-18
> **IndyBart said:**
> One question - is there a way to configure a static IP address instead of DCHP?
That depends on which program you're using to connect. If you're in the Network settings in the Administration folder, there's a drop-down menu under "Connection Settings" next to "Configuration" with a "Static IP Address" option. In WICD, it's under the "Advanced Settings" folder.

---

### Post by bmartin on 2007-08-18
> **b52doc said:**
> No error message. Couldn't detect any wireless networks, it was like it had no effect.
What are the relevant lines from the **lspci** command? Also, could you post the log file?

---

### Post by pbureau on 2007-08-18
I have a Gateway M520x Laptop with a purchsed BCM4605 from the internet, and your program worked like a charm !!! thank you and Amazing work my friend... I am storing this program on my spare HDD just in case.... :))

Cheers and Thank you.

---

### Post by v604mustangjoe on 2007-08-18
MADE A BREAK THROUGH. Wireless network card only works with my microsoft router when the router is in B mixed mode, i had it in G mode only. Apparently the driver might not allow G mode to work or something.

figured this out when it worked on my neighbors network, but not on my own.

Now there is nothign holding me back from ubuntu!

---

### Post by ronak on 2007-08-18
I have a Dell Latitude D610 with a Broadcom 4318. After multiple attempts at getting the wireless working (at one point I could detect all wireless networks, but not connect to them) your method worked like a charm! Thanks!

---

### Post by bmartin on 2007-08-18
> **pbureau said:**
> I have a Gateway M520x Laptop with a purchsed BCM4605 from the internet, and your program worked like a charm !!! thank you and Amazing work my friend... I am storing this program on my spare HDD just in case.... :))

Cheers and Thank you.
You're welcome. I update the program somewhat frequently, so there might be a newer version by the time you need to use it again. I'm always looking for ways to increase the number of people this technique works for.

A 4605? Which installation did the program recommend? Did it say it couldn't detect a Broadcom chipset, or did it say it detected an incompatible one? If you don't remember, you can check the log.

---

### Post by bmartin on 2007-08-18
> **v604mustangjoe said:**
> MADE A BREAK THROUGH. Wireless network card only works with my microsoft router when the router is in B mixed mode, i had it in G mode only. Apparently the driver might not allow G mode to work or something.

figured this out when it worked on my neighbors network, but not on my own.

Now there is nothign holding me back from ubuntu!
Congrats!

Well, actually, with the firmware, you get a maximum speed of 11Mbps, but with the ndiswrapper method you can get G speed (54Mbps). I believe the ndiswrapper works better in general and doesn't have any drawbacks. The firmware will eventually get to a state where it's more usable.

---

### Post by chastom on 2007-08-18
Thanks darkNoob and bmartin . I followed your initial instructions, and all went easy as 3.1417. :-)
My Dell True Mobile 1300 - Broadcom 4306- now works like a charm.
I dual boot Ubuntu 7.04 (2.6.20-16 generic), and Windows XP pro on an old Dell 5150 Laptop.

---

### Post by VistaBoard on 2007-08-18
> **Jonathan Harford said:**
> Alas, the script did not work for my HP V5101US laptop.

Well, that's not entirely true. After running the script, my WPA router started to show up under knetworkmanager and I was able to connect to it. AND I was even able to get to google.com!

But moments later -- though nothing had apparently changed -- I couldn't get to a single website. Looking at my System logs, I saw a lot of "CCMP: received packet without ExtIV flag"  errors had begun to crop up.

To make matters worse, as soon as I had installed the firmware, my mouse started acting all flaky (as described here: [https://bugs.launchpad.net/ubuntu/+bug/84119)](https://bugs.launchpad.net/ubuntu/+bug/84119)). When I added "i8042.nomux=1" to GRUB, this flakiness went away, but the mouse and keyboard started to hang at random.

I feel like I'm so close! Advice?

I use the compaq version of the same laptop, This fix made my wireless card work flawlessly, even the blue indicator light works. Installed on a fresh copy of ubuntu.

vB

---

### Post by IceCap on 2007-08-18
Dell Latitude 840C with TrueMobile 1450 running Feisty.
Installer came up with unsupported so installed ndiswrapper.  Worked like a charm running at 54Mbps.
  Very well put together.

  This thread should be sticky so that people don't miss this.

  Thanks

  IC

---

### Post by carbon-12 on 2007-08-19
Hello, sorry if this was answered earlier in the thread but I didn't feel like going through 43 pages of comments! :)

I have *NO* access to a wired internet connection, only through an unencrypted wireless connection. Is there a way to download a single package that I can install that includes everything I need (including NM) to get my integrated broadcom card to work? 

I've tried repeatedly before, where I had to constantly jump back and forth between Windows and my Ubuntu installation, downloading each package and their dependencies( a very tedious task) and could never get it to work.

---

### Post by bmartin on 2007-08-19
> **carbon-12 said:**
> Hello, sorry if this was answered earlier in the thread but I didn't feel like going through 43 pages of comments! :)

I have *NO* access to a wired internet connection, only through an unencrypted wireless connection. Is there a way to download a single package that I can install that includes everything I need (including NM) to get my integrated broadcom card to work? 

I've tried repeatedly before, where I had to constantly jump back and forth between Windows and my Ubuntu installation, downloading each package and their dependencies( a very tedious task) and could never get it to work.
I don't blame you for not wanting to sift through the comments.

Whether or not you can download/install easily depends on your Broadcom chipset version (you can check it using lspci). If it's a 4303/6/11/12/xG, then all you need is the firmware. The installer for the firmware can be found on the first page at the bottom of the first post.

If you have any other chipset, tsk tsk. You'll need ndiswrapper, which you won't be able to compile without a wired internet connection. ndiswrapper normally comes as source code, but I could make a tarball or a DEB package with ndiswrapper in it. You'll also need the Windows driver, and you'll need to know how to install it all.

If you want 54Mbps speed, you *must* use ndiswrapper. The firmware only works at 11Mbps.

---

### Post by likemindead on 2007-08-19
Please help!?

```
Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended.
** Kernel info: Linux owner-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
 * ndiswrapper installation attempted
 * End of ndiswrapper installation
** uname -a
Linux owner-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

** ndiswrapper -l
***** : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

** sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:13:C6:9A
                    ESSID:"CIA"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


** tail /var/log/kern.log
Aug 19 17:55:47 owner-laptop kernel: [ 1056.852000] usbcore: deregistering interface driver ndiswrapper
Aug 19 17:56:37 owner-laptop kernel: [ 1107.108000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 19 17:56:37 owner-laptop kernel: [ 1107.132000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
Aug 19 17:56:37 owner-laptop kernel: [ 1107.136000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Aug 19 17:56:37 owner-laptop kernel: [ 1107.144000] ndiswrapper: using IRQ 22
Aug 19 17:56:37 owner-laptop kernel: [ 1107.516000] wlan0: ethernet device 00:14:a4:25:8d:b5 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
Aug 19 17:56:37 owner-laptop kernel: [ 1107.520000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 19 17:56:37 owner-laptop kernel: [ 1107.524000] usbcore: registered new interface driver ndiswrapper
Aug 19 17:56:37 owner-laptop kernel: [ 1107.532000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Aug 19 17:56:37 owner-laptop kernel: [ 1107.552000] ADDRCONF(NETDEV_UP): eth1: link is not ready

** tail /var/log/syslog
Aug 19 17:56:37 owner-laptop kernel: [ 1107.108000] ndiswrapper version 1.47 loaded (smp=yes)
Aug 19 17:56:37 owner-laptop kernel: [ 1107.132000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
Aug 19 17:56:37 owner-laptop kernel: [ 1107.136000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Aug 19 17:56:37 owner-laptop kernel: [ 1107.144000] ndiswrapper: using IRQ 22
Aug 19 17:56:37 owner-laptop kernel: [ 1107.516000] wlan0: ethernet device 00:14:a4:25:8d:b5 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
Aug 19 17:56:37 owner-laptop kernel: [ 1107.520000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 19 17:56:37 owner-laptop kernel: [ 1107.524000] usbcore: registered new interface driver ndiswrapper
Aug 19 17:56:37 owner-laptop kernel: [ 1107.532000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Aug 19 17:56:37 owner-laptop NetworkManager: <debug info>^I[1187564197.912699] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_14_a4_25_8d_b5'). 
Aug 19 17:56:37 owner-laptop kernel: [ 1107.552000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by bmartin on 2007-08-19
> **likemindead said:**
> Please help!?
You're going to have to be a little bit more specific.

You installed the correct driver. Your WiFi card is currently being detected. It found a wireless network called "CIA". It seems to support WEP and WPA. Everything looks good. What problem are you having?

---

### Post by likemindead on 2007-08-19
It seems to be going through the motions, but then there's no juice. Everything looks good, but when I go to System > Administration > Network and uncheck Wired Connection and check Wireless Connection and configure the Wireless Properties I still have no Internet. I have my sisters laptop here (running Vista) and it's connecting to the Wireless just fine. You, sir, are a gentleman and a scholar, thanks for your wisdom and patience....

EDIT: Also, I'm not sure I fully understand what eth0, eth1, and lo are. I have two icons in my notification area: (1) "Wired Network Connection" which I can left click on to get "Manual Configuration," and (2) "Network Connection: eht0" which I can right click on, go to Properties, and change a few separate things. I have no idea where my Network Manager has gone. I'm a terrible human being and if you're ever in Texas, I owe you a few rounds for sure.... :EDIT

EDIT2: Is there any other log files or codes I can post to help? :EDIT2

---

### Post by bmartin on 2007-08-19
Actually, my workplace was going to relocate me to San Antonio, but I declined the job because they were going to make me work 3.5 12-hr days (instead of 5 8-hr days) and I'd be working a swing shift instead of regular hours. I'm waiting for my girlfriend to get a job so we can move somewhere. She majored in Aerospace Engineering, so Texas is a possibility; she's interviewing in SC (GE), then MA (Raytheon).

If you've got the newest version of the installer (0.3.0), try installing and using wicd to connect to the wireless network. You'll have to open up a terminal and type **wicd** to start the program. wifi-radar is also a good program; I've tried them all and wicd is by far my favorite (and the most intuitive). For some reason, using different software to connect makes a big difference.

---

### Post by likemindead on 2007-08-19
San Antonio is an awesome town. But then again, it is in Texas. ;) The missus and I are actually moving back to England in about 18 months, but Texas will always be home.

I'll try wicd and get back to ya. Uber-THANKS once again....

EDIT: It's working, it's working, it's working!!! Thank you so much for the help. You make Ubuntu what it is--a place for freedom. Holy $h1t, that was cheesecore, but I mean it.... thanks.... :EDIT

---

### Post by rockballad on 2007-08-20
I have followed your instruction, now what I get here is the driver seems to be installed. But there's still no wireless signal. Please take a look at my output resutls:

> 
testxpc@testxpc-laptop:~$ ndiswrapper -l

bcmwl5 : driver installed

        device (14E4:4311) present (alternate driver: bcm43xx)



> 
testxpc@testxpc-laptop:~$ sudo modprobe -l |grep 43xx

/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko

/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko


> 
testxpc@testxpc-laptop:~$ sudo iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"

          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   

          Bit Rate=1 Mb/s   Tx-Power=18 dBm   

          RTS thr:off   Fragment thr:off

          Encryption key:off

          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



> testxpc@testxpc-laptop:~$ iwlist scanning

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning


> testxpc@testxpc-laptop:~$ lspci -nn

03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 02)



> testxpc@testxpc-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network UNCLAIMED     

       description: Network controller

       product: Dell Wireless 1390 WLAN Mini-PCI Card

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@03:00.0

       version: 02

       width: 64 bits

       clock: 33MHz

       capabilities: cap_list

       configuration: latency=0

       resources: iomemory:b6000000-b6003fff irq:10



I have 2 questions:

1/ How to show Wireless connection in the 
System > Administration > Network box? Some days before, it was still there, but now for some unknown reason, it lost.

2/ If I install wicd, wifi-rada's lost, and vice versa. Even it makes my Internet connection lost. I have to restart to connect again.

I read your thread from last week. This morning, have the driver installed. But I'm stuck here. Please help me out. Thanks a lot!

---

### Post by bmartin on 2007-08-20
> **rockballad said:**
> 1/ How to show Wireless connection in the 
System > Administration > Network box? Some days before, it was still there, but now for some unknown reason, it lost.

2/ If I install wicd, wifi-rada's lost, and vice versa. Even it makes my Internet connection lost. I have to restart to connect again.
From your output above, I noticed that the **eth1** device had no output when **iwlist scanning** was run (you should probably run **sudo iwlist scanning**.

wicd and wifi-radar conflict. Installing one necessarily removes the other. Does anything appear in the wicd GUI? If you're using System > Administration > Network, that takes you to Network Manager, which you don't want to be using anyways.

Another thing you can try is using ndiswrapper instead of the firmware (or vice-versa; I didn't see your log). They each have their advantages.

---

### Post by Rykielz on 2007-08-20
I installed this. I can see the wireless card in the device manager, but I cannot get it to work.
I am running Wubi on a HP dv2000 laptop, this laptop has a switch on the front to enable and disable the wireless adapter. But even though the switch is turned on, the light that shows me the status stays orange (disabled) [It needs to be blue for it to be enabled, as per its functioning in Vista]
Anyone know what might be wrong?
Thanks

[The wifi card is a Broadcom 4312 Rev 2]

Also this is not related to the wifi issue, but I am running ubuntu on amd 64x2 turion TL-56 processor, but whenever I try to install a amd64 version of a program, it tells me "invalid architecture" but when I use i386 it works perfectly.

---

### Post by bmartin on 2007-08-20
> **Rykielz said:**
> I installed this. I can see the wireless card in the device manager, but I cannot get it to work.
I am running Wubi on a HP dv2000 laptop, this laptop has a switch on the front to enable and disable the wireless adapter. But even though the switch is turned on, the light that shows me the status stays orange (disabled) [It needs to be blue for it to be enabled, as per its functioning in Vista]
Anyone know what might be wrong?
Thanks
My laptop does that, too; the light doesn't turn on at all on mine until I'm connected to a wireless network. The built-in wireless program isn't very good (network-manager); I recommend using something else, such as wicd or wifi-radar. If you plan on using WPA, I **highly** recommend wicd; it'll make everything easier. After you install one of them, use **sudo wifi-radar** or **wicd** or **wicd-tray** to run one of them. For some reason, switching your wireless connection manager makes a huge difference for many users.

Also, run **sudo apt-get remove network-manager** if you install one of the other programs. Having multiple wireless connection managers running at once will cause you grief.

> **Rykielz said:**
> Also this is not related to the wifi issue, but I am running ubuntu on amd 64x2 turion TL-56 processor, but whenever I try to install a amd64 version of a program, it tells me "invalid architecture" but when I use i386 it works perfectly.
I imagine you're running a 32-bit version of Ubuntu. That's probably best, at least until you're used to the OS. Using the 64-bit version causes some issues; I know that you need to use a wrapper with Firefox plugins and I believe some packages (such as Wine) don't have 64-bit versions.

---

### Post by AliL on 2007-08-20
Hi there, I'm a bit confused as to what's going on because I had my 4306 chipset working (inside a Belkin F5D7010 card) using this tool and was able to just "Install BCM43xx firmware" and it was working.

However now with version 0.3 of this tool, it says I have an incompatible chipset and suggests that I install the ndiswrapper tool.

Is this a bug in the program or should it have done this last time but managed to work without doing it.

P.S. The reason for reinstalling is that I had to completely reinstall Ubuntu because I broke it. (I thought it was impossible though, oh well).

What is the suggested route to take, install with ndiswrapper like version 0.3 suggests, override this and go ahead and install the BCM43xx firmware instead, or go back to version 0.2.1 and use that again?

Thanks, AliL

---

### Post by bmartin on 2007-08-20
Yes, it's a bug, and I found the bug and have fixed it. Go ahead and use the firmware again.

Thank you for finding this; it's the result of sloppy coding on my part when I introduced an  earlier bug fix. I had a couple if statements that needed to be combined into an if/else clause.

Everyone who uses 0.3.0 (except the BCM43xG users) will receive a message saying that they have an incompatible device (or no Broadcom device at all). I'll package a new version today with the fix (I just tested it) and let DarkN00b know to remove 0.3.0 and leave 0.2.1 up until we're sure the newest one is OK.

---

### Post by darkmaer on 2007-08-20
THANKYOU SOOO MUCH!!!! now i feel like i didn't waste $50 only a mere couple of months back.:KS

---

### Post by NYCmob79 on 2007-08-20
Thank you for this script... I worked for me. It recommended me to do the ndiswrapper, but I ignored that and installed the firmware which solved my problem, I read on another place that my card only needed a firmware update, but that site's link to the firmware was expired. I have a Linksys WPC54G

I am trying Linux Ubuntu again, in the past I have tried Red Hat and SuSe, but its been years since, due to the OS not supporting wireless networks it turned me away. Hopefully this time around I'll stay with it :)

---

### Post by drspastic on 2007-08-20
Did not work. Still can't get the Wireless Network icon back in Network Manager. Why is this such hard work? Are the supported cards guaranteed to work?

---

### Post by bmartin on 2007-08-20
> **NYCmob79 said:**
> Thank you for this script... I worked for me. It recommended me to do the ndiswrapper, but I ignored that and installed the firmware which solved my problem, I read on another place that my card only needed a firmware update, but that site's link to the firmware was expired. I have a Linksys WPC54G

I am trying Linux Ubuntu again, in the past I have tried Red Hat and SuSe, but its been years since, due to the OS not supporting wireless networks it turned me away. Hopefully this time around I'll stay with it :)
Is it a USB device? My program is crude in that it only detects PCI devices, but your chipset is a 4306 which is 100% firmware compatible.

If it's a USB device, what's the output of **lsusb**? (So that I can detect it in future versions)
If it's not a USB device, what's the line from **lspci** that talks about your WiFi card?

---

### Post by bmartin on 2007-08-20
> **drspastic said:**
> Did not work. Still can't get the Wireless Network icon back in Network Manager. Why is this such hard work? Are the supported cards guaranteed to work?
Does your wireless device show up if you type **iwconfig** into a terminal? If so, what's the output of **sudo iwlist scanning**?

---

### Post by pat3691 on 2007-08-20
How do I fix this.  I spend too many hours (and I mean it) to make this .... wireless card working without any success.  I have enough of looking everywhere to find a solution.

This solution seemed pretty simple but again, I have no success...


root@PatLinux:/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3# id
uid=0(root) gid=0(root) groups=0(root)
root@PatLinux:/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3# pwd
/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3
root@PatLinux:/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3# ls -al ../
total 88
drwxrwxrwx 3 root    root     4096 2007-08-20 21:13 .
dr-xr-xr-x 5 root    root     4096 2007-08-20 21:12 ..
drwxrwxrwx 3 patrice users    4096 2007-08-16 17:59 bcm43xx-gtk-installer-0.3
-rwxrwxrwx 1 patrice patrice 71680 2007-08-20 21:07 bcm43xx-gtk-installer-0.3.tar
root@PatLinux:/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3# ls -al
total 48
drwxrwxrwx 3 patrice users 4096 2007-08-16 17:59 .
drwxrwxrwx 3 root    root  4096 2007-08-20 21:13 ..
-rwxrwxrwx 1 patrice users 3940 2007-08-16 09:13 bcm43xx-ndiswrapper.sh
-rwxrwxrwx 1 patrice users 2501 2007-08-16 17:56 bcm43xx.sh
-rwxrwxrwx 1 patrice users 5303 2007-08-15 21:43 installer.py
-rwxrwxrwx 1 patrice users  454 2007-08-16 09:13 LICENSE
-rwxrwxrwx 1 patrice users  520 2007-08-16 09:07 README
drwxrwxrwx 2 patrice users 4096 2007-08-15 20:55 READMEs
-rwxrwxrwx 1 patrice users  794 2007-08-16 17:52 S05firmware-init-script
-rwxrwxrwx 1 patrice users  245 2007-08-10 01:05 stats-logger
-rwxrwxrwx 1 patrice users  486 2007-08-15 19:41 wcm.sh
root@PatLinux:/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3# ./installer.py
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
./installer.py:46: Warning: invalid (NULL) pointer instance
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
./installer.py:46: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
./installer.py:61: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  sw = gtk.ScrolledWindow()
./installer.py:69: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  sw.add(textview)
./installer.py:69: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  sw.add(textview)
./installer.py:69: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  sw.add(textview)
./installer.py:69: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  sw.add(textview)
./installer.py:69: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  sw.add(textview)
./installer.py:69: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  sw.add(textview)
./installer.py:69: GtkWarning: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed
  sw.add(textview)
./installer.py:69: GtkWarning: gdk_keymap_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
  sw.add(textview)
./installer.py:69: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  sw.add(textview)
Segmentation fault (core dumped)
root@PatLinux:/home/patrice/Wireless/gtk/bcm43xx-gtk-installer-0.3#

---

### Post by bmartin on 2007-08-20
Pat, don't run the installer as root.

---

### Post by pat3691 on 2007-08-20
> **bmartin said:**
> Pat, don't run the installer as root.

I've never thought that being root would prevent things to work!  Anyways, that part worked thx for this...

But I still don't see my wireless card.](*,)

---

### Post by rockballad on 2007-08-20
Thank you, bmartin for your reply. But I'm still stuck there and don't know what to do now.

Sorry to interrupt your current discussion, but yesterday, when I typed "sudo iwconfig", it did show eth1,

```
testxpc@testxpc-laptop:~$ sudo iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311" 
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

but today, after uninstall, reinstall, I don't see eth1 anymore. I'm using Compaq Presario V6000Z, the wireless card is:

```
testxpc@testxpc-laptop:~$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Network controller 
       product: Dell Wireless 1390 WLAN Mini-PCI Card 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@03:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: iomemory:b6000000-b6003fff irq:10 

```

Please tell me if the eth1 config above is correct or not. If it's correct, what do I need to do to post the laptop information or installing log here. Thanks so much.

---

### Post by bmartin on 2007-08-20
> **pat3691 said:**
> I've never thought that being root would prevent things to work!  Anyways, that part worked thx for this...

But I still don't see my wireless card.](*,)
It causes failure because of how Python's GTK support works. It was having a hard time accessing your display.

If you type **iwconfig** into a terminal, does it show your wireless device? The built-in network manager doesn't work well for most users. I highly recommend **wicd**, but **wifi-radar** is OK.

---

### Post by MystaMax on 2007-08-20
I wanted to stop in and show my appreciation for this utility. It worked like a charm on my Dell Latitude D610 w/ Broadcom 4318. 

It took all of 5 minutes to complete, reboot, and access to the network was granted. Previously, I'd read many other tutorials and couldn't getting it going. Great job!

Now I'll see how good network-manager will work w/ encryption on my various networks. Otherwise I'll be moving to WICD.

---

### Post by bmartin on 2007-08-20
> **rockballad said:**
> Please tell me if the eth1 config above is correct or not. If it's correct, what do I need to do to post the laptop information or installing log here. Thanks so much.
Well, for starters, in 0.3.0 I accidentally introduced a bug that detected your WiFi card as unsupported by the firmware (when, in fact, it **is** supported). Try running the installer again, but this time select the firmware installation.

When iwconfig shows your device again, stop running installers. If it shows up and you still can't connect, you need to try something different. Using the wicd program to connect (as opposed to the built-in network manager) often solves the problem.

---

### Post by rockballad on 2007-08-20
Yeah, I'm still following your thread. Now I see the eth1. But still can't connect to wireless. I'm using wifi-radar  but it doesn't show any connection. Here's the output in terminal (running log)

```
testxpc@testxpc-laptop:~$ sudo wifi-radar
dhclient3 --version 2>&1
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        no wireless extensions.

```

Is it expected to auto detect wireless network and show in the box? Or do I have to "New" a connection? And if so, what's the general setting? (Wifi option: Mode, channel...) 

Many people here got success. Hic, keep going on...

---

### Post by pat3691 on 2007-08-20
> **bmartin said:**
> It causes failure because of how Python's GTK support works. It was having a hard time accessing your display.

If you type **iwconfig** into a terminal, does it show your wireless device? The built-in network manager doesn't work well for most users. I highly recommend **wicd**, but **wifi-radar** is OK.

Nope It does not show with iwconfig

patrice@PatLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


I installed wicd as you suggested and does not show up there either

](*,)

---

### Post by bmartin on 2007-08-20
My only suggestion at this point is to try WICD. You can install it with the 0.3.0 installer or by using the instructions [here]("http://blakecmartin.googlepages.com/wicd.html"). I hope that detects your wireless device. It seems strange to me that you can see your device in the terminal, yet the network connection software doesn't see it.

---

### Post by bmartin on 2007-08-20
pat, please post your install.log file. When posting, under the Additional Options section, use the Manage Attachments button to attach the log. It keeps the thread cleaner :KS

The fact that it doesn't show up in iwconfig means it won't show up anywhere else. Your system simply isn't detecting the device for one reason or another.

---

### Post by pat3691 on 2007-08-20
> **bmartin said:**
> pat, please post your install.log file. When posting, under the Additional Options section, use the Manage Attachments button to attach the log. It keeps the thread cleaner :KS

The fact that it doesn't show up in iwconfig means it won't show up anywhere else. Your system simply isn't detecting the device for one reason or another.


Well I don't what I am doing wrong, looks like I am the only that cannot make it work on this forum!!!!

Thanks for th help and hopefully my log file will help you troubleshoot and eventually fix my problem!  Looking forward to it

Thx again

---

### Post by rockballad on 2007-08-21
A good news:

The wireless connection has appeared on the Network dialog, and the wireless LED on the laptop has lighted on (blue, not red anymore). 

But now I don't know how to connect to my wireless network. I'm using router WRT54GC. Both wicd and the network manager (System->Admin->network) aren't able to detect wireless automatically. Could you please tell me how to connect to my wireless network. Thanks so much!

---

### Post by bmartin on 2007-08-21
First of all, does the wireless network show up if you type in **sudo iwlist scanning**? Second, are you using encryption of some sort?

---

### Post by DarkN00b on 2007-08-21
Updated installer and instructions posted. Have a look and remember, feedback is welcome!

---

### Post by rockballad on 2007-08-21
Yes, **bmartin**, here is the output

```
testxpc@testxpc-laptop:~$ sudo iwlist scanning
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```

The second thing, I doesn't really understand about the encryption here, but my router is set password, and in Windows, I have to enter that password in the Share key to connect. Could you tell me how to check the encryption please?

---

### Post by Rykielz on 2007-08-21
> **bmartin said:**
> My laptop does that, too; the light doesn't turn on at all on mine until I'm connected to a wireless network. The built-in wireless program isn't very good (network-manager); I recommend using something else, such as wicd or wifi-radar. If you plan on using WPA, I **highly** recommend wicd; it'll make everything easier. After you install one of them, use **sudo wifi-radar** or **wicd** or **wicd-tray** to run one of them. For some reason, switching your wireless connection manager makes a huge difference for many users.

Also, run **sudo apt-get remove network-manager** if you install one of the other programs. Having multiple wireless connection managers running at once will cause you grief.


I imagine you're running a 32-bit version of Ubuntu. That's probably best, at least until you're used to the OS. Using the 64-bit version causes some issues; I know that you need to use a wrapper with Firefox plugins and I believe some packages (such as Wine) don't have 64-bit versions.


I seem to have messed something up, when I typed in iwlist scanning, I got a message "no wireless extensions" :(
any suggestions on how to solve this?

---

### Post by will71110 on 2007-08-21
This works great...Why is this not a sticky?  Should be.

---

### Post by Parms on 2007-08-21
This worked perfect first time no troubles.... Thank you very much!!!

---

### Post by bmartin on 2007-08-21
> **rockballad said:**
> Yes, **bmartin**, here is the output

```
testxpc@testxpc-laptop:~$ sudo iwlist scanning
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```

The second thing, I doesn't really understand about the encryption here, but my router is set password, and in Windows, I have to enter that password in the Share key to connect. Could you tell me how to check the encryption please?
The encryption here is about the same. You simply choose your encryption type and enter your encryption key. If you're using WPA, you have to install WPA_Supplicant (instructions can be found on the first page), unless you're using WICD, which includes WPA support.

The best way to test whether or not your encryption works is to see if you can connect to an unencrypted network. Most of the time, when people can't connect, it's not their encryption that's the problem; the problem usually lies with the connection manager they're using.

I have another concern, though.
```
eth1      No scan results
```
This means that your wireless device isn't detecting **any** networks. Unless your network is hidden, this is a problem. There might be a switch on your computer (if your device is built-in, like mine) that you have to press in order to enable your wireless scanning.

I'm at my girlfriend's house (until Saturday) and they have a broadcasted SSID and no encryption. At my house, we use WEP. I've never had to connect to a WPA-enabled network. You're best off looking at the wireless encryption post that's sticking in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=136") section (it's at the top of the threads).

---

### Post by bmartin on 2007-08-21
> **Rykielz said:**
> I seem to have messed something up, when I typed in iwlist scanning, I got a message "no wireless extensions" :(
any suggestions on how to solve this?
Using **sudo iwlist scanning** makes a big difference (as opposed to simply **iwlist scanning**).

There might be a switch (if your Broadcom device is a built-in one) that activates your wireless scanning.

---

### Post by Robbie Pence on 2007-08-21
:guitar: :) :KS You guys rock! Sticky this!

I am writing this from a Gateway mx6453  Ubuntu 7.04,
Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

PS: To all those with my hardware, I will be making a howto
of the gateway mx6453 when I get my sound card working.
I already got wireless and Compiz Fusion.

---

### Post by bmartin on 2007-08-21
> **Robbie Pence said:**
> :guitar: :) :KS You guys rock! Sticky this!

I am writing this from a Gateway mx6453  Ubuntu 7.04,
Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

PS: To all those with my hardware, I will be making a howto
of the gateway mx6453 when I get my sound card working.
I already got wireless and Compiz Fusion.
I've been considering having this thread stickied... I'll contact a mod about it.

HOWTOs for computers are great. Right now I'm dealing with my girlfriend's Acer 5050. It's sad... the ENE card reader has no Linux support AFAIK and the ACPI won't work no matter what I do (I recompiled the DSDT file and made an initramfs file, tried the Gutsy kernel, etc.). I hope someone figures out that model some day. Acer computers are awful for many reasons. The hardware is OK, but they had my hard drive split into two partitions of equal size; one partition was intended for use in backing up the other! The ACPI is awful and getting the wireless to work was no easy task in Vista, XP, or Ubuntu. I removed Vista... it's just plain awful. My girlfriend uses Ubuntu primarily but needs XP to log into remote Windows servers.

---

### Post by ponderosajoe20 on 2007-08-21
This worked much better than the previous version.  Thank You very much.


Best Regards,


Joseph Cartwright

---

### Post by bmartin on 2007-08-21
> **ponderosajoe20 said:**
> This worked much better than the previous version.  Thank You very much.


Best Regards,


Joseph Cartwright
Yeah... you're the second person to tell me that. DarkN00b has been testing the recent versions; he's been a big help.

There's also another version coming out. We're going to fork the project into two different installers; one will have **everything** included in the installer (like an offline installer), but the installer will be gigantic and Google might start complaining about bandwidth usage on my page... maybe. We'll see. The other one will be as small as possible, downloading only what's necessary.

The problem I'm facing right now is trimming the size of the ndiswrapper kernel module. I'm trying to "strip" the module so its size is smaller, but when I do, it can no longer be loaded into the kernel. I want to get the DEBs (yep, we're gonna have ndiswrapper DEBs) as small as possible before I put up the newest installer.

---

### Post by rockballad on 2007-08-22
Thank Goodness, I installed successfully. The problem is I selected the wrong driver file from Dell. It must be [http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE)

All right, now I can see the wireless :

```
testxpc@testxpc-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:F9:90:29
                    ESSID:"Codesco"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Now how can I enter and use this wireless? Please tell me, so exciting!

---

### Post by bmartin on 2007-08-22
You can try a few different things (assuming you know the encryption key):
1. Install WICD and try that.
2. Install wifi-radar and try that.
3. Use the built-in network manager (System > Administrator > Network)

They're listed in order of recommendation. WICD comes highly recommended.

---

### Post by rockballad on 2007-08-22
I'm still using wicd. But it doesn't list the wireless network although I can see it by using 'sudo iwlist scaning'. I even run wicd as root (sudo wicd).

Then I click Hidden Network , enter my ESSID, click Connect. But nothing happends. Why is it :confused:

---

### Post by bmartin on 2007-08-22
That's strange... is the behavior the same under wifi-radar?

---

### Post by rockballad on 2007-08-22
Yeah, wifi-radar works. But not really. There's a question mark on the left on each connection. For example:

? Codesco (Signal=full) (Mode=Managed) (802.11=g) 

Hic, what is the next I do now? Thanks for your patience.

---

### Post by DarkN00b on 2007-08-22
> **rockballad said:**
> Yeah, wifi-radar works. But not really. There's a question mark on the left on each connection. For example:

? Codesco (Signal=full) (Mode=Managed) (802.11=g) 

Hic, what is the next I do now? Thanks for your patience.

Click the connection shown, then click the connect button. A dialog will pop up asking you if you want to configure the connection -- click yes. Make sure the essid is correct and set everything else to auto. That should get you connected unless you're using encryption.

EDIT: Oops, I see you are using encryption. You will need to enter your encryption key. If you are using WPA I think you'll need to install 
WPA_Supplicant. See the link on my original post for a howto on encryption.

---

### Post by rockballad on 2007-08-22
There's only Disconnect button. OK, I'll try the WPA_Supplicant. Thanks so much. I'll come back soon.

---

### Post by DarkN00b on 2007-08-22
It says its connected? And nothing happens when you open your browser? If you're not using WPA encryption you don't need WPA_Supplicant.

---

### Post by rockballad on 2007-08-22
Hmm, looks like it's not WPA. Please take a look here

```
testxpc@testxpc-laptop:~$ sudo wpa_supplicant -w -Dndiswrapper -i wlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=3):
     54 54 69                                          TTi             
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='TTi'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1a:73:64:68:cf
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
Segmentation fault (core dumped)
testxpc@testxpc-laptop:~$ 


```


Pls see the screen capture attached here

---

### Post by DarkN00b on 2007-08-22
Well one thing is for sure. You need more help than I can give. I'm going to bed for the night; maybe some sleep will give me better perspective.

---

### Post by horned0wl on 2007-08-22
Hmm...  I'm at my wits end trying to get my laptop 43xx card to connect... See below:

[ATTACH]41306[/ATTACH] Screen Shot Wifi Radar

[ATTACH]41307[/ATTACH] Screen Shot Starfire Wifi Profile

Notes:  
1. I'm using an Acer 3050 laptop with Ubuntu 7.04, and have a Broadcom 43xx Wireless Card.
2. The wireless card works/connects on my laptop's dual-boot XP side.
3. My network router (ssid=starfire) is a Linksys WRG54GS set to ch 11, auto, WPA2-TKIP.
4. My network server is a homebuilt with Windows 2000 Pro.
5. My IWCONFIG doesn't hold past a reboot.  See:

root@starfury:/home/ed# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@starfury:/home/ed# 

any thoughts...?  :confused:

Cheers;

---

### Post by Laynix on 2007-08-22
I almost can't believe I finally got this card working!
I guess I should have just looked on the Ubuntu forums to begin with.
Thanks for the help!

---

### Post by rockballad on 2007-08-22
Hi all,

I'm replying to you all on the wireless network. Here're something I'd like to sum up for one who's beginning to setup wireless with:

[LIST]
[*]Compaq Presario V6000Z
[*]Dell Wireless 1390 WLAN Mini-PCI Card 
[*]Broadcom 4311
[*]Ubuntu 7.04
[/LIST]

You'll need:

Option 1: using bmartin's script on this thread. ndiswrapper is hightly recommended. Thanks bmartin and DarkN00b for your big help.

Option 2: download driver and install manually, hereafter are the good links:
[LIST=1]
[*]Download the RIGHT driver for the notebook at [http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE)
[*]Download the ndiswrapper at [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz) Current version is 1.47. You can check at sourceforge.net for the lastest one.
[*]Follow exactly the first post at [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[/LIST]

OK. Now you can test the wireless network: 
```
sudo iwlist scanning
```

If you see one or more Cell, you got the target!

The last step, you can use wicd or wifi-radar as many people have done well. But for my part, I have to use gnome network manager. Get it like this:
Install:
```
 sudo apt-get install network-manager-gnome
```
then 
```
 nm-applet --sm-disable
```

Done. You now can see the network manager on the system tray. Select the wireless network, enter password and enjoy yourself!

Have fun!

Thanks you all so much!

Cheers,

---

### Post by bmartin on 2007-08-22
> **horned0wl said:**
> 5. My IWCONFIG doesn't hold past a reboot.
So you can't get this to connect at all, or you have to re-run the installer at every boot?

If you have to rerun the installer every time...
[LIST]
[*]And you installed the firmware originally, try typing **sudo modprobe bcm43xx** into a terminal after your computer boots.
[*]And you installed ndiswrapper originally, type typing **sudo modprobe ndiswrapper** into a terminal after your computer boots.
[/LIST]
If one of these does the trick, then the respective kernel module isn't loading up when your computer starts. And if so, my guess is that either the module is blacklisted (in /etc/modprobe.d/blacklist) or it isn't in the /etc/modules file (bcm43xx doesn't have to be in there; it loads by default).

Do you have WPA_Supplicant installed? See the first post on this thread. Another option is to use WICD, which has WPA support built in.

---

### Post by bmartin on 2007-08-22
@rockballad

Thanks for letting us know about the other driver. I downloaded that file from the other page; it's a whopping 52MB. I'll include the newer driver in the current versions so that people don't have to download the huge file.

**To everyone out there whose wireless doesn't yet work: **to get the new driver, I recommend using the [0.3.1]("http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.3.1.tar.gz") (faster download) or [0.2.2]("http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.2.tar.gz") installer (don't use the stable one, as it won't remove the old driver). If you ran the 0.3.1 installer but haven't restarted your computer since, you'll want to enter **sudo rm -r /tmp/bcmw*** into a terminal to remove the cached bcmwl5 drivers.

The 0.3.1 installer comes recommended; as long as you've restarted your computer since you last installed, it will always grab the newest firmware or drivers and it won't download anything that you don't need.

---

### Post by nickc523 on 2007-08-22
I spent 2 or 3 hours trying to find a way to solve this problem.  I'm lucky i found this thread. Works perfectly on my laptop. Compaq Presario V5207NR..... Thanks for making this!!!!

---

### Post by dkrepitD on 2007-08-22
Hi I installed the 0.2.1 after trying the 0.3.1 which didn't work. Gave me this error
> Password:
Traceback (most recent call last):
  File "./installer.py", line 21, in run_installer
    os.system("xterm -e \"" + perform + ' ; ./stats-logger ; echo \'Press CTRL+C to close this window\' ; tail -f 2> /dev/null\"')
NameError: global name 'perform' is not defined
But after installing the 0.2.1 which appeared to work, rebooted my machine, inserted the SSID and WPA Key using Gnome's Network manager, the pc waited for a long time and then told me that it could not onnect to the network.
I took a look at the dmesg output and it gave me this that I found interesting:

> [   33.192000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   33.192000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   33.192000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   33.192000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   33.192000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126

Any Ideas?
this is my card:

> 02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at faff6000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
Any ideas?
Thanks

---

### Post by bmartin on 2007-08-22
Try using ndiswrapper instead of the firmware.

Thanks for the bug notification. The bug has been fixed (I hope).

---

### Post by horned0wl on 2007-08-22
Where'd my post go?  I left a pretty detailed post about 1:00am CST (GMT-6) this morning, and verified that it got there; but this morning, its gone...  Help?

---

### Post by DarkN00b on 2007-08-22
That's odd, I can see it in your profile, but the post is gone. Was this it?

[quote="horned0wl"]Re: HOWTO: Broadcom 43xx based wireless cards the EASY way.

Hmm... I'm at my wits end trying to get my laptop 43xx card to connect... See below:

41306 Screen Shot Wifi Radar

41307 Screen Shot Starfire Wifi Profile

Notes:
1. I'm using an Acer 3050 laptop...[/quote]

I can see that much by going to your profile and finding all posts by you. If I click on it though, it sends me to the first post in this thread. You may want to contact a mod and let them know this has happened.

EDIT: wait a minute, it *is* there. It is post #500.

---

### Post by bmartin on 2007-08-22
Your WPA driver is wrong. It should be one of the following (probably **wext**):
[LIST]
[*]hostap = Host AP driver (Intersil Prism2/2.5/3)
[*]atmel = ATMEL AT76C5XXx (USB, PCMCIA)
[*]wext = Linux wireless extensions (generic)
[*]madwifi = Atheros
[*]wired = wpa_supplicant wired Ethernet driver[/LIST]

---

### Post by bapoumba on 2007-08-22
Thread stickied :)

---

### Post by DarkN00b on 2007-08-22
Thank you bapoumba!

---

### Post by horned0wl on 2007-08-22
Ouch!  If thread stickied, how to get interaction on the topic?  Having fun over in Lexmark printers, especially since I actually found a working fix, but here?  Help?

---

### Post by bmartin on 2007-08-22
Did you try correcting your WPA driver?

---

### Post by horned0wl on 2007-08-22
I've wrapped bcmwl5.  I'm unaware of any other driver I should be using...

Cheers;

---

### Post by bmartin on 2007-08-22
You'll need WPA_supplicant from [this page]("http://ubuntuforums.org/showthread.php?t=202834"). bcmwl5 is your Windows (ndiswrapper) driver; you need something else to use WPA.

---

### Post by bapoumba on 2007-08-22
> **horned0wl said:**
> Ouch!  If thread stickied, how to get interaction on the topic?  Having fun over in Lexmark printers, especially since I actually found a working fix, but here?  Help?
Sticking a thread means it's always going to be on the first page of the sub-forum, so easy to find. It's still open for feedback ;)

---

### Post by DarkN00b on 2007-08-22
bcmwl15 is your wireless driver, not your encryption driver. Try setting your driver to wext. I'm leaving for work in minutes, so I'll reply to any further messages around midnight Central time, USA.

---

### Post by split017 on 2007-08-22
last night i installed ubuntu 7.04 for the first time and googled for hours on how to get the wpc54g v1.2 to work. i had no luck. this morning before heading to work, i googled again and came across this thread.

i followed the instructions on post #67 (of this thread) first since i was messing with ndiswrapper last night. then i proceeded with DarkN00b's post #1. it looked like Ubuntu successfully recognized the card, as i was detecting available wireless networks. i did some tinkering and finally it worked.

thanks to DarkN00b for posting those instructions

---

### Post by Viruss on 2007-08-22
viruss@viruss-laptop:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have seen this error all day upon trying to install programs! Someone please help me remedy this issue. =D I need some configuring =P

---

### Post by pat3691 on 2007-08-22
I have made some progress with trying to get this wifi card working (many thx to bmartin) but i still can't connect.

My wifi card is present.
I can see wireless networks in wicd.  
When I try to connect to the network, i am unable to.  I can see that It is trying to get an IP but it can't.  

It is definitly working somehow, I can see info from the router under the network name I am tryin to connect to.

WAP supplicant driver is set to ndiswrapper (I also tried it set to broadcom).  I am not even sure if this does anything in my case, i am not using wap  

I must be close to get connected, what am I missing?

My patience is running low

---

### Post by bmartin on 2007-08-22
You have what's called "dependency hell", although on a small scale.

Try **sudo apt-get --purge remove clvm redhat-cluster-suite system-config-cluster**

If that doesn't work, shoot me a PM. I've had similar problems before and I'd like to know how you fix this one.

**sudo apt-get install -f** (no package name) might help, too (it tries hard to fix errors).

---

### Post by Viruss on 2007-08-22
viruss@viruss-laptop:~$ sudo apt-get --purge remove clvm redhat-cluster-suite system-config-cluster
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package redhat-cluster-suite is not installed, so not removed
Package system-config-cluster is not installed, so not removed
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 492kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131513 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

GRRRRR =P Hopefully someone can help me..please =D

---

### Post by bmartin on 2007-08-23
> **pat3691 said:**
> WAP supplicant driver is set to ndiswrapper (I also tried it set to broadcom).  I am not even sure if this does anything in my case, i am not using wap  

I must be close to get connected, what am I missing?

My patience is running low
What kind of encryption are you using? If you're not using anything, uncheck "Use Encryption"; if you're using WEP, check "Use Encryption", choose WEP, and enter your encryption key. You don't need to worry about WPA if you're not using WPA encryption on the router.

---

### Post by DarkN00b on 2007-08-23
> **split017 said:**
> last night i installed ubuntu 7.04 for the first time and googled for hours on how to get the wpc54g v1.2 to work. i had no luck. this morning before heading to work, i googled again and came across this thread.

i followed the instructions on post #67 (of this thread) first since i was messing with ndiswrapper last night. then i proceeded with DarkN00b's post #1. it looked like Ubuntu successfully recognized the card, as i was detecting available wireless networks. i did some tinkering and finally it worked.

thanks to DarkN00b for posting those instructions

Thank you very much but credit should go to bmartin for creating the installer and doing all the programming work. All I do anymore is test scripts and maintain the howto.

> **pat3691 said:**
> I have made some progress with trying to get this wifi card working (many thx to bmartin) but i still can't connect.

My wifi card is present.
I can see wireless networks in wicd.  
When I try to connect to the network, i am unable to.  I can see that It is trying to get an IP but it can't.  

It is definitly working somehow, I can see info from the router under the network name I am tryin to connect to.

WAP supplicant driver is set to ndiswrapper (I also tried it set to broadcom).  I am not even sure if this does anything in my case, i am not using wap  

I must be close to get connected, what am I missing?

My patience is running low

This is why I put up the notice to read the entire howto before trying the installer. There's a link in there pointing to the encryption thread. Ndiswrapper and Broadcom are not your encryption drivers. I'll reformat the first post to make it clearer.

---

### Post by Donkinator on 2007-08-23
Awesome fix !!! Had my old HP ZD8110us wireless in a jiffy thanks to you. Much Kudos! :):):):):)

---

### Post by rroutzong on 2007-08-23
Someone please help me.  I am new to ubuntu and have tried all of this but I still get the message "ADDRCONF(NETDEV_UP): eth1: link is not ready" when I do a dmesg.  The wireless adapter shows up but will not connect to my router.

---

### Post by pat3691 on 2007-08-23
I am giving up with this wireless sh..... 

I just tried with another router, configured plain, no security set what so ever and I still can't get an IP address.

There are 3 possibilities:

Or I suck
Or Dell sucks
Or Linux sucks

---

### Post by adempewolff on 2007-08-23
holy crap I finally got it to kind of work...  The offline and experimental versions say I have an incompatible chipset but the stable version says its compatible so I installed it, restarted and then as it was rebooting absentmindedly hit the radio on-off key combination (fn-F2) and saw my wireless light go on for the first in-linux time all day.  Now I just need to get it to connect to the network for which I will try wicd.  I wish I could get ndiswrapper to work... 11mbps is kinda slow...  Thanks out to the programs creator and the firmware creator, wish me luck with this wicd install.

*update*
so that worked about as well as I thought it would... wicd doesn't appear to work and it generously removed network manager for me.  I am now using the desktop.  Next time I think I will download the network manager packages before trying to install wicd.  anyway the laptop is no reinstalling ubuntu after which I will once again attempt to install wicd this time probably manually. wish me luck.

*update2*
IT WORKS!!  After yet another fresh install to get network manager back I tried the ndiswrapper once for good measure after upgrading the crap out of everything, restarted and it works.  Only took about 24 hours.

---

### Post by bmartin on 2007-08-24
It's unfortunate that the more people mess around trying to get their wireless to work, the lower the odds are of it working (statistically speaking).

Today I tried the PCLinuxOS Live CD. It asked for my wireless drivers right after I logged in and I instantly had wireless. Perhaps Ubuntu needs something similar; ndiswrapper was ready to load into memory immediately and the dialogs were very intuitive. That's really the best time to get WiFi working.

---

### Post by bmartin on 2007-08-24
> **rroutzong said:**
> Someone please help me.  I am new to ubuntu and have tried all of this but I still get the message "ADDRCONF(NETDEV_UP): eth1: link is not ready" when I do a dmesg.  The wireless adapter shows up but will not connect to my router.
Try using WICD or wifi-radar to connect instead of the built-in network manager. Many people have had great success with WICD.

---

### Post by tsairox on 2007-08-24
Alright,

I have an HPdv5035 and, after running the install script, the wireless light does come on (for the first time in linux!).  However when I open firefox and try connecting to the internet,I cannot connect wirelessly.  What do I do now?

Thanks,

tsai

---

### Post by bmartin on 2007-08-24
Either go to System > Administration > Network and set up your wireless settings or load WICD of wifi-radar to set up your wireless settings.

---

### Post by Gingerjohn on 2007-08-24
Brilliant!!!  I've spent all night in the terminal getting nowhere.  

Five minutes with this and my card and router have just lit up like a christmas tree!!!

Many thanks - now I'm off to bed as my eyes have gone funny from staring at the screen all night!

---

### Post by philven on 2007-08-24
I followed the instructions and got the wireless button to light up, but I can't hit the internet.  I input my wep key in both hex and ascii but still no hit.  I used the firmware only option and did not use the ndiswrapper when it asked me which one I wanted to use.  I have the Broadcom 4306 (rev 03) wireless card on my HP Pavilion zv5370 laptop.  I'm using Ubuntu 7.04.  Anything else I can do?

---

### Post by philven on 2007-08-25
Ok, a little more info.  I use a 2Wire wireless DSL router.  I downloaded Wicd and tried that but it says it does not detect any wireless connections.  So although my wireless card is active it is not getting a signal from the router.  Any suggestions?

---

### Post by philven on 2007-08-25
Last Post.  I am finally on the internet using my wireless card.  Thanks to the person who suggested using the newest drivers with ndiswrapper.  It worked like a charm and Wicd picked up the wireless router.  I was able to input my WEP and I'm on.  Thanks to everyone who posted workarounds, hints, fixes, etc.

---

### Post by bdoe on 2007-08-25
I wasn't sure how to vote on this.  Technically, it worked; but the ndiswrapper method did not.  I have a Microsoft MN-720 PCMCIA card (Broadcom BCM43xG).  When the first time I tried didn't work, I went on a hunch and edited the script to specifically install the 64-bit driver, and that didn't work either.

I'm up and running using the "install firmware" method, but 11M/s kinda blows. :???:

---

### Post by peebly on 2007-08-25
hello

All I have to do is install the firmware to get the pcmcia card working, the problem is I have to rerun the script and select install firmware every time I switch the computer on.

How do I make it so the firmware is installed automatically on boot up.

I am using gutsy.

thank you

---

### Post by peebly on 2007-08-25
hello

Please ignore my last post, I have resolved the issue by using the experimental installer rather then the off-line version.

To the creator, thanks for helping so many people.

5 stars.

:guitar:

---

### Post by Shinji Ikari on 2007-08-25
:KS:KS Another satisfied customer !! I did all the manual configuration the other day and it worked ok. I thought myself pretty clever except the card wouldnt work if i booted my computer with the card already inserted, but i was prepared to live with that. Then I found this, ran it, everything works perfect, even when I start my computer with the card already inserted. Again .. Heaps Thanx :KS:KS

---

### Post by bmartin on 2007-08-25
> **bdoe said:**
> I wasn't sure how to vote on this.  Technically, it worked; but the ndiswrapper method did not.  I have a Microsoft MN-720 PCMCIA card (Broadcom BCM43xG).  When the first time I tried didn't work, I went on a hunch and edited the script to specifically install the 64-bit driver, and that didn't work either.

I'm up and running using the "install firmware" method, but 11M/s kinda blows. :???:
I've never tested the installer on a 64-bit system as I don't have a 64-bit processor to test it on. There are 5 computers in my room right now, all bought within the last 5 years (3 within the last 2 years), all running Ubuntu, and none of them have 64-bit processors.

It seems like the INF and SYS files should be all that's necessary for the 64-bit processor (the SYS file is mentioned in the INF), but I couldn't be sure.

You could try deleting the bcmwl5.sys file and moving the bcmwl564.sys file to where it used to be. Let me know if that fixes the problem, and if it does, I can probably fix the problem in the script tomorrow. It should be as simple as checking whether the kernel is 64-bit or not (as a 32-bit kernel on a 64-bit processor should use the 32-bit driver).

---

### Post by bdoe on 2007-08-26
Well, I tried messing around with the drivers, swapping in 64-bit versions, XP versions, Vista versions...  Basically spent the last day and a half trying to find some combination of Windows drivers to work, and - nothing.  Thankfully, your firmware install script gets me back online within seconds, otherwise I'd have no hair left (has anyone mentioned just how *slooooow* Ubuntu gets when it loses network connectivity?) ;)

I think I just have to face it - there is just no way to make an ndiswrapper'd driver for a Microsoft MN-720.

Anyone know of any PCMCIA 802.11g cards that will work out-of-the-box in Fiesty at the full 54Mbps? :p

---

### Post by StackError on 2007-08-26
Hello:

your script worked and got my wifi working on inspriron 1501 but each time my laptop boots the keyring password box pops up and requires me to enter my admin password before  activating my wireless connection. How do i fix that??

Thankx

S

---

### Post by dpj23 on 2007-08-26
Well, 
         After 3 months of working off and on with wireless configurations this solution worked.  Thanks for the posting....

---

### Post by dpj23 on 2007-08-26
I guess I should point out that I used the 0.3.1v to enable wireless networking....

Thanks Again,
Daniel

---

### Post by oldgoat on 2007-08-26
If you are frustrated by bcm4306 chipset in xubuntu 6.06 - this is it!!  Hats off to Darknoob and related sources!!

Presario 2209 CL

---

### Post by BongoBob on 2007-08-26
I just wanted to say thank you very much, this worked like a charm on my HP Pavilion dv6448se laptop :)

---

### Post by rcatman on 2007-08-26
I'm on a amd 64-bit laptop ( Compaq Presario R3000) and using the bcmwl5.sys with bcm43xx-fwcutter worked great. Network manager didn't display any wireless networks until the second reboot (?). I installed Wicd (wicked!) and things have been perfect!

---

### Post by themadhatter on 2007-08-26
Finally got it. FYI:

Gateway MX6446

The final answer was to install WICD. It was mentioned in this thread, but I couldn't find out how to install it here, so I dug around in the other forums and finally got luck.

Note that I had tried Wifi Radar before, and while it could see the network, it woudn't connect, where WICD did.

Note that your mileage may vary <GRIN>. I have a lot of odd stuff installed on Feisty including Q-Cad (I use it for work), and I don't like Totem or Rhythmbox, replaced them with VLC and Amarok.

Wayne
:guitar:

---

### Post by dahli.llama on 2007-08-26
This worked great on my new Acer 5610Z laptop.  I just used the NDISWrapper and it worked like  a charm.  Thanks a ton!

---

### Post by insub2 on 2007-08-27
THANKS!

( ... sorry for the useless post, but this is the easiest way i know to "bookmark" this thread ... )

---

### Post by bmartin on 2007-08-27
Thread Tools > Subscribe to this Thread

---

### Post by dhar007 on 2007-08-27
Thanks a zillion for this magic potion that helped my Ubuntu loaded laptop see the light of the day (internet!!!) :)

---

### Post by know1.2 on 2007-08-27
Thanks! Worked like a charm on my HP Pavillion 6428CA.  After trying bcm43xx-fwcutter and failing this worked using ndiswrapper.

k1

---

### Post by StackError on 2007-08-28
> **StackError said:**
> Hello:

your script worked and got my wifi working on inspriron 1501 but each time my laptop boots the keyring password box pops up and requires me to enter my admin password before  activating my wireless connection. How do i fix that??

Thankx

S
Is no one monitoring these posts????? how does a Linux newbi gain experience and knowledge if no one answers his questions:confused:?????

---

### Post by bmartin on 2007-08-28
> **StackError said:**
> Is no one monitoring these posts????? how does a Linux newbi gain experience and knowledge if no one answers his questions:confused:?????
Many people are monitoring these posts. However, it's likely that no one monitoring this post knows the answer to your question.

I searched for **keyring wep ubuntu** in Google and found [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898"). It seems to be a bug in the Network Manager program. If you don't want to enter it every time, you could try using a different wireless connection manager, such as WICD or wifi-radar. They can be installed using the newest Broadcom installer. You can also install WICD using the instructions [here]("http://wicd.sourceforge.net/download.php"). You can also install wifi-radar by enabling the Universe repository and adding the wifi-radar package from Synaptic or with **sudo apt-get install wifi-radar**.

---

### Post by Ralph L on 2007-08-28
I know this is not the way to do things but could anybody tell me how to post a message on a Ubuntu Forum so I can get some help.  I have been searching the Forum web pages and see no way to ask for help.  In my case it is on printers.

Thanks, Ralph L

---

### Post by horned0wl on 2007-08-28
Script?  What script?  Where?  Did I miss a post?  Famished...  Please help?

Cheers;

===============================================================================
 Originally Posted by StackError  View Post
Hello:

your script worked and got my wifi working on inspriron 1501 but each time my laptop boots the keyring password box pops up and requires me to enter my admin password before activating my wireless connection. How do i fix that??

Thankx

S
================================================================================

---

### Post by bmartin on 2007-08-28
> **horned0wl said:**
> Script?  What script?  Where?  Did I miss a post?  Famished...  Please help?
The installer.py file that you ran before was a script (as opposed to a compiled program). A script is *a simple program in a utility language* as per the dictionary.com definition.

---

### Post by Ralph L on 2007-08-28
I have a Dell Latitude D610.  I originally installed Ubuntu 6.10.  I ran the commands "sudo aptitude update" and "sudo aptitude upgrade".  Both seemed to work.  Then I clicked "Stable (0.2.1) installer" from the web page.  It seemed to run fine and I created a directory "/home/ralph/bcm43xx-gtk-installer-0.2.1".  Then I double clicked installer.py and Run in Terminal.  I got a window with a default of "install ndiswrapper and Broadcom Windows driver.  I clicked install.  I got Terminal window with "gksudo './install-ndis-broadcom.sh'.  After entering my password a window called "null" popped up with the message "bash: ./stats-logger: No such file or directory".  I also tried the "Install BCM43XX firmware" option and got the same result.

I am completely new at this and don't understand the lingo nor the utility programs available, so any response should be dumbed down.

Any help would be appreciated.

---

### Post by bmartin on 2007-08-28
Try running it, but not in a terminal. Either double-click it and select run, or open a terminal, navigate to it, and run it from the terminal. You're the first person to have this problem.

It sounds like (for some reason) the installer scripts weren't in the proper place.

---

### Post by jtlovell on 2007-08-29
Worked flawlessly for my Linksys wpc54gs!  Thanks for the hard work

---

### Post by shadowplane676 on 2007-08-29
ok, i am new to ubuntu but not linux. i had my BCM4318 working before i crunked the install playing with an ati driver thing in preparation for installing beryl (ATi 200M). i re-installed the system, and the python gtk2 package and i get a bunch of warnings and a segmentation fault on the installer.py script.

> root@Takahashi:/home/stuart/bcm43xx-gtk-installer-0.3.1# python installer.py >> installlog.txt
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
installer.py:46: Warning: invalid (NULL) pointer instance
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
installer.py:46: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
installer.py:61: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  sw = gtk.ScrolledWindow()
installer.py:69: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  sw.add(textview)
installer.py:69: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  sw.add(textview)
installer.py:69: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  sw.add(textview)
installer.py:69: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  sw.add(textview)
installer.py:69: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  sw.add(textview)
installer.py:69: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  sw.add(textview)
installer.py:69: GtkWarning: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed
  sw.add(textview)
installer.py:69: GtkWarning: gdk_keymap_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
  sw.add(textview)
installer.py:69: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  sw.add(textview)
Segmentation fault (core dumped)


im not the greatest at programming or understanding it (networking major). thanks in advance

---

### Post by bmartin on 2007-08-29
@shadowplane: Don't run the installer as root. Run it as a normal user.

---

### Post by horned0wl on 2007-08-29
> **bmartin said:**
> The installer.py file that you ran before was a script (as opposed to a compiled program). A script is *a simple program in a utility language* as per the dictionary.com definition.

Uhhh...  Ahem!  I understand scripts. I've already used them at ./ in here.  Its just that I've apparently missed the post containing the script in question...  Help?

Cheers;

---

### Post by shadowplane676 on 2007-08-29
frusteration messes with you. (reason for running as root earlier) a short nap later and a sudo python command later the scrip runs. HOWEVER the  scrip dies and doesnt work this time around which is odd. it ran like a charm the first time before i messed things up a little and re-installed....

the broadcom chip is the 4318 in my HP zv6000. i had it working fine earlier so something has to be missing if its not working this time around

---

### Post by bmartin on 2007-08-29
> **horned0wl said:**
> Uhhh...  Ahem!  I understand scripts. I've already used them at ./ in here.  Its just that I've apparently missed the post containing the script in question...  Help?

Cheers;
It's in the very first post of this thread.

---

### Post by siralphred on 2007-08-29
hey bmartin good job on your wireless script....it saved me tons of time and i have recommended it to tens of people, i have a question for you.....if you happen to be using an hp dv6000 or 9000 with the inbuilt webcam (specifically the microdia webcam) i would like to know if it works and how you got it working...thanks

---

### Post by MavrickUK on 2007-08-30
Fantastic stuff!!

I had tried to get this running using the fwcutter but the fwcutter failed with a 404 when getting the firmware.  so then I tried manually getting the firmware up and running using ndiswrapper, got it all going except the wireless didn't seem to engage right when connecting, I use wpa so I guessed perhaps wpa wasn't running right.
I did a ton of searching and stumbled upon this.  Ran the install and rebooted...
Worked a charm wireless is running sweeeeeeeet!!!
thanks.:guitar:

---

### Post by Madmoose on 2007-08-30
Hey there, 

It worked!!

Though, I'm now getting an a cutter error. I thought I copied it, but I guess not. I'll post the error next time I get it!

Thanks!

---

### Post by horned0wl on 2007-08-30
When you try to install the cutter, are you getting an MD5 error?  I got that one, myself.  Aparently their file checking system is off...

---

### Post by iperez916 on 2007-08-30
Worked awesome!  Thanks!

---

### Post by lit1337 on 2007-08-31
Wow been searching for ever this worked right away thank you :)

---

### Post by likemindead on 2007-08-31
My laptop is freezing up a lot and having trouble updating, among other things. It all seems to be around an error loading "bcm43xx_microcode5.fw"

Help? Please? Thanks as always....

---

### Post by cmp1988 on 2007-08-31
I just tried this on a fresh install of Feisty on my sister's laptop, and it worked awesomely.  Thanks for the easy installer thingamajig.

---

### Post by bmartin on 2007-08-31
> **likemindead said:**
> My laptop is freezing up a lot and having trouble updating, among other things. It all seems to be around an error loading "bcm43xx_microcode5.fw"
Reinstall it, but use the ndiswrapper option instead of the firmware.

---

### Post by likemindead on 2007-09-01
I can't even get it to fetch all the needed updates before it freezes up.

And ndiswrapper won't run without some of the updates I need.

What a paradox!

Is there a way I can manually fix the firmware?

You are invaluable. Thanks so much....

---

### Post by DarkN00b on 2007-09-01
Can you plug it into a wired connection until you get what you need?

---

### Post by flyboy94ca on 2007-09-01
Thank you so much for this. I had tried Ubuntu and Linux before but not being able to use my hardware in my laptop without major work tuned me away. I recently tried again because Vista (which I was happy with) made me so frustrated due to windows explorer restarting repeatedly that I tried again with a PCMCIA wireless card. But these clear and easy to use instructions (especially for a new Linux user, who is still learning the whole system) have really encouraged me to keep the system.
Thank you so much, this was a life saver.

---

### Post by sklitzz on 2007-09-01
One more satisfied kubuntu user :-) Thanks alot it worked great for me.

---

### Post by bmartin on 2007-09-01
> **likemindead said:**
> Is there a way I can manually fix the firmware?
If you're receiving strange errors from dmesg or /var/log/messages, I would suggest that you install ndiswrapper instead and leave the firmware alone. If you want to get the firmware fixed without having to use the internet during installation, use the offline installer.

---

### Post by likemindead on 2007-09-01
> I would suggest that you install ndiswrapper instead and leave the firmware alone. If you want to get the firmware fixed without having to use the internet during installation, use the offline installer.

[LIST=1]
[*]Your program gets hung up looking for build-essential.
[*]I can't run the update manager without it freezing up the system.
[*]I even tried to boot from my Feisty Live CD *and* a Linux Mint 3.0 Live CD and *both* hang at an error trying to load bcm43xx_microcode.fw which seems to be the root of all my problems.
[/LIST]

I can't do anything right now. I can't even reinstall. Thanks so much for your patience. What can I do?

---

### Post by bmartin on 2007-09-01
> **likemindead said:**
> Your program gets hung up looking for build-essential.
If you were using the offline installer, the program wouldn't be looking for build-essential. You need an internet connection to retrieve the build-essentail package when using the online installer.
> **likemindead said:**
> I even tried to boot from my Feisty Live CD *and* a Linux Mint 3.0 Live CD and *both* hang at an error trying to load bcm43xx_microcode.fw which seems to be the root of all my problems.
You can remove the firmware, for one thing. This will disable your wireless connection.
```
sudo modprobe -r bcm43xx
for fw in `find -P /lib/firmware/ -name 'bcm43xx_*.fw'`; do sudo rm $fw; done
```
Then I'd use the offline installer ([here]("http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.2.tar.gz"), from the first post). You need to have a compatible kernel. If it says your kernel is incompatible, post the output of **uname -r** and I'll make a tarball so that you can install ndiswrapper without downloading build-essential.

---

### Post by likemindead on 2007-09-01
Thanks so much, I'll get on it right now and get back to you.

Never forget that it is you who make this community the amazing place that it is.

Peace....

***EDIT***

Looks like I'm back in business! Many thanks...

***EDIT***

---

### Post by likemindead on 2007-09-01
Maybe I was a bit too hasty....

```
owner@owner-laptop:~$ sudo aptitude update
Password:
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 573B in 5s (104B/s)
Reading package lists... Done
owner@owner-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic 
The following packages have been kept back:
  linux-headers-generic 
The following packages will be upgraded:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host 
  capplets-data dbus dbus-1-utils dnsutils evolution-data-server 
  evolution-data-server-common file firefox firefox-gnome-support gimp 
  gimp-data gimp-python gnome-app-install gnome-control-center gnome-panel 
  gnome-panel-data hwdb-client-common hwdb-client-gnome iptables 
  language-pack-en language-pack-gnome-en libbind9-0 libcamel1.2-10 
  libcurl3 libdbus-1-3 libdns22 libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libexif12 libfreetype6 libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx 
  libglu1-mesa libgnome-window-settings1 libisc11 libisccc0 libisccfg1 
  libjasper-1.701-1 libkrb53 liblwres9 libmagic1 libmagick9 libmetacity0 
  libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 
  libpoppler1-glib libslab0 libsmbclient libvorbis0a libvorbisenc2 
  libvorbisfile3 libwrap0 linux-generic linux-restricted-modules-common 
  mesa-utils metacity metacity-common openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer poppler-utils python 
  python-apport python-gdbm python-launchpad-bugs python-minimal 
  python-problem-report python-uno python2.5 python2.5-minimal rdesktop 
  rsync samba-common smbclient tar tcpdump ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core vim-common 
  vim-tiny xscreensaver-data xscreensaver-gl 
112 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 104MB/140MB of archives. After unpacking 3891kB will be used.
Do you want to continue? [Y/n/?] 
Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] ------------[ cut here ]------------

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] invalid opcode: 0000 [#1]

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] SMP 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] CPU:    0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] EIP:    0060:[kfree+122/128]    Tainted: P      VLI

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] EFLAGS: 00010002   (2.6.20-15-generic #2)

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] EIP is at kfree+0x7a/0x80

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] eax: 8000082c   ebx: f7b31f60   ecx: f74ccf80   edx: c1800000

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] esi: 00000001   edi: 00000202   ebp: 00000400   esp: f7b31f30

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] Process hald (pid: 4484, ti=f7b30000 task=dfcf7030 task.ti=f7b30000)

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] Stack: f7b31f60 f3a68b40 00000001 c0190cbe 00000400 080860e0 f71b93c0 f3a68b60 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]        00000000 00000000 dfe88900 00000000 00000000 00000000 f71b93c0 080860e0 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]        f7b31fa0 00000400 c0176e2c f7b31fa0 dfe88934 c0190c30 f71b93c0 fffffff7 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] Call Trace:

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]  [seq_read+142/672] seq_read+0x8e/0x2a0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]  [vfs_read+188/400] vfs_read+0xbc/0x190

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]  [seq_read+0/672] seq_read+0x0/0x2a0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]  [sys_read+65/112] sys_read+0x41/0x70

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000]  =======================

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] Code: 89 74 83 14 83 c0 01 89 03 89 f8 50 9d 66 66 66 90 66 66 66 90 5b 5e 5f c3 8b 52 0c eb c9 89 c8 89 da e8 9a fe ff ff 8b 03 eb d5 <0f> 0b eb fe 66 90 57 89 d7 8d 92 00 00 00 40 89 c1 c1 ea 0c c1 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.940000] EIP: [kfree+122/128] kfree+0x7a/0x80 SS:ESP 0068:f7b31f30

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] invalid opcode: 0000 [#2]

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] SMP 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] CPU:    0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] EIP:    0060:[kfree+122/128]    Tainted: P      VLI

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] EFLAGS: 00010002   (2.6.20-15-generic #2)

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] EIP is at kfree+0x7a/0x80

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] eax: 8000082c   ebx: f3a68b40   ecx: f3a68b40   edx: c1800000

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] esi: 00000001   edi: 00000202   ebp: f3a79cd4   esp: f7b31d54

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] Process hald (pid: 4484, ti=f7b30000 task=dfcf7030 task.ti=f7b30000)

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] Stack: f3a68b40 f74ccf80 f3a6942c c019057b 00000010 c01905e5 00000010 f71b93c0 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]        c0177747 00000000 00000000 f3a6942c df90d140 f3a79cd4 f71b93c0 f7d52840 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]        00000000 f7d52840 c0174ae7 f7b31da8 00007fff f7d52848 00000000 c01281af 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] Call Trace:

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [seq_release+11/32] seq_release+0xb/0x20

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [single_release+21/48] single_release+0x15/0x30

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [__fput+167/400] __fput+0xa7/0x190

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [filp_close+71/128] filp_close+0x47/0x80

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [put_files_struct+143/176] put_files_struct+0x8f/0xb0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [do_exit+308/2048] do_exit+0x134/0x800

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [printk+27/32] printk+0x1b/0x20

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [show_stack+0/64] show_stack+0x0/0x40

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [do_invalid_op+0/176] do_invalid_op+0x0/0xb0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [do_invalid_op+162/176] do_invalid_op+0xa2/0xb0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [kfree+122/128] kfree+0x7a/0x80

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [printk+27/32] printk+0x1b/0x20

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [acpi_os_vprintf+37/40] acpi_os_vprintf+0x25/0x28

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [error_code+124/144] error_code+0x7c/0x90

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [kfree+122/128] kfree+0x7a/0x80

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [seq_read+142/672] seq_read+0x8e/0x2a0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [vfs_read+188/400] vfs_read+0xbc/0x190

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [seq_read+0/672] seq_read+0x0/0x2a0

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [sys_read+65/112] sys_read+0x41/0x70

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000]  =======================

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] Code: 89 74 83 14 83 c0 01 89 03 89 f8 50 9d 66 66 66 90 66 66 66 90 5b 5e 5f c3 8b 52 0c eb c9 89 c8 89 da e8 9a fe ff ff 8b 03 eb d5 <0f> 0b eb fe 66 90 57 89 d7 8d 92 00 00 00 40 89 c1 c1 ea 0c c1 

Message from syslogd@owner-laptop at Sat Sep  1 11:32:57 2007 ...
owner-laptop kernel: [  241.944000] EIP: [kfree+122/128] kfree+0x7a/0x80 SS:ESP 0068:f7b31d54
  

```

Why does my laptop hate me?

---

### Post by markk1994 on 2007-09-01
My installer.py opens in     Kate what should it  open in?

---

### Post by martinmartinmartin on 2007-09-01
worked like a charm! thanks a lot - saved me a bunch of time..

---

### Post by AK47Jazz on 2007-09-01
I just installed Ubuntu on my machine. It cannot be directly connected to the internet so i have a wireless card. Belkin F5D7000. When i run the commands in the termanial and it tells me password. I am unsure of what to type in this field. Help would be GREATLY appreciated. thanks

---

### Post by bmartin on 2007-09-02
> **markk1994 said:**
> My installer.py opens in     Kate what should it  open in?
Darn KDE... it should execute... try right-clicking on it and seeing if there's an option to run the program.

---

### Post by bmartin on 2007-09-02
> **AK47Jazz said:**
> I just installed Ubuntu on my machine. It cannot be directly connected to the internet so i have a wireless card. Belkin F5D7000. When i run the commands in the termanial and it tells me password. I am unsure of what to type in this field. Help would be GREATLY appreciated. thanks
You should type in your password (the one you log in with). Linux does this fairly regularly as a security precaution. Any time you attempt to change system-wide settings, you'll be prompted for your password.

---

### Post by jlombs on 2007-09-02
Ok - it worked!  
But it will only connect when my wep is shut down.  I got to figure out that mess next. 

Thanks dude!

---

### Post by peebly on 2007-09-02
Hi

The Wicd install would not work, also I now cannot remove the entry this program made in the software sources.

---

### Post by bmartin on 2007-09-02
Try this: sudo rm /etc/apt/sources.list.d/wicd.list

Why didn't it work?

---

### Post by peebly on 2007-09-02
> **bmartin said:**
> Try this: sudo rm /etc/apt/sources.list.d/wicd.list

Why didn't it work?

Thanks that removed the entry.

I don't know why, it just kept bring up window saying cannot continue etc, As it was trying to install there were loads of cannot find etc, etc type messages in the terminal window.

Maybe his servers are down.

Installed it anyway by following instructions at sourceforge.

---

### Post by DarkN00b on 2007-09-02
Weird things like this crop up sometimes. We really have no idea why. bmartin and I have noticed that the sooner the drivers or firmware are installed after a fresh Ubuntu install, the smoother things go.

That's not to say that anyone should reinstall Ubuntu just to get their wireless working though. :D

---

### Post by ozarkman on 2007-09-02
I have tried everything with no luck. this worked the first try. thanks

---

### Post by Tuxaby on 2007-09-02
On a fresh intall of  6.06 LTS and upgrading to 7.04 Feisty Fawn,  after several tries I went back to the initial installer using theExperimental 0.3.1 Installer, installed the ndiswrapper and the Broadcom Windows driver.  Then tried Network Manager again.  Wireless showed up there but would not connect.  Found a post referencing WIFI Radar used with Network manager disabled.  Installed WiFi Radar withSynaptec Package Manager and  started WiFi Radar before disabling Network Manager and I now have very fast wireless internet.  Still haven't disabled Network manager and all seems well.  
      If you are having trouble with this tool, just keep trying all suggestions.  It just seems to take the right combination and it suddenly works.
      Many thanks for this How To.  Now on to my vid card.     Lee

---

### Post by AK47Jazz on 2007-09-03
I tried the offline installer and it didnt work, any other suggestions

---

### Post by Adr3nalin on 2007-09-03
Okay, so after an hour and a half of this bull xxxx i finally got my computer to recognize that there is a network somewhere nearby, but it can't even find an ip address... 

Wuts the deal?  I've installed Wicd and set the drivers to broadcom...



BTW, for the two people who do read this... this page was a huge step forward to get my crappy dell d600 online.  Thanks a bunch.




FCUK WINDOWS!

---

### Post by cdupree on 2007-09-03
When I double-click the .py file, I don't get a "Run" button.  Presumably I'm missing a package somewhere?  I've just done a clean install followed by updating as the package manager suggested, and installing basics like Emacs, Opera, and Firefox.  I seem to have Python installed (according to Adept), but when I double-click the .py file, I get Kate with the text of the file.

???

---

### Post by bmartin on 2007-09-03
> **AK47Jazz said:**
> I tried the offline installer and it didnt work, any other suggestions
Post your installer.log file. When you do, please attach it so it doesn't take up half the page.

When you say it didn't work, what do you mean? Did the installer run successfully? Did it freeze? Was your wireless device detected afterward?

---

### Post by bmartin on 2007-09-03
> **cdupree said:**
> When I double-click the .py file, I don't get a "Run" button.  Presumably I'm missing a package somewhere?  I've just done a clean install followed by updating as the package manager suggested, and installing basics like Emacs, Opera, and Firefox.  I seem to have Python installed (according to Adept), but when I double-click the .py file, I get Kate with the text of the file.

???
If you **right**-click, do you get an option to run it?

---

### Post by bmartin on 2007-09-03
> **Adr3nalin said:**
> Wuts the deal?  I've installed Wicd and set the drivers to broadcom...
I presume you installed ndiswrapper. Are you trying to connect to an encrypted network? If so, are you using an ASCII or HEX key? If it's ASCII, try putting quotes around it. If it's unencrypted... then I don't have much to suggest.

---

### Post by lowracer on 2007-09-03
> **bmartin said:**
> If you **right**-click, do you get an option to run it?

I'm having the same trouble.  Double-clicking the .py file (running Kubuntu), brings up two copies of the .py file in Kate.  

Right clicking the file, there is no option to run it.  I'm going to try running it from the command line.

edit to add: that worked. I guessed the command python installer.py would do it, and I do seem to be running the script now.  It says I have an incompatible broadcom chipset and ndiswrapper is recommended.

---

### Post by bmartin on 2007-09-03
I installed KDE a while back to debug some problems with the script. This appears to be a new one. I can't figure out a way to run the script in KDE other than by using the terminal. This also applies to .sh files, which is a bit shocking.

---

### Post by azoomm on 2007-09-03
*sigh*

This worked really well for me.

Then, I did the latest software update (Ubuntu) yesterday and now it will see it, but not get a signal.  :confused:

---

### Post by lowracer on 2007-09-03
OK I'm using Gnome now instead of KDE...
Says my chipset is incompatible, recommends Ndiswrapper.

Trying the second choice, install  ndiswrapper and Broadcom windows driver...
I get invalid module format errors when trying to install ndiswrapper.  

Trying 3rd choice, freshly compiled ndiswrapper, same deal, invalid module format... followed by multiple ndiswrapper: command not found errors.

Trying 4th choice...
well that didn't give an error but I'm not sure how removing the driver is going to make my wireless connection work?

Tried 1st choice to put the driver back in, did not give an error.

Installed WiFi Radar, it says I'm connected to my access point but with no IP address.  It doesn't show any other networks and we have a bunch of them here normally.

---

### Post by pfeifdog on 2007-09-03
Complete newbie here.  I'm in day 2 after installing Xubuntu on my old laptop (800 MHz, 256 RAM)  and am loving it.  It's a fresh install and I did the update/upgrade steps.

Problem: I still can't figure out wireless.  When I click on "installer.py" and try to install the BCM43xx firmware, a "null" window pops up saying: "xmessage: problems reading message file"

I checked "/lib/firmware/2.6.20-15-generic" and there's nothing there that looks like a bcm43xx.fw file, but if I rerun the installer, it seems to think the firmware is already installed.  I also tried the ndiswrapper, and got the same thing (although I still don't really know what that does differently).

I also tried: "sudo apt-get install bcm43xx-fwcutter" but just got a bunch of errors.

Part of the problem might be that I'm also not sure what is supposed to "happen" in order for me to view and connect to wireless networks.  I've set my wireless router to open unencrypted for the moment.  There's also a few encrypted ones around, and I would love to just "see" them for now.  I've looked at the Network Manager but nothing shows up under the Wireless Connection button.

Thanks in advance for any assistance.  I am utterly amazed at the amount of support there is  here for newbies.

---

### Post by bmartin on 2007-09-03
> **lowracer said:**
> Trying the second choice, install  ndiswrapper and Broadcom windows driver...
I get invalid module format errors when trying to install ndiswrapper.
Hmmm... try doing the following:
```
for mod in $(find /lib/modules/$(uname -r) -name ndiswrapper.ko); do sudo rm $mod; done
```
This will remove all of the ndiswrapper kernel modules. Then try installing ndiswrapper again and see if the problem goes away.

---

### Post by bmartin on 2007-09-03
> **pfeifdog said:**
> Problem: I still can't figure out wireless.  When I click on "installer.py" and try to install the BCM43xx firmware, a "null" window pops up saying: "xmessage: problems reading message file"
You're the second person to write that... you're doing something differently from everyone else.

Did you extract all of the files (i.e., did you create a folder on your desktop containing everything), or did you simply run installer.py without extracting the files? My guess is that you ran the installer without extracting the files. If you did extract them, cd into the installer directory and post the contents of the **find** command so that I can see what files are present/absent.

---

### Post by pfeifdog on 2007-09-03
Yep- I did extract them (albeit to a directory in my home folder).  I just copied the extracted folder to my desktop, not knowing whether that could make a difference.

> justin@Scrappy:~/Desktop/bcm43xx-gtk-installer-0.3.1$ find
.
./README-wcm-wicd
./README-installer
./README-bcm43xx-ndiswrapper
./LICENSE-BROADCOM
./install.log
./bcm43xx-ndiswrapper.sh
./stats-logger
./LICENSE
./README-bcm43xx
./wcm.sh
./wicd-tray.desktop
./S05firmware-init-script
./README
./installer.py
./GPLv2
./README-wcm-wifi-radar
./bcm43xx.sh
./CHANGELOG


Is it worth noting that the "null" error window comes up before I can even put in my password?  I also tried "gksudo ./installer.py" from the same directory and got;

> ./wcm.sh wifi-radar
gksudo './bcm43xx-ndiswrapper.sh'
gksudo './bcm43xx.sh'
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


The install window comes up, but basically the same thing happens, with the addition of: ":READMEs/LICENSE-BROADCOM: No such file or directory"

I'm pretty clumsy with the CLI still.  Is this something that I need to do as root?  I'm not even sure how to do that on Xubuntu, as it doesn't let me login as root.

Sorry for all the dumb questions.  Thank you so much for taking a look.

---

### Post by pfeifdog on 2007-09-03
Quick update: I figured out how to login as root using Ctl-Alt-F6 on Xubuntu.  I then tried executing installer.py and got a long list of errors.  Here are the first few lines:

> /var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
./installer.py:46: Warning: invalid (NULL) pointer instance
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
./installer.py:46: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)


I did figure out how to write errors to a txt file!  Baby steps...

---

### Post by lowracer on 2007-09-03
> **bmartin said:**
> Hmmm... try doing the following:
```
for mod in $(find /lib/modules/$(uname -r) -name ndiswrapper.ko); do sudo rm $mod; done
```
This will remove all of the ndiswrapper kernel modules. Then try installing ndiswrapper again and see if the problem goes away.

OK thanks...  I just tried that, tried to install freshly compiled ndiswrapper from the install.py script...
Says ndiswrapper: command not found in ./bcm43xx-ndiswrapper.sh lines 120, 122 and 124.  I've seen that error before.  When I do a "which ndiswrapper" command from the command line, it doesn't show any program with that name.

installing ndiswrapper without the fresh install from the installer.py script gives the invalid module format errors as before.

In a parallel effort to this, I am researching Cardbus WLAN cards with chipsets that are just supported out of the box.

---

### Post by bmartin on 2007-09-03
> **lowracer said:**
> Says ndiswrapper: command not found in ./bcm43xx-ndiswrapper.sh lines 120, 122 and 124.  I've seen that error before.  When I do a "which ndiswrapper" command from the command line, it doesn't show any program with that name.

installing ndiswrapper without the fresh install from the installer.py script gives the invalid module format errors as before.
OK... so for some reason, the precompiled kernel module doesn't work with your kernel, and you can't compile ndiswrapper for some reason. Try [this thread]("http://ubuntuforums.org/showthread.php?t=297092").

---

### Post by bmartin on 2007-09-03
> **pfeifdog said:**
> Yep- I did extract them (albeit to a directory in my home folder).  I just copied the extracted folder to my desktop, not knowing whether that could make a difference.
OK, with the file listing, I see what the error is... you're going to have to re-extract the files. You extracted all of them to the same directory. There are supposed to be subdirectories.

The default file extraction utility in GNOME is "File Roller". If you double-click on a package, it normally opens up in File Roller. If you click extract, a dialog opens up. Make sure the "Re-create folders" option is checked. If you right-click and click "Extract Here", it also *recreates the folders*. There should be a READMEs directory in the archive. If no READMEs directory is present, the installer won't work.

> **pfeifdog said:**
> Is it worth noting that the "null" error window comes up before I can even put in my password?
It's not an error window. The installer runs a script, which I chose to output to a window so that some information could be displayed to the user.

> **pfeifdog said:**
> I'm pretty clumsy with the CLI still.  Is this something that I need to do as root?
No. The installer should not be run as root.

---

### Post by Lanning on 2007-09-03
Wahoo!!!! I have been struggling to get online using Linux with this Broadcom chipset for months -- I've tried Fedora 7.0 and got nowhere. I also tried other methods suggested on this forum after installing Feisty Fawn, but I have never got further than getting the card to recognize my network. Then I got on wirelessly for the first time with Linux today using this HowTo. It took about 10 minutes (because I read everything first.) Thank YOU!!! Maybe I'll finally be able to wean myself from Windows entirely.

btw,
I'm running a Dell Latitude c400, 40GB, 1Ghz, Broadcom 4311 (Airforce 54g) mini-PCI, connecting to a Netgear router with WPA.

---

### Post by lowracer on 2007-09-04
> **bmartin said:**
> OK... so for some reason, the precompiled kernel module doesn't work with your kernel, and you can't compile ndiswrapper for some reason. Try [this thread]("http://ubuntuforums.org/showthread.php?t=297092").

Thanks for the info.  I got most of the way through that page, then something went wrong and I went to the ndiswrapper website and finished up the install from there.  Along the way I suspected it might be a 64bit/32bit thing, and since I had originally installed the 64bit OS, I went back, wiped the machine and started fresh with a 32bit install.

I now have the bcmwl5 driver installed and somewhat working.  I say somewhat because I was able to get it to scan and recognize all the access points in my vicinity.  Then I rebooted and I'm not able to do it anymore.  But I think I'm getting close.  The ndiswrapper site seems to be what I need to follow, since it matches most closely to what I'm experiencing with my system.

So my current state is, iwconfig shows my radio properly, but iwlist wlan0 scan does not show any scan results.  dmesg piped through grep for ndiswrapper shows the driver properly installed according to the ndiswrapper site.

---

### Post by bereanone on 2007-09-04
Never asked for a password and doesn't work. I have a HP Pavilion dv5040us with AMD Turion64 and Broadcom 4311. I need to run off of a CD until I can test all my Windows software. Can't get over the wireless hurdle. I need a CD/DVD that will boot and give me wireless. Either that or some way to run Windows and Ubuntu off my Hard drive simultaneously. I hooked my external disk up but cannot write to it from Ubuntu, Not sure why.

---

### Post by bmartin on 2007-09-04
> **lowracer said:**
> So my current state is, iwconfig shows my radio properly, but iwlist wlan0 scan does not show any scan results.  dmesg piped through grep for ndiswrapper shows the driver properly installed according to the ndiswrapper site.
It sounds like the wireless radio on your card is disabled. There's usually a keyboard combination (like Fn+F2) or a swich on your computer you can use to enable that.

---

### Post by lowracer on 2007-09-04
> **bmartin said:**
> It sounds like the wireless radio on your card is disabled. There's usually a keyboard combination (like Fn+F2) or a swich on your computer you can use to enable that.

Thanks for the reply. That was the same conclusion I came to.  There is a dedicated switch, and an LED. The LED is red for wireless disabled, and blue for enabled.  When the wireless was working, it was blue.  Now it is red and throwing the switch has no effect.  I'm going to try to retrace my steps to see what I did to get it to go blue the first time.  I think I'm getting close to having the WLAN working.

---

### Post by Madmoose on 2007-09-04
Hey, 

I have wireless now! Woot! I've been trying to get this to work forever,! 

Yet, I have a problem. When I try to install anything, updates, packages, or anything, I get this: 

```
E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1
```


Everything seems to install ok, but I get this error anyway. It doesn't matter if I'm connected wireless or hard line.

---

### Post by bmartin on 2007-09-04
You have a partially-installed package :confused:

Try running the following three commands and see if the problem goes away:
```
sudo apt-get install -f
sudo apt-get install bcm43xx-fwcutter
sudo apt-get remove bcm43xx-fwcutter
```

You shouldn't need the bcm43xx-fwcutter package anyways.

---

### Post by Madmoose on 2007-09-04
> **bmartin said:**
> You have a partially-installed package :confused:

Try running the following three commands and see if the problem goes away:
```
sudo apt-get install -f
sudo apt-get install bcm43xx-fwcutter
sudo apt-get remove bcm43xx-fwcutter
```

You shouldn't need the bcm43xx-fwcutter package anyways.

\\:D/ That seemed to do it, and I still have my wireless! 

Thanks

Moose

---

### Post by DarkN00b on 2007-09-04
> **lowracer said:**
> Thanks for the reply. That was the same conclusion I came to.  There is a dedicated switch, and an LED. The LED is red for wireless disabled, and blue for enabled.  When the wireless was working, it was blue.  Now it is red and throwing the switch has no effect.  I'm going to try to retrace my steps to see what I did to get it to go blue the first time.  I think I'm getting close to having the WLAN working.

What type of computer do you have? If it has an Acer motherboard, there is an applet that acts as a front end for acer_acpi. It makes it easy to enable/disable wifi controllers on Acer computers. It can be found at [gnomefiles.org]("http://www.gnomefiles.org/app.php/acerwificontroller"). I has to be compiled from source, but can be invaluable for Acer users. It is still at version 0.1, but I've read that it works.

---

### Post by Dirksy on 2007-09-04
After several hours of reading forums and trying to install my wireless card drivers through terminal and being TOTALLY new to Ubuntu.  THIS WORKED GREAT!!!  Thanks DarkNooB!!.      

Running Ubuntu 7.04 Fiesty
HP dv6406nr
Broadcom wirelss (rev02)

Total thanks

---

### Post by pfeifdog on 2007-09-04
Wow - thanks bmartin! :D  So simple, but it would have taken me forever to figure out.  Xubuntu's decompressor has an option "Extract files with full path" which defaults to off.  I didn't even know what it meant when I first looked at it.

Okay, so now the activity lights on the card are on, and iwconfig gives:

> 
eth1      IEEE 802.11b/g  ESSID:"dlink"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:3D:37:DE:6E   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level=-44 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:41  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(that's definitely my router, and there's no encryption/filtering at the moment)

So I thought this meant I was connected, but I'm not.  I can't even browse to 192.168.0.1.  When I open the Network Manager, there's nothing special to be seen (just "Enable Roaming Mode Checked").  I try to click on the Hosts tab, and Manager crashes - I have to kill it with the process manager or else it sucks up all the system resources.  

Any advice on what to do next?  I've been browsing the other forums but haven't gleaned anything useful.

Many thanks.

---

### Post by Adr3nalin on 2007-09-04
boyz!!!  I got it working!!!
I knew yesterday that my only choice was windows XP.  

Today, i open up my computer just to see what a failure I am.

AND... I tried for the last time to see if my computer could locate an ip after a new restart.  


voila!  success!  i put in the password and it works...

to everybody... my f00king dell is a piece of **** d600 and if it works on this piece of junk...it'll work on anything.

peace. 

Thank you all you Linux geeks out there, the force is strong w/ you fellas.  I hope to be there with you one day.

V

---

### Post by foosmith on 2007-09-05
great stuff! I tried about 3 other posts before this one and all failed. thx :)

---

### Post by bmartin on 2007-09-05
> **pfeifdog said:**
> So I thought this meant I was connected, but I'm not.  I can't even browse to 192.168.0.1.  When I open the Network Manager, there's nothing special to be seen (just "Enable Roaming Mode Checked").  I try to click on the Hosts tab, and Manager crashes - I have to kill it with the process manager or else it sucks up all the system resources.  

Any advice on what to do next?  I've been browsing the other forums but haven't gleaned anything useful.
If you have a wired connection and a wireless connection, you can't use both at the same time (without a network bridge; it's another headache). If all you're running on is wireless, then try installing [WICD]("http://blakecmartin.googlepages.com/wicd.html") or [wifi-radar]("http://blakecmartin.googlepages.com/wifi-radar.html") and connecting with one of them. Installing WICD will remove the other two. You shouldn't be using more than one wireless connection management program at a time; use either the built-in GNOME one (not recommended unless it's already working) or WICD (highly recommended) or wifi-radar (also recommended).

You can also install WICD or wifi-radar using the installer.py script. There's an option in there.

---

### Post by clancy on 2007-09-05
Worked perfectly on my Asus A6R notebook....First time ever i now have wireless.
Thanks heaps...

---

### Post by Team Freedom on 2007-09-05
Thanks,

This worked perfect with my Linksys WPC54G - V1 in an old Dell Inspiron 7500...

New to Linux, but I will give it a serious try this time ;-)

---

### Post by pfeifdog on 2007-09-05
Thanks once more, bmartin.  :)

Sadly, I'm still struggling.  Here's the weird thing: WiFi Radar says I'm connected, and the router sees that my computer is connected to it (checking from other laptop), but i can't actually use the connection.  No Google, no 192.168.0.1, no nothing.  I've restarted everything and its the same.  There are no access restrictions being placed by the router, as it's reset to factory defaults.  I'm stumped again.

Other oddities, probably unrelated, if you feel like commenting:

I tried a few times but couldn't install WICD.  I checked the wicd file and got a broken symbolic link to opt/wicd/gui.py (that file doesn't exist).  

I installed WiFi Radar instead, with relative success.  It shows all the networks, but they all have little question marks.  The "Disconnect" and "Edit" buttons are non-functional, although it does say I'm connected to my router, "dlink".  If that's true, I'm not sure why the buttons don't work.

I hope this is last hurdle in this process.  I definitely appreciate your time thus far and would understand if you just say, screw it, buy a new card.   Thanks again.

---

### Post by bmartin on 2007-09-05
Hmm... maybe the WICD repository is down.

The broken symbolic link exists because the installer I wrote creates it. WICD is installed to /opt/wicd/ by default, but for some reason it failed to install. You can try installing it manually by following the directions [here]("http://wicd.sourceforge.net/download.php"). You do need to type some things into the terminal to get WICD to install, such as "yes" when it prompts if you're willing to install untrusted packages.

It sounds like you're pretty close to solving your problem. My guess is that if you're connected but not getting an IP address, it has something to do with your WEP or WPA key (assuming you're using one). That's all I can think of for now.

---

### Post by pfeifdog on 2007-09-05
thanks, the manual install of wicd worked!  not sure why the install script was still failing though.

maybe i've got a separate problem with my router, as you said.  wicd also connects to the router, and iwconfig gives:

> eth1      IEEE 802.11b/g  ESSID:"dlink"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:3D:37:DE:6E   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=108/100  Signal level=-30 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:11  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


that's the router MAC address, but still no love.  no WEP/WPA encryption -  the router is completely reset to open.  it's a dlink di-624.  

maybe there's something that doesn't play well with Xubuntu and its Xcfe environment, which as i undestand it is slightly different than kde and gnome?  i don't know if that's even possible.

i'm about ready to call it quits on trying to connect with this card/router/distro, unless you've got a final card up your sleeve. :)  it might just be time to upgrade a few components or to full Ubuntu or another distro.  you've been a tremendous help, and i've learned a lot.   thanks a million.

---

### Post by bmartin on 2007-09-05
Are you using ndiswrapper or the firmware? You only have an 11Mbps connection speed. If you're using the firmware, try ndiswrapper.

A lot of people have problems with the firmware and success with ndiswrapper.

---

### Post by emailstimpy on 2007-09-06
xmessage: problems reading the message file

This is the error i get when i use the bcm43xx-gtk-installer found in the post HOWTO: Broadcom 43xx based wireless cards the EASY way.. I click on the installer.py and the prompt box pops up and asks me to select which thing i want to install. I click install. I terminal pops up and then this message is displayed. xmessage: problems reading the message file. What do I do?

FYI:
I used this before and it worked like a charm. I had to reinstall xubuntu on a compaq presario so I had to use this program again and now I have this error. My wireless card is a motorola Broadcom 4306 card. What is going on?

---

### Post by bmartin on 2007-09-06
There's an option to create the original directory structure (or something like that) when you extract the files. If it's not selected, the old installer won't work at all.

Did you download the newest installer? There's a new one out. It should take care of that problem.

---

### Post by brennydoogles on 2007-09-06
This howto helped me more than anything else I have found so far, but I am still lacking slightly. I am able to see all of the wireless networks in range, and wifi-radar says I am connected to them (It shows my IP and all), but I am unable to do anything with this connection. Firefox times out when I try to load my homepage (Ubuntuforums ), and I can't connect to my home network either (both of which work like a charm when I am wired to the router. This is on an old laptop running Xubuntu. If there is any more information you need, just post and I will get it up asap. Thanks for your help!!

---

### Post by bmartin on 2007-09-06
WICD is my connection program of choice. A lot of people have been able to connect using WICD whereas wifi-radar and network-manager have failed.

---

### Post by brennydoogles on 2007-09-06
> **bmartin said:**
> WICD is my connection program of choice. A lot of people have been able to connect using WICD whereas wifi-radar and network-manager have failed.

Wicd did not work as well for me as wifi-radar. It would only see one network, when there are three that should be in range. Wifi-radar shows all three. I just need to figure out how to connect. I may try to remove the encryption from the network to see if I can connect that way, and then trouble shoot more from there.

---

### Post by whirl on 2007-09-06
Cheers! worked instantly :)

---

### Post by mikessktr on 2007-09-06
will this really work on my laptop (dell latitude 110L) ? or should i find another way to get my wireless working.

---

### Post by peterv6 on 2007-09-06
I´m hoping someone can help me out.  I´m trying to use this to set up my card, but the installation script seems to have stopped  before completion.  Has anyone else had this happened, and can anyone help me out?
Thanks,
PETER V.

---

### Post by LuckyDevil on 2007-09-06
Worked like a charm for me!  Dell Inspiron 1720 with Dell 1390 mini wlan.

---

### Post by bmartin on 2007-09-06
> **mikessktr said:**
> will this really work on my laptop (dell latitude 110L) ? or should i find another way to get my wireless working.
I'll give it 311:73 odds :)

---

### Post by VON_CAPO on 2007-09-06
> **bmartin said:**
> There's an option to create the original directory structure (or something like that) when you extract the files. If it's not selected, the old installer won't work at all.

Did you download the newest installer? There's a new one out. It should take care of that problem.
I think I am doing the right thing, but I have this error.
[[IMG]http://img454.imageshack.us/img454/1416/99779020by0.th.png[/IMG]](http://img454.imageshack.us/my.php?image=99779020by0.png)

By the way, I downloaded the offline installer 30 minutes ago.
I am running Ubuntu 7.04 with a Broadcom 4318 chipset.

Wireles is already running with fwcutter, but I am tring to override it and to install ndiswrapper, could be this the problem???

---

### Post by Redhead on 2007-09-07
Thanks DarkN00b and bmartin, and all others who posted. I am about one month into Ubuntu but now I can connect to the Internet via a Linksys WRT54GL router and my Acer 5050 notebook that has an internal Broadcom chipset version 4318.



My Acer 5050 is setup to dual boot Ubuntu 7.04 64-bit version (kernel, 2.6.20-16 generic), and Windows XP Media Center. My connect speed with Ubuntu is generally over 70% (~38 mbps). No slow down of Ubuntu (as others reported) once the installation was completed.



I used the Gnome /XFCE Online (0.3.2) installer script and selected ndiswrapper, WICD is my Network Manager, and encryption is WPA 1 / TKIP.



Here is what I had to do before I could connect--I don't remember reading this in any posts. From the WICD Manager, I clicked the Preferences tab. The default setting for the WPA Supplicant Driver was broadcom. By trial and error, I tried "ndiswrapper" without connecting. Next I tried "wext" and was connected!



Is there a Linux command or log file where I can review what I did?

---

### Post by bmartin on 2007-09-07
> **VON_CAPO said:**
> Wireles is already running with fwcutter, but I am tring to override it and to install ndiswrapper, could be this the problem???
No. But a file was missing from the offline installer. I uploaded the file, but you'll have to download the offline installer again to run it... or you can find the LICENSE-BROADCOM file in the other archive and put it in the proper place in the offline archive.

---

### Post by bmartin on 2007-09-07
> **Redhead said:**
> and my Acer 5050 notebook
My girlfriend has one of those and we're having some problems with it, namely the ACPI (e.g. the battery meter doesn't display the battery level) and the card reader (ENE card reader, 0 support). If you have either of these working (and they didn't work before), please let me know how you fixed them.

Hres doesn't have the Broadcom chipset; it has an Atheros chipset that's not supported by Madwifi.

> **Redhead said:**
> I used the Gnome /XFCE Online (0.3.2) installer script and selected ndiswrapper, WICD is my Network Manager, and encryption is WPA 1 / TKIP.

Here is what I had to do before I could connect--I don't remember reading this in any posts. From the WICD Manager, I clicked the Preferences tab. The default setting for the WPA Supplicant Driver was broadcom. By trial and error, I tried "ndiswrapper" without connecting. Next I tried "wext" and was connected!

Is there a Linux command or log file where I can review what I did?
There isn't, but **wext** is the most common WPA driver, at least in terms of what works for users. I don't know what the Broadcom one is; it might have something to do with the firmware.

I'm glad it's working for you.

---

### Post by Spam Banjo on 2007-09-07
I Love You!!!!

Wireless was my only fear with buying this Dell Vostro 1000 Laptop... I am writing this reply using wireless as conclusive proof that this guide works!!

U ARE A STAR!!!!!

---

### Post by seiserres on 2007-09-07
After a lot of unsuccesfull and fustrating attemps of installing the wireless card in my hp zd7000 (zd7395ea) your procedure worked nicely. So simple and so easy! Thank you very much I am really happy wifi!!!

---

### Post by bmartin on 2007-09-07
> **Spam Banjo said:**
> I Love You!!!!
You shouldn't post such things so early in the morning. You made my girlfriend jealous and almost gave me a heart attack.

---

### Post by bigpenguin on 2007-09-07
That was amazing.  Worked brilliantly.  So easy I was stunned.  You are a god among men to me :).  Thank you for your work to provide this easy solution to others.:KS:KS:KS

---

### Post by Panganat on 2007-09-07
U da man or men or woman or women.............  I know it would have been better to buy a card that worked out of the box but why waste a good wifi card.  I hope to become as good as u guys and maybe girls at this LINUX thing. :)

---

### Post by pfeifdog on 2007-09-07
:confused:

:o

:guitar:

ROCK!  Thanks a million, bmartin.  I was about to throw in the towel.  It's a damn shame I can't buy you a beer right now.  I'll do my best to send some good karma your way.

---

### Post by peterv6 on 2007-09-07
I don't know if anyone still monitors this posting, but I'm having trouble with the sudo aptitude upgrade.  I ran the update, then when I run the upgrade, after a few minutes, I get the following question:

[COLOR="Red"][B]112 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 140MB of archives. After unpacking 3891kB will be used.
Do you want to continue? [Y/n/?] y[/B][/COLOR]

I answered yes, and messages scroll by for a few more minutes before getting the following error messages, then it hangs:

[COLOR="Red"][B]Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main mesa-utils 6.5.2-3ubuntu8 [45.0kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main openoffice.org-core 2.2.0-1ubuntu4
  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80][/B][/COLOR]
[COLOR="Red"][B]Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main openoffice.org-common 2.2.0-1ubuntu4
  Bad header line [IP: 91.189.88.31 80][/B][/COLOR]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-tiny 1:7.0-164+1ubuntu7.2
  Bad header line [IP: 91.189.88.31 80]
Get:61 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-common 1:7.0-164+1ubuntu7.2 [186kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-common 1:7.0-164+1ubuntu7.2
  Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisc11 1:9.3.4-2ubuntu2.1
  Bad header line [IP: 82.211.81.138 80]
Get:62 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libdns22 1:9.3.4-2ubuntu2.1 [499kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libdns22 1:9.3.4-2ubuntu2.1
  Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Get:63 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisccc0 1:9.3.4-2ubuntu2.1 [95.7kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisccc0 1:9.3.4-2ubuntu2.1
  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisccfg1 1:9.3.4-2ubuntu2.1
  Bad header line [IP: 91.189.88.31 80]
Get:64 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libbind9-0 1:9.3.4-2ubuntu2.1 [95.4kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libbind9-0 1:9.3.4-2ubuntu2.1
  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Get:65 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main liblwres9 1:9.3.4-2ubuntu2.1 [112kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main liblwres9 1:9.3.4-2ubuntu2.1
  Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Get:66 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main bind9-host 1:9.3.4-2ubuntu2.1 [115kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main bind9-host 1:9.3.4-2ubuntu2.1
  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Get:67 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main dnsutils 1:9.3.4-2ubuntu2.1 [184kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main dnsutils 1:9.3.4-2ubuntu2.1
  Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main file 4.19-1ubuntu2.1
  Bad header line [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libmagic1 4.19-1ubuntu2.1[5~^[[5~^[[5~^[[5~
  Connection timed out [IP: 82.211.81.138 80]
Get:68 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main rsync 2.6.9-3ubuntu1.1 [262kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main rsync 2.6.9-3ubuntu1.1
  Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
[COLOR="Blue"]**42% [Waiting for headers]**[/COLOR]

I would really appreciate it if anyone can help me out!  I have no idea how it's getting a write error, I know my drive has space, and the ip address isn't for my machine.

---

### Post by bmartin on 2007-09-08
Post the output of **df -H**

---

### Post by Redhead on 2007-09-08
bmartin:

Per your Acer 5050 battery icon question: I right clicked on the top panel, clicked on add to panel then scrolled down to Systems and Hardware and finally clicked on Battery Charge Monitor. I got one two-prong electrical plug icon when using AC power and two different battery icons (Power Manager 2.18.2 and Battery Charge Monitor 2.18.0) when using the battery. Before I switched from Network Manager to WICD, I ran the following command (suggested on another HOWTO)

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

Sorry, I have no input to the card reader.

A follow up on my router setting. If Wireless SSID Broadcast is Disabled, I can connect in Windows but not in Ubuntu 7.04. To connect in Ubuntu, I need to set Wireless SSID Broadcast to Enabled.

---

### Post by bmartin on 2007-09-08
> **Redhead said:**
> Per your Acer 5050 battery icon question:
[snip]
Sorry, I have no input to the card reader.
OK, so your Acer 5050 is completely different from mine. Mine has an ENE card reader and my battery monitor always shows the unplugged state. Thanks anyways. And thank you, Acer; I'll never buy another Acer laptop again.

---

### Post by lowracer on 2007-09-08
> **DarkN00b said:**
> What type of computer do you have? If it has an Acer motherboard, there is an applet that acts as a front end for acer_acpi. It makes it easy to enable/disable wifi controllers on Acer computers. It can be found at [gnomefiles.org]("http://www.gnomefiles.org/app.php/acerwificontroller"). I has to be compiled from source, but can be invaluable for Acer users. It is still at version 0.1, but I've read that it works.

Hi, I have an HP laptop dv9410us.  I got the wireless switch working.  The switch is labelled poorly.  (One side is an LED, and the other a graphic of an antenna radiating a signal out.  Guess which way is "ON"  Yeah, that's what I thought too.  Nope, toward the LED is on.  Toward the actively radiating antenna is off.  HP reverse logic again...

I have the wireless working with wicd but only in totally unencrypted mode, security totally off.  I'm nervous to continue to run my wireless network this way.  Any clues?  I read something about wpasupplicant but nothing I am trying works.  I've tried pasting the password in in quotes, without quotes, and even tried pasting in the huge hexadecimal number generated by the wpa_passphrase program, without quotes.  

I have my access point (Linksys WRT54G running DD-WRT open-source firmware) set to WPA Pre-Shared Key with TKIP+AES.  I have a windows PC (not my choice, my employer makes me use it) and it is happily talking to the router using this security level.  So I know the router is working, just can't figure out why my laptop won't connect securely.  I'm using the broadcom chipset with the ndiswrapper, if it makes any difference.

Thanks,
-Mark

---

### Post by wsx123 on 2007-09-08
It worked but I had to install the bcm43xx firware so I guess I went in a big circle, installing bcm43xx fwcutter would have done the same for me on a reinstall on an IBM thinkpad with a Belkin wireless card.
Also after using this I lost my connection manager that used to show all available wireless connections.
I think many people are posting solutions without doing thorough research.
This is the second bit of advice that caused me to do a fresh install.
Be warned!

---

### Post by brennydoogles on 2007-09-08
> **brennydoogles said:**
> Wicd did not work as well for me as wifi-radar. It would only see one network, when there are three that should be in range. Wifi-radar shows all three. I just need to figure out how to connect. I may try to remove the encryption from the network to see if I can connect that way, and then trouble shoot more from there.

so, I am able to see several networks, but even with all encryption off I am unable to connect. Any Ideas??

---

### Post by bmartin on 2007-09-08
> **lowracer said:**
> I have my access point (Linksys WRT54G running DD-WRT open-source firmware) set to WPA Pre-Shared Key with TKIP+AES.
Make sure you're using the "wext" WPA driver. I don't really know how to do that except in WICD. I don't use WPA.

In WICD, there's an Options or Preferences button that has the setting for which WPA driver you want to use.

---

### Post by Achilleus on 2007-09-09
Alright, I guess I'll post a little bit of background on my problem with any kind of internet in anything other then winblows veesta.

I originally tried installing osx86 on here, I got everything working.  Audio, exceptional video support, everything.  My only problem was ethernet and wireless, and I assumed I'd be able to get a driver or w/e and fix it pretty easily.

Well unfortunately, I'm on an aspire 3680.  The wireless card is a mini pci-e broadcom, device id of 4311.  It's nearly the exact same thing as an actual apple airport card.  The general consensus at the osx86 project is that power is not getting to the pci-e slot at boot, and therefore is not detecting anything ran off it, which also includes my Marvell Yukon ethernet.  However this cannot be true, because when I used some third party software that detects all your hardware(ran it in osx), it showed all the info of my wireless and ethernet hardware.  I told them this and it was disregarded, so I instead fell back on my second choice.


Linux.  Full of software that is incredibly difficult to install and one of the most non user friendly operating systems out there.  But hey, it beats windows(where veesta freezes when I delete a file, and it's a 50/50 chance of whether FF will even open).  Adobe makes software for Winders and OSX, but with linux I'm out of luck but at least I'll be able to open FF and browse the internet.  Hell I'll even have lots of eye candy with compiz.  Compiz-fusion and Beryl are both brilliant programs I might add.

Anyway, back to my point.  At the osx86 project, everything was pretty user friendly and all the tutorials and guides there explained which commands to use in Terminal to do what needed to be done.  Here I find no explanation of how to use this script to *maybe* get my wireless/ethernet to work.  The readme file contained within this says just to run the python script and that I'll need more libraries to run it if I'm not updated.

Well to the author of that readme file:

1. My ubuntu install is freshly downloaded about 2 hours before I tried running that script.  Do I *really* need to update it?  And how *would* I, because I don't even have internet yet!
2. *How* do I run this script?  I try to open it and it opens in a text editor.  I go in terminal and use what few commands I know from OSX to run the file, and it tells me permission denied.
3. *What* python libraries do I need?  At least tell me, that way I can see if I have them already or not, and if I don't I can boot up in to winblows and download them.

Forgive me if I sound rude because I don't mean to be.  I'm just *really* angry at Acer for selling me this piece of junk, and even angrier at Microsoft for putting out such a shitty memory eating beta-like OS and even worse, charging for it as if it's top of the line.  Hell, this laptop was 400 dollars new at wal-mart.  Since vista is oh, at *least* 150 dollars cost to Acer, that makes this one shitty laptop indeed(unfortunately, it's all I can afford).  I've been trying to get rid of windows permanently ever since I got this thing because windows and this laptop just plain don't get along.  I'm hoping that some other OS will, it's unfortunate that it's not osx86.

Any help getting my wireless/ethernet working would be *greatly* appreciated.  [Here](http://www.achilleustechnologies.com/schtuff.tiff) is a very detailed screenshot of all my hardware.

---

### Post by mikessktr on 2007-09-09
holy rusted metal batman, it worked like a charm.? but when i did n i did the sudo aptitude upgrade it through out a bunch of errors about the bcm43xx. all though when i clicked on the online (0.3.2) installer it worked with no problems. I'm actually using me wireless now.  thanks a million before this i was banging my head against the wall for about 2 months before i found this forum. :guitar:

---

### Post by dxmosiris on 2007-09-09
I found this post a couple months ago and the original fixed worked great. Now that I had a kernel update of course it ruined the compiled drivers so I sought this thread out again. It had updated and actually is a better fix than the original IMO; being that I use wicd now as a wireless manager so now I work in fluxbox exclusively. 

Thanks so much to Darkn00b and bmartin for taking this project on and helping so many users find a solution to this very annoying problem. ( f broadcom ). =] Thanks for saving so many hours on finding a working solution that works so seamlessly.

---

### Post by DarkN00b on 2007-09-09
> **Achilleus said:**
> Alright, I guess I'll post a little bit of background on my problem with any kind of internet in anything other then winblows veesta.

I originally tried installing osx86 on here, I got everything working.  Audio, exceptional video support, everything.  My only problem was ethernet and wireless, and I assumed I'd be able to get a driver or w/e and fix it pretty easily.

Well unfortunately, I'm on an aspire 3680.  The wireless card is a mini pci-e broadcom, device id of 4311.  It's nearly the exact same thing as an actual apple airport card.  The general consensus at the osx86 project is that power is not getting to the pci-e slot at boot, and therefore is not detecting anything ran off it, which also includes my Marvell Yukon ethernet.  However this cannot be true, because when I used some third party software that detects all your hardware(ran it in osx), it showed all the info of my wireless and ethernet hardware.  I told them this and it was disregarded, so I instead fell back on my second choice.


Linux.  Full of software that is incredibly difficult to install and one of the most non user friendly operating systems out there.  But hey, it beats windows(where veesta freezes when I delete a file, and it's a 50/50 chance of whether FF will even open).  Adobe makes software for Winders and OSX, but with linux I'm out of luck but at least I'll be able to open FF and browse the internet.  Hell I'll even have lots of eye candy with compiz.  Compiz-fusion and Beryl are both brilliant programs I might add.

Anyway, back to my point.  At the osx86 project, everything was pretty user friendly and all the tutorials and guides there explained which commands to use in Terminal to do what needed to be done.  Here I find no explanation of how to use this script to *maybe* get my wireless/ethernet to work.  The readme file contained within this says just to run the python script and that I'll need more libraries to run it if I'm not updated.

Well to the author of that readme file:

1. My ubuntu install is freshly downloaded about 2 hours before I tried running that script.  Do I *really* need to update it?  And how *would* I, because I don't even have internet yet!
2. *How* do I run this script?  I try to open it and it opens in a text editor.  I go in terminal and use what few commands I know from OSX to run the file, and it tells me permission denied.
3. *What* python libraries do I need?  At least tell me, that way I can see if I have them already or not, and if I don't I can boot up in to winblows and download them.

Forgive me if I sound rude because I don't mean to be.  I'm just *really* angry at Acer for selling me this piece of junk, and even angrier at Microsoft for putting out such a shitty memory eating beta-like OS and even worse, charging for it as if it's top of the line.  Hell, this laptop was 400 dollars new at wal-mart.  Since vista is oh, at *least* 150 dollars cost to Acer, that makes this one shitty laptop indeed(unfortunately, it's all I can afford).  I've been trying to get rid of windows permanently ever since I got this thing because windows and this laptop just plain don't get along.  I'm hoping that some other OS will, it's unfortunate that it's not osx86.

Any help getting my wireless/ethernet working would be *greatly* appreciated.  [Here](http://www.achilleustechnologies.com/schtuff.tiff) is a very detailed screenshot of all my hardware.

1. Probably not if its only been a couple hours.

2. It looks like you're running KDE. Neither bmartin nor I have been able to figure out how to execute a python script in KDE without using the command line. Its a mime-type issue. There is a separate section of the instructions for KDE users. Look at the part of the howto called [SIZE="5"][COLOR="Blue"]_Section2 - KDE_[/COLOR][/SIZE].

3. You need the python 2.5.1 runtime libraries. These are required before the script can be run.

I hope that helps.

---

### Post by Achilleus on 2007-09-09
Actually I'm, using gnome--but I'll check real quick to see if I have the python runtime library 2.5.1.  Thank you very much for your help :D  That SS was taken in os x btw ;)

---

### Post by Japh on 2007-09-09
I tried out the steps and it all seemed to work fine. I rebooted and checked ```
ndiswrapper -l
```

The output:
```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

Now the problem is that after I rebooted, the wireless was turned off(Dell Inspiron E1505).
So I tried turning it back on with Fn+F2 but it doesn't work.

Is there an alternative way of turning it on?

--J

---

### Post by brennydoogles on 2007-09-09
> **Japh said:**
> I tried out the steps and it all seemed to work fine. I rebooted and checked ```
ndiswrapper -l
```

The output:
```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

Now the problem is that after I rebooted, the wireless was turned off(Dell Inspiron E1505).
So I tried turning it back on with Fn+F2 but it doesn't work.

Is there an alternative way of turning it on?

--J

I had the same problem a while ago, and there is a solution (although you will need to remember to do the opposite if you are ever on an airplane). If you reboot your computer, you will see (before you boot into an OS) an option to enter setup, or change BIOS settings. Use that option (usually by hitting an f-key), and change your wireless radio settings to ON. I hope that helps!!

---

### Post by bereanone on 2007-09-09
Had a little trouble at first, probably since I had already tried another way. Reinstalled Fiesty Fawn, tried this method first.  Had some trouble since the Automatix site was down (not sure why) Once their site came back online, I tried again.  Worked like a CHARM!!! Finally. Now if only I could get Wine to work this well...:popcorn::)

---

### Post by brennydoogles on 2007-09-09
Ok, strange turn of events.... My wireless works perfectly on an unsecured Linksys router, but on my belkin router at home it does not work with or without encryption. Is this normal??

---

### Post by Japh on 2007-09-09
Hi, thank you for the reply, I tried what you told me to do brennydoogles, but it didn't work. I forgot to mention that the main thing is that even with the wireless "on", the card doesn't show up in the System > Administration > Network.

--J

---

### Post by lowracer on 2007-09-10
> **bmartin said:**
> Make sure you're using the "wext" WPA driver. I don't really know how to do that except in WICD. I don't use WPA.

In WICD, there's an Options or Preferences button that has the setting for which WPA driver you want to use.

Cool, thanks.  I was using the ndiswrapper driver for WPA.  I'll try wext.

---

### Post by kah00na on 2007-09-10
Sweet!!!  Finally after 3 months this dumb Broadcom card is working.  I should have searched the forums first.  Shesh...  THANKS!!!!

No more being chained to the desk!  Off to the couch for me!

---

### Post by richnormand on 2007-09-10
Thanks.
Worked perfectly.

---

### Post by bmartin on 2007-09-10
Our success rate keeps going down on this thread... hmmm...

Anyways, I wanted to let everyone know that I'm working with another forum member to create a new piece of software that's a bit more general purpose than this installer. It's going to detect many different wireless devices and locate/compile/install the necessary drivers. We're currently working on selecting a name. Voice your input on [this thread]("http://ubuntuforums.org/showthread.php?t=547740").

---

### Post by arabxptyltd on 2007-09-11
Well, stone the crows (that's a good thing).

I have a Dell 5150, and my Wireless BCM4306  has just never worked under Linux. Over the years I've been through CentOS, Fedora, Ubuntu 6.10 and now Ubuntu 7.04 without it succeeding. I've spent many days on this problem.

I was excited to read the positiveness of your HOWTO, so I carefull followed the instructions.  The installed cleared my dmesg errors of  [ 3370.740000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.

But my wireless still failed to start. Ndiswrapper reported everything fine, but it simply would not find a DHCP server. I was prepared to undo all wireless security on my router, just in case, and was about to set up a static IP when I decided to reboot a second time (I'd seen this problem on my T60 after moving between wireless points).

A second reboot, and still the wireless was not operational. Re-checked and then an ifdown eth1 and ifup eth1 and it works.  I'm now connected wirelessly.  

It still seems flaky in configuration (and I've been in this position under Fedora before), and obviously it just doesn't play well between wired and wireless, however this installation was definitely the simplest to date, so hat off there.

Let's hope it works long enough for me to solve my next long running problem with Ubuntu (it worked under CentOS/Fedora). This is the right NVIDIA driver and then to get my Dell 24" widescreen monitor working at 1920x1050  (it's such a waste not working properly with either laptop).

Ronald
[http://blog.arabx.com.au](http://blog.arabx.com.au)

---

### Post by bmartin on 2007-09-11
> **arabxptyltd said:**
> Let's hope it works long enough for me to solve my next long running problem with Ubuntu (it worked under CentOS/Fedora). This is the right NVIDIA driver and then to get my Dell 24" widescreen monitor working at 1920x1050  (it's such a waste not working properly with either laptop).[http://blog.arabx.com.au](http://blog.arabx.com.au)
I find the best way to fix the resolution is to run **sudo dpkg-reconfigure xorg-xserver** and select the correct resolution, then after loading X (GNOME, KDE, etc.), using the **xrandr** program (you might have to install it w/ APT) to set the correct resolution. xrandr has no GUI, but it's pretty intuitive to use.

---

### Post by aguttorm on 2007-09-11
*mad scientist voice*   IT'S ALIVE!!  IT'S ALIVE!!

Thank you so much for this.  I've been fighting with Ubuntu for about a week now, trying different how-to's to get my wireless running.  Thanks to this, I've got wireless now!  Granted, I had to use XP to download the install program, but not anymore!

System stats:

Dell Inspiron 1150
Ubuntu Edgy Eft 6.10
Broadcom 4306 802.11b/g wireless

Allen G. 
Sandy, OR   USA

---

### Post by gledgard on 2007-09-11
Thanks a lot, boy :D I was fighting win a new Compaq v3417la for about one month, now i have a home and I can dispose the windows (vista)

compaq presario v3417la
amd sempron 3500
1gb ram
120gb hdd
Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)

Thanks again

---

### Post by sqlpython on 2007-09-11
Would this work on my Kubuntu 7.04 amd64-bit install?

Card is> 
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01
)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
  is your method similar to the GUI ndisgtk wrapper package from Adept Added Software.?

I do have my card working but KnetworkManager will not connect to ESSIDs. I had to add the Wlassistant to connect and leave KnetworkManager to handle wired..
However Kmail seeing KnetworkManager Disconnected will not Download Email..

 I installed the WinXP 64bit driver bcmwl564.sys like so..
...Install assumes no ndiswrapper package installed
Installed from Adept.....  ndis-gtk package
.....Blacklisted bcm43xx  
 $sudo su
$sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
$sudo shutdown -r now
..You can check if blacklisted like so..
cat /etc/modprobe.d/blacklist
....Add WinXP drivers for Dell 1390..Download Dell package and unzip.. R151519
.....fils are
bcm43xx64.cat  bcmwl564.sys  bcmwl5.sys  bcmwl6.inf  bcmwl6.sys
bcm43xx.cat    bcmwl5.inf   bcmwl6.pnf
..that is a combo of the 32 and 64-bit..
..Install ndiswrapper with drivers and reboot

$sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf
$sudo ndiswrapper -l
$sudo ndiswrapper -m
$sudo modprobe ndiswrapper
$sudo shutdown -r now

..when you are rebooted 
iwlist scanning 
..to check connection
Seems to install the 64-bit or 32-bit as needed per the bcmwl5.inf file instructions.

BUT   KnetworkManager does not play well with amd64 drivers and broadcom wifi..

So seeing what I have done and Knowing the Knetworkmanager incomaptibilty what are the issues with this scenario and the gtk-python install of bcm43xx which does not install easily here........

---

### Post by bmartin on 2007-09-11
> **sqlpython said:**
> Would this work on my Kubuntu 7.04 amd64-bit install?
I really don't know. I haven't heard back from any 64-bit users saying that it worked or it didn't. You'd be the first. You can install the firmware (bcm43xx) or the ndiswrapper driver (bcmwl5) with it.

> **sqlpython said:**
> is your method similar to the GUI ndisgtk wrapper package from Adept Added Software.?
Not really. The installer works for just one installer and it compiles ndiswrapper for you as part of the installation procedure.

> **sqlpython said:**
> So seeing what I have done and Knowing the Knetworkmanager incomaptibilty what are the issues with this scenario and the gtk-python install of bcm43xx which does not install easily here........
If you select the ndiswrapper/bcmwl5 install, then the bcm43xx kernel module will be unloaded and blacklisted; if you select the bcm43xx kernel module, the firmware will be installed and the ndiswrapper module unloaded and removed from /etc/modules (so it doesn't boot up).

Let me know if it works. It might not work at all. If you can figure out how to get it to work, let me know.

---

### Post by ann smith on 2007-09-12
Hello everyone!
I'm extremely  new to Linux  and I have a serious problem installing Kubuntu 7.04 from a liveCD. The installation gets blocked at this error 

"bcm43xx: error: microcode bcm43xx_microcode5.fw not available or load failed";

 I tried the solution in the other post where a user had the same problem as I have, but I can't manage.
I want to install Kubuntu beside WinXP, I have 4 partitions: 3 NTFS for XP and one fat32 for Linux; I don't understand how to use the installer you've created and  if I dont have kubuntu installed how can i use the linux commands? 
It would be great if someone can help me;
Thanks a lot!

---

### Post by brennydoogles on 2007-09-12
> **ann smith said:**
> Hello everyone!
I'm extremely  new to Linux  and I have a serious problem installing Kubuntu 7.04 from a liveCD. The installation gets blocked at this error 

"bcm43xx: error: microcode bcm43xx_microcode5.fw not available or load failed";

 I tried the solution in the other post where a user had the same problem as I have, but I can't manage.
I want to install Kubuntu beside WinXP, I have 4 partitions: 3 NTFS for XP and one fat32 for Linux; I don't understand how to use the installer you've created and  if I dont have kubuntu installed how can i use the linux commands? 
It would be great if someone can help me;
Thanks a lot!

hmmm... You may want to consider making the fat partition into an Ext3 filesystem, because it is more stable, and you can get a driver to allow your windows partition to read it. As for your installation problems, you may try either getting another live cd (could be a bad burn on the one your using) or try the alternate cd, which may work out better. Hope that helps!!

---

### Post by bmartin on 2007-09-12
> **brennydoogles said:**
> hmmm... You may want to consider making the fat partition into an Ext3 filesystem, because it is more stable, and you can get a driver to allow your windows partition to read it.
It might be possible to install Linux on FAT32, but I doubt it. The FAT file system doesn't permit symbolic links, which are essential with Linux. ext3 doesn't require defragmentation. I second brenny on this one; use ext3 and install [the Windows driver]("http://kennethhunt.com/archives/001314.html"). Trust me: you'll like it.

I wanted this driver recently, too. My girlfriend bought a great Windows game (it's simply called "Fate") and I couldn't get it to work in Wine, plus I get the "Windows can't be activated" error in qemu. I'm now a dual-booter ](*,)

---

### Post by ann smith on 2007-09-12
I still have the problem the instalation doesn't get as far as selecting the types of partions; it gets blocked before the install window, just after checking the hardware and loading the programs with this error:
"bcm43xx:error: microcode "bcm43xx_microcode5.fw" not available or laod failed"; so my conclusion is that I don't have the wireless driver, but shouldn't that be installed after I install the system?
Thank you and please help

---

### Post by DarkN00b on 2007-09-12
> **ann smith said:**
> I still have the problem the instalation doesn't get as far as selecting the types of partions; it gets blocked before the install window, just after checking the hardware and loading the programs with this error:
"bcm43xx:error: microcode "bcm43xx_microcode5.fw" not available or laod failed"; so my conclusion is that I don't have the wireless driver, but shouldn't that be installed after I install the system?
Thank you and please help

Can you remove the card until after you have installed Ubuntu?

---

### Post by ann smith on 2007-09-12
I dont think so; isn't there another way?

---

### Post by ggardei on 2007-09-12
Writing this post wirelessly on my Thinkpad T23 using a Linksys wireless card that **was** unssuported by Linux.

Thanks for your help

=D>

---

### Post by ann smith on 2007-09-12
I tried to install it from the alternative CD and everything went well untill it finished the  installation; when it's finished and it tries to load Kubuntu I get the same error as before and the system wont load.This should be essier to fix I hope? please if anyone can help me

---

### Post by DarkN00b on 2007-09-12
Try booting in safe mode from Grub. This will get you to a command line. Type ```
startx
``` and hit the enter key. On another computer, download the offline installer move them to your machine with a flash drive. You can also install from the command line if you know how -- just follow the instructions I have listed for KDE. They will work for any version of Ubuntu.

---

### Post by lowracer on 2007-09-12
> **lowracer said:**
> Cool, thanks.  I was using the ndiswrapper driver for WPA.  I'll try wext.

Hate to quote my own message but just wanted to report ...   wext worked.  I have now WPA2 access and it's working perfectly.  We now have wireless access.  Somewhere in there I did upgrade to the 2.6.22-11 kernel though, not sure if that played a role.

---

### Post by bmartin on 2007-09-12
I'm sorry it took so long to figure out what was wrong. I'm glad to hear it's working, though. DarkN00b, want to point out in the instructions that the WPA driver should be set to **wext** if you're using WICD?

---

### Post by DarkN00b on 2007-09-13
> **bmartin said:**
> I'm sorry it took so long to figure out what was wrong. I'm glad to hear it's working, though. DarkN00b, want to point out in the instructions that the WPA driver should be set to **wext** if you're using WICD?

I'll make the change right now.

---

### Post by kenfeyl on 2007-09-13
I have to say, this script is like the immaculate conception. I had tried just about everything under the friggin' sun. Readmes, readmes without fluff, readmes for my machine, but everything was just a false prophet. Then came this baby lying in the manger and boom, wireless works fine in one shot. And here I am today to give thanks.

I'm on an HP dv6000z laptop running a dual-core AMD Turion under the amd64 arch.

---

### Post by ziul1979 on 2007-09-13
Thanks a lot, I tried several ways to activate the wireless connection on my HP Pavilion dv6448se, and with the others methods I can turn on the blue light of the wifi but the wifi itself don't works. But with this method I just do one click and installed eveyrthing I need to work, reboot the system and works, I'm using a ubuntu 7.04 fresh install if this can help somenone (2.6.20-15-generic).

Now I'm going to configure the others stuff on the laptop, bye.

Thanks

---

### Post by alira on 2007-09-13
Worked great but the card is not recognized now. 

/0/1                                                       network             BCM43xG 802.11 b/g

---

### Post by alira on 2007-09-13
I'm such a noob!! Working now. Thank you for the help. I love LINUX!!!

---

### Post by ann smith on 2007-09-13
I did everything as you said DarkNoob and now I get this error when I'm trying to launch ./installer.py:
 file "./installer.pw", line12, in <module>
 import pygtk
 importerror: no module named pygtk
and the installer stops.

---

### Post by bmartin on 2007-09-13
You need to either update all your system packages (if you did a fresh install) or install the PyGTK stuff manually:
```
sudo aptitude update
sudo aptitude install python-gtk2
```

---

### Post by RamsesII on 2007-09-13
This tutorial was very helpful. I finally get the wifi on this 
:evil: dell with its so notorious wifi card which doesn't work properly. Thank you to all the people who made this possible. I was wondering what's the point to have dell and ubuntu partners if all dell users can't have all their hardware, especially the one sold by default on a dell recognized by Ubuntu ?
but this forum solve my "lifelong" problem, so long that I had renounced to look for a driver.

---

### Post by bmartin on 2007-09-13
> **RamsesII said:**
> I was wondering what's the point to have dell and ubuntu partners if all dell users can't have all their hardware, especially the one sold by default on a dell recognized by Ubuntu ?
The fact that they're partners doesn't mean all of their stuff is 100% Linux compatible. Dell's not my favorite company (I prefer HP or Compaq for laptops), but in their defense, the hardware that runs on their Ubuntu-powered laptops is Linux-compatible (note: The Conexant modems in those Dell computers employ the Linuxant driver, which isn't free at all, and of course there are other issues like those awful ATI drivers).

They may be partners now, but that doesn't mean Dell is going to provide support for all of their hardware on every machine that they've ever sold.

---

### Post by kevdog on 2007-09-14
Question about the script

Im running kernel version 2.6.22.6.
I downloaded the offline version of the script

 I ran the installer. py -- it first told me that my kernel version wasnt supported since I was I was missing a deb which wasnt compiled for the kernel.  Can you elaborate what this means?

I found the source code:
```
# check for compatible ndiswrapper DEB
haveDeb=os.system("[ -f deb/ndiswrapper-*`uname -r`.deb ]");
if (haveDeb != 0):
        os.system("xmessage -file UNSUPPORTED_KERNEL")

```

Im not sure if this is the best way to do this since I am running ndiswrapper compiled from svn that was installed manually and not through the apt system.  Would a better method to simply execute the ndiswrapper -v statement and see if anything shows?  Im not exactly sure what is meant by this anyway??

Anyway the script did proceed -- although I thought it would bail or exit at this point since the error message suggested or hinted that it would exit.  I was surprised to find that all the options available.  I didnt try any at this point.

Just some feedback -- I can see someone put a lot of time into this script.

---

### Post by bmartin on 2007-09-14
> **kevdog said:**
> Im running kernel version 2.6.22.6.
<snip>
it first told me that my kernel version wasnt supported since I was I was missing a deb which wasnt compiled for the kernel.  Can you elaborate what this means?

I compiled ndiswrapper and packaged it as a DEB for the newest supported version of the generic kernel for Dapper/Edgy/Feisty/Gutsy. Last time I checked, those versions were:
[LIST]
[*]2.6.17-10-generic
[*]2.6.20-15-generic
[*]2.6.20-16-generic
[*]2.6.22-10-generic
[/LIST]
You're running a kernel not found on that list; the installer won't let you pick the "use the precompiled ndiswrapper option"; I left all of the other options in there in case this happened to anyone.

> **kevdog said:**
> Im not sure if this is the best way to do this since I am running ndiswrapper compiled from svn that was installed manually and not through the apt system.  Would a better method to simply execute the ndiswrapper -v statement and see if anything shows?  Im not exactly sure what is meant by this anyway??
You do bring up a good point. **ndiswrapper -v** is executed in the bcm43xx-ndiswrapper.sh file, which is used to determine whether ndiswrapper is compiled on your system or not. It checks against **the current stable version**, which I keep a copy of on googlepages.com, which means that it'd replace your version (presumably 1.48-something) with 1.47. I should do a floating-point comparison instead.

---

### Post by kevdog on 2007-09-14
Did you use the checkinstall tool to make your debs???

---

### Post by DarkN00b on 2007-09-14
I'm just dropping a note that I've missed a lot of posts because the forum is not notifying me by e-mail when there is a new post. I'll go back and read the threads I've missed and try to help where I can. My apologies for this and assure you that I was not ignoring the thread.

---

### Post by bmartin on 2007-09-14
> **kevdog said:**
> Did you use the checkinstall tool to make your debs???
No, but I probably should've. What I do is:
[LIST=1]
[*]Run 'make' with the argument for the desired kernel version.
[*]Copy the files that would normally be installed to the respective subdirectories.
[*]Run dpkg -b to build the DEB archive.
[/LIST]
I have all of this done inside a script for all kernel headers installed on my computer.

Should I be using checkinstall? It sounds a lot easier than what I've been doing, especially if the files used with ndiswrapper change at all.

---

### Post by sirbobbinhood on 2007-09-14
This is my first time with Ubuntu so I have no idea what I'm doing. I tried the steps about for the gnome interface and somehow after I ran the .py file I don't have the option of using a wireless network anymore. I can still see it in the hardware profile section but other than that it doesn't seem to exist anymore any ideas?

---

### Post by kevdog on 2007-09-14
bmartin

I dont know if you should run checkinstall.  I tried running checkinstall this morning on my compiled svn ndiswrapper sources -- it took like 10 mintues -- and then I finally got an error (sorry I didnt save it).  Im trying to learn how to make .deb files from compiled sources, and have to admit I really dont have it mastered as of yet.  Ive made a few posts asking for help, and everything has come back run checkinstall.  I should probably go back to the 16 generic kernel and try it again.  

Also Id like to make some additional suggestions for your installer script to ensure that the ndiswrapper interface is established as wlan0 after the procedure rather than something else.  This has been a major source of frustration for me, and know how to do it by hand, however have not integrated it into script, although I have some ideas.

---

### Post by bmartin on 2007-09-14
OK. Mine has always been eth1 on every distro I've installed on this laptop. Do you have a link to instruction on how to make it wlan0?

---

### Post by bmartin on 2007-09-14
> **sirbobbinhood said:**
> This is my first time with Ubuntu so I have no idea what I'm doing. I tried the steps about for the gnome interface and somehow after I ran the .py file I don't have the option of using a wireless network anymore. I can still see it in the hardware profile section but other than that it doesn't seem to exist anymore any ideas?
Did you install ndiswrapper or the firmware?

If ndiswrapper, what is the output of **ndiswrapper -l**?

If the firmware, what is the output of **lsmod | grep bcm43xx**?

---

### Post by kevdog on 2007-09-14
About the wlan0 standard

Although no a defacto standard -- all the documentation on the ndiswrapper website references wlan0 (about 100 times).  It even lists a troubleshooting section about if your interface isnt wlan0 (and then at the end lists a disclaimer stating it could be something else)

If fact the command:
ndiswrapper -m

Creates a file call /etc/modprobe.d/ndiswrapper that states:
alias wlan0 ndiswrapper

This command supposedly loads the ndiswrapper module when the wlan0 interface is brought up.

In fact the presence of another interface, for example eth1 along with a eth1 entry in /etc/iftab can really screw things up!

Im just saying that for consistency and given that part of the installation procedure assumes a wlan0 interface, I believe it would be correct to add to the installation procedure setting up the wlan0 interace which includes possibly altering the /etc/iftab file and /etc/network/interfaces file (if people are using network manager -- ohhh ugly).

I know you've seen my instrutions before, so Im not listing the entire set, but this is what I recommend for troubleshooting the wlan0 interface (im sure these instruction could be limited to about 4 -10 steps executed in code):

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case.
If after rebooting, and you issue the following command:
```
ifconfig
```
And you do not see an interface named wlan0, then continue.
Below are some strategies that I have used to ensure that your wireless device is assigned to the wlan0 interface.

**Verification/Modification of /etc/iftab file**

The /etc/iftab file acts to permanently asssociate a given MAC Address with an interface name.  Additions in this file are only necessary if you need to lock down the interface name with a MAC Address.  First discover what interface name is currently associated to your network card MAC Address:
```
lshw -C network
```

Example output:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       **serial: 00:12:17:35:17:10 **
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

In the example above my card's MAC Address - 00:12:17:35:17:10 - is currently assigned to wlan0 (logical name line).  If your card is assigned to a different logical name (such as eth1, ath0, ra0), then modifications will be needed to your /etc/iftab file.  

To modify your /etc/iftab file:
```
gksu gedit /etc/iftab
```

You will need to ensure your interface name is associated with wlan0 rather than a different interface name. There are two ways to accomplish this: 
#1) Let the computer do it automatically at boot, 
#2) Manually make the association  

In case #1 manually comment all the associations listed in your /etc/iftab file -- allow the computer to assign them internally at boot.  **This solution is probably the most viable for most users.**  An example of how to accomplish this:  

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1

```

Because the association of eth1 with the MAC Address was commented, the computer will internally and automatically make the assocation of an interface name with the MAC address.  This process of associating wlan0 with the networking device's MAC Address should work about 99% of the time.  If for some reasom it does not, proceed to step #2.

In case #2 - Manually make the association you need to ensure there is only one MAC address associated with one interface name.

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1
wlan0 mac 00:12:17:35:17:10 arp 1

```

In this example the old interface associated of eth1 was commented, and the new association of wlan0 to the card MAC address was made manually.

If modification of the /etc/iftab file was performed, a reboot is recommended at this time.
```
sudo shutdown -r now
```

**Modification of /etc/network/interfaces file**

First step is to comment out all the unnecessary interface names with the file.  In order to discover what interface names are currently needed:

```
lshw -C network
```
With all the devices listed, note their logical names.  An example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

Only the names mentioned with this command need to be listed in the /etc/network/interfaces file (along with the loopback address).

First backup your current interface file configuration in case something goes wrong:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

To modify your /etc/network/interfaces file:
[CODE]gksu gedit /etc/network/interfaces
```


A basic interface file, might include the following (assuming a wired ethernet device is present - eth0, and the wireless device installed with ndiswrapper - wlan0) -- Note in this example I commented out the old eth1 interface -- I could have also removed these lines to have the same effect.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

```

Further modications may be needed to this file, depending if you need to run your card in roaming mode (convenient with laptops that often connect to different routers of networks), configure your card with static IP address, desire to set WEP/WPA authentication parameters manually, etc.  Again there are many possibilites at this point, far too many to list the different permutations, however this gives you a basic starting point.

---

### Post by Clawinus on 2007-09-14
I have been advised to use the following command to install the firmware for Broadcom 43xx

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys

Please tell me what the command will do, particularly the modifier "-w".
As a newbie I do not understand the syntax of the command.
Thanks

---

### Post by bmartin on 2007-09-14
> **Clawinus said:**
> I have been advised to use the following command to install the firmware for Broadcom 43xx

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys

Please tell me what the command will do, particularly the modifier "-w".
As a newbie I do not understand the syntax of the command.
Thanks
**-w /lib/firmware** writes the firmware to the /lib/firmware directory. The command removes the firmware from the bcmwl5.sys driver. In English, this means that the part of the Windows software that makes your wireless card work is removed from the .sys file.

The installer at the first post of this thread contains the firmware already extracted so you don't have to go through the headache of using bcm43xx-fwcutter. In fact, most of the people on this thread will recommend that you don't use the firmware at all; using ndiswrapper will work much better. Again, the installer at the beginning of this thread can take care of that for you.

---

### Post by thelost on 2007-09-15
IF I was using The Firmware and getting poor results would it be advisable to move to ndiswrapper? I used fwcutter and it worked ok for me, and considering the struggle I had to get wireless working with Fiesty I am loath to do anything that might break it.

So how painless is it to move from the firmware to ndiswrapper? What do I need to uninstall if anything?

---

### Post by bmartin on 2007-09-15
> **thelost said:**
> IF I was using The Firmware and getting poor results would it be advisable to move to ndiswrapper?
Yes. It's a common complaint about the firmware.

> **thelost said:**
> So how painless is it to move from the firmware to ndiswrapper? What do I need to uninstall if anything?
If you run the ndiswrapper installer, it'll disable the firmware.

---

### Post by ann smith on 2007-09-15
Hello! Thanks so much for helping me; I managed to boot Kubuntu and now I'm writing from Kubuntu using the LAN connection I'm so happy I can't wait to learn using Linux; Thank you for all the help.

---

### Post by brennydoogles on 2007-09-15
> **ann smith said:**
> Hello! Thanks so much for helping me; I managed to boot Kubuntu and now I'm writing from Kubuntu using the LAN connection I'm so happy I can't wait to learn using Linux; Thank you for all the help.

Did you end up going with the EXT3 filesystem? I hope everything works out well for you!!

---

### Post by Kopachris on 2007-09-15
Good guide!  For Apple PPC users, try this:
[http://ubuntuforums.org/showthread.php?t=550717](http://ubuntuforums.org/showthread.php?t=550717)
I hope all you PPC users don't have to go through 2 straight days of hunting to figure it out like I did.

---

### Post by Podmornik on 2007-09-15
It's a good guide but it doesn't help me. My HP 6715B with Broadcom 4311 wireless card doesn't recognize my card.
Lspci:
> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916

I have ubuntu gutsy (7.10). What to do to make it recognize my wireless card?

---

### Post by brennydoogles on 2007-09-15
> **Podmornik said:**
> It's a good guide but it doesn't help me. My HP 6715B with Broadcom 4311 wireless card doesn't recognize my card.
Lspci:


I have ubuntu gutsy (7.10). What to do to make it recognize my wireless card?

Is it possible that it is a bug in Gutsy?? I haven't used it, but it's possible with a new release.

---

### Post by bmartin on 2007-09-15
> **Kopachris said:**
> Good guide!  For Apple PPC users, try this:
[http://ubuntuforums.org/showthread.php?t=550717](http://ubuntuforums.org/showthread.php?t=550717)
I hope all you PPC users don't have to go through 2 straight days of hunting to figure it out like I did.
This is the same as the firmware method, which is available at the beginning of this thread via the GTK interface and may not be appropriate for all PPC users.

---

### Post by bmartin on 2007-09-15
> **Podmornik said:**
> Broadcom 4311 wireless card doesn't recognize my card.
<snip>
What to do to make it recognize my wireless card?
Try **sudo update-pciids** and **sudo update-usbids**

Then see if it shows up under **sudo lshw -C network**

---

### Post by prophet665 on 2007-09-15
I am an extreme *nix noob (how many posts start with that sentence?).  I cannot get the python script to run because it keeps opening up in gedit instead of the python compiler.

What am I doing wrong?  I was under the impression that a python compiler is included with Ubuntu 7.04.

What ridiculously easy thing am I overlooking here?

---

### Post by prophet665 on 2007-09-15
I just looked in my add/remove applications and python 2.5 is installed.  So my problem is apparently associating .py scripts with the compiler.

---

### Post by bmartin on 2007-09-15
> **prophet665 said:**
> I am an extreme *nix noob (how many posts start with that sentence?).  I cannot get the python script to run because it keeps opening up in gedit instead of the python compiler.

What am I doing wrong?  I was under the impression that a python compiler is included with Ubuntu 7.04.
We've had this problem in KDE before, but not GNOME. I'm assuming you're in GNOME because you mentioned Ubuntu and gedit, not Xubuntu or kate or anything like that.

When you double-click the file, are you presented with any options? I get a GTK+ dialog asking:
[quote="GTK+"]Do you want to run "wifix.py" or display its contents?

"wifix.py" is an executable text file.[/QUOTE]
Did you extract the archive or did you try to run the file from within the archive? You have to first use the "Extract" button to extract the files from the archive, then you have to find the extracted file and run that.

In plain English:
1. Double-click on the archive.
2. Click "Extract".
3. Ensure the "Re-create folders" checkbox is checked.
4. Click "Extract".
5. Close the Window.
6. Assuming you downloaded the archive to your desktop, double-click the new folder on your desktop, then double-click on **installer.py**.

---

### Post by kenfeyl on 2007-09-15
Hi everyone,

Thanks for the script. It started everything working like magic, but now I have a new problem. My wireless seems to fail after about two hours of use, give or take. Turning the wireless switch off and on, locking the screen and logging out and back in all fail to fix this. The only remedy is to restart the computer. Can anyone provide any insights, or ways I might go about diagnosing this issue? This has happened three times now, so it seems consistent. I'm on a HP dv6000z laptop running a dual-core AMD Turion 64 with 2G of RAM and a fresh Ubuntu Feisty install, and I used this wireless script to get things going. Any tips would be appreciated. Thanks.

Ken:popcorn:

---

### Post by prophet665 on 2007-09-15
> **bmartin said:**
> We've had this problem in KDE before, but not GNOME. I'm assuming you're in GNOME because you mentioned Ubuntu and gedit, not Xubuntu or kate or anything like that.

When you double-click the file, are you presented with any options? I get a GTK+ dialog asking:

Did you extract the archive or did you try to run the file from within the archive? You have to first use the "Extract" button to extract the files from the archive, then you have to find the extracted file and run that.

In plain English:
1. Double-click on the archive.
2. Click "Extract".
3. Ensure the "Re-create folders" checkbox is checked.
4. Click "Extract".
5. Close the Window.
6. Assuming you downloaded the archive to your desktop, double-click the new folder on your desktop, then double-click on **installer.py**.

Ok.  Turns out I was trying to open it up from the extract dialog box.  Once I manually browsed my Home directory, it worked like a charm.  I am now posting from my wireless network.  Electronic high fives all around.

Whoever came up with this graphically installation is the MAN!  I definitely want to learn the intricacies of Ubuntu, but running in to problems from the very beginning can be demoralizing, to say the least.

Thanks for the help everyone.  i am sure i will be back here later.

---

### Post by prophet665 on 2007-09-15
> **kenfeyl said:**
> Hi everyone,

Thanks for the script. It started everything working like magic, but now I have a new problem. My wireless seems to fail after about two hours of use, give or take. Turning the wireless switch off and on, locking the screen and logging out and back in all fail to fix this. The only remedy is to restart the computer. Can anyone provide any insights, or ways I might go about diagnosing this issue? This has happened three times now, so it seems consistent. I'm on a HP dv6000z laptop running a dual-core AMD Turion 64 with 2G of RAM and a fresh Ubuntu Feisty install, and I used this wireless script to get things going. Any tips would be appreciated. Thanks.

Ken:popcorn:

I have run in to a similar problem that just happened, and I hope it is not a chronic thing.  I am on Earthlink and they use their own DNS servers.  For some reason after I manually entered the DNS servers for my wireless connection, it dropped them sometime between the time I hit post reply, typed a message, and then hit submit post.

I really hope this doesn't happen again.

---

### Post by bmartin on 2007-09-15
> **prophet665 said:**
> Whoever came up with this graphically installation is the MAN!  I definitely want to learn the intricacies of Ubuntu, but running in to problems from the very beginning can be demoralizing, to say the least.
I'm working on a "better" WiFi installer; it'll blow this one away. It uses Python and MySQL to determine which WiFi device you have installed and then fetch/compile/install/etc. what's necessary to make it work.

Don't worry about having problems at the beginning. Linux is very rewarding, especially if you learn a scripting language like BASH. You can write files to take care of all the "chores" of maintaining an OS (like keeping your security up to date, running programs periodically, etc.) Like with anything, practice makes perfect. Soon you'll be able to diagnose and solve problems that other people encounter.

---

### Post by bmartin on 2007-09-15
> **prophet665 said:**
> I have run in to a similar problem that just happened, and I hope it is not a chronic thing.  I am on Earthlink and they use their own DNS servers.  For some reason after I manually entered the DNS servers for my wireless connection, it dropped them sometime between the time I hit post reply, typed a message, and then hit submit post.

I really hope this doesn't happen again.
Are either of you using the firmware? The firmware tends to drop connections; I've never had a problem using ndiswrapper.

---

### Post by kenfeyl on 2007-09-15
How do I tell whether I'm using the firmware?

All I did was run the install script and ka-bling, wireless was working. Does the script install firmware, ndiswrapper, or what?

> **bmartin said:**
> Are either of you using the firmware? The firmware tends to drop connections; I've never had a problem using ndiswrapper.

---

### Post by bmartin on 2007-09-15
The default install is ndiswrapper, but there are options to install either. If all you did was press the install button, you've install ndiswrapper.

I haven't heard of anyone having problems with ndiswrapper and dropped connections.

---

### Post by kenfeyl on 2007-09-15
Yep, I think I'm using ndiswrapper because I right-clicked on the wireless bars, hit "Connection Information" and unearthed this gem: "Driver: ndiswrapper." Crap-o.

Is there anything I can do, once the connection is down, to diagnose the issue?

> **bmartin said:**
> The default install is ndiswrapper, but there are options to install either. If all you did was press the install button, you've install ndiswrapper.

I haven't heard of anyone having problems with ndiswrapper and dropped connections.

---

### Post by bmartin on 2007-09-15
> **kenfeyl said:**
> Is there anything I can do, once the connection is down, to diagnose the issue?
You could look at the output of **dmesg | tail** right after the connection goes down. That should tell you what happened.

---

### Post by absol_of_doom on 2007-09-15
Question: does this work on other distrobutions of linux, such as sabayon?

---

### Post by ace214 on 2007-09-15
Perhaps, since the bandwidth is used up, the first post should be updated to include the original source. People who can't download the script can go to [http://ubuntuforums.org/showthread.php?p=1071920](http://ubuntuforums.org/showthread.php?p=1071920) and follow the instructions there. You can google the bcm43xx-fwcutter package, download it, put it on a flash drive and install it on the target system. Download the driver file from [http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip) as linked to in the afore mentioned post.

---

### Post by basketcase on 2007-09-15
> **ace214 said:**
> Your bandwidth has been exceeded. Can someone not upload the file to the forum? I really need this.

What this guy said...I've got some bandwidth laying around, I'd be happy to host.

---

### Post by VicAlpha on 2007-09-15
Wow, It works perfectly with a fresh feisty install(internet version) on an Acer Aspire 3003 WLmi of all things!!! After installing ndiswrapper and the driver, I had to reinstall the driver again to make it work. Good stuff.

---

### Post by bmartin on 2007-09-15
I'm able to access my file on Google Pages by clicking on them. Is there a problem downloading the installers?

If worse comes to worse, I could just remove the offline installer.

---

### Post by bmartin on 2007-09-15
> **absol_of_doom said:**
> Question: does this work on other distrobutions of linux, such as sabayon?

The Python interface will. However, the BASH scripts will not. You'd have to modify **all** of the BASH scripts to make them work on another distribution. The file locations might have changed, too; if certain programs aren't in your $PATH, then those would fail, too.

---

### Post by basketcase on 2007-09-15
Working now...

Thanks!

---

### Post by gzenitsky on 2007-09-16
My hats off to all who worked on this install script! Excellent installer and the only method that worked for me in getting my Compaq Presario F500 up and running on Feisty (trust me, I tried several methods!). Bye bye Vista Home Premium...I loved thee not!!

---

### Post by kenfeyl on 2007-09-16
> **bmartin said:**
> You could look at the output of **dmesg | tail** right after the connection goes down. That should tell you what happened.

Okay, here's a dump of dmesg | tail -100 after the latest drop:

```
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Aug 30 23:16:15 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] Command line: root=UUID=3ad183b2-5e4d-4c29-97c3-c90f943772a6 ro quiet splash noapic
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  BIOS-e820: 000000007bf00000 - 000000007bf16000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf16000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 507648) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f88e0
[    0.000000] ACPI: RSDT (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000000) @ 0x000000007bf0cb68
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x000000007bf15b58
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000007bf15bcc
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x000000007bf15d90
[    0.000000] ACPI: HPET (v001 PTLTD  HPETTBL  0x06040000  LTP 0x00000001) @ 0x000000007bf15dcc
[    0.000000] ACPI: MADT (v001 HP     	 APIC   0x06040000  LTP 0x00000000) @ 0x000000007bf15e04
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000007bf15e62
[    0.000000] ACPI: SLIC (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000001) @ 0x000000007bf15e8a
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000007bf00000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 507648) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000007bf00000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   507648
[    0.000000] On node 0 totalpages: 507549
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1088 pages reserved
[    0.000000]   DMA zone: 2853 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6884 pages used for memmap
[    0.000000]   DMA32 zone: 496668 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: nVIDIA   MPTABLE: Product ID: C51-MCP51    MPTABLE: APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 2
[    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
[    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000d2000
[    0.000000] Nosave address range: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 499521
[    0.000000] Kernel command line: root=UUID=3ad183b2-5e4d-4c29-97c3-c90f943772a6 ro quiet splash noapic
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   12.363666] Console: colour VGA+ 80x25
[   12.365000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   12.367352] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.368170] Checking aperture...
[   12.368174] CPU 0: aperture @ 0 size 32 MB
[   12.375228] No AGP bridge found
[   12.399274] Memory: 1988004k/2030592k available (2218k kernel code, 42192k reserved, 1162k data, 304k init)
[   12.477152] Calibrating delay using timer specific routine.. 3621.11 BogoMIPS (lpj=7242236)
[   12.477210] Security Framework v1.0.0 initialized
[   12.477215] SELinux:  Disabled at boot.
[   12.477240] Mount-cache hash table entries: 256
[   12.477381] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.477384] CPU: L2 Cache: 512K (64 bytes/line)
[   12.477387] CPU 0/0 -> Node 0
[   12.477389] CPU: Physical Processor ID: 0
[   12.477391] CPU: Processor Core ID: 0
[   12.477412] SMP alternatives: switching to UP code
[   12.477656] Early unpacking initramfs... done
[   12.802598] ACPI: Core revision 20060707
[   12.805511] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   12.808318] ACPI: setting ELCR to 0200 (from 0ca0)
[   12.812141] Using local APIC timer interrupts.
[   12.867418] result 12557148
[   12.867420] Detected 12.557 MHz APIC timer.
[   12.869175] SMP alternatives: switching to SMP code
[   12.869281] Booting processor 1/2 APIC 0x1
[   12.879789] Initializing CPU#1
[   12.880935] spurious 8259A interrupt: IRQ7.
[   12.957140] Calibrating delay using timer specific routine.. 3624.27 BogoMIPS (lpj=7248555)
[   12.957147] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.957150] CPU: L2 Cache: 512K (64 bytes/line)
[   12.957152] CPU 1/1 -> Node 0
[   12.957154] CPU: Physical Processor ID: 0
[   12.957156] CPU: Processor Core ID: 1
[   12.957243] AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   12.961139] CPU 1: Syncing TSC to CPU 0.
[   12.961011] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 525 cycles)
[   12.961022] Brought up 2 CPUs
[   12.961035] time.c: Using 25.000000 MHz WALL HPET GTOD HPET timer.
[   12.961038] time.c: Detected 1808.228 MHz processor.
[   13.912262] migration_cost=312
[   13.912650] Time: 17:51:57  Date: 08/15/107
[   13.912692] NET: Registered protocol family 16
[   13.912778] ACPI: bus type pci registered
[   13.912784] PCI: Using configuration type 1
[   13.918844] ACPI: Interpreter enabled
[   13.918847] ACPI: Using PIC for interrupt routing
[   13.919928] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.919933] PCI: Probing PCI hardware (bus 00)
[   13.920160] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   13.920526] Boot video device is 0000:00:05.0
[   13.921273] PCI: Transparent bridge - 0000:00:10.0
[   13.921305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.969138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   13.970564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   13.970776] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   13.971226] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.971617] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   13.972006] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.972430] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.972818] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.973204] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.973591] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[   13.973981] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.974366] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   13.974752] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   13.975138] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   13.975526] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   13.975911] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   13.976297] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.976707] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.977095] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.977482] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   13.977880] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   13.978266] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   13.979464] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.979478] pnp: PnP ACPI init
[   13.982839] pnp: PnP ACPI: found 13 devices
[   13.982899] PCI: Using ACPI for IRQ routing
[   13.982903] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.982995] NET: Registered protocol family 8
[   13.982997] NET: Registered protocol family 20
[   13.983014] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   13.983018] hpet0: 3 32-bit timers, 25000000 Hz
[   13.984686] pnp: 00:04: ioport range 0x1000-0x107f could not be reserved
[   13.984689] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[   13.984693] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[   13.984696] pnp: 00:04: ioport range 0x1480-0x14ff could not be reserved
[   13.984699] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[   13.984702] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[   13.984705] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[   13.985014] PCI: Bridge: 0000:00:02.0
[   13.985017]   IO window: 4000-4fff
[   13.985021]   MEM window: b4000000-b5ffffff
[   13.985024]   PREFETCH window: d0000000-d01fffff
[   13.985027] PCI: Bridge: 0000:00:03.0
[   13.985029]   IO window: disabled.
[   13.985032]   MEM window: b6000000-b7ffffff
[   13.985034]   PREFETCH window: disabled.
[   13.985037] PCI: Bridge: 0000:00:10.0
[   13.985038]   IO window: disabled.
[   13.985041]   MEM window: disabled.
[   13.985044]   PREFETCH window: disabled.
[   13.985056] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   13.985063] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   13.985070] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   13.985155] NET: Registered protocol family 2
[   14.024421] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.024793] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   14.028036] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.028847] TCP: Hash tables configured (established 262144 bind 65536)
[   14.028850] TCP reno registered
[   14.040472] checking if image is initramfs... it is
[   14.686789] Freeing initrd memory: 6825k freed
[   14.691513] Simple Boot Flag at 0x36 set to 0x1
[   14.692140] audit: initializing netlink socket (disabled)
[   14.692155] audit(1189878717.284:1): initialized
[   14.692348] VFS: Disk quotas dquot_6.5.1
[   14.692369] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   14.692419] io scheduler noop registered
[   14.692421] io scheduler anticipatory registered
[   14.692423] io scheduler deadline registered
[   14.692438] io scheduler cfq registered (default)
[   14.908080] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.908101] assign_interrupt_mode Found MSI capability
[   14.908105] Allocate Port Service[0000:00:02.0:pcie00]
[   14.908171] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   14.908191] assign_interrupt_mode Found MSI capability
[   14.908194] Allocate Port Service[0000:00:03.0:pcie00]
[   14.934148] Real Time Clock Driver v1.12ac
[   14.934320] hpet_resources: 0xfed00000 is busy
[   14.934338] Linux agpgart interface v0.102 (c) Dave Jones
[   14.934341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.934955] mice: PS/2 mouse device common for all mice
[   14.935563] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.935718] input: Macintosh mouse button emulation as /class/input/input0
[   14.935755] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.935758] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.936313] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.953824] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.953830] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.953925] TCP cubic registered
[   14.954601] NET: Registered protocol family 1
[   14.954681] ACPI: (supports S0 S3 S4 S5)
[   14.954727]   Magic number: 7:288:896
[   14.954805]   hash matches device ptyy6
[   14.954851]   hash matches device 0000:00:10.1
[   14.954858] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   14.954944] Freeing unused kernel memory: 304k freed
[   14.968257] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.150151] Capability LSM initialized
[   16.191873] ACPI: Thermal Zone [THRM] (56 C)
[   16.635027] usbcore: registered new interface driver usbfs
[   16.635051] usbcore: registered new interface driver hub
[   16.650529] usbcore: registered new device driver usb
[   16.668540] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   16.668545] PCI: setting IRQ 7 as level-triggered
[   16.668550] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   16.668566] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   16.668569] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   16.668688] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   16.668719] ehci_hcd 0000:00:0b.1: debug port 1
[   16.668724] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   16.668733] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[   16.668741] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.668845] usb usb1: configuration #1 chosen from 1 choice
[   16.668872] hub 1-0:1.0: USB hub found
[   16.668880] hub 1-0:1.0: 8 ports detected
[   16.690944] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.709919] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   16.725836] SCSI subsystem initialized
[   16.764075] libata version 2.20 loaded.
[   16.776312] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   16.776317] PCI: setting IRQ 11 as level-triggered
[   16.776322] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   16.776340] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   16.776344] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   16.776601] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   16.776622] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[   16.833488] usb usb2: configuration #1 chosen from 1 choice
[   16.833698] hub 2-0:1.0: USB hub found
[   16.833712] hub 2-0:1.0: 8 ports detected
[   16.935635] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   16.935656] NFORCE-MCP51: chipset revision 241
[   16.935658] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   16.935662] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   16.935667] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   16.935676]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[   16.935687] Probing IDE interface ide0...
[   17.262651] usb 2-6: new low speed USB device using ohci_hcd and address 2
[   17.484655] usb 2-6: configuration #1 chosen from 1 choice
[   17.497026] usbcore: registered new interface driver hiddev
[   17.511676] input: Microsoft Microsoft Wireless Optical Mouse® 1.0A as /class/input/input2
[   17.511697] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.0A] on usb-0000:00:0b.0-6
[   17.511708] usbcore: registered new interface driver usbhid
[   17.511711] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.670530] hda: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[   18.006907] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   18.009624] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   18.009627] PCI: setting IRQ 10 as level-triggered
[   18.009631] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   18.009638] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   18.009646] forcedeth: using HIGHDMA
[   18.526426] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   18.526569] sata_nv 0000:00:0e.0: version 3.3
[   18.526585] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   18.527788] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   18.527793] PCI: setting IRQ 5 as level-triggered
[   18.527798] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   18.527827] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.527898] ata1: SATA max UDMA/133 cmd 0x00000000000130c0 ctl 0x00000000000130b6 bmdma 0x0000000000013090 irq 5
[   18.527928] ata2: SATA max UDMA/133 cmd 0x00000000000130b8 ctl 0x00000000000130b2 bmdma 0x0000000000013098 irq 5
[   18.527940] scsi0 : sata_nv
[   18.993749] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.001911] ata1.00: ATA-7: ST980811AS, 3.BHD, max UDMA/100
[   19.001915] ata1.00: 156301488 sectors, multi 16: LBA48 
[   19.009914] ata1.00: configured for UDMA/100
[   19.009920] scsi1 : sata_nv
[   19.321555] ata2: SATA link down (SStatus 0 SControl 300)
[   19.332241] ATA: abnormal status 0x7F on port 0x00000000000130bf
[   19.332363] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
[   19.347643] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[   19.347652] Uniform CD-ROM driver Revision: 3.20
[   19.348649] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   19.348664] sda: Write Protect is off
[   19.348666] sda: Mode Sense: 00 3a 00 00
[   19.348681] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.348730] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   19.348739] sda: Write Protect is off
[   19.348741] sda: Mode Sense: 00 3a 00 00
[   19.348754] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.348759]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   19.394068] sd 0:0:0:0: Attached scsi disk sda
[   19.398071] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.608392] Attempting manual resume
[   19.608396] swsusp: Resume From Partition 8:5
[   19.608398] PM: Checking swsusp image.
[   19.608585] PM: Resume from disk failed.
[   19.620114] EXT3-fs: INFO: recovery required on readonly filesystem.
[   19.620118] EXT3-fs: write access will be enabled during recovery.
[   26.082454] kjournald starting.  Commit interval 5 seconds
[   26.082475] EXT3-fs: sda3: orphan cleanup on readonly fs
[   26.082485] ext3_orphan_cleanup: deleting unreferenced inode 2359312
[   26.082535] ext3_orphan_cleanup: deleting unreferenced inode 2359311
[   26.082547] ext3_orphan_cleanup: deleting unreferenced inode 2359310
[   26.082558] ext3_orphan_cleanup: deleting unreferenced inode 2359309
[   26.082570] ext3_orphan_cleanup: deleting unreferenced inode 2359308
[   26.082580] EXT3-fs: sda3: 5 orphan inodes deleted
[   26.082582] EXT3-fs: recovery complete.
[   26.119582] EXT3-fs: mounted filesystem with ordered data mode.
[   37.707061] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.717424] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.910970] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   37.911006] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   37.929375] input: PC Speaker as /class/input/input3
[   38.318793] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   38.318798] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[   38.318818] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   38.599979] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   38.669589] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   38.915604] fuse init (API version 7.8)
[   38.998739] lp: driver loaded but no devices found
[   39.154750] ndiswrapper version 1.47 loaded (smp=yes)
[   39.271634] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   39.273507] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   39.274166] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 10
[   39.274170] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 10 (level, low) -> IRQ 10
[   39.274205] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   39.280601] ndiswrapper: using IRQ 10
[   39.643979] wlan0: ethernet device 00:1a:73:60:06:23 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[   39.644027] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   39.646440] usbcore: registered new interface driver ndiswrapper
[   39.679665] Adding 1421712k swap on /dev/disk/by-uuid/302baadb-aac8-4e1e-880b-ecf41a69f404.  Priority:-1 extents:1 across:1421712k
[   39.811818] EXT3 FS on sda3, internal journal
[   42.135380] ACPI: AC Adapter [ACAD] (on-line)
[   42.147450] input: Power Button (FF) as /class/input/input5
[   42.147723] ACPI: Power Button (FF) [PWRF]
[   42.148947] input: Power Button (CM) as /class/input/input6
[   42.149217] ACPI: Power Button (CM) [PWRB]
[   42.177197] input: Sleep Button (CM) as /class/input/input7
[   42.177482] ACPI: Sleep Button (CM) [SLPB]
[   42.189188] input: Lid Switch as /class/input/input8
[   42.189444] ACPI: Lid Switch [LID]
[   42.223828] No dock devices found.
[   42.233426] ibm_acpi: ec object not found
[   42.333890] Using specific hotkey driver
[   42.404616] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   42.404832] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.426448] ACPI: Battery Slot [BAT0] (battery present)
[   42.459562] pcc_acpi: loading...
[   42.475280] wmi_add device=ffff810078614000
[   42.475284] calling WQBA
[   42.723412] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (version 2.00.00)
[   42.724336] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   42.724341] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   42.724344] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   46.765502] eth0: no link during initialization.
[   49.191781] ppdev: user-space parallel port driver
[   54.609599] Bluetooth: Core ver 2.11
[   54.609660] NET: Registered protocol family 31
[   54.609663] Bluetooth: HCI device and connection manager initialized
[   54.609667] Bluetooth: HCI socket layer initialized
[   54.621765] Bluetooth: L2CAP ver 2.8
[   54.621769] Bluetooth: L2CAP socket layer initialized
[   54.639658] Bluetooth: RFCOMM socket layer initialized
[   54.639673] Bluetooth: RFCOMM TTY layer initialized
[   54.639675] Bluetooth: RFCOMM ver 1.8
[   60.558339] NET: Registered protocol family 10
[   60.558454] lo: Disabled Privacy Extensions
[   60.558517] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.558520] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.629505] NET: Registered protocol family 17
[   68.244796] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.618373] wlan0: no IPv6 routers present
[  204.981889] irq 7: nobody cared (try booting with the "irqpoll" option)
[  204.981896] 
[  204.981897] Call Trace:
[  204.981900]  <IRQ>  [<ffffffff802bd235>] __report_bad_irq+0x35/0x90
[  204.981931]  [<ffffffff802bd4b0>] note_interrupt+0x220/0x280
[  204.981957]  [<ffffffff88044465>] :usbcore:usb_hcd_irq+0x25/0x60
[  204.981967]  [<ffffffff802be1f3>] handle_level_irq+0xe3/0x140
[  204.981972]  [<ffffffff8026223c>] call_softirq+0x1c/0x28
[  204.981980]  [<ffffffff80270189>] do_IRQ+0x89/0x100
[  204.981984]  [<ffffffff8026e860>] default_idle+0x0/0x50
[  204.981990]  [<ffffffff80261631>] ret_from_intr+0x0/0xa
[  204.981993]  <EOI>  [<ffffffff80231700>] unix_poll+0x0/0xa0
[  204.982007]  [<ffffffff8026e889>] default_idle+0x29/0x50
[  204.982014]  [<ffffffff8024b1ab>] cpu_idle+0x9b/0xd0
[  204.982021]  [<ffffffff8027a435>] start_secondary+0x4d5/0x4f0
[  204.982044] 
[  204.982046] handlers:
[  204.982048] [<ffffffff88044440>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  204.982063] Disabling IRQ #7
[  582.979305] spurious 8259A interrupt: IRQ15.

```

I had to restart to get it working properly again. Any ideas? Any help would be appreciated. Thanks.

---

### Post by sqlpython on 2007-09-16
bmartin says:
> If you select the ndiswrapper/bcmwl5 install, then the bcm43xx kernel module will be unloaded and blacklisted; if you select the bcm43xx kernel module, the firmware will be installed and the ndiswrapper module unloaded and removed from /etc/modules (so it doesn't boot up).

Let me know if it works. It might not work at all. If you can figure out how to get it to work, let me know.

Sorry I didn't see your reply.
My configuration includes 4 identical laptops. Frankly, I am so wore out from configing these  4 laptops with various Linux OSs before landing on Kubuntu and even then trying 32bit and 64bit on each that I don't have the enthusiasm to configure anything else this month LOL
If it ain't broke, Don't fix it.
 Anyway I will keep it in mind for future needs. Thanks for your work/contribution.

---

### Post by basketcase on 2007-09-16
THANK YOU THANK YOU THANK YOU THANK YOU!!! 

Absolutely perfect!  Couldn't have asked for more!  Well maybe to have only found this sooner.

---

### Post by afuchi on 2007-09-16
I've tried that and i think all goes pretty well..only one problem..my wireless led wont light :/ and i cant use wireless.
What should i do?

---

### Post by brennydoogles on 2007-09-16
> **afuchi said:**
> I've tried that and i think all goes pretty well..only one problem..my wireless led wont light :/ and i cant use wireless.
What should i do?

Technically That's two problems :P . Did you use firmware or NDISwrapper??

---

### Post by eipmoc on 2007-09-17
Yessssss it works, this is easy

is there a same topic but then for the sound problem i have?
lenovo 3000 c200 hint

;-)

thank you

---

### Post by ruggrat on 2007-09-17
Holy cow, it worked!!
Thank you so much, I feel like I'd tried everything!

---

### Post by afuchi on 2007-09-17
> **brennydoogles said:**
> Technically That's two problems :P . Did you use firmware or NDISwrapper??


NDISwrapper.

---

### Post by brennydoogles on 2007-09-17
> **afuchi said:**
> NDISwrapper.

In windows did your card require that you use a keyboard shortcut to activate the card, or was there an external switch??

---

### Post by afuchi on 2007-09-17
> **brennydoogles said:**
> In windows did your card require that you use a keyboard shortcut to activate the card, or was there an external switch??

There was a keyboard shortcut (what, i think, i never used), but also extra button what works with Fujitsu Siemens Launchmanager application. But usually i had wireless turned on by enabling it in BIOS.

---

### Post by brennydoogles on 2007-09-17
> **afuchi said:**
> There was a keyboard shortcut (what, i think, i never used), but also extra button what works with Fujitsu Siemens Launchmanager application. But usually i had wireless turned on by enabling it in BIOS.

Ok, make sure it is still enabled by default, because that was the point I was getting at.

---

### Post by afuchi on 2007-09-17
> **brennydoogles said:**
> Ok, make sure it is still enabled by default, because that was the point I was getting at.

It is enabled, first thing i checked.

---

### Post by Ayce on 2007-09-18
Simply amazing. Thank you very much. I've put so many hours into getting this dumb wifi card working and then I came across this post. I only wish I found it days ago.

---

### Post by AliL on 2007-09-18
Hiya again, I've posted in this topic before about my card behaving strangely and it's doing it again. I'm using a Belkin 54g F5D7010 v3 with the broadcom 4306 chipset, and a while ago before this tool reached v 0.3 I installed the BCM43xx firmware and the card worked fine. However since a reinstall I've opened the tool and it suggests that I use ndiswrapper instead. So should I go with what it says or use the old method?

---

### Post by DarkN00b on 2007-09-18
> **AliL said:**
> Hiya again, I've posted in this topic before about my card behaving strangely and it's doing it again. I'm using a Belkin 54g F5D7010 v3 with the broadcom 4306 chipset, and a while ago before this tool reached v 0.3 I installed the BCM43xx firmware and the card worked fine. However since a reinstall I've opened the tool and it suggests that I use ndiswrapper instead. So should I go with what it says or use the old method?

I would use ndiswrapper because it is just more stable. You also get a little more transmit range. Hope that helps.

---

### Post by AliL on 2007-09-18
OK then. Thanks for the fast reply as well.

It's such a shame that Broadcom is such a ba****d of a company to cause people to have to reverse engineer their firmware and have it less stable than the windows version...sad sad world...

I don't see why they don't just release a dev kit. They'd get more custom if their cards were compatible with more OSes.

---

### Post by RamsesII on 2007-09-18
Hi all,

I used the tutorial and it worked well. Thank you Dark00Nb and all the guys who made this happened.
I'd just like to bring something to your attention. 
During the installation bcm43xx-0.3.2.tar.gz writes in /etc/networks/interface the wireless WEP-key in **clear** in the file /etc/networks/interface. Moreover the file  is readable by anybody (r right for u,g and o). It maybe more an issue related to Ubuntu than to the firmware but I think it's a security breach I needed to draw to your attention. Is there anybody working on it already ?

Thanks.

---

### Post by RamsesII on 2007-09-18
I completely agree with you AliL. This broadcom card almost made me regret to have bought my laptop at dell's.

---

### Post by bigern75 on 2007-09-18
I got mine, bcm4318, on my dell inspiron 2200, to work with this wiki how to: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It works in both feisty and gutsy.

I'm afraid to try this. So since the above wiki works for me, I'll hold off on this unless someone else thinks differently. ;)

---

### Post by bmartin on 2007-09-18
> **RamsesII said:**
> During the installation bcm43xx-0.3.2.tar.gz writes in /etc/networks/interface the wireless WEP-key in **clear** in the file /etc/networks/interface. Moreover the file  is readable by anybody (r right for u,g and o).
I wrote the installer, and I can confidently say that no, it does not write anything in that file. That installer has nothing to do with your WEP key. However, the program that you entered your WEP key into might have written something into that file. WICD doesn't write anything there either.

---

### Post by bmartin on 2007-09-18
> **bigern75 said:**
> I got mine, bcm4318, on my dell inspiron 2200, to work with this wiki how to: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It works in both feisty and gutsy.

I'm afraid to try this. So since the above wiki works for me, I'll hold off on this unless someone else thinks differently. ;)
The walkthrough you posted does the same things as the installer, except that it does it automatically as opposed to you doing it yourself. I wouldn't run the installer. ndiswrapper tends to work better than the firmware.

---

### Post by bkrispy on 2007-09-18
This did the trick for me!!!!  Just wanted to say thanks!

---

### Post by cybercreeper on 2007-09-18
First let me apologize for my ignorance. Total NOOB here. 2nd Day with Ubuntu and Edubuntu. i have an E-Machine that was given to me for my kids. Dumb machine had WMe plagued with spyware and viruses. Any way i decided to do away with Wme and put Edubuntu and added a Linksys WMP54GS (broadcom chipset 4306) Wireless card. Ran the script as instructed. The card shows up in the network settings as (eth0 is active) i click on properties, setting are as follows

Enable this connection  has a check mark

Network Name (ESSID)   No network is present And I'm right next to my wireless router.

Key Type   Hexadecimal 

Wep Key is blank

Conneciton setting :

Configuration is set to DHCP

Did I miss a Step or something? I can't connect to anything. any suggestion would be greatly appreciated. ](*,)

---

### Post by sirbobbinhood on 2007-09-18
Hey this thing is awesome I tried atleast 10 other solutions and nothing worked until I tried this. Thanks

---

### Post by DarkN00b on 2007-09-18
> **cybercreeper said:**
> First let me apologize for my ignorance. Total NOOB here. 2nd Day with Ubuntu and Edubuntu. i have an E-Machine that was given to me for my kids. Dumb machine had WMe plagued with spyware and viruses. Any way i decided to do away with Wme and put Edubuntu and added a Linksys WMP54GS (broadcom chipset 4306) Wireless card. Ran the script as instructed. The card shows up in the network settings as (eth0 is active) i click on properties, setting are as follows

Enable this connection  has a check mark

Network Name (ESSID)   No network is present And I'm right next to my wireless router.

Key Type   Hexadecimal 

Wep Key is blank

Conneciton setting :

Configuration is set to DHCP

Did I miss a Step or something? I can't connect to anything. any suggestion would be greatly appreciated. ](*,)

Try installing WICD. This is the preferred connection manager and it seems to work well for almost everyone.

---

### Post by cybercreeper on 2007-09-18
> **DarkN00b said:**
> Try installing WICD. This is the preferred connection manager and it seems to work well for almost everyone.

I type in the terminal WICD and the WICD Manager pops up. but all it shows is the Wired Network not the wifi. it says, "No wireless networks found". ](*,)



I can not get to the WICD without going threw the Terminal. is that normal? If i close the Terminal the WICD Manager closes too. I installed it from the bcm43xx-0.3.2

---

### Post by RamsesII on 2007-09-19
thx for the answer.

---

### Post by Jadephyre on 2007-09-19
okay, first off: I'm new here, i'm a Linux Newbie and don't know scat about the Linux-OS yet ;)

i have tried the Installer on Ubuntu 7.04 Feisty Fawn (32Bit Version) and Linux Mint 3.0 "Cassandra" (also 32Bit Version) and it works, just as long as i'm permitting the WLAN to broadcast it's ID.
I'm also using WPA & WPA 2 Encryption Methods, and it connected without a hitch.

My Question is if there is a Method of having Ubuntu or Mint, as they are basically the same OSes, connect to a hidden Network too.

My WLAN Chipset is an unsupported BCM43xx Broadcom Chipset, nonetheless i tried the Method of introducing the proper Kernel-Module as NDISWRAPPER gave me nothing but trouble.
I have only been online through WLAN for half an hour with my Laptop before going back to my Desktop PC to register here, but i had no connection blackouts whatsoever.

Thanks for compiling this and making it available to us :)

---

### Post by brennydoogles on 2007-09-19
> **Jadephyre said:**
> okay, first off: I'm new here, i'm a Linux Newbie and don't know scat about the Linux-OS yet ;)

i have tried the Installer on Ubuntu 7.04 Feisty Fawn (32Bit Version) and Linux Mint 3.0 "Cassandra" (also 32Bit Version) and it works, just as long as i'm permitting the WLAN to broadcast it's ID.
I'm also using WPA & WPA 2 Encryption Methods, and it connected without a hitch.

My Question is if there is a Method of having Ubuntu or Mint, as they are basically the same OSes, connect to a hidden Network too.

My WLAN Chipset is an unsupported BCM43xx Broadcom Chipset, nonetheless i tried the Method of introducing the proper Kernel-Module as NDISWRAPPER gave me nothing but trouble.
I have only been online through WLAN for half an hour with my Laptop before going back to my Desktop PC to register here, but i had no connection blackouts whatsoever.

Thanks for compiling this and making it available to us :)

Are you usin Wifi-radar, Wicd, or some other network manager?? Each should have a way to add hidden networks. The way  I did it was to Broadcast my ssid while I configured the network (in wifi-radar), and then turn broadcast off, and my lappy still sees the network. Hope that helps!!

---

### Post by cybercreeper on 2007-09-19
can anyone help from my previous posts....:confused:

---

### Post by Phelan on 2007-09-19
Wow, this was easy, worked great and now finally have my wireless up and running after 3 days!  Thanks!

---

### Post by bmartin on 2007-09-19
> **cybercreeper said:**
> I can not get to the WICD without going threw the Terminal. is that normal? If i close the Terminal the WICD Manager closes too. I installed it from the bcm43xx-0.3.2
There's a tray program for WICD. It should be located at /opt/wicd/tray.py. You can set it to start up with your computer by going to System > Preferences > Sessions (unless you're using KDE or Xfce... then there's some other way, check Google).

---

### Post by ENDI1111 on 2007-09-19
I am needing help here.  I got Ubuntu installed on my HP dv6000 and I cannot get the internet to work.  I need some serious help with this.  I am a bit new to this OS practically...so I am learning as I go.

---

### Post by bmartin on 2007-09-19
> **ENDI1111 said:**
> I am needing help here.  I got Ubuntu installed on my HP dv6000 and I cannot get the internet to work.  I need some serious help with this.  I am a bit new to this OS practically...so I am learning as I go.
Did you run the installer? And if so, does **ndiswrapper -l** say that the driver is installed and the device is present? And if so, which program are you using to connect to your router?

---

### Post by ENDI1111 on 2007-09-19
> **bmartin said:**
> Did you run the installer? And if so, does **ndiswrapper -l** say that the driver is installed and the device is present? And if so, which program are you using to connect to your router?

  Well when installing the text based Ubuntu it recognizes the card...yet fails to setup a wireless network so I skip that step to continue with the OS installation.  As far as the driver...I am unsure.  And the program I do not know nither.  Right now I am in the middle of another re-install.  I wanted to do a dual boot with Vista...but I guess that won't be happening.  I didn't do the partitioning right...soooooo!!!  It is in the middle of install software right now.

---

### Post by TimmiT on 2007-09-19
Worked for both my laptop and my desktop computer :D

---

### Post by ENDI1111 on 2007-09-19
I am still trying to figure out my wireless connection.  Ubuntu is up and running, and I am trying to figure out what I need to do next.

---

### Post by bmartin on 2007-09-19
> **ENDI1111 said:**
> I am still trying to figure out my wireless connection.  Ubuntu is up and running, and I am trying to figure out what I need to do next.
Do you have a Broadcom chipset?

---

### Post by ENDI1111 on 2007-09-19
> **bmartin said:**
> Do you have a Broadcom chipset?

  Yes.  when i iwconfig:  Nickname "Broadcom 4311"
Access Point:  Invalid.  RTS thr:  off.  Fragment thr:  off
Link Quality=0/100   Signal level=-256dBm   Noise level=-256dBm
Rx  invalid nwid: 0   Rx invalid crypt: 0   Rx invalid frag: 0
Tx excessive reties: 0   Invalid misc: 0   Missed beacon: 0

---

### Post by ENDI1111 on 2007-09-20
When I $ lshw -C network
It says my network is disabled
physical id: 0
bus info: pci@03:00.0
logical name: eth1
version 02
serial........... 
width..........
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes  driver=bcm43xx
driverversion-2.6.20-15-generic latency-0  multicast=yes  wireless=IEEE802.11b/g
  resources: iomemory:b6000000-b6003fff  irq:19

---

### Post by bmartin on 2007-09-20
> **ENDI1111 said:**
> When I $ lshw -C network
It says my network is disabled
Is there a switch or a keyboard combination you can press to turn your wireless on? A common keyboard combination is Fn+F2. There's probably also a setting in your BIOS that activates it.

---

### Post by cybercreeper on 2007-09-20
I need a specialist here.....Got the bcm43xx-0.3.2-internet file, i then ran the Installer.py. It gave me the optioin "install ndiswrapper and broadcom windos driver" i clicked install. it went thought then i redid the installer.py and selected "installl WICD wireless connection manager". But i still can't connect to any thing.


my chipset it Broadcom 4306 (a linksys WMP54GS)

What am I missing? Help i don't know what else to do..NOOB here!:confused:

---

### Post by bmartin on 2007-09-20
You should be able to run WICD from a terminal by typing **wicd** or **wicd-tray**, or by going to Applications > Internet > Wicd.

---

### Post by Raaben on 2007-09-20
Nevermind, got it to install. Still no wireless though.

---

### Post by cybercreeper on 2007-09-20
okay, So reinstalled Edubuntu and redid the steps on the original post. i now see the card but the wireless card can't seem to pic up any networks. and i am next to the wireless router....:confused: Now what?

---

### Post by linuxuser187 on 2007-09-21
I'm not sue if this will help but if anyone had trouble installing their broadcom onto their hp latop this might help, i have a hp dv6424 and i have a broadcom 4310 and when i ran installer.py everything installed correctly but the status light for my wireless card remained yellow  even if i flicked the switch to on so nothing changed, i restarted my pc and tried my card again and still no good, ran installer again and still no good, rebooted again and went to try and install a 3rd time and i realised that the last 2 times i ran installer.py  i had the wireless switch in the off position, i turned it on then ran installer.py and when it was done the status light went to blue meaning it was now configured properly and is visible on my network manager, basically make sure that you have turned the switch to on and then run installer.py

---

### Post by cybercreeper on 2007-09-21
anyone?
):P

---

### Post by Noah0504 on 2007-09-21
This script worked perfectly for me once, however, now when I try it on the exact same computer, it freezes up my entire system when inserting the ndiswrapper module.  Can someone throw some help my way?  Has anyone else had this problem?  No matter how many times I try, it freezes at the same point.

---

### Post by bmartin on 2007-09-21
> **Noah0504 said:**
> This script worked perfectly for me once, however, now when I try it on the exact same computer, it freezes up my entire system when inserting the ndiswrapper module.  Can someone throw some help my way?  Has anyone else had this problem?  No matter how many times I try, it freezes at the same point.
Does it freeze up if you manually insert the ndiswrapper module?
```
sudo modprobe ndiswrapper
```

---

### Post by Noah0504 on 2007-09-21
> **bmartin said:**
> Does it freeze up if you manually insert the ndiswrapper module?
```
sudo modprobe ndiswrapper
```
Well, I think I may should have done more, but running what you told me produces this:
> FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory


---

### Post by bmartin on 2007-09-21
> **Noah0504 said:**
> Well, I think I may should have done more, but running what you told me produces this:
OK, try the following:
```
sudo depmod -ae
sudo modprobe ndiswrapper
```

---

### Post by Noah0504 on 2007-09-21
> **bmartin said:**
> OK, try the following:
```
sudo depmod -ae
sudo modprobe ndiswrapper
```
Well, my system seemed to like those two commands.

---

### Post by bmartin on 2007-09-21
> **Noah0504 said:**
> Well, my system seemed to like those two commands.
The depmod -ae command takes a while. It might be that the script hung, or it might be the case that depmod simply takes a while and you thought it was hung. If it hung, it probably got hung up on that command and not the modprobe command. I'm trying to figure out where the hanging point is.

depmod refreshes your kernel module dependency cache. In other words, many drivers on your computer have dependencies on other drivers. It stores information such as where a certain kernel module is located.

ndiswrapper.ko wasn't located where your computer was expecting it to be, so it must be the case that **depmod -ae** was never executed in the script. I know this because of the message you got the first time when you ran **modprobe ndiswrapper**.

Anyways, I have to go feed the ducks with my girlfriend. We found some stale oyster crackers lying around. Is your wireless working now?

---

### Post by Noah0504 on 2007-09-21
> **bmartin said:**
> The depmod -ae command takes a while. It might be that the script hung, or it might be the case that depmod simply takes a while and you thought it was hung. If it hung, it probably got hung up on that command and not the modprobe command. I'm trying to figure out where the hanging point is.

depmod refreshes your kernel module dependency cache. In other words, many drivers on your computer have dependencies on other drivers. It stores information such as where a certain kernel module is located.

ndiswrapper.ko wasn't located where your computer was expecting it to be, so it must be the case that **depmod -ae** was never executed in the script. I know this because of the message you got the first time when you ran **modprobe ndiswrapper**.

Anyways, I have to go feed the ducks with my girlfriend. We found some stale oyster crackers lying around. Is your wireless working now?
No, but I will keep messing around with it.  Thanks for the information and help.

---

### Post by Nameroc on 2007-09-21
Hello,

I successfully used the script to install ndiswrapper and a driver for my wireless card on my Dell Inspiron 510m. The wireless interface seems to be working all fine, however I can't get it to see my network. Another laptop with windows xp on it does quite fine in detecting the wireless. What could be the problem?

Edit: I am using Kubuntu, by the way, with all updates done. I tried both the KNetwork Manager and Wicd.

---

### Post by bmartin on 2007-09-21
My guess is that your wireless radio on your hardware is disabled and that you can probably enable it with a physical switch on your keyboard, or by pressing a certain keyboard combination (such as Fn+F2), or that there's a setting in your BIOS that needs to be turned on.

---

### Post by Nameroc on 2007-09-22
Fn+F2 is the only switch I have, and it worked. So embarrassingly simple. I'm glad it got working eventually, though. Great script! Thanks!

---

### Post by bmartin on 2007-09-22
It's nothing to be embarrassed about. It's not something you have to worry about in Windows.

---

### Post by RetiredInMaine on 2007-09-22
Did not work for me. I did an online install since my laptop has both a wired and unwired connection. It started to work, ie, it installed a new copy of ndiswrapper but hung my system when it came to the insert ndiswrapper module step. I had to power down and reboot.Now when I go into network manager it no longer recognizes that I have wireless hardware. Seems like a step backwards. 

Full disclosure, I have been trying to get this working for two years. Have tried several versions of Fedora and SuSe, also half a dozen other distros. I have even tried a usb wireless that has Linux drivers, but for some reason I have never been able to get wireless working.  I have a HP Pavilion zv5434rs notebook. I am about ready to give up and buy a fully configured Dell but I would really like to get this working. Just stubborn.

Any ideas???:confused:

---

### Post by bmartin on 2007-09-22
> **RetiredInMaine said:**
> <snip>it installed a new copy of ndiswrapper but hung my system when it came to the insert ndiswrapper module step. I had to power down and reboot.Now when I go into network manager it no longer recognizes that I have wireless hardware. Seems like a step backwards.
My best guess is that you were using ndiswrapper before and the ndiswrapper kernel module is no longer present... or you were using bcm43xx and it has been blacklisted. Either way...

For some strange reason, when the kernel module is inserted, everyone seems to think their computer is hung up. The **depmod -ae** command is a long-running command (can take a minute or so). It's absolutely necessary to run that command.

Try running the following two commands:
```
sudo depmod -ae
modprobe ndiswrapper
```

---

### Post by RetiredInMaine on 2007-09-22
Tried running the commands as shown. depmod just returned without any indication. Modprobe returned a fatal error saying I was trying an illegal operation. I switched to being su and reran the two commands. Both just returned.

About ndiswrapper: when I ran the script it deleted a copy and then recompiled a new copy. I don't know how to check if bcm43xx is blacklisted or how to unblacklist it.:confused:

---

### Post by bmartin on 2007-09-22
> **RetiredInMaine said:**
> Tried running the commands as shown. depmod just returned without any indication. Modprobe returned a fatal error saying I was trying an illegal operation. I switched to being su and reran the two commands. Both just returned.
Neither of them are supposed to have any output. I forgot to put a sudo before modprobe. Now that you've inserted the ndiswrapper kernel module, is your device detected again?

> **RetiredInMaine said:**
> About ndiswrapper: when I ran the script it deleted a copy and then recompiled a new copy. I don't know how to check if bcm43xx is blacklisted or how to unblacklist it.:confused:
If you're using ndiswrapper, you want bcm43xx blacklisted. If it's blacklisted, you should have this line in your /etc/modprobe.d/blacklist file: blacklist bcm43xx

---

### Post by Eric the Grey on 2007-09-22
> **bmartin said:**
> The depmod -ae command takes a while. It might be that the script hung, or it might be the case that depmod simply takes a while and you thought it was hung. If it hung, it probably got hung up on that command and not the modprobe command. I'm trying to figure out where the hanging point is.

depmod refreshes your kernel module dependency cache. In other words, many drivers on your computer have dependencies on other drivers. It stores information such as where a certain kernel module is located.

ndiswrapper.ko wasn't located where your computer was expecting it to be, so it must be the case that **depmod -ae** was never executed in the script. I know this because of the message you got the first time when you ran **modprobe ndiswrapper**.

Anyways, I have to go feed the ducks with my girlfriend. We found some stale oyster crackers lying around. Is your wireless working now?

I was having the exact same problem, and even after giving the script 20 min to complete the insert command(s), it was still hung.  No mouse movement, no ctrl-alt-backspace, nothing worked to unfreeze the system.

Anyway, both these commands seems to have been taken, and I've checked to make certain bcm43xx is in my blacklist (for ndiswrapper) and rebooted after this, but still no go with wireless.  

iwconfig gives me:

```

lo        no wireless extensions
eth0      no wireless extensions

```

Any other suggestions?  

In the past, I've been able to get ndiswrapper to work on this laptop using automatix, and it has always worked perfectly, until this installation.  The last time I used it was was under 6.10 though.  It seems to be broken now.


:cool: Eric the Grey

---

### Post by DOH on 2007-09-22
Thank you so much for the how to help...I'm very noob with ubuntu and the way linux works, this guide was simple and easy to use.  Again thank you.

---

### Post by cybercreeper on 2007-09-22
I typed: iwconfig 

and this is what came up.

eth0
IEE 802.11g ESSID:off/any
Mode: Managed   Frequency: 2.462 GHz Access Point: Not Associated
RTS thr:2347 B Grgment thr:2346 B
Power Management:off
Link Quality:0 Signal lever:0  Noise Lever:0
Rx invalid nwid:0   Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0  Missed beacon:0


Does that mean my wifi card is off? if so how do i turn in on. Plus i just noticed the light is not on...(This is on a desktop PCI Card WMp54gs Broadcom 4306)

---

### Post by runemaste644 on 2007-09-23
How did you write this magic thing????? Im thinking you could make a big script that you select your laptop model and it will get drivers and software for ALL your hardware. I couldn't make a script that installs broadcom cards like that before the day the earth crashes into the sun! You guys are AWESOME! Im sendinng this wirelessly!

---

### Post by DarkN00b on 2007-09-23
> **runemaste644 said:**
> How did you write this magic thing????? Im thinking you could make a big script that you select your laptop model and it will get drivers and software for ALL your hardware. I couldn't make a script that installs broadcom cards like that before the day the earth crashes into the sun! You guys are AWESOME! Im sendinng this wirelessly!

Heh, you think this is something...

bmartin has a much bigger and better project in the works. :)

---

### Post by bmartin on 2007-09-23
> **runemaste644 said:**
> How did you write this magic thing????? Im thinking you could make a big script that you select your laptop model and it will get drivers and software for ALL your hardware.
[It's in the works]("http://www.wifixhq.org/") :-P

I'm currently setting up a MySQL on the SF servers for testing purposes, since my DB host has been AWOL for several days. Then I need to write a PHP file to perform the query; I'm going to have to learn how to connect from PHP to a MySQL database; it shouldn't be hard. Then I need to relearn how to parse HTTP query strings so that I can query using the built-in HTTP library in Python. Technically, it's a bit complicated, but it's necessary so that our MySQL database isn't "brute-forced".

All that, and I need to look up driver locations and try installing/compiling them; sometimes, the newest source code is in a CVS or SVN repository, or in a GIT tree, and compilation/installation is sometimes slightly different.

I'm planning on adding some new functionality before alpha testing, such as the ability to detect **why** your device won't connect (e.g., a disabled radio).

There's also the issue of ndiswrapper drivers, which are preferable for certain chipsets (such as Broadcom chipsets); can this program legally download and install them? I need to run this by the legal team @ Ubuntu. It seems very questionable with the Broadcom drivers; take a look at what's in the INF file.

I'll be adding to the table on that page. After I get a functional program running, I'm going to put it through proper alpha and beta testing. It's important to note, however, that upgrading the program will in no way affect the number of devices it supports; the supported devices depend on what's in the SQL database.

I'm pretty particular about the DB and the BASH installer script; those are parts of the program that I'd like to work on. I'm working with another guy on the project; we keep each other in check. His UI design skills and general knowledge of Python are superior to mine. I can't take all the credit.

There'll probably be a sticky thread on the forum once it's released. I have a nightly tarball set up, but it's mostly for developers. You might even see it in the Universe or Multiverse repository in the future, or even in both (for those who like to keep their OS truly "free").

---

### Post by cybercreeper on 2007-09-23
> **cybercreeper said:**
> I typed: iwconfig 

and this is what came up.

eth0
IEE 802.11g ESSID:off/any
Mode: Managed   Frequency: 2.462 GHz Access Point: Not Associated
RTS thr:2347 B Grgment thr:2346 B
Power Management:off
Link Quality:0 Signal lever:0  Noise Lever:0
Rx invalid nwid:0   Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0  Missed beacon:0


Does that mean my wifi card is off? if so how do i turn in on. Plus i just noticed the light is not on...(This is on a desktop PCI Card WMp54gs Broadcom 4306)


Muller?
Muller?
Anyone wanna give this NOOB a hand?:confused:

---

### Post by bmartin on 2007-09-23
> **cybercreeper said:**
> Muller?
Muller?
Anyone wanna give this NOOB a hand?:confused:
=D>

Muller? I looked it up on Wikipedia... didn't figure that one out.

If it's disabled, I'd check three things:
[LIST=1]
[*]Is there a keyboard combination to enable the radio? (Fn+F2 is typical).
[*]Is there a switch that activates your wireless radio? (This is also quite common; mine is a push button, my girlfriend's is a toggle switch).
[*]Is there a setting in your BIOS which controls whether the wireless radio is enabled by default? (Dell 1390's share this common, somewhat infuriating trait).
[/LIST]

---

### Post by cybercreeper on 2007-09-23
> **bmartin said:**
> =D>

Muller? I looked it up on Wikipedia... didn't figure that one out.

If it's disabled, I'd check three things:
[LIST=1]
[*]Is there a keyboard combination to enable the radio? (Fn+F2 is typical).
[*]Is there a switch that activates your wireless radio? (This is also quite common; mine is a push button, my girlfriend's is a toggle switch).
[*]Is there a setting in your BIOS which controls whether the wireless radio is enabled by default? (Dell 1390's share this common, somewhat infuriating trait).
[/LIST]

umm? this is a desktop,  the wifi is a PCI Card...no Fn Key here. but i will check the bios...thanks

Edit: checked the BIOS, nothing there about pci enable/disable. wondering if it's something else? 
it shows the wifi to be eth0 but there are no networks present

---

### Post by ham43 on 2007-09-23
I have an Acer 3680 and it worked like a champ!

I was getting frustrated as I had tried a few other things and they had not worked.

Now I just need to get my WPA working.

Thanks much!

---

### Post by yuv656 on 2007-09-24
I've used the program together with Wicd, but wicd would never show any wireless networks even though I am in range.

Today, when I plugged in my wired network cable, suddenly my wireless network showed up with full signal (like it's supposed to be).

But then, to my dismay, wicd and Ubuntu froze entirely and i had to reboot. After rebooting the wireless network didn't show up, as usual. Any ideas?

Thanks!

P.s. I've been struggling for days on end to get my wireless to work. I absolutely love ubuntu (haven't booted windows ever since and it's been months), yet wireless is the only thing i have yet to get to work.

Details: HP Pavilion DV5000
>           *-network
                description: Wireless interface
                product: Dell Wireless 1390 WLAN Mini-PCI Card
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@06:00.0
                logical name: eth1
                version: 01
                serial: 00:14:a5:be:12:36
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:30000000-30003fff irq:18


---

### Post by yuv656 on 2007-09-24
I forgot to mention that I tried both alternative drivers in your program.

---

### Post by bmartin on 2007-09-24
> **yuv656 said:**
> But then, to my dismay, wicd and Ubuntu froze entirely and i had to reboot. After rebooting the wireless network didn't show up, as usual. Any ideas?
For one thing, you appear to be using the bcm43xx (firmware) driver, which is probably why your computer locked up. The bcm43xx module/firmware combination is quite buggy, whereas ndiswrapper/bcmwl5 is quite stable. I recommend:
[LIST=1]
[*]Running the installer again and installing ndiswrapper.
[*]Checking to see whether your device is detected by running **sudo iwlist scanning**.
[*]If your device doesn't seem to be detected, try running **sudo depmod -ae** and **sudo modprobe ndiswrapper**.
[/LIST]
The non-detection of wireless networks might be due to your wireless radio. I believe the computers with the Dell 1390 wireless have a BIOS setting that should be set to **on** (it might be called WLAN or something like that). There also might be a switch or a keyboard combination (e.g., Fn+F2) that activates your wireless radio.

---

### Post by Paracropolis on 2007-09-24
Hello. I am wondering if this how-to would work on a new fresh install of Kubuntu 7.04 and is there any other things I must install first.

I am completely new to Linux and I am not sure what I am doing quite often when I use Kubuntu. Any help wil be much appreciated.

---

### Post by bmartin on 2007-09-24
> **Paracropolis said:**
> Hello. I am wondering if this how-to would work on a new fresh install of Kubuntu 7.04 and is there any other things I must install first.

I am completely new to Linux and I am not sure what I am doing quite often when I use Kubuntu. Any help wil be much appreciated.
You'll probably have to use the terminal to run this. If you update your packages after doing a fresh install, it should go off without a hitch. You might have to activate your wireless radio with a switch or a keyboard combination (such as Fn+F2); that should probably be added to the FAQ.

---

### Post by DFlame on 2007-09-25
Had to use the ndiswrapper, but it works a dream here. Many thanks for keeping this going!

Gareth

---

### Post by dresen on 2007-09-26
I tried this and now my Linux locks up on boot. I pressed ctrl-alt-f2 to see what's going on and it gives me this error

[37.404000] BUG: Soft lockup detected on CPU0

anyone have any idea what to do?

---

### Post by jkrolen5500 on 2007-09-26
This has been a problem for a couple months.  Ive tried searching this thread but there are too many pages.  Please assist.


root@jerlaptop:~# apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.6kB of archives.
After unpacking 119kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 123898 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_i386.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--10:02:13--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:02:13 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jerlaptop:~#

---

### Post by DarkN00b on 2007-09-26
[img]http://img164.exs.cx/img164/7827/offtopic8mg.gif[/img]

I want to urge everyone that hasn't voted in the poll at the top of this howto, to please do so. This is how we roughly gauge the effectiveness of the installers.

To quote post #1 in this thread:

[quote="DarkN00b"]The numbers appear to be skewed very badly and I think they do not reflect the actual usefulness of bmartins great scripts. As an example, from 16 Sept. 2007 to 26 Sept. 2007, about 390 people downloaded the installer, yet the poll indicates that only 463 people have voted in total since this project started on 10 April 2007. For those interested that's 546.3 MB, just over 1/10 my allowed bandwidth for 30 days.[/quote]

Now this could mean that it didn't work for many people and our numbers would look worse than they do, but what if the opposite is true? What if it worked for many more people?

So if you haven't yet please vote. How many people are being helped and how many aren't? Only you can let us know.

---

### Post by bmartin on 2007-09-26
> **dresen said:**
> I tried this and now my Linux locks up on boot. I pressed ctrl-alt-f2 to see what's going on and it gives me this error

[37.404000] BUG: Soft lockup detected on CPU0

anyone have any idea what to do?
Did you install ndiswrapper or the firmware? I'd file a bug report on launchpad regarding Ubuntu's kernel. Make sure to tell them which kernel you're using. You can find out using **uname -r**.

---

### Post by bmartin on 2007-09-26
> **jkrolen5500 said:**
> This has been a problem for a couple months.  Ive tried searching this thread but there are too many pages.  Please assist.
<snip>
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jerlaptop:~#
The program at the beginning of this thread doesn't use bcm43xx-fwcutter. We don't encourage you to use it. The installer includes the firmware so you won't need bcm43xx-fwcutter at all.

---

### Post by yuv656 on 2007-09-27
Thanks for your reply.

>    1. Running the installer again and installing ndiswrapper.
Ok, I did that and it completed successfully.

>    2. Checking to see whether your device is detected by running sudo iwlist scanning.

This is what was displayed after running **sudo iwlist scanning**:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


  >  3. If your device doesn't seem to be detected, try running sudo depmod -ae and sudo modprobe ndiswrapper.
I executed both of those commands.

  > The non-detection of wireless networks might be due to your wireless radio. I believe the computers with the Dell 1390 wireless have a BIOS setting that should be set to on (it might be called WLAN or something like that). There also might be a switch or a keyboard combination (e.g., Fn+F2) that activates your wireless radio.  
I checked the BIOS and there is a setting called "Embedded WLAN Device Radio" which was already set to "Enabled". There is a button for wireless on my laptop,
but pressing it (or pressing it together with Fn) has no effect.

 There is a lamp above the button which never lights up either. I guess that could indicate that the radio never goes on?

---

### Post by yuv656 on 2007-09-27
Searching for "dv5000 pavilion wireless" gives this result:

> I use dv5000 with a broadcom wireless, after a fresh install all i have to do in Ubuntu Edgy is:

```

sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

And voila! it starts to work!

I saw that this fwcutter was discouraged but maybe i should try it then?

---

### Post by bmartin on 2007-09-27
> **yuv656 said:**
> I saw that this fwcutter was discouraged but maybe i should try it then?
Go for it. To me, it sounds like your wireless radio is inactive for some reason.

---

### Post by brennydoogles on 2007-09-27
I am having a hard time getting WPA working at School. Are there any steps I need to take to get everything set up that may not be obvious?

---

### Post by DarkN00b on 2007-09-27
> **yuv656 said:**
> Searching for "dv5000 pavilion wireless" gives this result:



I saw that this fwcutter was discouraged but maybe i should try it then?

Fwcutter installs the exact same firmware as that included with bmartins script. That's because they come from the same place -- [here]("http://bcm43xx.berlios.de/").

---

### Post by mpatria on 2007-09-28
The isntalation your program stoped after I inserted my ubuntu CD .
Why?

---

### Post by bmartin on 2007-09-28
I have no idea. What stage was the installation at when it stopped?

---

### Post by shonen on 2007-09-28
I have a problem when i use the installer.

lspci returns this: 

```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 2)
```

Now i run the automated installer I get Ndiswrapper and I get the firmware...

Awesome.

NOW, here is where my problem starts.

I uninstall network manager

```
 sudo apt-get remove network-manager
```

I ended up just downloading WICD using apt get

```
sudo apt-get install wicd
```

Then I'll reboot.

I get stuck on the ubuntu loading screen.

Has anyone else ever had this problem? What would cause it and is there any trouble shooting i can do to help get this problem solved?

Thanks!

~shonen

---

### Post by A Loft on 2007-09-28
Worked perfectly.  Amazingly perfectly.  Thank you!

As to why the poll doesn't match your downloads: it takes waaaay too much time and effort to get past the verification string to register on this forum.  I almost gave up twice, but I really wanted to give you kudos so I stuck with it until what I saw matched what the server saw.

Thanks again!

---

### Post by chrimsonnight on 2007-09-28
Another happy customer it worked like a champ on the HP Pavillion dv9013cl:)

---

### Post by YoungQuiz on 2007-09-28
worked like a charm thanks a million!

---

### Post by bmartin on 2007-09-28
> **shonen said:**
> Has anyone else ever had this problem? What would cause it and is there any trouble shooting i can do to help get this problem solved?
Mine didn't "get stuck", but it used to take forever... I simply commented out everything in my /etc/network/interfaces *except* the following two lines:
```
auto lo
iface lo inet loopback
```
If that causes any problems, you can always uncomment the commented lines. To comment a line, put a # at the beginning of it.

---

### Post by woody22075 on 2007-09-29
I downloaded the offline installer (I dont have internet with my computer yet) and when I ran the installer, I received a message the program couldnt load the message file.  i then have to exit (
ctrl+c) out of the window.

How to I get around this?

---

### Post by bmartin on 2007-09-29
> **woody22075 said:**
> I downloaded the offline installer (I dont have internet with my computer yet) and when I ran the installer, I received a message the program couldnt load the message file.  i then have to exit (
ctrl+c) out of the window.

How to I get around this?
Extract the files from the archive before running the installer.

---

### Post by jkrolen5500 on 2007-09-29
> **bmartin said:**
> The program at the beginning of this thread doesn't use bcm43xx-fwcutter. We don't encourage you to use it. The installer includes the firmware so you won't need bcm43xx-fwcutter at all.


Thanks for clarifying that, but why do they leave broken stuff in the repository?  Just a side thought!

---

### Post by jonathanmotes on 2007-09-29
I tried this on my HP dv9428nr laptop running Gutsy. Right before the script ended it said something like "ubable to find module modprobe." It then said it was finished, but ndiswrapper didn't work when I rebooted. I had the same error when I tried installing ndiswrapper myself and using the driver from HP. Does anyone know how to fix this? I am tried everything...I used ndiswrapper with Feisty and it worked without any problems....

Thanks

EDIT: A post [here]("http://ubuntuforums.org/showthread.php?t=529336&highlight=modprobe&page=4") says that booting with "noapic noirqdebug" was "killing" ndiswrapper earlier in Gutsy development. I had to use this in order to get the Live Disc to work and it keeps changing back to this when I remove it from the boot options. Does anyone know if that is still a problem?

EDIT2: I finally got Ndiswrapper to work after installing version 1.48 by compiling the source code -- version 1.43 does not work with my card ( BCM9 4311 ) on Gutsy. I suppose that was why the script didn't work.

---

### Post by bmartin on 2007-09-29
> **jkrolen5500 said:**
> Thanks for clarifying that, but why do they leave broken stuff in the repository?  Just a side thought!
It's probably the case that the firmware is at a location where it can sometimes be retrieved... but not always... so they leave it up because it's not really broken. That's just a guess.

The Ubuntu packages are frozen right before release, so it might be against Debian or Ubuntu policy to suddenly remove a package from the repository. That's just another guess, though. You could always file a bug report at Launch Pad... they'd probably reply with a link to the answer.

---

### Post by soliac on 2007-09-30
Thankyou so much for making this script! I have finally gotten my Broadcom 4309 card working, after 1.5 years on Ubuntu without wireless. The driver install went smoothly, and NetworkManager has connected to my adhoc network for the first time ever.

One suggestion for this great program - a better GUI would make it easier to use for newcomers, maybe something like synaptic/gdebi where the terminal text is not displayed by default and a nice progress bar is displayed.

Thanks again, this script saved my computer from a wired life!

---

### Post by bmartin on 2007-09-30
> **soliac said:**
> One suggestion for this great program - a better GUI would make it easier to use for newcomers, maybe something like synaptic/gdebi where the terminal text is not displayed by default and a nice progress bar is displayed.
The terminal text is nice for debugging... but I know what you mean w/ the progress bar. I added one to my [other installer]("http://sourceforge.net/projects/wifix") using zenity.

---

### Post by emmir on 2007-10-01
I've tried this installer in the past with success. After a recent format I tried it again but when it comes to the point were it inserts the ndiswrapper module, the system freezes leaving me no choice but rebooting and of course my wireless card does not work. Any ideas?

---

### Post by bmartin on 2007-10-01
> **emmir said:**
> I've tried this installer in the past with success. After a recent format I tried it again but when it comes to the point were it inserts the ndiswrapper module, the system freezes leaving me no choice but rebooting and of course my wireless card does not work. Any ideas?
Run the following two commands:
```
sudo depmod -ae
sudo modprobe ndiswrapper
```
Don't run the script again. Just run those commands.

---

### Post by gogetmeaflapjack on 2007-10-01
ok i think ive got everything working, this is my first time with linux. I ran all the stuff, installed wifi radar and it works, i can see all the networks available, their signal strength and all that, but when i try to connect it says "could not get ip address". i think it must be some setting that im missing, or maybe i missed something when i ran the script. any thoughts or help would be appreciated.

---

### Post by emmir on 2007-10-01
> **bmartin said:**
> Run the following two commands:
```
sudo depmod -ae
sudo modprobe ndiswrapper
```
Don't run the script again. Just run those commands.

Same reaction..... is there any way to "undo" what the script has done so far and start over?

---

### Post by bmartin on 2007-10-02
> **emmir said:**
> Same reaction..... is there any way to "undo" what the script has done so far and start over?
Same reaction? Your system froze when you ran those two commands? I'm very surprised.

The script removed your old ndiswrapper kernel module, installed ndiswrapper, installed the bcmwl5 driver, and blacklisted the bcm43xx kernel module. You can remove the bcmwl5 driver using **sudo ndiswrapper -e bcmwl5** and you can remove the bcm43xx blacklisting using **sudo gedit /etc/modprobe.d/blacklist** and removing the **blacklist bcm43xx** line (replace gedit with the name of your preferred editor).

Removing ndiswrapper is harder. If you never want ndiswrapper to load again, you can blacklist the ndiswrapper kernel module... I don't recommend that. As for getting the old ndiswrapper kernel module back, you'd have to either get that from someone using the old kernel module or reinstall Ubuntu. I wouldn't be concerned with that, either.

---

### Post by bigbadnewill on 2007-10-02
Hi, I have followed the guide and my wireless still isn't working. I have the broadcom 4318, running on a hp nx6110 laptop.

After i have blacklisted the 43xx and installed ndiswrapper etc my wireless network connection is no longer available in the Network Settings. It used to offer a Wireless option for me to change the properties of, and now it only had a 'Wired Connection' and a "Modem Connection'

How can i get my wireless connection back? Also, where can i get the latest version of the Broadcom driver from? I'm new to all this Ubuntu stuff, but really want to get into it all, so any extra help would be great!! :)

---

### Post by emmir on 2007-10-02
> **bmartin said:**
> Same reaction? Your system froze when you ran those two commands? I'm very surprised.

The script removed your old ndiswrapper kernel module, installed ndiswrapper, installed the bcmwl5 driver, and blacklisted the bcm43xx kernel module. You can remove the bcmwl5 driver using **sudo ndiswrapper -e bcmwl5** and you can remove the bcm43xx blacklisting using **sudo gedit /etc/modprobe.d/blacklist** and removing the **blacklist bcm43xx** line (replace gedit with the name of your preferred editor).

Removing ndiswrapper is harder. If you never want ndiswrapper to load again, you can blacklist the ndiswrapper kernel module... I don't recommend that. As for getting the old ndiswrapper kernel module back, you'd have to either get that from someone using the old kernel module or reinstall Ubuntu. I wouldn't be concerned with that, either.

Actually the system froze in executing the second command which (correct me if I'm wrong here) it inserts the ndiswrapper module. The thing is that I want to re-run the script again. I don't know how can this happen, I mean one time the script works and I can use my wifi and the other it doesn't....:(:(:( Should I remove bcmwl5 driver and the bcm43xx blacklisting and then give the script another go?

---

### Post by bmartin on 2007-10-02
You know what? I've had a really frustrating day. I hope you guys get your questions answered. Earlier today, I installed VMware and it bricked my OS. Since then, I can't use Firefox... so now I'm in Opera, and my girlfriend would like to go shopping. Bye.

---

### Post by CommonClone on 2007-10-02
I finally got this script to enable my wireless connection.  First after I installed and configured the script, I could not reboot my computer...it would get stuck at the configuring networks phase of the reboot.  I had to reboot in recovery mode and do:

```

sudo depmod -ae
sudo modprobe ndiswrapper

```

after this everything worked for me.  I am using Fiesty 64 bit on a dell 1721 insiron laptop w/ AMD64 architecture.

hope this helps.

---

### Post by bmartin on 2007-10-02
> **emmir said:**
> Actually the system froze in executing the second command which (correct me if I'm wrong here) it inserts the ndiswrapper module. The thing is that I want to re-run the script again. I don't know how can this happen, I mean one time the script works and I can use my wifi and the other it doesn't....:(:(:( Should I remove bcmwl5 driver and the bcm43xx blacklisting and then give the script another go?
It'll just do the same thing (install the driver and blacklist bcm43xx again). [Here's]("http://ubuntuforums.org/showthread.php?t=297092&goto=newpost") a step-by-step guide that does pretty much the same thing.

---

### Post by bmartin on 2007-10-02
> **bigbadnewill said:**
> Hi, I have followed the guide and my wireless still isn't working. I have the broadcom 4318, running on a hp nx6110 laptop.

After i have blacklisted the 43xx and installed ndiswrapper etc my wireless network connection is no longer available in the Network Settings. It used to offer a Wireless option for me to change the properties of, and now it only had a 'Wired Connection' and a "Modem Connection'

How can i get my wireless connection back? Also, where can i get the latest version of the Broadcom driver from? I'm new to all this Ubuntu stuff, but really want to get into it all, so any extra help would be great!! :)
First, I'd try running **sudo depmod -ae** and **sudo modprobe ndiswrapper**, then see if it comes back. That should do it. ndiswrapper tends to work better than the firmware.

If not, you can always remove ndiswrapper (sudo modprobe -r ndiswrapper), unblacklist the bcm43xx kernel module (sudo pico /etc/modprobe.d/blacklist), and insert the bcm43xx module again (sudo modprobe bcm43xx).

---

### Post by Cyber-J on 2007-10-03
> **woody22075 said:**
> I downloaded the offline installer (I dont have internet with my computer yet) and when I ran the installer, I received a message the program couldnt load the message file.  i then have to exit (
ctrl+c) out of the window.

How to I get around this?

This one was getting me too. After a bit of digging, I found out that it the Ndiswrapper Installer script is not finding a file named LICENSE-BROADCOM. I noticed a file named LICENSE located in the root directory of the package which appears to be the file that is needed so I renamed it to LICENSE-BROADCOM and then reran installer.py accordingly and it worked. My HP laptop now happily connects.

---

### Post by DarkN00b on 2007-10-03
> **Cyber-J said:**
> This one was getting me too. After a bit of digging, I found out that it the Ndiswrapper Installer script is not finding a file named LICENSE-BROADCOM. I noticed a file named LICENSE located in the root directory of the package which appears to be the file that is needed so I renamed it to LICENSE-BROADCOM and then reran installer.py accordingly and it worked. My HP laptop now happily connects.

I re-uploaded the offline installer. It now includes a copy of the LICENCE file that had been renamed to LICENSE-BROADCOM. That should fix this particular problem.

---

### Post by sandiegotigerfan on 2007-10-03
Thank you.  I'm new to Ubuntu, and Linux in general.  The fix ended up not working for me, but installing Wicd did, so the thread did help!  Thanks for the help!

---

### Post by gnudoc on 2007-10-04
Another happy customer. :)

A heartfelt thankyou to everyone that has made this possible, from the original reverse engineering talent onwards.

gnudoc

---

### Post by bigbadnewill on 2007-10-04
> **Cyber-J said:**
> This one was getting me too. After a bit of digging, I found out that it the Ndiswrapper Installer script is not finding a file named LICENSE-BROADCOM. I noticed a file named LICENSE located in the root directory of the package which appears to be the file that is needed so I renamed it to LICENSE-BROADCOM and then reran installer.py accordingly and it worked. My HP laptop now happily connects.

Dude, you're a total legend!!!!!! I was trying to use the Offline installer and had the same error. But thanks to you and DarkNOOB I have now FINALLY got wireless working on my HP Laptop. Now i can get into the world of Linux...I have been waiting a long time!

Thanks again :D

I voted YES in the poll too :)

---

### Post by matchstick on 2007-10-04
This worked perfectly and was quick and painless.  This was the only thing holding me back from ubuntu because the same thing happened on my desktop.
This worked 100% on my gateway laptop.  Thanks!

---

### Post by DarkN00b on 2007-10-04
> **bigbadnewill said:**
> Dude, you're a total legend!!!!!! I was trying to use the Offline installer and had the same error. But thanks to you and DarkNOOB I have now FINALLY got wireless working on my HP Laptop. Now i can get into the world of Linux...I have been waiting a long time!

Thanks again :D

I voted YES in the poll too :)

Its good to know that little fix worked -- thanks for the feedback. :)

---

### Post by Brazman on 2007-10-04
This identified my U.S.Robotics Model 5417A as a incompatiable wireless card.  It then selected the correct choice of software that needed to be installed and performed successfully.  I am not connected to the internet due to being deployed but I do have a internet connection using my gov desktop.  Anyway, rebooted and my wireless was up and running.  Excellent work!  I do appreciate the people that made this happen.  I have been trying to join a wireless access point but was never successful until I used your program.

Thank You!

---

### Post by rpasell on 2007-10-04
Finally working wireless in one easy step.  Thank you so much.

---

### Post by mwacky on 2007-10-04
Thanks this worked great!  I'm using Gusty Beta AMD64 on Hp Pavilion zv6000.  

Had to enable and installl the firmware from the restricted drivers manager, then it was going.  

After the first restart wireless wasn't up, I reinstalled the package (for GNOME link at beginning of article), but ever since it has worked fine.  

For some reason I couldn't install the firmware (Restricted Drivers) before the package.

---

### Post by DarkN00b on 2007-10-05
> **Brazman said:**
> This identified my U.S.Robotics Model 5417A as a incompatiable wireless card.  It then selected the correct choice of software that needed to be installed and performed successfully.  I am not connected to the internet due to being deployed but I do have a internet connection using my gov desktop.  Anyway, rebooted and my wireless was up and running.  Excellent work!  I do appreciate the people that made this happen.  I have been trying to join a wireless access point but was never successful until I used your program.

Thank You!

Dude, that is awesome. Thanks for the feedback and good luck wherever you are. [img]http://img54.exs.cx/img54/2200/rockon5nk.gif[/img]

---

### Post by ev0lution on 2007-10-05
This method worked for me, but after a recent update, the wireless card just doesnt connect to my router anymore. It shows that the wireless network and hardware exist and are functioning but when it comes down to it, it cannot even make contact with the router. I tried reinstalling the drivers and ndiswrapper but it would just freeze up on me and lock me out of starting Ubuntu again. I was forced to do a full reformat. Any suggestions to how I can fix my wireless? Thanks

---

### Post by Brian79 on 2007-10-05
Truely a great help. I have been beating my head against the wall for 2 days on this. Your method worked like a charm. I did need to use the wicd, but it seems nicer than the network manager anyway!

for reference I have a HP dv6605us with broadcom 4311

Thanks
Brian:guitar:

---

### Post by DAJ on 2007-10-06
I have a compaq v2000 series lap top with a 64 bit Turion. The installer kept locking up when it was supposed to be inserting the ndiswrapper module. But the installer did take care of all the dependencies I needed after which I manually installed ndiswrapper and the wireless card activated. It seems that some older versions (pre 1.48) of ndiswrapper had trouble with AMD 64 bit chipsets, and that has been a confounding issue.

I still have network problems but the Broadcom card works.

---

### Post by bmartin on 2007-10-06
The 64-bit driver is not bundled in with the installer. That might be a big part of the problem... it depends on whether you're running 32-bit Ubuntu or 64-bit Ubuntu.

---

### Post by Beaker66 on 2007-10-06
I must thank you for this HOWTO. I've been trying for several days to get my wireless working. This HOWTO had me up and running in about 10 minutes.

Thanks!

---

### Post by Niniel on 2007-10-07
Maybe it's thanks to me using the latest 7.10 Beta, but I had no trouble at all getting the wireless up and running and enabling WPA. I did use the restricted drivers, so I may just have committed a mortal sin... :)

Had to enable roaming, but otherwise... nice and easy.

---

### Post by tdatu on 2007-10-07
Many Thanks! Works on my HP dv2410us, though it has a broadcom 41xx version, the installer automatically fixed the issue and installed the necessary driver. 
-tdatu

---

### Post by TrueN00b on 2007-10-07
I have tried a few methods to get my broadcom bcm43xx card working and it has not worked.  Just started with ubuntu and the whole linux thing.  I recently moved something and have to reinstall ubuntu, well it's what i prefer to do now with a clean slate.  I tried NDISWrapper but I am very sure I did not do a step right.  Plz help.

computer: compaq presario v5250
card: hp broadcom bcm4318

---

### Post by jwhorfin on 2007-10-07
Online installation choked on me at the inserting new nidswrapper module, but the offline installation worked like a charm on my Dell Inspiron 8200 ! =D>
Thanks to all who deserve credit :)

---

### Post by luchop on 2007-10-07
hi, I'm having a problem. I followed the instalation instructions, but fortgot to turn on my wireless card. I rebooted and turned on the card, run the installation again, and rebooted. But this time ubuntu wouldn't load, it got stucked qhile loading. I tryed to reboot it on recovery mode and i got this at the end: 
ndiswrapper: using IRQ 22
BUG: soft lockup detected on CPU#0!

I don't really know what's the problem, as I'm new to ubuntu.
I'm using a hp pavilion dv5120la, amd turion64.

---

### Post by luchop on 2007-10-07
well the problem misteriously solved itself. but now wireless connection is still not working. Any suggestions?

---

### Post by luchop on 2007-10-07
well, now I can't acces internet, even though it aparently detects the conections even the wireless. I'm writing from my friends computer now. anybody knows what may be happening?

---

### Post by salttalk on 2007-10-08
Hi. I actually fooled around with your program until it worked on my Acer Aspire 3000 laptop. I was very happy

UNTIL ...

I rebooted. Then it died, choked, froze ... you get the idea.

Well, I turned off the laptop and rebooted again, hit the ESC key and tried the Ubuntu Kernel 2.6.17-10 generic Recovery Mode (the 2.6.17-12 generic Recovery Mode died too).

At least I got to the terminal prompt.

The error is:

   .../lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
   loadndisdriver: loadndisdriver: main(544):version 1.9 doesn't match driver version 1.8
   ...

Now there is no way that computer is going to boot at all.

Do I have to try to install the whole system over again, and start from scratch?

I am sure this thing could work, although I have no idea what I'm doing. I actually got the wireless modem to work for a bit, before I rebooted. It sure would be nice to get this problem fixed so I could get back to whatever it was that was working so nice before.

Thanks, if anyone can help (with real simple instructions).

---

### Post by salttalk on 2007-10-08
Hi again.

Well, I did not need to completely install Ubuntu from scratch all over again after all. On page 86 of this thread, bmartin suggested a command **sudo ndiswrapper -e bcmwl5** and I tried it. I rebooted in Recovery Mode, got to the terminal prompt, entered this command, then entered the **reboot** command and the thing rebooted fine.

However, like everyone else, there is no wireless connection listed at all under **System=>Networking** window.

I tried the **sudo depmod -ae** and **sudo modprobe ndiswrapper** commands in the terminal. Nothing. Ran the Installer.py program again to "Install BCM43xx firmware," and still nothing (but at least it reboots OK). When I run Installer.py with "Install ndiswrapper and Broadcom Windows driver," it freezes on the reboot and I need to reboot in recovery mode, then use the **sudo ndiswrapper -e bcmwl5** command at the terminal prompt before rebooting again.

I am still looking through the threads to find some solution. There seems to be a conflict between the driver's version 1.8 and the version 1.9 of the firmware, or something like that. I haven't even got a clue as to what I am doing.

Thanks for the help, especially bmartin's suggestions.

Greg.

---

### Post by zdarova on 2007-10-08
thanks guys...you are the best...now is working!!! i made it in 3 minutes

---

### Post by bmartin on 2007-10-08
> **salttalk said:**
> I tried the **sudo depmod -ae** and **sudo modprobe ndiswrapper** commands in the terminal. Nothing. Ran the Installer.py program again to "Install BCM43xx firmware," and still nothing (but at least it reboots OK). When I run Installer.py with "Install ndiswrapper and Broadcom Windows driver," it freezes on the reboot and I need to reboot in recovery mode, then use the **sudo ndiswrapper -e bcmwl5** command at the terminal prompt before rebooting again.
OK, where do I start?

**sudo modprobe ndiswrapper** loads up ndiswrapper. **sudo ndiswrapper -e bcmwl5** removes the Broadcom NDIS driver, which renders ndiswrapper ineffective. The version conflict is an NDISwrapper-only problem. The firmware has nothing to do with any of that.

I recommend that you run the installer again and install ndiswrapper.

---

### Post by bmartin on 2007-10-08
> **luchop said:**
> well, now I can't acces internet, even though it aparently detects the conections even the wireless. I'm writing from my friends computer now. anybody knows what may be happening?
Run **sudo iwlist scanning** and see if the wireless network appears in the listing. If it does, try connecting using WICD or whatever program you have available to connect. If you're connecting to a WPA-enabled router, make sure you have WPA-supplicant installed.

---

### Post by luchop on 2007-10-08
Well after a series of events that seemed to follow some mysterious logic which to me seemed like pure randomness, I ended up in the following situation: 
I can only start ubuntu in kernel 2.6.20-15, the -16 freezes when it's starting. It only seems to detect my usb conection. just tried installing again ndiswrapper and bradcom driver, but it froze when compiling ndiswrapper. 

> **bmartin said:**
> Run **sudo iwlist scanning** and see if the wireless network appears in the listing. If it does, try connecting using WICD or whatever program you have available to connect. If you're connecting to a WPA-enabled router, make sure you have WPA-supplicant installed.

Thank's, I ran the command and it returned the following:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

I don't really know what to do, or what i'm doing, any suggestions? I'll try to run the program once more, see what happens.

---

### Post by bmartin on 2007-10-08
> **luchop said:**
> I don't really know what to do, or what i'm doing, any suggestions? I'll try to run the program once more, see what happens.
Try modifying /etc/network/interfaces so it only contains the following lines (put a # before any other lines)
```
auto lo
iface lo inet loopback
```
Then try booting the -16 kernel

---

### Post by Dean_Harryman on 2007-10-08
I canno get my wireless light to come on...

I Followed the directions to a T, and the wireless card shows up in the network manager, however I cant connect to the network via wireless, and the light is not turning on for the wireless card.

I have ubuntu 7.04 installed on an hp L2000 with a broadcom 54g wireless card.(4318)

Any Ideas on how to get this install up and running my wireless card would be greatly appreciated.

---

### Post by salttalk on 2007-10-08
> **bmartin said:**
> 
**sudo modprobe ndiswrapper** loads up ndiswrapper. **sudo ndiswrapper -e bcmwl5** removes the Broadcom NDIS driver, which renders ndiswrapper ineffective. The version conflict is an NDISwrapper-only problem. The firmware has nothing to do with any of that.

I recommend that you run the installer again and install ndiswrapper.

Hi. I did and it froze again when I rebooted normally. Actually, today I upgraded to 7.04, replaced **/etc/modprobe.d/blacklist** when the upgrade asked, and still no wireless showed up on the **System/Network** window. So I then:
[LIST]
[*]ran Installer.py to "Install ndiswrapper ..."
[*]wireless showed up after it, but no signal in WiFi Radar
[*]restarted system after this, froze
[*]reboot in recovery mode, with error: "ndiswrapper ... BUG soft lockup detected on CPU0!"
[*]Note: my Broadcom 802.11g network adapter PCI bus 0, func 0
[*]also: "loadndisdiver: main (544); ver 1.9 doesn't match driver version 1.8 ... loadndiswrapper failed (1536) ... Error inserting ndiswrapper (... ndiswrapper.ko invalid argument"
[*]So I did the **ndiswrapper -e bcmwl5** command & rebooted
[*]no wireless again
[*]ran Installer & it said "ndiswrapper already newest version"
[*]reboot, froze, so I rebooted in recovery mode
[*]this time did the **ndiswrapper -r bcmwl5** command & rebooted normally OK
[*]ran Installer "Install BCM43xx firmware" & rebooted normally OK
[*]no wireless still
[*]ran Installer "Install ndiswrapper ..." & rebooted, froze, etc.
[/LIST]

Basically, on my other computer, I have run Ubuntu for perhaps almost a couple of years, and am very happy with it. So I thought I'd try it on my son's laptop, since I've had to do a couple restores on it already with Windows XP, and it was so full of spyware (or something which antispyware could not remove) that it would barely run even a word processor anymore.

Now this laptop seems to run fine in Ubuntu, once I figured out how to install it with a version from a book I got at the library (and I have got to buy a good book on UBUNTU for myself soon). But, in that book, and elsewhere, I cannot seem to find a way to get the wireless modem running.

Thanks.

Greg.

---

### Post by Dean_Harryman on 2007-10-09
Ok I got it working..... I had to find firmware for the card, and install.... and someone on the irc helped me get the card enabled!

Worked rather smoothly, took a while.... but I am a linux noob so......LOL

Here is what I did.....

after following the guide, I did the following procedure...

firmware file was provided by a guy on the irc...

```
 cd Desktop
sudo tar -xjvf bcm4311_firmware.tar.bz2
sudo mv bcm43xx* /lib/firmware
ls /lib/firmware
sudo modprobe bcm43xx
dmesg|tail
iwlist eth1 scan
sudo modprobe bcm43xx
```

---

### Post by luchop on 2007-10-09
Ok, I ran install.py again and now I cant boot in any mode. I am now running ubunto on cd. Does anyone know how to get my ubuntu working again? help please!

I'll try what bmartin said once I get to boot normally....

---

### Post by dolomite792 on 2007-10-10
Hey Everyone, I was wondering if you could tell me if this driver fix will work with aircrack or kismet or some wireless packet capturing utility?  Are there any alternatives to be able to use aircrack with this broadcom modem problem?


I'd just like to give a big thanks to everyone in this thread that has contributed as well as the makers of this driver.  Thank you so much!!!!!!!!!

This is an excellent community.

---

### Post by salttalk on 2007-10-10
> **luchop said:**
> Ok, I ran install.py again and now I cant boot in any mode. I am now running ubunto on cd. Does anyone know how to get my ubuntu working again? help please!

I'll try what bmartin said once I get to boot normally....

Hi. Actually I don't know what I am doing either. But I had the same problem. You need to press the ESC key immediately after Ubuntu starts booting up. A menu will appear, and select one of the other kernels from that menu.

If you need to, boot in the kernel with the lowest number in "recovery mode." Then, it should get to a terminal prompt. There you might need to type in a command. I needed to get rid of a driver that a function called "ndiswrapper" was using, before mine would boot. So I typed in **ndiswrapper -r bcmwl5** at the prompt.

Like I say, I don't really know what I'm doing. But I hope that might help.

Greg.

---

### Post by salttalk on 2007-10-10
This Acer Aspire 3000 is now online wirelessly. This is what I did:
[LIST]
[*]The extracted folder of Blake Martin's installer program has a subdirectory called "bcmwl5." Into that subdirectory, I copied the **bcmwl5.sys** driver file from a backup of the old Windows drivers I had for the Acer.
[*]Then I rand the Installer.py to "Install BCM43xx firmware"
[*]Then I ran Installer.py again to "Install ndiswrapper ..."
[*]Then I removed the "WiFi Radar" program.
[*]Rebooted normally, without freezing.
[*]Wireless runs automatically (after set up in System=>Network).
[/LIST]

So Blake Martin's program works very well. But somehow his "bcmwl5.sys" was different from the one which the Acer required. Now I am typing this very message online wirelessly! :)

Thank you very much Blake! It works great! God bless you even!

Greg.

---

### Post by da_gargian on 2007-10-10
hi
i tried your online installer but through installation it asked me for the feisty fawn cd from there up nothing happens anymore. 
did i som wrong or doesn´t support my system? it is a dell wlan1500 minicard..

thank you for help

---

### Post by DarkN00b on 2007-10-11
You need to open the Synaptic Package Manager then click on the Settings menu. Now click on Repositories. Then click on the "Third Party Software" tab and uncheck any CDs you see there. Click the OK button and click the Reload button way over there on the left. Try the installer again and it should work fine.

---

### Post by cvcuse on 2007-10-11
Just wanted to say thanks for your 'how to'. Worked for me.

---

### Post by jnorthr on 2007-10-11
sorry friends, but i'm lost on this one:
broadcom 4318 was working perfect thru ndiswrapper 1.49 test version using lsbcmnds.inf, but something happened and wlan0 just disappeared and is no longer on my system. 

Now as we all do, i did NOT make  copious notes as to how wlan0 was created in the first place, so i'm having a devil of a time trying to get it back. I think ndiswrapper is ok and have done rmmod bcm43xx to stop all those dmesg messages about missing 'firmware5'. Any ideas as to how to re-create wlan0 device ?

ADMIN: sorry to have posted this in wrong thread, can you move it ? Ta

---

### Post by cvcuse on 2007-10-11
After the short lived success of 'wireless' surfing the net and if I should attempt to correct  the screen resolution from 'vesa' xserver default, (have tried numerous 'nvidia driver installs for gf8400gs on vostro 1400) decided to just reboot and hopefully see the wierless running. At login this now appeared......... "GDM could not write to your authorization file. This common out of disk space home directory  could not be opened for writing. Not possible to log in.Please contact system administrator."
Any help appreciated and thanks.

---

### Post by Steve Parsons on 2007-10-11
Many Thanks. After 3 days of trying various methods to get wireless networking running,I came across your "How to". 
Wireless network was up and running in less than half an hour.
I am using Ubuntu 7.04 (Fiesty Fawn) on a HP Pavilion zv6009EA laptop and have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) installed.
Again Many Thanks.:):):)

---

### Post by Stylized on 2007-10-11
[B][U][COLOR="Red"]does it works also for:
Linksys WPC54G ver 1.2 ????[/COLOR][/U][/B]

please help me i stuck with this card already for two months

---

### Post by Stylized on 2007-10-12
People PLEASE help me i'm stuck!

i have installed the fiemware and ndiswrapper and i don't know what to do after that
how can i configure the settings of my wifi card..
and how can i turn it on?

please help me i'm very new to linux and i don't know how to do this steps..
=(

---

### Post by schwinn on 2007-10-12
I had been struggling with ndiswrapper recently - it worked fine before, but along the way I simply couldn't get it to work manually.

This script worked perfectly, and is running now as I type. Thank you for making it so simple! I wish the BCM drivers were "included" in Ubuntu, but at least this makes the process much easier than it was before. Thank you!

---

### Post by schwinn on 2007-10-12
> **Stylized said:**
> People PLEASE help me i'm stuck!

i have installed the fiemware and ndiswrapper and i don't know what to do after that
how can i configure the settings of my wifi card..
and how can i turn it on?

please help me i'm very new to linux and i don't know how to do this steps..
=(

I am using 6.06, so the menu names may be a little different, but here's the process:

Go into the System menu, then Administration, then Networking. Within the new window, you should see the Wireless connection item in the list, indicating that the firmware works. If it's not there, then the install didn't work. If it is, then select the wireless connection, and click the properties button. In there, you select the appropriate access point and other related connection information. Also, make sure the wireless connection is "active". Then, lastly, select your "default gateway device" as the wireless connection, and click ok to complete. That should use your wireless connection from there-on...

Good luck.

---

### Post by Stylized on 2007-10-12
> **schwinn said:**
> I am using 6.06, so the menu names may be a little different, but here's the process:

Go into the System menu, then Administration, then Networking. Within the new window, you should see the Wireless connection item in the list, indicating that the firmware works. If it's not there, then the install didn't work. If it is, then select the wireless connection, and click the properties button. In there, you select the appropriate access point and other related connection information. Also, make sure the wireless connection is "active". Then, lastly, select your "default gateway device" as the wireless connection, and click ok to complete. That should use your wireless connection from there-on...

Good luck.

Thanks a lot I will try it..

---

### Post by Stylized on 2007-10-12
Ok i have a new problem i realized that the installation
didn't finish properly.

When i see this line:
```

Inserting ndiswrapper module...

```

_the system crushing.._
_everything stops_ and the only thing i can do is to turn the computer off...

**anyone know whats the problem? =\**

---

### Post by pat3691 on 2007-10-12
Well!  Back to square 1! 

My wireless card worked for a while but when I had to use a another router usign WPA instead of WEP everything stopped working.... And I did used the instructions at the beginning of the thread.

I decided that I would start all over again but now it is even worse than the 1st time, nothing detects the card not even installer.py

](*,)]                                          ](*,)]                                            ](*,)]

Here the results of various commands and I also posted my install.log file


patrice@PatLinux:~/Wireless$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

***************************
patrice@PatLinux:~/Wireless$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.
***************************
patrice@PatLinux:~/Wireless$ ndiswrapper -l
bcmwl5 : driver installed
patrice@PatLinux:~/Wireless$
***************************

---

### Post by luchop on 2007-10-13
Well, I'm stuck and I need help. The situation is the following: after running he install.py, ubuntu won't boot in any kernel now, not even in recovery mode. I'm running it on cd now. How can I uninstall ndiswrapper now? I can't seem to get a command line... 
Please if anybody knows how to get my ubuntu to boot normally, I need to get my pc working again...

---

### Post by stolid_agnostic on 2007-10-14
I want to say thanks, this works perfectly for me........


UNTIL.........



I reboot!


ndiswrapper -l shows the hardware and driver installed correctly and the device shows in the control center

when I first install and restart, it takes and IP and everything works great. when I restart my computer, it can never take an IP again. When it tries to ping the recorded lease, it does not get any responses. Any ideas?


P.S. I had no problems in feisty. <gulp> I put on gutsy last night and it sort of lost the wrapper and the driver, so I had to go through this process. a friend of mine set it up originally for me, so I do not know if this is the method he used or not.

---

### Post by luchop on 2007-10-15
> **luchop said:**
> Well, I'm stuck and I need help. The situation is the following: after running he install.py, ubuntu won't boot in any kernel now, not even in recovery mode. I'm running it on cd now. How can I uninstall ndiswrapper now? I can't seem to get a command line... 
Please if anybody knows how to get my ubuntu to boot normally, I need to get my pc working again...

Please I'm desperate, I need to boot normally to acces my files; anyone knows how I can boot normally again?

---

### Post by jflaker on 2007-10-15
THANK YOU.

This post needs to be made more prominent on the site.  I had asked this question in the support forum and downloaded the driver.  It worked, but then I had fudged the install of Ubuntu somehow and reloaded and OOPS!  I no longer had the link!

So, besides some of the driver issues (yeah, same issues under Window$), I am still afraid to move COMPLETELY over to Linux!....that is another soapbox for another posting though.

Thanks!  Great to see that this community support outdoes Windows KB articles by MILES!

Keep up the great work and start moving some of these helpful posts to the front!

JEFF

---

### Post by stolid_agnostic on 2007-10-16
> **stolid_agnostic said:**
> I want to say thanks, this works perfectly for me........


UNTIL.........



I reboot!


ndiswrapper -l shows the hardware and driver installed correctly and the device shows in the control center

when I first install and restart, it takes and IP and everything works great. when I restart my computer, it can never take an IP again. When it tries to ping the recorded lease, it does not get any responses. Any ideas?


P.S. I had no problems in feisty. <gulp> I put on gutsy last night and it sort of lost the wrapper and the driver, so I had to go through this process. a friend of mine set it up originally for me, so I do not know if this is the method he used or not.


well turns out that I just needed to take off networkmanager and install wifi-rader and everything was golden!  :D


thanks so much to the contributors to this thread!  :grin:

---

### Post by mowgli81 on 2007-10-16
> **luchop said:**
> Please I'm desperate, I need to boot normally to acces my files; anyone knows how I can boot normally again?

Not sure if it would work but you can boot using the live cd, mount your partitions and chroot to the / of your installation and uninstall ndiswrapper.

---

### Post by mowgli81 on 2007-10-16
ndiswrapper installed through apt used to oops for me on amd64. I downloaded the latest source from website and installed and now everything works as it should.

---

### Post by Papa-san on 2007-10-16
Worked like a charm! Running a Dell Lattitude C-610 with the Bcom 4306 card.\\:D/

---

### Post by Papa-san on 2007-10-16
Worked like a charm! Running a Dell Lattitude C-610 with the Bcom 4306 card.

lshw:
*-network:1
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth1
                version: 02
                serial: 00:90:4b:2c:52:6b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper ip=XXX.XXX.X.XX multicast=yes wireless=IEEE 802.11g

This script and an install of 'WICD' had me up and running in 15 minutes!

---

### Post by AmericanYellow on 2007-10-16
Worked perfectly for my Broadcom 4318 wireless card. I was previously using fwcutter firewire but it only gave me 24MB/s when my card we capable of 54Mb/s. Thanks! I was using Ubuntu 7.10.

---

### Post by toddharp on 2007-10-16
worked like a charm. thanks.

---

### Post by Ulysses on 2007-10-16
Hey

It worked and it didn't work
Dapper 6.06
IBM thinkpad P3 800 w/256MB RAM

Downloaded and followed the instructions

But it sees it as eth0 and not wlan1 and whenever I go to activate it, it says disconnected

Can you please help? My wife will make me go back to Windoze if I can't get her laptop to work like I promised (it's been 5 days!)

RAR

---

### Post by Am3ndment on 2007-10-18
I really cant thank you enough! Ive been crying blood with my Broadcom, and then you came and saved me! THANKS A LOT!

---

### Post by Niniel on 2007-10-18
> **jflaker said:**
> THANK YOU.
Thanks! Great to see that this community support outdoes Windows KB articles by MILES!

JEFF

Uhm, Jeff, you must have failed to discover the MS boards then... you know, kind of the same thing like this, only full of MS heathens. Very active as well. Lots of helpful people there.

I'm happy for you that you found a solution to your problem, but please, keep the comparisons real. The Knowledge Base is just that - a bunch of tech prose, not a support board.

---

### Post by Skigi on 2007-10-18
I'm currently running the online install on my laptop, and as far as I can tell it has frozen and locked completely up as soon as I got to the 'Inserting ndiswrapper module' thing. I can't see any visible progress, and it's been more than 5 minutes. Should I be worried?

---

### Post by pianojuggler4 on 2007-10-18
Thank you so much, worked perfectly.

---

### Post by JulienPDX on 2007-10-18
so ...yah, anyone got this to work with Gutsy yet? I just tried it today after a fresh install but his installer doesn't seem to work with my kernel..so it looks like a no-go:confused:

---

### Post by huntermaclean on 2007-10-19
I have a Dell TrueMobile 1300 aka BroadCom 4306. I tried to install using the easy app available on the forums and it did not work. Has anyone found directions that work?

---

### Post by Ulysses on 2007-10-19
Hello

I have an IBM X22 P3,800 laptop with Broadcom 4306 card and I am having troubles as well.
I tried installing 6.06 and using this with no-go
I have installed 7.04 and will try it again
I have not tried upgrading to 7.10 yet, but if it helps, I will

RAR

---

### Post by toscal on 2007-10-19
Well done this is the only one that worked. I'm using a DELL Inspiron 1300 Laptop. And the Ubuntu 6.06 Live CD version installed on the machine.

---

### Post by VON_CAPO on 2007-10-19
I made a fresh install of Gutsy and it works at once.
My card use Broadcom 4318 chipset.
I used the files "bcm43xx-fwcutter_006-3_i386.deb" + "wl_apsta.o". :)

---

### Post by MadEarThInk on 2007-10-20
Dude,

You are the best. Just wish i had found this 6 hours ago!  ty exponentially!:guitar:

---

### Post by brennydoogles on 2007-10-20
ok, so just wondering before I upgrade to Gutsy on my laptop, has anyone gotten the script to work in Gutsy?? What about upgrading a laptop that's working under Feisty? Thanks!

---

### Post by Dr.Suave on 2007-10-20
My kernel isnt supported! What do I do??!

---

### Post by Am3ndment on 2007-10-20
> **brennydoogles said:**
> ok, so just wondering before I upgrade to Gutsy on my laptop, has anyone gotten the script to work in Gutsy?? What about upgrading a laptop that's working under Feisty? Thanks!

Im running on Gutsy, and it works.

---

### Post by nadavvin on 2007-10-20
I upgraded to Gutsy and the wireless didn't work.

I installed again Ndiswrapper and the Broadcom windows driver successfully.

When I restated the computer, the Knetworkmanager didn't detect any interface, not the wireless and not the wire that I connect to it now.

In contract to it, the restricted-manager-kde detect that the firmware installed and in use.

Why does Knetworkmanager don't recognize any interface? and especially the wireless...

I use the old kernel of Feisty since in the Gutsy kernel, it isn't possible to change the brightness of the screen in Dell INSPEIRON 6400

---

### Post by kevindubrow on 2007-10-20
Wireless for the Boradcom 43xx isn't working in Gusty for me either. I have to reinstall the Broadcom firmware each time I boot up in order for wireless to work. Any ideas for what I should do? Thanks.

---

### Post by executor on 2007-10-20
tanks workd agin,  using ndiswrapper in gutsy, on broadcom 4318. 54Mb/s.

i used the bcm43xx-0.3.2  and it instaled the ndiswrapper, i had to have the 7.10 cd in the drive to make it work.

and i was online whit wired network to make it work.

and  i using Wicd to manage the network

---

### Post by Hanpusu on 2007-10-20
Used this installer on my Dell 120L with a Broadcom 43xx chipset in the newest version, 7.10 Gusty. Anyhow, after installing it and restarting the computer, it's not there. Theres no wireless configurations available in nm-applet and when I look in "Hardware information" the "WLAN interface" that was under the "BCM4318 [AirForce One 54g] 802.11g Wireless LAN" label is gone.

When I click on "BCM4318 [AirForce One 54g] 802.11g Wireless LAN" it say that the driver is unknown and also attainments say the same thing.

How to solve?

---

### Post by Am3ndment on 2007-10-20
> **nadavvin said:**
> I upgraded to Gutsy and the wireless didn't work.

I installed again Ndiswrapper and the Broadcom windows driver successfully.

When I restated the computer, the Knetworkmanager didn't detect any interface, not the wireless and not the wire that I connect to it now.

In contract to it, the restricted-manager-kde detect that the firmware installed and in use.

Why does Knetworkmanager don't recognize any interface? and especially the wireless...

I use the old kernel of Feisty since in the Gutsy kernel, it isn't possible to change the brightness of the screen in Dell INSPEIRON 6400

Try using that WiCD.

---

### Post by dammitTim on 2007-10-21
My wireless card is a Broadcom 440x, will this how-to work for me?

---

### Post by schwinn on 2007-10-21
Just used this with Gutsy on a 4306 card (HP zd7000 laptop - zd7102us). I'm not sure if it was necessary, but it's working in any case, using the bcmwl5 driver, which was downloaded by the script, I believe.

The reason I don't think it was necessary is because I was looking at the wireless LED to see if Ubuntu recognized the card, and I also didn't see any wireless networks in the network manager. Even after installing this driver, the LED remains off (though the network manager sees networks). The LED only turns on (blinks) when there is any transmit or receive data... weird, but if it works, I don't care.

In summary, this script worked for me on 6.06LTS as well as my newly installed 7.10. Awesome!

---

### Post by sbowne on 2007-10-21
It worked!  Thanks for providing this easy tool!

I got a Linksys WPC54G ver 3.1 to work in Ubuntu Feisty on a Dell Latitude CSx.

When I ran the Install.py script, this message appeared:

"Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended."

 tried that and it did not work.  So I just ignored the recommendation and tried the first option and it worked!

However, it did not automatically insert the module at the next startup.  So I added "bcm43xx" to the /etc/modules file with these commands:

cd /etc
sudo cp modules modules.bak
sudo pico modules

Add "bcm43xx" to its bottom ( without quotes ) and save the file.

Now it works fine, even after a startup!

---

### Post by Noobie1982 on 2007-10-21
Nope, doesn't work for me.  It ran, said there wasn't a chipset detected (compaq presario v6000 with a 4311 rev01 chipset), so installed ndiswrapper and no joy.

The LED for the wireless also says it's off. There is no keyboard control for the wireless as far as I can tell so it's not that, and it works fine under windows XP.

---

### Post by Noobie1982 on 2007-10-21
OK,  It _almost_ works for me... I ignored the message that it couldn't detect a compatible chipset, went for install firmware, and it now recognises the card in iwconfig and ifconfig -a.

It even flashed on briefly on boot.

However, once the OS is up and running it turns it off again, though it still shows as being there, and anything trying to use it (for example ifconfig eth1 up, says it doesn't exist.

Pulliing my hair out hasn't solved it, this is however as close as it's gotten to actually working.

---

### Post by matchstick on 2007-10-21
cant get this to work on 7.10.  I tried running the online version with a wired connection, and it installed ndiswrapper and everything, but when i restart i still dont have wireless networking, when i click on the networking icon in the taskbar all i see is Wired Connection, and Manual Config.  Can anyone help with this?

oh yea it worked on 7.04 flawlessly, and I have a Gateway MX6422 laptop

---

### Post by fasterthanjesus on 2007-10-22
[solved]
ACER Aspire 3000 with Broadcom wireless adaptor 4318.

had 2 weeks of problems - mostly acerhk/acpi related.  tried everything recommended.

1.  upgraded to 7.10.
2.  blacklisted the alternate driver.
3.  used wifiradar to configure wep.

success.  very happy. many thanks to all who has posted any tips.  

pm me if you have a similar acer aspire and want any further help.

regards

ftj

---

### Post by Bishop Hill on 2007-10-22
This is what it says for me when I press RUN:

bash: ./stats-logger: No such file or directory

Should I create a random folder named "./stats-logger"? Otherwise, what should I do?

edit Ok, I got it working, but this thing messed stuff up. Seriously.

Network manager cant find any wireless. When I try "iwconfig" in terminal it says:

idaniel@daniel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Help?

---

### Post by matchstick on 2007-10-22
> **matchstick said:**
> cant get this to work on 7.10.  I tried running the online version with a wired connection, and it installed ndiswrapper and everything, but when i restart i still dont have wireless networking, when i click on the networking icon in the taskbar all i see is Wired Connection, and Manual Config.  Can anyone help with this?

oh yea it worked on 7.04 flawlessly, and I have a Gateway MX6422 laptop

found a thread that fixed my problem.  I installed the restricted drivers/firmware, and the did the following:

```
gksu gedit /etc/modules
```
then added
```
bcm43xx
``` 
to the end of it.  I guess when I install the drivers it would call the module, but then after a restart it wouldn't load, and this loads it every time. 

(I guess thats whats happening, not 100% sure as I got this from another thread, but thought it might help out others here.)

---

### Post by Elotero on 2007-10-22
Tried the tutorial and it worked great.. i have a "wireless" switch that is supposed to light up and for a short while it was blinking and i was getting wireless... i disconnected my ethernet cord and was going to write a post here on how good it worked BUT immediatley i lost connectlivity.. i opened Wifi Radar and found my connection... logged into my connection but the message says i am connected to nothing and i have no IP address... can i get some help?

---

### Post by Noobie1982 on 2007-10-22
I can tell how close the stupid thing is to working, it seems to power the wireless up right until X loads (i.e. the login screen appears) at which point it powers down... Grrrrrrrrrr I will solve this if I have to stay up all bloody night!

---

### Post by DarkN00b on 2007-10-22
> **Elotero said:**
> Tried the tutorial and it worked great.. i have a "wireless" switch that is supposed to light up and for a short while it was blinking and i was getting wireless... i disconnected my ethernet cord and was going to write a post here on how good it worked BUT immediatley i lost connectlivity.. i opened Wifi Radar and found my connection... logged into my connection but the message says i am connected to nothing and i have no IP address... can i get some help?

Did you try using WICD? It is our preferred connection manager because it does about everything. Also, are you using an encrypted connection? You'll need to enter your keys if you are.

---

### Post by Elotero on 2007-10-22
> **Elotero said:**
> Tried the tutorial and it worked great.. i have a "wireless" switch that is supposed to light up and for a short while it was blinking and i was getting wireless... i disconnected my ethernet cord and was going to write a post here on how good it worked BUT immediatley i lost connectlivity.. i opened Wifi Radar and found my connection... logged into my connection but the message says i am connected to nothing and i have no IP address... can i get some help?

Forgot... i am using a HP ZV5000... BC 4311 i believe.. on Fiesty Fawn.....

---

### Post by manro on 2007-10-22
Hi to all!

I followed this tutorial (and others) but I cannot get may wireless card to work :(

I have a HP Pavillion dv6646us with a AMD Turion64 x2 Processor and a Broadcom 4328 (rev03) wireless adapter running Gutsy i386 distribution.

Basically when I install the driver with ndiswrapper the wireless adapter "respond" but it just don't "see" any wireless connection, even if I specify the SSID.

Please, if someone have a clue of how to make it work, let me know.

Apologies for my bad english

Best regards, :)
Manro

---

### Post by Noobie1982 on 2007-10-22
Any ideas why I'd get IRQ timeouts on the bcm43xx module?  I suspect it may be responsible for my bcm4311 not apparently existing (despite iwconfig recognising its existence).

---

### Post by Elotero on 2007-10-22
Shoot... ive been trying to get help here forever.. this tutorial worked but once i disconnected the ethernet cord it stopped.. i can see my signals and connect to my network but i get "No IP address" my IP address shows up as 0.000.00.00.  All i need is an IP.. can i get some help?

---

### Post by xxrealmsxx on 2007-10-22
> **Elotero said:**
> Shoot... ive been trying to get help here forever.. this tutorial worked but once i disconnected the ethernet cord it stopped.. i can see my signals and connect to my network but i get "No IP address" my IP address shows up as 0.000.00.00.  All i need is an IP.. can i get some help?

Are you running WPA? 

If so try not using a password, and then WEP.

---

### Post by Elotero on 2007-10-22
> **xxrealmsxx said:**
> Are you running WPA? 

If so try not using a password, and then WEP.

I think im running WEP... i typed in a code for WEP..

---

### Post by mauricevh on 2007-10-23
Hi there, I'm an absolute n00b in Linux, fut finally managed to fix my ethernet  :)
Next thing is is my wireless card. I got a vostro 1000 with ubuntu 7.10 but when I follow this guide, it comes up with more than one solution, Install BCM43XX firmware, WIFI-radar connection manager, etc. Which do I have to chose? When I chose for example the last one, it wants to download something from the internet, but it always stops around 50%, the same holds for WICD wireless manager. And when I chose de ndiswrapper option I lose my wireless connection logo in my network manager... So what is the best option and how can I allow the terminal to download files from the internet (because surfing and download using firefox is possible).  
Thanks in advance!

---

### Post by Elotero on 2007-10-23
No help for my wireless issue?  Even after i got so close?

---

### Post by DarkN00b on 2007-10-23
> **Elotero said:**
> No help for my wireless issue?  Even after i got so close?

You should first try disabling encryption on your wireless router or modem and making sure your connection works. Then re-enable encryption making sure the keys on your router/modem and your wireless smanager match.

---

### Post by DarkN00b on 2007-10-23
> **mauricevh said:**
> Hi there, I'm an absolute n00b in Linux, fut finally managed to fix my ethernet  :)
Next thing is is my wireless card. I got a vostro 1000 with ubuntu 7.10 but when I follow this guide, it comes up with more than one solution, Install BCM43XX firmware, WIFI-radar connection manager, etc. Which do I have to chose? When I chose for example the last one, it wants to download something from the internet, but it always stops around 50%, the same holds for WICD wireless manager. And when I chose de ndiswrapper option I lose my wireless connection logo in my network manager... So what is the best option and how can I allow the terminal to download files from the internet (because surfing and download using firefox is possible).  
Thanks in advance!

This installer really is not designed for Gutsy. That's why it stops when downloading WICD and probably ndiswrapper as well. The problem is that it was never planned for this method of installing to last as long as it has. The next stage of bmartin's installer can be found [here]("http://sourceforge.net/projects/wifix/"). bmartin has started another project that aims to be more than this little script can ever be -- cross platform. His project is still in the early stages and -AFAIK- not very usable at this point, but it will be very useful.

---

### Post by thomaswp on 2007-10-23
This method was the one that finally got my broadcom card working under gutsy.  Everything else failed.

I have one minor problem though.  If I boot normally the boot hangs on the splash screen with about 20% of the progress bar filled.

I have to power off, and then if I boot through safe mode and Control-D at the appropriate point everything works perfectly.

I am at a loss, I cannot even find a log that tells me why it hangs?

---

### Post by bmartin on 2007-10-23
> **thomaswp said:**
> I am at a loss, I cannot even find a log that tells me why it hangs?
If you go into GRUB and edit the "kernel" line under the normal boot and remove the word "splash", it should show you where your boot gets stuck. It might be where your network devices are detected. That would be the place to start.

Is this a USB device or a PCMCIA card you're using, or something else? If it's something that can be unplugged, unplug it... does your computer boot then? That's another thing to look for.

Once you know those two things, fixing the problem should be easier.

---

### Post by motang on 2007-10-23
Dude, this worked like a charm.  Thanks a lot! :-D

---

### Post by Elotero on 2007-10-23
[QUOTE=DarkN00b;3611258]You should first try disabling encryption on your wireless router or modem and making sure your connection works. Then re-enable encryption making sure the keys on your router/modem and your wireless smanager match.[/QUOTE

Do you know how i go about doing that?

---

### Post by ICrisis on 2007-10-23
First time Linux user here.

Tried it on Gutsy and actually left me worse off. Not only did it not work, it somehow managed to disabled my wired connection as well and now I can't connect to the internet, period (I'm typing this at the library). Is there anyway I can reset my wired connection at least? I'd like to get that back online before I try giving Wireless a go.

Edit: My card is a Broadcom4318 on an Acer Ferrari 4005.

---

### Post by elysium1298 on 2007-10-23
THANK YOU!!!! it works perfectly on my \\:D/ HP dv6625US

---

### Post by elysium1298 on 2007-10-23
Works great on a dv6625us with Ubuntu 7.10!!

---

### Post by Noobie1982 on 2007-10-23
Well, thanks for the howto, sadly it didn't work for me at all, so I've tried suse 10.3 and that has exactly the same problem.  ndiswrapper just doesn't want to work no matter what I try and bcm43xx simply doesn't actuate the device.

Having spent fruitless hours beating configs into nothingness and obeying practically every howto I could find I'm going to give up on linux, and probably just buy a macbook for christmas instead.

---

### Post by thomaswp on 2007-10-23
> **bmartin said:**
> If you go into GRUB and edit the "kernel" line under the normal boot and remove the word "splash", it should show you where your boot gets stuck	:biggrin: LOL - with "spash" removed it boots perfectly.  As soon as I put "splash" back it hangs again - three and a half squares in.

Thanks for that help - at least I can boot reliable now AND have wireless...

ubuntu is amazing but the wireless problems drive me nutty.  I would love to solve this spash screen problem and will keep searching.

Later:  I am stuck.  Have posted this thread: [http://ubuntuforums.org/showthread.php?p=3614055#post3614055](http://ubuntuforums.org/showthread.php?p=3614055#post3614055)

---

### Post by Izzy25 on 2007-10-23
sorry if this is a dumb question but i am a newbie at this
i just finished installing ubuntu 7.04 on my Acer Aspire 5100 laptop, however i cant seem to get any wireless feedback i have no idea on where to begin in configuring it, there are two computers that show up on the top right hand corner but when i click them it only take me to the network panel where i choose the way i want to connect, which are wireless, wired, or dial up. I have no idea on where to begin since i cant find any application that shows me a list of networks in range

---

### Post by bmartin on 2007-10-24
I've experienced the lock-up problem with inserting the NDISwrapper kernel module myself, even after performing the installation steps manually. The problem can be circumvented by using NDISwrapper v1.47. I've filed a bug report with the NDISwrapper team. We might see this fixed in the next version.

---

### Post by xenocryst on 2007-10-24
I've followed the instructions listed on this post and am still having trouble getting a connection. 

The installer didn't automatically tell me which option to use so I tried the ndiswrapper option. While it was installing it was infinitely printing out stuff (I managed to read the word Unexpected as the words flew by on the screen) in the terminal that opened from the installer.  

So then I decided to try the Install BCM43xx option. which ran without error, but I'm still having a problem. 

I have Wicd installed also. Prior to following this post iwconfig returned no wireless extensions but now eth1 is added with the following details:

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I can't find a wireless broadcast with Wicd, and I noticed above that Access Point says invalid. I'm not sure if that has any significance to my problem. Any ideas what I should do from here? 

Thanks

---

### Post by bmartin on 2007-10-24
Run the following command in a terminal:
```
sudo iwlist scanning
```
If no wireless networks are returned, your wireless radio is off. Usually there's a switch on your computer somewhere or a keyboard combination (Fn+F2 is the common one) or a button you have to press to activate it. Sometimes there's a BIOS setting that needs to be changed. After that, you should be able to scan and connect.

I'm going to save this response as a canned response; this is probably the most commonly asked question. It's already in the FAQ.

---

### Post by xenocryst on 2007-10-24
My switch is on, and there is no bios setting for it. After restarting my eth1 disappeared from what iwconfig returns... confused =/

---

### Post by bmartin on 2007-10-24
> **xenocryst said:**
> My switch is on, and there is no bios setting for it. After restarting my eth1 disappeared from what iwconfig returns... confused =/
What's the output of this:
```
lsmod | grep ndiswrapper
```
If it's nothing, then the NDISwrapper kernel module failed to load. Did you ever blacklist it?

To load it again, you can run
```
sudo modprobe ndiswrapper
```

---

### Post by xenocryst on 2007-10-24
the output of 
lsmod | grep ndiswrapper

was indeed nothing, so I did the modprobe then did lsmod | grep ndiswrapper again. which output the following:

ndiswrapper           185240  0 
usbcore               138632  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

Then I tried sudo iwlist scanning again and got
eth1 no scan results

---

### Post by bmartin on 2007-10-24
> **xenocryst said:**
> the output of 
lsmod | grep ndiswrapper

was indeed nothing, so I did the modprobe then did lsmod | grep ndiswrapper again. which output the following:

ndiswrapper           185240  0 
usbcore               138632  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

Then I tried sudo iwlist scanning again and got
eth1 no scan results
ndiswrapper isn't loading with your computer. Make sure the output of the following is empty:
```
cat /etc/modprobe.d/blacklist | grep ndiswrapper
```
If it's not empty, you need to remove the "blacklist ndiswrapper" line:
```
sudo gedit /etc/modprobe.d/blacklist
```
Try setting the switch to what appears to be the "off" setting, then... I've heard people complain that the switch "doesn't work at what looks like it should be the right setting" before.

We've established the following:
[LIST=1]
[*]The driver's installed properly and the device is detected (it shows up under iwconfig)
[*]ndiswrapper isn't loading at boot (a problem, but not too serious)
[*]Your wireless radio is off, OR you're not within range of a broadcasting router
[/LIST]
If you don't fix the ndiswrapper problem, you'll have to run **sudo modprobe ndiswrapper** every time your computer starts. Screw around with that switch until you can find an access point. Use **sudo iwlist scanning** to check for them.

---

### Post by Noobie1982 on 2007-10-24
To the originator of this applet, you are a GENIUS!

Fresh install of 7.10, ran the script, it's worked straight off!

You have saved my sanity and convinced me of the greatness of both ubuntu and yourself!

---

### Post by xenocryst on 2007-10-24
Still not getting any access point =/ I know I'm in range right now of a router I'm in my classroom on campus where I always get a signal and other around me have signal.. Is there any special that I have to do besides scanning for it in terminal/wicd? Also I did the sudo modprobe ndiswrapper before scanning..

---

### Post by bmartin on 2007-10-24
> **xenocryst said:**
> Still not getting any access point =/ I know I'm in range right now of a router I'm in my classroom on campus where I always get a signal and other around me have signal.. Is there any special that I have to do besides scanning for it in terminal/wicd? Also I did the sudo modprobe ndiswrapper before scanning..
The only thing I can think of is a key combination. You're using a laptop, right? With built in wireless, right? If those are both correct, what's the symbol on the F2 key? On mine, it looks like a printer, but on many laptops, it's the wireless radio kill switch.

---

### Post by xenocryst on 2007-10-24
mine looks like a printer too, I have a separate physical switch on the front of the laptop for wireless... I have an HP

---

### Post by bmartin on 2007-10-24
And the switch does nothing... weird... I'd post a new thread in the network and wireless section. State as much as you can about the model of your computer... or consult Google. Tell them that sudo iwlist scanning shows no wireless networks, but your Broadcom device is detected... and that you're using NDISwrapper.

---

### Post by captgadget on 2007-10-24
I had my BCM406 working at 80% before I followed these steps. Thought maybe I coudld get it to me more effiecent so I followed this and now it won't work at all. Is there some way to undo the step that installed ndiswrapper and the BCMxxx?

---

### Post by bmartin on 2007-10-24
> **captgadget said:**
> I had my BCM406 working at 80% before I followed these steps. Thought maybe I coudld get it to me more effiecent so I followed this and now it won't work at all. Is there some way to undo the step that installed ndiswrapper and the BCMxxx?
What were you using before? NDISwrapper or the bcm43xx firmware method?

Assuming you were using the firmware (or fwcutter - they're the same thing), to remove the NDISwrapper kernel module, add it to the blacklist file:
```
echo "blacklist ndiswrapper" | sudo tee -a /etc/modprobe.d/blacklist
```
Note that if you ever want to use NDISwrapper again, you'll want to unblacklist the kernel module so that you can use it again. 

To enable the bcm43xx kernel module (and firmware), modify the /etc/modprobe.d/blacklist file so that the "blacklist bcm43xx" line is removed:
```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by captgadget on 2007-10-24
I was using the bcm43xx firmware and then used the installation posted here that installed the ndiswrapper and the bcm43xx and now nothing works except hard wire.

---

### Post by BCEagles6 on 2007-10-24
I installed the file from the GNOME thingy... (i'm new to lunix)

I installed the NDIS Wrapper and Network Driver (i think.. it was the second option..) and the first option... Anyhow... I saved it to the desktop and extracted it to the desktop. Than I did all the .py installations. I Had the wirless working until I turned off my computer and than it wasnt working again. do I need to save the first file (from the orginal post) to somehwere other than my desktop? i'm using a 4318 wirless card.

So i did have it working but I shut down... restarted and it stoped working. Help?

---

### Post by sixstorm on 2007-10-24
I tried to go from 64-bit to 32-bit 7.10 and also tried installing the program used on page 1.  I needed NDISWrapper.  Everything installed just fine, except when I restarted, "Wireless Network" wasn't even in my list in Networking.  Worked fine in 64-bit . . . guess I'm just going to reinstall the 64-bit version.

Compaq Presario C714NR
Intel T2310 Dual Core
1GB RAM
Broadcom BCM94xxx Wi-Fi
120GB HDD
Intel X3100 Graphics

---

### Post by manro on 2007-10-24
Hey, 

For does who like myself got a Broadcom 4321/4328 abgn card, I finally made it work following *[**THIS**]("http://ubuntuforums.org/showthread.php?p=3625678#post3625678")* tutorial.

Thanks to **adamos** for all the help!

Regards,
Manro

---

### Post by Hishamz on 2007-10-25
Hey Guys, I' m realy new to Ubuntu Linux and just install via Gutsy dvd.

After Successfully install the OS, i can't connect to my school network which use **proxy** and i don't know how to search the wireless  network within my school area i keep going to Wired connection and i click properties and that's it end of story  .. using windows it will auto detect easily how can i auto detect the wireless network because there's no need any WPA security, its unsecure network where students can have free access.

sorry if my English damm bad will try to improve it

Sorry for being a newbie here ,

How can i solve this? 

 i using a Compag Presario V3246AU
Network intergrated Wireless Broadcom b/g/draft-n 

School network
SSID Nework Name: TP

Proxy : proxy.tp.edu.sg port 80

Really need YOU guys help! 

Thanks in advance

---

### Post by insulae on 2007-10-25
is work for me, i have a Compaq Presario V3415LA

with the chipset:

01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Grettings
insulae

---

### Post by DeadToad on 2007-10-25
After cussing for 2 whole weeks, I uninstalled Ubuntu v7.10 from my HP Pavilion dv9000z laptop.
I could not get my Broadcom BCM4312 Wireless Card to work!!!!!!!!!!!!!!!
ENOUGH IS ENOUGH!
I tried everything.  Nothing worked.
Back to Windows.
DeadToad

---

### Post by skykiller on 2007-10-25
I didn't use this HOW TO. 

I had been trying to use openSUSE a few times with no luck when it came to wireless. Even my wired Ethernet port didn't work. I have a HP zv6000 laptop.

I read that Ubuntu 7.10 was coming out so I decided to give it a try. Wireless did not work out of the box. Fortunately wired Ethernet did, so I was able to download the restricted Broadcom 43xx drivers. Wireless was able to work finally. There are issues, such as when I boot into Ubuntu, the wireless has a hard time connecting to my AP. It sees it, it just won't connect. I have to wait for it to stop trying to connect, then I get it to try to connect again and it works.

I'm a Windows guy but it's really nice to use something else for a change. With a connection to the Internet from Ubuntu now, I can find help when I need it.

---

### Post by familyjules74123 on 2007-10-25
hey, I followed your directions for GNOME

After I finished using your script, my wireless network does not even show up in the network manager anymore.  I just see my wired connection and a modem connection (inactive) and I used to see a wireless connection, but after this install that option is completely gone.

Am I doing something wrong, do I need to uninstall this somehow?  Any ideas? Otherwise I'll be reinstalling Gutsy and trying a different method.

---

### Post by brennydoogles on 2007-10-25
> **familyjules74123 said:**
> hey, I followed your directions for GNOME

After I finished using your script, my wireless network does not even show up in the network manager anymore.  I just see my wired connection and a modem connection (inactive) and I used to see a wireless connection, but after this install that option is completely gone.

Am I doing something wrong, do I need to uninstall this somehow?  Any ideas? Otherwise I'll be reinstalling Gutsy and trying a different method.

Maybe a warning should be appended in big bold letters to the first post saying that it does not work with Gutsy yet so that people don't have to read all 100 pages of the thread to find out it won't work for them.

---

### Post by cannontrodder on 2007-10-25
I agree. Once the discussion gets over 20 replies, no-one is going to read through them all.

I tried every trick in the book and this time I installed gutsy and when it asked for firmware to use with fwcutter, I used the .sys file in the windows driver package from my manufacturer and it has worked FLAWLESSLY. No more bombing out or losing my network. Wireless is now completely reliable.

```
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

---

### Post by Stoked on 2007-10-26
Hi, I used this How-to and installed the broadcom drivers and i could finally see the wireless networks but I couldn't connect.  So I installed WICD and after I did that i didn't see the networks at all anymore and I lost my Ethernet connection also.  Any ideas of what I did wrong or didn't do.

ps. I am relatively new to Ubuntu

Thanks, 
Mike

---

### Post by Student Driver on 2007-10-27
Just wanted to post that the "restricted drivers manager" worked great with my Dell Latitude D610 and the Broadcom chip in it.  I used the firmward, and just grabbed the file from the default website.  Works fine.

---

### Post by laxguy on 2007-10-27
does anyone have experience with this working on the new release, 7.10?

---

### Post by jgriffin316 on 2007-10-27
I tried it, it worked. No muss, no fuss. Thanks.

---

### Post by Wibbn on 2007-10-28
This solved it for me:) Thanks!

---

### Post by Criptonita_Y2k on 2007-10-28
My speacs
ubuntu Feisty Fawn! (64Bits)
Compac Presario V6000 (v6420us)
Broadcom 802.11 a/b/g Broadcom 802.11 b/g Broadcom [COLOR="Red"]**4321AG**[/COLOR] 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 54g MaxPerformance 802.11g


:lolflag:....This scrips is awesome.....just 2 click and thats it..my Wlan is working!!!

Thx..Dark and anyone who support this project.

:guitar:

---

### Post by ChristDude on 2007-10-29
This is very good to hear, I am getting Ubuntu 7.10 soon, and I rely on my wireless connection unless for emergencies. I just hope it works on 7.10...

---

### Post by oppo on 2007-10-29
Hi,

I have been struggling to get my wireless working on the latest Ubuntu release (7) AMD64 on my Compaq Presario V3000 (Broadcom 4311). I have followed the recommendations in many of the posts and I have tried this script but I always get the same result. My major problems are:
1. I am not sure which driver is 64bit. Some posts suggest the bcmwl5 is 32bit. Can you verify and confirm which driver I should be using. Note the compaq site does not have an spxxxx.exe with a bcmwl564.inf although the package contains a bcmwl564.sys
2. I can never get my system to show an installed wlan0...it is always eth2
I have tried using the ubuntu ndiswrapper and have also used v1.45 which i compiled from sourceforge source. I have also tried drivers from Broadcom, Dell and Compaq. I have tried the ubunto restricted 43xx firmware. 
I have never been able to find /etc/iftab file either.
I am new to linux but learning fast, but apparantly not quite fast enough it would seem.

Any tips would be greatly appreciated

---

### Post by analfabeta on 2007-10-29
My wireless is Dell Wireless&#8482; 1505 - Broadcom BCM4328 (rev 03).  Dont show in restricted drivers. Not work with bcm43xx driver and i try ndiswrapper, but doesnt work. I'll try again this night.

---

### Post by Ayuthia on 2007-10-29
> **oppo said:**
> 1. I am not sure which driver is 64bit. Some posts suggest the bcmwl5 is 32bit. Can you verify and confirm which driver I should be using. Note the compaq site does not have an spxxxx.exe with a bcmwl564.inf although the package contains a bcmwl564.sys
The .inf file only comes as bcmwl5.inf.  It looks for bcmwl564.sys if you are running 64-bit and bcmwl32.sys if you are running 32-bit.  So as long as you have both .sys files with your .inf file, NDISwrapper should be able to get it working for you.  For HP/Compaq laptops, sp33008.exe has worked well.  Some will also work with sp34152.

> **oppo said:**
> 2. I can never get my system to show an installed wlan0...it is always eth2
It generally does not matter what name it is given.  Mine has been using eth1 instead of wlan0 and has been working fine.

---

### Post by superwack on 2007-10-29
Many thanks! If only this had been the first tuturial I had read...

---

### Post by beebuntu on 2007-10-29
It's great to see a resolution of the Broadcom wireless problem.  I got tired of fighting the bcm43xx problem some time ago, and attacked the problem at it's source.

I got rid of the Broadcom Mini-PCI card in my Dell laptop, and installed an Atheros 5005 card that I bought on Ebay for about $20, + S&H.  The Atheros works great on every distribution I have tried, and Ubuntu loves it

bb

---

### Post by RetiredInMaine on 2007-10-30
Well, I  finally got tired of jerking around with Broadcom wireless under Linux. I loaded XP on the laptop. Wireless works fine. I made my grand daughter really happy by giving her the laptop and buying a Dell laptop with Ubuntu pre configured. I now have a  laptop with working wireless. My advice to anyone looking for a new laptop, DON'T BUY ONE WITH A BROADCOM wireless card.

---

### Post by Sutukh19 on 2007-10-30
I just currently reinstalled fiesty for the third time..I have a HP zv6000 with the Broadcom 4306 wireless card. My question is; How do I turn on the wireless card before continuing the How to without having the driver installed in the first place. There is no switch on the latop to turn on Wireless only a buton which will not work until the driver is loaded. 

Any help will be greatly appreciated!

---

### Post by Sutukh19 on 2007-10-30
I have the same problem right now..and still searching for a fix..I cannot even boot into the recovery mode..this sucks.

---

### Post by King_Louie on 2007-10-31
Big Big Thanks for this one! Worked like a charm. I used the Online (0.3.2) Installer for Gutsy Gibbon 7.10 on an Acer Aspire 3000. I had hammered my wireless somehow trying out KDE. Went back to Gnome and still could not get the wireless back. After hours of futile labor installing and unistalling ndiswrapper on my own and getting nowhere, this elegant script fixed everything. Thank You!

---

### Post by oodarthvader on 2007-10-31
This is a very slick way to install ndiswrapper.  I am constantly impressed at how the community keeps making things easier!  Thank you.

---

### Post by charlie_k on 2007-11-01
It worked.  Thank you!:)

---

### Post by Soglad on 2007-11-02
This got the wifi turned on, but I still can't connect.

I've tried manual and roaming mode and it just showed the two dots at the top right hand corner trying to connect. It does nothing! HELP!

---

### Post by snl2587 on 2007-11-03
I got the online installer to work with Gutsy and a Broadcom 4318. Thanks!

---

### Post by yurr on 2007-11-03
Thanks, that hepled, but only when I istalled everything on a fresh system, before doing any other operation (except configuring LAN)

It did not work first, but after I've reinstalled the whole system, and installed the software you provided I got my home wireless network working!

HP Compaq 530

---

### Post by gyst on 2007-11-03
Installed Gutsy on two Compaq Presario 710ED today. Ran into Broadcom trouble. Used the online install method, option 2 (ndis wrapper), then installed the wifi-radar, which immediately found my access point.

As a note, I needed 
[LIST]
[*]Gutsy CDROM in the tray (put it in and hit enter doesn't work, stdin is wrapped)
[*]working wired connection (using the online mode)
[/LIST]

Thanks for this, I expected a flawless Ubuntu install and got a real nasty *back to the nineties* feeling that I'd have to manually compile my own kernel, happily this click-n-script solved everything like a charm.

---

### Post by Priem on 2007-11-03
I'll admit i didn't read all the previous posts cuz there is 102 pages, but i used this and it said it worked fine, only thing is, now i don't even have the option for connecting wirelessly, just wired and dial-up. If there is a previous post could someone tell me what page or what might fix this error,

system

dell latitude 120L

broadcom 4318

---

### Post by samosamo on 2007-11-04
Any word on an offline installer for Gutsy ?

---

### Post by evilmrt on 2007-11-04
This is great! I personally think it should be added to the official distro....THANKS A TON! :)

---

### Post by ryandle on 2007-11-04
This worked flawlessly for me.  Thank you so much for creating this!

HP DV9420us Laptop with Broadcom 4312 chipset on gutsy

---

### Post by 449 on 2007-11-04
Hi, when I try to download either versions in the KDE section it gives me a 404 error. :confused:

---

### Post by DarkN00b on 2007-11-04
> **samosamo said:**
> Any word on an offline installer for Gutsy ?

Yeah. There won't be one unless bmartin can find someone to take over maintaining the scripts. [His project]("http://sourceforge.net/projects/wifix/") over at Sourceforge will replace this one when it is finished. It will be a much more fully featured installer, for just about any distro. For now, development is on hold for these scripts.

---

### Post by DarkN00b on 2007-11-04
> **449 said:**
> Hi, when I try to download either versions in the KDE section it gives me a 404 error. :confused:

That's because bmartin had to take the offline installer down because it was causing him to exceed his bandwidth. I don't really have an answer for you on that one because the file is gone and I don't have a copy. AFAIK you should be able to use the offline installer from the Gnome section, but you'll have to install it from a terminal window.

When I installed Gutsy, I had to first install the firmware from the offline installer, then get online and use the online installer to install ndiswrapper. Kinda a hassle I know but it worked for me.

EDIT: The original post has been amended to point to a working download. The files are the same, the only difference is the method of installation.

---

### Post by 449 on 2007-11-04
> **DarkN00b said:**
> That's because bmartin had to take the offline installer down because it was causing him to exceed his bandwidth. I don't really have an answer for you on that one because the file is gone and I don't have a copy. AFAIK you should be able to use the offline installer from the Gnome section, but you'll have to install it from a terminal window.

When I installed Gutsy, I had to first install the firmware from the offline installer, then get online and use the online installer to install ndiswrapper. Kinda a hassle I know but it worked for me.

Someone in another thread said there is a way to download it automatically if you have a wired connection? Do you know anything about that?

---

### Post by DarkN00b on 2007-11-04
> **449 said:**
> Someone in another thread said there is a way to download it automatically if you have a wired connection? Do you know anything about that?

Yes. You can use the Restricted Drivers Manager to install the BCM43xx firmware. I didn't want to bother, so I did it my way. Either way will work though.

---

### Post by kubel on 2007-11-06
Didn't work for me, but I couldn't get ndiswrapper to work manually either. 

DV6000Z with Broadcom 4312 on Gutsy AMD64.

---

### Post by yogiman_uk on 2007-11-06
Hi

I would love to try this Howto!  However I have a small problem.  I have a Satellite Pro A40 (Toshiba) and a Belkin 7010 PCMCIA Card.

With Fisty installed if I insert the PCMCIA card the machine locks up solid, this happens during install or if I insert the card post install.

I have tried 2 different cards, same model (both work under windows and other Linux distro's)

I have also tried gusty and no luck at all.

Anyone have any thoughts!

Thanks


yogiman!

---

### Post by csharpy on 2007-11-07
Well, this how-to has gotten me closer to the promise land than any other. However, I still cannot ping past my router. I am able to scan and find mine and a neighbors networks. I can connect to mine and ping the router (192.168.1.1). However, I cannot ping anything else including my cable companies DNS servers. I did notice when issuing the command"dhclient eth1" there is a message stating "SIOADDRT: No such process". Could this be part of my problem? Any assistance troubleshooting would be greatly appreciated. I've been struggling with this for a couple of weeks now.

Dell Precision M6
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by xSmartBombx on 2007-11-07
Thanks, this how-to worked perfect for me. 

I'm no linux noob, been running linux on my webservers since 1993 but this was my first Ubuntu install on my old laptop, a Compaq Presario R3000. Total time to getting the system up and running was about 3 hours thanks to this forum.

---

### Post by Lawke on 2007-11-07
Hi,

I'm running Ubuntu 7.10 on my Dell Inspiron 1501 with a broadcom wireless card. It all works perfect even the wireless, but i'm only getting 24mbit/sec. I don't even get a connection if I got to far away with my laptop, I didn't have this problem in windows though. Dunno if you guys know an answer for this. I hope anyone does :)

Greets

---

### Post by Kamy on 2007-11-07
Hi,

Pretty much a linux noob here but got Ubuntu working on my Sony Vaio laptop some time ago and even configured my Linksys PCMCIA wireless network card to run.

Unfortunately, I noticed there was an upgrade to 7.04 available and went for the upgrade, blowing away my connectivity.  Ubuntu still had ndiswrapper installed and saw the chipset on the card, but no matter what I did I couldn't connect to my network anymore.  So uninstalled ndiswrapper and attempted to use this app to get it working again, seems to work fine, saying the firmware should work but recommending ndiswrapper instead.  Everything seems to be going along fine until it comes to "Inserting Ndis module"  then it hangs the system, no response from anything.

I'm going to try and go the firmware route, but if that fails, where should I look to fix the problem?

Thanks,

Kamy

---

### Post by leespa on 2007-11-07
Just wanted to start saying thanks to all for a WORKING solution...

...problem I have though is that regardless of the access point I am connected to my wireless quits working after almost exactly 30 minutes....

Dell Latitude D830
installed  bcm43xx-gtk-installer-0.2.tar.gz with ndiswrapper and windows driver
Kubuntu 7.04

...symptoms are that everything looks fine, however, after approx 30 min no wireless traffic passes even though knetworkmanager shows still connected...

to reconnect I have to run:
... sudo ndiswrapper-buginfo  and reload ndiswrapper-module
... kill and restart knetworkmanager

this wouldn't be that big a deal for web-surfing but when you have VPN'd mail clients and multiple ssh sessions that hang and have to be restored its a pain in the ***...

thanks

---

### Post by Kamy on 2007-11-08
> **Kamy said:**
> Hi,

Pretty much a linux noob here but got Ubuntu working on my Sony Vaio laptop some time ago and even configured my Linksys PCMCIA wireless network card to run.

Unfortunately, I noticed there was an upgrade to 7.04 available and went for the upgrade, blowing away my connectivity.  Ubuntu still had ndiswrapper installed and saw the chipset on the card, but no matter what I did I couldn't connect to my network anymore.  So uninstalled ndiswrapper and attempted to use this app to get it working again, seems to work fine, saying the firmware should work but recommending ndiswrapper instead.  Everything seems to be going along fine until it comes to "Inserting Ndis module"  then it hangs the system, no response from anything.

I'm going to try and go the firmware route, but if that fails, where should I look to fix the problem?

Well, I tried the firmware route and no joy, ran the app again and it suggested the ndiswrapper method, tried it again and had the same problem hanging at "Inserting Ndiswrapper module"

Thanks for any help you can provide.

Karl

---

### Post by DeadToad on 2007-11-08
Kamy,
I have a 6 year old Sony Vaio laptop running Linux Ubuntu Gutsy Gibbon v7.10.
I have a D-Link DWL-G650 AirPlus XtremeG 2.4GHz Wireless PCMCIA Type II Cardbus Adapter.
Everything works fine for me, out of the box.
I have WinXP on one partition and Ubuntu v7.10 on the other.  Everything works on both OS.

You said you are using Ubuntu 7.04, that's Feisty Fawn, maybe you need to upgrade to Gutsy Gibbon v7.10.
I had no issues with 7.04 or 7.10.
Good luck.
DeadToad:)

---

### Post by Slayta on 2007-11-08
I'm having a problem that seems to be shared by others. 

When the installation gets to 

```
inserting ndiswrapper..
```

the system locks up and nothing can be done. 
[B]
Please help![/B]

---

### Post by sakid on 2007-11-08
This worked fine for me

Thanks so much

---

### Post by tashmooclam on 2007-11-08
Maybe this is a spam post, but...
The "easy" way for me was to take out the broadcom card and replace it with an Intel card for $24. It was money well spent.
Here is an article where the author mentions some wireless pcmcia cards which worked very well for him. 
[http://www.lockergnome.com/nexus/linux/category/wireless/](http://www.lockergnome.com/nexus/linux/category/wireless/)

---

### Post by Kamy on 2007-11-08
> **DeadToad said:**
> Kamy,
I have a 6 year old Sony Vaio laptop running Linux Ubuntu Gutsy Gibbon v7.10.
I have a D-Link DWL-G650 AirPlus XtremeG 2.4GHz Wireless PCMCIA Type II Cardbus Adapter.
Everything works fine for me, out of the box.
I have WinXP on one partition and Ubuntu v7.10 on the other.  Everything works on both OS.

You said you are using Ubuntu 7.04, that's Feisty Fawn, maybe you need to upgrade to Gutsy Gibbon v7.10.
I had no issues with 7.04 or 7.10.
Good luck.
DeadToad:)

Dead Toad,

Thanks for that, I'm gonna upgrad to Gutsy Gibbon now, see if it helps.  It's got to be the linux card though, I just wish I could remember how I got it working last time :(  If it doesn't come up recognizing it, I'll try running this app again and see what happens.

For what it's worth, I'm having the same issue that Slayta has posted just a couple of posts up.

Kamy

---

### Post by ser_virtual on 2007-11-08
Hi there,

I've just installed Gutst on a Dell 1501 with a 4311 Broadcom wireless card. Since the Restricted Driver Manager did let me enable the Broadcom firmware I tried the method in

[http://ubuntu1501.blogspot.com/2007/05/another-way-to-get-wi-fi-on-dell-1501.html]("http://ubuntu1501.blogspot.com/2007/05/another-way-to-get-wi-fi-on-dell-1501.html")

that has been reperted to work on Feisty. I first did
[COLOR="Sienna"]
Get the deb package
wget [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)

Install the firmware files
sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb

Remove the package
sudo rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb

Download the module for the 32 bit kernel
wget [http://linux-geek.org/files/bcm43xx.tar.bz2](http://linux-geek.org/files/bcm43xx.tar.bz2)
or get it here: [http://www.mediafire.com/?8mnjnsxubdn](http://www.mediafire.com/?8mnjnsxubdn)


Replace the bcm43xx driver provided by the Ubuntu kernel with the driver ported by Cosmin, from the 2.6.21-rc7 kernel
sudo rm /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

sudo tar xvjf ./bcm43xx.tar.bz2 -C /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/[/COLOR]

but when replacing the driver provided by Cosmin the card desapeared from the Network Administration Tool at System>Administration>Network so that I copied the original driver again. As a result, I got the interface recognized and it even sees the wirelles networks sorrounding. However, I do not know how to get connected at all.
When I click the Network Manager Icon and "Activate" the conecction nothing apparently happens. How to know whether or not I'm online? Firefox just does not connect. Sorry, I a newbie.

Any idea? Thanks
I don't have other form to connect from Ubuntu since I haven't had succes with  the dial up as well.

---

### Post by nu2lnx on 2007-11-08
Not sure if this helps, but [COLOR="Red"][[COLOR="Red"]this link[/COLOR]]("http://www.linuxquestions.org/questions/ubuntu-63/enabled-bcm4306-using-bcm43xx-fwcutter-516734/")[/COLOR] allowed me to get a Broadcom 4306 working near flawlessly on my Dell Latitude D600.

I am a n00b and just followed the instructions verbatim and lo and behold - my wifi works.

---

### Post by DarkN00b on 2007-11-09
NDISwrapper v1.48 doesn't seem to want to play well with Gutsy sometimes. At this time there is no fix that I know of. I can't reproduce the errors some of you are getting so I can't really troubleshoot the problem. Sorry. :(

---

### Post by Kamy on 2007-11-09
> **DeadToad said:**
> You said you are using Ubuntu 7.04, that's Feisty Fawn, maybe you need to upgrade to Gutsy Gibbon v7.10.
I had no issues with 7.04 or 7.10.
Good luck.
DeadToad:)

Thanks DeadToad, Gutsy Gibbon worked for me :)  Picked up the card as soon as it  rebooted after install  :)

Kamy

---

### Post by drinkmocha on 2007-11-11
Tried this three times after having to reinstall ubuntu in each try and unfortunately, still wouldn't work :(

I have Dell Vostro 1500 with this wireless card:

Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card


Any other ideas? I'm almost giving up making my wireless work. Thanks in advance!

---

### Post by diego1188 on 2007-11-11
THANK YOU! Worked perfectly for a Broadcom 4318 card on Acer Aspire 3630 laptop. It's kind of magic!!!:biggrin:
Thank you again and again!

---

### Post by Huntington Coal Miner on 2007-11-11
I am using Gutsy Gibbon 7.1 and the online download worked for me.  After I rebooted, I had to go into the wireless network configuration and enter your network name and set my configuration to DHCP.  You can enable roaming to find the network name first if you don't know the name.

---

### Post by padre44 on 2007-11-11
Didn't work for me - computer locked up when trying to install.:confused:

---

### Post by whaa on 2007-11-14
Hi

I have a HPdv6187eu and I'm using 7.10 so I could not even try.

I've activated the restricted driver for Broadcom, chose to download the firmware from the Internet. It says it is in use.

No luck getting the wireless work.

Then I tried ndiswrapper. Installed v1.49 manually and installed bcmwl5.inf

No luck again.

My iwconfig looks like this:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
and my ifconfig like this:

> 
eth0      Link encap:Ethernet  HWaddr 00:1B:24:95:2C:18  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe95:2c18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66014249 (62.9 MB)  TX bytes:4458733 (4.2 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Anyone who can help?

---

### Post by devindakid on 2007-11-15
I am pretty new to ubuntu and i am trying to get the wireless working on my averatec laptop and i have done everything said but when i click run a box comes up saying null....

bash: ./stats-logger: No such file or directory

any help would be great thanks

---

### Post by Ryadovoy on 2007-11-16
thanks this helped me a lot

---

### Post by infamousjre on 2007-11-16
> **Slayta said:**
> I'm having a problem that seems to be shared by others. 

When the installation gets to 

```
inserting ndiswrapper..
```

the system locks up and nothing can be done. 
[B]
Please help![/B]

I'm getting this too. The sad thing is, I had my wireless working perfectly last night but i tried messing with compiz and for some reason I lost my wireless card and my desktop cube (still got the jiggle for some reason).:confused:

Nevermind. The offline installer worked wonders. Got on my wireless network and then used this HOWTO to get on the internet: [http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

---

### Post by wsx123 on 2007-11-16
How do you undo this/remove this  after an online install?

---

### Post by DarkN00b on 2007-11-16
> **devindakid said:**
> I am pretty new to ubuntu and i am trying to get the wireless working on my averatec laptop and i have done everything said but when i click run a box comes up saying null....

bash: ./stats-logger: No such file or directory

any help would be great thanks

This might sound like a silly question, but did you extract the .tar.gz file first?

To uninstall:

If you used the firmware, re-run the installer and choose the uninstall option. If you used NDISwrapper, then uninstall ndiswrapper from Synaptic.

---

### Post by wsx123 on 2007-11-16
I wish I could get this to work rather than remove. If I restart my laptop I have a 50/50 chance that the firmware remains installed.
I had my Bcm 4306 card working before this with the default  7.10 drivers and fwcutter. I saw this and thought my speed would improve but both ways give 24 Mb/s.

---

### Post by drawkcab on 2007-11-17
I'm posting this on a **_live cd _**of PCLinuxOS 2007 (Gnome Remix). 

[http://www.linuxgator.org/Gnome/gnome_page/gnome.html](http://www.linuxgator.org/Gnome/gnome_page/gnome.html)

I know that broadcom is partly to blame for not releasing Linux drivers. * But even so, if this live cd is working with my broadcom card, why doesn't Ubuntu work with it?*:confused:

My broadcom card and Feisty got along OK (not great), until the last few updates.  Now it won't work with Gutsy at all.   Doesn't seem like a bug, but rather a systematic problem that no one knows what to do with.  And I don't want to spend my days experimenting with howtos that never seem to work.  It's been a month and I think I've been patient enough.   

Time to give PCLinuxOS, Mepis (which works with my card when installed) or the pile of other distros I just downloaded a shot.  Maybe I'll try ubuntu again in April.  But if PCLinuxOS develops an official Gnome branch before then, I may just stick with them.

So I guess what I'm saying is that this is dealbreaker.  Too bad, I've been using x/ubuntu for two years.:(

Good luck to everyone working on this problem.  I hope everything comes together in time for the next LTS distro.

---

### Post by CrinkElite on 2007-11-18
thanks dudes i was beginning to think i would have to buy a new card or go back to windows. thanks to you guys i can now move my computer back to its rightful position in my room.
excellent work!

---

### Post by zhespelt on 2007-11-18
I'm setting up a new laptop for a family member and I've run into a problem with the built in wireless card.  I tried the installer from this post...didn't seem to work, did a fresh install and tried again, still nothing.  I use a Dlink card for my laptop and it works out of the box.  I don't have access to a direct cable connection right now, but I'm able to access my network using the Dlink card on this new laptop.  Is the problem that I'm using a PCI wifi card to run the online setup for the built in card?

Compaq Presario R3000
Ubuntu 7.10 Gusty

:(

---

### Post by drawkcab on 2007-11-18
My wireless works fine in LInux Mint.  Go figure.

---

### Post by Sawman on 2007-11-19
Yeeeehhhhaaaaaaa !!!
Finally after 2 1/2 days of trying, I finally got my Broadcom card working.
HP DV5003cl
Ubuntu Studio 7.10
Broadcom BCM4318
I used fwcutter with the driver [wl_apsta-3.130.20.0.o']("http://linuxwireless.org/en/users/Drivers/b43").
Followed the directions on that page and she works like a charm.

Hope this helps someone.

---

### Post by mattchess on 2007-11-20
My Dell M1210 has a Dell wireless card ( Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)), and this worked flawlessly in under 5 minutes.  Thank you very much! :-)

---

### Post by zeller on 2007-11-21
Nothing in this thread has worked for me.

Broadcom 4318.

---

### Post by gyst on 2007-11-23
This script doesn't work anymore, since ndiswrapper-newest.tar.gz is missing on it's googlepages URL. You can work around this as follows:

download the latest stable ndiswraper sources from [http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482")

rename the tarball to ndiswrapper-newest.tar.gz

edit the script bcm43xx-0.3.2-internet/bcm43xx-ndiswrapper.sh

- comment out the line: 
$ASUSER $WGET http://blakecmartin.googlepages.com/$TAR > /dev/null 2> /dev/null

- insert instead the following line:
$ASUSER cp /home/yournamehere/$TAR .

And make sure to replace the "/home/yournamehere" part with the actual path to the downloaded ndiswrapper tarball.

Now you can run bcm43xx-ndiswrapper.sh as root and everything works like it should.

---

### Post by blackfly on 2007-11-23
Ok, so Im able to install the broadcom 4318 wireless card using the restricted drivers manager in Gutsy.

Im not up to par on my knowledge in the wireless networks department, so I was wondering about the strength and flexibility of joining networks with linux.

1. The signal is not as strong as in vista, so would that effect me in any way?
2. What about certain routers or hubs?  Is Gutsy incompatible with any?
3. How about encrypted or password protected networks, do I have to do anything else to be able to connect with them?

Thanks and cheers,

Josh

---

### Post by emotional1 on 2007-11-23
I am going to try a clean install

---

### Post by emotional1 on 2007-11-23
I re-installed the OS Gutsy 7.10 and used ndiswrapper with doze drivers.  I appreciate the hard work that went into creating this 'broadcom easy' script and forum.  I however would have appreciated a *uck-off, not enough information, or response of any kind. I have the HP TX1220us(tx1000) AMD Turion 64 Broadcom 4328 rev3.  I used the generic 2..6.22-14-generic kernel with the latest ndiswrapper 1.49, with the broadcom all 64-bit drivers from the Linuxant site.  Wireless is working.
Eric

---

### Post by vjktm on 2007-11-24
Hi,
was happy to find these instructions and script.  I have a 4318 based card by Dynex, black friday purchase.  It did not work for me for some reason.  I am attaching the install log, I can't deduce what to fix.  Installation of WICD did not work either, but the network-manager got uninstalled.

Also,
Is there a preferred brand/chipset that works "out of the box"?  I might just return the one I have and get that does not require additional installs etc.

I have Fiesty on a Toshiba Satellite, dual boot, but hoping to get rid of Windows.  Still can't because I have not been able to make various devices work.

Anyhow thanks of the great support on these forums.

vjktm

---

### Post by brennydoogles on 2007-11-24
> **vjktm said:**
> Hi,
was happy to find these instructions and script.  I have a 4318 based card by Dynex, black friday purchase.  It did not work for me for some reason.  I am attaching the install log, I can't deduce what to fix.  Installation of WICD did not work either, but the network-manager got uninstalled.

Also,
Is there a preferred brand/chipset that works "out of the box"?  I might just return the one I have and get that does not require additional installs etc.

I have Fiesty on a Toshiba Satellite, dual boot, but hoping to get rid of Windows.  Still can't because I have not been able to make various devices work.

Anyhow thanks of the great support on these forums.

vjktm

I have found that cards with an intel chipset work with a restricted driver very well. As long as you have feisty or above, it will be a breeze to install!

---

### Post by ralphie82m on 2007-11-25
Salutations to the entire ubuntu community! 
I've been visiting these forms for the past week and thanks to the help of this thread and many others I finally got my Broadcom 43xx based wireless card working with Gusty Gibbon. It took me so long because I rarely have extra time due to work. 

Although my wireless card is now working, the problem that I have now is that I must be within a 15 feet radius from my netgear router. 

When I boot with xp I'm able to go about 50 feet.

Does anyone one know what can be causing this?

I tried switching my router to a different channel but I doubt the problem lies with that. 

Any and all comments would be appreciated. Thanks for the support guys, I feel honored to be part of this community.

:lolflag:

---

### Post by frekimedia on 2007-11-25
I just wanted to say that I had submitted to having to use XP on my laptop (Dell Latitude D400) because I couldn't figure out what was wrong with my wireless until I read this. Fixed it in a jiff. Thanks.:guitar:

PS: BTW, this fix gave me NO issues whatsoever. I can roam wherever in my house and get a good signal, I even get most of the neighbor's signals with pretty good strength as well.

---

### Post by BrandonD92 on 2007-11-26
how did you get it to work?

---

### Post by aser7412 on 2007-11-27
[COLOR="Blue"]thank you v.much[/COLOR]

---

### Post by marzshadow on 2007-11-28
Got it working.  Thanks for the how-to.
Gutzy with a Broadcomm 4308 on a Dell Latitude D610.
First try was with the firmware and it worked on open systems, But not WPA2.
I used the python tool you wrote to uninstall the firmware and to install the ndiswrapper version.  After a reboot, WPA2 works too!

Thanks for an excellent tool.

--Mark

---

### Post by yomeh on 2007-11-28
works perfectly thanks very much

---

### Post by exquest on 2007-12-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/163703](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/163703) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				it worked!  Thank you for this solution.

---

### Post by sanketmedhi on 2007-12-01
Hi,

I am using Ubuntu Gutsy Gibbon 7.10 x86_64 on my HP Pavillion dv9000 entertainment laptop. It has a Broadcom 4328 wireless adapter.

$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I have successfully installed drivers for the card, the wireless indicator on my laptop glows. I see wireless connections available around me including my home connection, 2WIRE388. I tried selecting my connection using the Network Administrator, then entering my key, and Configuration to DHCP. See image:

[[IMG]http://img214.imageshack.us/img214/6716/screenshotwlan0propertijd5.th.png[/IMG]](http://img214.imageshack.us/my.php?image=screenshotwlan0propertijd5.png)

After all this, I am still not able to connect to the Internet. 

iwconfig shows:

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"2WIRE388"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Someone please help me with this problem. Thanks in advance.

---

### Post by mssever on 2007-12-01
> **DarkN00b said:**
> -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
These lines of hyphens on the initial post make the post nearly impossible to read. They stretch the post container too widely because there's no white space in the lines and so the browser renders the text to fill the now-stretched container. Perhaps the attached screenshot can illustrate this better than I can describe it.

---

### Post by hkgonra on 2007-12-03
Thanks, worked great.

---

### Post by mikessktr on 2007-12-03
i just upgraded to 7.10 My wireless was working on the feisty fawn version and now it doesn't. i can "see" the wireless but it tells me it's disabled. it could be my lack of sufficient knowledge of Ubuntu settings, i tried to reinstall the driver like i did on the previous Ubuntu version but i still got the same results. is there a way to "enable" the wireless? :confused:  I'm kind of stuck using my crappy *** windows until i can get it fixed. can any one HELP?

---

### Post by DarkN00b on 2007-12-04
> **mssever said:**
> These lines of hyphens on the initial post make the post nearly impossible to read. They stretch the post container too widely because there's no white space in the lines and so the browser renders the text to fill the now-stretched container. Perhaps the attached screenshot can illustrate this better than I can describe it.

Odd. It doesn't stretch at all on my screen (1024x768 ). Are you running a lesser resolution or perhaps larger fonts? 

For those having connection problems, are you using the WICD connection manager? It often works better than Network Manager especially if you can see your wireless connection but can't connect to it. You can install it with the installer. Installing WICD will uninstall network manager though.

---

### Post by mssever on 2007-12-05
> **DarkN00b said:**
> Odd. It doesn't stretch at all on my screen (1024x768 ). Are you running a lesser resolution or perhaps larger fonts?
I'm running 1024x768 as well, with Ubuntu's default fonts. I'm running Firefox on Gutsy. That's odd that you and I are seeing different things. Unless maybe you're not running Firefox.

By the way, I noticed that you're in East Texas. Me too (Linden).

---

### Post by Benchrest on 2007-12-06
I was referred to this site by another user who used this process successfully with an identical laptop. I have tried Feisty due to problems reported with Gutsy on HP and the Gutsy and now back to Feisty. I am getting to be an expert on installation and graphics:)

I have an HP DV6646US with Nvidia Geforce Go 7150M graphics and Broadcom BCM4328 wireless. Both have given me fits. 

Wireless switch is on and works in vista.

My process was to install Feisty from Alternate CD dual boot, Then I installed 166 updates. Had problems with Envy if I ran it before the updates. Then I installed Envy via [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ,  rebooted and graphics worked.

Then I performed the six steps of this thread. Step 4 unable to detect broadcom chipset. Selects "install ndiswrapper and broadcom windows driver"  All steps appeared to go correctly. But wireless doesn't work. Light is amber instead of blue as under vista.  Network Manager only shows Wired Connection and Modem Connection.   

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth1
       version: a2
       serial: 00:00:6c:dd:f0:f6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=192.168.1.111 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: iomemory:f2588000-f2588fff ioport:30f8-30ff iomemory:f2589c00-f2589cff iomemory:f2589800-f258980f irq:17
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 03
       width: 64 bitsmes
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:f2200000-f2203fff iomemory:f2000000-f20fffff irq:10

Notice the wireless card shows Unclaimed and has no logical id.

 ifconfig -v
eth1      Link encap:Ethernet  HWaddr 00:00:6C:DD:F0:F6  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fedd:f0f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1071774 (1.0 MiB)  TX bytes:320577 (313.0 KiB)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

Wireless doesn't show up in IFCONFIG

 iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

Any suggestions? Thankyou Rich

---

### Post by DarkN00b on 2007-12-06
> **mssever said:**
> I'm running 1024x768 as well, with Ubuntu's default fonts. I'm running Firefox on Gutsy. That's odd that you and I are seeing different things. Unless maybe you're not running Firefox.

By the way, I noticed that you're in East Texas. Me too (Linden).

I'm from Apple Springs (near Lufkin). I'm running Firefox by the way, with everything set to defaults.

> **Benchrest said:**
> I was referred to this site by another user who used this process successfully with an identical laptop. I have tried Feisty due to problems reported with Gutsy on HP and the Gutsy and now back to Feisty. I am getting to be an expert on installation and graphics:)

I have an HP DV6646US with Nvidia Geforce Go 7150M graphics and Broadcom BCM4328 wireless. Both have given me fits. 

Wireless switch is on and works in vista.

My process was to install Feisty from Alternate CD dual boot, Then I installed 166 updates. Had problems with Envy if I ran it before the updates. Then I installed Envy via [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ,  rebooted and graphics worked.

Then I performed the six steps of this thread. Step 4 unable to detect broadcom chipset. Selects "install ndiswrapper and broadcom windows driver"  All steps appeared to go correctly. But wireless doesn't work. Light is amber instead of blue as under vista.  Network Manager only shows Wired Connection and Modem Connection.   

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth1
       version: a2
       serial: 00:00:6c:dd:f0:f6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=192.168.1.111 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: iomemory:f2588000-f2588fff ioport:30f8-30ff iomemory:f2589c00-f2589cff iomemory:f2589800-f258980f irq:17
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 03
       width: 64 bitsmes
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:f2200000-f2203fff iomemory:f2000000-f20fffff irq:10

Notice the wireless card shows Unclaimed and has no logical id.

 ifconfig -v
eth1      Link encap:Ethernet  HWaddr 00:00:6C:DD:F0:F6  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fedd:f0f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1071774 (1.0 MiB)  TX bytes:320577 (313.0 KiB)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

Wireless doesn't show up in IFCONFIG

 iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

Any suggestions? Thankyou Rich

I notice that the Broadcom card is a PCMCIA card. Are you starting up the machine with the card already inserted? That makes a difference with mine. For some reason if I plug it in after Ubuntu is running, it is detected but won't connect or detect any network.

---

### Post by Benchrest on 2007-12-06
No it is a PCI as far as I know. It is built in. It will work in vista, then do a restart without changing anything and it doesn't work when Feisty comes up. I tried several other methods also when I originally installed feisty and with Gutsy and all give the same, appear to install ok , no errors, but doesn't work.

---

### Post by mike552 on 2007-12-06
Noob here,

It kinda worked for me... really slowly... 130kbps when I ran it on the CNET online speed test.
I tried to install WCID, but all it did was remove the WIFI and nothing else. Things don't work now... not even the ethernet card connection.
I perhaps thought that the ndiswrapper was conflicting with the 43xx driver... hmm... who knows. 

I have been at this for days, and as a total f'n newbie who wishes he had the skill to stay on Ubuntu, I will probably be going back to depressing XP. Depressing.

EDIT: In case it matters, specs: Ubuntu 7.10, BCM4306, Dell Latitude x300.

2ND EDIT: It's been 8 hours since my last edit, and I busted out my XP install cd only to see that my computer would not boot from it... it went straight to Ubuntu. My boot order was set for cd to boot first... strange...this happened twice. I was going to try it a third time, but realized that MY INTERNET IS UP AND RUNNING AGAIN!!!!  I don't know what I did or what happened, but my laptop is trying to tell me something!!

Yes, the internet connection speed is moody, that is, it's sometimes lightning fast and at other times slow as hell, mostly slow as hell though. Either way, I am happy with this temporary compromise. I used the search function on this site to find out that there are many ways to tackle this problem... I will try to strengthen my connection any way I can, but for now, this is really great!!! 

Thanks darknoob and martin and all of the guys who took the time...

---

### Post by re2st on 2007-12-08
HELP!!!!

I got the wireless thing on (the light is blue and all), but I still can't see any Network (while I can on my Windows PC).

I'm using Compaq Presario V6500Z,

lspci gives me this:
```
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```

lspci -n gives me this:
```
03:00.0 0280: 14e4:4311 (rev 02)
```

Network Manager Applet shows "Wireless Network" but nothing underneath it.

iwconfig eth1 gives me this:
```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

when i tried sudo iwlist eth1 scanning, it gives me this:
```
eth1      No scan results
```

I installed the bcm43xx driver using Restricted Driver Manager and have tried both the provide URL (the .de domain URL) and downloading the wl_apsta file from Wiki).

what gives/ I can't figure out what's wrong.

I literally am screaming for HELP now.. :((

---

### Post by Benchrest on 2007-12-08
I sorta got mine working last night. I regrouped and reinstalled Feisty from the Alternate CD as before. Then downloaded 167 updates. Proceeded to section one the 6 steps. At the end my blue light came on:) I then rebooted and still the blue light. Started the Network manager and it showed 3 items, wireless, wired and dialup. It showed 2 networks, mine and my neighbors. Now I need to setup WEP 128 bit security. Thanks for this post. Why it didn't work the first time I tried I don't know.
Rich

---

### Post by jrela2000 on 2007-12-09
Gateway MT6451 check!:guitar:

---

### Post by jrela2000 on 2007-12-09
Actually I have a small issue now. I actually have to reinstall the package every other time I have to reboot.  How do I fix?

---

### Post by JCSalomon on 2007-12-11
&#8195;I’m running a fresh install of Ubuntu 7.10 with a 2.6.22-14-generic kernel; the script tells me, “Your kernel is not supported by the offline ndiswrapper installer.…”&#8194;Then it proceeds to install the firmware anyway.
&#8195;I reboot, get a message about “restricted drivers”, and try to connect to the wireless network in my house—still unsuccessfully.
&#8195;As far as system info is concerend, lspci reports:
&#8195;&#8195;[FONT="Courier New"]02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/FONT]
&#8195;Anyone have suggestions for me?
—Joel

---

### Post by DarkN00b on 2007-12-12
The installer is no longer being developed, and is out of date. If you really want to use it, you can install the firmware (or the restricted drivers) to get online then run the installer again and install ndiswrapper. It still is an easy way to install ndiswrapper + drivers once you are online.

I'm sorry so many are having problems, but bmartin was maintaining the installer and has now moved on to another project. I don't know the first thing about Python or I would do it myself.

---

### Post by JCSalomon on 2007-12-12
> **DarkN00b said:**
> The installer is no longer being developed, and is out of date.&#8195;That confirms my decision to buy a new, out-of-the-box Linux-compatible, WiFi card.&#8194;Thanks.
—Joel

---

### Post by sbussy89 on 2007-12-13
Did the GNOME steps and it said it installed but when I reboot and try to configure manually there is no wireless option... ne help?

---

### Post by din on 2007-12-13
Fantastic guide! It work for me in 5 minutes.
I wonder, why i didnt started with this thread 3 days ago... 

THANKS!!!

---

### Post by sbussy89 on 2007-12-13
still not working here... no blue light, no wireless option in the manual configuration window... I looked for the wireless option right after install and after reboot but neither worked... any help???

---

### Post by Anpanman on 2007-12-14
Tried the online first but the command window hung.

Then tried offline, got a message that my kernel wasn't supported but the installed still carried on.

Took it's advice and now it seems to be working fine - great!

The only difference is that the led on my network card which should normally be unlit when not receiving/sending is permanently lit.
It them flashes normally when it is receiving or sending information.

I'm not complaining though.

Thanks very much.

---

### Post by miesnerd on 2007-12-14
installing the firmware works really well for me, and works immediately. Only caveat is that the settings dont seem to save themselves.
Every time I restart my laptop, I have to use the offline program over and over to re-install the firmware to coax it to work. 
Anyone know a command I can paste into the terminal that saves the settings?

Thanks bmartin for making this.

---

### Post by neoroses on 2007-12-15
exactly what ubuntu has been missing.....this is the way forward

---

### Post by lester8284 on 2007-12-16
I have a gateway laptop with (fiesty) and i am completely new to linux.

 I followed your instructions to get my broadcom card to work, when i restarted my computer my 'wireless internet connection' was gone in my 'network configuration' window and my computer still wont connect with my wireless card, i tried making it work with the wired connection but it doesnt seem to work either.

Im not sure if I am doing something wrong or if its the computer, but ANY help would be great! This has been giving me a head ache for 5 days now.

---

### Post by cool2000m on 2007-12-16
I followed these instructions, and they worked like a charm. however, wicd says that I'm connected when I'm not, and it even has a signal strength.

---

### Post by yxvaan on 2007-12-17
Yesterday, I tried the online installer on my new iMac on which I have an amd64 version of Gutsy. The iMac has a BCM4328 chipset of Broadcom Corporation, for which the online installer recommends Ndiswrapper. After some initial hickups the installation seemed to have succeeded; at least the installer claimed that the installation was complete. However, there was still no trace of a working wireless connection. 

Today, I have been digging into the scripts provided by the installer when trying to figure out what happened. In my case that means mainly the bcm43xx-ndiswrapper.sh. I subsequently found out that the address from where the sript should download the new ndiswrapper package doesn't seem to be correct. When trying it, "http://blakecmartin.googlepages.com/ndiswrapper-newest.tar.gz", out, the wget command complains "No such file or directory" and the browser chimes in with the familiar "The page you have requested could not be found. (404)". It seems that the file in question has been removed into a new location but the change hasn't been updated into the script. Could it be possibe for the maintainers of the installer to check out this problem and do something to it? As this tool seems to be wildly popular and mostly succesful, it would be a shame to leave this kind of a bug in it.

I also noticed that the error handling of this script (and probably of the others of the installer, as well) leaves a lot to be desired. The script plods on until the end no matter what happens. In my case, it messed up a couple of configuration files and loaded the nonexistant ndiswrapper module into the kernel. Fortunately, nothing went really broke, but trying to figure out what happened and why has been quite a job and certainly not anything a linux novice would be up to. I do appreciate the initiative and effort put into this installer and other similar tools provided by Ubuntu users but _please_ make an extra effort with the error handling and logging! They make such a difference in preventing disasters to happen and sorting out what went right and what wrong. 

In the meantime, I think I'm going to try out the ndiswrapper package provided by Ubuntu, even if its version lags a little behind. And if someone already happens to know how to make the iMac wireless work in ubuntu, please tell me, too.

---

### Post by l33t-sauce on 2007-12-17
This worked like a charm. Thanks alot for making that installer. You have no idea how many times i've spent hours trying to get the wireless working on this dell and it's weird wireless card. You have made my day. Thanks again.

---

### Post by Zelix on 2007-12-17
Im really new to linux so if this sounds easy or strange please bare with me.  i just finnished installing gutsy on my other desktop.  i have a PCI card with a bcm4303 chipset.  when i first started working on my wireless net it showed up in network settings.  and now its not there anymore.  heres exactly what i did.

since i have the net wired to the system for now i used the online installer.  \

i downloaded the installer directly to the desktop.  (downloading to the desktop makes things easier for me since i dont quite understand the file system just yet.)  im afraid this is where i went wrong because with i extracted the file it extracted to the desktop as well.  

i opened the installer.py and selected the "install BCM43xx firmware"

it finnished, i rebooted the system.  

the restricted drivers automatically turned on but the wireless is no longer in the network settings.

ive tried removing the firmware, also tried reinstalling it.  

now this is where i am.  lost and dont know what to do.

can anyone help me.

---

### Post by tinglew on 2007-12-17
Just to let everyone know, the solution listed below worked for me, I have the following hardware/software;

Dell Latitude D505
Broadcom 4309 wireless card
Ubuntu 7.10
I should add that it was Dell Wireless 1450 WLAN Mini-PCI Card too...

It was a lot of typing but at least my wireless works now...

Original message on page 51, plus links to another message.....

Warren


> **rockballad said:**
> Hi all,

I'm replying to you all on the wireless network. Here're something I'd like to sum up for one who's beginning to setup wireless with:

[LIST]
[*]Compaq Presario V6000Z
[*]Dell Wireless 1390 WLAN Mini-PCI Card 
[*]Broadcom 4311
[*]Ubuntu 7.04
[/LIST]

You'll need:

Option 1: using bmartin's script on this thread. ndiswrapper is hightly recommended. Thanks bmartin and DarkN00b for your big help.

Option 2: download driver and install manually, hereafter are the good links:
[LIST=1]
[*]Download the RIGHT driver for the notebook at [http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE)
[*]Download the ndiswrapper at [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz) Current version is 1.47. You can check at sourceforge.net for the lastest one.
[*]Follow exactly the first post at [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[/LIST]

OK. Now you can test the wireless network: 
```
sudo iwlist scanning
```

If you see one or more Cell, you got the target!

The last step, you can use wicd or wifi-radar as many people have done well. But for my part, I have to use gnome network manager. Get it like this:
Install:
```
 sudo apt-get install network-manager-gnome
```
then 
```
 nm-applet --sm-disable
```

Done. You now can see the network manager on the system tray. Select the wireless network, enter password and enjoy yourself!

Have fun!

Thanks you all so much!

Cheers,

---

### Post by gfd_2 on 2007-12-17
sorry, didn't work on a brand new HP 6633us. 

sigh... on to the next solution...

---

### Post by Catroast on 2007-12-18
Yeah, not working for me. This has really been frustrating. Almost nightmarish.
I extracted it, ran it, did what it said, and I don't even see wireless in the Network Manager. After restart, as well. I'm just too noobly to try and figure this out the rest of the way.

Thanks for the script writing, et al.

---

### Post by Catroast on 2007-12-18
Ok, here was my solution: dump the Linksys wireless card and get a Netgear with different drivers, etc. It didn't exactly work like a charm, but I finally figured out how to configure the security, since the Linksys wireless router has slightly different names for things than what the ndis-Gui-thingy says.

---

### Post by Pvt_Joker on 2007-12-19
THANKZ!!!!

You rock!!!

:guitar:


This works on a HP DV9000 Laptop with Kubuntu Gutsy Gibbon.  Just head to page one and follow the steps.

-PJ

---

### Post by miesnerd on 2007-12-19
not to dissuade anyone from using ubuntu, but in the course of installing many distros on my laptop I found out that Sabayon 3.4e works automatically with my card.  Just an FYI. If you prefer debian (as i do) its just one solution.

---

### Post by Sadaiyappan on 2007-12-19
Hi this guide didn't work for me.  I have a Dell Inspiron E1505 laptop and this is the card I have : 0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01).

Can anyone help me?  Not only did this "Easy" way not work for me but I tried a guide for E1505 and that didn't work right either.

Someone please help with this problem I would really like wireless on Ubuntu.

Thanks.

---

### Post by keithclark on 2007-12-20
I also have a broadcom card that works with pclos, but not with Ubuntu (by default on both).

Is there not an easy way to get it working with the same drivers that pclos uses?  These other ideas seem fine after installation, but not to run from the live cd just to try out ubuntu.

If not, I can always stick to PCLinuxOS.  Not a big deal.

Keith

---

### Post by DarkN00b on 2007-12-20
As stated in the original post, this method is outdated and may or may not work for any given user. Bmartin may have removed some of the files needed by the scripts from his Google account. If so then this method may not work anymore.

---

### Post by dhl on 2007-12-21
Hello,
Tried this solution but still no Wireless connection option and no wlan0 in ifconfig inspite of the successful installation of bcm43xx installer (ndiswrapper and win driver). Previously tried installing a broadcom driver manualy ( [http://ubuntuforums.org/showthread.php?p=3990600#post3990600](http://ubuntuforums.org/showthread.php?p=3990600#post3990600) )

<Hello,
I am trying to use a wlan card based on a broadcom BCH4318 chip under Ubuntu 10.7. During install I have been following the instructions from here: [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)
The bcmwl5.inf driver was successfully installed using ndiswrapper's ndisgtk. Note: lspci shows the wlan ID as 14e4:4318, here: [http://ndiswrapper.sourceforge.net/j...,33/id,list_b/](http://ndiswrapper.sourceforge.net/j...,33/id,list_b/) this ID is referenced to bcmwl5.sys and netg54s.inf drivers; bcmwl5.sys was present in my CD package, but I couldn't install it, while installing netg54s.inf in ndisgtk returned "Invalid driver!". So I have downloaded the bcmwl5.INF.
But unfortunately there is still no wlan0 in ifconfig and no Wireless connection in Network utility.... What caould be the solutions to this problem?>

What do you think?
Thank you in advance.

P.S. There actually WAS "Wireless connection" option before I blacklisted the default bcm43xx, but it was not working...

---

### Post by cloud-dew on 2007-12-22
THx what a great christmas present!

I got my GF a lappy which had an unsupported wireless, my step son bought this broadcom  (glup) but thanks to this thread it works!

well done to  all  the coders out there ( i can just about code simple C or complex VB [yeah i know its not reall coding ;)] )

anyway thanks all & DArknoob for posting this :D

---

### Post by StrangeBrew on 2007-12-24
The only problem I had was I couldn't get it to install in a different directory.  Other than that it works great.

---

### Post by derekr44 on 2007-12-25
I've got my wireless drivers loaded (Netgear MA-111 USB v1.0) and recognized by ndisgtk.

However, it sees the network connection as wired, not wireless.  Ideas?

---

### Post by MadEarThInk on 2007-12-26
re2st,

I don't know if you've figured this out yet or not, but I was having the same infuriating problem.  How I fixed it was by using ndiswrapper, I'm sure you've seen a million howto's for it.

But the crux was this...In my boot options for some reason the kernel update added the option "pci=noacpi" when I switched this to "noapic" everything worked.

---

### Post by theartofbone on 2007-12-28
This howto worked for me. I am using a Gateway MX6440 laptop that came with a Broadcom 4318 chipset. It is my second day using linux and I find it extremely frustrating and difficult but yet satisfying! It seems so powerful. 

Anyway, using Gutsy Gibbon or whatnot, 7.10 and the Online automated installer provided by the coder's friend worked. They said the offline installation didn't work at all with 7.10,and that the online might or might not work. I want to report to all who doubt, the online installer worked for me, under Gnome... and I am completely new to this. 

One thing to note, the program said my chipset was incompatible, so it automatically selected the option that said install ndiswrapper/download driver and so it did. Upon reboot, wala, WLan working! :D

Long live Ubuntu.

---

### Post by annasparklestar on 2007-12-28
Hi 

I am very new to this.  I was getting the message "the software source for the package bcm43xx-fwcutter is not enabled" and used the online version to fix this.  I have now got the firmware enabled.  However, the wireless option has now disappeared completely!  (It was there before but with no signal bars).

Does anyone have any suggestions for what I do now?  Any help much appreciated.

Thanks

Anna

---

### Post by theartofbone on 2007-12-28
Anna, try going to SYSTEM --> Preferences --> Network, and make sure your eth1 (assuming eth0 is your LAN) is enabled. This had happened to me once and clicking on the checkmark and typing in the appropriate SSID solved the issue.

Goodluck. Keep on posting.

---

### Post by Pvt_Joker on 2007-12-29
derekr44 ,

In response to seeing the wired and not the wireless connection... check your settings under System Settings make sure that your wlan0 is enabled.  I had to enable mine.  I'm in Kubuntu tho, so my settings are a bit different.

Also try to get the Wicd program, if you haven't already.  Sometimes after boot up, when I pull up Wicd , I have to click "Refresh" to see the wireless networks.

-PJ

---

### Post by annasparklestar on 2007-12-29
I tried this - there is no option for wireless - just Wired connection and Modem connection.  I can't see a way to add one.  I can't see anything for eth0 or eth1.

Thanks for you suggestion though.

---

### Post by ososxe on 2007-12-29
I have a weird problem with my Broadcom 4318 card, is a bit long to explain here, and I had already a post open with all the information, but sadly, no responses.
here's the link, if anyone's interested on it:

[http://ubuntuforums.org/showthread.php?p=4037552](http://ubuntuforums.org/showthread.php?p=4037552)

To make a resume, my card is being detected but does not show up on the network manager, not on wicd, not on anything I tried... and I'm lost :(

---

### Post by lynxair on 2007-12-30
Dell Inspiron 9100/7.10  - a no go with "kernel not supported" message (2.6.22-14 generic) for offline package. Not sure if I need to use the online one (kinda implies being on-line which I can't with the WLAN card not working? or what else to do?

---

### Post by r41nz0r on 2007-12-30
Thank you so much Dark for about 4 months now I've been w/out linux because of this exact reason but now that you've helped me I'm able to use linux and of course successfully connect to the internet! 	:wink:

-Thank You- Rain

---

### Post by Kevbert on 2008-01-01
Thanks for the suggestions.
Unfortunately it does not work with my Belkin F5D7000UK 802.11b/g card which is based on the Broadcom BCM4306 rev03 and Gutsy Gibbon.

---

### Post by rootware on 2008-01-01
> rut@k3rn3l:/root/bcm43xx-0.3.2-offline$ ./installer.py 
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
./wcm.sh wifi-radar
gksudo './bcm43xx-ndiswrapper.sh --use-deb'

It says it's a bad chipset and recomended to install ndiswrapper....I choose to install it, and I rebooted my laptop as it said.

What now? :confused:

PS: Used the offline file to unarchive and exxecute installer.py

---

### Post by lambres on 2008-01-02
Tengo una notebook Compaq presario F566LA y mi lspci es:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)


Funciono OK.
Muchas Gracias

---

### Post by ...Max... on 2008-01-03
No can do. Tried to follow this thread, this ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) and this ([http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)).

Symptoms are identical with 3 setups:

1. bcm43xx
2. ndiswrapper (Gutsy) + driver known to work in dual-booted XP install
3. ndiswrapper 1.51 (compiled) + similar driver from the second howto

What happens: I see the list of networks in network mgr applet after reboot. If I try to connect to my AP (64-bit WEP) the attempt times out after a minute (stage 2 completes according to the log but I never see a message with successful authentication). After a while even the list of networks disappears. I tried both WiFiRadar and manual iwconfig/dhclient sequence. Symptoms are similar: dhclient does not get any offers and times out. Also, iwlist scan gives no results.

Frustrating! If it weren't for this problem, I'd have spent much less time setting up Gutsy than XP on this laptop :(

Acer Extensa 5420, Gutsy, 4311 rev 01

lspci -vv:

05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0422
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at f0300000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [d0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
                Link: Latency L0s <4us, L1 <64us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

---

### Post by Coombabah on 2008-01-04
> **...Max... said:**
> No can do. Tried to follow this thread, this ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) and this ([http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)).

Symptoms are identical with 3 setups:

1. bcm43xx
2. ndiswrapper (Gutsy) + driver known to work in dual-booted XP install
3. ndiswrapper 1.51 (compiled) + similar driver from the second howto

What happens: I see the list of networks in network mgr applet after reboot. If I try to connect to my AP (64-bit WEP) the attempt times out after a minute (stage 2 completes according to the log but I never see a message with successful authentication). After a while even the list of networks disappears. I tried both WiFiRadar and manual iwconfig/dhclient sequence. Symptoms are similar: dhclient does not get any offers and times out. Also, iwlist scan gives no results.


I'm having similar problems.

It only works if I install Feisty get it working then upgrade to Gutsy.

I can't get wireless to work for more than about a minute after a fresh install of Gutsy.

---

### Post by gorby on 2008-01-04
Great guide mate!

I found an unlucky combo when i installed gusty today that really didnt want to work, 64 bit os + BCM4329!
bcm4329 is not supported by the b43 driver and 64 bit windows drivers are pretty hard to come by for this particular chip. 
32 bit with ndiswrapper is probably no problem but its day one of the install and too early to make a concession! =)
Perhaps consider adding a "this guide will not work for..." bit ;)

---

### Post by firehawk on 2008-01-05
wow, this was very easy!! thanks so much!! :) i now have wireless activated!

---

### Post by starkey on 2008-01-05
I tried the online script, but failed when the installed said I didn't have a Broadcom card.  I'm trying to install a Dell 1505 draft-n wireless card in my Latitude D430 notebook, under Ubuntu 6.1.  Dell recommends their R17429.exe driver.

I found an archived post <http://ubuntuforums.org/archive/index.php/t-572005.html> with what looked like a pretty good ndiswrapper installation process, and I tried that.  The driver appeared at first glance to install - ndiswrapper -l informed me that the driver was present and hardware found - but the device didn't show up in >System>Administration>Networking's list.  

dmesg |grep ndiswrapper reports the following depressing message:
ndiswrapper (check_nt_hdr:156): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl5'

All the posts I've found on this issue reference Feisty or Gutsy.  Any suggestions on what I should use as a driver for 6.1?  The CD install for 7.* fails right off the bat because it can't find the drive, and I get failure errata every time I try to apt-get install dist-upgrade.

Thanks for any sage advice,
starkey

---

### Post by Matsaki on 2008-01-05
AARRGGHH!!

This fix was working fine,, untill I restarted, and then every thing was gone. I tried "save session" but still not coming back. I had to import the firmware to make it work. AND NOW after the last try the network icon in the upper right corner is gone and I can't even connect with cable :(

If I open Network from the menu it is connected there, but still don't work. What did  mess upp this time :(

---

### Post by roaman on 2008-01-08
I tried all the advice on this forum and others trying to get my Compaq R3000 to work on Ubuntu Feisty. The broadcom adapter proved to be very confusing to get going especially for a new Linux user like me. Luckily I finally came across David Watson's site and it made everything work nicely. 

[http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html](http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html)

I had to clean out my Ubuntu installation cause I dont know what i did to it from all the advice but i couldnt even get it to connect through a wired connection. After redoing Ubuntu and following David's advice from the instructions provided, everything went up like magic.

The only thing I had to change was my type of encryption. Good luck. you may have to start over like me but at least setting and installing Ubuntu is way quicker and faster than XP.

cheers,

---

### Post by sagesparrow on 2008-01-11
Trying to get wireless working using Dell Latitude x300 with Broadcom 4318 in Gutsy. Not sure where to go from here.  After running the .py file and installing (or trying to) the recommended setup (ndiswrapper and broadcom driver) i got the attached message and i'm not sure if everything is now installed properly or not.  The only change I noticed under System, Admin, Network was the wireless which was listed is not longer there - just Wired and Modem.  This may sound stupid, but what am I supposed to see as far as available wireless connections?  do they appear in this Network Settings window or should they appear elsewhere so they can be selected easily?  Thanks

---

### Post by DarkN00b on 2008-01-11
Did you restart? Did you install WICD? My card is a Broadcom 4318 (Airforce1) chipset and works beautifully.

---

### Post by Paul86fxr on 2008-01-11
Hi, I've been dinking abound with this card for a day and a half, now it works great!! thank you very much!!

Paul

---

### Post by sagesparrow on 2008-01-11
> **DarkN00b said:**
> Did you restart? Did you install WICD? My card is a Broadcom 4318 (Airforce1) chipset and works beautifully.

I did restart.  i did not install WICD.  did I miss that in the instructions?

---

### Post by sagesparrow on 2008-01-11
when i selected WICD and ran it i got as attached.

---

### Post by sagesparrow on 2008-01-11
wicd now installed via synaptic.  will report results in a little while.  thanks

---

### Post by ibra_montreal on 2008-01-11
Thanks a lot for very useful how-to.

It worked for me.

All the best.

---

### Post by sagesparrow on 2008-01-11
wicd is installed and works but i do not detect the wireless signal.  i'm not sure that i have the preferences.  wpa driver is wext, the wireless interface is blank, and wired is eth0.  please let me know what further needs to be done.

---

### Post by icecoldtony on 2008-01-11
It worked, kind of. When I clicked on the installer.py file and it came up with the list of options. It said that it could'nt detect my wireless card but if I was sure it was there to install ndiswrapper and the driver. When I proceeded with that option it opened and window and said opening or installing driver (something like that) but it just hung there. Nothing happened. After a couple of tries I gave up on that and tried the option installing firmware. Worked like a charm. I rebooted and presto I have wireless. I've tried numerous other how to's and they failed time after time. This was easy and and semi quick. Thanks. I'm going to copy this to a cd incase I ever need it again. :)

---

### Post by sagesparrow on 2008-01-11
> **icecoldtony said:**
> It worked, kind of. When I clicked on the installer.py file and it came up with the list of options. It said that it could'nt detect my wireless card but if I was sure it was there to install ndiswrapper and the driver. When I proceeded with that option it opened and window and said opening or installing driver (something like that) but it just hung there. Nothing happened. After a couple of tries I gave up on that and tried the option installing firmware. Worked like a charm. I rebooted and presto I have wireless. I've tried numerous other how to's and they failed time after time. This was easy and and semi quick. Thanks. I'm going to copy this to a cd incase I ever need it again. :)

I'm still trying to get mine going.  I tried loading the firmware too.  Are you using Gnome Networking Manager or WICD?  What are you seeing that tells you that wireless is working?  What settings do you have for whatever manager you're using?  thanks

---

### Post by DrewB on 2008-01-11
Hi, this didn't work for me. It ran but I got errors.
Now when I boot I have no wireless at all and I can't get bcm43xx to load on startup.
Is there any way to undo\remove\uninstall the changes that this script made?
I'm using Ubuntu 7.10 on and AMD64 laptop.
Thanks a lot.

---

### Post by ios_base on 2008-01-12
I'm having problems.  I went with your cure and others to my bcm43xx blues and so far nothing is working.  Ubuntu community documentation pages didn't help either.  I'm stuck.  I'll show you some system information to help diagnose.

> kolby@Nautilus:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth9
       version: a2
       serial: 00:00:6c:60:50:60
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
kolby@Nautilus:~$ iwconfig
lo        no wireless extensions.

eth9      no wireless extensions.

kolby@Nautilus:~$ ifconfig
eth9      Link encap:Ethernet  HWaddr 00:00:6C:60:50:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4992 (4.8 KB)  TX bytes:4992 (4.8 KB)

kolby@Nautilus:~$ sudo iwconfig eth9 essid any
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth9 ; Operation not supported.
kolby@Nautilus:~$ 


hopefully someone here can help.  I don't know what do...  I tried to use ndiswrapper and it told me that "bcmwl5" is the wrong driver when I used the command: "ndiswrapper -l"

I'm lost and I tried everything I know.  I'm asking humbly now, what am I doing wrong here?

---

### Post by bbrownderville on 2008-01-13
I finally managed to get this how-to to work for me.  I am completely new to Linux all together so it was a lot different then Windows that i am so accustomed to.  It is a nice feeling to finally get wireless to work on my laptop.  Thanks to all that helped write this how-to, I don't know what i would have done without it.

---

### Post by Ralph L on 2008-01-13
One thing I noticed when running the install described above.  I had to have the directory in which installer was located selected in order for the script to work.  I just clicked the directory once and then executed one of the installers.  It worked fine under Fiesty..

---

### Post by skychen1900 on 2008-01-14
Wonderful, thank you !

---

### Post by rockbrawler884 on 2008-01-14
The installation when smoothly, but my wireless card has become unstable.  It works when I manually install it, but does not work after restart.

Anyone else have this same problem?

---

### Post by notsteve on 2008-01-15
my router is detected but i can't get online, also I tried to INstall WICD but it didn't work, any ideas?

---

### Post by manro on 2008-01-15
> **notsteve said:**
> my router is detected but i can't get online, also I tried to INstall WICD but it didn't work, any ideas?

Do the router is set to broadcast your SSID? I had the same issue with my router until I configure it to broadcast my SSID. IMHO broadcasting your SSID is not a good idea, but I cannot figure out another workaround for this issue.

Regards,
Manro

---

### Post by dankster117 on 2008-01-15
Omg darknoob thank you so so so so much. Every method I tried fail, this was amazingly easy and its up and running perfect on my dell 1501 inspiron notebook I really can't thank you enough:)

---

### Post by EmoDx on 2008-01-15
I started to do this and got the following output of my term window:
[COLOR="Red"]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [139kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [7842B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [27.6kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [979B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [85.9kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [11.2kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [85.9kB]
83% [10 Packages bzip2 0] [12 Packages 81/85.9kB 0%]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Fetched 410kB in 4s (93.3kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/COLOR]

1. What does this mean?
2. Does this matter?
3. If so, how do I recover from this?

Any informations would be very much appreciated.

-Emo

---

### Post by wa$ter on 2008-01-15
I plugged the computer into a wired connection and ran the online installation -- it worked and connected to my network, so I powered off, ran the computer back into the room where I wanted and  turned it on... But now there are no wireless controls to be found! Why?:(

---

### Post by EmoDx on 2008-01-15
> **EmoDx said:**
> I started to do this and got the following output of my term window:
[COLOR="Red"]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [139kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [7842B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [27.6kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [979B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [85.9kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [11.2kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [85.9kB]
83% [10 Packages bzip2 0] [12 Packages 81/85.9kB 0%]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Fetched 410kB in 4s (93.3kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/COLOR]

1. What does this mean?
2. Does this matter?
3. If so, how do I recover from this?

Any informations would be very much appreciated.

-Emo

I tried it later on and for what ever reason the aptitude update/upgrade worked.

---

### Post by EmoDx on 2008-01-15
okie dokie, I tried to do this following the directins an no worky for me. FWIW, when I look at my driver in XP, it says it is WPC200Nv1.sys. When I look at System-Administration-Windows Wireless Drivers, that app will only allow .inf files to be installed. Anyone have any ideas that can get Ubuntu to use the .sys file instead? TIA

-Emo

---

### Post by EmoDx on 2008-01-15
> **EmoDx said:**
> okie dokie, I tried to do this following the directins an no worky for me. FWIW, when I look at my driver in XP, it says it is WPC200Nv1.sys. When I look at System-Administration-Windows Wireless Drivers, that app will only allow .inf files to be installed. Anyone have any ideas that can get Ubuntu to use the .sys file instead? TIA

-Emo

Tried to trick the system by renaming it to WPC300nv1.inf, :lolflag: Didn't work. I right clicked on the .exe file on the driver disk and seleceted "open with wine". I showed some disk activity for about 45 seconds and then nothing. Any ideas?

I read on the Linksys forum that somone tried using the current ndiswrapper and it didn't work for them. After going back to v1.34 ov the ndiswrapper it worked. Any ideas?

If I can't get this to work, can someone recommend a card that is being sold "in store" at Bestbuy, Circuit City, Officemax, etc? I don't need the best or the latest, rather need what is the easiest to set up in Ubuntu.

-Emo

---

### Post by wa$ter on 2008-01-15
Uggh how to I undo changes made by running the installer? :confused: I thought it was the updates that made my wireless disappear.

---

### Post by EmoDx on 2008-01-15
> **wa$ter said:**
> Uggh how to I undo changes made by running the installer? :confused: I thought it was the updates that made my wireless disappear.

Can't you just reimage the compuer? I know it's a huge PITA, but at least you would be up and running.

---

### Post by mbarnes0 on 2008-01-17
Wokring like a charm so far. Seems like a great script!

---

### Post by donmor on 2008-01-17
Have not got mine working yet.  Dell Inspiron 1501.
Lost my connection icon from top panel.
How do I get this back?

Thanks
Don

---

### Post by bmcd31 on 2008-01-17
didn't work..I have a latitude D600

the installer said "Incompatible Broadcom chipset found. Ndiswrapper installation is highly recommended" and I should "install ndiswrapper (which I already have) and Broadcom windows driver" so I chose that. 

I don't know how to copy the output of the program but basically it said there was no usable font set and that package 'build-essential' is not installed.

Any ideas?

PS - I tried reinstalling the firmware which ended up in my computer freezing and, after a manual reboot, Ubuntu didn't load. It just stopped at the boot screen and couldn't load hardware drivers. I ended up having to reinstall Ubuntu. Then I tried everything all over again and it didn't work, so I tried to reinstall the firmware again and it froze again.  I see yet another Ubuntu installation in my near future.

---

### Post by EmoDx on 2008-01-18
I am trying to run the K version, but I keep getting a 403 Forbidden error. Is there a mirror to this site, or is there a kind sole that can provide me with an alternative to this?

-Emo

---

### Post by DarkN00b on 2008-01-20
The download should be working again now. Fileden was having some server trouble.

---

### Post by oposum on 2008-01-21
Hey,

I'm using HP compaq nx6125 with BCM4318 wifi adapter and am experiencing the same problem as bmcd31!  

First I installed the firmware  (Install BCM43xx firmware option)  and it seemed to do some good - i caught the SSID broadcast!  But when i hit properties i would like to choose no security, as i have these settings on the router, there are only 4 types from which to choose - there is no "none" function!

Ok then i said that there must be something missing and i went and installed all the stuff that comes with the *.py installer and i think after the WICD installation i lost the network icon and the network manager (which is uninstalled during the WICD installation)

Now i'm kinda stuck and after all of this i also tried reinstalling the firmware and can see the wireless network and can supposedly connect to it (as before) but can't ping the router...

---

### Post by bhavin66 on 2008-01-22
helped me get the right setup.
had the firmware installed but was unstable but this package said hardware incompatible install ndiswrapper.
i did and it is 24 hrs and no issues.
as others said works like a charm !

---

### Post by omgapolarbear on 2008-01-26
i've tried installing it and it says that my chipset is not compatable, and to do the ndiswrapper install. Well that doesnt do anything so i try the firmware install. It works for a while, its turned on, but it doesnt connect. Any advice, after a little while it cuts out again.

---

### Post by CatastrophicToad on 2008-01-26
I use Linux Mint and have a HP Pavilion ze4803us with a Broadcom BCM4306 wireless card.  I had some trouble with the script, but I got it to work, here's the short version:

I removed /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko then ran the script, then put the file back.

Here's the long version:

The script kept hanging after saying "removing old ndiswrapper module", so I searched for that in the scripts and found in bcm43xx-ndiswrapper.sh :

if [ "$1" = "--use-deb" ]; then
	deb="`ls $NDISWRAPPER_DEBS/ndiswrapper-*-$(uname -r).deb`"
	echo -n " * Removing old ndiswrapper module... "
	$RMMOD ndiswrapper > /dev/null 2> /dev/null
	rm $(find /lib/modules/$(uname -r) -name ndiswrapper.ko) 2> /dev/null
	depmod -ae
	echo 'done'

I tried running these commands in the terminal, found that it was looking to remove that file I said earlier, along with whatever "2> /dev/null" means.  After running them the script would still hang, so I decided to just delete the file.  Then the script ran through, but when it finished the wireless was completely gone (which didn't surprise me because I had just deleted the module that the script had just tried to install).  Obviously it would have been easier to simply copy the file somewhere else and replace it, but I found it on the installation CD in the same place and replaced it, and then it worked.

I hope this helps other people who may have the same problem, and maybe the script can be updated to work around this problem (I think it might have something to do with Linux Mint)(I used the online script btw but I don't think it makes a difference).  Thank you for this script, I've been trying for years to get the wireless to work with Linux on my laptop.

---

### Post by txbikerider on 2008-01-26
This doesn't work for a Broadcom 4310 Rev 01 card in my HP Pavilion DV2710US box.  I've tried everything I can find in the forums or on the net.  No joy to be found.  Happiness has surely left my office...:(

---

### Post by SarkkaS on 2008-01-29
> **txbikerider said:**
> This doesn't work for a Broadcom 4310 Rev 01 card in my HP Pavilion DV2710US box.  I've tried everything I can find in the forums or on the net.  No joy to be found.  Happiness has surely left my office...:(

Join the club. I admit, that I was lazy on following the advice of the first post to read the ENTIRE thread of over 100 pages.

I have a HP DV6615eo, have gotten the graphics to work at the correct resolution, but that's it. I can't get the WLAN to work. In Restricted Drivers under the Firmware-heading is "Firmware for Broadcom 43xx chipset family" with a checkmark and "in use" -text. No networking icon is present on the top menu bar.

What's a guy to do? Return to (ergh..) Vista?! :shock:

EDIT: lspci tells me that the exact hardware is identified as Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02).


-Sale

---

### Post by SarkkaS on 2008-01-29
It now seems, that I also lost wired networking capabilities as well. Hooray..

As stated, any help would be appreciated.


-Sale

---

### Post by sageb1 on 2008-01-30
how does one install wicd?

need instructions for that

---

### Post by rorshach on 2008-01-30
so i read through a couple pages of this thread and it seems like its a miracle worker, but the only thing is that theres no way for me to get my comp online that isnt wireless.  i use one of those big downtown wireless network providers, so i dont actually have a hardwires internet connection.  im a total nub to linux and i really just want to get on the internet.  can anyone help me?

---

### Post by Crimson_Wake on 2008-01-30
I am SOOOO bloody frustrated.

I have no problem connecting through a hardwire connection, but I cannot get this bloody wireless to work.

I used to have the problem of having a wireless card built into my hp ze4400 that was the 43xx card.  It was discovered as eth1 and was DISABLED.  eth0 is my standard ethernet cable connection.  I installed these drivers and still had nothing so I went to sourceforge and got WICD and installed it.  Now I do not have my network box anymore and WICD still cannot find a wireless network.  

I iwconfig in terminal now and it cannot find the eth1 at all.  There is no llonger a wifi card in the PC as far as it is concerned.

W.T.F.

I tried to set it up as the ndiswrapper, wext...etc.  Nothing.

Any clue?

---

### Post by donn29 on 2008-01-30
> **Crimson_Wake said:**
> I am SOOOO bloody frustrated.

I have no problem connecting through a hardwire connection, but I cannot get this bloody wireless to work.

I used to have the problem of having a wireless card built into my hp ze4400 that was the 43xx card.  It was discovered as eth1 and was DISABLED.  eth0 is my standard ethernet cable connection.  I installed these drivers and still had nothing so I went to sourceforge and got WICD and installed it.  Now I do not have my network box anymore and WICD still cannot find a wireless network.  

I iwconfig in terminal now and it cannot find the eth1 at all.  There is no llonger a wifi card in the PC as far as it is concerned.

W.T.F.

I tried to set it up as the ndiswrapper, wext...etc.  Nothing.

Any clue?

I am searching for this answer too.  43XX in my dv9317.  I did the firmware update, rebooted and it saw a connection, but I didn't connect to it as I use a hard wired connection, now i notice that it doesn't work anymore, but still does in windows (ugh).  
iwconfig shows:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

but if I use Hardware Information, I can see it and lspci shows the below.  Basiclly I think, correct me if I'm wrong, we need to create a new eth1?

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)**
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

---

### Post by Crimson_Wake on 2008-01-30
The strangest thing with my situation is I installed everything and then went into my "Restricted Drivers Manager" and 'enabled' the driver.  It then asked me to download the driver from the internet.  I have been connected (wired) since I first put xubuntu on this hp.

So I did and then I went to WICD and went into preferences.  Changed the WPA driver to Broadcom and BAM - networks show up!

I select mine, configure it to use it always, and connect!

Then I shut down and moved to the other room.  Loaded up everythingand t can't find te networks.  I went back into the restricted drivers and verified that it was enabled and running. T'was running.

I uninstalled it, then reinstalled it with myethernet cableconnected again. Suddenly I have networks again!

What is going on?

Am I going to have to uninstall and reinstall these drivers whilst connected every time I boot up the laptop?

oy.

---

### Post by Ayuthia on 2008-01-31
> **Crimson_Wake said:**
> The strangest thing with my situation is I installed everything and then went into my "Restricted Drivers Manager" and 'enabled' the driver.  It then asked me to download the driver from the internet.  I have been connected (wired) since I first put xubuntu on this hp.

So I did and then I went to WICD and went into preferences.  Changed the WPA driver to Broadcom and BAM - networks show up!

I select mine, configure it to use it always, and connect!

Then I shut down and moved to the other room.  Loaded up everythingand t can't find te networks.  I went back into the restricted drivers and verified that it was enabled and running. T'was running.

I uninstalled it, then reinstalled it with myethernet cableconnected again. Suddenly I have networks again!

What is going on?

Am I going to have to uninstall and reinstall these drivers whilst connected every time I boot up the laptop?

oy.

It sounds like the bcm43xx driver is not getting loaded on reboot.  You might try adding bcm43xx to /etc/modules and restarting to see if it works.

---

### Post by Crimson_Wake on 2008-01-31
ok, so how do I do that?

I tried to move it in the GUI, but it just moves back.  Also, there are so many files in the folder (BCM43XX folder) like the bc43xx.sh and bcm43xx-ndiswrapper.sh.  WHat files/folders exactly am I supposed ot move, and how do I do said moving?

Do I have to go into terminal to do it?

---

### Post by Ayuthia on 2008-02-01
> **Crimson_Wake said:**
> ok, so how do I do that?

I tried to move it in the GUI, but it just moves back.  Also, there are so many files in the folder (BCM43XX folder) like the bc43xx.sh and bcm43xx-ndiswrapper.sh.  WHat files/folders exactly am I supposed ot move, and how do I do said moving?

Do I have to go into terminal to do it?
You will need to go into terminal to do it.  I am not for sure about how comfortable you are in there, so the easiest way to add it would be to type in the terminal:
```
echo bcm43xx | sudo tee -a /etc/modules
```
This will ask you for your password and then it will add the 'bcm43xx' entry to the /etc/modules file.

---

### Post by Crimson_Wake on 2008-02-01
I don't have a modules folde--- wait.  I might.  It might just be hidden.  I'm at work now, so I cannot check.

I am pretty comfortable in Terminal - I just need to have my cheat sheet with me (all the commands).

I will try it when I get home.  I'm so close to getting this to work- I can taste it.

---

### Post by SarkkaS on 2008-02-02
I don't get it. Now it simply just began to work. I am surfing via wireless, with WPA security.

This rocks!


-Sale

---

### Post by SarkkaS on 2008-02-05
I now tested something and began to understand the problem. At least one thing doesn't work for sure: connecting on channel 13. All Windows XP boxes are fine (including this Linux box when booted into Win XP), but Ubuntu doesn't cope. When I got the system to work, I had set the AP to channel 1. When I set the WLAN to ch 13, the connection never again regained consciousness. I switched back to a lower channel, this time channel 3. Came right back up.

Have others noticed anything like this regarding channel numbers up higher? I don't have the time to do comprehensive testing, but hopefully I'll get some done this coming weekend.


-Sale

---

### Post by Nihilis on 2008-02-09
This did nothing but make my problem worse it got rid of the wireless option in my network settings i have tried everything to get my broadcom card working and i thought this might be it but i guess i was mistaken..:mad:

---

### Post by steve.t on 2008-02-10
Hey guys,

Hope someone is still watching this thread.  I got the following problem; could someone help:

alex@alex-laptop:~/bcm43xx-0.3.2-internet$ ./installer.py
./wcm.sh wifi-radar
kdesu './bcm43xx-ndiswrapper.sh'
sh: xterm: not found
alex@alex-laptop:~/bcm43xx-0.3.2-internet$

This is on ACER Aspire 3003WLMi with KDE Gutsy Gibbon.

Thanks in advance,
Steve

---

### Post by cybo on 2008-02-11
Is there a working offline version of the installer as I don't have a wired connection. Or maybe someone can explain how to install the drivers for Broadcom wireless the proper way (I'm new to Ubuntu). Any help will be appreciated.

Thank you.

---

### Post by jgriffinpark on 2008-02-11
I have the same problem... In 7.10 I've tried the firmware with bcm43xx-fwcutter and the light turned blue right away, however no wireless networks were detected. I've tried to compile ndiswrapper as well, this has also been a complete failure :( I would also like some sort of offline installer for ndiswrapper, as whenever I issue modprobe nothing happens at all. This is really frustrating and I think I'll give up if I can't get it working soon...

---

### Post by jake85 on 2008-02-14
i cant get my 4312 wifi card to work... i've tried using "ndiswrapper" and the windows driver (bcml6.inf) but still cant get it to work... i can see the AP but CANT connect to it. even if there is no encryption set.

also every another problem sometimes my wifi card appears in Network Manager but if i reboot its gone... adn to get it back sometimes takes a few reboots to get it back.. :(

My Laptop :

Compaq B1959TU, 12.1" 1280x800
Intel Core Duo 1.73Ghz
2GB DDR2 667mhz
ATI Express 200M Graphics
Broadcom 802.11 B/G WiFi BCM4312
160GB SATA HDD

---

### Post by jake85 on 2008-02-15
i fixed my Broadcom 4312


by referring to [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")

---

### Post by mattstakilla on 2008-02-15
awesome, the only reason why i never made the change to linux was because i couldnt get my wireless working. i just installed ubuntu and used this walkthrough, and it worked like a charm!! thanks a bunch.

for anyone else that has a dell xps pp09l, this does work!!

thanks again

---

### Post by bird5150 on 2008-02-17
wonderfull finally got my wireless working thanks for tut.
hpdv5139

---

### Post by wolfie19 on 2008-02-19
Had to post a reply. Have been a umbunto user for 20 mins, having resurrected an old PIII. wireless card was not working - followed your instructions for gnome - all works now. 

Have been a Windows user since day 1 - am a convert already!

---

### Post by Chutney on 2008-02-19
Posted this in a thread but I guess I should post it in here as well:

Hi folks,

Followed the instructions here to install drivers/firmware for my laptop's wireless through "Restricted Drivers Manager":

[https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy](https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy)

Got to "In Use", everything seems fine, "iwconfig" and "lshw" seem to show the interface properly, and network manager behaves as if everything is going smoothly. However, neither Network Manager or "sudo iwlist scan" can detect any networks.

So far I've tried:

-confirming there are indeed active networks in range (yes).
-disabling all security from my home network to see if that helped (no).
-installing ndiswrapper (failed with "can't initialize module" or similar in the error logs)
-uninstalling ndiswrapper and trying above "Restricted Drivers Manager" procedure again (same result)

"lspci" says my wireless controller is:

30:00.0 Network controller: Broadcom Corporation BCM 4312 802.11a/b/g (rev 02)


I'm reasonably handy with general Ubuntu troubleshooting (we have 5 PCs running Gutsy in the house) but don't know much about wireless issues (other times I have used wireless it has just worked straight away) so any help here would be greatly appreciated.

Thanks,

Chutney

---

### Post by Ayuthia on 2008-02-20
> **Chutney said:**
> Posted this in a thread but I guess I should post it in here as well:

Hi folks,

Followed the instructions here to install drivers/firmware for my laptop's wireless through "Restricted Drivers Manager":

[https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy](https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy)

Got to "In Use", everything seems fine, "iwconfig" and "lshw" seem to show the interface properly, and network manager behaves as if everything is going smoothly. However, neither Network Manager or "sudo iwlist scan" can detect any networks.

So far I've tried:

-confirming there are indeed active networks in range (yes).
-disabling all security from my home network to see if that helped (no).
-installing ndiswrapper (failed with "can't initialize module" or similar in the error logs)
-uninstalling ndiswrapper and trying above "Restricted Drivers Manager" procedure again (same result)

"lspci" says my wireless controller is:

30:00.0 Network controller: Broadcom Corporation BCM 4312 802.11a/b/g (rev 02)


I'm reasonably handy with general Ubuntu troubleshooting (we have 5 PCs running Gutsy in the house) but don't know much about wireless issues (other times I have used wireless it has just worked straight away) so any help here would be greatly appreciated.

Thanks,

Chutney

I am assuming that you went through the troubleshooting in the link that you provided.  What did dmesg say after you loaded the driver?

Also when you used ndiswrapper, which driver did you use?  The message that you described sounds like it did not like the windows driver that you provided.

---

### Post by Chutney on 2008-02-21
Yes I tried the troubleshooting section. Here's the end of the output from dmesg (before that it's more of the same):

> [ 2381.568000] printk: 250286 messages suppressed.
[ 2381.568000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2384.116000] APIC error on CPU0: 40(40)
[ 2384.116000] APIC error on CPU1: 40(40)
[ 2384.676000] APIC error on CPU0: 40(40)
[ 2384.676000] APIC error on CPU1: 40(40)
[ 2385.056000] APIC error on CPU0: 40(40)
[ 2385.056000] APIC error on CPU1: 40(40)
[ 2386.568000] printk: 254268 messages suppressed.
[ 2386.568000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2387.448000] APIC error on CPU0: 40(40)
[ 2387.448000] APIC error on CPU1: 40(40)
[ 2387.980000] APIC error on CPU0: 40(40)
[ 2387.980000] APIC error on CPU1: 40(40)
[ 2389.940000] APIC error on CPU0: 40(40)
[ 2389.940000] APIC error on CPU1: 40(40)
[ 2391.568000] printk: 253422 messages suppressed.
[ 2391.568000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2391.664000] ACPI: PCI interrupt for device 0000:30:00.0 disabled
[ 2391.716000] ieee80211_crypt: unregistered algorithm 'NULL'
[ 2401.772000] ieee80211_crypt: registered algorithm 'NULL'
[ 2401.776000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 2401.776000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 2401.780000] bcm43xx driver
[ 2401.780000] ACPI: PCI Interrupt 0000:30:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[ 2401.780000] PCI: Setting latency timer of device 0000:30:00.0 to 64
[ 2401.784000] bcm43xx: Unsupported 80211 core revision 13
[ 2401.788000] bcm43xx: Invalid PHY Revision 9
[ 2402.108000] printk: 2668 messages suppressed.
[ 2402.108000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2402.112000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2402.220000] bcm43xx: MAC suspend failed


The ndiswrapper driver I tried was from the ndiswrapper site.  I'll try looking elsewhere and see where that gets me.

---

### Post by Chutney on 2008-02-21
OK problem solved.  Tried ndiswrapper again, this time with Windows XP drivers, and it worked.  I'll put details for anybody else with the same problem on this thread:

[http://ubuntuforums.org/showthread.php?t=701966]("http://ubuntuforums.org/showthread.php?t=701966")

---

### Post by marioquark on 2008-02-23
i would say everybody that firmware is installable simply using the package in synaptics bcm43xx-fwcutter.
note that it's wrong the url in the script that the package installs: so you have to edit the installed script (see installed file from the package informations to find it)
 and replace the wrong link with:

```
http://svit.epfl.ch/stuff/wl_apsta.o
```

then re-run this script from sudo.

:P

---

### Post by Ayuthia on 2008-02-23
> **marioquark said:**
> i would say everybody that firmware is installable simply using the package in synaptics bcm43xx-fwcutter.
note that it's wrong the url in the script that the package installs: so you have to edit the installed script (see installed file from the package informations to find it)
 and replace the wrong link with:

```
http://svit.epfl.ch/stuff/wl_apsta.o
```

then re-run this script from sudo.

:P
For those who want to do this and don't know where the file is located, it is found at:
```
/usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

---

### Post by kapil_karekar on 2008-02-27
I am using a hp tx1000 machine with Gutsy. The funny thing is it detects my Broadcom wireless card sometimes. Whenever the card is detected wireless works fine.

Can someone help me to get the card detected consistently?

Whenever the card is detected, lspci lists it as:

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by K.Mandla on 2008-02-28
Unstickied.

---

### Post by DarkN00b on 2008-02-28
Thanks K.Mandla.

As K.Mandla stated, this thread had been unstickied - at my request. The fact is that it has  been doing more harm than good lately, and I do not have the programming knowledge necessary to update it. This driver installation method has outlived its expected lifetime and I think it is now time to let it die a quiet death.

So for those of you whom this has helped, congratulations. For those whome it hasn't helped, I'm sorry.

Darkn00b

---

### Post by Edf10503 on 2008-03-03
Thanks so much for taking the time to build this fix. For Linux newbies like me who need a GUI to make things happen, it's a life-saver. :KS

Ed

---

### Post by MattyG on 2008-03-06
Worked Great!!!!!Very Easy!!

---

### Post by CWaugh on 2008-03-06
All I had to do to enable my card was connect directly to my modem and enable the restricted driver.  Was this in a recent update,  was this a fluke, or has it always been the case?

---

### Post by felmaso on 2008-03-14
Gracias, probé el firmware inicialmente, probé instalando ndiswrapper y nada. La tarjeta wireless la detectaba en eth1. Instalé con este método python y funcionó. La diferencia es que ahora veo la tarjeta en wlan0

Thank you, I tried the firmware al first, I tried installing ndiswrapper and nothing. The wireless card was detected in eth1. I installed this python program and works. The only difference I saw is that now the wireless card is in wlan0.

---

### Post by swat253 on 2008-03-15
No apologies necessary Dark...  

The numbers speak for themselves:
[COLOR="Blue"]Yes   	   	585  	69.73%
[/COLOR]No 		254 	30.27%

This thread was my fourth series of attempts to configure and connect. Your instructions and links in the original page worked for me!

THANKS!=D>=D>=D>

---

### Post by pfeifdog on 2008-07-22
These posts were incredibly helpful -- thanks so much!

However, I'm experiencing a weird glitch. The wireless card doesn't activate when I start up the computer, or when I insert the card after startup. The only way I've found to get it working is to put the computer on "Hibernate" after starting it and then revive it. Then I'm good to go (11mb/s on a G-router) until I shutdown again.

This isn't a big deal, but can anyone explain why it happens or how to make it work right on startup?

I'm running Hardy.

---

