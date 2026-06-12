---
title: "forwarding audio output"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by xolot1 on 2006-09-29
the question:
can i forward my audio output to another computer?

background:
i finally got wireless working on my laptop in my dorm with my own router. i play music through two large tower speakers that rest on my desk, through an amp. now that wireless is working, the only cable that keeps me from "working" on my bed connects my laptop with the amp.

the setup:
ive included 2 diagrams, "before.jpeg" is what is set up now, and "after.jpeg" is what id like.
before:
[IMG]http://i93.photobucket.com/albums/l68/xolot1/before.jpg[/IMG]
after:
[IMG]http://i93.photobucket.com/albums/l68/xolot1/after.jpg[/IMG]

one router connects 3 computers (my laptop connects wirelessly). any/all of the computers could be attached to the amp.

vision:
that somehow i could forward **all audio** from my laptop, via the router, to one of the servers, which immediately passes the signal along to the amp.

i dont know much about streaming, but i was thinking of something to the effect: all audio output is converted to a stream (http, or something), and the server plays the stream in realtime, all the time.


is this possible?
what options do i have?

---

### Post by jmmcd on 2006-09-30
I've never done anything like that, but it is possible alright. It's not really a networking problem, so you might have better luck on another forum, but to start off, you should google for "icecast". 

As I understand it, you would set up an icecast streaming server on your laptop, and run xmms or equivalent on your desktop.

Dave Philips (a great guy from the world of linux audio) has a series of tutorials on [www.linuxdevcenter.com](www.linuxdevcenter.com) on this and related stuff, you can find it with google.

---

### Post by xolot1 on 2006-09-30
thank you, your resources should provide me with a lot of material browse and learn. very helpful!

willi

---

