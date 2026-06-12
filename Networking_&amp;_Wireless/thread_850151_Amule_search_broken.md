---
title: "Amule search broken?"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by iamah on 2008-07-05
I'm trying to search in aMule for days, but it doesn't returns nothing.

Servers are seem ok, connect at once, no low id... but no search... :confused:

---

### Post by conphuzed on 2008-08-17
i also have this issue right now, it worked before, now it returns 0 search results for any query and does not appear to be scanning for files (i.e. the only thing that happens when u start a search is the search tab appears)

any ideas?

---

### Post by iamah on 2008-08-18
Sometimes i used to work using the Kad feature... but last time I tried I coudn't connect to Kad, can anyone make a quick howto on connecting Kad? It seems to require port information...

---

### Post by Levander on 2008-08-20
Bump this because I've been trying amule for the first time in a very long time.  A few of my searches are returning a few results, but much less than what I used to get.

---

### Post by oldHat on 2008-08-30
It seems to be working for me now, but slowly.

I was fighting with the same problem.  Tried absolutely everything I could think of.  Downloaded 2.2.2 from GetDeb, redid my router and firestarter rules.

The last three things I tried were to click somewhere to refresh my ED2K server list (a little blue arrow on the Networks/ED2K tab).  Then I refreshed my KAD server list the same way on the Networks/KAD tab.

I made a point of connecting to a big server with lots of files and users.  Finally, on the Search screen, I changed the search type from "local" to "global".

I think the key is simply to use a global search, which might not necessarily be the default.

---

### Post by Levander on 2008-08-31
There was some lawsuit in Germany and a lot of e2dk servers are being shut down.  If you are going to use e2dk, this is the only server list I know of that is supposed to still have good servers in it:  [http://peerates.net/peerates/index.html](http://peerates.net/peerates/index.html)

I was in #amule on Freenode and some guy told me just to forget about e2dk and use Kad with aMule.

---

### Post by yaztromo on 2009-01-18
Search in amule 2.2.2 seems broken in Intrepid.

I was able to get a working search by installing 2.2.3 available here [http://ppa.launchpad.net/simontol/ubuntu/pool/main/a/amule/](http://ppa.launchpad.net/simontol/ubuntu/pool/main/a/amule/)

Hope this helps someone :)

Edit: KAD search won't do anything until it's connection state is OK (not firewalled) and for me that took a whole day to happen.

---

### Post by nicolasdiogo on 2009-04-17
the previous link worked fine for me (x64)

[http://ppa.launchpad.net/simontol/ubuntu/pool/main/a/amule/](http://ppa.launchpad.net/simontol/ubuntu/pool/main/a/amule/)

add the following line to your synaptic repository (/etc/apt/sources.list) 

deb [http://ppa.launchpad.net/simontol/ubuntu/](http://ppa.launchpad.net/simontol/ubuntu/) hardy main


**thanks yaztromo**

---

