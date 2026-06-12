---
title: "Network Manager 0.7 for Gutsy"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by frediE on 2007-10-26
Any one have or know where to get Network Manager 0.7 for Gutsy?  I am looking (but not finding) the following...

     network-manager_0.7
     network-manager-gnome_0.7.0
     network-manager-vpnc_0.7
     and and dependencies of course.

big thanks in advance!

Its seems as thought when I connect with network manager vpnc it does not update my route.  And 0.7.0 used to work well in Feisty, but after I upgraded to Gutsy, it downgraded my network manager.  :-(

---

### Post by jfrorie on 2007-10-26
> **frediE said:**
> Any one have or know where to get Network Manager 0.7 for Gutsy?  I am looking (but not finding) the following...

     network-manager_0.7
     network-manager-gnome_0.7.0
     network-manager-vpnc_0.7
     and and dependencies of course.

big thanks in advance!

Its seems as thought when I connect with network manager vpnc it does not update my route.  And 0.7.0 used to work well in Feisty, but after I upgraded to Gutsy, it downgraded my network manager.  :-(

I might be crazy, but I don't think 0.7 is out.  I think latest is .6.5.  Gnome FTP Server is here.

[http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/)

Jim

---

### Post by zorkerz on 2007-10-26
ya 0.6.5 is definitely the default in gutsy. I do not remember 0.7 being the default before but i probably never checked. Although network manager is much better than network monitor was it still has a long way to go in my mind.

Actually checking the network manager page [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
it looks like 0.6.5 is the newest stable version. I just check the ubuntu package search and it looks like feisty defaults to 0.6.4

That said one thing I would like to be able to do is restart network manager without restarting the computer. sometimes it craps out on me and wont connect to a network or does something funny and I am forced to restart my machine. I know there must be a better way to do this I just don't know how.

I have a intel PRO/Wireless 4965 using the iwlwifi driver I believe.

cheers

---

### Post by alastair on 2007-10-26
> **zorkerz said:**
> That said one thing I would like to be able to do is restart network manager without restarting the computer. sometimes it craps out on me and wont connect to a network or does something funny and I am forced to restart my machine. I know there must be a better way to do this I just don't know how.
cheers

Yes - NM is behaving a lot worse in 7.10 compared to 7.04 on my Thinkpad laptop (ipw3945).

I'd like to be able to properly reset as well - so far, the following generally works (from a shell) :

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/25NetworkManager start

Alastair

---

### Post by zorkerz on 2007-10-26
Ill give those a try what do you mean by generally? Are there time when they don't work? anything specific?

---

### Post by alastair on 2007-10-26
> **zorkerz said:**
> Ill give those a try what do you mean by generally? Are there time when they don't work? anything specific?

Well ...


Feisty (7.04) NM *generally* worked well. Few problems I can recall. Decent auto-sensing networks. Good connection quality. Passphrase requested once per session (gnome-keyring).

Gutsy :

Sometimes works OK.
Connection seems to drop regularly. Sometimes gets wedged (animation sticks even).
Reset (as per above) often "resets" to normal operation.
Sometimes NM seems to want a passphrase - multiple times, after dropping. Again.
It doesn't store passphrase in keyring (or at least is not prompting me to unlock keyring, like 7.0.4)

Basically a lot less reliable. 

The above stop/start - seems to work better from a shell. I have it as a "launcher" on my panel (gksudo ..), but it seems less functional there ...

---

### Post by zorkerz on 2007-10-26
I get dropped connections alot and once they are dropped it can rarely pick up anything again.

sometimes it automatically connects (or attempts) to the wrong network at my house and it cannot get anything else after that.

I have not had any problems with the keyring it seems to behave normally.

I get the animation freeze sometimes always when the head of the "comet" is at about 1 o'clock and other times it disappears completely leaving a blank spot next to the power meter where it normally sits.

---

### Post by FlyingIsFun1217 on 2007-10-26
It will be a godsend when NM 0.7 arrives. I'll be counting the days!

FlyingIsFun1217

---

### Post by tedrampart on 2007-10-26
you've described all the symptoms that have haunted me since installing gutsy.  

the only thing to add that I notice is nm won't update itself correctly if I go from one location to another without either suspending/hibernating (which generates its own problems with nm), disabling networking entirely, or shutting down before relocating.

so say I'm at a friends doing webdesign, then leave and come home, I get to my house and have to restart nm before I can even see my network.

I'm rather unimpressed by this release of NM, hopefully these get fixed asap!

---

### Post by zorkerz on 2007-10-27
any of us know  how to diagnose this a bit maybe file some kind of bug report?

---

### Post by portach king on 2007-10-27
I'm delighted (though disappointed) to see other people having my problem. The worst case for me is that it simply REFUSES to connect to my college network for more than 5 minutes. Once is disconnects, reconnecting rarely happens and if it miraciously does, it dies again (Usually crashing firefox and all the work I was doing on it in the process). Which is extremely irritating as I use JSTOR a lot.
Fiesty (or should I say, Network Manager 0.6.4) at least stayed connected. When is the expected release of 0.7? Or is there a way I could downgrade back to 0.6.4 (I've checked the repositories, but the option to downgrade isn't available)

---

### Post by kevdog on 2007-10-27
Try connecting from the command line -- if you get no crashes with the command line manual approach you can actually pinpoint that its most likely a problem with network manager rather than in the wireless tools package within the linux kernel.

The instructions are in my signature.

---

### Post by frediE on 2007-10-28
I get lost in the woods on the 4-wheeler for a few days and see all the goodness I miss.  Network Manager (NM) .0.7 is out there and .debs were created for Edgy.  I emailed the developers to see if they create some packages and help some folks out, even if it is, Yes the new works but not supported.

The issue I am seeing is with the network-manager-vpnc where it does establish a connection, it gets an IP address, even gets the DNS servers, but I don't think is setting up the route (route -n) correctly.  Not sure I know the linux output well enough to make that assumption.

Any who, it appears the vpnc connection makes a good connection, but I cannot pass traffic across the VPN connection.

---

### Post by zorkerz on 2007-10-28
Hmm i have no problems with vpnc or network-manager-vpnc which I use to connect to McGill's network for jstore and stuff.

Could you point a link to the NM 0.7 you have found. Judging from their website [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) 0.7 has not been released officially yet and is still under development. This should not mean its no good just likely not to be at a stable place for everything yet. If someone has reason to believe otherwise  please let me know. 

I read a blog that was saying great things about NM .7 I would be very surprised if it was out and not in gutsy.

cheers

---

### Post by frediE on 2007-10-29
you can download the Network Manager 0.7 Edgy debs from here
[http://ubuntuforums.org/showthread.php?t=285063](http://ubuntuforums.org/showthread.php?t=285063)

---

### Post by zorkerz on 2007-10-29
This thread is a year old in 3 days it was closed when feisty came out. NM 0.7 has still not been released in that time. The NM 0.7 debs linked to are now nearly a year old.

If you want to use prerelease software that is great but at least get it up to date so that you can help out by fileing bugs that were not fixed a year ago. Alot happens in a year especially on a high profile open source package such as Network manager.

If you can compile it again yourself from the CVS (as was done for those debs) or get someone to do it for you, then you will help yourself by having newer, more stable, and feature complete software. You will also help everyone by being able to file bugs and help NM 0.7 to be released.

if i ever find the time to learn how to compile .debs properly ill help directly.
cheers

---

### Post by frediE on 2007-10-30
yes i was trying to figure out the whole creation of deb files myself so i can help a few others.

not to start a banter but what's worse 2-year old .6.5 or 1-year old .7?  no pressure network-manager team.  :-)




in my testing,  command line also does not work (thanks kevdog for the suggestion).  i booted from a live CD (because my install was an upgrade) and it worked.  arg, at least there is hope.

resolve.conf, ifconfig, and route -n were the same on both systems.  any other thoughts on what i can test or troubleshoot.  i hate to fresh install just for this but I need my vpn for that silly thing they call work.

---

### Post by zorkerz on 2007-10-30
you do have a point about .65 being quite old. Its probably still more stable because it was made as a release. Whereas yours is just a random snapshot.

Im sorry youve got vpn troubles mine works fine in .65 could it be a wireless driver thing?

do you get any errors? maybe if you ran nm-applet in a terminal or network-manager-vpnc you will get some error that is meaningful to somebody.

There should be some way to reinstall networkmanager and vpnc and set all there settings back to default that would fix your problem if a live cd worked. This is one thing that there does not ever seem to be an easy way to do in ubuntu.

Good luck

---

### Post by adwatkin19 on 2007-11-01
Hi all

I did some googling and although this isnt a solution it has set me up until 0.7 comes out. 

I downloaded the deb packages from Fiesty for the 0.6.4 version and uninstalled the 0.6.5. ones and then installed the .6.4 ones, needed a couple of reboots for some reason, but now hay presto flawless wireless and wired connection

by the way i am running the AMD64 version. 

hope this helps someone.

---

### Post by GrammatonCleric on 2007-11-02
I too am having issues with the Gutsy release of NM.  VPN connectivity while on wireless is broken badly. Basically if you connect to your VPN while on wireless you loose all network connectivity.  Disconnect from the VPN everything returns.  Connect to same VPN using Ethernet everything works fine.

-GC

---

### Post by lisc998 on 2007-11-02
I seem to get the same symptoms as others, but I'm not using Network Manager. Just using vpnc  from the command line gives exactly the same. Also, I'm not using wireless, I currently use IP over mains, but I could try plugging in to my router directly. I shouldn't think it would make any difference though. :(
Tim

---

### Post by GrammatonCleric on 2007-11-02
Reported bug....

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/159484](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/159484)

-GC

---

### Post by zorkerz on 2007-11-02
Its interesting that .6.4 works better than .6.5.  I will also repeat just for some that my vpn works fine with network manager. I installed the packages vpnc and network-manager-vpnc. Sorry your all having trouble.

---

### Post by hcorey on 2007-11-02
I have similar problems with wireless and Gutsy as many other-frequent, unexpected drops, many attempts at work-around, etc. NM 0.7 (using debs posted here) works for me a little better than 6.5, in that after the drop it is eager to re-connect. The result is still annoying but at least more usable (but not good)

---

### Post by tvst on 2007-11-04
Can you try deactivating IPv6 to see if it's the same problem I used to have?

CAUTION: only do this if you're *not* using IPv6 (most people).

- edit /etc/modprobe.d/aliases
- change line "alias net-pf-10 ipv6" to "alias net-pf-10 off ipv6"
- reboot

if you don't see the original problem anymore, please post on the bug report below to make sure people notice it:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/158481](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/158481)

if the problem is still there, reactivate IPv6 as follows:

- edit /etc/modprobe.d/aliases
- change line "alias net-pf-10 off ipv6" to "alias net-pf-10 ipv6"
- reboot

---

