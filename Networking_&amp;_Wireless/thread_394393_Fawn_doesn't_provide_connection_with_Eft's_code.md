---
title: "Fawn doesn't provide connection with Eft's code"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by pterandon on 2007-03-26
Hello.

I have a machine which was working well with wirless under 6.10.  I just installed the new Fawn release to the same box and copied over the same /etc/network/interfaces.

I get no wireless connection (encrypted network.).   I have done wireless with 6.10, SUSE, and Knoppix, and kanotix on this box.

Any tips from a perspective of why fawn might choke on eft's  /etc/network/interfaces?

Thanks-o-riffic!

---

### Post by Floppyjoe on 2007-03-26
If you are using ndiswrapper you may need to reinstall it or install a newer version.
Your encryption settings if WPA may also need to be reentered.

---

### Post by pterandon on 2007-03-26
I believe I have an atheros-based card which worked well with eft.

I had a file for /etc/network/interfaces which called out my ESSID and KEY and got me connected.

I got the file from the old Eft installation, and re-used it for fawn.   I do not get connected.


Here's possibly buggy behavior with the network manager:

I type in all my info, especially the Wireless Settings--> ESSID and WEP Key.  
I chose "hexadecimal" and "OK".  
I immediately go back to configure the device again and it's switched to a Key type of "ASCII".  
I switch back to hexadecimal, OK, Apply.  
I wait a second, then go back to configure it again:  Key type is "ASCII" and the WEP Key is blank!

---

### Post by Floppyjoe on 2007-03-26
Fawn I think has a program called network-manager installed by default. For it to work you need to have all your network interfaces disabled in System/Administration/Networking. Then you probably need to comment out all but the lo(loopback) interface in your /etc/network/interfaces file by putting a # in front of the lines in that file.

---

### Post by pterandon on 2007-03-26
Okay, but how would network-manager know my KEY?

---

### Post by Floppyjoe on 2007-03-26
There will be a little icon with bars representing signal strength on your top panel. if you click on it it will show you the available networks and then you click the one you want and enter the necessary info.

---

### Post by pterandon on 2007-03-26
okay, now I see it. ):P 

It looks like a slick interface, but it didn't connect for me.
And in kubuntu, I don't see System--> Administration. but a SystemSettings--> Network Settings.  What would I do there?

But let's say I messed up my /etc/network/interfaces. Should I #-out every single line item?

---

### Post by Floppyjoe on 2007-03-26
> **pterandon said:**
> okay, now I see it. ):P 

It looks like a slick interface, but it didn't connect for me.
And in kubuntu, I don't see System--> Administration. but a SystemSettings--> Network Settings.  What would I do there?

But let's say I messed up my /etc/network/interfaces. Should I #-out every single line item?
You only need the lines for the lo interface in there.
I'm not sure of the menu structure in Kubuntu. You will have to find the networking area somehow.

---

### Post by pterandon on 2007-03-26
No.  It just says "Activating Wireless Network Connection" for a while at 28%, then gives me the little x. 

Any brainstorming on why fawn wouldn't work? Am I the first to find a bug?  Bad install??

---

### Post by Floppyjoe on 2007-03-26
You disable it not activate it. Under All apllications-System/networking

---

### Post by pterandon on 2007-03-26
The little icon in lower right tray, when I click on it, is "KNetwork Manager."  If I Disable it, everything is down.  When I enable wireless, it shows me some neighor's wireless names.   I enter in my own essid & 40 thing  key.  A little baloon pops up that says "activating Network Connection",  then goes away.  No internet connection.

Either your last statement is not correct-- you don't disable it HERE, or I missed somewhere much earlier a place to tell the puter what my essid and key are.

---

### Post by pterandon on 2007-03-26
Fawn ***comes with*** the same if not more wireless drivers, right?

---

### Post by Floppyjoe on 2007-03-26
> **pterandon said:**
> The little icon in lower right tray, when I click on it, is "KNetwork Manager."  If I Disable it, everything is down.  When I enable wireless, it shows me some neighor's wireless names.   I enter in my own essid & 40 thing  key.  A little baloon pops up that says "activating Network Connection",  then goes away.  No internet connection.

