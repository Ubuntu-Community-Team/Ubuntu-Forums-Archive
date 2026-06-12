---
title: "Extra server IPs don't resolve."
date: 2009-05-04
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-05-04
I have several dedicated IP Addresses on for my server. Like:
a.a.a.1
a.a.a.2
b.b.b.1
b.b.b.2

The first one a.a.a.1 resolves to my server, showing my index page for /var/www/

How do I get apache to listen to the other three IPs so they resolve as well?

---

### Post by decoherence on 2009-05-04
are all these ip addresses seriously on different class A subnets?

just makin sure...

---

### Post by ubuntuforums on 2009-05-04
I bought a vps which provided me with 4 dedicated IP addresses.

As for your question no, the first two are on the same, and the second two are on the same. Like:
a.a.a.1
a.a.a.2
b.b.b.1
b.b.b.2

I should have written it like this originally, so a.a.a.1 resolves but the other three do not.

---

### Post by decoherence on 2009-05-04
When you say 'resolve' do you mean you have a name (say, [www.thing.com](www.thing.com)) that resolves in to a.a.a.1 and you want it to resolve in to a.a.a.2, b.b.b.1 and b.b.b.2? So, for example, [www.thing.com](www.thing.com) would resolve in to all of the above? A curious setup...

Or do you mean you want to go to IP address b.b.b.2 and get the same site as you would if you went to a.a.a.1? I'm going to assume you mean the second since the first doesn't make much sense to me.

I've only ever done this with Apache 1.3, but I think if you look in the folder /etc/apache2/sites-enabled you'll find the file you need to edit. If I were to guess, I'd say make copies of the file and change the "<VirtualHost *:80>" in each copy to

<VirtualHost a.a.a.1:80>

replacing the a.a.a.1 with whichever IP address you're setting up. Then restart Apache and see if she goes.

Warning -- this is a TOTAL guess. Like I said, I haven't tried to do this since Apache 1.3. It does make a certain degree of sense to me, though. Let us know!

---

