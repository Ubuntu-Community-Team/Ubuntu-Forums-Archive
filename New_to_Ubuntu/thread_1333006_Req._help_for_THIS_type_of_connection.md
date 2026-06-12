---
title: "Req. help for THIS type of connection"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by psychlopath on 2009-11-21
Ok, I've gotten my NBR to where it's booted 10 out of 10 times.  Amazing feat.  I've got it connecting to wireless hot spots.

NOW what I need help with is how to make a connection of a particular type.  If I knew what it was called, I'm sure I would have found something online, but I dont.

Anyhow, with my provider, what I have to do (there is no wired option..none at all...) is connect to a provided wireless point..THEN use that to connect to my provider.

The hotspots have no encryption.  Anyone can connect to them, but they are "Local access only,".  Once you connect to the hot spot, you (in windows) right click on connection manager and open another connection (one that thinks it's wired..but really isnt) to my provider that has the username and password, etc, etc.

I know, I know it sounds kooky and there are all sorts of solutions regarding finding the router, etc, etc.  It's just not an option for me here. I have to buy my Internet from the "Company store."

I'm not finding out how to do this in Ubuntu.  

What I'd like is 

A) Figure out what this type of connection is called, if it has it's own nomenclature 

and 

B)Figure out how to do it in Ubuntu.

What I've done:  In Ubuntu, connected to the hot spot.  Right clicked on the connection manager and set up a DSL connection, entered my username, password, etc, etc as far as settings go so that it SHOULD be good once it does connect.  Checked "Connect Automatically," and...now I cant figure out how to open the "wired," connection whilst connected to the wireless.

Suggestions??

---

### Post by etali on 2009-11-21
Is the connection you're referring to a VPN?

Try installing network-manager-pptp (you may also need pptp-linux), and then see if you can set up the other connection in Network-Manager?

---

### Post by psychlopath on 2009-11-21
Ah, VPN!  I had tried that and couldnt add one.  After installing your package that you mentioned, I think I'm a step closer!! Thank you!

Now..to diagnose the "The VPN connection to 'io-global' failed." message.

---

