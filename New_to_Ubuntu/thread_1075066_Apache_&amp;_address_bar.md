---
title: "Apache &amp; address bar ?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by garyed on 2009-02-19
This is more of an Apache question but I haven't had much luck in the Networking forum so I figured I'll try this question here. 
I'm running Hardy with Apache2.  
I have a domain name & I pay for a shared web hosting service through 1and1.com where I already have a site put up. I also have some web pages that I am planning on running from my own Apache server too. I can just link to my server from my paid web host with no problem. I just don't want my ip address to appear in the Web Browser's address bar when someone gets redirected to my page. I assumed there is something I can do on my server config to make something other than my ip address appear in the Web Browser address bar.
Anyone know?

---

### Post by Triggerhapp on 2009-02-19
Wow its been a good few years since  I did this... You will want to no redirect to your IP, but make the nameserver of your host CNAME (i think?) to your IP...

One mo im going to go look this up again

On a futher note, if your machine and server are behind a router firewall, other people might not be able to connect until you set up the firewall port forward, and then after that your laptop wont be able to see the website when using the URL, but will be fine with the servers network IP ;)

---

### Post by Triggerhapp on 2009-02-19
Yeah my idiocy there, the DNS service i use labels it an "A type record" for the normal URL = this server

CNAME mean "URL = this URL"
and forwarding is what you're currently doing

---

### Post by garyed on 2009-02-19
I can access it fine from the web. Port forwarding works but I have to use port 8080 because Verizon blocks port 80. 
I just wish I could find a way to not show my ip address in the browsers address bar.

---

### Post by Triggerhapp on 2009-02-19
as i mentioned, you will want to get someone to host a name, and have it an A type, in the nameserver, this means you will come up as "http://your.url.here:8080/file"

if you want a nice simple and free server name, give afraid.org a spin. I use it myself.

---

### Post by garyed on 2009-02-19
> **Triggerhapp said:**
> as i mentioned, you will want to get someone to host a name, and have it an A type, in the nameserver, this means you will come up as "http://your.url.here:8080/file"

if you want a nice simple and free server name, give afraid.org a spin. I use it myself.

I'm not sure I understand. 
If I get a free server name will it show the new server name in the address bar or will it still show my ip address?

---

### Post by Triggerhapp on 2009-02-19
ubuntuforums runs on a machine and uses an IP, like your server, the difference is a Nameserver (.org nameserver) says that ubuntuforums.org = The specific IP for these forums.

afraid.org gives away subdomains something.somewhere.com, which you can link into your own IP address, so your server will be "http://whatevernameyouchoose.someone.org/" etc in the bar, instead of your IP.

---

### Post by garyed on 2009-02-19
Thanks for the clarification.
Now I see says the blind man!

---

### Post by Triggerhapp on 2009-02-19
no worries! give it a shot, if you have problems feel free to PM me.
I shall be heading to bed soon, so try other sources if you cant wait for me to wake up :p

---

