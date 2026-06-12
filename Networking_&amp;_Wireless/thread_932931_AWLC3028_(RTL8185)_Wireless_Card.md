---
title: "AWLC3028 (RTL8185) Wireless Card"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by untappedpilot2 on 2008-09-28
I've finally managed to get my Airlink AWLC3028 wireless card working on the most recent version of Xubuntu (Hardy) so I decided to write a tutorial for anyone else who is in the same boat I was!

-The installation process I describe here does require a working internet connection. I used the Windows Drivers via the ndiswrapper program.

1. Open the Synaptic Package Manager and install ndisgtk. This will require you to install ndiswrapper-utils-1.9 and ndiswrapper-common. Do it.

2. After installation of ndiswrapper you're going to need to get ahold of the Win98 Drivers for AWLC3028. They can be found on the installation CD you received with your wireless card or they can be found at [www.airlink101.com](www.airlink101.com) 

(The driver file you want is the net8185.inf found in the Win98 directory.)

3. Copy the .inf file from your CD or .zip file to your User Directory. 

4. Click Applications > System > Windows Wireless Drivers and click Install New Driver. Then point to the .inf file you just placed in your directory. 

5. At this point it should say net8185 hardware present: yes and the act led light on your wireless card should start blinking. 

6. From the point go ahead and open up the terminal. Go ahead and type ndiswrapper -l to verify you have the driver installed properly. You should get..

net8185 : driver installed
device (10EC:8185) present

7. In the terminal type sudo gedit /etc/modprobe.d/blacklist and make sure you have 

blacklist rtl8187
blacklist rtl818x 

8. Go to Applications > System > Network. Unlock this and select the Wireless Connection and click Properties. Under properties select the connection you plan to use, pick your encryption type, enter your key, and select automatic configuration. 


You're done! Your wireless connection should be working from here, if not you may need to reboot but you should be set. Let me know if this works for you or if you have any problems.u

---

### Post by nathhad on 2008-09-29
Thanks!  This HOWTO is spot on.  

I did this about eight months ago on my fiancee's laptop, and it took me a couple of weeks of light off-and-on searching and mucking about to find the solution.  I forgot to save my bookmarks to the fix.  Just sat down to reload the same laptop with a fresh install (we wanted a better partition arrangement than my first go), and wasn't looking forward to trying to remember the process.  Thanks to this HOWTO, I had the wireless up and running on her Gateway MX3414 with RTL8185 chipset wireless in about five minutes.

Chuck

---

### Post by n.brenner on 2008-10-18
Everything worked except wont link and im sitting underneath the router

HELP.......???

---

### Post by rattis on 2009-01-28
Trying to do this, but it freezes at number 4. Then on a reboot never gets past trying to configure network.

---

