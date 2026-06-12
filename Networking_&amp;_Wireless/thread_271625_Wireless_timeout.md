---
title: "Wireless timeout?"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Cyclops_ on 2006-10-04
So, I just installed Ubuntu CE (Dapper 6.06) on a machine I previously has plain Dapper 6.06 on.  Everything, for the most part is working great...  I was able to get my wireless USB Microsoft MN710 hooked up and working right away with ndiswrapper and the correct drivers loaded off the internet (not a problem, many a great forum post on that, and I've learned to be a virtual pro at setting up the wireless).

Trick now is that for some reason, we can be on the computer for some time, browsing the internet, and POW! we lose connection.  This happens multiple times per day.

Not the router / modem / ISP.  We are actually running off my neighbors router (with his permission), and when this happens restarting the computer will *always* (as far as I'm aware) fix the problem.

Now, I do know that Ubuntu CE comes with tinyproxy, firehol, and dansguardian installed (and that's the way I want it), so I tried to restart those services.  No go.  I try ifdown wlan0, ifup wlan0.  Nope.  "Well, how about deactivating the wireless and activating again?"  -- getting colder.

I can't seem to figure out what is going on, but then, I am certainly no Linux networking Guru.  I don't even know where to start (other than writing this forum post).

Any help?  (I appreciate it in advance!)

---

### Post by x64Jimbo on 2006-10-05
Is there a newer or older version of the card's drivers that you can try?

---

### Post by Cyclops_ on 2006-10-05
Well, I'm not sure if there are.  I remember downloading a few that I found on the internet, and this was the only one that would work at all. (This was a while ago.)  And it was working fine with Dapper 6.06.  I can probably try some others.

Are there also some diagnostics I can run when it happens?  I tried a dmesg, but I didn't see anything worthy of note.

---

### Post by wieman01 on 2006-10-05
Just to say that I am facing the same issue with "ndiswrapper"... After an hour of browsing (sometimes less) the PC disconnects for a reason unkown to me. 

I am currently investigating the issue and it all seems to boil down to the router. The card is working fine, the Firewall is turned off, restarting wpa_supplicant does not help, either. Even worse than that is the fact that you have to reboot. Restarting the network ("sudo /etc/init.d/networking restart") is a no-go.

Here is what I am testing at the moment: There is a chance that this has to do with the router's transfer rate being different from the one of you wireless card (e.g. wireless G vs. B). So what I am making sure now is that the router & my PC's wireless card run on the same rate (both G). I will continue to test the system & let you know if I face any more disruptions.

---

### Post by Cyclops_ on 2006-10-05
Interesting note.  

Although, my "card" and the router have been harmoniously working for some time now... (a year?) But you might be on to something.

---

### Post by wieman01 on 2006-10-05
> **Cyclops_ said:**
> Interesting note.  

Although, my "card" and the router have been harmoniously working for some time now... (a year?) But you might be on to something.
I'll try to narrow it down. Ndiwrapper does not seem to fail, because I can still scan for networks, etc. I find no error messages whatsoever. 

One thought: Have you tried restarting your router (pulling the power cable) after the PC has disconnected? And do you use any kind of encryption/authentication by chance?

---

### Post by Cyclops_ on 2006-10-05
Well, the router is my neighbor's (or in other words, located in his apt).
Yes, there is WEP encryption.

---

### Post by wieman01 on 2006-10-05
> **Cyclops_ said:**
> Well, the router is my neighbor's (or in other words, located in his apt).
Yes, there is WEP encryption.
Ok, we'll keep each other in the loop then. :-) I kept asking if anybody's facing the same issue but until today, no reply. I'll do some more testing over the weekend. This is a real challenge after all.

---

### Post by Cyclops_ on 2006-10-05
sounds like a plan.  (wow, we are practically having an instant message :) )

I just wish I knew of some commands I could issue to test what's going on.

---

### Post by wieman01 on 2006-10-05
> **Cyclops_ said:**
> I just wish I knew of some commands I could issue to test what's going on.
Don't worry. It DOES help to know that there is somebody else out there facing the same problem. Two days ago - when I discovered the problem - I thought I was stupid. But apparently I am not on my own.

Talk to you soon... very soon. :-)

---

### Post by Cyclops_ on 2006-10-05
so are you running Dapper 6.06?

---

### Post by wieman01 on 2006-10-05
Yes, since it came out in June. My wireless card is a Linksys wusb54g v4 with "ndiswrapper". Router is Linksys too. I don't particularly like the brand but somehow got used to it. 

Did you have similar problems in Windows? Occasional timeouts/disruptions?

---

### Post by Cyclops_ on 2006-10-05
good question.  i have windows dual booted, but haven't used it since i reformatted...

---

### Post by wieman01 on 2006-10-05
Did some testing last night and here are some finding:

1. Turned off MAC filtering: No results.
2. Set router to braodcast on wireless G only (no mixed): No results.

We're getting there. One more favor I got to ask from you if you have time: Can you boot your computer, ping your router from a terminal window (ping 192.168.xxx.xxx) and leave it running for a few hours until you get disconnected? 

Just trying to understand if "ndiswrapper" has a problem with the "idle state". If "ping" runs for a few hours without losing the connection, then we're one step further. I'll try the same tonight.

---

### Post by Cyclops_ on 2006-10-05
Sure thing.

I also did a /etc/init.d/networking restart the last time this happened, and, like you, nothing.

I will do the pinging tonight and see what happens... that's a good idea.

---

### Post by Cyclops_ on 2006-10-05
OK... uh... I just started a ping, and then I stopped it to see if it was doing anything and I got the following (without the masked IP's of course):

ping 192.168.xxx.xxx -b
WARNING: pinging broadcast address
PING 192.168.xxx.xxx (192.168.xxx.xxx) 56(84) bytes of data.

--- 192.168.xxx.xxx ping statistics ---
67 packets transmitted, 0 received, 100% packet loss, time 66090ms

---

### Post by Cyclops_ on 2006-10-05
I can ping a friend's server from here, if that would work?

---

### Post by wieman01 on 2006-10-05
The server will be fine as well. No idea why you cannot reach the router. Any other computer on the network will do. This will tell the router that "we are still there". :-)

Perhaps it's best if you turned any kind of firewall off for now (if you have one enabled). Let's see tomorrow what's happened.

---

### Post by Cyclops_ on 2006-10-05
uh... well, my friend's server is not on the network.  is that ok?

i have firehol on, (isn't that the firewall?) so I'll go ahead and turn it off.

---

### Post by wieman01 on 2006-10-05
I don't really know Firehol... But sounds pretty much like a firewall.

Yes, any computer you can reach will be fine as long as you stay connected to your mate's/neighbor's network you have been referring to. You can also ping yahoo or google. We're simply pinging because we want to tell the router that we're not "idle" if you know what I mean.

---

### Post by Cyclops_ on 2006-10-06
I was kind of wondering this same thing (whether it had anything to do with being idle)... but it happened to me whilst browsing the internet, so I just kind of scratched that off the list.... but hey, 3 hrs later, the ping continues... we'll see what it looks like tomorrow... maybe I'll leave it running through the night, and then while I go to work.

---

### Post by wieman01 on 2006-10-06
> **Cyclops_ said:**
> I was kind of wondering this same thing (whether it had anything to do with being idle)... but it happened to me whilst browsing the internet, so I just kind of scratched that off the list.... but hey, 3 hrs later, the ping continues... we'll see what it looks like tomorrow... maybe I'll leave it running through the night, and then while I go to work.
Yes... Leave it running for a few hours or a day. Will do so over the weekend. I have the slight feeling that this will work. Not sure why though... If there is no timeout whatsoever, I am pretty sure this will lead us to the router.

---

### Post by Cyclops_ on 2006-10-06
OK, got up this morning and took a look at it, and sure enough, it had disconnected me somewhere in the night between 1:30 am and 8:30 am.

Arg.

---

### Post by wieman01 on 2006-10-07
Interesting... Have been pinging my router & Google for 12 hours and I am still connected. This is what I did:

I have got a Linksys WRT54G router and I set the "beacon interval" to 10 milliseconds (default = 100). Apparently that did the trick. I will continue to test the settings and get back to you tomorrow.

*"The Beacon Interval value indicates the frequency interval of the beacon. A beacon is a packet broadcast by the Router to synchronize the wireless network."*

The problem is that you won't have access to your neighbor's router I reckon, however, I am sure you can ask him to change the settings for you.

---

### Post by wieman01 on 2006-10-07
Mmm... This seems to have resolved my timeout problem (still on line with not disconnection so far). I will shut down the computer for tonight & continue tomorrow. In the meantime you could have a chat with your friend who owns the router...

_**[COLOR="Red"]EDIT 1:[/COLOR]**_
Computer has been running well for another 4 hours without any sort of disruption. Strange thing but the **[COLOR="Red"]"beacon interval"[/COLOR]** seems to have worked. Check out the snapshot for the settings. Perhaps your buddy let's you configure his router accordingly.

BTW: I now remember that I used to have the same problem in Windows... Occasional timeouts, etc. Apparently Windows handles this kind of stuff much better than Linux because I never had to restart the PC (that's why I did not really pay attention or wouldn't do anything about it). 

Check it out & let me know how it goes!

_**[COLOR="Red"]EDIT 2:[/COLOR]**_
Has been running stably for 9 hours now. I think I may have tracked it down. Let's see what we can do about your stuff.

_**[COLOR="Red"]EDIT 3:[/COLOR]**_
Has been 12 hours now... Considering the problem solved on my side of the fence.

_**[COLOR="Red"]EDIT 4:[/COLOR]**_
The connection is definitely fine now. Suggest you to try the same thing.

---

### Post by da_maestro on 2006-10-08
Where is the beacon interval setting?

Is it on the router or on the system? My router doesn't seem to have this setting :(

---

### Post by wieman01 on 2006-10-08
> **da_maestro said:**
> Where is the beacon interval setting?

Is it on the router or on the system? My router doesn't seem to have this setting :(
It's a router settings. I am pretty sure you'll find it when you check all the possible settings & switches. It may have a different name though.

---

### Post by da_maestro on 2006-10-08
I think my problem is different to yours.

Mine disconnects regardless of activity, and it doesn't affect any windows machines. Also, the problem is getting worse now. It now disconnects after just a few minutes of being inactive. I've tried swapping the drivers around for the latest ones and even tried swapping out the winxp drivers and put in win2k ones.

Also now, when the system is on the network it refuses to accept SMB connections, even though it accepted them before. I might have a samba issue, but I don't see how samba is supposed to force my router to disconnect my system from the network. It just doesn't make any sense...

Alas nothing seems to work. While I'm here, can anyone tell me how to add the eth0 device back to the interfaces file?

Edit: I just realised that it doesn't accept any connections at all when it's "on the network". So that rules out Samba.

---

### Post by wieman01 on 2006-10-08
You may have a problem with your firewall. Still I suggest it's something to do with the router because this sounds familiar. However, if you believe it's something else, please open up a new thread so that we don't confuse things here. :-)

---

### Post by da_maestro on 2006-10-09
nah it's not a firewall problem. I don't think I installed one, unless that is of course that Ubuntu installs one by default and I didn't catch that...

As far as I can tell my card is not re-establishing the signal when it goes out of range of the wireless hub. I don't know how to fix this.

---

### Post by Cyclops_ on 2006-10-09
Oh... sorry I have been busy for a while.  Yeah, I will see if I can find that setting on the router.

---

### Post by wieman01 on 2006-10-10
Just to reconfirm: After changing the "beacon interval" from 100 to 10 I have not had a single timeout issue so far. As far as I am concerned the problem has been resolved. Hope you (Cyclops_) can confirm that as well.

---

### Post by ashram on 2006-10-13
My MoBo is m2n32 with WiFi RTL8187 chip.

Linux drivers didn't worked, so I moved to ndiswrapper and blacklisted r8187 module. Windows XP drivers gave me "linking with" problem.
The only driver that the solved problem was win98 original driver.

The only problem that it disconnecting all the time and the only sollution is reboot...

I have changed beacon interval from 100 to 10 but there is still problem with disconnectings.

Any recommendation are welcome

---

### Post by wieman01 on 2006-10-13
> **ashram said:**
> My MoBo is m2n32 with WiFi RTL8187 chip.

Linux drivers didn't worked, so I moved to ndiswrapper and blacklisted r8187 module. Windows XP drivers gave me "linking with" problem.
The only driver that the solved problem was win98 original driver.

The only problem that it disconnecting all the time and the only sollution is reboot...

I have changed beacon interval from 100 to 10 but there is still problem with disconnectings.

Any recommendation are welcome
Could you try to get the latest driver from the vendor's webpage? I would not recommend to use the Win98 driver, that's a moving target, really. If the new driver has the same issues, then we continue from there.

That's off-topic but when you deployed the "latest" driver did you have all driver files (e.g. *.CAB, *.INF, etc.) in one & the same directory? "ndiswrapper" sometimes fails to deploy driver (namely the *.INF file) if it cannot find the remaining driver files in the same folder...

---

### Post by ashram on 2006-10-14
The only drivers that ever worked were win98 and win me. Windows XP drivers didn't worked.
I tried it again but no luck.
When I installed new drivers, it could be found in directory:
/etc/ndiswrapper/netrtuw - .inf and .sys are there
I am using last drivers from realtek ftp: 8187 (1221) (0412)

Thanks,

---

### Post by wieman01 on 2006-10-14
Are there any other driver files next to *.INF and *.SYS. The reason why I am insisting is that I cannot image that the Win98 drivers would work & the Win XP would not. "ndiswrapper" should be able to deploy any wireless driver, no matter what because it sort of "emulates" a Windows environment that ALL windows driver comply with. Otherwise they would not work in Windows, either.

So are there any other files that you may have missed out?

---

### Post by ashram on 2006-10-15
I actually have:
ls -la /etc/ndiswrapper/netrtuw/
total 216
drwxr-xr-x 2 root root   4096 2006-10-08 22:03 .
drwxr-xr-x 3 root root   4096 2006-10-08 22:03 ..
-rw-r--r-- 1 root root    448 2006-10-08 22:03 0846:6A00.F.conf
-rw-r--r-- 1 root root    448 2006-10-08 22:03 0B05:171D.F.conf
-rw-r--r-- 1 root root    448 2006-10-08 22:03 0BDA:8187.F.conf
-rw-r--r-- 1 root root  10173 2006-10-08 22:03 netrtuw.inf
-rw-r--r-- 1 root root 182622 2006-10-08 22:03 rtl8187.sys

When I tried XP drivers it just didn't get IP address from wireless router and WIN98 drivers worked right after installation.

The fact that rtl8187 chip would work with WIN98 drivers under ndiswrapper I got from:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by wieman01 on 2006-10-15
> **ashram said:**
> I actually have:
ls -la /etc/ndiswrapper/netrtuw/
total 216
drwxr-xr-x 2 root root   4096 2006-10-08 22:03 .
drwxr-xr-x 3 root root   4096 2006-10-08 22:03 ..
-rw-r--r-- 1 root root    448 2006-10-08 22:03 0846:6A00.F.conf
-rw-r--r-- 1 root root    448 2006-10-08 22:03 0B05:171D.F.conf
-rw-r--r-- 1 root root    448 2006-10-08 22:03 0BDA:8187.F.conf
-rw-r--r-- 1 root root  10173 2006-10-08 22:03 netrtuw.inf
-rw-r--r-- 1 root root 182622 2006-10-08 22:03 rtl8187.sys

When I tried XP drivers it just didn't get IP address from wireless router and WIN98 drivers worked right after installation.

The fact that rtl8187 chip would work with WIN98 drivers under ndiswrapper I got from:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
That odd... But ok, if that's the case I am not sure what we can do about your disconnection problem. All I can suggest is that you play around with your router settings and test the system afterwards... :-(

---

### Post by ashram on 2006-10-15
It's odd, but now it's not disconnecting... I even affraid to reboot ;) 

The only change that I could think about is that I conected my desktop with cable to another router with DHCP during boot... 

Could it be that network connection have idle timeout only when it is wireless and when it connected with wired the timeout is disabled?  ](*,) 

