---
title: "Why don't you give it a try to Network Manager 0.7.0 svn ?   Guide to update"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Kosimo on 2008-07-03
I found a very useful post on planet about how to test the latest Network Manager 0.7.0 svn witch is very very easy to install in Hardy.

Just go here: [https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

Add those two repos and update/upgrade your system. 
Then restart

And start enjoying new Network Manager! I've been waiting for ages! With minor graphics change it have MANY new features.

Manual IP, DHCP with manual DNS, saving passwords,  VPN!!, you can save a wireless preferred list, Mobile Broadband, (use your cell!), a DSL ppp connection... And a more sensible Wireless discovery list

Guys, this rocks.  And even being a svn build I had no issues using it.

I strongly recommend to give it a try.


EDIT: If you're using Hardy, make sure you choose HARDY repos!!

---

### Post by Kosimo on 2008-07-03
I made some screenshots.

[IMG]http://kosimo.googlepages.com/Screenshot.png[/IMG]

[IMG]http://kosimo.googlepages.com/Screenshot-1.png[/IMG]

[IMG]http://kosimo.googlepages.com/Screenshot-EditingAutolasso-1.png[/IMG]

[IMG]http://kosimo.googlepages.com/Screenshot-2.png[/IMG]

[IMG]http://kosimo.googlepages.com/Screenshot-3.png[/IMG]

[IMG]http://kosimo.googlepages.com/Screenshot-5.png[/IMG]

---

### Post by the yawner on 2008-07-03
Finally, DHCP with manual DNS. That bothered me a lot whenever I use a DHCP network. How Ubuntu kept on fighting me over my choice of DNS aside from the ones provided by the network.

---

### Post by mech7 on 2008-07-03
A prefered wireless list that's about time :)

---

### Post by Mr. Picklesworth on 2008-07-03
Hey, quick question:
In the Edit dialog for a connection, there is a checkbox labelled "system setting". What does this do? Does that mean it will automatically connect from the login screen? (I was just thinking that we need a little applet area on GDM and some infrastructure for system-wide sessions that works the same as GNOME's existing session system. Would be interesting).

Should probably also be checked whether people are aware that the label there is horribly cryptic...
Pretty cool that I can set the MAC address and such. Just hoping that they reorganize these config dialogs, since they are not very straight-forward from a user interface standpoint. (From the perspective of those who don't know half the options in that "Wireless" tab, they're making ifconfig / iwconfig look easy).

---

### Post by zachtib on 2008-07-03
Wow...

That looks really nice, I'm debating whether I want to risk messing up my networking.  Last time I tried 0.7, it broke everything.

How stable is it?

---

### Post by Kosimo on 2008-07-03
> **zachtib said:**
> Wow...

That looks really nice, I'm debating whether I want to risk messing up my networking.  Last time I tried 0.7, it broke everything.

How stable is it?

Rock Solid. No issues at all.  Give it a try! ;)

---

### Post by Kosimo on 2008-07-03
> **zachtib said:**
> Wow...

That looks really nice, I'm debating whether I want to risk messing up my networking.  Last time I tried 0.7, it broke everything.

How stable is it?

By the way if you upgrade, let us know what do you think about it! ;)

---

### Post by zachtib on 2008-07-03
> **Kosimo said:**
> Rock Solid. No issues at all.  Give it a try! ;)

> **Kosimo said:**
> By the way if you upgrade, let us know what do you think about it! ;)

OK, after work today I'll give it a go

---

### Post by phaed on 2008-07-03
I intalled it.  Works fine.  Also got rid of the network manager errors that I got on shutdown.

---

### Post by Polygon on 2008-07-03
thank you so much for this, this has completely solved my wireless troubles with my laptop (half the time the wireless would refuse to connect, but now it connects almost instantly)

---

### Post by smbm on 2008-07-03
All peachy here.

Cheers.

---

### Post by Kosimo on 2008-07-03
We had a Network Manager update an hour ago (or so) just refresh your sources if you want to have the latest one!

---

### Post by smbm on 2008-07-03
Nothing here yet...

---

### Post by Kosimo on 2008-07-05
After three days using it: Something I can tell is that now Network Manager finds more wireless networks than before.  It is maybe more sensible?

And by the way, I had 0 issues.

;)

---

