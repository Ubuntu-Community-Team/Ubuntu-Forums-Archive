---
title: "Can you stream content from ubuntu to a PS3?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-11-14
I was not sure about this one, can you stream content from a laptop with ubuntu on it to a Ps3? I know windows can do it. Is there any programs that can do it?

---

### Post by D3mon_Spawn on 2009-11-14
well with windows you use windows media player...maybe try running windows media player through wine. Can't guarantee this will work, but its just a thought.

---

### Post by Rave Gloves on 2009-11-14
Dont you need to set up some kind of server so your ps3 can "partner" with your laptop? Im sure it will allready be set up in windows but im not sure about ubuntu.

---

### Post by Rave Gloves on 2009-11-14
Im going to bump this, i want to watch movies that are on my laptop on my ps3, without burning disks and all that.

---

### Post by sandyd on 2009-11-14
> **Rave Gloves said:**
> Im going to bump this, i want to watch movies that are on my laptop on my ps3, without burning disks and all that.
try the vlc streaming server.

---

### Post by SushiR on 2009-11-14
You can use [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/") or [media tomb]("https://help.ubuntu.com/community/MediaTomb")

---

### Post by phishie on 2009-11-14
You can easily do this using mediatomb.
```
sudo apt-get install mediatomb
```

Just add the files/ folders you want to be streamed though mediatomb's web controls, then you could start streaming it though the ps3. Almost no configurations required. ;)

---

### Post by Ewingo401 on 2009-11-14
+1 for media tomb.  Its crazy easy to get up and running.

---

### Post by chriscross93 on 2009-11-14
+1 for media tomb.  There really is no configuration required.  What you are doing is setting up your computer to be a UPnP server (PS3 is the client).  This will also work for any other devices on your network, or the over the internet if you open the port.  Here is a guide that uses a PS3, how convenient...

[http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me]("http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me")

---

### Post by coldReactive on 2009-11-15
> **chriscross93 said:**
> +1 for media tomb.  There really is no configuration required.  What you are doing is setting up your computer to be a UPnP server (PS3 is the client).  This will also work for any other devices on your network, or the over the internet if you open the port.  Here is a guide that uses a PS3, how convenient...

[http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me]("http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me")

Got a link on how to start it as a daemon so that we don't have to manually start it?

---

### Post by renkinjutsu on 2009-11-15
> **SushiR said:**
> You can use [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/") or [media tomb]("https://help.ubuntu.com/community/MediaTomb")

plus 1 for ps3mediaserver.. It's what i use, but you'll need to install mplayer/mencoder to do the decode/encode the videos for streaming


also, plus 1 for hugh laurie

---

