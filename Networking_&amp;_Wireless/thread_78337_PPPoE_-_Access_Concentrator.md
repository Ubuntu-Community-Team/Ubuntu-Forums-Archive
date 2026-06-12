---
title: "PPPoE - Access Concentrator"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by Zinckk on 2005-10-18
When I run Ubuntu 5.10 from DVD I cannot connect to the Internet (though can PING URLs).

A bit of Googling led me to PPPoE, but this gives the error message:
         "Access Concentrator of your provider not responding......"

Does anyone have any ideas what the problem is ?

[ DSL-G604T Router/Modem ADSL Ethernet connection, all works ok on same machine running XP ]

Thanks

---

### Post by Zinckk on 2005-10-18
Additional info that might be relevant:

1) Router Make & Model
          [http://www.dlink.com/products/?pid=372](http://www.dlink.com/products/?pid=372)
          - Ethernet, bought to replace USB supplied by the ISP (Tiscali UK)
          - not sure what 'mode' it's in, took the default options
          - broadband (ADSL) connection
Thanks

---

### Post by mips on 2005-10-18
I assume it is working via a windows PC ?
If the answer is yes did you have to run any special client software from Tiscali to make it work ?
Is the windows setup to use PPPoE or is the TCP/IP properties simply configured to get an IP address via DHCP ?

---

### Post by mips on 2005-10-18
I did some googling/searching and this problem seems very common with D-Link & Linux. Connectivity is there but DNS is buggered. 

Option 1&3 is NOT D-Link specific.

**_Option1:_**

In the firefox address/URL space type    "about:config"    , scroll down to    **network.dns.disableIPV6 = false**    ,double click this line to change it to **true**.
In the above do NOT type in any quotes.

The above will most probably help for Firefox but not your other applications. Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

**Save and reboot your PC**.



If this does not work revert to the original settings and we go to step 2:



**_Option2:_**


The second option is to upgrade your Firmware to version 2x or something of the kind to resolve the DNS issue.

Contact D-Link UK and ask then for the V2 firmware as I do not see it available on their FTP server  [ftp://ftp.dlink.co.uk/dsl_routers_modems/dsl-g604t/](ftp://ftp.dlink.co.uk/dsl_routers_modems/dsl-g604t/)
The South African support sites carries version 2 firmware but I dont know whether it would be compatible with the UK models as we seem to use the EU code,  [ftp://dlinktech.co.za/Product%20Drivers%20and%20Firmware/BroadBand/DSL-G604T/Firmware%20HW_A3%20FW_V2.00B01T01.EU.20050609/](ftp://dlinktech.co.za/Product%20Drivers%20and%20Firmware/BroadBand/DSL-G604T/Firmware%20HW_A3%20FW_V2.00B01T01.EU.20050609/)
Apparently a 20050930 version is supposed to be released soon. **UPDATE, firmware here:** [ftp://dlinktech.co.za/Product%20Drivers%20and%20Firmware/BroadBand/DSL-G604T/Firmware%20HW_A3%20FW_V2.00B01T01.EU.20050930/](ftp://dlinktech.co.za/Product%20Drivers%20and%20Firmware/BroadBand/DSL-G604T/Firmware%20HW_A3%20FW_V2.00B01T01.EU.20050930/)


If I was you I would pressurise D-Link UK for the code or ask them if the EU version is compatible.

[COLOR="Red"]Please note that it is not advisable to use code intended for one region in another region !!![/COLOR]
For your regional office look here: [http://support.dlink.com/international/](http://support.dlink.com/international/)

If this still does not work then we go to the next step:



**_Option3:_**


First, from Windose open a command prompt, enter  "ipconfig /all"  . Now record the IP address of the DNS name servers, there should be two. Alternatively you can look here but I trust the above method more:   [http://forum.portforward.com/YaBB.cgi?board=Routers;action=display;num=1115416655](http://forum.portforward.com/YaBB.cgi?board=Routers;action=display;num=1115416655)

Then follow **one** of the treads listed below:

[http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router)
or
[http://ubuntuforums.org/showthread.php?t=65669&highlight=D-Link+router+howto](http://ubuntuforums.org/showthread.php?t=65669&highlight=D-Link+router+howto)



**Please feed back and let us know which steps work.**

---

### Post by Zinckk on 2005-10-18
OPTION 1 works!

Well it did for me - many thanks to Mips.

As a newbie I'm not quite sure of all the reasons behind all this - but changing the browser parameter (network.dns.disable IPV6 to TRUE  was all that was needed to get my internet browser up and running)

---

### Post by mips on 2005-10-19
Just ensure that all your other traffic also works. Try stuff like Synatic, Limewire etc just to be sure.

---

### Post by otware on 2005-11-07
Is the updated link in **Option 2** deffinetly for the EU version?

---

### Post by mips on 2005-11-07
You are in the UK, do NOT use the EU version. 

Get yours from the UK link in Option 1   [ftp://ftp.dlink.co.uk/dsl_routers_modems/dsl-g604t/](ftp://ftp.dlink.co.uk/dsl_routers_modems/dsl-g604t/)
File: DSL-G604T_FW_V1.00B02T02.UK.20050815.zip

It looks new, dont recall seeing it there previously.

---

### Post by otware on 2005-11-07
I've had soe problems updating. For both the FS and Kernel files, it cannot complete the transfer. luckilly this doesn't screw with my router and make it useless. But it does mean I can't update the firmware. Has anyone else had this problem? I'll probably see if D-Link have a technical forum for asking this question aswell...

---

### Post by otware on 2005-11-08
DLink only have a technical support forum if you sign up and give them your details. i don't trust them any more that i trust Homecall. Before I meant that I cannot actually update the router firmware, not that I can't download the zip file.

---

### Post by mips on 2005-11-08
I have noticed that some routers have dodgy web interfaces when it comes to Firefox so I suggest using IE maybe.

1. Extract the zip file to a folder or something.
2. UNPLUG the adsl line/cable from the router.
3. Select FS file and update gateway. File will load and unit will reboot.
4. Log in again.
5. Select KERNEL file and update gateway.
6. Once rebooted you should see the new firmware version.
7. Reset the device to factory defaults and reconfigure from scratch.

---

### Post by otware on 2005-11-08
there is an option to save your configuration to disk in an xml file. can you use this to update your settings without having to type it all in again and that?

btw i tried it on IE (it didn't work), I tried it on Firefox, and for the FS file it said that it had no data.

---

### Post by mips on 2005-11-08
I dunno about the saving thing. You can try though, there is not that much to type in though.

---

### Post by mips on 2005-11-08
Try calling dlink tech support

---

### Post by otware on 2005-11-08
i might try downloading the previous version of the firmware and install that first before i move on to the latest.

---

### Post by markd on 2005-11-09
I updated my firmware last night using IE with no problem.  I also used the save confg/restore config xml file, which also worked for me.  Make sure to unplug DSL cable though.

---

### Post by otware on 2005-11-12
That's good. Has anyone else here tried to update using the UK firmware? I assume everyone here is probably not from the UK.

---

### Post by Pretzal on 2005-12-25
Thanks very much for the help Mips! Ive just bought a G604T Router and have managed to get it all working including synaptic, firefox and Gaim using Option #3 and using the first thread you listed within that option. You are a dead set LEGEND! People like you make Ubuntu so great. Thanks:D

---

### Post by mips on 2005-12-26
Thanks, only a pleasure but I also borrow from others. Glad it worked for you. Thats the nice thing about open source, everybody borrows from everyone else to achieve achieve some goal. Sharing is great ;)

---

### Post by oliwally on 2006-01-17
> Option3:


First, from Windose open a command prompt, enter "ipconfig /all" . Now record the IP address of the DNS name servers, there should be two. Alternatively you can look here but I trust the above method more: [http://forum.portforward.com/YaBB.cg...m=11154166](http://forum.portforward.com/YaBB.cg...m=11154166) 55

Then follow one of the treads listed below:

[http://www.ubuntuforums.org/showthre...nk+adsl+router](http://www.ubuntuforums.org/showthre...nk+adsl+router)

Bonza rip-snorting-beauty. Option 3 worked for my DSL-502T. Everything can access the internet now.

---

### Post by SlasherMCT on 2006-02-13
I have just fixed the problems I had by updating the firmware on my DLINK DSL-G604T to the V1.00B02T02.UK.20050815 release if anyone else has this problem and ADSL modem...

---

### Post by syawillim on 2006-08-17
And on the fith day he found this thread and all was right with the world.:D 

Updated the firmware, took two minutes and the headache I've had for four days and the urge to just install windows have both passed....Thank you.

---

### Post by Srirangan on 2006-10-03
While trying to fix this, I mistakingly changed the network hostname.

Now I'm not able to access any of the Admin programs. Nor is my default account recognized the owner of the /etc/ folder. How do I fix this?

---

### Post by ctrl_freak on 2006-10-17
I've successfully fixed my problem with my DLink router using; first Option 1, then Option 3 - using the second tutorial.

Thanks heaps. :D

---

### Post by Richardinho on 2007-08-03
Hello guys.

I too am struggling to connect my ADSL modem ( DSL-524T) to the internet using Ubuntu 6.06.

I have tried the various solutions suggested in this thread without success, but there seems to be various problems with them.

For example, that suggested by Python back in 2005;
[http://ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router)

"Finally, go to /etc/dhcp3/dhclient-script and comment out this:"

Problem here is that this script is 'read only' and can't be commented out!
It has also been altered somewhat from what is described in this post, so it's hard to know if this solution still applys.

---

### Post by mips on 2007-08-03
You are not telling us much....

---

### Post by Richardinho on 2007-08-03
Happily, I have now solved the problem of connecting with Linux Ubuntu version 6.06 to the internet using a D-Link DSL-524T ADSL2 Router. Basically it seems if you bang your head against the wall long enough you'll eventually come up with a solution!

Option 2 was the one that worked; Updating the Firmware. I am in the UK, so I went to the D-Link UK website, downloaded the latest firmware update to my hardrive, then accessed my router set up pages through internet explorer (obviously I did this on windows- I have a dual boot) went to the firmware update page, and followed the instructions there. I then went back to my Ubuntu boot, went to the network dialogue box and reactivated the connection.

Judging by the number of posts I researched, connecting to the internet with Ubuntu is one of the biggest problems, and I'm certain it's the number one thing that puts off those who have attempted to dip a toe into the linux water.  When you  are fiddling around with a new computer system, that  blank screen feeling is enough to put you off trying!- particularly when the warm familiar easiness of Windows sits temptingly just one re-boot away, and no amount of positive publicity for Linux, or pretty GUIs, is going to win converts when this problem remains.

---

### Post by thekungfuman on 2007-09-01
First let me say that I have tried finding the answer by searching the forum, so I apologize if this has already been handled.

I have a Dell E510 connected to a D-LINK DES-1105  SWITCH (not a router, hence, no firmware). I have a windows XP installation on the SAME hard drive but a different partition (the first partition, followed by Ubuntu, swap, and data) and for some reason I cannot connect to the internet. I don't think my partition configuration is the problem, as I am not able to get online from the LIVE CD either. My windows xp installation does have full internet and networking access. I tried disabling ipv6 in firefox, which didn't work, but even if it did I cannot connect to synaptic or any other services. The network manager says it is connected to the first of two wired services, but the second is grayed out and unusable. Any suggestions or ideas? Please let me know what additional information I can provide that might help diagnose this problem.

---

