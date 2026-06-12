---
title: "Will network print servers work?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by joejoe148 on 2008-12-26
I recently installed hardy, and now that I have gotten my wireless working, my Printer working (direct connection) flash and java working and all the updates installed I now want the print server to work.  
I can almost make it happen by setting up the printer URL as lpd://"server IP address/lpt1

when I try to print a test page it begins but after every pass it gets slower and slower.  

I got this far by searching the forums.  I can access the print server config page easily.  

Is there some setup I am missing for networked printers?

---

### Post by cmnorton on 2008-12-27
What is the brand of print server, or is it a PC offering print services?

What kind of settings are available on the print server?

---

### Post by joejoe148 on 2008-12-29
Update:  the print server seems to be working but is very slow in comparison to things running from windows pc's.  also long files get progressively slower as it prints.  I havent tried to print anything complicated like a photo but the ubuntu test page came through.

buffalo usb print server model LPV2-USB-TX1  I dont know anything about the settings really.  it was easy to setup.  I will see if I can get a screen capture from the server home page

---

### Post by joejoe148 on 2008-12-29
I thought i attached a picture.  I suppose that will have to be another thread.

---

### Post by cmnorton on 2008-12-30
> **joejoe148 said:**
> Update:  the print server seems to be working but is very slow in comparison to things running from windows pc's.  also long files get progressively slower as it prints.  I havent tried to print anything complicated like a photo but the ubuntu test page came through.

buffalo usb print server model LPV2-USB-TX1  I dont know anything about the settings really.  it was easy to setup.  I will see if I can get a screen capture from the server home page

For a short time, we used Hawking print servers here in our production environment. I like Hawking hardware, but these servers were trying to do too much, serve as a DHCP server, and our firewall got a lot of packets that we traced back to these servers and did not have time to diagnose. 

Therefore, I am asking about the configuration of your print server to see if the whole "blue plate special" (all extra print server features) is turned on and might be slowing things down.

---

### Post by joejoe148 on 2008-12-31
thats a thought, I have no idea how to test it as it works well with windows.  I am going to just let this be for now and maybe build a real server and solve the problem that way

---

