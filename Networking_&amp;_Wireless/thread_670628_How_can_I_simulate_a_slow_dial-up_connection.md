---
title: "How can I simulate a slow dial-up connection?"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by djaquay on 2008-01-17
Perhaps this is a silly question, but I'd like to open up a bash session somehow, and have its output simulate a slow dial-up connection.  The processing can/should run at normal speed, but all input/output (or at least output) should run at a specified rate (i.e. 300, 1200, 2400, 9600 baud, etc.)

Is there a term program (I use konsole, but would install another) that lets you limit output speed like this?

Thanks,
Dave

---

### Post by jetsam on 2008-01-18
It's a bit complex, but you can do it with ssh and [iprelay]("http://www.stewart.com.au/ip_relay/").  

If you don't have these installed already:
```
sudo apt-get install ssh
sudo apt-get install iprelay
```

then, start iprelay in one terminal:
```
iprelay 2222:localhost:22 -b 2880
```

This gets iprelay to listen to localhost port 22 (the ssh port), and redirect it's rate limited version to port 2222.  It limits the rate to 2880 bytes per second to start with. Then, in another terminal window:
```
ssh <yourusername>@localhost -p 2222
```

This starts ssh connecting through port 2222.  Put in your password, and it's kind of like a 28.8 modem.  

Now in the iprelay terminal, you can change the bandwidth to whatever you want,  The commands "sh bandwidth" and "set bandwidth <number>" show and set the current bandwidth limit for iprelay in bytes per second.  "sh stat" shows statistics for the connection, and control-c quits and closes the connection.  

There's more info in the web page I linked above, and there's a man page for iprelay.  It's pretty flexible.

---

### Post by djaquay on 2008-01-18
Thanks very much.  That gets me most of the way there, I think.  It'd be nice to have things displayed a character at a time, maybe by having ssh deliver its output more granularly, but it's a good start.

Regards,
Dave

---

