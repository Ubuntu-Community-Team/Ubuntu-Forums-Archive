---
title: "Web Based Admin for Karmic Sever"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-12
Hi Forum,

As you can tell from the location of the post, I'm a complete beginner. I've had an Ubuntu server for about 3 days now and am just getting into the hows of each function that I need.

Whilst I'm trying to learn each function on a command line intimacy and edit each config file manually, time is tight and I could do with an easy way to set the not-so-important functions like printer sharing, time sync, disk monitoring...

I've seen posts about webmin and am toying with using it. Most of the threads start with a simple tutorial the very next post is from someone with lots of linux knowledge warning that webmin is not the right way to go and commandline is better.

Which web based-admin could I use? Can anyone point me to a resource that will help understand the risks and mitigation?

TIA



Rich

---

### Post by alphacrucis2 on 2009-11-12
> **RichardCL said:**
> Hi Forum,

As you can tell from the location of the post, I'm a complete beginner. I've had an Ubuntu server for about 3 days now and am just getting into the hows of each function that I need.

Whilst I'm trying to learn each function on a command line intimacy and edit each config file manually, time is tight and I could do with an easy way to set the not-so-important functions like printer sharing, time sync, disk monitoring...

I've seen posts about webmin and am toying with using it. Most of the threads start with a simple tutorial the very next post is from someone with lots of linux knowledge warning that webmin is not the right way to go and commandline is better.

Which web based-admin could I use? Can anyone point me to a resource that will help understand the risks and mitigation?

TIA



Rich

Apart from webmin, another management tool you could look into is called puppet. I think it is a client-server type app rather than browser based:

[An article here]("http://www.linux.com/archive/feature/143893")

puppet and puppetmaster are in the Ubuntu repos so you can install via synaptic. 

[Puppet Website]("http://reductivelabs.com/trac/puppet/wiki/AboutPuppet")

---

### Post by jhillyerd on 2009-11-12
Puppet is definitely not a beginner tool, and it's designed for people that need to manage tens to thousands of servers.  It really won't do anything except add a ton of learning curve for someone with a single server.

-james

---

