---
title: "British Gas remote heating control Hive"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by SteveTyrer on 2015-11-21
Hi
This is a bit of a strange one I am running the following
Ubuntu 15.10 64-bit
Dell Vostro 1500
Internet router= BT Home hub 3
Google chrome [COLOR=#303942][FONT=Ubuntu]Version 46.0.2490.86 (64-bit)
[/FONT][/COLOR]Based in the UK

I have a British Gas remote heating control "Hive" that enables me to control my home heating over the internet, when I try to change setting from my Ubuntu laptop 
it gives a error if I use a windows computer (Google chrome) on my home network it works (sorry about naming MS product on this sites:-(

I have reset to default the chrome setting on Ubuntu with no success, also tried Firefox and Chromium with no luck
The windows machine is connected with a Ethernet cable and the laptop over WiFi, so tried the laptop with a Ethernet cable but still with no luck.

At a bit of loss now, can anyone Help

Steve

---

### Post by brian-mccumber on 2015-11-21
I am thinking the web app probably uses the .net framework which is present on your Windows computer but not on the Ubuntu computer.

Since this is a problem with their website, you should contact British Gas with your problem since it's not really an issue with Ubuntu.


But a couple questions here:

What error is it giving you when you use Ubuntu? 

Is your Windows computer 64 bit also?

---

### Post by SteveTyrer on 2015-11-21
Thanks for your response

This is the first error

"Apologies unable to connect right now"

then some times "internal database error" (or something close to this)

The windows m/c is 8.1 64bit

On the Ubuntu laptop I am running Mono so I can run a program called CamBam.

---

### Post by brian-mccumber on 2015-11-21
Well here is an archived ask Ubuntu question pertaining to this - [http://ubuntuforums.org/archive/index.php/t-2216043.html](http://ubuntuforums.org/archive/index.php/t-2216043.html)

It seems the website is using something that requires IE to be installed to work correctly. In the link above there is mention of an add-on for Firefox that fools the website into seeing IE, you could try that.

I think your best bet would be to contact British Gas support and tell them about your issue since it is obviously a problem with the website and not Ubuntu. They will probably tell you Windows and or IE is required for their website most likely due to them using something from the .net framework installed with Windows but it would be best if you heard it from them.

---

### Post by SteveTyrer on 2015-11-21
Thanks Brian, that make perfect sense, I will contact BG for what good it will do!
again thanks for your help  

Steve

---

### Post by brian-mccumber on 2015-11-21
No problem, glad to be of assistance.

I would like to hear about what they tell you after you contact them tho, for curiosities sake.

---

### Post by SteveTyrer on 2015-11-21
Hi Brian

Had a quick response but as expected as much use as a chocolate tea pot

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[FONT=arial]Hi Steven[/FONT]

[FONT=arial]Thanks for contacting us and for bringing this to our attention.[/FONT]

[FONT=arial]I think the best thing to do would be to post your feedback on our product forum. In the Hive app under Help & Support you'll find Product ideas, this lets you post suggestions for developing Hive.[/FONT]

[FONT=arial]Regarding a time when Hive will be compatible over all computer systems, I really couldn't give you a specific time-scale for this.[/FONT]

[FONT=arial]Thanks again for getting in touch Steven[/FONT]

[FONT=arial]Colin[/FONT]
[FONT=arial]Hive Digital[/FONT]

---

### Post by brian-mccumber on 2015-11-22
Chocolate tea pot, heheh.

> [COLOR=#000000][FONT=arial]Regarding a time when Hive will be compatible over all computer systems, I really couldn't give you a specific time-scale for this.[/FONT][/COLOR][COLOR=#000000][FONT=arial]

It seems that the site is only compatible with Windows at this time which is what I suspected. If you have a smart phone they have an app that you could use to control your heating remotely.[/FONT][/COLOR]

---

