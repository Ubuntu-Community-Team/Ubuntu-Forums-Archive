---
title: "Custom Distro for Iran Proxies"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by jdb1981 on 2009-06-16
Disclaimer: This question involves an ongoing political situation, but I don't intend for it to start a political discussion. This is a purely technical question. If you don't agree with the politics of what I'm asking to do, please move on, you're entitled to your opinion, and I hope you'd give me the same courtesy.


I'm interested in creating a custom Ubuntu/Xubuntu distro that would include very little in the way of features; the only thing it would really be any good for is creating Proxies using Squid to assist bloggers in Iran in connecting to the internet around government IP restrictions.

The goal would be to create a live CD that a non-technical person could simply place into a computer with an internet connection, and it would produce a few lines of feedback including the Proxy IP address and some instructions on how (and how not) to distribute it. No graphical interface, no filesystems mounted (except the CD, obviously) really nothing but the bare minimum needed to get a proxy up and running, and give the user some limited (like, 2-3 paragraphs at most) instructions about what to do next.

The world is changing fast, and the last few political uprisings have been coordinated largely on the backs of social networking sites like Twitter and Facebook. I imagine that the future holds more of the same. In times of heavy-handed government control of Internet access, people trying to get the truth out, in words and photos, should be afforded every possible opportunity to do so. I'd like to establish this as a tool that could be deployed in time of need to those who need it.

For more info, I'm going to quote this post from the blogger that inspired this idea; I'm quoting it uncut because his original post is all over Twitter and the servers are getting hammered, so a link might not load correctly, but it's at: [http://blog.austinheap.com/2009/06/15/how-to-setup-a-proxy-for-iran-citizens/](http://blog.austinheap.com/2009/06/15/how-to-setup-a-proxy-for-iran-citizens/)

> If you&#8217;re using CentOS/Redhat, it&#8217;s pretty straight forward to setup a proxy and help give access to those in Iran who are being censored.

Login as root and run the following

yum install squid

nano -w /etc/squid/squid.conf

Inside the code editor search (Control-W) for the line &#8220;http_access deny all&#8221; and change it to &#8220;http_access allow all&#8221;. This will make your proxy open and accessible to the world. If you would like to limit your proxy to Iranian IP blocks, you want to change &#8220;http_access deny all&#8221; to read &#8220;http_access allow TRUSTED&#8221; add a line (BEFORE the http_access line to setup an access control list [ACL]). This ACL line that defines TRUSTED should read:

acl TRUSTED src 62.60.128.0/17 62.193.0.0/19 62.220.96.0/19 77.36.128.0/17 77.77.64.0/18 77.104.64.0/18 77.237.64.0/19 77.237.160.0/19 77.245.224.0/20 78.38.0.0/15 78.109.192.0/20 78.110.112.0/20 78.111.0.0/20 78.154.32.0/19 78.157.32.0/19 78.158.160.0/19 79.127.0.0/17 79.132.192.0/19 79.170.144.0/21 79.175.128.0/18 80.66.176.0/20 80.69.240.0/20 80.71.112.0/20 80.75.0.0/20 80.191.0.0/16 80.242.0.0/20 80.253.128.0/20 80.253.144.0/20 81.12.0.0/17 81.28.32.0/20 81.28.48.0/20 81.31.160.0/20 81.31.176.0/20 81.90.144.0/20 81.91.128.0/20 81.91.144.0/20 82.99.192.0/18 82.115.0.0/19 83.147.192.0/18 84.47.192.0/18 84.241.0.0/18 85.9.64.0/18 85.15.0.0/18 85.133.128.0/17 85.185.0.0/16 85.198.0.0/18 86.109.32.0/19 87.107.0.0/16 87.247.160.0/19 87.248.128.0/19 89.144.128.0/18 89.165.0.0/17 89.221.80.0/20 89.235.64.0/18 91.98.0.0/15 91.184.64.0/19 91.186.192.0/19 91.206.122.0/23 91.208.165.0/24 91.209.242.0/24 91.212.16.0/24 91.212.19.0/24 91.212.252.0/24 92.42.48.0/21 92.50.0.0/18 92.61.176.0/20 92.62.176.0/20 92.242.192.0/19 93.110.0.0/16 93.190.24.0/21 94.74.128.0/18 94.101.128.0/20 94.101.176.0/20 94.101.240.0/20 94.139.160.0/19 94.182.0.0/15 94.184.0.0/17 94.232.168.0/21 94.241.128.0/18 95.38.0.0/16 95.80.128.0/18 95.81.64.0/18 95.82.0.0/18 95.82.64.0/18 95.130.56.0/21 95.130.240.0/21 188.34.0.0/16 188.93.64.0/21 188.121.96.0/19 188.121.128.0/19 188.136.128.0/17 188.158.0.0/15 193.189.122.0/23 194.225.0.0/16 195.146.32.0/19 212.16.64.0/19 212.33.192.0/19 212.50.224.0/19 212.80.0.0/19 212.95.128.0/19 212.120.192.0/19 213.176.0.0/19 213.176.32.0/19 213.176.64.0/18 213.195.0.0/18 213.207.192.0/18 213.217.32.0/19 213.233.160.0/19 217.11.16.0/20 217.24.144.0/20 217.25.48.0/20 217.64.144.0/20 217.66.192.0/20 217.66.208.0/20 217.146.208.0/20 217.172.96.0/19 217.174.16.0/20 217.218.0.0/15

