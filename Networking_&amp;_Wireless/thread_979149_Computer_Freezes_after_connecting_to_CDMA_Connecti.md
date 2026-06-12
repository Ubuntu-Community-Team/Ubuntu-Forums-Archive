---
title: "Computer Freezes after connecting to CDMA Connection (Auto mobile broadband).. 8.10"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by rickdane on 2008-11-11
I just installed Ubuntu 8.10 on my laptop and the networking features seem great.. it picked up my Verizon VZAccess PC5740 card and even allowed me to connect immediately using the option that appeared in the Wireless Options Panel (in the taskbar), I clicked the "Auto Mobile Broadband (CDMA)" connection option and then I was able to use the internet. Everything works fine for about 1 minute and then the computer freezes.. I've tried this multiple times with the same result each time, there seems to be no way to get control back and I have to reset. When I use my regular wireless connection (a local wireless network in my house with the broadcom wireless driver that is inside my laptop) everything works fine. I would appreciate any advice as to why this may be happening and any sort of patch or anything I could do to fix this. Thanks

---

### Post by tarstarkus on 2008-12-02
> **rickdane said:**
> I just installed Ubuntu 8.10 on my laptop and the networking features seem great.. it picked up my Verizon VZAccess PC5740 card and even allowed me to connect immediately using the option that appeared in the Wireless Options Panel (in the taskbar), I clicked the "Auto Mobile Broadband (CDMA)" connection option and then I was able to use the internet. Everything works fine for about 1 minute and then the computer freezes.. I've tried this multiple times with the same result each time, there seems to be no way to get control back and I have to reset. When I use my regular wireless connection (a local wireless network in my house with the broadcom wireless driver that is inside my laptop) everything works fine. I would appreciate any advice as to why this may be happening and any sort of patch or anything I could do to fix this. Thanks
just to let you know i am having the same problem. Recently added 8.10 to my Gateway laptop. I use the same PCI card and it works fine as you noted for maybe 4 minutes and then drops connection. Sometimes it will hang the system and all I can do is a power off and restart.
I used the4 network manager to edit a new connection and that allowed a connection. I blew that away and used pppconfig ti make another setup and that had the same problem. I'm using that card right now to post this from the windows side. The real kicker is that this service which I have had for three or four years just went broadband at my house. It flys compared to what I had before. I'm looking through the forum to see if I can find hints. If I come up with something I'll remember you..

---

### Post by wmason on 2008-12-08
I am yet another PC5740 sufferer.  I use Sprint with this unit and I see the same set of events.  I can login, browse and after a few minutes, total lockup.  Oddly, first time I tried this I was connected to power and it seemed to only disconnect, not lockup.  It also managed to stay connected log enough then to perform a speed test.  

I am running 8.10, current updates applied on a Dell Inspiron 8600 with 2gb of ram.  The cpu is a 1.6ghz Celeron.  

I will follow this post in case anyone has more to add to it or I manage to make some headway.

--Wes

---

### Post by ptejada on 2008-12-09
I have the same disconnect and occasional freeze issue with a Kyocera KPC650 on Verizon

---

### Post by tarstarkus on 2008-12-14
8.10 Intrepid

Well I got lucky, My Kyocera CDMA wireless modem is now WORKING..
I have had a connection up for 6+ hours and no freezing up of the system.
Here's the essential info;
My system is an "off the shelf" compaq persario SR2020NX.
AMD Athalon 64 3500+ 2.2GHz
When running windos XP the modem always worked. Now one thing I had to do 
to use the PCMCIA card in my desktop was to add a PCMCIA adapter. I always thought I might use the card in both my laptop and the desktop so this made sense to me.. I got one from Verizon that had an external antenna so I could make up for the card being in the back of the desktop.
OK that's the environment because this may not work in your environment.

I used the kubuntu version. so I right clicked on the networking icon and selected add new connection. the screens are very straight forward. Since I'm using Verizon my username is [email]502xxxxxxx@vzw3g.com[/email] password is vzw
If you don't know yours check with your isp provider. proceed through the screens and really don't change anything else until the last screen where you can "name" your connection and select auto so it will connect at boot time or not.....

Save the connection info and then.. open a terminal window and sudo su -
give your login password and you will be a root enabled login. cd /etc/ppp
Edit pap-secrets and check that your username is the same as what you entered in the new connection screens. Mine wasn't so I changed it. That's all I changed in this file.
write and quit the pap-secrets file and edit the options file. This is where the changes will help your modem stay connected. By the way my aircard (another name), is located by Ubuntu as /dev/ttyUSB0. Keep that in mind as you look through any ppp related files. OK so back to the edit of options.
find the line -- lcp-echo-interval XX it may be commented out if so remove the # or hash sign. change the numeric value to 65327.
find the line lcp-echo-failure XX. uncomment this line and change the numeric value to 65327.
find the line (near the bottom);
#Do not exit after a connection is terminated; instead try to reopen 
#the connection
#persist.
uncomment the line with persist. 
Write and quit.
You are good to go. I hope this helps you with your version and your provider.
It sure fixed mine and no more hangups. It was definitely the usb modem setup that was causing the hangups.

---

### Post by ledain on 2008-12-15
Hello All,

       I tried the settings proposed in the previous post but it still doesn't work.  It disconnected 2 times and the third one it froze solid leaving me no choices but hard powered my laptop. I have a HP nc6320 with a KPC650 aircard and I am with Bell Mobility network in Canada.

       Hope we'll find an answer to that issue.

Regards.

---

### Post by ledain on 2008-12-17
Hi all,

     I finally got this working with pppconfig and I double checked to be sure I wasn't dreaming.  I've been connected for almost 1 hour now and it still works fine.  I retried again with NetworkManager and it froze after 3 minutes.  So maybe it's a combination of the settings proposed by tarstarkus and the fact I used pppconfig that made my connection worked. pppconfig is quite selfexplained and after it finishes you connect with pon and disconnect with poff.

Cheers

Ledain

---

### Post by DominaDoom on 2008-12-25
I have been trying to get back online with Sprint Mobile Broadband after installing a Windows XP partition, and not having any WIFI detection with Windows and then being rejected in *Ibex.* 

*Ibex* was running solo for over fourteen days.  I had no problem with my Sprint Mobile Broadband USB air card being detected and connecting with CDMA.  It worked automatically. I installed a Windows partition and the Mobile Broadband was still working in Ubuntu and from boot disk, but XP internet was wacky.  I was kicked off line with failure to recognize my Sprint hardware, once, but a restart kicked it back on without further cause for alarm, until a few days ago.

Then, I was booted off the internet from *Ibex* boot disk, and could not reboot from the disk or hardrive- everything was frozen.  I learned that I had to unplug my Sprint Mobile Broadband hardware in order to load Ubuntu from boot disk or hardrive. I've removed my Windows partition.  I can connect to WIFI in Ubuntu, but have no earthly idea why I lost my Mobile Broadband connection.  

Any answers about the T-Mobile and AT&T options would be helpful.
  
After weeks of Mobile Broadband CDMA Connection success, I lost to this issue that everyone else here is sharing.  What gives?

---

