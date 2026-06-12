---
title: "Broadcom 43xx"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by genuchelu on 2008-02-29
Hi, I have a Compaq Presario C300, and apparently I have the Broadcom 43xx network card. I installed the firmware using the restricted driver window..and I got it to turn on and find network. The problem is that I am unable to connect to my router. I investigated further and realized that I am able to connect to it only if I disable the wireless security. Is there a way I can make the on board wireless card connect to a secured connection? 

If I set a password (WPA Personal) to the connection, I try to connect to the router via network manager, and I get a pop up asking for the wireless key. I type it in, and a few seconds later it appears again... Basically it just goes into a loop asking me for the key over and over and over again.

---

### Post by RussellGee on 2008-02-29
Could just be Network-Manager.Its not the easiest to setup with encription.

Try downloading wicd which basicly is a network manager replacement except works alot better with wirless.

go to Settings > Repositories > Third Party Software > Add

Add this:     deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

If your not using gutsy then change to edgy, feisty ect.

Then: 

sudo apt-get update
sudo apt-get install wicd

Launch it from Applications > Internet > Wicd

More info at: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Hope that helps you.;)

---

### Post by sillyxone on 2008-02-29
I had two laptops with BCM43xx, the first thing I always do after installing Ubuntu is to blacklist BCM43xx (rmmod) and then install ndiswrapper to use the Windows driver. When I use BCM43xx firmware, wicd can see the wireless networks but couldn't connect to them (even on unsecured wireless).

basically install ndiswrapper, copy bcmwl5.inf and bcmwl5.sys from Windows driver, then follow ndiswrapper manual to add the driver.

wicd is definitely better than NetworkManager, and the new update is much more stable.

---

### Post by genuchelu on 2008-02-29
> I had two laptops with BCM43xx, the first thing I always do after installing Ubuntu is to blacklist BCM43xx (rmmod) and then install ndiswrapper to use the Windows driver. When I use BCM43xx firmware, wicd can see the wireless networks but couldn't connect to them (even on unsecured wireless).

basically install ndiswrapper, copy bcmwl5.inf and bcmwl5.sys from Windows driver, then follow ndiswrapper manual to add the driver.

wicd is definitely better than NetworkManager, and the new update is much more stable.

I'm not sure how to do that..i'm pretty new... if you could link me with a tutorial..


> Could just be Network-Manager.Its not the easiest to setup with encription.

Try downloading wicd which basicly is a network manager replacement except works alot better with wirless.

go to Settings > Repositories > Third Party Software > Add

Add this: deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras

If your not using gutsy then change to edgy, feisty ect.

Then:

sudo apt-get update
sudo apt-get install wicd

Launch it from Applications > Internet > Wicd

More info at: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Hope that helps you.

I installed, and it wont start. and now I don't have the traditional network manager-running or wicd.

any idea what went wrong? or how I can get one of them to work...

---

### Post by sillyxone on 2008-03-01
I don't remember exactly the steps, just give it a try and post questions:

1. Blacklist BCM43xx
run in terminal: sudo rmmod bcm43xx
edit the file /etc/modprobe.d/blacklist (either using nano in terminal, or gedit), add the line:
"blacklist bcm43xx" to the bottom of the file (similar to other entries in the file)

2, Install ndiswrapper (just use ethernet connection and synaptic)

3. Download the windows driver for your wireless card, unzip/extract it, copy the files bcmwl5.inf and bcmwl5.sys to a directory

4.in the same directory, type "ndiswrapper -i bcmwl5.inf" to install the driver, then run "ndiswrapper -l" to verify that the driver has been installed (you should see something like "driver installed")

5. run "sudo ndiswrapper -m"  so that it will be modprobe automatically on startup

6. run "sudo modprobe ndiswrapper", the wireless light on your laptop should be on now. if you run "ifconfig" in terminal, you should see both eth0 (ethernet) and eth1 (wireless) interface



if you already installed wicd but it won't start, run "ps ax | grep wicd" in terminal, if you couldn't see something like "/opt/wicd/daemon.py" then wicd is not running, ask for more help. If it is running, you can try to run the tray icon manually by pressing Alt-F2, and type in "/opt/wicd/tray.py". Usually when wicd installed, it removed network-manager automatically, or they will conflict. Please search for Network-Manager in  Synaptic to make sure it has been removed.


Using wicd is pretty straight forward. Feel free to ask for more detail.

---

### Post by genuchelu on 2008-03-02
I did everything in the above instructions, but I'm stuck at wicd connect to the network. For some reason it alwasy gets stuck at "Optaining IP address"...after a while it goes back to "Not connected". Another weird thing is that Wicd shows my router twice. One time with WPA next to the router name, and the other with just the router name by itself. I tried connection to my router that has WPA (since I know thats what it has), but i'm still unable to do so... what could be causing this? any other configurations in wicd I should be looking at? everything else in the instructions above worked out fine, with correct outcomes...

---

### Post by Presto123 on 2008-03-02
Ack...ndiswrapper when the normal driver works?

Well...the best thing to have done with WICD is to disable the Network Manager in System/Preferences/Sessions in the Startup Programs tab. Add in "WICD" as a new program with the command "wicd". Reboot.

---

### Post by genuchelu on 2008-03-02
> Ack...ndiswrapper when the normal driver works?

what do you mean?

---

### Post by sillyxone on 2008-03-02
> **genuchelu said:**
> what do you mean?

I think that's mean if it's working, don't fix it.

The reason I suggested ndiswrapper is to eliminate possible problems. Although BCM43xx driver does work, it didn't work for me a few time. On the other hand, ndiswrapper never failed me before since it uses the manufacture-guaranteed driver directly. It just my troubleshooting habit: try to isolate the problem by making every issues as good as possible.

try to start from a clean state: restart both your wireless AP and your computer. If possible, use another good computer, connect to the wireless to make sure the AP is OK. If you want to find the problem, try one variable at a time.

A few commands that might be useful: iwlist, iwconfig, dhclient

---

