---
title: "Actiontec DSL Gateway --- No Internet"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by DLWood on 2006-09-02
OK, I'm a newbie to Umbutu and Linux.  I downloaded and burned the Live CD Dapper Drake 6.06 Distro.  I can boot from it, but my Actiontec GT704-WG Wireless modem/router will not connect to the internet with Umbutu.  It does just fine with Windows XP.

I called my telephone company (TDS-telecom) and they said they didn't support any Linux (is this pitiful or what?).

I called Actiontec and they said this model didn't support Linux.  They have a new model M1424 which does however.

I'm sure there are people out there who have gotten around this problem.  PLEASE let me know what your solution is.  I'm chomping at the bit to use Umbutu to its full ability including internet.  I want to make sure I can access the internet before installing Umbutu permanently on my HD.

I've already tried the ADSLPPPoE routine found here: [https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28dsl%29](https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28dsl%29)  I didn't see any difference.

If it isn't possible to make this work, could I install Umbutu under Windows using VMware and it would work???   Heheh...can you tell I'm really looking for ways to try out Umbutu with internet service??? ;) 

Hope someone can help.....thanks.

Dan

---

### Post by Crooksey on 2006-09-02
Well like it or not, im sure the old company supported linux. Its your ethernet card you need to worry about.

Open a terminal and type "ifconfig" paste the results back here, aslong as your ethernet card works in linux (im sure it will) its just a case of configuring it with the router.

---

### Post by DLWood on 2006-09-02
Here's the output:

eth0      Link encap:Ethernet  HWaddr 00:0C:F1:7B:FE:80
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe7b:fe80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2276 (2.2 KiB)  TX bytes:1938 (1.8 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

I also took a couple of screenshots of some network utilities.  Maybe this will help too.[IMG][IMG]http://img219.imageshack.us/img219/9431/screenshotmk9.png[/IMG][/IMG]
[IMG][IMG]http://img219.imageshack.us/img219/6226/screenshot2to0.png[/IMG][/IMG]

---

### Post by stu41581 on 2006-09-02
hey, 

i just saw your post when i was looking for the same problem i have. this is not the first time i installed ubuntu. in my case, the live cd works fine but after installing i had problem. i searched ubuntu forum for help and i got it to work. now the second time i have to search again for that same post. when i find it i will post the link to it.

hold on, viva ubuntu

---

### Post by SpikeyMike on 2006-09-02
I am having the same problem too, ubuntu was working fine until I reinstalled it, now I can't get it to work either from the live cd or after installation.  ](*,) ](*,) 

would be good if you could find the post again ;)

---

### Post by stu41581 on 2006-09-02
well, i have been looking for that post but i am having hard time locating it.   one thing which i remember where i found the post is that it was reply for a guy who was critical about the instlation problem.

---

### Post by stu41581 on 2006-09-02
well i got my internet to work again. i gusse the problme is two drivers are conflcting after boot up.  i don't know the detail but this fix below did the job for me. try it it will work

+++++++++++++++++++++++
I noticed that there isn't a post for this yet, and many people have been having this problem, so i decided to make one.

The solution to fix this is relatively easy. It's made up of only 2 steps.

First, you need to add dmfe to /etc/modules. To do this you need to open up modules with gedit by typing the following code into a terminal.

Code:

sudo gedit /etc/modules


Then, you need to add "dmfe" to this, without the quotes. Make sure you save.

Finally, you need to blacklist the tulip driver so it wont run at startup. To do this you need to run the following in a terminal.

Code:

sudo gedit /etc/modprobe.d/blacklist


After this is opened, you need to add "blacklist tulip", without the quotations, somewhere in the file. Then save.

After both of these steps have been completed, restart your system, and voila, you now magically have a working ethernet adapter.

I'm sorry if this is hard to understand, as it is my first post, and im fairly new to linux.
Reply With Quote
+++++++++++++++

this is not my just copied it from some other post, i don't know how to link to it

---

### Post by gils0040 on 2006-09-03
with the actiontec modems, make sure that your computer is recieving the correct dns.

---

### Post by SpikeyMike on 2006-09-03
Hi Stu

I am having the same problem although I have an onboard LAN 10/100 Marvell 88EC031 ethernet controller. I am going to try your suggestion to see if it works for me, quick question tho, does it matter where I add the 'dmfe' in sudo gedit /etc/modules or can I just add it anywhere in the file?  Same with the 'blacklist tulip' does it matter where I add it?

