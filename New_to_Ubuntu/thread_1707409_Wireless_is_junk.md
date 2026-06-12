---
title: "Wireless is junk"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by DFickel on 2011-03-15
Hey guys, had ubuntu for a few weeks now, only problem i have is it WILL NOT connect to any wireless system except for the one at my frats house. Not the campus net, my home wifi, girlfriends house's wifi etc. the passwords are right but the wireless on ubuntu just sits there and tries to authenticate and keeps popping up the password box on me. any ideas?

---

### Post by coolbrook on 2011-03-15
Which adapter are you trying to use?

What is the terminal output of:

lspci
ifconfig
iwconfig

What kind of encryption is enabled on the routers to which you're attempting to connect?

---

### Post by DFickel on 2011-03-15
ha uh i havent done anythin with the settings on the system, i just turn on and off the wireless card, nothing more. the networks arent anything special, just peoples routers that are hooked to dsl or other hard wire connections. Like i said it works on the network here at the house but no where else

---

### Post by capitalfear on 2011-03-15
i had the same problem, but with my windows7 partition on my system76 laptop, like he said it might be the encryption, try at your house changing it to wep just to see if it works

---

### Post by TBABill on 2011-03-15
Just a humble suggestion....your thread title is not the friendliest. For most all, wireless works great. Many have issues in the beginning with specific hardware devices, but to make such a blanket analysis of something without the experience to support it does not make your post one people will jump in to assist with. 
 
I'd also suggest offering more information when making a post, such as what you are working with (exact info on the device itself), encryption at each location, what you have tried, what you found through online searches, etc. This may help on future posts for assistance to help clarify the problem a bit to get you the most appropriate and clear answer early on instead of being prompted along the way with additional questions by other members who need more to go on.
 
Your issue sounds like it's encryption related and the suggestion to try changing encryption at home is a good one. Maybe start with it not encrypted at all (open network) and if you can connect, then try to go to WEP first, then move up to WPA. The normal mode into your router will be to enter 192.168.1.1 into a browser, then login with username/password the router was setup with, then make changes and see if you can connect with each change. Once you cannot, then the problem should be pretty easy to identify as "fails at x point".

---

### Post by coffeecat on 2011-03-15
@DFickel. I have another suggestion, not so humble. :wink: Post the output that coolbrook asked for.

---

