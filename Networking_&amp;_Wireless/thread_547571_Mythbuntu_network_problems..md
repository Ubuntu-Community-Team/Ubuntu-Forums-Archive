---
title: "Mythbuntu network problems."
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by bag123 on 2007-09-10
Dear all,

Forgive me if this is covered somewhere - but I've had a quick trawl and can't find anythign that would cover it...

I'm trying to install Mythbuntu.  I need to get the system to have internet access so that I can download updates and install nvidia drivers for TV-out access.  But I have a couple of problems...

1.  The motherboard that I'm using doesn't seem to have the ethernet port working.
2.  The wireless card requires ndiswrapper (I've had it working before so I know it CAN work).

Mythbuntu doesn't seem to come with ndiswrapper so I've got a bit stuck.

I've now got to get ndiswrapper installed so that I can get the wireless driver up and running.  Once that is done, I can get on with the rest myself...

So, I've downloaded ndiswrapper and the relevant driver for the wireless card.  But running make on ndiswrapper hits an error - claiming that it can't determine a build file?  Needs a path to it...

This is where I need help.  If I can correctly specify the build file - I hope that I can get ndiswrapper installed, and then get the wireless card up and running.

Your help would be appreciated.

Thanks,

Bag123.

P.S.  As an aside, could we look at getting ndiswrapper onto the Mythbuntu install disc?  Or if it's there already - how do I get it installed?  It certainly doesn't seem to be there at the moment...

---

### Post by bag123 on 2007-09-11
Bump.

Just to clarify - I am able to download information/files to a Windows machine and then mount the USB stick and copy data across to my standalone Mythbuntu installation which has no current internet connection.

To get internet I need to install ndiswrapper.

however, at this page:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

it says that I need to apt-get update, followed by an apt-get install build-essential plus an apt-get linux-headers... before trying to install ndiswrapper.  How important is this?
 
I am obviously going to struggle to do this without a working internet connection.  Any ideas on how to  either bypass this requirement, cheat on it, or to actually do it by transferring data from a Windows machine?

And I presume that this is why the path to the build file is missing...

I'd be grateful for any other ideas...

Thanks,

Mark.

---

### Post by bag123 on 2007-09-12
Still confused...  and not really advancing on this.

Trying to get Mythbuntu up and running without a working ethernet port - and by getting my wireless card installed through ndiswrapper.

Can anyone tell me if this can be done - or how I should go about it?

Thanks,

bag123

---

### Post by WhyWontThisWork on 2007-12-30
have you heard anything from this? im trying the same thing. I had it working in the last big ubuntu without having to go through the command line riggmaroll with ndiswarpper as I spend a long time trying to get that to work, the normal ubuntu has the support built in, was this support taken out, and if it was what sense does that make?

---

### Post by WhyWontThisWork on 2008-01-12
download the files onto a USB that the apt would have gotten

---

