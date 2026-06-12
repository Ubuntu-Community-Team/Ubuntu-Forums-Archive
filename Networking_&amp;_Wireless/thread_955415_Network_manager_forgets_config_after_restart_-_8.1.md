---
title: "Network manager forgets config after restart - 8.10"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-10-22
I've installed beta Ubuntu 8.10 Interpid Ibex. There is a bug when you set manual configuration to some interface specifying the IP address, when you restart comp, it's back to default (searches for dhcp).
Is anyone else experiencing this problem? Where should I report this bug?

---

### Post by walexand on 2008-10-22
Same here.  Restarting always reverts to DHCP which fails (even though I do have a DHCP server).  Manually setting the static IP reconnects me until the next restart when it reverts back to DHCP.

---

### Post by Aseke on 2008-10-23
Does anyone know where network manager stores information concerning network interfaces? In previous version(8.04) that file was /etc/network/interfaces. I think that the problem with network configuration reset might be related to the file where such kind of information is stored...

---

### Post by JD82 on 2008-10-28
> **ene_dene said:**
> I've installed beta Ubuntu 8.10 Interpid Ibex. There is a bug when you set manual configuration to some interface specifying the IP address, when you restart comp, it's back to default (searches for dhcp).
Is anyone else experiencing this problem? Where should I report this bug?

> **walexand said:**
> Same here.  Restarting always reverts to DHCP which fails (even though I do have a DHCP server).  Manually setting the static IP reconnects me until the next restart when it reverts back to DHCP.
I have the same problem :(

---

### Post by qwertzqwertz on 2008-11-03
Hey all, I've been struggling with this too, was about to revert to previous version until this got fixed, but then I saw this (See about 2/3rd down the page, section that says "More about the Network Manager..."
[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update)

Apparently you are supposed to UNCHECK the "System Setting" checkbox if you want it to be persistent after a reboot(?).  This is not at all easy to understand in my opinion and is hopefully fixed.  My next question is this though, /etc/network/interfaces does NOT get edited when you make this change.  So question is, where is the configuration file on the file system itself for this now??

---

### Post by natros on 2008-11-04
> **qwertzqwertz said:**
> Hey all, I've been struggling with this too, was about to revert to previous version until this got fixed, but then I saw this (See about 2/3rd down the page, section that says "More about the Network Manager..."
[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update)

Apparently you are supposed to UNCHECK the "System Setting" checkbox if you want it to be persistent after a reboot(?).  This is not at all easy to understand in my opinion and is hopefully fixed.  My next question is this though, /etc/network/interfaces does NOT get edited when you make this change.  So question is, where is the configuration file on the file system itself for this now??
Maybe that's the real problem. The network manager is not saving the configuration.

The Network Manager is supposed to be easy to use not hard.

---

### Post by qwertzqwertz on 2008-11-05
Yeah, I am growing more and more concerned about this.  I've noticed the behavior also that your network interfaces don't even startup/connect until you log into the GNOME GUI?  What if you want to reboot your machine remotely??  My concern for this new "feature" is growing enough that I might want to move back to 8.01, and I can't find ANY info about this?  Has anyone else?  Nothing but praise for this new Network Manager, but I sure don't get it.  I would just love to have a full explanation of this thing.  Where on the system are the configuration files for this saved?  No longer at /etc/network/interfaces, that's for sure.  I doubt the linux community is going to be at all ok with this.  If anyone has any info about this, please do share.  I'm glad at least I found the "trick" to keeping the IP static after a reboot, that only took me about 3 hours of searching the web...

---

### Post by marcuskoze on 2008-11-06
I've "solved" this by installing the KNetworkManager pack (the KDE version but works charming on ubuntu GNOME too), created a new connection with it and after reboot it held the configuration as I've set it :)

Not a fix for the GNOME NetworkManager, but rather a solution I've found :)

Hope it helps.

---

### Post by chadaneal on 2008-11-06
For whats its worth I had issues with my network not starting or forgetting its static IP's and tried everything from unsetting the system option to renaming the connection. 

At the end what worked for me was uninstalling the network manager and adding all my IP config info to /etc/network/interfaces

Hope that helps some of you...

Chad

---

### Post by ene_dene on 2008-11-06
For me the solution was to uncheck "system settings" and then restart. But it is interesting what someone said, if you want to reboot comp from remote location, would the connection get up?

---

### Post by hickop on 2008-11-06
Same problem, Network Manager Auto eth0 going Auto DHCP each time i reboot.
Even disabling "system settings" did not fix the problem.

---

### Post by cb951303 on 2008-11-06
unchecking "system setting" didn't work for me. It rechecks itself everytime I push "edit"

