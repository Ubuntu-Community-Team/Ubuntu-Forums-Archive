---
title: "Wireless issues; would like advice on installed driver"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by dissembly on 2010-08-01
Hi all,

I am at the end of a long day trying to get my wireless card to work. I've just (successfully) completed this tutorial:

[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

After being directed there from here:

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172]("https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172")

However, my NetworkManager Applet does not detect any wireless network (despite being right next to another computer (the one i am using right now) that is doing fine, and despite being only a couple of metres away from the wireless router.

However, my wireless card is 8172.

I have noticed that the tutorial linked above uses a driver called "8192", and there is another card called 8192.

But the Ubuntu community page for 8172 links you to the driver for 8192. I search on the Realtek website, and cannot find either driver, so as far as i can see, the only link i have is to 8192.

Does this matter?

I assumed that since it is linked on the 8172 page, the 8192 driver will work.

But my wireless card doesn't detect any networks (it should be detecting a handful of them - i'm in an apartment building and all my neighbours seem to have wireless too).

Do i need to uninstall the driver that i just installed, in order to install the 8172 (rather than 8192) driver?

How do i do that?

And, how do i find the 8172 driver? The only links i have, on the 8172 page, are to the 8192 driver. And the RealTek website claims it doesn't know what "8172" means: [http://www.realtek.com/downloads/searchView.aspx?keyword=8172](http://www.realtek.com/downloads/searchView.aspx?keyword=8172)

-------------------------------------------------
Edited to add:

These are the outputs from the commands "lspci", "lshw -C network", "ifconfig" and "iwconfig", in case it is important:

**lspci**:

> 

05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)**lshw -C network**:

> WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 10
       serial: 1c:4b:d6:30:cb:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=V 1.1 firmware=49 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:09:00.5
       logical name: eth0
       version: 02
       serial: 00:90:f5:9a:e5:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=jme driverversion=1.0.4 latency=0 multicast=yes
       resources: irq:28 memory:f0200000-f0203fff ioport:3400(size=128) ioport:3000(size=256)**ifconfig**:

> eth0      Link encap:Ethernet  HWaddr 00:90:f5:9a:e5:4d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:30:cb:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f8e38000-f8e38100 **iwconfig**:

> lo        no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.Ah geez. I don't know what to do with those smilies. I'm sorry. Hopefully they're not obscuring anything important. I'm so very tired and cold, and have been doing this all day long. Will go have dinner and then be back to see if any replies. :(

---

### Post by dissembly on 2010-08-01
I thought i should put the output for the "**lsmod**" command as well, as i gather that can give you an idea what driver is operating:
> 
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52544  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
psmouse                56180  0 
serio_raw               5280  0 
**jme                    30460  0 **
mii                     5212  1 jme
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
dm_crypt               12928  0 
**r8192se_pci           417140  0 **
jmb38x_ms               9600  0 
memstick               10072  1 jmb38x_ms
lp                      8964  0 
parport                35340  2 ppdev,lp
led_class               4096  1 sdhci
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 videoI can see "r8192se_pci" in that list, which is the driver i installed earlier today - i've bolded it, and i've also bolded "jme" - which i think is for the ethernet. (I'm sorry i'm not used to how posts work here yet - for some reason the forum has collapsed all the spaces into single spaces, making it hard to read.)

Could they be stopping each other from working? Or is this just wishful thinking, hoping for a simple solution...

---

### Post by k3lt01 on 2010-08-01
If you are using 10.04 (Lucid) you should have wireless if you update to the newer kernels (that's what it says in the Community help page anyway). You don't actually tell us what version you are using so we can't help you much until you do unfortunately.

Anyway its my bed time. I'll check this thread in the morning to see how you've gone and offer any help if you still need it.

---

### Post by dissembly on 2010-08-01
I am using 9.10 "Karmic Koala". (just added it to my user profile then)

I have seen a few different help pages about it, and they seem to say that my wireless card is generally unsupported on the latest versions of Ubuntu, and that I need to download a driver from elsewhere.

I'm not sure how to upgrade to 10.04; i don't have wireless, and when i connected an ethernet cable to it a few hours back, it produced an error message that i can't bring to memory at the moment. (The community help page says you can upgrade from a CD, but i have no CD drive on my Ubuntu machine (it's a 10" mini laptop).)

---

### Post by GaryTheCat on 2010-08-01
I had the same problem and can't for the life of me figure out how I got past it - not very helpful but there is a solution ;)

---

### Post by dissembly on 2010-08-01
Ha! Well, at least there's hope :)

I've found this old thread:

[http://ubuntuforums.org/showthread.php?t=1353049](http://ubuntuforums.org/showthread.php?t=1353049)

I've noticed three things:

1) dash86no posted this sequence of steps:

> 1: Download the latest driver from Realtek's site:
[http://www.realtek.com/downloads/dow...Downloads=true]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

2: Unpack the archive, cd into the folder.

3: sudo su

4: make

5: make install

6: reboot

7: Enjoy wireless...which is slightly different to the sequence in the tutorial i was using before ([http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)) in that step 5 above is slightly different to it's equivalent step 9 in Bill Giannikos's tute. I doubt that it makes a difference, but i don't know enough to know for sure.

2) eshwar_andhavarapu says to try the command: "ifconfig wlan0 up"; when i try that, it returns this message:> SIOCSIFFLAGS: Permission deniedI didn't have the guts to try "sudo su", "./wlan0down", "./wlan0up", which that poster also suggests, because of the scary looking "sudo su", and the fact that i don't know what those commands do, and a similar looking command already returned the SIOCSIFFLAGS error message (above).

3) And the third thing i noticed from that thread was that moviemaniac says there's another way to do it again:> Here's a quicker solution for y'all:

Just install this package and you should be fine (it's a dkms package so you don't have to reinstall it on every kernel update): [https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb]("https://launchpad.net/%7Ematt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb")

And add this ppa here for updates: [https://launchpad.net/~matt-price/+archive/mattprice]("https://launchpad.net/%7Ematt-price/+archive/mattprice")...which i haven't tried because i am not sure if he means to try that from scratch - presumably the fact that I've already installed the 8192 driver would conflict with other fixes? Like i said above, i don't know how to uninstall drivers cleanly.

I wrote earlier:
> when i connected an ethernet cable to it a few hours back, it produced an error message that i can't bring to memory at the moment.The error message that appears when i connect the ethernet cable:

A scary looking red exclamation mark (surrounded by what looks like an explosion) appears next to the icon for the NetworkManager Applet, and when I double-click on it, I get a message that says:> Your system encountered a serious kernel problem.

Your system might become unstable now and might need to be restarted.

You can help the developers to fix the problem by reporting it.

(report problem)    (close)... which makes me wonder if the ethernet problem could be addressed by upgrading to the 10.04 "Lucid Lynx" kernel.

But, of course, as i mentioned above, i have no wireless, no ethernet, and no cd drive on that machine. So unless i can figure out how to run a CD image from a file on the hard drive, or unlessi can solve my wireless or ethernet problems separately (the wireless is more important - i never use the ethernet connection to my modem normally, it is in an awkward position for everyday use), it seems i can't upgrade the kernel.

---

### Post by k3lt01 on 2010-08-01
Have you got access to another machine that you can download 10.04 and put onto a flash drive with? If you have that's what I'd be doing. Once it is on a flash drive you may be able, I'm not sure so I'll only say may be able, to update that way without actually removing 9.10.

---

### Post by orethrius on 2010-08-02
**SIOCSIFFLAGS: Permission denied** is just ifconfig's way of saying "you have to be root to bring additional hardware online."

**sudo ifconfig wlan0 up** will bring the interface up for further commands, **ifconfig wlan0 up** will continue to do absolutely nothing unless you modify **/etc/sudoers**, which you *also* would have to be root to do. ;)

My suggestion (in Alt+F2, "gnome-terminal"): 
**gksudo 'ifconfig wlan0 down; sleep 2; iwconfig wlan0 essid "yournetworknamehere" key restricted "yourkeyhere"; sleep 2; ifconfig wlan0 up; sleep 2; dhclient wlan0'**

It's by no means a permanent fix, but it should work for now.

---

### Post by red101 on 2010-08-02
I too had problems getting wi-fi to work. My laptop just woul not detect any wireless networks. But installing wicd from synaptic and removing gnome network manager did the work. Wireless works fine now.

---

### Post by k3lt01 on 2010-08-02
> **red101 said:**
> I too had problems getting wi-fi to work. My laptop just woul not detect any wireless networks. But installing wicd from synaptic and removing gnome network manager did the work. Wireless works fine now.
And now Mr Positive will say something, lol. Everytime I see someone tell a noob to remove NM and install WICD it ends in tears with Ubuntu having to be re-installed and the initial problem still having to be fixed. I'm not saying your suggestion wont work but I am saying I have never seen it happen.

---

### Post by orethrius on 2010-08-02
> **k3lt01 said:**
> And now Mr Positive will say something, lol. Everytime I see someone tell a noob to remove NM and install WICD it ends in tears with Ubuntu having to be re-installed and the initial problem still having to be fixed. I'm not saying your suggestion wont work but I am saying I have never seen it happen.

...and every I see those recommendations, it's because people either make people too afraid or too ignorant to bother with the baseline commands I reposted above.  If those don't work - as in, at all - then something's *really wrong*.  Yes, **sleep 2** isn't strictly necessary, but it can't hurt if you're not manually entering the commands.

---

### Post by k3lt01 on 2010-08-02
> **orethrius said:**
> ...and every I see those recommendations, it's because people either make people too afraid or too ignorant to bother with the baseline commands I reposted above.  If those don't work - as in, at all - then something's *really wrong*.  Yes, **sleep 2** isn't strictly necessary, but it can't hurt if you're not manually entering the commands.I agree totally, do the work to fix the issue properly instead of resorting to something that can, and in my experience always does, create more problems.

---

### Post by dissembly on 2010-08-02
Hi guys, thank-you for bearing with me there;

> **gksudo 'ifconfig wlan0 down; sleep 2; iwconfig wlan0 essid "yournetworknamehere" key restricted "yourkeyhere"; sleep 2; ifconfig wlan0 up; sleep 2; dhclient wlan0'**

I've entered this, and it takes me to the command prompt again, but there is no change in what my NetworkManager shows (i.e. no wireless). I've rebooted, and no change.

Which seems very ominous, since you said "If those don't work - as in, at all - then something's *really wrong*."!

What's happening? What should have happened?

---

### Post by orethrius on 2010-08-02
Hrm.  Perhaps **iwlist wlan0 scanning** shows your wireless?

---

### Post by dissembly on 2010-08-02
No, it says:

> wlan0        Scan completed  :  

...and beneath it there is a blank line before it goes back to the command prompt.

I have another machine right next to it that detects my wireless network at full strength, and i have tried moving it closer to the router, with no effect - so it must be something wrong with the Ubuntu machine.

But i gathered (from the information i've had from terminal previously) that the driver is installed, and other people seem to have gone okay using the RealTek 8172 wireless card with the 8192 driver.

-------
(Edited to add - i've tried that command with "sudo" and "gksudo" as well, with the same effect.)

---

### Post by orethrius on 2010-08-02
The only thing I can think of here is that your router's on WPA... which shouldn't cause this issue, given, but we'd be dealing with wpa_supplicant, which is something of a different kettle o' fish.

---

### Post by dissembly on 2010-08-02
I beleive it is - when i check network connections on my Windows XP machine (this one), it lists my network as "Security enabled wireless network (WPA)".

Is there a different command to get the the card to scan for WPA than what it was doing before?

(Forgive me, i know as little about wireless networks as I do about Ubuntu! I've never had to think about it before... maybe Windows wizards are spoiling.)

---

### Post by orethrius on 2010-08-02
Interestingly, I've been using WEP precisely to dodge having to deal with WPA issues.  Unfortunately, that also means that I have little to no experience in actually dealing with WPA issues.  Perhaps someone who's bothered can take the time to supplement the answers already provided. :(

---

### Post by k3lt01 on 2010-08-02
dissembly, I'm also out of my league with this but can help along the way with various things that may crop up. I would suggest you Google, or even use the search function in this forum and the main Ubuntu site, "WPA" and "WPA 9.10" or a variation of this. There will be an answer somewhere it is just a matter of finding it or waiting for someone who knows to help out.

[Here's another]("http://wireless.kernel.org/") wireless driver site you could take a look at it does mention yours.

---

### Post by dissembly on 2010-08-02
That's okay; thank you both so much for the patient advice so far, i do really appreciate it.

I will refine my searches to looks for WPA troubleshooting pages, and keep an eye on this in case a WPA-expert comes along.

---

### Post by dissembly on 2010-08-02
Just in case anyone with some thoughts on WPA come past, i have been flailing around the past couple of hours, and i thought i would post a log of the changes i have made to my system during the aforementioned flailing.

Among others, i have been looking at these two tutorials:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
&
[http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html)

I've modified my files according to these steps drawn from these tutorials; these are the only steps i (vaguely) understand, which is the reason i've limited myself to these changes to see if anything happens:

> 1) Open a terminal window and type:
  	Code:
 	wpa_passphrase your_ssid your_psk 
Note: your_ssid is the name of your wireless network (a.k.a. SSID) and your_psk is the password you want to use to protect your network. (Look below for an example).
 
 2) Now copy the psk string you got as output.
 
 3) Type:
  	Code:
 	sudo gedit /etc/wpa_supplicant.conf 
Then paste this as follow:
  	Code:
 	ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={

       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
} 
Note: your_psk is the psk string you got from step 1.
 
 Here is an example:
  	Code:
 	luca@laptop1:~$ wpa_passphrase mywlan thisisthepassword
network={
        ssid="mywlan"

        #psk="thisisthepassword"
        psk=[COLOR=Red]b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515[/COLOR]
} 
The red string is what you have to paste into /etc/wpa_supplicant.conf as your_psk (without quotes obviously). So you'll have something like this:
  	Code:
 	ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={

       ssid="mywlan"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515  
4) Save the file and close Gedit.

and

> Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
 sudo touch /etc/default/wpasupplicant


So far, nothing. No wireless networks detected.

The only thing it's done is to move my NetworkManager icon to the other side of my battery icon - that happened after rebooting, when i created the file "wpasupplicant" in "/etc/default/" and added the line "ENABLED=0" to it. I'm not sure if it means anything.

---

### Post by dissembly on 2010-08-09
I thought i would post this here for the benefit of any future searchers, and for the amusement of k3lt01 & orethrius, for being so very patient.

I have solved my WPA issue.

It turns out that the RealTek 8192SE driver works fine with the RealTek 8172 card, and my terminal commands were probably all behaving correctly. The problem was elsewhere.

I noticed this morning that there was a wireless icon marking the secondary function of my F12 key. I held down "Fn + F12" to see what it would do, thinking i would just get some sort of error.

Turns out that's the button for turning the wireless card on and off.

(In my defense, i was familiar with laptops where the wireless card is switched on and off both with a physical button *and* with the wireless manager. But... it's still pretty appalling.)

So, future searchers, i guess troubleshooting step 1 for wireless: Make sure your card is turned on.

I am going to go and sit in the corner in n00b shame.

---

### Post by k3lt01 on 2010-08-09
Mate, we have all been there and done that, well maybe not that exactly.

It's good to know you have it figured out. Cheers

---

### Post by k3lt01 on 2010-08-09
Lol, I just remembered I actually [asked another member a few days ago]("http://ubuntuforums.org/showthread.php?t=1545983") if he hadn't accidentally turn his switch off. I should have asked you.

---

### Post by dissembly on 2010-08-09
Oh dear. The first thing i did upon getting wireless was to install updates, and then it stopped working.

So i ran through this: [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10) again... with different results.

Now i have no wlan0!

---------------
Edited to add:

Ok, i have downloaded the newest driver from: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

And followed the procedure in [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10) with the newer driver substituted for the older one.

Now I have "Wireless Networks" show up in Network Manager, so that did the trick. it was just an outdated driver for my newly updated kernel.

Now i have pressed the wireless "on" button again, restarted, and Network Manager asks me for my password to connect right away.

Breathe sigh of relief.

Am slowly learning that computers actually do make sense, when you start to figure out what everything actually means... which is one of the reasons i wanted to try Ubuntu in the first place, so - i am quite happy.

---

