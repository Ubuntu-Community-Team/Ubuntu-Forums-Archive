---
title: "Getting wireless working in Gutsy Thinkpad T61 Intel 4965AGN"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by NigelHarrison on 2007-10-23
I have recently got a new Thinkpad T61, and waited for Gutsy final, mainly as it was said (here and elsewhere) to include kernel support for the Intel 4965AGN wireless card.  Installation (alternate CD, then loaded restricted support for nvidia graphics) went as expected, and nearly everything works as expected.  But the wireless network card didn't, although the iwl4965 module to support it is loaded.  The wireless applet thing shows up, but displays a 0% connection (to an Access Point two metres away).

Now, here's the strange thing: I then fetched the -server kernel image from the repository, rebooted into it, and, as if by magic, the wireless card is working correctly.

Is the -generic kernel image different from the -server image in some important respect?  Or is there some way I can get the same support for the wireless into the -generic image?

(I should add that I didn't add the support for the nvidia graphics into the -server kernel.

Nigel

---

### Post by John Jason Jordan on 2007-10-25
(I don't know the answer to your question. I have a brand new T61 (Intel 4965) with Gutsy amd64 Desktop and have only occasionally been able to get wireless working. The fact that I can get it working at all tells me that it ought to be possible to get it working all the time, if only I could figure out what makes it work on those few occasions when I have gotten it working.

I should add that the first time I had wireless working the nVidia driver had not yet been installed. But then I installed it and subsequently got wireless working twice. So I don't think the nvidia-glx-new driver is the issue.

I know little of computers and Linux. If I install the -server kernel as you did, will it mess up my existing installation and all the programs I have installed and configured? Your post was two days ago, are you still running the -server kernel and is wireless still working? If anyone else reads this, have you had any problems or experiences with wireless on Intel 4965?

---

### Post by kafo on 2007-10-26
Hi,

I also have a t61 with intel's 4965, lspci output:
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

For me wireless works out of the box. I just select my wireless network and enter the password and I get connected and receive an IP over the DHCP (currently network manager does not support setting a static IP). I am using WPA Personal mode with AES encryption. I have DHCP server enabled on my Linksys WRT54GL wireless router. Also check the wireless switch at the front left of the computer next to the firewire port is set to ON (right position).

I hope you get it working.

Best Regards, Saso

---

### Post by John Jason Jordan on 2007-10-27
> **kafo said:**
> Hi,

I also have a t61 with intel's 4965, lspci output:
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

For me wireless works out of the box. I just select my wireless network and enter the password and I get connected and receive an IP over the DHCP (currently network manager does not support setting a static IP). I am using WPA Personal mode with AES encryption. I have DHCP server enabled on my Linksys WRT54GL wireless router. Also check the wireless switch at the front left of the computer next to the firewire port is set to ON (right position).
Thanks for the reply. Since my original post I also received a reply from a local person who has a Thinkpad T61 with Gutsy. However, like kafo and saso in this thread, he is using 32-bit Gutsy. He has no problem with the wireless.

I have also tried a lot of different things. Gutsy amd64 sees the wireless. If I do "iwlist wlan0 scan" I get a list of available wireless networks. I can even connect to one. But I cannot get a DHCP address from a wireless access point. I can modprobe the iwl4965 driver and it is loaded and running fine. I don't know what the problem is. However, it appears to affect amd64 Gutsy only, so I am transferring this to the 64-bit forum.

---

### Post by NigelHarrison on 2007-10-27
I think you're right, that this is not to do with the installation of the restricted nvidia driver: I have since added it to my -server kernel which still works with iwreless connection correctly.

To answer your specific question, you can install the -server kernel just by choosing it with your package manager (Synaptics, for example).  It installs the kernel image, and adds helpfully an additional entry to your menu.lst file, so the next time you reboot, it shows up in the GRUB list.  None of your existing files are changed (bar the menu.lst, of course).

I'll add some further information from my logs to an additional message in this thread (and I'll go and check the 64-bit forum too).

Thanks for your reply, JJJ.  What's a homorganic excrescence, then?

Nigel

---

### Post by NigelHarrison on 2007-10-27
Hi, kafo

My lspci response is the same as yours.

My home wireless network doesn't use WPA (or WEP), but the list of acceptable MAC addresses is used as a simple access control.

And, yes, I have the switch set to on (and the network manager and wifi applet change to reflect that, and the router sees the connection) but I don't get a valid DHCP IP issued -- I think that is where the problem lies.

I have extracted some log information which I think may be relevant which I'll add to another message on this thread.

Thanks for your help.

Nigel

---

### Post by kafo on 2007-10-27
Just to clarify, I am using 64 bit gutsy, uname -a output:
Linux tinkpad 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I should probably also mention that I still have Vista installed on my machine and have updated it with Lenovo's system update and there were a couple of bios updates since I bought it. Maybe that could also have something to do with it. And I also have Nvidia Quadro NVS 140M and use the restricted driver and have no problems because of it.

---

### Post by NigelHarrison on 2007-10-27
Here's an extract from the debug log:

Oct 27 14:26:55 tpad NetworkManager: <debug> [1193491615.752750] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'GlenRock' 
Oct 27 14:27:01 tpad kernel: [   55.113419] wlan0: Initial auth_alg=0
Oct 27 14:27:01 tpad kernel: [   55.113431] wlan0: authenticate with AP 00:11:09:0e:d2:f0
Oct 27 14:27:01 tpad kernel: [   55.115155] wlan0: RX authentication from 00:11:09:0e:d2:f0 (alg=0 transaction=2 status=0)
Oct 27 14:27:01 tpad kernel: [   55.115163] wlan0: authenticated
Oct 27 14:27:01 tpad kernel: [   55.115168] wlan0: associate with AP 00:11:09:0e:d2:f0
Oct 27 14:27:01 tpad kernel: [   55.167829] wlan0: associate with AP 00:11:09:0e:d2:f0
Oct 27 14:27:01 tpad kernel: [   55.168721] wlan0: RX AssocResp from 00:11:09:0e:d2:f0 (capab=0x421 status=0 aid=1)
Oct 27 14:27:01 tpad kernel: [   55.168730] wlan0: failed to parse AssocResp
[/COLOR]Oct 27 14:27:01 tpad kernel: [   55.236830] wlan0: associate with AP 00:11:09:0e:d2:f0
Oct 27 14:27:01 tpad kernel: [   55.238956] wlan0: RX AssocResp from 00:11:09:0e:d2:f0 (capab=0x421 status=0 aid=1)
Oct 27 14:27:01 tpad kernel: [   55.238962] wlan0: failed to parse AssocResp
Oct 27 14:27:02 tpad kernel: [   55.300243] wlan0: association with AP 00:11:09:0e:d2:f0 timed out

... and I wonder whether the line:

Oct 27 14:27:01 tpad kernel: [   55.168730] wlan0: failed to parse AssocResp

... is a clue.

The debug message is from somewhere in the kernel (it seems).  So where is this?  Is this in the mac80211 code (which is, I think compiled into the kernel)? I presume it does not suggest a problem with the iwl4965 module -- or am I just wrong about that?

Anyway, does anyone have a clue about this?

(And I still do get an apparently correct connection if I reboot to the -server kernel.)

Nigel

---

### Post by NigelHarrison on 2007-10-27
OK, so the only differences between me and you are:

1. I don't have Vista installed: I removed the partition.
2. I haven't updated the BIOS since I got the machine.

I presume I can get to the BIOS update process via the 'ThinkVantage' button process (which is still on the machine)?  If so, I'll give that a try.

Thanks

Nigel

---

### Post by kafo on 2007-10-27
Yes, the line about failing to parse assocResp probably is the clue, because I don't have this:
[   67.885266] wlan0: Initial auth_alg=0
[   67.885278] wlan0: authenticate with AP 00:14:bf:a5:08:9c
[   67.887164] wlan0: RX authentication from 00:14:bf:a5:08:9c (alg=0 transaction=2 status=0)
[   67.887171] wlan0: authenticated
[   67.887177] wlan0: associate with AP 00:14:bf:a5:08:9c
[   67.890708] wlan0: RX AssocResp from 00:14:bf:a5:08:9c (capab=0x411 status=0 aid=1)
[   67.890715] wlan0: associated

Also check you have the correct MAC address configured on the access point, check that you have DHCP server active. The difference is also that I installed from a Live CD and you seem to have used the alternate. Maybe there are some differences between them. I can boot the live CD (in safe graphics mode) and can connect to my router from the live CD, maybe you could also try this. Also, if you have a chance to connect to some other wireless router or access point, try that also.

---

### Post by John Jason Jordan on 2007-10-27
> **kafo said:**
> Yes, the line about failing to parse assocResp probably is the clue, because I don't have this:
[   67.885266] wlan0: Initial auth_alg=0
[   67.885278] wlan0: authenticate with AP 00:14:bf:a5:08:9c
[   67.887164] wlan0: RX authentication from 00:14:bf:a5:08:9c (alg=0 transaction=2 status=0)
[   67.887171] wlan0: authenticated
[   67.887177] wlan0: associate with AP 00:14:bf:a5:08:9c
[   67.890708] wlan0: RX AssocResp from 00:14:bf:a5:08:9c (capab=0x411 status=0 aid=1)
[   67.890715] wlan0: associated

Also check you have the correct MAC address configured on the access point, check that you have DHCP server active. The difference is also that I installed from a Live CD and you seem to have used the alternate. Maybe there are some differences between them. I can boot the live CD (in safe graphics mode) and can connect to my router from the live CD, maybe you could also try this. Also, if you have a chance to connect to some other wireless router or access point, try that also.
I'm still having the same problems with the 4965AGN on my T61. Wireless works occasionally, but most of the time in the network manager GUI applet the drop-down doesn't work, that is, it fails to list available wireless networks (after unchecking Roaming Mode). Yet from a command line "sudo iwlist scan" shows available networks. I can even use "sudo ifconfig wlan0 ap <access address>" and get connected to an access point. But I cannot get a DHCP address except once in a great while. So far I have managed to get connected to a wireless network three times out of probably hundreds of attempts. And one of the times when I was connected I suddenly got disconnected after half an hour or so.

I also just now tried the live DVD just to see if perhaps it was something else in my setup that was causing it. The first time I went into the network manager GUI and disabled Roaming Mode I got a drop-down list of wireless networks. But the second and subsequent times the drop-down box would not drop down. So I know it is not just my installation.

I don't know which debug log you found the "wlan0: failed to parse AssocResp" line in. I probably have it there also, but I'd like to check. Where is the debug list file?

Also, which server modules should I try adding in Synaptic? Or did you guys already figure out that the server modules didn't help?

I can also add that a local person also has a brand new T61 with Gutsy. His wireless is working perfectly out of the box, but he uses the 32-bit version. 

[Off-topic] And Nigel, as a linguistics major I come across some strange terminology from time to time. An excrescence is the insertion of an extra sound in a word, and if it is inserted because you almost have to do so due to the way the mouth works, then it is homorganic. An example is the way most English speakers pronounce "something" with a [p] between the [m] and the [th]. The term sounds so nasty that I love it.

---

### Post by kafo on 2007-10-27
You can get the kernel outputs if you run 'dmesg' in a terminal. At the bottom you should see the output from wlan configuration.

---

### Post by kafo on 2007-10-27
Also, I have roaming mode enabled, if I disable roaming mode wireless doesn't work anymore. That also means that I have to have DHCP server enabled on my wireless router.

---

### Post by NigelHarrison on 2007-10-27
I've replied to JJJ's message 'inline': I hope that's OK.  

JJJ:
I'm still having the same problems with the 4965AGN on my T61. Wireless works occasionally, but most of the time in the network manager GUI applet the drop-down doesn't work, that is, it fails to list available wireless networks (after unchecking Roaming Mode). Yet from a command line "sudo iwlist scan" shows available networks. I can even use "sudo ifconfig wlan0 ap <access address>" and get connected to an access point. But I cannot get a DHCP address except once in a great while. 

Nigel: 
Your experience matches mine mostly.  I have never had an IP address successfully given to this laptop by the wireless router.  The router does see the laptop, the laptop's MAC address is shown at the router, and iwconfig, iwlist show an apparent connection.  No IP address, though.  (And I can also confirm that switching from 'Roaming Mode' doesn't seem to work (I can't get to the expected dialog.)

JJJ:
So far I have managed to get connected to a wireless network three times out of probably hundreds of attempts. And one of the times when I was connected I suddenly got disconnected after half an hour or so.

Nigel:
This doesn't seem good (-: but better than I've had (with -generic kernel).

JJJ:
I also just now tried the live DVD just to see if perhaps it was something else in my setup that was causing it. The first time I went into the network manager GUI and disabled Roaming Mode I got a drop-down list of wireless networks. But the second and subsequent times the drop-down box would not drop down. So I know it is not just my installation.

Nigel:
I will try booting from the live- CD (I don't have the DVD), but I know the graphics card won't be recognised ... I'll let you know.

JJJ:
I don't know which debug log you found the "wlan0: failed to parse AssocResp" line in. I probably have it there also, but I'd like to check. Where is the debug list file?

Nigel:
The file is var/log/debug and you can see it from the desktop from System/Administration/System Log.  I think the same information will be in other logs too.

JJJ:
Also, which server modules should I try adding in Synaptic? Or did you guys already 
figure out that the server modules didn't help?

Nigel:
No, my machine connects wirelessly correctly if I boot to the -server kernel.  to put that kernel on your machine (from the desktop) you can select the linux-image-2.16.22-14-server package (in Synaptic package manager, for instance), and just click on Apply.  The files will be downloaded and applied, and an extra line (probably two, one for the 'Recovery' mode) will be added to your GRUB boot list.  Reboot, and choose the server.  You will not now have the nvidia restricted drivers (although you can then use the Restricted Drivers Manager to add them) or anything else that was compiled into your -generic kernel.

JJJ: I can also add that a local person also has a brand new T61 with Gutsy. His wireless is working perfectly out of the box, but he uses the 32-bit version.

Nigel: Hmmm ...

JJJ:
[Off-topic] And Nigel, as a linguistics major I come across some strange terminology from time to time. An excrescence is the insertion of an extra sound in a word, and if it is inserted because you almost have to do so due to the way the mouth works, then it is homorganic. An example is the way most English speakers pronounce "something" with a [p] between the [m] and the [th]. The term sounds so nasty that I love it.

Nigel:
Thanks for that explanation.  I'm British, and originally from Yorkshire, and I don't pronounce the 'p' sound, but I certainly hear it.  As someone who's been learning French most of my life, I know that it is quite difficult to get people to actually hear how they pronounce words: I was thinking specifically there about the use of dipthongs for single vowel characters.  So thanks for the lession!

---

### Post by NigelHarrison on 2007-10-27
> **kafo said:**
> Yes, the line about failing to parse assocResp probably is the clue, because I don't have this:
[   67.885266] wlan0: Initial auth_alg=0
[   67.885278] wlan0: authenticate with AP 00:14:bf:a5:08:9c
[   67.887164] wlan0: RX authentication from 00:14:bf:a5:08:9c (alg=0 transaction=2 status=0)
[   67.887171] wlan0: authenticated
[   67.887177] wlan0: associate with AP 00:14:bf:a5:08:9c
[   67.890708] wlan0: RX AssocResp from 00:14:bf:a5:08:9c (capab=0x411 status=0 aid=1)
[   67.890715] wlan0: associated

Also check you have the correct MAC address configured on the access point, check that you have DHCP server active. The difference is also that I installed from a Live CD and you seem to have used the alternate. Maybe there are some differences between them. I can boot the live CD (in safe graphics mode) and can connect to my router from the live CD, maybe you could also try this. Also, if you have a chance to connect to some other wireless router or access point, try that also.

That is interesting.  I installed directly from the alternate iso in text mode, because I knew the live CD would have problems with the nvidia graphics card.  I will try to boot to the live CD and see if I get a different result.

Yes, the MAC address is correct, and other machines connect wirelessly using DHCP to this router.  I haven't been able to try with a different AP.  However, I was able to remove access control from the router entirely, and that didn't change things.  (However, I have a feeling that something in the software stack is caching the connection information, and I haven't discovered how to reset any such cache.)

Thanks for your further help: most welcome.

Nigel

---

### Post by John Jason Jordan on 2007-10-27
OK guys, I have it working. While reading another thread someone mentioned a utility called wifi-radar. Previously I had installed kwifi-manager, but I never liked it much. So I installed wifi-radar (it's in synaptic). Then I launched it and voilà! It found all my neighbors woireless networks - I use ethernet and cable myself - but my neighbors are always visible.

Since I can't connect to my neighbors, I went to a local coffee shop. I'm sitting here writing this totally connected via wireless! Yay!

Now, I can't say for sure that it was wifi-radar that did the trick. All I can related is the sequence of events and the result. Looking at the properties for wifi-radar, I note the following dependencies, which must have been installed automatically if they were not already installed:

python
pythoin-gtk2 (>=2.0)
dhcp3-client
wireless-tools
wpasupplicant

Of these dhcp3-client and wireless-tools are the most suspect. I say that because from the command line I could connect to an access point but could never get a DHCP address. So y'all might want to check out those two first.

Now I'm crossing my fingers that it continues to work. And I haven't tested it with the network-manager tool yet either. I was just so excited that I got it working that I had to post here immediately!

---

### Post by kafo on 2007-10-27
Cool. I checked on my machine and all the packages you listed as dependencies are also already installed.

---

### Post by NigelHarrison on 2007-10-28
JJJ:

I'm glad you've got some luck at last ... but this doesn't work for me.  I already had wifi-radar installed, and it did already locate my Access Point, but no IP address lease could be obtained.  I do like that particular front-end to the network tools.  However, network-manager already depends on dhcp3-client and wpasupplicant, and I therefore expect that you already had both of these libraries installed.  I don't, offhand, know what else has a dependency on the wireless-tools library, but I expect one of the other tools does.  So, please do let us know your continuing findings, so we can properly tie this thing down.

Thanks

Nigel

---

### Post by NigelHarrison on 2007-10-28
JJJ:

Further to my recent message, I also have the gtkwifi applet loaded, and it depends on the wireless-tools library, so I think I already had all the items you listed installed.

Nigel

---

### Post by John Jason Jordan on 2007-10-28
> **NigelHarrison said:**
> JJJ:Further to my recent message, I also have the gtkwifi applet loaded, and it depends on the wireless-tools library, so I think I already had all the items you listed installed.l
Nigel,

As I write this I am at the airport, where I have been connected to the airport network for the past half hour. The connection is  not the speediest (not enough bandwidth for the number of users), but I didn't have any trouble connecting. That is, it took wifi-radar almost a full minute to get a DHCP address, but afterwards it is fine. 

I can add that if I open the GUI network manager tool and click on Properties for the wireless, then uncheck Roaming Mode, the button to display wireless networks still usually fails to drop down. That is even right now when I am connected to flypdx.com. 

This all leads me to the conclusion that the wireless is fine, the drivers are fine, but there is some kind of bug in the way network-manager works. I think it's time for launchpad.

Another thing we could try is see if we can figure out exactly which modules relating to networking I have installed (and version number) so you can compare. We both have Gutsy amd64 on the same computer and wireless chip, but something must be different if it works for me but still not for you. 

Too bad I'm GMT-8. Post back with any further thoughts and I'll do my best to help figure it out.

---

### Post by NigelHarrison on 2007-10-29
My mchines's BIOS was out-of-date and, following kafo's suggestion, I updated it, downloading the convenient iso image for the BIOS updater.  I can report that this did _not_ fix my wireless connection problem.  (However, some things do now work: volume up/down buttons, sleep button (Fn F4), sound mute button, and the disk access is somewhat faster.)

Nigel

---

### Post by NigelHarrison on 2007-10-29
Guys:

I can now report that my wireless connectivity is working.  On the basis that the -server kernel somehow worked better for me than the -generic kernel, I went to the [www.intellinuxwireless.org](www.intellinuxwireless.org) website, downloaded the latest mac80211 and iwlwifi module source codes, and following the instructions there, and on the very useful [www.thinkwiki.org](www.thinkwiki.org) website, I recompiled my kernel.  Now, I can tell you I've never done anything so scary before, but, just following all the instructions, it apparently completed successfully.  Reboot into new kernel (old one not lost, which may still prove handy (-: ) and, voila, working wifi connection!

To complete our little investigation, I'm now (after dinner) going to restart with a freshly downloaded live-CD image, to see if that is OK, as kafo suggested.  I will, of course, keep you updated.

And, again, thanks for your help.

Nigel

---

### Post by John Jason Jordan on 2007-10-29
> **NigelHarrison said:**
> My mchines's BIOS was out-of-date and, following kafo's suggestion, I updated it, downloading the convenient iso image for the BIOS updater.  I can report that this did _not_ fix my wireless connection problem.  (However, some things do now work: volume up/down buttons, sleep button (Fn F4), sound mute button, and the disk access is somewhat faster.)l
Although I think I now have wireless working, I'm nevertheless interested in the BIOS update. However, I just had a very annoying experience. I decided to test the buttons. The volume buttons appear to be working, but don't actually change the settings. The sleep button works, but I can't get it to resume from sleep. I had to reboot. The computer did not come with a layout or instructions on what the keys and lights mean, but on lenovo.com I discovered that to get it out of sleep mode you just hit the Fn button. It just didn't work. :(  

What BIOS did you have and what is the latest one? According to Lenovo the latest one for the T61 is 1.22-1.06 (19 Sept 2007), however, it does not specifically list my model (6460). I don't really need those buttons working, but it might be a good idea to upgrade the BIOS if there's really a newer one than what I have.

---

### Post by John Jason Jordan on 2007-10-29
Never mind. I flashed the BIOS to 18 October 2007 version. But there was no change in the buttons. Sound buttons still appear to work (popup appears on screen), but don't actually change the settings in Gutsy. Sleep button still sleeps, and when I press Fn to return from sleep it appears to do so (hard drive runs, lights flash), but the screen remains black, keyboard and mouse are dead, and nothing will bring them back short of rebooting.

For my next step I'm going to try to install the server modules.

Edit: Just did it. Horrible results. When I booted to the -server it didn't recognize the video card, didn't recognize xorg.conf and booted me to vga 800 x 600. I tried the sound buttons and they didn't work at all. Tried the sleep button and it worked the same as it did under -generic; that is, it put the machine to sleep, but I was unable to get back. And there was no change in the wireless either - wifi-radar still sees the wireless networks and I can connect to them, but network-manager is still broken.

Luckily rebooting to -generic still works and nothing is changed. Now I'm going to uninstall -server.

---

### Post by kafo on 2007-10-30
Suspend and hibernate don't work for me either. I think that is the fault of nvidia proprietary driver. To make the volume buttons work correctly you have to do the following. Right click on the panel volume applet and select Preferences. Make sure HDA Intel and PCM are selected. Go to System -> Preferences -> Sound. Select HDA Intel and PCM for Default Mixer tracks. For me at least, this enables volume buttons to work correctly.

---

### Post by John Jason Jordan on 2007-10-30
> **kafo said:**
> Suspend and hibernate don't work for me either. I think that is the fault of nvidia proprietary driver. To make the volume buttons work correctly you have to do the following. Right click on the panel volume applet and select Preferences. Make sure HDA Intel and PCM are selected. Go to System -> Preferences -> Sound. Select HDA Intel and PCM for Default Mixer tracks. For me at least, this enables volume buttons to work correctly.
Thanks for the suggestion, but the buttons still don't work. Actually, the Preferences dialog box was already set to HDA Intel (Alsa) and PCM. All the test buttons work, and I hear sounds fine from applications and from the OS. It's just the buttons that don't work. And they do pop up a little visual on the screen showing the volume going up and down, and an x appearing and disappearing for the mute button. It's just that the buttons are not affecting the settings in Gutsy. Probably another 64-bit issue.

---

### Post by kudar on 2007-10-30
the only problem I have with the Intel 4965 AGN is that my wireless is deathly SLOW.  I am going to try booting into the -server kernel and trying wifiradar today.  Hopefully this helps as I've been trying to troubleshoot this for 2 weeks now.

---

### Post by kafo on 2007-10-30
> **John Jason Jordan said:**
> Thanks for the suggestion, but the buttons still don't work. Actually, the Preferences dialog box was already set to HDA Intel (Alsa) and PCM. All the test buttons work, and I hear sounds fine from applications and from the OS. It's just the buttons that don't work. And they do pop up a little visual on the screen showing the volume going up and down, and an x appearing and disappearing for the mute button. It's just that the buttons are not affecting the settings in Gutsy. Probably another 64-bit issue.

If you open the volume control by double clicking on the volume applet and then press the volume buttons, do you see any of the sliders going up and down? For me the PCM slider is moved, but before I changed the settings I mentioned the microphone slider was moving. I am also using 64-bit gutsy. Maybe your machine is a bit different, I have the 14,1 inch machine with nvidia graphics.

---

### Post by John Jason Jordan on 2007-10-30
> **kafo said:**
> If you open the volume control by double clicking on the volume applet and then press the volume buttons, do you see any of the sliders going up and down? For me the PCM slider is moved, but before I changed the settings I mentioned the microphone slider was moving. I am also using 64-bit gutsy. Maybe your machine is a bit different, I have the 14,1 inch machine with nvidia graphics.
Hey, they're working now!

Maybe I didn't understand how to use them. That is, to unmute you have to use the up-volume button. I normally keep the sound muted, so to unmute I was hitting the mute button, and it did nothing. 

Now I still need to figure out how to get it out of sleep mode. Fn-F4 puts it to sleep OK, but Fn is supposed to bring it back and it doesn't. Next I'm going to try closing the lid to see if that works any different. I also want to swap the Fn and Ctrl keys, but that may not be possible. Also off-topic for this thread.

Thanks for making me see how to use the volume buttons.

---

### Post by John Jason Jordan on 2007-10-30
> **kudar said:**
> the only problem I have with the Intel 4965 AGN is that my wireless is deathly SLOW.  I am going to try booting into the -server kernel and trying wifiradar today.  Hopefully this helps as I've been trying to troubleshoot this for 2 weeks now.
I have not used the wireless enough yet to comment on the speed, but I suspect I may have slow speed. The only places I have connected so far have been the city's ad-based wifi cloud (which is famous for being slow) and at the airport. Today I'm going to the university and they have great bandwidth, so we'll see what happens. I wonder if there is a utility to see what speed I'm getting.

---

### Post by kudar on 2007-10-30
> **John Jason Jordan said:**
> I have not used the wireless enough yet to comment on the speed, but I suspect I may have slow speed. The only places I have connected so far have been the city's ad-based wifi cloud (which is famous for being slow) and at the airport. Today I'm going to the university and they have great bandwidth, so we'll see what happens. I wonder if there is a utility to see what speed I'm getting.

just go to google and search for speed test. that is usually a good way to measure

---

### Post by wadeall on 2007-10-30
I have tried to install Gutsy on a new  Thinkpad T61  too and also cannot get wireless connectivity.
Im not  sure wheter i installed a 32 or  64 bit  version.

---

### Post by kafo on 2007-10-30
I am getting about 2,8 MB per second:
73740438 bytes received in 25.43 secs (2832.2 kB/s)
ftp> 
 I have tested this from my local ftp server. That seems about right.

---

### Post by John Jason Jordan on 2007-10-30
> **wadeall said:**
> I have tried to install Gutsy on a new  Thinkpad T61  too and also cannot get wireless connectivity.
Im not  sure wheter i installed a 32 or  64 bit  version.
Probably you installed 64-bit because I think we 64-bit folks are the only ones with wireless problems. You can find out from the command line with "uname -a" (without quotes).

---

### Post by John Jason Jordan on 2007-10-30
> **kafo said:**
> I am getting about 2,8 MB per second:
73740438 bytes received in 25.43 secs (2832.2 kB/s)
ftp> 
 I have tested this from my local ftp server. That seems about right.
I am currently at the university and it seems to be working fine. That is, first I went to the library and couldn't even find a wireless network. But the library here is famous for lousy wireless. So then I went to a computer lab and I'm sitting right under a wireless thingy. It's working fine and seems reasonably fast. But I don't know how to test the speed. How did you determine that you were getting 2.8 MB/s?

---

### Post by kafo on 2007-10-30
> **John Jason Jordan said:**
> I am currently at the university and it seems to be working fine. That is, first I went to the library and couldn't even find a wireless network. But the library here is famous for lousy wireless. So then I went to a computer lab and I'm sitting right under a wireless thingy. It's working fine and seems reasonably fast. But I don't know how to test the speed. How did you determine that you were getting 2.8 MB/s?

I used my ftp server. If you have access to a local ftp server, you can use that. Here's what to do:
$ftp servername
$get filename

You start the ftp command in a terminal window. At the end of transmission transfer speed is reported. File should be reasonably big, say 10MB or more.

---

### Post by kudar on 2007-10-30
> **kafo said:**
> Just to clarify, I am using 64 bit gutsy, uname -a output:
Linux tinkpad 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I should probably also mention that I still have Vista installed on my machine and have updated it with Lenovo's system update and there were a couple of bios updates since I bought it. Maybe that could also have something to do with it. And I also have Nvidia Quadro NVS 140M and use the restricted driver and have no problems because of it.


I think you have the same exact computer as me.  T61 Quadro NVS, INTEL 4965, 2.2 gig core 2 duo.  I am having wifi speed issues. think i should try using 64 bit gutsy??

---

### Post by kafo on 2007-10-30
Could be. You could try the 64 bit live cd and test your wireless connection there and see if it works as expected.

---

### Post by NigelHarrison on 2007-10-31
John:

Sorry for the delayed reply.  My machine previously had BIOS version 1.07 (Embedded Controller version 1.03), which Lenovo's website says "was not released", but somehow found its way into my T61!  The version I installed was 1.26 (with Embedded Controller version 1.06), and I downloaded the .iso file from this location:

[ftp://ftp.software.ibm.com/pc/pcccbs/mobiles/7luj09uc.iso](ftp://ftp.software.ibm.com/pc/pcccbs/mobiles/7luj09uc.iso)

You just burn that file to a CD, reboot with the CD in the drive, and follow the instructions.

I hope that helps.

Nigel

---

### Post by NigelHarrison on 2007-10-31
kafo:

Suspend/Resume (that is, to/from RAM) work correctly here, with nvidia restricted library running.  I can't get Hibernate working, though.  With the latest BIOS update, the volume controls actually work using the buttons ...

Nigel

---

### Post by NigelHarrison on 2007-10-31
John:

I'd try the BIOS update, if I were you.

Nigel

---

### Post by NigelHarrison on 2007-10-31
kudar:

Is the connection apparently slow, or does NetworkManager report a slow speed?  I ask, because I note that NetworkManager does not report the speed consistently (it's the subject of a bug report).

Nigel

---

### Post by kafo on 2007-10-31
> **NigelHarrison said:**
> kafo:

Suspend/Resume (that is, to/from RAM) work correctly here, with nvidia restricted library running.  I can't get Hibernate working, though.  With the latest BIOS update, the volume controls actually work using the buttons ...

Nigel

It doesn't work for me. It is the same for both suspend and hibernate. The machine seems to come up, but the screen remains dark. I have also updated to bios version 1.26. Strange.

---

### Post by John Jason Jordan on 2007-11-01
> **NigelHarrison said:**
> kafo:Suspend/Resume (that is, to/from RAM) work correctly here, with nvidia restricted library running.  I can't get Hibernate working, though. With the latest BIOS update, the volume controls actually work using the buttons.Nigel
I got the latest BIOS now, and the volume buttons are working. Brightness buttons pop up a thingy on the screen and it shows the brightness going up and down (same as for the volume), but the brightness doesn't actually change. 

As for suspend/resume and hibernate, I don't understand the difference. If I close the top it blanks the screen, but that is all. When I open the top again the screen is blank until I move the mouse, hit Esc, or something. The hard drive light does not come on. I don't think there is really any power saving going on.

If I press Fn-F4 it goes to sleep. The screen goes dark, the hard drive runs, the half-moon blinks, and eventually it appears dead. At this point you are supposed to be able to press Fn alone and it will restore. Someone also told me to hold down Fn for a long time. But no matter what I do, it is dead. No mouse, no keyboard, and I can hold the Fn down until next week and nothing will happen. The only option is to hold down the power button until it finally shuts off, then reboot.

I need to learn what suspend and hibernate mean, that is what they are supposed to do.

Edit: I didn't say clearly what happens when I press Fn alone. It does run the hard disk and appears to be coming back. But the screen remains dark as kafo said.

---

### Post by NigelHarrison on 2007-11-01
John:

I've replied inline:

JJJ:
I got the latest BIOS now, and the volume buttons are working. Brightness buttons pop up a thingy on the screen and it shows the brightness going up and down (same as for the volume), but the brightness doesn't actually change.

Nigel:
Good.  Your experience exactly matches mine.  If you want to make the brightness level actually change (-: you can switch to terminal mode (Ctrl-Alt-F1), then press your brightness up/down buttons (the brightness does vary), then switch back to your graphical mode (Ctrl-Alt-F7).  The brightness will be at the level you moved it to.  This is not very convenient, but at least it works at all.

JJJ:
As for suspend/resume and hibernate, I don't understand the difference. If I close the top it blanks the screen, but that is all. When I open the top again the screen is blank until I move the mouse, hit Esc, or something. The hard drive light does not come on. I don't think there is really any power saving going on.

Nigel:
Suspend/Resume saves the current process state to RAM, whereas Hibernate saves it to disk.  The idea, I think, is that Suspend/Resume is short-term, and Hibernate is long-term.  I haven't heard of anyone getting Hibernate to work with Ubuntu at all (unless someone out there can put me right), but Suspend/Resume definitely do work on my T61 in Gutsy.  Normally, I just click the close button and choose Suspend, but, if you set the Close Lid switch to do a Suspend (System/Preferences/Power Management from the desktop), then closing the lid does the job too.  The moon symbol flashes a few times, then stays on, and the machine is suspended.  Then, on lid open, the screen flashes some stuff (USB ports re-initialising?) and then it's up.

However, I have to tell you that I also had to do something to tell the script to shutdown the wifi kernel modules on suspend, and then restart them again on resume.  I can't recollect what exactly I did, but I'll go and check my notes after breakfast and post the info back here.

JJJ:
If I press Fn-F4 it goes to sleep. The screen goes dark, the hard drive runs, the half-moon blinks, and eventually it appears dead. 

Nigel:
I think you should end up with the moon symbol on.  I'll double-check that's what happens here shortly and confirm that.

Edit: Fn-F4 works correctly here (but it does depend on the setting in the Power Management preferences dialog -- which refers to the button as the Sleep button).

JJJ:
At this point you are supposed to be able to press Fn alone and it will restore. Someone also told me to hold down Fn for a long time. But no matter what I do, it is dead. No mouse, no keyboard, and I can hold the Fn down until next week and nothing will happen. The only option is to hold down the power button until it finally shuts off, then reboot.

Nigel:
I didn't know you could just press the Fn key: I'll test and get back to you.

Edit: Just pressing the Fn did work here: no need to hold it down.  Result exactly as lid close/re-open.

JJJ:
I need to learn what suspend and hibernate mean, that is what they are supposed to do.

Edit: I didn't say clearly what happens when I press Fn alone. It does run the hard disk and appears to be coming back. But the screen remains dark as kafo said.

Nigel:
I hope some of that helps.  I'll come back again shortly.

---

### Post by NigelHarrison on 2007-11-01
> **NigelHarrison said:**
> John:

JJJ:
As for suspend/resume and hibernate, I don't understand the difference. If I close the top it blanks the screen, but that is all. When I open the top again the screen is blank until I move the mouse, hit Esc, or something. The hard drive light does not come on. I don't think there is really any power saving going on.

Nigel:
Suspend/Resume saves the current process state to RAM, whereas Hibernate saves it to disk.  The idea, I think, is that Suspend/Resume is short-term, and Hibernate is long-term.  I haven't heard of anyone getting Hibernate to work with Ubuntu at all (unless someone out there can put me right), but Suspend/Resume definitely do work on my T61 in Gutsy.  Normally, I just click the close button and choose Suspend, but, if you set the Close Lid switch to do a Suspend (System/Preferences/Power Management from the desktop), then closing the lid does the job too.  The moon symbol flashes a few times, then stays on, and the machine is suspended.  Then, on lid open, the screen flashes some stuff (USB ports re-initialising?) and then it's up.

However, I have to tell you that I also had to do something to tell the script to shutdown the wifi kernel modules on suspend, and then restart them again on resume.  I can't recollect what exactly I did, but I'll go and check my notes after breakfast and post the info back here.


OK, I found this info (most of this courtesy of the good folks at [www.thinkwiki.org](www.thinkwiki.org), by the way).  You need to do two things to get Suspend/Resume to work properly:

1. Edit (you need to be root, or sudo this) /etc/default/acpi-support and make the following lines as below (... means scroll down the file ...):

SAVE_VBE_STATE=false
...
POST_VIDEO=false
...
HIBERNATE_MODE=platform


2. Also make the following changes (in the same file) (this to make wireless stop and restart on suspend/resume):

In the line which probably says

MODULES=""

add entries so it is as follows:

MODULES="iwl4965 iwlwifi_mac80211 cfg80211"

(Note that you do need the quotes. Assumes you are using the Intel 4965AGN or Intel 3965AG wireless card -- which I believe you are, JJJ)

3. Save the file and (probably) reboot.

Two further points noted in the thinkwiki.org entry: They say that you should _not_ have the "hibernate" or "uswusp" packages installed, or suspend/resume will not work.  And there are certainly folks (how GWB of me -:)) who report that this procedure has not worked for them.

So, I hope that gets you a step further ...

Regards

Nigel

---

### Post by jyrppa on 2007-11-01
I can't get WPA-PSK working on my T61 with Intel 4965. If WLAN has WEP I don't have any problems connecting. WPA doesn't work with wifi-radar, wlaassistant or directly with wpa_supplicant.

wlaassistant:
$ sudo rmmod iwl4965
$ sudo modprobe iwl4965
$ sudo wlaassistant

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:a5:79:f1
Sending on   LPF/wlan0/00:13:e8:a5:79:f1
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
No pre-connection command specified.
iwconfig_set: /sbin/iwconfig wlan0 mode managed channel 6 key off essid vellilanni
iwconfig_ap: /sbin/iwconfig wlan0 ap 00:02:CF:62:7B:2C
==>stderr: Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Using wpa_supplicant driver: wext
WPA client started. Waiting for status...
CONNECTION FAILED.
disconnect: /sbin/iwconfig wlan0 mode managed key off ap off essid off

wpa_supplicant:

jyrppa@potpuri:~/opt$ sudo wpa_supplicant -B -c /etc/wpa_supplicant/wpa_supplicant.conf -i wlan0 -D wext -ddd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ap_scan=2
Line: 4 - start of a new network block
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x1e
ssid - hexdump_ascii(len=9):
     76 65 6c 6c 69 61 6e 6e 69                        vellianni
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='vellianni'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:e8:a5:79:f1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - wpa_driver_wext_set_drop_unencrypted
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Setting scan request: 0 sec 100000 usec
Added interface wlan0

jyrppa@potpuri:~/opt$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"vellianni"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and here's my wpa_supplicant.conf :
# WPA-PSK
ap_scan=2
network={
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40

        ssid="vellianni"
        psk="secret"
}

any ideas?

---

### Post by jyrppa on 2007-11-02
I got WPA-PSK finally working with wcid. Great application:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by NigelHarrison on 2007-11-02
Excellent thing: thanks for the link.  Works great for me too.

---

### Post by John Jason Jordan on 2007-11-08
I continue to have problems with wireless. It acts as if there is an intermittent connection to the antenna. I came to the university today and connected right away. Twenty minutes later it went dead. All attempts at revival failed. I rebooted several times and it still failed to work. Eventually, while rebooting, I went into the BIOS and disabled the radio, then let it finish booting. Sure enough, no wireless at all. Then I rebooted one more time, enabling the radio in the BIOS before letting it boot, and wireless is back working fine. Right now I have been connected for an hour, but from past experience it will die at any moment and there is no way to get it back, sometimes even by rebooting.

This is a T61 with Gutsy amd64, 4965AGN, the latest BIOS, and Gutsy completely up to date. If anyone else has experienced this please respond.

---

### Post by mstralka on 2007-11-08
I highly recommend wicd - it's much better than NetworkManager and I have had no issues with it on my T61 with Intel 3945abg (T61 6459-CTO)..  NetworkManager worked intermittently for me - it would try to connect to my neighbor's unsecured AP and then take 5 minutes trying to re-connect.  With WICD, I just told it to always connect to my WPA-secured AP and it has never had another problem.

---

### Post by John Jason Jordan on 2007-11-08
> **mstralka said:**
> I highly recommend wicd - it's much better than NetworkManager and I have had no issues with it on my T61 with Intel 3945abg (T61 6459-CTO)..  NetworkManager worked intermittently for me - it would try to connect to my neighbor's unsecured AP and then take 5 minutes trying to re-connect.  With WICD, I just told it to always connect to my WPA-secured AP and it has never had another problem.
What is WICD?

Edit: Never mind, I found it.

---

### Post by NigelHarrison on 2007-11-13
John:

I apologise that I haven't been here for a few days.  I think your continuing problem is not unknown.  Here, I still get unpredictable events, where my wireless connection goes 'off the air'.  I continue to compile and apply the latest version of the iwl4965 diriver from intelwireless, and I don't now have any problems compiling/building the later versions.  However, there stll definitely are problems.  I do think Intel are taking this seriously: changes to the code are very often, sometimes more than once a day, and development is active.  However, there must still be bugs, I suppose.

Regards

Nigel

---

### Post by John Jason Jordan on 2007-11-15
> **NigelHarrison said:**
> I apologise that I haven't been here for a few days.  I think your continuing problem is not unknown.  Here, I still get unpredictable events, where my wireless connection goes 'off the air'.  I continue to compile and apply the latest version of the iwl4965 diriver from intelwireless, and I don't now have any problems compiling/building the later versions.  However, there stll definitely are problems.  I do think Intel are taking this seriously: changes to the code are very often, sometimes more than once a day, and development is active.  However, there must still be bugs, I suppose.Nigel
Nigel,

Thanks for the update. I am having the same exact problem. The wireless works fine most of the time, but the longest I've ever been able to stay connected was about an hour. It just goes off the air, as though the hotspot pulled the plug (but that can't be because it happens at various different places where I have connected). I'm actually glad to hear you're having the same issues, because I was beginning to think it was a physical issue - like an intermittent connector somewhere. It's a relief that apparently I won't have to deal with a warranty repair issue.

I don't have time to compile and try all the new builds of the driver. And fortunately I need the wireless only when I am at the university, which is only two or three days a week, and only for a short while. So I can afford myself the luxury of waiting until I hear that it has been fixed. Please do keep this thread posted, however. I'm sure we're not the only ones watching this issue.

---

### Post by Clancy_s on 2007-11-25
> **jyrppa said:**
> I got WPA-PSK finally working with wcid. Great application:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Thanks for the link - wicd seems to have fixed my probem with wireless under 64 bit GG :)

I was having problems with my Intel 4965 agn wireless under 64 bit GG, so much so that I installed the 32 bit on another partition.  I don't use encryption but control access via MAC and not transmitting the ESSID.

Under 64 bit I was able to connect using the network manager twice in about 20 boots.  Using wicd I've been successful every time so far (about 8 boots since installing wicd).  Oddly enough the 3 times I booted off the live CD whilst I was testing network manager managed to connect every time. :confused:

OTOH under 32 bit network manager has connected every time (about 10, once I got wireless sorted under 64 bit I've not used 32 bit much).

It looks like most of you have more experience with ubuntu than I (first install 4 days ago).  Is having wicd installed likely to cause problems with the next major upgrade?

Also, is there a bug report on this and should I report my experience with this since it seems to be a related problem?

------------
Toshiba Satellite A200/S01, Intel Core 2 Duo 2.2 Ghz T7500, 4096Mb DDR2 RAM (667 Mhz)
2 x 160 Gb SATA HDD, HD DVD-ROM DVD SuperMulti Double/Dual Layer Drive 
ATI Radeon 2600 HD graphics card with 512Mb RAM, 15.4" WXGA (1280 x 800) BrightView Screen
Intel 4965 agn Wireless LAN 802.11 a/g/n

---

### Post by John Jason Jordan on 2007-11-27
> **Clancy_s said:**
> Thanks for the link - wicd seems to have fixed my probem with wireless under 64 bit GG :)
I was having problems with my Intel 4965 agn wireless under 64 bit GG, so much so that I installed the 32 bit on another partition.  I don't use encryption but control access via MAC and not transmitting the ESSID.
Under 64 bit I was able to connect using the network manager twice in about 20 boots.  Using wicd I've been successful every time so far (about 8 boots since installing wicd).  Oddly enough the 3 times I booted off the live CD whilst I was testing network manager managed to connect every time. :confused:
OTOH under 32 bit network manager has connected every time (about 10, once I got wireless sorted under 64 bit I've not used 32 bit much).
It looks like most of you have more experience with ubuntu than I (first install 4 days ago).  Is having wicd installed likely to cause problems with the next major upgrade?
Also, is there a bug report on this and should I report my experience with this since it seems to be a related problem?
I don't know if wicd will cause any problems with updates. In theory it should not. However, I have not installed it yet because Synaptic wants to replace network-manager network-manager-gnome, and wifi-radar. Wifi-radar is no big deal but aren't the other two integral parts of Gnome or Ubuntu or something? I'd like to hear what breaks when they get uninstalled before I install wicd.

I'd also be curious if your success with wireless continues. I keep getting disconnected after anywhere from a few minutes to an hour or so. I've been hoping that Nigel would pop in and say that he finally got a new Intel driver that works as I don't have the time or expertise to compile a new driver. It sure would be nice to get the wireless problem fixed. Also, there are a couple local T61 users who are having the same problem on other distros.

---

### Post by John Jason Jordan on 2007-11-27
> **John Jason Jordan said:**
> I don't know if wicd will cause any problems with updates. In theory it should not. However, I have not installed it yet because Synaptic wants to replace network-manager network-manager-gnome, and wifi-radar. Wifi-radar is no big deal but aren't the other two integral parts of Gnome or Ubuntu or something? I'd like to hear what breaks when they get uninstalled before I install wicd.
Well, I tried it anyway. I installed wicd, which caused Synaptic to uninstall network-manager, network-manager-<something> and wifi-radar. After I rebooted my video was all messed up, I had no wireless at all, and I couldn't uninstall wicd and reinstall the others because Synaptic couldn't get to the network. 

But something really strange happened. I was at school, so I went to the library where they have study rooms with wired connections for graduate students. I plugged a cable into the wall (I always carry one just for situations like these, plus the wired network at school is incredibly fast). I booted the computer, and when Gutsy x86_64 came up my video was back to normal. I immediately opened Synaptic intending to restore the network to its former condition. Imagine my surprise when I discovered that the network-manager apps had been reinstalled and wicd had been uninstalled. I did not do that! But somehow Gutsy fixed things.

Anyway, I am not going to fiddle with wicd again.

---

### Post by NigelHarrison on 2007-12-05
> **John Jason Jordan said:**
> I don't know if wicd will cause any problems with updates. In theory it should not. However, I have not installed it yet because Synaptic wants to replace network-manager network-manager-gnome, and wifi-radar. Wifi-radar is no big deal but aren't the other two integral parts of Gnome or Ubuntu or something? I'd like to hear what breaks when they get uninstalled before I install wicd.

I'd also be curious if your success with wireless continues. I keep getting disconnected after anywhere from a few minutes to an hour or so. I've been hoping that Nigel would pop in and say that he finally got a new Intel driver that works as I don't have the time or expertise to compile a new driver. It sure would be nice to get the wireless problem fixed. Also, there are a couple local T61 users who are having the same problem on other distros.

John:

Sorry I haven't looked in here in a while.  However, I can tell you that there is a new release of the mac80211 and iwlwifi drivers available: I have downloaded them, and I'll put aside some time this weekend to rebuild them.  I'll let you know how I get on.

Nigel

---

### Post by airchie on 2007-12-05
Hi guys.
I'm reading this post with interest.
I have just installed Linux for the first time
Its on my laptop which is a Toshiba X200 with the same wireless card as mentioned.

Is this still an ongoing issue for everyone??

I tried installing wicd but it wouldn't download the necessary files when I hit reload in package manager. :(

Will watch this thread with interest... :)

---

### Post by airchie on 2007-12-05
Wierd.
I have two HDDs in this laptop.
I installed GG on the 2nd and have Vista on the 1st.
I booted into Vista and restarted the machine to go into GG.
Now my wireless seems to be working fine but Synaptics package manager is having problems downloading files.
It just sits there not moving. :(

Damn PCs can be annoying at times... :D

---

### Post by airchie on 2007-12-06
Screw this, I'm off back to Vista... :D

Just kidding, I'm just gonna go install the 32bit version of ubuntu instead...

---

### Post by ootz0rz on 2007-12-07
*edit* nevermind. sorry just realized what I said was already posted

---

### Post by minotaurjim on 2007-12-07
> **airchie said:**
> Screw this, I'm off back to Vista... :D

Just kidding, I'm just gonna go install the 32bit version of ubuntu instead...

I've got the same problems on my T61p with 64 bit as I do with 32 bit versions.  

I've tried all the solutions I could google and still nothing has fixed it.

Anyone know if there is anyone actually working to fix this?

---

### Post by airchie on 2007-12-08
Not sure what it actually means but I hear a lot about using ndiswrapper and using windows drivers.

I also believe Intel are firing out a lot of updates to drivers in order to fix this.

---

### Post by Clancy_s on 2007-12-08
> **John Jason Jordan said:**
> Well, I tried it anyway. I installed wicd, which caused Synaptic to uninstall network-manager, network-manager-<something> and wifi-radar. After I rebooted my video was all messed up, I had no wireless at all, and I couldn't uninstall wicd and reinstall the others because Synaptic couldn't get to the network. ...

Anyway, I am not going to fiddle with wicd again.

Sorry for the slow reply, I've been distracted.

Yes, wicd unistall the network-manger and wifi radar stuff on my system but that didn't break anything else: I'm connected via wicd at the moment.  My only issue is that I can't autoconnect to my hidden ESSID.  That seems to be due to iwlist scan not working.

I don't know if that's because of wicd uninstalling something since I didn't know to check  it before hand.  For the moment I'll put up with having to do manual connects since it's better than not being able to connect at all.

This problem appears to have many variations, presumably depending on one's exact hardware configuration.

The uninstall of the network manager stuff was the reason I thought I might have problems with the next major upgrade but reading some of the upgrade threads it sounds like I should be OK so long as I disable the wicd repositories first.  I'll have to use wired to upgrade and reinstall wicd afterwards if I still need it, which is simple enough.

I'm hoping the problem will be fixed in the next release anyway.

eta: the wicd forum admin didn't seem to think that wicd should have broken iwscan.  I guess I'll have to try uninstalling wicd and reinstalling network manager at some point. :rolleyes:

eta2: I booted into ubuntu 32 bit.  Since network manager is working fine with Intel 4965AGN there I haven't installed wicd.  iwlist scan still can't find any interfaces, not even my ethernet card.  I installed wifiradar, that couldn't find my network either.

I set the router to broadcast the ESSID and network manager autoconnects everytime in 32 bit GG, wicd autoconnects everytime in 64 bit GG but iwlist scan still can't find anything. :confused:

 So I think the iwlist scan problem is due to something else other than Intel 4965AGN 64 bit problem.  Since everything is actually working OK with wicd under 64 bit so long as I broadcast the ESSID I'll stick with my current setup until 8.4.

---

### Post by Clancy_s on 2007-12-09
I had a look through launchpad and couldn't find any reports of wifi with  Intel 4965AGN having problems specific to 64 bit Gutsy so I made a new bug report for this.  If we don't report it they probably won't  fix it...

If anyone wants to add a 'me too' it's here:

[https://bugs.launchpad.net/ubuntu/+bug/175200](https://bugs.launchpad.net/ubuntu/+bug/175200)

---

### Post by minotaurjim on 2007-12-13
I was hoping to see a [SOLVED] tag on this thread in the forums :(

---

### Post by Camasii on 2007-12-19
Hello,

I know I'm a late comer to this thread but I just got a new Thinkpad x61s through work and I may (or may not) be having a related issue to you guys. When I'm at home on my personal router (WPA) I connect with no problem and stay happily connected for hours, even days, at a time. However, when trying to connect at work (WPA-Enterprise) I can connect for anywhere between 5 and 45 minutes and then it drops off, and no matter what I do I can't reconnect. 

Anyone have any information about their ability/inability to connect to WPA-Enterprise networks? I really want to stop using XP, but I need wireless all day and Ubuntu just won't give it to me, no matter how nicely I ask...

Thanks guys!

-Tim

---

### Post by lenticular on 2007-12-20
Is the ESSID of the wireless router at work hidden?  How about at home?  I'm still have wireless problems with Gutsy, but the dropped connection thing went away when I had my WPA wireless router broadcast its ESSID instead of being hidden.  

Good luck.

-John

ps.  As a second magic trick, can you boot your laptop at work with the wireless switch set to off, then switch it on and let it acquire the network?  I'm using a Sony TZ130, but it has the intel 4965AGN wireless chipset and I have to do this to make it work.

---

### Post by Camasii on 2007-12-20
Actually that's true, the essid is hidden at work and public at home. I always assumed it was the WPA-Enterprise that was messing me up, not the fact that the essid was hidden. That's an interesting point and another avenue of research. I'll give the wireless switch thing a try too. Now, to try hiding my essid at home and see if it messes me up.

Thanks for the tips. I was considering switching to the ndiswrapper method of getting wireless working. Is it any more reliable that way? Or is that an outdated method?

-Tim

---

### Post by Camasii on 2007-12-20
Okay, so I hid my ssid at home and I've been connected for hours with no problems. So, I'm back to my original assumption that it's the WPA-Enterprise that ruins my day...

Any ideas?

---

### Post by lenticular on 2007-12-21
Here is another interesting fix for the intermittent disconnect problem.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24)

If, after you lose your connection at work, you run dmesg and see an error message about microcode error, replace your existing 4965 microcode with a more recent version.  I've just tried this at home.  Good news: it seems to stop the intermittent disconnects.  Bad news: I still have to boot Ubuntu with my wireless switch off, then turn it on.  Some major bugs associated with this chipset still.

Good luck!

-John

---

### Post by Camasii on 2008-01-03
Hey,

I had high hopes because I did, in fact, get the microcode error in dmesg after my wireless decides that it's not worth it to be connected any more. So I popped in the new version and viola! It worked! For about 25 minutes and then it doesn't disconnect like it used to (nm still THINKS it's connected) but I lose all network services, etc.

So, it seems to keep me on for a bit longer (step in the right direction?) but doesn't fix it completely.

Any other ideas?

---

### Post by mindless1973 on 2008-03-05
> **John Jason Jordan said:**
> Thanks for the reply. Since my original post I also received a reply from a local person who has a Thinkpad T61 with Gutsy. However, like kafo and saso in this thread, he is using 32-bit Gutsy. He has no problem with the wireless.

I have also tried a lot of different things. Gutsy amd64 sees the wireless. If I do "iwlist wlan0 scan" I get a list of available wireless networks. I can even connect to one. But I cannot get a DHCP address from a wireless access point. I can modprobe the iwl4965 driver and it is loaded and running fine. I don't know what the problem is. However, it appears to affect amd64 Gutsy only, so I am transferring this to the 64-bit forum.

Hi, I am using Gutsy 32bit and experiencing exactly the very same problems as you described (I can manually connect but don't get an IP address). 

I travel somehow a lot (that's also why I am very keen to get wireless working) and hat the opportunity to test wireless on several occasions. Sometimes it works just in seconds, sometimes it takes ages, but works and sometimes it won't work at all. I tried to find a pattern but was not successful yet.

I might depend on the manufactor of the access point - or on the signal quality...

Anyhow, this is a really annoying problem!

bye
me.

---

### Post by GeneralCody on 2008-03-05
I have the same card, and have updated the BIOS. For me this card worked without any mods after installing 7.10. No need for restricted drivers to run this card. My machine is a R61i, but the hardware is pretty much the same... I use WPA Personal/TKIP for authentication though...

---

### Post by mindless1973 on 2008-03-07
Hi,

> **NigelHarrison said:**
> 
I can now report that my wireless connectivity is working.  On the basis that the -server kernel somehow worked better for me than the -generic kernel, I went to the [www.intellinuxwireless.org](www.intellinuxwireless.org) website, downloaded the latest mac80211 and iwlwifi module source codes, and following the instructions there, and on the very useful [www.thinkwiki.org](www.thinkwiki.org) website, I recompiled my kernel.  Now, I can tell you I've never done anything so scary before, but, just following all the instructions, it apparently completed successfully.  Reboot into new kernel (old one not lost, which may still prove handy (-: ) and, voila, working wifi connection!
Nigel

I tried as well to compile the actual versions of the mac80211 and iwlwifi, but unfortually I get an error message when trying to make the mac80211 module:

> 
Kernel Makefile not found at '/lib/modules/2.6.22-14-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1


All the kernel sources and header files should be installed. Does anyone have a clue which Ubuntu package I should additionally install?

Thanks,

bye
Marcus.

---

### Post by koolcracker on 2008-06-15
I'm having this too, but I'm dual booting with Windows, and when I go to windows, Vista basically tells me that the card is turned off, and it turns it on for me. What in Ubuntu is causing this to happen?

It started off fine when I first installed it for about a day, but I no longer get conneted to the wireless. I'm not sure if that little piece of info will help anyone.

---

