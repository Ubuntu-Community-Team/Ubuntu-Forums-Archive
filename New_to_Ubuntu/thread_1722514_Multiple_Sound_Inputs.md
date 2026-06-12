---
title: "Multiple Sound Inputs"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by osc1882 on 2011-04-05
Hello I just started using Mumble and I had some questions about recording (or in this case streaming). In windows I had the option to use line in or master audio as my audio input channel. I was wondering if Ubuntu could do anything like this or greater. On mumble I would like to be able to stream not just my USB mic but also sound from a program, like music or sound clips or something. Anyone know anything about this?

---

### Post by sandyd on 2011-04-05
> **osc1882 said:**
> Hello I just started using Mumble and I had some questions about recording (or in this case streaming). In windows I had the option to use line in or master audio as my audio input channel. I was wondering if Ubuntu could do anything like this or greater. On mumble I would like to be able to stream not just my USB mic but also sound from a program, like music or sound clips or something. Anyone know anything about this?
Use JACK-audio-connection-kit. you can use it to route sound through different applications, and mix streams.
[[IMG]http://img861.imageshack.us/img861/3108/snapshot1c.th.png[/IMG]]("http://img861.imageshack.us/i/snapshot1c.png/")

---

### Post by osc1882 on 2011-04-06
Does it have a different name then "JACK-audio-connection-kit", I'm having a hard time finding it to install.

---

### Post by Daniel0108 on 2011-04-06
> **osc1882 said:**
> Does it have a different name then "JACK-audio-connection-kit", I'm having a hard time finding it to install.

```
sudo apt-get install jackeq
```

JackEQ is a tool for manipulating from/to multiple input/output sources.

It runs on the JACK-audio-connection-kit.

Yours,
Daniel

---

### Post by osc1882 on 2011-04-06
"jackEQ: Cannot contact JACK server, is it running?"
get this when running it on terminal.

---

### Post by Daniel0108 on 2011-04-06
> **osc1882 said:**
> "jackEQ: Cannot contact JACK server, is it running?"
get this when running it on terminal.

You have to install jack :)

Here's a tutorial: [http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730)

Yours,
Daniel

---

