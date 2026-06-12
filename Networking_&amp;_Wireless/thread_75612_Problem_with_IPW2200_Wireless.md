---
title: "Problem with IPW2200 Wireless"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by audax321 on 2005-10-13
Hello,

     I just did a clean install of Breezy on my new laptop and was surprised to see my wireless internet working using the IPW2200 drivers. The card is an Intel 2200 B/G. The problem is that after some time the connection dies and does not come back up without a reboot. I opened up the terminal and dmesg gave me this:

[4313620.087000] ipw2200: Firmware error detected. Restarting.

repeated about 20-30 times before the connection went. Any idea how to correct this?

Thanks.

---

### Post by mlomker on 2005-10-13
> [4313620.087000] ipw2200: Firmware error detected. Restarting.


I'm afraid that's 'normal' behavior for the Intel wireless drivers.

---

### Post by smack on 2005-10-14
Happens to me too. The drivers are quite crap.

Intel won't give the people making the driver any hardware specs so it's taking them a really long time to reverse engineer. :(

---

### Post by audax321 on 2005-10-14
That sucks. :( 

Oh well, I have an old D-Link PCMCIA card that works with the madwifi drivers. Guess I'll have to use that.

---

### Post by mlomker on 2005-10-14
> Oh well, I have an old D-Link PCMCIA card that works with the madwifi drivers. Guess I'll have to use that.

Why?  It has always been a benign error...I never have problems with my connection.

---

### Post by raghav_p on 2005-10-14
Interestingly enough, the connection seems stable on my end (on breezy and hoary). :confused:

---

### Post by audax321 on 2005-10-14
I don't know. It seems fine for web browsing. But if I transfer a large amount of data from my FTP I get that error and the connection drops and I can't reactivate it without a reboot.

---

### Post by xMetaRidley on 2005-10-14
Try this:

```

sudo gedit /etc/modprobe.d/ipw2200

```

now put this in the file:
```

options ipw2200 hwcrypto=0

```

then reload the drivers:
```

sudo modprobe -r ipw2200
sudo modprobe ipw2200 hwcrypto=0

```

the ipw2200 file in modprobe.d will set this option automatically on startup. I originally found this tip on another forum when I had similar issues. After doing this I haven't had any firmware errors.

---

### Post by audax321 on 2005-10-14
xMetaRidley, THANK YOU!!!!

That seems to have fixed the problem. I transferred a good 12 Gigs from my other computer and the connection didn't drop once. :)

---

### Post by HACKradio on 2005-10-16
I have the same card but it was not detected. I have the driver but i am new to linux and have not been able to find good install insturction.

---

### Post by RoyCowboy on 2005-10-16
xMetaRidley - youre a lifesaver!
Thanks alot

---

### Post by cbudden on 2005-10-16
When I restarted after doing this, i could not get on the internet.  Have I missed a step.

---

### Post by mlomker on 2005-10-16
xMetaRidley, 

Would you mind reposting that in the Customization forum as a how-to?  If not then I'll do it and give you attribution...this is a common problem and if it fixes it...

Now if I could only figure out what causes the continuous stream of APIC errors in dmesg whenever I have that driver loaded...

---

### Post by mohaham on 2005-10-16
xMetaRidley, Thank you

---

### Post by ajaustin on 2005-10-16
Slightly different problem here, well two problems actually.

1.  Should I report this one as a bug?
Wireless responds very slowly after a reboot with no network cable in, until I do 

```
#sudo ifdown eth1
```

eth0 is wireless and eth1 is wired.

2.  At one end of my house I seem to be picking up my neighbour's access point.    If I boot up in this location I cannot get the wireless working at all no matter how much I tinker with the GUI or issue iwlist scan, iwconfig, ifup and ifdown commands.  Is there some way to force eth0 to associate with a particular access point?   I thought iwconfig might do this but can't find anything to do it.

---

### Post by jakev383 on 2005-10-19
I tried the hwcrypto thing, and it worked. Until I got home. I could not connect to my access point there (which is a G, work is a B) until I removed the ipw2200 file from the modprobe.d directory.  
Let me clarify. It said I was connected, without an IP. Could not get it to lease one. Didn't even show any requests on the DHCP server coming from the laptop. Removed the file, and poof.  Grabbed a lease. Just to make sure, I put the file back, and could not get a lease. Removed it, and all is well.  Which is annoying, since it had solved the problem of the wireless dropping during big transfers... Oh well. Off to find the next fix for it.

---

### Post by ajaustin on 2005-10-20
[QUOTE=ajaustin]Slightly different problem here, well two problems actually.

1.  Should I report this one as a bug?
Wireless responds very slowly after a reboot with no network cable in, until I do 

```
#sudo ifdown eth1
```

eth0 is wireless and eth1 is wired.

2.  At one end of my house I seem to be picking up my neighbour's access point.    If I boot up in this location I cannot get the wireless working at all no matter how much I tinker with the GUI or issue iwlist scan, iwconfig, ifup and ifdown commands.  Is there some way to force eth0 to associate with a particular access point?   I thought iwconfig might do this but can't find anything to do it.[/QUOTE]

Further research shows:-

1. That if I comment out all the eth1 (wired) setup in /etc/network/interfaces the wireless network comes up without having to fiddle around.

2. That it would seem that the Network Connection applet lies about the signal strength, it shows about 90% right up to the limit of where my Zaurus will connect and then suddenly disconnects.  I think that a lot of the disconnects are actually due to low signal strength.

3. Someone tells me that using ndiswrapper would solve all these problems.  Does anyone have a view on whether this would be the way to go?

---

### Post by Patrik Johansson on 2005-10-20
Hey,
I have the same problem with my Cisco Aironet card...(atheros chipset)
How can i apply this to work on my computer...
I guess its just to change som text but how??

Thx

---

### Post by Psquared on 2005-10-20
I finally had success with ipw2200 wireless in Ubuntu Breezy with the 686 kernel.

I had borked my modprobe.d file. When I reworked it somehow it created a file called arch-alias.save. I deleted that. I created the file ipw2200 in that same directory and added the line options ipw2200 hwcrypto=0.

Then I ran sudo -r modprobe ipw2200 and then ran sudo modprobe ipw2200 and voila - the machine found the card.

I had hacked my machine so many times trying to get it to work I uninstalled just about everything related to it and started from scratch - adding things back one at a time changing the file noted above. I've yet to reboot, but it is working now. Good strong signal and fast. Excellent throughput.

I'm using fw 2.3 and ieee80211 1.0.3 along with ipw 1.0.6
 
I've been on for an hour with no problems ---- so far.

For those of you having trouble with the hardware/firmware detection definitely try this. (I have been struggling with this for a week now and tried everything. This was the solution that actualy worked.

Thanks to the contributors on this thread.

---

### Post by Psquared on 2005-10-21
OK, I rebooted and lost my wireless card. :???:  Can't seem to get it to start up again. Oh well, back to the drawing board. :rolleyes:

---

### Post by jakev383 on 2005-10-21
[QUOTE=Psquared]OK, I rebooted and lost my wireless card. :???:  Can't seem to get it to start up again. Oh well, back to the drawing board. :rolleyes:[/QUOTE]

If it's like mine, if you go in and remove the ipw2200 file from /etc/modprobe.d (the file that has the hwcrypto=0 directive in it) it will start working again... I'd be curious to see if that works.  Then you still are in the same boat as me - the wireless will drop from time to time, depending on how large of a file you transfer.

---

### Post by Psquared on 2005-10-21
[QUOTE=jakev383]If it's like mine, if you go in and remove the ipw2200 file from /etc/modprobe.d (the file that has the hwcrypto=0 directive in it) it will start working again... I'd be curious to see if that works.  Then you still are in the same boat as me - the wireless will drop from time to time, depending on how large of a file you transfer.[/QUOTE]

Funny thing ... what I did is just repeat the procedure all over again. This time it seems to have stuck. Wireless has been up all afternoon and has survived 2 reboots. At least I know what to do if it stops again.

On another thread it said to insert the same file in /etc/modules. I don't know if that will help, but the hycrypto=0 thingy defintely works - even though its a hack. ;)

---

### Post by jakev383 on 2005-10-22
[QUOTE=Psquared]Funny thing ... what I did is just repeat the procedure all over again. This time it seems to have stuck. Wireless has been up all afternoon and has survived 2 reboots. At least I know what to do if it stops again.

On another thread it said to insert the same file in /etc/modules. I don't know if that will help, but the hycrypto=0 thingy defintely works - even though its a hack. ;)[/QUOTE]

Wnat exactly did you do again?  There is no /etc/modules directory to add the ipw2200 file to, so I have to assume you added it to the modules file, right?  I still think it won't work if you move to a different AP....

---

### Post by Psquared on 2005-10-22
No, the /etc/modules thing was just a suggestion I read about. I didn't do it.

What I did was sudo gedit /etc/modprobe.d/ipw2200 and then added the following line to that file (which I didn't have)

options ipw2200 hwcrypto=0

and then save the file.

then I unloaded the ipw2200 driver with modprobe -r ipw2200

then I reloaded the ipw2200 with modprobe ipw2200 hwcrypto=0

I can't remember if I used sudo or not ... I don't think I did.

---

### Post by jakev383 on 2005-10-24
Tried that, still didn't work for me. When I went to a different AP, I was unable to obtain an IP. The DHCP server(s) didn't even show my laptop as making requests.  I tried a fix from another thread to roll back the ipw2200 driver to version 1.0.0.  This REALLY hosed my wireless card.  I was unable to fix it after that.  My ultimate solution was to pull the Intel 2200B/G card out and put the Broadcom back in.  Loaded ndiswrapper and the Win drivers, and have not had a hiccup since.  Guess that was my fix.  I may switch back in the next release if the ipw2200 driver matures enough.

---

### Post by raghav_p on 2005-11-17
any solution for this problem yet?

---

### Post by grnwood on 2006-03-27
Yes Yes!

This did work for me as well.

IBM Thinkpad T42 / w Intel 2200BG PRO Wireless

Was getting drops when I'd run SJPhone, or do a bit torrent client....

dmesg always reported a firmware error and  a restart.

50% through a torrent now w/out any drops!   Thanks for the tip!

---

