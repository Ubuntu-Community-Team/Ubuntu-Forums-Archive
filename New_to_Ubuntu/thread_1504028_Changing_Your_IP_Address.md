---
title: "Changing Your IP Address"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Darkhorse85 on 2010-06-07
Hi

My service provider, who is a guy in my neighborhood (via Wifi), seems to be rationing the available bandwith of everybody conected to him. Everytime I reinstall with any operating system, it works fast for like a week and then it just goes down boom. So i want to try something that will change my IP address manually or better yet changes it every time I boot up These are my Auto eth0 settings, this is the one i need to change. Also I have read some other post on changing your ip but i dont quite understand them.
   
IP Address: 192.168.9.206
Broadcast Address: 192.168.9.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.9.1
Primary DNS: 172.31.0.1
Secondary DNS: 172.31.0.2

Any Help?

---

### Post by barney385 on 2010-06-07
Just log into his router and lock him out.

---

### Post by metalf8801 on 2010-06-07
> **Darkhorse85 said:**
> Hi

My service provider, who is a guy in my neighborhood (via Wifi), seems to be rationing the available bandwith of everybody conected to him. Everytime I reinstall with any operating system, it works fast for like a week and then it just goes down boom. So i want to try something that will change my IP address manually or better yet changes it every time I boot up These are my Auto eth0 settings, this is the one i need to change. Also I have read some other post on changing your ip but i dont quite understand them.
   
IP Address: 192.168.9.206
Broadcast Address: 192.168.9.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.9.1
Primary DNS: 172.31.0.1
Secondary DNS: 172.31.0.2

Any Help?

The IP Address is assigned by the router so changing it is not going to help. I would think he was using your MAC Address but that wouldn't changed with your OS because its hardware. Maybe he is using the name of your computer do you change that with new installs? Also have you tried talking to the guy? 

hope this helps 
Dan

---

### Post by metalf8801 on 2010-06-07
> **barney385 said:**
> Just log into his router and lock him out.

Don't do that or he or she is going to lock down the router so no one else can use it. He or She is already being nice by letting people use his or her connection to get online even if its a slow connection its a lot better then nothing.

---

### Post by Darkhorse85 on 2010-06-07
No, im scared he is actively trying to not allow me so much bandwith so i dont want to talk to him. I also didn't explain fully how i am connected to him. I have a Wifi router on my roof, I just plug a LAN cable in my lucid desktop and it connects (auto eth0). I have never worked with or seen the router, its just installed on my roof. 

When i install a new OS or reinstall it tends to be miles faster but only for a while (has varied from a day to two weeks). So i just need to see whether changeing my IP is the issue

---

### Post by barney385 on 2010-06-07
It's probably just the network being dragged down by MyFace crap.


What a waste of bandwidth.

---

### Post by barney385 on 2010-06-07
> **Darkhorse85 said:**
> No, im scared he is actively trying to not allow me so much bandwith so i dont want to talk to him. I also didn't explain fully how i am connected to him. I have a Wifi router on my roof, I just plug a LAN cable in my lucid desktop and it connects (auto eth0). I have never worked with or seen the router, its just installed on my roof. 

When i install a new OS or reinstall it tends to be miles faster but only for a while (has varied from a day to two weeks). So i just need to see whether changeing my IP is the issue

You might just need to change ports, since you can't get into the router changing your port forwarding won't make a difference.

---

### Post by Darkhorse85 on 2010-06-07
Also i should mention, i can still browse the inernet although it is lower but it has a large affect on my downloads from th einternet from various sources torrents etc

---

### Post by barney385 on 2010-06-07
> **Darkhorse85 said:**
> Also i should mention, i can still browse the inernet although it is lower but it has a large affect on my downloads from th einternet from various sources torrents etc

Ahhh...yep, a port forwarding issue.

Are you using transmission?

---

### Post by Darkhorse85 on 2010-06-07
Oh yes im paying him, but can anybody give me a hint on changing the IP. I still like to give it a try

---

### Post by Darkhorse85 on 2010-06-07
yes transmission

---

### Post by barney385 on 2010-06-07
> **Darkhorse85 said:**
> yes transmission

You can change which port you use very easily then.

Open transmission>Edit>Preference>Network

You'll see a window that displays which port you're currently using.

If downloading is slow you should probably change it.

The help section of transmission can help with that, and it also gives recommendations.

Google is a big help also of course and their is probably a tips and tutorial section here.

---

