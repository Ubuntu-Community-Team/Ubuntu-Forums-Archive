---
title: "Getting on the internet with a cable connection, is it possible?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by newbietotal on 2010-01-07
Ok, as my name suggests I'm a total newb, sorry.  I installed Ubuntu on a secondary computer and was pleasantly surprised.  I like it.  The only problem that I have is that I cannot get on the internet.  

I contacted my cable provider and indicated that I was trying to get on the net with a Linux OS.  He indicated that, that was not possible.  The cable provider only supports Microsoft and Mac.  Is he right?  If not, what information do I need to connect my computer to the net?  If he is right, is there a special internet service provider I should look into?

I've tried the Ubuntu help button, and it did have a section on getting on the internet but I did not find it helpful.  

Sorry, if this question has been asked a million times.  But can anyone out of the kindness of their heart answer my question?  I would really appreciate it!  Thanks in advance!

---

### Post by Ocxic on 2010-01-07
yes oyu can get on the net, when he said they pn;y support win and mac, he mean't for tech support, so your on your own. save for us, I'm sure we can get u going.

how do u connect to the net?

---

### Post by sgosnell on 2010-01-07
You should be able to just plug in the ethernet cable and be connected.  If that won't work, right-click on the network icon in the panel, select Edit Connection, then click on the Wired tab.  You should see a connection named Auto eth1, which is the default.  Click on Edit.  The dialog which comes up should have the Connect Automatically box at the top checked.  If not, check it, OK out, and see if you get a connection.  The boxes below should have your machine's MAC address and the MTU should be set to automatic.  On the other tabs, you should have the 802.1x security unselected, the IPv4 set to automatic (DHCP), and the IPv6 set to Ignore.

---

### Post by Bartender on 2010-01-07
I know for sure that with Comcast you CANNOT just stick the ethernet cable from the modem into a Linux PC.  You need a router in between.  I'm guessing that may be all that's stopping you.  

If it's a brand new cable installation you may even have to go online at first with a Windows PC, then once the connection has been established you should be OK with a Linux PC behind the router.  Pretty sure that's how Comcast is with a new connection.

---

### Post by Iowan on 2010-01-07
I asked a potential DSL supplier about Linux (since they use MSN as home page) and got a similar answer... I'm using it anyway.

---

### Post by oldfred on 2010-01-07
Three or so years ago I was testing my first Ubuntu and did not have a router and was using Comcast. When I plugged in the Ubu machine it took 20 minutes or more to work as Comcast saw a new MAC address. I then spoofed the MAC address and was immediately able to use either computer. I gave up on all the plugging and then bought a router and the router is still using the MAC address from my old computer.

---

### Post by running_rabbit07 on 2010-01-07
They say that because they are only trained to help you with connection problems on Windows and Mac systems.

---

### Post by oldsoundguy on 2010-01-07
> **Bartender said:**
> I know for sure that with Comcast you CANNOT just stick the ethernet cable from the modem into a Linux PC.  You need a router in between.  I'm guessing that may be all that's stopping you.  

If it's a brand new cable installation you may even have to go online at first with a Windows PC, then once the connection has been established you should be OK with a Linux PC behind the router.  Pretty sure that's how Comcast is with a new connection.

This is incorrect.  I have Comcast and have used Linux on it for the last 3 years.  
Have had units wired through a router and wired direct.  Currently have 5 Linux based computers working on Comcast. (although all are through a router at this time)
But I TEST the router by by passing it and going direct to modem.
The modem firmware is Linux.  Most modems are, as are most routers.
I have had techs come out to service and they sat right down on an Ubuntu computer and did everything they needed to do.  Why?  Because everything is done with a BROWSER.  The platform is of no concern.

To the OP:
PLUG IT IN and give it a shot.  IF your Ethernet card works in Linux, you will be on line.  SIMPLE as that. (re-booting may be required.)
No need to make things more complicated.

---

### Post by Methuselah on 2010-01-07
You said it is a secondary computer.
How is your other computer connected?
If you have a router it should be sufficient to put another cable from your router to the second computer.

---

