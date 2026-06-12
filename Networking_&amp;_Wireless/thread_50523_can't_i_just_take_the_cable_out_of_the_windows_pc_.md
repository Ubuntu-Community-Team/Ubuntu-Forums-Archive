---
title: "can't i just take the cable out of the windows pc and plug it into the ubuntu one?"
date: 2005-07-20
forum: Networking &amp; Wireless
---

### Post by Rogue Elephant on 2005-07-20
excuse my ignorance, but
for some reason i thought 'ok, ubuntu's running, i have a linux-compatible-provider and -modem... can't i just plug it into the ubuntu box and do the sudo pppoeconfig?'

but i get that error about the access concentrator not responding... what IS an access concentrator... don't worry, i googled it and i probably wont understand you either!

i tried directly connecting the cable in and then through a router i happened to find lying around. i tried copying the static details from the windows box and i tried dhcp.
all sorts of combinations

i could be missing something... like entering the name of the provider somewhere, or configuring the router somehow... ... or how my netmask is 255.255.255.255.0 and it should be 255.0.0.0...

ubuntu recognises my eth0 and when i do run ifconfig it returns the same numbers i entered earlier. and the number of packets increases each time. when i ping my ip there is 0% packet loss. when i ping my gateway (not sure if this is relevant) there is 100% packet loss.

by the way, if there is a way to send the outputs from the laptop to the computer i'm using now without typing them up again, please let me know... i only have usb1 btw.

the laptop is a toshiba satellite 1710cds and the whole ubuntu installation was a success. the modem is a speedtouch 510. the 'router' is a netgear wgr614v2. the connection is a bostream scream ADSL 2.6 MBs. in my resolv.conf this appeared:

search bredbandsbolaget.se
nameserver 10.255.1.66

which is probably a good thing?

i've spent the whole day reading every post under 'networking' and don't think i found any answers. maybe it's something simple... it's just that when it comes to 'setting up broadband' instructions in the manual it just says 'sudo pppoeconf' and i think there are a few people crossing over from windows who just want to know clearly, step-by-step, the things that need to be done in order for this process to go smoothly and to not miss any little things or vital bits of information.

if anyone wants to help, please let me know the outputs required... i'll type them all out if i have to... i gotta get this box connected before uni starts or i'll get my ass kicked for wiping out the owner's xp!

thanks in anticipation...

---

### Post by az on 2005-07-20
I had the same problem once.  I think you need to reset the cable mode so that it knows to listen for a dhcp request (or something like that...)  I do not have a detailed unerstanding. 
I had read that your ISP can be overflown and you have to wait 30 minutes before you can get another lease, but I did not really understand - and that was not the case for me.

---

### Post by BaffledMollusc on 2005-07-20
First I'd like to say that I know practically nothing about networking.  :) 

Still, here's my thought. I found that the Ubuntu was extremely good at automatically configuring my network connection and sorting things out with my router (even with a wifi connection). So, my question is, did you have the network cable plugged in when you installed Ubuntu? Or did you do an installation without internet access and then try and configure network stuff later?

If you haven't already tried, it might be worth being connected during the install and seeing what the installer can come up with.

---

### Post by matthew on 2005-07-20
This may not fit your scenerio, but maybe it will help. I have three different computers. With two of them you can just plug the ethernet cable in and they will work immediately. The third is just picky. Whether it is running Ubuntu as it does today or whether it is running Windows (XP or Me) as it did in a previous life the hardware requires me to do the following EVERY time I plug it in.

1. turn computer on
2. make sure software is still set to receive DHCP
3. plug ethernet cable in
4. unplug power to modem/router, count to 10, power back up (this resets the modem)
5.  watch as my computer that said just seconds ago that there was nothing plugged in to the ethernet port suddenly finds a signal and works.

Sometimes I have had to do this 2 or even 3 times to get it to work. Needless to say, this one doesn't get plugged in to the internet much. It's an old Compaq laptop (PIII 800mHz) that has been relegated mainly to use by my three year old for TuxPaint and gcompris games.