By the way... is there way to unplug USB device (on OS level) and rescan USB bus  since my USB wireless is onboard?

Anyway thanks for help :)

---

### Post by wieman01 on 2006-10-15
The timeout certainly occurs when you are connected "wirelessly". It's a problem that particularly relates to wireless networks as far as this thread is concerned. I have never had issues when using cable/ethernet, so it is not surprising that your cable connection is stable as opposed to the wireless connection. 

As for the second question, you can configure "hot-plugin" through "/etc/network/interfaces". Cannot remember the exact stanza but you should have no problem finding it.

---

### Post by ashram on 2006-10-27
I gave up... :(

Just bought Access point and using it as bridge so now I have wireless over eth0 (wired).

Anyway it's better than buy M$

---

### Post by Cyclops_ on 2006-10-28
Boy, if you're still watching this thread, I am having problems like nothing else.  Time outs every couple minutes, especially when doing something that consumes a little more bandwidth than page refreshes...

I don't remember if I stated, but I did change that Beacon setting.  No go.  The only thing that did was kick me out from being able to access the router.

Maybe I will take your suggestions and try a different driver, though I could have sworn I've been using this one up til now with no problems.

We'll see if that does any good.

---

### Post by wieman01 on 2006-10-28
Is there a chance that your wireless network interferes other networks around your apartment? Please do a scan (while not connected to your router) & post the results. It is possible that other networks run on the same channel/frequency as yours.

Plus... Can you list all the wireless settings that your router offers?

Last thing: Are both router & wireless adapter set to either B or G? I would not enable dual broadcast (B/G).

---

### Post by Cyclops_ on 2006-10-28
Yes, the router is set to B/G.  The neighbor has different devices that use the two types.

How do I do the scan?

And what Settings would you like to know.  I think there a plethora of them...

---

### Post by wieman01 on 2006-10-28
Scanning:
> iwlist scan
Can you enable either B or G and not mixed mode? Perhaps that's your issue. 

I enclosed an image of my router settings. Those are the ones I am referring to. But let's see first if there is any other network around your place that may interfere with your network by running on the same channel for instance.

---

### Post by grim4593 on 2006-10-29
Since I upgraded to edgy I have had some similar problems with timeouts and lag during inactivity. I "fixed" it by running
```
ping -i 5 192.168.0.1
```
everytime I log in. I'll try that beacon interval thing and see how that works. 

Note: I did not have to do any of this in dapper.

---

### Post by Nakkis on 2006-10-29
I've been having similar dropout problems too in Edgy (although I can't speak for earlier versions, since Edgy is my first introduction to Ubuntu). Wireless connection works fantastically in Windows, but drops the connection after few hours of work in Linux. Only reboot helps. 

