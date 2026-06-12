---
title: "Configuring Squid as an SSL proxy?"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by RockStrongo on 2008-09-10
Hi everyone!  I don't post here very often, but this site has been a great resource for me over the years for configuring my home server.  My apologies if this is not the correct section for this topic.. It seemed to be the best fit.

I have and old dell desktop that I run as a LAMP server and it has been great for the past two years or so.   I currently tunnel my http traffic via ssh/putty and use foxy proxy to switch between my home proxy and local work proxy depending upon where I am going.  This works fine, but I also wanted to configure squid to act as a proxy as well so I can let a friend use the proxy during daytime hours without having to open an SSH session back to my server.  It seems to work fine, but it is currently not encrypted.. so any traffic over straight http is still caught in our company websense filter since I believe it is catching the meta data tags and flagging it.  SSL traffic seems to work fine, as I am guessing it can't due to being encrypted.

In short - I want to be able to configure Squid so my proxy connection is encrypted.  Is this possible?  Reading the documentation, it seems to me that the SSL flags available is only for SSL acceleration, etc.. and not for setting up Squid as and SSL proxy.   Is that possible with Squid?

Thanks!
Rock

---

### Post by amgat on 2008-09-16
I am wondering about the same exact thing. I have successfully installed squid3 and it's working very well. But I am not able to start SSL sessions. Do I need to compile from source? ( i installed squid3 the apt-get way ).

---

