---
title: "Setting up Linksys WRT54GL to work under 8.04... Help!"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by norfair on 2008-05-09
EDIT:
Initial issue solved, but a new issue has developed. Please see my latest post on page 3. Thanks!

-----

I have a new Linksys WRT54GL router that I am trying to get working on my built-for-Ubuntu Shuttle box and am have a terribly difficult time. I have connected my router to my computer and my cable modem to my router. Each device has the appropriate lights flashing, but when I try entering in the router's address in Opera I get an error message, as if not connected. What could I be doing wrong?

My only reason for setting up a wireless router is to go online with my DS and Wii (which is how I'm typing this message - my Wii was able get online without a hitch). I don't know what is going on with my computer.

Any and all responses would be appreciated. Thanks.

---

### Post by aamukahvi on 2008-05-09
I have this same problem. I can't get to the admin interface. I've tried resetting the router to defaults (hold down the button in the back) but I can't get to it. Traffic still flows through it.

---

### Post by Go_Bucks on 2008-05-09
Are you using [http://192.168.1.1?](http://192.168.1.1?)

The operating system should have nothing to do with communicating with your router. If your router works and you have a connection between your computer and router and you have a working web browser, you should be able to connect to the admin interface.

---

### Post by Hellweek on 2008-05-09
The WRT54G router comes with a default address of 192.168.1.1

If your network is not 192.168.1.X you will not be able to connect.

Set your IP address of the Linux box to something in the 192.168.1.X (Just not .1) then try and connect to you Router.

---

### Post by norfair on 2008-05-09
> **Go_Bucks said:**
> Are you using [http://192.168.1.1?](http://192.168.1.1?)

The operating system should have nothing to do with communicating with your router. If your router works and you have a connection between your computer and router and you have a working web browser, you should be able to connect to the admin interface.

Thanks for responding. Yes, that's the address I've entered - using Opera and trying it in Firefox. It keeps coming back with &#8220;failed to connect.&#8221; Also, nothing new popped up under my &#8220;connections&#8221; within &#8220;network settings.&#8221; I would think a wireless option would pop up or something. I don't know.

---

### Post by Go_Bucks on 2008-05-09
Are you getting internet?

---

### Post by norfair on 2008-05-09
> **Hellweek said:**
> The WRT54G router comes with a default address of 192.168.1.1

If your network is not 192.168.1.X you will not be able to connect.

Set your IP address of the Linux box to something in the 192.168.1.X (Just not .1) then try and connect to you Router.

Uh... I have no idea how to do that. I know, I'm Linux newbie. Would you mind elaborating?

Though, I think the address should work, as I was able to access D-link's setup interface when I attempted to get that router to work. I bought this Linksys router assuming it'd a snap to setup under Linux. Hahaha... WRONG! Oh well.

---

### Post by Hellweek on 2008-05-09
> **norfair said:**
> Thanks for responding. Yes, that's the address I've entered - using Opera and trying it in Firefox. It keeps coming back with &#8220;failed to connect.&#8221; Also, nothing new popped up under my &#8220;connections&#8221; within &#8220;network settings.&#8221; I would think a wireless option would pop up or something. I don't know.


First lets be clear.  The computer is hardwired to the router correct?

Next in networkconfig do you have a entehrnet connection?

I dont remember if the Linksys comes with DHCP configured out of the box.  

You might need to set a static IP address in networkconfig.

Try setting a static IP address listing your router as the gateway.

---

### Post by Go_Bucks on 2008-05-09
The router has its own operating system and sets up the same way whether you are using Windows, Linux or Mac.

Regarding the IP address, if you do not know how to set your computer's specific address, then you can ignore that post, because your computer would not be "stealing" your router's ip unless you had told it to do so previously. By default, your computer accepts DHCP IP assignments from your router, and your router should be doing DHCP assignments by default as well.

---

### Post by norfair on 2008-05-09
> **Go_Bucks said:**
> Are you getting internet?

Well, not via my PC currently as the internet connection is being fed to my router. I am online on my Wii - for some reason it works fine (with occasional drops).

---

### Post by Hellweek on 2008-05-09
> **norfair said:**
> Well, not via my PC currently as the internet connection is being fed to my router. I am online on my Wii - for some reason it works fine (with occasional drops).

Hmmm Very odd.

---

### Post by Go_Bucks on 2008-05-09
> **norfair said:**
> Well, not via my PC currently as the internet connection is being fed to my router. I am online on my Wii - for some reason it works fine (with occasional drops).

Then the issue is not your router. Your computer is not communicating with the router, period. The issue is either with your ethernet hardware in your computer or with the configuration of the network manager in ubuntu.

---

### Post by aamukahvi on 2008-05-09
> **Go_Bucks said:**
> Are you using [http://192.168.1.1?](http://192.168.1.1?)

The operating system should have nothing to do with communicating with your router. If your router works and you have a connection between your computer and router and you have a working web browser, you should be able to connect to the admin interface.

Yeah 192.168.1.1, I don't know what happened but somewhere along the line the web admin page died, that is, I can't get to it anymore. Used to work fine.

---

### Post by norfair on 2008-05-09
> **Hellweek said:**
> First lets be clear.  The computer is hardwired to the router correct?

Next in networkconfig do you have a entehrnet connection?

I dont remember if the Linksys comes with DHCP configured out of the box.  

You might need to set a static IP address in networkconfig.

Try setting a static IP address listing your router as the gateway.

Yes, my whole setup is wired. The only thing wireless about it is my Wii. By &#8220;networkconfig&#8221; do you mean my &#8220;network settings?&#8221; The only two things I have there are, wired connection and point to point. 

Also, I do believe the router is dhcp ready, so to speak.

---

### Post by Go_Bucks on 2008-05-09
> **aamukahvi said:**
> Yeah 192.168.1.1, I don't know what happened but somewhere along the line the web admin page died, that is, I can't get to it anymore. Used to work fine.

Do you have No Script installed in Firefox? If that is running, I don't think you can access the admin page.

---

### Post by Go_Bucks on 2008-05-09
> **norfair said:**
> Yes, my whole setup is wired. The only thing wireless about it is my Wii. By “networkconfig” do you mean my “network settings?” The only two things I have there are, wired connection and point to point. 

Also, I do believe the router is dhcp ready, so to speak.

The router is dhcp ready. I still believe the issue is with the network hardware or software on your computer.

---

### Post by norfair on 2008-05-09
> **Go_Bucks said:**
> Then the issue is not your router. Your computer is not communicating with the router, period. The issue is either with your ethernet hardware in your computer or with the configuration of the network manager in ubuntu.

Not to sound blunt, but you don't by chance know how I could determine the true cause of my system's communication issues do you?

EDIT:
On second thought, I think my system might be okay. When I tried setting up my network of sorts with my used D-link router, I was able to access the router's  IP address. I just couldn't get past the login screen (the default username wouldn't work). I don't know why this new router isn't working out.

---

### Post by Go_Bucks on 2008-05-09
I am usually pretty good at figuring those things out if I am in front of the computer, but in this fashion, not so much. Wish I could help more... perhaps someone with more expertise on the network manager will pop on here.

---

### Post by kevdog on 2008-05-09
Clarifications for everyone here:

1. How are you connected to the router (wired or wirelessly)?
2. Post ifconfig
3. Post iwlist scan

This should clear a few things up.

---

### Post by Go_Bucks on 2008-05-09
> **kevdog said:**
> Clarifications for everyone here:

1. How are you connected to the router (wired or wirelessly)?
2. Post ifconfig
3. Post iwlist scan

This should clear a few things up.

This kind of response is what I was alluding to in my last post.

---

### Post by norfair on 2008-05-09
> **kevdog said:**
> Clarifications for everyone here:

1. How are you connected to the router (wired or wirelessly)?
2. Post ifconfig
3. Post iwlist scan

This should clear a few things up.

I am connected to the router and modem in a wired way. And while I'd happily post my ifconfig, my only means of internet is my Wii. So, I guess you all can give up on me for now. Thanks anyway.

---

### Post by norfair on 2008-05-09
> **Go_Bucks said:**
> I am usually pretty good at figuring those things out if I am in front of the computer, but in this fashion, not so much. Wish I could help more... perhaps someone with more expertise on the network manager will pop on here.

I understand. Thanks anyway, and for your assistance.

---

### Post by kevdog on 2008-05-09
??

Ok -- sorry about the questions. Get back when you have a chance.  Where did the Wii come from?  I must have missed that part in the earlier posts.

---

### Post by norfair on 2008-05-09
Uh? Okay! Just for fun I typed in: sudo ifup eth0, and voila! My internet is up and running on my PC. But, why? Shouldn't I have to enter something into my router's setup menu? Where do I go to configure security settings? Do I still try and access the router's IP addess even though I'm up and running? And why are the only two things in my "Network Settings" "Connections" field still "Wired" and "Point to Point?" Shouldn't there be a "Wireless" option or something?

Ah! So many questions. Can anyone shed some light on this for me? Sorry to be such a pest.

(Oh, and on a side note... It's so much nicer being able to type using a keyboard than using a Wii remote!)

---

### Post by kevdog on 2008-05-09
A wired connection never has security settings. WPA, WEP etc are only for wireless connections.  Do you have a wireless card?

---

### Post by norfair on 2008-05-09
> **kevdog said:**
> A wired connection never has security settings. WPA, WEP etc are only for wireless connections.  Do you have a wireless card?

No, no wireless card. I have one computer (desktop) connected in a wired way to the router and cable modem. My Wii and DS are the only things that'll be accessing the internet wirelessly. But can't those nearby access my connection via my router? This is my first time ever using a router, so you'll have to excuse my ignorance on the matter. I've always heard of people mooching off the connection of others, but perhaps this only applies if your router isn't directly connected to a PC.

---

### Post by Go_Bucks on 2008-05-09
OK... so it looks like you are trying to set up wireless security for your wii. There is not, however, a wireless option in network manager because your computer can not connect wirelessly... you don't have a wireless card. So now that you have established internet, go to [http://192.168.1.1](http://192.168.1.1) and set up wep or wpa encryption on your router. As far as setting up devices such as your wii to use the encrypted signal, that is between you, your wii, and the wii instruction manual.

Setting that up will not affect the wired connection to your computer.

---

### Post by norfair on 2008-05-09
> **Go_Bucks said:**
> OK... so it looks like you are trying to set up wireless security for your wii. There is not, however, a wireless option in network manager because your computer can not connect wirelessly... you don't have a wireless card. So now that you have established internet, go to [http://192.168.1.1](http://192.168.1.1) and set up wep or wpa encryption on your router. As far as setting up devices such as your wii to use the encrypted signal, that is between you, your wii, and the wii instruction manual.

Setting that up will not affect the wired connection to your computer.

Ah, very good. That makes sense. Thanks a bunch for clarifying and sticking with me through all of this.

---

### Post by Go_Bucks on 2008-05-09
No problem. Most of the time I am the one asking for help. It is nice to be able to return the favor once in a while, or at least try to.

---

### Post by norfair on 2008-05-11
Well, so much for being issue free. 

For some reason every time I turn my computer off and then back on to use it again, my internet connection doesn't work. I have to enter the command: sudo ifup eth0, and then it's back up and running issue free. That's how I got it to work originally after I set up my router, but I didn't think I'd have to do this each time. 

Anyway, I copied the info below that the terminal gives me after entering the command in hopes that someone here might know how I can fix this. It seems perhaps it might have something to do with my firewall, Firestarter, as it stops and then starts it. 

-----

Here is the info given after I enter the command:

*****@ubuntu:~$ sudo ifup eth0
[sudo] password for *****: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:1b:46:b3:e6
Sending on   LPF/eth0/00:30:1b:46:b3:e6
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 39581 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
*****@ubuntu:~$ 

-----

Thanks in advance for anyone that might be able to help.

---

### Post by .rdg on 2008-05-11
Most likely your ethernet card is not set up to be brought "up" on system start. Check the file: /etc/network/interfaces if there's a line:

auto eth0

or something similar. If not - just add eth0 to the line which starts with auto and it should be fine.

---

### Post by Go_Bucks on 2008-05-11
I could be wrong, but from that output it looks like your computer is requesting a specific ip address from the router (ending in .102). If you don't need a fixed ip for that computer, check your network manager. Click on "unlock". Put in your password. Select "wired connection" and click the "properties" button. Select "roaming mode". If this wasn't selected already, this will allow your computer to accept whatever ip address your router assigns to it.

---

### Post by norfair on 2008-05-11
> **.rdg said:**
> Most likely your ethernet card is not set up to be brought "up" on system start. Check the file: /etc/network/interfaces if there's a line:

auto eth0

or something similar. If not - just add eth0 to the line which starts with auto and it should be fine.

Thanks for the quick reply. I found the file, but am not sure about if I should modify it or where I should add auto eth0. Would you mind taking a look at the file and recommending where to place it?

-----

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface








iface eth0 inet dhcp

-----

Thanks.

---

### Post by norfair on 2008-05-11
> **Go_Bucks said:**
> I could be wrong, but from that output it looks like your computer is requesting a specific ip address from the router (ending in .102). If you don't need a fixed ip for that computer, check your network manager. Click on "unlock". Put in your password. Select "wired connection" and click the "properties" button. Select "roaming mode". If this wasn't selected already, this will allow your computer to accept whatever ip address your router assigns to it.

Hmm... I do remember seeing "roaming mode" when I first cofigured my internet connection, but dimissed it as I didn't have a router then. I've left it as "Automatic Configuration DHCP" as I thought that's what I needed given my cable modem and the like. Perhaps that will do it. I'll try it, thanks again.

---

### Post by .rdg on 2008-05-11
Instead of:

auto lo

Make it look like:

auto lo eth0

So both eth0 and lo interfaces will start on system boot. That should fix your problem.

---

### Post by norfair on 2008-05-11
> **.rdg said:**
> Instead of:

auto lo

Make it look like:

auto lo eth0

So both eth0 and lo interfaces will start on system boot. That should fix your problem.

I'll try that. Thanks for your help!

---

