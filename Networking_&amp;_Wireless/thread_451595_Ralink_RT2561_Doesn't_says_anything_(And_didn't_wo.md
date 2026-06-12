---
title: "Ralink RT2561 Doesn't says anything (And didn't work)[Feisty] HELP PLEASE!"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by MetaMorfoziS on 2007-05-22
Hi all!
Im using kubuntu feisty, any my machine's infos (lsmod,dmesg,etc) available here:
[http://metamorfozis.hu/inf/](http://metamorfozis.hu/inf/) (Apache index of, and ~200k *.txt)

So, i have a PCI ralink wireless card (RT2561)
And i have setted up the (actually) latest serialmonkey driver.

The problem is i can't debug, whats wrong.
If i do: sudo iwconfig ra0 mode managed channel 1 key restricted s:PP essid NETWORK

absolutely nothing happens. Nothing in syslog or in the cli after the execution.
But, i didn't get ip from the router, and it's absolutely didn't work.
Also, i can scan for networks etc, so the driver looks work. But i'm not experienced in troubleshooting wireless cards, so i dunno.

Please help me!
I have this card about a half year ago, so i have some google behind me, but nothing helps. I thinks i'm near the working, because i tryed many versions of ndiswrapper and others, and i always haev some errors...
Please help me!
Thankfully..

Edit: And i have disabled the built-in networkmanager.

---

### Post by blazercist on 2007-05-22
you have the latest driver? is it the second beta? or the nightly?  the problem there is a glitch in the driver which makes it forget WEP keys, theres a patch in the rt2x00 forums you need to be registered on those forums to see it and download it. if you need a link holla at me.

Yea, about the debug thing, I dunno cuz I never needed to.  I have the same card built in to my laptop, feisty wouldn't even boot with network-manager installed, this is because having eth0 and ra0 both up at the same time causes a kernel lockup at least on my system.  

I have it working now and I can probably help you, so don't start pulling your hair out yet.

---

### Post by MetaMorfoziS on 2007-05-22
Hy! 
Thank you for answer!

in dmesg i see:
[   31.552000] rt61 1.1.0 Beta 2 CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

So i think i have the second beta.

this is? [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3669](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3669)
If not, please write that to me, because as i se a tons of patch exists.

And if you can, please help me a little in patching (i don't know how can i do that).


Thank you!

---

### Post by blazercist on 2007-05-22
BEFORE YOU DO ANYTHING TRY TO APPLY A WEP KEY

sudo iwpriv ra0 set Key1=YOURKEYHERE

then type 

sudo iwconfig

it should display  0000-00-0000 as your WEP key, if it does then proceed, if not then you and I have a different problem.

Try turning off WEP on your router and see if you can connect, if you can then all is well and we can move on to the driver fix:

this is the patch  [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3560](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3560)

and the instructions can be found here [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3752](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3752) in the last couple of posts.

the second link is actually my thread so it might do you good to read the whole thing and see if you have similar symptoms and what not maybe it will help.

edit : oh it looks like he's removed the patch saying that its obsolete, perhaps the hourly CVS has the patch applied already, try that instead.

EDIT AGAIN: LOL, if your WEP key actually does show up when u do the iwpriv command I said above, then you are still ok and you should use a script with a couple iwpriv commands that I wrote and it goes a little something like this:

sudo iwpriv ra0 set NetworkType=Infra 
sudo iwpriv ra0 set AuthMode=WEPAUTO 
sudo iwpriv ra0 set EncrypType=WEP 
sudo iwpriv ra0 set DefaultKeyID=1 
sudo iwpriv ra0 set Key1=YOUR KEY HERE
sudo iwpriv ra0 set SSID=YOUR SSID HERE
sudo dhclient ra0 
sudo ifdown eth0

---

### Post by MetaMorfoziS on 2007-05-22
Thanx, as i see it's solved, so this means, if i build the latest cvs tarball is enough?

---

### Post by blazercist on 2007-05-22
you may want to read my last post again cuz i edited it about 10 times. lol.

---

### Post by MetaMorfoziS on 2007-05-22
Sorry i just only read your 2-3 lines not before not more...:)
Sorry, i dotrydoandtry and pray...:)

---

### Post by MetaMorfoziS on 2007-05-22
Ouhm?!
Iwconfig says:
ra0       RT61 Wireless  ESSID:"mmc"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:746F-6B6F-6E73-7A75-726F-6D6D-61
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


wlassistant still says "Connection failed"
I'm using wpa2psk on the router actually, i can set that to other, but that needs to go back to the router to the other house:)



Iwpriv says:
ra0       Available private ioctls :
          set              (8BE2) : set 1024 char  & get   0
          stat             (8BE9) : set 1024 char  & get 1024 char
          rfmontx          (8BEA) : set   2 int   & get   0
          get_rfmontx      (8BEB) : set   0       & get   1 int
          get_site_survey  (8BED) : set 1024 char  & get 1024 char
          get_RaAP_Cfg     (8BEF) : set 1024 char  & get   0

After your first line...
So do i need to compile the latest cvs or not?

---

### Post by MetaMorfoziS on 2007-05-22
I have installed the new one, i see it has many changes. I go to reboot...

---

### Post by MetaMorfoziS on 2007-05-22
Hmm, it's still ra0 where i deleted that line from modprobe.conf (as the install asked)
For today i'm to tiread and angry, so thank you all, i will try again and again when once it starts to work. To save you from the refreshing this topic, i will send you pm, if i have questions, and again thank you!
(And sorry for my english grammar:/)

---

### Post by blazercist on 2007-05-23
have you tried RutilT from the rt2x00 site?  Its a GUI network manager type tool made specifically for the RT based cards. you might have more luck with that.

---

### Post by blazercist on 2007-05-24
Oh duh, you are trying to use WPA, WPA is broken currently in the RT drivers, try using WEP instead.

---

