---
title: "Rtl8187b Id: 0bda:8179 - Solved!!!!!!!!!!"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-02-26
I've got a RTL8187B ID: 0BDA:8179 internal wireless card from Realtek in my Toshiba A200 laptop. 
After around 3 days of trying to fix it.. I have now fixed/modified it a little bit and now it works, well, for me that is!

Its done through the Win98 Driver in Ndiswrapper. 
To install Ndiswrapper, go to System > Admin > Synpatic Package Manager and search for ndiswrapper. 
There should be 3 results:

ndisgtk (GUI of ndiswrapper)
ndiswrapper-common
ndiswrapper-utils-1.9

Install them all. 
ndisgtk with be located under System >Admin > Windows Wireless Drivers.
 
Now the Driver:

You can download it from [Here]("http://download2us.softpedia.com/dl/1be093dd5ac5f445050aa7cd9f5497e2/47fcf9b0/300054087/drivers/network/RTL8187B_driver_only.zip")

The original Win98 driver doesn't recognise the id of 0BDA:8179 but I found out a way which it will, by modifying the .inf file a very little bit. (well, adding one line of code to it). 

Just google RTL8187B Win98 Driver and download it. Extract it. and locate the .inf file. Open it and look on the lines where it says..

```
;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200


CHANGE IT TO

;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```

Then insert the new .inf file into Ndiswrapper 
```
Ndiswrapper -i /location/of/driver
```

or ndisgtk (Windows Wireless Drivers under System > Admin) 

Check if its installed,

```
ndiswrapper -i
```
And you should come up with...
```
net8187b : driver installed
              device  (0BDA:8179) present
```

This should be your wireless card sorted.


The best way to use the card is to do manual configuration of your wireless network. That is the best way for me and now it works flawlessly! :KS

Edit: WEP works for me. I haven't tried any other security because I don't have it on my network.

---

### Post by Tom--d on 2008-02-27
Bump

---

### Post by kevdog on 2008-02-27
What's the bump for?

---

### Post by Tom--d on 2008-02-27
Got bored :S

---

### Post by latanerp on 2008-03-30
Thanks for the heads-up at the other thread.  I tried your fix but had to rename the files because I wasn't able to uninstall the driver from ndiswrapper from before... It didn't work, but I am just going to reinstall Ubuntu (8.04) and try this again from a clean install.  I'll let you know if it works then.

ETA:  Can you add the link that you used to get the Win98 driver?  I got the one from Realtek.com
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by latanerp on 2008-03-30
No, unfortunately this did not work for me either.  I am wondering if possibly something else you did got yours working but you attributed it to adding that line?  I don't know.  I looked at your other post with the file that Realtek sent you but I don't understand the instructions included with it.  I've been using Linux for several years now, but I still can only fix stuff with clear step-by-step instructions.  :S


UPDATE
THIS worked for me
[http://ubuntuforums.org/archive/index.php/t-707447.html](http://ubuntuforums.org/archive/index.php/t-707447.html)
(scroll to bottom, post by Kachline)

---

### Post by Tom--d on 2008-04-02
The windows98 driver was from the realtek website. 
The driver was for the Rtl8187b. 
Manual configuration works the best. It connects all the time.

---

### Post by subpar on 2008-04-04
Works with the Vista driver as well.

Funny story, when I googled RTL8187b, this was the first hit. Thanks so much! Worked like a charm.

---

### Post by statik11 on 2008-04-06
Vista drivers might or might not work. I have the modified drivers for download at my site. Just follow the instructions on the page. If you have any questions feel free to email me. [www.geocities.com/dvs_statik](www.geocities.com/dvs_statik)

---

### Post by Tom--d on 2008-04-09
I havent tried any other driver than the Windows 98 one. 

Please post here if any other windows driver works.

Thanks :)

---

### Post by Tom--d on 2008-04-16
> **subpar said:**
> Works with the Vista driver as well.

Funny story, when I googled RTL8187b, this was the first hit. Thanks so much! Worked like a charm.

:) 
Glad to here it worked!

Just remember to press the Star on my post ;)

---

### Post by Aesir09 on 2008-04-27
THANK YOU SO MUCH I LOVE YOU LAWL

ok its working for me but i was right next to my router (wpn824v2)

and i was getting 79%

it was working ok from what i could tell.

now im up in my room and it reads 68% (wtf when i mouseover it does nothing at the right time [now!]) but it was reading like around there.

now are these actual statistics or....?

**EDIT: is there a command i can do to see up/down speeds for my connection?**

---

### Post by SeppTheHammer on 2008-04-27
Hi folks! Thanks for your efforts you put into the RTL8187b issue. However, it does not work pretty well for me.

I followed your instruction and changed the .inf file lines as you recommended. Installation worked properly and at first it seemed that WLAN would function as well. It did but after 10 seconds the connectivity dropped to 0%.

For testing purpose I deactivated the encrypting of my router and it turned out to work nevertheless connectivity was just around 68%.

I'm among the greenest newbies (2 days of Ubuntu experience) in the Ubuntu community and I would be very glad if anyone could provide me with a hint to use the RTL8187b WLAN of my Toshiba Satellite Pro L40 with WPA encryption.

I'd appreciate any help.

---

### Post by Tom--d on 2008-04-28
> **Aesir09 said:**
> 

**EDIT: is there a command i can do to see up/down speeds for my connection?**

Yes :) 

Its 
```
iwconfig
```
Do it while you are connected. 

and it will give your details of lo, wlan0 or wlan1 etc. 
The signal strength is there. 
I don't know how accurate it is.

In hardy, my RTL8187B just doesn't work :(
so Im just going to replace the card :D

Glad it worked for you too :)

---

