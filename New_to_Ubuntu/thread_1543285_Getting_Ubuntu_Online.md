---
title: "Getting Ubuntu Online"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Complete on 2010-07-31
I have an old computer with 128 megs of memory and one hard drive of 120 gigs.  I have gone back and forth between installing Ubuntu and Puppy.  Right now, despite advice against it because of the limited memory, I am thinking of sticking with Ubuntu.  Puppy has some problems but that is not what I want to address right now.  What I want to ask about in this discussion thread is how to get Ubuntu onto the Internet.

I think I get it, but I want to be sure.  There is a menu option called "Network Connections" and it opens a window that has several tabs.  Since I have a wired connection, I click on the "Wired" tab where it shows my connection in a list box.  When I click on Edit it opens another window that displays a MAC address and there is an "Apply" button.  When I click on this, there is an Authenticate window that opens up and it prompts me for a password.

Here is my question.  Is this password that it is asking for the same thing as the password that my router uses?

---

### Post by joshedmonds on 2010-07-31
I'm not sure how you normally connect, but you say you have a router (+modem?) with a wired connection. If the connection to your ISP is established using information stored in the modem (the normal way a home connection is set up), the internet connection will happen whenever the modem is turned on, and the ethernet connection should be recognised automatically by Ubuntu (and the network icon in the top panel will change to 2 opposing vertical arrows.)

If you use some sort of dialer or connection manager then consider whether it would be easier to store those details in the modem instead.

Hope that helps.

EDIT: The apply button will apply any changes you make to those settings. The password is likely the Gnome-keyring password, although I am happy to be corrected on this. If you already see the wired connection, you should be able to open a browser and use the internet (or open a terminal and ping an ip)

---

### Post by louieb on 2010-07-31
It asking for your Ubuntu user password. 

Hum wired connection to your router - you should not have to do anything -  run 

```
ifconfig 
```

to see if you have a IP address.

If not run 

```
sudo dhclient 
```

that will ask your router to assign the PC an IP address. Thats assuming your router is set up to be a DHCP server - most are setup that way by default.

---

### Post by JC Cheloven on 2010-07-31
That dialog window asking for a password reminds me the security keys asked in wireless connections. Does the dialog says something about a security keyring? It shouldn't indeed, but if it's the case, try to simply ignore it (leave it blank).

---

### Post by Complete on 2010-08-01
> **joshedmonds said:**
> I'm not sure how you normally connect, but you say you have a router (+modem?) with a wired connection. If the connection to your ISP is established using information stored in the modem (the normal way a home connection is set up), the internet connection will happen whenever the modem is turned on, and the ethernet connection should be recognised automatically by Ubuntu (and the network icon in the top panel will change to 2 opposing vertical arrows.)

If you use some sort of dialer or connection manager then consider whether it would be easier to store those details in the modem instead.

Hope that helps.

EDIT: The apply button will apply any changes you make to those settings. The password is likely the Gnome-keyring password, although I am happy to be corrected on this. If you already see the wired connection, you should be able to open a browser and use the internet (or open a terminal and ping an ip)

I have a cable, as in a television cable, connection going to a cable modem.  From the cable moden there is a network (I guess it is called "ethernet") connection that goes to a router.  From there, I have several connections.  One connection goes to the computer I am using to communicate to you, one goes to an XBOX, and one goes to the older computer we are discussing.  The router also handles a wireless connection to a laptop.  
I recall that I was able to use an IP address in a broswer and bring up a page that represented a connection to the router and there were passwords to set up.  I also recall that I had to tell the laptop network software what the password is.  Since I do not remember this password, maybe I will have to reset the password on the router and tell the Ubuntu network software what this password is. 

==================================================

> **JC Cheloven said:**
> That dialog window asking for a password reminds me the security keys asked in wireless connections. Does the dialog says something about a security keyring? It shouldn't indeed, but if it's the case, try to simply ignore it (leave it blank).

It seems to be the password I used when I installed Ubuntu.  When I input that, it accepts it.

> **louieb said:**
> It asking for your Ubuntu user password. 

Hum wired connection to your router - you should not have to do anything -  run 

```
ifconfig 
```

to see if you have a IP address.




Here is what I got from running:

```
ifconfig 
```

(I have deleted the actual hex digits for security reasons)

