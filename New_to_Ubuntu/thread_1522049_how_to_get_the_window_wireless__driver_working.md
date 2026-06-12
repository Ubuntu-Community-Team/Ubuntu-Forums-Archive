---
title: "how to get the window wireless  driver working"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by blackinferno on 2010-07-01
I was able to install the ndisgtk pakage onto my computer and as a result i could open Windows Wireless Drivers however i cant locate or seem to find the .inf file in order to run the program.

I am using a ACX 111 54MBPS wireless interface card plz help ty :)

---

### Post by bkratz on 2010-07-01
> **blackinferno said:**
> I was able to install the ndisgtk pakage onto my computer and as a result i could open Windows Wireless Drivers however i cant locate or seem to find the .inf file in order to run the program.

I am using a ACX 111 54MBPS wireless interface card plz help ty :)

You might look here to see if there is some help--

[http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx](http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx)

---

### Post by k3lt01 on 2010-07-01
> **blackinferno said:**
> I was able to install the ndisgtk pakage onto my computer and as a result i could open Windows Wireless Drivers however i cant locate or seem to find the .inf file in order to run the program First, ndisgtk has memory issues, it can forget that you have loaded the wireless drivers. You are much better off loading the driver via terminal commands which I will post below for you.

Second, what files do you actually have for the driver? If it is an .exe file then it wont work with ndiswrapper. You will need to find the driver source not the compiled .exe

If you have the driver source it is best to save it to your desktop, I also keep a copy of mine in my /home folder, so you can load the .inf file with terminal commands. Once you have this done follow this process in a terminal copying and pasting each command one at a time.

```
# Note: Make sure drivers are visible on the Desktop then copy and paste each command into a terminal to install the wireless network drivers for your wireless card.

# Note:substitute xxxxxxxx.inf for your .inf file.

cd Desktop

sudo ndiswrapper -i xxxxxxxx.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```
Let us know how you go.

---

