---
title: "firewall not enabled by default"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by mojolobo on 2009-05-14
Ive notice after installing 9.04 . The firewall is not active. Typing 'sudo iptables -L' , i get 3 short line with 'accept'. is this normal?

Ive installed gufw and enabled . 


is there a function where i can see the block list , like in firestarter?

---

### Post by mikewhatever on 2009-05-14
The question is do you need a firewall. Here is a short read for you.
[http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by skymera on 2009-05-14
If you're behind a router you're safe and IPtables isn't really needed.

If you need to configure Ubuntu for VNC you will need to configure IP tables.

---

### Post by Didius Falco on 2009-05-14
Welcome to the Ubuntu forums.

It may ease your mind to go to the GRC site, set up and run by Steve Gibson of SpinRite fame. He has a tester called "Shields Up!!" that will test to see if it can get to your PC.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

You should feel reassured after seeing the results there.

Regards,

Didius

---

### Post by mcduck on 2009-05-14
> **mojolobo said:**
> Ive notice after installing 9.04 . The firewall is not active. Typing 'sudo iptables -L' , i get 3 short line with 'accept'. is this normal?

Ive installed gufw and enabled . 


is there a function where i can see the block list , like in firestarter?
Yes, that's normal. The default setup of Ubuntu has no running services that would respond to incoming connections from network, thus a firewall isn't needed.

---

### Post by cariboo on 2009-05-14
> **Didius Falco said:**
> Welcome to the Ubuntu forums.

It may ease your mind to go to the GRC site, set up and run by Steve Gibson of SpinRite fame. He has a tester called "Shields Up!!" that will test to see if it can get to your PC.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

You should feel reassured after seeing the results there.


Regards,

Didius

The problem with Shield Up is that it only tests the firewall on your router, it can't get past that firewall, so it can't test the firewall setup on the computer.

---

### Post by Didius Falco on 2009-05-14
> **cariboo907 said:**
> The problem with Shield Up is that it only tests the firewall on your router, it can't get past that firewall, so it can't test the firewall setup on the computer.

Good point. As long as my router firewall is doing the job, I feel pretty secure, but I may take it out of the loop and test it that way, just to see the results.

Regards,

Didius

---

### Post by Didius Falco on 2009-05-15
In the interest of complete testing, and satisfying my own curiosity, I took the router firewall out of the loop and retest at GRC. I had the same results - nothing could get in.

I'm now back behind my hardware firewall, backed up by the software firewall and all is well.

Regards,

Didius

---

### Post by NHArticleTen on 2009-05-15
> **Didius Falco said:**
> In the interest of complete testing, and satisfying my own curiosity, I took the router firewall out of the loop and retest at GRC. I had the same results - nothing could get in.

I'm now back behind my hardware firewall, backed up by the software firewall and all is well.

Regards,

Didius

Great!

Thanks for reporting back on that.

Steve Gibson and GRC are awesome!

---

