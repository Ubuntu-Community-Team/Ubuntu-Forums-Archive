---
title: "Ubuntu as Second DNS server?"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by toolzen on 2008-05-10
Here is what I am trying to do. Our current DNS server is a win2k3 server edition machine. All of our windows servers are maintained by a third party that provides network administration. All clients use this DNS server for all the normal DNS server functions.

I am the "I.T. guy" for the company I work for, and one of my responsiblities is maintaining a linux web-server we use for our company intranet (the third-party Net admin doesn't want to have anything to do with linux). What I would like to do, is rather than a user typing in "http://192.168.x.x" to get to our intranet, is to just have them typ in "www.somecoolname.com." Since this is only an internal site, there should be a way to set up a second dns server on the linux box that would a): forward [www.somecoolname.com](www.somecoolname.com) to [http://192.168.x.x](http://192.168.x.x) when typed in on the internal network and b): forward users to our existing DNS for all other DNS functions.

Any thoughts?

---

### Post by toolzen on 2008-06-12
Ok, so it took me all of 30 minutes to figure out how to do this with bind9, and I had a server set up (though a very slooooow server with a 300 Mhz processor)that I pointed my Win XP machine to as the primary DNS, had web-content filtering ~without~ having to change proxy settings on client machine (using dansguardian/tinyproxy), and then the client was forwarded on to our "real" DNS server for all other dns services. This old slow server will hopefully be enough to show the head honchos how it works, so they'll let me use a better machine.

---

