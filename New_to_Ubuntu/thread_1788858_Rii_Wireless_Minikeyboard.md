---
title: "Rii Wireless Minikeyboard"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by mk78 on 2011-06-23
Guys,

1st of all "hi" since it's my 3rd post here, and most of you haven't ever seen me on this forum.
I recently bought one of these [http://www.initcron.org/wp-content/u...Keyboard_2.jpg]("http://www.initcron.org/wp-content/uploads/2010/10/Rii-Mini-Wireless-Keyboard_2.jpg")

I opened my lappy with Ubuntu 11.04, run bluetooth, paired, and... bang! It's working! :smile:
Then I have installed Ubuntu 10.10 minimal version for XBMC on other machine. I followed this manual [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)  but no joy. System says it's paired and trusted, but it just simply  doesn't work. I believe, as it works with Unity (and Gnome)  it should work with Ubuntu 10.10 + XBMC, am I right?

Thanks for your replies.

---

### Post by drascus on 2011-06-30
I would think So. One thing that you might want to try is open up synaptic and look up blue tooth and see if there is anything installed on your computer that it works with that isn't installed on the the computer that it doesn't work with. If there isn't anything to install try to just delete the keyboard from the bluetooth manager and reinstall it and see if that works. you might want to run an lspci from command line and fine out a bit more about the bluetooth card that you have and if there has been any support issue with it. 

Let us know how you make out. 
Mike

---

### Post by wildmanne39 on 2011-06-30
Hi, more then likely since you did a minimal install on the one that is not working, you just do not have what is needed for it to work installed. That is the downside to minimal installs when you need something extra you have to install the required packages for it. Use synaptic, in the search box type bluetooth and it should bring up all the bluetooth packages.

---