### Post by newbietotal on 2010-01-08
> **sgosnell said:**
> You should be able to just plug in the ethernet cable and be connected.  If that won't work, right-click on the network icon in the panel, select Edit Connection, then click on the Wired tab.  You should see a connection named Auto eth1, which is the default.  Click on Edit.  The dialog which comes up should have the Connect Automatically box at the top checked.  If not, check it, OK out, and see if you get a connection.  The boxes below should have your machine's MAC address and the MTU should be set to automatic.  On the other tabs, you should have the 802.1x security unselected, the IPv4 set to automatic (DHCP), and the IPv6 set to Ignore.

Ok thanks for the reply.  I did everything indicated, but the problem it appears that for some reason after it connects--very briefly--a message appears that it is disconnecting itself and that I'm working offline.  I've gone into Firefox to verify that it is not on offline mode and it is not.  

Some more information.  I'm using a PC with Ubuntu OS.   I have a laptop and a desktop.  The laptop is my primary computer as I use it for work and school.  The desktop is my secondary computer.  Ubuntu appears to be running fine on my desktop.  I'm currently plugged into the net through my laptop.  I only have one internet connection at home.  I'm trying to get the desktop to go on the net.

I believe the problem comes down to the router issue.  I am willing to buy a router but is there a specific one I should buy?  Also, it would be helpful for me to know why the router is the solution.  Is it because the router acts as a sort of converter box?

Thanks again, for all your time and attention regarding this matter.  I really appreciate all the replies.  I owe you guys a beer.

---

### Post by mikewhatever on 2010-01-08
With problems like that, it's advisable to provide info about your ISP and modem, as well as the type of connection (usb/ethernet). You've mentioned that you connect through the laptop, do you mean ad-hoc setup?
It may also be helpful to search for your specific setup + ISP, in your language. I am not sure a router will solve your problem, but perhaps the ISP's tech support will not refuse to help you with it.

---

### Post by HiImTye on 2010-01-08
what ISP do you use and what brand/model of modem are you using? (the brand will likely be on the front or top and the model on the back or bottom)

---

### Post by newbietotal on 2010-01-08
> **HiImTye said:**
> what ISP do you use and what brand/model of modem are you using? (the brand will likely be on the front or top and the model on the back or bottom)

Charter Communications and the modem is a Motorola.  I'm certain about the modem.  I looked up the ISP provider online through a website that provides your isp information.  Under provider it said "Charter Communications."  

Thanks in advance?

---

### Post by HiImTye on 2010-01-08
> **newbietotal said:**
> Charter Communications and the modem is a Motorola.  I'm certain about the modem.  I looked up the ISP provider online through a website that provides your isp information.  Under provider it said "Charter Communications."  

Thanks in advance?
what model is the motorla

your ISP is whoever you pay your bills to. often smaller companies lease IPs from larger ones so WHOIS queries are less than accurate

---

### Post by mastablasta on 2010-01-08
If you are using two computers and modem does not support that then router is the way to go. Otherwise you might have to connect to Modem and then fiddle with a few setting that are there. Maybe it is set to only one connection?!
 
Anyway i also use a router. I just bought the cheapest one (some chinese stuff i think). works ok and hasn't broken yet. Although it can only handle 5 computers at a time. been using it for over 5 years. Router is like a small computer server often with it's own firewall that routes the connection.
 
Switch would be an even cheaper option since it's only for two computers. Swtich is not so efficient as router and usually has much less settings.

---

### Post by underquark on 2010-01-08
If you get a wirelss router you can run both your desktop and your laptop.  Get connected by using a Windows PC first and make use of their support if there are problems.  Then it pretty much doesn't matter what OS you are running on any subsequent computers plugged into or wirelessley connected via the router as long as you set your home network up correctly since the router is already making the connection to the Internet.  Get the company to help with the connecting-to-the-internet bit and then if you have networking problems there will be plenty of help here.

---

### Post by sgosnell on 2010-01-08
Try opening the network connections again and adding a new wired connection.  Sometimes that works.

---

### Post by running_rabbit07 on 2010-01-08
On must home routers, once connected, you can go to 192.168.1.1 in your web browser and sign in using the factory password, then configure it whatever way you want it.

---

