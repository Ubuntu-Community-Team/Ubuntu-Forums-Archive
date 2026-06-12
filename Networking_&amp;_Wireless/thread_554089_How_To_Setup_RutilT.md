---
title: "How To Setup RutilT"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by sulligogs on 2007-09-18
To Everyone,

I have my Edimax EW-7128g wireless network card running successfully for weeks now with Ubuntu Feisty Fawn.  I am using a static IP network and would like to share how I got my card, which uses the  RT61 chipset, running flawlessly:-

[SIZE=4]1[/SIZE]) Uninstall Network Manager.  It's useless for you.  Go into Synaptic Package Manager and remove the following:-[INDENT][FONT=Courier New][COLOR=Red]network-manager
network-manager-dev
network-manager-gnome[/COLOR][/FONT][/INDENT]Then, whilst in Synaptic Package Manager, install the following:-[INDENT][FONT=Courier New][COLOR=Blue]libgtk2.0-dev
g++-4.1[/COLOR][/FONT][/INDENT][SIZE=4]2[/SIZE]) Download and extract the latest version of RutilT from [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) to your desktop.

[SIZE=4]3[/SIZE]) Open up a terminal and change to the directory to the download on your desktop.  Enter in these commands:-

```
./configure.sh --launcher=nopasswd
make
sudo make install
```Enter your password if asked.

[SIZE=4]4[/SIZE]) Now, within the terminal, enter:-

```
gksu gedit /etc/network/interfaces
```Enter your password if asked.

[SIZE=4]5[/SIZE]) Append the following to the file you just opened (see 4):-[INDENT][FONT=Courier New]# RT61
auto ra0
iface ra0 inet static
address *[COLOR=Gray] your machine's desired ip address[/COLOR]*
netmask *[COLOR=Gray]usually 255.255.255.0[/COLOR]*
gateway *[COLOR=Gray]the ip address of your router[/COLOR]*[/FONT]
[/INDENT]Save the file and close the editor application.

*This step is required for STATIC IP addresses.  At this point in time, using RutilT v0.15 for DHCP or dynamic addresses, still comply with this step, but note the advice at the footer of this post. *

[SIZE=4]6[/SIZE]) At the terminal enter the following:-

```
sudo nameserver *[COLOR=Gray]the ip address of your router[/COLOR]*>>/etc/resolv.conf
sudo route add default gw *[COLOR=Gray]the ip address of your router[/COLOR]*

```Enter your password if asked.  The two characters >> looking to the right actually mean "write to" a file or device.

[SIZE=4]7[/SIZE]) Reboot.  Click on Rutilt WLAN Manager from the Applications->Internet menu.  Up will pop the RutilT application.  Click on the **Profiles** tab then the **New** button.  Fill in the typical details that are required for a wireless network.  Click **Apply** to see if the RutilT icon in the top panel shows that it has connected.  If it has then well done!

[SIZE=4]8[/SIZE]) Now go to System->Preferences->Sessions.  Click **New** and in the box that pops up in the name field enter _RutilT WLAN Manager_ then in the command field enter _rutilt -tp *[COLOR=Gray]the profile you just created[/COLOR]*_.  Click **OK** and then **Close**.  This will ensure that on every boot it will run and automatically select the network profile you had created.

[SIZE=4]9[/SIZE]) Tell me how it goes!

Clicking the RutilT icon from the top panel will show and hide RutilT.  If you click **X** to close the application your network will still run.

[I]If you wish to temporarily change to a DHCP address just bring up the RutilT window, click the **Profiles** tab, then the **Edit** button selected with your profile, then the **IP settings** tab and choose **Automatic (DHCP)** then **OK** and **Apply**.  Click the RutilT icon to hide away.  You're now using DHCP!

If you wish to always use DHCP then go to System->Preferences->Sessions and change the _-tp_ bit to _-dp_.  Reboot and volia!  No severe editing of config files here![/I]

Sulligogs!

---

