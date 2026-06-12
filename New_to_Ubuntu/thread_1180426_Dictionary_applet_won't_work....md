---
title: "Dictionary applet won't work..."
date: 2009-06-06
forum: New to Ubuntu
---

### Post by sdim on 2009-06-06
Hi,everyone.
I'm just trying to look up some words on the Dictionary applet,but after I type the word and hit Enter,nothing happens.It just says after a while:
"Error while looking up definition
Connection timeout for the dictionary server at 'dict.org:2628'".

Any help?

many thanks.

---

### Post by baruch60610 on 2009-06-06
Hi, Sdim:

Are you connected to the Internet when you try to use the dictionary?  It's an online resource, meaning the applet looks up the words online (using port 2628..  See if you can get it to work when you're connected.

If you *were* connected to the Internet, then it sounds like your firewall is blocking port 2628.  Use [iptables]("https://help.ubuntu.com/community/IptablesHowTo") to open up port 2628 for you.

Hope this helped.

---

### Post by sdim on 2009-06-06
Thanks.
Yes,I know I have to be connected (and I am).
I suspected the firewall and tried to make an exception,but I couldn't.I'll try again.
Many thanks.

BTW:How can I allow incoming traffic through port 2628,as the message says?
    I'm not too familiar with commands.
    I'm using Gufw.

---

### Post by sdim on 2009-06-06
It's not the firewall.
I shut it down but still the Dictionary doesn't work.

---

### Post by InkyDinky on 2009-06-07
Does it work today?  I was having a similar problem yesterday. I could ping the dict server but kept getting a time out message.  However, today everything worked without changing anything.

---

### Post by ecmatter on 2009-06-07
I had the same problem yesterday.  Today it works.

---

### Post by Sir Jasper on 2009-06-07
Hi,

I had a similar problem. My Firewall is active and after I allowed dict on 2628 it worked. I didn't understand why though as typing dict.org into Firefox worked.

My regards

PS I added it to my outbound whitelist.

---

### Post by brijith on 2009-07-31
hai Everyone.

I too had the same problem. because of that I reached to this post after googling. I got it corrected just now. What I did is just took its preferences by right clicking in the panel dictionary icon. And clicked in the **add** button and simply clicked again in the **add** button in the new window.

After that it worked for me !!!

**[COLOR="DarkOrange"]Thanks[/COLOR]**

---

### Post by afeasfaerw23231233 on 2009-07-31
Hi, I know it's a bit off topic. Did any of you try stardict? It can work offline and I can add additional dictionaries on it. It also has scan function.

---

### Post by Zanzibar on 2009-09-13
I've had a similar problem. It turned out the firewall on my router was blocking the port. I had to enable TCP port 2628. It now works just fine.
I am not using a firewall on my ubuntu 9.04 and haven't changed iptables so I am sure the router is the reason- at least in my case.

---

### Post by RabbitWho on 2009-09-13
> **afeasfaerw23231233 said:**
> Hi, I know it's a bit off topic. Did any of you try stardict? It can work offline and I can add additional dictionaries on it. It also has scan function.


I use Artha, I love it. 
I could only find a .exe for Stardict, and I'm pretty happy with Artha now..

---