---

### Post by qwertzqwertz on 2008-11-06
> **ene_dene said:**
> For me the solution was to uncheck "system settings" and then restart. But it is interesting what someone said, if you want to reboot comp from remote location, would the connection get up?

Yep that's exactly my case, I was able to finally get it to save the static IP by UNCHECKING the "System Setting" checkbox (how Un-Intuitive is THAT??), but yes problem I'm seeing now is network interface doesn't come up at all until you log into GNOME GUI.  No more remote reboots.  My thought for now is to try and stick with 8.10, because it does seem to have some advantages (actually seems a tiny bit more snappy to me), but uninstall Network Manager.  But my question is, can you get the old style network utility back in the GUI if so?  I will give this a try unless there is anyone out there (Ubuntu Developers) that can help give us some insight into this Network Manager and why it's supposed to be such a good thing, because no one I talk to thinks so and is quite confused.

---

### Post by kabel_kabel on 2008-11-09
Unchecking "system setting" didn't work for me too. The same thing, it rechecks itself everytime i push "edit" and after every reboot. This is the worst network manager that they could think of, i'm really disappointed.

---

### Post by all13d on 2008-11-10
> **kabel_kabel said:**
> Unchecking "system setting" didn't work for me too. The same thing, it rechecks itself everytime i push "edit" and after every reboot. This is the worst network manager that they could think of, i'm really disappointed.

Try toggling "connect automatically," toggling that off and back on should let you uncheck system settings.  It's what worked for me.

---

### Post by cb951303 on 2008-11-10
> **all13d said:**
> Try toggling "connect automatically," toggling that off and back on should let you uncheck system settings.  It's what worked for me.

that worked perfectly
thanks

---

### Post by airborne_77 on 2008-11-11
Wow yeah, this is definitely not a good thing when we're having to "trick" the network manager into doing what it should.  Not intuitive at all.  I really thirst as well for some more detailed information about this and why the developers consider it to be a good advancement.  Maybe if someone could help describe this to us, I am all ears.  Otherwise, I hope it gets fixed very soon in a patch release.

---

### Post by Kisil on 2008-11-14
I'm currently having a similar problem in 8.04.  Every time I reboot I need to run "sudo ifconfig wlan0" and then hit "Connect to Other Wireless Network" in nm-applet.  My WPA2 settings are not saved when I restart.  

/etc/network/interfaces can still be used, but editing it overrides the settings from nm-applet - it throws me into "manual mode."  The nm-applet saves its information in gconf.  You can access these by running:
```
$ gconftool-2 -R /system/networking/wireless
```
But I don't see my wireless password in there, and my old WEP key is still stored somewhere else.  Anyone know where wireless keys get stored?

---

### Post by TheHammer23 on 2008-11-15
I believe wireless keys are stored with Gnome-Keyring.

As far as the system settings checkbox, there is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284298") where you can not save the system setting option without then toggling the Automatic connection checkbox off and on as an earlier poster noted. This could be affecting other options as well. I did notice that the Auto connections that NetworkManager was creating were refusing my changes. My workaround was to create a new connection and configure that as I wanted, then delete the old one (The wireless will recreate an auto entry but it doesn't seem to take precedence. I'm not sure how precedence is determined.)

In case anyone is wondering, the system setting option tells Ubuntu to start that interface up in that configuration, even before the user logs in. If no configuration has that checked, the interface supposedly will not come up until you log in. I haven't quite got it to work yet though.

---

### Post by nuttygamergeek on 2008-11-15
I had the same problem, tried "System Setting" and that seemed to work.  However after a reboot I now have two connections, the one I renamed to "eth0" and "Auto eth0" is back grr.

Edit: I just tried again but didn't rename the connection and I now have 2 x Auto Eth0 :lolflag:

Edit2: Found a related bug: [network manager won't save fixed ip settings on wired connections]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/283233")

---

### Post by Kisil on 2008-11-22
I managed to change my wireless key in the gnome keyring (using Seahorse), but when I reboot, nm-editor still shows my old WEP key.  It's not in gconf, it's not in the keyring, it's not in /etc/network/interfaces... where is this number stored?

Is there a painless way to search the contents of files, perhaps?  I suppose I could write a script, but I'd have to think a little about how to do it cleanly.

---

### Post by leohartx on 2008-11-25
here is another temporary solution :
first, you uninstall network manager
*sudo apt-get remove network-manager*
then, you install network-admin through add/remove... application - old tool for managing network connection or perform this command
*sudo apt-get install network-admin*
and config whatever u want to do like u did :)

---

