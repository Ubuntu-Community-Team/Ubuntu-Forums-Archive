---
title: "No network response until after logon"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by DHag on 2008-11-05
I have an Ubuntu 8.04 server. I installed it with LAMP options. I have been working/learning to set up Apache for reverse proxy.

When the server is rebooted, I cannot "see" it from the network. It won't respond to PING, and I cannot hook to it with mapped network drives or PUTTY.

So I go to the server itself, and log in to the console. I do nothing more than PING one of the other servers from it, and it works. Then I log off. 

After that, I can now "see" it from the network.

This has just started recently, after I started trying to configure Apache.

Can anyone tell me what to look for? I can't use a server that requires logon from its console before it will work.

Could it be I have screwed up the networking somehow while trying to configure Apache? Would uninstall/reinstall Apache (to get back to default configurations) be a way to fix it?

---