### Post by Kosimo on 2008-07-06
Can any admin pleeeeeeease move this 3rd from Community Cafe to Network and Wireess section? I tried contacting two of them but I had no answer :(

---

### Post by HansKisaragi on 2008-07-06
Cool, just updated .. thanks for the link.

---

### Post by sportman1280 on 2008-07-06
0.7.0 works great in the hardy repository. make sure you dont try to use the intrepid one because of dependences.

---

### Post by mech7 on 2008-07-06
:( Awww i updated it.. and now it doesn't recognize my wireless network card in laptop.. So no inteernet, anybody know how i can get it back or at least the old one :(

I have Intel Pro Wireless 2200 BG

---

### Post by Polygon on 2008-07-06
uninstall it , remove the repos and then reinstall it.

and be sure to submit a bug report as well ;)

---

### Post by HansKisaragi on 2008-07-06
> **mech7 said:**
> :( Awww i updated it.. and now it doesn't recognize my wireless network card in laptop.. So no internet, anybody know how i can get it back or at least the old one :(

I have Intel Pro Wireless 2200 BG

Did you reboot? 

Remove it, remove the repos you added in software source, then reinstall the old one from apt-get/synaptic

---

### Post by vikramaditya on 2008-07-06
> **phaed said:**
> I intalled it.  Works fine.  ***Also got rid of the network manager errors that I got on shutdown.***
Now, *that's* worth a looksee! :)

---

### Post by OldTimeTech on 2008-07-06
Interesting...I did the upgrade and update and my dialog boxes look the very same as what I had, plus my nm-applet is still showing 0.6.6

So what didn't I do that I should have?????

---

### Post by HansKisaragi on 2008-07-06
> **OldTimeTech said:**
> Interesting...I did the upgrade and update and my dialog boxes look the very same as what I had, plus my nm-applet is still showing 0.6.6

So what didn't I do that I should have?????

Reboot, i had to .. then the network manager will show up again.

---

### Post by OldTimeTech on 2008-07-06
Viiral, Thanks so much....worked like a dream!!!

---

### Post by Rotarychainsaw on 2008-07-06
Seems like vpn is not supported yet?

---

### Post by smartboyathome on 2008-07-07
You don't have to reboot, just run alt-f2 gksudo killall nm-applet then run nm-applet. That will start up the new network manager.

---

### Post by aktiwers on 2008-07-07
Looks very nice..  Im installing right now :)

---

### Post by mech7 on 2008-07-07
> **Polygon said:**
> uninstall it , remove the repos and then reinstall it.

and be sure to submit a bug report as well ;)