```

dawn@dawn-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr {first set of six hex digits seperated by :}  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63808 (63.8 KB)  TX bytes:63808 (63.8 KB)

wlan0     Link encap:Ethernet  HWaddr {second set of six hex digits seperated by :}
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

does this look ok to you?

I am just guessing but I think I should somehow put this information into this dialog:
(I figured out how to do screen captures on the Ubuntu OS system)
[http://i67.photobucket.com/albums/h292/Athono/microsoft/UbuntuNetwork.jpg](http://i67.photobucket.com/albums/h292/Athono/microsoft/UbuntuNetwork.jpg)

---

### Post by TheNerdAL on 2010-08-01
With the memory you have, I would suggest using Lubuntu. :P

---

### Post by louieb on 2010-08-01
The 6 digits you removed is your network cards MAC address.

Looks like you don't have an IP - It would be listed after [B]Inet addr:

[/B]Also looks like the laptop has a wired and wireless card. (eth0 and wlan0). At least Ubuntu is seeing the network card(s). 

lo is the loop back - it looks normal - its used to let the machine talk to itself. don't not provide Internet access.  

Anyway do you have a network icon on the panel?  Does it show any wireless networks when you left click on it? 

Wonder if the wired card still works?

Try ```
sudo dhclient eth0
``` It will be pretty clear from the output if it worked or not.

---

### Post by Complete on 2010-08-01
> **louieb said:**
> The 6 digits you removed is your network cards MAC address.

Looks like you don't have an IP - It would be listed after [B]Inet addr:

[/B]Also looks like the laptop has a wired and wireless card. (eth0 and wlan0). At least Ubuntu is seeing the network card(s). 

lo is the loop back - it looks normal - its used to let the machine talk to itself. don't not provide Internet access.  

Anyway do you have a network icon on the panel?  Does it show any wireless networks when you left click on it? 

Wonder if the wired card still works?

Try ```
sudo dhclient eth0
``` It will pretty clear from the output if it worked or not.

louieb, I appreciate your sharing of your knowledge.  It has been a great help and I have learned a few things.

You would not believe how I was able to get the computer online.  The truth is stranger than fiction.    All this started when I moved into a new place.  The older computer is in another room and there is an network cable running from the router towards the room where the older comptuer is.  But the lengh of the cable was too short so I bough an extension from a store which I will not mention but its initals is R.S..

Before trying any more software suggestions I thought I would first disconnect the cable from the older computer and try it on my newer computer.  It did not work.  I disconnected the extension that I bought from the store which I will not mention but its initals is R.S. and tried the remaining cable.  It worked.  I looked into my storage and found a cable I had packed away before the move and I used that as a replacement extension and tried it on my newer computer.  It worked.  I ran this new cable configuration back to the Ubuntu computer and I rebooted.

I opened a command window and typed ifconfig.  This time I saw the network address you said was missing.  I hoped a firefox browser and I was able to get online.

:D:o:D:o:D:o:D:o

---

### Post by JC Cheloven on 2010-08-01
LOL, one can get mad trying to solve by software a hardware problem :D

> **JC Cheloven said:**
> That dialog window asking for a password reminds me the security keys asked in wireless connections (...)
BTW, that dialog was more than likely what I said. Doesn't matter though.

---

### Post by Complete on 2010-08-03
> **TheNerdAL said:**
> With the memory you have, I would suggest using Lubuntu. :P
I was wrong.
It is more like 245 megs.
Would you still recommend Lubuntu?

---

### Post by k3lt01 on 2010-08-03
Your memory is about the same as mine and I run 10.04 Ubuntu with a few tweaks. It runs fine but after you install it, and that will be a trial in patience in itself, you will need to do a little bit of work. I find it worthwhile but others may not.

---

### Post by JC Cheloven on 2010-08-06
> **Complete said:**
> I was wrong.
It is more like 245 megs.
Would you still recommend Lubuntu?

IMO you shoud try it out at least, so you can form your own opinion. I'd be dubious if asked for a "yes/not" kind of advice, but for sure Lubuntu is an option to consider in your case. 
All I can tell is that I succeded to do with Lubuntu everything I needed. For example [http://ubuntuforums.org/showthread.php?p=9659502#post9659502](http://ubuntuforums.org/showthread.php?p=9659502#post9659502)
although I prefer using regular ubuntu if the machine can, perhaps simply coz I'm used to it (& I like to use compiz though).

---

