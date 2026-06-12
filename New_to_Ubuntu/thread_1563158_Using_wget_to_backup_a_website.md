---
title: "Using wget to backup a website"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by SlimBiggins on 2010-08-28
I am trying to backup my sisters myspace website, mainly to save all of the pictures that were uploaded. She somehow lost the orignals.

I read up on using wget and gave it a try, but no success. I used the recursive and page-requisites (-rp) options thinking that would download her user page, but it only downloaded the .html files and even downloaded some .html files from google.com and faq.myspace.com. I ended up killing the process because it seemed to be neverending like it was trying to download the entire myspace.com website.

Evidently I am misunderstanding the use of these options. My question is: what are the correct wget options to download just her user page. Also, do I need to put the u/n and p/w in the syntax?

Example: wget <OPTIONS> [http://www.myspace.com/username/](http://www.myspace.com/username/)

Any help is always greatly appreciated.
- Slim Biggins

---

### Post by stmiller on 2010-08-28
Most (many?) web servers block wget and other site-suckers.

It could be myspace is blocking either repeated attempts, or blocking specific wget calls.

---

### Post by andrew.46 on 2010-08-31
Hi stmiller,

> **stmiller said:**
> Most (many?) web servers block wget and other site-suckers.

True, although I will have to say a quick look at a sample myspace page seemed to show wget working well enough. A cautious use of wget's *--user-agent* option will usually get over some over zealous blocking efforts by web hosts, as long as this does not violate the site's conditions of use...

Andrew

---

