---
title: "network disconect..."
date: 2009-04-06
forum: New to Ubuntu
---

### Post by mustard greens on 2009-04-06
when I turned on my computer today, 1+ year running ubuntu, wired network failed to connect.  I have not changed anything.  checked all connections and had ISP do a health check on my modem, all good.  I finally reconnected to the web by creating a new wired connection, but cannot get it to access my printer (via ethernet).  I understand very little about networking, but managed to create a new connection.  I feel this has to do with the network manager, but cannot understand what caused the breakdown.  thanks for any help.

---

### Post by mustard greens on 2009-04-07
today, without any actions on my end, ubuntu reverted to the eth0 connection and is working perfectly.  any ideas what caused this?  seems like a glitch.

---

### Post by superprash2003 on 2009-04-07
your ubuntu machine wouldnt have received an ip address.. usually restarting networking in ubuntu or using the dhclient command would help

---

### Post by mustard greens on 2009-04-07
not sure what you mean about receiving an IP address.  I restarted the computer multiple times to no effect.  checking/unchecking the enable networking box did nothing.  ultimately I created a new connection which worked for my internet access, but not to connect to my printer server via ethernet.  today my computer switched back to auto eth0 when I restarted for new updates, but still is not connecting to my printer server.  my IP address is the same as it has been (same as the settings on my printer).  I have no router, but I do have a ethernet port switch box (almost a router but no IP).  dont need my printer imediately, but it would be nice to have it work when I do.

---

### Post by carml on 2009-04-07
An IP is like your postal address,you need one to be reachable on the net.:)

---

### Post by mustard greens on 2009-04-07
I understand what an IP address is, I just dont understand why the previous person referenced my receiving an IP in his post, or what he means by that.

---

### Post by nandemonai on 2009-04-07
> **mustard greens said:**
> I understand what an IP address is, I just dont understand why the previous person referenced my receiving an IP in his post, or what he means by that.

They were assuming you were using DHCP and not a static IP. If you are using static IPs then ensure you're not using the same IP for two devices. Other than that I'm not too sure.

Tried restarting the Printer I assume?

---

### Post by mustard greens on 2009-04-07
I am using DHCP, though I only barely understand that it helps maintain my connection while IP addresses come and go.  is that correct?  I havent ever changed the IP for the printer.  but none of this explains why I lost connection one day just by restarting the computer, or, why it came back the next, and why my printer now cant find the computer.  the printer has the correct IP, and computer password, and all the hard connections have been checked.  the modem and port switch box have both been restarted as has the printer.  I admit that I dont understand the finer points of my network, but random up and down seems to be a bug.  can anyone enlighten the situation.

---

### Post by Mike'sHardLinux on 2009-04-07
Hi!

I see two ways to answer your question. One would involve giving you a crash course in networking basics. The other would be just to agree, that, yes, it was basically just a glitch. The latter is most likely true in any case, even if the problem persists.

Networking issues can be caused by all sorts of things. If you learn about networking, you may learn about layered models, ie., the OSI model and the TCP model. The basic idea is that, in networks, there are many things happening simultaneously, at different "layers". There's data(bits) flowing on the media(cable), which is at the OSI Physical layer. There's also data (packets) flowing at the network layer traveling through the Internet between you and the destination URL (OSI Network layer). There's also stuff happening at other layers, all at the same time.

The reason I mentioned all that is because the issue could be related to something at many of those levels. Possibly, you may have a damaged or loosely connected cable causing an intermittent connection, and therefore, you wouldn't get an IP address from the DHCP server, or even be able to connect to the network at all. If there's an issue with the DHCP server, you may not get an IP address at all, or more likely, you would have an APIPA address, but then your computer might be on a different [logical] network from your printer or other equipment, which would basically cause a routing issue, which would keep your equipment from being able to communicate with each other. You could also possibly have some defective hardware, that only has problems intermittently. Also, it could very well be some glitch that happened as your computer was booting up. 

