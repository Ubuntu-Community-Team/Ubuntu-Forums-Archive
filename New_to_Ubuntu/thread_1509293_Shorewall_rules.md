---
title: "Shorewall rules"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by derek71 on 2010-06-14
I am setting up a server with Ubuntu 10.04 with Shorewall v4 to control access.

I have successfully implemented rules for accepting traffic between the firewall and the rest of the world.

The final modification I wanted to make is to reject all traffic not explicitly allowed by the rules I have created.  When I add a reject rule between the external network and the firewall, I can no longer connect to the machine.

Checking the logs I don't see any errors during startup of shorewall.

I have attached my rules/policy files for reference. I obfuscated the addresses a little.  The policy file is simple, for development purposes I have placed the rest of the network in the DMZ.

---

### Post by gdonwallace on 2010-06-14
My first suggestion would be to go to the Shorewall forums.  

That is a pretty specific, program wise, question You are asking.  Not that you wont get an answer from someone in this forum; but it would probably happen a lot quicker if you posted this question to the forums for Shorewall.

---

