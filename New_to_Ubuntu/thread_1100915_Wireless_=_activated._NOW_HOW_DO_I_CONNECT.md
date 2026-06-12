---
title: "Wireless = activated. NOW HOW DO I CONNECT??"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-03-19
Alright, after a long struggle, I finally got my wireless working on Ubuntu 8.10. For anyone who has been following my posts, yes, I installed Kubuntu, but I replaced it almost immediately with Ubuntu. 

I have wireless enabled, but I don't know how to scan for my router... Can anyone help?

---

### Post by bobnutfield on 2009-03-19
> **RAZRBAKK said:**
> Alright, after a long struggle, I finally got my wireless working on Ubuntu 8.10. For anyone who has been following my posts, yes, I installed Kubuntu, but I replaced it almost immediately with Ubuntu. 

I have wireless enabled, but I don't know how to scan for my router... Can anyone help?

If your wireless is actually working, there should be a signal strength indicator in your top taskbar.  Like a small graduated graph in blue.  Left click on that and it should show you all of the connection points within range.  From the command line, you could type:

> sudo iwlist wlan0 scan

Hope that helps

---

### Post by RAZRBAKK on 2009-03-19
> **bobnutfield said:**
> If your wireless is actually working, there should be a signal strength indicator in your top taskbar.  Like a small graduated graph in blue.  Left click on that and it should show you all of the connection points within range.  From the command line, you could type:



Hope that helps

I have the signal strength in a pull down bar when I click the 2 side by side computers.

I have the correct WEP key, but I cannot seem to connect...

---

### Post by ntrgc89 on 2009-03-19
I've had a similar issue with my wireless. I give it the correct key and it connects, but after a few reboots it refuses to connect, despite the fact that none of the settings have been changed.

What normally works for me is making new settings on my router and then feeding those into the wireless prompt.

And just to be safe, make sure all your setting match up (i.e. WEP 64-bit/WEP 128-bit/WPA, whatever) on both the router and computer.

---

### Post by RAZRBAKK on 2009-03-19
> **ntrgc89 said:**
> I've had a similar issue with my wireless. I give it the correct key and it connects, but after a few reboots it refuses to connect, despite the fact that none of the settings have been changed.

What normally works for me is making new settings on my router and then feeding those into the wireless prompt.

And just to be safe, make sure all your setting match up (i.e. WEP 64-bit/WEP 128-bit/WPA, whatever) on both the router and computer.

Mine won't even connect in the first place... I'm going to reset everything.

Thanks for the help, though!

---

### Post by acimmarusti on 2009-03-19
what is your wireless card? PCI? USB?

---

### Post by 73ckn797 on 2009-03-19
What brand of router do you have?

Maybe try a different encryption. I use WPA2 and have no problems.

---

### Post by RAZRBAKK on 2009-03-19
It works perfectly now. I switched to a 64bit WEP key instead of 128...

---

