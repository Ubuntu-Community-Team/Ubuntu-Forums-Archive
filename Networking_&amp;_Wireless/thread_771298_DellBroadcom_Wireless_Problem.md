---
title: "Dell\Broadcom Wireless Problem"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by HeroicWisdom on 2008-04-27
Hi everyone

I have installed ubuntu on my dell inspiron 1501 and am having wireless troubles. I have tried both the Ndiswrapper way, and the native driver method, and neither has worked. right now i have uninstalled ndiswrapper, and am trying to use the native driver. 

With the native driver i am able ot get a connection for a few seconds after boot up, but after a few seconds it dies out and i am unable to reconnect. I have tried the manual config and a static IP, and DHCP with no luck. Anybody have any ideas. The driver i am using is b43 fwcutter and i have installed the firmware via a guide on these forums, and even installed it via the command line over a wired connection to the internet.

Thanks for your help

HeroicWisdom

---

### Post by pHreaksYcle on 2008-04-27
Any misconceptions should be cleared by this article

[http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html](http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html)

Read the first section about wireless, you should be able to make at least one of the two work. Make sure you bookmark that site, it's great for 1501 users. I'm the editor and I STILL use it to help me! Good luck!

EDIT: I would recommend ndiswrapper, seems more stable and has faster speeds, least for me! gl

---

### Post by HeroicWisdom on 2008-04-27
That is the exact guide i used to get this far, sadly it has not got me all the way. DO you have any ideas? im lost, i do not understand what the problem could be, as i have folloowed the ndiswrapper instuctions to the letter, and still got zip. I never installed a newer version of the windows driver under ndiswrapper and got zip.

Any ideas?

---

### Post by fk4n on 2008-04-27
> **pHreaksYcle said:**
> Any misconceptions should be cleared by this article

[http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html](http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html)

Read the first section about wireless, you should be able to make at least one of the two work. Make sure you bookmark that site, it's great for 1501 users. I'm the editor and I STILL use it to help me! Good luck!

EDIT: I would recommend ndiswrapper, seems more stable and has faster speeds, least for me! gl

i second that, ndiswrapper is great. Here is link for fixing the wireless problem in Dell

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

---

### Post by pHreaksYcle on 2008-04-27
Well, I can give you a few options I guess.

1. Ubuntu is sweet. It's so good you can reinstall in basically minutes, so back up your home folder and reinstall, then start over, skipping the driver manager all together.

2. Use the GUI for NDiswrapper. I believe it's called ndisgtk or something. Get it from synaptic and open the driver from that. Worked for me a few times when Ndis was being picky.

3. If you are trying to do Ndiswrapper, make sure your proprietary driver is removed in the Driver Manager, the little green icon under the system tab. I tried to install ndiswrapper over the top of it once and it wasn't pretty. If the box is checked in driver manager, un-check it, that will uninstall it, leaving you fresh.

If you want to try ndiswrapper again, make sure the proprietary driver is removed (above) and in synaptic, make sure everything with ndiswrapper in the name is uninstalled. Then follow the guide from the beginning again.

GOOD LUCK! Hope you had fun reading my book on Dell Inspiron 1501 wireless :lolflag:

EDIT EDIT EDIT!: I noticed you said you had connection issues. Have you updated your install? There was a problem a while back with the early versions of network manager in hardy beta causing that type of issue. Make sure you have updated.

---

### Post by HeroicWisdom on 2008-04-27
Ok i have uninstalled the b43 driver, and reinstalled ndiswrapper and have the driver installed. I installed the GUI to ndiswrapper, and this is a very stupid question, but how do i run the GUI? I dont see a short cut anywhere...

Thanks for the help!

P.S. At the current moment i can see wireless networks via the nm applet, but if i try to connect i cant get anything, even on unencypted connections...

---

### Post by pHreaksYcle on 2008-04-27
The GUI for ndiswrapper IS for installing the driver :P

If you have the driver installed, you're set. Right click on your network manager icon in top right, click Connection Info and confirm the driver is ndiswrapper. Then reboot, you might have to do this to apply your settings. Get back to me, im interested.

---

### Post by HeroicWisdom on 2008-04-27
Ok i found the GUI, and it says the same thing the command line told me. It says that the driver is installed and hardware is present (on the command line a alternate driver is found ssb but thats supposed to be their right?). When i right clcik the icon and do the connection information, the drivers says ndiswrapper, on wlan0. Right now i dont see any networks, witch seems to happen if i leave the app alone for a bit. Im going to reboot, if it works i will let you know. Do you have any other ideas?

Thanks

HW

---

