---
title: "Xbox 360 Internet Sharing"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by xnerdx on 2008-10-31
Hello, I have an aircard from Sprint, it is a USB connection device. I have it connected to my laptop and I have it configured in 8.10 through the Network Manager. I followed the directions in this thread:
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)
I have this set up completely and I when I run the xbox 360 xbox live test it gives me a wired status, confirms my ip, but fails on DNS. I have it connected to my laptop over an ethernet cable and then I have my modem (aircard) connected to the laptop. On the last step of the thread above I set it up to use dhcp3-server to broadcast the IP over the ethernet. Any ideas?

---

### Post by xnerdx on 2008-10-31
Oh also when I connect the ethernet cable to my computer, the computer will not let me access the internet anymore, although the network manager still says it is connected to my CMDA network (Aircard).

---

### Post by dmizer on 2008-11-01
Did you use a [crossover cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable) to connect between the Xbox and the Ubuntu computer?

---

### Post by xnerdx on 2008-11-01
Yes I have tried both a cross-over cable and a standered Ethernet.

---

### Post by dmizer on 2008-11-01
You have to set the DNS servers manually on the Xbox.

---

### Post by xnerdx on 2008-11-01
Are you sure? Hmmm... I will try it but for whatever reason before I remember backing out of the screen and found that it had them set correctly... I will try it

---

### Post by xnerdx on 2008-11-03
I used a cross over cable and I set the DNS to manual, still no luck.

---

### Post by mips on 2008-11-03
Use Firestarter. Do you really need dhcp when a static IP config will suffice?

[http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)





.

---

### Post by xnerdx on 2008-11-03
Okay here is my setup, I have the laptop with 8.10 connected to the xbox over ethernet. I have the modem connected to the laptop, if both of these are connected then there is no connection but if it is just the modem then I have a connection on the laptop. I have the xbox 360 running on Auto settings but have tried the manual DNS on it. I am so damn confused, I have Firestarter running but either way I still have no connection to the internet with a present ethernet connection on either the xbox or the laptop... Anyone have a fix?

---

### Post by mips on 2008-11-04
> **xnerdx said:**
> Okay here is my setup, I have the laptop with 8.10 connected to the xbox over ethernet. I have the modem connected to the laptop, if both of these are connected then there is no connection but if it is just the modem then I have a connection on the laptop. I have the xbox 360 running on Auto settings but have tried the manual DNS on it. I am so damn confused, I have Firestarter running but either way I still have no connection to the internet with a present ethernet connection on either the xbox or the laptop... Anyone have a fix?

Are you using Network Manager? If 'yes' then disable it as it only allows one connection at a time.

If you still have problems can you post your IP settings here so we can have a look.

---

### Post by xnerdx on 2008-11-07
Well at this point my ethernet connections doesn't work no matter what with anything (in network manager) also when I edit the network interfaces file, like the tutorial says, I can no longer load my network manager. When I try to load it up through terminal it tells me that the network manager setting files are already in use. Also, I have tried to stop network manager or right click and disable networking, and at that point firestarter tells me that ppp0 is not ready. So my question is how can I use my modem without network manager so I can load firestarter or even run ethernet connections through network manager....

---

### Post by dmizer on 2008-11-07
At this point, I would suggest ditching NetworkManager and Firestarter, and just configuring things via CLI.

Here's a howto for CLI ICS: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by xnerdx on 2008-11-08
Sorry I am still confused :)

---

### Post by dmizer on 2008-11-08
What are you confused about? Ask me questions and I can answer.

---

### Post by xnerdx on 2008-11-09
Okay what I want to do is revert my computer to what it should be at a fresh install of 8.10 due to the fact that a lot of things are screwed up at this point. Is there anyway to do this without the disk? As in is it possible to format the kernal and filesystem without have a disk? If not then I will just get my 8.04 disk and install it and then install KPPP with a flash drive to use my internet then from there I would upgrade to 8.10...

---

### Post by dmizer on 2008-11-09
That's going to be difficult to answer without knowing what you've tried.

What kind of things are "messed up"?

---

### Post by xnerdx on 2008-11-09
Sorry for not being as specific, its mainly my networking problems due to the fact that I no longer have any access to Ethernet and I require at least a network filesharing ethernet connection with my windows desktop also I do enjoy having internet on both. Also, for some reason firefox when I first open it has the window decoration? covered (the bar that says Mozilla Firefox and has the minimize close maximize bottons on it. To fix that I have to click view, go full screen then click the maximize button and it pulls the bar under my top panel where it should be, would you happen to know the cause of that? I think I may just format everything unless of course there is some way to do the format without accually formating the FileSystem :). Lol I just am still a tad-bit new to the whole linux aspect (working on that :)) Anyways, any ideas?

---

