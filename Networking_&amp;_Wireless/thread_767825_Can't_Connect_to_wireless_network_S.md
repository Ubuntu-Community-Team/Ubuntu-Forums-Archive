---
title: "Can't Connect to wireless network :S"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by JULEZAH on 2008-04-25
Ok, i'm new to the linux world, and i just got my  Netgear WG 311v3 wireless card working, via ndiswrapper.

The problem is this:
I can see the wireless network i want to connect to.
I click connect, change the type to TKIP (this is WPA Personal, btw) and then put in the password.
It seems to do something for a minute or so, then i get the input password screen again :S

I don't know what other information to give, so just ask :D

Any ideas ?

---

### Post by ajmorris on 2008-04-25
It asking for the password again usually means the password is incorrect. If you are certain you are typing it correctly, consider changing the password in the router.

AJ

---

### Post by JULEZAH on 2008-04-25
I'm sure the password is right.

Whenever i put the password in, the dialogue box appears again.

I NEED HELP!

---

### Post by HunterThomson on 2008-04-25
Have you looked into other drivers available? Maybe try v2... after reading what has changed.... I think I remember reading about a driver wrapper other then ndiswrapper. Maybe, try that....

---

### Post by JULEZAH on 2008-04-25
mmm well i've got the v3 version of the card, which sucks basically.
They changed the chipset to Marvel, so you have to use ndiswrapper.

hmmm....

tricky stuff.

---

### Post by HunterThomson on 2008-04-25
I'll spend some time right now looking and report back... 

Are you using 64bit or 32bit?

---

### Post by JULEZAH on 2008-04-26
oooo thanks !

32-bit.

---

### Post by HunterThomson on 2008-04-26
Cool, give me a sec... hopfuly we will be able to put it into Monitor mode and do Packet injection too:) 

Also, try and change the password on your router gust to cover your bases and  use WPA not WPA2 or vice versa. And try a different encryption like AES or why not use WEP? I know it is week but it will still stop people from randomly using your AP.

---

### Post by HunterThomson on 2008-04-26
Here is an alternative driver that is suppose to be better. It is not the official NetGear driver... Still need to use Ndiswrapper

[http://www.trendware.com/fr/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=690#](http://www.trendware.com/fr/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=690#)

Have you tried to configure your driver in the terminal with 

iwconfig

Owe. I mite be on to something here I am looking at

[http://www.jimbo7.com/wiki/index.php?title=WG311v3#WPA-PSK_Passkey](http://www.jimbo7.com/wiki/index.php?title=WG311v3#WPA-PSK_Passkey)

You mite need to install wpa_supplicant with sudo apt-get install wpa_supplicant...

---

### Post by JULEZAH on 2008-04-26
I've used iwconfig.

But configuring it?
nope :S

---

### Post by HunterThomson on 2008-04-26
Ya, just read through that page try it out and report back.... It looks to me to be a complete guide and should work well. Ubutnu is a Debian based OS.

[http://www.jimbo7.com/wiki/index.php?title=WG311v3#WPA-PSK_Passkey](http://www.jimbo7.com/wiki/index.php?title=WG311v3#WPA-PSK_Passkey)

---

### Post by JULEZAH on 2008-04-26
I did that, until the part where you scan.

Terminal just did nothing.

---

### Post by HunterThomson on 2008-04-26
ok one sec i am eating...

Ok I am back now. really did nothing???? Like nothing nothing??? Click on the network conettion icon on the top bar and see if it shows any networks. 

also try ifconfig -a and see if it shows your wireless driver. Then try iwconfig Wlan0 up or was it ifconfig Wlan0 up... well try them both that order if the first one didn't work. Then try the command

iwlist wlan0 scan

again

---

### Post by HunterThomson on 2008-04-26
Then report back.... Make sure you can get a signal from the router like sit right next to it to cover your bases.

---

### Post by JULEZAH on 2008-04-26
Stiiiil nothing.

I have now deleted that driver and reverted back to the old Marvel one.
At least i am closer to the target :P

---

### Post by HunterThomson on 2008-04-26
Ya that sounds like a good idea. So this one dose see network you just can't connect to the wpa right... To tell you the truth it would be a whole lot EZ'r to just change your router to WEP.... Do you have a reason why you would not want to do this? In any case try and install that wpa-supplicant.

sudo apt-get install wpa-supplicant

and configure it.... then report back.

The thing with this is that you should be able to connect to wpa with the driver you are now running... But do it anyway. Also, go to your routers HTTP configuration page and make sure everything is set up the way you think it is. I think it mite not be a problem with your driver at all.

---

