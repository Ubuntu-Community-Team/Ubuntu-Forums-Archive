---
title: "Huh??"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-06-24
OK this is odd, but I did it a few times just to make sure I wasn't going nuts. Here's the story:
I boot up my laptop, wireless connects. I go to view a website and it takes a little longer than I am used to since I have a 10 Mb line connected to my router. Sites can take up to 15 seconds to load. 
Here is the experiment:
I plug in my ethernet line to check the speed. Loads very fast, getting the 10 megs I am buying.
Unplug the ethernet cord, and guess what? I get the same results all of a sudden. 
Tried this 3 times in a row and the results were the same.

What in the world could be causing this?
I have taken a few networking classes in my life and never had a question like this come up.
BTW - I am using the broadcomm driver supplied with fiesty. I tried the ndiswrapper and it did not work.
I am very happy with the speed I get once I plug in the ethernet cord and unplug it, but why could this be happeneing?
Thanx in advance!

---

### Post by benanzo on 2007-06-24
I would think it is something to do with ARP not updating in a timely fashion when first using your wireless.

A little experiment you can try is to time the ARP broadcast when your wireless is slow:
```
time arp -a
```
then do it when connected to ethernet and again when your wireless is fast.

If there are significant differences your can clear your ARP cache by restarting your interface:
```
sudo /etc/init.d/networking restart
```

The problem could also be that the ARP responder in your router is slow or just weird.

Just a guess.

---

### Post by lsutiger on 2007-06-24
Here's the output:
On Boot - Wireless
```
rreal    0m5.202s
user    0m0.004s
sys     0m0.004s

```

On Ethernet Cable:
```
real    0m5.024s
user    0m0.008s
sys     0m0.004s

```

Back on wireless
```
real    0m5.024s
user    0m0.008s
sys     0m0.004s

```

So the first one looks significant 202 vs 24

---

