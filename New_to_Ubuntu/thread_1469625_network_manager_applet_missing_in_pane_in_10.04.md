---
title: "network manager applet missing in pane in 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ankur1990 on 2010-05-02
Hey i install ubuntu 10.04 this morning... A gud experience till that when i came to know that there in no nm (network-manager) applet in my panel as a result of which i m unable to connect to the wireless network......
can anybody plz help me in getting the nm applet on to panel so that i m able to carry on my work in the wireless network.
thanx for your help in advance :)

---

### Post by dalee on 2010-05-02
Hi,

Sounds like you don't have it setup yet. If you know your card is working, go to System: Preferences: Network Connections. There you can enter your router's connection name, SSID, and other needed information.

dalee

---

### Post by Georgie-o on 2010-05-02
This is the same problem I'm having.  Different wireless cards, reinstalled Ubuntu and the wireless applet still disappears at random.  I have to shutdown or log into another user account to connect.  The notifications panel is terrible.  You can't tweak it or add a new network manager to the panel.  If this problem persists I'm giving up on this release.  It is not stable - several lockups (black screen with a only cursor showing) when I switch users or log-out.  This is not ready for primetime, not even close.  They should have delayed it for months of testing.  After 5 years of ubuntu use and being a strong advocate, I'm considering to give up and switch back to Windows 7.

---

### Post by Sealbhach on 2010-05-02
Try adding the Indicator Applet to the panel, maybe that got removed for some reason.

.

---

### Post by Kangaroo_Style on 2010-05-02
> **Georgie-o said:**
> This is the same problem I'm having.  Different wireless cards, reinstalled Ubuntu and the wireless applet still disappears at random.  I have to shutdown or log into another user account to connect.  The notifications panel is terrible.  You can't tweak it or add a new network manager to the panel.  If this problem persists I'm giving up on this release.  It is not stable - several lockups (black screen with a only cursor showing) when I switch users or log-out.  This is not ready for primetime, not even close.  They should have delayed it for months of testing.  After 5 years of ubuntu use and being a strong advocate, I'm considering to give up and switch back to Windows 7.


Sadly this ^. I've been a strong advocate of Ubuntu, and in the past the only major issues I had was installing the restrictive-extras. Everything else just worked. This is the first release, where I'm getting a lot of bugs, and it doesn't "Just Work".  Now, I don't mind working on my computer, and usually I can resolve issues. However, this is my only computer so if this goes, I lose all my data. In the future I'm going to wait a month or two before upgrading. But 10.04 is nowhere near a stable release.

---

### Post by ankur1990 on 2010-05-02
> **Georgie-o said:**
> This is the same problem I'm having.  Different wireless cards, reinstalled Ubuntu and the wireless applet still disappears at random.  I have to shutdown or log into another user account to connect.  The notifications panel is terrible.  You can't tweak it or add a new network manager to the panel.  If this problem persists I'm giving up on this release.  It is not stable - several lockups (black screen with a only cursor showing) when I switch users or log-out.  This is not ready for primetime, not even close.  They should have delayed it for months of testing.  After 5 years of ubuntu use and being a strong advocate, I'm considering to give up and switch back to Windows 7.

i m having one more problem with 10.04... it is not showing me grub too...
no "grub loading and menu list" there......
plz help me

---

### Post by ankur1990 on 2010-05-02
> **Sealbhach said:**
> Try adding the Indicator Applet to the panel, maybe that got removed for some reason.

.

i tried that. itz opening a panel but that too without the nm applet........
feeling frustrated bcoz never faced such problems
plz help me guys 
thanx in advance

---

### Post by Sealbhach on 2010-05-02
Well, open a terminal and copy and paste this in:

```
nm-applet --sm-disable
```

It will start the applet. You can then manually add it to startup sessions.

If that doesn't work, just install wicd, it's a different network manager and is often more reliable.

.

---

### Post by ankur1990 on 2010-05-02
> **ankur1990 said:**
> i m having one more problem with 10.04... it is not showing me grub too...
no "grub loading and menu list" there......
plz help me