### Post by airborne_77 on 2008-11-25
> **leohartx said:**
> here is another temporary solution :
first, you uninstall network manager
*sudo apt-get remove network-manager*
then, you install network-admin through add/remove... application - old tool for managing network connection or perform this command
*sudo apt-get install network-admin*
and config whatever u want to do like u did :)

I gave this a try, but network-admin is not showing up in the Synaptic package manager for me.  Also, the command line install says it can't find package "network-admin".  I like this line of thinking though, prob the best solution I see so far until Ubuntu devs hopefully put out a patch release fix for this...

EDIT:  Oops, was able to search for it and it's actually "gnome-network-admin".  I was able to install this package and indeed have the old 8.04 network interface style back, which works fine just as before and successfully edits the /etc/network/interfaces file when you make changes.  This is my personal best recommendation for now until this gets fixed.

---

### Post by hindutool on 2008-12-01
I too have had the same problems.  Thanks to all for the previous posts they were very helpful.

-I simply uninstalled all network managers, including the Knetworkmanager (could not get it to load after install). 

-I then edited the "interfaces" file in /etc/network/
Check out this URL for examples of working with this file (this file, BTW is where NetworkManager stores its config information - trust me)
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

-I then typed in "network-config" at a root command prompt and lo and behold this beautiful graphical network manager popped up! 
(make sure you have the package - "network-config" -----> *sudo apt-get install network-config*). NOW, the config files for this program are located in /etc/network-config/ in a file called "settings.txt"

I am writing this because I could not change my configuration at all using the gui gnome networkmanager (i.e. I couldn't uncheck boxes or anything)- my computer was essentially useless in connecting to the internet with a static IP config. Using network-config, I was able to get static IP configuration up and running on the fly (i.e. without a restart).

Hope this helps.  I am a newbie, so my syntax and structure may be a little off... my apologies.

---

### Post by larukuinsane on 2008-12-23
Hi all, well first of all . I'm from peru  so please , excuse my bad english!! hehehe. I rebooted my PC  and the network settings are the same as i putted in the network manager.
The steps:

-Edit the connection name , change that name for something else . I put just "eth0" instead of "auto eth0".

-Toogle a little with the checkbox SYSTEM SETTINGS but let the checkbox marked.
-Put the network setting as you required.

Then you hit the ACCEPT button,  Ubuntu will ask for you password. Thats the sign we are looking for, then just reboot and BOOOOMMM heheheh ip settings as you putted.
I hope that this work for all.
Byeee

---

### Post by airborne_77 on 2009-01-26
> **larukuinsane said:**
> Hi all, well first of all . I'm from peru  so please , excuse my bad english!! hehehe. I rebooted my PC  and the network settings are the same as i putted in the network manager.
The steps:

-Edit the connection name , change that name for something else . I put just "eth0" instead of "auto eth0".

-Toogle a little with the checkbox SYSTEM SETTINGS but let the checkbox marked.
-Put the network setting as you required.

Then you hit the ACCEPT button,  Ubuntu will ask for you password. Thats the sign we are looking for, then just reboot and BOOOOMMM heheheh ip settings as you putted.
I hope that this work for all.
Byeee

Problem with this still FYI is that once you reboot, if you don't log into the Gnome Xwindows login screen, the network adapter is not enabled.  This means you would not be able to log into the machine remotely after a reboot via SSH, etc unless someone is there to log into the system physically so the network adapter turns on - unacceptable for me.

---

### Post by hundrambit on 2009-01-27
> **larukuinsane said:**
> Hi all, well first of all . I'm from peru  so please , excuse my bad english!! hehehe. I rebooted my PC  and the network settings are the same as i putted in the network manager.
The steps:

-Edit the connection name , change that name for something else . I put just "eth0" instead of "auto eth0".

-Toogle a little with the checkbox SYSTEM SETTINGS but let the checkbox marked.
-Put the network setting as you required.

Then you hit the ACCEPT button,  Ubuntu will ask for you password. Thats the sign we are looking for, then just reboot and BOOOOMMM heheheh ip settings as you putted.
I hope that this work for all.
Byeee

Works like a charm! The Accept button would be OK in English version though.

Problem actually lies in authorization (when you enter the password), the system cannot create a file called "eth0" in "/etc/NetworkManager/system-connections", which is then automatically loaded during next startup. These steps explains me why in old Network Manager there was a button called Unlock, you had to hit it in order to proceed to network settings.

You cannot save any file in a directory that is not owned by you (your login name), basic Linux rules. This new Network Manager should get same Unlock button, bug confirmed. :)

Thank you!

---

