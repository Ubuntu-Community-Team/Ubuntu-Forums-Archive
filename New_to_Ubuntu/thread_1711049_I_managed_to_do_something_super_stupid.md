---
title: "I managed to do something super stupid"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-20
I accidentally removed the wifi indicator from my top toolbar and I cant get it back. To top if off now I cant connect to the internet on that computer now. If I right click on the tool bar to "add to panel" its not in the list to put back. 

I'm hoping theres a way to go into terminal and restart it please please please help me.

---

### Post by durand on 2011-03-20
It might be Indicator Applet, Indicator Applet Complete or Notification area.

---

### Post by tordeu on 2011-03-20
Right click somewhere on the panel and select "Add to Panel..."

It will display you a list of items you can put on the panel. It should contain a Wifi indicator or Network indicator.

---

### Post by TexasRussian on 2011-03-20
If you go to System -> Preferences -> Network Connections, you can connect to your wireless hub that way, as for getting your Icon back you might want to try right clicking the panel on the top, click add to panel, then search for 'Notification Area'. That should work :D

Hope I helped.

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> Right click somewhere on the panel and select "Add to Panel..."
 
It will display you a list of items you can put on the panel. It should contain a Wifi indicator or Network indicator.
 
I already tried that but theres nothing to add thats remotely like that and its terminated my internet conection and I dont have a wired connection. Is there a terminal command to restart the network manager?

---

### Post by themusicalduck on 2011-03-20
Press alt+f2 and type nm-applet

If the wifi indicator re-appears then your notification area is still there and something else is wrong. If not, then most likely the notification area is not there.

---

### Post by DGINSD on 2011-03-20
> **TexasRussian said:**
> If you go to System -> Preferences -> Network Connections, you can connect to your wireless hub that way, as for getting your Icon back you might want to try right clicking the panel on the top, click add to panel, then search for 'Notification Area'. That should work :D
 
Hope I helped.
 
K adding the "Notification area" restored the applet, and also put up a mouse icon, but when i click on the icon it says there is no network adaptor available whats that about and how can I get things back to normal.
 
I rebooted hopeing it would start up my network connectors but no dice Odd all was fine before I pulled a stupid.

---

### Post by tordeu on 2011-03-20
If you use a laptop, have you checked if you accidentally disabled the wifi using a button or switch on the laptop itself?

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> If you use a laptop, have you checked if you accidentally disabled the wifi using a button or switch on the laptop itself?
 
So far as I know I have no such button or switch. I'm gonna boot my windows partition to make sure everything is working ok
 
When I go to additional drivers I dont show any, which there should be one for my wifi adaptor I tried installing it again (a real pain with no internet) but no luck.  All this for disabling an applet?

---

### Post by tordeu on 2011-03-20
Well, this not the normal behaviour for disabling an applet, so I assume there is something else wrong. Of course, it might be a bug of some kind. But it is a good idea to boot Windows and see if the problem is existent there too or not, which might help finding what the problem is.

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> Well, this not the normal behaviour for disabling an applet, so I assume there is something else wrong. Of course, it might be a bug of some kind. But it is a good idea to boot Windows and see if the problem is existent there too or not, which might help finding what the problem is.
 
On my Windows partition now and posting to the internet so my networking adaptors are in good working order. Isnt there an easy way to re-initalize previously used drivers?

---

### Post by 5149.5 on 2011-03-20
> **DGINSD said:**
> So far as I know I have no such button or switch. 

I haven't seen many that didn't. Look at all of the keys especially the function keys. The one you're looking for will have a symbol that looks a little like the applet only sideways.

---

### Post by tordeu on 2011-03-20
Thanks @5149.5, totally forgot that:

As 5149.5 mentioned, it might be a key combination that is used. Laptops normally offer "Function Keys" and pressing the function key and some other key does things like change the brightness of the display, the volume or enable/disable the wlan adapter.

As this only works in software, your wlan adapter would work under Windows, but Linux would have it disabled/shut off, so it probably would not even show as a network connection.

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> I haven't seen many that didn't. Look at all of the keys especially the function keys. The one you're looking for will have a symbol that looks a little like the applet only sideways.
 
Your correct I do have one I just forgot about it. It's in conjunction with a function button but since wireless was working with windows though I'm sure thats not the issue.
 
When I get to the connection preferences I dont show anything wired wireless nothing like I have no networking devices at all?

---

### Post by 5149.5 on 2011-03-20
Booting windows only proved that the WLAN hardware isn't defective.  You turned it off in linux so the mystery is discovering how you did it and undo that.

---

### Post by tordeu on 2011-03-20
Exactly, these function buttons do not turn the hardware like a real switch, they are just implemented in software. So basically, if you use the key in Linux, then the wlan adapter is typically not physically turned of, it's just a software setting. So it might indeed work in windows. It's like setting an ip address in linux does not make you have the same ip address when you boot windows.

---

### Post by DGINSD on 2011-03-20
This is where I'm lost all i did was remove the wifi indicator icon and try to get it back and now when I right click on the icon the enable networking box is totaly greyed out so I cant select it.
 