### Post by NotoriousTF on 2007-09-27
Great how-to sulligogs!
... If only I had come across it last night, it would've sped things up a lot. Only problem I'm having so far is making RutilT run automatically when I boot. Each time I add RutilT to the list, it disappears on exit. :confused: I was only putting "*rutilt -dp*" in the command field, could that be a problem?

---

### Post by sulligogs on 2007-09-29
Hi NotoriousTF!

Thanks for giving my HOWTO a try.  Glad it's sort of helped you out.

When you say it disappears on exit do you mean on  reboot or when going back to the Sessions window?  Have a look at the pic below:-

[IMG]http://www.newclearview.co.uk/rutilt/rutilt-sessions.png[/IMG]

That's generally how you would have it setup in the Sessions window.  Replace the MYROUTER with the profile you created in step 7 of the HOWTO.  Click OK and then Close to accept the changes in the Sessions window.

Of course, change the "-tp" to "-dp" for DHCP.

If this is what you are doing and it's just not staying in the Sessions window then I think we might have a problem with Ubuntu itself.  Just thinking, have you had any severe crashes recently?  Are you able to add anything else to Sessions - like gedit, for example?

Get back to us on this one because it sounds a bit nasty!

---

### Post by gnudoc on 2007-09-30
thanks, sulligogs! i learnt a lot from your howto and seem to have *almost* got my rt61-based card sorted.

unfortunately, i have a problem. i get a link quality of 0%, and can't get any connection, despite the fact that, from my windows partition, there is over 70% quality. (the router's strength is set to max)

oddly enough, i am getting packets transmitted and received.

any ideas? i feel as if i'm soo close!

cheers,
gnudoc

---

### Post by NotoriousTF on 2007-09-30
Thanks sulligogs, but I think its a problem with Ubuntu. Every time I add something to the 'programs on start-up' list, they just disappear when I go back into the sessions window.I'm having problems adding numerous programs to it, not just RutilT. Its nothing major, but it'd be nice to get it working.

Another thing with RutilT though, obviously with my 'Sessions' problem each time I boot up I have to start-up RutilT and select the wireless network I want to connect to. I made a profile in RutilT when I first used it. Straight away using the profile my wireless connection worked. On booting-up the next time (ie 2nd time using RutilT), selecting the profile and attempting to connect via that profile doesn't work. I have to into the 'Site Survey' and connect there. Only annoying thing there is by connecting that way I have to enter my WEP key each time.
All my settings seem ok within the profile I connected, so any idea what's going wrong?

EDIT: Ok just got some help and everything working with programs on start-up!

---

### Post by mastergunner on 2007-09-30
I am a noob with linux sulligogs so can you tell me how to change to the download of this program when I have downloaded it straight to my desktop. Also I want to use DHCP exclusively so exactly what do I need to do. hanks.

---

### Post by sulligogs on 2007-09-30
Hi guys and thanks for using my post.

First of all, gnudoc

> **gnudoc said:**
>  unfortunately, i have a problem. i get a link quality of 0%, and can't get any connection...  oddly enough, i am getting packets transmitted and received.

This either sounds like something very specific to your brand of network card or your RutilT profile not quite being exact - WEP or WPA?  Did the installation go smoothly by the way?  Are you able to run RutilT each time without being asked for the administration password?  Sounds very interesting.

Get back to us on that one please.  Need a bit more info before continuing.

P.S.  Don't worry too much about the packets.  I get it as well :)

And now, NotoriousTF

> **NotoriousTF said:**
>  EDIT: Ok just got some help and everything working with programs on start-up!

Whooah!  Is everything now running *completely* fine???  How?  Was it that you was logged in with restricted access and someone pointed you to a quick fix or was it just some silly bug in Ubuntu?  I'm still intrigued by it.  Spill the beans!

And if all problems have been eradicated how well is your network now?  How long has it been running this way?  Tell me more!

Okay and lastly, mastergunner:-

> **mastergunner said:**
> I am a noob with linux sulligogs so can you tell me how to change to the download of this program when I have downloaded it straight to my desktop. Also I want to use DHCP exclusively so exactly what do I need to do. hanks.

