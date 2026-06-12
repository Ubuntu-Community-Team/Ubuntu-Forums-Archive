---
title: "Problens logging into my router"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by uwe-bungto on 2015-11-01
I an trying to connect to my router and get the following warning from both foxfire and Vivaldi.

This started a few weeks ago. I have not logged into the router in about 6 months. It is not something requires a lot of attention. 


Secure Connection Failed

An error occurred during a connection to 192.168.0.1. SSL received a weak ephemeral Diffie-Hellman key in Server Key Exchange handshake message. (Error code: ssl_error_weak_server_ephemeral_dh_key)

    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
    Please contact the website owners to inform them of this problem.

---

### Post by DK1993 on 2015-11-02
May I ask what kind of router you are trying to connect to? Usually getting into a routers administration panel does not require using HTTPS or SSL. Are you using any browser extensions that force HTTPS connections?

---

### Post by uwe-bungto on 2015-11-02
> **DK1993 said:**
> May I ask what kind of router you are trying to connect to? Usually getting into a routers administration panel does not require using HTTPS or SSL. Are you using any browser extensions that force HTTPS connections?

I am using a D-Link DSR 250. I have disabled every browser extension and it still uses https. I have a much older version of fire fox on windows and it asks if I trust the connection so I can add an exception and log into the router.
I have tried this with a clean install of Chromium and Vivaldi they all default to https. Is there an app in Ubuntu 14.04 that causes the browsers to do this?

---

### Post by sandyd on 2015-11-02
Your router is vulnerable to the [logjam attack]("https://weakdh.org/").

[Mozillla has added protection for it in it's browser.]("https://bugzilla.mozilla.org/show_bug.cgi?id=1138554")
It can be disabled by going to about:config in Firefox (no http/https, just copy/paste), and disabling the following values.
security.ssl3.dhe_rsa_aes_128_sha
security.ssl3.dhe_rsa_aes_256_sha

Note that this will make your browser vulnerable to the attack.

---

### Post by rkstarr on 2015-11-03
I have a similar problem.  After recent update about two weeks ago I  could not get into the configuration utility for my TP-Link Archer D7  modem/router from Firefox.  I can get into it using Chromium and Opera  but not Firefox.  Is there a similar issue and/or fix? Using 14.04 LTS.

---

### Post by uwe-bungto on 2015-11-03
> **sandyd said:**
> Your router is vulnerable to the [logjam attack]("https://weakdh.org/").

[Mozillla has added protection for it in it's browser.]("https://bugzilla.mozilla.org/show_bug.cgi?id=1138554")
It can be disabled by going to about:config in Firefox (no http/https, just copy/paste), and disabling the following values.
security.ssl3.dhe_rsa_aes_128_sha
security.ssl3.dhe_rsa_aes_256_sha

Note that this will make your browser vulnerable to the attack.

Thanks.
I disabled the two and now have a warning
> This Connection is Untrusted

You have asked Firefox to connect securely to 192.168.0.1, but we can't confirm that your connection is secure.

Normally, when you try to connect securely, sites will present trusted identification to prove that you are going to the right place. However, this site's identity can't be verified.
What Should I Do?

If you usually connect to this site without problems, this error could mean that someone is trying to impersonate the site, and you shouldn't continue.



Which is not bad. confirming the exception gets me to the router.
Now that the exception is registered I reset the two and can log into the router.

Once again thanks
Paul

Update log into the router before resetting. Looks like this has to be done every time. Then how often does a router configuring?

---

