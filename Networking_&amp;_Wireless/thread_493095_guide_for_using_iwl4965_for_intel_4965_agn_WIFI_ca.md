---
title: "guide for using iwl4965 for intel 4965 agn WIFI card"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by rye_ on 2007-07-05
EDIT: Thanks to the suggestions made by those who have used this guide, changes have and are continued to be made in order to make it clearer.
I, and I'm sure the others contributing on this thread, encourage any feedback, comments, suggestions etc.


hello,

I'm not sure if such a guide has been posted in any detail before (if so I apologise);
as follows is the method I used to install the iwlwifi driver for ubuntu feisty;

1. add a reference to the gutsy sources for the installation of the 2.6.22-7-generic kernel.
(I'm told the most recent kernel is changing frequently; look for the most recent kernel and substitute 
any references within the guide to 2.6.22-7-generic with that most recent you are using)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

(graphically the above can be added via system->administation->sources add the line exactly as it is)

or alternatively via the terminal, copy and paste the above sources into the following file.

sudo gedit /etc/apt/sources.list


2 install the following; (kernel and sources), after having updated the sources.
(substitute '2.6.22-7-generic' with the most recent kernel)

linux-image-2.6.22-7-generic
linux-headers-2.6.22-7-generic

REMOVE THE CHANGES TO THE SOURCES MADE IN STEP 1, unless you want the unstable gutsy package updates (which I do not advise)

3. download the following from [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) 

