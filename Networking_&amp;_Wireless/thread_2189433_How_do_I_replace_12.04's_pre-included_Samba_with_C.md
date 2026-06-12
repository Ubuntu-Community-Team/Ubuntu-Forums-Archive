---
title: "How do I replace 12.04's pre-included Samba with Centrify-Integrated samba?"
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by saxplayer1216 on 2013-11-22
I'm working toward making an Ubuntu 12.04 image that's as 1d10t proof as Window's (Windows' ?) "Browse to server. Double-click printer. Installed." and "Browse to network share. Use files" I have successfully set up [Centrify express]("http://www.centrify.com/express/free-active-directory-tools-for-linux-mac.asp") to allow for network logins, and that's working successfully, but I'm struggling with how to replace the pre-included Samba that comes with Ubuntu 12.04 with Centrify-integrated Samba. ([here]("http://www.centrify.com/resources/samba.asp?c=53&f=1") and [here]("http://www.centrify.com/downloads/public/centrify_wp008_samba.pdf")). Also, I'm thinking to write scripts to set up printers and shortcuts to network shares. The important parts are that they must connect to the printers via a windows ad-integrated print server so that we can track print jobs and it must be 1d10t proof. Has anyone done this or have any advice?

---

### Post by unixisfun on 2013-11-23
Hi

On "[COLOR=#000000]how to replace the pre-included Samba that comes with Ubuntu 12.04 with Centrify-integrated Samba", h[/COLOR]ave you looked at page 11-13 of this guide [http://www.centrify.com/downloads/products/documentation/suite2013/centrify-samba-guide.pdf](http://www.centrify.com/downloads/products/documentation/suite2013/centrify-samba-guide.pdf) where there are some recommendations.

Feel free to post this question in Centrify Express forum too
[http://community.centrify.com/t5/Centrify-enabled-Samba/bd-p/b_products_samba](http://community.centrify.com/t5/Centrify-enabled-Samba/bd-p/b_products_samba)

Sincerely
IdentitySolver

---

