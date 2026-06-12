---
title: "Ubuntu 10.10 System wide proxy - Automatic configuration URL"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by abhishek.b.naik on 2011-04-07
Hi All,

I have installed Ubuntu 10.10

I have set the proxy URL in "Automatic Proxy Configuration"  via "System -> Preferences -> Network proxy" and then selected "Apply System-Wide"

I tried accessing firefox via that and the proxy configuration effect has not taken place. I restarted the system and tried but the same.

Is there any way in which we can set an automatic proxy URL for system wide proxies. Pretty basic stuff but cant find it. :( :confused:

Regards,
Abhi

---

### Post by spikoley on 2011-04-08
Did you set Firefox to use the proxy?

1.  Edit
2.  Preferences
3.  Advanced
4.  Network tab
5.  Click Settings next to Connections

Make sure the proxy settings are set up there.

What happens when you do a traceroute or ping by IP and name?

---

### Post by abhishek.b.naik on 2011-04-08
Hi Spikoley,

Thanks for the reply.

I have set that and it works but I am speaking specifically about Synaptic package manager.

I want to apply a system wide proxy so that all apps use the same URL for connection to net. Is there any way i can configure that.

Regards,
Abhi

---

### Post by xuzan on 2013-01-02
Hello, Spikoley and Abhishek,

I have encountered the same problem.   

Setting the "Proxy Automatic Configuration URL ===>  http://proxy1.hella.com:8080/proxy.pac" in the Firefox browser, it works well.   I can surf the internet after input my user name and password.  

I also set the same URL in the System setting ---> Network ---> Network Proxy, and apply system wide.  

But it failed to work when I try to do 'apt-get update', the Synaptic Package Manager neither works.   as well as the 'Ubuntu Software Center'. 

Could you show me how to fix this problem?

Because my Ubuntu server lives in the intranet LAN of my company,  I can access the internet only through proxy,  what's worse, I can not get the IP address of proxy server. 
This Ubuntu server is very important for my department, without it, we cannot carry out the development collaboration task.  We are very anxious for the failure of accessing internet for apt-get software update and installation.

Please help me!
Many thanks!

Looking forward to your reply urgently....

From Shanghai, China.

---

### Post by oldgraf on 2013-01-02
/etc/environment ... http_proxy="http://webproxy:3128/" ftp_proxy="ftp://webproxy:3128/" https_proxy="https://webproxy:3128/" no_proxy="office-mirror"  try something like that

---

### Post by oldos2er on 2013-01-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

