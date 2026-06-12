---
title: "Ubuntu Netbook Remix can't connect to FiOS Router"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Capt. Easy on 2010-05-01
I've just loaded Ubuntu Netbook Remix 9.10 onto an Acer Aspire One.  It's on a new hard disk and is the only OS -- no Windows.

Nearly everything is working well, but I cannot connect to our wireless router, from Verizon for FiOS.  The netbook is picking up our network but won't accept the key.

I've looked at the Router's Basic Security Settings, and it seems to be looking for a 64/40 WEP Hex Key (64-bit WEP).

The Admin settings offer me:

WEP 40/128-bit Key
WEP 128-bit Passphrase
LEAP
Dynamic WEP (802.1x)


I've tried our key in all of those options, just in case, but no luck.  Does anyone know of a way to get the proper option for the netbook?

Thanks!

---

### Post by Jon Monreal on 2010-05-01
A64-bit key should work with WEP 40/128.

Which Aspire One are you using?

Thanks.

---

### Post by Capt. Easy on 2010-05-02
Thanks --

I'm using an Acer Aspire One model D250-1958 (AKA AOD250).

I just got it and I made one change to the hardware -- I removed the original 160 GB hard drive (with Windows XP installed) and replaced it with a 120 GB Western Digital hard drive (WD1200BEVT).  I installed Ubuntu as the only OS on the 120 GB drive.

When I searched for a signal I got our home network as well as two neighbors' -- but entering the key never establishes a connection.  I am sure that I am entering the correct key.  I've got a print-out of the router's basic security settings and I *seem* to be doing everything right -- but no connection.



I should note that *almost* all other aspects of the OS seem to be working.  I have used the Open Office word processor and spreadsheet, I've played MP3s on Rhythmbox, turned on the internal camera with Cheese, etc.

The only other problem I'm having is that I cannot change the system time, but I can't see how that would be connected to the wireless problem.

I'm brand new at Ubuntu (and Linux) but worked a lot with Unix Sys V R1 through R3 back in the 80s, so I have some familiarity with the basics.  I appreciate any guidance you can offer.

---

### Post by Capt. Easy on 2010-05-02
Just for the heck of it I tried installing Ubuntu Netbook Remix 10.04.

No change at all on the wireless router problem.


Bu-uuu-ut, the time was a different matter.  I opened the admin tool and reset the clock.  I changed the hour, the minute, and the day.  I got an error message saying that an Unspecified Error had occured and that the information could not be saved (not the exact wording) -- but the change ***had*** been made.:confused:

Then I noticed that I'd set it to the wrong time -- I was 4 minutes fast.  I tried to set the time again, but no luck.  No error messages, but no changes.




Still, I'd love to reach the router and get that netbook on the internet.

---

### Post by louieb on 2010-05-02
Since you can see the router. Just a shot in the dark - is router doing MAC filtering?  Each network card has a unique MAC address - most routers can be set to allow only certain MAC addresses to connect.

---

