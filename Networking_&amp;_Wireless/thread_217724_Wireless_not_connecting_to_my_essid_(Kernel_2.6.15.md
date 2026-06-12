---
title: "Wireless not connecting to my essid (Kernel 2.6.15-26)"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by Sak on 2006-07-17
Hey everyone,

I'm experiencing something of a strange problem.  Last night I decided to give this a try here... [http://www.ubuntuforums.org/showthread.php?t=194993](http://www.ubuntuforums.org/showthread.php?t=194993)

I kept running into X freezing up on me whenever I tried to do anything with 3D accel.  But I digress... anyway, during my adventure I got a new kernel and a myriad of other changes that I'm not really sure of, but everything works fine except for my wireless connection.  This morning when I tried to connect my laptop to a smb share on my Ubuntu box I made the discovery that my wireless connection on my Ubuntu machine was grabbing my neighbor's access point.  

A quick trip over here... [http://www.ubuntuforums.org/showthread.php?t=195259](http://www.ubuntuforums.org/showthread.php?t=195259) to rebuild the driver for my wirless USB adaptor.  My network uses WEP, so that an an older machine can still connect, so I skipped all the mumbo-jumbo about the WPA stuff.

Anyway, everything seems to be working fine in regards to the driver, yet for reasons beyond my comprehension the USB dongle won't pickup my network, and keeps defaulting to the neighbor's convieniently unsecured wireless access point.

My settings in under System -> Administration -> Networking for wlan0 are all correct.  The correct ESSID, key, etc.  Everything is verified under /etc/network/interfaces as well.  

I can do...
```
sudo iwconfig wlan0 essid 102010
```
...which sets the ESSID correctly, but still doesn't grab my access point.  

So I tried...
```
sudo iwconfig wlan0 ap 00:14:BF:0D:D7:B2
```
... but I get the following error...

Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Operation not supported.

Anyway, I'm stumped.  Is there something that I'm missing here?  It worked just fine before yesterday using the old 2.6.15-23 kernel and whatever else before the changes from the automatic Xgl and Compiz install script.  

Any suggestions or thoughts would be great.  =)

---

### Post by t0dzilla on 2006-07-17
hmmm... sure wish I could be of more help but, I'm running into very similar issues as well. I say this because I'm starting to think that it's more of a bug with wep than anything else - I too can connect to any unsecured ap, but   any wep encryption seems to be no go. It's weird because iwconfig looks all right, minus an ip addy... and the wlan applet shows full signal strength with my carrier. Wifi radar lets me connect, but the resulting ip is my loopback addy (127.0.0.1)

I've been following alot of posts, and seen many good suggestions, but still no love. BTW, I'm typing this right now over a wireless ap - unsecured - @ work. So I'm 100000% positive it's not a driver issue, and my g3 powerbook at home connects just fine with my ap using same key/wep settings, so I'm reasonably convinced it's not a router configuration issue.

I'll keep following this post (and others) in the hopes that someone more knowledgeable than me will give us the right prescription here. (xanax, maybe?) :)

---

### Post by Sak on 2006-07-18
I agree.  The driver seems to perform fine, and the access point is accessible.  It only seems to work just fine without any security at all - which is unacceptable to me.  The odd thing is that the entire configuration worked just fine with the WEP settings as I had them before the kernel change.

---

### Post by t0dzilla on 2006-07-18
hmmmm...
so maybe a downgrade in the kernel is necessary? 
perhaps a bug should be filed...
anyone else wanna weigh in here?

i've never filed a bug report before, but there's a first for everything, right?

---

### Post by Sak on 2006-07-18
Well, this morning I ended up playing around with this some more, and I'm even more confused than before...

After I booted up I had a notice that there were some updates to install.  Since they were updates to the 2.6.15-26 kernel and headers I figured I'd give it a try.  I then rebuilt the zd1211 driver from scratch using the newly installed kernel stuff.  

Still no go.  By default the wireless dongle still grabs my neighbor's unsecured network...

```

sak@demian:~$ sudo iwconfig wlan0
wlan0     802.11b/g NIC  ESSID:"Wirelessly"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:09:5B:EA:9C:FA
          Bit Rate:54 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=64/92  Signal level=20/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:126  Invalid misc:0   Missed beacon:0

```

However, I played around a bit and actually got this to change to what is supposed to be correct - at least mostly...

If I do...
```

sak@demian:~$ sudo iwconfig wlan0 key restricted xxxxxxxxxxxxxxxxxxxxxxxxxx

```

Then I get the following output...
```

sak@demian:~$ sudo iwconfig wlan0
wlan0     802.11b/g NIC  ESSID:"102010"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:BF:0D:D7:B3
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=68/92  Signal level=20/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:149  Invalid misc:0   Missed beacon:0

```

Just about everything here is correct.  The ESSID, the MAC address for the accesspoint, the frequency.  The only thing that isn't is that it still reports "Security mode: open"  Which, according to the 'iwconfig' man page shouldn't be the case since I told it 'restricted' and fed it the key.

What's even more strange is that when I run 'ifconfig' I'm still using the same ip address from my neighbor's DHCP server.  I verified this when I looked up the client DHCP table in my access point, and I'm not showing up in there.  

It doesn't matter if I bring the wlan0 interface down and up again either.  The 'iwconfig' output stays the same, and the ip address does also, and it's getting it from my neighbor still.  

Anyway, with my new discoveries and confusion aside, I'm a bit concerned about downgrading the kernel t0dzilla.  When I was running the previous kernel and video drivers that were installed by default my system would freeze up on me whenever I tried to do anything that required any 3D or OpenGL.  Now all the video works great, but the wireless is borked.  If I downgrade the kernel, in order to try and get wireless working again, would it just break the video again?  I'm afraid I don't know enough about this stuff to try switching kernels and such.  =P

---

### Post by ischg on 2006-07-20
I have a similar issue with a Broadcom chip. Starting from Hoary, I had it working with a secure connection at times, while unsecured wireless always worked (Hoary: WEP key ok with ndiswrapper; Breezy: no WEP key, still ndiswrapper).
On dapper, I originally got it to work with the new kernel module after fiddling with it for a while. I got it to work using the sequence (don't ask me why I have to kick out the kernel module and reload it - it just worked):
```
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx
sudo iwlist eth1 scan | grep ESSID
sudo iwconfig eth1 essid <myEssid> key <myKey>
sudo ifconfig eth1
```
where bcm43xx is the driver for the Broadcom and eth1 is the wireless device. I stopped investigating and was happy until a kernel-update came around (I think it was the step from 2.6.16-25 to 2.6.16-26). So I have a similar story for a different driver. However, I never had any trouble with the Atheros chip on my Desktop (works out of the box).

---

### Post by Sak on 2006-07-20
Thanks for your suggestions ischg.  I tried your tips this morning, but unfortunately met with no success.  You motivated me to noodle around with it a little more, however, and I was able to make another interesting discovery in the process.

For whatever reason, using iwconfig to force the ESSID and Key would work enough to give me the output above, but I was still getting an IP address from the Wirelessly network.  So this morning I tried something different.  I  brought up the wlan0 interface and let it do it's thing.  I then manually edited the /etc/network/interfaces file and removed the entry for wlan0.  When I launched System -> Administration -> Networking, the wlan0 interface showed up as "Not configured."  So I hit the properties button, filled in the fields with the appropriate information - i.e. selected my accesspoint, entered the Hex key and selected DHCP.  The entry was put back into /etc/network/interfaces properly, and miraculously I was connected to MY accesspoint!  

I monitored the progress from the status reports on my wireless accesspoint.  At first it showed up under the filtered clients MAC address listing, then after about five minutes the accesspoint finally coughed up an IP address, and the system then showed up under the DHCP clients table in the accesspoint as well.  

On my Ubuntu machine, everything looked good, but performed terribly.  In System -> Administration -> Networking the DNS servers from my ISP showed up under the DNS tab, yet I couldn't ping anything with a name.  Also, this all only lasted temporarily.  I could do 'ifconfig wlan0 down' and 'ifconfig wlan0 up' and it would still connect to my accesspoint, but when I rebooted the machine it would run back to my neighbor's Wirelessly accesspoint again.

---

### Post by oss_monkey on 2006-07-30
Fantastic thread, guys!

Call me lucky, but after configuring my Wireless-G card, I fiddled around with WiFi Radar and ended up disabling the connection.

What I did to resolve it (using the GUI), was to run System -> Networking and reconfigure the wlan0 device. I now have two profiles there: one "Wireless" and one "Wired", depending on the setup.

The two now work well interchangeably, depending on my location. Hope this helps.

---

### Post by Sak on 2006-07-30
Thanks for the suggestion oss_monkey!  I didn't even think of setting up two different locations.  However, I still get no joy on the wireless side.  

After I plugged my USB dongle back in I had to do 'ifconfig wlan0 up' to get it to show up in System -> Administration -> Networking again, but it showed up as "Unconfigured"  I created a new location called "Wireless" with wlan0 configured and eth0 disabled.  When I hit the "OK" button, the switch was mostly complete.  I say "mostly" because according to 'iwconfig' it was using the correct ESSID, but it still had no Access Point listed.  Also, according to 'ifconfig' there wasn't any IP address being given from DHCP.  

It seems that unless I give it explicit information via the 'iwconfig' commands I mentioned earlier it just nevers picks up the correct Access Point.  And even when I do feed it the explicit information, it only lasts as long as the current session.

I also discovered something interesting playing around with it this morning.  If I had the "Wireless" location enabled, and switched to the "Wired" location in the GUI, it would blow away the wlan0 configuration completely!  In otherwords, it wouldn't even show up in the GUI anymore for either location!

This whole adventure has taken a turn for the surreal.

---

