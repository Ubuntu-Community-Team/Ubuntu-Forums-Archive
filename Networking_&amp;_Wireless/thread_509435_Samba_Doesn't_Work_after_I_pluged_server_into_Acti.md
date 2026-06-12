---
title: "Samba Doesn't Work after I pluged server into Actiontech Router from my Belkin Router"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by mdsypr on 2007-07-25
Board,

I am a self professed computer nerd from a windows perspective for a LONG time and tried to learn Linux over the years but nothing clicked until Ubuntu came around so thanks.

Basically I had my Ubuntu 7.04 server sharing my files with my laptop (when I had the sever plugged into the wireless router).  Last night I plugged the server into my FIOS Actiontech router directly and now I can't see the server, share a thing or print with CUPS.

I am sure it has something to do with the way the computer is plugged in but I don't know enought about domains, etc to fix it.  I need the server plugged DIRECTLY into the Actiontech so I need to know how to fix this issue.

Can someone help?  I am no expert on the command line I prefer GUI but I still don't understand how both computers can't read anything from eachother.

My laptop runs XP wirelessly to my Belkin Router that also plugs into my Actiontech router ... I had my server setup to share files, got the print server to work, even accessed it remote with a VCN client and now trying to also hit it with FTP (thus the reason to plug directly into the Actiontech Router) but now I can't do the basic things.

How can I fix this Samba issue and make both boxes point to eachother?

I have ensures I set-up my account on samba, even reset the password ... I ever stopped the service, reloaded and restarted and still nothing.  I know it has something to do with DNS but I am clueless.

A newbie to Ubuntu would LOVE to have some help, I do love the product and would like to toss my XP out the window but it shouldn't be this hard.

Thanks
Mike

---

### Post by guilly on 2007-07-25
Please disreguard if this has already been checked, but do you have the proper ports opened on your other router?

have you checked if both p.c's can ping each other accross both networks? maybe it's moer than a DNS issue if they can't?

one more thing correct me if i'm wrong but i believe router to router connection requires a cross over cable does it not?

---

### Post by mdsypr on 2007-07-25
Gulley.

Thanks fro the reply .... I Actiontech router has 4 ports just like any normal Linksys Wireless Router.  I simply plugged my new Belkin Wireless G router into the Actiontech and it works great.  Originally I had my Ubuntu Server plugged into the Belkin so I guess since it was in there and I connected wirelessly with my XP laptop it saw it no problem. 

Now I am plugged into the Actiontech router, my Ubuntu server I mean and now I can't see my server in Network Neighborhood in XP or on the Ubuntu box.

Your question about ports, I am not sure I know enough to answer ... I do know the Actiontech automatically blocks all ports so could that be it?  Do I need to port forward 80 from the Actiontech to the Belkin Router so they can talk?

I just don't know, can someone else give their 2 cents?

Thanks,
Mike

---

### Post by guilly on 2007-07-25
ok well first things first can the two computers communicate in any way, By communicating can you do a simple test by opening a command prompt on your Windows p.c and typing ping [ip address oflinux server]

if you get a successfull reply then we know the two p.c can successfully communicate accross the network.

try that and post your reply 

thanks

---

### Post by mdsypr on 2007-07-25
Gully,

Wow what a quick response ... I am at work now and I will try that when I get home but for now lets assume they can't because since I did that both file share and CUPS don't work at all and I can't see either machine on either network ... that much I know for sure.

What do you recommend?  I am sure it has to do with Network settings but again I am not smart enough to figure it out.  I do know I tried to set-up the printer in XP (as CUPS recommended) with the IP address and it didn't find it at all.

Please help.
Mike

---

### Post by guilly on 2007-07-25
if the ping fails. the next thing i would suggest is to make sure both p.c's can ping each others gateways... i'm assuming your linux's gateway will be something like 192.168.1.1, you can easily figure this out by typing ipconfig in a command prompt and i believe ifconfig in linux should give you similiar results but don't quote me on that since i'm quite the linux noob as well!!!

if both p.c's can reach there Default gateways then we know the problem is related to the communication between the two routers. 

i suppose you can always just simply try and browse the net from each p.cs if successfull then obviously then can leave the network hehe, sorry for the big explanation!!!

---

### Post by mdsypr on 2007-07-25
Gully,

Again thanks for the quick response ... well I can hit the net on both PC's so if you say that isn't a network problem then OK, I am willing to try anything.

