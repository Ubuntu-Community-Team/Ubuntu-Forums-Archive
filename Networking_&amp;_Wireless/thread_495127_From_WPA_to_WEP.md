---
title: "From WPA to WEP"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by mtbosworth on 2007-07-07
So I was using a WPA wireless network and everything was working fine with ubuntu feisty.  Recently, I switch ISP to Qwest.  My XP machines were connected in a snap.  I changed my configuration settings on my ubuntu box in /etc/network/interfaces , but its not working.  I have no connection.  Does anyone know what's up?  I did replace the previous config settings with the new stuff.

---

### Post by jimbob on 2007-07-07
I don't know why you have to manually change settings in /etc/network/interfaces - why not use the network-manager GUI?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by mtbosworth on 2007-07-07
Yeah, I've used that too.  I still don't have a connection.

---

### Post by Swab on 2007-07-07
I don't know how to fix your problem, but you might as well turn off WEP, anyone that wants to break it can do so in under a minute.

---

### Post by jimbob on 2007-07-07
Post a copy of your /etc/network/interfaces.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mtbosworth on 2007-07-07
Thanks for the heads up.  I'm switching to WPA.

---

### Post by mtbosworth on 2007-07-07
SO I switched to wireless roaming mode and selected the network I want to connect to.  Where asks you to select the security it on has options for WEP.  So I can't select WPA.  What's up with that?

---

### Post by jimbob on 2007-07-07
Download Wicd from here:  [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

When you get it, delete network-manager and install Wicd.  It is a much better package IMHO and will allow you to set up your WPA1/2.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

