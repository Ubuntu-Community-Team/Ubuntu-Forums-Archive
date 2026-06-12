---
title: "Squid on Ubuntu - How to tell if caching is working?"
date: 2014-02-13
forum: Networking &amp; Wireless
---

### Post by josh36 on 2014-02-13
Running Squid3 on 12.04 in a test environment. Installing squid was easy enough but now I'm trying to see if caching is turned on and if so, it is working properly. 

I tried downloading webmin 1.670 but everytime I go into Squid Proxy Server-->Cache Manager stats I either get a bad header message or squid seems to be blocking even if I'm not routing traffic through it. 

What is the best way to tell if caching is working properly?

I'm a bit of a newb to Ubu so feel free to dumb things down for me.

---

### Post by Lars Noodén on 2014-02-13
Squid needs to be configured before the first usage.  That's not something webmin can do.  In general, it is faster, safer, more flexible to use the shell for server maintenance.  So I recommend pulling off the band-aid quickly rather than slowly and opening up the terminal.  Webmin is good for assistants once the head sysadmin has set everthing up, but its usefulness ends there.  Once you're running you should be able to go back to webmin.

Only a few things *need* to be set before use, though the other options are nearly endless.  Look in the manual page and the online documentation for squid for information about the directives **cache_dir**, **acl** and **http_access**  

```

# Uncomment and adjust the following to add a disk cache directory.
# cache_dir ufs /var/spool/squid3 100 16 256

```

The size is given in MB.  So the 100 in the default is 100MB.  Maybe that is too small.  

Then there is the question about who to allow access to.  There **acl** and **http_access** come into play.  Look through the acls to see what the pre-set options are.  Then set **http_access**

```

# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
...
# uncomment this line to allow access to the localnet as defined by the acl above it
#http_access allow localnet

```

Once it is configured, you need to create the cache.  That is done with the -z option.

```

sudo service squid3 stop
sudo squid3 -z
sudo service squid3 start

```

That's a lot but now it should just run on its own and maybe it is time for webmin.

But you can always watch the access logs real time with [tail](http://manpages.ubuntu.com/manpages/saucy/en/man1/tail.1.html).

```

tail -f /var/log/squid3/access.log

```

---

