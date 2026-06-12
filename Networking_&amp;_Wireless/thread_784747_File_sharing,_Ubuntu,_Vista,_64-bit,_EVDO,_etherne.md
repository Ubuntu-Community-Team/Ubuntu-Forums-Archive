---
title: "File sharing, Ubuntu, Vista, 64-bit, EVDO, ethernet..."
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by KillaKurt on 2008-05-06
My goal:  Share files between Ubuntu PC and a Windows Vista PC with JUST an ethernet cable attached directly between the two.  I want to do this without having to buy a router or anything!!

Ubuntu PC Info:
  OS: Ubuntu 8.04 Hardy Heron 64-bit
  I get internet via a Verizon USB720 evdo modem, it's working great.

Windows Vista PC Info:
  OS: Windows Vista Ultimate 64-bit
  No internet connection (Verizon USB720 is my only option at the moment).

Other possibly useful info:
  -  "System>Administration>Network" does not recognize my internet
     connection at all, because it is evdo and had to be set up manually.
  -  "Samba" doesn't seem to help but I may be doing things wrong anyway.
  -  On the Vista PC, the networking icon in the system tray has a yellow 
     exclamation mark on it.  It recognizes that I have the ethernet cable 
     connected.  It says "unidentified network" when I open the network and 
     sharing center, but when I right-click the icon and go to "status" it
     shows that it is connected at a speed of 1.0Gbps.
  =  On the Ubuntu PC, when I go to "Places>Network" there is an icon 
     called "Windows Network".  I don't know if this has any significance.
  -  Entering "ifconfig" into terminal gives me the following output:
         ```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:782072 (763.7 KB)  TX bytes:782072 (763.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XX.XXX.XX.XXX  P-t-P:XX.XXX.XX.X  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:13177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:14902281 (14.2 MB)  TX bytes:971226 (948.4 KB)

```

I put X's in "inet addr" and "p-t-p" because I don't know if giving out that information could do me any harm.  As you might already be able to tell, my experience with networking is like this: none.

This Verizon evdo connection is the only internet I've had other than dial-up AOL (mom still uses it here in the house, that's why I don't have AT&T or Comcast...).

I do have dvd burners and external hard drives and thumbdrives.  But I'd rather be able to just drag and drop a file into a sharefolder.  The way my desk is set up (all cables running behind it, including cables of the externals) makes disconnecting and connecting the external hard drives a big stupid task all in itself, or else I would do that.

I'm not just doing this to move my files now.  If that were the only reason I was doing this I would've just given up by now.  But now I want to learn how to do this just for the knowledge of it, and to feel that I accomplished something that is quite a challenge for me so far.  Please help!  Thank you in advance!

PS a step-by-step of what I'd have to do from start to finish would be amazing...I really have no idea where I'm supposed to start or anything.  I've never even done windows to windows file sharing before!!!

---

### Post by ephro on 2008-05-06
To not get too deep into networking mumbo jumbo, what you need to do is connect the two computers using a 'crossover cable'. 

Quick lesson:

Ethernet cables have 8 wires in them, but in most cases (and cases that you care about), only 4 of them are used, transmit positive (Tx+), transmit negative (Tx-), receive positive (Rx+), and receive negative (Rx-). When you run a regular ethernet cable between two computers they are both trying to send on the transmit and listen on the recieve (see the problem?). It's like having a 4 lane road but all the traffic is driving at eachother on the same 2 lanes.

Luckily there is a easy solution if you don't want to buy a router or hub or switch.

With pictures you can see here:

