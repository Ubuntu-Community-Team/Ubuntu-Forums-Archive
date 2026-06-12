---
title: "I want to limit my internet speed / minimal requirements to stream flash videos?"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Org1 on 2011-06-24
I stream music/video's and I'd like to limit my internet speed at times when others might be using the internet.
  
Ideally I want something that can shows current network usage and a way to set my max download speed to X.




Also whats the minimal hardware requirements to stream flash video? Preferably 480 video. 

I use Intel celeron 2.7ghz {single core}, 1.25gb ram ddr1, ATI 9550 video card it can stream 360 but it skips and uses 100% cpu.

---

### Post by Abir Valg on 2011-06-25
I am not aware of a graphical tool to set limits, but if you are willing to look into iptables options, there is one to set a limit on bandwidth coming from/to a certain user.

Streaming flash video should be no different then simply sending a file to another computer. If you are streaming to just one person, surely you PC specs are more than enough. 100%CPU? Which streaming program are you using?

---

### Post by Paqman on 2011-06-25
Check your router, you may be able to turn on QoS, which should ensure that nobody on the network runs out of bandwidth totally.

---

### Post by Org1 on 2011-06-25
> **Abir Valg said:**
> 
Streaming flash video should be no different then simply sending a file to another computer. If you are streaming to just one person, surely you PC specs are more than enough. 100%CPU? Which streaming program are you using?

Just using firefox its gota decode the flash video which takes alot of cpu power. I'm not uploading video I'm downloading it. {i.e youtube and its like}

> **Paqman said:**
> Check your router, you may be able to turn on  QoS, which should ensure that nobody on the network runs out of  bandwidth totally.

Turned it on and plunged in the mac addresses I think it should work.

---

### Post by gordintoronto on 2011-06-25
An Nvidia video card with vdpau installed should work fine, if your Internet connection is fast enough. With a 5-meg connection, 720P videos do not stream reliably.

---

