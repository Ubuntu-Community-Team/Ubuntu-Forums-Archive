---
title: "Broadcom wireless bliss without the use of ndiswrapper"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by mrpeanut on 2007-03-23
[Original Document](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

This is a guide to getting your Broadcom wireless card working in Edgy.
This is tested and working on a 4311 chipset, although meant for any card in the 43xx series.
In this guide you will not use ndiswrapper, but the bcm43xx driver that you are suggested to blacklist in other guides.
You will need to be connected via ethernet to be able to complete this process.
Also, chances are you will not be completely successful if you have the 4311, 4312, or 4318 chipsets.  This is a problem with the transmission power, and the developers of the bcm43xx-firmware are working on a solution.  Further information can be found [here](http://linuxwireless.org/en/users/Drivers/bcm43xx).

Start out by adding a repository line to your sources:
```
sudo gedit /etc/apt/sources.list
```

Add this line:
```
deb http://ubuntu.cafuego.net edgy-cafuego bcm43xx
```

Save and then exit.
Add the GPG key:
```
wget http://ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```

Then update and install needed package:
```
sudo apt-get update
sudo apt-get install bcm43xx-firmware
```

Next step is to load the driver:
```
sudo modprobe bcm43xx
```

Now, for some strange reason it will be loaded as either eth1 or eth2, to find out we enter into the terminal:
```
iwconfig
```

For me it listed my wireless connection as eth1.  This step may not be neccessary, but I chose to change the identification from eth1 to wlan0. To do this we type in the terminal:
```
sudo gedit /etc/iftab
```
You will get a document that pairs a device name to a mac address.  Simply rename the device you identified in the prior step to wlan0. Save the file and then exit.

The default network manager seemed to be very fickle with my connection, so I opted to install network-manager. To do that enter into the terminal:
```
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
```
This will enable you to easily manage your network connections.

Lastly you will need to hand over the control of network connections to network-manager.  It would be wise to backup this file before you modify it.
```
sudo gedit /etc/network/interfaces
```
You will want to delete everything except for your loopback interface, which is identified as lo.  The resulting file should look like this:
```
auto lo
iface lo inet loopback
```
Then save the file and exit.

Once you have completed all of the steps restart your pc.  When it starts back up you will see a network-manager icon in the notification area.  you can right-click it to ensure your wireless connection is enabled, and then left-click it to select the network that you would like to connect to.  After that you should be in wireless bliss!

Please let me know if this tutorial works for you.  If there is something that anyone would like to add to, or if anything needs to be elaborated on please let me know.  I don't want to post something to help and have anyone end up worse off!

Again, all credits go to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

### Post by johnc4510 on 2007-03-23
The first line of code should read:
sudo gedit /etc/apt/sources.list

---

### Post by mrpeanut on 2007-03-23
> **johnc4510 said:**
> The first line of code should read:
sudo gedit /etc/apt/sources.list

Thank you for catching that!

---

### Post by johnc4510 on 2007-03-23
No problem, it looks like you put a bit of work in on it and I didn't want the first terminal command not to work.

---

### Post by JengaBlocks on 2007-03-24
Does this assume that you are attached to the Internet via Ethernet? For example, in order to do a wget... :)

---

### Post by xopher on 2007-03-24
> **JengaBlocks said:**
> Does this assume that you are attached to the Internet via Ethernet? For example, in order to do a wget... :)

Well if you don't have supernatural powers, then I suppose it does assume that, yes ;) Hehe

Any idea if this is available/needed for Feisty? Im eager to get rid of ndiswrapper :)

---

### Post by mrpeanut on 2007-03-24
> **JengaBlocks said:**
> Does this assume that you are attached to the Internet via Ethernet? For example, in order to do a wget... :)

Haha, yeah that's a safe assumption.

> **xopher said:**
> Well if you don't have supernatural powers, then I suppose it does assume that, yes ;) Hehe

Any idea if this is available/needed for Feisty? Im eager to get rid of ndiswrapper :)

