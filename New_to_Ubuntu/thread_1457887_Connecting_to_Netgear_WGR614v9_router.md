---
title: "Connecting to Netgear WGR614v9 router"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by petert33 on 2010-04-19
Hi, I have the Netgear WGR614v9 set up serving an iMac and an iBook. I have an old Compaq PC with WindowsXP on which I have installed Xubuntu 9.10.
I'm trying to connect with an Edimax EW-7711UTn USB adapter.
From other threads I have found the output of 'lshw -class network' which gives
description: wireless interface
physical id: 2
logical name: wlan0
serial : 00:1f:1f:76:54:43
capabilities: ethernet physical wireless
configuration: broadcast - yes, multicast - yes, wireless = IEEE 802.11bgn

Where do I go from here?
All help appreciated.
Thanks
Peter

---

### Post by Paddy Landau on 2010-04-19
Your post doesn't have enough information.

Please tell us what you have tried, what results you get, and how you know it's not connected.

---

### Post by 3rdalbum on 2010-04-19
There's a little icon on your top panel which manages networks - it's simply called Network Manager.

If you left-click on it, you'll be given a list of available wireless networks, assuming that your wireless adapter is supported by Ubuntu (which it appears to be). If you find the name of your network on that list, you should be able to connect simply by selecting it and then typing your network's password/key.

---

### Post by petert33 on 2010-04-19
Thanks for the responses. I've got as far as trying to connect but Authentification is requested and the password entered and sent off the dongle keeps flickering but nothing happens till I disable the network connection.:(

---

### Post by Scunnered on 2010-04-19
**petert33**

A quick stab in the dark.  I see you are in Cheshire and the router is the same as supplied to me by Virgin.  If you similarly are connecting via cable then the password that you give is the one agreed between Virgin and yourself when you first set up the router.

Perhaps this will assist

---

### Post by petert33 on 2010-04-20
Thanks for your stab in the dark, Scunnered. I really thought it was going to work as I am with Virgin but supplied my own router.
This is what is happening.

When I click the Network Manager icon I get a window listing;
Wired Network - disconnected
Wireless Network - disconnected
VPN Connections
Connect to hidden wireless network
Create new wireless network.

In the hidden wireless network window I enter the name of the hwn, the security option of wpa + wpa2 and the password set up for the Netgear router.

The network icon starts twirling and then a window appears:
The Network Manager Applet (usr/bin/nm-applet) requires access to the default keyring which is locked and a password is requested. I have entered again the Netgear password after it has represented itself after entering the Virgin broadband password.
The window disappears and next to appear is:
Authentication required by wireless network and showing Netgear as the name but with the connect button greyed out. :(

Where now?

Thanks for your assistance to this stumbling dolt - I really want to get Xubuntu fully up and running, the rest seems fine.:)

Peter

---

### Post by Paddy Landau on 2010-04-20
> **petert33 said:**
> The Network Manager Applet (usr/bin/nm-applet) requires access to the default keyring which is locked and a password is requested. I have entered again the Netgear password after it has represented itself after entering the Virgin broadband password.
There's your problem. The default keyring password is the same as your Linux password.

The keyring is controlled by the operating system and has nothing to do with your router; it keeps all encrypted keys for your system.

Try again, and type your Linux password to unlock the default keyring.

---

### Post by petert33 on 2010-04-20
Thanks for your input Paddy. I don't remember setting up a 'keyring' passport when I loaded the cd into the Compaq.
However I note that when a password is requested if an incorrect one is entered the window returns blank until the acceptable/correct one is entered.
I'm still ending up with the window requesting a password but with the connect button in grey.

---

### Post by Paddy Landau on 2010-04-20
> **petert33 said:**
> I don't remember setting up a 'keyring' passport when I loaded the cd.
Ubuntu has a keyring to hold all passwords that it needs, and it's protected by your login password. (I understand that you can change it, but I don't remember how.) It's part of Ubuntu. You don't install it explicitly.

When you enter the password for your wireless router, Ubuntu keeps a record in the keyring.

> **petert33 said:**
> I'm still ending up with the window requesting a password but with the connect button in grey.
Can you be very explicit what window this is? Perhaps add a screenshot, so we can see?

---

