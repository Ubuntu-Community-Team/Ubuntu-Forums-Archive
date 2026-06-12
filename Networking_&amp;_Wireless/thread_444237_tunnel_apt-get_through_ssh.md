---
title: "tunnel apt-get through ssh"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by eentonig on 2007-05-15
Hi,

I've searched the forums but couldn't come up withe the correct keywords to find what I need.

At work, I can't get apt-get to reach the repositories. I do however succeed in setting up an ssh tunnel to a machine at home.

I can open remote X programs and stuff. But how would I set up ssh to be able to install through the ssh tunnel. That basically means I need my remote machine to forward the apt-get traffic coming from the ssh tunnel.

---

### Post by bmartin on 2007-05-15
The term you're looking for is "proxy". The person [here]("http://ubuntuforums.org/showthread.php?t=438763&highlight=apt-get+proxy") had a similar problem; you might want to ask them to post their solution. I also have to work around work restrictions to do certain things, such as connect to my laptop at home using SSH.

---

