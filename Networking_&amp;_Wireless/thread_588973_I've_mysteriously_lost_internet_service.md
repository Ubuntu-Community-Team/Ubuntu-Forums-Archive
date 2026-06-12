---
title: "I've mysteriously lost internet service"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2007-10-23
I upgraded to Gutsy Gibbon on it's release date. Internet was working fine with my Broadcam 4318 wireless card.

But starting today, every software I use says I have internet and am connected (whether it's wireless or wired) but nothing connects to the internet. Not my browsers, not my gdesklets, not my IRC clients. Nothing. iwconfig, Wireless Assistant 0.5.7, and WICD all say I'm connected just fine. It's just not adding up and I have no idea how to start trouble shooting this.

I get my internet through a router with two other computers accessing internet from it (one wired, one wireless). So I know my router is working fine and that it's definitely getting internet.

Any ideas out there? My laptop's useless without internet.

---

### Post by Lambert on 2007-10-24
> **mahasmb said:**
> I upgraded to Gutsy Gibbon on it's release date. Internet was working fine with my Broadcam 4318 wireless card.

But starting today, every software I use says I have internet and am connected (whether it's wireless or wired) but nothing connects to the internet. Not my browsers, not my gdesklets, not my IRC clients. Nothing. iwconfig, Wireless Assistant 0.5.7, and WICD all say I'm connected just fine. It's just not adding up and I have no idea how to start trouble shooting this.

I get my internet through a router with two other computers accessing internet from it (one wired, one wireless). So I know my router is working fine and that it's definitely getting internet.

Any ideas out there? My laptop's useless without internet.

If it says you're connected then let's try some simple ping troubleshooting.

Run the following commands and if any of them give you trouble, post what that is and we can take it from there.

You can open network tools from the menus or do this from the command line.

From command line
```

ping -n 3 127.0.0.1

ping -n 3 192.168.0.2

ping -n 3 192.168.0.1

ping -n 3 91.189.94.199

ping -n 3 www.ubuntu.com

```

replace 192.168.0.2 with the ip address assigned to your internet device. You can find this through iwconfig or ifconfig.

replace 192.168.0.1 with the ip of your router it that is not it.

---

### Post by mahasmb on 2007-10-26
I don't know what happened. Again I didn't do anything but the internet seems to be working again.

---

### Post by Bubbo on 2007-10-26
I get the same problem, internet works fine, then after awhile, it just stops. I can access my router config menu but nothing online. However, restarting the computer fixes it, until it happens again.

I have a broadcom 4318 as well, and i am using ndiswrapper and wicd to connect. This setup worked fine on feisty.

---

