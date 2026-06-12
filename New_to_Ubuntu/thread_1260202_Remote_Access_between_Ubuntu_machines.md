---
title: "Remote Access between Ubuntu machines"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by KyleRickards on 2009-09-07
Hi all

My girlfriend has just installed Ubuntu on her laptop and I am trying to remotely access it to fix some settings for her.

I have tried vncviewer and Remote Desktop but don't seem to connect. I am trying to follow the guides on the internet but think that I am doing something (basic!) wrong. Could anyone assist.  Remote Desktop Access is enabled on her machine and she has told me the ip and hostname of her machine.

Thanks
Kyle

---

### Post by Jazzy_Jeff on 2009-09-07
Is she on the same network as you or does she live somewhere else? If she lives somewhere else you will need to get her true ip address and not the one the router has assigned her. She can goto [http://www.ipchicken.com](http://www.ipchicken.com) and it will show her what the ip address is.

---

### Post by KyleRickards on 2009-09-07
Thanks Jeff, stage closer. When I start vncviewer and use the ip address we just got, it just seems to put me in localhost mode and just seems to try and show my desktop?

Kyle

---

### Post by Jazzy_Jeff on 2009-09-07
Some one else will have to help you from here. I have not use the remote desktop function and I am not sure how to set it up.

---

### Post by mapes12 on 2009-09-07
I struggled for ages to access my Dad's remote machine over the internet. We eventually got the connection to work using this simple app to configure remote desktop on both machines: [https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

If the other machine has the ISP IP address assigned dynamically (most do) then what I have done is registered a free domain at [http://www.dyndns.com/](http://www.dyndns.com/) and configured it to automatically track what IP address the ISP has assigned. You will need to configure it with ddclient (it's in Synaptic) to keep track of the dynamic address. I followed this HowTto: [http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)

---

### Post by KyleRickards on 2009-09-07
Hi Mapes

Have got the app, I have checked what IP she has assigned at the moment.  I guess I have to open the port it suggests my router? Her side has just asked for my IP address (which it showed me on screen and told me to tell her). Sorry for being bit clueless!

Kyle

Edit: I can now connect and see the desktop but can't do anything. She definitely has allow user to control desktop enabled? Is there something I need to press?

---

### Post by KyleRickards on 2009-09-07
Solved - not sure what I did but it worked! Thanks all!

---