i resolved this by making changes in the /etc/default/grub ..........
its wrks now but the problem of the nm-applet still exsist after too much attempts too..
sad :(

---

### Post by ankur1990 on 2010-05-02
> **Sealbhach said:**
> Well, open a terminal and copy and paste this in:

```
nm-applet --sm-disable
```It will start the applet. You can then manually add it to startup sessions.

If that doesn't work, just install wicd, it's a different network manager and is often more reliable.

.

command still not wrking........
any more  suggestions ??????? waiting for that :( :confused:

---

### Post by Jim Shunamon on 2010-05-02
I have a similar problem also.The icon disappeared from my panel even though network manager is still running. I sometimes have to connect to other networks if I am at someone else's home etc. This makes for a tedious process without the ease that that icon provided. I also have had a lot of problems with packages not being downloaded due to dependency issues or md5 sums not matching. I have been using Ubuntu since the 6.06 LTS release, and although this is _**not**_ the first time I have encountered a shoddy release, for the first time I am considering switching to another distro. This release was certainly not stable enough to be released, and it is especially disturbing because this is a long-term support release. I am afraid that Ubuntu may be on its way to becoming the "Windows" of the Linux world. :( :( :(

---

### Post by Sealbhach on 2010-05-02
> **ankur1990 said:**
> command still not wrking........
any more  suggestions ??????? waiting for that :( :confused:

The other suggestion was to install wicd. It will handle your wireless connection. Just connect a wired connection and install wicd.

.

---

### Post by ankur1990 on 2010-05-03
> **Sealbhach said:**
> The other suggestion was to install wicd. It will handle your wireless connection. Just connect a wired connection and install wicd.

.
i don't know how to configure wicd....
will u please guide me on that so that it would automatically obtain the ip address :confused:

---

### Post by Sealbhach on 2010-05-03
> **ankur1990 said:**
> i don't know how to configure wicd....
will u please guide me on that so that it would automatically obtain the ip address :confused:

It should just handle your connection just like network manager, the only thing you need to do is put in the passphrase you got from your ISP. Click refresh and it should find all available networks.

.

---

### Post by ankur1990 on 2010-05-04
> **Sealbhach said:**
> It should just handle your connection just like network manager, the only thing you need to do is put in the passphrase you got from your ISP. Click refresh and it should find all available networks.

.

it showns unable to obtain the ip address.
what to do?

---

### Post by ankur1990 on 2010-05-04
Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

---

### Post by Sealbhach on 2010-05-04
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

Congrats and thanks for sharing your solution with others - I was stumped.:redface:

.

---

### Post by albert s on 2010-05-04
right click panel>add to panel>Notification Area

that done it for me.

---

### Post by ankur1990 on 2010-05-05
> **Sealbhach said:**
> Congrats and thanks for sharing your solution with others - I was stumped.:redface:

.

Hey no need of thanx buddy... 
After all sharing of knowledge is the main motive of OPEN-SOURCE :p

---

### Post by Troll_the_Great on 2010-05-05
Hello guys!

I have the same problem (network applet gone) and rather then opening a new thread I will continue this one (even though I see is marked as solved). I tried editing the nm-system-settings.conf and I got the applet back, but the problem was that I lost my internet connection. The internet wire was plugged in, but the applet appeared as disconnected. So, I reverted the changes, I have internet again, but no applet. Any suggestions for me?

---

### Post by ankur1990 on 2010-05-05
> **Troll_the_Great said:**
> Hello guys!

I have the same problem (network applet gone) and rather then opening a new thread I will continue this one (even though I see is marked as solved). I tried editing the nm-system-settings.conf and I got the applet back, but the problem was that I lost my internet connection. The internet wire was plugged in, but the applet appeared as disconnected. So, I reverted the changes, I have internet again, but no applet. Any suggestions for me?
 u r using wired network or wireless?.......
I m running wired network of mine through "pppoeconf" and its works for me

---

### Post by Troll_the_Great on 2010-05-05
> **ankur1990 said:**
> u r using wired network or wireless?.......
I m running wired network of mine through "pppoeconf" and its works for me
I use the exact same settings: wired network through pppoeconf.

---

### Post by ankur1990 on 2010-05-05
> **Troll_the_Great said:**
> I use the exact same settings: wired network through pppoeconf.

ok i  m nt sure but in  my case when i connect to wired using pppoecong it uses eth0 interface hence i need to configure the sudo pppoeconf again while in case of wireless it uses eth1 interface so againg i have to reconfig it...... it depends on your interface i think...
as i sadi i m not sure abt it its my opinion but do concern pthers too :):)

---

### Post by Troll_the_Great on 2010-05-06
Any suggestions for me?

---

### Post by Troll_the_Great on 2010-05-08
.....

---

### Post by iamunknown on 2010-05-18
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D
Thanks for your posting, it helped my ubuntu too :). I published your solution at the German community ubuntuusers.de ( [http://forum.ubuntuusers.de/topic/vorschlag-falls-nm-applet-verschunden-ist/#post-2493277](http://forum.ubuntuusers.de/topic/vorschlag-falls-nm-applet-verschunden-ist/#post-2493277) )!

---

### Post by joccpe on 2010-05-19
> **albert s said:**
> right click panel>add to panel>Notification Area

that done it for me.

That done it for me too ! 
I had tried almost everything else with no result. 
I had removed the "Notification Area" before, but wasn't  unaware of the consequences as I didn't loose wireless connectivity immediately.
Thank you very much.

:)

---

### Post by chicken159 on 2010-05-20
As someone said early in this thread, Ubuntu 10.04 is NOWHERE NEAR STABLE.
- I'm having the indicator applet issue with both missing nm-applet, AND battery level appearing twice today; also broadcom wireless on a mini 10v (which is 1 of the very few machines to come pre-installed with Ubuntu!!!) just does NOT work. 

AND NOBODY SEEMS TO BE TAKING IT SERIOUSLY - are we back to the 'well its free so what do you expect?' days??

Apologies for not being entirely on-topic, but I'm losing patience here and I've been fully converted for 4 years...whats happened? The ball has not just been dropped, its been kicked into the long grass and lost!?

---

### Post by kopcicle on 2010-05-22
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

werks for me ! tnx

---

### Post by Rob Maddison on 2010-05-24
Thanks - I never knew about the notifications pane in systray and it had got turned off. I've been looking for ages without popping in here but turning it back on has solved my problem with nm and the battery monitor :-)

---

### Post by ankur1990 on 2010-05-25
> **iamunknown said:**
> Thanks for your posting, it helped my ubuntu too :). I published your solution at the German community ubuntuusers.de ( [http://forum.ubuntuusers.de/topic/vorschlag-falls-nm-applet-verschunden-ist/#post-2493277](http://forum.ubuntuusers.de/topic/vorschlag-falls-nm-applet-verschunden-ist/#post-2493277) )!

Thanks for promoting the solution fella bu t i m still wondering the solution of the "toll-the-great" problems,. so plz help him guys after all forums are about the help. 
Thanks :KS

---

### Post by bhadotia on 2010-05-27
> **ankur1990 said:**
> Thanks for promoting the solution fella bu t i m still wondering the solution of the "toll-the-great" problems,. so plz help him guys after all forums are about the help. 
Thanks :KS

You might consider removing the [SOLVED] tag from your thread title. This will have more people visiting this thread (as we generally tend to ignore the solved threads) and thus this might help troll with his problem..

---

### Post by umouklo on 2010-05-28
Why is this marked as solved?  There was no answer that concisely explained how to solve this.  I am having the same problem.  This is a major bug and a show stopper.  Everyone needs to control access to networking.  Why not just have the network item in the add to panel app to fix this when it occurs?

---

### Post by umouklo on 2010-05-28
Hello - I tried the "solution" and got the following results:

error after typing the edit command:

lorieu@umouklo-laptop:/etc/NetworkManager$ sudo edit nm=system-settings.conf

Warning: unknown mime-type for "nm=system-settings.conf" -- using
"application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

I got around this by using gksudo gedit nm=system-settings.conf

However, when I type:  killall nm-system-settings

I get:  nm-system-settings: no process found

After rebooting the userid that had the problem appeared to be fixed.  However, the userid I had that was working lost both the battery and network icon from the panel.

STILL NO SOLUTION FOR ME.  I NEED BOTH IDs TO WORK.  THE PANEL NEEDS A LOT OF DEBUGGING IN 10.04.  IS THIS GOING TO HAPPEN?

---

### Post by umouklo on 2010-05-28
All - After mucking around with this I discovered the following:

I can fix the battery indicator by going to SYSTEM->PREFERENCES->POWER MANAGEMENT General tab and clicking the "Always display an icon" button.

The Network Manager icon has something to do with switching users.  Even if you set both users to be able to manage wireless connections when you create them only the first user logged in will get the icon.  I STILL THINK THIS IS A BUG AND IT IS CONFUSING AND SHOULD BE FIXED.

---

### Post by ankur1990 on 2010-05-30
> **umouklo said:**
> Hello - I tried the "solution" and got the following results:

error after typing the edit command:

lorieu@umouklo-laptop:/etc/NetworkManager$ sudo edit nm=system-settings.conf

Warning: unknown mime-type for "nm=system-settings.conf" -- using
"application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

I got around this by using gksudo gedit nm=system-settings.conf

However, when I type:  killall nm-system-settings

I get:  nm-system-settings: no process found

After rebooting the userid that had the problem appeared to be fixed.  However, the userid I had that was working lost both the battery and network icon from the panel.

STILL NO SOLUTION FOR ME.  I NEED BOTH IDs TO WORK.  THE PANEL NEEDS A LOT OF DEBUGGING IN 10.04.  IS THIS GOING TO HAPPEN?
dude it not edit nm=system-settings.conf its gedit nm-system-settingd.conf......
plz look up to the solution carefully and i have marked it solved bcoz i m the creator and my problem got solved using that solution........

---

### Post by bhadotia on 2010-06-06
Here's the bug report for this problem:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/456468](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/456468)
Just hope that they get it fixed soon.

EDIT:
Sorry, but this turned out to be the wrong bug report :confused::p. here's the right one:[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/577678](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/577678).
It also describes an alternate method for getting the nm-applet back.

---

### Post by dkuhlman on 2010-06-08
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

This fix worked for me.

Thanks.

- Dave

---

### Post by jomex on 2010-06-10
i'm having the same issue: no indicator  applet for network


 interestingly, when i start System -> Preferences -> Network Connections i  don't see any connections even though i'm connected. i did the ste__ps described above (managed=true). i then get a "wired connection" in "Network Connections" called  "ifupdown (eth0)" which i can't edit and it is set as "used: never"(?).


when i do "gksudo gedit /etc/network/interfaces" and edit it to
    auto lo
    iface lo inet loopback


the connection is called "Auto eth0" "used: never".

---

### Post by stefcep on 2010-06-10
> **ankur1990 said:**
> dude it not edit nm=system-settings.conf its gedit nm-system-settingd.conf......
plz look up to the solution carefully and i have marked it solved bcoz i m the creator and my problem got solved using that solution........

the solution says > hey Fellas
nm-applet problem solved
Solved it own after searching long.
Method---
in the terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result 

I had to go into /etc/NetworkManager/ and then right click on "nm-system-settings.conf"->properties->open with->text editor.

I then sudo gedit /etc/NetworkManager/nm-system-settings.conf and then changed "managed=false" to "managed=true" and then save it.  To get the applet to appear on the top panel, I had to put mouse pointer over top panel, right click->add to panel->Notification Area.

---

### Post by ankur1990 on 2010-06-10
> **jomex said:**
> i'm having the same issue: no indicator  applet for network


 interestingly, when i start System -> Preferences -> Network Connections i  don't see any connections even though i'm connected. i did the steps described above (managed=true). i then get a "wired connection" in "Network Connections" called  "ifupdown (eth0)" which i can't edit and it is set as "used: never"(?).


when i do "gksudo gedit /etc/network/interfaces" and edit it to
    auto lo
    iface lo inet loopback


the connection is called "Auto eth0" "used: never".

if u want to run wired network you can do it with pppoeconf file. it will scan your port and then will ask ur username and password....... then read the instruction and ready to go for wired networking :):KS

---

### Post by Tig3rzhark on 2010-06-10
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

It is unfortunate that this solution didn't work for me.

I had an internet connection on one of my computers yesterday and now...I can't even connect to my wireless router because the nm-applet refuses to appear on the upper panel.  It's a good thing that I have a backup computer.  My netbook hasn't experienced that problem thankfully.  This is coming from the desktop version of 10.04.

---

### Post by stefcep on 2010-06-10
> **Tig3rzhark said:**
> It is unfortunate that this solution didn't work for me.

I had an internet connection on one of my computers yesterday and now...I can't even connect to my wireless router because the nm-applet refuses to appear on the upper panel.  It's a good thing that I have a backup computer.  My netbook hasn't experienced that problem thankfully.  This is coming from the desktop version of 10.04.

try this

I had to go into /etc/NetworkManager/ and then right click on "nm-system-settings.conf"->properties->open with->text editor.

I then sudo **gedit** /etc/NetworkManager/nm-system-settings.conf and then changed "managed=false" to "managed=true" and then save it. Reboot .  To get the applet to appear on the top panel, I had to put mouse pointer over top panel, right click->add to panel->Notification Area.

OR

try system->preferences->network connections, choose wired/wireless/mobile broadband/dsl->select your connection then edit or add a connection, tick connect automatically.  That should at least give you an internet connection.

---

### Post by Tig3rzhark on 2010-06-10
> **stefcep said:**
> try this

I had to go into /etc/NetworkManager/ and then right click on "nm-system-settings.conf"->properties->open with->text editor.

I then sudo **gedit** /etc/NetworkManager/nm-system-settings.conf and then changed "managed=false" to "managed=true" and then save it. Reboot .  To get the applet to appear on the top panel, I had to put mouse pointer over top panel, right click->add to panel->Notification Area.

OR

try system->preferences->network connections, choose wired/wireless/mobile broadband/dsl->select your connection then edit or add a connection, tick connect automatically.  That should at least give you an internet connection.

Ok, I tried it again.  The first time, I had to wait a long time before I established a connection to my router again.  The second time, was no different.  I had to wait at least a half hour, so there is a bug with network manager.  Hopefully someone has already put out a bug report.  

When I finally get the connection established, I'll switch to wicd until there is a permanent solution to this bug.

---

### Post by jomex on 2010-06-11
notification area now works again when i add it to the panel, thank you all! :)