omg how without internet connection :(

---

### Post by Kosimo on 2008-07-07
> **Rotarychainsaw said:**
> Seems like vpn is not supported yet?

Yes, looks like.
Being a svn I guess that soon or later this option will be activated.

---

### Post by keiichidono on 2008-07-07
Does this fix the problem that didn't allow you to have autologin enabled while using the gnome keyring to autologin to wifi? If so, i'll take a look.

---

### Post by aktiwers on 2008-07-07
I dont think so..  besides from that I really like it so fare.
And it seams very stabil

---

### Post by vikrant82 on 2008-07-10
All I want from network-manager is to automatically connect to preferred wirless point after a disconnect due to lets say,power outage, which for some strange reasons it can't seem to support.

If wireless point is down and if it can't connect, it stays on password popup sceen, and expects to manually click "Connect", to restore connectivity.

Back to WICD, until network-manager starts to restore my wirelss connection as soon as wireless point is back in range.

---

### Post by kevin11951 on 2008-07-10
will this be the default in intrepid (sorry if this was said already, i didn't have time to search the whole thread)

---

### Post by dracule on 2008-07-10
my current one works fine so no thank you.

---

### Post by aktiwers on 2008-07-10
> **dracule said:**
> my current one works fine so no thank you.
Mine did too..  but this one works better:D

---

### Post by len1x on 2008-07-11
I installed it and everything is fine, I set up an adsl connection ( adsl tab ).. but each time I want to connect it asks for the password to be written, I don't see a "save password" feature, any idea?

---

### Post by dmac71 on 2008-07-12
> **kosimo said:**
> i Found A Very Useful Post On Planet About How To Test The Latest Network Manager 0.7.0 Svn Witch Is Very Very Easy To Install In Hardy.

Just Go Here: [https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

Add Those Two Repos And Update/upgrade Your System. 
Then Restart

And Start Enjoying New Network Manager! I've Been Waiting For Ages! With Minor Graphics Change It Have Many New Features.

Manual Ip, Dhcp With Manual Dns, Saving Passwords,  Vpn!!, You Can Save A Wireless Preferred List, Mobile Broadband, (use Your Cell!), A Dsl Ppp Connection... And A More Sensible Wireless Discovery List

Guys, This Rocks.  And Even Being A Svn Build I Had No Issues Using It.

I Strongly Recommend To Give It A Try.


Edit: If You're Using Hardy, Make Sure You Choose Hardy Repos!!



How Do You Do The Upgrade--very New To Linux/ubuntu--did Not Notice Any How To Information On The Page.  Thanks.

---

### Post by Polygon on 2008-07-12
> **dmac71 said:**
> How Do You Do The Upgrade--very New To Linux/ubuntu--did Not Notice Any How To Information On The Page.  Thanks.

first, go to system > administration > software sources, it will ask for your password, enter it

then go to the third party sources tab. click "add", and then go back to the webpage you clicked on

there should be a drop down box that says 'intrepid", make sure that box says 'hardy" and then the apt-lines (as they are called) will change. there are two lines, simply copy and paste them into the box that you just brought up in software sources by clicking add, (do this twice for both lines), and then click close. it will ask you to reload your software sources, you should click yes.

then it will either tell you that updates are available or you can run update manager manually and it will upgrade it. Be sure to restart after you install it as network manager will die during installation, but afterwards its all fine.

---

### Post by dmac71 on 2008-07-12
Thanks Polygon.  I appreciate the assistance.

---

### Post by SilverDragon on 2008-07-14
Kosimo, thank you very much for this update :)

Every since I built my first computer during my last winter break and installed Ubuntu on it, my only problem was that I could not connect to the internet through my Ethernet cable. (I had a thread about it back then) I had to use a USB cable. This wasn't really a problem, besides the fact my family wanted to use a wired router which required my Ethernet port to work.

Shortly after updating the Network Manager, plugging in the Ethernet cables and reseting the modem, I was happy to find out that everything works. I'll definitely be upgrading to this version of the Network Manager when my laptop for college comes in :D

> will this be the default in intrepid (sorry if this was said already, i didn't have time to search the whole thread) 

I was curious also, except I did search the whole thread. :-P

---

### Post by reacocard on 2008-07-14
tried it, but it won't remember my WEP key so its back to WICD for me.

---

### Post by Kosimo on 2008-07-15
> **reacocard said:**
> tried it, but it won't remember my WEP key so its back to WICD for me.

How come?  For me remember all passwords with no issues

---

### Post by Kosimo on 2008-07-15
> **SilverDragon said:**
> Kosimo, thank you very much for this update :)

Every since I built my first computer during my last winter break and installed Ubuntu on it, my only problem was that I could not connect to the internet through my Ethernet cable. (I had a thread about it back then) I had to use a USB cable. This wasn't really a problem, besides the fact my family wanted to use a wired router which required my Ethernet port to work.

Shortly after updating the Network Manager, plugging in the Ethernet cables and reseting the modem, I was happy to find out that everything works. I'll definitely be upgrading to this version of the Network Manager when my laptop for college comes in :D



I was curious also, except I did search the whole thread. :-P

You`re welcome :) Even if you should say thanks to NM developers! ;p

0.7 is a very-long-time-waiting for me and considering the stability of this SVN release I can`t wait to test the final one

---

### Post by Polygon on 2008-07-15
latest NM-7.0 update that i just downloaded on my laptop broke my wireless, it just hangs on 'acquiring network address' and then fails and asks for my network key again, have tried reentering the password and resetting my router, no go.

wheeeee.....

---

### Post by reacocard on 2008-07-15
> **Kosimo said:**
> How come?  For me remember all passwords with no issues

it just doesn't. the normal "allow access to keyring" popup happens, and if I enter the key manually it works fine, but the key is never there when I look in the edit connection dialog.

Additionally, it seems not to apply settings for static IP on wireless, another feature I need. :(

---

### Post by SilverDragon on 2008-07-15
> latest NM-7.0 update that i just downloaded on my laptop broke my wireless, it just hangs on 'acquiring network address' and then fails and asks for my network key again, have tried reentering the password and resetting my router, no go.

wheeeee..... 

The latest update broke my wired set-up too. Before I could connect with either USB or Ethernet, but now I can't connect with either :(

---

### Post by Polygon on 2008-07-15
yeah, it broke wireless on two seperate computers with different wireless cards (both atheros) and on my laptop i cant connect with Ethernet either.

so basically both of those computers are bricks until i can manually download a older version of network manager and install it manually on both machines

but i have a bug report about the issue, dunno if they will even see it however. I reported it on the gnome bugzilla as the launchpad ppa just compiles code from source and i dont think anything would get done if i reported it on launchpad

requires a gnome bugzilla account to comment: [http://bugzilla.gnome.org/show_bug.cgi?id=543153](http://bugzilla.gnome.org/show_bug.cgi?id=543153)

---

### Post by waapwoop1 on 2008-07-15
Hi guys...

i'm not sure i understand.

I installed this, now i my wireless card isn't called ath0, its called lo.

I used to get this cool wireless manager in the top right of the panel, i could click on it, and it would show all available wireless conenctions, it is gone now. I want that back.

Also, how do you open this network manager, i open network from the admin menu, and i see none of what is in the screenshots. I don't understand.

---

### Post by waapwoop1 on 2008-07-15
IT is acting really strange now.
I managed to get the applet back via another reboot, however it won't connect to any network, however the internet works as it conencts automatically in the background.

I think lo connects automatically, however the applet manager is trying to use ath0, i don't know, its just not right after this install.I see all the new options now.

---

### Post by Polygon on 2008-07-15
network manager might be bugging out on you, because lo is not the same thing as ath0, its loopback....while ath0 is supposed to be the atheros wireless interface

---

### Post by waapwoop1 on 2008-07-15
oh wait, sorry, internet doesn't work. I think this update stuffed up my wireless completely.

---

### Post by Polygon on 2008-07-15
add yourself to the list, the most recent update seemed to of borked wirless for at least three people (yourself included).

---

### Post by SilverDragon on 2008-07-15
Yeah I'm just going to back up and reinstall. Oh well, I wanted to go back to 32 bit anyway. I'll just wait for the final version to come out.

---

### Post by waapwoop1 on 2008-07-15
So now ethernet and wireless don't work

so i can't use my laptop for anyhting anymore

how do i fix this? I can't connect to internet, i'm new to linux can someone give detailed instructions.

---

### Post by waapwoop1 on 2008-07-15
Can i use the hardy install cd as a repository?

---

### Post by SilverDragon on 2008-07-15
I believe you can. It doesn't hurt to try :)

---

### Post by phaed on 2008-07-15
I got the same problem.  It killed my wired internet connection (can't get dhcp address).

I tried to use the Live CD as a repo but networ manager wasn't listed on there.  This is what I had to do (luckily I had two optical drives):

I booted my Live CD and downloaded the following packages from packages.ubuntu.com:

dhcdbd_3.0-1ubuntu1_i386.deb
libnl1_1.1-1_i386.deb
libnm-util0_0.6.6-0ubuntu5_i386.deb
network-manager_0.6.6-0ubuntu5_i386.deb
network-manager-gnome_0.6.6-0ubuntu3_i386.deb

Burned them to a CD (the packages are only about 1 MB in total, so you can probably use a floppy), rebooted and installed them manually. The first three are dependencies. You have to uninstall network-manager, network-manager-gnome AND libnm-util0 as it's the 0.7 version, before you install the debs.

Then log out / log in. That should get you back to a working Network Manager 0.6.6

---

### Post by TheAL76 on 2008-07-15
Easiest way is to download from packages.ubuntu.com on another machine (if you have it).

You will need 3 packages:

1. network-manager
2. libnm-util0
3. network-manager-gnome (or kde if you have that)

Remove the 0.7 version and use the debs for those 3 packages.

Only issue I see is my network-manager-gnome doesn't work right. It says it's version 0.7 somehow, even though I removed it, and it thinks my PC is disconnected from the ethernet cable. No matter, though, as I am connected to the Internet anyway.

---

### Post by High Roller on 2008-07-15
If you're on a wired connection and want to wait this bug out until the next update strolls along..  here's what I did (seems to work).

1. Right click on the NM tray icon and disable networking.
2. Go to "System"-->"Administration"-->"Network".
3. Click the "Unlock" button at the bottom right.
4. Left click/select "Wired Connection"
5. Click the "Properties" button at the top right.
6. De-select "Enable roaming mode".
7. Click the "Configuration" dropdown and select "Automatic Configuration (DHCP)".
8. If Firefox complains about being in offline mode you might need to de-select "Work Offline" under the file menu.

---

### Post by waapwoop1 on 2008-07-15
I managed to uninstall  0.7

When i try to reinstall 0.66 it says for the package to install it needs to remove evolution, pidgin and lots of libraries.
wtf?
I tried it anyway and it can't remove those libraries.  I might need to do a clean install. I wish i never installed this thing. I would not recommend it to anyone.

Basically I have Internet back, but no network manager, and no way of installing network manager.

---

### Post by TheAL76 on 2008-07-15
> **waapwoop1 said:**
> I managed to uninstall  0.7

When i try to reinstall 0.66 it says for the package to install it needs to remove evolution, pidgin and lots of libraries.
wtf?
I tried it anyway and it can't remove those libraries.  I might need to do a clean install. I wish i never installed this thing. I would not recommend it to anyone.

Basically I have Internet back, but no network manager, and no way of installing network manager.

Don't panic just yet.

If you have internet, then you have network manager. What's missing is the frontend (network-manager-gnome). 

Copy down the names of the packages Synaptic wants to remove. Remove them, you can get them back later. You should be able to remove them regardless of whether you have internet.

---

### Post by waapwoop1 on 2008-07-15
why should i have to remove evolution and pidgin?

---

### Post by TheAL76 on 2008-07-15
> **waapwoop1 said:**
> why should i have to remove evolution and pidgin?

Since there is a broken package that results, there must be a dependency somewhere with the libraries. 

All of your Pidgin data will still be there when you re-install it, and I assume that is the case with Evolution as well, since it should keep your files and data in your home directory somewhere.

It's kind of annoying, but I did it, and now I have Internet working again.

---

### Post by TheAL76 on 2008-07-15
Once I restarted, my network-manager-gnome started working correctly again. It shows the old version and doesn't think my ethernet cable is disconnected.

---

### Post by waapwoop1 on 2008-07-15
thanks so much. I have it back to normal now. Yu are right, my evolution emails are still there. what a mission

---

### Post by CNLiberal on 2008-07-15
I decided to try this out because I needed an AT&T (formerly Cingular) PCMCIA broadband card to connect to the internet.  This is remarkable, because NetworkManager detects it as a GSM modem and automatically works.  Just amazing.  However, now I can't connect to my wireless AP in my house.  This isn't the greatest solution.  And I also can't get my VPN working.  Looks as if VPN isn't implemented yet.  I kinda need that for work.  Not great.  This NM applet has HUGE potential.  Very exciting stuff.  I suppose that I should uninstall it and install the old version.  Any specifics on how to do that?  I'm thinking that I have to uninstall NM, then remove the link to the launchpad repo.  Is that right?

Jim

---

### Post by Polygon on 2008-07-15
> **CNLiberal said:**
> I decided to try this out because I needed an AT&T (formerly Cingular) PCMCIA broadband card to connect to the internet.  This is remarkable, because NetworkManager detects it as a GSM modem and automatically works.  Just amazing.  However, now I can't connect to my wireless AP in my house.  This isn't the greatest solution.  And I also can't get my VPN working.  Looks as if VPN isn't implemented yet.  I kinda need that for work.  Not great.  This NM applet has HUGE potential.  Very exciting stuff.  I suppose that I should uninstall it and install the old version.  Any specifics on how to do that?  I'm thinking that I have to uninstall NM, then remove the link to the launchpad repo.  Is that right?

Jim

yeah, remove the repo, uninstall network manager and then reinstall it (if you somehow have access to internet)

---

### Post by Mr. Picklesworth on 2008-07-15
To avoid dependency issues, go into Synaptic and Force Version of all the NM 0.7 packages to be 0.6.

---

### Post by CNLiberal on 2008-07-15
I figured out my problem.  I managed to completely uninstall NM.07.  When I connected to a hard ethernet line, I had to setup the network to use DHCP.  Once that was done, I was able to connect to the internet.  When I went to uninstall NM 0.7, I had forgotten some of it's dependencies.  Once those were gone, installing NM 0.6.6 worked fine.  I am not back up.  I'll have to wait until NM 0.7 becomes available.  Too bad, cuz I'd really like to use this 3G AT&T card.  If anyone has any ideas on that, let me know!

Jim

---

### Post by SomeGuyDude on 2008-07-15
> **Viiral said:**
> Did you reboot? 

Remove it, remove the repos you added in software source, then reinstall the old one from apt-get/synaptic

That would work...

...EXCEPT I CAN'T GET ONLINE. It broke my connection, so now I cannot do anything in Synaptic because it insists on downloading files. I am now completely and utterly fvcked, using a friend's PC to try and download ALL of the files for .6 in order to get back online.

Gee thanks, nothing like completely shattering my connection to piss me off at 11:45pm. :mad:

---

### Post by waapwoop1 on 2008-07-16
just don't install this.

---

### Post by waapwoop1 on 2008-07-16
> **SomeGuyDude said:**
> That would work...

...EXCEPT I CAN'T GET ONLINE. It broke my connection, so now I cannot do anything in Synaptic because it insists on downloading files. I am now completely and utterly fvcked, using a friend's PC to try and download ALL of the files for .6 in order to get back online.

Gee thanks, nothing like completely shattering my connection to piss me off at 11:45pm. :mad:

from experience, you have to completely remove everything. reboot once or twice.
If you have the cd handy, you have to mount it to do this i can't remember the command for this. then you can use the cd as a repo. Then you can remove everything.

make sure you have no network manager at all of any version. connect to a lan point, or have wireless card in. You need to go tot eh network settings and enable the eth or the wireless. Networking will work without network manager.
Then install the old network manager.

Uninstalling .70 might make you uninstall evolution and pidgin, just reinstall after.

---

### Post by SomeGuyDude on 2008-07-16
It was faster to simply reformat. Fun times.

---

### Post by bpmorris on 2008-07-16
This update broke my laptop as well, I had to manually download the orignal debs on another machine and transfer them via usb stick to get mine up and running again.... boooo

---

### Post by Polygon on 2008-07-16
here is how i solved it and reverted back to the hardy default version of network manager

1. remove the ppa repos
2. uninstall network-manager network-manager-gnome libnm-glib0 libnm-util0
3. download the archive attached to this post and extract it to a folder (in this example, 'ubuntu') on your desktp
4. open up a console, type

```

cd ~/Desktop/ubuntu/

sudo dpkg -i *.deb


```

it will warn you about downgrading two packages but it should install fine, and network manager will warn you about not having enough resources to continue, and just restart and you should get your net back.

---

### Post by rudihawk on 2008-07-16
> **Polygon said:**
> latest NM-7.0 update that i just downloaded on my laptop broke my wireless, it just hangs on 'acquiring network address' and then fails and asks for my network key again, have tried reentering the password and resetting my router, no go.

wheeeee.....

Same problem....

---

### Post by TheAL76 on 2008-07-16
> **SomeGuyDude said:**
> It was faster to simply reformat. Fun times.

Really? It took me 10 minutes tops to get my internet back up and running.

To each his own...

The lesson I've learned is that even though I love tinkering (that's one of the reasons I use Linux), I shouldn't use unsupported versions for critical applications. It's one thing to try the new AWN or the new Pidgin, but a totally different game when messing with what has become the lifeline of the computer.

At the very least I should've waited to check user feedback before blindly hitting "Update."

---

### Post by CNLiberal on 2008-07-16
The reason I tried it was because a few people said theirs worked "out of the box".  I was hoping I'd be that lucky too.  But NM 0.7 doesn't support VPN yet.  They must still be working on it.  My GSM modem worked out of the box.  It was amazing.  All I did was choose "Automatic GSM" and it prompted me for the password (which I found on this website).  It worked like a charm.

I was able to get NM 0.6 back by going to SYSTEM-ADMINISTRATION-NETWORK and choosing my wired network and telling it to use DHCP.  I then rebooted, and I had wired internet back.  Then just removed the repos and uninstalled everything network manager related in Synaptic that referred to the 0.7-svn-yadda and rebooted again.  Then ran Synaptic again and reinstalled everything related to Network Manager 0.66 (gnome, all VPN etc).  I rebooted again, and it was magically back and working beautifully.

Jim

---

### Post by tact on 2008-07-16
This afternoon I had the same (hangs waiting forever for DHCP to get IP address) problem.  Googled a little, found the answer in another thread in these forums...  minor edit to a text config file and dhcp works again.... both wired and wireless.

 Later in the evening I see a new update came thru and it asked to replace that same file (seeing as I had edited the original and the update manager somehow knew it).  I checked the differences, realised it was a fix for the dhcp problem.....so let it replace my edited file.  No issues.... working fine.

I did go through a stage of pulling out my hair, no internet connection at all, no idea how to roll back to the older version... but patience and google to the rescue.  Very minor edit to that text file and all happy.  hehehe  and now apparently even that little edit is not needed.

As some others have observed...  it is a self inflicted pain to install any pre-release software.  :)

I think a more pressing "gotcha"  - its not made clear that pptp vpn will not work in this pre-release version.  Fortunately the laptop I installed it on was not my work laptop as on that I do need to connect to corporate pptp vpn.

---

### Post by roaldz on 2008-07-16
> **tact said:**
> This afternoon I had the same (hangs waiting forever for DHCP to get IP address) problem.  Googled a little, found the answer in another thread in these forums...  minor edit to a text config file and dhcp works again.... both wired and wireless.

 Later in the evening I see a new update came thru and it asked to replace that same file (seeing as I had edited the original and the update manager somehow knew it).  I checked the differences, realised it was a fix for the dhcp problem.....so let it replace my edited file.  No issues.... working fine.

I did go through a stage of pulling out my hair, no internet connection at all, no idea how to roll back to the older version... but patience and google to the rescue.  Very minor edit to that text file and all happy.  hehehe  and now apparently even that little edit is not needed.

As some others have observed...  it is a self inflicted pain to install any pre-release software.  :)

I think a more pressing "gotcha"  - its not made clear that pptp vpn will not work in this pre-release version.  Fortunately the laptop I installed it on was not my work laptop as on that I do need to connect to corporate pptp vpn.

Yes, today´s update fixed the problem for me too, I couldn´t get a DHCP adress either, but now it´s working again, both wireless and wired!
So everyone who want´s to try it: The current version (as i´m posting) is working great!

---

### Post by SilverDragon on 2008-07-16
> Yes, today´s update fixed the problem for me too, I couldn´t get a DHCP adress either, but now it´s working again, both wireless and wired!
So everyone who want´s to try it: The current version (as i´m posting) is working great!

Strangely, I think I am going to try it after I reinstall, mainly because the Ethernet did work when I had originally updated it. If not, well I'll just reinstall again before configuring so it's not that big of a deal. I think I just like messing around with my computer :D

---

### Post by Polygon on 2008-07-16
Ill install it on my laptop again (since it actually needs this newer version to work properly ) but i think ill stay with the hardy default on my desktop, not having internet sucks Dx

---

### Post by SomeGuyDude on 2008-07-16
> **Polygon said:**
> Ill install it on my laptop again (since it actually needs this newer version to work properly ) but i think ill stay with the hardy default on my desktop, not having internet sucks Dx

Not to mention unlike most OTHER snafus, if this thing screws up you can't hope an update fixes it since... you can't get updates. :mad:

---

### Post by High Roller on 2008-07-16
> **SomeGuyDude said:**
> Not to mention unlike most OTHER snafus, if this thing screws up you can't hope an update fixes it since... you can't get updates. :mad:

If an update to this version of NM screws up, just simply disable NM and manually configure a wired connection as I mentioned [earlier]("http://ubuntuforums.org/showpost.php?p=5393931&postcount=60") in the thread.  Or watch this thread whenever you see an update popup for NM.  There'll likely be reports of success and failure here.

It should be noted that only a few hours passed before an update was made available that corrected the problem on this _testing version_ of NM 0.7.  That's pretty good.

---

### Post by mc4100 on 2008-07-16
Each time I tested 0.7.0svn (Hardy, and Intrepid), it wouldn't play nice with DHCP. So... it took a while, and a bit (read: alot ;)) of research, 
but here's a few tips if you're going to try this with Wifi:

With a working connection, go to nm-applet and right click -> connection info (Or login to your router, since you'll also find the info there)
Note down...

The SSID (The name of your network), for example,
Skynet

The Default Route, e.g.,
192.168.2.1 	(this is your router's LAN IP, it is your "Gateway")

The Subnet Mask, e.g.,
255.255.255.0	(This relates to how many IP's your router will give out, you might see "255.255.0.0")

The Security, e.g.,
WPA/WPA2


Then, after you've installed the new version, and find you're having wifi trouble:

Right click on the applet again and "Edit Connections..."
Choose the Wireless tab,
If a network is listed, then select it and choose "edit", otherwise choose "add".
Make sure the SSID matches your network, e.g., "Skynet", and have the mode set to "Infrastructure"
I left "BSSID" and "MAC ADDRESS" empty, it works fine.
In the "Wireless Security" tab, select your security type, then put in your password,
In the "IPv4 Settings" tab, find "Method" and select "manual" from the drop-down list,
Find the "Address" section, and click "Add" ...
Then for the "Address", type the first three parts of your router's ip (e.g., "192.168.2"   ) 
and then type "."  
and finally a number higher than the routers last digit; I recommend any number between 5 and 100, thus "192.168.2.5"

Again, this is important, the IP you just set should not be the same as the "Default Route" which is your router's (AKA gateway's) IP Address.
For...
"Netmask", 
make sure it matches the "Subnet Mask", for example, "255.255.255.0"

"Gateway", 
Type your "Default Route", i.e., type the router's IP, e.g., "192.168.2.1"

Finally, for "DNS Servers", type your router's IP again, e.g., "192.168.2.1"

If this doesn't work, then there's another issue, (Password issue maybe?) but to undo, go to that "IPv4 Settings" tab again and change back to DHCP.

---

### Post by SilverDragon on 2008-07-16
Well after reinstalling and updating to Network Manager 0.7.0. svn, I got my USB connection to work, but my Ethernet doesn't :(

Oh well, I'll just keep updating and trying out my Ethernet cable until hopefully it works again. Then I can set up my router and move my computer out of my room for my laptop. Either way, it's nice to see progress on the Network Manager, even if there are regressions.

---

### Post by tact on 2008-07-16
> **SomeGuyDude said:**
> Not to mention unlike most OTHER snafus, if this thing screws up you can't hope an update fixes it since... you can't get updates. :mad:

When toying with experimental or pre-release stuff you are meant to EXPECT problems and breakage and then be a good citizen and report the problem with the attitude of contribution to the community.   Putting your (pc's) metal/silicon on the line and ready to take a bullet, so to speak, in the interests of advancing the technology.  

People forget that.  

No matter what part of the system you are toying with breakage has to be anticipated - for example pre-release or experimental...:
- updates to the kernel  may leave you with no way to boot let alone access internet
- updates to GDM may leave you no way to get into your account to fix things, let alone internet connection
- updates to xorg may leave you unable to get into your system too, forget about internet
- applications, like desktop managers, can get you into a spot of bother like being able to load up your desktop but not be able to click or do anything.
-  etc etc etc ...

All of the above actually make the minor inconvenience of the NM "snafu" pale into insignificance.

Of course its not your fault.  You read an enthusiatic review of a pre-release making a lot of sense and so went for it.  I did too.  Forgetting for a moment that perhaps it'd be a good idea to google around and see if there are any gotchas and preparing for it.

Right at this moment, on my "mission critical" corporate work laptop, my daily driver, my company issued key to getting a salary every month, on which, according to all good wisdom I should never experiment! - I am running beta versions of Lotus notes, Lotus Domino, OpenOffice 3, Cairo-Dock release candidate, 3 PPA's enabled (personal repos for specific customised apps I am trying out), and likely a dozen other apps are updated past "safe release" as those updates come down the pipe when you have the backports and hardy proposed repos enabled

I get a little slack in that checking arena as I have a safety net at all times anyway -  I always have a recent clone of my laptop internal drive on hand (bootable) and I do incremental backups of /home to it regularly).  So in case disaster strikes I can swap in/out physical HDD's in minutes.

Anyways... so cheong hei ..  returning you now to your regularly scheduled program for your viewing pleasure.

---

### Post by BC7333 on 2008-07-19
Also playing around with this one.  Did not see network manager, or nm applet anywhere in the menu's but....
> 
brian@brian-laptop:~$ nm-applet

(nm-applet:10440): Gtk-CRITICAL **: gtk_notebook_set_tab_label: assertion `GTK_IS_WIDGET (child)' failed

after doing nm-applet wireless started running and works.

intrepid alpha 2 here upgraded from hardy.

---

