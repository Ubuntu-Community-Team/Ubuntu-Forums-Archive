---
title: "plulse audio applet has my usb headset working but......."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by nubix on 2009-02-05
this seemed to help:
is there any guide to make it fully usable? i only seem to get rhythmbox and a few other select applications.
thanks in advance for the help!
nubix is offline   	Reply With Quote
nubix
View Public Profile
Send a private message to nubix
Find More Posts by nubix
Old 13 Hours Ago 	  #2
kostkon
May the Ubuntu Be With You!
 
kostkon's Avatar
 
Join Date: Apr 2005
Location: EU - UK
Posts: 1,684
Ubuntu 8.04 Hardy Heron
Send a message via ICQ to kostkon Send a message via MSN to kostkon Send a message via Yahoo to kostkon Send a message via Skype™ to kostkon
	
Re: logitech usb headset in intrepid ibex 8.10
Install the PulseAudio Device Chooser. Run it (it'll be in Applications &#8594; Sound & Video) and then left-click on its icon in your taskbar. Select Volume Control. In the Playback tab you will see the audio streams of your various applications. Right-click on the application you want and select Move Stream... In the list that will appear you should see all of your audio devices listed. Select your headset to send the audio of this application to your headset.

You can set your headset as the default audio device (if you want) in the Output Devices tab. Right-click on it and enable the Default option.

For this to work you need to set all your sound playbacks in your sound preferences (i.e. in System &#8594; Preferences &#8594; Sound) to Autodetect.

You can set PulseAudio Device Chooser to load every time you login from its preferences.

Hope that helps.
__________________
linux user #387628 | ubuntu user #4719 | ubuntuforums user #17209
UbuntuGuide | Ubuntu Security
Compaq AP550, dual Pentium III 773MHz, 512MB RDRAM, GeForce 2 MX 200, SB Live! 5.1, WD My Book WE 500GB, iPod Video 80GB 


when i play sounds it seems to be unusually low even when its all the way up to high. i know for a fact there is a way to fix this as i looked the solution up yesterday myself. however i forgot and i need to be pointed in the right direction. thank you guys!!!

---

### Post by LowSky on 2009-02-05
Um.... What do you need help on?

Dude your message is not clear at all. Do you need help with a microhpone, or is the sound tooo low, or does a headset not work..

Please just give us the details of what is not working for us to fix and please dont copy other things like poeople's names and avatars and bean count it make a pst too hard to understand..

Thanks

---

