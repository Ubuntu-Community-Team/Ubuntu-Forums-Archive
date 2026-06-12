---
title: "Wireless network issues."
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Windows Nerd on 2009-08-25
Hey y'all,

Lets get straight to the point. I cannot connect to the internet with my computer. I was able to up until yesterday night. It says I am connected via wireless to my home network, but I cannot see the other computers on the network, or access any internet related services. It is like I am not connected to any network, in a sense, though the icon in the notification area says I am connected with 4 "bars" of connectivity.

Ubuntu has been a bit frustrating for me since installation. For me it has been: Problem->Post to Ubuntu forums for solution->Find a good solution after a couple days->Fix problem->Repeat. First it was creating and enabling a swap partition. Then it was making hibernate and suspend features work. Then it was making it possible to play dvd's. Now this. I am exploding in frustration here; if it is commonplace for new Ubuntu users to feel like this, let me know. 

As always, when providing a solution, I am not afraid of the terminal or command line applications; so feel free to provide the solution without the limitation most users have with terminal or command line.

Scott

---

### Post by Windows Nerd on 2009-08-25
Anyone? I see 39 views and 0 replies...

---

### Post by 0faber on 2009-08-25
Scott -

This sounds like it could be something really simple like resetting the modem the wireless router is connected to. (Windows is a bit more helpful in this situation, it says "a cable is not connected" or something like that. Ubuntu's network manager acts like everything's fine as long as long as it's getting a wireless signal, and doesn't tell whether the router's connected. You just find out when you try to connect.) Obviously, if you getting on the web through another computer on the same network that's probably not the problem, but I hope so .., The fact it was working before suggests it's not Ubuntu.

2nd question:
Is it commonplace for new Ubuntu users to feel frustrated? From what I see here, it's pretty common, especially for people installing Ubuntu on laptops. I personally didn't have any problems, but hibernate suspend problems are par for the course with laptops.

Keep in mind that you're installing an operating system that's different from the one the machine was originally designed to work with. Hopefully once everything's working you'll think it was worth the effort.

To get quicker answers on the forums, try using search first before posting. It wouldn't work for this question, but searching "hibernate" + your make and model of laptop could turn up another thread with the same computer and same problem, already answered.

---

### Post by Windows Nerd on 2009-08-25
I searched the forum for hibernate/suspend issues, and none appeared to have a clear solution. Just to let you know :). But anyways, how do I get it to stop Ubuntu "thinking" it is connected when it is really not...
 
Scott

---

### Post by 0faber on 2009-08-25
Strictly speaking, it doesn't think it's connected, it thinks it's got a signal from the router. And if it's on, that is true.

I've heard a lot of people saying wicd is a better network manager, but I haven't tried it, and don't know if it handles this sort of thing any differently.

---

### Post by Windows Nerd on 2009-08-25
Wicd...Is this availible to download as a .deb file? Because Synaptic won't download them when you have no internet. 
 
I can access internet perfectly well from my windows partition, if it makes a difference...
 
Scott

---

### Post by zkriesse on 2009-08-26
Wireless? Here. Wireless is actually quite easy to set up. Opposite click on system go to edit menus. Go down to preferences then make sure that the option network connections is clicked. Close the menu. Then go to System/Preferences/Network Connections. Go to the Wireless tab. It should show the available networks that you can connect to. Click the one that you want and then click the Edit tab to the right of the screen. Make sure that the Connect Automatically option is checked if you want it to connect when the wireless is turned on. Hopes this helped.

---

### Post by Windows Nerd on 2009-08-26
> **Zachk18 said:**
> Wireless? Here. Wireless is actually quite easy to set up. Opposite click on system go to edit menus. Go down to preferences then make sure that the option network connections is clicked. Close the menu. Then go to System/Preferences/Network Connections. Go to the Wireless tab. It should show the available networks that you can connect to. Click the one that you want and then click the Edit tab to the right of the screen. Make sure that the Connect Automatically option is checked if you want it to connect when the wireless is turned on. Hopes this helped.

Didn't you read in my first post that I could connect to the network before? It is set up with the right password and is set to connect automatically.


Scott

---

### Post by wojmur on 2009-08-26
Can you show us output of
```

$ /sbin/ifconfig
$ /sbin/iwconfig
$ /sbin/route -n
$ cat /etc/network/interfaces

``` while your icon says you are connected

---