How could I reactivate the original networking and wireless driver that install with the live CD?

---

### Post by tordeu on 2011-03-20
You do not need to reinstall your driver. I am sure it did not just mysteriously uninstall.

Have you tried to check your function keys for a possibility to enable/disable the wireless device? You could also upload a picture of your keyboard layout if you want us to have a look.

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> You do not need to reinstall your driver. I am sure it did not just mysteriously uninstall.
 
Have you tried to check your function keys for a possibility to enable/disable the wireless device? You could also upload a picture of your keyboard layout if you want us to have a look.
 
OK I actually dont have a wifi off function key, it just looked like one. It was actually eject, my wifes which is also a Dell does though and its function F2, tried it to no avail.
Good Lord this is so frustrating I had most everything working pretty good too and I have this sinking feeling my only recoarse is reinstall.

---

### Post by tordeu on 2011-03-20
One thing you could try is

```

sudo /etc/init.d/networking restart

```

Otherwise please run the following two commands and post the output:

```

ifconfig
lspci

```

---

### Post by madjr on 2011-03-20
good thing in the next ubuntu version (coming in april) you wont be able to "accidentally" remove the network icon :)

---

### Post by 5149.5 on 2011-03-20
Try System>Admin>Networking tools>click configure>select the wireless tab>select your ssid from the entries. There is a check box for connect automatically. Is it checked?

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> You do not need to reinstall your driver. I am sure it did not just mysteriously uninstall.
 
Have you tried to check your function keys for a possibility to enable/disable the wireless device? You could also upload a picture of your keyboard layout if you want us to have a look.
 
Couldn't get a good picture that would make function keys visible
 
The only key that I dont get is "SysRq"

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> Try System>Admin>Networking tools>click configure>select the wireless tab>select your ssid from the entries. There is a check box for connect automatically. Is it checked?
 
On my loopback the configure button is in active (greyed out)

---

### Post by DGINSD on 2011-03-20
> **madjr said:**
> good thing in the next ubuntu version (coming in april) you wont be able to "accidentally" remove the network icon :)
 
Oh I cant wait idiots such as myself need to have things stupid proofed for them DuHHHHHHHHH):P

---

### Post by 5149.5 on 2011-03-20
> **DGINSD said:**
> On my loopback the configure button is in active (greyed out)

That would seem to indicate that all of networking is shutdown and doesn't have anything to do with wifi. Open terminal, enter ifconfig and paste the output in a post.

---

### Post by tordeu on 2011-03-20
> **DGINSD said:**
> On my loopback the configure button is in active (greyed out)

That's greyed out for me as well. Try choosing something else than the loopback interface. (e.g. example, I have an "Ethernet Interface" and an "Unknown Interface" as well. If you choose one of your interfaces, the Configure button should not be greyed out.

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> That would seem to indicate that all of networking is shutdown and doesn't have anything to do with wifi. Open terminal, enter ifconfig and paste the output in a post.
 
 
Here is the output it seemed to get a bit garbled in the linux text to windows text
 
> 
 
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:24:ea:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9080 (9.0 KB)  TX bytes:9080 (9.0 KB)
 
wlan0     Link encap:Ethernet  HWaddr 00:11:f5:04:99:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> That's greyed out for me as well. Try choosing something else than the loopback interface. (e.g. example, I have an "Ethernet Interface" and an "Unknown Interface" as well. If you choose one of your interfaces, the Configure button should not be greyed out.
 
 
If I select wlan and folow the rest of the instructions, yes I get a box checked that says automatically connect.

---

### Post by 5149.5 on 2011-03-20
> **tordeu said:**
> That's greyed out for me as well. Try choosing something else than the loopback interface. (e.g. example, I have an "Ethernet Interface" and an "Unknown Interface" as well. If you choose one of your interfaces, the Configure button should not be greyed out.

I'm wrong and both of you guys are right. I should have checked before I said anything. In that case choose your wifi connection in the dropdown box and resume the post above where I talked about setting the wlan for connecting automatically.

---

### Post by DGINSD on 2011-03-20
5149.5........O-side eh? I'm in Esco LOL

---

### Post by 5149.5 on 2011-03-20
> **DGINSD said:**
> 5149.5........O-side eh? I'm in Esco LOL

Don't even think about asking me to make a house call in this weather. :D

---

### Post by DGINSD on 2011-03-20
Just to reiterate the automatcally connnect is checked.
 
Seems odd that the propritery driver is no longer listed in that section?

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> Don't even think about asking me to make a house call in this weather. :D
 
Wouldn't dream of it, besides I wouldn't subject my worst enemy to a trip to Esco its bad enough I live here. Could be worse....could be stabbed.

---

### Post by tordeu on 2011-03-20
It seems to me that all that is lost might be the wlan configuration. Because ifconfig is correctly listing your wlan hardware.

If you go to System > Preferences > Network Connections and click on the "Wireless" tab, is the list empty or is there an entry?

---

### Post by 5149.5 on 2011-03-20
> **DGINSD said:**
> Just to reiterate the automatcally connnect is checked.
 
Seems odd that the propritery driver is no longer listed in that section?

