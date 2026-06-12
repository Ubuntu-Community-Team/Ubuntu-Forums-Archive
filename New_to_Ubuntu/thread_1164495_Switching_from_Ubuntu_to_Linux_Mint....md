---
title: "Switching from Ubuntu to Linux Mint..."
date: 2009-05-19
forum: New to Ubuntu
---

### Post by hellothere2 on 2009-05-19
How do I switch from Ubuntu to Mint?  I know how to get Mint, but do I need to delete Ubuntu or something?  I'm a total beginner.  Thanks!

---

### Post by raymondh on 2009-05-19
> **hellothere2 said:**
> How do I switch from Ubuntu to Mint?  I know how to get Mint, but do I need to delete Ubuntu or something?  I'm a total beginner.  Thanks!

Out of curiosity, have you tried to virtualize?  I find it (virtualization) very useful when trying out other distros. But, if you've made up your mind, you can always install mint over/on top of your Ubuntu install.  When you reformat, that will erase your current ubuntu install.

Good luck on your endeavors ..... try virtualbox :)

Regards.

---

### Post by hellothere2 on 2009-05-19
> **raymondhenson said:**
> Out of curiosity, have you tried to virtualize?  I find it (virtualization) very useful when trying out other distros. But, if you've made up your mind, you can always install mint over/on top of your Ubuntu install.  When you reformat, that will erase your current ubuntu install.

Good luck on your endeavors ..... try virtualbox :)

Regards.

 I've just gotten too frustrated trying to get internet connection in ubuntu and heard that it might be easier in mint.  I have a wireless networking adapter (Linskys USB54GC version 3) and am having no luck getting connection.

---

### Post by MontelEdwards on 2009-05-19
Well Mint is based off of Ubuntu.
I personally do not find anything different about it, except the Gnome Panel, which can be installed on Ubuntu. What you heard is probably wrong. And if you do want Mint, just burn a Mint CD and boot it just like you did Ubuntu. 


Last time i used Mint it was instable, but that may have changed in the last 2 years.

---

### Post by xavierp94 on 2009-05-19
You just burn the cd for Mint and run the installer.

Download the ISO:
[http://www.linuxmint.com/download.html](http://www.linuxmint.com/download.html)

---

### Post by raymondh on 2009-05-19
> **hellothere2 said:**
> I've just gotten too frustrated trying to get internet connection in ubuntu and heard that it might be easier in mint.  I have a wireless networking adapter (Linskys USB54GC version 3) and am having no luck getting connection.

I understand your frustration until I realized that I simply needed the drivers for my wifi card. In my particular case, I had a realtek driver 8187 on my MSI wind.  Here is the link I used for your reference:

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Also. I have seen threads where some posters/forum members advocate using wicd which, they say, is better and easier to use than the standard network manager.  WICD can be found at synaptics ... that is if you are able to connect (ethernet) to the internet.  

I am no wifi expert but am willing to give this a try ... if you wish.  If not, may I suggest that you try the mint liveCD (hoping they have one) as liveCD's are good indications for that specific distro vis-a-vis your hardware/system.

It is supper time now and I promised my kids pizza.  If you want, I will check back in 1-2 hrs. to see if you want to give it another try.  In the meantime, try the liveCD of mint.

Regards.

---

### Post by cjv8888 on 2009-05-19
Have you tried the live CD of Mint to see if the wireless works?  If that works then you should not have much problems generally.

I also use a Linksys WUSB54GC which works out of the box in both Ubuntu and Mint, but it is probably version 1 or 2, different from yours.  Best thing is to try the live CD to see if you can make it work, if necessary using Ndiswrapper.

---

### Post by Duskao on 2009-05-19
Yeah, I am going to agree with cjv. Give Linux Mint Live cd a try before you for go for the whole install.
My wifes laptop with a very similar wifi card gave me problems at first as well. I hooked it up to the net hard wired at first to download the ubuntu updates for ubuntu. After I did that my video and wifi drivers were available in "system - Administration - Hardware Drivers". So if you can hook it up to the net by hard wiring it for a few minutes give it a try. 

What version of ubuntu are you using?

Also just so you are aware, Linux Mint is based off of Ubuntu (which has been mentioned before) but it didn't state that it uses an older version of ubuntu then the latest one. They are usually 1 release behind ubuntu. 

Best of luck

---

### Post by hellothere2 on 2009-05-19
Yeah, I have to use the adapter to have internet, which is a catch-22, b/c it's damn near impossible for me to get the adapter working on ubuntu w/o internet.  Honestly, i just want to give linux a shot.  Any suggetsions on which distribution would be easiest to get this adapter up and runnign?

---

### Post by lindsay7 on 2009-05-19
fyi, I have this adapt and it works fine Ubuntu out of the box.

---

### Post by hellothere2 on 2009-05-19
> **lindsay7 said:**
> fyi, I have this adapt and it works fine Ubuntu out of the box.

Not for me.  do you have version 3?

---

### Post by Sarai the Geek on 2009-05-19
I believe the main difference between Mint and Ubuntu (besides the panel, extra GTK themes, and Mint tools) is that Mint comes with unfree codecs and drivers preinstalled. It's not that the drivers aren't available for Ubuntu, Mint just saves you time searching for them. That said, not all drivers are included- the Broadcom STA driver needed for most broadcom wireless cards (like mine) isn't included. In fact I had trouble getting that driver installed in Mint, when it's very easy to install in Ubuntu. That said, I got bored of trying after about 20 minutes and went back to Ubuntu.

Bottom line: if you like the UI of Mint and the Mint Tools, go for it. Download the live CD and if the wireless works out of the box, then great. Otherwise, it's probably not worth the effort.

---

### Post by gymophett on 2009-05-19
Manually partition in the installer and just overwrite Ubuntu. :)

---

### Post by lindsay7 on 2009-05-19
I can not find the version number but the chip set or driver is Linksys WUSB54GC 802.11g Adapter [ralink rt73]

I have tried it on two different Ubuntu systems.

---

