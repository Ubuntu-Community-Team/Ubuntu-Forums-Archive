---
title: "Network Manager install with live cd"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by tanman on 2007-01-16
I have Edgy running on my desk top, but would also like to put it on my laptop. When I run the live CD I can get Ubuntu to see my wireless router which is WPA protected. When I run networking through the admin menu it asks for my ssid , but also my hex password, which I understand is a wep key.
When I install wlassist it sees my router, but once again asks for a wep key. When I nstall network manager gnome I can not find the program. I now see that I have to reboot, but If i reboot with the live cd I am back to square one again. I do want to put Ubuntu on my laptop, but just want to make sure that I can connect to my router.
Any suggestions would be great.
If I can run something from the terminal would be OK though I am still getting used to using it.
Thanks

---

### Post by spd106 on 2007-01-16
Open the /etc/networks/interfaces file and put a # in front of every line except those for lo. **gksudo gedit /etc/network/interfaces**
I.e```

auto lo                                     #  < -- Leave this alone or expect breakage
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

iface eth0 inet static            #  <-- If static leave alone
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

#auto wlan0
#iface wlan0 inet dhcp
```
Alternatively make sure that the interfaces have been disabled in network-admin (System -> Admin -> Network).
The restart network manager with this command **sudo /etc/dbus-1/event.d/25NetworkManager restart**

---

### Post by tanman on 2007-01-16
Thanks for the response.
I just have a stupid question though. Do I put "gksudo gedit /etc/network/interfaces" in the terminal and then I will get the code that you put in the text box and then put # in the places you asked. I do use dhcp.

Also should I install network-manager-gnome from the terminal first.

The command "sudo /etc/dbus-1/event.d/25NetworkManager restart" will actually restart everything with out rebooting?

Sorry about the questions, but I am still trying to get the hang of the terminal and commands.

Once again thanks for the help.
I am really hoping to get this to work for I have already gotten rid of my windows partition from my desktop and hoping to go all linux.

Thanks again

---

### Post by spd106 on 2007-01-16
Yes, you quite right to question.

The first command will open a text editor will root privileges to allow you to modify the file. Just put the hashes in so that you don't have to delete any information you may need later.

You may be more comfortable following this guide [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by tanman on 2007-01-16
Thank you so much. It works really well. I never thought of logging out and then back in. 
I try to figure these things out before asking questions, but I never came across that section of the wiki.
Once again thank you.

---

