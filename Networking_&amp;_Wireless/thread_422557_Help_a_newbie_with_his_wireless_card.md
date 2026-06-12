---
title: "Help a newbie with his wireless card"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by macka` on 2007-04-25
Hi there, 

i have a RTL-8185L Wireless chipset on my card.  Hence I have gone to the Realtek site and got the appropriate linux drivers. 
Tried to compile these, but it didn't seem to want to work. Just exited with an error, i  can post the log if someone needs it. 

I have tried using ndiswrapper, and the card seems to detect my network however it only seemed to support WEP, so not really a solution as i want to be able to use WPA (since my DD-WRT linksys firmware does!)

So - really my question is, does anyone have the same chipset, and have they managed to make it go under linux? and how does one tackle this.  Can they give me a pointer or 2?

Cheers
Grant

---

### Post by chili555 on 2007-04-25
Try here: [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

---

### Post by macka` on 2007-05-06
thanks - didn't seem to help much? is there anything i can post now to get some ideas from people?
cheers
Grant

---

### Post by Intel D805 on 2007-11-03
Whatever you are doing just stop. I went through the same problem. 

If you are not using 7.10 Gusty. I recommend you do so simply because it works better on the internet, 

You will have to blacklist the linux driver called r8180.

Bring up terminal. How to access terminal? Look up to the left of the screen and see the word Application...click....then Accessories....click then Terminal...click.

The terminal window should pop up.

Type in these commands...after the commands hit enter on keyboard:

sudo su 

Terminal asks you for password...type in your password and hit enter.

gksudo gedit /etc/modprobe.d/blacklist

Hit enter

By the time you hit enter on keyboard the file should pop up and show you the list of items that are blacklisted drivers.

Scroll down and see if you see any file related to your wireless card...if not then scroll down to the bottom type this

# Bad r8180 linux driver
blacklist r8180

Then you should see in the upper of that window and click save. Once you have saved it then reboot by shutting the computer off entirely not a simple reboot.,..I mean dead...no power. Then go ahead and power your PC up by time you are in the linux desktop the r8180 driver should be dead.

Use ndiswrapper to install your windows driver by finding the .INF for windows XP on your driver CD that came with your wireless card.

If you don't know how to use ndiswrapper or know how to install it...let me know.

I am using 7.10 and my airlink 101 3028 with R8185L driver is working flawless with the help of ndiswrapper 1.45 version.


As for experienced users please type your directions more clearly. The steps have I outlined above are few weeks of research I had to commit to find the answers.

:guitar: Enjoy!

---

### Post by lamarcheb on 2007-11-07
Thanks for the instructions on blacklisting drivers. It was my missing link.

Note that In 7.04 this driver (RTL8185) was blacklisted by default! (but not in 6.10). Anyway when I was configuring a 7.04 install a few months ago I read that the driver was blacklisted because it simply did not work. Right now it tries to connect but locks-up the machine ... the lights on the keyboard are blinking.

---

### Post by Aathos on 2007-11-08
There is also a quite good How-To [here]("http://ubuntuforums.org/showthread.php?t=580309").  It includes the instructions for ndiswrapper.

---