iwlwifi-0.0.xx (Get the most recent)
iwlwifi-4965-ucode-4.44.xx (
mac80211-8.0.x (The developers advise the use of the 8.x.x branch rather than the more experimental 9.x.x branch, [http://intellinuxwireless.org/mac80211/downloads/mac80211-8.0.2.tgz](http://intellinuxwireless.org/mac80211/downloads/mac80211-8.0.2.tgz))

and extract the contents of the compressed folder, via the terminal (replace x with the appropriate numbers)

tar zxvf mac80211-8.0.x.tgz
tar zxvf iwlwifi-4965-ucode-4.44.xx.tgz
tar zxvf iwlwifi-0.0.xx.tgz

4. REBOOT INTO THE NEW KERNEL 

5. create the following folder for your firmware via the terminal;

sudo mkdir /lib/firmware/$(uname -r)


6. installation of the packages adapted from Zoltan's Blog (credit goes to him);

sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source

cd DIRECTORY_WHICH_CONTAINS_mac80211-8.0.x
sudo make patch_kernel

cd DIRECTORY_WHICH_CONTAINS_/iwlwifi-0.0.xx
make
sudo make install

cd DIRECTORY_WHICH_CONTAINS_/iwlwifi-4965-ucode-4.44.xx
cp iwlwifi-4965.ucode /lib/firmware/$(uname -r)

(this folder you have copied to is the one you created earlier, you ought to double check it exists.)

7. if you have ndiswrapper running (if not ignore this);

comment out from /etc/modprobe.d/ndiswrapper the line that says 'alias wlan0 ndiswrapper'
i.e. #alias wlan0 ndiswrapper

8. load the modules iwl4965 & mac80211

sudo modprobe mac80211
sudo modprobe iwl4965

FINISHED

SOME OBSERVATIONs;

strong stable connection.
no apparent flashing light for wireless.

The above worked without a hitch, I hope others have similar success.

PS.  future iwlwifi updates (an almost daily occurrence) can be installed over the current iwlwifi installation without any difficulties.
i.e via 'make' then 'sudo make install'

Ryan (+edits due to suggestions by jwater7, pem725, hisstareia

---

### Post by vronp on 2007-07-05
Ryan,

Thanks for all the effort you are putting into this.

I think I will give this a go.

I am curious to know if you have run into any problems as a result of the new kernel?  

thanks,
Dave

---

### Post by rye_ on 2007-07-05
hi,

thus far I've had no problems whatsoever with the new kernel, everything appears to be running very smoothly. (though of course I only updated a few days ago).

I'm looking forward to seeing whether you and others have any success in this.  It would nice to think we've cracked the driver problem in an easy to apply manner.  (and I thank zoltan? principally in this)

Ryan

---

### Post by jwater7 on 2007-07-06
I was not able to get this to work on my Toshiba A205, as soon as I modprobe iwl4965 (or reboot), my system hangs.

I discovered if I turn the hardware switch to the off position before I do this, it seems to boot normally, but after turning it on, it still does not recognize the device.

---

### Post by rye_ on 2007-07-06
jwater7,

did you apply this to the kernel from gutsy, if not that is the source of your problem.

This is my fault, with hindsight the guide should have explicitly said to reboot into kernel 2.6.22 after having installed the kernel and headers from the gutsy sources.  I've updated this.

Ryan

---

### Post by jwater7 on 2007-07-07
Yes, thank you for the clarification.

You would also want to modprobe iwl4965, not iwlwifi right?

I did actually do this, I also noticed at [http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)
that people were having similar problems, I wonder if this is a difference in hardware or kernel options or something?

Thanks.

---

### Post by rye_ on 2007-07-07
jwater7,

yes it should have been modprobe iwl4965. (I thunk it was late when I posted this:))

As far as kernel stability goes; I wasn't aware that any problems have been experienced in the 2.6.22-generic kernel, though from my own and other's experience the feisty kernels don't accommodate it (at least using zoltan's method).

If it helps you I'm using a dell 640m (core 2 duo 1.83 Mhz, 1 GB Ram, 160 GB hard disk, intel integrated graphics).  Everything thus far works wonderfully.

Could you elaborate on the problems you are experiencing? Maybe I or others can offer suggestions.

Ryan

---

### Post by jwater7 on 2007-07-07
Well,
After some more testing, It looks like it will boot up and work most of the time, but not every time.  I must have caught it when it wasn't working before.

The first time I did it, I'm suspicious if ndiswrapper was causing problems/conflicts, so that should be completely disabled now.

When it doesn't boot up, the symptom is that the Caps Lock Key Light blinks on and off, and the computer is frozen.

I also noticed that once and a while, I would see a "wlan0:ava" device from ifconfig, so I disabled avahi-daemon for a while just to see if that was doing something bad.

I'll see if I get find any more correlations to what's going on in the next few days.

Side Note: I'm also noticing that when I boot without the hardware switch on,and then turn it on after boot, it will not recognize the device.

---

### Post by vronp on 2007-07-09
The Intel guys have released a newer version of the driver at:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by iammeagain on 2007-07-09
> **jwater7 said:**
> Well,

When it doesn't boot up, the symptom is that the Caps Lock Key Light blinks on and off, and the computer is frozen.

I have a similar problem, where when I attempt to connect wirelessly it starts, the connecting spinning thing starts, and then everything freezes with the caps lock blinking at me.

---

### Post by Scotty562 on 2007-07-09
```
make
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
make -C /lib/modules/2.6.22-7-generic/source O=/lib/modules/2.6.22-7-generic/build M=/home/zach/Desktop/Ubuntu Wireless/iwlwifi-0.0.32/compatible/ modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-7-generic'
make[1]: *** No rule to make target `Wireless/iwlwifi-0.0.32/compatible/'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-7-generic'
make: *** [modules] Error 2

```

What did I do wrong?

---

### Post by rye_ on 2007-07-10
firstly,

my guess would be that build-essential or linux-headers are not installed.
run the following in the terminal.

sudo apt-get install build-essential linux-headers-$(uname -r)

secondly,

I sorry that more or you have not been able to recreate the same success that I'v had.  since I last emailed I 
have experienced one of the boot freezes.  These however are very rare, and I'm trying to figure (or research) a reason and solution.

Ryan

---

### Post by vronp on 2007-07-10
Guys,

I can't remember how I found this site but the Intel guys have setup a web site for bug reporting on this driver:

[http://www.bughost.org/bugzilla/](http://www.bughost.org/bugzilla/)

Please check it out and post your bugs to the iwlwifi section.

Also, please note they apparently are having discussion forums on Thursday on an irc channel.

Dave

---

### Post by muldy on 2007-07-11
Hi!

Can't make my asus f3sv wireless card work with th 4965 driver, it locks up and the caps key light starts blinking.

Tried the latest ndiswrapper and it works ok for the most part  in gutsy.
It's not stable, sometimes it disconnects from network, and i have to reconnect manually.

This is the best working solution i found, i tried in feisty both solutions that did not work (4965 driver / ndiswrapper ).


Just sharing information :)

---

### Post by Hisstareia on 2007-07-12
Whenever I try to install iwlwifi I get this error:

WARNING: "ieee80211_start_BA_session" [/home/hisstareia/iwlwifi-0.1.1/compatible/iwl4965.ko] undefined!
WARNING: "ieee80211_stop_BA_session" [/home/hisstareia/iwlwifi-0.1.1/compatible/iwl4965.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-7-generic'

And I get a similar issue when I try to modprobe:

FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-7-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Tried some synaptic searching and found 80211 source, but can't install that either (at least following the basic readme directions).

Any ideas?

---

### Post by rye_ on 2007-07-12
hi,

I'm also unable to make iwlwifi-0.1.1, try the prior release (0.0.35)

ryan

---

### Post by Hisstareia on 2007-07-12
Thanks so much for this I finally got it working!!! =D>. Quick improvements I can think of with my minimal linux knowledge.

1. The command you are looking for to create a directory is:
> sudo mkdir /lib/firmware/2.6.22-7-generic

2. If you have set up the 4965 AGN ndiswrapper drivers before, you need to check /etc/modprobe.d/blacklist for this line and remove it if it is there:
> blacklist bcm43xx

3. You need to remove the ndiswrapper alias from /etc/modprobe.d/alias, not /etc/modprobe.d/ndiswrapper.

=D> But really, I'm being picky. This is a great, easy to follow guide and it works! =D>

---

### Post by jmfrey on 2007-07-13
Excellent and easy to follow tutorial.

I'm going to reference this thread  on the dv9000 thread for others in my situation.

I initially followed your directions using the latest driver - iwlwifi-0.1.1 - but that did not work, receiving the "unknown symbol ieee80211_stop BA_session" error.

Repeating the tutorial with the previous driver - iwlwifi-0.0.38 - worked perfectly.

Initially, I got an error when the hardware kill switch was enabled - dmesg showed me that was what it was.

Turned the switch on, rebooted, and wham!   

OOPS - SPOKE TOO SOON... I DON'T HAVE ERRORS BOOTING, BUT THE SYSTEM DOES HANG (CAPS LOCK BLINKING) WHEN I TRY TO CONNECT TO A WIRELESS NETWORK USING WPA/PSK - HAVEN'T TRIED OPEN NETWORKS YET.

Thanks so much.

---

### Post by Hisstareia on 2007-07-13
> **jmfrey said:**
> 

OOPS - SPOKE TOO SOON... I DON'T HAVE ERRORS BOOTING, BUT THE SYSTEM DOES HANG (CAPS LOCK BLINKING) WHEN I TRY TO CONNECT TO A WIRELESS NETWORK USING WPA/PSK - HAVEN'T TRIED OPEN NETWORKS YET.

Thanks so much.

Having same issue with WEP. Since the driver isn't finished yet, I guess it is to be expected. Still, I'm really really hoping intel sends out a finished version soon!

---

### Post by iammeagain on 2007-07-13
I want to try out the ndiswrapper, since i get the blinking caps lock, ill switch ack when there is a solution. 
But how would I completely remove the changes that I made? and should i keep the new kernel or go back to using the older one? Mainly which will have less problems with ndiswrapper?

NVM I was impatient and installed ndiswrapper anyways with the drivers and also updated my kernel to 2.6.22-8 and somehow it is working now. So I decided not to mess with anything else for a while. lol.

---

### Post by jmfrey on 2007-07-13
I'm wondering if the hangup is not the wireless driver, but NetworkManager.

I'm going to remove NetworkManager and see if that solves the problem.

But first I have some clean-up to do.  After you update your kernel with the Gutsy repositories, it's a good idea to comment them out.  Doh!!!

---

### Post by jmfrey on 2007-07-13
I removed network manager - no luck.

Received a segmentation fault when running wpa_supplicant.

I upgraded the wireless tools and wpa_supplicant with the gutsy version - no luck - caps lock crash.

---

### Post by rye_ on 2007-07-13
> **iammeagain said:**
> I want to try out the ndiswrapper, since i get the blinking caps lock, ill switch ack when there is a solution. 
But how would I completely remove the changes that I made? and should i keep the new kernel or go back to using the older one? Mainly which will have less problems with ndiswrapper?

NVM I was impatient and installed ndiswrapper anyways with the drivers and also updated my kernel to 2.6.22-8 and somehow it is working now. So I decided not to mess with anything else for a while. lol.


I used to use ndiswrapper on the initial feisty kernel (I think this was 2.6.20-15-generic).  It installed and loaded fine, though of course it was unstable, especially during sustained downloads.  I tended to fine that after a couple of minutes it was necessary to remove and then reinsert the ndiswrapper module.

With practice it wasn't an entirely unreasonable solution, 

Ryan

---

### Post by vronp on 2007-07-13
I hate to beat a dead horse, but please report all bugs on this Intel site for the 4965 driver:

[http://www.bughost.org/bugzilla/](http://www.bughost.org/bugzilla/)

---

### Post by Hisstareia on 2007-07-13
After a day and a night of lots of debugging I found some success by downgrading to the older mac80211 subsystem (anything older than 9.*.*.*). The light doesn't light up, but the connection itself works fine :). I'll see how it works from here.

---

### Post by cmonkey on 2007-07-14
> **Hisstareia said:**
> After a day and a night of lots of debugging I found some success by downgrading to the older mac80211 subsystem (anything older than 9.*.*.*). The light doesn't light up, but the connection itself works fine :). I'll see how it works from here.

Thanks for the suggestion.  After a couple days of failing to get it working on my T61, it's now working happily with mac80211-8.0.2 and iwlwifi-0.0.38.

---

### Post by Hisstareia on 2007-07-14
> Recent news for mac80211
Jul 10 2007 snapshot: 9.0.2

    * NOTE: **9.x.x branch is experimental since it includes patches which are not submitted to linux-wireless yet. If you are not using IEEE 802.11n functions, please still use 8.x.x branch.** 

And there you have it (emphasis mine). So, if the new versions don't work for you the 8.x.x branch is worth a go. Still running like a charm on my PC.

---

### Post by ehmdjii on 2007-07-15
thank you very much for this guide!

i followed it and it gave no error messages. unfortunately i still have no wlan device in my ifconfig. also the light indicating the wlan card is off. it also doesnt switch on if i activate it with the hotkeys.

this is an asus g1s laptop.am i missing something?

edit: ok, now i also got the mentioned capslock crash. does anyone yet know how to solve this?

---

### Post by pem725 on 2007-07-16
rye_,

Thanks for the great guide.  I have a few minor suggestions that might help some newbies avoid trouble. 

under 2.

Be sure to check for version of the kernel headers and image files.  When I used the guide, I found that the repositories updated from -7 to -8.  Newbies might find this confusing.  So I issued a simple search for the versions in the gutsy repository.

apt-cache search linux-image

sure enough, the latest version was linux-image-2.6.22-8-generic

I suspect that with the development of gutsy, the kernel versions might change quite rapidly.

under heading 3.

iwl driver website is here:

[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)

You will find the mac80211, iwlwifi-4965-ucode, and iwlwifi files at that site.

To unpack the files, just issue these commands.

tar zxvf mac80211-8.0.x
tar zxvf iwlwifi-4965-ucode-4.44.xx
tar zxvf iwlwifi-0.0.xx

Be sure to eliminate the x and replace it with the specific version you downloaded from the Intel website.  We recommend that you stick with the 8.0.x version (8.0.2 is the latest as of July 16th, 2007) since the later versions are experimental and pertain only to 802.11n.  If you absolutely need 802.11n support, give the latest version of mac80211 a try (YMMV).

under 8.

modprobe mac80211
modprobe iwl4965

These two steps make the kernel module loading explicit.  I also included the two modules in my /etc/modules file.

sudo nano -w /etc/modules

mac80211
iwl4965

Finally and perhaps most important, I would emphasize that users ought to comment out the gutsy repositories from /etc/apt/sources.list lest they continue to run into odd updates that have nothing to do with feisty.

nano -w /apt/sources.list

change the following two lines

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
 
to

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted


Thanks again for the fine HOWTO.  I was stuck on the kernel for the longest time and even thought of rolling my own as I usually do but I just needed my Lenovo 3000 v200 to work with standard apt-get stuff for now.

---

### Post by ehmdjii on 2007-07-17
does anyone with the capslock crash have any news yet?

i am still stuck with this. the card seems to work, but as soon as i try to connect to a network i get the capslock crash. :(

---

### Post by rye_ on 2007-07-17
hi,

my guess would be that you are using the 9.x.x branch of mac80211.
if its of interest the packages I'm using are;

kernel 2.6.22-8-generic
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-0.0.41.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-0.0.41.tgz)
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz)
[http://intellinuxwireless.org/mac80211/downloads/mac80211-8.0.2.tgz](http://intellinuxwireless.org/mac80211/downloads/mac80211-8.0.2.tgz)

also from my experience this newer kernel is more stable than the last.

ryan

---

### Post by ehmdjii on 2007-07-17
thank you, yes that may be possible.

how can i check the version of my mac80211 module. and if it is 9x version how can i replace it with a 8x version?

thanks!

---

### Post by rye_ on 2007-07-17
I'm guessing a little with the following.  it may be that after doing this you have to rebuild iwlwifi as expressed in the guide.  But first just try to rebuild the mac80211 package;

-download and unzip the mac80211-8.0.2 compressed folder for whose link I posted above.
-in the terminal;

  cd Where_the_unzipped_folder_is/mac80211-8.0.2
  sudo make patch_kernel
  sudo modprobe mac80211

 
Good luck

Ryan

---

### Post by ehmdjii on 2007-07-17
thanks i will try that and report back here.

---

### Post by mikeschuld on 2007-07-17
> I'm guessing a little with the following. it may be that after doing this you have to rebuild iwlwifi as expressed in the guide. But first just try to rebuild the mac80211 package;

-download and unzip the mac80211-8.0.2 compressed folder for whose link I posted above.
-in the terminal;

cd Where_the_unzipped_folder_is/mac80211-8.0.2
sudo make patch_kernel
sudo modprobe mac80211


Good luck

If that doesn't work for you, you might try running

```
sudo aptitude reinstall linux-headers-2.6.22-8 linux-headers-2.6.22-8-generic
```

 (substituting your kernel version of course)

Then trying it again to make sure you are patching a clean unpatched version of the source. That seemed to work fine for me

---

### Post by ehmdjii on 2007-07-18
it works now! thank you very much!

---

### Post by ubnachete on 2007-07-18
I'm using mac80211 on its latest 8.x version, and iwl 0.36, as 0.1.1 doesn't even compile with 2.6.22 kernel. It works fine, except WPA, which doesn't work at all, anyone having the same trouble?

---

### Post by ubnachete on 2007-07-18
Nevermind what I said, just restarted the laptop, reentered the key, Gnome asked me for the key ring, and right now I'm writing this with a WPA connection. For further information, I'm using an Asus F3sv, iwl version 0.0.36 and mac80211 8.0.2. Any mac80211 9.0.x causes system to freeze.

---

### Post by Curio on 2007-07-19
Also my thanks for this really helpfull guide.

I followed this guide exactly and all was going without an error. My Ubuntu find now the wlan-module.

But I cant use WPA. When I go to "Network -> Wlan -> Options" i can only find WEP. The first time I got a massage that the wlan-module is compiled for the 2.6.22-8-generic kernel and that's why not all funktions are available. (My system starts with the new kernel)

Now I have updated "wireless-tools" and "wpasupplicant" from the gutsy-sources. But the problem is the same.

What can I do to have the possibility to use WPA2?

Excuse me please for my bad English. I hope you understand my problem.
My System: Dell notebook XPS 1710, Intel Core Duo 2 T7400, 2048MB DDR2, Ubuntu 7.04 on an external usb-drive.

Curio

---

### Post by cacycleworks on 2007-07-19
> **Curio said:**
> Also my thanks for this really helpfull guide.
But I cant use WPA. When I go to "Network -> Wlan -> Options" i can only find WEP. The first time I got a massage that the wlan-module is compiled for the 2.6.22-8-generic kernel and that's why not all funktions are available. (My system starts with the new kernel)
Curio


Hi Curio, I suggest researching NetworkManager. I had the same problem on my old laptop and took me forever to figure that out. In kubuntu, it is knetworkmanager and is typically the same icon in the system tray... no connection is a box with a red x at the bottom. With wired, it's like a cable plugged in. Wireless has the 4 bars indicating signal strength. Right-click on that icon to see more.

I spent hours trying to figure out wireless when it was there in the system tray all along!

:) Chris

ps - scribbling notes for my Dell D630 with the intel 4965. I'm tired of the 35' patch cord!!

---

### Post by iammeagain on 2007-07-21
i used this to install the newest everything when i did, which was only a week or two ago. It didnt work and i installed the ndiswrapper, and i have no boot or shut down problems. I find that strange i wish i could explain it better. But i don't really know all that i did. It does take a while to initiate the card once its booted up. But it works.

---

### Post by pem725 on 2007-07-21
iammeagain,

When you say you installed the "newest everything," do you mean you tried to compile the latest version of mac80211?  If so, I suggest you try the 8.0.X version instead.  If you have happy with the ndiswrapper then there is no need to fuss.  I chose to drop the ndiswrapper approach because my network connect kept dropping out with large file downloads.  With the Intel driver installed, my Lenovo 3000 v200 is rock solid (minus the little wifi light but that is a minor inconvenience). 

Submit another post to this thread if you would like some help with the Intel driver.

---

### Post by keirnna on 2007-07-22
I installed 2.6.22-8-generic. I get the following errors with both mac80211-9.0.X and mac80211-8.X.X:

```
geralyn@geralyn-laptop:~$ cd mac80211-9.0.2/
geralyn@geralyn-laptop:~/mac80211-9.0.2$ sudo make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
Applying patches and scripts from pending/.
 + Applying: pending/0001-mac80211-add-WE-range-name-and-rate-capabilities.patch
        From ca19fa17bfd9a34cd1e9445b4124fd5b66302e51 Mon Sep 17 00:00:00 2001
 + Applying: pending/0002-mac80211-Fix-user-specified-TXPOWER-from-being-over.patch
        From e914351da4334d7eb18ac1516a108556167a288e Mon Sep 17 00:00:00 2001
 + Applying: pending/0003-mac80211-fix-SIOGIWRATE-return-value.patch
        From 84e36289e4002f8944ade738211875ad4dd0604a Mon Sep 17 00:00:00 2001
 + Applying: pending/0004-mac80211-HT-IEEE_802.11n_TX_AMPDU-send-actframes.patch
        From 7fd05ee99c41e2dcc72f6622b783c4856cdd13c0 Mon Sep 17 00:00:00 2001
 + Applying: pending/0005-mac80211-HT-add-IEEE-802.11n-TX_AMPDU-API.patch
        From 3fd40cc5feac8ed7fe1a85c3a32bf96e2664b4a4 Mon Sep 17 00:00:00 2001
 + Applying: pending/0006-mac80211-HT-add-TX-AMPDU-MLME-data.patch
        From ba2b967594ad6858cea5b1326a44b4ff28d2718c Mon Sep 17 00:00:00 2001
 + Applying: pending/0007-mac80211-HT-IEEE-802.11n-TX-AMPDU-MLME-implementa.patch
        From ec565ab4b9d490dd5554c12936afdbdd9c99dd69 Mon Sep 17 00:00:00 2001
 + Applying: pending/0008-mac80211-HT-IEEE-802.11n-debugfs-support.patch
        From b0b06902885fbc03afbeebb83bc6dfb14b441c62 Mon Sep 17 00:00:00 2001
 + Applying: pending/0009-mac80211-HT-IEEE-802.11n-block-ack-support.patch
        From 0fa31a29d10406e0ee7a35651899028c6454434b Mon Sep 17 00:00:00 2001
 + Applying: pending/0010-mac80211-HT-IEEE-802.11n-block-ack-debugfs-suppor.patch
        From 12ec6dab4bf95266d74ce8cbd3114145f3e2d709 Mon Sep 17 00:00:00 2001
 + Applying: pending/0011-mac80211-HT-add-IEEE-802.11n-qos-queues.patch
        From 0e687081d063e4ea7892452d21205cb9e6341094 Mon Sep 17 00:00:00 2001
 + Applying: pending/0012-mac80211-HT-IEEE-802.11n-RX-aggregation-BAR-supor.patch
        From b02bb0b0826a006b75d5664dffcfeeca60202ddf Mon Sep 17 00:00:00 2001
 + Applying: pending/0013-mac80211-HT-IEEE-802.11n-RX-aggregation-API-and-M.patch
        From 04b12bb5ad75ff065c1c979484c160850e60fd17 Mon Sep 17 00:00:00 2001
 + Applying: pending/0014-mac80211-HT-add-addtional-type-parameter-for-ieee.patch
        From a29e1fe44ea1d66ff3cd6e37be1f359987793db8 Mon Sep 17 00:00:00 2001
 + Applying: pending/0015-mac80211-HT-fix-ieee80211_send_addba_resp-interfa.patch
        From 955ebbec76af4730f5bcf494977069383726a4dc Mon Sep 17 00:00:00 2001
 + Applying: pending/0016-mac80211-HT-fix-master-mode-net-type.patch
        From b12e2fb2c3219801db7bc441dcd91a97c8f06203 Mon Sep 17 00:00:00 2001
 + Applying: pending/0017-mac80211-HT-IEEE-802.11n-RX-aggregation-MLME-supp.patch
        From 7f34da900318f6a8f660b2d7efab30867ce43b0c Mon Sep 17 00:00:00 2001
 + Applying: pending/0018-mac80211-HT-IEEE-802.11n-RX-aggregation-debugfs-s.patch
        From b0b7b8a1fa6a5099c45e0cf15121843f047efab3 Mon Sep 17 00:00:00 2001
 + Applying: pending/0019-mac80211-HT-AP-mode-block-ack-MLME-support.patch
        From b64beebbb58e81ac927903709dbf30c2783aeb4f Mon Sep 17 00:00:00 2001
 + Applying: pending/0020-mac80211-HT-AP-mode-association-support.patch
        From 01d8e6194118b41e3b3f6cbfd7927ae770bfd0ee Mon Sep 17 00:00:00 2001
 + Applying: pending/0021-mac80211-HT-fix-wrong-param-used-for-ieee80211_ht.patch
        From 4c8ada3d263332c7ff2d13638b07f63eb8a3b8f4 Mon Sep 17 00:00:00 2001
 + Applying: pending/0022-mac80211-HT-use-KERN_DEBUG-for-HT-debugging-messa.patch
        From e7f39f46ee0bb8d59ecf05cf27c5e494e7ad9377 Mon Sep 17 00:00:00 2001
 + Applying: pending/0023-mac80211-rssi-averaging-filter.patch
        From 6cc13e67fa40f8172ff1d66c83cbe54116122881 Mon Sep 17 00:00:00 2001
 + Applying: pending/0024-mac80211-add-802.11h-channel-switch-packet-handling.patch
        From ac91953cea3c9f379608617d75afed877f979e6e Mon Sep 17 00:00:00 2001
Checking kernel compatibility in:
        /lib/modules/2.6.22-8-generic/source//
grep: /lib/modules/2.6.22-8-generic/source//drivers/base/core.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires device_rename compat
   - Requires ilog2 compat
Building compatibility version in 'compatible/' directory:
Copying compatible/ from modified/...done
 + Running: ilog2.sh
        IEEE80211_STYPE_QOS_DATA's mask is 0x0080
Patching from compatible/ to /lib/modules/2.6.22-8-generic/source/:
 + Copied 4 files.
 + Replaced 56 files.
Checking for required kernel build updates...
 - checking net/Kconfig and net/Makefile...
 - checking net/core/Makefile for old 'wireless'...
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_process_ioctl v. wext_handle_ioctl...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for linxu/wireless.h v. net/wext.h...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/Makefile and Kconfig for old 'd80211'...
 - checking drivers/net/wireless/Kconfig...
Done.

NOTE:  As of mac80211-2.0.0, kernel built-ins for the wireless extension 
handlers have been replaced with built-ins provided by mac80211.  This 
requires you to rebuild your main kernel image and reboot to that 
kernel in order to use the mac80211 subsystem.  We are looking for ways 
to correct this in the future.

Patching from patches/ to /lib/modules/2.6.22-8-generic/source/:
Checking kernel compatibility in:
        /lib/modules/2.6.22-8-generic/source//
 * Kernel supports required features for 'modified' version.
geralyn@geralyn-laptop:~/mac80211-9.0.2$ sudo make install

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

make: *** No rule to make target `install'.  Stop.

```

I would greatly appreciate any help!

---

### Post by Scotty562 on 2007-07-22
Thanks for this guide. I ended up figuring out what I did wrong. I was using a neiwer version of iwlwifi-0.0.xx. I downloaded iwlwifi-0.0.35 and used that and things worked perfectly!

keirnna:

Did you try mac80211-8.0.x yet? It looked like you used mac80211-9.0.2.

---

### Post by keirnna on 2007-07-22
> **Scotty562 said:**
> Thanks for this guide. I ended up figuring out what I did wrong. I was using a neiwer version of iwlwifi-0.0.xx. I downloaded iwlwifi-0.0.35 and used that and things worked perfectly!

keirnna:

Did you try mac80211-8.0.x yet? It looked like you used mac80211-9.0.2.

Yes as I said in my post I tried 8.0.x. I tried it first. Got the errors, so I decided to give 9.0.x a try. Both gave the same result.

---

### Post by Hisstareia on 2007-07-23
I had the same errors when I was compiling, but from the looks of it you'll be fine to continue on without problem. Also, once you run "make patch_kernel", no "make install" has to be run. Just continue to install iwlwifi and iwl4965 as the instructions say and report back with any issues.

> **keirnna said:**
> I installed 2.6.22-8-generic. I get the following errors with both mac80211-9.0.X and mac80211-8.X.X:

```
geralyn@geralyn-laptop:~$ cd mac80211-9.0.2/
geralyn@geralyn-laptop:~/mac80211-9.0.2$ sudo make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
Applying patches and scripts from pending/.
 + Applying: pending/0001-mac80211-add-WE-range-name-and-rate-capabilities.patch
        From ca19fa17bfd9a34cd1e9445b4124fd5b66302e51 Mon Sep 17 00:00:00 2001
 + Applying: pending/0002-mac80211-Fix-user-specified-TXPOWER-from-being-over.patch
        From e914351da4334d7eb18ac1516a108556167a288e Mon Sep 17 00:00:00 2001
 + Applying: pending/0003-mac80211-fix-SIOGIWRATE-return-value.patch
        From 84e36289e4002f8944ade738211875ad4dd0604a Mon Sep 17 00:00:00 2001
 + Applying: pending/0004-mac80211-HT-IEEE_802.11n_TX_AMPDU-send-actframes.patch
        From 7fd05ee99c41e2dcc72f6622b783c4856cdd13c0 Mon Sep 17 00:00:00 2001
 + Applying: pending/0005-mac80211-HT-add-IEEE-802.11n-TX_AMPDU-API.patch
        From 3fd40cc5feac8ed7fe1a85c3a32bf96e2664b4a4 Mon Sep 17 00:00:00 2001
 + Applying: pending/0006-mac80211-HT-add-TX-AMPDU-MLME-data.patch
        From ba2b967594ad6858cea5b1326a44b4ff28d2718c Mon Sep 17 00:00:00 2001
 + Applying: pending/0007-mac80211-HT-IEEE-802.11n-TX-AMPDU-MLME-implementa.patch
        From ec565ab4b9d490dd5554c12936afdbdd9c99dd69 Mon Sep 17 00:00:00 2001
 + Applying: pending/0008-mac80211-HT-IEEE-802.11n-debugfs-support.patch
        From b0b06902885fbc03afbeebb83bc6dfb14b441c62 Mon Sep 17 00:00:00 2001
 + Applying: pending/0009-mac80211-HT-IEEE-802.11n-block-ack-support.patch
        From 0fa31a29d10406e0ee7a35651899028c6454434b Mon Sep 17 00:00:00 2001
 + Applying: pending/0010-mac80211-HT-IEEE-802.11n-block-ack-debugfs-suppor.patch
        From 12ec6dab4bf95266d74ce8cbd3114145f3e2d709 Mon Sep 17 00:00:00 2001
 + Applying: pending/0011-mac80211-HT-add-IEEE-802.11n-qos-queues.patch
        From 0e687081d063e4ea7892452d21205cb9e6341094 Mon Sep 17 00:00:00 2001
 + Applying: pending/0012-mac80211-HT-IEEE-802.11n-RX-aggregation-BAR-supor.patch
        From b02bb0b0826a006b75d5664dffcfeeca60202ddf Mon Sep 17 00:00:00 2001
 + Applying: pending/0013-mac80211-HT-IEEE-802.11n-RX-aggregation-API-and-M.patch
        From 04b12bb5ad75ff065c1c979484c160850e60fd17 Mon Sep 17 00:00:00 2001
 + Applying: pending/0014-mac80211-HT-add-addtional-type-parameter-for-ieee.patch
        From a29e1fe44ea1d66ff3cd6e37be1f359987793db8 Mon Sep 17 00:00:00 2001
 + Applying: pending/0015-mac80211-HT-fix-ieee80211_send_addba_resp-interfa.patch
        From 955ebbec76af4730f5bcf494977069383726a4dc Mon Sep 17 00:00:00 2001
 + Applying: pending/0016-mac80211-HT-fix-master-mode-net-type.patch
        From b12e2fb2c3219801db7bc441dcd91a97c8f06203 Mon Sep 17 00:00:00 2001
 + Applying: pending/0017-mac80211-HT-IEEE-802.11n-RX-aggregation-MLME-supp.patch
        From 7f34da900318f6a8f660b2d7efab30867ce43b0c Mon Sep 17 00:00:00 2001
 + Applying: pending/0018-mac80211-HT-IEEE-802.11n-RX-aggregation-debugfs-s.patch
        From b0b7b8a1fa6a5099c45e0cf15121843f047efab3 Mon Sep 17 00:00:00 2001
 + Applying: pending/0019-mac80211-HT-AP-mode-block-ack-MLME-support.patch
        From b64beebbb58e81ac927903709dbf30c2783aeb4f Mon Sep 17 00:00:00 2001
 + Applying: pending/0020-mac80211-HT-AP-mode-association-support.patch
        From 01d8e6194118b41e3b3f6cbfd7927ae770bfd0ee Mon Sep 17 00:00:00 2001
 + Applying: pending/0021-mac80211-HT-fix-wrong-param-used-for-ieee80211_ht.patch
        From 4c8ada3d263332c7ff2d13638b07f63eb8a3b8f4 Mon Sep 17 00:00:00 2001
 + Applying: pending/0022-mac80211-HT-use-KERN_DEBUG-for-HT-debugging-messa.patch
        From e7f39f46ee0bb8d59ecf05cf27c5e494e7ad9377 Mon Sep 17 00:00:00 2001
 + Applying: pending/0023-mac80211-rssi-averaging-filter.patch
        From 6cc13e67fa40f8172ff1d66c83cbe54116122881 Mon Sep 17 00:00:00 2001
 + Applying: pending/0024-mac80211-add-802.11h-channel-switch-packet-handling.patch
        From ac91953cea3c9f379608617d75afed877f979e6e Mon Sep 17 00:00:00 2001
Checking kernel compatibility in:
        /lib/modules/2.6.22-8-generic/source//
grep: /lib/modules/2.6.22-8-generic/source//drivers/base/core.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires device_rename compat
   - Requires ilog2 compat
Building compatibility version in 'compatible/' directory:
Copying compatible/ from modified/...done
 + Running: ilog2.sh
        IEEE80211_STYPE_QOS_DATA's mask is 0x0080
Patching from compatible/ to /lib/modules/2.6.22-8-generic/source/:
 + Copied 4 files.
 + Replaced 56 files.
Checking for required kernel build updates...
 - checking net/Kconfig and net/Makefile...
 - checking net/core/Makefile for old 'wireless'...
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_process_ioctl v. wext_handle_ioctl...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for linxu/wireless.h v. net/wext.h...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-8-generic/source/net/core/dev.c: No such file or directory
 - checking net/Makefile and Kconfig for old 'd80211'...
 - checking drivers/net/wireless/Kconfig...
Done.

NOTE:  As of mac80211-2.0.0, kernel built-ins for the wireless extension 
handlers have been replaced with built-ins provided by mac80211.  This 
requires you to rebuild your main kernel image and reboot to that 
kernel in order to use the mac80211 subsystem.  We are looking for ways 
to correct this in the future.

Patching from patches/ to /lib/modules/2.6.22-8-generic/source/:
Checking kernel compatibility in:
        /lib/modules/2.6.22-8-generic/source//
 * Kernel supports required features for 'modified' version.
geralyn@geralyn-laptop:~/mac80211-9.0.2$ sudo make install

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

make: *** No rule to make target `install'.  Stop.

```

I would greatly appreciate any help!

---

### Post by keirnna on 2007-07-23
Okay so I got this to work. It turns out that the build-essential linux-headers didn't have all of their dependendecies met, so this fixed that after adding the two gusty repositories back:

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

That upgraded about 10 packages. Then I tried the install instructios with:

[B]iwlwifi-4965-ucode-4.44.17
iwlwifi-0.1.2
mac80211-8.0.2[/B]

It failed and gave me errors when I tried to make and make install **iwlwifi-0.1.2** so I downloaded **iwlwifi-0.0.42** and everything worked. 

Thanks for the great instructions and help everyone! I really need to study up on all of this.

---

### Post by bluesky3368 on 2007-07-26
> **rye_ said:**
> 
6. installation of the packages adapted from Zoltan's Blog (credit goes to him);

sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source



by me there is a erro.

huan@suo:~$ sudo ln-s/usr/src/linux-headers-2.6.22-8-386/lib/modules/2.6.22-8-386/source
sudo: ln-s/usr/src/linux-headers-2.6.22-8-386/lib/modules/2.6.22-8-386/source: command not found

has anyone this problem ?

ths a lot

---

### Post by abadfish on 2007-07-26
> **rye_ said:**
> 1. add a reference to the gutsy sources for the installation of the 2.6.22-7-generic kernel.
(I'm told the most recent kernel is changing frequently; look for the most recent kernel and substitute 
any references within the guide to 2.6.22-7-generic with that most recent you are using)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

(graphically the above can be added via system->administation->sources add the line exactly as it is)

or alternatively via the terminal, copy and paste the above sources into the following file.

sudo gedit /etc/apt/sources.list


2 install the following; (kernel and sources), after having updated the sources.
(substitute '2.6.22-7-generic' with the most recent kernel)

linux-image-2.6.22-7-generic
linux-headers-2.6.22-7-generic



Okay, when i did this part, I put the gutsy sources in my list and used the system update manager to get the latest linux-image-2.6.22-X-generic and linux-headers-2.6.22-X-generic.  The version that came up was 2.6.20 instead of 2.6.22.

what did I do wrong??  How can I get the 2.6.22 version??


Also, intellinuxwireless.org has 3 versions of iwlwifi:
0.1.4
1.0.0
0.1.3

which one should be used????  I'm guessing it should be 1.0.0 because that's what their site calls the latest even though 0.1.4 has a later build time.

---

### Post by rye_ on 2007-07-26
blueky3368,

your missing spaces in  the command.  it may be difficult to see in the font this website but just highlight and copy into the terminal the command.  as an aside the terminal functions similarly to a programming like say python/ruby, in that spaces allow the terminal to discern the difference between functions and the variables it requires to function.  

abadfish,

a few weeks two 'strands' of the project seemed to occurr (I'm not sure, but without trying I'm tempted to speculate that the 0.x strand is intended to integrate with 9.xx mac module branch, and the x.0.0 goes stably with the stable 8.x.x mac module.)

my (and other's advice) is stick with the 8.x.x mac module, and use the 1.0.0 iwlwifi package.
however try them as you fancy, I found the 0.x.x iwlwifi wouldn't even 'make' for me.

Ryan

---

### Post by abadfish on 2007-07-26
any insight as to why I couldn't get the 2.6.22 version of the kernel????

---

### Post by victorgreen on 2007-07-28
I cant believe I didnt find this thread before! Ive been pulling out my hair trying to make wifi work on my new x61 and just concluded today that it couldnt be done. Intel driver version 1.0.0 caused a kernel disaster that prevented boot. I had to plug the hdd into another computer and blacklist the module. 

Thanks for the tip on using the new Gutsy kernel. Duh!! In retrospect it was obvious.

---

### Post by dracomordag on 2007-07-28
sudo modprobe iwl4965

returns: 

FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-8-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by abadfish on 2007-07-28
I got wireless working.  But it came at a price.  When I booted the new kernel (2.6.22), my sound card stopped working.  When I try to access the the volume control, I get a message "No volume control GStreamer plugins and/or devices found."   When I boot back to a previous version (with the GRUB screen), the sound card works.  I'm guessing that something is missing with the new kernel but I don't know what.  I tried loading a buttload of GStreamer packages to no avail.

Any ideas??

---

### Post by StratosL on 2007-07-28
Hi there, thanx for the thread. 

I'm going to try it now with an Acer Aspire 5920G (intel 4965agn, intel T7300, nvidia 8600m GT).

Just a quick trivial note: in point 6, there should be a "sudo" before

```
cp iwlwifi-4965.ucode /lib/firmware/$(uname -r)
```

---

### Post by StratosL on 2007-07-28
The situation at IntelLinuxWireless.org is a little confusing. It would be nice if they could sort out a couple of "sets" of files to use together.

I tried various combinations and the one that seems to work for me is:

kernel 2.6.22-8-generic
mac80211-8.0.2
iwlwifi-1.0.0
iwlwifi-4965-ucode-4.44.17

I can connect to my network using WPA(1)-PSK.

As mentioned before, mac 9.0.x seems to be the development branch for "n" networks.
ucode 4.44.18 did not work for me
When I first used iwlwifi-1.0.0, after reboot the touch pad did not respond, but that was fixed using the keyboard shortcut keys
YMMV

Not quite perfect yet, though. Downloads seem to be coming in "bursts", meaning that every few seconds it seems to pause for a few seconds and then continue... ideas, anyone? Maybe I should check the driver's bug reporting site.

---

### Post by dracomordag on 2007-07-28
> **StratosL said:**
> 
kernel 2.6.22-8-generic
mac80211-8.0.2
iwlwifi-1.0.0
iwlwifi-4965-ucode-4.44.17
yea, this one is perfect, btw.

---

### Post by cacycleworks on 2007-07-28
> **abadfish said:**
> I got wireless working.  But it came at a price.  When I booted the new kernel (2.6.22), my sound card stopped working.
Any ideas??

What I've learned from my Dell D630 is that I need alsa_hd_audio ( or is the word intel in there??). I got my 1440x900 resolution going now and sound is my next step. THEN I work on the wireless. I've got wires anywhere I go, so wireless isn't required at this moment for me.

Anyhow, knowing the hardware is an amazing thing. The output of lspci is amazing. The driver won't match what the hardware is or the pci address will be wrong. Curiously, lspci says my wireless is 3945... so lspci may simply report what the drivers think your hardware is. :P

If you find something in that, please let me know.

---

### Post by victorgreen on 2007-07-29
> **dracomordag said:**
> yea, this one is perfect, btw.

Thank you so much for the guide, Rye. I thought I was just going to have to do without until they released a more stable driver or when gutsy comes out in October. The same config that worked for the two posters above worked for me too on a Thinkpad X61. I can connect to anything, wpa personal works great.

kernel 2.6.22-8-generic
mac80211-8.0.2
iwlwifi-1.0.0
iwlwifi-4965-ucode-4.44.17

---

### Post by mattmueller on 2007-07-31
This is amazing...after spending hours last night trying to get wireless to work I finally found this guide and in no time *poof* wireless is working correctly.

The only problem is that I no longer have sound after making this work....I assume that might be due to the new kernel or something?  Any ideas?

I like the guy above am on a Dell, Latitude D830....I assume sound is provided by Intel.

---

### Post by cacycleworks on 2007-07-31
Aw man, I'm jealous... are you using the "normal" 32 bit i386 or 64bit "AMD" / generic install?

For the sound... from everything I've read, you need the snd_hda_intel module to load in the kernel. I'm trying to get to where I can just compile a kernel. I'm also looking in to remastering the install cd to include things like snd_hda_intel and not have the other sound devices.

Here are 2 D630 thread here in the forums (may be of interest to your D830):
  [http://ubuntuforums.org/showthread.php?t=481651](http://ubuntuforums.org/showthread.php?t=481651)
  [http://ubuntuforums.org/showthread.php?t=513204](http://ubuntuforums.org/showthread.php?t=513204)
  

Here's an interesting page with some info for Dells:
 [http://linux.dell.com/wiki/index.php/Ubuntu_7.04](http://linux.dell.com/wiki/index.php/Ubuntu_7.04)
and specifically:
 [http://linux.dell.com/wiki/index.php/Tech/Audio](http://linux.dell.com/wiki/index.php/Tech/Audio)

Please keep us updated. :) Oh, are you using i915 video? or did it work 1440x900 upon install? 

:) chris

---

### Post by AlbinoButt on 2007-07-31
When I try to make mac80211, I get the following error:

```
Kernel Makefile not found at '/lib/modules/2.6.22-9-generic/source/'
```

Also, after upgrading the kernel my FN brightness controls stopped working (Vaio VGN-TZ90HS Laptop)

Please help!

---

### Post by cacycleworks on 2007-07-31
> **AlbinoButt said:**
> When I try to make mac80211, I get the following error:

```
Kernel Makefile not found at '/lib/modules/2.6.22-9-generic/source/'
```

Also, after upgrading the kernel my FN brightness controls stopped working (Vaio VGN-TZ90HS Laptop)

Please help!

There are a few packages you'll need to get in order to compile the kernel... 
Searching found me this: [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel)
... which looks VERY good.
... also links to: [http://www.kroah.com/lkn/](http://www.kroah.com/lkn/)



I formerly was using this:
 [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
... which didn't really work for me. I have yet to actually succeed. 

:)

---

### Post by AlbinoButt on 2007-07-31
Thanks, cacycleworks. I found out what the problem was, which was that when I typed in the following,

```
sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source
```

The symbolic link was already there, so it wasn't replaced. I had to type in

```
sudo rm /lib/modules/$(uname -r)/source
```

and then remake the link for it to work.

The wireless connection is listed now, but I can't choose WPA under the Network Settings for some reason, as someone else stated earlier in this thread. (I have to turn roaming mode on and then select Connect to Other Wireless Network, but then I can't configure my manual IP address/DNS/etc :( ).

And my FN brightness keys still don't work (Sony VGN-TZ90HS). :)

---

### Post by cacycleworks on 2007-07-31
> **AlbinoButt said:**
> The only thing left to fix are my FN brightness keys (Sony VGN-TZ90HS). :)


OH! I forgot to mention that, sorrry! There is an option in the menuconfig for Sony acpi. I suspect it could be fixed with that ??? It is buried in the ACPI area (I think.....).

I have a Sony SZ220 and a Dell D630. The Sony is pretty good... just fixed a long timeout delay during startup by changing networking to S99 in the startup scripts.

---

### Post by AlbinoButt on 2007-07-31
I almost got wireless working, but here are the problems. (Computer is a Sony Vaio Laptop VGN-TZ90HS)

[LIST=1]
[*]I don't know if it was the kernel upgrade or the wireless driver, but my system is running like molasses. Launching applications takes about 30 seconds when it used to take 1.
[*]I can't connect to WPA networks. I can only choose WEP unless I pick "Roaming Mode", but then I can't specify my static IP/DNS/etc settings. I'm currently trying to see if [this thread]("http://ubuntuforums.org/showthread.php?t=512647") can help me.
[*]The kernel upgrade has messed up my FN keys. I tried running make menuconfig with no success.
[*]Sound no longer works!
[/LIST]

:confused:

---

### Post by mattmueller on 2007-07-31
@cacycleworks

I'm using the 32bit version, had to use the alternate cd in fact to install.

Sound I'm still working on, will have a look at those threads you mentioned a bit later, thanks for your help.

Oh and I got the nvidia quadro nvs card (128mb) with the wuxga screen...took me a bit to get it working correctly (in the end using envy first and then customizing x config worked out pretty well)...now running happily at 1920x1200

---

### Post by vronp on 2007-08-01
Ryan,

Great job.  I finally got around to trying this and everything is working pretty well so far.

I accidently upgraded to Gutsy across the board though.  I added the repositories for the kernel and then forgot about it.

A couple nights later, I was half asleep when I noticed a ton of updates waiting for me.  Stupidly, I accepted the updates and the next morning realized what I had done.

Long story short, I went 100% gutsy and then followed your instructions.  Wireless is working now with my 4965 card in a Dell Inspiron 9400 laptop.

I have noticed that the WiFi led on my laptop doesn't light up.  This is a minor irritation.

I will start doing some testing with the Fn-key switch and see what happens.  I'll also test with WPA and WEP.

Thanks again Ryan !

Dave

---

### Post by Hisstareia on 2007-08-02
Good News Everybody!!!

kernel 2.6.22.9 has this module preinstalled! In the latest kernel right now with no fuss. Just uncomment the gutsy lines in your sources.list and download the latest kernel.

---

### Post by _0D_0A on 2007-08-02
> **dracomordag said:**
> sudo modprobe iwl4965

returns: 

FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-8-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Same here, trying to use the driver provided by the 2.6.22-9-kernel for Gutsy. dmesg returns:
iwl4965: Unknown symbol ieee80211_start_BA_session

I'm running Kubuntu Feisty x86_64. I'd love getting rid of ndiswrapper!

---

### Post by golem3 on 2007-08-02
> **Hisstareia said:**
> Good News Everybody!!!

kernel 2.6.22.9 has this module preinstalled! In the latest kernel right now with no fuss. Just uncomment the gutsy lines in your sources.list and download the latest kernel.

Can someone confirm the latest Gutsy daily build has instant support for 4965

---

### Post by o3rat on 2007-08-02
Thanks for the guide! Now I have finally have the wireless running on my d630.

Unfortunately now my sound doesnt work. If anyone has and ideas i would appreciate it.

---

### Post by cacycleworks on 2007-08-02
> **o3rat said:**
> Thanks for the guide! Now I have finally have the wireless running on my d630.

Unfortunately now my sound doesnt work. If anyone has and ideas i would appreciate it.

There's a D630 thread here:
 [http://ubuntuforums.org/showpost.php?p=3116123&postcount=80](http://ubuntuforums.org/showpost.php?p=3116123&postcount=80)

:D

Currently about to compile 2.6.22.1 for my D630 and then try to install the wireless driver. As it turns out, I'm not sure if my Dell has the 3945 or the 4965. :P

---

### Post by pem725 on 2007-08-03
For those of you who are experiencing errors, can you please provide us with a checklist of what steps you followed from the guide and results of those steps?  Your feedback will help us improve the guide as well as troubleshoot the iwl4965 driver limitations.  Thanks.

---

### Post by Scotty562 on 2007-08-03
Feisty users may enjoy this thread. The script in this thread updates the kernel to the latest gutsy kernel. The drivers that this thread provides are incorporated into this kernel. It's just a different way of fixing the same problem. I found it to be much less stressful.

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by pem725 on 2007-08-03
Scotty562,

Thanks for the thread link.  Yes, the drivers are included in the kernel but I believe they are an older snapshot of the intel (almost) daily release.  If you want to see some of the problems resolved such as the lights then I suggest users opt for the latest versions as directed through the guide in this thread.

---

### Post by jrzlaw on 2007-08-04
First I would like to thank Rye for the Thread. It has solved my problems. Wireless is up and Working. :guitar:


I would also like to thank Hisstareia and Scotty562 for their info. That was key to my success!!!

I used Scotty562 post to update my kernel. I originally planned to use his script. However, I decided to use his manual instructions.

I followed Ryans installation for the intel drivers and used Hisstareia info to fix some issues and Bamm!!! worked like magic. My wireless is rock solid.

My only problem caused by these steps is my vmware server doesn't work. Tried to re-install but no luck. I guess I will have to search to find a solution for that.

Nevertheless I'm pleased to have wireless. Once again thanks. I love Ubuntu.  I just need to tackle sound and vmware and I'm there.

---

### Post by digeratess on 2007-08-07
Thanks for these instructions. Without this thread, I would've had absolutely no clue how to begin getting this new wireless to work.

I followed the instructions and got no errors other than the one about the shell not being set to bash. Everything seems to have completed properly; however, my wireless still doesn't seem to be detected at all. Based on the HOWTO at intellinuxwireless.com, I also did

```
ifconfig wlan0 up
```

That results in

```
wlan0: ERROR while getting interface flags: No such device
```

A few notes that might be relevant:
[LIST]
[*]I have rebooted.
[*]I did reboot after applying the new kernel, so all changes were applied to the new kernel.
[*]I have double-checked the wireless on/off switch position.
[*]I'm running Kubuntu Feisty.
[*]KNetworkManager will not start.
[*]My laptop is an HP DV6565 and has Intel 4965 wireless.
[*]I used mac80211-8.0.2, iwlwifi-0.1.8 and iwlwifi-4965-ucode-4.44.17
[/LIST]

I'm completely at a loss as to what to try to have the wireless detected. Any help would be much appreciated.

---

### Post by tturk on 2007-08-08
I don't know if anyone else is having the same problem, but it's been a while since iwl4965 drivers worked perfectly for me as long as I connect directly through the command line using both WEP and WPA access points and killing the nm-applet and NetworkManager processes, but whenever I use NetworkManager, it only stays connected for a while and get disconnected afterwards, then it struggles to connect again.

Using wpa_supllicant directly is rock solid tho, I could be hours connected without glitches. Today there's a new network-manager update in gutsy, and I'm connected using it right now, so I hope they've fixed it and doesn't lost the connection.

---

### Post by jb1789 on 2007-08-08
> 9 Hours Ago 11:19 PM
digeratess 	
Re: guide for using iwl4965 for intel 4965 agn WIFI card
Thanks for these instructions. Without this thread, I would've had absolutely no clue how to begin getting this new wireless to work.

I followed the instructions and got no errors other than the one about the shell not being set to bash. Everything seems to have completed properly; however, my wireless still doesn't seem to be detected at all. Based on the HOWTO at intellinuxwireless.com, I also did

Code:

ifconfig wlan0 up

That results in

Code:

wlan0: ERROR while getting interface flags: No such device

A few notes that might be relevant:

    * I have rebooted.
    * I did reboot after applying the new kernel, so all changes were applied to the new kernel.
    * I have double-checked the wireless on/off switch position.
    * I'm running Kubuntu Feisty.
    * KNetworkManager will not start.
    * My laptop is an HP DV6565 and has Intel 4965 wireless.
    * I used mac80211-8.0.2, iwlwifi-0.1.8 and iwlwifi-4965-ucode-4.44.17


I'm completely at a loss as to what to try to have the wireless detected. Any help would be much appreciated.



I had the same problem as you, until I used the newer iwlwifi-1.0.0 in place of iwlwifi-0.1.8.  I would also suggest that you do the following instead of the last step of the guide,
> 
sudo rmmod iwl4965 mac80211
sudo modprobe mac80211
sudo modprobe iwl4965


(The first statement removes the modules if they were already loaded.)

---

### Post by cacycleworks on 2007-08-08
The intel site's instructions were really confusing to me. :( Turns out, I don't have the 4965, but also a few "simple" things in the logs completely prevented the wireless on my Dell to work. Check out my troubleshooting here to see if it applies to the other new Intel-based PCI chipsets: [http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

Also about the bash thing....
cd /bin
ls -al *sh*
sudo rm sh to remove the link to dash...

... and make a new one to bash.
sudo ln -s bash sh

:)

---

### Post by feistybill on 2007-08-09
Thanks to this thread I was able to get the 4965 working on my Acer Travelmate 6292 with Kubuntu 7.04. However, I can't get Kismet to work. I tried using "source=iwl4965,wlan0,wlan0" in kismet.conf but it looks like iwl4965 is not recognized as a valid module :-k Can anyone offer any advice please?

---

### Post by digeratess on 2007-08-10
Thanks so much again for this thread. I'm posting this from my wireless connection. For everyone else out there working on their wireless, here's exactly what worked for me:

Kubuntu Fiesty
kernel (from Gutsy) 2.6.22-9
mac80211-8.0.2
iwlwifi-1.0.0
iwlwifi-4965-ucode-4.44.17
128-bit WEP
all command-line config using iwconfig. When I use kNetworkManager on my wireless interface, I get the system freeze and blinking caps lock.

man iwconfig was extremely helpful as was the HOWTO at intellinuxwireless.com.

I'm using an HP dv6565.

FWIW, I was also having fits with the graphics on this machine and had been working on different drivers for that too. I stopped before I ever got X to load and decided to get wireless done first. As soon as I upgraded to the Gutsy kernel and rebooted, X started loading and I've had no problems with graphics, no banding like others talk about. My sound is not working, but I have not even worked on it.

---

### Post by Hisstareia on 2007-08-11
> **ehmdjii said:**
> does anyone with the capslock crash have any news yet?

i am still stuck with this. the card seems to work, but as soon as i try to connect to a network i get the capslock crash. :(

Try using mac80211-8.0.2 from the website. I got the same problem when I tried using the mac80211-9.*.* version.

---

### Post by jeremy215 on 2007-08-14
Hi, I noticed there might be a problem when you enable 64bit Hex WEP, this is when my Toshiba A205 crashes/freezes.  When I disable the WEP and just leave it unsecure I don't have any problems at all.

---

### Post by Hisstareia on 2007-08-14
Just to tell everyone, Intel has finally posted the 1.0 linux drivers on their support website:
> [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2753&DwnldID=10315&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2753&DwnldID=10315&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)
It can be built the same way as the guide says, so if you're having trouble with getting the development versions to work or are having connection issues with the dev builds, it's probably worth a shot. I'm using it to post but I haven't seen any major improvements from older versions as of yet. Will keep you posted and I'll see if it fixes the occasional disconnect I'm having.

---

### Post by Guyver1 on 2007-08-15
ok had a problem modprobeing the iwl :

```

guyver1@m9750:~$ sudo mkdir /lib/firmware/$(uname -r)
Password:
guyver1@m9750:~$ sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source
guyver1@m9750:~$ cd /home/guyver1/mac80211-8.0.2/
guyver1@m9750:~/mac80211-8.0.2$ sudo make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
Applying patches and scripts from pending/.
 + Applying: pending/09-range-name-rate-but-no-channel.patch
        diff -urp origin/include/net/mac80211.h test/include/net/mac80211.h
 + Applying: pending/10-txpower.patch
        Fix user specified TXPOWER from being overridden by stack.
 + Applying: pending/11-iwlist-channel.patch
        From: Hong Liu <hong.liu@intel.com>
 + Applying: pending/30-fixup-giwrate.patch
        Fix SIOGIWRATE so it actually returns the most recent rate *or* highest
 + Applying: pending/99-mainline-2.6.23-fix.patch
        Add three patches from upstream 2.6.22-rc7 GIT.
Checking kernel compatibility in:
        /lib/modules/2.6.22-9-generic/source//
grep: /lib/modules/2.6.22-9-generic/source//drivers/base/core.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires device_rename compat
   - Requires ilog2 compat
Building compatibility version in 'compatible/' directory:
Copying compatible/ from modified/...done
 + Running: ilog2.sh
        IEEE80211_STYPE_QOS_DATA's mask is 0x0080
Patching from compatible/ to /lib/modules/2.6.22-9-generic/source/:
 + Copied 44 files.
 + Replaced 12 files.
Checking for required kernel build updates...
 - checking net/Kconfig and net/Makefile...
 - checking net/core/Makefile for old 'wireless'...
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-9-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_process_ioctl v. wext_handle_ioctl...
grep: /lib/modules/2.6.22-9-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for linxu/wireless.h v. net/wext.h...
grep: /lib/modules/2.6.22-9-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-9-generic/source/net/core/dev.c: No such file or directory
 - checking net/Makefile and Kconfig for old 'd80211'...
 - checking drivers/net/wireless/Kconfig...
Done.

NOTE:  As of mac80211-2.0.0, kernel built-ins for the wireless extension 
handlers have been replaced with built-ins provided by mac80211.  This 
requires you to rebuild your main kernel image and reboot to that 
kernel in order to use the mac80211 subsystem.  We are looking for ways 
to correct this in the future.

guyver1@m9750:~/mac80211-8.0.2$ cd /home/guyver1/iwlwifi-1.0.0-1/
guyver1@m9750:~/iwlwifi-1.0.0-1$ sudo make install
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'. Stop.
guyver1@m9750:~/iwlwifi-1.0.0-1$ make SHELL=/bin/bash
Checking kernel compatibility in:
        /lib/modules/2.6.22-9-generic/source
 * Kernel supports required features for 'tip' version.
Building compatibility version in 'compatible/' directory:
Copying compatible/ from origin/...done
make -C /lib/modules/2.6.22-9-generic/source O=/lib/modules/2.6.22-9-generic/build M=/home/guyver1/iwlwifi-1.0.0-1/compatible/ modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-9-generic'
  CC [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/base-3945.o
  CC [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl-3945.o
  CC [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl-3945-rs.o
  CC [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/base-4965.o
  CC [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl-4965.o
  CC [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl-4965-rs.o
  LD [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl3945.o
  LD [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl4965.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl3945.mod.o
  LD [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl3945.ko
  CC      /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl4965.mod.o
  LD [M]  /home/guyver1/iwlwifi-1.0.0-1/compatible/iwl4965.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-9-generic'
guyver1@m9750:~/iwlwifi-1.0.0-1$ cd /home/guyver1/iwlwifi-4965-ucode-4.44.1.18/
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ cp iwlwifi-4965.ucode /lib/firmware/$(uname -r)
cp: cannot stat `iwlwifi-4965.ucode': No such file or directory
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ ls
iwlwifi-4965-1.ucode  LICENSE.iwlwifi-4965-ucode  README.iwlwifi-4965-ucode
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ cp iwlwifi-4965-1.ucode /lib/firmware/$(uname -r)
cp: cannot create regular file `/lib/firmware/2.6.22-9-generic/iwlwifi-4965-1.ucode': Permission denied
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ sudo cp iwlwifi-4965-1.ucode /lib/firmware/$(uname -r)
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ sudo modprobe mac80211
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ sudo modprobe iwl4965
FATAL: Module iwl4965 not found.
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ sudo modprobe iwl4965-1
FATAL: Module iwl4965_1 not found.
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ ls
iwlwifi-4965-1.ucode  LICENSE.iwlwifi-4965-ucode  README.iwlwifi-4965-ucode
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ cp iwlwifi-4965-1.ucode /lib/firmware/$(uname -r)
cp: cannot create regular file `/lib/firmware/2.6.22-9-generic/iwlwifi-4965-1.ucode': Permission denied
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ sudo cp iwlwifi-4965-1.ucode /lib/firmware/$(uname -r)
guyver1@m9750:~/iwlwifi-4965-ucode-4.44.1.18$ cd /lib/firmware/
guyver1@m9750:/lib/firmware$ ls
2.6.20-15-generic  2.6.20-16-generic  2.6.22-9-generic
guyver1@m9750:/lib/firmware$ cd 2.6.22-9-generic/
guyver1@m9750:/lib/firmware/2.6.22-9-generic$ ls
iwlwifi-4965-1.ucode
guyver1@m9750:/lib/firmware/2.6.22-9-generic$ sudo modprobe i
Display all 204 possibilities? (y or n)
guyver1@m9750:/lib/firmware/2.6.22-9-generic$ sudo modprobe iw_c
iw_c2     iw_cm     iw_cxgb3  
guyver1@m9750:/lib/firmware/2.6.22-9-generic$ sudo modprobe iwlwifi-4965-1.ucode iwlwifi-4965-1.ucode 
FATAL: Module iwlwifi_4965_1.ucode not found.
guyver1@m9750:/lib/firmware/2.6.22-9-generic$ 

```

any help on this would be appreciated

cheers

---

### Post by ntaylor0909 on 2007-08-15
That worked great for me. Thanks.

The upgrade to the new kernel broke a couple of other things though. The sound stopped working on my Dell Latitude D630, and vmware server has started giving this error every time I try to start a virtual machine:
Unable to change virtual machine power state: The process exited with an error:
End of error message.

Any help would be appreciated.

Thanks.

---

### Post by cacycleworks on 2007-08-16
> **ntaylor0909 said:**
> That worked great for me. Thanks.

The upgrade to the new kernel broke a couple of other things though. The sound stopped working on my Dell Latitude D630, and vmware server has started giving this error every time I try to start a virtual machine:
Unable to change virtual machine power state: The process exited with an error:
End of error message.

Any help would be appreciated.

Thanks.

Did you check the post I made above? Sounds just like what I faced for a while...

---

### Post by kkjaergaard on 2007-08-17
I'm sorry to say this, but it doesn't work for me. I does not seem to have any effect. I did as you wrote, but it does not work.

---

### Post by qfb_ros on 2007-08-17
Hello!

Thanks for the great post.  I have a SONY VAIO VGN-CR160F.  I followed the step to install the Wifi Intel 4965 card and it all went well.  The card detects networks in the Network Manager Applet, but when I click on the network I want to connect, it shows the "Wireless network key required" window, I put on the correct password and nothing happens, it does not connect to the wireless network.  Even if I disable security password to the network, it wont connect.

Have I done something wrong?

Thank you for your help!

---

### Post by ntaylor0909 on 2007-08-17
@cacycleworks

I hadn't checked what you wrote. It looks like you had to go through a lot to get it working. I think I will probably live with no wifi for another 2 months and wait for gutsy. Thanks for the help.

---

### Post by rye_ on 2007-08-19
not to dissuade anyone from using this guide, as quite soon the used software and modules will be very stable; but for those unsuccessful with this guide, or finding the cyclic  download pattern of the iwl4965 module irritating, ndiswrapper may be an alternative.

download ndiswrapper version 1.48 test version (not 1.47), with the latest windows driver and the connection should be ok.  One proviso, if after a few minutes your connection goes down, just select the wireless applet and your wifi connection to re-connect for a stable connection.

Ryan

---

### Post by mrpurple on 2007-08-19
when You say the lastes windows driver .. You intend the XP driver or what ?

---

### Post by rye_ on 2007-08-19
yes, the latest XP driver.
(But I would still encourage everyone to keep their eye on the iwl4965 progression).

---

### Post by mrpurple on 2007-08-20
sure and i still working on it, but i'm a newby of linux, and i try yesterday night but for some strange reason the kernel doesn't update. after passage 1 when i have the list of updates but the two you indicate are not selectable. so i think to have update all. 
tonight i'll work on it.
thank you again

---

### Post by mrpurple on 2007-08-22
WOW !!!! i just follow the steps 1, 2, 3, and after step 4 i was already connected nothing to do more lastes kernel is 2.6.22-10-generic.
there is a note to do. in step 3 i did all the upgrade and update that i had not only kernel linux. 
thank You so much !! :guitar:

---

### Post by exoren22 on 2007-08-23
Well, as I type this I am connected wirelessly through the gutsy kernel as installed by the script here: [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
I haven't had a single wireless dropout since I booted into the new kernel, and I am very pleased. I am on a completely clean xubuntu x86_64 edgy system, with the 6.22-10 kernel and network-manager installed, so I still have tinkering to do, but I am downloading updates via aptitude now, so thanks for this thread!

---

### Post by biosckon on 2007-08-27
Ubuntu 7.04 (updated) and kernel 2.6.22-10  on
Fujitsu S6410 Core2Duo, 2Gb, video Intel x3100, wifi Intel 4965

wifi is working thanks to the guide author
:guitar:

---

### Post by newt256 on 2007-08-30
Thanks for the guide!! As I followed it, I didn't get any errors, so I'm thinking it worked fine, but I don't have a wireless network nearby to test it. One thing that concerns me is that the only adapters that show up when I run ifconfig are eth0 and lo. Is this normal? I'm on an X61 running 2.6.22.10-generic.
Thanks in advance.

---

### Post by newt256 on 2007-08-31
So, four hours later and one hell of a lot of reading, I figured it out. As I said, no wifi adapter showed up, my card reader stopped working, no removable devices would receive power, and there was no sound. I read the instructions on [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) (simple kernel upgrade) and just completed the kernel upgrade (installed linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic). I rebooted and suddenly all my problems went away!! Everything works! (well, not everything, but all I really care about)

yay!

---

### Post by vronp on 2007-08-31
Hi,

I think you should be showing a wlan device.

I am running the same kernel here.

---

### Post by hippomofatumas on 2007-09-02
ive been trying to tget this to work for a while. im running 7.10 tribe 5, wireless is only thing not working.

im trying this howto/guide but when im in my iwlwifi directory/folder and i try to run make i get this:

chris@ubuntuchris:~/Desktop/iwlwifi-0.1.14$ make
Makefile:22: 
Makefile:23: WARNING: $SHELL not set to bash.
Makefile:24: If you experience build errors, try
Makefile:25: 'make SHELL=/bin/bash'.
Makefile:26: 
Kernel Makefile not found at '/lib/modules/2.6.22-10-generic/source'
chmod: cannot access `compatible/*': No such file or directory
/bin/sh: cannot create compatible/kversion: Directory nonexistent
-e 
Makefile has been modified by generate_compatible, please run `make' again

make: *** [compatible/kversion] Error 1


and i did everything up until that point ok i think. please help me out. i dont know if this has been answered in this forum yet, 11 pages can be a lot to read. thanks.

---

### Post by vronp on 2007-09-03
Did you do:

make SHELL=/bin/bash


????

---

### Post by StratosL on 2007-09-03
> **rye_ said:**
> not to dissuade anyone from using this guide, as quite soon the used software and modules will be very stable; but for those unsuccessful with this guide, or finding the cyclic  download pattern of the iwl4965 module irritating, ndiswrapper may be an alternative.

download ndiswrapper version 1.48 test version (not 1.47), with the latest windows driver and the connection should be ok.  One proviso, if after a few minutes your connection goes down, just select the wireless applet and your wifi connection to re-connect for a stable connection.

Ryan

So, the "cyclic download pattern" was not just me!!!
Any news on that front, anyone?

Has anyone successfully tried the newer versions (other than 1.0.1)?

---

### Post by vronp on 2007-09-04
I am about to try the latest version.  I should be able to get to it this afternoon and I'll post here after.

But, I have a question.  How does one determine the version of a module ?  It appears that mac80211 is "preinstalled" in the gutsy kernel but how would I determine the version of mac80211 ???

thanks

> **StratosL said:**
> So, the "cyclic download pattern" was not just me!!!
Any news on that front, anyone?

Has anyone successfully tried the newer versions (other than 1.0.1)?

---

### Post by hippomofatumas on 2007-09-06
yeah i tried make shell = bash.

i tried updating mac80211 but got the same kernel makefile error. i think maybe something is messed up in my kernel. but i havent tampered with anything. on a clean install, i cant get my wireless to work. iwlwifi/iwl4965 returns no kernel makefile at every turn. and i cant get ndiswrapper to work. but quite frankly i want iwlwifi to work because other ppl with the same computer have got it working, following the same procedures im trying to follow!


poooooooo

---

### Post by aldeby on 2007-09-07
Hi all,
just a note: in **ubuntu gutsy tribe 6 **module mac80211 is already compiled as a kernel module and also already loaded (you can check by yourself by typing ```
lsmod |grep mac80211
```
so there is no need to install it.

installing the iwlwifi drivers you have to pay attention that this command: 
```
sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source
```

outputs several errors even after installing via apt-get the linux-sources:
```
grep: /lib/modules/2.6.22.10-generic/source//drivers/base/core.c: No such file or directory  
(missing file was actually another, but the error should look alike)
```
I checked manually and actually there are no core.c and so on files, obvious since I linked as a soruce only the headers!

you should *[I]**bunzip2 ***[/I]and ***tar xf*** the linux-soruces you find in /usr/src and then changed the symbolic link as follows:

in /lib/modules$(uname -r) you should first delete the old source symlink 
```
sudo del source
```
then make the new one
```
sudo ln -s /usr/src/linux-source-2.6.22.10 /lib/modules/$(uname -r)/source
(obviously change the linux source verion number according to the one you find there)
```

done this commands **make **and **make install** within the iwlwifi folder do not prompt any more errors

hope it helps

cheers

---

### Post by dippy2323 on 2007-09-09
I got a T61 notebook a month ago, and I have had a lot of problems getting the wireless to work.  After much work, finally got it running with ndiswrapper, but that crapped out a week ago when I installed some linux updates and restarted.  Even booting into older kernels wouldn't help.

It was recommended that I get the newest gutsy kernel (as newt256 posted above; I now have 2.6.22.11-generic).  Upon reboot, almost immediately connected to wireless network (90% connectivity near router).  However, I can't connect to any pages, even though iwconfig and my network manager think that i am.  My only guess is the message I get with iwconfig:

"Warning: Driver for device wlan0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20.  Some things may be broken..."

Any ideas?  I am new to linux after being annoyed with vista not working...

---

### Post by frenchcr on 2007-09-10
What sofware do you all use to locate available networks ??

All i know is wifi radar...any others or better?

---

### Post by hippomofatumas on 2007-09-12
aldeby could you please be more specific on the bunzip2 and tar stuff? everything out is laid out in copy and paste format, just that stuff i dont really know how to do unless written out exactly. im so excited it sounds like you have the fix for my problem exactly. yay!

---

### Post by aldeby on 2007-09-12
hippomofatumas, 
if I don't make a mistake when you install via apt-get the linux-sources this drops in /usr/src directory a file named something like linux-source-2.6.22.10.bz2 this is the linux sources in a compressed format (bzip2). You have to unzip it by typing into the shell
```
sudo bunzip2 linux-source-2.6.22.10.bz2
```
after having issued this command you will find over there a file named like linux-source-2.6.22.10.tar which is the tarball of the sources (you know, before the coming of bzip2, when there was only gzip compression only one file at a time could be handled, so people used to do first wrap the directory/files into a ball (the tarball) and then compress it)
in order to get the directory unwrapped type 
```
sudo tar xf linux-source-2.6.22.10.tar
``` 
at this point you should find a directory named linux-source-2.6.22.10 over there.

please note that the actual number of the kernel source version may change to reflect the current stage of its development.

---

### Post by blinxdk on 2007-09-15
> **dippy2323 said:**
> 
It was recommended that I get the newest gutsy kernel (as newt256 posted above; I now have 2.6.22.11-generic).  Upon reboot, almost immediately connected to wireless network (90% connectivity near router).  However, I can't connect to any pages, even though iwconfig and my network manager think that i am.  My only guess is the message I get with iwconfig:

"Warning: Driver for device wlan0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20.  Some things may be broken..."

Any ideas?  I am new to linux after being annoyed with vista not working...

Check and see if there is a newer wireless-tools package that is build with the same wireless extensions version as your new kernel.

Anyways, being connected but not able to use the connection sounds to me like an IP problem, first check with ifconfig that your wireless interface has been assigned an IP, if it has, check dns, routing and so on.

---

### Post by MickSulley on 2007-09-15
Hi,

I am still having problems getting my wireless connection working.  It all seems to go OK down to 6) then I get - 

mick@mick-laptop:~/WiFi Drivers Temp/iwlwifi-0.1.16$ sudo make install
Password:
Makefile:22: 
Makefile:23: WARNING: $SHELL not set to bash.
Makefile:24: If you experience build errors, try
Makefile:25: 'make SHELL=/bin/bash'.
Makefile:26: 
make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'.  Stop.

I have also tried 'make SHELL=/bin/bash' and that gives - 

mick@mick-laptop:~/WiFi Drivers Temp/iwlwifi-0.1.16$ make SHELL=/bin/bash
make -C /lib/modules/2.6.22-11-generic/source O=/lib/modules/2.6.22-11-generic/build M=/home/mick/WiFi Drivers Temp/iwlwifi-0.1.16/compatible/ EXTRA_CFLAGS="-DCONFIG_IWLWIFI_DEBUG=y -DCONFIG_IWLWIFI_SPECTRUM_MEASUREMENT=y -DCONFIG_IWLWIFI_SENSITIVITY=y -DCONFIG_IWLWIFI_QOS=y" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-11-generic'
make[2]: *** No rule to make target `Drivers'.  Stop.
make[1]: *** [Drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-11-generic'
make: *** [modules] Error 2

I don't know what to do to fix this.  I have a Dell XPS M1710 with a 4965AGN wireless network card.

I am very new to Linux and Ubuntu so please keep any advise down at the idiot level!

Thanks
Mick

---

### Post by siralphred on 2007-09-16
> **dippy2323 said:**
> I got a T61 notebook a month ago, and I have had a lot of problems getting the wireless to work.  After much work, finally got it running with ndiswrapper, but that crapped out a week ago when I installed some linux updates and restarted.  Even booting into older kernels wouldn't help.

It was recommended that I get the newest gutsy kernel (as newt256 posted above; I now have 2.6.22.11-generic).  Upon reboot, almost immediately connected to wireless network (90% connectivity near router).  However, I can't connect to any pages, even though iwconfig and my network manager think that i am.  My only guess is the message I get with iwconfig:

"Warning: Driver for device wlan0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20.  Some things may be broken..."

Any ideas?  I am new to linux after being annoyed with vista not working...

i have exact issue, installed everything correctly on 2.6.22.11- generic but i cannot connect to the internet , i looked at connection information and everything seem correct..ip ...dns..submask etc, someone please help

---

### Post by Proqrammer on 2007-09-16
> **rye_ said:**
> 
2 install the following; (kernel and sources), after having updated the sources.
(substitute '2.6.22-7-generic' with the most recent kernel)

linux-image-2.6.22-7-generic
linux-headers-2.6.22-7-generic

I'm sorry this may look too silly but how do we do that?
I have a Toshiba Satellite A205-S4639 and I'm using

2.6.20-16-generic

I'm stock on this level
I also can't find "system->administation->sources" there is no sources in my system-> administration

I just edited the file as you have ordered.

I also tried to update my ubuntu with the two following commands:
sudo apt-get update
sudo apt-get upgrade

It downloaded some stuff from gusty too..

Thanks

---

### Post by MickSulley on 2007-09-16
It works!!!!

I went through it all again (several times) and it seemed to install correctly at last and I had a wireless network option in Networks, but then I could not connect.  After searching loads of other forums I installed wicd and managed to connect.

Many thanks for providing this guide, it took me two days to get it to work with this, without it I would never have got there!

Thanks

Mick

---

### Post by wheezart on 2007-09-16
You have to install the Gutsy repos in Synaptic Package Manager, located in **System>Administration>Synaptic Package Manager **(if you're using Ubuntu and not Kubuntu) There you have the **Settings>Repositories** menu, and under **Third-Party Software**, add the

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

lines and continue following step 1. I strongly advise you to get through the entire post, since there are a lot of details you have to be careful about, that are mentioned later on. Good luck dude! \\:D/

---

### Post by Proqrammer on 2007-09-16
> **wheezart said:**
> You have to install the Gutsy repos in Synaptic Package Manager, located in **System>Administration>Synaptic Package Manager **(if you're using Ubuntu and not Kubuntu) There you have the **Settings>Repositories** menu, and under **Third-Party Software**, add the

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

lines and continue following step 1. I strongly advise you to get through the entire post, since there are a lot of details you have to be careful about, that are mentioned later on. Good luck dude! \\:D/

Thanks for your reply
In Synaptic Package Manager, when I click on Settings > repositories it seems to refresh something and then it doesn't show any window or something, so I can't see **Third-Party Software** anywhere, where is that?

I guess it should show something like this => [http://www.debianadmin.com/images/syn/5.png](http://www.debianadmin.com/images/syn/5.png) but it doesn't what's the problem?

---

### Post by wheezart on 2007-09-16
It should look like this [IMG]http://i11.tinypic.com/62oggud.png[/IMG]... try restarting it might fix it. Otherwise you'll have to do 

**sudo gedit /etc/apt/sources.list**

and paste the two lines in the bottom, and proceed to step 2 =)

---

### Post by wheezart on 2007-09-16
By the way, can someone please help me with my problem [here]("http://ubuntuforums.org/showthread.php?t=552565"). It's directly connected to this thread, but i'm just very :confused: !

When i try to connect using ndiswrapper, wicd stops connecting at "obtaining IP address" when using DHCP, and with a static IP it connects, but it says "connected to None at 0%" (Meaning 0% signal strenght). GtkWiFi does the same as well... please help!

---

### Post by Proqrammer on 2007-09-16
Hey,
I'm trying to do this
> 
cd DIRECTORY_WHICH_CONTAINS_/iwlwifi-0.0.xx
make
sudo make install

and I get this error:> 
nicolas@nicolas-laptop:~/drivers/iwlwifi-0.0.32$ make
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
Kernel Makefile not found at '/lib/modules/2.6.22-11-386/source'
make: *** [compatible/kversion] Error 1
nicolas@nicolas-laptop:~/drivers/iwlwifi-0.0.32$ sudo makeMakefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
Kernel Makefile not found at '/lib/modules/2.6.22-11-386/source'
make: *** [compatible/kversion] Error 1
nicolas@nicolas-laptop:~/drivers/iwlwifi-0.0.32$ sudo make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.22-11-386/source'
make: *** [compatible/kversion] Error 1
nicolas@nicolas-laptop:~/drivers/iwlwifi-0.0.32$ 

And by the way your ubuntu looks cool dude how did you get that skin?

---

### Post by hippomofatumas on 2007-09-17
keep getting same problem. hadnt tried downloading linux-source and it seemed like that would work, but something still isnt right. maybe im screwing up. but it shouldnt be this hard lol. i shouldve just gotten the 3945! draft-n crap.

---

### Post by siralphred on 2007-09-17
good job ..finally got it working,.. but like someone mentioned i had to install WICD to get it work so for those who get the wireless signal but cannot logon to any website should try to install WICD a good instructions can be found here, i recommend using the manual method and restarting after installing thats how mine worked on SONY AR520 [http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

---

### Post by StratosL on 2007-09-24
I can confirm that using gutsy and since kernel version 2.6.22-12 the intel 4965agn wifi card is working perfectly out of the box.

---

### Post by rye_ on 2007-09-29
I can also confirm this.

---

### Post by frenchcr on 2007-09-29
**LOOKS LIKE THIS THREAD IS GOING OBSOLETE **

mines works too, just did gutsy upgrades from last 24 hours (gutsy beta release software in repos)...during updates gutsy configured it, wasnt working previously...now wifi radar finds all networks in the area for the first time since i got this laptop.

GOOD WORK dev's !!!!

see sig for platform

---

### Post by Netrunner on 2007-10-02
hello everyone, i've got hands on an acer aspire 5920g of a friend, he told me to put ubuntu on it.
installed gutsy.
i can't get the speakers (virual surroundsound) speak but the jak works, and neither the wireless work.
Speaking of the wireless, after following the howto when i do:
sudo modprobe iwl4965

it says 

FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-12-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

kernel is 2.6.22-12-generic
mac80211 is 10.0.0
iwlwifi is 1.1.17

dmesg:
[  837.459107] iwl4965: Unknown symbol ieee80211_stop_BA_session
[  837.459236] iwl4965: Unknown symbol ieee80211_start_BA_session
[ 1116.964839] iwl4965: Unknown symbol ieee80211_stop_BA_session
[ 1116.964966] iwl4965: Unknown symbol ieee80211_start_BA_session


anyone can help?
guess i have to try older versions of iwlwifi
hope it works

---

### Post by frenchcr on 2007-10-04
youve got the sound muted thats all. go into sound and enable front and surround the shove the volume up.

gutsy updates will fix the wireless.

---

### Post by Rikiji on 2007-10-05
Thank you thank you for the guide, it solved my problem! :KS

---

### Post by vronp on 2007-10-06
> **StratosL said:**
> I can confirm that using gutsy and since kernel version 2.6.22-12 the intel 4965agn wifi card is working perfectly out of the box.

Guys,

Can you help me out?  I am getting:

FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-13-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

This is with the latest versions of the stuff on the iwlwifi site.

I am running Gutsy 2.6.22-13-generic and things are not running out of the box for me.  I wonder if I screwed something up with the 4965 install procedure.

How would I back out all my changes so I can just try the Gutsy "virgin" setup ????

Help !

---

### Post by joetaxpayer on 2007-10-06
I thought I would link this to a post I've commented on over in the development forum.  I guess I am wondering if anyone else can confirm similar results.  I think it is probably not an issue with gutsy, but rather with card compatibility.  

[http://ubuntuforums.org/showthread.php?p=3485860#post3485860](http://ubuntuforums.org/showthread.php?p=3485860#post3485860)

---

### Post by vronp on 2007-10-06
Hi all,

Can someone tell me the significance of these two driver locations?

./lib/modules/2.6.22-12-generic/kernel/drivers/net/wireless/iwl4965.ko
./lib/modules/2.6.22-12-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko

thanks

---

### Post by atlas95 on 2007-10-06
How to enable de wifi light?

---

### Post by slyboots on 2007-10-08
I am [COLOR="Red"]**using intel 4965 agn WIFI card**[/COLOR] (latest kernel of **[COLOR="Red"]Kubuntu gutsy with integrated driver v1.1.0[/COLOR]**) in my Dell Latitude D630. Wifi work with the latest kernel 2.6.22-13,

 but it [COLOR="Red"]**need too much time to connect to the AP**[/COLOR], and often won't connect the first time or disconnect after some times and try to connect after them (this occurring only sporadically).

AP (Access point) is ok. Other PCs with other cards work ok. When i connect with the Intel 4965 to other AP -> i have same issue.

Previously i thought that is possible issue by the network manager, but on other pc with other wla card and newest network manager all work ok. I will upgrade manualy the firmware from [http://intellinuxwireless.org/?n=downloads&f=ucode&p=iwlwifi](http://intellinuxwireless.org/?n=downloads&f=ucode&p=iwlwifi) but i don't now if it work then or if i have any other wey to solve it.

[COLOR="Red"]**Many thanks for possible advice by solving the issue**[/COLOR]. ;)

[COLOR="SeaGreen"]**SOLUTION:**[/COLOR]

If you using hiden SSID it is possible that the time by connecting is too long, but the issue is with the driver v 1.1.0. caused too.

I have used this guide to install the newest:

[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)

that [COLOR="SeaGreen"]works without issues.[/COLOR]

---

### Post by Nunslaughter on 2007-10-08
i upgraded yesterday to gutsy beta with kernel 2.6.22-13 and the card works...one thing only, the wifi led on my dell xps m1710 doesn't light up...

---

### Post by ZenithUK on 2007-10-20
I've read a number of threads about enabling the 4965 chipset wifi (including this thread) and they all come down to the same thing.

Get the drivers from intellinuxwireless.org

My problem is that I simply can't access the site.  I've tried a number of computers and they all report unable to load the site.  I tried the ndiswrapper route and that didn't work out well for me so I'm kind of stuck right now.

[edit] After checking my computer and router, it comes down to my ISP's DNS servers.  Sorry for bothering you. :)

---

### Post by tturk on 2007-10-21
For the past weeks is working perfectly with the ones included in Ubuntu Gutsy Gibbon, no need to download and compile it anymore, not for me at least.

---

### Post by oniltonmaciel on 2007-10-22
tturk:

Mine is working too, but doesn't seem stable, I think everytime I change the wifi button of my laptop to off I can't not get any connection again until I reboot my system.

Is everything working good for you?

---

### Post by tturk on 2007-10-22
> **oniltonmaciel said:**
> tturk:

Mine is working too, but doesn't seem stable, I think everytime I change the wifi button of my laptop to off I can't not get any connection again until I reboot my system.

Is everything working good for you?

It depends on the access point, I have two at home and one of them is unstable and keeps reconecting all the time, the other one is rock solid tho. Some weeks ago I was only able to stablish a stable connection through the command line (using iwconfig and/or wpa_supplicant) because NetMonitor was always disconnecting constantly but it's been a while since NM started working ok.

Try connecting to another access point and try disabling networkmanager and using the comand line tools. Hope that this helps.

---

### Post by showe1966 on 2007-11-22
i have a smsung x65 which has additional problems involving the invidia graphics card and i think possibly something else relating to the dual core processor.
i have an older kernel, as the network card was not detected with the newer kernel and so far, the patch and ndiswrapper did not work and causes a bad system hang.

Anyway, I will now try the gutsy kernel upgrade trick and report back on results.

---

### Post by showe1966 on 2007-11-22
erm vis a vis my last post it doesn't work.
the system hangs whilst booting with the error "failed to allocate resource region 8 of bridge" when the new kernel is used.
Does anyone have a solution to this problem ??
I might just try using the 86 kernel rather than the generic one and see what happens:-

here is what i did:-


Edit /etc/apt/sources.list:-

sudo gedit /etc/apt/sources.list
save original sources.list as sources.list.old

add new references to gutsy kernel:-

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

save file and then get the new kernel and source:-

sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release [65.9kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages [1075kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages [7664B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages [4065kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages [158kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources [306kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources [2120B]
Fetched 5680kB in 28s (198kB/s)
Reading package lists... Done

apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image - Generic Linux kernel image.
linux-image-2.6.22-14-386 - Linux kernel image for version 2.6.22 on i386
linux-image-2.6.22-14-generic - Linux kernel image for version 2.6.22 on x86/x86_64
linux-image-2.6.22-14-server - Linux kernel image for version 2.6.22 on x86/x86_64
linux-image-2.6.22-14-virtual - Linux kernel image for version 2.6.22 on x86
linux-image-386 - Linux kernel image on 386.
linux-image-debug-2.6.22-14-386 - Linux kernel debug image for version 2.6.22 on i386
linux-image-debug-2.6.22-14-generic - Linux kernel debug image for version 2.6.22 on x86/x86_64
linux-image-debug-2.6.22-14-server - Linux kernel debug image for version 2.6.22 on x86/x86_64
linux-image-debug-2.6.22-14-virtual - Linux kernel debug image for version 2.6.22 on x86
linux-image-debug-386 - Linux kernel debug image for 386 kernel image
linux-image-debug-generic - Linux kernel debug image for generic kernel image
linux-image-debug-server - Linux kernel debug image for server kernel image
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image geared towards virtualised hardware
linux-image-2.6.22-14-rt - Linux kernel image for version 2.6.22 on RT kernel
linux-image-2.6.22-14-ume - Linux kernel image for version 2.6.22 on Ubuntu Moblie and Embedded
linux-image-2.6.22-14-xen - Linux kernel image for version 2.6.22 on This kernel can be used for Xen dom0 and domU
linux-image-debug-ume - Linux kernel debug image for ume kernel image
linux-image-rt - Linux kernel image on realtime kernel
linux-image-ume - Linux kernel image on 386 Embedded/Mobile
linux-image-xen - Linux kernel image on Xen
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
virtualbox-ose-modules-2.6.22-14-generic - virtualbox-ose modules for linux-image-2.6.22-14-generic
virtualbox-ose-modules-2.6.22-14-server - virtualbox-ose modules for linux-image-2.6.22-14-server
xen-image-2.6.19-4-generic - Linux 2.6.19 image on PPro/Celeron/PII/PIII/P4
xen-image-2.6.19-4-server - Linux xen 2.6.19 image on x86.
linux-image-2.6.15-26-386 - Linux kernel image for version 2.6.15 on 386.

latest version seems to be 2.6.22-14 therefore:-

sudo apt-get install linux-image-2.6.22-14-generic linux-headers-2.6.22-14-generic
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.1 gcc gcc-4.1 gcc-4.1-base gcc-4.2-base libc6 libc6-i686 libgcc1 libncurses5 libstdc++6
  linux-headers-2.6.22-14
Suggested packages:
  binutils-doc cpp-doc gcc-4.1-locales gcc-multilib manpages-dev autoconf automake1.9 libtool flex bison gcc-doc
  gcc-4.1-multilib gcc-4.1-doc glibc-doc linux-doc-2.6.22 linux-source-2.6.22
Recommended packages:
  libmudflap0-dev lilo
The following packages will be REMOVED
  build-essential g++ g++-4.0 libc6-dev libncurses5-dev libstdc++6-4.0-dev
The following NEW packages will be installed
  cpp-4.1 gcc-4.1 gcc-4.1-base gcc-4.2-base linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-image-2.6.22-14-generic
The following packages will be upgraded:
  binutils cpp gcc libc6 libc6-i686 libgcc1 libncurses5 libstdc++6
8 upgraded, 7 newly installed, 6 to remove and 878 not upgraded.
Need to get 37.5MB of archives.
After unpacking 106MB of additional disk space will be used.
Do you want to continue [Y/n]? y

packages were installed, but i got multiple warning messages about the languages as follows:-

Setting up linux-headers-2.6.22-14 (2.6.22-14.46) ...
Setting up linux-headers-2.6.22-14-generic (2.6.22-14.46) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").


REMOVE THE CHANGES TO THE SOURCES MADE IN STEP 1

REBOOT.

system hangs during reboot with error message "failed to allocate resource region 8 of bridge"
or something similar.

---

### Post by brundlfly on 2007-12-04
You nailed it for me. I was still working under the false pretense that newer=better. I wrestled with this for several says, pouring through way too many forum threads. I ended up reinstalling Feisty and following the dv9500 tutorial forum:

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

*except* after updating to the gutsy kernel (and included backport updates just in case, for sound. Something I read. Don't ask me) and installing Envy I went straight for the wireless drivers. The latest intel driver versions installed ok but after modprobe no errors, no wireless. 

I went back and reinstalled mac80211-8.0.2 & iwlwifi-0.0.38, but kept the newer iwlwifi-4965-ucode-4.44.17. 

Tada!

Thanks to EXCiD3, Hisstareia, and the community. My new dv9500 never has to see Vista again. :D

---

### Post by showe1966 on 2008-02-08
hi everyone i fixed the problems with my samsung laptop as follows:-

1. Installed from the alternate cd-rom using non-GUI mode
2.The latest kernel picks up the intel wifi no probs.
net time i am on the road i will find out if it works or not and post my findings........

---

### Post by showe1966 on 2008-02-08
oops i forgot to say what it was i installed....I installed gutsy 7.10.
But then i upgraded it from the command line to hardy 8.08 or whatever the version is....

it was only a matter of time till they got the driver sorted........

---

### Post by AegisTalons on 2008-03-20
I have a Dell XPS m1330 with the Intel 4965 AGN card. Currently, it is working, but sometimes I don't get strong connections where other people get a decent connection. I was thinking about trying this and see if it would help. Has anyone tried this guide on a m1330? If it is actually worse than the standard Gutsy install, is there a way to revert back to the previous drivers/delete the installed drivers.

---

### Post by HunterThomson on 2008-03-30
The best way to back up your sys is to partition the hard drive well. This way you can make  a backup of each separate partition. This way making backups is a whole lot ez'r and you can re install just one partition at  a time, or just the one you need to.


I have my 250gb HD partitioned like this. 

Primary partition    /boot 150Mb    ext2
Swap partition       4Gb               swap
Primary partition    /home  150Gb ext3

Then I have a 58Gb free space in the midle by placing the rest of the partitions at the end of free space. This way I have room to expand my /home or /usr partition or make new partitions EZ.

Logical partition     /usr  30Gb    ext3
Logical partition     /   (root) 3Gb ext3
Logical partition     /temp   2Gb  ext3
Logical partition     /var  2Gb      ext3

You can make any standered file in your file system its own partition. like /etc mite be a good one. But disk partition follows the templet established for DOS machines a long time ago at most a disk and hold four primary partitions and you can divide one (and only one) of these primary partitions into multiple logical partitions. This divided primary partitions is called an extended partition. You can divide an IDE/ATA/SATA disk into a maximum of 63 partitions and a SCSI disk into a maximum of 15 partitions.

Also for your driver thing.... I bet you could just uninstall and reinstall the standered ubuntu drivers from synaptic.

I wan't to get a IPWRAW driver for my intel pro/wireless 4965 A/B/G/N. I am going to try the intel 3945 IPWRAW drivers in BackTrack in... 27 min's + ISO CD burning time. I have a    lenovo ideapad y510 1.83Ghz newegg.com were I got it from said it has a 3945 but ubuntu is saying it has a 4965. I bet BIOS would tell me the truth.

---

### Post by AegisTalons on 2008-04-05
I'm trying to install the drivers but I'm having issues. In step 6, I'm having issues patching with mac80211. This is the results from terminal:

```
$ sudo make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Patching from compatible/ to /lib/modules/2.6.22-14-generic/source/:
 + Replaced 56 files.
Checking for required kernel build updates...
 - checking net/Kconfig and net/Makefile...
 - checking net/core/Makefile for old 'wireless'...
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-14-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_process_ioctl v. wext_handle_ioctl...
grep: /lib/modules/2.6.22-14-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for linxu/wireless.h v. net/wext.h...
grep: /lib/modules/2.6.22-14-generic/source/net/core/dev.c: No such file or directory
 - checking net/core/dev.c for wireless_proc_init vs. wext_proc_init...
grep: /lib/modules/2.6.22-14-generic/source/net/core/dev.c: No such file or directory
 - checking net/Makefile and Kconfig for old 'd80211'...
 - checking drivers/net/wireless/Kconfig...
Done.

NOTE:  As of mac80211-2.0.0, kernel built-ins for the wireless extension 
handlers have been replaced with built-ins provided by mac80211.  This 
requires you to rebuild your main kernel image and reboot to that 
kernel in order to use the mac80211 subsystem.  We are looking for ways 
to correct this in the future.


```

Afterwards iwlwifi fails make and consequently fails to install.

Any help will be appreciated.

---

### Post by pandayanyan on 2008-04-16
i am having the same problems as the post above. I am sure it is user error on my part. anyone can help????:(

here is my error:

trickyrick@trickyrick-laptop:~/mac80211-10.0.4$ sudo make SHELL/bash

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

make: *** No rule to make target `SHELL/bash'.  Stop.
trickyrick@trickyrick-laptop:~/mac80211-10.0.4$ make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.22-14-386/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1
trickyrick@trickyrick-laptop:~/mac80211-10.0.4$ pre/
bash: pre/: No such file or directory
trickyrick@trickyrick-laptop:~/mac80211-10.0.4$

---

### Post by sebast on 2008-07-15
I'm having the exact same problem as the above two mentioned posts. I really need this wireless to work and I'm lost in all this now.

```
sebb@sebb-laptop:~/Desktop/mac80211-10.0.4$ make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
Applying patches and scripts from pending/.
 + Applying: pending/0001-mac80211-Add-basic-IEEE-802.11n-support.patch
	From 26e77a5fef845edcb5c27db52f413e7558db0e20 Mon Sep 17 00:00:00 2001
scripts/generate_modified: line 57: patch: command not found
-----patch failure output-----

pending/0001-mac80211-Add-basic-IEEE-802.11n-support.patch failed. Terminating.
If patch or script failed, check pre/ and post/ for current stage.
make: *** [modified] Error 1
```

---

