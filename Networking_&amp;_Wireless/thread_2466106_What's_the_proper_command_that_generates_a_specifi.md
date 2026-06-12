---
title: "What's the proper command that generates a specific route that I should add to ubuntu"
date: 2021-08-19
forum: Networking &amp; Wireless
---

### Post by marietto2008 on 2021-08-19
Hello.

I would like to know what's the command to add this route on ubuntu :


[https://ibb.co/NT6hVzH](https://ibb.co/NT6hVzH)


I tried with this command :


**route add default gw 192.168.1.1 enp0s5**


but this route has been added :


[https://ibb.co/9HzLwtf](https://ibb.co/9HzLwtf)


The other entries that I have on ubuntu are correct. I mean the routes below :


[https://ibb.co/HP60Bs5](https://ibb.co/HP60Bs5)


as u can see,there are some wrong entries that I don't know how to fix. They are "_gateway" instead of "192.168.1.1" or "modemtim" and "metric" should be 100,but it is 0. can someone suggest me what's the right command that generates the route that I want ? Problem is that I'm trying to configure the network inside ubuntu guest vm,emulated with bhyve on freebsd and it needs that I add the missing route or it will give the error "Destination Host Unreachable"

---

