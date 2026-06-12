---
title: "Broadcom BCM43xx on Ubuntu 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by sbrbot on 2008-04-26
Ubuntu 8.04 has new b43 driver for Broadcom wireless cards. Ndiswrapper is not needed anymore. b43 driver (module) uses Broadcom card firmware for running wireless card. Problem with Broadcom cards is that Broadcom company copyrighted its wlan firmware and it is not distributed with Ubuntu. Wireless card (b43 module) will not work without this firmware. Here is one way how one can easily install Broadcom firmware:

1) connect your computer to Internet using ethernet connection

2) using Synaptic Package Manager install b43-fwcutter tool

This tool is used for extracting Broadcom firmware that b43 module needs.

At the end of b43-fwcutter installation procedure Configuration of b43-fwcutter will be initiated where you will be asked whether to "Fetch and extract firmware" - answer Yes, of course.

PICTURE#1

After installing b43-fwcutter tool, in background a script will start which will from internet (that's why you need ethernet connection) automatically download Broadcom libraries containing needed firmwares, b43-fwcutter will extract firmwares in /lib/firmwares directory and finally you should only restart you computer.

PICTURE#2

3) you should blacklist ndiswrapper and old bcm43xx drivers if they were not blacklisted already in /etc/modprobe.d/blacklist file.

4) in Network-Manager (icon with two screens in upper right corner) setup needed connection data in order to connect to your Access Point

PICTURE#3 and PICTUR#4

That's it folks!

HTH

---

### Post by sbrbot on 2008-04-26
If you look in System->Administration->Hardware Drivers you should get this:

---

### Post by dicecca112 on 2008-04-26
You should warn users that they will not get the full 54G speeds.  You can only achieve this with ndiswrapper

---

### Post by bagelong on 2008-04-26
Can you give me more terminal commands for getting into the blacklist file?  Also, are there any others that should be blacklisted?

---

### Post by brew1brew on 2008-04-26
also note that this does not work for everyone. It does not work for my laptop, compaq f579. ndiswrapper instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") work fine for me. I did have to use the "Hardy Bug Fix".

---

### Post by TubaTodd on 2008-04-27
> **bagelong said:**
> Can you give me more terminal commands for getting into the blacklist file?  Also, are there any others that should be blacklisted?

sudo nano /etx/modprob.d/blacklist

You can substitute gedit for nano if your want.

---

### Post by nullmind on 2008-04-27
b43 causes a userspace process (named "b43") to exist. The process takes up a lot of time, and has a nice of -5!

