---
title: "ncpmount issues -- rather strange error"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by twiceasworn on 2007-10-18
Ok, so I am running Ubuntu Feisty Fawn on a 3 ghz intel pentium 4 processor with 512 mb of ram. 80 gig hard drive  etc...I don't really know what information is needed for this particular issue, so if you need more info just say so and I will get it for you.  Also, I am not newbie when it comes to most of this stuff, so don't feel the need to dumb things down.  I am a web/network admin and I use the command line all day long, so it isn't scary.

So, about two weeks ago is when I decided to put ubuntu on my desktop here at work.  When i first installed, the first thing I did was get ncpfs and ipxutils so that I could mount the Novell shares we have here.  The command I was using to mount the NFS was 
```

sudo ncpmount -A xxx.xxx.xxx.xxx -S server.name.com -U username /home/gsb/HD
```

Now at first everything was hunky dory and it would prompt for my password and let me mount.  However, in the past week whenever I try to mount the volume it spits this error out at me 

```
ncpmount: No such entry (-601) in nds login
```

So, I figured something screwed up my user account on the Novell server.  However after spending a considerable amount of time with that box's admin, we can not figure out why it is doing this.  My account is there, it is free and open for me to login but for some reason ncpfs cant find it?  Any help would be appreciated, while it is not a life or death situation it is extremely frustrating.

---

### Post by twiceasworn on 2007-10-18
bump.  seriously, any idea is better than no ideas.

---

### Post by luke2760 on 2007-10-18
I get this after ubgrading to Gutsy. I got no such errors under Feisty.

I did do a clean reformat of my root partition, but just the same.
```

Logging into server.name.com as username
Password: 
ncpmount: Invalid server response (-330) in nds login
Login denied.

```

---

### Post by luke2760 on 2007-10-18
You might take a look at [https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/140464' ](https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/140464' ) 

You said Feisty Fawn, but it's possible you upgraded to the Gutsy ncpmount?

---