### Post by mikechant on 2010-01-08
If you're actually switching between two PCs by unplugging/plugging them directly into the modem, you may need to reboot the modem when switching over. This would apply regardless of whether the PCs were running Windows, Mac OS or Linux. This is due to the MAC address changing as mentioned by a previous poster.
I'm not saying this is definitely your problem, but the fact that you see the connection occur and then drop immediately could be the modem connecting and then checking and rejecting the MAC address.

I used to have to reboot my cable modem when switching devices until I got a router (a Netgear WGR614, which has been very reliable so far, and cost about £30 sterling).

---

### Post by pricetech on 2010-01-08
The monkeyrola modems used by charter aren't very good, but that's probably not your problem.  Cable modems "marry" themselves to a MAC address.  If you change computers you'll have to reboot the modem to get it to talk to the new computer's MAC.

Your best bet is to get a router.  (not a switch, that won't work)  Any brand name should be OK.

I hate netgear, but not because of their equipment.
Linksys is common and has gotten much better than it used to be since Cisco bought them out.
I never saw a dlink that was worth the trouble of throwing it away.
Allied Tellesyn, if they're still in business, made some pretty good stuff.
Trend makes good stuff at a very reasonable price.

When you get the router, hook it up, power cycle the cable modem, then connect using your winders box.  (your router manufacturer probably favors winders as well)  You'll more than likely encounter a wizard that will walk you through any additional setup.

If your winders box can't find the router to begin with, refresh your IP and try again.

If you need any additional help, let us know.

---

### Post by Bartender on 2010-01-08
Regardless of oldsoundguy's post (# eight) I've dealt with Comcast at 3 different people's houses, and talked to two Comcast reps.  What they told me is that the Comcast infrastructure wants to see a Windows PC at the other end of a new connection.  That means a Windows PC connected directly to the modem.  Once the connection's been established, you've gotten on and off a few times, and the Comcast servers are satisfied that you're not trying to hack the system, you can drop a router in between.  UNPLUG the Comcast modem's power (turning it off is not the same thing) for a couple of minutes, then turn it on, then attach the router and turn it on.  Doesn't really matter what router, any name-brand should be fine.  Once the router comes up to speed (a minute or two) you should be able to plug in a Windows or Linux PC, turn it on, and go online.  I'd want to go online with a Windows PC first just to make sure.

Of course, if you buy a wireless router you'll want to set up security.

---

### Post by running_rabbit07 on 2010-01-08
The OP has already had his Windows machine connected to the net. 

I have never dealt with Comcast, but that is poor business on their part. The modem is supposed to connect to their switch no matter what OS is connected to the router.  What if you have a small business and you are running Red Hat desktops and Debian servers? Would they really require someone to buy a Windows PC just to activate their modem? If so, I would call whichever contractor offered DSL and let them set up the network.

---

### Post by pricetech on 2010-01-08
The OP says he has Charter, not comcrap.  Charter used to have, and may still have, a winders based program they want their installer to run.  It has something to do with the installer getting credit for the install.  (that's how it was explained to me by an installer).  It's not required at all, it's just the "preferred" method, or at least it was.

---

### Post by Bartender on 2010-01-08
> **pricetech said:**
> The OP says he has Charter, not comcrap.

oops, you're right, guess I was fixating on Comcra - er, cast.

---

### Post by lisati on 2010-01-08
> **newbietotal said:**
> 
I contacted my cable provider and indicated that I was trying to get on the net with a Linux OS.  He indicated that, that was not possible.  The cable provider only supports Microsoft and Mac.  Is he right?  
He could have meant that it isn't possible for him to provide support for getting set up with Linux. Many of us here successfully use a Linux-powered machine for our connection. 

Good luck, and I hope that some of the suggestions so far have been helpful.

---

### Post by Bartender on 2010-01-08
> **running_rabbit07 said:**
> I have never dealt with Comcast, but that is poor business on their part.

Six or seven months ago I pulled up at a coffee shop in town that was offering free wi-fi.  Fired up the Linux laptop, got an error message.  I don't remember what it said exactly, but it was clearly a Comcast message and it said I was trying to access their network with an incompatible computer or something to that effect.

---

### Post by Locke_99GS on 2010-01-08
My Compcast cable internet didn't see Windows for the first 6 months I had it. It's internet, it doesn't care about the operating system. When the cable installer did his thing, he plugged the modem into the back of the computer, got onto a website and entered some numbers, asked me what I want my login info to be, tested a few sites for connectivity and left. Aside from him asking how to open a browser, he never mentioned the fact I wasn't using Windows or Mac. I hooked my router up afterwords.

OP: Please paste the output of this command:
```

cat /etc/network/interfaces

```

---

### Post by running_rabbit07 on 2010-01-08
> **Bartender said:**
> Six or seven months ago I pulled up at a coffee shop in town that was offering free wi-fi.  Fired up the Linux laptop, got an error message.  I don't remember what it said exactly, but it was clearly a Comcast message and it said I was trying to access their network with an incompatible computer or something to that effect.

That is effed up. I guess if I ever move to a place that has comcast, I will be sure not to order their services.

---

### Post by Bartender on 2010-01-08
Well, there are now two guys in this thread saying that I'm wrong.  

Actually, come to think of it, I had another experience with CC besides the ones already described.  This was my first.  There's a guy at the bottom of our rural road.  Comcast comes about 1/10 mile up the road, so he had it.  I dropped by with my laptop.  He'd turned off his Comcast because his PC broke, so he called Comcast, they turned it back on, I plugged into his modem, nothing.  No connection.  That was my first experience with Comcast.  I assumed the problem was Ubuntu.  But since then I've conencted to CC numerous times, wired and wireless, as long as a router was in the mix.

So I don't know what the real true answer is, just relating my experiences.

---

### Post by running_rabbit07 on 2010-01-09
I am not saying you are wrong, do not bend my words. I am saying Comcast is wrong and that I will refuse to be a client of theirs, if in fact this is the way they operate. If I were a business owner and had to buy all new servers because an ISP doesn't support non-Windows systems, I would be mad. 

I have friends that are network engineers and they say their company's system will recognize and block anything that doesn't not have the Windows XP OSI stack. But, this is at a private company that does everything possible to keep their network secure not an ISP.

---

### Post by Bartender on 2010-01-09
I wasn't bending your words.  Funny how easily things can be misinterpreted.  I was simply acknowledging that some other folks were not agreeing, and that I could be posting information that wasn't representative of the average Comcast experience.

---

### Post by pricetech on 2010-01-11
> **Bartender said:**
> oops, you're right, guess I was fixating on Comcra - er, cast.

Trust me;  it's "comcrap".  I'm stuck with them here.  Not my decision.  I did have the pleasure of being a thorn in their side until they made it work though.

---

### Post by running_rabbit07 on 2010-01-11
> **pricetech said:**
> Trust me;  it's "comcrap".  I'm stuck with them here.  Not my decision.  I did have the pleasure of being a thorn in their side until they made it work though.

Awesome! I am glad to hear you stood up to them. For them to say what you can and cannot use is total BS.

---

### Post by pricetech on 2010-01-11
> **running_rabbit07 said:**
> Awesome! I am glad to hear you stood up to them. For them to say what you can and cannot use is total BS.

It's easy for me.  I'm an *******.

---

### Post by running_rabbit07 on 2010-01-11
Me too.

---

### Post by silverglade00 on 2010-01-11
> **Bartender said:**
> Regardless of oldsoundguy's post (# eight) I've dealt with Comcast at 3 different people's houses, and talked to two Comcast reps.  What they told me is that the Comcast infrastructure wants to see a Windows PC at the other end of a new connection.  That means a Windows PC connected directly to the modem.

The Comcast guy that brought me a new modem two weeks ago did not care one bit when I handed him my Hackintosh Dell Mini. He said "It's all web based anyway, we don't care what you use." It's not the infrastructure, it's their horrible help desk monkeys that can't handle anything not made by Microsoft. I have been using Comcast for 10 years now. The Windows-only thing is because they want you to mindlessly install their Comcast branded IE version. It's straight-up standard TCP/IP that you get after that. I have run FreeBSD, OSX, Windows 98-7, and about 20 different Linux distros over the years. Comcast doesn't care.

---

