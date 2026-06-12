---
title: "No Internet Connection (New to Ubuntu)"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Pidgin English on 2007-02-23
*(In advance, please excuse me for my total lack of experience with Ubuntu.)*

I recently made the switch to the Ubuntu 6.10 (Edgy Eft), and I'm having issues setting up my internet connection. I have a westell DSL modem [courtesy of Verizon DSL], and a Linksys Cable/DSL Router. Prior to my change from Microsoft OS to ubuntu, I had both of my computers running smoothly and the internet was stable, and when I switched over to ubuntu, the internet on the converted desktop did not work [I'm using the other desktop to write this post]. Can anyone run me through some troubleshooting methods and perhaps help me just get this connection flowing?

I followed the instructions under "Help", but those are unfortunately basic.

Oh, and the DNS server adress is not specific. My windows just searches for it every time.

Any advice would be greatly appreciated! I want to familiarize myself with this new OS, but right now I am incredibly lost.

:confused:

---

### Post by JJNam on 2007-02-23
I'm in the same boat (new, etc...).  Though I have figured out how to enable internet access through Firefox.  

I'm installed on ~5 year old Intel hardware w/built in NIC and I had to disable IPv6 in Firefox to get it running.  This may not be true for you, but it doesn't hurt to try.

From Firefox, type "about:config" and search for ipv6.  Set it to disabled.


I still can't get the software updates to work or add/remove programs to update though. :(

---

### Post by Pidgin English on 2007-02-24
Wow, that's infuriating! There must be some better explaination.:mad: 