### Post by Capt. Easy on 2010-05-03
Someone saw my problem, pointed me at [this thread](http://ubuntuforums.org/showthread.php?t=974272), and suggested that WICD might solve my problem.

This is my first Ubuntu implementation, and I couldn't find the answer to this on my own, so I'm need some newbie help.  Is there any way that I can download WICD to a Windows computer, copy it to a CD or flash drive, and then install it on the netbook?  Obviously I can't use the internet to get this with the netbook, since I can't get onto the internet without it. :(


Also, does anyone else have an opinion on whether or not this is likely to help fix my problem?  I'm not doing anything serious with the set-up yet, so I can always try something and then reinstall the OS if necessary.

Continued thanks for any help!

---

### Post by Jon Monreal on 2010-05-03
WICD is another network manager you could try.

You can download a .deb package for offline installation at the [bottom of this page]("http://packages.ubuntu.com/karmic/wicd"); however, you would likely need additional dependencies as listed above (which have their own dependencies, and so on).

Could you possibly connect using an Ethernet cord or change the encryption used by the wireless router at least until you can download the packages? This would be much easier than trying to download the package and all of its dependencies by hand.

---

### Post by Capt. Easy on 2010-05-03
Changing the router settings is more complicated than one might think.  My wife works at home and absolutely needs the router and her Windows laptop to work.  This is a matter of "don't fix it if it ain't broke" for her -- and, right now, her Windows laptop "ain't broke."

Honestly, given my experience with Windows, I would also be reluctant to mess with a working setup unless I absolutely needed to.



I could probably look into connecting the netbook with a cable, but that will have to wait until the end of the week when I intend to do some maintenance on my (Windows) desktop PC.  Since the netbook is a "blank slate" right now I might just go ahead and try the download method.  I'll let you folks know how it works.

---

### Post by Capt. Easy on 2010-05-03
Update:  I seem to have successfully removed Network Manager and restarted the netbook.  The good news is that I am no longer getting prompted to connect to the wireless network (which eventually fails and prompts me again).

The bad news is that when I try to install the WICD package from the flash drive I get a screen that tells me it conflicts with Network Manager.  It doesn't let me get any farther -- at least, I can't find a way.

Have I left traces of Network Manager even after rebooting?  Any ideas?

(Once again, there's nothing but an empty OS on the netbook at this point -- if I completely trash it I can always reinstall.)

---

### Post by Jon Monreal on 2010-05-03
Did you remove both network-manager and network-manager-gnome?

> Changing the router settings is more complicated than one might think.   My wife works at home and absolutely needs the router and her Windows  laptop to work.  This is a matter of "don't fix it if it ain't broke"  for her -- and, right now, her Windows laptop "ain't broke."

Honestly, given my experience with Windows, I would also be reluctant to  mess with a working setup unless I absolutely needed to.

If it's Vista or 7, then it's simple really to delete the old wireless configuration and make a new one, but I'm not trying to force anything on you.

Also, if you're worried about security over the network, you should know that [WEP is fairly weak]("http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws") compared to WPA and WPA2.

---

### Post by Capt. Easy on 2010-05-03
> **Jon Monreal said:**
> Did you remove both network-manager and [COLOR=Red]network-manager-gnome?[/COLOR]
...


:redface:

And I was so-ooo proud of myself for a few minutes.




> **Jon Monreal said:**
> 
...
If it's Vista or 7, then it's simple really to delete the old wireless configuration and make a new one, but I'm not trying to force anything on you.

Also, if you're worried about security over the network, you should know that [WEP is fairly weak]("http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws") compared to WPA and WPA2.

That's okay.  It's XP and it has been set up (and probably tweaked) by her employer -- a major computer corporation.  I will mention the security aspect (probably not major -- we live at the end of a long dead end, out of the way, and no place for people to loiter unnoticed), and she'll probably want to run it past her IT dept.

---

### Post by Jon Monreal on 2010-05-03
> **Capt. Easy said:**
> :redface:

And I was so-ooo proud of myself for a few minutes.

It's a small mistake; if you're using Synaptic, make sure to select remove completely (or use apt-get remove --purge in the terminal).

Can you connect to the network now, or is it still giving you problems?

> That's okay.  It's XP and it has been set up (and probably tweaked) by her employer -- a major computer corporation.  I will mention the security aspect (probably not major -- we live at the end of a long dead end, out of the way, and no place for people to loiter unnoticed), and she'll probably want to run it past her IT dept.

Really understandable with XP. I can remember getting problems with networks showing up as "NETGEAR", "NETGEAR 1", "NETGEAR 1 2", etc with XP. For as much as Vista was bashed, it does feature some nice improvements over XP, especially in networking.

---

### Post by Capt. Easy on 2010-05-04
Here's my current status.  When I tried to install wicd_1.6.1-3ubuntu1_all.deb from a CD I did, indeed, wind up with a dependency problem and it balked.

I rolled the netbook back to Ubuntu Netbook Remix 9.10, removed Network Manager and tried to install wicd_1.5.9-2_all.deb.  It seemed to install and run properly, but won't connect to the wireless router either.  No error messages, it just doesn't connect.

I won't be able to try a hardwired connection for a few days, but I'll let you know how it goes.

---

### Post by RetchingRabbit on 2010-05-04
I always recommend turning OFF any encryption TEMPORARILY for troubleshooting purposes. After you establish a connection, it is often easier to set up encryption.

---

### Post by Jon Monreal on 2010-05-04
Just curious: have you ever successfully connected to a wireless network with your netbook? Just want to make sure we aren't dealing with some kind of hardware problem.

---

### Post by Capt. Easy on 2010-05-04
No -- in order to test that I could swap the original HD back in and fire up the Windows XP that it came with.  Before I do that I'd rather try installing WICD via a hard-wired connection.  Especially since it looks like others have had this problem.  I should be able to do that this weekend.


Here's a thought, though.  We have Barnes and Nobles and Starbucks nearby with wifi access.  I'm assuming (always dangerous) that I'd be able to connect easier to a public wifi setup.  Is that reasonable?  Worth a shot?

---

### Post by Jon Monreal on 2010-05-04
It would probably be easier. I believe that both Barnes and Noble and Starbucks charge for access, but you should be able to at least get on to the screen where they charge you just to see that it works.

---

### Post by Capt. Easy on 2010-05-06
Status Update:

I got a hardwired connection for the netbook to the router and downloaded all updates and WICD.  Using Synaptic I completely removed Network Manager (and Network Manager gnome) and installed WICD.

I got WICD and tried to establish the wireless connection.  It reported that it successfully passed several steps, but got stuck on trying to find the IP.  I opened the properties for the wireless network and entered the IP.  

On the next try it looks like WICD got the Netmask and Gateway on its own, but now it's stuck on the next step.

The error message is:

Connection Failed:  Could not contact the wireless access point.



I hate to feel like a sponge, but this is all new to me.  Can anyone make a suggestion for my next move?


Thanks!

---

### Post by Capt. Easy on 2010-05-06
Sorry -- Posting from my Windows XP desktop, and it hiccupped..

---

### Post by BlitzkreigBop on 2010-05-06
Try connecting using an Ethernet Cable, then activate your Hardware Drivers if they arent already. I've had the same problems not too long ago.

(I haven't read the thread so I don't know if someone may have told you this already.)

EDIT: I just read your last post, we're using the same service provider so check and make sure that you have entered the correct information. Oh, and try connecting to a Hidden Wireless Network and then put in your Router's Info.

---

### Post by Capt. Easy on 2010-05-06
I opened Hardware Drivers in System -- all it says are "No proprietary drivers are in use on this system."

I'll try the hidden network approach next.

---

### Post by Capt. Easy on 2010-05-06
Using WICD it looks like I have to find a hidden network by its ESSID, which I've already used for our home network.

Anyway, I tried and get the same result.

---

### Post by Capt. Easy on 2010-05-07
Okay, I'm investigating along the lines **BlitzkreigBop** suggested and found this page:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Although specifically for the Dell Mini, there are success reports from Acer Aspire One AOD250 owners.

I used the Synaptic Package Manager to find the Broadcom drivers.  They appear to load properly and I reboot, but nothing shows up in Hardware Drivers, and when I go back to SPM I find the Broadcom files have to be marked to be reinstalled.

Does this ring any bells with anyone?

Thanks.

---

### Post by Capt. Easy on 2010-05-07
Also, I'm wondering if I should move this to the Networking and Wireless forum.  I think this may be beyond just Absolute Beginner Talk. :-(

---

### Post by Capt. Easy on 2010-05-07
Okay, well, apparently Acer is pretty flexible when it come to making AOD250s.  I just did an "lspci" in a terminal window and it appears I have an "Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)"

I suppose that explains why the Broadcom stuff didn't stick.

---

### Post by Jon Monreal on 2010-05-07
Here's something to try:

Press Alt+F2, type
```
sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```
and press enter.

Now comment out "blacklist ath_pci" by adding a # in front of it, so it will read
```
# blacklist ath_pci
```
and save the file. Restart your computer, and see if it works.

---

### Post by Kli4d on 2010-05-07
Sorry, I'm just gonna interrupt for a second. I've been having some seemingly unrelated problems with my internet connection on my acer aspire one and wicd fixed them. Thanks for whoever suggested that. Interruption over.

---

### Post by Capt. Easy on 2010-05-07
Good for you, **Kli4d**!  :D


No luck here, though.

I commented out the blacklist item and tried it with my WICD setup -- no luck.

I then did a new reinstall of UNR, commented out the blacklist item, and tried it with the Network Manager that comes with the OS -- no luck.



As much as I'd rather not, I guess I'll put the original HD back in and start up Windows XP to see if *that* can get connected.  :(

---

### Post by Jon Monreal on 2010-05-07
Maybe you should give UNE 10.04 a try.

---

### Post by Capt. Easy on 2010-05-07
Not to be dense, but is that Ubuntu Netbook Remix 10.04?

That's what I've been using for most of these trials, including the most recent.



I guess my terminology may be inaccurate.

---

### Post by Jon Monreal on 2010-05-07
Sorry, I meant give 9.10 another try (with 10.04, it's now Ubuntu Netbook Edition). There seem to be a multitude of problems with Atheros AR928X and Ubuntu, and the only solution (besides using XP) might be an older kernel.

---

### Post by Capt. Easy on 2010-05-10
Okay, I'm back to the Raw Sienna screen of 9.10 UNR.  I haven't tampered with anything -- no WICD, no un-blacklisting, etc. -- and I'm open to suggestions.  I'm connected with a cable and updating right now.

---

### Post by Capt. Easy on 2010-05-11
I should also mention that I tried a few other distros over the weekend.  Most fared no better than Ubuntu, but two -- Slax and Zenwalk -- seemed to do better.  In both the computer reported that I was connected to the wireless router after one try and continued to show that I was connected, but I was not actually able to go online.  Of course, I didn't go to deep with it in terms of tweaking WICD or any profiles, etc.

Ubuntu also won't let me change the time on the netbook, but both Slax and Zenwalk had no trouble at all with changing the system time.

---

### Post by Capt. Easy on 2010-05-23
And I'm back.

Inspired by how close Zenwalk came to connecting I tried a few more distros.  In particular I spent the past few days running Mandriva.  It struck me as very powerful, but better suited to a desktop -- it was too awkward to get around on the netbook's 10 inch screen.

But ... the wireless worked right away.



I decided to give Ubuntu one more try and loaded the 10.04 Netbook Edition.  I downloaded the updates,, disconnected the cable, configured the wireless, and ... I had wireless.  Firefox had no trouble getting to Google.

I got no idea.


Anyway, I may try some other versions of Ubuntu -- the Netbook Edition seems a little too "blocky."  Although I suppose I should leave well enough alone!



Thanks to everyone who tried to help.  I wish I could tell you what worked.

---

