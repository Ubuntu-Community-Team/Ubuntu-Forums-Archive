---
title: "New Dell Mini 12, trouble with wireless."
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Shope on 2009-04-16
Hello Everyone,

I just got a Dell mini 12 with ubuntu 8.04 on it. I am having trouble connecting to my wireless internet. It connected once for a period of time but does not seem to anymore. My network shoes up in the drop down menu and the keychain but when I click to connect it does not. Please help me, I am a TOTAL noob to Linux so please take it step by step with me. I tried to go through the troubleshooting but it is confusing. Thanks.

---

### Post by nothingspecial on 2009-04-16
You need to post what wireless card you have.

Open a termeinal Acessories > Terminal and type 
```

sudo lshw -c network
```

Then copy and paste the output in a post here.

---

### Post by illustria on 2009-04-16
> **nothingspecial said:**
> You need to post what wireless card you have.

Open a termeinal Acessories > Terminal and type 
```

sudo lshw -c network
```

Then copy and paste the output in a post here.

Hi - I'm having problems with Dell Mini 12, too. I can't get the wireless connection going. I tried this one, but the sudo lshw -c network code in terminal shows up as "sudo: lshw: command not found."

Oh boy...

---

### Post by illustria on 2009-04-16
UPDATE:

I got my manual out, and it says: WLAN, WWAN (Mini-Card) Bluetooth(TM) Wireless Technology.

---

### Post by LowSky on 2009-04-16
> **illustria said:**
> UPDATE:

I got my manual out, and it says: WLAN, WWAN (Mini-Card) Bluetooth(TM) Wireless Technology.

yeah sorry that means absolutly nothing... and nothingspecial they have preconfigured with Ubuntu Dell netbooks. The stuff should just work

Try rebooting your routers, sometime they can hang. Or you the network applet and delete the current known networks from trying to auto connect.


you canalso try another application to get wireless working called 
wifi-radar, open a terminal to install using this code.

sudo apt-get install wifi-radar

[http://thedailyubuntu.blogspot.com/2007/09/wifi-radar-ubuntu-wireless-application.html](http://thedailyubuntu.blogspot.com/2007/09/wifi-radar-ubuntu-wireless-application.html)

---

### Post by illustria on 2009-04-16
> **LowSky said:**
> yeah sorry that means absolutly nothing... and nothingspecial they have preconfigured with Ubuntu Dell netbooks. The stuff should just work

Try rebooting your routers, sometime they can hang. Or you the network applet and delete the current known networks from trying to auto connect.


you canalso try another application to get wireless working called 
wifi-radar, open a terminal to install using this code.

sudo apt-get install wifi-radar

[http://thedailyubuntu.blogspot.com/2007/09/wifi-radar-ubuntu-wireless-application.html](http://thedailyubuntu.blogspot.com/2007/09/wifi-radar-ubuntu-wireless-application.html)

Oh dear - it says Err

Failed to fetch and unable to fetch some archives? I'm working on my PC and trying to make my Mini12 work. Feel so helpless:(

By the way, how do I delete the auto-connecting wifi networks?

Thanks, by the way!

---

### Post by snowpine on 2009-04-16
Try plugging in to a wired ethernet connection and updating your system. You can do this either by clicking the little update manager icon on the toolbar, or, open a terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
```

Then reboot and see if the problem is solved.

Never used a Mini 12, but if it's the same as my Mini 9, it is a Broadcom bcm8312 card, and the pre-installed Dell version of Ubuntu should support it out-of-the-box.

---

### Post by illustria on 2009-04-16
Oh dear...errors...it can't resolve the dell canonical, the terminal says. now very sad indeed...

I tried it on ethernet but I couldn't connect either. What is with this laptop?!?!?

---

### Post by illustria on 2009-04-16
My laptop's working now! YAY!

---

### Post by &lt;m.&gt; on 2009-04-21
care to tell us how you fixed it?

I installed WINE and since then I don't get any hint that the computer even knows it has WIFI.  The network button just shows WIRED.  My MAC is pulling 2 wifi signals but my mini 12 sees nothing.  
I bet I have to plug it into a ethernet for some update....grrr....
I tried WIFI RADAR, nothing...
I also get "lshw not found" when I try terminal

---

### Post by Shope on 2009-04-22
> **nothingspecial said:**
> You need to post what wireless card you have.

Open a termeinal Acessories > Terminal and type 
```

sudo lshw -c network
```

Then copy and paste the output in a post here.

It says command not found. Would updating to 8.10 help? This is strange because sometimes my dell connects to wireless just fine and sometimes it doesnt want to.

---

### Post by Shope on 2009-04-23
ttt, anyone?

---