Turn off logging by adding these two lines:

access_log none

cache_store_log none

Save the config file and as root issue the following command to start the Squid proxy server:

service squid start

Please don&#8217;t run this on a machine that you&#8217;re worried about or is used for production sites; and take basic security precautions, ie: moving SSH off the default port, using iptables, etc.

Obviously, the commands would be different, but I don't even know where to start in terms of stripping stuff out of an Ubuntu distro, adding Squid, anything. 

I'm appealing to this community, so if this sounds like a worthy project, I'd love it if someone could help me out. 

Can anyone tell me how to begin?

---

### Post by meldroc on 2009-06-16
I'm looking for info on setting up one of my boxes as an Iran free-speech proxy.  Granted, I'm in the U.S., and for all I know, all of the US may be blocked, but it's certainly worth a try.

---

### Post by sdennie on 2009-06-16
I think you are looking for remastersys.  It allows you to create a custom live CD and should be capable of doing exactly what you are asking for.

---

### Post by jdb1981 on 2009-06-16
@ meldroc: Well, that's what I'm trying to accomplish. The above quoted instructions, slightly modified, should work on Ubuntu, but I'm looking for a solution that would be secure (in terms of not even possibly accessing the HD if someone chose to exploit it instead of use it properly,) and offer a turnkey solution to the non-technically minded who want to help.

This is a link to the original source (which I meant to add to my post) and includes an email address at which the author is collecting proxy IPs for use in Iran:

[http://blog.austinheap.com/2009/06/15/how-to-setup-a-proxy-for-iran-citizens/](http://blog.austinheap.com/2009/06/15/how-to-setup-a-proxy-for-iran-citizens/)

I can't make any claim to the method or safety of his/her procedure, nor can I say your proxy IP will end up in the right place if you set it up and email it... I'd do a Twitter search for "proxies, #iranelection" and that should, with a little digging, get you to someone who could make use of your Proxy. I'd give you more specific info, but Bloggers in Iran are asking for US and other foreign folks to refrain from using any identifying information in public forums.


@sdennie: Thanks, I'll check it out. 


Speed is of the essence, so if anyone else is interested in helping, please let me know. It'll take me a while to cram all the info about how to make this work into my old brain, so feel free to share if you have tips!

---

### Post by eyal_allweil on 2009-06-17
I'll add a direct link to what seems to be ubuntu instructions for this:

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by vincentsrose on 2009-06-18
can someone help me configure my squid server. i installed it but every time i try to configure nothing happens i think i am missing a step. This is to help the people the in iran. When i run the command sudo vi /etc/squid/squid.conf in terminal i get a  lot of text but can't seem to edit it.

---

### Post by Vendaval on 2009-06-18
vincentsrose- Try the command sudo **gedit** /etc/squid/squid.conf

jdb1981, this looks like what you're trying to make- [http://hackerswithoutborders.net/index.php/HWB_LiveCD](http://hackerswithoutborders.net/index.php/HWB_LiveCD)

---

### Post by jimmy the saint on 2009-06-18
Also, the best way to keep the resident HD from being accessed if the machine is (remotely) hacked by nefarious anti-speech agencies would be to simply unplug the HD.  If it is a tower, this can be done by simply unplugging it, in a lappy removing a screw is usually all that is needed to slip it out.  I am not saying this is neccessarily a HUGE risk, but anti-speech agencies typically have a large ammount of resources, so it is a reasonable precaution, especially if the machine is going to be booted from the live CD and ran that way for a time.

---

