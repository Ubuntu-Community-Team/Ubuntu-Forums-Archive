---
title: "Network Mageger wont work after Suspend in 8.10"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by StageCraft on 2008-11-04
Here is the problem

After I suspend my desktop, the network manager says that it is disconnected, although it is not and I cant get it to re connect without restarting the system. I dont want to leave my computer on all the time but I also dont want to have to shut it off and turn it on 4 or 5 times a day. 

I've tried some things to restart the network manager, but I dont think I did it right (I used to do it to my wireless on my old laptop, but things may have changed since 7.04)

This problem didn't ever happen in 8.04 on the same desktop, so I dont think its a hardware problem

Any ideas?

---

### Post by mike310z on 2008-11-04
I am also hunting issues with ibex dissconnecting and one of my investigations is to see if the suspend is the issue. 

Also did you see this [http://ubuntuforums.org/showthread.php?t=970818](http://ubuntuforums.org/showthread.php?t=970818)  for me it may be related.

---

### Post by StageCraft on 2008-11-05
I'm not sure if its is related. I'm about to try something and I'll let you know if it works. I just turned off the system settings feature in the network manager. so here goes nothing...

---

### Post by StageCraft on 2008-11-05
Well that didn't work, lets see what else I can find.

---

### Post by StageCraft on 2008-11-07
are there any new eyes that can take a look at this, I've found nothing

---

### Post by askarliechew on 2008-11-09
I think I am chasing the same problem.  Clean install of 8.10 on same machine as have been using 8.04 (different hard drives so I can switch between them).  Hibernate works fine in both 8.10 and 8.04, Suspend didn't work in 8.04 and at first I thought it was working in 8.10 but the networking applet reports that the network was "disconnected".

Tried the following:
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart
sudo dhclient eth0

But none of the above works.  So far the only way to bring it back is to reboot.  After reboot it has reverted to DHCP settings too, despite my setting a fixed IP address.

I will carry on hibernating until I can fix this...

---

### Post by flyonthewall on 2008-11-12
Just wanted to post and tell you you're not alone. As much userfriendlyness as this new Network Manager has brought, it's also crippled the usage of my wlan. I've tried the same things mentioned in this thread, none of which have helped. Also there's the fact that I cannot currently connect to WPA encrypted networks, the manager just keeps on asking me for the password. 

However, looking at the webpage for the Network Manager, there's a statement saying that the manager doesn't doesn't yet support WPA encrypted networks and that they're trying to fix that asap. 

With the exception of this most unfortunate series of wlan-related problems, I've generally found 8.10 a posotive experience. It's sad that this thing makes the dist shoot itself in the foot in such a blatant manner.

---

### Post by StageCraft on 2008-11-13
I still have had no luck. Hybernate is a little slow on mine so I've just been turning my machine off and on, but I hope that there is some way of getting the it to work soon. just for referance, what computers are you two using? Ive got an HP desktop and I'm starting to wonder if its a problem with the netowrk addaptor and not the manager at all. I shall investigate further...

---

### Post by buixuanduong1983 on 2008-11-19
I have Acer 4920, install 8.10, everything work find except Network Manager: it cannot connect me to a wireless network. So I change to wicd (wicd.sourceforge.net) and I like it. I notice that if I suspend my laptop with the wireless button turn on (wireless light on) then when it wake up, wireless work fine. But if I suspend it with wireless button off then wireless not work at wake up. And another straing thing is, if it not work, I press it to "turn it on" (count the number of press: 1 turn on, 2 turn off, 3 turn on...) then I suspend, next time wake up wireless work again as it "invisible remember its button status".

---

### Post by hickop on 2008-12-25
hello, I'm having the same problem on my desktop computer (abit an-m2 board). Resuming from suspend makes network inactive. Even without network manager and network configured static in /etc/network/interfaces & /etc/resolv.conf 

Might be some module failing to suspend but I'm not enough experienced to tell actually.

---

### Post by aesis05401 on 2008-12-30
I am experiencing the same issue on a HP a6230n, Ubuntu 8.10 32 bit, clean install 1 week ago.  After hibernate or suspend the network manager indicates that the wired network is unplugged.

I originally thought the issue was related to a tunnel I had set up for a VBox Guest, and I stumbled on what appears to be an erratically reproducible result.

Unfortunately I have not been able to reproduce the result reliably, so maybe someone who knows more can tell me what might be happening.

To set up the VBox Guest tap/bridge I run:

tunctl -u <user> -t <tap>
brctl addbr <bridge>
ifconfig eth0 0.0.0.0 promisc
brctl addif <bridge> eth0
dhclient <bridge>
ifconfig <tap> <ip address> up
brctl addif <bridge> <tap>
chmod 666... etc..

After waking from hibernate and confirming that I could not communicate with the network from Ubuntu host install I did the above process in reverse while pinging out to see if I was getting anywhere.

Occasionally, the following steps will result in a return to connectivity.

ifconfig <tap> down
tunctl -d <tap>
dhclient <bridge>  

For some reason I have never been able to get eth0 to successfully obtain network credentials directly after resuming from hibernate, but running dhclient on the bridge occasionally works.

I have no idea why this might happen, if it is incidental behavior, or what.  Maybe someone with more know how can make something of it.

---

### Post by rwalk on 2009-01-30
This [workaround]("http://www.ubuntu.com/getubuntu/releasenotes/810#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver") from the 8.10 release notes worked for me.

---

### Post by lloydkuhnle on 2009-02-01
Hello
I am kind of new to UBUNTU, and there are certain things I just don't know how to do.
I have the same issue. Network disconnected after suspend. Reboot seems to be my only cure for it.

While researching this, I was led to the following:

To work around this issue, users can create a file /etc/pm/config.d/madwifi 

containing the single line:
 
SUSPEND_MODULES=ath_pci

I don't want to sound ignorant, but how do I create that file? Do I just type "/etc/pm/config.d/madwifi" into a terminal, followed by "SUSPEND_MODULES=ath_pci"

I have been a WINDOWS user up to now, and so far I'm enjoying the switch to UBUNTU.

Thanks for any help you can provide me with.

Lloyd

---

### Post by jimtristate on 2009-02-01
In trying to configure my Broadcom wireless connection (which now isn't working after an upgrade from 8.04) in ubuntu 8.10 I cannot get Network Manager to do anything.  Network Manager saves the changes but they are not used/implemented. Appears that something else is managing my adapter settings. My wired connection works and is using dhcp, although in Network Manager I have it set manually to a different ip address. Even after a reboot, ifconfig reports different settings than those saved in Network Manager.

Where are the settings kept, I'd rather just set them manually in the configuration files with a text editor for now.

I also seem to have a DNS problem, since I can ping  my local network via ip address with my wireless card (ethernet cable unplugged). So even though I thought the wireless weasn't working, it was sort-of. Seems the wireLESS adapter cant get beyond the gateway but the wired one can.

---

### Post by pumansky on 2009-03-25
I just upgraded to 8.10 on my Compaq Presario F700. 8.04 worked flawlessly for me. I had the same problem after the upgrade with my wireless network becoming useless after resuming from suspend.

This fixed it for me:

Open a **terminal** window

type: **sudo gedit**

then type your password

then insert this single line:  **SUSPEND_MODULES=ath_pci**

then hit SAVE. Name the file **madwifi** and save it to **/etc/pm/config.d**

Then try suspending, resuming and see if your problem isn't fixed.

Good luck!

---

### Post by Glitchd on 2009-03-30
So, what if this doesnt work?
My wireless still requires me to restart my computer.
help..
_GLiTchd:confused:

---

### Post by gastoncs on 2009-04-05
Yes! this soluction worked for me, I have a lenovo T60  :guitar:
Thanks

---

