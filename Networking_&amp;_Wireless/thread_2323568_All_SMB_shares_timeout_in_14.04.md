---
title: "All SMB shares timeout in 14.04"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2016-05-06
I found a really old (over 2 years) post concerning this, but I'd like to see if anyone else can help me.

I have a couple of Windows machines on my local LAN and the computer I am on now is dual-boot (Windows 7-64 and Ubuntu 14.04 (XUbuntu)). I started up the XUbuntu after a week of not using it and for some reason my SMB shares have met with timeouts. Normally, they can be seen immediately in my file manager when I open it.

When I booted up in the past, I always get the request for my password for "keyring". This time and subsequent reboots have NOT asked me for a password. Instead, I go directly to my desktop as if everything is normal.When I move to my Windows 7 machine(s), I can "see" all my shares on the Ubuntu machine just fine. I can read/write files to them at will. BUT, I cannot connect to a single one of my Windows shared directories on the Windows machines. I have made sure that the workgroup is correct in smb.conf, yet no connection is possible.

This has worked in the past for over 2 years, but has now suddenly stopped working. When I shut down my Ubuntu machine a week ago, it worked. Today, when starting up, it wouldn't work. Just today, I created a shared directory on the Ubuntu machine and Windows can see it, read/write into it just fine.

Can someone help?

Bill

---

### Post by WB0HYQ on 2016-05-06
After over 50 years in the IT business, it never fails to amaze me that sometimes extremely strange things happen in this field.

In the spirit of "one more try", I reviewed everything that had happened since the networking DID work. I hit on the replacement I had made a week ago of a small wireless access point in the basement to boost reception there. I thought nothing of it. Then I looked in a few Windows Event logs and saw that "browser" was having issues at retaining its hold on being "boss" of the network. This made me think a little. Being a tiny UNIX server, the wireless AP took over as "boss" when I had my main Windows computer down to replace a fan. When I rebooted the Windows machine, it never took over the task of being "boss".

So, I powered down the AP, rebooted the main computer, and then powered it back up.

Problem solved.

Since my computers tend to remain powered up and in-service 24/7/365 unless required to reboot or go down for maint, I never would have thought of the AP blocking my network up like that. But it did. I investigated and found that the AP had a firmware date of 2008, plus it was a hugely limited instance of UNIX, so it had no idea how to handle my LAN.

This whole thing has been written down in my "stuff you won't believe, but have to use to fix a problem" notebook.

I will mark this thread as SOLVED, and thanks to anyone who read it.

BIll

---

### Post by QIII on 2016-05-06
Thanks for the tale!

It never ceases to amaze me that after doing this computer thing since the 70s, that is just exactly the same sort of irritating trifle that bits me in the behind, too.

---

### Post by WB0HYQ on 2016-05-06
Over the last hour, I re-verified that this happens. I shut down my primary Windows computer and watched my network carefully. The AP sent out a few queries and then, apparently, assumed control of the LAN. When I turned to my Ubuntu machine and tried to access the Windows shares on my other computers, it began timing out again. But heres the even stranger part: I rebooted my second machine, a laptop running Windows 10, and IT took over as "boss". As soon as it did, I got a prompt on the Ubuntu machine for my "keyring" password again, and all the shares were again visible.

Even when I restarted my main machine, the Win 10 refused to relinquish it's hold on the LAN. I had to shut it down and restart to release. But, once I did, the main machine took over again.

That is what I'd call pretty bizarre behavior but, in a certain twisted way, it makes sense. You never know what evil lurks in the mind of computers.

Bill

---

### Post by WB0HYQ on 2016-05-06
Well, shoot. I spoke too soon. I was in the middle of transferring some files FROM my Ubuntu machine to my Windows 7 machine and the connect just died. Any attempts to reconnect meets with "the connection timed out". Gigolo will not connect, nor will Samba. A reboot (again) of the main computer failed to solve the problem. When I rebooted Ubuntu, I did NOT get the "unlock keyring" password dialog box. I went straight to my desktop without entering ANY password. I thought that wasn't possible.

Anyway, I'm back in fixit mode.

Bill

---

### Post by bab1 on 2016-05-07
> **WB0HYQ said:**
> ...In the spirit of "one more try", I reviewed everything that had happened since the networking DID work. I hit on the replacement I had made a week ago of a small wireless access point in the basement to boost reception there. I thought nothing of it. Then I looked in a few Windows Event logs and saw that "browser" was having issues at retaining its hold on being "boss" of the network. This made me think a little. Being a tiny UNIX server, the wireless AP took over as "boss" when I had my main Windows computer down to replace a fan. When I rebooted the Windows machine, it never took over the task of being "boss".

So, I powered down the AP, rebooted the main computer, and then powered it back up.

Problem solved.

