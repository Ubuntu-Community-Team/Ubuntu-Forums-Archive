---
title: "dsl"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by gridd on 2010-12-14
hi I have just had a problem logging on to my isp (static)when going  to network manager wired networks Auto etho  then after auto etho connects I usually have to manually go to dsl and click connect.this usually works but this morning I kept getting a popup box requesting my dsl isp password.This has never happened before.Is this a bug or spyware my password is correct in my DSL settings. and eaven  after i got desperate and filled in the password request it didn't let me connect it just came up with the same box and request again I had to 1)  disconnect the modem  switch off the computer twice before it connected again

---

### Post by gridd on 2010-12-16
bump

---

### Post by gridd on 2010-12-17
Hummm doing the same thing cannot connect at all now. looks like complete uninstall again.

---

### Post by CharlesA on 2010-12-17
It sounds like it's not authenticating properly. Have you contacted yer ISP?

Also, you could try booting off a livecd and see if it'll let you connect or not, That would rule out software.

---

### Post by gridd on 2010-12-17
> **CharlesA said:**
> It sounds like it's not authenticating properly. Have you contacted yer ISP?

Also, you could try booting off a livecd and see if it'll let you connect or not, That would rule out software.

they dont seem to like linux I have trouble of minor sorts every time I change from windows to ubuntu.Three or four attempts to connect. Could the static ip be the problem.

I will try a live cd and get back to you.

---

### Post by gridd on 2010-12-17
ok tried an old hardy live the only live I have and I cant even get a lan connection.yet no problem at all with win 7 in the next partition.which I am on now.?? maybe I should ring my Isp.or a fresh install I bet will do it.

---

### Post by CharlesA on 2010-12-17
I'd suggest trying to more recent livecd (Lucid or Maverick) and see if it'll work for you.

---

### Post by QLee on 2010-12-17
[QUOTE=gridd]...
 Could the static ip be the problem.
....[/QUOTE]

Are you using static IP on the Windows connection.

Do you actually have a static IP from your ISP (outfacing), generally you have to pay a higher fee for a static IP.

---

### Post by gridd on 2010-12-17
> **QLee said:**
> Are you using static IP on the Windows connection.

Do you actually have a static IP from your ISP (outfacing), generally you have to pay a higher fee for a static IP.

yes,to both,the same computer, Ethernet connection. When I check the IP is always the same.I presume that is outfacing.

---

### Post by gridd on 2010-12-17
> **CharlesA said:**
> I'd suggest trying to more recent livecd (Lucid or Maverick) and see if it'll work for you.
will do cheers.

---

### Post by QLee on 2010-12-18
If I were you, certainly before I did a reinstall or upgrade, I would go to Network Manager-->Edit Connections-->DSL tab and delete the connection you have set up for your DSL, then I would add a new connection, entering all the necessary stuff.

---

### Post by gridd on 2010-12-18
> **QLee said:**
> If I were you, certainly before I did a reinstall or upgrade, I would go to Network Manager-->Edit Connections-->DSL tab and delete the connection you have set up for your DSL, then I would add a new connection, entering all the necessary stuff.

Ok thanks will do.

---

### Post by gridd on 2010-12-18
> **gridd said:**
> Ok thanks will do.
Yes this was successful thanks to QLee and  CharlesA.

---

