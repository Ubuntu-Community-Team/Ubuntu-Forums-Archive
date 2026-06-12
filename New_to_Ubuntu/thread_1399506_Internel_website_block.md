---
title: "Internel website block"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by fendy87 on 2010-02-05
hai..i got problem to access internet..my internet always block some website..like 'www.onemanga'..anyone can help me,so i can read naruto manga..huhu..:(

---

### Post by thulefoth on 2010-02-05
Right at the top of the OneManga home-page is this:

> (note: users in NZ seem to be having problems loading the site and images.. we are looking into this.) 

(note2: some users report getting redirected to a fake antivirus scanning page. we are looking into this. in the meantime, if you get any strange popups or redirects, please let us know. Also, avoid clicking on anything on these fake/misleading ads. we definitely do not approve of them! thanks for the help and sorry for the trouble.) Looks like bad news for Manga fans!  :???:

I hope you can find a way ... what country are you in?

---

### Post by sandyd on 2010-02-05
> **thulefoth said:**
> Right at the top of the OneManga home-page is this:

Looks like bad news for Manga fans!  :???:

I hope you can find a way ... what country are you in?
looks like someone hacked the DNS server for whatever country the OP is in.... (the ISP's DNS I mean....)

Try this.
[https://store.opendns.com/get/basic](https://store.opendns.com/get/basic)

Its free and its very very very fast.

p.s. if your to lazy to sign up and set up opendns, just browse to 
[http://174.142.79.41](http://174.142.79.41)
and you will see your manga ;)

p.p.s if you type in the terminal
```

ping onemanga.com
```what IP do you get?

If you get a different IP address than the one above, it means the DNS has been hacked. just use the ip address link I gave (or opendns) to access the site. 
And you might wanna send them an email to tell them whats wrong too ;)

p.p.p.s One thing I admire about this site. It does not use direct (solid) addresses in its links, but instead uses relative links.

---

### Post by thulefoth on 2010-02-06
I had seen mention of OpenDNS, but assumed (yeah, hazardous word!) it was for like ISPs etc.  We set it up local, eh?  I will make a detour and go there after work tomorrow.  

I wanted to be able to do CMS local, so I used Synaptic to put PHP & MySQL & Apache on my new 9.10, over the weekend.  My first Linux. I kinda crept up on the LAMP package little by bit, or so I thought ... pulling on a string that proved endless.  

When I got done I did some server-reading, and issued a sudo for 'server-install' ... and it found 4 items I needed, and said 'there ya go'. Does it sound like I have proper base?  

I'd like to get into this area, to the extent it's practical for a 'basic' person. 

Thanks! 

Ted

---

### Post by mushwars on 2010-02-06
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/) <-- take a look at that, that is what I use ( my isp sucks too )

8.8.8.8
8.8.4.4

put it in your router by going to 192.168.x.1 and then change your dns server.

---