Anyway, try resetting any routers/cable or high speed internet modems and so on after booting the computer starting in order from the wall to the computer. Reboot the computer as step 6 if it doesn't work as shown. Try this a few times and see what happens. Worst case scenerio, you waste a few minutes, but you eliminate one possibility.

---

### Post by Rogue Elephant on 2005-07-21
it was a good idea and worth the try matthew, but unfortunately not successful... maybe after a few shots... and azz, i'm not really sure how to reset the cable mode. all i can see is the power plug and the modem going into the telephone jack in the wall... not sure whether there is a control box somewhere if that's how i'm supposed to reset it? but i'm actually gonna try BM's idea (which actually crossed my mind earlier) to re-install with the modem connected.
when i had xp running, it wouldn't connect to the internet unless the ethernet was connected on boot (probably common, but that's what gave me the same idea).
well, here goes...

---

### Post by MikeyXX on 2005-07-21
[QUOTE=Rogue Elephant]it was a good idea and worth the try matthew, but unfortunately not successful... maybe after a few shots... and azz, i'm not really sure how to reset the cable mode. all i can see is the power plug and the modem going into the telephone jack in the wall... not sure whether there is a control box somewhere if that's how i'm supposed to reset it? but i'm actually gonna try BM's idea (which actually crossed my mind earlier) to re-install with the modem connected.
when i had xp running, it wouldn't connect to the internet unless the ethernet was connected on boot (probably common, but that's what gave me the same idea).
well, here goes...[/QUOTE]
 I may not really be getting what your asking. But if you aren't obtaining an IP it is a common problem on PPOE and highspeed connections. The MAC address is registered with the DHCP server. Normally a proper shutdown and then a bootup of a new system (different MAC address if it's a different NIC) will be smooth. However, some companies have a poor implementation of DHCP OR for security they require you to call in and ask them to release the MAC address. Either way, try plugging your Linux box in and give them a call. They probably don't support Linux, but they don't have to. You can just pretend your running XP.

---

### Post by Rogue Elephant on 2005-07-21
[QUOTE=MikeyXX]I may not really be getting what your asking. But if you aren't obtaining an IP it is a common problem on PPOE and highspeed connections. The MAC address is registered with the DHCP server. Normally a proper shutdown and then a bootup of a new system (different MAC address if it's a different NIC) will be smooth. However, some companies have a poor implementation of DHCP OR for security they require you to call in and ask them to release the MAC address. Either way, try plugging your Linux box in and give them a call. They probably don't support Linux, but they don't have to. You can just pretend your running XP.[/QUOTE]
 well, first i would like to say thanks for the idea, baffled mollusc... i knew it was going to be good, when, during installation it said 'configuring DHCP',' network autoconfig success' and then gave me the host name:activation... when installation was complete, i clicked on firefox and the debian.org link and at least it took me to the broadband company's site for activation.

i haven't done anything yet as it might mess it up for the main home computer or something... must check that out. also, does the above mean that i don't have to sudo pppoeconfig anymore? anyway, you're probably right, mikeyxx... i might have to inform the provider or something... will check out the site again, but it's in swedish... i don't want to do anything like change the service for ubuntu and then the windows machine will suffer or something (is something like this possible?) also, do companies have something against linux boxes? maybe if they don't support it, they just don't know how to help people if things go wrong. anyway our company does.

well, thanks all... i think the problem is fixed and i have a feeling just having the modem connected on installation might cure a few of the other problems in this networking category....

---

### Post by Rogue Elephant on 2005-07-21
well, the pppoeconf results are the same... the old access concentrator not responding... so maybe that involves activating whatever with on the provider's site... so i went there and it said that i have plugged the ethernet cable into the wrong jack. (1x which is apparently used for or reserved for 'IP telefoni' [however that translates]). and it uses a diagram of a router with a green arrow pointing to jack '2x', saying using nuber 2,3 or 4 is the way to go... 'turn of your computer for 30 minutes and try again'. 

which is annoying because the modem was directly connected to the only ethernet jack on the laptop. no router. so what do you do there? then i thought i'd use the router.. but it doesn't work. i'm not sure how they work, but i think it you can test it by using between the modem and the computer that has a working connection... it appears to be connected, but can't find any websites. strange... and same thing with the ubuntu box. 

