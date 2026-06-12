---
title: "Getting WiFi Signal, but Status = Disconnected?"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by theonedigg on 2006-12-22
IBM TP recognizes wireless card, but status is disconnected.

root@tp:~# iwconfig
eth1      IEEE 802.11b  ESSID:"AccessPoint"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:21:38:E9   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=35/92  Signal level=-61 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@tp:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:86:49:1A:C8  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:86ff:fe49:1ac8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:611 errors:0 dropped:0 overruns:0 carrier:16
          collisions:0 txqueuelen:1000 
          RX bytes:215697 (210.6 KiB)  TX bytes:108415 (105.8 KiB)
          Interrupt:11  

Did work at one point, but the box got rebooted, now it doesn't connect, Any Ideas?

---

### Post by Ashrael on 2006-12-22
Did you use encryption like wep or wpa before? Maybe you gotta connect to the router by cable and copy the ecryption code from the router to your network setup.....  Or the other way around maybe.....


hope this helps

---

### Post by floke on 2006-12-22
Did you reboot the PC or the router?

A useful wi-fi manager that might help is available via: 
sudo apt-get install network-manager-gnome

Should help if you have encryption

And you've definitely 'enabled' the wireless connection in the network box right?
(just checking!)

---

### Post by theonedigg on 2006-12-22
The AccessPoint is open (No Authentication WEP/WPA). I do get a signal strength of 80%.
And it looks like it's picking up the ESSID. But I can't ping the router.

The interface eth1 shows as active in Network Settings, but Status is disconnected.

I installed network-manager-gnome, and it says "No network connection".

iwconfig picks up eth1 (wifi card) link quality, signal, noise level, and Mac Address of Access Point, but status is still Disconnected and I can't ping the router.

Man that's strange? Any other ideas?

---

### Post by floke on 2006-12-22
And you've definitely got it set up right in 'System/Administration/Networking'?
Wireless is enabled + the Preferences are set up right?
You've got no encryption set up in your preferences? + the SSID name is entered + you have it set to DHCP with all the other boxed blank?

---

### Post by theonedigg on 2006-12-22
> **Steve.K said:**
> And you've definitely got it set up right in 'System/Administration/Networking'?
Wireless is enabled + the Preferences are set up right?
You've got no encryption set up in your preferences? + the SSID name is entered + you have it set to DHCP with all the other boxed blank?

Sys/Admin/Networking configured perfectly. Tried DHCP and Static
No Encryption or Mac Address filtering (Wide Open).
It does show the interface as active, but no connection. - my other laptop connects just fine.
Tried with different wifi card on Ubuntu, same results = finds signal, status=disconnected

Ident recognizes the card. iwconfig shows the settings and all. Just can't connect?

reboot Access-Point, same result...

Need to get this working...Any more ideas?

---

### Post by floke on 2006-12-22
I'm afraid I'm all out of ideas on this one. It sounds very strange, but the answer is probably something ridiculously simple: your wireless router is definitely connected to the internet? I've had problems before only to discover that I've had a brief dropout or have been disconnected.
And all the settings you have are exactly the same as for the other PC?

You say it used to work and then you did a reboot - do you mean complete reinstall or just rebooting the PC?

---

### Post by theonedigg on 2006-12-22
Yeah, just a PC reboot.

The wierd thing is I can see signal changes in the taskbar as I take down the Access Point and restart it. Running a sniffer on another machine, I can see SSID broadcast from the card and the Acesspoint. 

Just no damn connection. 

Very puzzling, very frustrating.

the eth0 interface (hardwired to another router works just fine).

netstat -r setup correctly. 

Still Stuck.

---

### Post by floke on 2006-12-22
A couple of suggestions - but not sure how useful they'll be.
(1) You could try changing the SSID - i.e. it seems like yours is currently 'AccessPoint' with a different nickname - you could set it to something else and see if that helps ??
(2) You could try disabling the LAN - when I set my wireless up I couldn't connect at all until I disabled the wired connection (something that the instructions failed to mention).

On the positive side - it does seem as if it will actually work - since (a) you had it working before; and (b) all the hardware etc. is detected. Using Linux can be a very frustrating experience, but at least it teaches you something - so keep looking on the bright side:) 

You'll get there in the end!

---

### Post by MrHorus on 2006-12-22
Mine connects but doesn't pick up an address - I have to run DHCP manually.

Drop to a terminal and run dhclient - see if it picks up an address.

You may have to be root to do this.

---

### Post by Ashrael on 2006-12-22
Does your router have mac-address blocking? see if it's on... you are not getting an ip address so this could be the problem....

---

### Post by theonedigg on 2006-12-22
Thanks for all the help!!!

Decided to reinstall after trying everything I could think of...

When I started the reinstall using the Ubuntu CD, it detected the wireless interface and am now using it for the install!!!

What a f'ing pain in the ***!!

No f'ing clue why it wouldn't come up normally...and if it happens again, no idea how to fix...

JHChrist ...;) don't mind me...just blowing off some steam....;)

Thanks for all the help!!!

---

### Post by floke on 2006-12-22
Very funny!
Glad to hear you got it sorted.
Hope it doesn't go again!

---

### Post by dujlinvik on 2006-12-22
my probleme is very similar to yours.... I'm newbie in Linux and trying to establish a wifi connection in Ubuntu, without success for 4 days...
my w. card is enabled and configured in Network Manager, here is a listing of the config :

dujlinvik@dujlinvik:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"ravangrad_kupusina"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:02:6F:32:33:F3   
          Bit Rate:11 Mb/s   Tx-Power:2 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level=-74 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

dujlinvik@dujlinvik:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 ra0
dujlinvik@dujlinvik:~$       

I can't ping the AP (i supposed it's on 169.168.0.1 ), nor any other host on the network. Therefore, i'm not able to load any site in Firefox......
is there something wrong in this configuration, or i made a mistake somewhere.... don't know where to search.
Any help will be appreciated.

---

### Post by floke on 2006-12-22
I think that to get help with this you would be better off starting a new thread, and search the forum for similar issues. By posting your query at the end of this thread, you reduce the chances of it being seen.

You could, though, try:

sudo apt-get install gnome-network-manager 

and see if the gnome wireless manager can solve it.

---

### Post by dujlinvik on 2006-12-23
sorry for posting here, i've been posting for few days about my probleme in a new thread, but nobody replied yet, i'm getting desperate...... :( 
anyway, thanks for your help!

---

### Post by floke on 2006-12-23
Have yuo tried messing around with the network settings?
When I first tried to use the wireless I had all the settings entered and nothing for 2 days - then I deleted all the settings - i.e. just entered the SSID, the WEP code, and set to 'Automatic (DHCP)', and left all other entries blank - and it worked.

Also - I've read that you should really try to set up wireless with the encryption turned off - so I would try that too.

---

### Post by dujlinvik on 2006-12-23
i think that there's no encryption on my ISP's wireless network at all (not sure), but i don't know how to turn off encryption in Ubuntu. Don't forget, i'm totally new in Linux :p

---

### Post by dujlinvik on 2006-12-23
i'm happy to inform you that i've succeded in establishing a wireless internet connection in Ubuntu, so that's my first post in Linux!!!!
the only thing i had to di is to create a new ppp0 nterface with 'pppoeconf'
i forgot (?!) that i'm using pppoe protocol vie my ISP's wireless network :)  
anyway, thanks for Your help!

---