I explain my irritation with b43 and how to replace it via ndiswrapper, including workarounds for bugs that existed since the start of the Hardy beta in a blog post: [http://devangelist.blogspot.com/2008/03/ubuntu-804-beta-hardy.html](http://devangelist.blogspot.com/2008/03/ubuntu-804-beta-hardy.html)

---

### Post by sbrbot on 2008-04-27
> **brew1brew said:**
> also note that this does not work for everyone. It does not work for my laptop, compaq f579. ndiswrapper instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") work fine for me. I did have to use the "Hardy Bug Fix".

It's not so important which laptop you have but which wireless card (chip) you have. Which one is yours? What is happening when you try to install b43-fwcutter and firmware as explained?

"Hardy Bug" is about ssb catching wlan before ndiswrapper where you should setup your system in order ndiswrapper catch wlan first. When one uses b43 instead ndiswrapper this bug does not matter.

---

### Post by nullmind on 2008-04-27
While the "Hardy bug" dealing with ssb obviously doesn't affect b43, I don't know if it affects bcm43xx. This was my motivation for the post above.

---

### Post by amir1979 on 2008-04-27
i need help please this didnt work for me or i didnt do it correctly...  im a noob! lol nvr really used linux/ubuntu before

---

### Post by TrevP on 2008-04-27
> **brew1brew said:**
> also note that this does not work for everyone. It does not work for my laptop, compaq f579. ndiswrapper instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") work fine for me. I did have to use the "Hardy Bug Fix".

Hi,

I used this method (including the Hardy bug fix) and it worked very well. Unfortunately, after entering the lines to make the fix permanent, after rebooting the computer, there is no facility anymore to connect to a wireless network although the network appears when "Edit wireless networks" is selected.

Any help would be gratefully accepted. It's frustrating to see the network but not connect to it. Is there any way to make my system see the device again so that it is visible when I click on system>administration>network?

Trev

Trev

---

### Post by nullmind on 2008-04-27
> **TrevP said:**
> Hi,

I used this method (including the Hardy bug fix) and it worked very well. Unfortunately, after entering the lines to make the fix permanent, after rebooting the computer, there is no facility anymore to connect to a wireless network although the network appears when "Edit wireless networks" is selected.

Any help would be gratefully accepted. It's frustrating to see the network but not connect to it. Is there any way to make my system see the device again so that it is visible when I click on system>administration>network?

Trev

Trev
What is your output of **ndiswrapper -l**?

---

### Post by JoshLukas on 2008-04-27
Hello. I have a similar problem. On Friday I upgraded my parents' system to hardy x64. Well. After my mother screwd up the upgrade process while installing, I made a clean installation. So far so good. Everything works fine now, except the wireless card. It's a Linksys WMP54G card, based on a broadcom bcm4306 chipset. I just can't get it to work. Under Gutsy x64 everything went all right out of the box.
Is there a special card you can recommend to buy? After two days I just want the wireless network to work. There is a conceptronic C54Ri PCI card that should work with ubuntu out of the box, but it only offers WPA and no WPA2 encryption. Is it worth it to buy that card? Will it really work out of the box? Or if there is a way on how I can get my Linksys card to work easily, then please just let me know.


best regards,

Josh

---

### Post by brew1brew on 2008-04-28
> **sbrbot said:**
> It's not so important which laptop you have but which wireless card (chip) you have. Which one is yours? What is happening when you try to install b43-fwcutter and firmware as explained?

"Hardy Bug" is about ssb catching wlan before ndiswrapper where you should setup your system in order ndiswrapper catch wlan first. When one uses b43 instead ndiswrapper this bug does not matter.

Sorry, I have the 4311 mini pci rev 02, and with my laptop I had to compile ndiswrapper to make it work Feisty. I removed it and tryied the b43-fwcutter and it did not work, so I recompiled and installed ndiswrapper again. all is good for me.

---

### Post by brsmnky007 on 2008-04-28
Since upgrading to Hardy my wireless (with Broadcom 4306) is also broken.  I don't have ready access to ethernet , but installed fwcutter without incident from the install disc and added the module.  I have tried allowing nw-manager configure the connection and also configured it manually, both without success; connection just repeatedly times out.  Any advice?  Thanks in advance.

P.S.  I have also read through most of these posts; I ensured that the old BCM43xx drivers were blacklisted, etc...

---

### Post by unMourned on 2008-04-28
I finally lugged :) my laptop down to my wireless router and followed your recommendation @ [http://ubuntuforums.org/showpost.php?p=4805938&postcount=1](http://ubuntuforums.org/showpost.php?p=4805938&postcount=1)

...and now I am in Ubuntu, posting on ubuntuforums.org!!!!   woo woo

I just updated the drivers for my video card, and enabled max visual effects and WHOA.

This Ubuntu thing might work, after all...

Neat!

Thank you, sbrbot!

-Paul

---

### Post by grumpylad77 on 2008-04-28
[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html")

try this guide.. it works perfectly for me

---

### Post by unMourned on 2008-04-28
In fact, though the bw43cutter method leads to a 1 Mb/s connection speed, I just obtained this test result from dslreports.com:

[IMG]http://www.dslreports.com/im/49974034/7205.png[/IMG]

...which is within spitting-range of testing through XP drivers.  \\:D/

I'd say that Ubuntu Hardy Heron is quickly growing on me....  :D

-p

---

### Post by mattbytes on 2008-04-29
Thanks!  I'll need to give this a try later.  I installed Ubuntu on my Dell D600, but wireless no workie.  Hopefully, this fixes it.

---

### Post by mikeymo1741 on 2008-04-29
I've noticed that when using my 4318 rev.2 via b43 on an unsecured network, there is no problem at all.   

When I use it at home on my WEP-enabled system, it drops the connections a couple of times, and then will not reconnect at all. 

Back to work, and it hooks right up to the unsecured network without a sniffle.  

I don't know if that tells anyone anything.   it seems to tell me it's a bad driver, but who knows?

---

### Post by aerotjk on 2008-04-29
> **mikeymo1741 said:**
> I've noticed that when using my 4318 rev.2 via b43 on an unsecured network, there is no problem at all.   

When I use it at home on my WEP-enabled system, it drops the connections a couple of times, and then will not reconnect at all. 


I just discovered the same thing.  Changed my router to WPA security from WEP and I too am writing this on the wireless connection now with the B43-fwcutter.

---

### Post by unMourned on 2008-04-30
> **aerotjk said:**
> I just discovered the same thing.  Changed my router to WPA security from WEP and I too am writing this on the wireless connection now with the B43-fwcutter.

ah-HA!  I tried WEP with my bcm4318 (b43-fwcutter)--no connection.  I will now try WPA.

Any recommendation on the type of WPA to run?  WPA-PSK, AES or TKIP?

Thanks,

Paul

---

### Post by SomeGuy1 on 2008-04-30
> **brsmnky007 said:**
> Since upgrading to Hardy my wireless (with Broadcom 4306) is also broken.  I don't have ready access to ethernet , but installed fwcutter without incident from the install disc and added the module.  I have tried allowing nw-manager configure the connection and also configured it manually, both without success; connection just repeatedly times out.  Any advice?  Thanks in advance.

P.S.  I have also read through most of these posts; I ensured that the old BCM43xx drivers were blacklisted, etc...

I'm having a very similar problem. I was able to get fwcutter installed and the drivers set with only a bit of trouble, but now my machine simply won't connect to my network. It just times out, despite detecting the network. Anyone have any ideas?

---

### Post by fz43mw on 2008-05-05
I also found bw43cutter works for me!!!

Upgraded from 7.10 and it was a no-go - soooowent for a clean install and it worked! I'm using WPA on a AMD 64 Athlon and a Broadcom 4318 rev 02.

It has been working for 10 days, only one problem so far, this morning I lost the cingular style signal bar icon in upper right corner for the monitor on monitor icon. How do I get the former back?????

I'm beginning to become a convert for Ubuntu over Win XP

---

### Post by jsattin on 2008-05-05
Hi. My wireless card uses the BCM4318 rev.2 chipset. I installed B43-fwcutter as directed, and confirmed in "Hardware Drivers" that it is enabled. I manually configured the wireless connection with my SSID and WPA2 password. I rebooted the computer.  The "link" light on my card is solid green, which I think is a problem, since it's usually off (if no connection) or blinking irregularly (if data are being transmitted). Needless to say, I was unable to access the internet.

I disabled and then re-enabled B43-fwcutter and went through the above steps again, but to no avail.

Any suggestions?  I'd like to exhaust the B43 route before trying NDIS wrapper, since I'm new at this and it looks even more complicated . . .

Thanks.

---

### Post by RequinB4 on 2008-05-06
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Has some information on blacklisting modules (I know it's ndiswrapper) if you have multiple ones installed (so you can get the correct driver loaded)

---

### Post by Ayuthia on 2008-05-06
> **jsattin said:**
> Hi. My wireless card uses the BCM4318 rev.2 chipset. I installed B43-fwcutter as directed, and confirmed in "Hardware Drivers" that it is enabled. I manually configured the wireless connection with my SSID and WPA2 password. I rebooted the computer.  The "link" light on my card is solid green, which I think is a problem, since it's usually off (if no connection) or blinking irregularly (if data are being transmitted). Needless to say, I was unable to access the internet.

I disabled and then re-enabled B43-fwcutter and went through the above steps again, but to no avail.

Any suggestions?  I'd like to exhaust the B43 route before trying NDIS wrapper, since I'm new at this and it looks even more complicated . . .

Thanks.
You might want to try to connect without encryption first just to see if you can connect.  Once you have that figured out, put the encryption back.

---

### Post by bobbins on 2008-05-06
> **mattbytes said:**
> Thanks!  I'll need to give this a try later.  I installed Ubuntu on my Dell D600, but wireless no workie.  Hopefully, this fixes it.

If you ever get this working then let me know. I am heading into working on this for a week and I consider myself to know a little about computers. Of course, if I find a working fix for my Dell laptop which is exactly the same as yours I will post back.

I have had no luck so far other than it working via Ethernet.

---

### Post by jsattin on 2008-05-07
> **Ayuthia said:**
> You might want to try to connect without encryption first just to see if you can connect.  Once you have that figured out, put the encryption back.

Thanks for the good suggestion.  It appears that for my connection to work, 1) The SSID broadcast needs to be enabled (I had previously disabled it for security) and 2) I need to be in roaming mode; manual configuration seems not to work.

This is reasonably acceptable, but if anyone knows a solution to the above, it would be much appreciated.

---

### Post by Dhammikae on 2008-05-17
After so much googling this forum helped me to get my WMP54G working (Broadcom 4306 rev 03) using Ndiswrapper. I had to reinstall Hardy and not touch out of the box b43 driver. I appreciate Nullmind and brew1brew for showing me the correct direction. I also had to deal with the so called Hardy bug.
As some one pointed out I also cannot do a manual connect but roaming works OK. Good for now. 

D

---

### Post by Ayuthia on 2008-05-17
> **jsattin said:**
> Thanks for the good suggestion.  It appears that for my connection to work, 1) The SSID broadcast needs to be enabled (I had previously disabled it for security) and 2) I need to be in roaming mode; manual configuration seems not to work.

This is reasonably acceptable, but if anyone knows a solution to the above, it would be much appreciated.You might try installing Wicd.  It is a different wireless manager.

---

### Post by Dhammikae on 2008-05-22
I tried Wicd but that program alone could not get the card working. It can see the networks but would not connect. Finally I found a post [here]("http://ubuntuforums.org/showthread.php?t=426598")
and instead of "ra1" I subsituted "wlan0" and now Wicd is working like a charm. I simply wish I did not have to edit those files and Wicd can do that too. Now I can get a Fixed IP and use hidden SSID. Thanks for the suggestions.

---

### Post by Steve413z on 2008-05-23
If you are still having problems getting fwcutter to work with a broadcom card, try this, it worked for me:

[http://ubuntuforums.org/showthread.php?t=803986](http://ubuntuforums.org/showthread.php?t=803986)

---