OK.  Enter: nm-tool in a terminal and paste the output in a post.

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> It seems to me that all that is lost might be the wlan configuration. Because ifconfig is correctly listing your wlan hardware.
 
If you go to System > Preferences > Network Connections and click on the "Wireless" tab, is the list empty or is there an entry?
 
 
All my entrys are there, only one is available where Im at now (the one Im using on this computer)

---

### Post by tordeu on 2011-03-20
When you choose the entry from your wlan and click "edit", check that all the options are correct (the ssid of the wlan, the security (wep/wpa/...), try entering the password again, should you need a password)).

If that does not work, you might try deleting the entry and creating a new one again, entering ssid/security type and maybe password.

---

### Post by 5149.5 on 2011-03-20
> **DGINSD said:**
> All my entrys are there, only one is available where Im at now (the one Im using on this computer)

Then the output of nm-tool will really be relevant.

---

### Post by K_Boomer on 2011-03-20
Oh yes, I have done that before. This link should lead you in the right direction. Best of luck.

[http://ubuntuforums.org/showthread.php?t=423543](http://ubuntuforums.org/showthread.php?t=423543)

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> OK. Enter: nm-tool in a terminal and paste the output in a post.
 
 
Here's the output
 
> 
** (process:1928): WARNING **: _nm_object_get_property: Error getting 'WirelessHardwareEnabled' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
 
** (process:1928): WARNING **: _nm_object_get_property: Error getting 'WwanHardwareEnabled' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
 
** (process:1928): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
 
NetworkManager Tool

** (process:1928): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist

State: unknown

** (process:1928): WARNING **: error: could not connect to NetworkManager


---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> When you choose the entry from your wlan and click "edit", check that all the options are correct (the ssid of the wlan, the security (wep/wpa/...), try entering the password again, should you need a password)).
 
If that does not work, you might try deleting the entry and creating a new one again, entering ssid/security type and maybe password.
 
One of the first things I tried.

---

### Post by 5149.5 on 2011-03-20
OK. System> preferences>Startup applications. Is the box for Network manager checked? If not check it, log off and log back in.

---

### Post by tordeu on 2011-03-20
Which version of Ubuntu are you running? And do you use the elementarydesktop/elementary OS?

Oh, and I might have missed that, but have you tried
```

sudo /etc/init.d/networking restart

```
yet?

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> OK. System> preferences>Startup applications. Is the box for Network manager checked? If not check it, log off and log back in.
 
Yes it's checked. just for good measure I unchecked, rechecked and rebooted. No Joy

---

### Post by tordeu on 2011-03-20
Please run the following in your command line:
```
[FONT=monospace]
sudo apt-get remove connman
[/FONT]
```[FONT=monospace]

and then reboot

EDIT: Apparantly there might can be conflicts between connman and network-manager, which you probably have installed both, since they are installed by default. Maybe the problem started after an update.
[/FONT]

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> Which version of Ubuntu are you running? And do you use the elementarydesktop/elementary OS?
 
Oh, and I might have missed that, but have you tried
```

sudo /etc/init.d/networking restart

```
yet?
 
 
Just did, no dice as well it would seen that my N.M. is gone. Is there a way to reload from a live DVD?
 
BTW I'm running maverick

---

### Post by tordeu on 2011-03-20
Another thing you could try first (or afterwards) is to boot and choose a different kernel in GRUB.

---

### Post by 5149.5 on 2011-03-20
> **DGINSD said:**
> Yes it's checked. just for good measure I unchecked, rechecked and rebooted. No Joy

I thought that would do it. For some reason your Network manager isn't running which is indicated by the output of nm-tool, and I thought that would fix it.

---

### Post by DGINSD on 2011-03-20
> **tordeu said:**
> Another thing you could try first (or afterwards) is to boot and choose a different kernel in GRUB.

Tried that actually, third thing I tried. However your....
.```
[FONT=monospace]sudo apt-get remove connman
[/FONT]
```

......is a winner all is back to normal.

Thanks to both of you for all your help

---

### Post by 5149.5 on 2011-03-20
OK. Try Alt-F2. Paste: nm-applet --sm-disable    in the box. Click run.What happens?

---

### Post by tordeu on 2011-03-20
> **DGINSD said:**
> Tried that actually, third thing I tried. However your....
.```
[FONT=monospace]sudo apt-get remove connman
[/FONT]
```......is a winner all is back to normal.

Thanks to both of you for all your help

No problem. I am glad everything works now.

---

### Post by 5149.5 on 2011-03-20
OK Glad to see you got it going again. Disregard my last post. A conflict between connection manager and network manager. I learned something tonight.

---

### Post by DGINSD on 2011-03-20
> **5149.5 said:**
> OK Glad to see you got it going again. Disregard my last post. A conflict between connection manager and network manager. I learned something tonight.
 
 
I did as well thougt I'm still a bit confused on how this happened.
 
Oh, side unrelated question, when I boot my Windows partition it takes an unusually long time to finish booting, is that normal?

---

### Post by 5149.5 on 2011-03-20
My Win 7 came up normally the last time I checked.

---