### Post by petert33 on 2010-04-20
I don't know how to do a screenshot and it's not this machine that I have xubuntu on.
The bold heading is 
Authentication required by wireless netwrork
under it says
Passwords or encryption keys are required to access the wireless network 'netgear'
Box labelled Wireless Security has 'WPA & WPA2 Personal' showing
Box labelled Password reuires completing
below is a tickbox to show the password, a 'Cancel' button and a greyed Connect button.

---

### Post by petert33 on 2010-04-20
[I][QUOTE=Paddy Landau;9148034]Ubuntu has a keyring to hold all passwords that it needs, and it's protected by your login password. (I understand that you can change it, but I don't remember how.) It's part of Ubuntu. You don't install it explicitly.

When you enter the password for your wireless router, Ubuntu keeps a record in the keyring.[/I]  

Why, if it has the password in the keyring, does Ubuntu require it again once it has been entered in the connection request window?

---

### Post by Paddy Landau on 2010-04-20
> **petert33 said:**
> I don't know how to do a screenshot and it's not this machine that I have xubuntu on.
To do a screenshot, simply press Alt-Print Screen (hold the Alt key down and then tap the Print Screen button). Print Screen may be abbreviated, e.g. PrtSc.

The window you described is asking for the WPA or WPA2 Personal passphrase for your Netgear router.

[LIST]
[*]Are you sure that you have chosen your router and not a neighbour's router? I notice that you're using a hidden network and that your router uses the default name 'netgear', so unless you have no nearby neighbours, you could be connecting to the wrong router.
[/LIST]
I would recommend that you go into your router's settings (you'll need to connect via an Ethernet) and change its name, so that you easily recognise it as yours and no one else's. Be aware that this will mean reconnecting *all* your existing wireless connections.

[LIST]
[*]Are you sure that you have typed the correct password?
[/LIST]
Go into your router's settings to double-check your passphrase. It needs to be typed **exactly** the same, including uppercase and  lowercase, and the number of spaces including leading and trailing spaces.

> **petert33 said:**
> Why, if it has the password in the keyring, does Ubuntu require it again once it has been entered in the connection request window?
Probably because it's been entered incorrectly, or you are connecting to the wrong wireless. If you haven't yet connected successfully, then Ubuntu might have not stored the passphrase because it realises that it's wrong.

---

### Post by petert33 on 2010-04-20
There are no other routers adjacent to the house. 
Ubuntu declares it hidden I have not hidden the router from the Compaq. 
My ipod detects Netgear and accesses the internet without problem why not ubuntu?
The password for Netgear is correct and being entered correctly.

Why is the button greyed out?

---

### Post by Paddy Landau on 2010-04-20
> **petert33 said:**
> Why is the button greyed out?
So, you type your passphrase, and you can press only Cancel? The button doesn't become available after typing the passphrase?

---

### Post by petert33 on 2010-04-20
Sorry Paddy, yes you're right. When I put in the acceptable password the button firms up.
The bad news is after pressing it the same window comes back, pass entered, button pressed and ...

So I've lost the grey button but not yet found salvation ...

---

### Post by Paddy Landau on 2010-04-20
> **petert33 said:**
> The bad news is after pressing it the same window comes back, pass entered, button pressed and ...
That means that the router is not accepting the passphrase for whatever reason.

As I mentioned in the previous post, you need to be very sure that you're connecting to the right router and that your passphrase is **exactly** correct.

I repeat: I recommend changing the router's name (i.e. the network name or SSID) to be sure that it's the right router you're connecting to, but that does mean changing the connection for every single wireless device you currently connect to the router. For safety, connect with an Ethernet while doing this.

---

### Post by petert33 on 2010-04-22
I agree that the router for some reason seems not to accept the password delivered from Xubuntu.
I have an even older laptop which ran on Windows XP and to which I have introduced Xubuntu. I have installed the dongle there under MS Windows XP and it works OK but slow, very slow, but Xubuntu is unable to make it work. It keeps returning to the same window with the greyed out password.
Setting up under Windows XP I can see there is one other router with a 15% signal strength against the Netgear 85%, no others are detected, so the correct router is being contacted and the same password is acceptable under Windows.

It seems as though my expectations have again been raised and dashed about the accessibility and usability of Linux. I tried some years ago with Suse without success, but I have to say that connectability to internet excepted Xubuntu seems otherwise very good and I would still like to be able to use it. Having an OS system that is fast and lean but internet-free seems like a toy rather than a serious information highway.

