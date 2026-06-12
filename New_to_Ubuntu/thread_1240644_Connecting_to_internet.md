---
title: "Connecting to internet"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Majik_420 on 2009-08-14
I just installed Kubuntu, but I can't figure out how to even setup my network connection. I found someone else had the same problem, and someone said to check the /etc/network/interfaces file. This is what mine says: 
auto lo
iface lo inet loopback

This isn't right is it? 

I tried setting up my network, Got the connection and the password, but theres no "Connect" button or anything or any tray icons for anything like that.

---

### Post by john stiles on 2009-08-14
I'm on Ubuntu and auto lo is fine for me.  Are you connecting through a router? Has this been set up by your provider? All you normally need to do is simply join your computer and router by cable and you are away without any further configuration (cause it was all in the router). There is no need for a connect button, you are connected. Open the browser and try.  

If you need to set up the router your ISP should have given you a list of instructions with default gateway and such settings. Connect to the router as before open your browser and in the address enter 192.168.1.1 . I hope the top of any list from the ISP will give user and password for the router and then fill in the boxes or follow any setup wizard.

---

### Post by Majik_420 on 2009-08-14
> **john stiles said:**
> I'm on Ubuntu and auto lo is fine for me.  Are you connecting through a router? Has this been set up by your provider? All you normally need to do is simply join your computer and router by cable and you are away without any further configuration (cause it was all in the router). There is no need for a connect button, you are connected. Open the browser and try.  

If you need to set up the router your ISP should have given you a list of instructions with default gateway and such settings. Connect to the router as before open your browser and in the address enter 192.168.1.1 . I hope the top of any list from the ISP will give user and password for the router and then fill in the boxes or follow any setup wizard.

Alright well I'm not at home right now so I can't access 192.168.1.1 but Ill try that when I get home.

And I would need to acutally use a cable to connect to my internet? I'm on a laptop, so I just go with my wireless, or do i just need to connect it once to get it to register or something?

And how would I connect in my situation when I am not at home and can't use a cable or anything? should I not be able to see the available connections in range and connect as with windows or even Ubuntu...?

---

### Post by john stiles on 2009-08-14
You will need a cable to initially set up your internet and wireless connection, but once done you can pack it away.

After setting up the router and accessing/testing the internet by wire, you can then think about wireless.

To set up a wireless connection you need to physically connect to the router. Following the 192.168.1.1 bit from before, you should also find a tab/section for wireless. You will need a name for your network (SSID). Check that your laptop can then see the SSID and connect to it and the internet. Once successful I recommend going back into the router and setting WPA encryption with a strong password. You will need to repeat this on your laptop. I hope that after this you will have a secure wireless connection.

If you are away from home it is a very mixed bag. From free and open wireless in Mc Donalds, to Starbucks pay as you go, to zip nada. If you are out and about often and need connection, consider buying a 3G usb dongle (it's a sim card in your computer). Just pop into any Orange/Virgin media store and they will give you rates and deals for that (aprox 20 quid each month, often less).

---

### Post by Majik_420 on 2009-08-15
> **john stiles said:**
> You will need a cable to initially set up your internet and wireless connection, but once done you can pack it away.

After setting up the router and accessing/testing the internet by wire, you can then think about wireless.

To set up a wireless connection you need to physically connect to the router. Following the 192.168.1.1 bit from before, you should also find a tab/section for wireless. You will need a name for your network (SSID). Check that your laptop can then see the SSID and connect to it and the internet. Once successful I recommend going back into the router and setting WPA encryption with a strong password. You will need to repeat this on your laptop. I hope that after this you will have a secure wireless connection.

If you are away from home it is a very mixed bag. From free and open wireless in Mc Donalds, to Starbucks pay as you go, to zip nada. If you are out and about often and need connection, consider buying a 3G usb dongle (it's a sim card in your computer). Just pop into any Orange/Virgin media store and they will give you rates and deals for that (aprox 20 quid each month, often less).

alright cool thanks, ill try hooking up a cable when I get home and check that 192. stuff. As for the 3G card thing, I live in Alaska so I'm pretty sure we don't have those up here yet. So as for internet on the run, I might as well just keep using Windows for internet on the run, I still have to learn and get used to Kubuntu anyway. thanks

---

### Post by Majik_420 on 2009-08-15
alright I plugged in... internet works fine wired. But 192.168.1.1 doesn't take me anywhere, says the connection is refused. And I still can't make any sense of the networking menus in Kubuntu. What should I do since 192... doesn't work? How can I configure a Wireless Network connection to my printer and the internet?

---

### Post by Crunchy the Headcrab on 2009-08-15
To connect to your router try 192.168.0.1

If you were already using wireless under a different operating system then you don't need to set it up again.

The version of Knetwork Manager that ships with Kubuntu 9.04 isn't great.  I suggest using wicd instead.

sudo apt-get wicd (in the terminal)

Sidenote:  I find it is easier to learn Linux under the gnome desktop environment (what Ubuntu uses).  Both gnome-desktop manager and synaptic (the ubuntu package manager) are leaps and bounds ahead of their kde counterparts in my opinion (at least in the latest versions of Ubuntu/Kubuntu).  To put your mind at ease gnome (ubuntu) applications and kde (kubuntu applications) both work on either Kubuntu or Ubuntu though.

---

