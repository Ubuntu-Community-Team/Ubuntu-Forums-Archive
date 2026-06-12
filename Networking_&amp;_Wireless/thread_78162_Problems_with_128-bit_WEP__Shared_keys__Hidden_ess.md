---
title: "Problems with 128-bit WEP / Shared keys / Hidden essid"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by ibanez88 on 2005-10-17
I'm running Kubuntu Breezy with 686 kernel on an Averatec 1050-EB1 with Intel Centrino / ipw2200 built-in wifi.  

At first I thought my problem was with changing access points from within Kwifi - but now I'm not so sure as I can't get a working connection even at home (which works great at 64 bit encryption, open key, broadcast ssid) if I change even one of the parameters on my router to 128 bit, shared key, or hidden ssid.

I can test the problem most readily on a DLink DI-524 router although I'm certain I've experienced the same problem on almost every other network that I've tried to gain access to.

When I create a new profile in Kwifi everything seems to go fine.  I set it up according to the details I get in iwlist eth0 scanning.  The command sees networks just fine and I plug in the essid, managed / master / etc, according to the output.  I enter the key in the appropriate field, check "string" if its a hex string, uncheck if ASCII.  Hit apply, then activate.  Great, I see green bars in the main Kwifi screen.

However, the IP field on that window says IP not available.  I'm not actually connected.  I can sudo ifdown eth0, sudo ifup eth0 to my heart's content, reboot (which actually causes the splash to break at "configuring network interfaces").. still no access.

I can't figure out what to do from there.  If I'm on a 64-bit network with broadcast essid and open key, I don't need to do anything else.  What additional steps am I missing for 128 bit / shared key / or hidden essid?

My /etc/network/interfaces is exactly as Kwifi created, it lists my home profile only but allows for mapping.

I'm not posting my ifconfig because I have a working (although weakly secured) setup right now.  If anyone wants me to post it a non-working ifconfig or otherwise please let me know. 

Thanks.

---

### Post by ibanez88 on 2005-10-18
...

---

### Post by wwwebster on 2005-10-19
[http://ipw2200.sourceforge.net/faq.php](http://ipw2200.sourceforge.net/faq.php)

---

### Post by ibanez88 on 2005-10-19
Thanks for your reply.  As far as I can tell the only entry in that FAQ that relates to my experience is the following:

1.7. Why am I unable to associate when WEP is enabled? 
The most common reason for this is that the security mode is set to restricted instead of open, since restricted mode means that the driver will only associate with APs that it can first do shared key authentication with. If the AP is not configured to require shared key authentication, association won't happen. 
Ensure that you are associating using the steps: 

% modprobe ipw2100
% iwconfig eth1 essid <essid>
% iwconfig eth1 key open <key>
% ifconfig eth1 up


I've tried this against the APs that I'm having trouble with, with no change in results.

---

### Post by coffeeggsbacon on 2005-10-24
I was having a similar problem, i made the key open and it auto detected that it was 128 bits. thanks for the help!


is it weird that the motto for unbuntu is coffee, and my nickname is related to a wholesome breakfast?

---

### Post by ibanez88 on 2005-10-24
Is that really a healthy breakfast?  lol

I should have posted (sorry) that I found a resolution to this problem.  I've posted it on other people's threads but not my own - the way I got hidden essids and128-bit WEP to work is by adding:

wireless-key restricted xxxxxxxxxxxxxx

to my interfaces file.  Please try that out, hope it works for you.

---

### Post by Ben_Miled on 2006-01-12
ibanez88,

I have just landed on your post and thanx to it I am one last step away from completing my installation: CPU scaling. 
Eventhough my wireless worked out of the box, it was running with only 64 bit encryption. Which meant switching the setings in the routrer when switching windows/ubuntu. It wasn't too bad, but now.... niiiiiice.

So, thank you for your post and many thanks to everyone else whom takes the time to post their solutions. Without them, there would be a sea of desperate people out there.

Config:
Gateway 6510GZ (M360 series) Centrino
Pentium M 1.6 GHz - 1GB Ram - 80GB HDD
Intel 855 Chipset - Intel 2200BG

Ben-

---

### Post by malaprohibita on 2006-01-25
[QUOTE=ibanez88]
wireless-key restricted xxxxxxxxxxxxxx

to my interfaces file.  Please try that out, hope it works for you.[/QUOTE]


So, ummm... where's that "interfaces" file?  I think it would be handy to have a reference to that (or a link to where that might be) here for other newbies.  :smile: 

Cheers!

---

### Post by malaprohibita on 2006-01-25
/etc/network/interfaces;)

---

### Post by cpoint on 2006-01-26
Hey all - I have read through this thread and done some due diligence on Google but I still can't get *my* connection to work with a shared key.

Ubuntu detects the wireless network and I can plug in the SSID but I get no IP and I think that's because Ubuntu expects the key to be an Open key.  It's not and I'm not in a position to change that.  The key is shared.

Does anyone know how I can get my system to recognize a shared key?

Thanks!

---

### Post by malaprohibita on 2006-02-16
Anyone willing to bite on this?  I thought I had it figured out, but my problem remains the same.  I think **cpoint** describes my problem to a "T", and it would be awesome if there were a fix for this.

---

### Post by Lambert on 2006-02-17
Each driver handles it a little differently. For example, with the madwifi driver you need to change the driver with a iwpriv ath0 authmode 2 command. As stated earlier in this thread, just adding restricted in the key line in the interface sets the ipw2200 driver to work with shared key.

so the question is what device/driver are you using?

---

