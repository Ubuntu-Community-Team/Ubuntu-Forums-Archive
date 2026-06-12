---
title: "Linksys WUSB54GC Question"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by penguin5 on 2008-03-26
Hello, 

Iv been looking everywhere for some help but was unsuccessful finding anything.  

Im using a linksys wusb54gc wireless adapter on gutsy and I do get internet. However, my internet connection is very slow ( i already disabled IPV6 and followed the instruction on how to make firefox more reliable) and when i click on that wireless icon in the panel, i can connect to my network but it still says " Unknown USB devise"  In the hardware menu, it clearly shows that I do have Linksys Wireless Adapter plugged in but wireless menu does not recognize it. 

I used the scrip found here [http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649) but it made my internet connection go from 78% to 56%. Should i just reinstall ndiswrapper? 

Any help or advise would be greatly appreciated.

Thank you.

---

### Post by Sam Lars on 2008-03-26
The signal strength is really iffy and differs between drivers.  I wouldn't worry about it unless you notice a significant change in actual speed.

---

### Post by penguin5 on 2008-03-26
so different drivers show different % connectivity but the connection itself is the same right? My internet was fast at first but then slowed down. I used the script from the link i gave earlier and it didn't help.

---

### Post by Sam Lars on 2008-03-26
Some people do say that with some drivers on some cards that they have to be right next to the router to get just a little connectivity.
Did you change anything that made it slow down?

---

### Post by penguin5 on 2008-03-26
Thank you for trying to help me with this, 

Well after I added the script from [http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649), the connection no longer drops and i can connect with only 1 try. However, the speed of the internet did not improve from before the addition of the script. I get 4 bars with the script and 56% connection and had 4 bars without the script. Not sure if that even matter at all. 

But as for changing anything to cause the sudden change,  I did not change anything except maybe a required update from ubuntu. I dont remember what the update was. But an hour later my connection is busted. The videos on youtube for example load fine but getting there is the problem. I takes longer than usual.

---

### Post by Sam Lars on 2008-03-26
Updates do that sometimes.
I guess it's worth a try removing your driver and re-adding it, or reinstalling ndiswrapper.
If you're really serious about this you could try reverting to an older ndiswrapper to see if that's an update that caused the problem.

---

### Post by penguin5 on 2008-03-26
sorry but Im new to this. I looked online on how to remove ndiswrapper but could find it for 7.10. Also can you tell me how to reinstall it?

Thank you and sorry for the dumb question

---

### Post by Sam Lars on 2008-03-26
Look in
System > Administration > Windows Wireless Drivers
If it's not there, run
```
sudo apt-get install ndisgtk
```
You can remove the driver that's there, and install the driver from the script (rt73.inf, in wusb54gc/compressed_files/32bit after extracting everything)
If that doesn't work, then you can do
```
sudo aptitude remove --purge ndiswrapper ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
sudo apt-get install ndiswrapper ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
And then add the driver as mentioned above.

---

### Post by penguin5 on 2008-03-26
i tried it but no luck. is there a way to uninstall what the scrips installed? im not sure what i just did. I just wold like to go to the way it was before the scrip was installed. 

Maybe i should reinstall firefox? or maybe update the version of ndiswrapper?

---

### Post by Sam Lars on 2008-03-26
Well that doesn't seem very simple from looking at it, but I can try to get it generally undone.  I'd wait for an answer on that thread first.

Packages it installs:
ndiswrapper
     If you're running KDE
          wlassistant
     Also maybe:
          libc6-dev
          linux-libc-dev

Other changes it makes:
Adds "blacklist rt73usb" or "blacklist rt2x00lib" to /etc/modprobe.d/blacklist
Adds "ndiswrapper" to /etc/modules
Installs rt73.inf driver in ndiswrapper

And if it installed the "maybe" packages, it also installed the newer version of ndiswrapper... and I'm not sure how to undo that.

---

### Post by penguin5 on 2008-03-26
I HAVE NO IDEA what happened but now my internet is blazing fast. All i did was enable the restricted driver for my onboard wireless card and now my Linksys USB is running way way better.  It still says 56% but I have 3 bars like i usually do.

As long as it keeps working, im a happy man. Thanks for your help.

EDIT: Actually it only worked for a few minutes and then slowed down again. For some reason, it automatically got online twice  after i restarted the computer twice. It looks as if the on board broadcom card tries to connect to the network during the ubuntu startup but then switches to Linksys. Sometimes it does not. Im so confused to why its acting so bizarre.

---

### Post by Sam Lars on 2008-03-26
I think that networking is a relatively bizarre area... I have similar things happen with my Linksys PCI card.  The drivers work fine for months, then begin to randomly drop the connection, or be excruciatingly slow.
You can try
```
sudo ifdown wlan0
sudo ifup wlan0
```
Replace "wlan0" with what you wireless is actually called.  This will restart the network, and it may or may not help.
You could also try
```
sudo rmmod idk
sudo modprobe idk
```
between the previous two commands.  Replace "idk" with whatever your restricted driver is called.  That reloads the driver module, which, again, may or may not help.

---

### Post by penguin5 on 2008-03-26
Do you think its worth trying out the serialmonkey drivers? If so, how do I do it? 

Thanks again for your repeated  help.

---

### Post by Sam Lars on 2008-03-26
The serialmonkey drivers seem even more complicated than that script.  It says that they're in testing, and it may be harder to undo than the script.  I'm not sure how bad things would be if it didn't work.
If you want to you can try.  I'd do my best to help you if they didn't, or you could look at the serialmonkey threads to see if anyone has advice of feedback about it, and how to uninstall it.

---

