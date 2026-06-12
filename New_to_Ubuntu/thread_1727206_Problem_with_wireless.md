---
title: "Problem with wireless"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by de_island on 2011-04-12
Hey.

I'm having trouble with using Ubuntu on my wireless network.

I can get it to connect properly and it works fine except for when I want to have more than one programme access the internet. One of the programmes appears to hog all the bandwidth and the other(s) get nothing. I know that it's not a bandwidth problem since it's a 20Mb/s connection.

Programmes within programmes work fine, (eg. I can still browse the web with Firefox while something like Downthemall is working) but if I wanted to run Chrome and Firefox at the same time, only one of them will be able to use the internet.

This is fairly awkward when trying to use Transmission or anything of that ilk because I can't browse the internet while that's running.

Has anyone come across this before?

---

### Post by sanguinoso on 2011-04-12
I have never heard of such a thing. So Firefox works on its own, as does Chrome and transmission?

---

### Post by de_island on 2011-04-12
They all work fine individually, but never together.

If I have Transmission running correctly and then open Firefox, Transmission will either lose its connection to the internet and Firefox will start working or Transmission will continue and Firefox will show a timeout error. The preference seems to be entirely random.

---

### Post by akakingess on 2011-04-12
I know this shouldn't make a difference, but how are you connecting to the net, is it a router, switch, sharing some other connection, etc. This info could help us to identify where the issues lies. Also, could you start a download within FireFox and then run a ping in the background and let it just keep on pinging and see if you get some time outs?

FYI: To do a never-ending ping add a -t to the end of the command, i.e.  'ping google.com -t' (without the quotes of course) and it will just keep pinging until you hit ctrl-c to stop it. The advantage is you don't have to watch the 'console', you can just let it go for a while and scroll up and down after stopping it to see if there were any timeouts.

---

### Post by de_island on 2011-04-12
I'm connecting through a router at home, and I'm currently the only one on the network.

I just started a download (the Ubuntu install file, of course) and Firefox can still browse. The time per ping has increased (it's taking 3-4 times longer), but I assume that's expected since the download is running at over 1 MB/s.

Then I ran Transmission (which was downloading something at the time) and the ping is still working with a 0% loss and no timeouts. This is confusing, since Firefox couldn't access anything, despite the ping working. :-S

---

### Post by akakingess on 2011-04-12
Is this the only computer accessing the net and is it going through a modem (not sure how things are done in Ireland) or is there a router or switch to which it is connected. If there is a router of some sort, I would just check to make sure that nobody else is also connecting through your connection/router. Let us know just a few more details as far as the connection, not just your computer, but the rest of the setup as well and maybe we can come up with some more troubleshooting.

---

### Post by de_island on 2011-04-12
This is definitely the only laptop in the house that is accessing the network. Unless someone in a neighbouring house has managed to hack it, I can assume that it's the only one in general.

Housemates using Windows and Mac OS can use our internet without encountering this problem, so I'm pretty sure that it isn't a problem with the connection itself. The problem must be with the hardware in my laptop or with Ubuntu.

In any case, I don't know all that much about the connection. The house is set up for internet and television which both come in through the same cable. After separating, it just goes through our router which is a Cisco EPC2425.

I'm also using a Dell Wireless 1397 WLAN Mini-Card

Sorry I can't tell you any more.

---

