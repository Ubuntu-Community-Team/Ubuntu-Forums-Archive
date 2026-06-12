---
title: "xubuntu and linksys question"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by bcnaday on 2006-08-30
Hello,
I have a linksys compact usb 2.0 network adapter, and id like to know if its xubuntu comptable.
Has anyone tried this before?

---

### Post by dannyboy79 on 2006-08-31
go to a terminal, type in "dmesg" and go thru that and  look for the area when it starts listing usb info and see if your xubuntu is seeing your usb wireless adapter. That's all I can tell, I am a linux newbie but I thought I could give you a tiny bit of help.

---

### Post by doobit on 2006-08-31
> **bcnaday said:**
> Hello,
I have a linksys compact usb 2.0 network adapter, and id like to know if its xubuntu comptable.
Has anyone tried this before?

Can you tell the exact model number? Also, this is an ethernet adapter, not a wireless, right?

The USB device can be recognized and show up in dmesg, but you still might need to identify the driver to make it work. 
Here are a couple of places to look:

[http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)
[http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)

---

### Post by bcnaday on 2006-08-31
USB200M
according to the box.
cool links also.
yea its not wifi

---

### Post by bcnaday on 2006-09-01
bump :?

---

### Post by doobit on 2006-09-01
> **bcnaday said:**
> USB200M
according to the box.
cool links also.
yea its not wifi

Everything I can find with Google says the USB200M has worked since kernel 2.4.22. 

Boot up with it plugged in to the computer and your network. When you get to the desktop open a terminal and type sudo iwconfig and paste the result here.

---

### Post by bcnaday on 2006-09-01
Yay thanks. ill post what it says.

---

### Post by doobit on 2006-09-02
> **doobit said:**
> Everything I can find with Google says the USB200M has worked since kernel 2.4.22. 

Boot up with it plugged in to the computer and your network. When you get to the desktop open a terminal and type sudo iwconfig and paste the result here.

Sorry, I screwed up. The cammand is ```
ifconfig 
``` and you don't need to sudo.

---

### Post by bcnaday on 2006-09-02
Ok, Ill do that, My only problem is I misplaced the spare wire. ](*,)

---

### Post by GodsMoon on 2006-12-20
apparently Linksys updated the USB200M with a new chip set and didn't change its model number.
I got it to work with the beta version of Ubuntu Feisty Fawn Herd 1 (kernel 2.6.19). But I haven't been able to get it to work with Edgy.
If anybody has any ideas or knows how to update the kernel it would be helpful

---

