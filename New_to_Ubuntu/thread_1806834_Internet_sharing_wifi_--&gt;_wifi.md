---
title: "Internet sharing wifi --&gt; wifi"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by giannakis on 2011-07-18
how to share internet from my pc to smart phone help !!!!!!
I have ubuntu 11.04 and try many guide from google (share internet) but i failed 

this is what i want to do :[ATTACH]197748[/ATTACH]

router --> wlan1/pc/wlan2 ---> iphone

router:Belkin N+
wlan1:rtl8188s(r8712u)
wlan2:ralink 2573 usb rt73 usb
pc:Toshiba qosmio g50 11s
iphone:3gs

*I am from Greece and my English is not good*

---

### Post by amjjawad on 2011-07-18
> **giannakis said:**
> how to share internet from my pc to smart phone help !!!!!!
I have ubuntu 11.04 and try many guide from google (share internet) but i failed 

this is what i want to do :

router --> wlan1/pc/wlan2 ---> iphone

wlan1:rtl8188s(r8712u)
wlan2:ralink 2573 usb rt73 usb
pc:Toshiba qosmio g50 11s
iphone:3gs

*I am from Greece and my English is not good*

Hello and Welcome, Greek friend :)

Please note that it has nothing to do with your PC. You need to check your router. Perhaps you need to change the range of IP address. I had the same issue as I have many devices connecting to the same router so I increased the IP range and it works :)

Good luck :)

---

### Post by giannakis on 2011-07-18
> **amjjawad said:**
> Hello and Welcome, Greek friend :)

Please note that it has nothing to do with your PC. You need to check your router. Perhaps you need to change the range of IP address. I had the same issue as I have many devices connecting to the same router so I increased the IP range and it works :)

Good luck :)
[thanks for your time mr amjjawad]("http://ubuntuforums.org/member.php?u=941822") i miss to write about my router it's Belkin n+!!
change the range of IP address???how ???

when I do it with windows works flawlessly without any change to router


*perhaps I am not understood i want to make adhoc share internet conection through my pc to iphone*

---

### Post by amjjawad on 2011-07-18
> **giannakis said:**
> [thanks for your time mr amjjawad]("http://ubuntuforums.org/member.php?u=941822") i miss to write about my router it's Belkin n+!!
change the range of IP address???how ???

when I do it with windows works flawlessly without any change to router


*perhaps I am not understood i want to make adhoc share internet conection through my pc to iphone*

Hi again :)

I do have the same Router. Give me few mins. I'll have a look and will come back to you, okay?

---

### Post by amjjawad on 2011-07-18
Hi again,

First thing you need to do is to Open your Browser, I assume Firefox is your default browser.

On the address, please type : 192.168.2.1

Then, login with the admin password for your router

Go to LAN Settings

And set something like the attached screen shot.

Hope that will help you.

Let me know if you need more help ;)

---

### Post by giannakis on 2011-07-18
> **amjjawad said:**
> Hi again,

First thing you need to do is to Open your Browser, I assume Firefox is your default browser.

On the address, please type : 192.168.2.1

Then, login with the admin password for your router

Go to LAN Settings

And set something like the attached screen shot.

Hope that will help you.

Let me know if you need more help ;)
don't work :(

---

### Post by amjjawad on 2011-07-18
> **giannakis said:**
> don't work :(

Are you able to connect to your Wireless Router from a Laptop or a PC?

---

### Post by giannakis on 2011-07-18
> **amjjawad said:**
> Are you able to connect to your Wireless Router from a Laptop or a PC?
yes i connect with my pc using wlan1(rtl8188s) this moment now

---

### Post by amjjawad on 2011-07-18
> **giannakis said:**
> yes i connect with my pc using wlan1(rtl8188s) this moment now

If you followed the steps I posted before then you should be able to connect.

Perhaps there is something wrong with your iPhone? I don't have one and I have no idea how to connect it to a Wireless Router.

---

### Post by giannakis on 2011-07-18
> **amjjawad said:**
> If you followed the steps I posted before then you should be able to connect.