If the router is blocking all ports and my Belkin is wired to the Actiontech router then wouldn't that explain why I can't see the machine on either network?

Do I need to port forward? If so from the Actiontech router or the Ubunto Server?  If so what ports?

Like you said I think since the sever is plugged into the Actiontech and the belkin as well the router is causing something to not connect.

I am really at a loss here, I am leaving the office now and will plug in and try when I get home.

Am I right or something else is off?

Thanks,
Mike

---

### Post by guilly on 2007-07-25
Mike, ya your on the right track if both p.c's can get onto the net then traffic is defenetly being passed thru properly between both routers. So the next step is the port and also you may need to configure your firewalls... the ports that you will need to open are 137 138 139 i'm not 100% positive which protocol it uses but to be on the safe side open it for UDP and TCP.

now to open the ports you will need to play around with the settings inside your routers firmware. usualy if you open up your browser you can access the firmware by typing in the gateway address into your browser. For example for linksys you will type in 192.168.1.1 then it will prompt you for a username and pass. if you've never done this before then mostlikely your linksys is still configured with default settings so the user and pass will be admin admin.... as for your other router sorry can't ya much on that as i have no experience but i'm sure a quick google search will tell you all the rest....

your going ot need to do the same for your firewalls on each p.c if you have any configured

p.s your going to need to restart the samba server once everything is done simply type sudo /etc/init.d/samba restart!!!

---

### Post by mdsypr on 2007-07-25
Gully,

Thanks again ... well in Ubuntu I am trying to PING my laptop and Belkin wirless router and nothing is working so obviously Samba wont work.

I just don't fully understand the router confg ... I have both the Ubuntu Server and the Belkin Wireless Router plugged into the Actiontech router.

Do I go into the Actiontech router and port forward those ports you suggested to both the Server and the Belkin?  I dont think that makes sense because both can access the Internet, the Belkin is not getting through the Actiontech to connect with the Belkin so do I go into the Action tech to prt foward or the Belkin?

I am familiar with Router setups and I can access both but I don't know what to do.

Do I put the Belkin in the DMZ zone through the Actiontech?  Will that allow all requests to access the router and thus any computer connected to it?

Need help.
Thanks,
Mike

---

### Post by mdsypr on 2007-07-25
Ok I can now ping the Ubuntu server from my XP laptop.  What I did was enable Port Triggering so anything than comes through any port is opened incomming or outgoing.  

But that was only half of it, I am guessing I have to do something similar to the Belkin but I see nothing for port triggering.

Am I getting hot?

Mike

---

### Post by guilly on 2007-07-25
hey mike,

im not too familiar with port triggering, my networking skills are a little rusty since i've jumped into the dark side :\, but have you tried to simply open those ports i mentioned on both of the routers? do both your p.c's have static ips. might be a good idea for testing purposes to set that for now then play around with that later on. 

How about firewalls? anything set up there?

---

### Post by mdsypr on 2007-07-25
Gully,

I disabled the firewall on the Belkin and thought that might work but it doesn't work.

So now I am completely lost, I can ping from the XP laptop but whatever I do to the Actiontech router or the Belkin router I still can't ping to the XP laptop from the Ubunto server.

What is going on here?  Why is this so friggin hard? You wonder why no one wants to use Linux, my friends would say I am a computer genious but I can't get simple file share working.

Extremely frustrating.  Anyone help me?

Mike

---

### Post by mdsypr on 2007-07-25
I dont know if this will help anything but here are the settings of my XP Laptop and my server

Ubuntu Desktopr 7.04 - connected directly into my Verizon Actiontech Router.
IP: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.255

XP Laptop - connected directly into my BELKIN Router which is connected directly into my Verizon Actiontech
IP: 192.168.201.4
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.201.1

Now I enabled port triggering on the Actiontech and I now I can ping the UBUNTU from my XP laptop but not the other way around.  I still can't ping the XP from UBUNTU.

I tried to add the BELKIN ROUTER to the DMZ figuring it would let all data in but it gave me an error message that it wasn't associated with any valid LAN.

I did turn off the Firewall on the BELKIN and I thiought that would do it, but no.  I had to change the IP of the Belkin because that and the Actiontech were both 192.168.1.1,

Anyone have any ideas?  I know it has something to do with the gateway I am guessing but I don't know for sure.

Mike

---

