---
title: "Brodcom 4311 - Can see networks but cannot connect to them"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by tweak50 on 2008-10-05
Sorry if this is posted somewhere else, I searched but could not find a solution to my peticular problem.

I installed ubuntu on a hp pavilion dv2500 which has a brodcom 4311 wireless card.  After following a couple of tutorials on the ndiswrapper, I can now see wireless networks, but when I connect to them it does nothing.  It looks like it tries for about a minuet and then gives up.

Here is the information about the card from a lspci

04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

I would really appreciate any help or a shove in the right direction with this.  I am a 100% noob to this, as this is my first linux install, please be gentle.

---

### Post by martinplt on 2008-10-05
Presumably you have got the security settings correct?

This sounds similar to the problem I am having with a Broadcom 4306. The card can see the networks okay but then does not connect.It seems that it is not being assigned an IP address, which suggests the process is failing at the authentication stage. That is why I mention the security settings. Not that I get any further when I switch the security off at the access point... 

I'm working with Gutsy Gibbon release.

---

### Post by tweak50 on 2008-10-05
Yeah I had thought of that at first.  Security is disabled at the ap I want to connect to.

---

### Post by amanita on 2008-10-05
I have exactly same problem with BCM4312 in my laptop HP 6720s :( ](*,)

---

### Post by tweak50 on 2008-10-05
> **amanita said:**
> I have exactly same problem with BCM4312 in my laptop HP 6720s :( ](*,)

Frustrating isn't it?  This isn't a very good experiance for a first timer ;)

---

### Post by maruda on 2008-10-06
Hi,
if you agree I want to join to this thread.

I have the same problem with BCM4312 (rev 01) in Dell XPS1330n
I am sure the problem is in drivers I can see wifi network but I cannot connect to. But, if I suspend my laptop and wake on it up ...tada! I am connected to my wifi network! Why does it work after that?

I am using ndiswrapper and wicd manager.

Please anybody let me explanation where is the problem? 

-=maruda=-

---

### Post by Ayuthia on 2008-10-06
What all of you might try to do first is remove the encryption on your router and see if you can connect.  If you can, then we know that it is a matter of figuring out how to get the encryption to work.  If it is an encryption issue, then it might just be a matter of checking to see if you are using the correct option when entering your password.  I can't remember what Ubuntu uses as a default, but I think that 128-bit needs to be selected. Unfortunately, I am not an expert in encrption, but there are others here that could help.

However, if you cannot connect without encryption, then please post the results of lspci -nn from the Terminal (except for the original poster since the information is already provided) so that we know which chipset you are using.

---

### Post by seagullplayer77 on 2008-10-06
I had the same issue with a different wireless card, and one of the suggestions that was made was that I download Wicd and use it instead of the Network Manager. I don't think Wicd is in the official Ubuntu repos, but it shows up if you Google it. Btw, this particular solution didn't work for me, but you might want to give it a try.

For me to actually get WiFi, here's what I've got to do:

[PHP]chrkal@ubuntu:~$ sudo ifconfig wlan0 down
chrkal@ubuntu:~$ sudo ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
[/PHP]

After that, I can connect to wireless networks. If you're wireless network interface is called something other than wlan0, substitute that in wherever you see wlan0. And xx:xx:xx:xx:xx:xx is going to be the MAC address of your wireless network interface. 

Give both solutions a try, and good luck!

EDIT: Ach...the angry faces weren't supposed to be there. Sorry about that...should read as a generic MAC address.

---

### Post by Lexus Dominus on 2008-10-06
Are you using hardy? if so, your problem has already been solved. check the highest sticky in the networking section.

---

### Post by martinplt on 2008-10-07
Thats kind of interesting, the MAC piece. I need to think how that would work, Sorry to say it, but I fixed the problem- put in a D-Link card. Texas Instruments rules. I now have two WLAN radios but what the hell? It works and  that's good enough for me, until I re-assemble the energy and patience to have another go at this. 

Best regards to all. Martin

---

### Post by maruda on 2008-10-08
Hi,
Ayuthia thanks for advice. In fact when I turned off authentication in my router I got connection. So, you have right it seems to be problem with an encryption. I guess I need to read abut this in Linux.

In router I am using WPA 128 bit encryption. I am using Linux Ubuntu 8.04.

-= maruda =-

---

### Post by maruda on 2008-10-08
> **maruda said:**
> Hi,
Ayuthia thanks for advice. In fact when I turned off authentication in my router I got connection. So, you have right it seems to be problem with an encryption. I guess I need to read abut this in Linux.

In router I am using WPA 128 bit encryption. I am using Linux Ubuntu 8.04.

-= maruda =-

Oh, My mistake. I am using WEP 128 bit enscryption - not WPA, but...
There is two tabs in configuration of my router.
First: Wireless.
I can set there general information about wireless network like name, channel, encryption type (WEP 128bit) , encryption method (Shared key).
Second: 802.1x/WPA
In this tab there is option to set 802.1X Authentication and I can choose three values for 'Wireless Port Control': auth. required, no auth. required, no access allowed.
I am a little confused because in wicd manager in advanced option the WPA and WEP are separately position in the encryption list.

Thanks for advice.
-= maruda =-

---

