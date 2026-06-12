---
title: "firestarter security issue?"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by polemarchus on 2006-12-30
Hi everyone,

I have been running firestarter for a while now and although the GUI does not load on boot it still appears to be running. I have checked the status of firestarter using 
```
ps -aux | grep firestarter
```
and also
```
sudo /etc/firestarter/firestarter.sh status
```
and both tell me that it is functioning correctly.

However, when doing a port scan with the utility on [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) my computer fails. If I manually start the GUI it passes but fails when the GUI is not active, even though the above commands show it to be running.

Is this a problem and how might it be resolved if it is?

Cheers, Joe

---

### Post by Crakie on 2006-12-30
First of all, you're right: Firestarter is supposed to run even when the GUI is not active.

I know the site you're using. I used it often configuring Windows machines. How exactly does your computer fail? Are there any ports open? My own system, for example, always fails the stealth analysis because it responds to ping. Not much to worry about, since all my ports are closed.

(The ping response is actually coming from my router by the way and I cannot figure out on how to make it stop doing that).

---

### Post by handy on 2006-12-30
I like to use iptables without the Firestarter interference.

You might like this how-to by Frodon:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

It works beautifuly & is really easy to setup & modify.

After you have read it through once, it will take you much less than 10 minutes to set up your computers in the future! :KS

---

### Post by polemarchus on 2006-12-31
Cheers Guys, 

Thought someone might suggest iptables - been meaning to have a look at them for a while! So might have a go in the near future!

I have just been failing on the stealth test but as it is not my router that is the problem I am still confused as I fully pass everything when the GUI is active. 

Will post more as and when I find out!

---

### Post by aidanr on 2006-12-31
on the firestarter website, in the faq section it shows you how to have firestarter (the gui) start automatically

---

### Post by handy on 2006-12-31
My understanding is that Firestarter is  basically just a front end for iptables anyway?!

---