Since my computers tend to remain powered up and in-service 24/7/365 unless required to reboot or go down for maint, I never would have thought of the AP blocking my network up like that. But it did. I investigated and found that the AP had a firmware date of 2008, plus it was a hugely limited instance of UNIX, so it had no idea how to handle my LAN.

This whole thing has been written down in my "stuff you won't believe, but have to use to fix a problem" notebook.

You "problem" is neither strange nor unusual.   This is a this is a normal occurrence when you shut down the Master Browser ("boss"in your terms) as you did.  

The Master Browser is a machine that is configured for SMB services (a server) and has won an election between all the other hosts on configured as SMB servers on a NetBIOS naming network.  The Master Browser holds the list of all the other SMB servers and clients as they are announced when they come on line or leave.  This list is assembled and maintained by matching the announced  NETBIOS NAMES their IP addresses.  It is a dynamic system, unlike DNS which is designed to match fixed IP addresses to hostnames.

When you shut down the current Master Browser an election is held.  This usually takes about 15 minutes or so to complete.  When this election is being held you will not be able to have access to NETBIOS naming services.  The Samba server is still available and the shares are still functional.  You just can't browse for the available shares.  You can always access the shares by explicitly using the IP address instead of the NETBIOS NAME (e.g. //<server ip addr>/share-name ).

Although there is nothing to taxing about running a host as a Master Browser, it must be a SMB server of some kind and configured correctly.  The caveat is that it should stay "up" for most of the time.  So a server that is as you say "in-service 24/7/365" is a good thing.  My Samba servers go off line every once in a while so I never know (or care) which of my Samba servers is currently the Master Browser.  Sometimes I see the "Cannot retrieve share list from server" error.  I'm aware that the share browsing will return shortly.  The NETBIOS naming service is pretty consistent as once a host wins the election it will stay the Master Browser until it goes off line and a new election is held.

[/QUOTE]Even when I restarted my main machine, the Win 10 refused to relinquish it's hold on the LAN. I had to shut it down and restart to release. But, once I did, the main machine took over again.[QUOTE]
The Windows 10 machine will do just as well as the Samba server.  There is no reason to force the election winner to your Samba server.   If you really feel the need to have the Samba server win all elections you can configure that.  You can check the man pages ```
man smb.conf
```
The pertinent section in the man page is this```
 os level (G)

           This integer value controls what level Samba advertises itself as for browse
           elections. The value of this parameter determines whether nmbd(8) has a chance of
           becoming a local master browser for the workgroup in the local broadcast area.

            Note: By default, Samba will win a local master browsing election over all Microsoft
           operating systems except a Windows NT 4.0/2000 Domain Controller. This means that a
           misconfigured Samba host can effectively isolate a subnet for browsing purposes. This
           parameter is largely auto-configured in the Samba-3 release series and it is seldom
           necessary to manually override the default setting. Please refer to the chapter on
           Network Browsing in the Samba-3 HOWTO document for further information regarding the
           use of this parameter.  [COLOR="#FF0000"]Note: The maximum value for this parameter is 255. If you use
           higher values, counting will start at 0!
[/COLOR]
           Default: os level = 20

           Example: os level = 65

```...I'm sure that if you turn off the SMB server in the AP you will  eliminate the AP from ever becoming the Master Browser.   If you really feel the need for the Samba server always win these elections then set the  os level to 100 or so in the [global] section of the smb.conf file for the Samba server.  


FYI the "tiny UNIX server, [for] the wireless AP" is almost certainly a Linux server.  Nobody pays UNIX royalties anymore when they can use Linux for almost nothing if they also comply with the Open Source Licensing.

---

### Post by WB0HYQ on 2016-05-07
I certainly thank you for the refresher in networking, Bab1. Although I already knew about master browser elections and such, I was not familiar with the part that SMB played (or COULD play) in the situation. I am still learning about Linux (and mis-named UNIX inside the AP). Ans, speaking of the AP, it is quite old (around 2007 or so). it is a Netgear WN-604 and quite primitive. The web access page allows changing the broadcast wireless ID, and applying primary and secondary DNS servers, and a DHCP server (which I have turned off). There is no method I can discover that will turn off the SMB server in the AP.

Instead, I have decided to remove the AP entirely and substitute the DSL broadband modem/router that AT&T left me when they upgraded my system to the uVerse server. It is still completely functional, just older than dirt. So old, in fact, that the AT&T tech handed it to me and said "here. I don't want it.". It has a good b/g/n wireless setup that surpasses the old AP. It just won't have an "outside" connection. It will connect to my LAN using one of the four Ethernet ports. I'll have to shut off the DHCP, too, as my uVerse modem/router already has it set up. Initially, I'll have to connect it outside the LAN so I can change its response IP from 192.168.1.254 to 192.168.1.253 or something to avoid conflict.

I have noted several threads involving strange occurrences on local networks when a Windows 10 computer joins. I haven't seen anything outlandish, but I only have one laptop running Win10 anyway. It isn't on all the time.

Thanks again.

Bill

---

