---
title: "Thin Clients for Classrooms"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by fourthofjuly on 2008-02-10
For our school located in India, we plan to make classroom learning more interesting for children by enabling teachers with animated digital media content to explain concepts from the syllabus... using CDs created using Flash...

We plan to replace all our blackboards with interactive whiteboards that can function as blackboard as well as display.

For a total of 30 classrooms, would it be possible to store the entire syllabus from the CDs in a central server, and have thin clients installed in each classroom that can connect to the server using Wi-Fi? Provided 15 classes request the server simultaneously, will this setup work, since the data will be rich media content?

Or will laptops for teachers be a more prudent choice?

Please guide & thanks in advance...

---

### Post by fourthofjuly on 2008-02-11
Please guide if someone has expertise in this area?

Thanks...

---

### Post by fourthofjuly on 2008-02-12
For our school located in India, we plan to make classroom learning more interesting for children by enabling teachers with animated digital media content to explain concepts from the syllabus... using CDs created using Flash...

We plan to replace all our blackboards with interactive whiteboards that can function as blackboard as well as display.

For a total of 30 classrooms, would it be possible to store the entire syllabus from the CDs in a central server, and have thin clients installed in each classroom that can connect to the server using Wi-Fi? Provided 15 classes request the server simultaneously, will this setup work, since the data will be rich media content?

Or will laptops for teachers be a more prudent choice?

Hope someone can give some guidelines...

---

### Post by aeiah on 2008-02-12
yes that would work. make sure you have a good wireless router, and compatible wireless cards of course. you should also be aware that wireless may struggle with access to CDs worth of information, but if you only need a few mb at a time (and not a whole 700mb of content) then you'll be fine. because its flash the best thing to do may be to set up a webserver and embed the flash files in webpages. this would make it easier for the teachers to use.

if you are thinking of using video, you may have to look at different streaming options and whether wireless will be able to handle them reliably. it may be cheaper to install a wired network if it turns out you need to install loads of wifi boosters

---

### Post by fourthofjuly on 2008-02-13
Thanks for the reply.... much appreciated...

I am not sure whether a wired / a wireless system will give better speeds? Cost not being a factor, can a wireless network perform better than a wired one?

Since all the educational content will mostly be flash animations / videos & sound,  the network should be able to handle these. 

If we have multiple servers  to manage this load, will that reduce the network burden?

Also, can thin clients (without monitors) be connected directly to the LCD projectors?

Please throw some light...

Thank you so much...

---

### Post by netztier on 2008-02-13
> **fourthofjuly said:**
> Thanks for the reply.... much appreciated...

I am not sure whether a wired / a wireless system will give better speeds? Cost not being a factor, can a wireless network perform better than a wired one?

Never, and if you over-engineer a Wireless LAN to perform half as good as a decent switched 100Mbps LAN environment, it'll cost a fortune.

Remember: A WiFi AccessPoint is nominally rated at 54Mbps and creates a "WiFi cloud" that behaves somewhat like a classic Ethernet hub. It's half duplex only and amongst the stations in the cell (the AccessPoint itself also being one) only ever one can send at any time. The net capacity of a single "WiFi cloud" is ~25Mbit/s (which makes "54mbps" a blunt marketing lie). 

So all stations in one cloud will have to share these 25Mbit/s that are available. This might be enough.
If you make sure that the neighboring classroom gets it's own WiFi cloud (using a another 802.11b/g channel that does not overlap with the neighbours), you might just get away with it. The downside is that you'll have to "uplink" these clouds to a central site where the servers are; you had better do this with wired connectivity.

> **fourthofjuly said:**
> 
Since all the educational content will mostly be flash animations / videos & sound,  the network should be able to handle these. 


If this is just about opening a video file of 5-10MBytes, the ~2MByte/s throughput of a single WiFi clound might be good. If it is about 700MByte files, you'll have no joy. You could set up a "Video on Demand" server that would stream the content at a few hundred kBit/s to the clients to save bandwith.

On the other hand: if your goal is multimedia, then using thin clients is the wrong approach. Using thin clients with multimedia brings considerable load on the terminal server (which does all the computing, e.g. decoding video) and the network by streaming the raw, uncompressed video to the thin client: Your WiFi network will choke.

If you intend to use the Linux Terminal Server Project (available for instance as Edubuntu), you should investigate on their forums, wikis and web pages if their platform suits your multimedia needs.


> **fourthofjuly said:**
> 
If we have multiple servers  to manage this load, will that reduce the network burden?


Only if you implement "one server per classroom" (or bulding unit), AND if you bring that server into the same classroom, AND if you make sure that the server itself has wired ethernet. 

> **fourthofjuly said:**
> 
Also, can thin clients (without monitors) be connected directly to the LCD projectors?


If the thin client hardware has a VGA or DVI output connector, there is no reason why an LCD projector should not be able to digest that video signal. Just make sure that the thin client outputs a Signal of a screen resolution and refresh rate that the LCD projector can handle. 800x600 at 60Hz or 1024x768 at 60Hz are most common for projectors. Consult the projector's documentation for the right values.

The actual network topology to choose will depend on multiple factors, not the least of which are your campus topology and building infrastructure (how far away from each other are the classrooms?) , how many PCs you will deploy per building/classroom and a whole lot of other things.

For example, it could be an interesting concept to use cheap Wired Ethernet within a building, but do the uplink to the central site (where the servers are) with a point-to-point WiFi solution using directional antennas.

Could you give some more information about the campus environment? 

regards

Marc

---

### Post by fourthofjuly on 2008-02-13
Thank you so much Marc...

I understand that since we will have multimedia content, a wired network will be the best choice to avoid congestion... We would definitely like to have a superfast network...!!! 

I too have my fears about using thin clients for rich multimedia..., but can we distribute the work on 3 servers (say 1 server per 10 clients) to balance this load? Also, all the classroom will not run the system simulteneously, let's say at the most 15 out of 30 thin clients request the servers at a time, will that setup work provided we have wired ethernet throughout.

Information about our campus environment...

Total 30 classrooms are in a single building distributed evenly on the ground floor, 1st and 2nd floor. The administrative offices in the centre of the building divide each floor in two separate sections - on the left and right side.

Another request... we also have been given an option to give laptops to teachers instead of thin clients...  is it feasible, since I have learnt that thin clients & a central server make the admin job (data management) much easier...? 

Your guidelines please...

Thanks & Regards,

Devang.

---

