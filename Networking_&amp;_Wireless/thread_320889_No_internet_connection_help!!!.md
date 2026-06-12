---
title: "No internet connection help!!!"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Downunder connections on 2006-12-18
hi,
im totally new to this ubuntu thing, i just installed it just before and i dont have any internet connection through my dsl modem cable or through my inbuilt wireless ability on a compaq presario m2000. Is some able to help me out please, and yes i know there is a lot of forums about this problem, but they its just gobbles on about nothing really. im abit of a computer ilitteret, like i know bit but not all the lingo talk, so please try and keep it simple
thankz 4 all ur ideas :)

---

### Post by n00b@linux on 2006-12-18
It's possible your ethernet interface (ie. your 'network adapter', 'ethernet card', 'NIC', etc. etc.) has not been detected.
Open a terminal session, ie. navigate with your mouse to Applications > Accessories > Terminal and click on it to open it.
In the terminal, type```
lspci
```You should see your ethernet adapter listed.  
Is it a Realtek RT8139L Fast Ethernet Adapter?  
In any event, take a note of the details and post them to this thread.
Next, run```
ifconfig
```to see if your NIC is active.
If you don't see it listed, try:```
sudo ifconfig eth0 up
```(assuming your NIC is 'eth0' which is should be - check the lspci results above to see what it's called)
Type in your password when prompted and hit <return>. 
Then re-run 'ifconfig' to see if the NIC has been detected. 
If it hasn't, copy and paste the results of the above to this thread.

---