solution: after having done all prior steps, re-add the **Notification Area** again **NOT** **Indicator Applet**

---

### Post by arkmundi on 2010-06-12
> 
Originally Posted by ankur1990 View Post
Hey Fellas
nm-applet problem solved
Solved it own after searching long.
Method---
in the terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result 


This fix worked for me.  I believe its a combination of making sure that the *Notification Area* is on the panel, as well setting "managed=true" in /etc/NetworkManager/nm-system-settings.conf file as ankur suggests.

---

### Post by wizard_karan on 2010-06-26
hey 

thanks a lot ankur1990, i had been facing this problem for sometime in Ubuntu 10.04 server edition and i followed your instructions exactly and it helped me get back the nm-applet icon in the system notification area.

This disappearance of the network manager icon from the notification area is a frequent bug and usually happens with me after a big update(300Mb or greater approx.). After each such update we the users are bothered by this annoyance.

I will try to find out why this occurs and how can it be solved.

thanks again
Karan Pratap Singh

P.S.
for those that are getting the icon but not the internet check your internet settings by typing: "sudo vi /etc/network/interfaces" (without the quotes) and see whether your eth0 settings are ok(if you are using a wired connection)

if you want a dynamic ip to be set everytime you connect your computer to your modem, then the following settings should be thier in the interfaces file:

auto eth0
iface eth0 inet dhcp

if you want a static ip to be assigned for your pc then write the following in the interfaces file:
auto eth0
iface eth0 inet static
address "the ip address you want without the quotes"
netmask 255.255.255.0

after this save the interfaces file and type the following in the terminal:

sudo ifdown eth0(assuming that your interface device is eth0)
sudo ifup eth0

Hope this helped!!

---

### Post by neglesaks on 2010-06-29
> **umouklo said:**
> Hello - I tried the "solution" and got the following results:

error after typing the edit command:

lorieu@umouklo-laptop:/etc/NetworkManager$ sudo edit nm=system-settings.conf

Warning: unknown mime-type for "nm=system-settings.conf" -- using
"application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

I got around this by using gksudo gedit nm=system-settings.conf

However, when I type:  killall nm-system-settings

I get:  nm-system-settings: no process found

After rebooting the userid that had the problem appeared to be fixed.  However, the userid I had that was working lost both the battery and network icon from the panel.

STILL NO SOLUTION FOR ME.  I NEED BOTH IDs TO WORK.  THE PANEL NEEDS A LOT OF DEBUGGING IN 10.04.  IS THIS GOING TO HAPPEN?

I agree. I got the nm-system-settings not found as well, and my problem remains even after editign the conf file as stated.