[http://www.duxcw.com/digest/Howto/network/cable/cable5.htm](http://www.duxcw.com/digest/Howto/network/cable/cable5.htm)

All the sites you are going to Google are going to tell you to go buy a cable crimpers, wire, ethernet ends, etc. However in a pinch you can DIY with out any of that need if you are willing to sacrifice a regular ethernet cable.

**Hacky Solution**

[LIST=1]
[*]Cut your ethernet cable in half in the middle of the wire
[*]Strip back the casing on each end about 6 inches
[*]Strip back the insulation on the following wire colors
[LIST=1]
[*]Green
[*]Green/White
[*]Orange
[*]Orange/White
[/LIST]
 
[*]Now put the two different ends point away from eachother so we have a right side and a left side
[*]Now we are going to twist some ends together like so:
[LIST=1]
[*]Left Green to Right Orange
[*]Left Green/White to Left Orange/White
[*]Left Orange to Right Green
[*]Left Orange/White to Left Green/White
[/LIST]
 
[*]Wrap all the ends in a little tape and make sure none of them are touching
[/LIST]
The less you untwist and of the wires the better (high speed) your connection is going to be, however I have found it doesn't matter much if the cable is under 20 feet long.

Now plug the two computers into the new wire you just made. On the linux computer set up your network like this:

IP Address: 10.0.0.10
Subnet: 255.0.0.0
Gateway (unnessisary, but set it to 10.0.0.1)

On the vista computer set it up like this:

IP Address: 10.0.0.11
Subnet: 255.0.0.0
Gateway: Same as above

Now all you have to do is open up Nautalis (your file browser in Ubuntu) and browse to 'smb://10.0.0.11/'

You should be able to move files to your hearts content.


Hope this helps, let me know how it goes.

---

### Post by KillaKurt on 2008-05-06
Hmmm.  Seeing as how this seems rather easy after the modding of the cable...I might just go buy a crossover cable.

I guess my next question would be...how do I set up a network in ubuntu like that?

And...how do I setup the network in Windows?  I'm sorry but I'm entirely new to networking I have no experience whatsoever with it except just connecting to my Verizon modem! :(

Also, the way you told me to set this up...would I be able to move files from the windows pc to the ubuntu pc as well?  Are the files going to have to be moved through the terminal?

---

### Post by KillaKurt on 2008-05-06
> **KillaKurt said:**
> Are the files going to have to be moved through the terminal?

Nevermind, you said use Nautilus lol.

---

### Post by ephro on 2008-05-06
> **KillaKurt said:**
> Hmmm.  Seeing as how this seems rather easy after the modding of the cable...I might just go buy a crossover cable.

I guess my next question would be...how do I set up a network in ubuntu like that?

And...how do I setup the network in Windows?  I'm sorry but I'm entirely new to networking I have no experience whatsoever with it except just connecting to my Verizon modem! :(

Also, the way you told me to set this up...would I be able to move files from the windows pc to the ubuntu pc as well?  Are the files going to have to be moved through the terminal?

Buying a cable is a good solution too, just depends on if you want to spend any money. They also make crossover dongles like this:

[http://www.cables4computer.com/ProductSearch/ProductPages/TST-LOOP-004.html](http://www.cables4computer.com/ProductSearch/ProductPages/TST-LOOP-004.html)

If you set up your ethernet connection like I said in my first post then you will be all set. You can also get really fancy and share the EVDO connection back to windows if you wanted to, but lets go one step at a time. (You would set up the linux box to have NAT if you want to do some Googling.)

You won't have to use the command line at all, your normal file explorer in Ubuntu will work fine, and if you install the samba-server package you will be able to browse your Ubuntu machine in windows using explorer.

---

### Post by ephro on 2008-05-06
> **KillaKurt said:**
> Hmmm.  Seeing as how this seems rather easy after the modding of the cable...I might just go buy a crossover cable.

I guess my next question would be...how do I set up a network in ubuntu like that?

And...how do I setup the network in Windows?  I'm sorry but I'm entirely new to networking I have no experience whatsoever with it except just connecting to my Verizon modem! :(

Also, the way you told me to set this up...would I be able to move files from the windows pc to the ubuntu pc as well?  Are the files going to have to be moved through the terminal?


Sorry, should have been more specific with the setting up the network. (This is *only* from memory and not with Vista since I have never used it.) You will go to Network Connections then open the LAN Connection properties. In there you will see a line item called TCP/IP, which is what you want to edit. There will be boxes named very similar to my original post and if you put in those values everything should work fine.

---