Ahem!  Well, yes.  The download is a compressed file anyway.  You have to uncompress it once downloaded - that way it then becomes a folder.

I take it you are using the Firefox browser? By default, all downloads will go to your desktop.  Once it is downloaded to your desktop you could just *right* click it.  Up will pop a context menu and towards the bottom of that menu you will see a menu item that says, "Extract Here".  Click it and a folder will miraculously appear on your desktop somewhere.  It should have the name "RutilTv0.15" (if you are using the 0.15 version, of course).  From here you should be as safe as houses with the HOWTO.

As with using DHCP - just follow everything in the HOWTO.  Version 0.15 of Rutilt is still a little rough around the edges.  You must take special consideration of step 5 of the HOWTO.  You need to edit /etc/network/interfaces and add those lines to the end of the file.  If you don't know what IP address to give to your machine, just try 192.168.0.10, for example.  You can still fully use DHCP by following the advice at the bottom of the HOWTO.  Hope it helps!

I know more technical bods will say a few ifs and buts about my advice here, but I think this is the more direct and isolated way of getting RutilT up and running.  I know that a DHCP network needs a slightly different configuration in the /etc/interfaces/network file - but at least this way the HOWTO can apply to everyone with as few steps as possible.

---

### Post by gnudoc on 2007-10-01
> **sulligogs said:**
> This either sounds like something very specific to your brand of network card or your RutilT profile not quite being exact - WEP or WPA?  Did the installation go smoothly by the way?  Are you able to run RutilT each time without being asked for the administration password?  

Sulligogs,
Yes, it may well be my card - there are a couple of threads in the forums about rt61 cards giving 0% link quality. It's a linksys wmp54g, by the way, which does indeed use the rt61 chip.
I've tried with both wep and wpa - getting it to work with wep has been easier in the past (i did eventually get it working in feisty with wep, but never wpa). The install went exactly as planned, i'm not being asked for passwords. It's recognising the card ok, but just not recognising the network properly, which makes me think it's a driver problem.

cheers,
gnudoc

---

### Post by sulligogs on 2007-10-01
> **gnudoc said:**
> Sulligogs,
Yes, it may well be my card... It's a linksys wmp54g, by the way, which does indeed use the rt61 chip.Okay - thanks for that bit of info.

You can give us a bit more info by entering this at the terminal:-

```
[INDENT]sudo ifconfig[/INDENT]
```

Enter your password if asked.  Then this after:-

```
[INDENT]sudo iwconfig[/INDENT]
```

And after entering your password again, this one last line:-

```
[INDENT]sudo iwlist scan[/INDENT]
```

With your password if asked.

Sorry, if you already know about these commands.  Maybe I can search elsewhere with what you get from these commands and give you back something definite.

Fingers crossed!

---

### Post by mastergunner on 2007-10-03
Sulligogs I screwed something up. Can you give me a step by step for DHCP? I mean from download to finish. Thanks.

---

### Post by mastergunner on 2007-10-03
Well got it BUT I can connect to the internet but it shows no signal strength. I am using a Netgear WG511v1 card. What gives?

---

### Post by gnudoc on 2007-10-04
sorry about the vanishing act - i was away from home for a while and couldn't ssh into my box without someone connecting up the cat5 - and there was no-one there to do so. Anyways,

> **sulligogs said:**
> 
Sorry, if you already know about these commands.

- very diplomatic, sulligogs, i like it! To be fair, not mentioning these commands in the first place was a bit n00bish of me. On the other hand , the reason i didn't was because having looked through ifconfig et al, i saw nothing unusual or interesting so didn't bother.

Unfortunately, i still can't give you them (not in any useful form), because i arrived home to find someone had bought me a new wireless card as a present (w00t!), which has now been installed.

belkin 125mbps, broadcomm-based. euch, proprietary nastiness. but at least it works. :)

thanks for all your help anyway, sulligogs! keep it up mate - it's folk like you that make ubuntu what it is.
gnudoc

---

### Post by sulligogs on 2007-10-05
> **gnudoc said:**
> Unfortunately, i still can't give you them (not in any useful form), because i arrived home to find someone had bought me a new wireless card as a present (w00t!), which has now been installed.

