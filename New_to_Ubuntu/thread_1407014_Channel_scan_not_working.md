---
title: "Channel scan not working"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by gunnartr on 2010-02-14
I am using Haupauge HVR-1300. I am not sure which is the the Analog part and which is the digital part of the following 4VL driver.:

4L: Haupauge WinTV-HVR 1300 DVB-T/B [cx88_Blackbird]
4L: Haupauge WinTV-HVR 1300 DVB-T/B[cx8800]

I can't get "Capture cards" to do channel scan.
I inserted some channels at "Channel editor" but without  any luck. Here is a cut out from my Mythbackend.log. I did clear out all capture cards and created only the Haupauge [cx8800] card. I am stuck can some one get me going?


2010-02-12 22:17:02.119 MainServer::ANN Monitor
2010-02-12 22:17:02.180 adding: gunnar-tv as a client (events: 0)
2010-02-12 22:18:53.170 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-02-12 22:29:43.865 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-12 22:52:25.961 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-02-12 22:52:26.019 Using runtime prefix = /usr
2010-02-12 22:52:26.059 Using configuration directory = /home/mythtv/.mythtv
2010-02-12 22:52:26.110 Empty LocalHostName.
2010-02-12 22:52:26.151 Using localhost value of gunnar-tv
2010-02-12 22:52:26.200 New DB connection, total: 1
2010-02-12 22:52:26.259 Connected to database 'mythconverg' at host: localhost
2010-02-12 22:52:26.303 Closing DB connection named 'DBManager0'
2010-02-12 22:52:26.359 Connected to database 'mythconverg' at host: localhost
2010-02-12 22:52:26.421 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-12 22:52:26.466 MythBackend: Starting up as the master server.
2010-02-12 22:52:26.518 New DB connection, total: 2
2010-02-12 22:52:26.561 Connected to database 'mythconverg' at host: localhost
2010-02-12 22:52:26.614 New DB connection, total: 3
2010-02-12 22:52:26.655 Connected to database 'mythconverg' at host: localhost
2010-02-12 22:52:26.936 Channel(/dev/video0) Error: GetCurrentChannelNum(182.25): Failed to find Channel
2010-02-12 22:52:26.978 Channel(/dev/video0)::TuneTo(182.25): Error, failed to find channel.
2010-02-12 22:52:27.047 New DB scheduler connection
2010-02-12 22:52:27.087 Connected to database 'mythconverg' at host: localhost
2010-02-12 22:52:27.199 Enabling Upnpmedia rebuild thread.
2010-02-12 22:52:28.630 Main::Registering HttpStatus Extension
2010-02-12 22:52:28.670 Enabled verbose msgs:  important general

---

