---
title: "Why wont my wireless connect?"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by mLes-_- on 2007-12-20
Okay,  I need to know why my WUSB54GSC picks up my wifi signal but it does not connect.  The Network Manager program sometimes shows it sending packets but im not sure if it is actually passing them to the adapter itself, because the light never flashes green on it.  I spent two days just trying to get the drivers to work and now it wont connect.  SOMEBODY PLEASE HELP!?!!?!?!  I am using Ubuntu 7.10 and a WEP encryption w/ SSID broadcast.

---

### Post by spiderbatdad on 2007-12-20
I read another post where the WEP key had to be entered as a hex number...and I don't know how to do that. Have you tried setting your wireless router to open access to see if you can connect? This may not be the desired end result, but it is how mine is set up and it works.

---

### Post by mLes-_- on 2007-12-20
ok WOW!... anyways I disabled the SSID broadcast and WEP encryption and it works!!! I am posting this in Ubuntu NOW!  It kind of sucks but if i catch anyone on my wireless network then ill see them at work the next day with a corrupted OS saying "Uh, My computer wont start!" BWAHAHAHA

---

### Post by mLes-_- on 2007-12-20
Well I just did the updates for Ubuntu 7.10 and now it doesnt work... back to step 1!!! oh well ill figure it out, unless somone will actually help me???

---

### Post by mLes-_- on 2007-12-20
okay I think im headed in the right direction(correct me if not)...

I went into "Device Manager" and found my wirless adapter.  So I know its there and it knows what it is.  Although I clicked on Advanced and where it say "usb.device.can_wake_up" (I think) the value is set to "false".

I checked all the other USB devices and they say "true"  so I think this needs to be "true" also.  However, my problem is it will not let me change it under normal mode, so I logged in Recovery mode and teh Device Manager crashed whenever i start it.  WTF?! haha.

How do I change it please someone?!?!

---

### Post by mLes-_- on 2007-12-21
anyone?

---