one other thing... i haven't go the power supply for the router. it is a 5Volt at 2Amps but i'm using a discman adapter which is 4.5Volts and 500 milliamps. would that have anything to do with it even if the router appears to be funtioning properly (all the lights working correctly etc.).

should i insert the other ethernet card too and have an eth0 and an eth1 and use the second one? has anyone heard of not using the first jack before?

---

### Post by Rogue Elephant on 2005-07-23
called up the provider.

1. on a static-only deal, so re-entered the static IPs etc.
2. the company that bought the old company had two new DNS's for me.
3. commented out the resolv.conf re-writer.

takes a very long time to search for sites and then can't find them.

pppoesonf still gives me the access concentrator message.

so i'm doing the usual routine of unplugging the modem (yes it helps thanks matthew) and this time i'm going to leave the computer and modem unplugged for half an hour (like that's going to help).

anymore ideas? anything to do with how the computer sets up the network on installation with dhcp? 

operator said it has nothing to do with MAC/NIC, but also said she didn't know how to 'repair a connection with linux'.

any special considerations for static connections?

---

### Post by varunus on 2005-07-23
I'm a little confused...your connection is static?  Then why did it work earlier when you had it on DHCP (which is automatic configuration)?

If it wants you to activate, this means that your computer is being seen as a different computer than the other one (which makes sense) and the company wants to keep track of which MAC address (unique to each computer) is connected.  So you may have to reactivate when you switch, or see if they let you put two computers on their activation.  (That's what I do with insight broadband, same with AT&T i think; you just connect and have to register the computer's MAC address).

To "repair" a connection in linux, you need to open up a terminal and type the following:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

I'm still not sure if you're static or DHCP, though, so if you're static, get rid of that last line above.

---

### Post by Rogue Elephant on 2005-07-23
[QUOTE=varunus]I'm a little confused...your connection is static?  Then why did it work earlier when you had it on DHCP (which is automatic configuration)?

If it wants you to activate, this means that your computer is being seen as a different computer than the other one (which makes sense) and the company wants to keep track of which MAC address (unique to each computer) is connected.  So you may have to reactivate when you switch, or see if they let you put two computers on their activation.  (That's what I do with insight broadband, same with AT&T i think; you just connect and have to register the computer's MAC address).

To "repair" a connection in linux, you need to open up a terminal and type the following:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

I'm still not sure if you're static or DHCP, though, so if you're static, get rid of that last line above.[/QUOTE]
 well, the main family computer is static. and maybe that was an excuse for the operator to tell me that the line is for static only. i never really got a connection at all, as such, meaning i didn't ever find any 'real' web pages and neither static or dynamic IP's helped locate the access concentrator with pppoeconf.

all i got was that certain DNS and domain name (somehow [is this possible without a connection?]). apparently it was a useless one which only told me that my cable was not in the right port, incorrectly assuming that i was using the company's 'other' style of modem. which looks like a router. i had the modem directly connected. plus i couldn't find that web page on the net on the normal computer.

but i guess it still means that page came from somewhere into my supposedly unconnected laptop. even if it is stored in some hardware or anywhere on this side of the net (imagination going wild). but yes, i was confused too, about the dhcp/static thing.

the thing is, isn't that dynamic address supposed to change for each boot? i don't think it did, even after i commented out the 'DNS rewriting code'.

well, thanks for showing the 'repair' code. tried it, but didn't solve the problem, although it's another thing on the checklist to do while i'm trying to sort this out. 

i also changed the host name thinking that if i left it at 'activation', the computer would draw some connection to the dhcp thing it used on installation.

is there anything else in the system (or more code that needs to be commented out) that is also 'running the pppoeconf process which controls the modem?) maybe it is somthing to do with the provider and i need to ask them to perform the 'flush' thing mentioned earlier.

do i need to enter certain things like the domain to search for servers, a domain name, a location or to delete anything under 'hosts'?

would it happen to have anything to do with 'PCI: cannot allocate resource region 4 of device' (boot) (stab in the dark).

i might just have to ring them again tomorrow...

---

### Post by varunus on 2005-07-24
Hmm...I think I see.  I don't think ubuntu has any built in pages though, so you may have gotten something from the company's website...This seems like a very strange internet service, for my cable modem I just plug in, register at the web page that pops up, and go.  (I have a router on it now, so no problems occur.)

Lets try something else...Boot up into your windows box, and open up the Network Connections control panel.  Right click the connection, and choose properties; then scroll down to TCP/IP and click properties (I think, or it might be options) again.  What settings are listed there?

EDIT: We might even be able to get around the registering thing by faking the MAC address of your computer (in other words, making the company think its the windows PC).  I think.  We'll have to see how you connect...

---

### Post by Rogue Elephant on 2005-07-25
it was definitely the company's own page but it's not a typical web page. 

anyway, thanks for reminding me to check the xp for the dns's IT's using - two different ones to those the operator gave me. so i plugged them in, but alas, the same result.

just can't get pass this access concentrator thing. maybe it IS something to do with the MAC address or something... is this something i can steal from the xp machine?
meaning 'is it possible' (not 'is it moral').

when it is scanning (pppoeconf), i think it says 'success' in the quick flash of a message after a scan.

so was it something other than dns's you wanted me to look for in the properties?

---

### Post by varunus on 2005-07-27
I was thinking you should look up how the IP address is configured in windows, is it set to automatic?  If not, copy everything over from the TCP/IP section, then try pppoeconf...

---

### Post by Rogue Elephant on 2005-07-27
in the first set of options, it says it doesn't get the ip or dns automatically and has all the details typed in, which i typed into the ubuntu box.

when i go into advanced, it says (under standard gateway) the gateway number and then under the next collumn (mått in swedish, which means measure or felt, so i don't really know what it says on english boxes - can someone tell me?) it says automatic. maybe i have to set the equivalent property to automatic in ubuntu?

then in the box below that one, it has the little box checked at automatic 'mått'. measurement? maybe meaning configuration...

i went deeper and here are a few of the options the computer has, i hope you can pin-point the problem! (once again, thanks for your time) i am just trying to translate the swedish, so you may know the exact terminology and a clearer picture.

checked options:

add to primary and connection-specific DNS suffix.

add to superior suffix for the primary DNS suffix.

register this connection address in DNS.

use LMHOSTS file.

use netBIOS options from the DHCP. if a static IP is used or if DHCP server doesn't indicate netBIOS options, should you activate netBIOS over TCP/IP.

TCP/IP filtering chosen.

activate IEEE 802.1 authentication for this network.

EAP type: smartcard or another certificate.
authenticate as computer when info about computer is available.

does ubuntu have these options??

cheers

---

### Post by crispingatiesa on 2005-07-27
Dude, I'm a little confused, you mentioned that you'r modem is connected to a telephone jack?

If yes then what you have is DSL and I'm not quite sure how to help you at this time.

But if what you have is cable, please, answer this:

Do you have more than one computer using the same connection before?

If yes, was using windows connection sharing or a router?

If it was a router you shouldn't have a problem configuring Ubuntu, at least the problem is not before the box.

If not,  I don't know the kind of service or setup U have but in a cable service (and it should apply to DSL as well)  the modem mac address is the important one (is the only device that your ISP should see anyways. So, it shouldn't be a MAC problem or your ISP.

Please, could you describe the phisical setup in terms of what connects to what before and after?

---

### Post by Rogue Elephant on 2005-07-28
okay. it's dsl. the phone jack in the wall is connected to the dsl socket on the modem. and then there's the power supply and the ethernet cable attatched to the computer. just those three wires. 

another laptop has been connected before directly to this connection and through a wireless router. i've been trying to use this router without the wireless thing and i was just told i couldn't. only things is, i can't find the little card thing or even power supply. apparently i need to install special drivers too. i know nothing about routers.

anyway, it should work being directly connected. i mean, why would it work on one computer and not the other? all you would have to do is find all the connection details in one and transfer them to the other, right? well, that's how my 'newbie' mind works, so i'm trying to find all the connection details and see if i can even apply them in ubuntu. 

i don't know if it has all these options and if they can be configured manually by manipulating some code. i'm also struggling to read everything in swedish. it delays the troubleshooting.

so, it's dsl. and yes, there have been other setups here, but the instance where a router was used was before a virus killed the computer and we had to start all over again.

and it's just a simple phonesocket-modem-computer eth. and it can be unplugged and plugged in (eth cable) at anytime and it just picks up from where it was last left.

with the ubuntu, i have to reset the modem each time, reboot with the cable in, etc... and i just can't configure pppoeconfig. that's the bit that annoys me. what else is using this process? is it something to do with the fact i have another inbuilt modem in the laptop?

i'm running out of ideas and because no-one here can put their finger on it yet, it's probably some tiny little stupid mistake of mine... but i don't even know the basics. i just need to know all the reasons that would get in the way of this ubuntu box not just connecting as soon as the ethernet  cable is in.

first, you have to have all the numbers right... addresses.
then you have to pppoeconfig... this is where nothing happens and there is relatively nothing much about this access concentrator error either in here or on google or debian. no details like "ok... if it cannot locate your access concentrator, here are all the possible reasons for this" so then i could go through them one by one.

i know, asking too much but that's how i normally solve computer problems. with google and creative search queries.

anyway, i'm rambling, but thats the next lot of info to work with.

but i'm thinking, maybe it's not really worth the hassle, because when we do move to the study location, i will be connecting there. maybe there wont be the same hassles?  i guess i'm worried that maybe there will, and there, i wont have another pc to search for answers.

besides, it's been a while since my last reinstallation. maybe i should just do that with all the new figures. 

one more thing on that note... when it's doing the autoconfiguration ( installing with eth cable in ) it uses dhcp... is that the only way it autoconfigures?

---

### Post by varunus on 2005-07-28
**Settings:**
Hm...I'll have to look into your settings...it seems you're not actually set to static on that computer, so your ubuntu machine should be set to "DHCP" in the ethernet properties box.  You can copy over the DNS's into the Networking Administration Tool in GNOME, and also copy over the domain into the "search domains" box in GNOME.  If this isn't giving you internet access, then the problem has to be that your company only wants "registered" computers on the network, and you should get an option to register your new computer when you plug in the cable and open a web browser.

**If you're willing to use/buy a router:**
Using a router would be the easiest solution, actually.  Your ISP would probably be knowledgeable on how to configure a router, so if you just let them tell you how to do that, everything will work.  You said you had a wireless router on the connection before; if you have that router hanging around and it has the option to connect some wired computers to it too, then you dont have to do *any* configuration.  You should just set up the router just like you did so that the laptop works, plug in your computer, and choose "DHCP" (Autoconfiguration) in ubuntu.  Everything will just work like magic.

Even if you don't have a router, if you're willing to spend $15 after mail in rebate(and are in the US) you could get [this](http://www.newegg.com/Product/Product.asp?Item=N82E16833129225) guy.  I'm sure you might even be able to find one for cheaper; I've seen Best Buy have Sunday deals with wireless routers on sale for $15.

What do you mean you were told you couldn't use a router?

EDIT: Typos.

---

### Post by woedend on 2005-07-28
ive worked for 2 internet companies so I can shed some light on one end, while it looks like varunus is able to give you everything you need on the computer side.  With my first company, you could only have one device registered on the modem.  So if you switched computers, or added a router, etc etc, you had to call and let us update that.  With my current company, its a little more automated, just have to 'powercycle' the modem...that is - unplug it for 30 seconds and replug.  To do a full hardware reset on most modems is unplugged for 5 minutes.  Installing a router is not supported by any ISP i've worked for or seen.  They let you use one, but won't tell you how.  This would be your easiest solution.  This way, the modem's destination device is always the router(no powercycling!), and you can set the computers to use DHCP so that the IP address is assigned by the router(192.168.1.x normally).  And you wouldn't have to switch out cables so many times.  To access the internals of your modem to do  a manual reset, in any browser you can typically surf to '192.168.100.1', routers are normally '192.168.1.1' but the third range(1 in this case), seems to vary much more throughout.

---

### Post by KLineD on 2005-07-28
I had a similar problem before.

I was on cable and it got it's address by DHCP. Later I added a second computer and a router to share the connection, the router was configured to give ips automatically but with no internet (just for internal networking) and if you wanted a way to the internet you just needed to configure the ip, etc manually.

Anyway, then I got DSL and tried to configure it with ubuntu with no luck until I realized that the DSL modem autodialed the ISP and I was trying to set it up through the router giving it my username/password. 

In the process of troubleshooting I directly conected the DSL modem to the ubuntu machine and using DHCP I got internet, later I plugged the router and configured my static ip. My other PCs (running windows) could get to the internet just fine, but not the ubuntu machine. It turns out that in /etc/resol.conf the nameserver was changed when the machine got configured with DHCP.

My advice: check your other PC for your ip/nameserver and make sure (using ifconfig and seeing resolve.conf) that it matches.

---

### Post by varunus on 2005-07-28
[QUOTE=woedend]ive worked for 2 internet companies so I can shed some light on one end, while it looks like varunus is able to give you everything you need on the computer side.  With my first company, you could only have one device registered on the modem.  So if you switched computers, or added a router, etc etc, you had to call and let us update that.  With my current company, its a little more automated, just have to 'powercycle' the modem...that is - unplug it for 30 seconds and replug.  To do a full hardware reset on most modems is unplugged for 5 minutes.  Installing a router is not supported by any ISP i've worked for or seen.  They let you use one, but won't tell you how.  This would be your easiest solution.  This way, the modem's destination device is always the router(no powercycling!), and you can set the computers to use DHCP so that the IP address is assigned by the router(192.168.1.x normally).  And you wouldn't have to switch out cables so many times.  To access the internals of your modem to do  a manual reset, in any browser you can typically surf to '192.168.100.1', routers are normally '192.168.1.1' but the third range(1 in this case), seems to vary much more throughout.[/QUOTE]

I guess I've been spoiled by Insight Broadband (the cable internet provider here).  They're really nice; only a couple of times over the 5 years I've been with them has the net gone out, and each time when I called they had a believable explanation.  (And they had it back when they said they would!)  They also have information on their website on how to configure routers (with info for different brands, even), game consoles, and a bunch of other networking stuff.

---

### Post by woedend on 2005-07-28
[QUOTE=varunus]I guess I've been spoiled by Insight Broadband (the cable internet provider here).  They're really nice; only a couple of times over the 5 years I've been with them has the net gone out, and each time when I called they had a believable explanation.  (And they had it back when they said they would!)  They also have information on their website on how to configure routers (with info for different brands, even), game consoles, and a bunch of other networking stuff.[/QUOTE]
 insight is the provider here as well(louisville) and was the 'company a' in my example.  They have great connectivity, terrible support.  I pay 65/mo for 6 mbps down, 512 up.  AT any given time i'd most likely be grabbing about 1.2 mbps down... been so for 2 or 3 months, yet every time I call they are 'working on it'.  There system of having to install software or else call to switch from router to computer, or even change out routers...well, sucks.  I do, however, have a good tip for you that they generally don't let people know..and as a matter of fact I had forgotten about it since my router does work fine now.  12.223.2.8(i think, it may be 8.2 or 8.3), gives you the option to change devices, naturally as long as said computer is somewhere in the mix.

---

### Post by varunus on 2005-07-29
Insight hasn't been good to you?  Wow...That's strange.  I've never had problems when I called them, they were usually helpful...And they documented their method of registering computers, and how to do it on their website in the "Member services" section.  (The register page comes up automatically if you open a web browser on a non-registered computer, and I set up my router following the instructions on their website to make sure it would work.)

Are we talking about the same insight?  Its strange that it would be so bad in Kentucky but so nice in Indiana...
[http://www.insightbb.com/](http://www.insightbb.com/)

---

### Post by woedend on 2005-07-29
yes, same insight indeed.  I do like the service as a whole, I don't think i've had an outage in 2 years or so that i've known of.  At my old house, the service was fast as could be on the basic plan, which at the time was 45.00 a month.  That was when they first came here, I was originally with @home.net, who they bought out or took over one.  It's this new neighborhood i've moved into.  The base price went down to 30$ a month, which was great...but my download speeds would get at low as 300 kbps and online gaming(through xbox, that is) was impossible because of the latency associated with.  I figured i may get more priority by getting 6 mpbs down, but does not seem to be the case.  I even had the opportunity to talk with the VP, whose son I work with.  He was the only one, out of the 20 people i've talked with, who could give me a straight answer, although it in itself was not so promising.  They do however, offer me partial credit to the bill, which in itself is funny.  They say "well it's only slow in our peak hours, 5 pm to 12 am".  This answer stuns me because I get home from work at 6 pm, usually in bed by 12...when exactly am I to experience "high speed?". This credit, however, does not matter, as I explain to them that I'm not complaining for money, i'm complaining so I can use the internet!   That answer, by the way, was that insight is contracting out their server upgrades.  Something to do with waiting for the bid to end and equipment.  I do not badmouth the company as a whole, as I'd always loved it until I moved which put me in a different area.  I'm glad you are pleased with yours.

---

### Post by Rogue Elephant on 2005-08-05
haven't done much with the ubuntu laptop yet. waiting to move into the new place.

but did put together an old pentium and installed xp on it. all i had to do was configure the network by clicking in a box that said 'connect to a dsl modem that is always online' (don't even know if i had to do that) and then put in all the static details. connected immediately.

---

### Post by dude2425 on 2005-08-05
I'm actually living here in Lexington and use InsightBB also. What I had to do is set the roughter and modem up on my dad's PC, who is running windows, and install the software they gave me on it. It then allows me to use the internet through the router. For some odd reason, insight requires you to use their software and use an account number unlike all the other providers out there. It was much easyer when I used Charter in California. Also insight is slower than hell sometimes, (but charter cut me off at 11). We use Vonage too, and if the net is slow, we sometimes get cut off when we're talking on the phone. We just bought a brand new Linksys Gaming Router because we thought it was our bottleneck. We then spent 3 hours on hold with insight trying to ask what the hell is going on. That's 3 hours I could have had downloading through bittorrent or 3 hours I could have spent talking long distance with my friend's in CA, or 3 hours I could have spent making the perfect sandwich. Damn, I better rap this up, I'm getting hungry.

I can not get broadband internet here without being forced to use their cable TV. If it werent for that, I would be watching 100% digital HD satalite with Dish Network by now.

Sorry if I'm straying a little off topic. I think the insight here in KY is a scam, or some MS junkies idea of a joke. I am downloading of a reletively fast server right now, at 58 KB/s. With charter, that exact same server I could have gotten 412 KB/s. With insight, I got the 4Mb/s deal, with Charter it only took the 3Mb/s deal to get speeds like that.

I am now wondering why I'm complaining in a topic that isn't mine in the Ubuntu Forums and not directly to insight themselfs. I must be bored.

---

### Post by woedend on 2005-08-05
dude - I, in a way, agree with you.  What I do like about Insight is the uptime, and when  I do have a problem they are out here ASAP.  With charter most of our work is contracted out, with people having to wait as long as 2 weeks in some markets for a simple line problem.  But, I, like you, have slow speeds most of the time...they kinda blow me off while still heavily advertising in my area...an area theyve admitted to me is already overloaded...should be fun.  Anyhow, last time I called with slow speed they told me to go around the router...and to run their software that you mentioned.  I told them I wasn't running the software because I do not have windows...which is when he gave me that website.  12.223.2.8

---

### Post by dude2425 on 2005-08-05
Ah, I recognise that url, I disabled NAT on my neighbors router to get some new games and stuff with BT when I was waiting for the guy to come and hook our internet up in a week. When I disabled it, I saw that in my network configuration thing, and decided to see what it was all about. I registered and didn't tell the rest of my family about how to get by it, and I was the only one who could connect to "belkin54g"

I knew it had to be something. My family thought the neighbors caught us and cut us off. They still have no clue how I was able to connect easily.
Their still running an unprotected AP. I should find out who it was and tell them to lock it down or something. Maybe. >;-)

---

