---
title: "Can I throttle NNTP/119 usenet downloading?"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by thelamer on 2009-02-27
I have hit a wall in getting this to work. 

Basically I am trying to limit the download speed of my newsgroup downloads so my internet is still usable. 

I am using the latest version of HellaNZB and LottaNZB as a frontend under intrepid.  

These are the solutions I have tried: 

- Set limit in HellaNZB.conf- HellaNZB does not limit download speed instead it will use max bandwidth for short periods of time to "average" your inputted speed. (this would be OK if I wasn't trying to play TF2 on another computer and getting ping spikes) 

- WonderShaper- This works, but reduces all of the traffic on my NIC to that set speed, so I cannot browse the web etc as my bandwidth is maxed out. 

- Trickle- This kind of works, but the speed fluxuates sometimes breaking the set limit I launched it with. It also uses about 75%-90% of one of my cores constantly (q6600) not a good thing.

- MasterShaper- I cannot justify turning my computer into a full blown webserver just to throttle the bandwidth of one port.  

- pyshaper- just plain did not work for limiting one ports traffic or application traffic. I don't think it has been updated in awhile. 



Does anyone have any experience limiting the bandwidth for any port usage (21..etc) it will apply the same here. 
Is their a way to configure IPtables to accommodate this? 



Thanks for reading and I hope you have a suggestion!

:)

---

### Post by blueridgedog on 2009-02-27
I use trickle:

[http://monkey.org/~marius/pages/?page=trickle](http://monkey.org/~marius/pages/?page=trickle)

You can install it with 

```
sudo apt-get install trickle
```

You launch it with:

```
trickle -d 50 /path/to/application
```

Here, 50 is for 50KB/s (note big B).  Adjust speed as you see fit.

It is command line only and seems to work better than nothing.

From the man page, worth reading:

     -t seconds   Set smoothing time to seconds s.  The smoothing time deter&#8208;
                  mines with what intervals trickle will try to let the appli&#8208;
                  cation transceive data.  Smaller values will result in a
                  more continuous (smooth) session, while larger values may
                  produce bursts in the sending and receiving data.  Smaller
                  values (0.1 - 1 s) are ideal for interactive applications
                  while slightly larger values (1 - 10 s) are better for
                  applications that need bulk transfer.

You may want to tweak this as it is very granular otherwise.

---

### Post by thelamer on 2009-02-27
Thanks for the suggestion, but I went down that road and it really doesn't work well and it hogs my CPU. 

> - Trickle- This kind of works, but the speed fluxuates sometimes breaking the set limit I launched it with. It also uses about 75%-90% of one of my cores constantly (q6600) not a good thing.

When you are using trickle open up system monitor and check your CPU usage, tell me if you see anything weird.

---

### Post by Lantash on 2009-02-28
This bug has also been reported on launchpad.net: [https://bugs.launchpad.net/ubuntu/+source/trickle/+bug/234342](https://bugs.launchpad.net/ubuntu/+source/trickle/+bug/234342)

Too bad. trickle seemed like the perfect solution.

---

### Post by thelamer on 2009-02-28
ok so let me rephrase this, 

has anyone found a workaround to the Trickle 100% CPU bug?

---

### Post by thelamer on 2009-02-28
Well I came up with a roundabout solution. I thought back to when my printer wouldn't work and I used a VM to print from my machine. 

Should have seen it before, just run a windows usenet program that can control bandwidth with wine. 

[IMG]http://www.ryankuba.com/DropBox/AltBinz.png[/IMG]

Alt.Binz works great even pars and rars properly. 

I really wish their was a linux solution though, I don't like running a wine usenet program as it still uses more CPU than I would like just to download files.

---

