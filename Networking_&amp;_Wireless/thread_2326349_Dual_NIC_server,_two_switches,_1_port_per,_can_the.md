---
title: "Dual NIC server, two switches, 1 port per, can they talk?"
date: 2016-05-30
forum: Networking &amp; Wireless
---

### Post by Roasted on 2016-05-30
Hi friends. I'm considering segregating some of my video surveillance traffic off of my main LAN via a POE switch (right now it's just a series of POE injectors -- meh). What I'm unsure of is if I go the dual NIC route (different IP on each NIC), if they'll be able to "talk" to one another.

For example, let's say I IP NIC A @ .20, and NIC B @ .21. NIC B would be plugged in to the POE switch with the cameras, NIC A would be plugged in to the regular LAN switch that feeds the rest of the network in my house.

If I go this route, this would allow all of my video surveillance traffic to hang out on a dedicated switch specifically for that task. Likewise, it would leave my main household switch alone. Having two NICs in the server, and thus, each NIC plugged in to each switch, I'm *thinking* this would keep things segregated.

...but can they talk? Given the subnets would be the same, I'm thinking yes, but I'm not feeling entirely confident of my suspicion. By "talk" I mean, if I set up my Bluecherry client (the video surveillance software) to point to my "server" and I choose .21 (NIC B), would it be able to pick it up?

That path would look like this: Netgear router >> main household switch >> server NIC A >> server NIC B

Again, if I keep NIC A and NIC B subnets the same, I suspect yes. What say you?