### Post by guilly on 2007-07-26
Hey Mike, you must be getting closer... I'm not too familiar with port triggering but from what i read on wikipedia that should work. Did you or were you able to enable port forwarding on both routers? if so you'll see that you will need to specify to which host you want to enable that "port" too. That's why i suggested to use static ips for now.... try that and let me know. One more thing which port are you using to plug the actiontech router into your Belkin ?

---

### Post by mdsypr on 2007-07-26
Gully,

On the Actiontech router I am forwarding all ports and on the BELKIN I cant find the port forwarding on it so I have to find that out.

Just did some reading and wouldn't this make sense?

My Actiontech router ip is 192.168.1.1  .... my Belkin Router (which I changed) is 192.168.201.1.  By doing this aren't both computers confused because in essence I created two networks?

If I simply change the Belkin router from 192.168.201.1 to 192.168.1.100 or something like that wouldn't they be able to talk ont he same network?

And wouldn't I have to make sure that the defalut gateways for both machines = the Actiontech Router 192.168.1.1?

I am learning alot but again really frustrating.

Any help guys?
Mike

---

### Post by guilly on 2007-07-26
changing the ip of your belkin to 192.168.1.X with a subnet mask of 255.255.255.0
could maybe make a difference, however if you can successfully ping i'm still leaning towards it being a port issue.

As for setting the hole default gateway you want both p.c's to be pointing to there sepereate DG. that's the hole idea behind a router, it routes things for you hehe... so by telling the p.c ok here is your default gateway if the router that is directly connected to that p.c does not know where to send a particular "message" it checks with the guy next to him meaning the other router that is directly connected to him, then if that router knows where this "message" needs to go he says ya i knwo where that network is i''ll take the message and make sure it's delivered...

i hope i'm not confusing you too much with this explanation just thoguth i'd give you a brief over view of how the process works...

another thing mayeb check on Belkins website maybe that particular model dosen't support port forwarding???

---

### Post by rickyjones on 2007-07-26
OK, lets see if I can understand this.

```


--------------------
      Internet
--------------------
             |
             |
     ------------
        Actiontek Router (zone A)
     ------------
             |
             |
     ------------
        Belkin Router (wifi) (zone B)
     ------------


```

Your server is in zone A right now and your workstation (XP) is in zone B, correct?

If so, then you have two routers working. By default it will be difficult to get SAMBA traffic flowing between the two zones - it's a hardware firewall.

What you can try doing is disable the DHCP server on the Belkin router and take a CAT5 cable from one of the switch ports on the Actiontek router to one of the switch ports on the Belkin router (not the WAN port!!!). This will, in essence, create one large network which will enable communication between your two boxes. It'll look like this:

```


--------------------
      Internet
--------------------
             |
             |
     --------------------------------------------------------------------------
        Actiontek Router + Belkin Router (wifi)  [ ONE INTERNAL NETWORK NOW ]
     --------------------------------------------------------------------------


```

Hope this helps!

-Richard

---

### Post by guilly on 2007-07-26
Unless i'm completely lost but i'm pretty sure that's what he has configured already is it not??

---

### Post by mdsypr on 2007-07-26
Gully, thanks your confused me alittle but again not sure what to do I can try to re-set the IP and see if that works but then I read rickyjones post.

Rickyjones ... yes you are correct I have my Ubunto connected directly to the Actiontech router and I plugged the Belkin WiFi router to the Actiontech and my XP laptop connects through the Belkin.

I did change the IP address on the Belkin from 192.168.1.1 to 192.168.201.1 so don't know how that impacts anything.

I currently do have a cable conenect from the actiontech to the belkin ... are you saying I just need to go into the settings and disable DHCP?  Will that solve any port issues? Will all communication be on the same network and flow within the network without any issues?

I think I am getting close, hopefully with your help I will get there soon.

Thanks,
Mike

---

### Post by rickyjones on 2007-07-26
> **guilly said:**
> Unless i'm completely lost but i'm pretty sure that's what he has configured already is it not??

I believe the OP has it configured like my first picture, where the routers are separated into different zones. I am proposing that he connect them via the switch ports, just like you would plug a normal 4 port switch in to expand your network.

Example: I believe he has a cable going from a port on the Actiontech router to the WAN (or Internet) port on the Belkin router. If so then he should first DISABLE the DHCP server on the belkin router and proceed to move the cable from the WAN (or Internet) port on the belkin to on of the normal switch ports (ports 1 - 4 probably).