The quoted solution doesn't work for me - I'm having all sorts of panel notification applets missing - network manager, parcellite, Gnome DO...

---

### Post by djscribe on 2010-07-20
1st things 1st...here's what I'm working with:

MoBo: Asus M4A89GTD PRO USB3 - [No OC]
CPU:  AMD Phenom II X6 1090T 3.2gHz [No OC]
RAM:  4GB [No OC]
Media: Dual WD Black Caviar 640GB 6gb/s 64MB Cache Drives
LAN: Onboard Realtek 8111E/8168 GigaBit [Native adapter on this Asus board]
VGA: Onboard ATI HD4290 [Native adapter on this Asus board] [Again, no OC]

                           [OC=OverClocking]

That having been said, I'm running into something that threw a wrench into all my workings with netmgr/networking. Have been installing a Dual Boot with Vista and Lucid, straight factory setup, no eyecandy, nothing special. Ubuntu installs fine, reboots, comes up fine once or twice, then netmgr bails irrecoverably. Tried:

- Enabling it in Startup, since it would default to disable
- Editing the NM-SYSTEM-SETTNIGS.CONF file, false 2 true - using both sudo and gksudo, to no avail.    
- Eventually started getting UNKNOWN MIME-TYPE when attempting to further edit this conf file.  
- Installing on both separate drives on their own, same results.