### Post by dmizer on 2008-11-09
Apparently, the theme you've chosen is not interfacing well with your system. That's why buttons don't work or can't be seen. You can fix this by changing the them settings.

For file sharing, you'll probably fix things simply by uninstalling Firestarter, as that is what's probably blocking your file sharing.

Once you've uninstalled firestarter, then you can follow the howto I linked to earlier.

---

### Post by f93mustanggt50 on 2009-10-05
Okay here is my setup to get on XBOX live through my Verizon Air Card.
I'm a long time windows guy just switching to Ubuntu.

The software I'm using:

Ubuntu 9.04
Latest Virtual box with XP guest

Hardware:
1 Verizon 3G air card
1 Standard (non crossover) Cat5e Ethernet cable


So because Virtualbox essentially is a software based router in some ways, it works great for what we are trying to do.

You will need your XP guest to have 2 network adapters on it.

Have NIC card number one bridge to host eth0, or eth1 etc. etc...

Have NIC card #2 NAT

Have Verizon (or other) air card inserted and tell Ubuntu to connect to your CDMA connection

Your Eth0 NIC card will be physically connected to the Xbox.

Your NAT recieves its IP info from Virtualbox and then gets Routed through Ubuntu and off to the internet

So what you do is from inside XP, go to your network connections and Bridge Connection 1 and 2. (highlight them both and right click, Bridge)

Now Turn on (or reset) your Xbox and it will recieve its IP info from Virtualbox. And you will notice if you look at the network config in the xbox that it has a Virtualbox IP address but the Air Cards DNS.

And voila! you can now get on Xbox Live!

(Pat yourself on the back....)

P.S.

You will recieve an MTU size error when doing a connection test....

I changed the MTU of my adapters on XP already but still recieve it. Oh well, I can still get on and play =)

^ I dont know if anyone else has done this yet... Maybe I'm the first? ;)

*Edit: 15 Min later*

Lagging isnt that noticeable on GTA 4 so far. 

Im now downloading a game demo and watching the Gnome System Monitor. Averaging about 300-350 kb a sec download...

Not to bad I guess lol

But damn this brings up another topic...You sure send a lot of data back across the connection..

For example:

170mb recieved and 165mb Sent

Interesting...

---

### Post by dmizer on 2009-10-05
> **f93mustanggt50 said:**
> Okay here is my setup to get on XBOX live through my Verizon Air Card.
I'm a long time windows guy just switching to Ubuntu.

The software I'm using:

Ubuntu 9.04
Latest Virtual box with XP guest

Hardware:
1 Verizon 3G air card
1 Standard (non crossover) Cat5e Ethernet cable


You're getting a lot of traffic because you essentially have 3 computers running through one network card: your host, your XP guest, and the X-box.

There's no need to go through all that effort and expend so much overhead in order to get ICS to work. Jaunty's Network-Manager supports internet connection sharing. It's a click and go process.

Right click on Network-Manager (in your notification area) and select "edit connection". Select the adapter you use to connect to the internet, select "edit" and enter your password. Then, click on the "ipv4 settings" tab and change "Method" to "shared to other computers"

That's it.

---

### Post by f93mustanggt50 on 2009-10-05
Well that doesnt work because the only options I am given are PPP Automatic and PPP address only.

Thats why I started on this whole little adventure in the beginning.

I am very aware of how to share an internet connection by using the network manager. But as far as tunneling a connection from the Verizon Air Card, I couldnt find an "easy" way. So if you come up with something better...Let me know.

---

### Post by ~Niebr~ on 2009-10-06
Im not having the same problem, i just cant seem to get a shared connection to work, i have my ipv4 method settings set shared to other computers

---

### Post by f93mustanggt50 on 2009-10-06
Whats your current setup?

---

### Post by ~Niebr~ on 2009-10-06
Im notsure what you mean

---

### Post by f93mustanggt50 on 2009-10-06
You said you cant share IPV4? So how are you trying to do it and what are you sharing to

---

### Post by f93mustanggt50 on 2009-10-21
OKAY so forget everything I ever posted on here! Im a complete idiot! Here is a working tutorial that is very very simple.

[http://ubuntuforums.org/showthread.php?t=74925]("http://ubuntuforums.org/showthread.php?t=74925")

---

### Post by jamiepgs on 2009-10-31
Though I'd update this thread, seeing as it still seems an area of confusion and it's something I just managed to get working. In 9.10, I was aiming to share my Internet Connection from wlan to my 360 via eithernet. I achieved this by using dmizers instructions, with a little change.

Right click on the Network notification icon and select "Edit Connections...," and select what method you're using to share (rather than what you use to connect, as suggested by dmizer). In my case, this was ethernet, so I selected Auto eth0, clicked edit and under ipv4 settings and put the method to 'Shared to other Computers.'

This may have been what dmizer meant and I could have read it wrong :p

---