### Post by nothingspecial on 2009-08-26
If you could connect before but can`t now it may be that a kernel update has stuffed your wireless.

Restart and when that message about grub loading comes up press escape and choose a previous kernel (lower number) from the options.

---

### Post by Windows Nerd on 2009-08-26
I upgraded my kernel to the new one developed for Karmic, so that I could hibernate/suspend my computer. I could connect fine even with my new kernel up until 2 days ago. I will try to see if booting into an older kernel makes a difference. And I will post the output of those 4 commands tommorow morning,as I have to get to bed early as I am not feeling to well.

Scott

---

### Post by zkriesse on 2009-08-26
Just a warning. Karmic is still in development so be careful with the new kernel. It's gonna be a couple months be it's labeled as officially stable so just make sure you back up your system!

---

### Post by Windows Nerd on 2009-08-26
Hey guys,

As promised, I tried to boot into my second newest kernel (the newest one for Jaunty), and it did not change a thing: I still had the same problem.  ](*,)


I entered those commands you asked me to enter into the terminal too. I saved them to a text file in windows so I could upload them easier. Here you go:

```

scott@scott-laptop:~$  /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:c5:c0:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:de:d7:67  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fede:d767/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180365 (180.3 KB)  TX bytes:1580 (1.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-DE-D7-67-37-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

scott@scott-laptop:~$  /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home1"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:21:29:92:1B:2E   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

scott@scott-laptop:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
scott@scott-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

scott@scott-laptop:~$  
```

Scott

---

### Post by Windows Nerd on 2009-08-26
After some recommendations by my cousin (who works with Linux machines at work) I booted into my Live CD, and by golly, I had internet connectivity, I could see everything else on my network, and I could access goggle and all that. So the problem I have must have something to do with an update I installed earlier. One solution would be to reinstall Ubuntu with a fresh clean install, then setup hibernate/suspend, playing encytped dvd's, ect ect again. I am treating this solution as a last resort, because by doing that, I am not exactly solving the problem...nor do I learn anything according to how to solve the problem...

Scott

---

### Post by pablolie on 2009-08-26
I think the "new" network manager represents a compromise that makes some things easier, some things harder. 

I for one have replaced it with the wicd application, which is a bit more power-user friendly, versatile and compatible with more enterprise environments and hidden networks.

Do so only if you think you have run out of other options - again, for home environments I have found the packaged in functionality to be very, very stable -more so than the Windows functionality, and far more intuitive.

To install wicd, it is as easy as going to terminal and going
sudo apt-get install wicd

Restart you computer and you will see a new network application in your taskbar. 

...pablo

---

### Post by Windows Nerd on 2009-08-26
Ahh yes, I forgot about sudo apt-install....

Can I uninstall wicd later if need be and go back to my default network manager?

Scott

---

### Post by zkriesse on 2009-08-26
Most likely yes, you could uninstall that wicd program. Just be careful regarding commands. ALWAYS! make sure to do some research on the command that is given just to make sure it's valid. And you might find something better at the same time.

---

### Post by Windows Nerd on 2009-08-26
> **Zachk18 said:**
> Most likely yes, you could uninstall that wicd program. Just be careful regarding commands. ALWAYS! make sure to do some research on the command that is given just to make sure it's valid. And you might find something better at the same time.

I'm pretty sure sudo apt-get install wicd is a valid command...unless you mean when uninstalling it via command line. 

Going to give wicd a try now, folks. Be back in 10 minutes.

Scott

Edit: I forgot that Gparted was still in the middle of something. I shrank my recovery partition by 4 GB (It had 6 GB free) and handed that space over to my Linux partition. Going to have to wait for quite a lot longer...extending partitions takes forever...

---

### Post by zkriesse on 2009-08-26
Yeah....that's what I meant. If it's not valid it could either mess up your system something fierce or it might not work at all and just flash an error at you which not bad is still annoying.

---

### Post by Windows Nerd on 2009-08-26
Ok, one problem about wicd; I cannot download it even through terminal...because I cannot access anything in ubuntu except what is on my machine. Anyone got a deb package they can let me download to my Linux partition on windows or within my Live CD?

Scott

---

### Post by Windows Nerd on 2009-08-28
Hey all,

After a day spent staring at a computer screen searching for possible solutions, at the end of it I decided to give up and start from a clean install. I could connect to internet again, and after a few hours of adding some programs I had last time (not all of them), I ran into the same problem again. I noticed that the network manager notified me that it had disconnected from my network. When it reconnected, I had the same problem: Network manager says I am connected to the network, when I am really not. So, I decided to uninstall network manager and give Wicd a try (I downloaded this in my Windows partition as a .deb). It too gave me the same situation: it said it was connected, but it really wasnt. 

Attatched below is a screenshot of what happened with Wicd. My home network is named "home1".

Scott

---

### Post by Windows Nerd on 2009-08-29
Bump

---

### Post by Windows Nerd on 2009-08-29
Anyone? This thread is sort of dieing, but  my problem has not been solved. I understand that though it might be such an obvious solution  and that I should be figuring it out by myself, I have tried everything I can think of or has been suggested to me with no avail. I would like to solve this problem as one cannnot do much without Internet in ubuntu. 

Scott

---

### Post by Windows Nerd on 2009-08-30
Bump- hmm 300 views, it looks like this is one tricky problem no one seems to know the answer too...

---

