---
title: "Remote desktop works, but not from work"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by upalox on 2009-07-22
hi,
im complete stranger to linux so i decided to install ubuntu 9.04 desktop on my old computer(without monitor) and access it remotely to learn some new stuff. ubuntu remote desktop enabled, for vnc client i use tightvnc (windows). it works from LAN, it works from my girlfriend computer which is outside LAN(so port 5900 forward at router seems to be ok), but it  no way to go from my works computer. probably employer blockade uncommon ports. what can i do? is able to set vnc server listening port to 80 or something? thank you much for help

---

### Post by Stebalien on 2009-07-22
I would recommend forwarding port 80 on your router to port 5900 on your machine. You need root to bind to the lower ports and running a vnc server as root would be a very bad idea. This is how the connection would look:
```
[You] (port 80 out) ---> 
(port 80 in) [Office Router] (port 80 out) ---> 
(port 80 in) [home router] (port 5900 out) ---> 
(port 5900 in) [home computer]
```

---

### Post by superprash2003 on 2009-07-23
do you have firestarter or anything running in that machine?? use this scanner to see if 5900 is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by upalox on 2009-07-23
5900 port is opened, remote desktop works in general, but not from my work machine. i[COLOR=Black] t[/COLOR]ried Stebaliens scheme but my uploading speed decreased to 10% of normal, web browsing was almost impossible. further more, i realized that im behind proxy server. can i set proxy server setting in vnc like in browser?

---

### Post by Old_Grey_Wolf on 2009-07-23
I would suggest talking to the person or people that are responsible for maintaining the computers and network where you work.

If the company is blocking they will tell you. They may also tell you that trying to bypass company security is ground for termination.

---

### Post by superprash2003 on 2009-07-24
as mentioned i above , i feel your company is blocking this connection therefore your not able to connect

---

### Post by swoody on 2009-07-24
Yes, as the other's have mentioned, this does sound like something your company has blocked rather than just some error in between. To cut back on risks, I'm guessing your company has blocked anything that is deemed to be outside of what is necessary to accomplish the company's goals. So all other network activity is probably banned. Your best bet may be asking someone in the tech dept, but as mentioned above, it may be bad if they think you're trying to get around security measures.

---