### Post by pHreaksYcle on 2008-04-27
Yes, having an alternate driver there is normal I believe. Tell me what your reboot gives you.

P.S. WiFi light is on right?

---

### Post by HeroicWisdom on 2008-04-27
Yea the Wifi light is on, and after a reboot nothing new happened. I reinstalled the driver that you recomended on your site via the GUI and rebooted and am getting nothing. I just noticed though, that if i try to do a **sudo iwlist scanning** The interface wlan0 says that nothing is found, even though the applet is displaying my wireless network.  Any ideas?

---

### Post by pHreaksYcle on 2008-04-27
If it makes you feel any better, it says nothing found on my scans about 90% of the time too. Sometimes if I just keep putting it in over and over it finds something. I have found the 1501 to suck with wireless ubuntu as well, so don't feel like this is your fault haha. The only thing I haven't had you try is reinstalling. Copy your home folder to a flash drive or whatever, reinstall, then replace the home folder. All I can think of. Sorry, I tried!

---

### Post by Jonas Wakefield on 2008-04-27
I have an Inspiron 6400, and can't get wireless either...

---

### Post by HeroicWisdom on 2008-04-27
Ok i guess i will try a fresh install.. if im lucky it will work out. i took some screens of my config files, maybe somebody can make since of them. Thanks for the help, I'm going to try a reinstall and start of from square one...

---

### Post by pHreaksYcle on 2008-04-27
Remember to update when you are done with reinstall before attempting anything. Also, I noticed in your last screenshot that the version of ndiswrapper is not correct. Instead of 1.9 it's 1.5 or something. Did you install it from the ubuntu repos instead of following the guide? Don't feel bad or anything, just tell me so I know what's up. That version number might be the reason it isn't working like the guide says it should.

---

### Post by HeroicWisdom on 2008-04-27
I think i installed via the CD, but if i didnt i would have gotten it via the apt-get command. The installation is running now, when its done i will update then install ndiswrapper. Unless you think it would be better to install ndiswrapper first then update.

Thanks for your effort, i think we are at least getting somewhere.

---

### Post by pHreaksYcle on 2008-04-27
You do not need to install ndiswrapper on your own, installing it is part of the guide. To make myself clear, do not install ndiswrapper using any other method than following the guide exactly. Update first, then do the guide, with nothing else in between. I'm glad I am helping.

---

### Post by pHreaksYcle on 2008-04-27
After a bit more research, I found you were definitely using the wrong version of Ndiswrapper. So as long as you update and only follow the guide, nothing else, you should be okay.

---

### Post by HeroicWisdom on 2008-04-27
I did a fresh install and re followed the guide and i cant get anything still. the version that ndiswrapper reports with the -v is still 1.5 is that what yours says?

---

### Post by pHreaksYcle on 2008-04-27
I don't exactly remember what mine says as I'm not with it presently. Well, if you want, uninstall everything with ndiswrapper in the name by searching in synaptic and then use the proprietary driver. Worth a shot.

EDIT: When Ndiswrapper is gone, use this
sudo apt-get install b43-fwcutter
then this
sudo reboot
then hit me back

---

### Post by HeroicWisdom on 2008-04-27
Ok uninstalled ndiswrapper and am using the broadcom driver, and it still has the same problem as before. It can connected only for a few seconds after a restart. it connects, get an IP and i am able to get on the Internet, but after a minute it just stops working. What the hell is wrong with me?! ARRGGG this is unbelievably frustrating. I though i had a hard time with fedora, but damn, this just make no since to me...

Thanks for the help, do you have any other ideas on what the issue could be?

---

### Post by pHreaksYcle on 2008-04-27
Are you too close/too far from the access point?

---

### Post by pHreaksYcle on 2008-04-27
Also, which router do you have? My router, the Belkin N1 part # F5D8231-4 gives me that kind of **** all the time, kicking me off if I actually get connected in the first place, which is scarce.

---

### Post by HeroicWisdom on 2008-04-28
My distance is fine, i have tried sitting next to the router.


EDIT: ANd my router is a linksys Wireless B/G Draft N, I dont know the model number of the top of my head, but i dont think its the router.

---

### Post by HeroicWisdom on 2008-04-28
Hows this for a funny story...

So i decided to give up and return to windows (gasp)
I reinstalled vista (arrg) and tried to install my wireless driver... and it didn't work... so im gunna say that my card its self is fried.. im ordering a new wireless card, hopefully this one will work for me.

---

### Post by pHreaksYcle on 2008-04-28
Well, doesn't sound very funny for you, but for me, yes, yes it is. Continue to read [www.ubuntu1501.com](www.ubuntu1501.com) man...
Glad to help, kinda

---

