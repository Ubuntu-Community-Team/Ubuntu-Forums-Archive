---
title: "to DNS or not to DNS"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by 007casper on 2009-07-03
I have set of static IPs for my sites. I am curious to know the pros and cons of having DNS servers/providers.  

There are several companies with different features such as dyndns, ultradns, zoneedit, opendns etc... then there is gbindadmin from synaptic.

I was thinking of using gbindadmin.

Are there any disadvantages/benefits of having your own dns set up on your server vs. having a service provider like dyndns.

Thank you.

---

### Post by 007casper on 2009-07-03
I really would like to find out the pros/cons.

Please, advise.

---

### Post by XCan on 2009-07-03
Easy to remember address? That's probably the most significant advantage.

---

### Post by decoherence on 2009-07-03
I used to do hosting + authoritative DNS for my domain. It was extremely handy to not have to go through a registrar to make changes -- I could quickly set up prototyping/testing servers and make the host names available to the world (after some delay.)

The main con is that it'll be a target.

I would suggest that, if you're going to be making a lot of changes, bringing new hostnames online temporarily or registering new domains, it might be useful to have your own DNS.

Otherwise, I'd say spare yourself the headache and potential security risk and use a service.

---

### Post by 007casper on 2009-07-03
thanks everyone.  Is there a difference between DNS service providers?  I was checking their peering.  And some of them peered with lots connections, and some just have a single connection to cogent.

Does anyone know a good dns provider? I hear opendns shows ads.

---