Finally, I broke down and used an old 40gb Quantum drive. Installed Lucid on its own, and works like a charm. I mean everything; restricted drivers, bluetooth, compiz, apps, cairo dock, even wireless! I was able to dual boot on a Dell Optiplex, but using XP, not Vista. 

So, I will be wiping it clean, and installing dual environment on this drive Quantum drive since I don't wanna lose my only clean installs on this Dell, to start narrowing things down from there - maybe even use XP instead of Vista. Not sure if it's Vista, the drive/cache size limitations, tried both 6, 3gb/s and AUTO settings on BIOS , Loaded Default Settings as well - still working on it.

Of course, any input would be greatly appreciated. 

Good things, everyone
-Scribe

---

### Post by 1915flyer on 2010-08-05
I am having the same problem. The wireless network indicator was there this morning. When I started the computer this evening, no indicator. The applet was running and I could get on-line.

I changed the MANAGED to false. Killall didn't work. No change after rebooting.

---

### Post by kwestrom on 2010-08-17
How does one re-add the network connection applet in the system-preferences area? I have no network connections applet to open up when i go into the system-preference area. Furthermore, i have encountered numerous spots that indicate the kdelibs5 is missing from my system. Is there anyway to get it readded without fully reinstalling my full system? 
Thanks in advance for any assistance rendered on this problem.

---

### Post by will81 on 2010-08-24
Same problem.  Network Manager applet was there (and had been for a month or so) but was gone when I rebooted.  managed=true; Indicator Applet present; Notification Area present; user in netdev group.  Grr!

EDIT: Editing /etc/network/interfaces and commenting out "auto eth0" worked in the end.

---

### Post by fmurrieta on 2010-09-03
I had apparently the same problem, I tryed everithigng you've suggested with no luck.

I have a bunch of users in this machine.

I've prevoiusly checked the "Available to all users" checkbox for all the wireless networks I use.

After 2 months I've got my problem solved:
 
All I need to do to fix the missing nm-applet was1.- Login as your first user
[INDENT]2.- Go to Edit Network Connections- 
3.- Select your first network
4.- Click the **Edit** button
5.- Unckeck the "**Available to all users**"
6.- Click **Apply**
7.- Repeat for all connections
8.- Repeat for all users
[/INDENT] Hope thi*s can save you* some time!


Fernando Murrieta

---

### Post by vijaybilgoji on 2010-09-22
Restore it by the following way

gksudo gedit /etc/NetworkManager/nm-system-settings.conf

look for this two lines
[ifupdown]
managed=false

change it to
managed=true

---

### Post by t6ti00 on 2010-09-23
Other solution could be this (worked for me):

1) Remove the following folder:

/home/user/.gconf/apps/panel

2) Logoff.

3) Login back.

4) There it is! Then customise the panels again.

---

### Post by jlemonier on 2010-09-26
> **Georgie-o said:**
> This is the same problem I'm having.  Different wireless cards, reinstalled Ubuntu and the wireless applet still disappears at random.  I have to shutdown or log into another user account to connect.  The notifications panel is terrible.  You can't tweak it or add a new network manager to the panel.  If this problem persists I'm giving up on this release.  It is not stable - several lockups (black screen with a only cursor showing) when I switch users or log-out.  This is not ready for primetime, not even close.  They should have delayed it for months of testing.  After 5 years of ubuntu use and being a strong advocate, I'm considering to give up and switch back to Windows 7.

I agree completely!!

I was on Ubuntu 8, upgraded to 10.04 and now I have 2 issues that make me ready to jump to Win 7 also:
1) minor - Screen resolution for Dell 17" will not set at 1440/900 correctly - fine in Ubuntu 8 with some config work of course.  Can only get to 1280x854 now.

