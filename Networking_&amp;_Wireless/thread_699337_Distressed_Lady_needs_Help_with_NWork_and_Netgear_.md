---
title: "Distressed Lady needs Help with NWork and Netgear DG834GT WAS working!"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Mayborn on 2008-02-17
Hello, I hope someone has the answer to this very puzzling occurrance!  I installed the above mentioned Router to PC and a Netgear WG511T PC card for the Laptop. It worked perfectly well until midway through this morning! Now, I cannot go online with the PC but CAN with the Laptop, I've tried viewing the Router page on the PC by typing 192.168.0.1 into address bar but it doesn't load, and the network shared folders have disappeared! I can only see the Laptops on the laptop and the PCs on the PC.  

I've noticed about 3 times in the past 2 hrs the connection to the internet has dropped.  I have no idea what is wrong or how to put it right.

I don't understand, it seems the PC is set up as the main station, yet the internet connections is bypassign it but I can connect on the Laptop. 

I don't know what o try next.  I unplugged from power and disconnected the ADSL plug from the router for 5 minutes, maybe that might clear something but no.  

--------------------

I've just gone into look at the PC, and low and behold, I CAN SEE ALL SHARED FOLDERS AGAIN!  I'm very mystified now, and my questions still stands.  Is there anyone please that knos what's happened?

Many thanks

Maybaby

Anyone please?

---

### Post by Speedoo on 2008-02-17
Hi Mayborn,
Not sure what your problem is, but I have a continual problem with my wireless dropping out on my laptop, due to the internal Realtek RTL8187B wireless adapter, which is not very linux friendly!
I've discovered that I can usually reconnect manually by issuing the following commands in the terminal:

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "<insert your network name here>"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

In fact, I need these commands so often that I wrote a little shell script called wdown, so now I just type "sh wdown" and (usually) get my wireless reconnected.
Hope this is of some help,

---

