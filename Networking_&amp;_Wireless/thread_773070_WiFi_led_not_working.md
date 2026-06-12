---
title: "WiFi led not working"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by kikapu on 2008-04-28
Hi,

i have a Thinkpad T61 with an Intel 4965 agn wireless card. After some problems, i finally got Wireless to work by installing Wicd and got rid of gnome network manager.
The only problem i have is that of the wireless led is not working. 
Wicd it uses "wext" as WPA Supplicant Driver. I have read at the net that the driver for the iwl4965 is causing troubles and is propably responsible for the not working led.

My question is: As i understand, Wicd is not using iwl and the like. If so, can i remove iwl4965, iwlwifi_mac80211 and cfg80211 from the list of loading modules without causing any troubles to my system ?

Thanks for any help!

---

### Post by EarloftheWest on 2008-04-28
I have the 3965 intel card on my t61 and my led isn't working either.
I've also had a problem with it connecting to wireless networks with hidden SSIDs.
I think a kernel recompile may be needed to get the led working. 
According to the driver site:
[http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)
The LED should be working.
UPDATE:
I just reviewed the site and it looks like LED has been worked on and should be working in the most recent driver. The most recent driver isn't included in Hardy. 
Any brave soul want to install the new drivers and provide their experience?
Another update:
I followed the information for installing the most recent driver. No led light. Bummer. I'd like a little more bling.
Can anyone tell me how to check to see which driver my wireless is using and get the date of the drivers it's using? I want to make sure it's using what I just installed.
Thanks.
Another update.
I followed this guide:
[http://linuxtechie.wordpress.com/200...-ubuntu-hardy/](http://linuxtechie.wordpress.com/200...-ubuntu-hardy/)
My LED is now on all the time. It should flicker as the data is transfered.

---

### Post by kikapu on 2008-04-29
> **EarloftheWest said:**
> I followed this guide:
[http://linuxtechie.wordpress.com/200...-ubuntu-hardy/](http://linuxtechie.wordpress.com/200...-ubuntu-hardy/)
My LED is now on all the time. It should flicker as the data is transfered.

Hmmm..link is not working, i think is not correctly written (and i desperately need this)

EDIT: You meant this ?
[http://linuxtechie.wordpress.com/2008/04/24/](http://linuxtechie.wordpress.com/2008/04/24/)

---

### Post by EarloftheWest on 2008-04-29
Yep. That's the link.

---

### Post by EarloftheWest on 2008-05-01
I'm willing to apply the patch that's listed here:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209)

if someone can point me to a how to on how to do it.

Can anybody point me in the right direction?

---

### Post by kikapu on 2008-05-02
> **EarloftheWest said:**
> I'm willing to apply the patch that's listed here:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209)

if someone can point me to a how to on how to do it.

Can anybody point me in the right direction?

I applied the thing EarloftheWest said, and it is ok now!

---

### Post by reggie_mac on 2008-05-02
Hi, so I'm new to ubuntu and so far all is going well, the only issue i've had so far is getting the LED on the wirless to work properly. I've done the back port thing from [http://linuxtechie.wordpress.com/2008/04/24/](http://linuxtechie.wordpress.com/2008/04/24/) and now the LED is constantly on rather than blinking when connected. Will installing the patch from [http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209) make it all go properly? and if so is this something i should sink my teeth into or is my level of n00bness going to cause more pain. If its one of those things that will probably be fixed in a couple of months or so in an update i think i'll just leave it. 

Cheers

---

### Post by EarloftheWest on 2008-05-02
reggie_mac,
I noticed the same thing. The LED is on all the time. It should flicker like it did in Windows.
It's one of those non-essential things for me but I want to get it working because I just want it I suppose.

I do want to give this patch a try:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209)
But it's a bit over my head at the moment.

---

### Post by Ayuthia on 2008-05-02
Have you already installed linux-backports-modules-hardy-generic?  I thought that I read somewhere that it makes the LED work.  It contains the iwl4965 module.

---

### Post by kikapu on 2008-05-02
> **Ayuthia said:**
> Have you already installed linux-backports-modules-hardy-generic?  I thought that I read somewhere that it makes the LED work.  It contains the iwl4965 module.

Yes, it works but not flickering on data traffic. It remains ON. But when you hit Fn-F5 (on my laptop) you can turn it off.

---

### Post by reggie_mac on 2008-05-02
Im in the same boat, it works fine but the LED is always on, i just want it to flicker because i want it to. But im happy how it is now while i get everything else up and running.

---

### Post by BUGabundo on 2008-05-15
did any u guys have trouble using the soft switch fn+F2?

i dont have any "real" button, just the keyboard shortcut, but I dont seem to be able to turn off the radio kill switch....

please help
more info at [https://answers.launchpad.net/ubuntu/+question/32865](https://answers.launchpad.net/ubuntu/+question/32865)

---

### Post by reggie_mac on 2008-05-29
My kill switch isn't part of the Fn buttons, its a seperate switch on the front and its works fine. If i remember correctly i chose a different type of keyboard layout than the default to get all my Fn buttons working correctly, but i did that at the install. my setup is :

 Keyboard Model : Generic 105-key (intl) PC
 Layout : USA International (ALtGr dead keys)

I'd check out the keyboard stuff and maybe that'll sort you out.

---

### Post by sirix on 2008-06-08
any updates?

---

### Post by EarloftheWest on 2008-07-16
I posted my most recent experiences here:
[http://ubuntuforums.org/showthread.php?t=759157&page=2](http://ubuntuforums.org/showthread.php?t=759157&page=2)

---