### Post by Darkhorse85 on 2010-06-07
Thanks, but cant seems to find it there is only "network connections" and "network proxy" in preferences. Its on lucid

---

### Post by darkdragn on 2010-06-07
If you really want to give the IP thing a try, just make an entry in your ifup file. You can also use your network manager. Just right-click the network icon, open connection manager, and select auto eth0. Alter the ip, but replicate the rest from your current configuration (Gateway, DNS etc). As long as the ip is within the range and not currently taken you should be good, even if the network is configured to provide via dhcp.

The way i see it, if you want your ip changed, it's your decision. If the issue is still going on, ask for some more help with it, ^_^. (If you need help with ifup just ask on this thread, ^_^)

---

### Post by barney385 on 2010-06-07
> **Darkhorse85 said:**
> Thanks, but cant seems to find it there is only "network connections" and "network proxy" in preferences. Its on lucid

We have the same OS and the same Torrent Client.

Probably have to start a torrent download to see the same thing I am.

---

### Post by barney385 on 2010-06-07
Also, I have version: Transmission 1.92 (10363)

To find your version of Transmission: 

In terminal: transmission --version

---

### Post by Darkhorse85 on 2010-06-07
Got it, Will try and figure it out. It says the port is closed, so im looking for posts explaining port fowarding. I really appreciate the help, as always, the help i get in the forum is fantastic!

---

### Post by barney385 on 2010-06-07
> **Darkhorse85 said:**
> Got it, Will try and figure it out. It says the port is closed, so im looking for posts explaining port fowarding. I really appreciate the help, as always, the help i get in the forum is fantastic!

You can also under "preferences" reduce the upload speed also, which can make a big difference on how fast you can download.

Especially on wireless networks.

Good Luck

---

### Post by QIII on 2010-06-07
If I may be so bold as to interject an ethical component here...

The technical aspects not withstanding, you may find yourself out of a connection altogether by attempting to take advantage of your neighbor's kind (if terribly foolish) gesture.

Say he has five "customers".  Four IP/MAC addresses remain constant.  A  fifth connection hops from IP/MAC to IP/MAC and that one uses a good deal more bandwidth than the others.

It would not be hard to figure out who is changing.

Most people don't take kindly to being taken advantage of.

That, and "reselling" his service from his ISP may violate his own contract.

---

### Post by Mariane on 2010-06-07
If his neighbour is foolish then I must be out of my mind. I leave my wifi wide opened and I have a router with 3 aerials which reaches quite far. Last time I looked 9 computers were connected, counting mine. I set up a poster in the hall, saying how much I pay every month and telling people "If you use the Miklabraut network I would appreciate a contribution". It works. Not regularly and not every user contributes but it works, and sometimes it even adds up to more than my bill. 

Isn't sharing in the spirit of Ubuntu, the whole "Humanity to others" business? Why do you call this foolish? If some youngster is broke should he/she be denied surfing? And if he/she has been blacklisted by his/her previous ISP I just hope he/she will have learned to use tor by now... 

Mariane

---

### Post by IAmAnarch on 2010-06-07
> **Mariane said:**
> If his neighbour is foolish then I must be out of my mind. I leave my wifi wide opened and I have a router with 3 aerials which reaches quite far. Last time I looked 9 computers were connected, counting mine. I set up a poster in the hall, saying how much I pay every month and telling people "If you use the Miklabraut network I would appreciate a contribution". It works. Not regularly and not every user contributes but it works, and sometimes it even adds up to more than my bill. 

Isn't sharing in the spirit of Ubuntu, the whole "Humanity to others" business? Why do you call this foolish? If some youngster is broke should he/she be denied surfing? And if he/she has been blacklisted by his/her previous ISP I just hope he/she will have learned to use tor by now... 

Mariane
If some youngster is broke, he/she can go to the public library. Just a thought.

---

### Post by QIII on 2010-06-07
I share my home with the children of parents who are unable or unwilling to take care of them.  That is Ubuntu.  My wife would make a good deal more money being employed than we are receiving from the State to raise children.  (It's their money, not ours, so we don't profit from it.)  That is Ubuntu.  We have taken young people down on their luck into our home for nothing.  That is Ubuntu.  I have resources enough to help others and I give same willingly for their benefit.  That is Ubuntu.

