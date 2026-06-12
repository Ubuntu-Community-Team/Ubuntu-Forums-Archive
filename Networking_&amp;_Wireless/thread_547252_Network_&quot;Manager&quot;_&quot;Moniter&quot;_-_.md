---
title: "Network &quot;Manager?&quot; &quot;Moniter?&quot; - WPA help"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Seamus77 on 2007-09-09
I'm running Ubuntu Fiesty and wireless internet works fine.
However, I'm trying to access wireless at the university which uses WPA. I have a user name and password, but I have to way to enter it in any application I have to be able to connect.
I've been reading a lot here about "Network Manager", which I have installed through the terminal and through synaptic, and I've installed the wpa supplicant as well. It says that the latest version is installed.
However, I don't see "Network Manager" anywhere, neither in the panel nor on the bar. I've tried to add it to the bar, but it doesn't appear in the options. I've also tried to run it with alt f2, but nothing happens.
I have been using "Network Monitor" (which no one seems say much about on the forums) to manage my connections. I can connect to things that don't need wpa fine, change some settings, and save them. I can even see the signals that I am supposed to access at the university, but there's nowhere to enter the info I need to put in.This Network Monitor has an icon on the task bar with 2 monitors and the signal strength displayed which shows activity, etc. I've read that you can right click this and the possible networks should appear, but I just get "about" "properties", etc. 
Is this Network Monitor the same as Network Manager? It seems like it kind of is, but it doesn't do what I need it to do. If not, how do I get the network manager that I need?

---

### Post by bwhitaker on 2007-09-09
NetworkManager should open at boot by default on Feisty.  It is normally in your task bar, and left clicking on it should allow you to connect to a network.

I got WPA working on my laptop for my home connection in feisty and I remember it being fairly easy.  I think this is what you'll have to do:

Left click on the NetworkManager Icon in the system tray, if you don't have it go to a terminal and type:
```

sudo NetworkManager

```


Then go to connect to another wireless network.

Enter the Network Name, and Select WPA2 Enterprise.

This should be the place to enter the data provided to you by the university.


Hope this helps,

---

### Post by Seamus77 on 2007-09-10
Thank you for your response.
I don't have an icon for Network Manager, so I can't left or right click anything. When I sudo it in the terminal, I then enter my password and then nothing happens - I get the command prompt again. It's like it's already running or something.
I can see the applet running in the system monitor, and again, I have it downloaded and installed, but I can't access it in any way to make any changes or click anything to go through any graphical windows. For all intents and purposes, it's not even there.
Any other suggestions?

Thanks again.

---

### Post by luisjorge on 2007-09-19
Hi!

The "Network monitor" you have in your panel is not the same as the "Network manager" you are looking for. This last one doesn't appear in the "Add to panel" section. Therefore, try pressing Alt+F2 and type in:

nm-appler --sm-disable

The network manager icon with the signal strength an all that should appear in the panel. If not, check if you have the "notification area" in your panel, if not, add it through the "Add to panel" option. Then, the network manager should be there. Also, you can add it to your startup programs by choosing  System-- Preferences-- Sessions and check if there is an entry with "Network Manager". If not, you can add a new one with that name, and type the command:

nm-appler --sm-disable   (same one as before).

The network manager icon should now appear every time you boot.
As for the WPA, try what bwhitaker says! :)

Hope this helps!

Luis Jorge

---