Am I wrong?

---

### Post by novelty on 2010-04-22
On the router side:

It would be a good idea to check all the settings on your router.  Check if you filter by MAC address.  If you do, you may have missed adding the dongle's MAC to your list.  I know with my router I can also limit the number of wireless connections if I want.

On the network card side:

Try setting your network card up manually instead of relying on it auto detecting the settings. 

On the Ubuntu side:

I had a similar problem with an old laptop.  What finally 'fixed' it was dumping the KDE desktop and switching to a different one.  This either completely cleared some setting on the card I had borked or the different network manager applet 'worked better' with my card.  I don't know which because really I am a linux NOOB and I was focusing on getting it working rather than why it worked.

Also, if possible, you may want to connect your lappy by wired connection first.  This will allow you to get updates.  Sometimes an update is all it takes.

Linux is a great OS, as with anything there is a learning curve.  I started to put it on a few machines in the interest of learning it. On my older machines I have had to poke and tweak a little to see what works best with the hardware present. Within a couple weeks I put it on my  newer machines and it is pretty much install and go.

Good luck!

---

### Post by Paddy Landau on 2010-04-22
[LIST]
[*]Tell us whether novelty's suggestion of first applying updates works.
[/LIST]

[LIST]
[*]Please also do what we said earlier: Temporarily remove security from your router.
[/LIST]

[LIST]
[*] As your Ubuntu can already access the wireless dongle, it would seem unlikely (though possible) that it's the driver at fault.
[/LIST]
  
[LIST]
[*]Two more things occur to me, Peter. But, please, try the above-mentioned things first!
[/LIST]

[LIST]
[*]In a previous post, I said:> **Paddy Landau said:**
> Are you sure that you have chosen your router and not a neighbour's router? I notice that you're using a hidden network and that your router uses the default name 'netgear', so unless you have no nearby neighbours, you could be connecting to the wrong router.

I would recommend that you go into your router's settings (you'll need to connect via an Ethernet) and change its name, so that you easily recognise it as yours and no one else's. Be aware that this will mean reconnecting *all* your existing wireless connections.That bears repeating.
[/LIST]

[LIST]
[*]The other thing is that you could try a different version of Linux. On your very old computer, you could try [PuppyLinux]("http://puppylinux.org/"). It's basic -- really, really basic -- but boy it's fast!
[/LIST]

---

### Post by petert33 on 2010-04-22
Thanks Novelty.
My router does not restrict on MAC it is open to all - so I will sort that later.
Why muck about with the network card when the same card is creating access under Windows?
I really am a Linux newbie and my ignorance of most of what goes on 'under the bonnet' is becoming clearer to me by the minute.:confused:

---

### Post by petert33 on 2010-04-22
Thanks Paddy. I'm not sure what update is required. Xubuntu is newly acquired.

---

### Post by Paddy Landau on 2010-04-22
> **petert33 said:**
> Thanks Paddy. I'm not sure what update is required. Xubuntu is newly acquired.
When you get a Windows disk, you still need to apply all the updates. The same applies to *buntu.

Please follow the steps, otherwise we can't help you any further.

---

### Post by petert33 on 2010-04-22
I must assume that the package I downloaded the other day from Ubuntu is not uptodate - OK.
How do I do that? I have located an ethernet cable which I had previously used for the BT broadband connection but now I am in the tender embrace of Virgin. Do I unplug the Netgear router from the Virgin box and connect the laptop, presumably with Ubuntu running or what? When I get connected what do I do?

---

### Post by Paddy Landau on 2010-04-22
> **petert33 said:**
> I have located an ethernet cable...

[LIST]
[*]Leave your router plugged in to the Virgin modem. You want to connect to the router, not to the modem. The router most likely has an extra firewall built in.
[*]At the back of the router you should have two or more places that you can plug in your Ethernet. Connect the Ethernet from the router to your computer.
[/LIST]
> **petert33 said:**
> When I get connected what do I do?