### Post by normanp on 2009-01-27
I found renaming auto eth0 no good (as in larukuinsane's post) - it just re-appeared - so this is what I did:
In Network Connections, Add, type the following:
Wired Connection 1, IPv4 Settings: 192.168.0.22, 24
Toggle off/on then leave both 'Connect Automatically' and 'System Setting' as ON,  then OK.
Delete connection 'auto eth0'
OK & close.
If necessary click icon top R on screen and enable network.
Reboot.
Network Manager now has ONLY Wired Connection 1 in it.
sudo ifconfig gives correct info.
ping own IP is OK, ping other Ubuntu 8.10 IP is OK.
Set up shared folder in Places, Home with Guest access, can browse to them from each computer using Places, Network (each computer has own icon here, no need to go into 'Windows Network').
(can't yet access shares without Guest access - will pursue in another thread)
Connection remains on further reboots.
Connection also OK when logged in as a non-admin user

---

### Post by silverbullet007 on 2009-01-27
I just upgraded from Hardy to Intrepid last night.. first issue?  Network Manager showing both of my nics as being unmanaged and my original static info not allowing me to connect to my lan.

Skimmed thru the bug reports and read where commenting out your static info and letting the adapters hit dhcp worked.. and it did for me as well.  But that has broken my being able to ssh into the box from work.

I will def give gnome-network-admin a shot and hope for the best.

---

### Post by chunderdog on 2009-02-12
My goal was to configure a static IP address for a machine that will host some servers and only connect through a wired network.  I tried all kinds of things, but the DHCP settings just kept on re-appearing after reboots.  The simplest solution for me was to use the Synaptic Package Manager to remove NetworkManager.  Be sure to remove the framework and daemon too (not just the GUI applet).  Then edit the config the old fashioned way by editing two text files:

/etc/network/interfaces
/etc/resolv.conf

The syntax is very simple, but, if needed, you can search the web for those file names to find some how-to articles.  Here's an example of /etc/network/interfaces:
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

resolv.conf is even simpler:
```
nameserver 192.168.1.1
nameserver 205.171.3.65
nameserver 205.171.2.65

```

Of course, you should enter your own *address*, *netmask*, *gateway*, and *nameserver* address(es) since the addresses above are only examples.  To edit those files, you have to be root.  For example, at a prompt you type "sudo gedit /etc/network/interfaces" (or substitute your favorite text editor for gedit).  To make the changes take effect, you can restart the network by typing "sudo /etc/init.d/networking restart", or you can just reboot.  Type "ifconfig" at a prompt to display the current address/status of your network interfaces.

I think NetworkManager is great if you want to use DHCP (especially if you have a laptop that connects via WiFi, etc.).  If you just want to use a wired network with a static IP, it is not appropriate (at least, not in its current version).

---

### Post by flyingthings93 on 2009-02-12
> **hundrambit said:**
> Works like a charm! The Accept button would be OK in English version though.

Problem actually lies in authorization (when you enter the password), the system cannot create a file called "eth0" in "/etc/NetworkManager/system-connections", which is then automatically loaded during next startup. These steps explains me why in old Network Manager there was a button called Unlock, you had to hit it in order to proceed to network settings.

You cannot save any file in a directory that is not owned by you (your login name), basic Linux rules. This new Network Manager should get same Unlock button, bug confirmed. :)

Thank you!


larukuinsane's tip worked for me, too--especially the part about: "Toogle a little with the checkbox"!  I would add: "While holding your mouth just so"! :? :-s :idea:  I lost track of how many variations on order of clicks and renames I tried before I got one to stick.  And then, I couldn't remember what worked when I set out to configure my other interface, so had to run through the whole thing again! (I have one built-in the laptop and one in the docking station.)
Wow!  What an ordeal!

Incidentally, I was never asked for a password.  I'm not sure why not, but there it is.  Also, once I got the second interface done and rebooted one more time, just to be sure, I noticed that the system had reentered the Auto eth0 and Auto eth1, both set to DHCP and therefore dysfunctional on my system, right there underneath the two I had successfully saved!  Persistent little flaw, isn't it?! :-k

BTW: One thing I think I figured out while doing my second interface--I believe one needs to have an active Ethernet line plugged into the interface one is trying to configure.  I had gotten the docking station one first and found that all my configuring and mouth contorting was for naught until I moved the cable to the input on the back of the laptop.  I'm not certain I wouldn't have eventually gotten the built-in interface to save its settings, but my experience seemed to indicate there had to be a live line in there. Something just seemed to "pop" into place once the interface actually connected to my router.
There!  That's my two cents worth, newbie that I am. ):P

Thanks to all who posted!  Even the early ones--It was helpful to me to learn back on page one of this thread that I wasn't alone! Or crazy!  Reading through the whole thread was very helpful.

---

