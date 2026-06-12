---
title: "proxy help: gaim and https"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by exar on 2007-02-06
First I'd like to say this is my very first post.  I've been very impressed with Ubuntu and have even gotten several non-technical friends to try it.  They all love the community support here.  Thanks to all of you here.

On to the problem:

My girlfriend is studying abroad in Germany right now and called me asking what the funny noises coming from her computer were.  Long story short her hard drive died, and Dell won't replace it untill she comes home.  So in the mean time I talked her through setting up a bootable 1gb flash drive with ubuntu on it ([http://pendrivelinux.com/)](http://pendrivelinux.com/)).

Problem is, she connects through a proxy to the internet.  She has an http, https, and a socks proxy address, no username or password.  She can access some webpages in firefox by setting the http proxy within firefox, but cannot log into her email or any other secure page.  She has also not been able to connect to aim through gaim even while trying to set different proxy settings within gaim.

I don't have alot of experience with proxies and the pendrive linux is running xfce which doesn't have a global proxy setting that I have been able to find.

Any tips or suggestions?  She'd like to be able to work on her papers and email them to be able to print them as well as be able to communicate with people at home. (She loves Abiword now).

Thank you in advance,
James

---

### Post by chggr on 2007-02-18
Hi there!

I don't like to leave questions unanswered, so I will post an answer even if it's late...

I am also using a computer behind a squid proxy on port 8080 and I had the same problem.

When I opened GAIM for the first time, a strange message appeared saying more or less that the proxy server is not configured to accept connections to some specific port. The problem was that I did not have physical access to that server, so I couldn't change the squid configuration file in order to accept these connections. (But even if I had, I probably wouldn't for security reasons! :) ) So what I did was modify the preferences of GAIM and configure it so that it would use the http proxy.

Follow this procedure:
Click on "Accounts" -> (Your account's name) -> "Edit Account"
Then go to "Advanced" tab and where it says "Proxy", select "HTTP".
Fill in the information (Host, Port, username, password) and press "Save".
That's it. You should be up and running. If not, try to restart GAIM so that the new configuration takes full effect.

If the above instructions don't work, try to use another Proxy Server Type. If it still doesn't work, then it's probably certain that the Proxy Server Administrator has deliberately forbidden chat programs, so you can do absolutely nothing about it (except try to persuade him to do so :D)

---

### Post by exar on 2007-02-19
Thanks alot for the reply, she actually did get it working a couple of days ago by doing just as you said.  She went through her list of proxy types provided and one of them worked (don't remember which it was now).  Thanks alot for the help!

---

