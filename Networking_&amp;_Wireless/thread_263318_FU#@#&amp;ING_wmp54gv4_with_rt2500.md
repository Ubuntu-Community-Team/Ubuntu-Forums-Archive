---
title: "FU#@*#&amp;ING wmp54gv4 with rt2500"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by Quacker on 2006-09-23
I have just installed 6.06 and have been fighting it ever since.
 
I have been going at this for hours, first starting out with the ndiswrapper which I guess isnt nessesary. Then looking through all the tutorials that you have to download driver updates or what ever.

I have no wired connection (This is from a neighboors computer)

I need to get this wireless working and I dont need wpa since all the tutorials for my card uses wpa.

Anybody who can give some simple strait forward instructions to get this card to connect to my network will be greatly appreciated. 

thanks

---

### Post by wieman01 on 2006-09-23
I have a WUSB54G V4 and only could get it working with "ndiswrapper". I gave up on rt2xxx, the driver is a bl..dy pain.

When you install the Windows driver using "ndiswrapper" make sure all driver files are in the same directory (*.inf, *.cat, etc.) when you deploy the *.inf file. A lot of people fall into the same trap and eventually end up in the forums.

Once you card has been recognized we can continue with the rest. Piece of cake... If you don't need WPA it's even simpler.

---

### Post by wieman01 on 2006-09-23
And one more piece of advice... Bad language is not appreciated in here. The administrators keep an eye on posts like this. This is not the right way to draw attention.

---

### Post by tonab on 2006-10-06
> **wieman01 said:**
> 
When you install the Windows driver using "ndiswrapper" make sure all driver files are in the same directory (*.inf, *.cat, etc.) when you deploy the *.inf file. A lot of people fall into the same trap and eventually end up in the forums.

Once you card has been recognized we can continue with the rest. Piece of cake... If you don't need WPA it's even simpler.

i have a similar problem with my usb adapter i have deployed the inf and its reqognised by ndiswrapper,my question is can you eloborate further on how would one know the proper directory the .cat .sys files should by in.and or where i should move these files too.

---

### Post by wieman01 on 2006-10-06
You don't need to move the files at all. "ndiswrapper" will move the necessary files to this folder:
> /lib/firmware
You don't have to do anything in that respect.

---

### Post by the.dark.lord on 2006-10-06
Mind your language... bad language is not welcome here

---

### Post by DaH-RaT on 2007-09-22
i also am having hairloss trouble with this card. ive tried ndiswrapper source and also wlassistant,  but it reads it as an unknown device still. i used these 3 posts:

maybe you can have better luck than me

[SOLVED] I've installed ndiswrapper, now how do I install the drivers
[http://ubuntuforums.org/showthread.php?t=483548](http://ubuntuforums.org/showthread.php?t=483548)

Drivers for Linksys WMP54g wireless adapter
[http://ubuntuforums.org/showthread.php?t=487906&highlight=WMP54GV4](http://ubuntuforums.org/showthread.php?t=487906&highlight=WMP54GV4)

NdisWrapper source install doc
[http://ndiswrapper.sourceforge.net/joomla/index.php?component/option,com_openwiki/Item,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?component/option,com_openwiki/Item,33/id,installation/)

try not to cuss but i do understand your situation.

---