[LIST=1]
[*]Give your computer a minute or so to connect.
[*]Go to System > Administration > Update Manager.
[*]Press Check, and enter your password if prompted. Wait while it looks for updates.
[*]Press Install Updates (if remains greyed out, then you're up-to-date already) and follow the instructions, if any.
[*]Reboot, even if you are not prompted to do so.
[/LIST]
Now you can disconnect your computer. Connect your wireless and find out whether it works. If it doesn't, follow the instructions to temporarily disable security, and I strongly recommend that you also change the SSID of the router to clearly identify it as yours and not your neighbour's. You might have been connecting to your neighbour's wireless accidentally.

---

### Post by petert33 on 2010-04-22
Thanks Paddy, I'll give it a go.

> **Paddy Landau said:**
> You might have been connecting to your neighbour's wireless accidentally.

When I checked on MAC selection I could see my laptop as acceptable to the router (in Windows)!
I am reluctant to upset my existing setup by changing the router name etc when on current evidence I may not run or be able to run as I wish Xubuntu.

---

### Post by petert33 on 2010-04-22
Update manager tells me I'm uptodate. Last updated 6 days ago.

---

### Post by petert33 on 2010-04-22
I've looked in my Netgear router manager programme and the laptop has disappeared now I'm trying to connect in Xubuntu, but it was there in Windows.

---

### Post by petert33 on 2010-04-23
Is there anybody who can pick up this problem and help me resolve it? Or must I ditch a promising OS?

---

### Post by alphacrucis2 on 2010-04-23
> **petert33 said:**
> Is there anybody who can pick up this problem and help me resolve it? Or must I ditch a promising OS?

Just a thought. Is your wireless access point actually configured to use WEP instead of WPA?

---

### Post by petert33 on 2010-04-23
Thanks for responding.

I have selected wpa+wpa2 on the router and the same when requested by Ubuntu.

Looking for similar posts I found one where his connection problem was solved by unlocking the driver in the Hardware Drivers program. When I access HD it says 'No proprietary drivers are in use on this system'.

---

### Post by alphacrucis2 on 2010-04-23
Grasping at straws here but you could try adding the connection to Network Manager manually. Instead of left clicking Network Manager, use the right hand button and select Edit Connections.Then:

1. Click the Wireless tab and click ADD.

2. Type in a name for the new connection. This can be anything as it is only used by Network Manager. Type in the SSID and make sure Mode is set to Infrastructure.

3. Click the Wireless security tab and select WPA & WPA 2 personal. Type in your password/psk. Note that you might have trouble here if the password is less than eight characters as 'Network Manager' doesn't allow shorter passwords:confused: and will disable the apply button for shorter passwords. 

4. Click Apply then Close.

5. Right click Network Manager again and click where is says enable wireless (this will remove the tick and disable wireless). Repeat to enable. Will it connect then?

---

### Post by petert33 on 2010-04-23
Sorry Alphacrucis2, I've done as you suggested but it still loops around to the same panel requesting Authentication.
I'm putting in the same info as I do for Windows, which connects, the hardware is the same the drivers are the same unless generic drivers are used by Ubuntu ...:confused:

---

### Post by alphacrucis2 on 2010-04-23
> **petert33 said:**
> Sorry Alphacrucis2, I've done as you suggested but it still loops around to the same panel requesting Authentication.
I'm putting in the same info as I do for Windows, which connects, the hardware is the same the drivers are the same unless generic drivers are used by Ubuntu ...:confused:

I believe it is possible to use the Windows driver in Ubuntu using a thing called Ndiswrapper. I don't know much about it though. You would have to search the forums for an explanation. Another thing might be to wait until Xubuntu 10.4 is released next week and try that as it comes with newer versions of the OSS drivers, kernel, network manager etc. If you don't mind the extra download you could download the release candidate now. You can test it out without installing via the live CD option.

---

### Post by petert33 on 2010-04-23
Thanks alph, I'll give it a try.
Should I do it straight to the laptop via ethernet or via this iMac?

---

### Post by petert33 on 2010-04-23
I've checked the Xubuntu site and it says 10.4 beta is not for persons looking for a stable system - that's me:(

No other ideas?

---

### Post by Paddy Landau on 2010-04-23
> **alphacrucis2 said:**
> I believe it is possible to use the Windows driver in Ubuntu using a thing called Ndiswrapper.
Good call! You're right. I've used it before (not for Belkin, though).

[LIST]
[*]Install ndisgtk from Synaptic.
[/LIST]
Here are two references for how to use it.

[LIST]
[*][Ubuntu Community Documentation for ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). This tells you how to use ndiswrapper, including the GUI interface (see [section 3.4.1]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver%20using%20ndisgtk%20%28ndiswrapper%20graphical%20interface%29")).
[*][Auto ndiswrapper]("https://launchpad.net/auto-ndiswrapper") to automate the process. I've never used it, so I don't know whether it works.
[/LIST]
 Peter, as you need a stable system, I'd wait until 10.04 is released. However, until then, experiment with ndiswrapper on your current Xubuntu system to find out whether you can make it work.

Good luck.

---

### Post by petert33 on 2010-04-24
Even though I have the Edimax dongle driver on the windows system I have noticed that there is Linux driver on the Edimax CD.
What should I do? Install the Linux driver? If so how? The ndiswrapper page warns against driver conflict disabling ubuntu. Should I uninstall the Windows driver?
Or just sit on my thumbs until 10.4 is out?
Or buy another dongle? Netgear to match the router?

Comments/assistance appreciated.

Many thanks

Peter

---

### Post by petert33 on 2010-04-24
I've looked on the ndiswrapper pages and my Edimax EW-7711UTn dongle doesn't appear on the list there.
Is there anyway of finding out which usb wireless adapters will be supported on Xubuntu 10.4? The simplest way would seem to be to ditch the Edimax and use a supported dongle- right?
Or not?
:confused::confused::confused:

---

### Post by Paddy Landau on 2010-04-25
> **petert33 said:**
> The ndiswrapper page warns against driver conflict disabling ubuntu. Should I uninstall the Windows driver?
Or just sit on my thumbs until 10.4 is out?
Or buy another dongle? Netgear to match the router?
Peter, whatever you do on Xubuntu:

[LIST=1]
[*]If you follow the instructions for ndiswrapper, you can undo all those changes, and:
[*]Soon, you will be able to install 10.04, meaning that if you totally screw up then it doesn't matter. At this point, you're experimenting.
[/LIST]
 > **petert33 said:**
> 
Is there anyway of finding out which usb wireless adapters will be supported on Xubuntu 10.4? The simplest way would seem to be to ditch the Edimax and use a supported dongle- right?
Yes, I guess so. But, Peter, you still haven't done what we asked you to before. Your system does recognise your current dongle, and you know that because the system sees the wireless networks out there. So quite possibly it's something else, and we can't check it until you do what we asked.

---

### Post by petert33 on 2010-04-30
Thanks for all the advice so far, especially Paddy (whose patience was strained by my obstinacy:() I have used a Netgear dongle onto the desktop PC (Compaq) under Ubuntu 10.4 from the CD. SUCCESS!!:)
Now that I can access the internet I want to have Ubuntu 10.4 on that PC rather than the Xubuntu 9.10 currently on the hard drive.
I think I'd still like to keep Mr Gates' OS as an insurance for now but what is the best way to proceed? I assume the Xubuntu update manager would not easily switch me over to Ubuntu.
Installing from the ubuntu cd would the Xubuntu be overwritten (I'd also like to increase the Linux share of theHD).
What is the best way to proceed?

Thanks in advance
Peter

---

### Post by Paddy Landau on 2010-04-30
I'm glad you got it sorted!

Please remember to mark this thread as Solved.

> **petert33 said:**
> I think I'd still like to keep Mr Gates' OS as an insurance for now but what is the best way to proceed?
Peter, there is a way to convert Xubuntu to Ubuntu, but sorry I'm not sure how.

However, I would suggest that you **back up your data** on **both your Windows and your Xubuntu** and then:

[LIST]
[*]Delete the Xubuntu.
[*]Freshly install Ubuntu 10.04 (it's a long-term release, so a fresh install will be a good idea).
[*]The Ubuntu installation should automatically recognise the Windows already on the computer. Each time that you boot, it will allow you to choose which system to boot into.
[/LIST]
Don't delete Windows until you've gone at least a year without using it, just in case.

Good fortune.

---

### Post by petert33 on 2010-04-30
It's been Gordian Knot time here in Cheshire and I've done a drastic thing I've gone totally over to Lucid Lynx for good or ill. Although we still have two Mac 'puters.
No doubt I'll be back on other threads ...):P

---

