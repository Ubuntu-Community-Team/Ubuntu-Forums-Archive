---
title: "Horrible ping rates"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-14
While Playing Wolf ET I have noticed I have really bad pings

While playing on windows I had a ping of 30 on a bba clan server

But on Ubuntu 8.10 I have a ping around 150 on the same server.

Is there a way to fix this?

---

### Post by Peter09 on 2008-12-14
Are  you pinging by ip address or name?

---

### Post by nakama85 on 2008-12-14
> **Peter09 said:**
> Are  you pinging by ip address or name?

uhh good question for witch i have no answer.

the only thing I know is that at the end of each match it shows player stats and each players ping.

---

### Post by Peter09 on 2008-12-14
I just wondered whether it was a difference in name resolution services.

If you type 

```
route -n
```

in a terminal it will give you you routing setup.

Are you  able to issue a ping in the terminal

```
ping <servername>
```
and
```
ping <server IP>
```

---

### Post by nakama85 on 2008-12-14
yes my pings all average 30-40. So I guess it is only while I am playing. Any fix for that?

---

### Post by Peter09 on 2008-12-14
Well, I cannot go much further with this, just check that the difference is always there between windows and Ubuntu.

Also - are you playing on an account with Compiz running, it can affect performance.

---

### Post by nakama85 on 2008-12-14
> **Peter09 said:**
> Well, I cannot go much further with this, just check that the difference is always there between windows and Ubuntu.

Also - are you playing on an account with Compiz running, it can affect performance.

how to disable compiz (and renable it for that matter) and what does compiz do?

---

### Post by iponeverything on 2008-12-14
its the visual effects.

go to system->preferences->appearance

go to the "visual effects" tab and change it to "none"

---

### Post by nakama85 on 2008-12-14
> **iponeverything said:**
> its the visual effects.

go to system->preferences->appearance

go to the "visual effects" tab and change it to "none"

already set to none.(no need for fancy looks as long as it works)

So do you think this could just be a problem with the game?

---

### Post by epitaph on 2008-12-14
Can you post a traceroute from your computer to the server IP address?

```
traceroute SERVER_IP_HERE
```

Have you changed some of your cvars inside of Enemy Territory? What if you use your configuration from your windows install? The difference your describing is huge and I find it quite a challenge to believe it was simply caused by changing the operating system. Perhaps some external factors have come into play.

---

### Post by nakama85 on 2008-12-15
> **epitaph said:**
> 

Have you changed some of your cvars inside of Enemy Territory? What if you use your configuration from your windows install? The difference your describing is huge and I find it quite a challenge to believe it was simply caused by changing the operating system. Perhaps some external factors have come into play.

don't know what cvars are

I no longer have windows

this happens with all servers.

Furthermore when I try to connect now it takes forever to download maps(if at all) and it almost kills my internet connection. If I quit the game and try to access a web page it takes a good few minutes before my speed is back to normal

---

