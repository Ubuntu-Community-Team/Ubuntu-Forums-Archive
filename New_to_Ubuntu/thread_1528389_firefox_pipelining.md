---
title: "firefox pipelining"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by 13k on 2010-07-10
uhh... i'm not sure if i should be writing this here so... yeah...  fasterfox lite add on, pipelining the browser or something(not sure about anything  computers)  i read in wikipedia it increases latency... goes on and on, then my a.d.d. kicked in....  The point is... does pipelining/fasterfox lite in general, increase bandwidth

---

### Post by Bachstelze on 2010-07-10
> **13k said:**
> uhh... i'm not sure if i should be writing this here so... yeah...  fasterfox lite add on, pipelining the browser or something(not sure about anything  computers)  i read in wikipedia it increases latency... goes on and on, then my a.d.d. kicked in....  The point is... does pipelining/fasterfox lite in general, increase bandwidth

No. Increasong bandwidth requires either a modification of your physical line, or a configuration change in the router you're connected to at your ISP's.

---

### Post by 13k on 2010-07-10
> **Bachstelze said:**
> No. Increasong bandwidth requires either a modification of your physical line, or a configuration change in the router you're connected to at your ISP's.

 physical line of my router?

---

### Post by lovinglinux on 2010-07-11
The only thing pipelining does is to send multiple requests to a web site without waiting for a response. For example instead of requesting the image of the pager banner, wait for the response then requesting the image of the first article of the page, it sends all requests simultaneously. So it won't increase your bandwidth usage.

There is a good article [here](http://devcentral.f5.com/weblogs/macvittie/archive/2009/04/02/http-pipelining-a-security-risk-without-real-performance-benefits.aspx) that debates the effectiveness of pipelining and explains it well.

Keep in mind none of the Fasterfox extensions are approved by Mozilla, which means they don't review the code. That being said, I use Fasterfox Extreme and it works well for me.

---

### Post by QLee on 2010-07-11
> **13k said:**
> uhh... i'm not sure if i should be writing this here so... yeah...  fasterfox lite add on, pipelining the browser or something(not sure about anything  computers)  i read in wikipedia it increases latency... goes on and on, then my a.d.d. kicked in....  The point is... does pipelining/fasterfox lite in general, increase bandwidth

No, as Bachstelze told you in answer to your previous question, the things you download (file sizes) are what determines the bandwidth you are using (and that's why you are running into the bandwidth cap). 

Bandwidth is a characteristic of the "line" you make the connection on and if you want more bandwidth it usually means paying more for it. Think of the line as a pipe and only so much water can come down the pipe at one time, if you want more water you need a bigger pipe. If I remember correctly from your previous post, your parents have a cap on the bandwidth available to you, there is probably some reason for that, could you discuss your needs with them and ask for more bandwidth? What might be happening is that the account has a set maximum amount of Gigabytes per month and, usually, if one goes over the extra is charged at a higher rate. Whatever you are doing may be triggering extra charges.

---

### Post by 13k on 2010-07-11
> **lovinglinux said:**
> The only thing pipelining does is to send multiple requests to a web site without waiting for a response. For example instead of requesting the image of the pager banner, wait for the response then requesting the image of the first article of the page, it sends all requests simultaneously. So it won't increase your bandwidth usage.

There is a good article [here]("http://devcentral.f5.com/weblogs/macvittie/archive/2009/04/02/http-pipelining-a-security-risk-without-real-performance-benefits.aspx") that debates the effectiveness of pipelining and explains it well.

Keep in mind none of the Fasterfox extensions are approved by Mozilla, which means they don't review the code. That being said, I use Fasterfox Extreme and it works well for me.

 thanks, and i don't see fasterfox extreme in mozilla add on page. ?? and interesting article  > **QLee said:**
> No, as Bachstelze told you in answer to your previous question, the things you download (file sizes) are what determines the bandwidth you are using (and that's why you are running into the bandwidth cap). 

Bandwidth is a characteristic of the &quot;line&quot; you make the connection on and if you want more bandwidth it usually means paying more for it. Think of the line as a pipe and only so much water can come down the pipe at one time, if you want more water you need a bigger pipe. If I remember correctly from your previous post, your parents have a cap on the bandwidth available to you, there is probably some reason for that, could you discuss your needs with them and ask for more bandwidth? What might be happening is that the account has a set maximum amount of Gigabytes per month and, usually, if one goes over the extra is charged at a higher rate. Whatever you are doing may be triggering extra charges.

 I already get the whole idea of a 'bigger pipe' and the water thing, just asking if pipelining makes it more expensive to use the internet.

---

### Post by lovinglinux on 2010-07-11
> **13k said:**
> thanks, and i don't see fasterfox extreme in mozilla add on page. ?? and interesting article


My bad. It is [Extra Fasterfoxx](https://addons.mozilla.org/en-US/firefox/addon/59745/). :)

---

### Post by stmiller on 2010-07-11
This is looked down upon by web admins everywhere. pipelining basically makes repeated simultaneous request to the web server causing huge excess loads. Bah!

[http://skattertech.com/2006/02/how-to-block-fasterfox-requests/](http://skattertech.com/2006/02/how-to-block-fasterfox-requests/)

:)

---

### Post by 13k on 2010-07-11
> **lovinglinux said:**
> My bad. It is [Extra Fasterfoxx]("https://addons.mozilla.org/en-US/firefox/addon/59745/"). :)

 i see, nice then lol, whats the difference between fasterfox lite and all the others like extra fasterfoxx?> **stmiller said:**
> This is looked down upon by web admins everywhere. pipelining basically makes repeated simultaneous request to the web server causing huge excess loads. Bah!

[http://skattertech.com/2006/02/how-to-block-fasterfox-requests/](http://skattertech.com/2006/02/how-to-block-fasterfox-requests/)

:)

 so these simultaneous requests, is bad for my internet bill/bandwidth?

---

### Post by lovinglinux on 2010-07-11
> **13k said:**
>  so these simultaneous requests, is bad for my internet bill/bandwidth?

Is not the pipelining that increases bandwidth usage, but the Enhanced Prefetching feature, which is disabled in Fasterfox Lite. 

The Prefetching feature downloads content from web links in advance, presuming you are going to open them. I don't know if that "Enhanced Prefetching" feature even works, because Firefox does prefetching by default and not all sites support it. As far as I know, is a feature created by Google, to speed up page load of their search results.

> **13k said:**
> i see, nice then lol, whats the difference between fasterfox lite and all the others like extra fasterfoxx?

Fasterfox Lite doesn't have advanced link pre-fetching. The funny thing is that it has more options than Extra Fasterfoxx :)

The extra options are mostly checkboxes that allow to disable some things, but it also has additional rendering options.

Extra Fasterfoxx is faster in my opinion.

---

### Post by 13k on 2010-07-11
> **lovinglinux said:**
> Is not the pipelining that increases bandwidth usage, but the Enhanced Prefetching feature, which is disabled in Fasterfox Lite. 

The Prefetching feature downloads content from web links in advance, presuming you are going to open them. I don't know if that &quot;Enhanced Prefetching&quot; feature even works, because Firefox does prefetching by default and not all sites support it. As far as I know, is a feature created by Google, to speed up page load of their search results.



Fasterfox Lite doesn't have advanced link pre-fetching. The funny thing is that it has more options than Extra Fasterfoxx :)

The extra options are mostly checkboxes that allow to disable some things, but it also has additional rendering options.

Extra Fasterfoxx is faster in my opinion.

 thank you very much

---