Either your last statement is not correct-- you don't disable it HERE, or I missed somewhere much earlier a place to tell the puter what my essid and key are.

The network interfaces in System/Networking must all be disabled. Your router should be on the list of wireless networks available. You click on your access point and enter your info.

---

### Post by pterandon on 2007-03-26
Fawn 7.04 22-Mar-2007

Kubuntu has no "System--> Networking" but a "System Settings--> Network Settings".  I disabled the wireless interface there.

I go to KNetworkManager icon in lower right tray, clidk, "Connect to other wireless network", enter in my essid & key.  No dice.

Q: any chances i've got a bad install, or could it be buggy?

---

### Post by Floppyjoe on 2007-03-27
> **pterandon said:**
> Fawn 7.04 22-Mar-2007

Kubuntu has no "System--> Networking" but a "System Settings--> Network Settings".  I disabled the wireless interface there.

I go to KNetworkManager icon in lower right tray, clidk, "Connect to other wireless network", enter in my essid & key.  No dice.

Q: any chances i've got a bad install, or could it be buggy?

I don't think it is buggy or a bad install.
On my laptop when I am in Kubuntu mode it does have system/networking under the heading of All applications and also settings/networking under All applications.

Do you have a hidden essid?

---

### Post by zorkerz on 2007-03-27
Feisty's network drivers should have only improved.  The main difference as mentioned before is the switch from network monitor to network manager which gives you that spiffy interface.

I also am a gnome user so do not know exactly what you should be looking for in KDE. However your system settings -> network settings sounds right.  The idea is to disable all networking devices everywhere because network manager configures them itself. This sounds like Knetwork-manager in your bottom right bar is the only thing you want undisabled.

-So disable in settings -> network settings (if this is actually the kde place)
-/etc/network/interfaces everything commented out (# at beginning of line) except lo
so something like this
> auto lo
iface lo inet loopback
I think you have done this and i am just trying to summarize and get us all on the same page. Hope it helps others besides myself. 
-is this the place where network-manager or Knetwork-manager does not connect to your network?

---

### Post by pterandon on 2007-03-27
yes, that's the place.

I type in my ESSID, select Encryption: WEP hex, paste in the key, then Connect.

I get the rotating purple gears "Activating Wirless Network Connection," but then it goes to a little red x.



Feisty's wireless support got much worse.  For 6.10, I didn't have to ask because I already knew.

---

### Post by zorkerz on 2007-03-27
Sorry for the trouble. You are now past my ability to help though there will most likely be someone out there with the same problem. Keep in mind feisty has not been released yet so if you can locate you problem and file a bug or more likely join an already created bug it could get fixed for release. Also if you could find another kde user you have diff icons and everything which limits my ability to know what works and does not.

I might try starting a new post with a more specific title also liking here so people know they are related but a diff title may draw the attention of some one who knows more about it. Use network-manager or search around for it there are lots of people trying to switch to this app as it in the long run will be much better than network monitor. Good luck sir.

Actually a great place to start would be to try to connect to an unencrypted network or one without wep or any security. If knetman can connect here then you know that everything is working except wep. Ive had alot of trouble with wep but network-manager is supposed to be much better at this.

---

### Post by pterandon on 2007-03-27
> **zorkerz said:**
> Sorry for the trouble. 

Thanks to everyone who read or responded, but especially zorkerz for this positive attitude towards a griper.

This surely ain't  *[FONT="Comic Sans MS"]other distro name deleted to prevent a flame war.[/FONT]*

---

### Post by zorkerz on 2007-03-27
ever find a solution?

---

### Post by pterandon on 2007-03-28
> **zorkerz said:**
> ever find a solution?

No.  I was thinking that either:   i)  it's a buggy interface,   ii) my physical media were bad, or   iii) my blind tinkering with the stuff at the beginning, in my 6.10-thinking, messed it up.   

I burned new media, and did a CD check. It shows a Buffer I/O problem.

[http://www.ubuntuforums.org/showthread.php?t=395251](http://www.ubuntuforums.org/showthread.php?t=395251)

---

