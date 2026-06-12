---
title: "help with WUSB54Gv4 and ndiswrapper.."
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Mia_tech on 2007-01-21
I'm trying to get WUSB54G working with 6.10, after installing ndiswrapper, and wpasupplicant, with synaptic, issued this command

sudo ndiswrapper -l
sudo ndiswrapper -i /home/username/filename.inf
sudo ndiswrapper -l 
rt2500usb             driver installed, hardware present
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found   " this is where I think is the problem"
sudo ndiswrapper -m

of course I configure my connection with admin--> network entered my essid, and network password, using the plain test ASCII, also tried 
sudo /etc/init.d/networking restart       "it tries to negotiate an ip, but unsuccessful"
also tried restarting OS, same result unable to connect 

any help appreciated
thanks

---

### Post by teaker1s on 2007-01-21
install 
**ndiswrapper-utils-1.8**

---

### Post by Mia_tech on 2007-01-21
> **teaker1s said:**
> install 
**ndiswrapper-utils-1.8**

I made sure every ndswrapper  tool was installed from CD, including ndiswrapper-utils-1.8, it shows as installed under synaptic

---

### Post by teaker1s on 2007-01-21
strange, in edgy the module is there by default I believe, I know that there is problems from repository installed ndiswrapper. 
While I don't know the answer in your case I have had success with the version compiled in my signature

---

