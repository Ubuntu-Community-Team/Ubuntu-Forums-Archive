---
title: "Disabling Internet access in wireless network"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by artursm on 2008-09-25
Hi, we have a wireless network here at home, to which I'm connected. All computers share an internet connection through this network. The thing is, I already have a separate (private) internet connection here at my computer. If I keep both connections running, the system usually ends up using more bandwidth from the wireless than the private, which is bad for the other computers.

That's why I'm asking this. How can I disable my own internet access through the wireless network? I'd rather not disconnect from the actual network, cause it's useful for file transfer and stuff.


Good evening, and thanks in advance.

(while we're at it, can anyone tell me how to keep track of how much data comes in on a weekly/monthly/yearly basis. I use Knemo, but it only tells me how much comes in each time I connect.)

---

### Post by pytheas22 on 2008-09-25
What is your private Internet connection?  Do you mean that you have a wired connection available?  Or are you talking about a VPN or something?  Please clarify so that we can figure out how to solve the problem.

As for bandwidth logging, I don t know of any easy way to do it over a long period of time, although there must be some program out there to do it.  Did you check your router, though?  It may be able to keep track of that for you.

---

### Post by artursm on 2008-09-25
Sorry if I wasn't specific, english is not my native language, so I'm not sure what everything's called. 

It's not a serious problem. 
To be clear: my house has a modem connected to a wireless router. We all share a wireless network, and access the internet through this network (thanks to the modem, of course:P). I'm running (k)ubuntu 8.04, and I'd like to block my own computer from accessing the internet through this network. I still want to be connected to the network itself, to share files with the other computers in the house. I just want my computer to stop sucking up the internet bandwidth.*


*(the reason for that is that I already have a separate internet connection that only I can use.)

Thanks again,:)

---

### Post by pytheas22 on 2008-09-26
I guess you would want to have two IP addresses in that case. I know that this can be done but I'm not sure how.  You would need to assign routes to your wireless interface so that it would only be used to connect to IP addresses in the 192.168.X.X range, and the other networking device in your computer would be used for all other traffic.

Let me do some searching and see if I can come up with anything that will explain exactly how to do this.

Also, for a bit more clarification: you have a wireless card connecting to your wireless router, right?  And a separate card (ethernet or wireless?) connected to your private Internet connection?

---

### Post by artursm on 2008-09-26
Yes. I have an ethernet card connecting to my private internet, and a wireless (USB) adapter conecting to the router.

---

### Post by willca on 2008-09-26
check the route your nics have.

Do this right after your computer boots up and you have not run any software yet.

sudo netstat -rn | egrep "Default|default|0.0.0.0"

May look like this.

192.168.1.0   0.0.0.0  255.255.255.0   U   0 0          0 wlan0
0.0.0.0    192.168.1.1     0.0.0.0     UG  0 0          0 wlan0

So what you need to do is delete the route for wlan0 since thats what I thought you want to rid of internet access ya?

sudo route del -net 0.0.0.0 netmask 0.0.0.0 dev wlan0

I am not 100% sure on the syntax I used since I dont want to try it out and break my connection since I am vpn in at work at the same time while goofing around here in the forums when I dont do anything. Another story.

So try that out and let me know if dont work.

---

### Post by artursm on 2008-09-29
It actually worked. thank you very much :)

---

