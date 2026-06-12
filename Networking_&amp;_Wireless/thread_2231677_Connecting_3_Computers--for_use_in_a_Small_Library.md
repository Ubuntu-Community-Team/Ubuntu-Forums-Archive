---
title: "Connecting 3 Computers--for use in a Small Library"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by Rebecca_Chapman on 2014-06-27
Dear all,

I am a teacher at a school in South Korea. 

We have a small library here (and 3 previously messed-up Windows OS computers).

I installed Ubuntu on these computers, and as far as I know these computers connect to a master server in an office near the library (same building).

After installing Ubuntu, I noticed several error messages about not being able to connect to the network (I can only imagine this must be the infamous "server is an office nearby" network ...possibly). There is no issue connecting to the internet, but I want the computers to connect to each other (like a happy family).

I want to run Readerware so that we can check books in and out, but the computers need to communicate with each other to make it possible.

Any help/advice for this noob here is greatly appreciated. 

Sincerely,

Rebecca

(P.S. Is there a book/library database program for Ubuntu?)

---

### Post by steeldriver on 2014-06-27
Hello and welcome to the forums

Can you be more specific about the exact errors you are getting? Networking is a multi-layered thing - and that would help to narrow down where to look

---

### Post by SeijiSensei on 2014-06-27
You could build a small network with just the library computers and a [router]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010065%208000&IsNodeId=1&bop=And&ActiveSearchResult=True&page=1").  Connect the local machines to the router, then tell it to use the machine upstream as its default gateway.  (That might be as simple as having the router use DHCP to get its configuration information from the upstream server.)  That would create a small local network among your machines but still enable connections to the Internet.

---

### Post by yancek on 2014-06-27
> After installing Ubuntu, I noticed several error messages about not being able to connect to the network 

What network?  You said you haven't set it up yet.  Do you mean connecting to the server in the other office?  Networking Linux computers is usually done with nfs (network file system) which has been around and used for decades.  Lots of support and documentation.  Do you want to share files from and to eachUubuntu computer?  The question then is, do you just want to network the 3 Ubuntu computers or do you want to include the 'server' in the office?  What's on the server for an operating system?

---

### Post by Bucky Ball on 2014-06-27
Welcome.

> **SeijiSensei said:**
> You could build a small network with just the library computers and a [router]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010065%208000&IsNodeId=1&bop=And&ActiveSearchResult=True&page=1").  Connect the local machines to the router, then tell it to use the machine upstream as its default gateway.  (That might be as simple as having the router use DHCP to get its configuration information from the upstream server.)  That would create a small local network among your machines but still enable connections to the Internet.

^^^
This

... is where I'd be going. Elegant and simple. The whole library will then be going out through one gateway (the router). Possibly more secure also. Naturally, you would need to let the IT crew (or person) know what you are intending to do and that three computers are about to disappear to be replaced by one router at their end (which could be sending a fake IP, i.e. not the one you are using to connect to it which will probably be 192.168.0.1 or something like it). 

Not sure what you need to set up to have the networked machines recognise computer names on the network, but I always set-up static IPs for each machine. For me, easier.

PS: Using a router will make it very simple to network with other wireless devices in the library, most notably printers! Another note: depending on the size of the organisation and IT procedures, some organisations disuade or ban 'networks within networks' preferring ALL machines to be connected individually to the organisations main server.

---

### Post by Rebecca_Chapman on 2014-06-27
Hi!

Its actually Saturday for me in Korea, but I will write the specific error when I get a chance. Basically, these machines have been sitting in the school's library (looking as if they have worked) for the last 6 years, but have never actually been used (and if they had, someone severely messed-them-up).

So, I thought the best solution would be to erase everything and install the Ubuntu OS on them.

When I lauched Ubuntu on the machines for the first time, and error message appeared in the top corner in a square, dark blue box. It said that it can no longer connect to the network (yada yada).

This could have always been a problem, but I would have no idea of knowing. 

The main thing is: There is no problem with the internet at this point. 

I will write as soon as I know the specific error.

---

### Post by Rebecca_Chapman on 2014-06-27
I think I could pull this off--connecting the computers to the same router.

 It just depends if I can find where the wires end. They seem to travel up into the ceiling, but maybe there is a closer termination point. 


Also, any word on a Ubuntu Library software? If not, its alright. 

The most important thing is not really for the computers to work on a large network, but for them to work in the library with each other. 


Thank you all for your help! I will check back on Monday when I am at my school.


> **Bucky Ball said:**
> Welcome.



^^^
This

... is where I'd be going. Elegant and simple. The whole library will then be going out through one gateway (the router). Possibly more secure also. Naturally, you would need to let the IT crew (or person) know what you are intending to do and that three computers are about to disappear to be replaced by one router at their end (which could be sending a fake IP, i.e. not the one you are using to connect to it which will probably be 192.168.0.1 or something like it). 

Not sure what you need to set up to have the networked machines recognise computer names on the network, but I always set-up static IPs for each machine. For me, easier.

PS: Using a router will make it very simple to network with other wireless devices in the library, most notably printers! Another note: depending on the size of the organisation and IT procedures, some organisations disuade or ban 'networks within networks' preferring ALL machines to be connected individually to the organisations main server.

---

### Post by bobnn on 2014-06-28
So if you have internet connectivity, you must have network connnectivity (whatever tyhe warning box says) and the issue is connectivity to the server.

So, can you ping the server?

```
ping <server_name>

ping <server_IP>

sudo traceroute -I <server_IP>
```

also, what do the following show?

```
nslookup <server_name>

ip addr ls

ip rou ls

ip link ls

```


Editted to add: I would avoid reconfiguring the netowrk until there is a good understanding of what is going on. You may create more problems for other people by doing that.

---

