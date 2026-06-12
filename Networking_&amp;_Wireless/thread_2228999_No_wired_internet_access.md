---
title: "No wired internet access"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by 1249256chris on 2014-06-10
Hi, windows xp died on my moms old laptop so I saved it from the trash and put ubuntu on it, as I've been wanting to learn Linux. Its a dell latitude d610, with just Ubuntu 12.04, and it appears everything is working well (though a little slowly, could ubuntu be too much for it? the laptop is kinda old) except it can't connect to the internet, neither through wireless nor ethernet. Wireless it cant detect, but from looking at other solved posts I think I'll just need to run apt-get install to get the software I need and if that doesn't work I'll figure that out when I get there. Problem is, my ethernet doesn't work either. Or at least I think it doesn't. I dont have access to an ethernet port/router or anything, but I tried to hook it up to my new laptop (which gets wifi) after reading about how to do so, but it appears to not work.. I get a pop up when I connect the cable saying "connection established" but opening a website or running apt-get update doesn't work- it says there isn't any connection. What confuses me most is that if I ping [www.google.com]("http://www.google.com"), I get responses back, with a time of about 43ms.
Let me know what commands to run/what info to give so I can be helpful. I'm pretty new to linux but not to programming/computers in general so hopefully I'll be able to keep up. Running iwconfig gives me "lo" and "eth0", both of which say "no wireless extensions". I've looked into all the other posts I could find but all of the solutions that seemed applicable didnt work. 
Sorry thats a lot of text. Thanks a lot for any help.

---

### Post by Mar Komus on 2014-06-10
There's a lot to say here. First, the Dell Latitude D610 has an Intel Pentium M processor for its engine. It will therefore be *very* slow (especially if it has < 2GB of RAM). That said, it might be advisable to set your laptop up with Lubuntu instead. I've had a very successful time using that on a single core processor like the AMD Athlon 3200+. Even so, a pure 32-bit installation of Debian running with LXDE has also proved useful and will work just fine for your Linux learning experience. Ubuntu uses the Unity desktop environment which uses a *lot* of resources for video display (that you don't really need in this phase of your education).

That said, let's pretend that installing Lubuntu or Debian with LXDE doesn't solve the problem.

I follow your post right up to where you say, "I dont [*sic*] have access to an ethernet port/router or anything, but I tried to hook it up to my new laptop (which gets wifi) after reading about how to do so, but it appears not to work." At this point I'm not following. When you say you don't "have access to an Ethernet port/router or anything," I'm left wondering, "Then how did he hard wire his old laptop in the first place?" Second, I'm not clear on what you mean by "it" in "I tried to hook it up to my new laptop." Do you mean you tried to hook your mother's old laptop up to the new using the new as a proxy?

As for your iwconfig results: this means your adapter is not detected by the system. It should have come up with an entry for wlan0. So you might also run ifconfig and see if that brings up anything about wlan0. If not, then try the following command:
> ifconfig wlan0 up

Speaking of which, why not run ifconfig and copy/paste back the results? :)

---

### Post by Hadaka on 2014-06-10
hi, let's take a quick look at what drivers
you are suppose to have for your comm cards.
open a terminal..,ctrl/alt/t COPY and paste the following
commands
```
lspci -n |egrep '0200|0280' | awk '{print$3}'
 lsmod | grep mac80211 | awk '{print$4}'
```
post the output
thanks

---

### Post by 1249256chris on 2014-06-10
--> Mar Komas
Sorry, I was pretty unclear. The apartment I'm in now just has wifi, so I'm connected to the internet on my new laptop through that. I plugged one end of a new ethernet cable into the port on my new laptop, and the other end into the old one. I changed the settings of my new laptop to allow other computers to access the internet through it. Here's the results of ifconfig:

james@james-Latitude-D610:~$ ifconfig


eth0      Link encap:Ethernet  HWaddr 00:12:3f:1c:d4:33
          inet addr:192.168.137.176  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe1c:d433/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000

          RX bytes:305984 (305.9 KB)  TX bytes:163463 (163.4 KB)
          Interrupt:16 


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:63719 (63.7 KB)  TX bytes:63719 (63.7 KB)



And thanks, thats good to know. I'll try installing Lubuntu.

--> Hadaka
So copy/pasting it in, the first line gave the result "14e4:1677" which I guess makes the ethernet card the "broadcom netXtreme BCM5751".
But was the second line supposed to print something?.. I copied it just as it was, but no output.

Thanks for helping:)

---

### Post by 1249256chris on 2014-06-10
K so I put on Lubuntu and everythings the same, aside from the packet sizes mentioned in the ifconfig data. It is going noticeably faster though:)

---

### Post by Hadaka on 2014-06-10
Hi, the first line should have given you the pci-id of the ethernet
and the wifi card,,,you only posted one,,,
the second line should have posted something if you had some
kind of wireless driver loaded...in lsmod. so please re-run the
first command and see if there is a change,,,not plugged into
another computer,,or even plugged in at all
thanks,

---

### Post by Mar Komus on 2014-06-10
Glad to read that Lubuntu is working more efficiently for you! Now let's see if we can tackle this wireless card problem.

One thing we might do--just to eliminate the sometimes overlooked obvious: I'm concerned your wireless NIC didn't show up in *ifconfig*. This could be due to what Hadaka is hinting at: a missing driver, which is a good probability. But...let's just make sure: the Dell Latitude D610 utilizes the key combination <Fn> + <F2> to toggle the on/off switch of the wireless signal. Perhaps try toggling it--just once--and see if it turns on a switch that might have defaulted off.

---

### Post by 1249256chris on 2014-06-11
Ok, used the key combo but there was no change, and I re-ran the two commands while the computer wasn't plugged into anything and got the same result as last time- just the one thing (14e4:1677) for the first command, and nothing for the second.
Thanks