I didn't install any drivers since I could get the wireless connection to work out-of-the-box. Inactivity doesn't seem to be the problem since it has dropped while countinuous downloading many times. 

Any ideas? I have a Buffalo WLI-U2-KG54 USB WLAN adapter.

---

### Post by ashram on 2006-10-29
For me "ping -i" didn't helped... 
I saw "destination host unreachable" after some time.

Mine now working with bridge...

---

### Post by wieman01 on 2006-10-29
Generally I suspect that our problems relate to the hardware (i.e. router) rather than anything else. Interferences with other wireless networks can play a role (in that case changing the wireless channel may be the solution), router settings can be inappropriate, or a closed door disrupts the wireless signal.

I don't think this relates to much to Ubuntu, but if people are saying that wireless networking worked fine in previous versions, this could be the case after all. Personally I don't think so.

Have you guys tried using the latest drivers available for your cards?

---

### Post by grim4593 on 2006-10-29
When i say "ping -i 5 192.168.0.1"  I am pinging my router every 5 seconds.  You might wanna ping your own computer or an outside internet server.

---

### Post by Nakkis on 2006-10-30
Disabling EHCI seems to have solved my dropout problems with the WLI-U2-KG54. There have been some reports on [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) regarding problems with ECHI USB 2.0 driver. 

