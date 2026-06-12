---
title: "I need HELP from the experts regarding trouble with my PuTTY and FreeNX connections"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Getwild2 on 2006-07-21
I really hope you guys can help me because I'm at my wits-end with this remote-connect business.  ](*,) 

For the past several days/weeks/months I have been connecting to my Ubuntu box at home from work via both PuTTY and FreeNX.  Life is grand, everything worked great.  

This morning I try to connect and (I wish I would have hit print screen on this) I received a message- something about fingerprint, key, etc.  It was telling me that if I knew the host I was trying to connect to, to click OK/Yes to continue connecting.  I also received another message about the RSA key in the cache, I believe, something to that effect.  This also needed me to acknowledge by clicking OK/Yes to continue.  

When I try connect via PuTTY I get the following:
[COLOR="Blue"]login as: cstiff
cstiff@##.###.###.###'s password:
Access denied
cstiff@##.###.###.###'s password:[/COLOR]

Now I KNOW I can go home and enter in my username "cstiff" and my password and I will log on just fine.  It just won't authenticate through SSH for some reason, though it has in the past with no trouble.  

When I try to connect via FreeNX I get the following:
[COLOR="Blue"]"Server not installed or NX access disabled"[/COLOR]
(...after clicking Details...)
[COLOR="Blue"]NX> 203 NXSSH running with pid: 2772
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: ##.###.###.## on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.[/COLOR]

Now I get connected each time, it just wont authenticate.  I know its got to be a SSH key issue, just not sure what to do about it.  BTW, you should know that I'm just running the default NOMACHINE key with FreeNX, nothing special, also nothing special with my PuTTY sessions.  

Thanks for any and all help in advance.  This is very frustrating because I have lots of time while at work to play with my Ubuntu box, but some days I cant get in.  I had this issue once before but I was still an Ubuntu noob and thought reinstalling would fix it, LOL, it did but I never learned what the issue was.  I'm ashamed to admit I actually reinstalled Ubuntu in the past over this issue.  Oh well, live and learn.  

-Cory

BTW, I'm running Dapper...thanks again!

---

### Post by Getwild2 on 2006-07-21
Just as an update:
I called my wife to have her reboot my machine in case something did not load properly.  She did and I still have the same issues.  

I believe the issue is with my PC here, I dont know, I'm just not sure.

---