Sharing is certainly in the spirit of Ubuntu.  Sharing that which is  yours to share.  Sharing that which is not yours to share is certainly  not, in any spirit, ethical.
 
 Most ISP contracts forbid reselling -- even a "donation" would fit that.
 
 And if anyone and everyone within shouting distance can use your router,  they can also use it for nefarious purposes.  That would lead the  authorities to knock on your door.  Never mind the ease with which they  could putter around directly with your machine.
 
 You do lock your doors when you leave, don't you?  Wouldn't it be foolish not to do so?

I would say that failing to lock down your wifi is foolish.  Yes.

If you set up your router to accept connections from particular MACs, that is up to you.  If you don't charge anyone -- or ask for donations -- you haven't violated your contract.  But you would still be opening your machine up for abuse and making yourself liable for any illegal activities your patrons might enjoy on your dime.

---

### Post by Mariane on 2010-06-07
> **IAmAnarch said:**
> 
If some youngster is broke, he/she can go to the public library. Just a thought.


I wish. No such thing here. There is a public library but it does not give internet connection.

> **QIII said:**
> 
Sharing is certainly in the spirit of Ubuntu.  Sharing that which is  yours to share. 


My connection is mine to share. I have limited - though quite high - bandwith and monthly volume of download/upload. 

> **QIII said:**
> 
And if anyone and everyone within shouting distance can use your router, they can also use it for nefarious purposes. That would lead the  authorities to knock on your door. Never mind the ease with which they  could putter around directly with your machine.


Or I with their machine. I don't do it and neither do they. What kind of relationship would you prefer to have with your neighbours? One based upon trust and mutual goodwill or one based on mistrust and selfishness?

> **QIII said:**
> 
You do lock your doors when you leave, don't you?  Wouldn't it be foolish not to do so?


Actually, I don't always lock it. Sometimes I even leave it wide opened for fresh air. It is not unusual in Iceland, there is practically no criminality here. OK, you could not leave a vine shop door wide opened over the weekend and expect to find all the bottles the following Monday. But Icelanders are highly moral and would not walk into your home to steal something. 

The way of life here is very different. No one teaches kids to fear strangers because Icelanders would never harm a kid. Once an unknown young kid climbed into my lap on a bus because there was no vacant seat. The whole country is like that, for example Iceland does not have an army, it just relies upon its neighbours not attacking. And it works. 

If someone did something bad through my internet connection - I don't consider that using torrents is bad - and I got into trouble, I would stop leaving my connection opened. And I would tell everyone why it is now closed. We would quickly find out who did it and shame him/her. People know that. People who might be tempted to do something bad won't do it because of social pressure, because they don't want all their neighbours to look down on them. 

Mariane

---

### Post by QIII on 2010-06-07
Your connection is yours to share.  It is likely not yours to resell.
 
I will refrain from a philosophical discussion about the morality of any  particular culture over any other beyond saying that claiming higher  morality over others is often ethno- or culturo- centric rather than  objective.

There is trust, and there is objective assessment of danger.  There is sharing and there is violation of contract.

My recommendation to the poster stands.  His "provider" is likely  violating his contract with his provider.  From a security perspective, wide open Wifi for a personal network is ill-advised.

---

### Post by Zill on 2010-06-07
> **QIII said:**
> Your connection is yours to share.  It is likely not yours to resell...From a security perspective, wide open Wifi for a personal network is ill-advised.
All excellent advice IMHO.

---

### Post by Darkhorse85 on 2010-06-08
well i didn't really want to get into this but its actually a small service provider in a town about 20km away, I just thought I would simplify the problem so that we can get down to the core of the issue. But since we are debating my ethics i should probably clear up the scenario (although its not the real issue). I've had this contract for 4 years, capless broadband is just a bit more expensive. So if he has me and 3 other people on the same line (I assume he uses the same capless broadband, if not an even better package from a large service provider) his gross profit is almost 300%. Obviously he is out to make a profit and thats cool, but is also my right to maximise my usage experience as there is no stipulation as to what that is by definition of bandwith or cap. I will try whatever I can to maximise my experience. It is up to him to ration his bandwith to which ever level of profitability he prefers. And as for why i haven't got broadband already, I will definitely look into it if i cant sort this out. And of course he would then be losing a profitable customer.

---

### Post by QIII on 2010-06-08
My intent was not to directly impugn your ethical integrity.  It was simply to raise the question.

Getting the best deal you can find is fair game.  I like capitalism and free trade.  If  you'd like to come over to my home some time, I'll demonstrate the benefits to be gained.

But a "best deal" made in the context of possible breach of contract (in this case, your provider's possible breach of contract with his provider) is dangerous ground, however interesting the academic pursuit of its technical solution may be.

---