I haven't experimented with Feisty at all yet, so I can't say for sure. I do know that in the original guide says you need linux kernal 2.6.17-rc2 or greater, so I would assume it would work.  I'd love it to work out of the box, but sadly I don't see that happening.

---

### Post by spd106 on 2007-03-24
Broken link, should be [Original Document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy").

gksudo is preferred to sudo for gui apps such as gedit ([http://www.psychocats.net/ubuntu/graphicalsudo)](http://www.psychocats.net/ubuntu/graphicalsudo)).

I'm also not too enthusiastic about adding third party repos (Beryl/Compiz/Coral? excluded).

Sorry for the criticisms, it's nice to see someone put a bit of effort into simplifying such a complex process.

---

### Post by nanog on 2007-03-28
Thanks for the tutorial...I was dreading using ndiswrapper. I wanted to report that it worked on a Dell e1405/640m in Feisty beta. 

I want to respond to the previous poster. I consider well-integrated wifi to be essential to an Ubuntu install on a laptop.

---

### Post by callyn on 2007-04-09
Followed this guide for Feisty Fawn and was unsuccessful. Card shows, but unable to connect. Seems to be a problem with the beta - all updates applied as of 4-9-2007. Thank you

---

### Post by spd106 on 2007-04-09
On Feisty the first few steps of this guide can be replaced with simply installing the bcm43xx-fwcutter package. It will go fetch and extract the recommended firmware for you, as long as you have another working connection.

The firmware it fetches is the one pointed to [here]("http://linuxwireless.org/en/users/Drivers/bcm43xx")

---

### Post by nanog on 2007-04-12
I was able to get this tutorial working on a dell e140/640m in  feisty beta. I did have to reinstall network manager to gain greater stability. 

I was able to fix the tx power problem and to get speeds of >500kb/s by updating my kernel to 2.6.21rc6. 
a link with a tutorial can be found here:
[http://ubuntuforums.org/showthread.php?t=391961](http://ubuntuforums.org/showthread.php?t=391961).

---

### Post by mrpeanut on 2007-04-13
> **callyn said:**
> Followed this guide for Feisty Fawn and was unsuccessful. Card shows, but unable to connect. Seems to be a problem with the beta - all updates applied as of 4-9-2007. Thank you

Which chipset is your card?  Type lspci into your terminal window and find the line with Broadcom in it to identify it.  If you are the lucky owner of the 4311, 4312, or 4318, chances are you will have problems.  I just updated the first post with this information, so to spare you from rereading it you can check out [http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx) for more updated information on the firmware used in this tutorial.  There is a transmission power issue with those specific chipsets, and there is a solution in the works from the team that created it.

---

### Post by mrpeanut on 2007-04-13
> **nanog said:**
> I was able to get this tutorial working on a dell e140/640m in  feisty beta. I did have to reinstall network manager to gain greater stability. 

I was able to fix the tx power problem and to get speeds of >500kb/s by updating my kernel to 2.6.21rc6. 
a link with a tutorial can be found here:
[http://ubuntuforums.org/showthread.php?t=391961](http://ubuntuforums.org/showthread.php?t=391961).

Hey, the link you provided bounced me right back to this thread.  If you still have it would you mind reposting it?  I'm interested in taking a look.  Thanks!

---

### Post by stoopid1 on 2007-04-13
it works, but the speed is terribly slow.  I feel like i'm on dialup.

---

### Post by mrpeanut on 2007-04-13
> **stoopid1 said:**
> it works, but the speed is terribly slow.  I feel like i'm on dialup.

Which chipset do you have?  Most likely one that's not supported yet, ie 4311, 4312, or 4318.

---

### Post by nanog on 2007-04-15
Mr.Peanut:
[http://ubuntuforums.org/showthread.php?t=407859](http://ubuntuforums.org/showthread.php?t=407859)

If you are interested I can provide my compiled kernel. Send me a pm.

---

### Post by maltepalte on 2007-04-22
I tried to use fw-cutter and the same bcm43xx driver before, that did work but seemed to only enable WEP-encryption.
Now I followed this guide and everything works perfectly. Thanks thanks thanks!

I'm using Ubuntu Feisty (final) with everything updates (as of 4/22/07).

Now some keywords so fellow googlites can find this easier:
Card: Linksys PCMCIA wmp54g
Chipset: bcm4306
WAP works? Yes.

---

### Post by sourcedriver on 2007-04-22
This guide also worked well for me.  

I have:
Dell Wireless 1390 WLAN Mini-PCI Card
Feisty 7.04
2.6.20-15-generic

WPA works!

I had tried manually applying fwcutter before without any luck.  I removed the files I'd created and turned off ndiswrapper before following your guide. Now everything works fine. I had been stuck on this for the past two days. Thanks!

---

### Post by nanog on 2007-04-23
OK...I've gotten some requests for the compiled kernel.

Please refer to this tutorial:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

PM me for the deb.

---

### Post by mariavon on 2007-04-23
THANK YOU !!!!

IT worked on my Acer Aspire 3681 with the **Broadcom 4318**.

Can´t believe it finally works

---

### Post by inchaos on 2007-04-23
I'm still having problems.  I've got a BCM4318 (Lucky me!) in an HP pavillion laptop.
I boot up, the light for my card comes on, it detects networks and signal strengths and tries to connect.  Then, the light turns off and network manager gets stuck 'preparing wlan0 to connect to network...'  

I'm running Feisty, by the way.

---

### Post by inchaos on 2007-04-23
It works!  I seem to have made a silly error, but thank goodness I caught it.  
Thank you soooo much!  You have no idea how long I've been trying to get my wireless working.

The only thing is that no matter how strong the wireless signal, I can't seem to get a connection speed faster than 11mb/s.  In Windows I've had up to 54mb/s.  Is this a driver issue that may be resolved in the future?

---

### Post by RobN on 2007-04-24
> **spd106 said:**
> On Feisty the first few steps of this guide can be replaced with simply installing the bcm43xx-fwcutter package. It will go fetch and extract the recommended firmware for you, as long as you have another working connection.

Thanks! After two days of Linux-newbie wrangling, this was the tip that finally got me up and running! Even got on my WPA-TKIP network without any problems! Good how-to, and this tip really helped.

I should probably mention...fresh install of Feisty, on a Presario 3410 laptop with an internal Broadcom 4306.

...uh oh. Maybe I spoke too soon. Lost the wireless on restart.

Got it back again, running "sudo modprobe bcm43xx" -- so what piece am I missing that's keeping it from working on startup? I wonder if one of the changes I made earlier is coming back to bite me, but I'm not sure. After a little searching I remembered un-commenting an entry in /etc/modprobe.d/blacklist while following one "how-to" page that didn't pan out, so I commented it again, and we'll see how it goes.

---

### Post by jeditang on 2007-04-25
> **RobN said:**
> restart.

Got it back again, running "sudo modprobe bcm43xx" -- so what piece am I missing that's keeping it from working on startup? I wonder if one of the changes I made earlier is coming back to bite me, but I'm not sure. After a little searching I remembered un-commenting an entry in /etc/modprobe.d/blacklist while following one "how-to" page that didn't pan out, so I commented it again, and we'll see how it goes.

Same problem here, but good golly thank you for getting my wifi up & running.  Now i just need to figure out why I have to sudo modprobe bcm43xx everytime i boot.  Thank you thank you thank you!

---

### Post by nanog on 2007-04-26
If anyone wants the patched kernel that fixes the speed and power issues please see post below:

---

### Post by geo_saleh on 2007-04-28
thanks,

but I don't have internet connection what can I do.

I can connect to internet only via wireless connection and it's not  work.

my card is Broadcom 4312 80211a/b/g.

---

### Post by mrpeanut on 2007-04-28
> **geo_saleh said:**
> thanks,

but I don't have internet connection what can I do.

I can connect to internet only via wireless connection and it's not  work.

my card is Broadcom 4312 80211a/b/g.

Well, you're on the internet now, so would it be safe to assume that you will have access to it again?  Maybe you can get the .deb that nanog has kindly compiled and save it to some removable storage, and then gain access to it in Ubuntu.  Would this be a possible solution?

---

### Post by geo_saleh on 2007-04-29
> **mrpeanut said:**
> Well, you're on the internet now, so would it be safe to assume that you will have access to it again?  Maybe you can get the .deb that nanog has kindly compiled and save it to some removable storage, and then gain access to it in Ubuntu.  Would this be a possible solution?


yes :) 

can you pleas send for my link for the required files with instructions.

THANK YOU

---

### Post by mrpeanut on 2007-04-30
> **geo_saleh said:**
> yes :) 

can you pleas send for my link for the required files with instructions.

THANK YOU

PM Nanog, I'm sure he'd be glad to help out ;)

---

### Post by cohoking on 2007-04-30
Thank for this, I can finally see the available wireless networks. However, I still can't connect. to them. Inchaos had the same problem and said it was something small, could anyone share what that was? 

(running Edgy on Gateway **26GX, broadcom 4306 wireless)

thanks!

---

### Post by nanog on 2007-05-02
The compiled kernel for the updated problem that fixes many of the broadcom 43xx problems is back up:

[kernel/]("http://137.53.250.52/kernel/")

After extensive testing, the only issue I've found is that virtualization is broken.

---

### Post by d-base on 2007-05-02
thanks a lot
worked first time for a 2 week ubuntu user

---

### Post by rabbit20 on 2007-05-05
is it normal to have a slow connection via wireless? its taking pages a really long time to load. is there anywhere to tweek the wireless card speed? im only getting a 11mb connection to my router? any ideas?  i have a dell that is using the 1390 WLAN minicard

---

### Post by mrpeanut on 2007-05-06
> **rabbit20 said:**
> is it normal to have a slow connection via wireless? its taking pages a really long time to load. is there anywhere to tweek the wireless card speed? im only getting a 11mb connection to my router? any ideas?  i have a dell that is using the 1390 WLAN minicard

You most likely have one of the cards not fully supported by BCM43XX yet.  You can give nanog's custom kernel he posted a few posts above this one, it might solve your problem.

---

### Post by SnapCracklePip on 2007-05-07
I also got the card working no problem Dell 1390 (BCM 4311) on 64bit ubuntu.  However I also suffer from horrible performance.  11mbs limit on wireless transmition   and dl/ul speeds about 10% of what they should be. Its worse than dialup, as large files often time out after a few min.  

I think its awesome what you did making new kernal however  don't think it will help me w/ 64 bit version.  Anything else I can try?  


Thanks,
Snap

It should work ...works fine under saybayon linux and windows.  I just hate both of those OS's tho.  (Saybayon uses Gentoo portage and its a nightmare compared to Ubuntu's methods)
Im using 7.04 Fiesty ~AMD64 on a clean install + these firmware drivers

---

### Post by jscheel on 2007-05-07
I'm running amd64 and have horrible connection speed as well. Nanog, any chance on you giving us a tutorial on what you did when recompiling the kernal so that us 64-bit folks can get normal connection speeds? Thanks alot for your hard work!

---

### Post by fnorte on 2007-05-08
Before use this tutorial my wireless card it's not working, but in the Network-manager allways appear the option to use Wireless network, but without listing or connecting. 
My HP Pavilion dv1740-br laptop have a wireless button and led, and I'd can't get the led on.

Now after use this tutorial the led is on, but the network-manager doesn't show the option to Wireless Network.

I think the wireless network is now working because my iwconfig and ifconfig answer, below. 

But WHY network-manager doesn't show a option to choose and connect to a wireless netowrk??

By the way:
- Yes, I reboot!
- I am plugged with a wired connection.
- Ubuntu version is 7.04
- I didn't install ndiswrapper

```

fnorte@fnorte-laptop:/var/log$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:"fnorte@gmail.com"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

fnorte@fnorte-laptop:/var/log$ ifconfig 
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:18:FE:27:E2:CB  
          inet end.: 192.168.2.103  Bcast:192.168.2.255  Masc:255.255.255.0
          endereço inet6: fe80::218:feff:fe27:e2cb/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:3472 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:3394 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:2440783 (2.3 MiB) TX bytes:520150 (507.9 KiB)

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:80 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:80 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:6444 (6.2 KiB) TX bytes:6444 (6.2 KiB)

wlan0      Encapsulamento do Link: Ethernet  Endereço de HW 00:14:A5:B4:D7:93  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:145 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:7150 (6.9 KiB)
          IRQ:3 Endereço de E/S:0x8000 

wlan0:ava  Encapsulamento do Link: Ethernet  Endereço de HW 00:14:A5:B4:D7:93  
          inet end.: 169.254.9.182  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:3 Endereço de E/S:0x8000 

```

---

### Post by farbird on 2007-05-08
this thread's 1st post was useful..

realised feisty included the bcm43xx module but not the firmware drivers..guess copyright issues require users to get it themselves huh?

---

### Post by pixeldotz on 2007-05-16
is there quick un-install method?

i'd like to try the ndiswrapper again on ubuntu studio. though this method was quick and simple the performance is horrible. my laptop is right next to my router when i'm home and i'm only pulling 11k/sec (20 minutes to download a 13.5 meg file).

or can i just do the ndiswrapper method with my bcm4311 windows driver without worries?

---

### Post by nanog on 2007-06-03
This tutorial is very detailed:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by bruce.hobson on 2007-07-04
Thanks this solution it fixed my problem. And I'm using my wireless for this reply. 

Oh, a bit of information for others:

Ubuntu 7.04 on a HP Laptop DVD9225us.

By the way. My Wireless light on the front of my laptop would not light, in Windows or Linux. HP sent out a new wireless card. Still no light. Sent the laptop in for repear and now I have a wireless light. 

Moreover, only after your solution do I now have Internet by wireless.

Bruce
7/4/07

---

### Post by nanog on 2007-07-09
Update on bcm4311

I recently noticed that Ubuntu compiled kernel 2.6.22 for gutsy. 
Added gutsy main to sources.list.
Downloaded the kernel and header files. 
***Very important: Do no forget to remove gutsy repos from your sources!
I then restarted and...

My dell 1390 bcm4311 now has no powe/transmission issues. 

Woo hoo!

---

### Post by JoeBob Hankey on 2007-07-14
Thank you for the information.  Ndiswrapper would not work for me on a clean install of Ubuntu 7.04, regardless of the version of Broadcom wireless driver I used for my HP Pavillion ZD7260.  

Your information on installing native drivers got me up and running.

Thanks again!

JBH

---

### Post by Mr. Win on 2007-07-14
Worked great for my Compaq R3000 using 4306... Thanks!

---

### Post by t4thfavor on 2007-07-14
Theres a thread here with an attached fwcutter, and the firmware, for those who have no internet connection.

[http://ubuntuforums.org/showthread.php?t=500737](http://ubuntuforums.org/showthread.php?t=500737)

---

### Post by DenKain on 2007-07-18
I'm using 7.04 and this tut almost worked for me. My problem is whenever I restart my laptop it forgets all about the wireless card until I enter this command into the terminal: "sudo modprobe bcm43xx". After I enter that it works just fine. I hate to say it but I just started using Ububtu over the weekend and I really know nothing about this command or what I should do.

---

### Post by kevdog on 2007-07-18
Could you post the contents of your /etc/modprobe.d/blacklist file??

Thanks

---

### Post by DenKain on 2007-07-18
Your correct it was listed in the "blacklist" file but at the time I had no idea that file existed. I solved my problem by adding "sudo modprobe bcm43xx" to my "rc.local" file.

---

### Post by kevdog on 2007-07-18
You could do that or simply delete or comment (# sign) the line where it states > blacklist bcm43xx

---

### Post by NJHokie on 2007-07-24
On this issue:
All I did to get it working was install the fwcutter program in synaptic, restart, and disable the wired connection.  I have a broadcom 4309 chipset.  This was with a clean install.
Before I was trying to go to this from trying ndiswrapper without success.  That may have been screwing things up.

What kind of connection speed are you guys getting.  My is stating 11mb/s.  Should I try the kernel update to boost it up?  Does anyone have a link to do so?

thanks,
Nick

---

### Post by qamelian on 2007-07-24
> **NJHokie said:**
> What kind of connection speed are you guys getting.  My is stating 11mb/s.  Should I try the kernel update to boost it up?  Does anyone have a link to do so?

thanks,
Nick

If you use the bcm43xx-fwcutter method, your speed will always max at 11Mb/s. This is currently a limitation of the open-source kernel support for these NICs. At the moment, the only way to 54Mb/s is to use the NDISwrapper tool to install the native Windows drivers.

---

### Post by nanog on 2007-07-25
Actually the bcm43xx driver works at 54 mbs in 2.6.21+. Ndiswrapper is not required.

---

### Post by kevdog on 2007-07-25
> Actually the bcm43xx driver works at 54 mbs in 2.6.21+. Ndiswrapper is not required.

I thought the debian version of the bcm43xx driver had not yet been released.  Is there a link you can post that confirms this statement?

---

### Post by qamelian on 2007-07-25
> **nanog said:**
> Actually the bcm43xx driver works at 54 mbs in 2.6.21+. Ndiswrapper is not required.

Not on my laptop it doesn't. I tested this and the bcm43xx driver is still maxing out at 11. This is with a clean install of Gutsy tribe 3 with the latest updates. Switching to ndiswrapper takes me back up to 54.

---

### Post by Ayuthia on 2007-07-25
The Broadcom 43xx site says that the 4311 is now supported for kernel 2.6.20.6 and later.

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

From the devices list, it does not look like all Broadcom cards are going past the 11 Mb.  I also was able to see 54Mb using a 4311 card on Gutsy Tribe-1, but I have not tested it again on tribe-3.

---

### Post by dexterbt1 on 2007-07-25
Hey, thanks for the guide, it works perfectly on my Presario v2000's bcm4318. 

I was using ndiswrapper before this but WPA was not working. Thanks to you, I got it to work! 

:guitar:

---

### Post by MrMatty on 2007-07-29
Thank You!, Thank You!, Thank You!  After nearly pulling out the last remaining hairs on my head trying to get my wlan working using all of the other tutorials yours worked flawlessly.  I can now use Linux for good and free up a valuable partition on my drive!

---

### Post by AiBo on 2007-08-08
> **nanog said:**
> Thanks for the tutorial...I was dreading using ndiswrapper. I wanted to report that it worked on a Dell e1405/640m in Feisty beta. 

I want to respond to the previous poster. I consider well-integrated wifi to be essential to an Ubuntu install on a laptop.


Proof that someone got it to work on my system!!!

I am running a clean install of Fiesty on a Dell e1405, well mostly clean!  I did try the ndiswrapper attempt first at: [http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+inspiron+E1405](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+inspiron+E1405)

Then I came across this howto ... tried it but to know avail!   All goes well until:

ai@ai-laptop:~$ sudo modprobe bcm43xx
ai@ai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Any suggestions?

---

### Post by R-Dot-Yung on 2007-08-26
omfg i love you i freaking love you, you dont understand how long ive been trying to make my D600 laptop wireless, i freaking love you

---

### Post by BigD77 on 2007-09-07
I did that and it worked.....Sorta.  The light lights up, and it "sees" networks available, but it doesn't connect to any.  I was at a mall that had free WiFi access, and no dice.  Is there some other configuration that needs to be done?

I have the Broadcom 4311 using Feisty Fawn.

---

### Post by vincentvee on 2007-09-08
man, you are my hero, i been working on ndiswrapper all day with no luck, now i got just what you said.....wireless bliss
great how-to
just a shame it took me so long to find it
really well done
also, you said it worked for edgy.....i'm running feisty and its fine

---

