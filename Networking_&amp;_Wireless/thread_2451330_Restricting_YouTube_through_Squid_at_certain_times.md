---
title: "Restricting YouTube through Squid at certain times and selective transparent proxy"
date: 2020-10-02
forum: Networking &amp; Wireless
---

### Post by wowiesy2 on 2020-10-02
At this time of Online Schooling due to community restrictions, I have setup ubuntu to work as router / dhcp thru dnsmasq at home. 

There has been numerous times that my son can't keep away from YouTube during class so I had to setup Squid to prevent that. 

 I have set up basic authentication to work with Squid as well, and manage to get it to work somehow.. 
```

[COLOR=#000000][FONT=Menlo]auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/passwd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth_param basic [COLOR=#CA3323]children[/COLOR] [COLOR=#CA3323]5[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth_param basic [COLOR=#CA3323]realm[/COLOR] Squid Basic Authentication[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#D17125]acl[/COLOR] auth_users [COLOR=#D17125]proxy_auth[/COLOR] REQUIRED[/FONT][/COLOR]


```

through this acl / http_access lines, I was able to directly prevent Squid from loading on the browser of the laptop: 


```

[COLOR=#000000][FONT=Menlo][COLOR=#D17125]acl[/COLOR] U1010_clients [COLOR=#D17125]src[/COLOR] [COLOR=#CA3323]192.168.254.0[/COLOR]/[COLOR=#CA3323]24 #lan ip addresses[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#D17125]acl[/COLOR] Test_Device [COLOR=#D17125]src[/COLOR] [COLOR=#CA3323]192.168.254.204[/COLOR]  [COLOR=#5620F4]#target device [/COLOR][/FONT][/COLOR]
[COLOR=#CA3323][FONT=Menlo][COLOR=#D17125]acl[/COLOR][COLOR=#000000] YouTube_Service [/COLOR][COLOR=#D17125]dstdomain[/COLOR][COLOR=#000000] .youtube.com .youtu.be .ytimg.com .googlevideo.com .i.google.com .ytimg.l.google.com .youtube.l.google.com[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#D17125]acl[/COLOR] school_hours [COLOR=#D17125]time[/COLOR] MTWHF [COLOR=#CA3323]07[/COLOR]:[COLOR=#CA3323]30[/COLOR]-[COLOR=#CA3323]12[/COLOR]:[COLOR=#CA3323]00[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
http_access deny Test_Device YouTube_Service
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo][COLOR=#5620F4]
[/COLOR][/FONT][/COLOR]but this means that, YouTube will be *forever* banned for that machine (at least while the Squid is running as proxy for that machine). 

But there are certain times when certain school materials will actually point to a YouTube link. So I thought that for those times, I figure my son just have to come over to me, my wife or our daughter to authenticate and my son can continue on only for that link (hopefully next time he tries to go YouTube on to watch his preferred videos, the authentication feature will kick in again and he can't get past that... have to have a way to do that right? 

the question then is:

How do I prohibit YouTube for a certain device, only during school hours without any proper authentication? 

further, 

My testing involved having to setup the Windows client to use my Squid proxy setup. but I'm pretty sure my son would be able to find a way to disable that eventually, so I'm thinking of setting Squid as a transparent proxy. 

But, is it possible to only do that for certain clients within the LAN? say only for the Windows client my son uses ? (and maybe an backup tablet..) 

this is supposed to be the line in my firewall script to setup the transparent proxy: 

```
#$IPT -t nat -A PREROUTING -s 192.168.254.0/24 -p tcp --dport 80 -j REDIRECT --to-port 3128  

```

instead of the whole LAN ip address pool, I can specifically use the client specific address here ya? Since I do have control on IP address assignment through mac address of the machines (via dnsmasq). 

Is it good practice to also have Port 443 go through Squid? (since YouTube also heavily uses that port) ? 

thanks for the feedback.

---

### Post by TheFu on 2020-10-02
I don't know how to do it on squid, but new pi-hole software since May has different groups possible by different client machines.  [https://docs.pi-hole.net/database/gravity/groups/](https://docs.pi-hole.net/database/gravity/groups/)

So, setup a pi-hole and point the squid server at it for DNS as the first test. That would block everyone the same way.  Then you can push the pi-hole as DNS to different client machines later.  May want to run 2 pi-hole systems on different machines.  I run them inside LXD containers.

Another option:
You might be able to just setup a trivial script to swap /etc/hosts files at specific times on the squid server.  hosts.yt ---> /etc/hosts that file would have all youtube.com domains (must be about 50) pointed to 127.0.0.1.  Then another would have the typical 10 line /etc/hosts file.  Using cron, just copy the normal or yt-blocking hosts files at specific times. The change should be immediate.

Sorry, but those are my best guesses.

---

### Post by wowiesy2 on 2020-10-03
i do have Pi also running on the same box (ubuntu / dnsmasq / squid / pi hole).. just to block ads...
will look into this..  

to restate my problem (stated like if-else):

```

if (is the target Winclient) and (during study hours) then

   if (is authenticated)  then

     allow YouTube

   else
 
     deny YouTube

   endif 
    

else

   allow YouTube

endif


```

---

### Post by SeijiSensei on 2020-10-03
HTTPS via Squid is much more difficult than proxying HTTP requests. Basically you have to create SSL certificates for the proxy server and the clients. Squid then sends the request to the remote HTTPS site and uses its certificates to authenticate the site. Then it forwards the content to the client machine using its own certificate which the client accepts.  [https://wiki.squid-cache.org/Features/SslPeekAndSplice](https://wiki.squid-cache.org/Features/SslPeekAndSplice)

You might consider just blocking the YouTube IPs on the router. Use cron jobs to activate these blocks at the beginning of the day and to remove them when done.

youtube-ui.l.google.com has address 64.233.185.91
youtube-ui.l.google.com has address 64.233.185.136
youtube-ui.l.google.com has address 64.233.185.190
youtube-ui.l.google.com has address 74.125.138.136
youtube-ui.l.google.com has address 108.177.122.91
youtube-ui.l.google.com has address 108.177.122.93
youtube-ui.l.google.com has address 108.177.122.190
youtube-ui.l.google.com has address 108.177.122.136
youtube-ui.l.google.com has address 172.217.215.91
youtube-ui.l.google.com has address 74.125.136.136
youtube-ui.l.google.com has address 74.125.136.91
youtube-ui.l.google.com has address 172.253.124.91
youtube-ui.l.google.com has address 64.233.176.91
youtube-ui.l.google.com has address 74.125.21.91
youtube-ui.l.google.com has address 64.233.177.136
youtube-ui.l.google.com has address 64.233.177.93

---

### Post by wowiesy2 on 2020-10-04
looks good.. will try it out..

---

