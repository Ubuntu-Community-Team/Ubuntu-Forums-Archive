---
title: "help with ISPconfig"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by gorilly on 2007-02-07
Hi All,

I'm hoping someone on here has some experience with ISP config.

I set up a ubuntu 6.06LTS server and followed the guide on howtoforge for making the perfect web server.

i then installed ISPconfig and its all running ok.

the question i have is so stupid im embarrased to ask but i cant figure out where i am going wrong.

i am trying to set up a hosting account for one of my friends, he wants to host a web page via my webserver (so i am his ISP).
i made his account in ISP config, he can log into the user control panel etc, he can upload his site etc.

the questions is where do i view his site?!?!

so for example i have a ispconfig server at 192.168.1.100
i have created him a website called websitetest
surely to get to his site internally it will be something like 192.168.1.100/websitetest??

Any help will be much appreciated!

thanks

just to add to my stupidity ive posted this in the wrong place! please delete this post admin

---

### Post by xciso on 2007-03-27
Have u try: [https://192.168.1.100:81](https://192.168.1.100:81) or [http://192.168.1.100:81](http://192.168.1.100:81)
It depens if u set SSL or not.
First time the pass and username is admin.

Good luck!

---

### Post by blmartin777 on 2007-06-08
> **gorilly said:**
> Hi All,

I'm hoping someone on here has some experience with ISP config.

I set up a ubuntu 6.06LTS server and followed the guide on howtoforge for making the perfect web server.

i then installed ISPconfig and its all running ok.

the question i have is so stupid im embarrased to ask but i cant figure out where i am going wrong.

i am trying to set up a hosting account for one of my friends, he wants to host a web page via my webserver (so i am his ISP).
i made his account in ISP config, he can log into the user control panel etc, he can upload his site etc.

the questions is where do i view his site?!?!

so for example i have a ispconfig server at 192.168.1.100
i have created him a website called websitetest
surely to get to his site internally it will be something like 192.168.1.100/websitetest??

Any help will be much appreciated!

thanks

just to add to my stupidity ive posted this in the wrong place! please delete this post admin

Do you have a url for the websitetest? You need to tell ispconfig that when someone types your url say [www.websitetest.com](www.websitetest.com) that it points to that virutal server that you set up. Otherwise you will get the SharedIP page.

---