I downloaded the OS hoping that things would just work. This networking problem is really killing me. :(

---

### Post by chewearn on 2007-02-24
Could you give some background on your network wirings?  Like, how you connects your PCs to the router/modem?

---

### Post by mips on 2007-02-24
> **AstalaVista said:**
> Could you give some background on your network wirings?  Like, how you connects your PCs to the router/modem?

+1

If you still have a windoze box the output of **ipconfig /all** could also be helpfull.

---

### Post by mips on 2007-02-24
> **Pidgin English said:**
> 
I downloaded the OS hoping that things would just work. This networking problem is really killing me. :(

You thought wrong and if someone led you to believe otherwise they were lying ;)

---

### Post by Pidgin English on 2007-02-24
> **AstalaVista said:**
> Could you give some background on your network wirings?  Like, how you connects your PCs to the router/modem?

Alright, it's all wired. I had the converted desktop on the inernet for months prior to my switchover (running Windows).

I tried the pppoe instuctions under "Help" just in case my connection needed it, but nothing was found when I tried the little app.

---

### Post by Floppyjoe on 2007-02-24
We do most things in the terminal in linux to get things working.
To access a terminal click on Applications/Accessories/Terminal.
enter the following command into the terminal and post the output:
```
ifconfig
```

---

### Post by Pidgin English on 2007-02-24
> **mips said:**
> 
If you still have a windoze box the output of **ipconfig /all** could also be helpfull.

Gah... What is a windoze box, and how do I use the output of ipconfig /all?



I should have never made the switch. :confused:  I'm only making a fool of myself due to my lack of computer skills.

Oh, well... Better to have made a fool of oneself and made a successful switch to a better OS than sat on one's buttocks and basked in the artificial light of an agonizingly slow Windows spyware dump.

If I do go back, I'll be needing something while my Media Player loads...:popcorn:

---

### Post by Pidgin English on 2007-02-24
> **Floppyjoe said:**
> We do most things in the terminal in linux to get things working.
To access a terminal click on Applications/Accessories/Terminal.
enter the following command into the terminal and post the output:
```
ifconfig
```

Thank you for putting it in simple terms, but when I did that I just got a bunch of incomprehendible text and a internet connection that still doesn't work.

---

### Post by Floppyjoe on 2007-02-24
Can you copy that incomprehesible text and post it here somehow?

---

### Post by undertakingyou on 2007-02-24
Those random numbers are information that can help get your internet connection going.  What I am guessing that your problem is the same one that I had when I first used ubuntu.  What you could do is get onto your working windows box and go to START=>CONTROL PANEL=>NETWORK CONNECTIONS and from there double click on the network connection there.  A box should pop up and one of the tabs is status.  Click that and it will give you several things.  The most important of which is the IP address and the default gateway.

Next, on your ubuntu box go to SYSTEM => ADMINISTRATION => NETWORKING  click on the wired connection and hit properties, if it says "Assigned by DHCP" hit that and put it to static IP address.  Now, the IP address from your working machine is probably 192.168.0.2 or something like that.  Put in the ubuntu box 192.168.0.7 or something that has a different last number than your working box.  Subnet mask should be 255.255.255.0  and the default gateway should be the same as your working box.  Hit OK and go to the DNS tab.  In there I want you to remove all numbers that are in there and add the following:  208.67.222.222 and 208.67.220.220

Hit close and then run firefox.  See if you can get to the web.  Worked for me.

---

### Post by Pidgin English on 2007-02-24
> **Floppyjoe said:**
> Can you copy that incomprehesible text and post it here somehow?

Alright, it took a while... (I had to take a screen, throw it on a usb drive, download it onto my blog, and then get the png on here).. but I did it!

[IMG]http://a752.ac-images.myspacecdn.com/images01/60/l_53633fbc61c70ad27cc07ce6c27982b7.png[/IMG]

---

### Post by Floppyjoe on 2007-02-24
Try this command in the terminal:
```
sudo dhclient eth0
```
The 0 behind eth is a zero.
If it assigns you an Ip address then try your web browser.

---

### Post by Pidgin English on 2007-02-24
> **undertakingyou said:**
> Those random numbers are information that can help get your internet connection going.  What I am guessing that your problem is the same one that I had when I first used ubuntu.  What you could do is get onto your working windows box and go to START=>CONTROL PANEL=>NETWORK CONNECTIONS and from there double click on the network connection there.  A box should pop up and one of the tabs is status.  Click that and it will give you several things.  The most important of which is the IP address and the default gateway.

Next, on your ubuntu box go to SYSTEM => ADMINISTRATION => NETWORKING  click on the wired connection and hit properties, if it says "Assigned by DHCP" hit that and put it to static IP address.  Now, the IP address from your working machine is probably 192.168.0.2 or something like that.  Put in the ubuntu box 192.168.0.7 or something that has a different last number than your working box.  Subnet mask should be 255.255.255.0  and the default gateway should be the same as your working box.  Hit OK and go to the DNS tab.  In there I want you to remove all numbers that are in there and add the following:  208.67.222.222 and 208.67.220.220

Hit close and then run firefox.  See if you can get to the web.  Worked for me.

I did everything as you told me to, but the connection is still flat. Any other ideas?

---

### Post by Pidgin English on 2007-02-24
> **Floppyjoe said:**
> Try this command in the terminal:
```
sudo dhclient eth0
```
The 0 behind eth is a zero.
If it assigns you an Ip address then try your web browser.

Alright, I tried it, and I got nothing but this: 

```
No DHCPOFFERS recieved
No working leases in persistent database - sleeping"
```

---

### Post by Floppyjoe on 2007-02-24
Go back into System/Administration/Networking and change it back to DHCP then make sure the interface is enabled. Then try the "sudo dhclient eth0" again.

---

### Post by Pidgin English on 2007-02-24
> **Floppyjoe said:**
> Go back into System/Administration/Networking and change it back to DHCP then make sure the interface is enabled. Then try the "sudo dhclient eth0" again.
Nothing, I got the exact same result. :(

---

### Post by Floppyjoe on 2007-02-24
Is your router setup to hand out dhcp IP addresses or static IP addresses?
I am running out of ideas here fast. Hopefully someone more knowledgeable will be able to help you with this.

---

### Post by Pidgin English on 2007-02-24
My working computer is fine searching for an IP, so I don't think I NEED a static IP. I'm guessing the modem assigns IP addresses.

This is really suprising, actually. I thought I might make  a thread, get a reply 5 minnutes later, fix my computer, and bob's your uncle, have a wonderful new computer that "Just Works".

---

### Post by Floppyjoe on 2007-02-24
There may be some kind of trouble with IRQ assignment for your wired interface. I noticed that the bottom line of your network interface after the iwconfig command showed a line that says something about interupt. I had the same problem on my laptop after compiling a custom kernel and could not get my wired interface to work. It also said something about interupt on the last line then. But I don't think that line is usually there when the interface is working. Maybe someone can enlighten us.

---

### Post by undertakingyou on 2007-02-25
Pidgin English,

Can you post for me what you put in ubuntu as the IP address, the default Gateway, and Subnet Mask?  I think that might answer some questions I have.

Thanks.

---

### Post by chewearn on 2007-02-25
> **Pidgin English said:**
> Alright, it's all wired. I had the converted desktop on the inernet for months prior to my switchover (running Windows).

I tried the pppoe instuctions under "Help" just in case my connection needed it, but nothing was found when I tried the little app.

Ok, I hear a lot of frustration, but very little in details on your existing network set up.  In order for us to help you, we need to know exactly how your network is set up.  That is the reason for all the questions about how you wired up your network, the output from your ifconfig and ipconfig commands.  Please work with us if you want us to work with you to solve this problem.

First, the most basic:
How do you connect to the internet?  I understand that you have a DSL modem?  How are you connecting your two PC to the modem?  Does the modem has built in router, when you simply plug your PCs to two of its ports?

Then:
Is your router set up as DHCP?  Or are you using static IP?  I see the screen shot of your ifconfig, showing eth0 using IPv6.  What is the ipconfig output at the Windows PC?
Go to Start -> Run -> cmc <Enter>; a terminal window will open; type in ipconfig <Enter>.  Copy the text output and post it here.

---

### Post by mips on 2007-02-25
> **Pidgin English said:**
> Gah... What is a windoze box, and how do I use the output of ipconfig /all?


Do you have a Windows PC on that network ? 
If you do go Start-->Run-->cmd  (type in cmd). This will open a command prompt/dos box, in there type **ipconfig /all **and paste the output here.

---

### Post by Pidgin English on 2007-02-25
Results from **ipconfig /all:**

```
Windows IP Configuration

Host name: COMP-DC3E0B8F38
Primary Dns Suffix: (NONE)
Node Type: Unknown
IP Routing Enabled: No
WINS Proxy Enabled: No

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix: (NONE)
Description: NVIDIA nForce Networking Controller
Physical Address: 00-40-CA-99-C5-D4
Dhcp Enabled: Yes
Autoconfiguration Enabled: Yes
IP Address: 192.168.1.100
Subnet Mask: 225.225.225.0
Default Gateway: 192.168.1.1
DHCP Server: 192.168.1.1
DNS Servers: 192.168.1.1
Lease Obtained: Sunday, Februrary 25, 2007 10:29:35 AM
Lease Expires: Tuesday, Februrary 27, 2007 10:29:35 AM
```

---

### Post by chewearn on 2007-02-25
Ok, sorry to ask again, but could you go to your ubuntu, run this command in the terminal:
```
ifconfig
```

Post the text output again.  (If you have a thumbdrive, you can copy paste into a text file, copy the file to you working windows PC via thumbdrive).

Again sorry to ask again, but I did not keep track of the changes since you last posted many hours ago.

---

### Post by Pidgin English on 2007-02-25
Sorry it took a while. ifconfig results:

[IMG]http://a796.ac-images.myspacecdn.com/images01/64/l_aa2d4044640234c2342a8cadf1a3febb.png[/IMG]

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> Ok, I hear a lot of frustration, but very little in details on your existing network set up.  In order for us to help you, we need to know exactly how your network is set up.  That is the reason for all the questions about how you wired up your network, the output from your ifconfig and ipconfig commands.  Please work with us if you want us to work with you to solve this problem.

First, the most basic:
How do you connect to the internet?  I understand that you have a DSL modem?  How are you connecting your two PC to the modem?  Does the modem has built in router, when you simply plug your PCs to two of its ports?

Then:
Is your router set up as DHCP?  Or are you using static IP?  I see the screen shot of your ifconfig, showing eth0 using IPv6.  What is the ipconfig output at the Windows PC?
Go to Start -> Run -> cmc <Enter>; a terminal window will open; type in ipconfig <Enter>.  Copy the text output and post it here.

I connect to the internet using both a DSL modem and a (wired) Linksis 4 port Cable/DSL router. It is completely wired. No, the modem does not have a built in router.

My router (I believe) is set up as DHCP; this working desktop is set up to search for it's addresses under my connection properties. I just posted the ipconfig /all results a minnute ago. I hope that helped.

---

### Post by chewearn on 2007-02-25
I saw the DHCP messages on top (before you execute ifconfig), but it came back negative.  Then in your ifconfig output, there is no IP address assigned.

Seems like DHCP is not working.  Three things you could do:
1. Check your router DHCP settings
2. run this:

```
sudo dhclient eth0
```

3. Use a static IP instead

---

### Post by Pidgin English on 2007-02-25
> **undertakingyou said:**
> Pidgin English,

Can you post for me what you put in ubuntu as the IP address, the default Gateway, and Subnet Mask?  I think that might answer some questions I have.

Thanks.

I have it under DHCP currently. So, I have no addresses entered.

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> I saw the DHCP messages on top (before you execute ifconfig), but it came back negative.  Then in your ifconfig output, there is no IP address assigned.

Seems like DHCP is not working.  Three things you could do:
1. Check your router DHCP settings
2. run this:

```
sudo dhclient eth0
```

3. Use a static IP instead

Alright, I tried the dhclient again and I still cannot get the DHCP to work.

Is there any way you could help me get into my router's settings?


...or otherwise help me set up some static IP's?

---

### Post by Pidgin English on 2007-02-25
Alright, I can access my router settings if that helps.

How should it be set up? "Obtain an IP automatically" maybe "PPPoE"?

---

### Post by chewearn on 2007-02-25
To get into the router settings, use your internet browser, type in the address bar the IP address of the router: 192.168.1.1

A dialog box should pop up, asking for the username and password.  In case you have never change your router login, I belief the default for Linksys is "admin" for both username and password.  Else, you need to look for it in your router manual.

If that didn't work, to set up static ip, goto: System-> Administration -> Networking.  Select wired connection (eth0), click property, change the list box to Static IP, enter:

1. a free ip address (e.g. 192.168.1.50)
2. 225.225.225.0 for mask
3. 192.168.1.1 for gateway

---

### Post by chewearn on 2007-02-25
> **Pidgin English said:**
> Alright, I can access my router settings if that helps.

How should it be set up? "Obtain an IP automatically" maybe "PPPoE"?

No, those are the IP you get from the ISP.

Go down the page, you should see Local DHCP server.  Should be enabled.
Also, check the start iP, default should be 192.168.1.100
And the next item should be number of addresses; default should be 50.

---

### Post by Pidgin English on 2007-02-25
I did try that before, but nonetheless, I felt that I should try it one more time. It didn't work. 

I'm stumped! If there is a perfect line to the internet and it's flowing fine, what could be precventing my desktop from accessing it? There's got to be a way to fix this!


Maybe I should start praying to the computer gods?

---

### Post by Rui Pais on 2007-02-25
> **undertakingyou said:**
> Those random numbers are information that can help get your internet connection going.  What I am guessing that your problem is the same one that I had when I first used ubuntu.  What you could do is get onto your working windows box and go to START=>CONTROL PANEL=>NETWORK CONNECTIONS and from there double click on the network connection there.  A box should pop up and one of the tabs is status.  Click that and it will give you several things.  The most important of which is the IP address and the default gateway.

Next, on your ubuntu box go to SYSTEM => ADMINISTRATION => NETWORKING  click on the wired connection and hit properties, if it says "Assigned by DHCP" hit that and put it to static IP address.  Now, the IP address from your working machine is probably 192.168.0.2 or something like that.  Put in the ubuntu box 192.168.0.7 or something that has a different last number than your working box.  Subnet mask should be 255.255.255.0  and the default gateway should be the same as your working box.  Hit OK and go to the DNS tab.  In there I want you to remove all numbers that are in there and add the following:  208.67.222.222 and 208.67.220.220

Hit close and then run firefox.  See if you can get to the web.  Worked for me.

Thats a good solution. 
In your case it probably failed because dhcp must have automatically overwrite the 
manually DNS ips. 

To workaround this, check this [page here]("http://opendns.com/start/ubuntu.php").

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> No, those are the IP you get from the ISP.

Go down the page, you should see Local DHCP server.  Should be enabled.
Also, check the start iP, default should be 192.168.1.100
And the next item should be number of addresses; default should be 50.

Check, check, check... It seems that my router is fine. I guess that would make sence seeing as this computer is running smoothly (except for little hicups now and then).

Alright, so if the DHCP server is enabled, why wouldn't my ubuntu desktop be able to sence it?

I just did a cable check just to make sure nothing was up. Seems like everything is fine; it'd be one heck of a coincidence if a squirrel decided to chew through the cable the moment I downloaded ubuntu.

---

### Post by chewearn on 2007-02-25
Could you post the text output from when you run sudo dhclient eth0 ?
Also, have you tried the static ip option?

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> Could you post the text output from when you run sudo dhclient eth0 ?
Also, have you tried the static ip option?

Alright, here's the text output:

[IMG]http://a65.ac-images.myspacecdn.com/images01/54/l_c75adb1bb1a7f598ca8d1634b833fa00.png[/IMG]



I did try the static IP option, it didn't work. But I might add that this DHCP solution that Rui Pais posted did have some exciting results.

Beforehand, whenever I started firefox it would immediately jump to the error page. Now, (after following that article) firefox is TRYING to find websites, but alas, does not in the end.

---

### Post by undertakingyou on 2007-02-25
I don't think that your router has DHCP running at all.  If it did you would have a line that said something like this

   * inet addr:192.168.10.187  Bcast:192.168.10.255  Mask:255.255.255.0*

Which would tell you the IP address.  The Broadcast IP,(Which Alludes to the Default Gateway) and the subnet mask.  You don't have any of those.  You need to either log into the router on the working machine and make sure that DHCP is running (because it _really_ doesn't look like it) or you need to set a static IP so that a line similar to above fills in when you run IFCONFIG

---

### Post by chewearn on 2007-02-25
When you assigned a static ip address, e.g. 192.168.1.10 do you then see the ip address appearing in the ifconfig command under eth0?

```
inet addr:192.168.1.10
```

---

### Post by Pidgin English on 2007-02-25
> **undertakingyou said:**
> I don't think that your router has DHCP running at all.  If it did you would have a line that said something like this

   * inet addr:192.168.10.187  Bcast:192.168.10.255  Mask:255.255.255.0*

Which would tell you the IP address.  The Broadcast IP,(Which Alludes to the Default Gateway) and the subnet mask.  You don't have any of those.  You need to either log into the router on the working machine and make sure that DHCP is running (because it _really_ doesn't look like it) or you need to set a static IP so that a line similar to above fills in when you run IFCONFIG

