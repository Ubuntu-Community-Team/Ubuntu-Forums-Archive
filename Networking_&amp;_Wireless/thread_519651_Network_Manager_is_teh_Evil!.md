---
title: "Network Manager is teh Evil!"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Sean Babu on 2007-08-07
I’ve enjoyed the week of new vitality Ubuntu has given my old PC, but unless I can get this fixed quickly, I’m deleting its partition.

Network Manager simply will not leave my network settings alone. I access the internet over a LAN with a fixed IP address (described in more detail [here]("http://ubuntuforums.org/showthread.php?t=514848")). I have to configure all the settings manually (takes about 30 seconds in Windows). I eventually got it set where I wanted by editing the following files:

/etc/network/interfaces
/etc/iftab
/etc/resolv.conf
/etc/rc.local

The only problem is network manager feels it periodically has to go in all willy-nilly and change my settings, seemingly at random:

-It changes eth0 to eth1, thus making all my hacks moot (this especially happens after rebooting from Windows).
-It wipes out the hard-assigned MAC address to 00:00etc., when my ISP needs the original address. I have to spoof this manually using ifconfig.
-It periodically wipes out the DNS server I set in resolv.conf.

I can't kill ten minutes every time I start up tracking down the problem and fixing it. Is there any way I can simply and easily make the settings permanent so that Network Manager will leave them alone? I removed NM from the start-up session, didn’t fix the problem. I tried removing the package wholesale through synaptic, but then networking didn’t work at all.

Please help me find a quick and lasting solution. I want NM out but my network to work. A linky to a helpful thread or FAQ complete enough for a newbie would be sufficient if no one has much time to help.

Many thanks.

Sean

---

### Post by raijinsetsu on 2007-08-07
uhm... Disable the network manager?

---

### Post by Sean Babu on 2007-08-07
If I disable it through the sessions menu, it still seems to make changes to the settings.

If I remove it through synaptic, networking doesn't work at all. Beyond configuring the files referenced above, I don't know how to set up networking drivers in Linux.

If there is a third, more effective way of disabling it, I don't know it.

---

### Post by kevdog on 2007-08-07
Remove network manager and install wicd or wifi-radar perhaps?

---

### Post by noob12 on 2007-08-07
Hmm.  I think you're ascribing a bit too much evil to NetworkManager.  

It sounds like you're seeing two issues interacting.

The changing eth0 to eth1 are probably due to your mac address tweaks on the Windows side persisting across the non-power-down reboot and fooling udev.  Each time udev doesn't find a mapping there it is going to create a new name. Read the man page on iftab carefully.  You are likely to be better off using something more stable than the macaddr mapping in your case, eg. try bus driver and businfo in combination.

NetworkManager won't mess with anything mentioned in iface lines in /etc/network/interfaces.  The first issue is causing you to get new eth* mappings that aren't mentioned in your /etc/network/interfaces.  When that happens, NetworkManager assumes it should take control, and you may then see additional weirdness to resolv.conf if it starts dhclient for any of these.

Solve your udev problems and then mention each of your devices in /etc/network/interfaces iface lines and you should be good to go.

You shouldn't need to remove NetworkManager, but I haven't heard any reports that removing it causes /etc/init.d/networking to fail, and I don't see why it should.   You may not have purged conf files properly.

---

### Post by Sean Babu on 2007-08-07
> **noob12 said:**
> 
The changing eth0 to eth1 are probably due to your mac address tweaks on the Windows side persisting across the non-power-down reboot and fooling udev.  Each time udev doesn't find a mapping there it is going to create a new name. Read the man page on iftab carefully.  You are likely to be better off using something more stable than the macaddr mapping in your case, eg. try bus driver and businfo in combination.

NetworkManager won't mess with anything mentioned in iface lines in /etc/network/interfaces.  The first issue is causing you to get new eth* mappings that aren't mentioned in your /etc/network/interfaces.  When that happens, NetworkManager assumes it should take control, and you may then see additional weirdness to resolv.conf if it starts dhclient for any of these.

Solve your udev problems and then mention each of your devices in /etc/network/interfaces iface lines and you should be good to go.

Thanks. That sounds promising. Where can I get the needed information on iftab and the other items you mentioned? I'm very new to Linux, and my computer skills peaked about 15 years ago, so I'm not too up on network stuff.

---

### Post by noob12 on 2007-08-07
Sure, I think I can walk you through all this.  Start by posting these
```

sudo lshw -C network

cat /etc/iftab

```

I'll be stepping out but will be back online in about an hour

---

### Post by Sean Babu on 2007-08-07
> **noob12 said:**
> Sure, I think I can walk you through all this.  Start by posting these
```

sudo lshw -C network

cat /etc/iftab

```

I'll be stepping out but will be back online in about an hour

Thanks. It's the middle of the night here, and it will take me some time to repair the last mess up which I probably exacerbated by temporarily removing network manager. Actually, if you could give me a link to an iftab faq or thread that would probably help me along quite a ways. I think it is a case of mac address confusion and things not getting flushed from Windows. Frequent power interruptions and my UPS not quite catching hold fast enough means frequent warm boots.

IIRC I fix the mac address in rc.local through **ifconfig eth0 ether HWaddress** 11:22:33whateveritis. Perhaps a command elsewhere would work better; I don't know.