belkin 125mbps, broadcomm-based. euch, proprietary nastiness. but at least it works. :)

thanks for all your help anyway, sulligogs! keep it up mate - it's folk like you that make ubuntu what it is.
gnudocHey gnudoc - glad to hear you're sailing!  Nothing worse than bashing your brains out on something when all you want to do is get on with the matter in hand, that is, browsing.

Live long and prosper, sir!  Over and out :)

> **mastergunner said:**
> Well got it BUT I can connect to the internet but it shows no signal strength. I am using a Netgear WG511v1 card. What gives?This has affected both you and gnudoc.  And to tell you the truth it breaks me heart.

When I first installed Ubuntu on two PCs and one laptop, all using Edimax wireless products (rt61 and rt2500 chipsets respectively), the two PCs were crashing like a couple of old 386s trying to run Vista.  And believe me, if you think that sounds bad you don't want to see my bald patch after tearing my skull out with a tin opener whilst trying to get my PCs working.

Bald patch has now been repaired.

Anyway, perhaps I've discovered from these posts that RuTilt will only work with my HOWTO on Edimax wireless cards.  If that is true then what a complete bummer.  Let's try one last thing...

Open up a terminal and do this:-

```
sudo ifconfig
```Enter your password if asked.  Then this after:-

```
sudo iwconfig
```And after entering your password again, this one last line:-

```
sudo iwlist scan
```With your password if asked.

After each one of these tell me what output you get from the terminal.  Just copy and paste it for me to see.  Make sure RutilT is up and running in the way you left it last.

Let's see if I can crack this cookie!  Or a bald patch might reappear :(

---

### Post by NotoriousTF on 2007-10-08
> **sulligogs said:**
> 
And now, NotoriousTF

Whooah!  Is everything now running *completely* fine???  How?  Was it that you was logged in with restricted access and someone pointed you to a quick fix or was it just some silly bug in Ubuntu?  I'm still intrigued by it.  Spill the beans!

And if all problems have been eradicated how well is your network now?  How long has it been running this way?  Tell me more!


Sorry for taking so long to get back to this. Well my post [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=562433"), pointed me to a bug report posted [_[COLOR="Blue"]here[/COLOR]_]("https://answers.launchpad.net/ubuntu/+question/11154") on launchpad.
It worked straight away for me. Something like this: (remember to remove the user name 'lex' and replace with your own!!)
```
rm ~/.config/autostart
mkdir ~/.config/autostart
sudo chown lex:lex .config/autostart
```

And that was it, all worked perfectly!
I'm still having a problem with RutilT connecting to the profile I created for connecting to my wireless network at home. Still connect to the network via the 'Site Survey' tab and enter the WEP each time. Any ideas? 
Also, is there a way to remove the entering a password on each boot? I have RutilT set-up to begin on startup, but on each boot it opens asking me to enter my password. Would be nice to get rid of that. 
Neither are major 'problems', but just little kinks I'd like to get rid of!

---

### Post by sulligogs on 2007-10-14
> **NotoriousTF said:**
> Still connect to the network via the 'Site Survey' tab and enter the WEP each time. Any ideas?
Hello there mate!

To tell you the truth I am a bit stumped by it really.  To eliminate any mishaps try setting the Name field and SSID field the same.  For example, when you click on the Profiles tab and edit your profile, you get the Wireless Setup tab.  In there it has on the left "Name" and on the right "SSID".  Set them the same as the SSID you use on your router to connect to.

Also, just thinking, use an SSID that uses simple characters.  Something like ABCDEF.  Set RutilT and your router to use that and see if it connects automatically.  Just a last resort, but I guess it won't do anything.

> **NotoriousTF said:**
> Also, is there a way to remove the entering a password on each boot? I have RutilT set-up to begin on startup, but on each boot it opens asking me to enter my password. Would be nice to get rid of that.
Hmmm.  That's a bit strange.  Did you follow absolutely everything in the HOWTO to the T?  On installation you have to explicitly use a parameter so that it doesn't ask for a password.  That is in step 3 of the HOWTO.

[SIZE=4]3[/SIZE]) Open up a terminal and change to the directory to the download on your desktop.  Enter in these commands:-