P.S. - as I typed this up, I questioned if I could articulate this question in words appropriately. Here's a diagram. 
[http://i.imgur.com/I0J22gP.png](http://i.imgur.com/I0J22gP.png)
Question is this: If my laptop has the Bluecherry client with the server address 192.168.1.20 (NIC A's IP) will I be able to stream the traffic from the network cameras residing on the POE switch, and thus, 192.168.1.21 @ NIC B on the same server?
(the main switch and POE switch would *not* have an ethernet line connecting them)

Thanks for any assistance!

---

### Post by Fire_Chief on 2016-06-03
Hi Roasted,

This won't quite work like you expect it to because the server is not bridging traffic between the two NICs. It will simply ignore the request for the communication on the .21 IP since it's only technically listening on .20 through that switch link.
I'm not sure why you want to segment the network like this since you are still trying to communicate across both switches. It would seem easier to just run a switch uplink between the two switches and have your server just use 1 NIC for it's network activity.

Cheers!

---

### Post by Roasted on 2016-06-03
> **Fire_Chief said:**
> Hi Roasted,

This won't quite work like you expect it to because the server is not bridging traffic between the two NICs. It will simply ignore the request for the communication on the .21 IP since it's only technically listening on .20 through that switch link.
I'm not sure why you want to segment the network like this since you are still trying to communicate across both switches. It would seem easier to just run a switch uplink between the two switches and have your server just use 1 NIC for it's network activity.

Cheers!

Thanks for your input! I was thinking that that would be the case. The reason I want to segregate the network a bit is just to keep the load off of the NIC. There are times I am pushing massive backups from several wired locations to my server. My server handles two functions - 1x2TB WD Purple for video surveillance, 4x3TB WD Red (RAID6) for NAS data. Since I have the two data pools split, I'd like to keep the NIC traffic split as well. Last thing I want is to hammer the server with backups across the same NIC as my video surveillance. I don't want to see it struggle. Maybe it's a non-issue, but I always banked on splitting it a bit despite using the same exact box to handle everything.

I just ordered an 8 port POE switch. I have 6 cameras at the moment. If I stay with my dual NIC idea, port 7 goes to the server. That would require port 8 go to my bigger 24 port switch for the rest of the LAN. I can handle that. It'll just mean if I add another camera (likely in the future) that I'll have to either get another POE switch or just use a POE injector I already have into the main 24 port switch.

---

### Post by Roasted on 2016-06-04
I couldn't help but to put some more thought into this earlier this evening. Instead of trying to explain it (even though I'm going to anyway), I gimp'd a picture to go with it. Here's the basic idea... let's just say I am stuck on keeping the video traffic as localized as possible. Likewise, it's (oddly) cheaper for me to get two 8 port POE switches than it is for me to get a 16 port POE switch. So, I'm rolling with that idea for now. 

Overall, there's 3 switches in this theory of mine. 24 port (LAN for the house), POE 1 (8 port for cameras), POE 2 (8 port for cameras). I'm also (again, this is theory/idea toying) working with 3 NICs in my server. Basically one for each switch all IP'd differently.

[http://i.imgur.com/G3no8cy.png](http://i.imgur.com/G3no8cy.png)

The pink lines are uplinks.

The thought process here is this... let the 24 port switch be for everything on the LAN. .200 would be the main NIC of the server which is what will be utilized for auto mounting my samba shares through autofs, ssh work, etc etc. The other 2 NICs would be IP'd .201 and .202. Each of the POE switches would have several cameras. By keeping the cameras, and as such, my "CCTV NICs" on the server on segregated switches, I am wondering if it would route traffic in the way I am questioning. 

Consider this... during a typical day, the cameras are recording 24/7. The cameras are connected to the POE switches. The POE switches are connected to the CCTV NICs (.201, .202). I would think the video traffic would have no reason to flow back to the 24p switch in order to get into the server. If this is the case, that'd be great, because if other systems kick on a backup and flood the .200 NIC on the server it shouldn't sacrifice bandwidth space from the cameras with everything hitting the same NIC. The backups would be hitting .200, while the cameras would be hitting the .201 and .202 NICs. But what if I open my desktop client (which points to 192.168.1.200)? I question if it'll be able to talk to the incoming video traffic on POE 1 and POE 2 NICs on the server (.201, .202) if the client program itself running on my desktop system would acknowledge the incoming video traffic and say oh, that's on .201 and .202, but your client is talking to .200 (and as a result fail), or if it would be smart enough to route everything correctly. Any thoughts on this?

Also, is there a way to make the NICs talk to each other? If my client is pointed to .200, and I open the Bluecherry CCTV client, would it say "oh, this live stream is being processed locally despite it being on a different IP/NIC (but same subnet) and say "here, let me just sling this live feed locally and back out .200 to the client system." ??

Hopefully that, somehow, makes sense...

---

### Post by Fire_Chief on 2016-06-06
Ok, so after your first reply about the drive configurations I have some questions that need confirming.

Are the switches and all NICs running at 1Gb link speed? If not, what are the link speeds at the server?

Based on your setup description though I can't tell if the cameras push data to the server via individual configuration or if there is software on the server that queries and pulls the video streams from the cameras. Can you clarify?
It would be great to know what the bandwidth and throughput demands are from each camera to know where your bottleneck will first appear as the environment scales up.
Also, does your LAN switch support Link Aggregations or Port Channels? This would be a good way to increase the bandwidth to the server (bonding multiple NICs together) and simplify the IP connectivity.

---

### Post by Roasted on 2016-06-06
Surely. This is the basic idea. The entire LAN is currently gigabit via a 24 port switch. The server has one NIC. The server runs software known as Bluecherry. Bluecherry pulls the camera streams from the cameras, thereby saving the feeds as events as per the settings of the Bluecherry software.

What I'd like to do is add an 8 port gigabit POE switch and a 2nd NIC for the server. All still remaining gigabit.

The point of the 8 port gigabit POE switch started simply as a means to power the cameras + provide networking, as I had previously been using six POE injectors for all six cameras. This turns into a wiring fiasco. The POE switch simplifies that.

Given I was 11 dollars away from adding a 2nd gigabit NIC from the server, I figured it might be in my best interest to try and further segregate the network traffic. NIC A to 24 port switch, NIC B to 8 port POE camera switch.

In a perfect world, I'd like to IP NIC A to 192.168.1.20 and IP NIC B to 192.168.1.21 (or something). I'd also like to not uplink the 24 port LAN switch and 8 port POE switch together.

My concern comes in with the Bluecherry client, which runs on my laptop, desktop, etc (basically everything but the server). The BC client points to a specific IP. If I point it to NIC A @ 192.168.1.20, yet the Bluecherry feeds are being pulled in over NIC B @ 192.168.1.21, that's where I question if the BC client would be able to hit the server + the server itself would realize "oh, you're incoming from NIC A, and requesting live streams coming on from NIC B. Here, let me do that for you" and make it all magically happen.

I may be making this unnecessarily difficult. My goal is just to try and firmly isolate camera traffic from the main NIC on the server *but* still retain all of the Bluecherry client functionality on my laptop/desktop/etc I currently enjoy. That way if a massive backup kicks in and floods NIC A, the camera feeds wouldn't be in the mix. I have no idea what would happen, maybe nothing, but it'd be nice to not have to worry about it. :D

If the NICs don't talk to each other like I mentioned above, I suppose I could leverage a proxy of some sort on the interfaces to allow traffic to pass?

---

### Post by NadirPoint on 2016-06-06
> **Roasted said:**
> Surely. This is the basic idea. The entire LAN is currently gigabit via a 24 port switch.
This is your bottleneck with the traffic pattern described.  The 24-port switch fabric is your limiting factor.  No amount of slicing and dicing whatever is connected to it will improve throughput.  Upgrade the backup links to a 10-Gig path if that actually is the source of the problem.

---

### Post by Fire_Chief on 2016-06-06
Ok, super. I was hoping it was driven by an app on the server.

Since the BC client only needs to talk to the BC server software and not directly to the cameras, then I suggest building your segmented network with the two nics. But instead of 1 IP subnet, use two separate ones.

NIC A: LAN switch
Existing IP subnet: 192.168.1.x /24
-Default route to Internet, LAN access, etc.

NIC B: POE switch
New IP subnet: 10.0.0.x /24 for example
- Do not configure a default gateway on this network. Leave it blank.
- All cameras get IP on this network and can only talk to the server via the dedicated interface

The LAN switch and the POE switch will not have any cross-connects between them (it's not needed for any useful reason anyway unless you needed to directly access a camera from your laptop/desktop). 
If you do need to directly access cameras from your LAN systems, then you could put the cross connect in place but I would assign a secondary IP address to the LAN system (laptop/desktop) from the 10.0.0.x /24 network and then you can see both environments from your desktop while keeping the network traffic properly isolated from the other LAN systems. I read through the BlueCherry documentation and it isn't clear with the Client Live Viewing whether the client attempts to get the live streams from the server or directly from the cameras. I would try it from the server to see if you even need the cross connect for any client side functionality.

The BC Server should listen by default on all NICs in the system so it will see the cameras on NIC B and see your BC client connection on NIC A.

Make sense?

Cheers!

---

### Post by Roasted on 2016-06-06
> **NadirPoint said:**
> This is your bottleneck with the traffic pattern described.  The 24-port switch fabric is your limiting factor.  No amount of slicing and dicing whatever is connected to it will improve throughput.  Upgrade the backup links to a 10-Gig path if that actually is the source of the problem.

I'm not having an actual problem. I'm simply trying to set up the camera portion in the recommended way, as it's always preferred to keep video surveillance segregated in some capacity. I know I'm complicating things by using the same server for my home/file/backup/centralized storage as my video surveillance server (one rig, just different hard drives inside to house the different data sets).

Point is I just want to keep the video stuff "over there" on the POE switch/NIC B, and keep the main file/backup/etc data "over here" with the 24P/NIC A, while maintaining my ability to fire up the client and still see the camera streams. 

Chances are the bandwidth coming from my cameras is so minimal that it's a non-issue altogether... but that won't stop me from trying to build things out the way I have in my mind assuming it's somehow do-able. :P

Thanks for your 2c!

---

### Post by Roasted on 2016-06-06
> **Fire_Chief said:**
> Ok, super. I was hoping it was driven by an app on the server.

Since the BC client only needs to talk to the BC server software and not directly to the cameras, then I suggest building your segmented network with the two nics. But instead of 1 IP subnet, use two separate ones.

NIC A: LAN switch
Existing IP subnet: 192.168.1.x /24
-Default route to Internet, LAN access, etc.

NIC B: POE switch
New IP subnet: 10.0.0.x /24 for example
- Do not configure a default gateway on this network. Leave it blank.
- All cameras get IP on this network and can only talk to the server via the dedicated interface

The LAN switch and the POE switch will not have any cross-connects between them (it's not needed for any useful reason anyway unless you needed to directly access a camera from your laptop/desktop). 
If you do need to directly access cameras from your LAN systems, then you could put the cross connect in place but I would assign a secondary IP address to the LAN system (laptop/desktop) from the 10.0.0.x /24 network and then you can see both environments from your desktop while keeping the network traffic properly isolated from the other LAN systems. I read through the BlueCherry documentation and it isn't clear with the Client Live Viewing whether the client attempts to get the live streams from the server or directly from the cameras. I would try it from the server to see if you even need the cross connect for any client side functionality.

The BC Server should listen by default on all NICs in the system so it will see the cameras on NIC B and see your BC client connection on NIC A.

Make sense?

Cheers!

Thanks for your input! Makes total sense. I am nearly positive that Bluecherry client pulls directly from the server. I've watched "bmon" over SSH to my server before, and upon opening the client, my TX ramps up bigtime, whereas before that the TX is all but completely idle. If Bluecherry-client was calling out to the cameras, I can't imagine that would instigate the TX traffic to increase on the server itself, as that would be a direct me-to-camera connection then.

So basically, all I'm doing is setting a static IP on NIC B on a different subnet from NIC A, resetting the static IPs on the cameras to coincide with the network settings of NIC B, and uh... that's it. I'll tinker around and see what I come up with. Thanks for the info!

---

### Post by NadirPoint on 2016-06-06
> **Roasted said:**
> I'm not having an actual problem. I'm simply trying to set up the camera portion in the recommended way, as it's always preferred to keep video surveillance segregated in some capacity.
But you're not.  It's on the same machine in the same network.  It sounds like all you are doing is making it more complicated than it needs to be.

What does logical separation buy you?

---

### Post by Roasted on 2016-06-06
> **NadirPoint said:**
> But you're not.  It's on the same machine in the same network.  It sounds like all you are doing is making it more complicated than it needs to be.

What does logical separation buy you?

Segregated video surveillance traffic. Which, is kind of the goal.

Keep video surveillance feeds over there, keep all other stuff over here.

If 24 port gigabit POE switches with VLAN support were more affordable, I'd have just gone that route. ;)

---

### Post by NadirPoint on 2016-06-06
> **Roasted said:**
> Segregated video surveillance traffic. Which, is kind of the goal.
But why?  What's the point?  Or "goal" as t'were.  You are setting up a whole new network, hardware and all for what amounts to by your own admission, an insignificant amount of traffic.

---

### Post by Roasted on 2016-06-06
> **NadirPoint said:**
> But why?  What's the point?  Or "goal" as t'were.  You are setting up a whole new network, hardware and all for what amounts to by your own admission, an insignificant amount of traffic.

During a typical time of day, yeah, it'll be insignificant. If my other boxes kick on a backup at the same time, it may possibly cause issues.

I say possibly because while I have not verified this with Bluecherry, on an older setup I used to run into issues, such as the quality of my feeds suffering whenever a bulk of other LAN bandwidth was hitting my server. The videos would play back slow, stuttered, and appeared to have lost FPS during the transmission process. Given I was watching my activity monitors at the time, it looked like my network port was just getting too hammered with all of the inbound traffic over the line.

By segregating these feeds on their own switch and NIC port on the server, it gives the camera feeds their own carpool lane. 

It still may be overkill. I'm not sure. I may find this turns out to be entirely nonsense. I'll know more when I set it up and test things out. In the end, the POE switch was an inevitable move to clean up wiring and get rid of the POE injectors, so that was a guaranteed purchase either way. Beyond that, the only other thing purchased was an 11 dollar gigabit NIC. If this overcomplicates things beyond a reasonable justification, I can easily put things back how they were with the 8 port switch joined as part of the network and toss the new gigabit NIC on the shelf for the inevitable use I'll have for it with another system in the future.

---