Regards

Mikey

---

### Post by SpikeyMike on 2006-09-03
Hi

"I don't believe it"  after spending over a week trying to get my ethernet connection to work, not to mention reinstalling ubuntu a few times I finally got it working, it seems the problem was a wireless NIC in the computer.  I knew this wasn't being recognised by ubuntu but ignored it because I am using an onboard ethernet controller.  Out of curiosity I removed the wireless NIC and the ethernet connection works without having to change any settings.  Seems the card was causing problems even though I wasn't using it. :???: :)

---

### Post by DLWood on 2006-09-03
> **SpikeyMike said:**
> Hi

"I don't believe it"  after spending over a week trying to get my ethernet connection to work, not to mention reinstalling ubuntu a few times I finally got it working, it seems the problem was a wireless NIC in the computer.  I knew this wasn't being recognised by ubuntu but ignored it because I am using an onboard ethernet controller.  Out of curiosity I removed the wireless NIC and the ethernet connection works without having to change any settings.  Seems the card was causing problems even though I wasn't using it. :???: :)As a newbie, how do I "remove the wireless NIC"?

---

### Post by diggity on 2006-09-04
I have the same modem/router. I didn't have any problems with internet, but I had a problem with synaptic (add/remove applications).

I'm not sure what's causing your internet to not work, but from your screenshots, it seems that your ethernet card did pick up an IP address from the router. Try pinging a website by openning a command line
```
ping -c 4 www.google.com
```
If you get a response, your internet connection is working.
If it is working, you might be running into the IPv6 problem with Firefox.
In firefox, go to **about:config** in the address bar. Look for **network.dns.disableIPv6** and make sure the value is **true**
If you are getting connection time out errors from Synaptic (this is the problem I ran into), open up System -> Administration -> Networking
and click on the DNS tab. If you see 192.168.0.1 as a DNS Server, delete it and add your ISPs DNS servers (you can find this information on the Status page of your router.)

HTH

---

### Post by SpikeyMike on 2006-09-04
> **DLWood said:**
> As a newbie, how do I "remove the wireless NIC"?


Hi

As long as your wireless pci is a seperate card you can remove it, you will have to open your computer case and then locate it, it will be at the back of the computer and secured with a screw, remove the screw and then the card.  Hope this helps, let me know.

Regards

Mikey

---

### Post by DLWood on 2006-09-04
diggity,

Thanks for your help.  I did get a response from the ping command.

The ****network.dns.disableIPv6**** was set to false.  I changed it to true and things are now working.  I'm happy to report that I'm now posting this under Ubuntu Live CD and Firefox!!!  Woo Hoo ! ! !  :-D 

I haven't run into any time out errors from Synaptic yet, but for future reference, in case this should arise, how can I get my ISP's DNS servers?  Where is the Status page of my router found?

Interesting, I don't have to disable the IPv6 in Firefox when using Windows XP.

SpikeyMike, thanks for your information.  I guess I don't have a wireless PCI card....all 3 of my PCI slots are empty at the moment.

Thanks again for all who helped.  Now I get to decide what method to use to install Ubuntu on my computer:

1. Dual boot
2. Using VMware with Windows as host and Ubuntu as guest
3. Chucking Windows entirely :-k 


Any suggestions out there for a newbie to Linux/Ubuntu and someone with just average computer skills?

---

### Post by diggity on 2006-09-04
> I haven't run into any time out errors from Synaptic yet, but for future reference, in case this should arise, how can I get my ISP's DNS servers? Where is the Status page of my router found?

In Firefox, go to **[http://192.168.0.1](http://192.168.0.1)** (this is the URL of your router).
Click on the "Status" link. Under the WAN section you should see DNS #1 and DNS #2. These are your ISPs addresses.

BTW, I would suggest Dual Boot at first and move to Chucking Windows. I run Win2K with VMware inside Ubuntu :)  (I'm a web developer and need MSSql)

---

### Post by dionnow on 2006-10-01
Thank you!  I have been having connection issues as well.  Everything worked, Just took forever for pages to get moving... I had always assumed my problem was specific to my DSL modem since everything worked properly with my old cable modem.. Nonetheless Disabling the IP6 in Firefox took care of my problems immediately..

---