I won't be able to post more for almost a day, but any help you can give me or links to get me going in the right direction would be appreciated.

---

### Post by Sean Babu on 2007-08-07
I found [this page]("http://linux.die.net/man/5/iftab") that looks helpful. Any other suggestions? I can't practice too much tonight (rebooting Windows to test it takes far too long), but I would be able look up other suggested information tomorrow as the rest of the world sleeps.

---

### Post by noob12 on 2007-08-07
Yes.  You'll get the local version by typing **man iftab**;  that is what I meant by "Read the man page for iftab...".

I don't know of any iftab FAQ or thread.  You could search using google for iftab and udev.  I can help you step by step if and when you're able to interact, but I don't have a HOWTO I can provide.
I'll watch the thread for a couple of days.

---

### Post by Sean Babu on 2007-08-07
> **noob12 said:**
> Yes.  You'll get the local version by typing **man iftab**;  that is what I meant by "Read the man page for iftab...".

I don't know of any iftab FAQ or thread.  You could search using google for iftab and udev.  I can help you step by step if and when you're able to interact, but I don't have a HOWTO I can provide.
I'll watch the thread for a couple of days.

Well, I think I've got it working now. I used **iftab businfo** on eth0, and so far the settings have survived two warm boots from Windows. I'll bump the thread if I run into any more problems, but I think it will be o.k. now.

Thanks for all your help!

---

### Post by noob12 on 2007-08-08
OK.  If you have your udev/iftab issues fixed, make sure to list any interfaces that you don't want NetworkManager to start managing in your /etc/network/interfaces file.  **man interfaces** will teach you about that.

Let me know if you need help.

---

### Post by Sean Babu on 2007-08-08
> **noob12 said:**
> OK.  If you have your udev/iftab issues fixed, make sure to list any interfaces that you don't want NetworkManager to start managing in your /etc/network/interfaces file.  **man interfaces** will teach you about that.

Let me know if you need help.

Right. That I think I'm o.k. with:

```
# The loopback network interface
auto lo
iface lo inet loopback

#newly placed for eth0
iface eth0 inet static
address 10.2.23.2
netmask 255.0.0.0
gateway 10.0.11.1

auto eth0
```

Three warm boots from Windows so far and everything's holding. I think this is solved. The only odd thing is that the hard MAC address is not showing up (probably again from Windows) so I'm having to spoof it with ifconfig, but that I've got taken care of in rc.local.

Anything else I should look at? You've been a tremendous help. I appreciate it.

---

### Post by kevdog on 2007-08-08
Your spoofing your MAC address like the following:

```
sudo ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
```

Ive tried this before and it never seems to work for me!

---

### Post by Sean Babu on 2007-08-08
> **kevdog said:**
> Your spoofing your MAC address like the following:

```
sudo ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
```

Ive tried this before and it never seems to work for me!

This is what I do in **/etc/rc.local**:

```

#newly placed for eth0
ifconfig eth0 down hw ether my:ma:ca:dd:re:ss
sleep 1
ifconfig eth0 up
route add -net 0.0.0.0 gw 10.0.11.1 eth0

```

Which I picked up from some thread here. The **ifconfig hw** command doesn't seem to work if the device is up. The sleep is in there to give it a little time to set in.

The ironic thing is that I am actually spoofing my MAC address to my real MAC address. Something is (sometimes) setting it to 00:00etc. when Ubuntu starts up so I have to re-register it. (I had the same problem when I was trying out Puppy Linux). At this point in time I don't care why this is because everything is working fine now. Four warm reboots from Windows and no further problems, so i don't want to mess with anything.

---

### Post by Sean Babu on 2007-08-08
> **Sean Babu said:**
> This is what I do in **/etc/rc.local**:

```

#newly placed for eth0
ifconfig eth0 down hw ether my:ma:ca:dd:re:ss
sleep 1
ifconfig eth0 up
route add -net 0.0.0.0 gw 10.0.11.1 eth0

```


BTW the** route add** is something I do to get my gateway setting right. Why I have to do that I don't know, but it was necessary to get my connection working. It is probably unnecessary for normal situations, which mine is not.

---

### Post by MetalMusicAddict on 2007-08-08
I for one still completely uninstall NetworkManager. I use all static IPs and am always on the same network. Just gets in the way for me. 1st thing I get rid of.

---

### Post by Sean Babu on 2007-08-08
@MetalMusicAddict:

My main problem was actually that Windows was teh evil (YA RLY!), but I'm also interested in doing this at some point. (Not now. I'm supposed to be writing a thesis proposal!) Is there a howto or FAQ for how to manually set up a static IP without network manager? When I uninstalled it the network completely stopped working so I stuck it back in.

---

### Post by odin1965 on 2007-08-09
> **Sean Babu said:**
> @MetalMusicAddict:

My main problem was actually that Windows was teh evil (YA RLY!), but I'm also interested in doing this at some point. (Not now. I'm supposed to be writing a thesis proposal!) Is there a howto or FAQ for how to manually set up a static IP without network manager? When I uninstalled it the network completely stopped working so I stuck it back in.

Even without Network Manager, to should still be able to setup the network, with static IP or DHCP in Gnome. Go to System > Administration > Network. There you can edit the settings for each interface via GUI.

---