2) show-stopper - nm-applet won't f&*^ing show up.

So many posts saying where it is or that it isn't started.  Come on ... anybody surviving and attempting to run Ubuntu or any linux can do a ps -ef, probably fix compilation problems, etc.

I have tried vpn client which won't compile.  Tried 4 patches but none work on 10.04.  I wish I could have this command line option back instead of this garbage, non-existent nm-applet.

Tried KVpnc also since nm-applet won't appear.  No luck there either but at least something was trying to use the cisco config and attempt.  It asked me for the group password even though the enc_GroupPwd is in the pcf file.  Every other client seems to understand this and not prompt for it.

Now to find the code inside of nm-applet so we can connect to Cisco VPN in 10.04 directly.

WTF ... awful.

---

### Post by ivany4 on 2010-11-09
**ankur1990**, thanks.
i have distributiv Rosinka (aka Mint 9), kernel 2.6.32-25.
and helped me to your way of

---

### Post by Jonatty on 2010-11-09
THANK YOU Sealbhach!
I, too, have had no luck whatsoever getting Network Manager applet to appear, and I've been jumping through terminal hoops left and right.  Your suggestion of installing the Wicd Network Manager was perfect!  I didn't need the network manager applet icon in the system tray, anyway.  I just wanted my wireless to work again.  You saved me so much hassle!  I was seriously considering reverting back to Ubuntu 6.06!

---

### Post by loopzilla on 2010-11-09
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

Big thanks !
I spent about one hour with searching why my wifi isn't working ...
Your post really helps me !

---

### Post by Reeal on 2010-11-16
> **t6ti00 said:**
> Other solution could be this (worked for me):

1) Remove the following folder:

/home/user/.gconf/apps/panel

2) Logoff.

3) Login back.

4) There it is! Then customise the panels again.
Big thanks !
This solution worked for me.

---

### Post by jjuup on 2010-11-17
I have the same problem. None of the suggestion here or in any of the links worked for me. (Ubuntu 10.10 here)

I have 2 accounts on this laptop, my wife (user1) and me (user2). The network indicator works in her user1 profile, also bluetooth indicator is there and turns bluetooth off. However user2 the network manager is missing so I can not change wifis or turn off bluetooth. Also, When the laptop is turned on, one has to first log on as user1 for the wifi to start and then switch users, else wifi will be off... 

This is a major problem and this thread shoud NOT be marked SOLVED as none of the suggestions solve the problem.

Thank you everybody for the effort thou!

---

### Post by noamik on 2010-11-26
> **ankur1990 said:**
> Hey Fellas
then in the terminal type "killall nm-system-settings"
and then reboot......

Haven't read what followed, but easier is to edit then just restart the NetworkManager:
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
Now type "sudo /etc/init.d/network-manager restart" and enjoy your icon ...
This will work for Ubuntu 10.04 unless you messed with your NetworkManager-Installation.

---

### Post by amjjawad on 2010-12-11
WHAT A MESSED UP THREAD!