```
./configure.sh --launcher=nopasswd
make
sudo make install
```Enter your password if asked.

The "--launcher=nopasswd" parameter tells RutilT to bypass your passwords.

If you have done that then I think you should try uninstalling RutilT and then follow the HOWTO all over again.  What's that, you say?  How do you uninstall it?  Okay, okay!

Bring up a terminal window and change to the directory of the source code.  That is, for example, if you downloaded RutilT version 0.15 to your desktop then your source files will be on your desktop in a folder called RutilTv0.15

At the terminal enter "sudo make uninstall"  Enter your password if asked.  And there you go.  It's gone!  Before reinstalling keep the terminal window open and enter "sudo make clean".  Enter your password if asked.  This will erase any leftovers and prepare your next installation as if it was the first time being done.

Hope that helps at all.  If not, keep any tin openers away from your hair.  Just in case...

---

### Post by NotoriousTF on 2007-10-16
Thanks sulligogs , I'll get looking into all of that tonight!

---

### Post by nickpaton on 2007-10-16
Hi Sulligogs

Many thanks for this HOWTO which worked perfectly.

For the record using an Advent 7086 laptop installed with Feisty 7.04 and Asus WL-167g USB WLAN device.

Have plenty of signal strength over 2 floors and no crashes or lockups for the last couple of hours since I installed.

Many thanks once again.

Nick

---

### Post by sulligogs on 2007-10-23
Hello nickpaton,

That's fantastic to hear.  Out of all the posts on this thread you are the only who said straight away to say that it works.

What's more, yours is an Asus WL-167g USB wireless adapter so that lifts hopes a bit that RutilT works on not just my wireless hardware, but others as well.

Thanks ever so much for the feedback.  Hope there's been no problems since.

---

### Post by linyanam on 2007-10-31
Hi dear Sulligogs,
Thank you for your excellent post, with which I am able to connect to internet with serial monkey driver for RA73 chipset and WAP encryption.
But once in a while RUTILT does not show ip address. Some times it is corrected by restarting Ubuntu and sometimes by restarting my router. Sometimes nothing works. I just have to take time off try next day.
My windows is able to acquire Ip address and connect during these periods. It is not static IP.
Do you have any suggestions.
Thanks.

---

### Post by sulligogs on 2007-11-03
Hello linyanam :)

Good to hear you have mainly success from RutilT.

When you say you are using the serialmonkey driver for your RA73 chipset is it already provided with RutilT or have you compiled it yourself?

Also, does Windows "never" get this same problem of losing its IP address?

With my router, an EDIMAX one, I can't remember the exact model, I have to sometimes switch it off then on to be able to browse again and that is with a static IP address.  This problem happens under both Ubuntu AND Windows.

Evaluate if you get this problem under Windows and then come back to me.

Over and out!

---

### Post by bastikr on 2007-11-04
Hi all,
I'm experiencing some troubles with rutilt, but hopefully you can help me to get rid of them.
First thing is that everytime I choose a profile in the GUI and hit apply, the program crashes und I get the following output:

> 
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSterminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
basti@basti-desktop:~$ Listening on LPF/rausb0/00:11:09:4e:00:96
Sending on   LPF/rausb0/00:11:09:4e:00:96
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.160 -- renewal in 457667 seconds.


This is annoying, but since the network works afterwards, I can live with it.

The other problem is to start rutilt automatically at startup. I think if I do it the way it is described in this thread it will only run for one user (or I would have to do this for each user separately). It also seems like rutilt needs su rights to set up a connection, and this can't be done that way.
I tried to use the following startup-script (in /etc/init.d), but it doesn't work for any reason.

> 
#!/bin/sh
sudo rutilt -dp kr-net
 

Any ideas?

---