We'd really need more information from you to pinpoint exactly what happened. For example, are all the "link" lights for all the connections lit up and showing activity?

Also, you say your printer can't find the computer (which sounds kind of weird. Why would the printer need to find the computer, it is generally the computer that needs to find the printer....) Then you say the IP address is correct in the printer. How do you know this? Do you mean, it "was" previously correct, and you are assuming it hasn't changed for some reason?........ 

Sorry to bore you, but you did kind of ask for it! (I actually left out a lot of info.) I hope I don't sound like I am scolding...I don't mean to be. :-)

---

### Post by mustard greens on 2009-04-07
that was very helpful, although it fits the basic understanding that I already have.  
to answer your questions, all link lights are lit and green, and although it very well could be the ether port or cabling it is all very new and likely ok.  when I was having the initial problem, the network manager would not even attempt connecting through eth0.  I would check/uncheck the disconnect/connect option, but never got the attempt graphic from the icon, it just remained disconnected.  as I reported above, when I created a new connection through the network manager I was instantly able to connect to the modem/internet, but not the printer.  now, regarding the printer issue.  my printer has its own server which my web browser finds via the servers IP address.  I have never changed this address as it seems out of my league, and unnecessary.  when the computer could not find the printers server, I attempted to scan a document from the printer to the computer, and the printer was unable to find the computer as well.  when I said the IP was correct on the printer, what I meant was that in the printer server settings, it has my computers correct IP, as well as my computers correct password in order to gain access to the folder I was attempting to scan to.  the folder also has correct read write privilages.  I dont know if any of this brings us closer to a resolution, but I felt I should explain.  by all means please let me know if there are more variables I should be listing in my posts, as I have only one+ year of experience with linux.  thank you for your time also.

---

### Post by Mike'sHardLinux on 2009-04-07
Ok. That's sorta answers a question or two. I didn't realize you were using an all-in-one printer, versus a plain old network printer. So, I am assuming the printer has a little screen where you can verify its network settings, and that is how you know they are correct....

As for the link lights on the ports, did you actually verify them at the time of the original problem?

The fact that you created a new "wired connection" in Network Manager makes me wonder if you have a new/different IP address than previously on your PC. If so, does the printer know this new IP address? I am not sure how the printer is setup, but I would think it might need to know the computers IP address to talk to it.....I've never connected a network all-in-one......

There are some basic commandline tools that are very helpful in this situation. See if you can ping the printer's IP address from your computer. Also, what is the current IP address of your PC? (ifconfig) 

Tell us what the network settings are for the printer, too, if you can. And, how is everything connected? Is your modem also a router, or do you have a separate router? OR, is your computer connected directly to the modem via USB.....then, how is your printer connected? 

OK, I just thought of something. I was just *assuming* your printer was connected to your computer with Ethernet (which is a BIG no-no in trouble-shooting). Is you printer connected to your computer with a USB connection? If so, Network Manager would have NOTHING to do with this problem on your printer. That would make it an issue with the printer driver, settings, or the printer itself....or maybe the USB port. 

I get the feeling that you are suspecting a bug with Ubuntu or Network Manager, which is entirely possible, but, you'd want to search for known bugs, but, even if this is a bug, it might not be known yet...??

I guess, ultimately, we may never know what originally caused the issue. Don't feel too bad, though, this is typical of LAN/WAN. :-)

---

### Post by mustard greens on 2009-04-07
yes I checked the lights at the moment of the problem.  I made the new wired connection using the exact same IP and MAC info copied and pasted from the eth0 connection.  my IP has not changed in several months and it was the first thing I verified when the problem arose.  no ping from the printer on request of ten plus packets.  the printer is connected via both USB 2.0 and an ethernet cable. I dont understand why, but the scanning requires ethernet while the print function USB 2.0.
so my CPU's single ether port connects to a port switch box, through which the modem and the printer make their connection.  it is niether a router nor a hub, but is basically a router without an IP.

---