Can the OP confirm WHAT was the "exact" solution for this issue?
Is it: [http://ubuntuforums.org/showpost.php?p=9236722&postcount=16](http://ubuntuforums.org/showpost.php?p=9236722&postcount=16) ??

Please confirm.

[B][SIZE=5][COLOR=Red][SIZE=3]For anyone else:
Please, do yourself a favor and do everyone here a favor and start*_ YOUR OWN THREAD_*, PLEASE if you have similar issue.[/SIZE]
[/COLOR][/SIZE][/B]

I'm trying to help someone and I found this thread. I spent more than 30mins now and I didn't even finish reading and can't understand what's going on. Why you afraid of starting new thread?
It this thread is marked SOLVED from Page2 so why you keep posting?????

Please don't get me wrong, I'm not trying to offend anyone but it's so hard for someone who's looking for something and can't find it because it's a mess :(

Thank you!

---

### Post by wcorey on 2010-12-24
I believe when people open an issue (open a thread) it should be for a single issue, not a laundry list. That way, if people find it via google they don't waste their time by seeing someone, perhaps the original author, kidnapped the thread by saying "I've got this other problem".

That said, my nm-applet icon is gone from the top panel. This on 10.10.

I was trying to add / configure eth1. Over the course of trying to do that the icon changed from a square with the cord at the bottom to twin terminals. It later changed back and then, finally, failed to appear on the panel. When trying to start it manually, it says it is already running and it shows as programs to start at boot time.

amjjawad - yes that fixed it.. works in 10.10 as well.. I've been in software dev and support for a long time and I have to disagree with you. Effectively though I am actually agreeing. 

For others that have PRECISELY the same problem do NOT open another thread....and do NOT enter, ME TOO, just follow the thread. If the thread dies, then open your own. When one says "me too" or, ESPECIALLY "I have another problem" then you are just polluting the original thread which get everyone irritated.

---

### Post by tushar maroo on 2010-12-24
may be this site can help you out......[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)

---

### Post by josepaul on 2011-01-18
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

dude ty so much, been trying to get this to work for so long!

---

### Post by okos on 2011-03-06
I tried all of the above and none worked for me.
I switched from WICD to Network Manager. My reasons are irrelevant to this thread other than I could not get the NM applet to appear on the task bar.

This is what worked for my by shear accident:

I tried adding the notification applet as others had posted and it did not work for me. I could see tiny lines on the bar where I added the notification applet multiple times.

To clean things up, I removed all of the tiny lines from the task bar.

The last set of lines also removed the HP icon. I thought, "I am making this an even bigger problem!"

So I added the notification applet one more time after cleaning things up. Wala! Not only did the HP icon come up but also the Network Manager came up!

I determined that the notification applet will not work if posted multiple times. Only the first addition of the notification applet worked. Since I already had the notification applet up displaying the HP icon, adding it again was not going to display the Network Manager. It was only after accidentally removing all postings of the notification applet did everything actually work.

---

### Post by Baji P. on 2011-05-09
> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

Thanks, exactly what I needed.

I created the problem in the first place by selecting static IP instead of letting the installer configure for DHCP.

---

### Post by Baji P. on 2011-05-09
> **Sealbhach said:**
>  [...]

If that doesn't work, just install wicd, it's a different network manager and is often more reliable.

.

I installed wicd with *aptitude install wicd* and it brought a network manager icon on the panel rightaway, thanks for that tip.

When I went into config options for wicd, I also found that it detects multiple access points with the same SSID, which is pretty cool since most Network Managers in Linux & Windows don't do that.

However, wicd stumbled with my wpa-psk config so I removed the pkg. Original problem of missing nm icon on panel was solved by changing to *managed=true* in nm's config file.

thnx.

---

### Post by salemboot on 2011-12-17
There are three 'indicator applets' :
1. Indicator Applet
An indicator of something that needs your attention on the desktop.

2. Indicator Applet Complete (installed from synaptic)
A unified applet containing all of the indicators.

3. Indicator Applet Session
A place to adjust your status, change users or exit your session.


There is also an applet called, "Notification Area"
It's description is: Area where notification icons appear

The problem with the applets disappearing happens after updates to 10.04.  "Indicator Applet Session" gets graphic problems and you have to kill and reload it.

Adding an entry for   "  nm-applet --sm-disable  " to System//Preferences//Startup   does solve the problem for the wifi applet.

---

### Post by PROFESONE on 2012-03-24
OK OK OK!!!!!  Please pay attention.  

go to System >> Preferences >> Startup Applications

Scroll down until you see the NetworkManager icon.

Click and drag it to the menu bar on your screen.

Make sure you give it the right command you want in the properties.

You should be ok.

PROFESONE

---

### Post by aaronLund on 2012-09-10
DAMN!

I switched themes and my network manager applet is totally gone.

I did the above trick and now it's showing up like a wireless connection (wireless icon) and I don't even have a wireless card in this thing.

How do i get on my work's vpn now???

EDIT:
Fixed it.

Just gotta add the 'notification area' and all's well.

DAMN!

---

### Post by lorne1525 on 2012-11-12
I just found another spot that could make the indicator disappear... I couldnt figure out why the root account had the indicator, but my limitted user account did not..so I did some digging    

cat ~/.config/autostart/nm-applet.desktop    

[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=false
X-Ubuntu-Gettext-Domain=nm-applet

I moved that file out and if fixed it,   
code:    

sudo mv ~/.config/autostart/nm-applet.desktop ~/.config/autostart--nm-applet.desktop.bak    


[https://mail.gnome.org/archives/networkmanager-list/2011-May/msg00145.html](https://mail.gnome.org/archives/networkmanager-list/2011-May/msg00145.html)

---

