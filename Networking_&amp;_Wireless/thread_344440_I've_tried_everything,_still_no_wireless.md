---
title: "I've tried everything, still no wireless"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by jaymz on 2007-01-22
First of all I'm terribly sorry to post yet another "no wireless" thread, I wish I could say any of the others were helpful...

I'm using Ubuntu Edgy

I've tried everything from NetworkManager to trying to configure it from the terminal...

The stupid thing is I can get perfect wireless in my university's campus, which I get from a VPN connection by just doing

```
sudo iwconfig eth0 essid e-UM

sudo dhclient eth0

sudo vpnc
```
But at home there is just NO WAY I can manage to get it...

I have an LG P1 Express Dual laptop, the drivers are propperly installed, I checked (I read the other threads)... I can connect to the network, I get a signal from it, I've got the correct DNS and IP (they work for windows and cable connection).

Help please, any information you need I'll be pleased to provide...

---

### Post by phossal on 2007-01-23
Your post doesn't make sense, which is probably why no one has offered to help you. You mention that you're able to get connected at the University, but not at home. Okay, so your hardware is installed correctly. Then you say 
> I can connect to the network, I get a signal from it, I've got the correct DNS and IP (they work for windows and cable connection). 
What does that mean? You *do* connect at home? What does Windows have to do with anything? You can connect to the network? Be patient, take your time, explain the situation thoroughly so we can help you.

---

### Post by jaymz on 2007-01-23
Perhaps I haven't been clear and I'm sorry.

I can connect at the university, no problem.

At home I get a signal with NetworkManager but when I try to connect the NetworkManager just refuses to work... 

Sorry if I didn't express myself properly.

I only mentioned Windows as comparison because the IP and DNS work there.

---

### Post by olejorgen on 2007-01-26
Are you sure you've got the correct dns adress? vpnc-connect removes the old dns adress here :-/

---

### Post by Caraibes on 2007-01-26
You might want to try Linux Mint, it is Ubuntu Edgy with all the goodies... it might work out of the box...

---

### Post by jaymz on 2007-01-28
I am sure I've got the correct DNS, I've replaced it.

I tried virtually every little piece of advice I could find and still nothing. And I think I screwed up by trying multiple advices.

Now my Network Manager reads "No network devices have been found", my /etc/hosts file is blank and I can't even get a wired connection...

This is probably the most frustrated I've ever felt when dealing with a computer. I just can't get it to work...

So I'd be most thankful if anyone could help me here... Ask away, I'll try to answer any questions you might have about my chaotic situation and please help...

---

### Post by featherking on 2007-01-28
you cannot use static ip's with NetworkManager, everything has to be controlled by NetworkManager in order for NetworkManager to work. This includes your wired connection. The first thing you need to do is pretty much start at the beginning.