---

### Post by Hadaka on 2014-06-11
Hi , it looks like your wireless card is not there,
it may need reseating or replaceing. If possible
remove and reseat the card,,,issue that same command
if you still only get one line of data...then your card is bad
or you have other issues.
good luck

---

### Post by 1249256chris on 2014-06-11
Ok.. but is ethernet fixable though? ethernet was what I was hoping to fix..
thanks for helping though

---

### Post by Mar Komus on 2014-06-11
That should be fixable enough. Where is the tutorial you followed for connecting your laptops and bridging the Internet connection?

---

### Post by 1249256chris on 2014-06-11
I used the last section of this 
[http://www.labnol.org/software/connect-computers-without-router/11049/](http://www.labnol.org/software/connect-computers-without-router/11049/) for the windows one (my new laptop, its windows 8.1)

 and I used the third answer to this question 
[http://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet](http://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet)
for the old laptop when I had ubuntu, but now that I installed lubuntu I haven't redone it because I'm not sure if it was the right thing to do.
So right now on Lubuntu the network settings for "Connection 1" are just set to "automatic".
Thanks, I'm sorry that I don't really understand much..

---

### Post by Mar Komus on 2014-06-11
Ok...there's an easier way :) I did just about exactly what you did, but with Windows 7 on my laptop and my office PC (running...TAH-DAH...Lubuntu :) ). So here you go, but you'll have to translate this for Windows 8 as I don't have that. But I'm confident you'll get it.

First thing, set up a bridge on your new laptop running Windows 8 (*host* from here). To do that, you'll need to find your Network Connections page. Once you find that, you'll see that you have at least two adapters: a Local Area Connection (Ethernet) and Wireless Network Connection. To start off, unplug the crossover cable (and shut down the laptop with Lubuntu; *client* from here). This should make it so that your Wireless Network Connection is "Enabled, Connected" and the Local Area Connection should be unplugged (red "x"). Now draw a box around the two so they're highlighted. Right-click on either one. Choose "Bridge connections." Once that happens, you should see a new Network Connection called, "Network Bridge."

Next, go ahead and plug your crossover cable into the Ethernet port of both computers. Now power on the client.

Let me know how that works for you. As for me, I posted this over that very network bridge. And I've never done that before :) So I learned something new :)

Note: the reason I have you shut down the client is because Lubuntu isn't so excited to simply automatically connect. There's *probably* a command for that. I'll look it up when I'm less lazy.

---

### Post by 1249256chris on 2014-06-11
Thanks:)
but so ok so the bridge part worked fine on the win8 host but still no internet on the lubuntu-side.. and pinging google no longer gets a response.

Crap. I just realized my ethernet cable is just a regular one, not a crossover. 
So I guess I'll be taking a trip to the store tomorrow, I'll retry your solution once I have the proper stuff:)
Thanks again

---

### Post by Mar Komus on 2014-06-11
I was beginning to wonder if you had a crossover cable ;) I can pretty much guarantee it will work after that. :)

---

### Post by 1249256chris on 2014-06-15
Hey, it took me longer than I thought it would to get a crossover cable, but it isnt working as far as I can tell.. Both ends are plugged in, the bridge you had me make is enabled, but pinging google still gives the unknown host error. apt-get update/ going on internet dont work either. But whats weird is when I disconnect the cable, I get a pop-up message in Lubuntu informing me that I have disconnected an ethernet cable and am now offline. Any ideas? 
Thank you for helping

---

### Post by 1249256chris on 2014-06-15
ok so looking more, ifconig still only returns eth0 and lo, but in eth0, there is part of a line that says "UP BROADCAST RUNNING MULTICAST" when the cable is plugged in and the bridge connection is disabled, but only says "UP BROADCAST MULTICAST" when the cable is either unplugged or the bridge is enabled.
I have no idea if this helps or not
Thanks

---

### Post by 1249256chris on 2014-06-17
Well.. It looks like it was my windows laptop that was the problem, though with it being windows 8.1 there's not too much surprise there:p I found a router I can use and plugged in my Lubuntu laptop and it works gorgeously. But while I was looking for a router I had been looking into the wireless issue, and I had a thought and looked up where the wireless card plugs into on a dell d610, and I found a card in my laptop labelled MODEM on one side and ASKEY CONEXANT RD02-D110 on the other.

I found that dell actually has an ubuntu (an older version of Ubuntu though, 7.04) driver for that card, so I downloaded that and used dpkg and got errors, googled them when necessary (most just required an apt-get install), fixed them and got different errors, googled them, installed stuff, fixed them, rinse and repeat:P 
So now it looks like I could make this card work and I probably will but it appears the card uses dial-up, so I might just take a tour of ebay and look for something that won't get outrun by a turtle.

Thanks for your help, its cool using an OS that actually works and gives helpful advice. I'm so used to "Unable to connect to network, starting network troubleshooter-->unable to detect any problems (really, does windows troubleshooter ever do anything besides display that end message?)", that its mind-blowing to see "package something requires such-and-such, install such-and-such first using sudo apt-get install such-and-such", and have it work:P


EDIT:
I found that that dial-up has a different function than a wireless card and is not simply an old version of it, and that the computer actually doesn't have a wireless card.

---

### Post by christopherbalz on 2014-08-02
In my case I solved a problem where I had no wired ethernet (but wireless worked).  I tried `sudo dhclient` and that did not fix the issue, at least right away.  Next, I rebooted and toggled the 'Enable Onboard LAN' setting from the BIOS. Then wired ethernet worked again for me.

Note that to get into the BIOS, you'll need to press F2 or F10 or your system's specified key, and then in once in the BIOS you'll need to find the 'Onboard LAN' setting.

---

