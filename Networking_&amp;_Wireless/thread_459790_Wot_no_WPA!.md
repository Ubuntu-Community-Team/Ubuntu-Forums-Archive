---
title: "Wot no WPA?!?"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2007-05-31
I am really dissapointed that the new version (7.x) has still not got wpa as an option. I managed to get it working in dapper but it was a right mission of editing files that took 3 days to get working and cannot remember what i did.

Is there any program i can install that simply has an options box that gives the options:

O - NONE
O - WEP
O - WPA/PSK

Passphrase/key:          
_____________      
  
Key number:< 1 >

System Type:  
O - Open 
O - Shared Key 

[Connect]

I really cannot go through all the pain i went through last time and as i move between 3 zones wpa(@home), wep (@work) and none (in hotspots/trains). I need to have a way of simply and quickly changing my wireless settings.

I feel this is one area where windows is winning that cannot be blamed on hardware support, because wpa DOES work in ubuntu 6/7, there just seems to be no interface for it (except txt file editing)... Why?.

---

### Post by Buffalo Soldier on 2007-05-31
Ubuntu works quite nicely with wifi encryption. Got mine working to WPA and WEP. Attached are screenshots of the network manager applet configuration window.

IF you've got a wifi card from a linux-friendly manufacturer, it should work perfectly out of the box. Not like windows where you have to install additional drivers and config tools after installing OS.

---

### Post by epee on 2007-05-31
> **dgrafix said:**
> I am really dissapointed that the new version (7.x) has still not got wpa as an option.
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=318539").

And also look around for [RutilT]("http://cbbk.free.fr/bonrom/") - and you'll get what you're looking for, I think.

---

### Post by wieman01 on 2007-05-31
I must agree... It's a shame wireless is still not fully function as of today. Support for static IP is insufficient, some cards do work with WPA out of the box, some don't for some reason. I wish Canonical would put a higher emphasis on it as it keeps a number of people from converting to Linux/Ubuntu full-time.

---

### Post by dgrafix on 2007-05-31
Aha thats great if it does,

but im confused...

Do i have to install extra stuff or is it just the card that doesnt work?

-edit-

@epee thanks epee, but thats what i did before and it worked but i need a quick way of reconfiguring it as i have 3 separate wireless zones to work with.

@buffalo i dont understand what you have done to get those options because my fiesty install doesnt have them, just wep. did you do something to get them or is it card specific?

---

### Post by wieman01 on 2007-05-31
> **dgrafix said:**
> Aha thats great if it does,

but im confused...

Do i have to install extra stuff or is it just the card that doesnt work?

-edit-

@epee thanks epee, but thats what i did before and it worked but i need a quick way of reconfiguring it as i have 3 separate wireless zones to work with.

@buffalo i dont understand what you have done to get those options because my fiesty install doesnt have them, just wep. did you do something to get them or is it card specific?
Really depends on the piece of hardware that you have got. It's possible that you need to replace the current driver (whatever it is). What card have you got?

---

### Post by netreg on 2007-05-31
I have done a fresh install of Ubuntu 7.04 this morning on my inspiron 9300. I have got wifi working with WPA :D not sure how, but it is working...  however i cannot get it to use a static IP...

So am i correct in what i have picked up along the way that using a static IP address with WPA is a lotter whether it works or not.. :(

thanks
Darren

---

### Post by wieman01 on 2007-05-31
> **netreg said:**
> I have done a fresh install of Ubuntu 7.04 this morning on my inspiron 9300. I have got wifi working with WPA :D not sure how, but it is working...  however i cannot get it to use a static IP...

So am i correct in what i have picked up along the way that using a static IP address with WPA is a lotter whether it works or not.. :(

thanks
Darren
Static IP is definitely a problem. Some users have reported it works, however, I cannot confirm that along with a few others.

---

### Post by dgrafix on 2007-06-04
Got it working with a netgear one OOTB but my belkin one was just wep (wich is wierd as i use it with WPA on win)
Strange thing is it says it (the netgeat) is only getting 58% signal strength even when i hold it right by the access point ??

O well, least its working.

Thanks for helping and i take it back (and change it to Wot no wpa on a belkin :O)

---

### Post by esc1 on 2007-06-04
No wpa option with my Belkin wifi card either.

---

### Post by jeremija on 2007-06-04
> **Buffalo Soldier said:**
> Ubuntu works quite nicely with wifi encryption. Got mine working to WPA and WEP. Attached are screenshots of the network manager applet configuration window.

IF you've got a wifi card from a linux-friendly manufacturer, it should work perfectly out of the box. Not like windows where you have to install additional drivers and config tools after installing OS.

how can i get my network manager applet to display wpa like it is displayed on your screenshots? it displays my Intel 3945ABG wlan card, but i can only select WEP. What do I need to do to get WPA and WPA2 on the list?
I already installed wpa supplicant if that matters :)

---

