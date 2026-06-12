---
title: "Mounting folders on startup"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Nickopotamus on 2009-10-11
Hi guys

Really stupid question, but no amount of googling will help me find the answer (GIGO...). Anyways, I'm using two hdds shared between an Ubuntu and Windows install - one for documents, mounted as /media/Data and one with media (original name of /media/Media. Within these are My Documents, My Music, etc, so I've mounted them using

```

sudo mount --bind "/media/Media/My Music" "Music"
sudo mount --bind "/media/Data/My Documents" "Documents"
...

```

Works a charm, but then the links disappear when I restart.

So my question is twofold:

1) Is that the best way to achieve what I want to do?
2) How do I make it mount automagically? I've tried playing with fstab but it's confusing me...

Cheers
Nick

---

### Post by sisco311 on 2009-10-11
the corresponding fstab entries should look like this:

```

/media/Media/My**\040**Music       /home/username/Music        auto    bind 
/media/Data/My**\040**Documents    /home/username/Documents    auto    bind
```


[quote=man fstab]If the name of the  mount  point  contains spaces these can be escaped as '\040'.[/quote]

---

### Post by m0re0n on 2012-04-02
> **sisco311 said:**
> the corresponding fstab entries should look like this:

```

/media/Media/My**\040**Music       /home/username/Music        auto    bind 
/media/Data/My**\040**Documents    /home/username/Documents    auto    bind
```

I tried the --bind command in /etc/rc.local and it didnt work.
so thanks so much for this answer! it saved my home mediaserver :guitar:

---