Try:

sudo modprobe -r ehci_hcd
wconfig rausb0 rate 11M

The downside with this is that USB will operate on 1.1 speed. :neutral:

---

### Post by wieman01 on 2006-10-30
> **Nakkis said:**
> The downside with this is that USB will operate on 1.1 speed. :neutral:
Yeah... I don't think this will be an option then...

---

### Post by wieman01 on 2006-10-30
Those still following this thread... Try to switch channels. Perhaps there is some kind of interference with other networks around you. Use a channel that is not used by any other networks in the neighborhood. This did the trick for another guy.

---

### Post by ashram on 2006-10-30
Tried switching channels... no luck

Reducing USB from 2.0 could be pain

I hope that in short future ;) someone will write native linux drivers that would support this hardware or some generic linux driver for all wireless cards LOL

---

### Post by Comedy Dave on 2007-02-16
I think i may have a situation which may shed some light on this

A few months ago I used 6.10 edgy for a couple of weeks.
During this time I suffered the dropoff problem (Linksys WUSB54G v4 connecting to a BTHomeHub) and during the same period it would knock my housemates pc off the network and he was running XP and a belkin usb adaptor. (and windows being windows he would actually have to disable the adaptor and re-enable it to get it to reconnect)

Then I went back to XP and the problems stopped, no dropoffs at all.
Recently I have gone back to Edgy and the problem has reappeared.

May I also point out that in Edgy, the Linksys runs straight from install. No need for ndiswrapper.

---

