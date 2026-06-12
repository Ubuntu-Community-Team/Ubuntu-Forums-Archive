---
title: "Is it true that downloading multiple files simultaneously decreases the average..."
date: 2011-06-09
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-06-09
download time? If so, why?

How do I circumvent this?

---

### Post by Paqman on 2011-06-09
Depends. 

A lot of things can affect download speeds. If the bottleneck is at your end, then that will be a hard limit on how fast you can download overall, no matter how many downloads you queue up. But the issue could be due to the server(s) at the other end throttling you. Depending on how things are set up at that end you might get more bandwidth for multiple separate files than you'd be given for one download.

There's not really much you can do about that.

---

### Post by brawnypandora0 on 2011-06-09
> **Paqman said:**
> Depends. 

A lot of things can affect download speeds. If the bottleneck is at your end, then that will be a hard limit on how fast you can download overall, no matter how many downloads you queue up. But the issue could be due to the server(s) at the other end throttling you. Depending on how things are set up at that end you might get more bandwidth for multiple separate files than you'd be given for one download.

There's not really much you can do about that.

What are possible bottlenecks on my computer?

How do I find out what the maximum server broadband limit is?

---

### Post by Paqman on 2011-06-09
> **brawnypandora0 said:**
> What are possible bottlenecks on my computer?

Your ISP and the connection they provide you, mostly. There's only a set amount of bandwidth they'll let you have, and you're also limited by the actual copper/fibre/wireless/smoke signal connection you've got. Some ISPs also do traffic shaping, which is deliberately throttling down certain types of content at certain times of day.

> 
How do I find out what the maximum server broadband limit is?

Depends. Some things like file sharing sites will tell you what your max download speed will be for a particular level of service (ie: pay more for faster downloads). But generally you won't know.

---

### Post by jtarin on 2011-06-09
It's common sense....you have limited bandwidth dictated by your provider. That bandwidth is distributed over the number of incoming connections you have.One download=full bandwidth. Two downloads =50% each and so on, but thats not exact science either. There are other factors to consider. Does the server throttle at a certain bandwidth, is your ISP throttling different ports, distance to server and many other factors. The answer in a nutshell is....it's true.

---

### Post by Peter09 on 2011-06-09
Often your router has a page which (amongst other things) tells you what the established maximum connection speed is. This speed is not the one you have bought into but the one that has been established between your router and the exchange. It is dependant on the quality of your connection and other things. For instance I have an 8Mb/sec contract but the line is running at 5Mb/s.
 
This does not give you your (instantaneous) download speed as ADSL is a shared connection and you will be competing with others for bandwidth.

---

### Post by brawnypandora0 on 2011-06-09
What does it mean for an ISP to throttle at different ports?

So since ISPs usually provide less than advertised, can I sue them?

Where do I go to access the connection speed on my router page?

---

### Post by Paqman on 2011-06-09
> **brawnypandora0 said:**
> What does it mean for an ISP to throttle at different ports?

It means they don't want somebody downloading the entire internet via torrents to chew up all the bandwidth and stop grandma from checking her email, so they restrict the amount of bandwidth available to torrents (for example). Since ISPs bundle groups of users together onto a single package of bandwidth, this ensures the other people have enough to do stuff like web browsing.

> So since ISPs usually provide less than advertised, can I sue them?

No.

> 
Where do I go to access the connection speed on my router page?

Depends on your router. Generally 192.168.0.1, or similar. See what brand of router you have and Google it. While you're at it, change the default password if you haven't already.

---

### Post by migs73 on 2011-06-09
ISP's usually advertise download speeds as **UP TO** (although that is usually in small print) 8Mb or whatever. 
If you google 'what is my broadband speed' you'll get lots of sites that'll test it for you.

I don't know the answer to your other question.

:)

EDIT: just tested mine and it is 6.9Mb/s and my ISP tells me it is upto 8Mb. I have tested it at other times and it varies from 5.5 to 7 depending on the time of day, i.e. other traffic from other users.

---

### Post by Mariane on 2011-06-09
A hypothesis: 

If you don't use cache and you download several large files which get saved on different parts of the hard disk, it could slow down the average because the downloading program will get one packet (or piece) of one file, rotate the disk to write it where it should go, then it will get a piece belonging to another file and it will have to rotate the disk again... 

But I don't know if this is true or not, it is just an idea. I avoid downloading too many files at once because I think it slows down the average but I never tested this. 

One thing I know is that some programs are more aggressive than others. I have a slow connection according to: 
[http://www.mybroadbandspeed.co.uk/](http://www.mybroadbandspeed.co.uk/)
Download Speed: 527 kbps (65.9kB/s)
Upload Speed: 132 kbps (16.5kB/s)
and if I use vuze (azureus) nobody in the house can go online at all, vuze is very aggressive, it grabs the bandwith and won't let go. Very nice program when you have a fast connection. 

Mariane

---

### Post by Peter09 on 2011-06-09
> If you don't use cache and you download several large files which get saved on different parts of the hard disk, it could slow down the average because the downloading program will get one packet (or piece) of one file, rotate the disk to write it where it should go, then it will get a piece belonging to another file and it will have to rotate the disk again...
 
While this ***may*** be true under some circumstances its is unlikely to be true for a download from the internet, this is because, in computer terms, it is sitting 99% idle waiting to get packets from a slow download to put on a fast disk. (When downloading look at how often you disk activity light comes on).

---

### Post by Mariane on 2011-06-09
Thanks for that Peter09, it makes a lot a sense. 

Mariane

---