Perhaps there is something wrong with your iPhone? I don't have one and I have no idea how to connect it to a Wireless Router.
thank's for your time friend i try with another phone or pc:)
when i connect to my modem router directly from my iphone everything it's ok
:)*i follow this guite [https://help.ubuntu.com/community/Internet/ConnectionSharing ]("https://help.ubuntu.com/community/Internet/ConnectionSharing%29*")
**Wireless Ad-Hoc connection sharing scenario**

and dont work* :(

---

### Post by MartyBuntu on 2011-07-18
You don't need an ad-hoc connection...just configure your phone with your router's security settings.

This is *your* router and *your* internet service, correct?

---

### Post by giannakis on 2011-07-18
> **MartyBuntu said:**
> You don't need an ad-hoc connection...just configure your phone with your router's security settings.

This is *your* router and *your* internet service, correct?
hello [MartyBuntu]("http://ubuntuforums.org/member.php?u=704369") the router it's 1 km away That's why I want adhoc connection check the picture [ATTACH]197749[/ATTACH]

when I do it with windows works flawlessly

---

### Post by MartyBuntu on 2011-07-18
And why would your router be 1 KM away?

---

### Post by amjjawad on 2011-07-18
> **MartyBuntu said:**
> And why would your router be 1 KM away?

I think it's a typo :)

---

### Post by giannakis on 2011-07-18
> **MartyBuntu said:**
> And why would your router be 1 KM away?
:) because it's my fiancee router ;)

---

### Post by jerome1232 on 2011-07-18
I doubt using your laptop as a range booster will cover an entire Kilometer, If a router is sitting in an unobstructed field it should cover around 250m, I doubt a wireless card on a laptop would even double that. Throw in some walls and etc and your range is even shorter.

---

### Post by giannakis on 2011-07-18
:)i have thi's baby's [ATTACH]197755[/ATTACH] :)

---

### Post by giannakis on 2011-07-18
> **jerome1232 said:**
> I doubt using your laptop as a range booster will cover an entire Kilometer, If a router is sitting in an unobstructed field it should cover around 250m, I doubt a wireless card on a laptop would even double that. Throw in some walls and etc and your range is even shorter.

in my area all buildings do not exceed two floors and both my router and wlan card it's on the roof!!!!
i use 15 feet usb cable to connect wlan N and yes it's work for me without booster amplifier

---

### Post by MartyBuntu on 2011-07-18
> **giannakis said:**
> :) because it's my fiancee router ;)

I'm pretty sure your fiance's ISP does not allow for the type of internet "sharing" you're asking about. Most certainly a violation of their terms of service.

And with that, this thread should be put to rest.

---

### Post by giannakis on 2011-07-18
:)  Ok I do it with windows for awhile i hope community
 find a solve as soon as possible :P

---

### Post by amjjawad on 2011-07-19
> **giannakis said:**
> :)  Ok I do it with windows for awhile i hope community
 find a solve as soon as possible :P

What did you do exactly? Could you explain that please?

---

### Post by jerome1232 on 2011-07-19
Is you card in this list of cards that support adhoc networking under Ubuntu? 


[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I don't have any experience setting these kind of connections up, but do check that so we know we aren't trying something that won't work with your card. There are also how to's for the various cards.

---

### Post by giannakis on 2011-07-19
> **amjjawad said:**
> What did you do exactly? Could you explain that please?
first I connect my computer to the router with wlan1 then I make Adhoc in wlan2 to share internet!! I can connect with my ihone but I do not have Internet on iphone thi's is what i am do
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by giannakis on 2011-07-19
> **jerome1232 said:**
> is you card in this list of cards that support adhoc networking under ubuntu? 


[https://help.ubuntu.com/community/wifidocs/wirelesscardssupported](https://help.ubuntu.com/community/wifidocs/wirelesscardssupported)

i don't have any experience setting these kind of connections up, but do check that so we know we aren't trying something that won't work with your card. There are also how to's for the various cards.
[attach]197809[/attach]

---

