---
title: "Setting up Vuze"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by alohanate on 2011-01-08
I am attempting to set my computer up to use Vuze (from thepiratebay.org).  Somehow I downloaded 1.3% of a torrent and then it stopped and will not download any torrents. I believe my problem is either opening a port using iptables (which I know nothing about) or forwarding the port to my router.

This is the error I receive:

"Testing port 6881 ... 
NAT Error - Connection to 204.9.111.230:6881 (your computer) refused."

What information will you need in order to help me?

I am using a wireless connection behind a router.

Pleas help!

---

### Post by mikewhatever on 2011-01-08
First, what is 'Vuze (from thepiratebay.org)'?

For opening a port on your router, check out portforward.com, it has nothing whatsoever to do with iptables.

---

### Post by Ocxic on 2011-01-08
ok, first thing, DO NOT use port 6881, use a higher port number, in the 4500-6000 range.
not having the port open only prevents incoming connections, and while may impede your downloading, will not prevent you from anything.

it is possible that you have a bad torrent, that does not have any seeds for the download, or could be a bad torrent designed to wast your time and bandwidth.

---

### Post by alohanate on 2011-01-09
Thank you for the prompt responses.

mikewhatever:  Vuze is a torrent site and thepiratebay.org is the website I use to find torrents.  I am currently trying to go through the site you recommended and I am confident that it will get me to where I need to be.  I am unsure if I have a static IP address or not, however (I tried to set it up earlier).  On the file "interfaces" in **/etc/network/interfaces **it reads 

"auto lo
iface lo inet loopback"

which I believe means that it IS a static IP address.  If you know, does that mean it is or isn't?

Ocxic:  Thank you for the advice.  Just out of curiousity, why should I not use port 6881?  I changed it to 4555.

And that's what I thought!  I didn't think it would prevent information from coming in.  But apparently I am unable to connect to any peers or seeds.  And I know for a fact that it isn't a bad torrent, I downloaded the same torrent on windows 2 days ago (I just switched to incredible ubuntu) and chose it specifically because I know that it works.

Thoughts?

Thanks again for the promptness!

---

### Post by mikewhatever on 2011-01-09
Basically, there are two ways to go about it. The simplest and easiest is to enable upnp in Vuze. Upnp is the technology that allows opening ports dynamically, no need for port forwarding or static ips. There should be a setting in Vuze (the program, not the site) to turn upnp on. Look for it or check the wiki. The other way is to set up a static ip and forward a port. It's no rocket science, but may be a bit difficult, depending on the starting level.

To set up a static ip, right click the network applet in the panel, select 'Edit connections...', Wireless Tab, your network, and click Edit. I've attached an example of what it should look like, but don't copy my settings, as they are likely wrong for you. Just to make sure, there is no need to edit /etc/network/interfaces.

---

### Post by alohanate on 2011-01-09
mikewhatever, I definitely owe you a beer!  You are the man.  After having to undo a few things that other people told me to do, it worked like a charm.  I really appreciate your help, made my life a whole lot easier.  Thanks again man.


If you are setting up Vuze (or any other torrent program) use portforward.com.

---

### Post by Ocxic on 2011-01-09
you don't want to use port 6881 because it is the "standard/default" torrent port and most ISP's will block this port, and it is a dead give away that your torrenting.

use something higher like in the 10000+ range

---

### Post by Dwnshft on 2011-01-17
I can't seem to get my Vuze working. I've checked the TCP/UDP setting and I have it set to 49151 and have tried others too...but anytime I try a search it just blinks. 

Anyone know how to set this up or if there is a better app for torrent downloading?

---

### Post by Ocxic on 2011-01-18
don't search for torrents in vuse, thats not what it's for,,, you need to get your torrents from torrent sites.

---

### Post by Dwnshft on 2011-01-24
Sorry, you obviously misunderstood. Vuze is a search engine that seeks out files listed in torrent sites. All i meant was an application like Vuze that will allow me to search for media/applications in the same fashion. 

At any rate, can anyone help with a really dumbed down step by step of how to install via the terminal? I've tried to google stuff, but always seems like the commands i try to use aren't working...even the simple stuff like cd. lol

---

### Post by Ocxic on 2011-01-24
download the vuze tar.gz for your system, then:

"sudo tar xvf /path/to/tar.gz -C /opt/ && chown -R your_username:root /opt/vuze"

then add a menu item in to launch "/opt/vuze/azureus" and you can find the icon in the same folder.

*NOTE: Make sure you download the right architecture for you computer, if your running 64-BIT(x86-64) then the 32-bit(i386/x86) vuze download WILL NOT WORK, and visa-versa

---

