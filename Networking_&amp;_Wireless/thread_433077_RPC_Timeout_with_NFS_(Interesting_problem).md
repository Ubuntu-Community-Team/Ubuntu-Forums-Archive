---
title: "RPC Timeout with NFS (Interesting problem)"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by guysmiley25 on 2007-05-04
I got an e-mail from my ISP a while back saying that they will be down as of yesterday, just for 1-2 hours. And they where. That was no problem for me as I only needed to access my local network that day.

However when my internet was down, when I tried to mount my NFS share, I got at RPC Timeout message. when the internet returned it worked find again!

So why would my NFS share only work when I have internet, when my NFS share is local?

My setup is:
Cable Internet --> Ubuntu Server --> Switch --> Local Machines (Ubuntu).

Where my local machines mount there /home from the Ubuntu Server (via NFS).

On my Ubuntu Server I have masquerading setup for internet sharing. I kinda suspect this is whats causing the problem.

If I was not to use masquerading for internet would I use a proxy? I do not know much about proxy's but I would need to be able to access the internet for all sorts of all sorts of ports and types. eg SSH P2P etc. I understand that the good thing about proxy's is that they can cache stuff. I do not want to do this.

If I where to look into a proxy I would like something that is easy to setup and configure. I would like to look into Bandwidth, and User name/Password Control as well.

Maybe something that is really good, but hard to configure, but has a good frontend available for it?

Thanks

---