I'm in my router's setup right now, and DHCP is definitely enabled. I've tried static IPs and that isn't working. We're going to need new ideas. Like I said though, that DHCP article that was posted did get firefox to actually look for websites, so I'm guessing that would be the right direction to head in.

---

### Post by undertakingyou on 2007-02-25
The reason I say that it doesn't look like the DHCP server is running is because in you output you posted two posts ago, Said "NO DHCPOFFERS".   That means that your computer is not receiving anything from DHCP.  Without a line in your ifconfig output that says inet addr: . . . you will never get to the internet.  Which is why several of us have suggested to do the static IP address aproach.  If you do the static IP address, and then run the command ```
ifconfig
``` do you see a line that says inet addr: . . . Bcast: . . . Mask: . . .?

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> When you assigned a static ip address, e.g. 192.168.1.10 do you then see the ip address appearing in the ifconfig command under eth0?

```
inet addr:192.168.1.10
```

No, I don't get anything like that when I run ifconfig.

Just that line that says:

```
inet6 addr: fe80::20c:6eff:fe72:e32/64 Scope:Link
```


Should I burn a new live CD and load ubuntu again?

---

### Post by Pidgin English on 2007-02-25
> **undertakingyou said:**
> The reason I say that it doesn't look like the DHCP server is running is because in you output you posted two posts ago, Said "NO DHCPOFFERS".   That means that your computer is not receiving anything from DHCP.  Without a line in your ifconfig output that says inet addr: . . . you will never get to the internet.  Which is why several of us have suggested to do the static IP address aproach.  If you do the static IP address, and then run the command ```
ifconfig
``` do you see a line that says inet addr: . . . Bcast: . . . Mask: . . .?

No, I get the exact same lines as were posted on the last page.

---

### Post by mips on 2007-02-25
> **Pidgin English said:**
> 
I did try the static IP option, it didn't work. But I might add that this DHCP solution that Rui Pais posted did have some exciting results.


Did you copy and paste the ipconfig /all or did you type it out. The subnet mask is weird 225.225.225.0, it's usually 255.255.255.0. Maybe try that with your static config and see if it helps. Use your routers address as that of the dns server.

---

### Post by Rui Pais on 2007-02-25
uhmm...
since you got only a inet6 addr: fe80::20c:6eff:fe72:e32/64 Scope:Link i wonder if it's a ipv6 issue blocking standard ips numbers to be set...

You may try:
```
sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
```
and reboot to see if you got an inet xxx.xxx.xxx.xxx instead of inet6

---

### Post by chewearn on 2007-02-25
That article described assigning a DNS address.  It is not directly related to DHCP.

What you need right now is an IP address for your ubuntu setup.

Translation: assigning DNS address right now is looking two steps ahead; without an IP, you cannot connect to your router.  So there is no way to connect to the DNS.

Since DHCP is not working for unknown reason, I am thinking you need a static IP, but it has got to appear in your ifconfig first.

Then, you ping your router, see if you get a response.

```
ping 192.168.1.1
```
Ctrl^C to stop.

Then, you can goto DNS tab, add in the DNS IP.  Usually, the router IP can be used; if still not working, then you add in the external DNS, as stated in the article.

---

### Post by Pidgin English on 2007-02-25
> **mips said:**
> Did you copy and paste the ipconfig /all or did you type it out. The subnet mask is weird 225.225.225.0, it's usually 255.255.255.0. Maybe try that with your static config and see if it helps. Use your routers address as that of the dns server.

Sorry, dumb mistake. I couldn't copy it (I'm not sure how you highlight that text) so I did try to type it.

---

### Post by Pidgin English on 2007-02-25
> **Rui Pais said:**
> uhmm...
since you got only a inet6 addr: fe80::20c:6eff:fe72:e32/64 Scope:Link i wonder if it's a ipv6 issue blocking standard ips numbers to be set...

You may try:
```
sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
```
and reboot to see if you got an inet xxx.xxx.xxx.xxx instead of inet6

Alright, good news: It worked. I have an IP. :) 

Bad News: Still no Internet. :(

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> That article described assigning a DNS address.  It is not directly related to DHCP.

What you need right now is an IP address for your ubuntu setup.

Translation: assigning DNS address right now is looking two steps ahead; without an IP, you cannot connect to your router.  So there is no way to connect to the DNS.

Since DHCP is not working for unknown reason, I am thinking you need a static IP, but it has got to appear in your ifconfig first.

Then, you ping your router, see if you get a response.

```
ping 192.168.1.1
```
Ctrl^C to stop.

Then, you can goto DNS tab, add in the DNS IP.  Usually, the router IP can be used; if still not working, then you add in the external DNS, as stated in the article.

Alright, I've got an IP appearing in ifconfig, but when I tried to ping my router I had no received packets.

---

### Post by chewearn on 2007-02-25
Ok, this is getting strange.  Are you sure there is no problem with your ethernet cabling?

Try pinging your ubuntu from your Windows PC; in a command prompt in **Windows**, type:

```
ping 192.168.1.10
```

assuming 192.168.1.10 is your new ubuntu IP address.

---

### Post by Pidgin English on 2007-02-25
> **AstalaVista said:**
> Ok, this is getting strange.  Are you sure there is no problem with your ethernet cabling?

Try pinging your ubuntu from your Windows PC; in a command prompt in **Windows**, type:

```
ping 192.168.1.10
```

assuming 192.168.1.10 is your new ubuntu IP address.

No recieved packets. This is weird, I haven't touched the cabling since I made the switch to ubuntu. It was working beforehand.

---

### Post by mips on 2007-02-25
ping 72.14.203.99
ping 196.25.1.1

If you get a response from those then your internet is working but DNS is not which will have to be fixed.

---

### Post by Pidgin English on 2007-02-25
> **mips said:**
> ping 72.14.203.99
ping 196.25.1.1

If you get a response from those then your internet is working but DNS is not which will have to be fixed.

A response from what? Both pings failed.

---

### Post by Rui Pais on 2007-02-25
sorry, but isn't your router ip 192.168.1.1? 

are you sure that you used that ip?



btw, are you on static ip or dhcp set?

---

### Post by Pidgin English on 2007-02-25
> **Rui Pais said:**
> sorry, but isn't your router ip 192.168.1.1? 

are you sure that you used that ip?



btw, are you on static ip or dhcp set?

Yes, I am sure I used 192.168.1.1 when I tried a ping on my ubuntu. This computer is pinging to that address just fine.

My router has DHCP enabled and this computer is set to obtain both it's own IP and a DNS server address. My ubuntu is (currently) set to a static IP... I guess because some people think my DHCP isn't working (but at the same time is... with this windows). I trust their ideas more than mine though, I haven't a clue when it comes to ubuntu.

In my opinion, things should "Just Work"... :lolflag:

---

### Post by Lionmew on 2007-02-25
I just installed ubuntu today and ran into the same issue as you.

I also use a DSL modem and my windows drive connects using automatic DHCP.

The problem I found for me is the DNS server it is trying to look at.

To see if this is your problem too, try going to:
[http://72.14.207.99](http://72.14.207.99)

Wait a few moments and if firefox brings up Google then your internet connection is working just fine, it's just the DNS setting that is incorrect.

Let us know how that works out.

For the others, is there anyway to set Ubuntu to automatically detect a DNS server to use?

It assigned my gateway as the DNS IP and that's not working.

---

### Post by Lionmew on 2007-02-25
Also if you try what I told you to, set it back to Auto DHCP assignment... like you had it to begin with.

---

### Post by Rui Pais on 2007-02-25
some times it's easier with static ip, besides with only one computer it's usually faster then wait for the assignment of the ip from the dhcp server...

i asked to confirm the 192.168.1.1 because above you guys are mention 192.168.1.10...

so you still with no connection? what the output now of 
```
cat /etc/resolv.conf
```
and
```
cat /etc/network/interfaces
```

---

### Post by Pidgin English on 2007-02-25
Lionmew, when I enterred in 72.14.207.99 I got nothing... unfortunately.

---

### Post by BoZZ on 2007-02-25
pidgin........Is you box by any chance Sli?

---

### Post by Pidgin English on 2007-02-25
> **BoZZ said:**
> pidgin........Is you box by any chance Sli?

What do you mean by that? Sorry, I'm not to great with computers. My box? Sli?

---

### Post by Pidgin English on 2007-02-25
> **Rui Pais said:**
> some times it's easier with static ip, besides with only one computer it's usually faster then wait for the assignment of the ip from the dhcp server...

i asked to confirm the 192.168.1.1 because above you guys are mention 192.168.1.10...

so you still with no connection? what the output now of 
```
cat /etc/resolv.conf
```
and
```
cat /etc/network/interfaces
```

The results:

[IMG]http://a889.ac-images.myspacecdn.com/images01/53/l_0db86e88385be6ba93ff048755cba410.png[/IMG]

---

### Post by BoZZ on 2007-02-25
box= P.C.    sli is a type of intel motherboard I ask Becouse I got a new Pc and I am having the exact same problems as you are......

---

### Post by Pidgin English on 2007-02-25
> **BoZZ said:**
> box= P.C.    sli is a type of intel motherboard I ask Becouse I got a new Pc and I am having the exact same problems as you are......

I'm not sure if it's a Sli; It's my parent's old VAIO, actually. If your new PC has a Sli motherboard, I doubt that my 3 year old VAIO would.

---

### Post by Rui Pais on 2007-02-25
you set a wrong ip to your machine and gateway...

```
gksudo network-admin
```

and change 192.168.0.3 ->192.168.1.3 on ip field
and  192.168.0.1 -> 192.168.1.1 on gateway field

Try to surf the web then and post results.

---

### Post by psignosis on 2007-02-25
> **JJNam said:**
> I'm in the same boat (new, etc...).  Though I have figured out how to enable internet access through Firefox.  

I'm installed on ~5 year old Intel hardware w/built in NIC and I had to disable IPv6 in Firefox to get it running.  This may not be true for you, but it doesn't hurt to try.

From Firefox, type "about:config" and search for ipv6.  Set it to disabled.

I still can't get the software updates to work or add/remove programs to update though. :(

Thanks for the IPv6 hint, that really helped me out.  Fortunately I don't seem to have the same problem with software updates etc.

---

### Post by chewearn on 2007-02-25
Well, there your problem.  You have 192.168.1.1 for router, 192.168.0.3 for ubuntu.  Your ubuntu is not in the same subnet as the rest.  Make sure the first, second and third digits are the same.  The last digit should NOT be the same.

p.s. sorry not able to stay around earlier to follow thru with you; have to go offline a couple of hours.  Meanwhile, you  have to start all over again with new people coming into this thread.

---

### Post by Pidgin English on 2007-02-28
> **Rui Pais said:**
> you set a wrong ip to your machine and gateway...

```
gksudo network-admin
```

and change 192.168.0.3 ->192.168.1.3 on ip field
and  192.168.0.1 -> 192.168.1.1 on gateway field

Try to surf the web then and post results.

Didn't work... I tried 192.168.1.3 for my IP and 192.168.1.1 in gateway. Some suprise it failed again. (I even switched the cables between the computers today [BIG OPERATION] and that didn't work so I know it's something a little more complicated.)


I've been thinking, could it be my ISP? I have frequent problems with my windows as well, I sit down to use the internet and it just... doesn't work. Most of the time I disable the connection, reset the modem and router, enable the connection, repair it and for some damn reason IT WORKS! I have no idea why it does this, but my solution seems to work... temporarily. I'm starting to get sick of it though. :mad: 

Or could it possibly be the distro? Should I try Dapper Drake? I'd be my guess that the older versions of ubuntu would be a little more reliable.

I'm just throwing out ideas because I'm getting desperate. I felt so excited about ridding myself of the chains of Microsoft, but if things don't work out... That desktop is going to have to suck again (Yes, it will be slow as heck... but at least it will work!). After all, this is my parent's computer and I want my own. (I'm seventeen, so don't think  I'm some sort of weirdo)

I'm just thowing out ideas, please if you're reading this, just give me any good ideas that you might have.

---

### Post by chewearn on 2007-03-01
Just throwing in a wild idea... are you running heavy bittorrent traffic?  Then, what router (brand, model number) are you using?

---

### Post by Rui Pais on 2007-03-01
> **Pidgin English said:**
> Didn't work... I tried 192.169.1.3 for my IP and 192.168.1.1 in gateway. Some suprise it failed again. (I even switched the cables between the computers today [BIG OPERATION] and that didn't work so I know it's something a little more complicated.)


I've been thinking, could it be my ISP? I have frequent problems with my windows as well, I sit down to use the internet and it just... doesn't work. Most of the time I disable the connection, reset the modem and router, enable the connection, repair it and for some damn reason IT WORKS! I have no idea why it does this, but my solution seems to work... temporarily. I'm starting to get sick of it though. :mad: 

Or could it possibly be the distro? Should I try Dapper Drake? I'd be my guess that the older versions of ubuntu would be a little more reliable.

I'm just throwing out ideas because I'm getting desperate. I felt so excited about ridding myself of the chains of Microsoft, but if things don't work out... That desktop is going to have to suck again (Yes, it will be slow as heck... but at least it will work!). After all, this is my parent's computer and I want my own. (I'm seventeen, so don't think  I'm some sort of weirdo)

I'm just thowing out ideas, please if you're reading this, just give me any good ideas that you might have.

hi,
my 2 or 3 cents. then.

Computers deal with each others through net cards so they use ip addresses, it's natural for them. Us, humans, we call machines things like www . mozilla . org, etc. for one specific reason. We deal badly with series of numbers. When one have to deal with ip addresses must take double care or mistakes will eventually raise. Don't go light on these, most of network problems is bad function of that *hardware* that stays between the keyboard and the chair ;)
You have before put wrong ip numbers and now on your post you mention a "192.169.1.3 for my IP and 192.168.1.1 in gateway". Are this a typo? You **must** ensure that for ip you have 192.16**8**.1.3 and gateway is 192.168.1.1. last number of ip can vary as long that it won't colide with other machine ip on your network, but the first 3 numbers must be 192.168.1 

Second, as we put names on number named computers, we need servernames. In most cases we just point DNS servernames as our gateway and the router managed by it self to get it. But with some models that don't work (D-Link, among others, usually have that problem). Sometimes /etc/resolv.conf is overwritten and if you have put there opendns ones or your ip provider specific ones they may have be replaced by your gateway ip only, that may or may not work. Check it again. (Note that this is apparently a *nix only problem.)

And my third cent, is the one i would check first. 
You say you wave problems on windows too, with connection lost? You need to trace that.
It could, of course, be hardware failures. Equipment broke with time and use... but usually routers and net cards are solid and long time duration.
There are 2 things that usually can make internet connection problems. 
Your internet provider use ADSL2 and your router is older and don't know such technology. 
I had problems with that. My connection failled randomly after some hours connected and some times it take 1 or 2 hours to be back again (after i got synchronization line on router window). A new modern router was the only solution.
The second is the high speed normal on these days, lightly offered by our internet providers. This is an insane world of high-tech/high-speed internet, based on our last century phone lines... you know that 2 little thin wires that stick out of the wall that (supposedly) can take Mb of data, up and down plus our talks simultaneously!! 
On Windows you can open your router configuration windows and search around for the values you get for 'SRN Margin' and 'Line Attenuation'. If your your SNR margin is too close to 10 (like 11,12) your line is saturated and your connection will be easily lost. Bellow 10, you don't have synchronization and your network fail to connect.


Sorry the long post. hope it give you some clues.

---

### Post by undertakingyou on 2007-03-01
My thoughts are in line with the others.  If this is a "universal" problem between both the windows machine and the ubuntu machine it very well could be hardware.  Maybe a firmwire update to your modem or router could do it, maybe replacement.

---

### Post by Pidgin English on 2007-03-01
Alright, I just want to make a point and say that **I really appreciate all the help I've had in this forum.** I switched my desktop to a ubuntu client hoping just for free aplications and freedom from the spyware and virus scum that builds up around the gills of most windows zombies. But now I've realized that ubuntu is truly a *community,* and not just an OS. I'll quit being so sappy before I make anyone cry, but again thank you all. :) 

I don't think there is much I can do about my connection but look for a new ISP and (maybe) a new router. :-k Before I jump to any conclusions, however, I'm cutting the router out of the equation and checking to see if I get the little pot-holes in my internet connection. I think you can do the math and figure out that network problems minus router equals worthless modem. Your opinions are obviously well backed, Rui Pais and undertaking you; I keeping them in mind.

Oh, and 192.169.1.3 **was** a typo. (DUH!) I should check these messages before I submit them. ](*,)

~Cheerio! :) 


[Hah! I try to submit this... and my bloody internet doesn't work. Typical, right?]

---

### Post by Pidgin English on 2007-03-01
> **AstalaVista said:**
> Just throwing in a wild idea... are you running heavy bittorrent traffic?  Then, what router (brand, model number) are you using?

No, I don't download anything on my computer. I'd say that my internet connection was in use for 2-3 hours a day to surf the web. But if it helps, I have a westell DSL modem (model 6100) and Linksis Cable/DSL Router With 4-Port Switch (model no. BEFSR41 ver. 3). :-|

~Cheerio!

---

### Post by Rui Pais on 2007-03-04
Hi again,
Yes Linux community spirit is one of the best of Linux things :) 
And one always learn things about computers and OSs, instead of learn brandmarks of anti-virus and whats the last spywares or the last viruses on the block ;)

Don't worry about the typos. It's even worst for those, like me, that don't have English as a native language (luckily FF2 with it's syntax check save me for so many embarrassing situations). 
But always ckeck twice for information or code when post. That's so easy one make mistake or induce others in error (i just made that in another thread :()

back to business. You have 2 problems. 
Internet connection failed (on both OSs) an you can connect with Ubuntu.

Your equipment are relatively new and should support any dsl protocol, so no worrys with that.
Whats the SRN margin and Attenuation values you get from Windows when you are connected? (Available through the config windows of your modem with a browser)

On Ubuntu we need to go again (sorry) with the usual rotine of ask for the output of:
```
cat /etc/network/interfaces
``` and
```
cat /etc/resolv.conf
```
?

---

### Post by Pidgin English on 2007-03-05
Alright, *this is weird.* I try to access my modem by typing in 192.168.1.1 in my address bar and I get my Linksys Router's firmware *(Yeah, yeah... that's what would be expected)*. I don't know any other way to access my modem, so I disconnect the router and try a direct cable to the modem. Unfortunately enough, my working desktop then decides not to work. I don't know whether it's some sort of DHCP error or what but when I connect directly, this computer cannot assign itself an IP address when wired to that modem. So, the "This connection has limited or no connection" bubble pops up and the computer just forfeits the search for the holy grail (or make that the IP address).

Ok, so I have no connection... That's not good. So I rewire my network so that the cables run from the modem to the router and eventually to the desktop. Now it works, and I don't know why. It seems that, when wired directly, this desktop faces the same problems that my ubuntu box does. :-| 

Summary:

~Direct Connection to Modem fails on Windows desktop:
   -Computer unable to assign itself an IP
   -Runs smoothly when connection is wired through router

~Unaware of methods of access for modem besides address: 192.168.1.1 (results in Linksys firmware)

So, simply put, **how do I connect to my modem?** :D

(Oh, and Rui Pais, I do somewhat understand the ubuntu environment. I did a little exploring, and quite frankly, it's basics are pretty simple. I do admit to my slight inexperience with computers... I am, after all, only 17 and have self-taught myself everything I know about computers. But nonetheless, I believe I know much more about computers than the average student at my school. I find it infuriating to witness people ruining computers over and over again due to their misunderstanding of their basic components, and that's why I really looked into computers in the first place. Toolbars make me go nuts.)

---

### Post by undertakingyou on 2007-03-05
Pidgin, what is the IP address to your router?  How do you log into the router to change settings etc. ??

---

### Post by chewearn on 2007-03-05
> **Pidgin English said:**
> Alright, *this is weird.*...

It's not weird; it is easily explained. :)  (see next)

> 
~Direct Connection to Modem fails on Windows desktop:
   -Computer unable to assign itself an IP
   -Runs smoothly when connection is wired through router


You have been using your router as DHCP.  Naturally, if you remove router from the link, your Windows machine don't get an IP address.

> 
~Unaware of methods of access for modem besides address: 192.168.1.1 (results in Linksys firmware)

Once router sits between modem and PC, you can't connect to your modem, because the router NAT blocks you access to modem.


> So, simply put, **how do I connect to my modem?** :D


Connect PC directly to modem, set you PC to static IP *in the same subnet*.

...

Now, I will throw in another wild idea (for others monitoring this thread, please go back through the posts; you will find we have exhaust every *known/normal* methods to resolve Pidgin English connection problem).

Do you check whether your ethernet cables are straight or crossed type.  Most modern equipment are able to autoconfigure their ports to take care of this, but I have seen rare/intermittent cases where the ubuntu machine messed up the autoconfiguration.

---

### Post by chili555 on 2007-03-05
Here is another thought: [http://www.dslreports.com/forum/remark,16432924](http://www.dslreports.com/forum/remark,16432924)

---

### Post by standards on 2007-03-06
I actually had a lot of similar issues as the original poster- for some reason it seemed like the router just wouldn't cough up an IP for me. The whole "No DHCPOFFERS Received" error via `ifup eth0`. But internet on my windows partition worked fine.

As a last resort I tried resetting the router's original software defaults, by logging onto the router ala 192.168.0.1 (or whatever it is for you). This restored all the services I had deleted, all the static IPs I had configured, etc etc. I had to wait a bit for the router to renew its DHCP lease, then I rebooted back to ubuntu and tried again. And magically everything suddenly worked perfectly, and I have no idea why. But yeah, one more thing to try?

---

### Post by FernandoGonzalez on 2007-03-06
I've been following this discussion from the beginning as I had problems with my connection as well.

<verbose>
When I first installed Ubuntu it recognized everything perfectly, including my internet connection (cable/ethernet). I subsequently went on a downloading spree for a couple of weeks.

Then I started having problems with my connection on this machine as well as three other Windows boxes. Nothing too serious, just rare, periodic times of unresponsiveness.  After a change in modem, (from Motorola Surfboard to Motorola SBV5120) everything started working fine again.

For about a week.  Then my Ubuntu wouldn't recognize my eth0. 

Disconnect lan, connect lan, restart, disconnect, connect, shutdown, boot, connect,disconnect, switch to enlightenment, repeat, switch to back to gnome, repeat, switch repeat ... Nothing worked. 

Tried it on my Windows machines. Perfect. Damn.

I'm pretty new to Linux so I googled and googled till I stumbled upon this thread were the starter's symptoms matched mine.  I tried to follow the instructions but still nothing worked.

I finally concluded that my inexperience and overzealousness in trying out stuff were the culprits.  I knew I hadn't touched my network settings at any point but since I had already somehow lost my ability to control volume through my gnome volume applet or my e17 mixer module, resorting to gnome-volume-control from a terminal instead, I had to give Ubuntu the benefit of the doubt.

So today I reluctantly did a clean install of Edgy Eft from the same CD as before (after a backup, of course).  Last time, I had the machine plugged to the internet through ethernet during the installation. This might have contributed to the easy detection.  Since my connection wasn't working on this machine I forgot to keep it connected during the installation process. This might or might not have any effect.  After installation and before the first reboot I remembered the aforementioned fact and plugged the LAN line to the cable modem. Reboot. Everything looks fine. Network monitor applet in gnome-panel shows...   no eth0.   Noooooo!!   I mean, Damn.

Firefox -> [www.google.com](www.google.com) -> Nothing.  Damn.
Terminal -> ifconfig -> Same as before. Damn.
What could I do?
Check plug is in really tight. Nothing. Try to push it in just a liiittle bit more. Nothing.

Disconnect power to my modem. Wait 5 seconds.  Connect power. Wait for it to startup ...

Success!!! :guitar:

network monitor shows eth0. Chooooose it...  [www.google.com](www.google.com)...  Yesss!!

Now I can sleep. 

WAIT!  Not before posting on Ubuntuforums, cause that's what ubuntu's all about I guess ;)
</verbose>

I hope this helps someone out there. I tried not to leave anything out 'cause I don't know what might be key.

Thanks to all.

---

### Post by Pidgin English on 2007-03-06
> **undertakingyou said:**
> Pidgin, what is the IP address to your router?  How do you log into the router to change settings etc. ??

I use the generic IP: 192.168.1.1

---

### Post by gerkin on 2007-07-16
Hi, check out my post here it might help:

 [http://ubuntuforums.org/showthread.php?p=3030748#post3030748](http://ubuntuforums.org/showthread.php?p=3030748#post3030748)

---

