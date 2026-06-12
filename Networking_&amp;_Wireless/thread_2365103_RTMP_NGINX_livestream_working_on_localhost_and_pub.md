---
title: "RTMP NGINX livestream working on localhost and public ip for self, but not for others"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by luc9 on 2017-07-02
Hello,

I was working on this livestream website to give people the opportunity to livestream, but i have one problem, on my side i have my localhost, everything works on there, i can see other peoples streaming to my website, and on my public ip (that is visible and accessable by everyone) i can see theirs too.

But the problem is, whenever someone from outside my own pc tries to get on my public ip and watch the livestream, it gives an error:

[COLOR=#AAAAAA][FONT=Whitney]'No compatible source found for this video'
[/FONT][/COLOR][COLOR=#AAAAAA][FONT=Whitney]
[/FONT][/COLOR]I am using videoJS to show the video. 
I am also using bridged network between my windows pc and my virtualbox ubuntu

Nginx listens to port 999, which is portforwarded.
Livestream listens on port 1935, which is also portforwarded, other people can access it, but the video simply wont show for other people?


I hope that anyone can help me with this, sorry if its not enoug information!

---

