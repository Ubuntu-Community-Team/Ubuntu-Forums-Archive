---
title: "Network Messenger"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by //randi on 2007-10-23
hey, 

is there a network messenger available to be able to use not necessarily over the inernet but just like over a network...nothing big but just very simple.  Does ubuntu have anything built in that could be used?

-thanks

---

### Post by wolfvorkian1 on 2007-10-23
If your lan has some windows machines in it, you can activate Net Meeting in XP and then send popups with the following command. I believe earlier windows OS have a popup program that isn't turned off by default like XP is. Apparently it can be a security risk. 

```
smbclient -M Netbios name -U name
```then if you 'connect', you type your text, hit enter and then control-D and the popup shows up on the monitor of who you sent it too. If they are all *nix machines, I don't know. There is a front end for the above command called linpopup but it really isn't necessary and doesn't speed things much or any at all. Netbios name if you don't know is the windows computer name. 

I have fun with it, telling my daughter "it is time to do the dishes", etc. The popups are pretty hard to ignore and can be annoying as hell, which is why I use them on her. Oh - if you ignore the -U name in the command above, it says the sender is whatever your login name is on whichever 'buntu you use.

---

### Post by CheshireMac on 2008-05-19
Okay, so I'm interested now too. I'd like to work out the syntax in this, but that's where I always run into trouble with Terminal-based clients.
So, hypothetically, let's say that I run the command:
```
smbclient -n VegasGirls3 -U Tara
```
Where VegasGirls3 is the network name, and Tara is the Windows username. Would that be correct?
If not, please help. ~LOL~ If so, what then, in order to send messages? This seems like a really handy thing to be able to do, and I'd like to be proficient in its use. 
Thanks for any help. :)

---