i posted in [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2024518&postcount=4") thread a solution. Try the steps listed there and post back here..

EDIT: Put this in your /etc/hosts file

```
127.0.0.1 localhost <yourcomputername>
127.0.1.1 <yourcomputername>
```

---

### Post by jaymz on 2007-01-28
Thanks, that worked perfectly BUT I do have a static IP... 

So if you could please keep on assisting that would be excellent :(

---

### Post by featherking on 2007-01-29
well if you plan on using network manager you will have to use dhcp, thats what im saying. If you must use your static ip you will have to switch to something else, i have heard good things about [[COLOR="Red"]connection manager[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=299462") but i have never used it personally. But if you are able to switch to using dhcp then NetworkManager will work just fine

---

### Post by jaymz on 2007-01-29
OK, connection manager doesn't do static IP either.

So if you could please assist me in connecting to wireless without the help of any apps or if you could tell me how to switch to DHCP (HUAWEI ROUTER) that would be wonderful...

---

### Post by featherking on 2007-01-29
Well you need to set your router to give out address automatically (DHCP). Type your routers ip address into an internet browser. The address is should be what you have under default gateway in your network properties. So if it says Default Gateway=192.168.0.1 then you type that number into say, firefox.

This will bring up a username/password window, if you have never logged into this before the default **username/password** is **admin/admin**. Then you are looking at your router configuration pages. On the left there should be something that says home. 

Inside of that home container will be an entry that says "DHCP", click on this and look for anything that says "DHCP enabled". It might not be worded exactly that way, but the idea is to enable DHCP on your router for your home network. Once this is done save/apply your settings and then follow the steps to connect with NetworkManager that i posted in post #7. You should not have to use a static ip now to connect and so now NetworkManger should work for you?

Try all that and post your results

---

### Post by jaymz on 2007-01-29
Ok, did what you suggested, this is what it looks like ->

[IMG]http://img406.imageshack.us/img406/4932/imagemjx6.png[/IMG]


NetworkManager now connects okay, says "wireless network connection to '<my essid>' (96%)"

But still no show, can't get firefox to open any sites nor use "apt-get"

(one curious detail. On windows if I use the static IP I used to use it still connects but it doesn't work if I select DHCP... Is it not in DHCP??? I changed it...)

---

### Post by featherking on 2007-01-29
you probably have a DNS problem in ubuntu.

try to run this while connected to your wireless connection

```
ping -c 4 www.google.com
```

and post its output, then run this

```
ping -c 4 66.102.7.104
```

and post its output. Also open System > Admin > Networking - click on the DNS tab and take a screenshot of it (alt + PrintScreen) and post it.

Also on your windows box look something up for me. go to Start > All programs > Accessories > Communications > Network Connections. Once that opens up right click your wireless connection and hit properties. Then click TCP/IP and hit properties again. If you have this set up as a static IP you will see 5 lines with numbers on them. Post the last 2 lines under 'use these DNS servers'

we are almost there!

---

### Post by frick on 2007-01-29
Greetings,

I have found the wireless connection with Edgy to be very frustrating.  I agree the the network manager does not seem to do a great deal.

I used WIFI-Radar and things finally started working.  Here is the rub.  I still have not been able to get connected if any WEP or WPA has been turned on.  It will only connect if my security is off.

I have spent some time messing with the WEP/WPA patches but I have not gotten them working yet.

Try WIFI-Radar and see if that will work for you.

frick

---

### Post by jaymz on 2007-01-29
featherking ->

I know what a static IP looks like. In Windows I have to use it... I have to use the so said "five lines with numbers" for it to work. That's what bugs me. It's supposed to be using DHCP but it's not! If I set Windows to find the IP automatically the net just doesn't work which leads me to believe that I'm not using DHCP although what I'm told by the modem site is that I am...

Anyway... 

For the first command I get a lot of time waiting and then:

"ping: unknown host www.google.com"

and for the second

"PING 66.102.7.104 (66.102.7.104) 56 (84) bytes of data.

--- 66.102.7.104 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3005ms"

frick -> I just lost all internet access on ubuntu and going through all the dependencies with a pen is just too much for me right now, so I'll do that only as a last resource.... Thanks anyway :)

---

### Post by Rogmatic on 2007-01-29
Hello, I'm having the exact same problem.  It doesn't seem to make any sense, because my wireless worked perfectly right out of the box, then all of a sudden this evening I was reading some man pages for about an hour straight, tried to launch firefox, 'Problem loading page.'
I can connect to my network, DHCP works fine, but it seems like I'm having the same DNS problem as jaymz, based on the results of a ping to google vs a ping to 66.102.7.104.
The only DNS server entry in my config is 196.128.0.1 (my router), but I think that could just be cached.
Anyways, greatly appreciate all the help I can get; I've never been this frustrated with a computer before.  I just don't understand how all of a sudden it could have just stopped working without my intervention.

---

### Post by featherking on 2007-01-29
@Rogmatic (jaymz can try too if you want)

if you want to try something, you could log into your router and look for a status page for your outside ip address. Look for something like WAN status. On this page it should list your outside IP address (the one that doesnt start with 192.168.), somewhere around that ip address it should list your primary and secondary DNS servers. Write those numbers down and put them into your System > Admin > Networking - DNS tab. Erase whatever you already have there when you do this. then either restart or type

```
sudo killall NetworkManager
```

```
sudo /etc/init.d/networking restart
```

```
sudo NetworkManger
```

and see if you can browse the internet now?

---

### Post by Rogmatic on 2007-01-30
Tried that already, I even edited my /etc/dhcp3/dhclient.conf file to include my ISP DNS servers, but makes no difference.
I can't even ping within my local network, it claims that the 'remote host is unreachable'.
This is the most retarded nonsensical computer problem I have ever dealt with.

EDIT:  Fixed it, finally.  I had to have the DNS server addresses set locally AS WELL AS on my router.  What I still dont understand is how it worked -before- this setting was enabled, and then suddenly just up and quit.
In any case, thanks jaymz and featherking for pointing me in the right direction.

---

### Post by featherking on 2007-01-30
@Rogmatic - glad you got it working, it most definately looked like a DNS problem

@jaymz (if you still have trouble plz give this a shot, id like to think i wrote all this for something...)

Okay this is the only other solution i can think of. If you **must** have a static ip (which it seems for some reason you do) you can use wpa_supplicant and the built in gnome networking tool. I have written directions for a script that will connect you to your wpa access point. So whenever you need to connect to it simply right click your desktop > select scripts > and then click the script that we will create to connect to your access point

! Before you start !> Set your static ip in System > Admin > Networking for your wireless interface. (note* if anyone wants to use dhcp set your interface to use dhcp and simply run 'dhclient <wifi-interface>' after all the steps i list here)

Now type this in terminal:
(this installs wpa_supplicant)
```
sudo apt-get install wpa_supplicant
```

this opens a window with a blank wpa_supplicant file. Paste the next text into that window
```
sudo gedit /etc/wpa_supplicant.conf
```

replace the bold text with your network specific info then save and exit.
```
network={
ssid="**your wireless network name**"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
psk="**your wireless security code**"
}

```

Back in terminal type:
```
gedit /home/**<your user name>**/.gnome2/nautilus-scripts/wifi-connect.sh
```


That will open another gedit window paste this into that window:
replace the bold text with whatever your wireless interface is, then save and exit.(find out what interface is wireless by typing 'iwconfig' in the terminal)
```
gksudo "killall wpa_supplicant"
sudo wpa_supplicant -Dwext -B -w -i**eth1** -c /etc/wpa_supplicant.conf
sudo /etc/init.d/networking restart
```

Now close gedit and type this into the terminal:
again replace the bold with your user name.
```
chmod +x /home/**<your user name>**/.gnome2/nautilus-scripts/wifi-connect.sh
```
Go ahead and close the terminal now.

After all those steps simply right click any empty space on the desktop and go to Scripts > wifi-connect.sh to connect to your wpa protected access point with your static ip. If you ever wanted to connect to a hotspot somewhere you could simply edit your System > Admin > Networking and change from your static ip back to dhcp and input the ssid of the hotspot you want to connect to. Then to connect back at home change back to your static ip and right click the desktop and run your script etc. etc. rinse and repeat

---

### Post by jaymz on 2007-01-30
I don't have a network connection, so I can't apt-get anything... But I was under the impression I already had it, so I just skipped that step...

I did what you told until "Go ahead and close the terminal now."

From then on I couldn't understand a thing...

When I right click my desktop all I see is "Create Folder, Create Launcher, Create Document, Clean Up By Name, Keep Aligned, Paste and Change Desktop Background"...

Nothing about scripts.

But anyway, I've tried

```
./home/<my user name>/.gnome2/nautilus-scripts/wi-ficonnect.sh
```

and it failed.

Could you try and help me get DHCP??? I think that would be easier... I followed your instructions but for some reason it's not enabled...

---

### Post by featherking on 2007-01-30
The "Scripts" option ususally isnt in your right click menu until you actually add one script. Instead of typing ./home/<my user name>/.gnome2/nautilus-scripts/wi-ficonnect.sh try running ```
sh /home/<my user name>/.gnome2/nautilus-scripts/wi-ficonnect.sh
```
See if it will run in the terminal that way.. post your results [COLOR="DarkRed"](note* you should not be using NetworkManager at all when trying to connect this way* if you are - type 'sudo killall NetworkManger' and setup your static ip in System > Admin > Networking before running this script)[/COLOR]

If it still doesnt, browse to /home/<your user name>/.gnome2/nautilus-scripts/ and see if your script is there, post here if it is/is not

I agree the DHCP is far simpler to set up, but i suspect some things would have to change in how your router is setup for that to work. You said with your DHCP enabled that you werent able to browse the internet.. When you had DHCP on, did you ever try the steps i posted in [[COLOR="Red"]post number 17[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=2081616&postcount=17")?

---

### Post by jaymz on 2007-01-30
I got the exact same results
```

Line 6: WPA-PSK accepted for key management, but no PSK configured.
Line 6: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

```

I don't think you understand what I've said... The modem page reads that I do have DHCP but I don't! Neither Windows or Ubuntu can use it. Really weird...

Anyway I tried what you said in post 17 again to the very same result...

---

### Post by featherking on 2007-01-30
I would like to see your setup in your router, can you send me a screenshot of your DHCP page in your router? or point me to somewhere i can see each page in your router, maybe an online user guide or something? If both of your OS cant use DHCP something is probably messed up in your router.. what is the model number of it you said it was a huawei right?

Speaking of that 'connection manager' program again.. did you see this [[COLOR="Red"]screenshot[/COLOR]]("http://compwiz18.blackhole.cx/connection-manager/screenshot2.png")? It seems like that would be a perfect solution for your wireless, and you wouldnt have to touch your router..? This is a link to the [[COLOR="Red"]connection manager[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=299462") page again. Tell me, what happened when you tried it earlier?

EDIT: I have connection manager installed an running on my machine using a static ip and wpa.. I would say in your situation you ought to use connection-manager(renamed **wicd** now apparently) for your connection so you can use static ips. Normally i recommend networkmanager but its dhcp only.. I think the easiest way for you to be connected is to use that connection manager, i can help you setup your static ip in that if you want..

---

### Post by jaymz on 2007-01-30
I didn't manage to install it... I don't have any form of internet so I have to download the dependencies one by one from here (desktop) and I have come across some "Dependency is not satisfiable" error messages...

When I try to install the said dependencies that aren't satisfiable nothing happens... I double-click the package and nothing happens...

So long story short I couldn't install the connection-manager...

It's a Huawei MT800 and I've already posted the screenshot you asked for a few posts ago ;)

Unless it's not the one, if it isn't please say so...

---

### Post by featherking on 2007-01-31
Look through all the pages in your router and see if there are any other pages with DHCP or things that talk about your LAN. If so, post a screenshot of it. Maybe there is an option somewhere that is conflicting with the DHCP...

EDIT: Looking at this [[COLOR="Red"]page[/COLOR]]("http://img222.imageshack.us/my.php?image=huawei011ms.jpg"). what are your settings for 'Connection Type'? Also i notice that there is a 'Lan Config' page and a 'NAT' page, perhaps you could post a screenshot of these two. Also it looks like this router doesnt have built in wireless? Do you have another router hooked up to your huawei in order to provide wireless? because if you do they have to be configured a certain way in order for it to work, i found a tutorial [[COLOR="Red"]here[/COLOR]]("http://cookedmode.com/archives/4") if you want to look at it.

---

### Post by jaymz on 2007-02-04
Don't ask me how I did it, I DO NOT KNOW, but the truth is I'm getting DHCP now and as such I am connected :)

Thank you so much for all the time you have dedicated to this problem featherking ;) 

Much abliged

---

### Post by featherking on 2007-02-04
Great!

Wondered where you went for a few days, but glad its finally working. That dhcp really makes things easy. Congrats again..

-The King

---

