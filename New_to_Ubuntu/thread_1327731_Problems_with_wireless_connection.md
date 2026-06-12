---
title: "Problems with wireless connection"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Sidthedeviant on 2009-11-15
I switched over to Ubuntu last night (v9.10) from windows, installation went smoothly but today when I tried to set up my wireless connection on it I ran into issues.

My router is set up through another computer in our house and the network shows as available but when I attempt to connect to it it just repeatedly asks me to enter the security password. I verified that the password was correct and that it is stored in the keyring  but the problem persists. 

Any thoughts?

---

### Post by -kg- on 2009-11-15
> My router is set up through another computer in our house and the network shows as available but when I attempt to connect to it it just repeatedly asks me to enter the security password. I verified that the password was correct and that it is stored in the keyring but the problem persists.

I am assuming that the network shows as available in the Ubuntu "Network Manager" applet, so apparently that's working right.  I'm not sure of the status of Network Manager in Karmic, but it works perfectly in Jaunty (for me).

In your home network, which security protocol are you using; WEP or WPA?  Are you entering your security key (your password?) under the correct protocol?  If you are using WPA for your router and you use WEP under Network Manager, naturally it won't work.

Of course, you also have to have the correct selections when configuring your wireless network.  I'm using WEP, and under "Security" in the configuration menu, I have several selections for the security scheme.  I have "WEP 40/128-bit Key" selected.  You may have to edit things a little before you find the right settings that will enable your wifi to operate.

It might possibly be that your specific wifi chipset has issues.  I remember reading that some people were having problems in entering their security codes and connecting with the network or router, but most of what I read on that issue concerned the networking widget under the newer Kubuntus.  That's an area you might need to research.

So far, I personally have had no issues with wifi other than to enter my security key.  That doesn't mean that it will work like that for everyone who installs it.  This will give you a start and a few things to check initially.  Also, what kind of wireless card or chipset do you have?  That will help us loads.

---