### Post by linyanam on 2007-11-05
Thanks Sulligogs for your reply.
Yes I did recompile rt73 driver from source.
My IP address problem may be related to my router.
The router seems to be connecting to net intermittently and works when i restart it.
Thanks a lot for your help.

---

### Post by sulligogs on 2007-11-10
Hello Everyone,

Well, this post has helped some and for others perhaps not so.  That's a shame, but I'd like to inform on something that I've done that ever since has given me rock solid performance for the past few days regarding my wireless network and my system's stability.

What have I done?  I did a fresh install of Ubuntu 7.10, codename Gutsy Gibbon.  And it has been like a breath of fresh air!

Suddenly, Network Manager now works with my RT61 chipset!  Not a single crash!  Additionally, I don't have to bother with the Keyring Manager either, like I had to with Feisty Fawn on my laptop.

The whole thing, I can honestly say, now "Just Works"!  Well Done, Ubuntu Team!

So, suffice to say, I won't be maintaining this post anymore.  Should anybody else feel the need to step in and help out then please do so.  Hope my step-by-step guide still has its uses!

Over and Out!

---

### Post by kevdog on 2007-11-10
Thats a shame you wont be maintaining the post anymore -- you've provided some very valuable information although not everyone had great results.  Needless to say I can tell you upgrading to gusty gibbon is not the cure all for all people, and the built in rtpci drivers do not work for everyone.  Compiling serial monkey sources still seem to be the rock stable fallback for most.

Thanks for your help

---

### Post by Ronin69 on 2007-11-13
A little background Kubuntu 7.10, RT61 wireless.  I am up and running with a connection using WEP.

Would like to have this automatically start on startup.  I have not ran through the process listed.  Wondered if there was a simple solution, such as, editing a file to contain the launcher=external ?

Thanks,

---

### Post by sulligogs on 2007-11-25
Hi Ronin69

Just popped in to see what was happening.  Saw your post and thought I would just query it.

I would strongly advise on running through the guide at the start of this thread.  That way if you do get unexpected results we can eliminate a dodgy rogue configuration file.

Try the guide.  You might like it :)

See how it goes,

Sulligogs

-------
Greetings to Alex Dover at monarchrecruitment.co.uk

---

### Post by TRANQU111TY on 2008-01-18
[solved]

---

### Post by Juhla Mokka on 2008-04-19
Hello, I hope somebody can help. I have spent weeks trying to get my laptop wireless sorted. With the help of this thread [http://ubuntuforums.org/showthread.php?t=400236&page=106](http://ubuntuforums.org/showthread.php?t=400236&page=106) I installed RT73 Linux driver and got a connection. However, I need GUI to switch networks etc.

Unfortunately I am having problems with RutilT setup. I was stuck in step 6 first line.

First I got a message 'permission denied' then I logged in as root and got 'bash: nameserver: command not found' and with sudo 'sudo: nameserver: command not found'. 
I went round this by doing the first line of step 6 by locating the file, opening it and adding a line myself. Then I did the second line of step 6.

I re-booted. Clicked RutilT and got a warning pop-up **[COLOR="Blue"]Critical Error : Data parsing error (1). Code : -41.[/COLOR]**

I clicked OK and it opened the program. Then I went to scan networks and the pop-up came again, when I clicked OK it closed the program.

**EDIT - So the main problem is the warning pop-up, I cannot do site survey scan. Secondly, did I do something wrong at the set-up?**

[B][COLOR="DarkOrange"]
Help?[/COLOR][/B] :(

---

### Post by jacl11 on 2008-05-10
Hey there!
I also have a wifi adaptor running on the rt73 module. When going through the tutorial (installing RutilT) I skipped the part with the 'sudo nameserver...'.

First, I just checked the contents of the resolv.conf and all was fine there was no need to change that. Same with the gateway part (2nd line of part 6 of the tutorial). The default gateway seemed to look ok (I assume kicking out network-manager does not influence your routing config).

RutilT seems to work quite fine for me. I haven't had any problems so far. Maybe you made a mistake in point 5 (are you sure named the devices in 'interfaces' correctly?).

Cheers!

---

