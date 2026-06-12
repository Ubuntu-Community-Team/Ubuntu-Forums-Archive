---
title: "GameServers wrong IP"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by is kla. on 2011-08-04
First of all hello to you all and the community.
I'm a new ubuntu user and so far I am very pleased with it.

I have installed a CS 1.6 server with the hldsupdatetool and when I start it with the command 

> ./hlds_run -game cstrike -pingboost 3 +sys_ticrate 1000 +heapsize 250000 -port 27015 -autoupdate +secure +sport 27014 +maxplayers 8 +map de_dust2
And this pops out, but I think that this works then, the only problem is that my friends can't see the server in their "Favorites" list.

> Auto detecting CPU
Using AMD Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Counter-Strike Base Content' version 35


Checking/Installing 'Linux Server Engine' version 55


Checking/Installing 'Half-Life Base Content' version 12


HLDS installation up to date
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 70 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 0 multi object alertable sleeps

Console initialized.
scandir failed:/home/iskla93/warzonezombie/./platform/SAVE
Protocol version 48
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 16:56:04 Mar  8 2010 (4883)
STEAM Auth Server
Server IP address 192.168.1.237:27015
scandir failed:/home/iskla93/warzonezombie/./platform/SAVE
[S_API FAIL] SteamAPI_Init() failed; unable to update local steamclient. Continuing with current version anyway.

Server logging data to file logs/L0804008.log
L 08/04/2011 - 18:42:48: Log file started (file "logs/L0804008.log") (game "cstrike") (version "48/1.1.2.6/Stdio/4883")
L 08/04/2011 - 18:42:48: Server cvar "sv_contact" = "email@yoursite.com"
Connection to Steam servers successful.
   VAC secure mode is activated.
L 08/04/2011 - 18:42:56: World triggered "Round_Start"
status
hostname:  test server
version :  48/1.1.2.6/Stdio 4883 secure  (10)
tcp/ip  :  192.168.1.237:27015
map     :  de_dust2 at: 0 x, 0 y, 0 z
players :  0 active (8 max)

#      name userid uniqueid frag time ping loss adr
0 users

And I don't know if it is important I am connected with wireless on my router that is connected to my phone.

---

### Post by linuxford on 2011-08-04
I don't know I'm still a noob but conceptually it seems you may have different things at work here.

1. You have the router configuration itself that is responsible for authorizing and forwarding packets. 
2. You have the server itself that I believe does something similar in authorizing, receiving, and sending packets, etc.
3. You have the socket which is composed of the IP address plus the port. 
4. You have the game itself to setup.
5. You may need certain directory permissions that may also come into play.

I am new but these can get a little tricky. Some of this is automatically done, but it may be helpful to think about each piece and take it a step at a time to get it working and check it if you can somehow.

You are on a local lan I am assuming so it should be simpler. Perhaps first start with a basic ping from the client computer to your server just to make sure the packets are being received. 

Then also I think there is a command that you can run on your server to make sure that the port is open and receiving communication.

Those two steps may help just to make sure that the socket is good to go. Then maybe you can check on the game itself and some of the settings, etc., plus again maybe those other issues mentioned at top may come into play.

---

### Post by is kla. on 2011-08-04
Thanks for your reply, I'll sleep it over and start fresh tomorrow, afterwards I will post the results.

---

