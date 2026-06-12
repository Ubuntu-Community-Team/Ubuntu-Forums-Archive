---
title: "Jaunty running HOT + unexpected shutdowns"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by belikralj on 2009-05-11
I have had issues with 9.04 running a bit on the hot side and shutting my laptop down as it got up to 80*C so I was wondering if anyone else has had similar problems since I have no idea as where to even begin looking for solutions. Also it happened a few times after leaving the computer off for several hours that it just wouldn't start, it boots up and as it's about to start GDM bugs out and powers off instantly. I'm happy with Jaunty and have no other problems with it but this one is a bit of a pain in the rear because I now have to manually watch the temperature before it goes critical.

Also Vista is quite happy to work at 80*C and usually doesn't go higher even under full load, so could I (or should I) make ubuntu shutdown at 85*C rather than 80?

I know I left the problem quite vague but if you have any ideas, no matter what they are, put them down cause I'm a little stuck.

PS. This happened mostly with Compiz on but even when I turned it off it still overheated a few time. So I'm wondering if I can make ubuntu lower the processor load once temperature goes critical rather than powering off...

---

### Post by nhasian on 2009-05-11
wow 80C seems pretty hot.  can you give us more details about your computer?  Desktop or laptop?  what model of cpu do you have?

```
cat /proc/cpuinfo
```

or

```
lshw -C cpu
```

also what kind of video card do you have?

```
lshw -C display
```

Is your CPU or GPU running at 80C?  Is that with a heavy workload like editing video or raring/unraring archives or is that your idle temp?

also if you have a desktop do you know what cpu cooler you installed?

---

### Post by yaknowwat on 2009-05-11
A computer shouldn't be running at 80 C period. 50C is hot.

Jaunty might be pulling more strength from the hardware or spinning the fans less to conserve power.  Though seriously 80C you really need to get your computer checked on now from the heat.

---

### Post by nhasian on 2009-05-11
I think it depends on the processor.  my centrino duo laptop is idling right now at at 45C for the first core and 50C on the 2nd.  Nvidia GPU is even higher at 70C.

> **yaknowwat said:**
> A computer shouldn't be running at 80 C period. 50C is hot.

---

### Post by aksheyjawa on 2009-05-11
For a temporary solution may be you can run the cpu at lower frequency. You can set it using the gnome CPU Frequency Scaling Monitor applet. And you can track the temperature using sensors-applet.

---

### Post by capnthommo on 2009-05-11
hi belikralj,
following my usual principle of go for the simplest first, have you checked that the fan inlets and so on are clear and there is little dust and fluff?  i assume you have already checked that?
cheers
nigel

---