This would create ONE network instead of TWO.

The problem is that the Belkin router is not routing traffic between the two networks because it is not designed to do so. So, make it easy and have one network.

-Richard

---

### Post by guilly on 2007-07-26
Richard i think i know where your going with this... if Mike was to connect his network like stated in your second picture and then configure his parameters like this...

XP BOX: static ip of 192.168.1.10
Ubuntu Server static ip of : 192.168.1.11
Belkin : 192.168.1.12
ActionTec: 192.168.1.1

have xp and ubuntu configured with default gateways pointing to 192.168.1.1

this should work right???

---

### Post by rickyjones on 2007-07-26
> **guilly said:**
> Richard i think i know where your going with this... if Mike was to connect his network like stated in your second picture and then configure his parameters like this...

XP BOX: static ip of 192.168.1.10
Ubuntu Server static ip of : 192.168.1.11
Belkin : 192.168.1.12
ActionTec: 192.168.1.1

have xp and ubuntu configured with default gateways pointing to 192.168.1.1

this should work right???

Yes, that is correct.

I would personally make the following changes:
1) Configure the Belkin router as follows:
      * Static IP: 192.168.1.2
      * Subnet Mask: 255.255.255.0
      * Gateway: 192.168.1.1
      * DNS: 192.168.1.1
      * Take a network patch cable from switch port 1 to one of the switch ports on the Actiontech router
2) Configure the Ubuntu server with a static IP address of 192.168.1.11
3) Configure the XP box as DHCP unless a static is preferred

After doing that the following results should be apparent:
      * Internet will be accessible for all clients plugged directly into the network or connected wirelessly to the Belkin router.
      * Communication between all clients/servers should be restored.
      * Simple network allows more dynamic changes without affecting performance in the future.

Hope this helps the OP and everyone else reading the thread.

-Richard

---

### Post by mdsypr on 2007-07-26
Rickyjones.

So I know what to do:

1) Set the belkin router to 192.168.1. whatever I want
2) In the belkin router disable DHCP
3) Make sure I have a cable from the Actiontech to belkin router
4) Leave laptop settings alone, DHCP will take care of it all

If I do that do I need to go in and make sure the default gateways are the same, etc?  The above should be the most automated correct?

My Actiontech router is 192.168.1.1
My Ubunto Server is 192.168.1.2
My Belkin Router is 192.168.201.1 ---- I will change to something like 192.168.1.111 or whatever
My laptop will connect wirelessly and if I leave DHCP alone it will automatically be assigned an IP from the Belkin

Did I get it right?

Mike

---

### Post by rickyjones on 2007-07-26
You have it right up until the end I do believe.

Step 1: Disable DHCP on the Belkin router. We don't want this router to think - at all.
Step 2: Set the IP address on the Belkin router to be 192.168.1.xx - whatever you'd like. This way it is on the same network as the Actiontech. Assign a gateway address of 192.168.1.1 as well.
Step 3: Plug the Belkin router into the Actiontech router using one of the switch ports on the front - this way it is just like an access point.
Step 4: Watch it work...

The internal IP address will be assigned by the Actiontech router if I am correct in this. What will happen is the Belkin router will just be an extension to the Actiontech, so the wireless clients will get an IP from the Actiontech router as well.

I hope this clears it up for you. :)

-Richard

---

### Post by mdsypr on 2007-07-26
Richard,

Dam thanks ... I did learn ALOT but what a pain in the butt.  I need to do this when I get home so I am not sure it will work but it makes sense.

If the belkin will just pass data to the Actiontech then it should assign an IP like you said.

Do I have to manually set anything in the belkin besides disable DHCP?  You said to update the gateway, I a assume this has to be done in the setup somewhere in the belkin?

I hope this makes everything work ... I do have an issue with ftp'ing but I will start a seperate thread on that after I clear this hurdle.

I will try later and let you know, I hope this works.

Mike

---

### Post by mdsypr on 2007-07-26
Dam,

It worked, I can see files on the XP ... but the wierdest thing is when I browse it in Ubuntu, PLACES then NETWORKS and I click on my Ubuntu server, I see the WORKGROUP I setup and then the folder but I can't access it, it says that it must have been deleted.

When I goto PLACES and COMPUTERS and drill into my shared file it is there ... how wierd it that?

Any answers?

Mike

---

