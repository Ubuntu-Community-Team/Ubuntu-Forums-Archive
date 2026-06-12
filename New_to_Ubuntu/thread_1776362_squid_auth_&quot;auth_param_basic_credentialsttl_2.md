---
title: "squid auth &quot;auth_param basic credentialsttl 2 hours&quot;"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by jijiisme on 2011-06-06
I want to known "auth_param basic credentialsttl 2 hours" what is this config line really mean?

I used auth in squid.
all are really work but to day i want a user to temporary disable, so i go to auth file and put "#" in front of the user name. but it can't work. so I delete the whole line. I can't work too. 

I watching the access.log whole time. so help me how to diable the user.

---

### Post by Lexus45 on 2011-06-06
> **jijiisme said:**
> I want to known "auth_param basic credentialsttl 2 hours" what is this config line really mean?

> 
    "credentialsttl" timetolive
    Specifies how long squid assumes an externally validated
    username:password pair is valid for - in other words how
    often the helper program is called for that user. Set this
    low to force revalidation with short lived passwords.  Note
    setting this high does not impact your susceptibility
    to replay attacks unless you are using an one-time password
    system (such as SecureID).  If you are using such a system,
    you will be vulnerable to replay attacks unless you also
    use the max_user_ip ACL in an http_access rule.

From [http://www.squid-cache.org/Doc/config/auth_param/](http://www.squid-cache.org/Doc/config/auth_param/)

By the way, have you restarted/reload SQUID after commenting the user out ?
Try this:
```
squid -k reconfigure
```

---

### Post by jijiisme on 2011-06-06
thank you for your answer. I already read form that site but I want to know more simplex.
and some aid for my problem

---

### Post by Lexus45 on 2011-06-06
> **jijiisme said:**
> thank you for your answer. I already read form that site but I want to know more simplex.
and some aid for my problem
You're welcome.

But what is unclear? 2 hours is the time, during which Squid doesn't re-ask the user for login and password since they were typed. I'm not a Squid-expert, so I'm not sure if the user's access will be denied even after reload of the config file. That's why I suppose that restarting Squid is the better way.

---

### Post by jijiisme on 2011-06-06
yes, you are right. the official site say like you. but I used the proxy now but the proxy never claim the username and pass after 2 hours. I login and used until i close the browser. ( I used firefox 4 and i am on xp sp2) and i don't want that happen.

my problem is I want to disable the user (he is downloading the file over 2H) so I want to shut him down now. I delete the his account and stop the squid and re start the squid, and watch the access log. he is not exit. I reboot the server. and check the log. he is online. so what can i do him? guide me. thank you.

---

### Post by Lexus45 on 2011-06-06
> **jijiisme said:**
> yes, you are right. the official site say like you. but I used the proxy now but the proxy never claim the username and pass after 2 hours. I login and used until i close the browser. ( I used firefox 4 and i am on xp sp2) and i don't want that happen.

my problem is I want to disable the user (he is downloading the file over 2H) so I want to shut him down now. I delete the his account and stop the squid and re start the squid, and watch the access log. he is not exit. I reboot the server. and check the log. he is online. so what can i do him? guide me. thank you.
Can it be that you have some little problems with the order of your ACLs in squid?
This is the first what came to my mind.

Sometimes these situation take place. The order of each line (each ACL) can be very important.

Give us please your config. The whole config file is too big, so it would be nice to see at least the part describing your ACLs, like allowed networks, users, etc, and the rules which allow/deny access to/from them.

---

### Post by jijiisme on 2011-06-06
> 
#auth_param digest nonce_max_duration 30 minutes
#auth_param digest nonce_max_count 50
auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/squid_users
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours
auth_param basic casesensitive off

#  TAG: authenticate_cache_garbage_interval
#    The time period between garbage collection across the username cache.
#    This is a tradeoff between memory u

and 

> 
#Examples:
#acl macaddress arp 09:00:2b:23:45:67
#acl myexample dst_as 1241
#acl password proxy_auth REQUIRED
#acl fileupload req_mime_type -i ^multipart/form-data$
#acl javascript rep_mime_type -i ^application/x-javascript$
#
#Recommended minimum configuration:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 172.16.0.0/12    # RFC1918 possible internal network
acl localnet src 192.168.0.0/16    # RFC1918 possible internal network
#
acl SSL_ports port 443        # https
acl SSL_ports port 563        # snews
acl SSL_ports port 873        # rsync
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl Safe_ports port 631        # cups
acl Safe_ports port 873        # rsync
acl Safe_ports port 901        # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
acl users proxy_auth REQUIRED

#  TAG: http_access
#    Allowing or Denying access based on defined access lists
#
#    Access to the HTTP port:
#    http_access allow|deny [!]aclname ...
#
#    NOTE on default values:
#
#    If there are no "access" lines present, the default is to deny
#    the request.
#
#    If none of the "access" lines cause a match, the default is the
#    opposite of the last line in the list.  If the last line was
#    deny, the default is allow.  Conversely, if the last line
#    is allow, the default will be deny.  For these reasons, it is a
#    good idea to have an "deny all" or "allow all" entry at the end
#    of your access lists to avoid potential confusion.
#
#Default:
# http_access deny all
#
#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow users
http_access allow manager localhost
http_access deny manager
# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
# Deny requests to unknown ports
http_access deny !Safe_ports
# Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports
#
# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

#  TAG: http_access2
#    Allowing or Denying access based on defined access lists
#


thank you for you interest

---

### Post by Lexus45 on 2011-06-06
Try to do what they recommend:
```

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

```and comment out
```

acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 172.16.0.0/12    # RFC1918 possible internal network
acl localnet src 192.168.0.0/16    # RFC1918 possible internal network

```though the 'http_access allow localnet' is already commented out.

And if I were you, I would place the '**http_access allow users**' somewhere nearer to the '**http_access deny all**' (but of course higher then this rule).
For debugging I'd also comment out ACLs and rules describing '**purge**', '**localhost**' and '**manager**'.

---

### Post by jijiisme on 2011-06-06
sorry i tried it now but it won't work.

---

### Post by jijiisme on 2011-06-06
sorry,  it work, it really working. i can shut him down now. sorry I think your way is not working, because of time. I stop and re start the service. every is under control. 

> thank you so much. Mr. lexus45
I am really nice to meet you. :D

---

