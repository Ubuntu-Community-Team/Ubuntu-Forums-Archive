---
title: "Parental controls"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by baguahsing on 2010-06-03
What parental control programs are available for Ubuntu?  I know that the child can not have the root password.  I am used to using Windows and Nortons.

---

### Post by aeiah on 2010-06-03
there aren't really parental controls, just administrator controls. just plan what you dont want your child to have access to and create a user that doesn't have those privilages.

if you want to restrict online content, then it's certainly doable as well.

obviously, you aren't gonna know how to do that stuff from the get-go, but if you search you'll find a load of stuff. perhaps you didnt get very far because you were searching for parental controls instead of 'limit user access' etc

---

### Post by bodhi.zazen on 2010-06-03
What kind of controls do you want ?

Nothing replaces parenting.

Personally I have several children and I use Dansguardian to filter websites. It is not perfect, and all web filters take some time and effort to manage. After looking at the options I found Dansguardian + Privoxy was the easiest to manage.

No Filter will do everything all parents want, we all have different values, so you will likely need to customize them.

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

Alternates would include squid, but squid is IMO more difficult to learn and requires more initial customization then Dansguardian.

Dansguardin requires a second proxy, and Privoxy is easy to configure, light weight, and adds adblock as well.

So I find Privoxy + Dansguardin works well.

Oh, one last thing, I recently changed to OpenDNS which helps as well. IMO, "One stop shopping" such as OpenDNS works better then tools such as WOT, which would need to be installed per user and monitored.

[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

So those tools will get you in the general ball park.

IMO anything beyond that is your responsibility, as a parent, to monitor.

---

### Post by Georgia boy on 2010-06-03
+1 for OpenDns. I use it on my computer. Real good program.

Tom

---

### Post by pricetech on 2010-06-03
I used to block stuff in my router, which was very time consuming.  I reset the router to defaults (can't remember why now) and lost all that.

When I found out about OpenDNS, I signed up and we haven't had a problem since, nor have I had to block anything in my router.

Nothing replaces parental supervision though.  We have a rule about accidental encounters with undesirable sites as well.  If they stumble upon something accidentally and tell us about it as soon as it occurs, they're off the hook.  If I find it and they didn't tell us about it, they're off the computer.

Works for us.

---

### Post by greenwom on 2010-08-10
I agree with Opendns, it is a great way to block the bulk of content.

the DNS settings for the family filter are
```
208.67.220.123
208.67.222.123
```
Just log into you router and change them.  You should still make an account.

The next thing to do is build the transparent proxy filter.
(I'm still working on mine, so I can't tell you it's simple)
You need a computer with a 2nd Ethernet port.  so old pc form the basement with a $20 network card.

You can install Ubuntu server, shorewall, dnsmasq, and dansguardigan.
(there's is a bunch of configuring todo.  If you find a how to it takes about 2 hours)

You can also take that same hardware and install smoothwall firewall and then the dansguardian plug-in.

Both of these options take away the routing, PPPOE, and DNS functions of your router.  The new filter does the routing for you.  

This device is important.  It filters everything that opendns doesn't get and it's using it's own resources.  It doesn't slow you down as much as if you installed the filter on each machine.  

It's also nice that your whole network is protected.  So if your kid or the friend comes over with a laptop or wifi enabled phone it's covered.

There is also Net Responsibility.  This does run on each machine.  It logs all websites and sends a txt email to whoever you are accountable to.  

In my case, my wife and I are accountable to each other, it will also be nice as my boys get older to have something in place.

---

### Post by mastablasta on 2010-08-10
Never had any parental controls when i was young. Either on TV, computer or the net.
 
i turned out OK i guess...

---

### Post by bodhi.zazen on 2010-08-10
> **mastablasta said:**
> Never had any parental controls when i was young. Either on TV, computer or the net.
 
i turned out OK i guess...

Parents are people and there is a lot of variability in their behaviors and parenting styles and skill.

Because of this it is difficult to release something such as dansguardian and keep everyone happy, some will complain it is too restrictive, others that it is not restrictive enough.

Although you did not have parental (internet) controls, I am sure your parents had rules and limits.

As you turned out "OK" , be sure to appreciate your parents.

---

